---
title: "changed from crt to lcd -&gt; low resolution?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by ELD on 2008-05-06
Hi all recently changed from those old and big crt monitors to my dads old lcd just to upgrade a little.

Ubuntu still picks it up as a crt and max resolution it gives me is 640x480 which is impossible to work with, and when booting up and ubuntu is loading it keeps setting refresh far beyond what my monitor supports??

---

### Post by NightwishFan on 2008-05-06
Perhaps reconfigure the xserver:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer as best you can, and what you do not know leave default.

---

### Post by ELD on 2008-05-06
> **NightwishFan said:**
> Perhaps reconfigure the xserver:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer as best you can, and what you do not know leave default.

All that seemed to do was ask stuff about my keyboard? :S

---

### Post by philinux on 2008-05-06
you must be on Hardy then as recon xorg only offers keyboard and mouse settings. It's supposed to auto detect the monitor. 

System>Prefs>Screen Res detect display is supposed to be the new way.

As far as boot up goes, you can use startupmanager to configure the login in screen res.

---

### Post by ELD on 2008-05-06
> **philinux said:**
> you must be on Hardy then as recon xorg only offers keyboard and mouse settings. It's supposed to auto detect the monitor. 

System>Prefs>Screen Res detect display is supposed to be the new way.

As far as boot up goes, you can use startupmanager to configure the login in screen res.


Detect Display changes nothing at all.
Using that xorg thing did jack as well.

Tried startup manager that seemd to be the only program capable at setting my screen resolution higher.....but it didn't even work! :(

---

### Post by ELD on 2008-05-07
BUMP surly someone knows how i can get 1024x768??

---

### Post by maramot on 2008-05-07
I have a similiar problem only with this little twist - when I enable my proprietary NVIDIA driver the only resolutions I get to choose from are 800x600 and 640x480. If I disable the driver, I get all resolutions my display supports but no hardware acceleration :)

I upgraded from Ubuntu 7.10 on my Dell Inspiron 1520. The display is maximum 1650x1050, the videocard is NVIDIA GeForce Go 8600GT.

---

### Post by ELD on 2008-05-09
> **maramot said:**
> I have a similiar problem only with this little twist - when I enable my proprietary NVIDIA driver the only resolutions I get to choose from are 800x600 and 640x480. If I disable the driver, I get all resolutions my display supports but no hardware acceleration :)

I upgraded from Ubuntu 7.10 on my Dell Inspiron 1520. The display is maximum 1680x1050, the videocard is NVIDIA GeForce Go 8600GS.

I get that too, if i enable the driver i get bugger all res, if i disable i also get access to more resolutions, this is fracking annoying!!

---

### Post by maramot on 2008-05-09
It's kind of relieving to know I'm not alone with this problem. :) So, are there any solutions besides waiting for a new nvidia-glx-new package to be released? I've tried some of the offered solutions for that but nothing works. And I'm not surprised of this, since I know that the problem is with this exact package, not anywhere else. And the solutions are usually about altering your xorg.conf file. If you find anything please pm me or post it here :)

---

### Post by maramot on 2008-05-09
Funny, I just found a solution for my case. Go read it quick and see if it works for you: [http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4922126&postcount=19](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4922126&postcount=19)

---

### Post by ELD on 2008-05-10
Didn't change a thing since my ubuntu is a fresh install and so had everything correct :(

I can't beleive theres no easy way to force a resolution grr

---

### Post by N.N. on 2008-05-10
A possible solution could be to specify the horizontal and vertical sync frequencies of your monitor manually in your /etc/X11/xorg.conf file. The following wiki entry explains how you do this: [https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541)

---

### Post by ELD on 2008-05-11
> **N.N. said:**
> A possible solution could be to specify the horizontal and vertical sync frequencies of your monitor manually in your /etc/X11/xorg.conf file. The following wiki entry explains how you do this: [https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541)

I don't particurly want to mess around with editing files where i can bugger up my install. I would rather there be some GUI way to force a screen resolution, would solve a lot of peoples problems!

---

### Post by N.N. on 2008-05-11
> **ELD said:**
> I don't particurly want to mess around with editing files where i can bugger up my install. I would rather there be some GUI way to force a screen resolution, would solve a lot of peoples problems!
Don't worry. It might seem intimidating at first, but if you backup the file, you can always just revert to it if things go wrong:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
You can then proceed to edit the file, knowing that you can just revert to the backup if an error is made. Type the following command in the terminal to start editing the file:
```
sudo gedit /etc/X11/xorg.conf
```
Scroll down to the "Monitor" section which looks somewhat as follows:
```
Section "Monitor"
     Identifier         "FLATRON 995F"
     Option             "DPMS"
     HorizSync          30-96
     VertRefresh        50-160
EndSection

```
Now simply edit the intervals that are specified for HorizSync and VertRefresh so that they match the values of your new monitor (you can find the right values in the manual that came with the monitor, on the box that it came in, or by doing a google search). Once you've done that, press CTRL+ALT+BACKSPACE to restart xserver. However, you might want to read the following before you do that:

IF things go wrong, xserver will prompt you with an error message once restarted, and you will eventually end up in a command line system (you might have to say "No" when xserver asks whether it should attempt to correct the problem) where you will be prompted for login details. To restore your system to the way it was previously, simply login as you would with the graphical interface and type the following command:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Then just reboot, and things should be back to normal:
```
sudo reboot
```
I believe this is the quickest way you can solve your problem.

---

### Post by ELD on 2008-05-13
Only problem is i have no way to find the HorizSync and VertRefresh of my monitor, it's a few years old now, was picked up at tescos so it's a real low end cheap one.

Says "iQon" on the front, product number is "LP717", only found 3 pages on google all in a foreign language :(

---

### Post by Abetorius on 2008-05-13
Quick and painless (usually)way of solving many problems with graphic drivers is installing EnvyNG from repo and running it with automatic detection setting.

---

### Post by ELD on 2008-05-13
All that EnvyNG does is install the right driver though, to which i have.

---

### Post by ubuntu-freak on 2008-05-13
Press Alt F2, type "gksudo displayconfig-gtk" and your password when prompted, then select your resolution.
 
Nathan

---

### Post by sailor2001 on 2008-05-13
if you go to /usr/share/applications/screens & graphics  maybe you can find your monitor there and get your resolution from that.  never heard of that monitor though.

---

### Post by N.N. on 2008-05-13
> **ELD said:**
> Only problem is i have no way to find the HorizSync and VertRefresh of my monitor, it's a few years old now, was picked up at tescos so it's a real low end cheap one.

Says "iQon" on the front, product number is "LP717", only found 3 pages on google all in a foreign language :(

Haven't been able to find the specifications of the monitor myself either. If you want to try to proceed with the fix, however, you might be able to acquire the correct specifications by means of the [FONT="Courier New"]read-edid[/FONT] package, which is a "hardware information-gathering tool for VESA PnP monitors".

First install [FONT="Courier New"]read-edid[/FONT] (it's in the universe repository): ```
sudo apt-get install read-edid
```

Then run the following command to use [FONT="Courier New"]read-edid[/FONT] to query your monitor for EDID data: ```
sudo get-edid | parse-edid
```

If EDID fails, you will not get the specifications of your monitor, and the tool will give you a message along the lines of: "The EDID data should not be trusted as the VBE call failed". Usually EDID reads only fail if (a) the queried monitor is ancient (i.e. from the days before EDID), or (b) you're using a video extension cable or some other piece of equipment that lacks the EDID wire to connect the monitor to the video card. There are, however, also a number of unexplained EDID fails beyond these (see *[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760)*).

I hope that it works for you. But if it doesn't, a last resort might be to manually increase [FONT="Courier New"]HorizSync[/FONT] and [FONT="Courier New"]VertRefresh[/FONT] a bit (I don't know if that's really safe though).

---

### Post by ELD on 2008-05-13
> **reassuringlyoffensive said:**
> Press Alt F2, type "gksudo displayconfig-gtk" and your password when prompted, then select your resolution.
 
Nathan

That didn;t work since i can't normally select the right resolution, but in that config i was able to manually change my monitor to generic lcd and hazza i can choose a resolution there wooo :D

---

### Post by ubuntu-freak on 2008-05-13
> **ELD said:**
> That didn;t work since i can't normally select the right resolution, but in that config i was able to manually change my monitor to generic lcd and hazza i can choose a resolution there wooo :D

 
So it DID work? :-)
 
I just didn't say to select a different monitor.
 
Nathan

---

### Post by ELD on 2008-05-14
> **reassuringlyoffensive said:**
> So it DID work? :-)
 
I just didn't say to select a different monitor.
 
Nathan


shhhhhhhh lol, yeah i suggest for anyone having problems change your monitor to generic

---

