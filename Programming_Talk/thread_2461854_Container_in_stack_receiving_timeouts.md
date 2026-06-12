---
title: "Container in stack receiving timeouts"
date: 2021-05-08
forum: Programming Talk
---

### Post by samithdfm on 2021-05-08
This is on Synology DSM latest, using linuxserver/nzbget:latest and fully updated docker compose. Using Portainer to review stacks/networks/containers in Docker.


So up to now I’ve been using multiple individually-run containers deployed with docker run commands for my [[COLOR=#696969]NZBget[/COLOR]]("https://outdoorbasketballshop.com/best-outdoor-basketball-hoops/")/*arr goodness, and they’re working fine. Then I discovered the joys of docker-compose, so went about setting up a multi-service yaml to deploy nzbget, sonarr and radarr. They deploy nicely.


Sonarr connection tests are successful to NZBget, it connects to my indexers, searches work and reports are sent to NZBget.


NZBget then attempts to download the received reports, but even with all news-server settings being the same (and everything else as far as I can tell having multiple-checked loads of times now) returns `[ERROR] Connection to [news server] failed: ErrNo 110, Operation timed out` on both news servers. They still return successful tests in the individual container I’ve been using up to now, but not in the stack container.


I’ve not found anything online which seems to have had this same issue (the other ErrNo 110 topics on this site seem to be people not using an actual news server) so any help/suggestions I could chase on this would be great. For anybody asking, the compose file looks like this, and the issue persists when the network assignments are removed and it’s just left to docker’s auto generation:


```
```
services:
  radarr:
    image: ghcr.io/linuxserver/radarr
    container_name: radarrCompose
    environment:
      - PUID=[MYPUID]
      - PGID=[MYPGID]
      - TZ=Asia/Tokyo
      - UMASK_SET=022
    volumes:
      - /volume1/docker/Compose/Radarr:/config
      - /volume1/Test/ComposeStackTest/Movies:/movies
      - /volume1/Test/ComposeStackTest/Downloads:/downloads
    ports:
      - 7879:7878
    restart: unless-stopped
    networks:
      - Docker


  sonarr:
    image: ghcr.io/linuxserver/sonarr:preview
    container_name: sonarrCompose
    environment:
      - PUID=[MYPUID]
      - PGID=[MYPGID]
      - TZ=Asia/Tokyo
      - UMASK_SET=022
    volumes:
      - /volume1/docker/Compose/Sonarr:/config
      - /volume1/Test/ComposeStackTest/TV:/tv
```
```

---

### Post by TheFu on 2021-05-08
I'm sorry.  Exactly which Ubuntu release is being used?

---

