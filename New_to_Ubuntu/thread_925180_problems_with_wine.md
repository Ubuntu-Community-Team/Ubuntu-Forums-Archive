---
title: "problems with wine"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by pyromanic123boom on 2008-09-20
Ok...So I'm trying to get that old game SimTower running on ubuntu using wine, and am hitting a few problems.
At the end of the installer, it tells me it can't access wavmix16.dll, but that's just a audio driver. I disable the audio in winecfg, so now I can open the program in my wine c drive. It loads the game splash, and just stays like that no matter what I do. Then I haveto hit ctrl+alt+delete and logout and back in to get rid of the crashed program in wine. Any ideas?

---

### Post by temporos on 2010-12-24
I know I'm resurrecting a thread here, and I'm not particularly fond of zombies, either.  :p  However, I found a workaround for this.

The *wavmix16.dll* file can be downloaded [here]("http://members.chello.at/theodor.lauppert/download/wavmix16.zip").  Once downloaded, extract the DLL file and copy it to the Windows system directory.

```
cp WAVMIX16.DLL /home/[USERNAME]/.wine/drive_c/Windows/system/WAVMIX16.DLL
```

Then, launch the program in a terminal window.

```
wine /home/[USERNAME]/.wine/drive_c/Maxis/Simtower/simtower.exe
```

An alert window will appear warning you that there is no sound support.  Click "yes" to run the program anyway.  I can't fathom why the Wine developers didn't include this DLL.

---

