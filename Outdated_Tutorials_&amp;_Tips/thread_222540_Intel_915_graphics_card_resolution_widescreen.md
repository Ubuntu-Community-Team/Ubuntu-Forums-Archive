---
title: "Intel 915 graphics card resolution widescreen"
date: 2006-07-25
forum: Outdated Tutorials &amp; Tips
---

### Post by kennylog on 2006-07-25
I had some trouble getting the resolution of my graphics card right on my laptop, I found several solutions, but I think this is the best one:

(I didn't write it! sorry but forget where I got it from but I guess the author won't mind)

Graphics
The Intel Extreme 915GM graphics chip is detected by the Ubuntu installer and it correctly writes the /etc/xorg.conf file with modelines for 1280x800 that appear to be appropriate for the built-in panel and no other modelines. Unfortunately the video BIOS fails to report the TFT panel's dimensions as one of the modes available from the card and when X starts however it decides that the most appropriate mode to be in is 1024x768. The resulting video gets mapped onto the TFT and looks wrong because its aspect ratio is incorrect (1280x800 is a widescreen TFT and 1024x768 is a standard screen mode) and the pixels of the mode don't exactly map onto the pixels on the panel. There are also some unfortunate times when bits of windows fall off the screen and can't be accessed.

I was pointed in the direction of a program called 855resolution which rewrites the video BIOS tables of machines with the Intell 855 Centrino chipset and allows the reported modes to be redefined. I was unsure whether 855resolution was suitable for my 915GM card but I located a fork of the project called 915resolution which definitely is. Its website is [here] I chose the "Debian packages can be found here" link and downloaded 915resolution_0.4-1_i386.deb .I opened a root shell and installed the package with dpkg -i

I ran 915resolution from the command line with no arguments and it displayed the available resolutions reported by the BIOS. I selected a resolution I didn't use (I chose the highest as I can't afford a monitor that expensive!) and wrote down the mode numbers in each of the bit depths (in my case 3c, 4d and 5c.) 915resolution must change the mode definitions before X starts if X is to correctly read the modes so I decided to run it at boot time. I opened the file /etc/init.d/bootmisc.sh with an editor and went to the end. The last line of the file read ": exit 0" before that line I added the following lines to change the resolutions of my chosen modes to 1280x800.

 #
 # Modify video BIOS tables to report correct mode for LCD
 #
 /usr/sbin/915resolution 3c 1280 800
 /usr/sbin/915resolution 4d 1280 800
 /usr/sbin/915resolution 5c 1280 800

I saved the file, logged out and rebooted. The graphics immediately came right.

This worked for me, it can be pretty frustrating to have a wrong resolution

---

### Post by joehayhurst on 2006-08-11
Excellent, cheers!

---

### Post by joehill on 2006-08-11
915resolution is actually in the Dapper repositories, making it much simpler.  Just do this:

1. Install it from Synaptic or apt-get

2. Find a mode you want to overwrite by typing "915resolution -l" and choosing a resolution you don't use, like 1600xsomething

3. sudo gedit /etc/defaults/915resolution, and set x=1280, y=800, mode=3d (or whatever mode you don't need)

4. Then start 915resolution (do sudo /etc/init.d/915resolution start)

5.Restart X (ctrl-alt-bkspc).

The whole problem should take about 2 minutes to fix.

---

### Post by dage on 2006-08-13
to joehill :
you made an error :
/etc/default/915resolution not /etc/defaults/915resolution
salut :)

---

### Post by Icarus3000 on 2006-08-13
I am using a Dell 700m, so of course would like to use 915resolution like everyone else.  However, I am running into a problem.  I finally figured out how to get and install 915resolution, but when I type "915resolution -l" in the terminal, I get a message saying "Unable to obtain the proper IO permissions: Operation not permitted".

How should I proceeed from here?

Thanks!
Icarus

---

### Post by sonny on 2006-08-15
> **Icarus3000 said:**
> I am using a Dell 700m, so of course would like to use 915resolution like everyone else.  However, I am running into a problem.  I finally figured out how to get and install 915resolution, but when I type "915resolution -l" in the terminal, I get a message saying "Unable to obtain the proper IO permissions: Operation not permitted".

How should I proceeed from here?

Thanks!
Icarus

You need to do this:

sudo 915resolution -l

because the program needs root privilege.

---

### Post by cosh1 on 2006-08-19
Thanks to all in the above posts.  I just switched to Ubuntu on my Asus w5a yesterday and finally managed to get my Buffalo Linkstation, and my resolution (thanks to you all) working. :)

---

### Post by DaveT on 2007-02-21
Hi Im pretty new to all this Debian stuff but am learning quite well.

Im having a similar issue to this on my Sony Vaio VGN-FS115E.

Im running Fiesty Xubuntu (original install was Edgy, updated to see if it solved my problem)

Its using the 915GM express graphics chip(listed as i810 driver), ive tried the above and various different things that ive come accross over the net but to no avail.

what ive found out is listed below:- (sorry if its vague, logs can be posted if needed)

The graphics has two pipes (two different addresses it would seem 0:2:0 and 0:2:1, maybe these are unrelated)

None of the resolutions settings in xorg.conf are applied and all ive got in my display settings is 'Default' (which happens to be 1024 768)

can anyone point me in the correct direction?

---

### Post by dotman on 2007-03-07
If the 915resolution hack isn't working for you may want to consider installing a different Intel driver that supports mode setting.

---

