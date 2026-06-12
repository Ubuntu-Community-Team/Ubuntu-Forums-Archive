---
title: "New MythTV/PVR-250/nVidia/TV-out HOWTO"
date: 2005-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by scholzie on 2005-04-24
I had started this a few weeks ago, and I noticed someone else had also started one. I refused to let my hard work go to waste, so I finished it up and I'm posting it all for you to enjoy. There's nothing wrong with a bit of healthy competition, though :)

It goes through the set up of Partitioning, what you need for Ubuntu, getting nVidia drivers set up with TV-out, IVTV, MythTV, automatic login, etc etc etc. The only thing it does not have at the moment is lirc, since it's a royal pain in Ubuntu at the moment.

I hope you like it, and I'll take suggestions, as it's a work in progress.

[Ubuntu MythTV HOWTO with nVidia TV Out and Hauppauge PVR-250](http://www.cs.rit.edu/~css8044/?q=mythtv)

---

### Post by windexh8er on 2005-04-25
Awesome guide!  One thing I noticed when skimming through it is that to compile IVTV you don't really need the entire source, just the headers.  Might cut down on the steps you have in.  We should merge our guides...  I was planning on finishing up the LIRC stuff this weekend (which - is actually very easy) but I ended up being out of town until late last night.  :(

---

### Post by scholzie on 2005-04-25
[QUOTE=windexh8er]Awesome guide!  One thing I noticed when skimming through it is that to compile IVTV you don't really need the entire source, just the headers.  Might cut down on the steps you have in.  We should merge our guides...  I was planning on finishing up the LIRC stuff this weekend (which - is actually very easy) but I ended up being out of town until late last night.  :([/QUOTE]
 I did notice that with the headers, too, but this was more for the whole overall install of nvidia drivers, lirc, etc. Some of the compile steps do need a full source install, and the guide isn't finished yet, so it should become apparent at some point why a kernel source is needed.

It could use some revisions, for sure, but for now it's up :)

Oh, edit: If you finish up the LIRC stuff, let me know. I can link it from my guide to yours if it looks good. It's been driving me nuts since the modules don't compile correctly  ](*,)

---

### Post by poofyhairguy on 2005-05-13
bump.

---

### Post by Heliode on 2005-05-13
Whats the status on the Lirc howto? I --NEED-- it!  :grin:

---

### Post by scholzie on 2005-05-16
[QUOTE=Heliode]Whats the status on the Lirc howto? I --NEED-- it!  :grin:[/QUOTE]
Finals have kept me from doing much of anything lately...I'll try to work on it when I'm done :/

---

### Post by Heliode on 2005-05-16
Ok dude, no problem! I hope you do well!

---

### Post by vibranze on 2005-05-26
Thanks Scholzie for the great HOW-TO.

I encountered problem when I tried to install mythtv, here is the error :

$ sudo apt-get install mythtv
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-frontend (= 0.18-1) but it is not going to be installe d
          Depends: mythtv-backend (= 0.18-1) but it is not going to be installed
E: Broken packages

$ sudo apt-get install mythtv mythtv-frontend mythtv-backend
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv-backend: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is t o be installed
                  Depends: libmyth-0.18 but it is not going to be installed
                  Depends: libqt3c102-mt (>= 3:3.3.4) but 3:3.3.3-7ubuntu3 is to  be installed
  mythtv-frontend: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
                   Depends: libmyth-0.18 but it is not going to be installed
                   Depends: libqt3c102-mt (>= 3:3.3.4) but 3:3.3.3-7ubuntu3 is t o be installed
E: Broken packages

Any idea what is the error?

Would it be the same for other TVTuner card using bttv chip instead of Haupage? My card is AverMedia

Regards,
Vibrane

---

### Post by malachakla on 2005-05-26
I have the same error, unfortunately.
I have an Airlink card.

---

### Post by qrazi on 2005-06-04
[QUOTE=malachakla]I have the same error, unfortunately.
I have an Airlink card.[/QUOTE]
 i have the same error too.... anybody knows why?

---

### Post by TimmyJ on 2005-06-28
scholzie,

Great looking guide. I noticed a few typos throughout and It may be useful for new users if you make sure that you include 'sudo' in your code snippets when neccesary. I tried following this guide w/ no luck :( I'm trying to get my pvr-150 up and running and ran into trouble making ivtv. Keep up the great work.

Edit: I got ivtv up and running but ran into the same problem as the 2 previous posters with installing mythTV  :(

---

### Post by dirkoneill on 2005-06-29
I also ran into the dependency problems that the last three posters had. I tried running the install for mythtv-frontend then, but then I had dependency issues with libvc or something. Libvc was already installed so I don’t know what the problem was. I’m at work now but when I get home I’ll post the actual console errors. Hopefully, someone can come up with a fix soon.

---

### Post by craveytrain on 2005-06-30
I was getting the same conflict errors while using his guide (which really helped me). I took the mythtv line out of hte sources.list and just left it with the multiverse edit and I was able to install mythtv with no problem. I'm watching off of it right now as we speak. now to try to figure out lirc.

as for the headers vs. full source, doing it verbatim of the guide was giving me errors while running make. I did a little "apt-get install build-essential linux-headers-`uname -r`" at the point of the other apt-get source and repeated the steps and it worked fine. I don't know what that actually means, but I know it worked for me after I did that.

btw, the myth-setup now appears to be called mythtv-setup. minor detail, but it's an important one.

---

### Post by dirkoneill on 2005-06-30
What version of mythtv are you running now? I noticed, before i tried the guide, that mythtv 0.17 was showing up. I was hoping to get 0.18 eventhough i hear reports that 0.17 is more efficent at software decoding.

---

### Post by tom-ubuntu on 2005-08-10
I am in the process on setting up an MythTV Box following your guide. I recognized that there are a few steps missing. I'll try to record everything here in this thread.

As I am in the office now, I'll just try out of my mind with what I had problems with:

- after installation, do also an "apt-get dist-upgrade" to get the base system to the latest versions
- Kernelheaders need to be installed aswell (for ivtv/driver compilation)
- the repository arguments (or whatever they are called) for [http://dijkstra.csh.rit.edu/~mdz/debian](http://dijkstra.csh.rit.edu/~mdz/debian) the way you described them gave me error messages about broken packages. I will post it this evening how it did work for me. Perhaps some else got problems aswell.

Ok, that's it so far. Thanks for writing this guide, great work  :)

Regards
  Tom

---

### Post by crouton on 2005-08-13
[QUOTE=joeuser]I am in the process on setting up an MythTV Box following your guide. I recognized that there are a few steps missing. I'll try to record everything here in this thread.

As I am in the office now, I'll just try out of my mind with what I had problems with:

- after installation, do also an "apt-get dist-upgrade" to get the base system to the latest versions
- Kernelheaders need to be installed aswell (for ivtv/driver compilation)
- the repository arguments (or whatever they are called) for [http://dijkstra.csh.rit.edu/~mdz/debian](http://dijkstra.csh.rit.edu/~mdz/debian) the way you described them gave me error messages about broken packages. I will post it this evening how it did work for me. Perhaps some else got problems aswell.

Ok, that's it so far. Thanks for writing this guide, great work  :)

Regards
  Tom[/QUOTE]
 Looking forward to your post, joeuser.  I like Chris's guide but I'm getting stuck on getting nvidia drivers to work (i'm compiling my own kernel) and ivtv refuses to compile (even with full source available.)

---

### Post by tom-ubuntu on 2005-08-13
[QUOTE=crouton]Looking forward to your post, joeuser.  I like Chris's guide but I'm getting stuck on getting nvidia drivers to work (i'm compiling my own kernel) and ivtv refuses to compile (even with full source available.)[/QUOTE]
My box is more or less up and running. ivtv, lirc everything is working. Just need to configure everything to my liking.

But I started following this guide, which seems far more complete to me, including a forum:
[http://www.abarbaccia.com/](http://www.abarbaccia.com/)

---

### Post by scholzie on 2005-08-14
Hi guys. Sorry, I pretty much forgot about this guide.

I have been doing a long co-op employment at Intel this summer in Oregon, and as such don't have access to my Myth box and haven't been able to fix the guide up.

Things are very different on the MythTV front than they were earlier this year when I wrote the guide. When I get back to RIT, I'm going to start over with 0.18. As I understand it, there are new packages specifically for Ubuntu and I'll rewrite the guide accordingly.

Many of you are noting problems like kernel headers and sudo. When the guide was written, it was possible to follow the instructions and get the system working provided you followed them exactly. The guide was written on a fresh-as-fresh-can-be installation of Ubuntu Hoary. Apparently things have changed on the myth/ivtv end and thus need to be investigated more. I promise that once I'm back with my PVR I will upgrade it for new versions and distro changes.

Until then, please help eachother. I'm essentially out of the loop until I get back home in a few months. God speed :)

(ps, if you find any essential changes, please let me know. I'll ssh into the guide and update them if enough of you email me about it.)

---

### Post by tom-ubuntu on 2005-08-15
Hi scholzie, no problems at all. We got our boxes up and running.

What about the packages which are done specially for Ubuntu? Are they already in a repo? Url's?

Cheers Joe

---

### Post by scholzie on 2005-08-16
[QUOTE=joeuser]Hi scholzie, no problems at all. We got our boxes up and running.

What about the packages which are done specially for Ubuntu? Are they already in a repo? Url's?

Cheers Joe[/QUOTE]
 adding "deb [http://dijkstra.csh.rit.edu/~mdz/debian](http://dijkstra.csh.rit.edu/~mdz/debian) hoary mythtv" to sources.list should do it. He re-designed the hierarchy of his debs, and since he's added hoary and warty specific packages they're more likely to work.


Incidentally,  many people have told me that linux-kernel-headers need to be installed for this and that, etc... If you install a base ubuntu system they are INSTALLED BY DEFAULT. I re-ran an Ubuntu installation last night just to make sure I was correct, and sure enough they were there. So, I'm fairly confident that my guide is correct on that aspect, but next time I update it I will make a point of informing the user to install it if they don't have it for some strange reason.

---

### Post by cwestpha on 2005-08-17
probebly doing something wrong but...

root@Ubuntu:~ # echo "myth-setup" >> /home/mythtv/.xsession
root@Ubuntu:~ # chown mythtv.mythtv /home/mythtv/.xsession
root@Ubuntu:~ # /etc/init.d/mythtv-backend start
Starting MythTV server: mythbackendQSettings: error creating /root/.qt
.


and then...

root@Ubuntu:~ # su mythtv
sh-3.00$ startx
xauth:  creating new authority file /home/mythtv/.Xauthority
xauth:  creating new authority file /home/mythtv/.Xauthority

X: user not authorized to run the X server, aborting.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
Couldnt get a file descriptor referring to the console

So what idiotic and moronic thing did I do? (used Universe as source since MythTV apt source spouted crazy dependencies)

---

### Post by tom-ubuntu on 2005-08-17
[QUOTE=scholzie]adding "deb [http://dijkstra.csh.rit.edu/~mdz/debian](http://dijkstra.csh.rit.edu/~mdz/debian) hoary mythtv" to sources.list should do it. He re-designed the hierarchy of his debs, and since he's added hoary and warty specific packages they're more likely to work.[/QUOTE]
Cheers for this, will try as soon as I have time.

[QUOTE=scholzie]Incidentally,  many people have told me that linux-kernel-headers need to be installed for this and that, etc... If you install a base ubuntu system they are INSTALLED BY DEFAULT. I re-ran an Ubuntu installation last night just to make sure I was correct, and sure enough they were there. So, I'm fairly confident that my guide is correct on that aspect, but next time I update it I will make a point of informing the user to install it if they don't have it for some strange reason.[/QUOTE]
Ok. But looks like if you are doing a server installation, it is not included. So adding a hint would be great. Just to save a few users the time for hunting for the error. Thanks mate!

---

### Post by matt1980 on 2005-08-24
> root@Ubuntu:~ # /etc/init.d/mythtv-backend start
Starting MythTV server: mythbackendQSettings: error creating /root/.qt

For this part, I got a similar error when trying to start (with sudo) logged in as my own user. However, if I tried to start it when logged in as the mythtv user I didn't get the error. Also, this page (near the bottom) has more information on this issue and has some pretty good information on other ubuntu/mythtv issues:

[http://www.wlug.org.nz/MythTvNotes](http://www.wlug.org.nz/MythTvNotes)

---

### Post by matt1980 on 2005-08-24
[QUOTE=joeuser]- the repository arguments (or whatever they are called) for [http://dijkstra.csh.rit.edu/~mdz/debian](http://dijkstra.csh.rit.edu/~mdz/debian) the way you described them gave me error messages about broken packages. I will post it this evening how it did work for me. Perhaps some else got problems aswell.[/QUOTE]

Did you ever get this repository to work? Based on your later post, it looks like you may have gone with the 0.17 stuff in the hoary repositories (I also am primarily following the [http://www.abarbaccia.com/](http://www.abarbaccia.com/) guide, and installed the 0.17 stuff on my test box when doing a dry-run through it), but I really need the 0.18 version, if not from this repository from *somewhere*--I'm running Mac OS X 10.4 (Tiger) on several boxes and the only front-end I've found so far for that platform is a 0.18, which I don't think will work with the 0.17 backend...plus I'd love to play with the mfd/daap stuff in CVS to get it to serve music to my iTunes clients.

Has *anyone* gotten 0.18 up and running properly under hoary? I've had the same dependency problems from the above mentioned repository as others  ](*,) . What about building from source? Anyone been able to do it that way? I'm part newbie and part advanced--I did manage to get the saa7134 module recompiled and installed from a v4l snapshot for my AverTV 007 Go card, so I'm not completely incapable of building stuff, I just don't know all the tricks yet.

TIA

---

### Post by tom-ubuntu on 2005-08-24
I switched also to the guide on abarbaccia.com. Honestly, I don't know, which version I am running. MythVideo and MythDVD are working fine, don't need the rest know. Just recognized, that MythMusic is not setupped, although it is installed. MythGame does also not work either.

---

### Post by scholzie on 2005-08-24
[QUOTE=matt1980]
Has *anyone* gotten 0.18 up and running properly under hoary? 

TIA[/QUOTE]
I compiled 0.18 from source and had it working right away.

---

### Post by Chareos on 2005-08-28
I tried to compile it, but it doesn't find my lirc installation (I have it, up and working... but compiled by my own, due ubuntu's lirc is something like a JOKE... "cto configure this, go read hat file which points to another readme file, which says nothing but install another package... that package's doc says to go read a readme file which says to go read another reaAAAAHHHH)

---

### Post by evilbunny on 2005-08-28
[QUOTE=scholzie][Ubuntu MythTV HOWTO with nVidia TV Out and Hauppauge PVR-250](http://www.cs.rit.edu/~css8044/?q=mythtv)[/QUOTE]

Ummm what happened to this, it was working yesterday and today I'm getting 403 errors...

---

### Post by evilbunny on 2005-08-28
[QUOTE=matt1980]Has *anyone* gotten 0.18 up and running properly under hoary?[/QUOTE]

Yes... stick the following line in your sources apt-get update/apt-get install mythtv

deb [http://dijkstra.csh.rit.edu/~mdz/debian](http://dijkstra.csh.rit.edu/~mdz/debian) hoary mythtv

Although I haven't found a suitable 0.18 mythgame package for ubuntu so I'll prolly end up building that myself...

---

### Post by evilbunny on 2005-08-29
[QUOTE=evilbunny]Ummm what happened to this, it was working yesterday and today I'm getting 403 errors...[/QUOTE]

nm it's working again...

While I found the [howto](http://www.cs.rit.edu/~css8044/?q=mythtv) a great place to start, there's a couple of issues/descrepencies that could make it more useful for newbies:

1) It didn't suggest using LVM, so was a big PITA when I ran out of hdd space and needed to add some more... Even if you think you will only ever use one hdd/partition for recorded data turning LVM on by default during install will save you a lot of time and suffering later!

2) It links to the debian packages instead of the ubuntu ones (although others already pointed it out, it's not obvious there are ubuntu packages unless you go digging) which is compiled/built against the stable/unstable debian libraries, and so you either need to install those (which does work) or just change unstable in the information to hoary (or even warty)

3) Ideally to pass the normal user test (gf/wife/etc) it needs to have a spalsh screen, this is something I haven't managed to get working yet, so I'll make some notes on it, because they just don't get seeing a bunch of text...

4) Unless you go digging in the xorg configs a normal user isn't allowed to start X, the easiest way I found round this (although slightly bloating things) was to install gdm and then set mythtv to auto login (nano /etc/gdm/gdm.conf)
```
AutomaticLoginEnable=true
AutomaticLogin=mythtv

TimedLoginEnable=true
TimedLogin=mythtv
TimedLoginDelay=1
``` 

5) Having the screen blank was annoying and difficult to find out how to disable, so adding "xset s off" to the top of the .xsession file will disable this

6) The details given about the mysql section is either out of date or he left out a step as it was confusing and didn't work, basically you need to set the user password for mythtv to match what you tell it when you get prompted during package install.

7) The mythsetup details could be a little more detailed for newbie users as there is a substantial amount of information to take in and process, after the 5th wipe of the database and setup it surprisingly becomes a lot clearer on what's going on and what needs to be done.

8) I agree with the other poster about ubuntu's idea of how to setup LIRC not to mention being a fair way out of date I ended up simply downloading the latest tarball and compiling it up myself, I tried the pvr-150 remote/card but that kept locking up and the only way I could restart it was with a cold boot, I ended up just grabbing a MCE USB remote which works flawlessly, if you've followed the rest of the howto all you need to do is grab the latest and greatest tarball and extract it (I dump everything in /usr/src) go into the drivers sub-directory and simple "make; make install" then run lircd -d /dev/lircd0.

The MCE USB gets loaded in via the hotplug system and what I can't work out is how to load and quit lircd the same way, otherwise it's just a hack job of reloading lircd until the device exist in /dev

---

