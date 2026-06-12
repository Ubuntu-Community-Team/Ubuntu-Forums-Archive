---
title: "[SOLVED] Shockwave/Flash not working in ff3beta5"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-05-28
Just wondering, can anyone else click this link and see the main content?

[http://www.miniclip.com/games/big-catch/en/](http://www.miniclip.com/games/big-catch/en/)

Says I need a plugin but :( doesn't work.. 
orb

---

### Post by id1337x on 2008-05-28
Do you have JavaScript enabled? It may be that is loading the noscript from the source which loads a .dcr file.

```
<embed src="gioco.dcr" logo="false" swStretchStyle="fill"swRemote="swSaveEnabled='true' swVolume='false' swRestart='false' swPausePlay='false' swFastForward='false' swContextMenu='false'"menu="false" pluginspage="http://www.macromedia.com/shockwave/download/" width="750" height="490"></embed>

```

---

### Post by sayakb on 2008-05-28
```
sudo apt-get install ubuntu-restricted-extras
```

Or simply install the flashplugin-nonfree package.

---

