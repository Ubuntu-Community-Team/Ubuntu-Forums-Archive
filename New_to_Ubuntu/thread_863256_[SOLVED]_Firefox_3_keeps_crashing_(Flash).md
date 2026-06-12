---
title: "[SOLVED] Firefox 3 keeps crashing (Flash)"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-07-18
Recently, I have been having problems with flash and Firefox 3. I fixed the no sound issue by installing "libflashsupport". Now Firefox keeps crashing on pages that contain flash (especially Youtube).Either the process becomes unresponsive and I have to force quit or the process just exits.This usually happens when the page is being loaded. Can anybody help me? Thanks in advance. :)

---

### Post by tuxxy on 2008-07-18
There could a conflict of some sort? have you tried reinstalling the plugins/firefox?

---

### Post by Promaster91 on 2008-07-18
I tried to reinstall flash by this command. I don't know if it is right or not.
```

sudo rm /home/stefan/.mozilla/plugins/libflashplayer.so

```

---

### Post by gandaran on 2008-07-18
> sudo rm /home/stefan/.mozilla/plugins/libflashplayer.so

this command just removes the flash from your hidden home .mozilla/plugins folder. if it's installed there.
libflashsupport is what's crashing firefox, try adobe flash 10 beta, flash 10 fixes the sound issue, no need to have libflashsupport installed.
remove flash 9, if you installed it using synaptic, use synaptic to remove it.
if you installed the adobe tarball, find where it's installed and just delete the libflashplayer.so file.
to install flash 10 download [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html") and just extract the package. drag the libflashplayer.so file to home/.mozilla/plugins folder (no plugins folder there! just make one.)

---

### Post by SunnyRabbiera on 2008-07-18
flash can be problematic, what version of firefox 3 are you using?

---

### Post by Promaster91 on 2008-07-19
Ok. I will try the beta flash.

---

### Post by Promaster91 on 2008-07-22
The beta flash help a little, but it still crashes. I am using Firefox 3.0.

---

### Post by gandaran on 2008-07-22
> **Promaster91 said:**
> The beta flash help a little biut but it still crashes. I am using Firefox 3.0.

yes, a web-page with heavy flash content will crash firefox, but I think it's a firefox 3 final problem (I didn't have any crash problems with firefox 3 rc 5), not the flash 10 beta 2, (flash 10 beta 1 was in-fact much better) it also crashes with flash 9.
I'm also using opera, and it doesn't crash on any site that firefox does.

did you remove libflashsupport?

---

### Post by sotiriss on 2008-07-22
The solution for me is : 
flash 9 + libflashsupport + nspluginwrapper installed.
This works fine for me. No crashing on pages contain flash and no problem with sound. I had flash 10 beta installed but i had some problems so go back to flash 9.

---

### Post by Promaster91 on 2008-07-22
Yea, i got rid of libflashsupport and it continues to crash. I also removed adblock because i heard that can cause it to crash too but the same result. So, I might have to delete .mozilla folder and start over again.

---

### Post by schnauzer93 on 2008-07-22
[https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/192888)

---

### Post by stmiller on 2008-07-22
This is a common problem of Flash and Linux. The 10 beta crashes less. :)

---

### Post by Promaster91 on 2008-07-24
Yea the beta does crash less. Oh well guess I will just have to deal with.

---

### Post by Promaster91 on 2008-11-08
Update: Flash 10 is much better. It never crashes for me. Note: Don't use libflashsupport. It makes flash crash alot.

---

