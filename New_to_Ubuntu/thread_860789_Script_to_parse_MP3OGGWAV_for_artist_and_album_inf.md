---
title: "Script to parse MP3/OGG/WAV for artist and album info?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by bethebunny on 2008-07-15
I've been scouring plaintexts of these for a few hours now trying to discern a pattern that I might be able to utilize in a regexp to filter these out; obviously such things exist, since if you right click on a song and view its properties, oftentimes the artist and album will show up.

Any ideas on how to do this / where it's already been done?

Shouldn't have any effect on the scripting, as both use bash, but this is for use on a debian headless ampache server.

---

### Post by txcrackers on 2008-07-16
There are quite a few CLI-driven ID3 tools - I'm currently using *eyed3* available from the Ubuntu repositories. Open your package-manager of choice and search for applications that have ID3 in the description. Play with them and have fun...

---

