---
title: "HOWTO: Change Metacity/Twinview window placement behavior [Dapper, Edgy]"
date: 2006-08-23
forum: Outdated Tutorials &amp; Tips
---

### Post by TLE on 2006-08-23
[SIZE="1"]**Keywords: Metacity, Twinview, Xinerama, dual-display, dualdisplay, dual-view, dualview, window, placement, algorithm, patch, other screen, arghh, doh, dapper, edgy, 6.06, 6.10**[/SIZE]

[SIZE="4"]HOWTO: Change Metacity/(Twinview/Xinerama) window placement behavior [Dapper, Edgy][/SIZE]
[SIZE="2"]*This HOWTO applies to 32 bit Dapper and 32 bit Edgy only*[/SIZE]

[SIZE="2"]Hey everybody
First of all, what is this HOWTO for? This HOWTO can help solve your problem if you meet the following two criteria:
[LIST=1]
[*]You have a functional Twinview system, (no matter which graphics card) meaning that your desktop extends onto an other screen
[*]You are pulling your hair out because every time you open the second window on a desktop, this window automatically opens on the second monitor and that was NOT what you wanted it to
[/LIST]
If you meet the criteria above, please read on.

The solution to this problem is a simple one line patch of the Metacity (the window management application in GNOME) source-code. This will change the behavior of the window placement algorithm so that it works like it did before EXCEPT that it will always open new windows on the same screen as the one the mouse is in.

***Be aware:** This patch is neither supported or encouraged by the Metacity development team, in fact they claim that it is wrong (see comment 12 in [this thread]("http://bugzilla.gnome.org/show_bug.cgi?id=145503")), and I don't have any c-programming experience so that I can check it out for myself. So use it at your own risk* That being said, it works fine for me and I haven't experienced any side-effects, plus, the place where I found the patch in the first place is a university that supplies the patched packages to all the users of a certain piece of software they develop, soooo it HAS been tested and is still in use there.

There are two ways to install this. The first one is to simple install the patched .deb's that I've supplied and the second, which is somewhat more "hands on", is to, download the source-code, place the patch, repackage and install the packages. Since I have now updated this for edgy also this guide now covers two different version of metacity, 2.14.5(Dapper) and 2.16.3(Edgy). Therefore the download commands are split in two and you are off course only meant to get the one that corresponds to your system. In the rest of the instructions I have just left them as they were for Dapper so here you have to replace the version with the right ones yourself. I hope this is clear. Here we go[/SIZE]

[SIZE="3"]**Installing the .deb's I have made**[/SIZE]
[SIZE="2"]If you don't want the trouble of patching yourself you can just use the packages I have made from the patched source-code. They have a slightly different version-number so they will install as an update to the current version of Metacity (2.14.5). This prevents apt to just replace them the next time you run update. But this also means that the next time there do come some new Metacity packages you will have to do this again. But no worries, it easy, it doesn't happen that often and I will keep supplying .deb's for the purpose. Enough talk already. To install simply do the following.[/SIZE]
```
cd /to/whereever/you/keep/temporary/files
```
In Dapper do:
```
wget http://www.student.dtu.dk/~s021749/metacitydebs/metacity-2.14.5-0ubuntu2_i386.tar.gz
```
In Edgy do:
```
wget http://www.student.dtu.dk/~s021749/metacitydebs/metacity_2.16.3-0ubuntu3_i386.tar.gz
```
Then:
```
tar -xvzf metacity*.tar.gz
cd metacity*
sudo dpkg -i *.deb
```
That's it. Restart X, CTRL-ALT-BACKSPACE and we're done.

[SIZE="3"]**Patching the source-code and repackaging**[/SIZE]
[SIZE="2"]First of all, the "apt-get install" command for dapper might be missing some packages, but for edgy it should be sufficient. Ok, download the patch and the source-code, and install the extra packages we need.[/SIZE]
```
cd /to/whereever/you/keep/temporary/files
```
Now in Dapper do:
```
wget http://www.student.dtu.dk/~s021749/metacitydebs/2.14.5_i386/021-twinview-modification.patch
sudo apt-get install devscripts fakeroot cdbs debhelper liborbit2-dev libpopt-dev libxml2-dev libgconf2-dev libglade2-dev libstartup-notification0-dev libxml-parser-perl gnome-pkg-tools
```
In Edgy do:
```
wget http://www.student.dtu.dk/~s021749/metacitydebs/2.16.3_i386/021-twinview-modification.patch
sudo apt-get install devscripts fakeroot cdbs debhelper libgtk2.0-dev liborbit2-dev libpopt-dev libxml2-dev libgconf2-dev libglade2-dev libice-dev libsm-dev libx11-dev libxt-dev libxext-dev libxinerama-dev libxrandr-dev x-dev libxinerama-dev libstartup-notification0-dev gnome-pkg-tools
```
Then:
```
apt-get source metacity
```
[SIZE="2"]That was the download. So now we copy the patch into it's right place and edit the change-log so the new package will work like an update.[/SIZE]
```
cd metacity-2.14.5/
cp ../021-twinview-modification.patch debian/patches/
debchange -i
```
[SIZE="2"]Now an editor should pop up. Here you can add a change log entry. It's not necessary as it has already automatically created the one important line that describes the new version so you can just save and exit. But if you want to you can add something. This is the entry I added in the ready-made .deb's:[/SIZE]
```
metacity (1:2.14.5-0ubuntu2) dapper-updates; urgency=low

  * debian/patches/021-twinview-modification.patch
    - Keeps newly opened windows on the same twinview display
      as the mouse is on

 -- Kenneth Nielsen <k.nielsen81@gmail.com>  Mon, 21 Aug 2006 15:29:38 +0200
```
[SIZE="2"]Now all we need to do is to repackage and install[/SIZE]
```
fakeroot dpkg-buildpackage -us -uc
sudo dpkg -i ../*.deb
```
That's it.

[SIZE="3"]My story:[/SIZE]
Ok so if you are still not sure about the reason for installing this, here is a description of my system and the way I use, maybe it'll clear it up.
My second monitor is the television. What I wanted from this setup is to be able to watch movies from my computer on the television, so that when I wanted to watch a movie I could open a movies player an drag it to the television and blow it up to full-screen. This also means that I NEVER want anything to open on the television per default, I'll drag whatever need to go there myself. This is however not possible because Metacity will always place a new window where there is more space, until is has all been used, then another algorithm kicks in.  So after I got the Twinview setup to work, I would constantly have to drag windows from the television, which is a real pain in the.....

[SIZE="3"]Credits[/SIZE]
[SIZE="2"][LIST]
[*]**ookami** from the forum, for encouraging me to snope around to find a solution to this problem, and has also tested it
[*]**Christoph Willing** from the University of Queensland. He supplied the patch and pointed me in direction of Klaus Reimer's website
[*]**Klaus Reimer**. On his [website]("http://www.ailis.de/~k/") there is a [extensive guide]("http://www.ailis.de/~k/docs/atilinux/") about this patch and some other ATI stuff for Breezy. In fact this HOWTO is largely based on this page
[*]The guys at **#ubuntu-motu** for answering some of all my newbie questions about repackaging
[/LIST][/SIZE]

[SIZE="3"]**Please give me feedback. I would very much like to know, of course, if something doesn't work, but also, please write a post, if you used it and it worked just fine, so that I can see how many has this problem.**[/SIZE]

---

### Post by ÄlveKatt on 2006-09-02
Wouldn't it be desirable for the application to just remember where you used it the last time? 

I am not a fan of cascading windows, I gather I use the panel that lists open windows the way you use the cascading of windows and I imagine that cascading windows would be more useful when you have a real big screen (or eyesight like a hawk).

I liked the simplicity of using two screens in microsoft windows, the way you just relate the screen virtually to fit their relative physical placement in a graphical interface and how i could start firefox, move it to the other screen and close it for it to remember that it was where I wanted it.

---

### Post by TLE on 2006-09-02
> **ÄlveKatt said:**
> Wouldn't it be desirable for the application to just remember where you used it the last time?
Yes....is the short answer. The desktop envoriment GNOME has after a long time of trying other system (Enlightenment and Sawfish, see this [article]("http://en.wikipedia.org/wiki/Metacity")) decided to use Metacity as its window manager tool. This was done to try and keep GNOME lightweight yet functional, and for the most part I think it works quite weel.
For all single screen use I'm quite satisfied with the way Metacity handles windows in GNOME and in particular I don't mind the cascading window policy. But for dualscreen purposes it really sucs. But this is due to another feature in metacity. Metacity will, before the cascading window feature kicks in, try to place every new window at a position where there is enough room. And it is this feature that's responsible for placing windows at the other screen. As I indicated in the original post the Matecity deveopers are aware of this problem, but are unvilling to change it because they feel that group of people that need this feature is to small to justify complicating the code.

So in short.
I understand and respect the decision of the GNOME people for choosing Metacity as a part of an effort for keeping GNOME lightweight.
I don't agree with the Metacity developers that this feature isn't worth changing.
I would certainly prefer it IF the window manager in GNOME would either, per default keep newly opened windows on the same screen as the mouse, or remember the placement of where the applicaions where the last time.
But untill that happens I guess we're stuck with either using this HOWTO or, changing window manager or changing desktop enviroment (which I would rather not do since I really like GNOME)

Regards TLE

---

### Post by bluevoodoo1 on 2006-09-16
Hey! This is working quite well! I am very pleased so far. No issues at all. I hope this is problem is addressed in future versions of metacity. 

Thanks!

---

### Post by zooounds on 2006-09-25
I love you :)

It is stupid the Gnome/Metacity team not fix this issue.
Is REALLY annoying when you have twinview.

---

### Post by TLE on 2006-09-29
I'm glad that it works for you

---

### Post by bluevoodoo1 on 2006-10-29
Will you be updating this for Edgy?

---

### Post by TLE on 2006-10-30
> **bluevoodoo1 said:**
> Will you be updating this for Edgy?

Yes, as soon as I get Edgy installed. I'm having major problems. But if I don't get it to work any time soon, I can help you make the packages yourself instead.

---

### Post by TLE on 2006-11-08
The HOWTO is now updated for Ubuntu 6.10 (Edgy)

Let me know if you have any problems

---

### Post by cabaro on 2006-12-05
Hi i applied the patch with the first method and after that gnome won't start, it just hangs, and i have to hit ctrl+alt+backspace to reset X. Just upgraded to Edgy (which had some problems, but that's another story).
Any ideas, on how to remove the patch?

Cheers

---

### Post by TLE on 2006-12-05
Yes but before you do that, could you please post the output of the following commands here?
```
apt-cache policy metacity metacity-common libmetacity0 libmetacity-dev
```
\TLE

[Edit] You are running a 32 bit version of Ubuntu Edgy or Dapper right?

---

### Post by cabaro on 2006-12-06
Here's the output

metacity:
  Installed: 1:2.16.3-0ubuntu3
  Candidate: 1:2.16.3-0ubuntu3
  Version table:
 *** 1:2.16.3-0ubuntu3 0
        100 /var/lib/dpkg/status
     1:2.16.3-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
metacity-common:
  Installed: 1:2.16.3-0ubuntu3
  Candidate: 1:2.16.3-0ubuntu3
  Version table:
 *** 1:2.16.3-0ubuntu3 0
        100 /var/lib/dpkg/status
     1:2.16.3-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
libmetacity0:
  Installed: 1:2.16.3-0ubuntu3
  Candidate: 1:2.16.3-0ubuntu3
  Version table:
 *** 1:2.16.3-0ubuntu3 0
        100 /var/lib/dpkg/status
     1:2.16.3-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
libmetacity-dev:
  Installed: 1:2.16.3-0ubuntu3
  Candidate: 1:2.16.3-0ubuntu3
  Version table:
 *** 1:2.16.3-0ubuntu3 0
        100 /var/lib/dpkg/status
     1:2.16.3-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages

---

### Post by TLE on 2006-12-06
And you are running a 32 bit version of Ubuntu ?

---

### Post by cabaro on 2006-12-06
yes. 32 bit kubuntu edgy.
I've been mostly using kde for two features that seem to be lacking in gnome; 
Both related to Twinview, first i have my tv connected to nvidia 6600gt tvout 
and i use vlc player fullscreen to go to tv, secondly was the problem of new
windows popping (semi)randomly on each screen, wich is a pain.

If you need any console output, i'd be happy to send.

/cab

---

### Post by marcele on 2006-12-06
Thanks for this. Works great in Edgy :)

---

### Post by bluevoodoo1 on 2006-12-06
> **cabaro said:**
> yes. 32 bit kubuntu edgy.
I've been mostly using kde for two features that seem to be lacking in gnome; 
Both related to Twinview, first i have my tv connected to nvidia 6600gt tvout 
and i use vlc player fullscreen to go to tv, secondly was the problem of new
windows popping (semi)randomly on each screen, wich is a pain.

If you need any console output, i'd be happy to send.

/cab

You have metacity, but Kubuntu uses kwin as its window manager, correct?

---

### Post by cabaro on 2006-12-07
I might be wrong here, but i think the window manager is kwin when i'm using kde and metacity when using gnome, since i have them both installed.

So any advice on how to remove this patch, since gnome is not starting since?

---

### Post by TLE on 2006-12-07
> **marcele said:**
> Thanks for this. Works great in Edgy :)

Great.

---

### Post by TLE on 2006-12-07
> **cabaro said:**
> So any advice on how to remove this patch, since gnome is not starting since?

Yes I can't really think of anything else to do. It's a small simple patch and shouldn't create any problems. Maybe, just maybe, it has something to do with that it is a upgraded system, but it is also is a little too convinient an excuse, since it has given problems with a lot of other things. I don't really think it is the case, but I would appreciate it if you would test it again if you ever do make a clean install of Edgy.

Regarding the removal, I just need to figure out the right command for you, to downgrade all four packages at the same time so there wont be any dependency issues. I write here as soon as I have it. Sorry for the inconvenience.
\TLE

---

### Post by cabaro on 2006-12-07
Thanks in advance.
I might give it another go, if i do a reinstall.
By the way, does it work in 64bit ubuntu/kubuntu?

---

### Post by cabaro on 2006-12-08
Any ideas yet?
Even though i mainly use KDE, i still wouldn't like to leave my 'puter on a broken state.

Cheers
/cab

---

### Post by TLE on 2006-12-08
I will help all I can and I confident that it can be fixed but I'm actually really really busy right now. I have exams on Wednesday and Thursday, so I would appreciate it if you could wait until Friday.

---

### Post by cabaro on 2006-12-15
Got it working after updating everything.

Now I also installed a fresh Edgy 64 bit, so my question is, Is there a 64 bit version of this patch?

---

### Post by TLE on 2006-12-15
Great. That's good news.
About the 64 bit version. There aren't any packages for that yet, but I'll get right on it. So they should be here soon.

---

### Post by R4tmonkey on 2006-12-15
Thank you! This works great! I used beryl for a while because that also forced windows to open in main display only, but beryl was too heavy to use IMO.

---

### Post by TLE on 2006-12-15
> **R4tmonkey said:**
> Thank you! This works great! I used beryl for a while because that also forced windows to open in main display only, but beryl was too heavy to use IMO.

Great thanks for the reply.

---

### Post by mojoman on 2007-01-21
> **TLE said:**
> Great. That's good news.
About the 64 bit version. There aren't any packages for that yet, but I'll get right on it. So they should be here soon.

Any news on the 64-bit package? I sure could use it. This seems like a perfect fix for me. I'm using a projector as my second monitor and I only use it for watching movies. Dragging the windows is, well, a drag. :wink: 

Best regards
/Mojoman

---

### Post by andytof47 on 2007-01-30
Hey The behaviour changed after performing the install but one of the packages had a depenency problem.....


what files do you need to fix this e.g. logs that i can post to give you the info you need????? and what can Install to fix the dependency problems so it will just work??

thanks


Great idea when it works

---

### Post by TLE on 2007-01-30
> **mojoman said:**
> Any news on the 64-bit package? I sure could use it. This seems like a perfect fix for me. I'm using a projector as my second monitor and I only use it for watching movies. Dragging the windows is, well, a drag. :wink: 

Best regards
/Mojoman

Sorry for not replying sooner. Actually since Feisty is just around the corner it is doubtful if I will find the time to install a 64 bit edgy just to build these packages. But what I can do is that I can help you build them yourself. It isn't difficult at all, we could do it over some IM program in a couple of hours if you are interested. And then we could upload the packages you build and link them here for other people to use.
What do you think ?
\TLE

---

### Post by TLE on 2007-01-30
> **andytof47 said:**
> Hey The behaviour changed after performing the install but one of the packages had a depenency problem.....


what files do you need to fix this e.g. logs that i can post to give you the info you need????? and what can Install to fix the dependency problems so it will just work??

thanks


Great idea when it works

Hmm. That's wierd. Ok yes I'll need to know. Which method you used, what kind of a system you have and what commands you executed and ANY and ALL output you get/got when you install(ed) them.

\TLE

---

### Post by mojoman on 2007-01-30
> **TLE said:**
> Sorry for not replying sooner. Actually since Feisty is just around the corner it is doubtful if I will find the time to install a 64 bit edgy just to build these packages. But what I can do is that I can help you build them yourself. It isn't difficult at all, we could do it over some IM program in a couple of hours if you are interested. And then we could upload the packages you build and link them here for other people to use.
What do you think ?
\TLE

If you're willing to hold my hand and walk me through it, sure, I'd love to give it a shot! But I warn you, I have no experience whatsoever when it comes to compiling software or building packages so you might have to *really* walk me through it... If you're prepared to put in the time and the effort I'd really appreciate it. You can get a hold of me through ICQ or MSN, and we can work out some time that fits us both.

/Mojoman

ps: jag är i Stockholm så vi är i samma tidzon. ds :D

---

### Post by andytof47 on 2007-01-30
ok

I used your prebuilt packages and followed the instructions

I use edgy


as for output - which log file should i look in ???? i'm fairly green around the edges


Cheers

---

### Post by TLE on 2007-01-30
> **andytof47 said:**
> ok

I used your prebuilt packages and followed the instructions

I use edgy


as for output - which log file should i look in ???? i'm fairly green around the edges

Cheers

Ok let's forget the logs for a second. Can you post the output of this command:
```
apt-cache policy metacity metacity-common libmetacity0 libmetacity-dev
```
\TLE

---

### Post by walmartshopper67 on 2007-02-06
Awesome - great job. It's funny because I needed it for the exact same reason you did and I was going crazy. 

It seems to work great, but not with the administrative apps like synaptic, etc. It doesn't seem to work with anything launched with gksudo. Is this normal?

---

### Post by rubberglove on 2007-02-20
Wow - this looks great. This issue has bugged me for the longest time. Most of the time, I just give up and disable my second display (also a TV), but having things work properly would be a definite bonus! 

I do need a 64-bit version, though. So I'll see if I can get impatient enough to put one together myself, instead of waiting for feisty to come out. 

At very least, thanks for showing me that i'm not just missing some 'turn off annoying behaviour' option somewhere that's causing my windows to open across the room from me....

cheers.

---

### Post by mojoman on 2007-02-20
Rubberglove: TLE helped me compile .debs for 64-bit dapper. If you're running dapper, they should work fine for you and I'd be happy to transfer them to you (through ICQ or mail or whatever). Just let me know, ok?

/mojoman

---

### Post by cabaro on 2007-02-24
Would this work for 64 bit Edgy as well?

I was also wondering since i also use TV as my second monitor with twinview, would it be a better solution to have just two screens without twinview and send the output from vlc or whatever you use to second screen in fullscreen mode?

/cab

---

### Post by mojoman on 2007-02-24
> **cabaro said:**
> Would this work for 64 bit Edgy as well?

I was also wondering since i also use TV as my second monitor with twinview, would it be a better solution to have just two screens without twinview and send the output from vlc or whatever you use to second screen in fullscreen mode?

/cab

I suppose you need to compile .debs for 64-bit edgy. 

I use TwinView and a projector as my second screen. Usually with Xine but sometimes with vlc or mplayer. When I watch a movie I just run xine/vlc/mplayer in fullscreen in the projector-part of the screen (there is an option in TwinView used to make sure that a maximized window is just maximized in one screen and don't stretch over both screens). :popcorn:

It works great, especially now when all my applications are opened in whatever screen I'm active in.

---

### Post by rubberglove on 2007-02-26
Hey Mojoman:
I am running 64-bit edgy, so I guess I'll have to make my own .debs - do you have the emails/ICQ logs that helped you make the dapper packages? I'm sure I could figure it out from there...


thanks.

---

### Post by xiota on 2007-03-23
This patch will probably not work with metacity 2.18.0+ because the code in place.c got shuffled around.  The patch seems to add "n_xineramas = 1;" at about line 921.  In 2.18.0, it should probably add at about line 863.

Metacity 2.18.0+ xinerama behavior is even more annoying than previous versions.  I start working primarily on one monitor, windows open on the other monitor.  So I switch my attention to that monitor, only to have windows start opening on the monitor I was using earlier.  Back and forth.

---

### Post by 3togo on 2007-04-10
Is there any chances to include this patch into Feisty?

---

### Post by bluevoodoo1 on 2007-04-27
> **3togo said:**
> Is there any chances to include this patch into Feisty?

I agree!

---

### Post by tich on 2007-04-27
i would also like to see this work in feisty!

so now there are 3 of us...

---

### Post by RawMustard on 2007-04-29
Wow!  first time I heard about this patch, metacity is the dogs breath with twinview, it sucks so hard the universe imploads.  Yes, yes, for feisty 32bgit and 64bit :)

---

### Post by TLE on 2007-04-29
Hey everybody
Sorry for my absence. I'm happy that some of you are interested in this. If I can get it to wok I'll be updating this soon. I'm really busy right now, but I got some time off starting May 11. So if you can wait I plan to update this for both 32 and 64 bit Ubuntu 7.04 Feisty at that time.
Regards TLE

PS: At that time I'll also be adding Mojomans 64 bit dapper packages

---

### Post by francisco_athens on 2007-04-29
I'll be looking forward to your patch for feisty as well!  I'm surprised this was not included in the release! It's a very annoying behavior.

Thank you!

Francisco

---

### Post by 3togo on 2007-05-03
We should vote for this patch be added to Feisty/Gutsy.

---

### Post by mojoman on 2007-05-04
> **3togo said:**
> We should vote for this patch be added to Feisty/Gutsy.

Yes, you should.

[http://ubuntuforums.org/showthread.php?t=426962](http://ubuntuforums.org/showthread.php?t=426962)

/mojoman

---

### Post by hihihi on 2007-05-08
thats a very nice how to.
running feisty and twinview and beryl and all seems ok, actually, the best os experience ever.
but i'm wondering if anybody here knows how to make somekind of a desktop-profile for twinview, b-caus what irritates me is when switching over from twinview to single-screen-mode, all icons and panel go to the most wrongest places... and to every-time clean it up and put in the right place is contra-productive, any hint would be very nice, sorrythanks...

---

### Post by PowerlessRacing on 2007-08-16
Long past May so I was just wondering how this is coming along for Feisty 64bit?  We really appreciate the time you put into doing this.  Thanks.

---

### Post by TLE on 2007-09-25
Sh*t guys I'm sorry. I completely forgot. I'll get something done soon.
Right now I'm looking into using the PPA for this as it will make things easier to maintain.
Regards TLE

---

### Post by elysion on 2007-10-08
Does anyone know of a same kind of thread for kwin? I'm not sure how kwin does this, guess the default is to open the window where the cursor is. Would really like to be able to change it so that I could somehow define where to open the windows. Also that "remember last state" kinda function would be sweet.

Nice thread btw. Big up for TLE! Sorry for this a bit off-topic post.

---

### Post by mojoman on 2007-10-09
> **elysion said:**
> Does anyone know of a same kind of thread for kwin? I'm not sure how kwin does this, guess the default is to open the window where the cursor is. Would really like to be able to change it so that I could somehow define where to open the windows. Also that "remember last state" kinda function would be sweet.

Nice thread btw. Big up for TLE! Sorry for this a bit off-topic post.

You could have a look at devilspie. It's in the repositories. It helps you define window behaviour (e.g. where to open it, how big etc) for specific applications though I don't think it alters the standard behaviour (e.g. cascade windows vs open window where cursor is).

/mojoman

---

### Post by alexlzl on 2008-04-26
The annoying behavior got back in Ubuntu 8.04. Just found another fix somewhere if you are using Compiz and later versions of Ubuntu. It is just a Compiz Setting change.

[http://autopragmatic.com/2007/11/11/gutsy-nvidia-twinview-window-placement/](http://autopragmatic.com/2007/11/11/gutsy-nvidia-twinview-window-placement/)

---

### Post by Clappy on 2008-09-02
I still really want to use metacity because compiz has major stuttering problems when scrolling and it's a resource hog to begin with.

Unfortunately, this patch doesn't work with metacity 2.22 . I figured out where n_xineramas is used. Can someone please help me (and others like me) decipher this code?

metacity-2.22.0/src/core/screen.c

```

meta_screen_get_natural_xinerama_list (MetaScreen *screen,
                                       int**       xineramas_list,
                                       int*        n_xineramas)
{
  const MetaXineramaScreenInfo* current;
  const MetaXineramaScreenInfo* tmp;
  GQueue* xinerama_queue;
  int* visited;
  int cur = 0;
  int i;

  *n_xineramas = screen->n_xinerama_infos;
  *xineramas_list = g_new (int, screen->n_xinerama_infos);

  /* we calculate a natural ordering by which to choose xineramas for
   * window placement.  We start at the current xinerama, and perform
   * a breadth-first search of the xineramas starting from that
   * xinerama.  We choose preferentially left, then right, then down,
   * then up.  The visitation order produced by this traversal is the
   * natural xinerama ordering.
   */

  visited = g_new (int, screen->n_xinerama_infos);
  for (i = 0; i < screen->n_xinerama_infos; i++)
    {
      visited[i] = FALSE;
    }

  current = meta_screen_get_current_xinerama (screen);
  xinerama_queue = g_queue_new ();
  g_queue_push_tail (xinerama_queue, (gpointer) current);
  visited[current->number] = TRUE;

  while (!g_queue_is_empty (xinerama_queue))
    {
      current = (const MetaXineramaScreenInfo*) 
        g_queue_pop_head (xinerama_queue);

      (*xineramas_list)[cur++] = current->number;

      /* enqueue each of the directions */
      tmp = meta_screen_get_xinerama_neighbor (screen,
                                               current->number,
                                               META_SCREEN_LEFT);
      if (tmp && !visited[tmp->number])
        {
          g_queue_push_tail (xinerama_queue,
                             (MetaXineramaScreenInfo*) tmp);
          visited[tmp->number] = TRUE;
        }
      tmp = meta_screen_get_xinerama_neighbor (screen,
                                               current->number,
                                               META_SCREEN_RIGHT);
      if (tmp && !visited[tmp->number])
        {
          g_queue_push_tail (xinerama_queue,
                             (MetaXineramaScreenInfo*) tmp);
          visited[tmp->number] = TRUE;
        }
      tmp = meta_screen_get_xinerama_neighbor (screen,
                                               current->number,
                                               META_SCREEN_UP);
      if (tmp && !visited[tmp->number])
        {
          g_queue_push_tail (xinerama_queue,
                             (MetaXineramaScreenInfo*) tmp);
          visited[tmp->number] = TRUE;
        }
      tmp = meta_screen_get_xinerama_neighbor (screen,
                                               current->number,
                                               META_SCREEN_DOWN);
      if (tmp && !visited[tmp->number])
        {
          g_queue_push_tail (xinerama_queue,
                             (MetaXineramaScreenInfo*) tmp);
          visited[tmp->number] = TRUE;
        }
    }

  /* in case we somehow missed some set of xineramas, go through the
   * visited list and add in any xineramas that were missed
   */
  for (i = 0; i < screen->n_xinerama_infos; i++)
    {
      if (visited[i] == FALSE)
        {
          (*xineramas_list)[cur++] = i;
        }
    }

  g_free (visited);
  g_queue_free (xinerama_queue);
}

```

---

### Post by HerbCSO on 2008-10-01
> **alexlzl said:**
> The annoying behavior got back in Ubuntu 8.04. Just found another fix somewhere if you are using Compiz and later versions of Ubuntu. It is just a Compiz Setting change.

[http://autopragmatic.com/2007/11/11/gutsy-nvidia-twinview-window-placement/](http://autopragmatic.com/2007/11/11/gutsy-nvidia-twinview-window-placement/)

Worked great for me in Hardy 8.04.1 - thanks!

---

