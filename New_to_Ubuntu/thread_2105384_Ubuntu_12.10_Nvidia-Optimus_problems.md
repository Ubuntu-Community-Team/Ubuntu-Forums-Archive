---
title: "Ubuntu 12.10 Nvidia-Optimus problems"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by LouisPM on 2013-01-15
I'm new to these forums and pretty new to Ubuntu, but I've  been trying to learn and I just installed Ubuntu 12.10 on my XPS17 as a  dual-boot with windows 7. I had some problems during installation but I  managed to tentatively fix them and ubuntu was working fine on first  boot-up but when I installed bumblebee with these instructions: [http://www.howtogeek.com/124685/how-to-make-nvidias-optimus-work-on-linux/](http://www.howtogeek.com/124685/how-to-make-nvidias-optimus-work-on-linux/) 
And restarting my computer after that, none of the menu's and the dock thing would  load, I could see my desktop items but when I tried to open one of my  folders, it would load fine, but their would be no outline to the  window.
  I really dont know what else to say, I've never used Ubuntu before so  I may have made some huge nooby mistake, it might not even be related to Nvidia optimus it's just that's the only connection I've found. If anyone is willing to  help, I'm willing to do what I need to to fix this. c:
  My video card is a Nvidia Geforce 555m, if that's of any use.

---

### Post by androssofer on 2013-01-16
> **LouisPM said:**
> I'm new to these forums and pretty new to Ubuntu, but I've  been trying to learn and I just installed Ubuntu 12.10 on my XPS17 as a  dual-boot with windows 7. I had some problems during installation but I  managed to tentatively fix them and ubuntu was working fine on first  boot-up but when I installed bumblebee with these instructions: [http://www.howtogeek.com/124685/how-to-make-nvidias-optimus-work-on-linux/](http://www.howtogeek.com/124685/how-to-make-nvidias-optimus-work-on-linux/) 
And restarting my computer after that, none of the menu's and the dock thing would  load, I could see my desktop items but when I tried to open one of my  folders, it would load fine, but their would be no outline to the  window.
  I really dont know what else to say, I've never used Ubuntu before so  I may have made some huge nooby mistake, it might not even be related to Nvidia optimus it's just that's the only connection I've found. If anyone is willing to  help, I'm willing to do what I need to to fix this. c:
  My video card is a Nvidia Geforce 555m, if that's of any use.

I had a similar issue on mine.. bumblebee worked under 12.04, but not 12.10.. no idea why.. but my built in graphics wored well enough under 12.10 to play minecraft.. so I didn't mind.. 

 never got it fixed.. although I did manage to get my desktop back...

load up your ubuntu.

then press

```
ctrl    alt   T
```

this will open a terminal for you. From there we can open anything.. first option would be to uninstall bumblebee:

```
sudo apt-get install ppa-purge

sudo ppa-purge ppa:bumblebee/stable
```

then restart.. if it still broke after that let me know

---

