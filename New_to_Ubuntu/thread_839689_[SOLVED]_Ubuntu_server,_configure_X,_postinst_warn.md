---
title: "[SOLVED] Ubuntu server, configure X, postinst warning"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by batfastad on 2008-06-24
Hi everyone
Been messing around with Ubuntu server 8.04 today. All installed ok.
I wanted to install Gnome on the top, and a few other packages as well.
So I did the following:

```
sudo apt-get update
sudo apt-get install xorg
sudo apt-get install gnome-core synaptic
```

Then once all that was done I could just startx and go straight in to Gnome. Then using Synaptic I installed a few other things, Firefox, cd burner, 7zip archiver, some network tools, samba etc.

All seems to be working fine, but I'm still stuck in the world of 800x600 resolution.

So I tried the following to reconfigure X
```
sudo dpkg-reconfigure xserver-xorg
```
Any following through the instructions I get to the point where I specify additional keyboard options (lv3:ralt-switch) then the config program quits with the following message:
```
xserver-xorg postinst warning: overwriting possibly-customised configuration file
```

I didn't get to select any video options or anything, only setting up a few keyboard options.

When I boot into Gnome and go to the 'Screen Resolution' option in Preferences there's only 640x480 and 800x600 listed, and the auto-detect monitor option doesn't work.

Any ideas on why this is messed up?

---

### Post by avtolle on 2008-06-24
Try```
gksudo displayconfig-gtk
```and see if your monitor is listed there. If so, select it and close out (you'll need to do a restart of x for this to take effect).

---

### Post by bodhi.zazen on 2008-06-24
Hard to say from the information you provided.

That "warning" is just telling up you overwrote xorg.conf.

/note to self : Always back up system files before editing them :twisted:

Try :

```
sudo dpkg-reconfigure xserver-xorg
``` 

go with the defaults.

Should be working. If not, boot to recovery mode and try xfix.

back-up the file and re-try editing the keyboard options.

Otherwise, what videocard ?

---

### Post by batfastad on 2008-06-24
I'm using the onboard graphics on a new Tyan server motherboard:
[http://www.tyan.com/product_board_detail.aspx?pid=591](http://www.tyan.com/product_board_detail.aspx?pid=591)

The monitor is a 19" CRT, probably about 5 years old. Don't know the brand, will have to check at work in the morning.
Puppy Linux and Knoppix Live CDs don't seem to have any problems though.

When I run the dpkg-reconfigure xserver-xorg it's strange that it just quits every time after the keyboard options.
After loads of googling that's when I realised there were problems, because there were loads of images of people selecting graphics modes etc.

To restart x, am I right in thinking all I need to do is quit gnome, which drops me back to the command shell? Then startx to go back in?

@avtolle: will try that command first thing back in work tmrw

I followed these walkthroughs...
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

I installed the package xresprobe and ran the following command:
```
sudo ddcprobe | grep monitorrange
``` and there was no output. Just gave me a prompt immediately from that.

I also tried adding a line... Driver "vesa" into the Display section of xorg.conf and that didn't seem to do anything.

My xorg.conf file is only 50-odd lines, and most of that is comment at the top, does that sound right?

Thanks, B

---

### Post by cariboo on 2008-06-24
This may be a little off topic, but wouldn't it be easier to set up Ubuntu Desktop version and then use tasksel to add the LAMP components. In a terminal type:

```
sudo tasksel
```

Once the interface comes up select LAMP and tab to OK and hit enter.

Jim

---

### Post by JoshuaRL on 2008-06-24
@ batfastad

The new version of Xorg that comes with Hardy is different.  It doesn't have a video reconfigure option in dpkg-reconfigure xserver-xorg. The new version of Xorg is set to autoconfigure at login.  So that's why it doesn't have the same options as old examples.  Also, if you compare an xorg.conf from Gutsy to one from Hardy, it is really different too.  The best thing to try is what avtolle said, just you need that package first:
```

sudo apt-get install displayconfig-gtk
gksu displayconfig-gtk

```
That should give you the options you need to change drivers and resolutions.

---

### Post by batfastad on 2008-06-25
Ok that's brilliant. Chose generic VESA compliant graphics driver, and managed to tell it to use 1024x768 as the resolution.
That will work perfectly for our purposes - it will be hooked up to a KVM in the server room eventually anyway and all the other servers all run 1024x768

Thanks for your help!! :)
Ben

---

### Post by JoshuaRL on 2008-06-25
> **batfastad said:**
> Ok that's brilliant. Chose generic VESA compliant graphics driver, and managed to tell it to use 1024x768 as the resolution.
That will work perfectly for our purposes - it will be hooked up to a KVM in the server room eventually anyway and all the other servers all run 1024x768

Thanks for your help!! :)
Ben

Glad to hear it man.  Welcome to Ubuntu!

---

### Post by bodhi.zazen on 2008-06-25
Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by batfastad on 2008-06-25
Ok, marked as solved.
That's a much better idea than manually adding [solved] into the subject

Thanks for the help & info :D

---

