---
title: "Unreadable diagonial screen NVIDIA, U12x, AMD64"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by dsiddens on 2012-09-15
Hello.  I'm not sure which forum to post this into (Installation & Upgrades, Multimedia & Video, Hardware & Laptops) because it seems my problem touches on all three areas, so I'm posting it in Beginners.

The issue is that I have older computer that will run U9.10 but won't show a useable screen when a newer version is loaded. I've tried U10's, U11's and 12's along with Linux Mint (LM) coming from the same U bases.

What I get is a screen that is divided into three strips on the diagonial 

      [http://s19.postimage.org/nsxfwsv0z/NVIDIA_Ub_display.jpg](http://s19.postimage.org/nsxfwsv0z/NVIDIA_Ub_display.jpg)

Notice on the right side, middle panel, the white object.  That is the cursor arrow.

The equipment:  NVIDIA GeForce 6150LE, AMD Athlon 64 X2 (W) 3800+ 2.0 GHz.

I'm thinking that maybe a NVIDIA driver update might fix this.  But how I would achieve this is a mystery to me.

Thank you, for your detailed assistance.

---

### Post by Epodx64 on 2012-09-15
I use to have a very similar chipset "Nvidia Geforce 6150se Nforce 430" and had major problems with it first if you can atleast get to the login screen right click the ubuntu dealy and change it to 2D Unity you should be able to atleast boot in to that it'll probably be ugly and big (mine always was) then add this PPA

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

then 

sudo apt-get update 

don't upgrade yet though go to the Dash menu and search for Jockey and install the "Nvidia Post-Release Current" driver it should be 304.x it's the only driver I was able to get working with Ubuntu/Kubuntu (Linux Mint 13 Cinnamon was pretty much a no go) Kubuntu was much much more difficult because they don't have the 2D option I'm not gonna lie that chipset gave me such a hard time with everything I ended up selling mine but it is possible you just have to get the newer nvidia drivers if you can't even get to the login screen switch to TTY1 (ctrl+alt+f1) add the PPA then 
sudo apt-get update
sudo apt-get install nvidia-current

That should get it running for you.

---

### Post by mips on 2012-09-16
ctrl-alt-f1 should drop you to a console and ctrl-alt-f7 will get you back to the desktop. You can then try installing nvidia 304.43 from xswat ppa.

---

