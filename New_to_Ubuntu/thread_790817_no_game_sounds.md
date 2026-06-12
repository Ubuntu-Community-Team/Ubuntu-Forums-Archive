---
title: "no game sounds"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-11
so in a previous thread of mine (cant remember now, might check later), i said i had onboard sound and a sound card, and to fix a problem with onboard not playing mp3s i took out the sound card. now it plays mp3s, but not sound in games, like battle for wesnoth, sauerbraten, nexuiz, etc. it couldnt before i took out the card, but then again it could play mp3s either. perhaps i need drivers for my onboard? i believe it is an NVidia NForce 405...

---

### Post by pro003 on 2008-05-11
reconfigure your wine

```
gksu nautilus 
```

go to your home folder, press ctrl+H and delete folder .wine

then:

in terminal type as user!!!

```
winecfg
```

---

### Post by Zopiac on 2008-05-11
> **pro003 said:**
> reconfigure your wine

```
gksu nautilus 
```

go to your home folder, press ctrl+H and delete folder .wine

then:

in terminal type as user!!!

```
winecfg
```

??? i did nautilus, ctrl+h, delete .wine, but then, what???

---

### Post by pro003 on 2008-05-12
then in terminal type as user!!!

```
winecfg
```

you'll get one window opened and its wines... you will have to configure your drives, default sound , etc...

---

### Post by Zopiac on 2008-05-12
zopiac@zopiac:~$ winecfg
The program 'winecfg' is currently not installed.  You can install it by typing:
sudo apt-get install wine
bash: winecfg: command not found
zopiac@zopiac:~$ 
 and why would i need wine anyways? i just recently uninstalled it.

---

### Post by Zopiac on 2008-05-22
bump

---

