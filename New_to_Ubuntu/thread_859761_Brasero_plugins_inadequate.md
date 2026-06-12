---
title: "Brasero plugins inadequate"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by philk949 on 2008-07-14
Hi,
When I try to use the Brasero disc burning facility, I am informed that I cannot do so with the current set of plugins. I tried to download some current plugins from the net, but no luck.
Any suggestions, please?
Thanks,
philk949

---

### Post by ChameleonDave on 2008-07-14
I have no experience of Brasero myself, so I can only suggest that you try out K3B, available in the repositories.

---

### Post by cariboo on 2008-07-14
Which  version of Ubuntu are you using and it would help if you could show us the error message so that we can help you resolve this problem.

Jim

---

### Post by philk949 on 2008-07-14
Thanks for the reply Jim. I'm using Hardy Heron 8.04 and have attached a screenshot of the error message. In case it doesn't translate too well, it reads:
"The medium is not writable with the current set of plugins"

Phil

---

### Post by philk949 on 2008-07-15
Thanks Dave,
I do in fact prefer K3b but went on to Brasero when my K3b application persistently told me that I had no media inserted in the drive (I hate that). Could be a hardware problem - I'll keep tinkering.

Phil

---

### Post by kendallben on 2008-09-05
I get the same error, It worked for a long time, I think it has something to do with a update of something because it happened right after i installed some updates.

---

### Post by phorgan1 on 2008-09-12
The same with me--I wonder if it's related to the problem of no removable media automounting anymore?  I filed a bug about that after seeing a lot of complaints on the net but no bug filed and the only reply was to go to the debugging page for removable media and provide those reports, which I had already done and provided when I wrote the bug.  The bugs marked as needing more information although it was provided when I wrote it and I imagine after awhile they'll close it because I haven't provided the information I've already provided which is clearly there when you look at the bug!!!!  Astonishing, no?  Also, I and many others can't run openoffice anymore and they just say to install Sun's version instead of the Ubuntu version.  :confused: 
Unfortunately I need to burn a data DVD for someone today, so I'll got look for something else that might work.

Patrick

---

### Post by djdarkside on 2008-11-08
Was this ever solved because I have the same error message using Brasero under Hardy.

---

### Post by daone on 2008-11-08
me to

anyone else have ideas as to how to fix this?

---

### Post by mgibeault on 2008-11-08
Me too!
I'd like to copy a DVD onto a DVD+R DL but Brasero says it can't with the current plug-ins.

---

### Post by odduck on 2008-11-20
ditto, i'm having this problem as well.

---

### Post by perixx on 2009-01-17
The problem remains persistent.

It's 8.5GB DVD+R DL media here. Xfburn won't work either and newer versions of Brasero, > 8.x won't compile. K3B would spoil my XFCE-desktop, I'm afraid.


perixx

---

### Post by rf277 on 2009-04-07
hey i'm using ibex and it keeps telling me that it can't burn because the dvd isn't compatible and it can't do it with my current set of plugins i'm trying to use memorex 16x 4.7gb 120min dvd-r's because i got some videos from youtube out of my cache folder and i'd like to burn them to a dvd so my friends and i can watch them on the bigger tv or take them to their houses and stuff, any help at all would be great i don't know a whole lot about dvd burning and stuff

oh yea and i already tried k3b but it won't burn a video dvd just a data video disc or like if you could show me how to use this program i found called todisc that would help too thanks a lot!

---

### Post by Sam Lars on 2009-04-12
I'm using Jaunty right now and have the same problem... I can totally see why they made Brasero default... :-k
I used Devede to make an iso... haven't tried burning it.  I guess that works, but that doesn't really solve the problem...

---

### Post by gallonallen on 2009-05-01
I also have been having trouble with this.  I have inserted several different brands of DVD-R and DVD+R.  They are all similar in that the software seems to think that they are 8 GB discs when they are the smaller 4 GB discs.  I don't know if that helps but if it does I hope it makes everyone as happy as me to have my burner back!

---

### Post by perixx on 2009-05-11
Maybe I'm wrong, or this specific problem isn't related to the matter, but have a look at this:

[http://cdrecord.berlios.de/old/private/linux-dist.html](http://cdrecord.berlios.de/old/private/linux-dist.html)

The mentioned method to verify whether the broken debian-cdrecord tool is installed, suggests, that Ubuntu is shipped with the crippled version as well.

I'm going to remove and replace it by a freshly compiled cdrecord version and see what happens.


EDIT:
Although it still might be worth trying the original cdrecord tool, I'd rather not advise springing into action just for fun; counterstatements to the one above, as well as the missing GPL lincense.
The smake build system can be downloaded here, anyway (ftp password and user: anonymous):
[ftp://ftp.berlios.de/pub/smake/alpha/smake-1.2a41.tar.bz2](ftp://ftp.berlios.de/pub/smake/alpha/smake-1.2a41.tar.bz2)


perixx

---

### Post by Rody on 2009-09-20
I am having this issue on 9.10 karmic and 9.04. it is very strange. I have to boot into windows to burn some dvd's.

rody

---

### Post by RedSingularity on 2009-10-16
Same here.  Anyone have a solution?

---

### Post by Bramkaandorp on 2009-10-24
I have the problem that Brasero says I have to insert another type of cd/dvd, even though I have a standard cd-r cd in there.

For the record, I want to burn a video disk.

---

### Post by ikt on 2009-10-24
> **Bramkaandorp said:**
> I have the problem that Brasero says I have to insert another type of cd/dvd, even though I have a standard cd-r cd in there.

Do you have the same issue if you use K3B?

> **Bramkaandorp said:**
> 
For the record, I want to burn a video disk.

Video files onto a Data CD or S/VCD?

---

### Post by silvagroup on 2009-10-28
Having problems also. I can burn dvd and cd iso's created by other programs such as Devede all day long but problems trying to do svcd or vcd.
Googling show notjhing in help with this that I could find.
All the recommended packages are also installed.
When I go to burn I get ```
Please replace the disk with supported cd/dvd
``` ```
It is not possible to write with the current ste of plugins
```
I have a standard cd-r in the drive. Searching for plugins doesn't show up anything specific for this error nor does googling show any fixes.

---

### Post by ikt on 2009-10-28
> **silvagroup said:**
> Googling show notjhing in help with this that I could find.
All the recommended packages are also installed.

Have you tried with K3B?

```
sudo apt-get install k3b
```

---

### Post by RedSingularity on 2009-10-28
I have but still nothing.

---

### Post by TenPlus1 on 2009-10-28
try installing dvdauthor, that's been known to fix the problem...

sudo apt-get install dvdauthor

---

### Post by RedSingularity on 2009-10-28
It would seem i already have it installed.

---

### Post by humphreybc on 2009-11-02
Just chiming in here, Karmic and I have the exact same problem and message as post #21.

I'm going to try some other programs and see how we go.

---

### Post by Tholley on 2009-11-02
Brasero has never worked for me in 8.10 or 9.04 so after updating to 9.10, I didn't even try, I just removed it. 

I use DeVeDe to burn an ISO image and K3b to burn it to disc.

Too bad Linux doesn't have something that will work like DVD FAB for windows, that actually rocks. So I do most of my copying in windows since dvdfab works so good.

There are ALLOT of post about Brasero and how bad it is, search "brasero sux" and you will see.

---

### Post by RedSingularity on 2009-11-02
> **Tholley said:**
> Brasero has never worked for me in 8.10 or 9.04 so after updating to 9.10, I didn't even try, I just removed it. 

I use DeVeDe to burn an ISO image and K3b to burn it to disc.

Too bad Linux doesn't have something that will work like DVD FAB for windows, that actually rocks. So I do most of my copying in windows since dvdfab works so good.

There are ALLOT of post about Brasero and how bad it is, search "brasero sux" and you will see.


Yeah thats what i decided to do as well.

---

### Post by Tholley on 2009-11-02
But it is just totally bizarre that Ubuntu doesn't know that Brasero doesn't work and makes it the default.

Has anybody tried it in 9.10 yet?

---

### Post by BarisBlaq on 2009-11-04
It doesn't work for me in 9.10. Used to work fine in 9.04, but now it says that thing about plugins.
=(

---

### Post by coolbrook on 2009-11-04
I never had a problem with Brasero til now.  Same error message as the rest.  CD-R in CD-RW drive.  Ubuntu 9.10.

---

### Post by malty on 2009-11-04
Gave up on both Brasero and K3B some time ago, went back to tried and trusted Nero, new version out now.
Yes, I know it's not free, still cheaper than turning out coasters.
Amarok's going the same way shortly.

---

### Post by perixx on 2009-11-10
Hi,

an interesting observation here (switched to karmic a few days ago):

I wanted to burn and install Ubuntu 9.10 after update of 9.04 messed up the sound and used Brasero from Ubuntu 9.04 for that.
It turned out that the rewritable CD wasn't burned correctly. After that, I used Mint7 (=9.04 I believe) and there was no problem with it.

Having installed Ubuntu 9.10, the sound was non-functional from start. 
Fed up and downloaded and burned Xubuntu 9.10 from Ubuntu 9.10 to install it over - guess what: CD was crap again..!

I made another try and burned it with Mint7 and no problem, installation was done in minutes and sound worked! So it seems, that Brasero is a total mess since 9.04, but NOT in Mint7 (which is based on Ubuntu).
I'll have to try burning from the new Xubuntu now...

By the way, in Mint, there's an option 'use burn proof', which is missing in Karmic's version of Brasero.


perixx

---

### Post by nmyrick on 2009-12-01
To everyone on this post who is having trouble with Brasero,

If you are trying to burn a DVD project (equivalent to Windows Movie Maker or DVD Maker projects) with AVI, Mpeg, or ASF files, try DVDStyler.  It is in the Ubuntu software center on Karmic Koala.

---

### Post by silvagroup on 2009-12-01
nmyrick thanks. Another option and less cryptic for those of us who aren't that savvy with command line options is DeVeDe.

---

### Post by nmyrick on 2009-12-01
Sylvagroup,

DVD Styler is very user freindly and has a very good user interface. I haven't tried DeVeDe, but from the description in the Ubuntu Software Center, it doesn't appear to do nearly as much as far as creating DVD projects with several video segments.

DVD Styler also allows you to create DVD menus similar to the menus on professionally done DVD's.

---

### Post by silvagroup on 2009-12-01
It is really much more than that. I suggest you check it out it's simple enough to install from the repos. I have it and DVDStyler and find I use DeVeDe much more. But then when editing videos I end up using AviDemux, DeVeDe, Kino and DvdStyler. They each have their great points and their bad.

---

### Post by svtguy88 on 2009-12-02
I recently ran into this problem myself.  I was trying to burn a .mov file that Final Cut Express spit out for me (school project), and my Mac only burns DVD-RAM (lol...I know).  Anyway, transferred the .mov to my laptop, and Brasero (running under 9.10 - Karmic) will not burn a video DVD.  It WILL burn the .mov to a disc if I try doing a data disc...

Still no real solution for Brasero it seems?

---

### Post by Eric Fortuna on 2009-12-04
The message on the above of the Brasero is: 
Please replace the disc with a supported CD or DVD.
It is not possible to write with the current set of plugins.

---

### Post by Eric Fortuna on 2009-12-04
> **cariboo907 said:**
> Which  version of Ubuntu are you using and it would help if you could show us the error message so that we can help you resolve this problem.

Jim
[IMG]http://ubuntuforums.org/images/rank_uf_staff.png[/IMG]
 			  			 				 					 
[[IMG]http://ubuntuforums.org/customavatars/avatar77104_7.gif[/IMG]]("http://ubuntuforums.org/member.php?u=77104") 				
 			  			 				 
				Join Date: Mar 2006
 				Location: Williams Lake
 				 	  					Beans: 12,100 				
 			       Ubuntu Development Release  				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				 				**Re: Brasero plugins inadequate** 			
 			 			 		   		 		 		Which version of Ubuntu are you using and it would help if you could show us the error message so that we can help you resolve this problem.

Jim


To Jim: Ubuntu 9.10 version. The message on top of the Brasero Disc Burner is:
**Please replace the disc with a supported CD or DVD.**
It is not possible to write with the current set of plugins.

---

### Post by nmyrick on 2009-12-05
To Jim,

I'm using Ubuntu 9.10, and mine is the same as the above.  The message in the top of the Brasero window says that I do not have the proper plugins to burn to the disk.  

However, I found that after I installed DeVeDe and DVDStyler, Brasero now works. So the installation process of one of these must have installed the plugins that Brasero needs that did not come with the Ubuntu 9.10 release.

---

### Post by vastus on 2009-12-15
> **nmyrick said:**
> To Jim,

I'm using Ubuntu 9.10, and mine is the same as the above.  The message in the top of the Brasero window says that I do not have the proper plugins to burn to the disk.  

However, I found that after I installed DeVeDe and DVDStyler, Brasero now works. So the installation process of one of these must have installed the plugins that Brasero needs that did not come with the Ubuntu 9.10 release.

Also installed DVDStyler and Brasero appears to be working now D:

---

### Post by guevaraj on 2009-12-17
I had the same problem, but it got fixed when I installed DVDauthor.

Maybe someone can post a bug if there is none... The message should
be more clear. Or even better: brassero should offer to install the
necessary plug-ins automatically.

Greetz

---

### Post by groping_blindly on 2010-01-06
I've had all these problems too :(  Brasero has taken Audio CDs, DVDs and Data projects and turned them all into expensive frisbees.

I just downloaded K3B via the repositories and successfully burnt a data DVD.


Ubuntu 8.04, Kernel 2.6.24-24, GNOME 2.22.23  AMD Athlon 64.

---

### Post by kronictokr on 2010-01-06
k3b is the only burning software you need, you can add codecs to rip in many formats as well

---

### Post by ClanClover on 2010-01-24
Same problem here with Brasero (version 2.28.2). Loaded DVD Styler first and no change, then loaded DeVeDe and still gives the same error message as posted above.

Will try DVD Styler and/or DeVeDe to generate a DVD.

---

### Post by llawwehttam on 2010-01-24
I just used Brasero to rip a dvd that is a 106 min film. It gave me a 7.7 GB Iso which was unreadable by anything else. What happened to the nice dvd copying tool that was the default in 8.10 that I had before Brasero?

---

### Post by Das Goat on 2010-01-26
You got that right llawwehttam. I have only had off and on problems with Brasero. I wish they would get rid of it. right click on the ISO and write to disk always worked. Why make something complicated for a simple operation?

---

### Post by kemargrant on 2010-02-03
I'm also having the same problems with Brasero.

---

### Post by krayzee8 on 2010-03-06
I am also having the same problem.

---

### Post by Chito on 2010-03-24
I had the same problem, and when I try to look for any plugins for Brasero on the Sypnaptic Package Manager, I was redirect to this url

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

And solve my problem. I'm running Ubuntu 9.10, but it gives an option for older version also

Problem has been solve.

Make sure you have the Sypnaptic Package Manager close, and follow the sequence of installation. (Very Important)

For versions 9.04 and 9,10 do this:

1.  sudo apt-get install libdvdread4 (enter)
2.  sudo /usr/share/doc/libdvdread4/install-css.sh

For version 8.10

1.  sudo apt-get install libdvdread3 gstreamer0.10-plugins-ugly
2.  sudo /usr/share/doc/libdvdread3/install-css.sh

For version 8.04

1.   sudo apt-get install libdvdread3
2.   sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by Miljet on 2010-04-13
> Problem has been solve.

Make sure you have the Sypnaptic Package Manager close, and follow the sequence of installation. (Very Important)

For versions 9.04 and 9,10 do this:

1. sudo apt-get install libdvdread4 (enter)
2. sudo /usr/share/doc/libdvdread4/install-css.sh

Afraid this did nothing for me. I am running 9.04. Funny thing is, I just burned these same two video clips two weeks ago using Brasero. Now suddenly it doesn't work anymore.

---

### Post by kjnelan on 2010-04-27
> **TenPlus1 said:**
> try installing dvdauthor, that's been known to fix the problem...

sudo apt-get install dvdauthor

This worked for me.  I had the very same problem everyone else was having with the won't burn with current plugins.  Once I installed dvdauthor, Brasero has worked without any problems!!!  

I knew it couldn't be my burner because it is brand new, and works without problems under a Windows environment. (I know there could be address issues and the such, but not likely if working under one and not the other...)

I'm burning my latest dvd as we speak; my wedding.

There is nothing to loose by trying and seeing if it works.

If it doesn't work, perhaps troubleshooting your drive.  Does the drive work?  Will it burn a music cd?  Does it burn a data dvd cd? The drive may well have issues?

K

---

### Post by nmyrick on 2010-04-28
Mine works since I installed DVD Styler, which is actually a really good DVD making program for home movies.  I knew my DVD burner was working because I have IMGBurn installed in wine, and that has allways worked.

---

