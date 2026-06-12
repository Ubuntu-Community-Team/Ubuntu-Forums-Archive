---
title: "[SOLVED] updating vlc (it wont update)"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-17
*_Note: Ubuntu 8.04 does not officially support Vlc 9x however since vlc no longer supports 8x I think this may be useful/necessary for some of you_*

**How To Update Vlc from 8x to 9X in Ubuntu 8.04 **_(special Thanks To **"mc4man"**)_

If you want to try a 0.9.x version you can add the *korn ppa* sources to your sources list and install 0.9.3.

Before trying to install go into synaptic, search vlc and remove vlc, vlc-nox, libvlc0, and any vlc plugins.

copy and paste the 2 lines below one at a time into System -> Administration -> Software sources -> Third-party Sources -> add.       (these are the _korn ppa_ sources)
```
deb http://ppa.launchpad.net/c-korn/ubuntu hardy main

deb-src http://ppa.launchpad.net/c-korn/ubuntu hardy main
```

Now Go to Terminal and enter the following.
```
 sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

[B]Congrats. You now have VLC 9.3
[/B]

If you try 0.9.3 from (*korn ppa*) and want 0.9.5 with 'embedded' video enabled and for the bug fixes follow the directions below.

_***Note: This Is Only For Ubuntu 8.04 Hardy***_
**You must still have the *korn ppa* sources (listed above) enabled as a software source for this to work.**

All the needed .debs are in a *.7z* file, archive manager can extract as long as *p7zip* is installed. If you don't already have *p7zip* you can install it by entering the following code in terminal.
```
sudo apt-get install p7zip
```

From here download the *install.7z* file

[http://download151.mediafire.com/9bxe6mbydxxg/mwymzmzgvyj/install.7z](http://download151.mediafire.com/9bxe6mbydxxg/mwymzmzgvyj/install.7z)    
*Note: this download was provided to us from "mc4man" himself (thanks again "mc4man")*

Extract it to your *"Home"* folder (It will create a file called *"install"*). Once you have done this we can install it by entering the following code in Terminal

```
cd install && sudo dpkg -i *.deb
```  

Thats it You are done. Again, many thanks to **"mc4man"** without his help this would not have been possible!!!!!!!!!!!

*_A Side Note From "mc4man"_*
> **mc4man said:**
> 

Hardy uses libdvdnav4-0.1.10 which is perfectly fine. There are though some titles that won't playback due to a udf structure protection. In *many* but not *all* cases using a patched libdvdnav4 would resolve.
There are now some newer versions of libdvdnav4 available which have already been patched.

Version 4.1.2-3 is fully compatible with hardy and vlc. 
I'd be careful of Version 4.1.3-1 which is only needed for the dvdnav enabled mplayer.

Can be gotten here 
[http://packages.ubuntu.com/intrepid/libdvdnav4](http://packages.ubuntu.com/intrepid/libdvdnav4)
[B]
Do not[/B] uninstall current version of libdvdnav4, just download and let GDebi handle the install if the need to use this version arises (in region 1 limited to some New line releases, more widespread in regions 2, 4


_*Some Known Issues from "mc4man"*_:

> **mc4man said:**
> there are some things that don't work or work right in vlc 0.9.x

I'm continuing to have no issues though with the 'embedded'.

As far as 'other' issues, I think that comes down to one's use. 

For me it's accessing a video_ts dir. from vlc is broken, though opening vlc from the video_ts dir. works.

The other minor issue for me is the equalizer only stays enabled for one track.

side note: just built the latest 1.0 unstable with 'embedded' enabled, again no issues.
Whether it's ubuntu, my hardware or combo of the two don't know, post back if vlc shows problems or crashes at random.

---

### Post by bennachie on 2008-11-17
Perhaps the version on your chosen repository is still 8.6?

---

### Post by SuperSonic4 on 2008-11-17
It is 8.04 offers 0.8.x

---

### Post by nakama85 on 2008-11-17
> **bennachie said:**
> Perhaps the version on your chosen repository is still 8.6?

vlc's website just says to make sure that I have the multiverse repository activated. I double checked and it is.

Is there another repository i could get it from maybe?

I'm not sure what else to do

---

### Post by SuperSonic4 on 2008-11-17
You could build it from source or risk putting intrepid sources onto your hardy sources.list but i wouldnt recommend it

---

### Post by nakama85 on 2008-11-17
> **SuperSonic4 said:**
> It is 8.04 offers 0.8.x

so if it wont update is there a way to get it?

---

### Post by SuperSonic4 on 2008-11-17
It won't update because the people maintaining the hardy repo have not added a deb of vlc 0.9x to their servers

---

### Post by nakama85 on 2008-11-17
> **SuperSonic4 said:**
> You could build it from source or risk putting intrepid sources onto your hardy sources.list but i wouldnt recommend it

I wish I new how to build it from source...(is there someplace i could learn)

Do you think it will eventually be offered for 8.04

---

### Post by nakama85 on 2008-11-17
does anyone know of a safe repo i could get it from?

---

### Post by mc4man on 2008-11-18
If you want to try a 0.9.x version you can add the korn ppa to your sources and install 0.9.3.
[https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive)

Before trying to install go into synaptic, search vlc and remove vlc, vlc-nox, libvlc0, and any vlc plugins.

At the link above you would switch the "Display sources.list entries for:" entry to hardy and copy and paste the 2 lines one at a time into System -> Administration -> Software sources -> Third-party Sources -> add.


Note; 
The korn ppa had been offering 0.9.5 but went back to the 0.9.3 build because it had 'embedded' video enabled which starting with 0.9.4 has been disabled in the vlc source and remains so even in the 1.0 unstable.

Personally i think this was a mistake, the qt interface itself is what's 'broken' and the 'potential' for issues exists in all 0.9.x versions.
The 'embedded' video can be easily reenabled in any 0.9.x source before building and 0.9.6 has less bugs and security issues than .3, .4, .5., ( though the few regressions I've seen still remain, even in the 1.0 i just did.

Some setups are are affected by the 'embedded' video, others aren't. I myself have had no problems, am currently running built versions of .5 and .6 with 'embedded' enabled just fine.
So installing the korn 0.9.3 should give you a good idea if it's an issue for you, and allow you to see if you even want the 0.9 vlc.

In the long run building your own versions is the best way to go, you don't need to install it, after the build (make), vlc can be run from the build folder, you can enable 'embedded' if you want and build new versions as they're released.
Hopefully at some point they will release a 'keeper'

If you try 0.9.3 and want 0.9.5 with 'embedded' enabled for the bug fixes that could be possible. When korn was offering .5 with 'embedded' disabled i redid his package set, enabling the 'embedded' video.
I only uploaded the vlc package, the rest could be had from his repo which is no longer possible.
Three out of the thirteen are needed, the rest are optional. see screen.
If you really want I'll upload what you need to mediafire.

---

### Post by PierreDeKat on 2008-11-18
What mc4man said.

---

### Post by sabitha on 2008-11-18
> **mc4man said:**
> If you want to try a 0.9.x version you can add the korn ppa to your sources and install 0.9.3.
[https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive)

Before trying to install go into synaptic, search vlc and remove vlc, vlc-nox, libvlc0, and any vlc plugins.

At the link above you would switch the "Display sources.list entries for:" entry to hardy and copy and paste the 2 lines one at a time into System -> Administration -> Software sources -> Third-party Sources -> add.


Note; 
The korn ppa had been offering 0.9.5 but went back to the 0.9.3 build because it had 'embedded' video enabled which starting with 0.9.4 has been disabled in the vlc source and remains so even in the 1.0 unstable.

Personally i think this was a mistake, the qt interface itself is what's 'broken' and the 'potential' for issues exists in all 0.9.x versions.
The 'embedded' video can be easily reenabled in any 0.9.x source before building and 0.9.6 has less bugs and security issues than .3, .4, .5., ( though the few regressions I've seen still remain, even in the 1.0 i just did.

Some setups are are affected by the 'embedded' video, others aren't. I myself have had no problems, am currently running built versions of .5 and .6 with 'embedded' enabled just fine.
So installing the korn 0.9.3 should give you a good idea if it's an issue for you, and allow you to see if you even want the 0.9 vlc.

In the long run building your own versions is the best way to go, you don't need to install it, after the build (make), vlc can be run from the build folder, you can enable 'embedded' if you want and build new versions as they're released.
Hopefully at some point they will release a 'keeper'

If you try 0.9.3 and want 0.9.5 with 'embedded' enabled for the bug fixes that could be possible. When korn was offering .5 with 'embedded' disabled i redid his package set, enabling the 'embedded' video.
I only uploaded the vlc package, the rest could be had from his repo which is no longer possible.
Three out of the thirteen are needed, the rest are optional. see screen.
If you really want I'll upload what you need to mediafire.

I need to try this 
please upload :D

---

### Post by mc4man on 2008-11-18
@ sabitha
I can probably do that tonight, plus I'd want to test it first on one of my boxes as to what at a min. you'd need to install.

You definitely would need to install any 0.9x version first and confirm that it runs. IIRC when you first install 0.9.x on hardy there's more needed than just the vlc packages. (don't actually remember, atm I'm just running versions from their build folders.

So I'd add korn as a source, install 0.9.3, ck it out and ck. back here later. Plus as noted  you'll see if embedded is an issue (at least at first, can be a random timing thing) and whether you want 0.9 at all. (it does have issues

---

### Post by mc4man on 2008-11-18
Here you go

for hardy only

i put all the needed .debs in a .7z file, archive manager can extract as long as p7zip is installed, if that's a problem I'll redo or upload the .debs separately

```
 sudo apt-get install p7zip
```


You should/must have the korn ppa enabled as a software source and his vlc 0.9.3 installed. Vlc and vlc-nox have a lot of dependencies, libass is one you'll need from korn.
If you install 0.9.3 from korn your good to go.

No need to uninstall first.

From here download the install.7z file (the vlc file is previous upload, don't use unless your running korn's 0.9.5 with 'embedded' disabled and want to try 'embedded' enabled. 

[http://www.mediafire.com/?sharekey=c4620fa470d481e2d2db6fb9a8902bda](http://www.mediafire.com/?sharekey=c4620fa470d481e2d2db6fb9a8902bda)

Extract to home folder (will extract to a folder named install

Then in terminal run
```

 cd install && sudo dpkg -i *.deb
```

Note : before running command open the install folder and if you don't want the mozilla plugin remove it. The alsa plugin also is in there, not really needed, (dummy package, no harm either way

you should see this in terminal

> doug@doug-desktop:~$ cd install && sudo dpkg -i *deb
[sudo] password for doug: 
(Reading database ... 124567 files and directories currently installed.)
Preparing to replace libvlc0 0.9.3+x264snapshot20080928+faad2.6.1+1-1~ppa1 (using libvlc0_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb) ...
Unpacking replacement libvlc0 ...
Selecting previously deselected package mozilla-plugin-vlc.
Unpacking mozilla-plugin-vlc (from mozilla-plugin-vlc_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb) ...
Preparing to replace vlc 0.9.3+x264snapshot20080928+faad2.6.1+1-1~ppa1 (using vlc_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb) ...
Unpacking replacement vlc ...
Preparing to replace vlc-nox 0.9.3+x264snapshot20080928+faad2.6.1+1-1~ppa1 (using vlc-nox_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb) ...
Unpacking replacement vlc-nox ...
Preparing to replace vlc-plugin-pulse 0.9.3+x264snapshot20080928+faad2.6.1+1-1~ppa1 (using vlc-plugin-pulse_0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1_i386.deb) ...
Unpacking replacement vlc-plugin-pulse ...
Setting up libvlc0 (0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1) ...

Setting up vlc-nox (0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1) ...
Setting up vlc-plugin-pulse (0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1) ...
Setting up vlc (0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1) ...

Setting up mozilla-plugin-vlc (0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
doug@doug-desktop:~/install$ 

---

### Post by sabitha on 2008-11-18
thanks 'mc4man' :D
its work perfect :popcorn:

---

### Post by mc4man on 2008-11-18
> its work perfect

time will tell there, there are some things that don't work or work right in vlc 0.9.x

I'm continuing to have no issues though with the 'embedded'.

As far as 'other' issues, I think that comes down to one's use. 

For me it's accessing a video_ts dir. from vlc is broken, though opening vlc from the video_ts dir. works.

The other minor issue for me is the equalizer only stays enabled for one track.

side note: just built the latest 1.0 unstable with 'embedded' enabled, again no issues.
Whether it's ubuntu, my hardware or combo of the two don't know, post back if vlc shows problems or crashes at random.

---

### Post by nakama85 on 2008-11-18
THANKS "MC4MAN" your the best.
Would You mind If I write a tut. Based on the info you gave..(thanking you ofcourse)

---

### Post by nakama85 on 2008-11-18
bump

---

### Post by mc4man on 2008-11-18
@ nakama85

feel free
In some regards though this is just a temp. thing to allow people to try out the 'embedded video' on hardy and gain whatever bug fixes vs. 0.9.3

hopefully someone if not korn will continue to release a proper .deb package set of future releases of vlc 0.9.x (or even 1.0 when that day arrives.

Whether or not they'll enable 'embedded' is a question mark and may depend on if it's 'fixed'. Videolan does consider it broken, as seen in the latest source, notice the comment

> #if 0 /* this is totally broken */
    add_submodule ()
        set_capability( "vout window", 50 )
        set_callbacks( WindowOpen, WindowClose )

It's basically fairly easy and quick to 'redo' an existing package or set of from their sources, in this case there were a couple of tricky spots during the build but overall it was/is easy. On the other hand building vlc into a proper package set like korn isn't trival and quite honestly beyond me.
But if future packages are released without embedded enabled then we'll keep redoing them for those that want to try/use.

Hope this is a little perspective for you

note on vlc in hardy
Hardy uses libdvdnav4-0.1.10 which is perfectly fine. There are though some titles that won't playback due to a udf structure protection. In *many* but not *all* cases using a patched libdvdnav4 would resolve.
There are now some newer versions of libdvdnav4 available which have already been patched.

Version 4.1.2-3 is fully compatible with hardy and vlc. 
I'd be careful of Version 4.1.3-1 which is only needed for the dvdnav enabled mplayer.

Can be gotten here 
[http://packages.ubuntu.com/intrepid/libdvdnav4](http://packages.ubuntu.com/intrepid/libdvdnav4)
[B]
Do not[/B] uninstall current version of libdvdnav4, just download and let GDebi handle the install if the need to use this version arises (in region 1 limited to some New line releases, more widespread in regions 2, 4

---

### Post by nakama85 on 2008-11-18
> **mc4man said:**
> @ nakama85

feel free


Thanks For Everything mc4man
Here is the thread where I posted the tutorial for now. I may post it other places as well in the future.
[http://ubuntuforums.org/showthread.php?t=986781](http://ubuntuforums.org/showthread.php?t=986781)

question: will the install.7z download link expire at any point?
if so please let me know so that i can upload it to a more permanent server.

Thanks again

---

### Post by mc4man on 2008-11-18
> expire at any point?
No, it will stay good.
I'm fairly impressed with mediafire, doesn't seem like they bombard users with pop ups, ect.

Edit: I figure you installed 0.9.3 last night, may be useful if you ck. in synaptic -> file ->  history and see what additional packages were installed when you installed 0.9.3 and make a list.

---

