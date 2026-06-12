---
title: "[SOLVED] Portable Starcraft to work in Ubuntu?"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by lehvrhon on 2008-09-25
Hi, I have switched to ubuntu last week and courious if it is possible to play portable starcraft or portable WOW using WinE?

Thank you,

---

### Post by medic2000 on 2008-09-25
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Also site can help:

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by lehvrhon on 2008-09-25
thank for the reply medic2000, but I don't have cd to install, I only have a streamlined starcraft+broodwar folder, :( could their be possibility this would work?

---

### Post by medic2000 on 2008-09-25
Yes it works for me with SC+BW and with latest patch.But first just add starcraft or broodwar.exe to "winecfg".

To open it type in terminal or first hit "alt+f2" then write winecfg.

---

### Post by lehvrhon on 2008-09-26
Hi medic2000, I think that is lacking to run the starcraft, but can you kindly tell me how to write the starcraft.exe? or to any link that will lead me in writing the winecfg? Thank you very much,

---

### Post by medic2000 on 2008-09-26
Hi,
-First did you installed "wine"? 
-Is starcaft installed on your hard-drive?

---

### Post by lehvrhon on 2008-09-26
Hello, :)
1) Yes, I have install the wine in my system, but
2) The starcraft I have doesn't need to be installed when I am in windows, I just put it anywhere then play, :)

What I did was to copy-paste the file to c:/wine the when I click starcraft.exe it requires CD,
should it be installed in order to run? :confused: thank you,

---

### Post by medic2000 on 2008-09-26
No you dont need to copy the SC directory. Wine can execute it from anywhere on your hard-drive. 

For no cd,from wine appdb:

WINE has no trouble with Starcraft and Broodwar copy protection. If you've installed it and still get the "Insert Starcraft CD" message, make sure your CD-ROM drive is listed in your config - and that it's marked as a CD-rom drive, not a local hard drive.

1) run wine config (winecfg)

2) Click drives. If yours isn't listed, Add it.

3) Select your cdrom drive, click show advanced, then set type to CD-ROM drive.
4) Hit "OK" to save and exit.

If this changes your the drive letter that it was installed from, you might have to run regedit, and manually update this registry key: "HKEY_LOCAL_MACHINE\Software\Blizzard Entertainment\StarCD" to reflect this.

---

### Post by lehvrhon on 2008-09-26
Thanks medic2000, Ok, I attach a screenshot of my desktop and run the regedit, but I don't find any Blizzard Intertainment folder under it.

```

...Broodwar copy protection.[COLOR="red"] If you've installed it[/COLOR] and still get the "Insert Starcraft CD" message, make su...
```

:( Still no luck,


Edit:
Good News! I have found this link [http://www.ghoztcraft.net]("http://www.ghoztcraft.net/forums/index.php?automodule=downloads&req=idx&cmd=viewdetail&f_id=828") and downloaded the "scloader2b.exe" and put it in the folder, I put it in winecfg and it worked!
thank you medic2000 for the help! :) :) I can play starcraft again!!

---

### Post by medic2000 on 2008-09-26
Oh, pardon me. You didnt install SC with wine so you wont have a registry record there.
Maybe if you add manually it will work.

Anyway you've succeded to work the starcraft. Oh i didnt do anything. You are always welcome to ask and i will try my best to help.

By the way the game runs as fast as on Windows or is it slow?

---

### Post by lehvrhon on 2008-09-26
This is a bit slow than running in windows,, 
I type in ```
wine "scloader2b.exe" -opengl
``` in the terminal, maybe a little of a workaround and it will be working fast, i hope so,, :lolflag: heheh,

Edit:
I have seen an improvement on my game, all I did is to put keys in the regedit, as discribed in the 
[http://www2.udec.cl/]("http://www2.udec.cl/~eliaspizarro/SC/sc.html")

```
# Start your regeedit and go for "HKEY_CURRENT_USER\Software\Wine\". Add the key "Direct3D" and add:

   1. string "DirectDrawRenderer" with value "opengl"
   2. string "RenderTargetLockMode" with value "readtex"
```

and thats it,, it moves smoothly now,, :popcorn:

---

### Post by medic2000 on 2008-09-26
I was going to tell you about that regedit config but you've have already did it :)

"Flee back to your masters Aldaris and huddle with them in darkness. For your actions we all set us unto the Zerg" -Tassadar of the Templar

---

