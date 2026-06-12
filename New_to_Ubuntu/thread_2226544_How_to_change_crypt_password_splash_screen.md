---
title: "How to change crypt password splash screen"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by sam-hort on 2014-05-27
*Hello, I'm newly back to Linux and Ubuntu after a few years and really just getting back to grips with the basics, so don't flap if I've missed something obvious. Also new to the forum so: ):P hello all and thanks in advance for your responses. Hope I will be able learn enough here to help solve someone elses problems one day. Anyway, onto my problem.*

--

 I run Ubuntu 14.04 LTS 64-bit with both a full disk encryption (requiring password on boot) and an encrypted /home folder. I breifly installed Edubuntu Desktop, quickly realised I didn't need it, and removed it through the Software Centre. After uninstalling, my splash screens and branding remained as Edubuntu rather than reverting to the default Ubuntu splash. It's only a minor issue but it is irritating me, and I wonder if there are further changes Edubuntu may have made which have not been removed, suggesting a botched uninstall?

I tried using basic commands such as:
```
sudo apt-get remove edubuntu-desktop
sudo apt-get install ubuntu-desktop
```
...as well as:
```
sudo aptitude remove edubuntu-desktop
sudo aptitude update&&sudo aptitude install ubuntu-desktop
``` 
...but these did not change anything. I also tried to locate the folder where splash screens are supposed to be stored (can't remember the directory right now) but it did not exist (though I may have been looking at the directory for a previous Ubuntu release). I have now managed to change the shutdown splash screen using Plymouth-themes, but the crypt password splash screen (for want of a better name for it) which shows as I boot remains as the Edubuntu splash (it was previously the default Ubuntu splash before I installed Edubuntu Desktop). I've also noticed I still get an 'Edubuntu 14.04 LTS' branding in the lower left of the screen as I log into each session. 

I was wondering if anyone knew how I could change these back, either to the original Ubuntu ones or to something new? Also, if Edubuntu did uninstall incorectly, is there any way I can make sure I have fixed it all, or is it a case of solving each issue as it arises?

Thanks in advance,
Sam

--

Update: Solved

I finally managed to fix this so simply it's embarrasing but I will share it in case someone can make sure of it. All I did was log into the GNOME desktop environment (by clicking the Ubutuntu logo at the top right of the login prompt), then logged out and changed it back to Ubuntu default. On next reeboot the splash screens had reverted. 

Cheers anyway!

---

