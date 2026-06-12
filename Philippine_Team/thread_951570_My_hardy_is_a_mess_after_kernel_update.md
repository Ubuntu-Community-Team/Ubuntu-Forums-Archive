---
title: "My hardy is a mess after kernel update"
date: 2008-10-18
forum: Philippine Team
---

### Post by Kulaspiro on 2008-10-18
fellow Pinoy ubuntu users, I badly need help.. after an update from 
linux 2.6.24-19 to -21, nasira na firefox and anything na related sa internet. event main menu bar wont work.. i run firefox using alt-f2..di ko na rin ma i shut down ng matino ang laptop.

i normally boot using -rt (ubuntu studio)..im using 
hp laptop
1g ram
amd sempron 1.7ghz dual boot with win xp


thanks in advance guys.

---

### Post by pendletone on 2008-10-18
try mo mag-boot sa mas mababang kernel just to verify that it is indeed because of the kernel update.

---

### Post by Kulaspiro on 2008-10-18
thanks for your help...i already tried to go back to my previous kernel before the upgrade.. ganun pa rin...kala ko nga everything will go back to normal pag nag boot ako sa lumang kernel. pero same problem...

---

### Post by wersdaluv on 2008-10-18
Ano exactly ang sira ng Firefox at ibang apps? Hindi man lang nagsstart?

---

### Post by Kulaspiro on 2008-10-18
firefox; no back buttons, all bookmarks are gone, can't open mulriple windows,tapos walang history of previous browsing
yung ibang application naman,transmission torrent client d na nag work, and ang panel, some are not working, when i hit the quit button, top and bottom panels disappear, i have to push the laptop's power  button to shut it down. i tried to install ephipany browser , but it wont launch..i tried editing the application drop down menu and now its not working. preferences main menu does not work. im glad i have thunar so i can go places and i might back up today. ang dami kasi important documents sa linux partition ko. its my primary os, my windows is just for games and for times like this...this is the first time an upgrade ruined my system... may way pa kaya to fix this without reinstalling? d pa ako nag install ulit since feisty.

---

### Post by loell on 2008-10-18
maybe the core libraries are messed up badly.

---

### Post by _duncan_ on 2008-10-19
Baka naman hindi kernel ang problema. Naalala ko, na-update din ang nvidia drivers kasabay ng kernel. May iba pang packages na kasabay pero hindi ko na maalala kung alin. 23 packages lahat ang na-update sa system ko pero ayos naman, walang problema.

Mas maganda kung separate ang /home partition sa root /. Para kung kailangan ng reinstall, hindi wiped out ang data.

---

### Post by ysNoi on 2008-10-19
Share ko lang :

It also happened to me pero ibang case naman yung sa akin, nawala yung Wireless Network ko pero nung mag-boot ako sa lower kernel, okey naman...! What I only did is nag-update ulit, tapos nagboot ako sa kernel 2.6.24-21 bigla lang na okey...! :guitar: 

Idea ko lang baka hindi na complete ang pag-update mo ng kernel linux 2.6.24-19 - 21 bro...

---

### Post by Kulaspiro on 2008-10-19
any idea how to fix the core libraries?... i did try to update from a lower kernel via terminal... still no good result... i might wait for the Ubuntu community to recommend another system update ...if it is still messed up, i don't know what to do, maybe download hardy iso ...just Ubuntu...no more ubuntu studio for me.

---

### Post by loell on 2008-10-19
> **Kulaspiro said:**
> any idea how to fix the core libraries?... i did try to update from a lower kernel via terminal... still no good result... i might wait for the Ubuntu community to recommend another system update ...if it is still messed up, i don't know what to do, maybe download hardy iso ...just Ubuntu...no more ubuntu studio for me.

most probably these are gtk core libraries, i'm not sure if this is fixable,you could try to execute say epiphany in the cli, see the error output, we'll start from there. 

yeah your it may be better to just download vanilla ubuntu(hardy).

---

