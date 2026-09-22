# Madden League Network — Connected Edition

This is the real data-connected architecture for the custom Madden League Network.

## How it works

Madden Companion App
→ this server's Companion export URL
→ server stores the POSTed franchise tables
→ `/api/data`
→ the visual website

The server mirrors the Companion-App exporter route pattern used by existing Madden exporter projects:
- `/:platform/:leagueId/leagueteams`
- `/:platform/:leagueId/standings`
- `/:platform/:leagueId/week/:weekType/:weekNumber/:dataType`
- roster routes

## Important

The current `https://mxport.herokuapp.com/samb0903` URL belongs to the old exporter and its GET page only says "Madden Data". It is already receiving your exports, but that old service does not provide this custom website with a public read API. Therefore this project needs to be deployed as your own receiver before the Companion App can send directly to it.

Once deployed, you will change the Companion App export URL ONE TIME to the new site's export URL. After that:

Play/advance → Companion export → website updates.

## Deployment

This project is designed for a Node/Express host. It needs a persistent filesystem or database so exported data survives restarts.

For a production version, replace `data/madden-data.json` with MongoDB/another persistent database.

## Local test

`npm install`
`npm start`

Then open the printed local URL.

## Next build

The frontend is already wired to real stored export tables. The next polish pass can add:
- complete roster/team mapping
- all player stat leaders
- box scores
- division/conference standings
- playoff bracket
- transactions
- draft history
- season history
- automatic league-news/storyline generation
