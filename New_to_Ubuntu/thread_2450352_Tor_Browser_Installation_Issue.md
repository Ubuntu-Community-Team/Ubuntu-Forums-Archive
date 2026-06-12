---
title: "Tor Browser Installation Issue"
date: 2020-09-11
forum: New to Ubuntu
---

### Post by desertwalker1 on 2020-09-11
Hey all, hello again! A new issue as expected. :razz:

I installed Tor browser. I first tried installing it through the  terminal. However, when I clicked on 'Install Tor Browser' through the  Tor Browser Launcher, it got stuck on 'Verifying Signatures'. I then  downloaded it directly from the website and 'Extract Here' etc. I  followed a Youtube video: [https://www.youtube.com/watch?v=SvNV7jkV5ls ]("https://www.youtube.com/channel/UC5weW8V_Z_bjEax-ANpnpkg")(I hope posting links is ok? Please let me know if it's not)

Anyway, the second method has worked. However, now there are two Tor  Browser icons in the application list. One works just fine. The other  brings up the same installation box. A popup shows up saying Ubuntu  experienced an error and the installation is once again stuck at  Verifying Signatures. How do I get rid of this defective Tor Icon? 

Thanks in advance!

---

### Post by bustamanteguevara on 2020-09-11
Maybe you can try to uninstall the defective installation.

---

### Post by T6&amp;sfpER35% on 2020-09-12
the defective one was installed through terminal right?
so just remove/purge  it through terminal again?

---

### Post by monkeybrain20122 on 2020-09-12
Tor browser doesn't need installation, just download the bundle, extract and click the binary, that's it.

To remove the defective one, where is it installed? You can probably just delete the folder.

---

### Post by desertwalker1 on 2020-09-12
The defective one was installed through the terminal, yes. I would be happy to uninstall it through the terminal as suggested, however I am unaware of the commands. -.- 

Just to clarify again; Tor IS working for me now guys, I was able to get it working by downloading directly from the website. So essentially I now have 2 Tor icons in the applications list. Just trying to figure out how to get rid of the defective one. 

Really appreciate your responses so far! Thanks again.

---

### Post by CelticWarrior on 2020-09-12
What commands have you used to install? "[COLOR=#000000] installed through the terminal" is meaningless, you can do all sorts of things. How it was installed determines how it can be uninstalled.[/COLOR]

---

### Post by desertwalker1 on 2020-09-13
> **CelticWarrior said:**
> What commands have you used to install? "[COLOR=#000000] installed through the terminal" is meaningless, you can do all sorts of things. How it was installed determines how it can be uninstalled.[/COLOR]

My apologies. I checked the commands history and this is the command I used:

sudo apt install torbrowser-launcher

Went to applications and launched the Tor Browser Launcher. The installation began but got stuck on Verifying Signatures. I then went the other route to install it. I hope this brings more clarity.

---

### Post by T6&amp;sfpER35% on 2020-09-13
> [COLOR=#000000]sudo apt install torbrowser-launcher[/COLOR]
 to remove then
```
sudo apt remove torbrowser-launcher
```

---

### Post by desertwalker1 on 2020-09-13
> **3nd said:**
> to remove then
```
sudo apt remove torbrowser-launcher
```

That did it. Thank you! :)

---

### Post by Butthead on 2020-09-13
Would "purge" (as in sudo apt purge torbrowser-launcher) be a better option if you wanted to start reinstalling it from scratch though? :confused:

---

### Post by T6&amp;sfpER35% on 2020-09-14
[https://www.linuxforfreshers.com/2018/02/what-is-difference-between-apt-get.html](https://www.linuxforfreshers.com/2018/02/what-is-difference-between-apt-get.html)

---

