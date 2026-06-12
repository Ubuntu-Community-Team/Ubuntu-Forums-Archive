---
title: "[SOLVED] video problem with new install"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by GordHatt on 2008-05-09
Hi All

I just installed 8.04 server then on advice from here i reinstalled 8.04 desktop which to which i am going to add server software as required.

that was no problem i now have desktop installed and it appears to run ok....except the desktop video is all wrong the is gray section added into the video and that splits it a puts the two parts out of sync so that it is hard to figure out what anything is. SO i have a driver problem i am assuming and the box is using built in video, i have a driver cd that came with the box but when i try to install the drivers i can not read what is on the screen so i have no idea how/what/where to input what i want to do

could there be some confusion between the two different versions of ubuntu 8.04, should i wipe the hard drives (its a raid 1 setup) and start with fresh clean ones?

thanks for your help and tolerance with my newness

Gord

---

### Post by Vadi on 2008-05-09
What video card are you using?

---

### Post by GordHatt on 2008-05-12
i am using the onboard video chip on a ASUS P5VD2-VM SE motherboard 

more i have found

when using a 17" LCD monitor the picture is scrambled as described in the previous email but when i connect it to a 19" wide monitor the picture has slashing of white lines cutting through on an ~30 degree angle. i can read the screen at least like this, and maybe install a new video driver... as son as i figure out how,

i too a screen shot of the desktop for show and tell, but when i looked at the screen shot it looked correct??!!

thanks for asking
Gord

---

### Post by GordHatt on 2008-05-12
it continues, i tried to install the linux vga driver that came with the computer, when i did i was unable to install. when i simply tried to run the program from the terminal window and just a normal run it was unable to. both of these selected from a double click in the browser window. 

the program doesn't seem to have access to forder ./utility/gtkthemes   and alot of other folders, it gives a permission denied.

could this have something to do with the onboard RAID1 controller i have configured. SHould i remove the raid1 config, reinstall the OS and when it is working then get raid1 working.

thans again
Gord

---

### Post by GordHatt on 2008-05-12
and then i found this explaining why and how to fix my problem but.....being such a newbie i don't know what they are talking about, trunks and branches and experimental stuff??

[http://thread.gmane.org/gmane.linux.drivers.openchrome.user/266](http://thread.gmane.org/gmane.linux.drivers.openchrome.user/266)

want to give this a try but i don't know how

Thanks
Gord

---

### Post by Vadi on 2008-05-12
Well, wait up, the guy there just has the same problem as you

---

### Post by Vadi on 2008-05-12
Alright, so they did fix it.

Go to Applications - Accessories - Terminal, then copy and paste this command in:

```
mkdir ~/Programs && cd ~/Programs && svn co http://svn.openchrome.org/svn/trunk
```

You'll need to right-click and paste or ctrl+shift+v, because plain ctrl+v doesn't work.

Then paste these commands in, one by one:

```

cd trunk
./autogen.sh --prefix=/usr
make
sudo make install
```

After you're done try logging out and logging back in (or reboot), is it better?

---

### Post by GordHatt on 2008-05-12
yes and the guy named xavier has a fix and tells how to fix it but i don't understand what he is saying
here is what he said

 From the svn revision in the log.
(!!) (development build, at svn revision 483)
483 is the last changeset of the experimental branch.

To check out and build trunk, just use :
svn co [http://svn.openchrome.org/svn/trunk](http://svn.openchrome.org/svn/trunk)
cd trunk
./autogen.sh --prefix=/usr
make
sudo make install

---

### Post by Vadi on 2008-05-12
See my instructions above

---

### Post by GordHatt on 2008-05-12
when i input ./autogen.sh --prefix=/usr
 i get
 ./autogen.sh 9:autoreconf:not found
returned


thanks for your help
Gord

---

### Post by Vadi on 2008-05-12
Try doing this:

[quote]sudo apt-get install libchromexvmcpro1 libchromexvmc1 xserver-xorg-video-openchrome[/code]

What do you get?

Also, are you on Ubuntu 8.04?

---

### Post by GordHatt on 2008-05-12
yes i am using Ubuntu 8.04 on a new clean computer

here is what was returned

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libchromexvmcpro1 is already the newest version.
libchromexvmc1 is already the newest version.
xserver-xorg-video-openchrome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

i tried to carry on with the make command but that was unsuccessful

---

### Post by GordHatt on 2008-05-13
bump

---

### Post by etitor on 2008-07-05
> **GordHatt said:**
> bump

I have just solved this same problem on a friend's PC (double boot Windows XP and Ubuntu 8.04). Maybe this solution can help you.

My friend's PC has a 19-inch LCD display with a native resolution of 1440x900. After finishing Ubuntu 8.04 installation from the i386 alternate CD, the screen appeared crossed by diagonal white lines, separated by approximately 5 centimeters (2 inches). Worse still, those lines were cutting the screen in unsincronized slices that made it very difficult to follow mouse movement.

As we couldn't get an Internet connection, I prepared for my friend a DVD Ubuntu (instead of the CD I had used to carry out the first install).

In the process of trying to use the DVD as a repository (in order to solve the lack of Internet connection) I inadvertedly left the DVD in the drive and rebooted the PC.

The live DVD Ubuntu that launched from the disc came with the proper screen resolution OK and no diagonal lines.

So I simply reinstalled the whole thing using the DVD on top of the previous installation I had made from a CD (I had to wipe the previous installation out).

¡Todo perfecto, mi amigo!

No fiddling with drivers or recompiling. Just try to install from the live DVD Ubuntu.

I hope you have the same success I had.

---

