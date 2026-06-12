---
title: "Installation nightmare"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by windowskiller on 2008-11-10
Ok, I have a Compaq Evo D510 with plenty of ram, a 2.4-GHz Pentium 4, and now a clear 40 gig hardrive. I cannot get past the black screen with the mouse pointer. Here is what I have done so far:

Downloaded disk image- OK.
Burtn image to CD- OK.
Checked hash sums- OK.
Checked disk for errors (one of the few things I can do)- OK.
Tested Memory- OK. 
Tried every possible live boot and install- not OK.

Background of machine:

It was a used business PC and had a windows password I could not get around, tried everything and that is how I found Ubuntu, decided eventually to just use it and ditch windows altogether (can't go back now) read on. Company is out of business and sold as is so there is now way to get past password.

I tried many different combinations of options in F6, removed quiet splash or whatever it was from text line, tried safe mode, tried manually boot from disk in bios, etc. Nothing worked until I tried the EOM install which got me at least to the nice graphic and I was excited when it pulled up firefox and I got all the way through the installation... but unfortunately it doesn't reboot from the hardrive. I set the partition option to wipe out windows entirely (hence the no going back comment above) because it was dead to me. My other PC and laptop will be next to make the swap if I can get this sucker to work. Anyway here is usually what happens, depending on what options in F6 I choose.

I get a blank yellow screen in most attempts and hear the introductory noises and sometimes some bongos afterwards. I have seen a screen a couple times that asks for a user name but after that it goes black and I get a functioning mouse pointer but nothing else. I waited for 30 minutes thinking maybe it was compiling code or something but that is as far as I can get. 

Sometimes I only get to the dos looking text screen list of checks, it changes font halfway through and seems to mark everything okay except for an I/O error on sr3 or something, it's too fast to read honestly. I get computer speaker beeps sometimes and once in a while I get "loading please wait" for as long as I leave the room and come back. I get the musical intro noise quite often and the manufacturer installation seemed to go fine. I don't get it.

Anyone wanna take a guess at what I need to do before I give up and fork over another $95 microsoft to get this machine online?

---

### Post by shifty_powers on 2008-11-10
have you tried the alternate install disc? (it is not a live cd and only has a text installer without a gui. it is still relatively easy to use mind...)

---

### Post by spiderbatdad on 2008-11-10
You didn't say what type of hard drive sometimes sata work configured as ide with the f6 option: all_generic_ide

The other thing that comes to mind is...your cd image is bad. I had a similar issue once, where the md5sums checked out and I kept getting the I/O error. I gave up for months. Finally I downloaded a new image from a different site, burned a new disk, and voila...sort of. On that old HP, installing Gutsy, I still had to use noapic nolapic. Though the newer kernels use a dummy apic emulation, so the lack of those parameters should not prevent you from booting.

---

### Post by Slim Odds on 2008-11-10
> **windowskiller said:**
> Ok, I have a Compaq Evo D510 with plenty of ram, a 2.4-GHz Pentium 4, and now a clear 40 gig hardrive. I cannot get past the black screen with the mouse pointer. Here is what I have done so far:

Downloaded disk image- OK.
Burtn image to CD- OK.
Checked hash sums- OK.
Checked disk for errors (one of the few things I can do)- OK.
Tested Memory- OK. 
Tried every possible live boot and install- not OK.
...


So it doesn't work OK from the Live CD?

I have an EVO D510T similar to yours. I've run Ubuntu on it for a long time (it's currently running 8.04). I have replaced the 40G drive (old one crapped out recently). I also added a better graphics card (it's a little old now, an FX5200).

I also added a gig of RAM. It runs like a champ.

Can you get a console? Check the logs.

---

### Post by jrothwell97 on 2008-11-10
Welcome to the Ubuntu Forums!

From what you've told us, it sounds like the X server (the system which draws the graphics, cursor and windows on the screen) is starting, but the desktop environment (the file manager, panels, widgets, etc) isn't. I'm not sure what might have gone wrong here, so I'm going to make some suggestions based on intuition.

[list][*]When you used the OEM install and got as far as the first reboot, did you eject the disk on reboot? Otherwise, your machine may boot from the CD again. Otherwise, it may be that the boot loader (GRUB) was not installed properly.
[*]Try re-downloading and re-burning the CD, at a slower speed, to a brand new disc (check it's been finalised as well). You can also order a free CD (shipit.ubuntu.com) if you want.
[*]Try using the 'alternate' installation CD. This uses a text-based installer as a failsafe, so you should be able to run that.[/list]

Let us know how you get on. Good luck.

---

### Post by Pro-reason on 2008-11-10
It doesn't seem like Ubuntu has any problem running on your machine, because you were able to boot from the live CD just fine.  But something is stopping your X server from working properly now.

There does seem to be an input-output error on one of your drives.  This would be enough to make any operating system because faulty.

Boot from the live CD again.  From there, you can run tests such as “fsck” which will scan the drive for errors.  It may be that you need to reformat the drive or get a new one.

---

### Post by metallicamike on 2008-11-10
did the screensaver go up while it was installing? i noticed the last few times ive reinstalled it would fail or have major issues and errors if the screensaver comes up during install.

---

### Post by Bölvaður on 2008-11-10
> **jrothwell97 said:**
> From what you've told us, it sounds like the X server (the system which draws the graphics, cursor and windows on the screen) is starting, but the desktop environment (the file manager, panels, widgets, etc) isn't.

Right on! This is what I was going to say.

So somehow it stops before it finishes loading up all the programs, but it gives sign that it has gone through the login stage (the music you hear).

For me it is like you have gone too far into the installation to be either cd drive that is slow (I trust that the cd is ok) or that the ram isn't handling it.

Without more info on this, or person that has exactly the same problem with same type of computer... we might not get to know what is wrong because this is the solution:


[QUOTE=jrothwell97;6147262Try using the 'alternate' installation CD. This uses a text-based installer as a failsafe, so you should be able to run that.[/QUOTE]

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")



(lol I almost forgot to press Submit:lolflag:)

---

### Post by cariboo on 2008-11-10
Have you tried the safe graphics mode that is available by pressing F4 at the menu screen? A couple of versions ago I had the same problem and by booting in safe graphics mode I was able to install Ubuntu.

Jim

---

### Post by alzie on 2008-11-10
This sounds similar to an issue I had with my wife's Windows XP box.  I used the [COLOR="Blue"][Ultimate Boot CD]("http://www.ultimatebootcd.com/")[/COLOR] to run  diagnostics on the hard drive.  I ended up using one of the utilities to over write the entire drive with 1's or 0's and then I was able to properly format and install XP.

I'm not sure if this will help but I'm hoping.

---

### Post by windowskiller on 2008-11-11
Wow, a lot more responses than I imagined!

"have you tried the alternate install disc? (it is not a live cd and only has a text installer without a gui. it is still relatively easy to use mind...)"

Not yet, will burn one again if I cannot get a validation for a an old xp disk I found this morning.

"You didn't say what type of hard drive sometimes sata work configured as ide with the f6 option: all_generic_ide

The other thing that comes to mind is...your cd image is bad. I had a similar issue once, where the md5sums checked out and I kept getting the I/O error. I gave up for months. Finally I downloaded a new image from a different site, burned a new disk, and voila...sort of. On that old HP, installing Gutsy, I still had to use noapic nolapic. Though the newer kernels use a dummy apic emulation, so the lack of those parameters should not prevent you from booting. "

I'll look at it again and report back that hard drive unless I throw the PC out the 2nd floor window tonight. I do not see all_generic_idle as an option in F6. CD image seems fine I as far as I can tell the computer has a sticker that says "designed for windws XP" on it, could that be some proprietary hardware scheme? I'll try the alternate CD install first if I cannot get someone in the all center in mumbai to activate my XP tonight when I get home. I tried noapic and nolapic and just about every combination in between. 

"When you used the OEM install and got as far as the first reboot, did you eject the disk on reboot? Otherwise, your machine may boot from the CD again. Otherwise, it may be that the boot loader (GRUB) was not installed properly. 
Try re-downloading and re-burning the CD, at a slower speed, to a brand new disc (check it's been finalised as well). You can also order a free CD (shipit.ubuntu.com) if you want. 
Try using the 'alternate' installation CD. This uses a text-based installer as a failsafe, so you should be able to run that."

(SORRY- could not figure out how to quote each person in one post!)

Yes, I took the disk out. And tried to reboot off hardrive alone. Then I tried to run live again off CD since the drive was reformatted from OEM install attempt. I burned the CD at super low speed and it gets me through most of installation, I am leaning towards a hardware problem. I will post a more detailed list of configuration tonight. I will look into getting the disk from shipit if the alternate install does not work. Running out of CD's!

"Boot from the live CD again. From there, you can run tests such as “fsck” which will scan the drive for errors. It may be that you need to reformat the drive or get a new one."

That's just it, I can only get to the opening terminal, select my language, use the function keys, I cannot get it to actually boot at all. I can get all the way through the OEM installation though and I clicked on a link at one point and it pulled up web browser (no internet connection yet but the app opened). I get a giant yellow block and the intro audio then I get some more CDROM activity and then a black screen with a small mouse pointer that I can move around (which gets old after a couple of hours).
 
"Have you tried the safe graphics mode that is available by pressing F4 at the menu screen? "

Yes as well as as many combinations of F6 that I could from memory (free software/noapi/nolapi/holding my breath).

I did not see any graphics except when I ran EOM install and saw the weird abstract lion watercolor thingy or whatever it was. heard some bongos a few times too. 

I was about to give up on this but after a surprizing amount of help on here I might dig in a try it again. 

Thanks for all the help and suggestsion, I'll check back tonight if my head doesn't explode.

---

### Post by edvan on 2008-12-10
hello windowskiller, any outcome with your Compaq Evo D510???

i have exact same pc as yours and the same problem... nothing is running after i enter my password...

i got the Ubuntu 8.10 CD sent from Ubuntu.

tried installing twice and still same error, clean install also...

regards

---

### Post by scorp123 on 2008-12-10
> **windowskiller said:**
> Ok, I have a Compaq Evo D510 with plenty of ram, a 2.4-GHz Pentium 4, and now a clear 40 gig hardrive.  I worked for HP between 2000-2007 and I had lots of their hardware at my disposal back then. In fact I think I have laid my hands on pretty much any laptop, desktop and server produced by HP between 2000 and 2007. And I tried Linux on all of them. I think this qualifies me to make the following statements:

Compaq Evo xxx PC's, especially the "small formfactor" ones which are only slightly bigger than a 5.25" computer drive, seem to have one _really weird BIOS._ And there isn't much you can do about it, a BIOS update is unlikely to help.

The various Evo Dxxxx PC's that I had during my time at HP refused to boot when the GRUB boot loader was used on the harddisk. Yes, that's no joke.

So whenever I installed any Linux onto those PC's I had to make sure that I used the LILO boot loader, not GRUB!

There is something in their BIOS which will break GRUB and in 99% of the time prevent it from booting properly, thus "freezing" the machine upon power-up.

With LILO however ... no issues at all.

The problem here is that only few distros still use LILO and even fewer let you choose which boot loader you actually want to use. (OpenSUSE will default to GRUB too but it lets you select LILO during the installation if you want ... )

_Workaround:_

Install Ubuntu from the CD ... but when the installation finishes: **_Don't reboot!_** Instead you have to use the "**chroot**" command, get into your harddisk's installation (as if you had booted off the harddisk already) and then tell "apt" to install "lilo". Example ... this is assuming that your "/" disk is on /dev/sda1 (please adjust accordingly):
[LIST=1]
[*]There will be a message that you need to reboot for the installation to take effect. **Ignore it.**
[*]instead open a terminal:  Applications > Accessories > Terminal
[*]a terminal should have opened
[*]make yourself "root" (shouldn't need a password): **sudo su -**
[*]Switch over into your installation:  **chroot /dev/sda1 /bin/bash**
[*]you should still be root, if not use "**sudo su -**" (if it asks for a password this time: that should be the password you defined during the installation)
[*]Install LILO, remove GRUB:  **apt-get install lilo**
[*]Get out of the shell:  **exit**
[*]Now reboot .... !
[/LIST]

Hopefully your Evo D510 will boot now.

If there are other weird things happening please come back and let us know.
.
.
.

---

### Post by Slim Odds on 2008-12-11
> **scorp123 said:**
> ....
Hopefully your Evo D510 will boot now.

If there are other weird things happening please come back and let us know.
.
.
.

So you're saying that it's a fluke that my EVO D510T works just fine with GRUB?

I have my doubts that any system that will boot with LILO will not also boot with GRUB.

---

### Post by Duck2006 on 2008-12-11
> **slim odds said:**
> so you're saying that it's a fluke that my evo d510t works just fine with grub?

I have my doubts that any system that will boot with lilo will not also boot with grub.

+1

---

### Post by scorp123 on 2008-12-11
> **Slim Odds said:**
> So you're saying that it's a fluke that my EVO D510T works just fine with GRUB?  D510T? Isn't that a tower?? The towers always worked as far as I remember. It's those small beasts which were the troublemakers, e.g. like this one:
[IMG]http://www.pacificgeek.com/productimages/xl/D510E-PC-3B.jpg[/IMG] ... that's a 510E and it's only slightly bigger than a standard 5.25" CD drive. I have worked with 510E's ... and they had the problem I described above. OpenSUSE would work OK on those things for as long as you installed LILO.

> **Slim Odds said:**
>  I have my doubts that any system that will boot with LILO will not also boot with GRUB. You can believe what you want. I tested this stuff extensively and I found that those ex-Compaq "small formfactor" PC's are weird and broken by design. Whenever I had the choice I'd pick e.g. HP Vectra and Kayak PC's for the stuff I had to do and not those ex-Compaq PC's, especially not "small formfactor" ones.

If I had to guess I'd say that those "small formfactor" PC's had a very customized BIOS, e.g. to keep them from overheating and so on. And it's likely that this didn't play too well with Linux. It would not be the first time that a hardware maker does something like that and that whatever they did doesn't play well with Linux. Just to mention the recent case of Foxconn motherboards which behave differently when those boards detect Linux. It could very well be something similar here.
.
.

---

### Post by Slim Odds on 2008-12-11
Yes, the D510T is a tower unit.....

Interesting..... I'm not familiar with those "little beasts"  :p

---

### Post by edvan on 2008-12-11
i found my solution for my Compaq Evo D510

[IMG]http://webdevsys.com/images/d510sff_sm.jpg[/IMG]

it was the video card causing the problem, i have to remove the compiz with instruction from launchpad.

[https://bugs.launchpad.net/ubuntu/+bug/259385](https://bugs.launchpad.net/ubuntu/+bug/259385)

it works fine after removing compiz...

---

