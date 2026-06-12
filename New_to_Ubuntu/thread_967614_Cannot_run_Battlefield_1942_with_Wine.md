---
title: "Cannot run Battlefield 1942 with Wine"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by ewingmaestro on 2008-11-02
I have recently installed wine on my ubuntu eee os, and i cannot get it to work. Could someone possibly give me a step by step guide on how to install and run battlefield 1942 on my laptop, as i am an absolute beginner.

Much appreciated.

thanks.

---

### Post by okey666 on 2008-11-02
Is this it:
[http://appdb.winehq.org/appview.php?iAppId=1370](http://appdb.winehq.org/appview.php?iAppId=1370)

If so, what version. Click on the version you are running further down that page. There is a how-to. 

For this to work, you MAY need to the latest version of wine. Did you use [these instructions]("http://www.winehq.org/site/download-deb") to install wine?

---

### Post by shifty_powers on 2008-11-02
> **ewingmaestro said:**
> I have recently installed wine on my ubuntu eee os, and i cannot get it to work. Could someone possibly give me a step by step guide on how to install and run battlefield 1942 on my laptop, as i am an absolute beginner.

Much appreciated.

thanks.

are you talking about the eee pc?

---

### Post by ewingmaestro on 2008-11-02
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7591](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7591)

thats the version

i have just run the updater instructions so now im at the latest, and as i have an eee pc i do not have a disk drive so what do i do??

thanks

---

### Post by Daveth on 2008-11-02
um, that is going to be a bit tricky then. I assume you already own a copy on cd or dvd, so your problem is porting it to the flash drive. You could use an external usb drive, though the setup.exe file would need to know where a) all the files for building the game are, and b) where to put them when it had build them. Ditto loading them onto a pen drive.
You could try copying all the files off the cd/dvd and dumping them into a bespoke file on the eeepc, and see if wine will play nicely. You can point wine to where the setup.exe is, and if all the game files are copied across in the same file structure, it should work. You might need, of course, to be connected to the internet as well.
I'm not even going to go into the arguments about write times and flash drive failure, or that fact that I think it will be a rather mean experience and hardly do justice to the game, but that is your call.

---

### Post by shifty_powers on 2008-11-02
dude, i know it's not the newest of games, but is the eeepc, a not very powerful notebook, even going to be capable of running it?

can't help but thinking you are being very optimistic there.

could well be wrong mind :D

---

### Post by Paqman on 2008-11-02
> **shifty_powers said:**
> dude, i know it's not the newest of games, but is the eeepc, a not very powerful notebook, even going to be capable of running it?


I have a 1.5GHz Celeron with Intel915 graphics that *almost* runs BF1942. I'd expect that an eee 900 or later might be in with a chance. No chance on any of the 700 models, though.

---

### Post by ewingmaestro on 2008-11-02
i downloaded the files off a torrent so i could use them with my eee pc, although im using a genuine keygen from the retail version i bought for my pc :)

okay where should i put the files after i have installed wine??

and how do i run them??

thanks.

---

### Post by Paqman on 2008-11-02
> **ewingmaestro said:**
> 
okay where should i put the files after i have installed wine??

Anywhere you like. During installation they'll be copied into the correct location, so make sure you've got some free space.

> 
and how do i run them??

The Wine App DB page for BF1942 will have install instructions. In general though, once you've installed Wine you can just click on .exe's to run them.

---

### Post by ewingmaestro on 2008-11-02
Okay iv added the setup files into C drive program files foler, and then ran the setup, which installed the files into the programs folder.

I double click on BF1942.exe and nothing happens, and i right click and select "open with wine windows program loader" and nothing happens.

what do i do??

---

### Post by okey666 on 2008-11-02
Its usually best to run .exes through the terminal though, that way you can take a peak at any errors that occur.

wine stores its stuff in a hidden folder in your "home folder" to display hidden folders, pres ctrl+h while in your home. Then find out where wine has put your game by looking around inside ".wine/drive_c/program files". Use this info in the commands below.

Navigate in the terminal using cd, to the place where the setup file is to do this run:
```
cd /home/<your user name>/.wine/drive_c/Program\ Files/<name of folder where game is>
```

Then run
```

wine <name of game .exe>

```

---

### Post by Daveth on 2008-11-02
the file association with WINE does not always play nicely, so fire up a terminal (I forget the keystrokes for the eeepc) and type

```
wine battlefield1942
```

or similar- I don't know what it calls itself and that is important, and it is case-sensitive. Some Battlefield players shopuld be able to comment on this. This will then get WINE to load itself and then run the .exe.

---

### Post by ewingmaestro on 2008-11-02
i have done both these commands in the terminal, and nothing happens. The terminal stops for a moment, then resumee.

Any ideas??

---

### Post by Paqman on 2008-11-03
> **ewingmaestro said:**
> 
Any ideas??

Have you gone through everything in the [Wine App DB entry for BF1942](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7591)?

---

### Post by The Tapsa on 2009-06-05
I have problems with BF1942 too. I haven't got EEE pc but problem seems to be somewhat similar.

when I try to run .exe I can see the spash screen of BF1942 but then it closes and nothing happens. I've tried it trough command line and it says things like thist:

```
942$ wine BF1942.exe
/usr/bin/pulseaudio: error while loading shared libraries: libsndfile.so.1: cannot open shared object file: No such file or directory
E: context.c: waitpid(): Ei lapsiprosesseja
err:seh:raise_exception Unhandled exception code 80000003 flags 0 addr 0x4097ee
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0xb3e4d4,0xc6d49a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x12b798,0xc6d49a): stub
err:eventlog:ReportEventW L"6"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000000cc,0xb3e4d4,0xc6d51a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000000cc,0x12b798,0xc6d51a): stub
err:eventlog:ReportEventW L"7"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
sinbitch@sinbitch-server:~/.wine/drive_c/Ohjelmatiedostot/EA GAMES/Battlefield 1942$ 
```

My graphics card is integrated Intel GMA3100.

---

### Post by unicycletim on 2009-06-14
Hey,
Battlefield 1942 will not run without a cd drive- even the cracked version requires the presence of a cd drive to operate.

this is easily fixed with wine,
applications -> Wine -> Configure Wine -> Drives

then click "Add" - this will add a new drive to wine
click "Show Advanced" 
change "Type" to CD-ROM

click OK and try starting battlefield again

---

