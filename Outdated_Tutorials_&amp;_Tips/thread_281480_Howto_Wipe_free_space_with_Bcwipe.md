---
title: "Howto: Wipe free space with Bcwipe"
date: 2006-10-21
forum: Outdated Tutorials &amp; Tips
---

### Post by CupofDice on 2006-10-21
Just decided to throw this out here if anyone is interested in wiping free space on Linux. It wasn't meant to be a how to, so sorry if it isn't that 'deep'. I was going to put it in cafe, but didn't want it to disappear so easily.

Bcwipe is a proprietary file wiping program, but it can also wipe free space and file slacks. Since I could not find any easy information about doing that on Linux, this may be a good option if you are interested. It uses Peter Gutmann (automatically I think), DoD, or your own defined number of wipes.

1a. Download alien converted rpm to your desktop-
[http://www.sendspace.com/file/eob9tj](http://www.sendspace.com/file/eob9tj)
[http://www.gigasize.com/get.php/125525/bcwipe1.64i386.deb](http://www.gigasize.com/get.php/125525/bcwipe1.64i386.deb)

1b. Or download the latest rpm-
[URL="http://www.jetico.com/linux/BCWipe-1.6-4.i386.rpm"]
http://www.jetico.com/linux/BCWipe-1.6-4.i386.rpm[/URL] 

```

sudo apt-get install alien [COLOR="Red"](if alien is not already installed)[/COLOR]
cd ~/Desktop
sudo alien --to-deb -v BCWipe-1.6-4.i386.rpm

```

2. Unpackage and install.

```

cd /Desktop
sudo dpkg --install bcwipe_1.6-4_i386.deb

```

3. To wipe free space on root.

```

sudo bcwipe -F / [COLOR="Red"](where -F stands for free space)[/COLOR]

[COLOR="Red"]I believe this automatically uses Gutmann's method, and this may take a LONG time, so you might want to 
define it to DoD or your own number by entering-[/COLOR]

sudo bcwipe -F -md /  [COLOR="Red"](-md stands for DoD)[/COLOR]
sudo bcwipe -F -m3 /  [COLOR="Red"](-m stands for mode (in this case 3 wipes))[/COLOR]

```
[COLOR="Red"]The same rules works for /home or whatever partition you wish to wipe. As in wiping my 10 gig ext3 partition.[/COLOR]
```

bcwipe -F -v -m1 /media/hda7/

```

A bit of advice. You may screw up, cancel your wipe, and notice all or a lot of your free space is taken up. Just delete the bcwipe folders that were created (using sudo). 
```

cd /thedirectory
sudo rm -r bcwipe-wiping_free_space-tImFVa (or whatever name it has)

```
Before
[[IMG]http://img20.imageshack.us/img20/5056/beforenh1.th.png[/IMG]]("[URL=http://img20.imageshack.us/my.php?image=beforenh1.png)"][[IMG]http://img20.imageshack.us/img20/5056/beforenh1.th.png[/IMG]](http://img20.imageshack.us/my.php?image=beforenh1.png)[/URL]
After
[[IMG]http://img224.imageshack.us/img224/6551/afterfq0.th.png[/IMG]]("[URL=http://img224.imageshack.us/my.php?image=afterfq0.png)"][[IMG]http://img224.imageshack.us/img224/6551/afterfq0.th.png[/IMG]](http://img224.imageshack.us/my.php?image=afterfq0.png)[/URL]

That worked for me when I did this for the first time and Gutmann was taking to long. If you run into the same problem as Ziggy72, try DDM's solution.



[http://www.jetico.com/]("http://www.jetico.com/") for more information or the original rpm. They also have an encryption program if you are interested (of course open source options are better:D) They also have versions for Windows.

Also make sure you look at "man bcwipe" first and use at your own risk (in other words I know as little as possible about wiping and this program). This is just what worked for me.

---

### Post by Ziggy72 on 2006-10-23
Yes..... But......!!

I installed BCWipe and then used the command

 sudo bcwipe -F /

The disk whirred away happily so I went to bed and left the program to do its stuff. 10 hours later, the program was still running and the disk was still whirring. So, enough was enough and I stopped the BCWipe program.

I then did a df -h and found that instead of having about 15Gb of free spece, I now had only 1.9Gb.

As CupOfDice suggested, I deleted the bcwipe folders that were created (using sudo) but the free space that should have been there wasn't - still only 1.9Gb.

I then did everything I could think of to get the free space back but, to cut a very long story short, I was unsuccessful and my Ubuntu partition was effectively trashed.

So I had to restore the partition from a recent backup using Acronis True Image and after 4 hours of solid work I'm now more or less back to where I started, but without BCWipe!

If you do use BCWipe, be a lot more careful than I was and have a good backup which will allow you to restore everything if necessary. Good luck to those of you who are brave enough to experiment with the program...

---

### Post by DDM on 2006-10-24
Ziggy, why didn't you use a program like Kdirstat to find the junk files? BCwipe didn't really bork your system, just used a temp file where you weren't expecting it.

---

### Post by Ziggy72 on 2006-10-24
DDM - well, if there *was* a temp file, hidden or not, I surely couldn't find  it anywhere. It would have to have been about 15Gb  to leave me with only about 1.9Gb free and none of the searches I used could find it - and I really did search very diligently for many minutes. I would have thought it should have been in /, but I couldn't find anything that looked like a promising temp file... in any directory... It may be worth noting that the BCWipe web site does not list BCWipe as having been tested with Ubuntu.

---

### Post by Ziggy72 on 2006-10-25
Following on from yesterday's disaster with BCWipe, I have downloaded and successfully used LinuxWipe Tools which is available at

[http://basicsec.org/LinuxWipeTools.tar.gz](http://basicsec.org/LinuxWipeTools.tar.gz)

I've used Wipefree2.sh (because this suits the way my directory structure is set up) and Wipeswap.sh. Both scripts ran without any problems.

Anybody who wants to use this set of 4 scripts should look at the Readme to view the wipe limitations and so they can use the most appropriate wipe routine for their purpose.

I was able to work on my pc without any problems until Wipefree2 was nearing the end of its routine when I received some error messages about "not enough disk space" when trying to save files and create folders, but this was expected and explained in the documentation. 

For me, these have proved to be pleasing, trouble-free scripts.

I'm using Dapper.

---

### Post by CupofDice on 2006-10-25
I have no idea what caused that. I just "sudo -F -v -m1 /" myself and cancelled when it got rid of a 100 mb, then "cd" to the directory, and "sudo rm -r bcwipe-wiping_free_space-tImFVa". I regained the space with no problems. I use ext3. You?

---

### Post by Ziggy72 on 2006-10-25
Yes - ext3. I have no idea why I got the problem  - but nowhere did I find any file called bcwipe-wiping_free_space_xxxxxx. Something got screwed up - why or how - I have no idea...

---

### Post by CupofDice on 2006-10-25
It creates this folder in root (if root is what you are wiping) and I assume it holds all the temporary files that fill up your harddrive and then deletes them (all wiping programs seem to do this). It also seems you have to be in root to delete it.

Before
[[IMG]http://img20.imageshack.us/img20/5056/beforenh1.th.png[/IMG]]("[URL=http://img20.imageshack.us/my.php?image=beforenh1.png)"][[IMG]http://img20.imageshack.us/img20/5056/beforenh1.th.png[/IMG]](http://img20.imageshack.us/my.php?image=beforenh1.png)[/URL]
After
[[IMG]http://img224.imageshack.us/img224/6551/afterfq0.th.png[/IMG]]("[URL=http://img224.imageshack.us/my.php?image=afterfq0.png)"][[IMG]http://img224.imageshack.us/img224/6551/afterfq0.th.png[/IMG]](http://img224.imageshack.us/my.php?image=afterfq0.png)[/URL]

---

### Post by Ziggy72 on 2006-10-25
Ok - I assumed the file was created in root - but it definitely wasn't there after the program had been running for 10 hours. Wipefree2 which I used earlier today created a temporary file of about 15Gb before it was deleted and so I suppose that's about the size of file BCWipe tried to create. However, for whatever reason, BCWipe wasn't able to complete its work and its temporary file (though presumably still there physically) just wasn't visible and able to be deleted. Oh well... water under the bridge...

---

### Post by Ziggy72 on 2006-10-25
Just a quick thought... CupOfDice - have you tried to do a 

sudo bcwipe -F /

and then left the program to finish - however long that might take? I'd be interested to hear of your success, or otherwise. Mine is (or was when I tried the program) a 20Gb ext3 partition with about 5.1Gb used.

---

### Post by CupofDice on 2006-10-25
Yeah, the first time I used it. Gutmann is like 34 wipes, so sudo bcwipe -F m1 / and allowing that to finish should give you an  idea. I can't remember how long it took me because I forgot about it or if I used gutmann for that matter. I probably had around 3.2 gigs free at the time on root.

---

### Post by user2037 on 2007-12-07
Open terminal and type something like:

dd if=/dev/urandom of=/tmp/shred-free-space-slug
rm /tmp/shred-free-space-slug

If you forget --or can't run-- the "rm" command then the slug should still be removed after a restart.

This solution isn't perfect as the OS may still reserve space or other software may complain free space is low.

---

### Post by BLTicklemonster on 2008-02-21
Um, if you're wiping a 30 gig drive that has 1 gig free space on it, wouldn't it like make sense just to use gparted to reformat the drive, then run bcwipe on a free and open 30 gig drive so space wouldn't be an issue? (replace the word drive with partition as needed, of course)

I have a hard drive with some filth on it that I'd as soon not have around, and desire to have the drive totally clean. I've run magic rescue on it after having formatted it, and the images were still there. I then reformatted it to ext 3, then reiser, then fat32, then back to ext 3, ran magic rescue, and nothing would show up. It said it found stuff, but couldn't do anything with it.

Since then, I've done this:

dd if=/dev/zero of=/dev/hda

but I really want to be sure nothing remains at all regardless.


*in case you're wondering, it was a "this machine's junk, if you want it for spare parts, help yourself" situation. Yeah, being nosey, I looked around, and yep, found some pron sites in in the temporary files, and lo and behold some rather um, well, images that would get someone in a heapa trouble. I looked at the sites visited's names, and none looked like anyone was purposely looking for anything "wrong", but the size of the images pretty much led me to believe that they were thumbnail sized images on pages serving as links to other sites, so I figure the fellow wasn't like some prevert or anything. And it's not like there were that many. They all dated to one week out of what looked like ages of browsing. (I had no idea that much stuff would stick around)  Which leads me to beg the question, "what if someone who didn't know how to work on their computer had cruised some pron sites, and these little nasties were in their temp folder, and some straightlace tattle tale who had no business snooping saw them and called the law? Would the owner be in a heapa trouble because of the images on the drive? I mean, you open a page, and you have no control over the content, right? But the images get cached, and bam, you have stuff on your drive; in your possession. Scary thought...

---

### Post by lespaul_rentals on 2008-02-21
If you want to get rid of these pictures, reformatting and the like will not destroy all traces.  If I get your drift about the possible content (CP) I would recommend using Darik's Boot and Nuke.  Use either DoD 7-pass or Guttman Method, and you are pretty much safe.  ;)

---

### Post by BLTicklemonster on 2008-02-21
You probably do get the gist, unfortunately.

So with dban, can I specify just what exact drive or partition (yes, I looked at it while it was slaved, so I have that crap on this drive most likely)? I have to make a bootable disk, right? Run it, then what?

---

### Post by lespaul_rentals on 2008-02-22
> **BLTicklemonster said:**
> You probably do get the gist, unfortunately.

So with dban, can I specify just what exact drive or partition (yes, I looked at it while it was slaved, so I have that crap on this drive most likely)? I have to make a bootable disk, right? Run it, then what?

Just download the CD image from the site: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)  Burn the ISO to a CD using K3b or Gnomebaker or whatever you use.  Then, boot up with the desired device to clean connected to your motherboard.

**DO NOT USE THE AUTONUKE.**  When you boot up you will have a list of options.  You want to select the interactive option.  From there, select the device you want to scramble (take note of the size, make, and model on the hard drive itself) and select a certain partition or just the whole device.

From there, you can select the method, data stream type, and number of passes.  If you want to be 100% sure it's gone, go for the Gutmann method (read the [Wikipedia article](http://en.wikipedia.org/wiki/Gutmann_method) if you would like; it's a very fascinating read and cool to learn about).  If you want to be 99% and you plan on installing an operating system over it anyway, just use the DoD 7-pass.

If you're going for the Gutmann Method, I'd expect at the very least 12 hours to finish the wipe.  But, hey, peace of mind, right?

[QUOTE=BLTicklemonster]"what if someone who didn't know how to work on their computer had cruised some pron sites, and these little nasties were in their temp folder, and some straightlace tattle tale who had no business snooping saw them and called the law? Would the owner be in a heapa trouble because of the images on the drive? I mean, you open a page, and you have no control over the content, right? But the images get cached, and bam, you have stuff on your drive; in your possession. Scary thought...[/QUOTE]

This is one of the reasons I am against some of the child porn laws out there today.  Don't get me wrong, I'm not a pedophile and I don't support anyone who harms a child, but some of the laws are flat out asinine.  I remember reading about a court case where this college student got arrested and charged with possession and using a computer for child pornography, and he was going to get a few years.  Then, forensic scientists found out somebody used Sub7 (yes, Sub7, that old-school backdoor) to upload it to his computer.  More recently, a kid, 15 years old or so, was caught with some pictures of young girls in "seductive positions."  He would have faced life in prison since he lived in Arizona, and you get many years for each picture.  Turns out someone had uploaded them to his computer since he had some open p2p folders on his computer.

Now, you tell me, shouldn't the authorities be hunting down the ones who touch little kids in naughty places instead of barging in, guns drawn, on someone who has a picture of a naked 16-year old on his computer?  The people who make that porn should be locked up, but possession seems to me to be a victimless crime, so long as it is not used for grooming of potential victims.

Oh, well.  I don't take part in it, so it doesn't concern me too much.  Anyway, yeah, get that hard drive wiped.  :)

---

### Post by BLTicklemonster on 2008-02-22
Child pron? Heavens no, it's Hillary campaign ads.




Just kidding.




Thanks for the tips.

---

### Post by BLTicklemonster on 2008-02-22
Thank you, I think I've got this going along fine now.

---

### Post by OldSpiceAP on 2009-03-26
How is this better than doing
```
sudo apt-get install secure-delete
```

and then using the tools it includes:

srm 	Secure remove; used for deleting files or directories currently on your hard disk

smem 	Secure memory wiper; used to wipe traces of data from your computer’s memory (RAM)

sfill 	Secure free space wiper; used to wipe all traces of data from the free space on your disk

sswap 	Secure swap wiper; used to wipe all traces of data from your swap partition.

---

