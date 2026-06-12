---
title: "HOWTO: MythTV with Hauppauge PVR-150 on Breezy"
date: 2005-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by quietglow on 2005-11-17
The HOWTO is here: [http://www.quietglow.com/docs/ubuntumythtv.html](http://www.quietglow.com/docs/ubuntumythtv.html)

Synopsis: This document describes the process of getting a very cheap ($80 at BestBuy in the US) capture card working well with MythTV and Breezy. If you do it right, this means a PVR for less than $200 or so and no monthly fees!

HOWTO on getting the remote to work will follow just as soon as I figure it out.

Feel free to email me questions, comments and corrections!

---

### Post by arnieboy on 2005-11-18
[QUOTE=quietglow]The HOWTO is here: [http://www.quietglow.com/docs/ubuntumythtv.html](http://www.quietglow.com/docs/ubuntumythtv.html)

Synopsis: This document describes the process of getting a very cheap ($80 at BestBuy in the US) capture card working well with MythTV and Breezy. If you do it right, this means a PVR for less than $200 or so and no monthly fees!

HOWTO on getting the remote to work will follow just as soon as I figure it out.

Feel free to email me questions, comments and corrections![/QUOTE]
good job on the howto! but an immediate comment regarding the sources.list file:
thats for hoary (NOT breezy). please do make sure u change that.
it also might be a good idea to port the howto to the forums.. I know its a lot of work.. but it will make it a lot more accessible..

---

### Post by quietglow on 2005-11-22
Hey, thanks for the heads-up on the source list--I'd already modified mine so I never noticed!

I'm trying to find time to write it up as a forum Howto...will get to it eventually!

---

### Post by TimmyJ on 2005-11-23
Been waiting for this one!! :)

One question though: mythTV is more for set-top and is therefore not resize friendly or anything. Does anyone know of a TV player that can use the IVTV drivers that is more suited for watching TV in a resiable window on the desktop (so I can do other things while watching). So basically I'm looking for something with a regular media player GUI that can I can use my pvr-150 with.

thanks a lot,
Tim

---

### Post by Drain on 2005-11-23
[QUOTE=TimmyJ]Been waiting for this one!! :)

One question though: mythTV is more for set-top and is therefore not resize friendly or anything. Does anyone know of a TV player that can use the IVTV drivers that is more suited for watching TV in a resiable window on the desktop (so I can do other things while watching). So basically I'm looking for something with a regular media player GUI that can I can use my pvr-150 with.

thanks a lot,
Tim[/QUOTE]

Well, if you want to just watch some tv (and not necessarily watch recorded stuff), tvtime is a good application for that.  It's been a while since I've dug into my mythtv settings, but I thought there was somewhere in there a setting to have it run in a window, rather than full-screen.

---

### Post by quietglow on 2005-11-23
Yup, I think tvtime is the app set up for doing that. I do remember seeing a setting somewhere that would allow you to run in a window. Truthfully, though, MythTV is sort of overkill for that.

I actually used to run composite audio and video out of my cable box, into a spare DV camera and out of the camera via fire wire into my box. I'd watch Tv in Kino, which deals with DV in. So the camera essentially served as a bridge from composite to firewire. Worked well!

---

### Post by TimmyJ on 2005-11-24
Thanks for the input guys, I'll check out TV time (although a perfect solution would be able to record as well, but I suppose beggers can't be choosers). Just to clear up mythTV capabilities: I know you can run myth in a non-full screen mode, but that window is still not resizable if I recall correctly. If i'm wrong though don't hesitate to tell me, cuz that would be fantastic! :)

---

### Post by quietglow on 2005-11-25
Oooo...the thread got moved into the Howto section so now I REALLY need to update that repository list!

---

### Post by greenwom on 2005-11-25
[QUOTE=quietglow]The HOWTO is here: [http://www.quietglow.com/docs/ubuntumythtv.html](http://www.quietglow.com/docs/ubuntumythtv.html)

Synopsis: This document describes the process of getting a very cheap ($80 at BestBuy in the US) capture card working well with MythTV and Breezy. If you do it right, this means a PVR for less than $200 or so and no monthly fees!

HOWTO on getting the remote to work will follow just as soon as I figure it out.

Feel free to email me questions, comments and corrections![/QUOTE]

Few Questions!!
What are the specs of your box?  What kind of hardware are you running.  I'm looking to build a PVR and you said you had a 150.00 box + the card.  I'm currious. I have a regular capture card an old TV wonder VE  I use now for my desktop but I'd like to buy the PVR card and build a nice looking box that will run both front and back end for Myth.

I've installed all the packages in the guide (I had them installed prior to reading your guide).  When I run mythbackend and then frontend everything runs nice, but when I select watch TV I get a black screen. 

I tried your guide and when I tried to goto "localhost" in firefix I got nothing...
I tried to restart apache2, that didn't seem to work.  What should I look at next?

I also installed the plug-ins for news / web / weather.  These all work except that when I run the browser I can't really use the keyboard.  If you press M you get the Myth browser setup.  Is there a way to disable that?  If I run this at my TV I would love to use the brower for quick email checks and ebay :)

---

### Post by TimmyJ on 2005-11-25
Just a quick note on the previous suggestion to use tvtime. Unfortunately tvtime has no MPEG2 decoding and is therefore incompatible with cards that use the ivtv drivers (like my Hauppauge PVR-150) :(  Looks like i'm back to an unresizable myth (I'll live).

---

### Post by GrammatonCleric on 2005-11-25
First, thanks for the how to.  I've been wanting to build a new HTPC using Ubuntu & MytTV for sometime now.  I'm currenty using SageTV... One thing I love about SageTV is how it names the recorded shows (i.e.
Firefly-TheMessage-661201-0.mpg).   Could some one give me an example of how MythTV names the recorded shows?

Thanks,
GC

---

### Post by JazzCrazed on 2005-11-25
Hi all,

Trying to install MythTV in a freshly formatted Breezy box, but the mythtv package doesn't seem to be in the repositories! Anybody know what repositories I need to have in my sources.list?

Thanks for your help!

By the way, that howto has two "step two"s. I don't know if that's part of the humor of the article (it's a bit more obfuscating than funny, in my opinion). Otherwise, it seems like a good howto, if I can actually get past that second step two!

Thanks,
Marco

---

### Post by Mustard on 2005-11-25
[QUOTE=JazzCrazed]Hi all,

Trying to install MythTV in a freshly formatted Breezy box, but the mythtv package doesn't seem to be in the repositories! Anybody know what repositories I need to have in my sources.list?

Thanks for your help!

By the way, that howto has two "step two"s. I don't know if that's part of the humor of the article (it's a bit more obfuscating than funny, in my opinion). Otherwise, it seems like a good howto, if I can actually get past that second step two!

Thanks,
Marco[/QUOTE]


Try this link for creating a new sources.list.  ( I would avoid using the unofficial repositories that are optional in creating the sources.list)

[http://ubuntulinux.nl/source-o-matic](http://ubuntulinux.nl/source-o-matic)

---

### Post by quietglow on 2005-11-25
Thanks for the help all! I've got 6 zillion deadlines right now, but updating the howto is on my list for the weekend. Until then, use it at your own risk! 

Make sure your repositories are adjust to refer to "breezy" not "hoary" as the howto erroneously instructs now. In other words, if you're cutting and pasting that sources.list, you'll need to switch all instances of hoary with breezy.

Glad to see people getting (some!) use out of it. A couple of weeks with a myth box and I have no idea how I got along w/o it! Old episodes of x-files rock!

---

### Post by NeoFax on 2005-11-25
I am having a problem with mythfilldatabase not being able to login to mySQL via 127.0.0.1:6543.  Anyone know how to correct this?

---

### Post by Brando569 on 2005-11-25
how would i install mythtv on a box that isnt a PVR but just a everyday desktop? my dad has an Angel PCI dual tv tuner, and i dont know how to set it up. do i need specific drivers/firmware for it? also how do i figure out what video device it is? i tried /dev/video0 but it didnt work...

---

### Post by Brando569 on 2005-11-25
[QUOTE=NeoFax]I am having a problem with mythfilldatabase not being able to login to mySQL via 127.0.0.1:6543.  Anyone know how to correct this?[/QUOTE]

i had that same problem i just fixed it by running mythtv-setup as the mythtv user and make sure the password is what you set it at, mine was something completely different than what i remember setting it to. just make it easy on yourself give the user in linux and the user in mysql the same passwd thats what i did. now i just have the problem of figuring out what card(s) i have.

---

### Post by quietglow on 2005-11-25
[QUOTE=Brando569]how would i install mythtv on a box that isnt a PVR but just a everyday desktop? my dad has an Angel PCI dual tv tuner, and i dont know how to set it up. do i need specific drivers/firmware for it? also how do i figure out what video device it is? i tried /dev/video0 but it didnt work...[/QUOTE]

The cards are pretty different. The Hauppauge cards use the IVTV driver. You'd have to check to see what the Angel cards use. I know that getting a capture card working under Linux means picking one of a few cards which have have drivers (or getting lucky).

---

### Post by Brando569 on 2005-11-25
how would i find out what it uses?

---

### Post by JazzCrazed on 2005-11-26
[QUOTE=Mustard]Try this link for creating a new sources.list.  ( I would avoid using the unofficial repositories that are optional in creating the sources.list)

[http://ubuntulinux.nl/source-o-matic](http://ubuntulinux.nl/source-o-matic)[/QUOTE]

Thanks for that tip! That got me past that step.

But I still have a problem. In the very end, running *mythfrontend*, I get this error:

```
Unable to read configuration file mysql.txt
Could not open settings file /home/jazzcrazed/.mythtv/mysql.txt
```

I peeked inside ~/.mythtv, and I think a good reason I might be getting this error is because mysql.txt doesn't exist in that folder. But correct me if I'm wrong, because I often am. ;)

---

### Post by quietglow on 2005-11-26
I just did a reainstall on my home workstation (new black friday HD led to lots of organization changes!) and found a few other problems with the guide.

I just checked my .mythtv directory and there was no file by that name there either. 

Have you tried running the myfrontend as root? I.e.
```

sudo mythfrontend
```

---

### Post by JazzCrazed on 2005-11-26
That did the trick! I just figured when it instructed "and as your user run 'mythfrontend'" that that meant non-sudo... Although I guess sudo still means you're your user.

Any-hoo... That gets me into the frontend all right, but then I get this error when I try to watch TV:

> Could not connect to the master backend server -- is it running? Is the IP address set for it in the setup program correct?

I'd believe that it weren't since I don't remember setting that up...

Thanks for your help!!

---

### Post by quietglow on 2005-11-27
I've gotten that error when I've installed and not restarted after the install. Have you?

Did the "mythfilldatabase" work well (I think that also is necessary for a working backend).

---

### Post by JazzCrazed on 2005-11-27
Thanks a ton for your help, and howto, quietglow.

Yes, I did actually reboot - after the part that instructed I turn off the sound server.

I ran *sudo mythfilldatabase* again, and for the most part it seemed to work. However, at the end, I got this:

```
Connecting to backend server: localhost:6543 (try 1 of 1)
Connection timed out.
You probably should modify the Master Server settings in the setup program and set the proper IP address.
error resceduling id -1 in ScheduledRecording::signalChange
```

Gonna' run through the directions again; I'm sure I missed something!

**_EDIT:_** Yes, I *did* stupidly miss something, although it wasn't in that howto. I just ran **sudo mythbackend**, first, and that fixed everything! Now I'm able to watch TV just fine!

---

### Post by quietglow on 2005-11-27
Woo Hoo! Great news. If what you figured out was not specific to your setup, let me know what it is and I'll add it to the guide (which I'm gonna edit here in a few minutes!).

---

### Post by DDaland on 2005-11-27
Interseting- I may well give this a shot after Xmas- but have a lot of reading and research to do before I start. Thinking of going with 2 Hauppauge Low Profile PVR-150MCE cards- but have some questions- anyone with thoughts about the following- feel free to tell me.....

 Can I set this up to use a remote?
 How can I make it work with DirecTV? 
 Will my hardware handle 2 programs at the same time (either watching and recording one, or recording 2 at same time)
 My hardware (what I'm thinking of using for this project, anyway)
 AMD 1800
 PC Chips M825LU board (Built in video)
 512 MB memory (32 MB shared)
 80 GB HD
 "Book" PC slimline case

---

### Post by quietglow on 2005-11-27
I know you can set up multiple cards (two would be nice so you could watch and record different things at the same time). No clue on your hardware--I'm running a n AMD 3400+ with 1G of ram, so we're not in the same ballpark. You may be able to find some other systems online and see what they're gettin away with.

---

### Post by JazzCrazed on 2005-11-27
[QUOTE=DDaland]Interseting- I may well give this a shot after Xmas- but have a lot of reading and research to do before I start. Thinking of going with 2 Hauppauge Low Profile PVR-150MCE cards- but have some questions- anyone with thoughts about the following- feel free to tell me.....

 Can I set this up to use a remote?
 How can I make it work with DirecTV? 
 Will my hardware handle 2 programs at the same time (either watching and recording one, or recording 2 at same time)
 My hardware (what I'm thinking of using for this project, anyway)
 AMD 1800
 PC Chips M825LU board (Built in video)
 512 MB memory (32 MB shared)
 80 GB HD
 "Book" PC slimline case[/QUOTE]

Mine's sorta similar... AXP 2000+ in a Shuttle XPC (SK43G) w/1GB PC3000 SDRAM, 80GB PATA HDD. Has on-board video, but I opted for a cheapo nVidia GF4 MX440. I'm using regular KB/mouse. Don't know if I'll ever use a remote with it... Possibly, but low priority for me. Also worth noting is that although the nVidia (and the on-board) have S-VIDEO outs, I'm using an LCD monitor for the display, so I'm using RGB out.

Also, I'm using a PVR-250 rather than 150, but I don't think the differences are very significant, functionally.

I haven't tried recording anything yet (been out all day so I couldn't play with it too much).

One thing I'd like to solve is interlacing... It's *very* obvious on this LCD monitor.

Also, quietglow: the **sudo mythbackend** part wasn't in the howto.

---

### Post by emperor on 2005-11-27
[quote=GrammatonCleric]Could some one give me an example of how MythTV names the recorded shows?
Thanks,
GC[/quote] 
Exampe recorded file name:
================

1248_20051125203000_20051125210000.nuv

1248 = channel number = 248, (1248 in sql dbase)
20051125203000 = record start time
20051125210000 = record stop time

Actual name of program recorded and program description in the quide is stored in the SQL database entry; viewable when looking and selecting the program to play.

I got my MythTV backend and frontends working within the last week. Also have a MediaMVP connected to one of my TV's. Now everyone in the house can watch recorded or liveTV from their desktop, wireless laptop or on the TV.

I put the a PVR350 in my file server in my office which is my MythTV Backend. I have DirecTV and am using a serial cable connected to the low speed data port to change the changes from MythTV. I bought the PVR350 and MedaMVP directly from Hauppauge at their current special price of $219 plus $8.00 shipping.

Will be buiding a frontend/slave machine for the main room soon with an HDTV tuner card. A VGA to component video converter will be used to connect to the HDTV. It seems that the ATI Remote can be used as a remote for the front end.

---

### Post by Micro Rotors on 2005-11-28
I am thinking of using Myth TV and getting rid of my Tivo. I just picked up 2 Maxtor 300 G SATA drives and am going to do a RAID setup on my AMD 3400. Has anyone done this with the 350 version? I am getting one Wednesday and want to know if there is a big difference between the 150 V the 350.

Thanks
Bill

---

### Post by emperor on 2005-11-29
[quote=Micro Rotors] Has anyone done this with the 350 version? I am getting one Wednesday and want to know if there is a big difference between the 150 V the 350.

Thanks
Bill[/quote]

Yes, I have a 350 in my MythTV backend. Both the 150 and the 350 have a hardware MPEG-2 encoder for recording. So in that respect they are identical. However the 350 has a hardware decoder as well. The decorder can be used for playing the video back and/or as a video out to your TV directly using X and a frame buffer output.

 As a result, the CPU load is almost nothing. The only load is the activity writing/reading the hard disk during recording/playback, so, the faster the drive the better. The backend is also my file server and which only has an  AMD AthlonXP 1600 CPU but seems to handle the disk I/O at about 40+ load during recording. the drive is a Segate ATA100 160GB. Disk usage is about 1GB/30 minute record time; recording hi-res 640x480.

I found that the "ext3" file system was adaquate for my needs with file erasing in the 1 to 2 second range.

---

### Post by quietglow on 2005-11-29
And if you use the 350, you can skip the step where you copy the audio driver from the CD as well--the 350 uses the driver in the package you d/l.

My TV is my 23" display so I'm not using TV out from the card anyway--the 150 was perfect for me. The 350s ability to do output (or passthrough I suppose...right?) may work better in other situations. The onboard decoder may also help with lag. I'm not much of a channel surfer (I tend to watch what I want to  which is why I like the PVR so much) but switching between channels is pretty slow with the 150 even on my 3400+ box.

---

### Post by windexh8er on 2005-11-29
Yeah, that's fine.  If you actually go through the setup it should generate it.  If, for some reason it can't -- it's a permissions problem in that .mythtv directory.  If all else fails make sure it doesn't exist (of which you have seemed to already done), then 'touch mysql.txt' as your jazzcrazed user.  Then rerun the frontend.  Should be golden...

It's good to see quietglow redid my doc!  Was very courteous of him to ask permission before he went reposting.  Sorry for the bad humor and horrible formatting.  I would have taken the doc further but someone squat on the work I did after I posted it.

[QUOTE=JazzCrazed]Thanks for that tip! That got me past that step.

But I still have a problem. In the very end, running *mythfrontend*, I get this error:

```
Unable to read configuration file mysql.txt
Could not open settings file /home/jazzcrazed/.mythtv/mysql.txt
```

I peeked inside ~/.mythtv, and I think a good reason I might be getting this error is because mysql.txt doesn't exist in that folder. But correct me if I'm wrong, because I often am. ;)[/QUOTE]

---

### Post by windexh8er on 2005-11-29
BTW, just wanted to clear this up.  There were two high level "phases" and steps below that...  So -- yes, there were two step twos and step ones for that matter!  :)

[QUOTE=JazzCrazed]Hi all,

Trying to install MythTV in a freshly formatted Breezy box, but the mythtv package doesn't seem to be in the repositories! Anybody know what repositories I need to have in my sources.list?

Thanks for your help!

By the way, that howto has two "step two"s. I don't know if that's part of the humor of the article (it's a bit more obfuscating than funny, in my opinion). Otherwise, it seems like a good howto, if I can actually get past that second step two!

Thanks,
Marco[/QUOTE]

---

### Post by quietglow on 2005-11-29
Man, your humor rocked--especially when I had to install for the third time this weekend :-)

---

### Post by apollyonis on 2005-11-29
Any idea when the game plugin will show up in the repositories? I've been having  trouble installing from the mythplugins. Edit:Actually, I should ask if there's a Correct version of the plugin in the repositories. The one online is .17, not .18

---

### Post by JazzCrazed on 2005-11-29
[QUOTE=windexh8er]It's good to see quietglow redid my doc!  Was very courteous of him to ask permission before he went reposting.  Sorry for the bad humor and horrible formatting.  I would have taken the doc further but someone squat on the work I did after I posted it.[/QUOTE]

No, I really appreciated the humor!

The formatting maybe could have been a little better to account for my ignorance of your multiple phases. But it's no howto-killer - yours was the only one that got me to a working MythTV setup (others scared me off with kernel compiling steps).

[QUOTE=quietglow]My TV is my 23" display so I'm not using TV out from the card anyway[/QUOTE]

I'm also running straight from my video card into a monitor (19" LCD). How do you take care of interlacing in this situation? I noticed the setting in the "Playback" section of the setup menu for deinterlace, but I activated it and it didn't help at all. I'll have to double check when I get home.

Also, is there a way to automatically scan for channels? I see the option in *mythtv-setup*, but I can't actually choose it. The reason I ask is because my channel mappings are actually divergent from what Zapit has in their database for my zip code. No big deal if I can't pick this option since I can do it manually (even if I auto-scanned, I'd still have to redo the channel name information by hand).

The interlacing is definitely a bigger issue for me... But next on my plate is hooking it up with my DVD backup share on my file server (mostly XviD videos with a couple x264 encodes... hope this isn't too difficult!).

---

### Post by oblib on 2005-12-02
I just tried installing MythTV, and the frontend just shows a pretty background without any controls or buttons. I am thinking that it is a theme problem. Did anyone else have this problem? What is the default theme for Ubuntu? Mine went with G.A.N.T.

Update: Changing the theme to "blue" fixed it. GANT still won't work.

---

### Post by quietglow on 2005-12-02
[QUOTE=JazzCrazed]

I'm also running straight from my video card into a monitor (19" LCD). How do you take care of interlacing in this situation? I noticed the setting in the "Playback" section of the setup menu for deinterlace, but I activated it and it didn't help at all. I'll have to double check when I get home.
[/QUOTE]

I don't notice the interlacing problems really: I tend to watch TV while sitting 15 feet away or so. If you discover a solution let me know and I'll throw it in the guide.


>  Also, is there a way to automatically scan for channels? I see the option in *mythtv-setup*, but I can't actually choose it. The reason I ask is because my channel mappings are actually divergent from what Zapit has in their database for my zip code. No big deal if I can't pick this option since I can do it manually (even if I auto-scanned, I'd still have to redo the channel name information by hand).

I have problems with this too. I know you can actually manually make changes to your setup, but mine is close enough that I haven't bothered. The Myth people actually suggest calling zap2it to point out the errors! I keep expecting them to pull the whole support in general so I've avoided doing that thusfar :-)

---

### Post by quietglow on 2005-12-02
[QUOTE=oblib]I just tried installing MythTV, and the frontend just shows a pretty background without any controls or buttons. I am thinking that it is a theme problem. Did anyone else have this problem? What is the default theme for Ubuntu? Mine went with G.A.N.T.[/QUOTE]


That sounds like an install problem. I think GANT is the default, and it works fine on my system. Did you get any other errors upon installing?

---

### Post by JazzCrazed on 2005-12-02
[QUOTE=quietglow]I don't notice the interlacing problems really: I tend to watch TV while sitting 15 feet away or so. If you discover a solution let me know and I'll throw it in the guide.[/QUOTE]

Actually, I stupidly *didn't* have the "deinterlace" option checked. The option is under "Playback" underneath some hierarchy of the setup menu. It turns out that you have to make sure to hit every page of the "Playback" options and hit the "Finish" button after it's all said and done. Deinterlace was on the first page, so I just checked it and "Escape"d out of it, which apparently cancels anything I did. So that solves that!

[QUOTE=quietglow]The Myth people actually suggest calling zap2it to point out the errors![/QUOTE]

It turns out that my Myth-using friend also suggested I ask zap2it to incorporate my specific mappings. I just figured I was too small a fry to make it worthwhile - I'm on the "less-than-basic" cable plan that comes for free with my internet connection. But I guess based on my and your friends' recommendations, zap2it is pretty receptive of user input - even MythTV user input.

---

### Post by quietglow on 2005-12-02
[QUOTE=JazzCrazed]But I guess based on my and your friends' recommendations, zap2it is pretty receptive of user input - even MythTV user input.[/QUOTE]

You know, I suppose you're right about this, but I'm still kind of bothered by the whole zap2it setup. What incentive to they have to handing out this info? I just got an account with them using the MythTV code that is on the Myth homepage somewhere. So they are providing the fuel for my PVR, but I wonder what it is they get out of it? One of my friend's suggested it is something like the CDDB service (which is also a private entity). The difference is, fo course, we are getting a whole lot more raw info from zap2it than the few lines of text which identifies a CD. Hmmm...

---

### Post by thechitowncubs on 2005-12-04
[QUOTE=quietglow]The HOWTO is here: [http://www.quietglow.com/docs/ubuntumythtv.html](http://www.quietglow.com/docs/ubuntumythtv.html)

Synopsis: This document describes the process of getting a very cheap ($80 at BestBuy in the US) capture card working well with MythTV and Breezy. If you do it right, this means a PVR for less than $200 or so and no monthly fees!

HOWTO on getting the remote to work will follow just as soon as I figure it out.

Feel free to email me questions, comments and corrections![/QUOTE]
illinois power.

---

### Post by quietglow on 2005-12-04
word.

---

### Post by stargurl on 2005-12-04
I don't seem to have HcwMakoA.ROM on my CD, only HcwMakoB.ROM and HcwMakoC.ROM. Do I use one of these, or where can I get HcwMakoA.ROM?

---

### Post by quietglow on 2005-12-04
And you're using a 150 model? (any of the others won't have it). Let me know and I can probably just send it to you (its small).

---

### Post by stargurl on 2005-12-04
Yeah, a 150... just bought it this week. I'd love if you could send it my way.

---

### Post by Micro Rotors on 2005-12-06
Has anyone installed this from this write up? I see so many errors and have to modify the code a little here and there, and it still wont install. Aghrrrrrr. I have tried 3 times!:confused:

---

### Post by quietglow on 2005-12-07
**I've finally gotten around to updating today 7th of Dec. Please keep the observations coming and I'll edit as time permits.**

(Yeah, I've gotten a few emails regarding people installing via these directions. If you post some specifics about what you're having problems with I'm sure someone will offer some help!)

---

### Post by Micro Rotors on 2005-12-07
[QUOTE=quietglow]**I've finally gotten around to updating today 7th of Dec. Please keep the observations coming and I'll edit as time permits.**

(Yeah, I've gotten a few emails regarding people installing via these directions. If you post some specifics about what you're having problems with I'm sure someone will offer some help!)[/QUOTE]


Hmmmmm,, Ok here just a few.

[http://www.ubuntuforums.org/showthread.php?t=100353]("http://www.ubuntuforums.org/showthread.php?t=100353")

---

### Post by quietglow on 2005-12-08
[B]Updated page Dec 8 to add:

warning about how difficult this is
warning about using IE to view the page
added link to download the audio driver from my CD (no clue why its not on them all)

Enjoy![/B]

---

### Post by Sn1pe on 2005-12-08
For some reason it's cutting off your webpage right after the IVTV instructions.

---

### Post by quietglow on 2005-12-08
Thanks! I don't know what the issue was but I just put it back together.

---

### Post by daller on 2005-12-16
Installing the needed packages went fine!

```

sudo apt-get install apache2
sudo apt-get install mysql-server
sudo apt-get install phpmyadmin

```

But when running mythtv-setup, I get this:

```
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

``` - Multiple times!

Entering phpmyadmin and logging in with mythtv:mythtv isn't allowed. (As the setup-app is logging in with...)

How do I solve this?

---

### Post by daller on 2005-12-16
Got around the issue by using root:<PASSWORD>!!!

But now I'm stuck with the backend:

```

Could not connect to the master backend server -- is it running?
Is the IP address set for it in the setup program correct?

```

I found the settings:

```

Master server IP address: 127.0.0.1
Port the master server runs on: 6543

```

Trying to start the backend:

```

nikoline@ubuntu:~$ sudo mythbackend
2005-12-16 14:20:22.793 New DB connection, total: 1
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.

```

Trying to start the frontend, confirms this:

```

nikoline@ubuntu:~$ sudo mythfrontend
2005-12-16 14:29:34.199 New DB connection, total: 1
Total desktop width=1024, height=768, numscreens=1
2005-12-16 14:29:34.260 Using screen 0, 1024x768 at 0,0
2005-12-16 14:29:34.318 mythfrontend version: 0.18.1.20050510-1 www.mythtv.org
2005-12-16 14:29:34.320 Enabled verbose msgs : important general
2005-12-16 14:29:35.369 Switching to square mode (blue)
mythtv: could not connect to socket
mythtv: Ingen sådan fil eller filkatalog
lirc_init failed for mythtv, see preceding messages
2005-12-16 14:29:37.256 Joystick disabled.
2005-12-16 14:29:37.550 Registering Internal as a media playback plugin.
2005-12-16 14:29:48.678 New DB connection, total: 2
2005-12-16 14:29:48.891 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
Connection timed out.
You probably should modify the Master Server settings
in the setup program and set the proper IP address.
2005-12-16 14:29:49.650 Changing from None to None
2005-12-16 14:29:50.245 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
Connection timed out.
You probably should modify the Master Server settings
in the setup program and set the proper IP address.
2005-12-16 14:29:52.018 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
Connection timed out.
You probably should modify the Master Server settings
in the setup program and set the proper IP address.


```

---

### Post by emperor on 2005-12-16
Start the backend with the verbose on as follows:

mythbackend -v

or

mythbackend -v all

You can write the output to a file by putting  ">mythtv.log" at the end of either of the above.

Your problem may be an my-sql database user/password problem, see:
[http://www.abarbaccia.com/content/view/17/32/](http://www.abarbaccia.com/content/view/17/32/)

other helpful guides:
[http://www.abarbaccia.com]("http://www.abarbaccia.com/content/view/17/32/")
[http://wilsonet.com/mythtv/fcmyth.php]("http://wilsonet.com/mythtv/fcmyth.php")

Mythtv forums: (very helpful!)
[http://www.gossamer-threads.com/lists/mythtv/]("http://www.gossamer-threads.com/lists/mythtv/")

---

### Post by krusk on 2005-12-18
I think you should mention that Zap2It only works for people in USA and Canada. Took some time for me to figure out, but europeans have to use xmltv. (Unless there is an european alternative to Zap2It, which i'm not aware of)

---

### Post by rude on 2005-12-18
I'm having a small problem setting up my first mythtv box.
Everything has worked fine (I think) up to this point in the howto.
In Phase Two, Step One -IVTV
------------------------------------
Now:

cd /usr/src

sudo mv ~/ivtv-0.4.0.tar.gz ./
-------------------------------------
When I type that last command I get this error --> mv: cannot stat /home/myname/ivtv-0.4.0.tar.gz : No such file or directory

I tried looking in the man mv page and I couldn't figure out what I'm doing wrong. (Thanks for helping out a noob who needs a mythtv box really bad.)

---

### Post by emperor on 2005-12-19
[quote=rude]I'm having a small problem setting up my first mythtv box.
Everything has worked fine (I think) up to this point in the howto.
In Phase Two, Step One -IVTV
------------------------------------
Now:

cd /usr/src

sudo mv ~/ivtv-0.4.0.tar.gz ./
-------------------------------------/quote]

The final forward slash is incorrect; just the '.' is required. The following will move the "ivtv-0.4.0.tar.gz" file to "/usr/src", the current directory after the "cd" command:

sudo mv ~/ivtv-0.4.0.tar.gz .

---

### Post by rude on 2005-12-19
Thanks for the help. I've taken the final forward slash and typed

sudo mv ~/ivtv-0.4.0.tar.gz .

and I still get the same error. :(  So I did the windoz thing (I used my mouse) and right-clicked the file (I had it on the Desktop) to untar it. It seemed to work. 

Thanks again for the help.

---

### Post by emperor on 2005-12-19
[quote=rude]Thanks for the help. I've taken the final forward slash and typed

sudo mv ~/ivtv-0.4.0.tar.gz .

and I still get the same error. :( So I did the windoz thing (I used my mouse) and right-clicked the file (I had it on the Desktop) to untar it. It seemed to work. 

Thanks again for the help.[/quote] 
Then "ivtv-0.4.0.tar.gz" was not in "/home/yourname" directory. It was in "/home/yourname/Desktop" directory. That's why the "mv" failed.

The creator of the install guide prefers to install the source files to "/usr/src". You can untar and do the 3 step in your home directory if you want to. However, the Desktop directory is not a good choice. I generally create  a  download directory under /home/myname/  (/home/myname/download).

---

### Post by rude on 2005-12-20
Thanks emperor for the help. I just couldn't figure out what I did wrong and I was thinking about it over and over all day at work. Now it makes it sense. I 'll  but sure and make the right changes. Thanks again.

---

### Post by smit0737 on 2006-01-04
I get the following after the make install:

v4l-cx2341x-init-mpeg.bin needs copying to the hotplug firmware
directory if needed for PVR350 mpeg initialization

Then after dmesg, I see the following:

[4294694.353000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[4294694.353000] ivtv0: did you put the firmware in the hotplug firmware directo ry?
[4294694.353000] ivtv0 warning: failed loading encoder firmware
[4294694.353000] ivtv0 warning: Error loading firmware -3!
[4294694.353000] ivtv0: Error -3 initializing firmware.
[4294694.387000] ivtv0: Error -12 on initialization
[4294694.387000] ivtv: probe of 0000:00:09.0 failed with error -12
[4294694.387000] ivtv:  ====================  END INIT IVTV  =================== 

Can anyone inform this newbie as to what/where the "hotplug firmware directory" is?  Also, I don't see the files v4l-cx2341x-init-mpeg.bin or v4l-cx2341x-enc.fw in my /usr/src/ivtv-0.4.1/driver/ directory.  Where do I look for this?

System info: 2200 Celeron, 512k RAM, PVR-150MCE, nVidia 5200, 120GB and 80GB IDE drives

Thanks in advance for any help.

---

### Post by emperor on 2006-01-05
[quote=smit0737]I 

Can anyone inform this newbie as to what/where the "hotplug firmware directory" is? Also, I don't see the files v4l-cx2341x-init-mpeg.bin or v4l-cx2341x-enc.fw in my /usr/src/ivtv-0.4.1/driver/ directory. Where do I look for this?

[/quote] 
/lib/hotplug/firmware

firmware:
[http://ivtvdriver.org/index.php/Firmware](http://ivtvdriver.org/index.php/Firmware)

---

### Post by Prefader on 2006-01-07
First, a HUGE thank you for this howto, it worked almost perfectly.  I do have one issue, though . . .

I can only view 2 channels, the rest are all snow.  I'm relatively sure this is a tuning problem, but I can't seem to work around it.

I'm using a PVR-350, and dmesg shows that it's got tuner type 47 . . . apparently, there were some problems with this tuner and older v4l drivers . . . everything I've read says they were resolved in kernel 2.6.10, though.

Any thoughts?

---

### Post by emperor on 2006-01-09
You might try the latest driver and instructions from here:
[http://ivtvdriver.org/index.php/Howto:Ubuntu](http://ivtvdriver.org/index.php/Howto:Ubuntu)

Also, make sure that the correct firmware is being loaded.

---

### Post by majkmil on 2006-01-09
I went through setup and got the guide but when I run mythfrontend I get a cant connect to X server error. Any Ideas.

---

### Post by emperor on 2006-01-09
Are you running mythfrontend on the same machine?

---

### Post by Prefader on 2006-01-09
[QUOTE=emperor]You might try the latest driver and instructions from here:
[http://ivtvdriver.org/index.php/Howto:Ubuntu](http://ivtvdriver.org/index.php/Howto:Ubuntu)

Also, make sure that the correct firmware is being loaded.[/QUOTE]

The instructions I followed don't match those verbatim, but more or less match.

I'm using driver version 0.4.1 and firmware version 1.18.21.22254 as recommended on [this]("http://ivtv.writeme.ch/tiki-index.php?page=FirmwareVersions") page.  Everything loads w/o errors.  After tinkering for a while I did find that I could fine tune stations, but this is unbelievably cumbersome, as I can't SEE what I'm tuning.  Or is there a way that I'm not aware of?

---

### Post by emperor on 2006-01-09
[quote=Prefader]After tinkering for a while I did find that I could fine tune stations, but this is unbelievably cumbersome, as I can't SEE what I'm tuning. Or is there a way that I'm not aware of?[/quote]

The "finetune" field in the database is exposed in the web interface which is much easier to edit than the database directly.

---

### Post by evuraan on 2006-01-19
I've made it work with PVR 150 -- works like a charm. 

Question: Is there a way to use the Remote Control that came along with PVR 150? Right now, I've to use the keyboard to navigate .

---

### Post by dhyams on 2006-01-19
[QUOTE=evuraan]I've made it work with PVR 150 -- works like a charm. 

Question: Is there a way to use the Remote Control that came along with PVR 150? Right now, I've to use the keyboard to navigate .[/QUOTE]

Check out the LIRC section here:

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

---

### Post by quietglow on 2006-01-23
Okay, I spent yesterday doing three (3!!) seperate installs of MythTV--the story is long and boring so I'll refrain from inflicting it on you. Despite the warning, I think you may be able to do a straight cut-and-paste from the HOWTO at this point, assuming you use the versions of the drivers that I did.

I did the install the second two times from the html of my HOWTO while it was open in an editor. This allowed me to fix most of errors and add notes as needed. Lots of changes and I didn't start a changelog at the beginning, so lets just say its better now, okay?

The big news for me, though, was that Myth has apparently dissapeared from the standard repositories (notes made in the HOWTO)! I hunted around a bit and found that the package maintainer can't keep them up any longer. I sure to hope someone picks that up! I'm reading up on deb package creation in case they really are looking for someone to keep it going.

Enjoy all.

---

### Post by arjay1 on 2006-01-23
quietglow

First, thanks for all the work you have done on the howto.  It got me further than knoppmyth (config probs) and Fedora FC4 (brilliant distro but dreadful repos) - hence my trying ubuntu!

However, I have hit a snag well into the config of mythtv.  When I run mythfilldatabase I just get error messages - 
```
richard@ubuntu:~$ mythfilldatabase
2006-01-23 20:19:42.790 New DB connection, total: 1
2006-01-23 20:19:42.811 Unable to connect to database!
2006-01-23 20:19:42.811 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.3' (111)

2006-01-23 20:19:42.823 Failed to init MythContext, exiting.
richard@ubuntu:~$
richard@ubuntu:~$ sudo mythfilldatabase
2006-01-23 20:20:22.010 New DB connection, total: 1
2006-01-23 20:20:22.030 Unable to connect to database!
2006-01-23 20:20:22.031 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.3' (111)

2006-01-23 20:20:22.042 Failed to init MythContext, exiting.

```

You can see that I have tried as me as the user - richard -  and also as sudo.  My ip address for this computer is 192.168.1.3  and i have used it throughout in all the setup screens (replacing the local loop 127.0.0.1).

Can you offer anything to try?  I have followed your wiki religiously (at least 2 complete re-installs and endless reboots).  I note that you say you have recently reworked your howto (today?), but if it is the link in your signature, I can't find anything very different.  It is a bit disconcerting to hear that you had to re-install and reboot endlessly too - and you are the expert:D   

It would help if you updated to cover ivtv .41 or whatever as the firmware file is quite different (if memory serves me right it i0s now a *.inf.zipfile - it could be very confusing for us newbies!!  

Of course the best thing of all would be screenshots for each stage but I guess that is really shooting for the moon.  Now what is this about under-priviledged kids and schools and what have you?  There are real fat middle-class white males out here that need help ;) 

I am running Breezy, with a pvr150, but trying to get it set up for the UK and a sky satellite box (not USA and Zappit).  I have tried to follow a couple of guides for sky  and/or digital boxes but they are gooblydegook as far as I am concerned.

Regards

Richard

---

### Post by quietglow on 2006-01-23
First of all Richard, you're gonna be able to do this. It worked on my box, with the same card, so its gonna work on yours too. The reason I had to install 4 times has to do with me a. stopping in the middle of doing the install to go tend to other things and b. drinking beer while doing it. Its mostly b.

> My ip address for this computer is 192.168.1.3 and i have used it throughout in all the setup screens (replacing the local loop 127.0.0.1)

No, the guide is vague there, but you want to leave the local address which is default. You want the backend looking for the one and only database you have running. 

The current firmware is called pvr48wdm_1.8.22037.exe (just as the guide indicates). If you're using something else, that isn't it. It is marked with a *** and not a **** by the way :-) You're a new guy so I'll spare you the RTFM. Okay, I suppose I didn't spare you.

> Of course the best thing of all would be screenshots for each stage but I guess that is really shooting for the moon. Now what is this about under-priviledged kids and schools and what have you? There are real fat middle-class white males out here that need help


No this is a great suggestion, and I think for the next install (probably when dapper comes out) I'll do screenshots too. 

There were quite a few updates that I made so make sure to refresh the page: especially important is the one which indicates that you'll have to use a specialized sources.list file since it looks like Myth is out of the repos for the time-being. 

Remember, if it worked on my machine, its gonna work on yours too.

---

### Post by Dromio on 2006-01-24
Thank you very much for your work on putting together a simple guide.  It's good too see others have already gone through this all.

I'm having trouble installing ivtv to work with a PVR 150MCE card.  I've gone through a lot of attempts, and now when I "modprobe ivtv", dmesg shows a lot of errors:

> 
[4295324.864000] cx88xx: disagrees about version of symbol tveeprom_hauppauge_analog
[4295324.864000] cx88xx: Unknown symbol tveeprom_hauppauge_analog
[4295324.866000] cx8800: Unknown symbol cx88_reset
[4295324.866000] cx8800: Unknown symbol cx88_call_i2c_clients
[4295324.866000] cx8800: Unknown symbol cx88_wakeup
[4295324.866000] cx8800: Unknown symbol cx88_risc_stopper
[4295324.866000] cx8800: Unknown symbol cx88_print_irqbits
[4295324.866000] cx8800: Unknown symbol cx88_set_scale
[4295324.866000] cx8800: Unknown symbol cx88_shutdown
[4295324.867000] cx8800: Unknown symbol cx88_vdev_init
[4295324.867000] cx8800: Unknown symbol cx88_core_put
[4295324.867000] cx8800: Unknown symbol cx88_audio_thread
[4295324.867000] cx8800: Unknown symbol cx88_core_irq
[4295324.867000] cx8800: Unknown symbol cx88_core_get
[4295324.867000] cx8800: Unknown symbol cx88_get_stereo
[4295324.867000] cx8800: Unknown symbol cx88_set_tvnorm
[4295324.867000] cx8800: Unknown symbol cx88_vid_irqs
[4295324.867000] cx8800: Unknown symbol cx88_risc_buffer
[4295324.867000] cx8800: Unknown symbol cx88_set_stereo
[4295324.868000] cx8800: Unknown symbol cx88_sram_channels
[4295324.868000] cx8800: Unknown symbol cx88_set_tvaudio
[4295324.868000] cx8800: Unknown symbol cx88_sram_channel_dump
[4295324.868000] cx8800: Unknown symbol cx88_sram_channel_setup
[4295324.868000] cx8800: Unknown symbol cx88_print_ioctl
[4295324.868000] cx8800: Unknown symbol cx88_free_buffer
[4295324.868000] cx8800: Unknown symbol cx88_boards
[4295324.868000] cx8800: Unknown symbol cx88_newstation
[4295325.186000] cx88xx: disagrees about version of symbol tveeprom_hauppauge_analog
[4295325.186000] cx88xx: Unknown symbol tveeprom_hauppauge_analog
[4295325.187000] cx8802: Unknown symbol cx88_reset
[4295325.187000] cx8802: Unknown symbol cx88_wakeup
[4295325.188000] cx8802: Unknown symbol cx88_risc_stopper
[4295325.188000] cx8802: Unknown symbol cx88_print_irqbits
[4295325.188000] cx8802: Unknown symbol cx88_shutdown
[4295325.188000] cx8802: Unknown symbol cx88_mpeg_irqs
[4295325.188000] cx8802: Unknown symbol cx88_core_irq
[4295325.188000] cx8802: Unknown symbol cx88_sram_channels
[4295325.188000] cx8802: Unknown symbol cx88_sram_channel_dump
[4295325.188000] cx8802: Unknown symbol cx88_sram_channel_setup
[4295325.188000] cx8802: Unknown symbol cx88_free_buffer
[4295325.188000] cx8802: Unknown symbol cx88_boards
[4295325.188000] cx8802: Unknown symbol cx88_risc_databuffer
[4295325.191000] cx88_dvb: Unknown symbol cx8802_fini_common
[4295325.191000] cx88_dvb: Unknown symbol cx88_core_put
[4295325.191000] cx88_dvb: Unknown symbol cx88_core_get
[4295325.191000] cx88_dvb: Unknown symbol cx8802_resume_common
[4295325.191000] cx88_dvb: Unknown symbol cx8802_buf_prepare
[4295325.191000] cx88_dvb: Unknown symbol cx8802_init_common
[4295325.191000] cx88_dvb: Unknown symbol cx88_free_buffer
[4295325.191000] cx88_dvb: Unknown symbol cx88_boards
[4295325.192000] cx88_dvb: Unknown symbol cx8802_buf_queue
[4295325.192000] cx88_dvb: Unknown symbol cx8802_suspend_common
[4295325.321000] cx88xx: disagrees about version of symbol tveeprom_hauppauge_analog
[4295325.321000] cx88xx: Unknown symbol tveeprom_hauppauge_analog
[4295325.323000] cx8802: Unknown symbol cx88_reset
[4295325.323000] cx8802: Unknown symbol cx88_wakeup
[4295325.323000] cx8802: Unknown symbol cx88_risc_stopper
[4295325.323000] cx8802: Unknown symbol cx88_print_irqbits
[4295325.323000] cx8802: Unknown symbol cx88_shutdown
[4295325.323000] cx8802: Unknown symbol cx88_mpeg_irqs
[4295325.324000] cx8802: Unknown symbol cx88_core_irq
[4295325.324000] cx8802: Unknown symbol cx88_sram_channels
[4295325.324000] cx8802: Unknown symbol cx88_sram_channel_dump
[4295325.324000] cx8802: Unknown symbol cx88_sram_channel_setup
[4295325.324000] cx8802: Unknown symbol cx88_free_buffer
[4295325.324000] cx8802: Unknown symbol cx88_boards
[4295325.324000] cx8802: Unknown symbol cx88_risc_databuffer
[4295325.327000] cx88_blackbird: Unknown symbol cx8802_fini_common
[4295325.327000] cx88_blackbird: Unknown symbol cx88_set_scale
[4295325.327000] cx88_blackbird: Unknown symbol cx88_vdev_init
[4295325.327000] cx88_blackbird: Unknown symbol cx88_core_put
[4295325.327000] cx88_blackbird: Unknown symbol cx88_core_get
[4295325.327000] cx88_blackbird: Unknown symbol cx8802_resume_common
[4295325.327000] cx88_blackbird: Unknown symbol cx8802_buf_prepare
[4295325.327000] cx88_blackbird: Unknown symbol cx8802_init_common
[4295325.328000] cx88_blackbird: Unknown symbol cx88_print_ioctl
[4295325.328000] cx88_blackbird: Unknown symbol cx88_free_buffer
[4295325.328000] cx88_blackbird: Unknown symbol cx88_boards
[4295325.328000] cx88_blackbird: Unknown symbol cx8802_buf_queue
[4295325.328000] cx88_blackbird: Unknown symbol cx8802_suspend_common


Does anyone recognize this?  Any ideas how to get by it?  My last attempted install was using the exact files and versions listed in the guide.

---

### Post by evuraan on 2006-01-24
[QUOTE=dhyams]Check out the LIRC section here:

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)[/QUOTE]

Thank you, that does it. I've got it working, and we love it. 

Quick question: It skips the commercials during playbacks, but is there an option to have it skip the advts when shows are recorded? IOW, if we [copy ]("http://www.mythtv.info/moin.cgi/ArchiveRecordingsToDvdHowTo")the .nuv file to a DVD, the ads go along with it. 

Was wondering is there an option to have recordings removed of any ads.. 

Thanks in advance..!!

---

### Post by arjay1 on 2006-01-25
quietglow - thanks for the tip re leaving the ip address as the default.  I'll give that a try.


As to your second point: Actually, I **did** RTFM a good few times - but maybe I am just thick.  You see your guide says to download the latest files - in this case version 0.42 - which I did.  

However,  your instruction to then download the pvr48wdm_1.8.22037.exe file directly contradicts the advice on the ivtv firmware page.  That page says the relevant files are:

pvr48wdm_1.8.22037.exe*** and	
pvr_1.18.21.22254_inf.zip****	

 but the page then says:


*** This is the version of firmware (encoder revision 0x02040011) recommended for use with ivtv **before 0.3.9**. 

**** This is the version of firmware (encoder revision 0x02050032) recommended for use **with ivtv 0.3.9 and later**.

Give me another rollicking if I am wrong but that suggests that I used the correct file - one marked with ****.

Of course, you might be right and I should still have used the "old" file you recommend.  But if so, should you not point out in your guide that we should ignore the ivtv instruction?

In the spirit of spirited debate ;) 

Regards

Richard

---

### Post by quietglow on 2006-01-25
> However, your instruction to then download the pvr48wdm_1.8.22037.exe file directly contradicts the advice on the ivtv firmware page.

LOL! Okay Richard, who's directions are you following, theirs or mine :-)

In an ideal world, I'd do quite a few things differently (correcting spelling etc. for starters). So if your point is that I could improve the guide, your point is taken--I noticed the erroneous note on the IVTV site this past time. The greatest feature of linux is its most damning I think: endless choice on how to do things is both freeing and bewildering. I'm sure you probably can get an install to work with the newer firmware, but not the way I've done it.

Let us know when its workin'!

---

### Post by arjay1 on 2006-01-25
OK quietglow - I'll call it a draw if you will. :D 

I'm gonna go back and do a re-install and this time follow YOUR guide hee hee.

I know I still won't get the final bit done because no one has ever come back to me with a decent guide for an installation using the UK's SKY digital settop box.  But if I can get to the stage of an install of mythtv to the point that I have the "6 ringed circus" up on the screen - I'll be happy for now.

Keep up the good work.

RJ

BTW fo you think it should be RMFM (my) not RTFM (the) ?:p

---

### Post by quietglow on 2006-01-25
> BTW fo you think it should be RMFM (my) not RTFM (the) ?


Hey, thats super-catchy! 

I know this is asking a whole bunch, but if you feel like it, document the process of getting SKY working--I've heard it really is a pain in the arse. If you get things functional, I'd be more than happy to include it on the HOWTO page. I would also then have someone else to blame any and all mistakes upon LOL! :-) 

RMFM...excellent.

---

### Post by arjay1 on 2006-01-26
Well Quietglow.

This time I followed your howto religiously.  Still didnt get very far.   I am running the 2.6.9 kernel and I notocied that the apt-get upgrade did not upgrade the kernel - presumably that is right.  Anyway, I downloaded the kernel headers as per apt-get install linux-headers-386, but when I got to "make" in driver,  I just got:

```
root@ubuntu:/usr/src/ivtv-0.4.2# cd driver
root@ubuntu:/usr/src/ivtv-0.4.2/driver# make
make -C /lib/modules/2.6.12-9-386/build M=/usr/src/ivtv-0.4.2/driver modules
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
make: *** [all] Error 2

```

I checked the /lib/modules directory and this is what I got:
```
root@ubuntu:/usr/src/ivtv-0.4.2/driver# ls /lib/modules
2.6.12-10-386  2.6.12-9-386  HcwMakoA.ROM  ivtv-fw-dec.bin  ivtv-fw-enc.bin
root@ubuntu:/usr/src/ivtv-0.4.2/driver# find / -name build
/lib/modules/2.6.12-10-386/build
```

It seems as if the make instruction is looking for a build file in 2.6.10 not 2.6.9?

Should I have upgrade the kernel, and if so how do I do that?

If not where should I go from here?  I noticed that at no time in your howto do you say we should reboot - e.g. for  a new kernel

Richard

---

### Post by smit0737 on 2006-05-01
quietglow - Thanks for your committment to helping others get their systems up and running.  I had to put mine on hold for a couple of months and am finally able to work on it again.

I'm working through the instructions to get ivtv running and am seeing errors.  I've added "ivtv" to my /etc/modules file, copied the /lib/modules/2.6.12/ivtv directory contents to the /lib/modules/2.6.12-10-386/kernel/drivers/media/video directory, run "sudo depmod" and "sudo modprobe ivtv", but the output stream is as follows:

brian@mythtvbox:/lib/modules/2.6.12/ivtv$ sudo dmesg
setkeycodes 68 <keycode>' to make it known.
[4320828.844000] atkbd.c: Unknown key released (translated set 2, code 0x65 on isa0060/serio0).
[4320828.844000] atkbd.c: Use 'setkeycodes 65 <keycode>' to make it known.
[4320882.121000] atkbd.c: Unknown key released (translated set 2, code 0xe1 on isa0060/serio0).
[4320882.121000] atkbd.c: Use 'setkeycodes e061 <keycode>' to make it known.
[4320882.124000] atkbd.c: Unknown key pressed (translated set 2, code 0x68 on isa0060/serio0).
[4320882.124000] atkbd.c: Use 'setkeycodes 68 <keycode>' to make it known.
[4320882.126000] atkbd.c: Unknown key released (translated set 2, code 0x65 on isa0060/serio0).

..... so and and so forth until the end of the output stream below .......

[4407314.906000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4407315.132000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4407315.132000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4407315.344000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4407315.344000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4407315.495000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4407315.495000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

What does this mean and what should I do to address it?  Thanks for all of the help posted here.  I appreciate it!

---

