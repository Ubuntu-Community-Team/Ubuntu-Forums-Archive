---
title: "HP Printer Ink Levels. HP Device Manager"
date: 2005-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by PeteJ on 2005-05-06
Hi all,

I just completed installing the HP Device Manager on Hoary 5.04 for my hp deskjet 5550 using 
[http://hpinkjet.sourceforge.net/install.php](http://hpinkjet.sourceforge.net/install.php)

It took a little while, but it was fairly straightforward, with excellent detailed instructions. 

Notes:

In Step 1: Set up the Linux environment, I put sudo in front of EVERY command line they provided.  I think that helped, but I'm not sure.

For unknown reasons, the apt-get command line didn't work for me, so I used System, Administration, Synaptic to install the many packages.  

In Step 2: Download and install the HP printing software, the link in sub-step 1 sends you to a busy page.  Click on 

"download source code"  

That takes you to another busy page.  Scroll WAY down to near the bottom, look for "hplip", and then click

hplip-0.9.2.tar.gz

to download it.  (I think you can ignore the hpijs stuff because hplip contains it all, but I'm not sure.)

During Step 2 (I forget which sub-step; either after configure or make, I think), I had to use Synaptic to additionally install  

libjpeg62-dev

because the hplip compile exited with an error saying jpeg support was not available.

In Step 2, sub-step 11,  

/etc/init.d/cups restart 

should be  

sudo /etc/init.d/cupsys restart

In Step 3, USB, sub-step 4, 

killall -HUP cupsd

didn't work for me.  I used 

sudo /etc/init.d/cupsys restart

instead (I probably shoulda used "sudo killall -HUP cupsd" and didn't).

In Step 3, they show using the web interface (webmin?) to setup the printer, but I was too lazy to setup a real root user, which I think you have to do to use that feature, so I just used the System, Administration, Printing menu instead.

In Step 3, USB, sub-step 10, I selected

HP deskjet_5550

(note the underscore) which was automatically detected and there waiting for me.  

In Step 3, USB, sub-step 14, I couldn't find any menu item for the HP Device Manager, and am not smart enough to know how to add it, so I ran 

/usr/share/hplip/toolbox

(OK, I didn't use sudo on that one either, but it worked fine.)

In the HP Device Manager, I think I had to add

lp

under Settings, Configure, Function Commands, Print Command.

In the HP Device Manager, "print test page" is on the Information tab (far right tab, after Maintenance and Panel).

I hope that helps.  Good luck!

Pete

---

### Post by sissou on 2005-05-09
Thanks for your post.
I would not have been able to install hplip by myself...

One question yet : does the "Ink cartridges and toner cartridges supply levels" display anything on your "machine" ?

---

