---
title: "Can't get DVD-Rom to mount"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by redaxe90 on 2012-10-11
I know this kind of thing has been posted thousands of times before and believe me, I've been using every kind of search string I can think of, but nothing comes close to helping me spot this damn thing.

I was going to play a video DVD in the computer, something I had already done a couple of times before I upgraded to 12.04, but for some reason nothing happens. I've tried using every bit of trickery that I've come across in the threads here and still nothing. I can't get anything to talk to me via the DVD drive (I think it's a dvd reader and cd reader/burner, though the burn bit there might be wishful thinking).

When I use the command 
```
sudo mount /dev/cdrom /media/cdrom5
```I get the response
```
mount: no medium found on /dev/sr0
```Then I used
```
wodim --devices
```which yielded this:
```
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'    rwrw-- : 'PLEXTOR' 'CD-R   PX-W5224A'
-------------------------------------------------------------------------

```After reading through quite a few posts here, I decided to try this
```
sudo mount -t iso9660 /dev/sg1 /media/cdrom5
```But of course I was kicked back with this response:
```
mount: /dev/sg1 is not a block device
```When I go to the My Computer folder in the file manager I right click the CD Drive icon, not getting any mount options, and can do two things. One is open, which doesn't work, the other option is check the properties, which I did and that yields the following permissions.

Owner: 0
Group: 0
Access control
Owner: None
Group: None
Other: None

The General tab tells me that it's a CD Drive,  location is My Computer, File type is Mount Point, and then I get the standard mumbojumbo about what program to use for opening, when it was last accessed (jan 1st 1970) etc.

So now I'm completely stumped. All my search strings end up with nothing, whether I try here or on any of the search engines out there.

The BIOS spots the drive without a flaw, so I'm thinking it has to be something to do with Ubuntu, or LXDE which is my preferred desktop environment.

I hope I remembered to put everything in there, I even went as far as to use the methods pointed out in the Multimedia and Video thread, just to be on the safe side.

Kind regards in advance
Tomas

---

### Post by TheFu on 2012-10-11
If it is a commercial movie DVD, then you need the correct, DRM, codecs.  Those are not installed without you specifically asking for them. In many countries, installing them without a license is illegal.   I don't know what Ubuntu calls the package, but it is probably in the **Restricted** area of Synaptic.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) explains more.

---

### Post by asmoore82 on 2012-10-11
Is the region code unset on your DVD drive and/or is the Disc from a different region?

---

### Post by redaxe90 on 2012-10-11
I have no idea if the region has ever been set in the DVD drive I have, though I'd expect it to be region 2, due to the fact it's bought in Iceland which is a region 2 country. The DVD I was trying to watch is also region 2 and it's also region 4.

I found a post earlier about switching between regions, though I can't be certain where I did

---

### Post by redaxe90 on 2012-10-11
I decided to test a different disk, inserting a CD with copies of developed film I had done for me in the UK a few years back. That one starts without a problem, so it has to be the region thing. Can anybody remember how to set the correct region??

---

### Post by redaxe90 on 2012-10-11
Installed regionset

```
sudo apt-get install regionset
```

And wanted to use the regionset command in the terminal

```
sudo regionset
```

That yielded a surprising result

```
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
```

The odd thing is that the DVD was being used in my stepson's laptop yesterday afternoon and there are no scratches on it :confused:

---

### Post by redaxe90 on 2012-10-11
Logged into root and tried the 
```
wodim --devices
```command

the result was 0 devices located :confused:

---

### Post by redaxe90 on 2012-10-11
I keep trying and I finally found out how to properly use regionset, but look here:

```
sudo regionset /dev/sr0
```
```
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not retrieve region code settings of the drive!
This could mean your drive is region free and doesn't need any setting.
Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:2
New mask: 0xFFFFFFFD, correct? [y/n]:y
ERROR: Region code could not be set!
```

I feel like screaming my head off:mad:

---

### Post by redaxe90 on 2012-10-11
ARGHHHHHHH I feel like such a numpty :(

When I had a better look at the drive, I found out that it was a simple CD drive, with the possibility of being a writer too, though I doubt it. At least now I realise my silly mistake and I hope this can be left up as a reminder to others that they should check up on their hardware, properly, before yelling their heads off :)

---

### Post by redaxe90 on 2012-10-12
Well, turns out I was too quick to condemn myself. I decided to pick up a DVD drive that I had lying about, one that I know works because it was in a Win box that could use it only last night.

Tried all the above methods to get things to work and nothing worked. However I went into the Hardinfo program, to see if something could be retrieved and this is what it showed me.

-SCSI Disks-
ATA Maxtor 6Y200M0
ATA SAMSUNG HD501LJ
ATA WDC WD2000JB-32E
SAMSUNG DVD-ROM SD-608

```
wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg3'    rwrw-- : 'SAMSUNG' 'DVD-ROM SD-608'
-------------------------------------------------------------------------

```

The mount command yields only error messages. So I'm a bit stumped. I can't even open the drive to retrieve the disk in it with the button at the front.

Any ideas??

---

### Post by redaxe90 on 2012-10-12
Since I started delving into everything here, I found out more about the current computer setup. I'm running a 64bit system on a 32bit OS and have decided to burn a 64bit version of the OS to a CD and then reinstall everything from scratch. I'm pretty sure that I've managed to mess up quite badly with all my tinkering since I installed Ubuntu, so a clean start is probably the best way for me to go on, especially since the operating system now completely refuses to boot and I had to bounce about and find a live cd to work on.

For those who already tried to give me a hand, I say thanks guys. Too bad I hadn't paid enough attention before I posted my original question.

If everything works out fine when I've installed the 64bit OS, then I'll report that here and if it doesn't then I'll no doubt come back crying on someone's shoulder

See you on the other side folks :)

---

### Post by redaxe90 on 2012-10-16
So far no joy, but at least I have a clean install of the 64bit system. The latest error message was about the dvd drive not being able to read block 0 on the disk, despite the disk working to perfection in every dvd player in the house and all the winblows computers in the house. I'm about to run out of ideas, can anybody throw me a bone?

---

