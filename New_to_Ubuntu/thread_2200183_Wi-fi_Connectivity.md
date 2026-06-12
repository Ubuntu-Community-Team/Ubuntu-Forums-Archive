---
title: "Wi-fi Connectivity"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by doug3 on 2014-01-17
Hi, I'm a total newbie when it comes to Ubuntu (and really Linux also). I installed Ubuntu 13.04x64 on my Sony Vaio after Windows 7 failed for me. One thing I've noticed is that where Windows kept me connected to my WiFi network, Ubuntu seems to disconnect me and I subsequently have to reset my router to reconnect. Any ideas maybe about settings I could change or something?

---

### Post by mörgæs on 2014-01-18
Before we go deeper into the troubleshooting please consider a fresh install of 13.10 using wired internet access. 
13.04 is out of support at the end of january.

---

### Post by Bucky Ball on 2014-01-18
> **mörgæs said:**
> Before we go deeper into the troubleshooting please consider a fresh install of 13.10 using wired internet access. 
13.04 is out of support at the end of january.

^^^
This.

Or 12.04 LTS. Both are directly upgradeable to 14.04 LTS when it comes out in April, which has five years support.

---

### Post by doug3 on 2014-01-19
I think I have solved the problem by editing some router settings.

---

### Post by Sef on 2014-01-19
> [COLOR=#000000][/COLOR][[COLOR=#000000]doug3[/COLOR]]("http://ubuntuforums.org/member.php?u=1898711")[COLOR=#000000] 
[/COLOR][COLOR=#000000][INDENT]I think I have solved the problem by editing some router settings.[/INDENT]


[/COLOR]


Please share what you edited, so others may benefit for your eperience.

---

### Post by Bucky Ball on 2014-01-20
> **Sef said:**
> Please share what you edited, so others may benefit for your eperience.

+1. Forum etiquette. ;)

---

### Post by doug3 on 2014-02-26
I apologize for being so late to this. All I did was simply change the security on the router. I changed it from WPA-PSK [TKIP] to WPA2-PSK [AES]. I can't remember why I did this, but I think I read something about Ubuntu working best with the latter security.

---

