---
title: "Dell Inspiron 1545, Serious Internet Issues"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by john_tabor2 on 2014-01-20
Here's the entire background of this computer.

I recently found an old laptop (Dell Inspiron 1545, no known modifications) with Vista thrown on it, so obviously I decide to replace the nasty heresy and decide it would be a nice time to give Linux a shot.

I found Ubuntu, and after many youtube videos, figured out how to install 12.04 LTS on said Lappy. I tried the live version first, and noticed there was no way to connect to the internet, either via cable or wireless. I decided to go ahead and install anyways since it would be easier to modify the setup with a traditional installation instead of a temporary "Live" version.

Installation completed smoothly and I was left with practically the same exact thing as before, except permanent. The nifty OS realized there weren't a connect to the webs, so it asked me to check something like "additional drivers" it's gone now and I can't remember quite exactly what it said. Needless to say, nifty OS didn't fix it on its own. I've been searching various forums and boards and stack-exchange to no avail, and I'm almost positive that my wireless network card simply isn't compatible with Ubuntu 12.04 LTS.

I've gone through some b43firmware installation... here: [http://ubuntuforums.org/showthread.php?t=871906](http://ubuntuforums.org/showthread.php?t=871906)Still after rebooting it has yet to make any improvements.This is currently the closest solution I've found, but didn't work:  [http://askubuntu.com/questions/331513/internet-wont-work-wired-or-wifi-ubuntu-12-04](http://askubuntu.com/questions/331513/internet-wont-work-wired-or-wifi-ubuntu-12-04)TL;DR - Dell Inspiron 1545 Laptop with Dell wireless card. Ubuntu doesn't recognize my wireless card and either I can't find the right driver, or I'm installing them incorrect. Most likely User ErR0r.  I have a tendancy...

---

### Post by john_tabor2 on 2014-01-20
I apologize for the lack of organization on that post, I can't seem to edit it, and it's ignoring the formatting I gave it while I was typing it originally.

---

### Post by Zhivargo on 2014-01-20
```

Sudo lspci
Sudo ifconfig -a
Sudo iwconfig 

```
Post results for all

---

### Post by mastablasta on 2014-01-21
otherwise additional drivers are now "hidden" in software sources in software center.

strange that it wont' connect by wire. usualyl that is hwo one would install the drivers. are you sure your modem/router is setup good (to allow access from this mashicne, DHCP settings etc...)

---

### Post by SeijiSensei on 2014-01-21
Having just installed Kubuntu 12.04 on a similar vintage Inspiron with a Broadcom adapter, I found [this method]("http://ubuntuforums.org/showthread.php?t=1997880&p=12001985&viewfull=1#post12001985") worked successfully.  You need to see if the identifier for the wireless adapter returned by the "lspci" command begins with "14e4:4311".  If so, the method chili555 describes in that posting will probably work for you.  If not, you'll need to do some more searching.

---

### Post by whitesmith on 2014-01-21
> **Zhivargo said:**
> ```

Sudo lspci
Sudo ifconfig -a
Sudo iwconfig 

```
Post results for allNot to be picky, but sudo isn't needed here. If used, it should not be capitalized.

---

