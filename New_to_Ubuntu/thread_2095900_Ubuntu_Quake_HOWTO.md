---
title: "Ubuntu Quake HOWTO"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by scar3crow on 2012-12-18
sudo apt-get install darkplaces darkplaces-server

sudo mkdir /usr/share/games/quake

sudo mkdir /usr/share/games/quake/id1

# mount Quake CDROM and navigate to the id1 folder

sudo cp pak0.pak pak1.pak /usr/share/games/quake/id1

# mission packs ctf and maps go in their corresponding folders

# start the game with:

darkplaces -basedir /usr/share/games/quake

# to set up a dedicated server add the following to /etc/rc.local

/usr/games/darkplaces-server -basedir /usr/share/games/quake +exec debian_server.cfg&

# (one line before exit 0)

# and open up port 26000

# be sure to edit debian_server.cfg

included are two cool Quake.png icons if you wanna make custom launchers
copy them to /usr/share/icons/hicolor/

enjoy ;)

--scarrs

ask me about my quake servers :)

---

### Post by LuciferRex on 2012-12-18
Wow, looks awesome!  I may have to try this out :)

---

### Post by scar3crow on 2012-12-18
The quakespasm client is really hard to configure I made this faq for all you old school gamers :D

---

