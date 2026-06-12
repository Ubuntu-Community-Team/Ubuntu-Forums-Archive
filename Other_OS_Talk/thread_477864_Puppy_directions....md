---
title: "Puppy directions..."
date: 2007-06-18
forum: Other OS Talk
---

### Post by Jareth on 2007-06-18
been messing with puppy and realy impressed by its speed so I was wanting to instal it on my desktop as its gettin old and nearing retirement.
But, it gets to "uncompressing linux........ ok booting kernel" and stops when booting off the live cd. Can anyone help or point me to an answer elsewhere, sorry to ask here but you guys are the best place to start,
Ta!

---

### Post by reset3x on 2007-06-18
Which version are you using? 2.15 CE gave me headaches..... 2.14 ran great.. Have you given Xubuntu a shot?

---

### Post by Jareth on 2007-06-18
Its 2.16, It does run off the disc on my laptop, which I think is roughly the same spec, but I think its probably the desktop having other 'issues'. It never did boot anything quite right.

Yeah xubuntu is good too but still is quite slow on this machine for some reason.

---

### Post by reset3x on 2007-06-18
What the specs on the machine you're trying to install it on? Have you looked here? [http://www.murga-linux.com/puppy/](http://www.murga-linux.com/puppy/)

---

### Post by smoker on 2007-06-18
> **Jareth said:**
> been messing with puppy and realy impressed by its speed so I was wanting to instal it on my desktop as its gettin old and nearing retirement.
But, it gets to "uncompressing linux........ ok booting kernel" and stops when booting off the live cd. Can anyone help or point me to an answer elsewhere, sorry to ask here but you guys are the best place to start,
Ta!

how much ram have you got, puppy loads straight to ram and i think you need about 64 to run from the live cd, but once installed to a hard drive it will run on less.

---

### Post by Jareth on 2007-06-18
I'll have a look at that site, thanks

Its a pentium 3 650 mhz, I'm sure its got all thats required. Can't quite remember how much memory its got. Isn't there a command to find the spec out in the terminal?

---

### Post by smoker on 2007-06-18
hi, your pc should show the ram amount on the post screen, or if not, go into the bios and you'll find the info. 

i found this link that may be of help (or not!) [http://puppylinux.org/wikka/HardDiscInstallWithDos?show_comments=1](http://puppylinux.org/wikka/HardDiscInstallWithDos?show_comments=1)

what operating system have you installed at the moment, and are you planning to dual boot, or a complete install of puppy?

---

### Post by reset3x on 2007-06-18
The machine should tick off your ram at boot unless it got one of the oem boot screens...

---

### Post by reset3x on 2007-06-18
sorry smoker... didn't mean to step on your toes:oops:

---

### Post by smoker on 2007-06-18
> **reset3x said:**
> sorry smoker... didn't mean to step on your toes:oops:

no probs, the more the merrier:D:D:D

---

### Post by Jareth on 2007-06-18
Oh yeah, of course it does, doh!
Its telling me theres 500MB of memory in it.
It actualy runs ubuntu nicely at the moment and there's no problems running that, considering the relatively ancient specs. But, using puppy on my laptop just felt that bit faster, and rather than messing the laptop up experimenting I would rather use the desktop.

I remember running the ubuntu live cd, I have to type a bit of info at the grub to get that to run so I reckon it must be the same for puppy. Incase you're interested the ubuntu live cd just keeps rebooting so I have to add:
gdth=disable:y mca-pentium no-hlt acpi=off noapic nolapic
then it starts up great and I can instal it and everything.

Think my comp just doesn't like Live discs?

---

### Post by reset3x on 2007-06-18
I'm not trying to demean you but that sounds like its the processor speed ie:500 MHZ.... If you have anything near 500 it would be 512MB ... But being that you can run Ubuntu you have more than enough RAM to run Pup.... That stuff you have to type in to get Ubuntu Live to work is because of bios issues.... That doesn't mean you can't get puppy to work... I have to be honest and tell you I'd be doing you a disservice in helping you out with that... Maybe smoker can hook you up.... 

Good luck!!!

---

### Post by smoker on 2007-06-18
hi, as reset3x, mentioned, it may be a bios issue, if i make changes to the bios, i usually make a note of them so i can change things back if anything untoward happens! though most bios's have a 'factory defaults' setting you can use to get back to a working state. before i mucked about with the bios though, i think i would check the ram. you can do a ram check off the ubuntu live cd (third or fourth option when the boot screen appears, if i remember!) or you can download and burn a copy of memtest86 from here:
[http://www.memtest.org/](http://www.memtest.org/)

it may also just be a bad burn of the puppy cd mixed with an aging cd-rom, did you burn at a slow speed?

best of luck

---

### Post by Jareth on 2007-06-18
No probs reset3x, I'm a total 'newb' and not very sharp tonight either so thanks for the help.

---

### Post by HermanAB on 2007-06-18
The command 'top' will tell you a few things, including how memory you got.

Puppy works great when it works, but when it doesn't, then it is best to move on to something else since it is hard to tweak.

I'm using Puppy every day on a rotten company laptop which has a locked down WinXP with an encrypted disk drive - so I boot Puppy off a memory stick without using the disk drive...grumble, grumble, so there!, grumble...

---

### Post by Jareth on 2007-06-19
Yeah, I tried a Damn small linux live cd as well and it did the same thing.
Shame really.

---

### Post by IceVapour on 2007-06-20
Is it just me or does 500mb strike anyone as an odd number?  Surely that should be 512mb.  Sorry if it was a typo :redface:

I personally run Puppy on my own laptop (2ghz, 1gb ram) and on my mother's laptop (400ghz, 128mb ram), and have never had any problems.  May I suggest you install it to a USB drive and see if it works after that?  There is a tool in the install section to install it directly to a USB drive.

Hope that helped!

---

### Post by smoker on 2007-06-20
> **IceVapour said:**
> Is it just me or does 500mb strike anyone as an odd number?  Surely that should be 512mb...

yes, that is odd, memory should show, eg, 64, 128, 256, 512, etc. sometimes with onboard video a proportion of the ram is swiped for graphics, but usually something like, 32, or 64, or whatever a user decides through the bios. that's one of the reasons i recommended a ram test.

---

### Post by Jareth on 2007-06-26
Apologies, I think I was being lazy and rounding off (badly) there.
I just did the top command and the total memory is 580836k.
I'm sure its got plenty from that to run puppy but I think it just doesn't like Live discs. I think i'll try to install it straight to the Hard drive rather than booting it live (if poss) with that link
[http://puppylinux.org/wikka/HardDiscInstallWithDos?show_comments=1](http://puppylinux.org/wikka/HardDiscInstallWithDos?show_comments=1)

I'll try and let y'all know whats happenin,
Ta!

---

### Post by Kowalski_GT-R on 2007-07-02
dumb question:

can Puppy be configured to "look like" gnome gui as in Ubuntu?

I guess it will come at the expense of lightness, if possible at all.

thanks

---

### Post by smoker on 2007-07-02
> **Kowalski_GT-R said:**
> dumb question:

can Puppy be configured to "look like" gnome gui as in Ubuntu?

I guess it will come at the expense of lightness, if possible at all.

thanks

i think you can configure it to look like anything you want!
screenshots of puppy: [http://www.puppylinux.org/user/photogallery.php?album=3&rowstart=0](http://www.puppylinux.org/user/photogallery.php?album=3&rowstart=0)

---

