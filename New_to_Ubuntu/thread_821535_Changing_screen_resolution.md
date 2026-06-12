---
title: "Changing screen resolution"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Tek-Noir on 2008-06-07
How is it you change the screen res in xorg.conf. Ive reinstalled hardy and having problems. Used to be able to get 1024*768 but will only let me do 800*600 now

---

### Post by superprash2003 on 2008-06-07
ok.. this is strange as i faced the similar problem today when i rebooted.. i then checked the resolution settings again under system->preferences and it didnt allow me to choose 1024*768.. then i switched off the pc and just removed and inserted back my graphics card and it solved the problem.. i had to reboot twice though.. i know its strange but this worked for me

---

### Post by N.N. on 2008-06-07
Please post the contents of your xorg.conf file. The problem might be caused by the refresh rate of your monitor being specified in a too conservative way in this file. If that is the case, a possible fix can be found on the community wiki: [https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541).

---

### Post by Tek-Noir on 2008-06-07
Cheers, actually im gonna just re install, i think its something to do with my install.

---

### Post by N.N. on 2008-06-07
> **Tek-Noir said:**
> Cheers, actually im gonna just re install, i think its something to do with my install.

That shouldn't be necessary, but, naturally, you're free to do so if you please. However, learning how to troubleshoot and correct problems such as the one you're currently facing will help you take control of your installation instead of letting the installation control you.

---

