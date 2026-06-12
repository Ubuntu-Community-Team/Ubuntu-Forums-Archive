---
title: "Help with real audio file"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Tews on 2008-11-28
what is the best way to play Real audio files??
any help will be greatly appreciated!:)

---

### Post by evilkastel on 2008-11-28
You'll need to install the aproppiate codecs. the codecs are architecture dependant. If you are running an x86 ubuntu, use

```
sudo apt-get install w32codecs
```

if you are running x32_x64 architecture use

```
sudo apt-get install w64codecs
```

As long for the player, mplayer will play them, and amarok, banshee and rithmbox might play them. realplayer will play them

```
sudo apt-get install realplayer
```

I will suggest anyhow, to convert the format to an regular audio format. realaudio is not that good.

---

