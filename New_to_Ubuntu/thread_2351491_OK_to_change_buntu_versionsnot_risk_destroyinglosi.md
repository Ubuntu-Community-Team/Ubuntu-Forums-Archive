---
title: "OK to change *buntu versions/not risk destroying/losing anything"
date: 2017-02-03
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2017-02-03
Thanks for reading. 
Question. I currently run Xubuntu 14.0.5

I would like to try a different flavor(?correct term?) of Ubuntu

Specifically 
LUBUNTU 14.04.5

```

i have (always) had each "/dev/ portion it's own partition of my drive. 
EX: With Xubuntu, I have partitions for 


/ (root)
/boot
/home
/usr
/usr/local
/var
/opt
/tmp

you "get it" aka 
/dev/sdb1/    /
/deb/sdb2     /boot              
  


I've had to reinstall Xubuntu DOZENS of times (Different reasons). 
Each time I do..as long as I use the same above-*AND* same Login credentials..

I never lose anything. (other than obvious-programs I installed manually,etc.). 

Everything always looks as I expect it (Icons-Folders-etc on desktop). 



``` 


Can I do the same with Lubuntu and reasonably expect the same behavior (aka I know Icons diff) but you know. Expect to still have all my Data

Thanks in advance for reply.

---

### Post by yetimon_64 on 2017-02-03
With both being 14.04 based have you considered just adding another DE, this time lubuntu, from the terminal. 

You can add either a full lubuntu-desktop with all its packages/applications or just the simpler lxde package (less packaged applications etc, just the desktop session).

The terminal commands for both ...
```
sudo apt-get install lubuntu-desktop
```
**or **
```
sudo apt-get install lxde
```

The first code is the complete packaged lubuntu desktop, the second is just the lxde session package. Both will give you another lxde environment to log into from the greeter screen. When you change sessions at the log in screen, the session will continue to be used for further subsequent boots until you decide to change it back there.

I currently also run 14.04 and have several DEs side by side. I run the xbuntu-desktop, ubuntustudio-desktop (just another xfce desktop/session with ubuntustudio applications set up for use in it) and ubuntu-desktop packaged DEs on this install and can log into either of them at the log in screen. I could very easily add the lubuntu-desktop or the lxde packages to get a lxde desktop as well very easily. 

It would pay to backup your home data regularly and especially before any installation such as a new desktop environment; but adding a new desktop (from the official repositories) should not be too large of a data risk. Installing such a second DE carries a much reduced risk as compared to doing partition alterations for example, still a good data backup is a very good idea.

Cheers, yeti.

---

### Post by ian-weisser on 2017-02-04
Yetimon_64 is right, and I'll amplify his final paragraph (backup your data anytime you make major changes to your system) with just a bit of healthy paranoia: 
You have installed and reinstalled plenty of times...but the next time is when something may go wrong and you lose it all. Backups are so easy and so cheap.

---

### Post by Bucky Ball on 2017-02-04
> **ian-weisser said:**
> Yetimon_64 is right, and I'll add just a bit of healthy paranoia: Backup your data anytime you make major changes to your system.
You have installed and reinstalled plenty of times...but the next time is when something may go wrong and you lose it all. Backups are so easy and so cheap.

+100

---

### Post by Tadaen_Sylvermane on 2017-02-04
For home use that complicated of a partition structure is useless. Best idea for backing up your data is a separate /home or /data partition and keep your personal stuff there. Then you can reinstall to your hearts content.

---

### Post by Impavidus on 2017-02-04
Those partitions look needlessly complicated to me. I run my current system with just root and /home.

Also note that Xubuntu 14.04 and Lubuntu 14.04 will reach end of life in about two months. Why still install one of those?

Other than that, yes, if you do a fresh install of Lubuntu, re-use Xubuntu's /home partition and and don't format it, you'll still have your data.

---

### Post by bearlake on 2017-02-04
The OP is using Xubuntu 14.0.5

Isn't the EOL spring of 2019? ;)

---

### Post by HermanAB on 2017-02-04
You don't need to re-install the whole house of cards.  You can install various DEs with the software manager and choose which one you want to run at login.

---

### Post by Impavidus on 2017-02-04
> **bearlake said:**
> The OP is using Xubuntu 14.0.5

Isn't the EOL spring of 2019? ;)
Not 14.0.5, I assume it's 14.04.5.
LTS releases of Xubuntu and Lubuntu only have 3 years of support, which means that after 3 years support for the packages unique to Xubuntu or Lubuntu is dropped. The parts they have in common with Ubuntu get the full 5 years of support.

---

### Post by bearlake on 2017-02-04
> **Impavidus said:**
> Not 14.0.5, I assume it's 14.04.5.
LTS releases of Xubuntu and Lubuntu only have 3 years of support, which means that after 3 years support for the packages unique to Xubuntu or Lubuntu is dropped. The parts they have in common with Ubuntu get the full 5 years of support.

Thanks

---

### Post by whereismymindat2 on 2017-03-03
You for help!!

---

