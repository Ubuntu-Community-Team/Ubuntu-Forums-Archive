---
title: "How do I install VLC 1.1.11 in Ubuntu 12.04?"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by Asday on 2013-04-11
Pardon the language.  I have yet to successfully install *ANYTHING* from source ever, and I am slowly losing faith.

Thankfully, apt is pretty kickass, and I've done well enough with it up until now, but installing old versions of things is apparently meant to be difficult.

And so, when I find myself with a need to use an old version of VLC ([http://bogy.mine.nu/sc2/stream2vlc.php](http://bogy.mine.nu/sc2/stream2vlc.php)), fifty different error codes, and the fact I can't do anything but run from a livedisc, I end up here.

First up, doing things like "./configure" didn't actually do anything, and I trial and errored my way into using "bash configure", which of course is terrible.  At some point later I was instructed to install build-essential, which worked nicely.

So, I get into the configure script, (from the source I downloaded), and it complains about not having lua.  I try to use my intuition and "sudo apt-get install lua", and nothing happens.  Especially nothing useful like telling my what package I might actually be wanting, so off to Google it was.  Google gave me some incomprehensible package name like "libclua5.1turnaroundtouchtheground" which I would have had much trouble guessing.

Next up, the configure script complains about something else, and I believe at this point I just kept adding switches like --disable-anycoolfeatures, until it came up with something about some "xcb" packages, which were pretty difficult and unintuitive to find, too.

Something like an hour after I started, and after disabling anything which might have made the time worth anything, the configure script finished without too many errors, and I tried a "make install".  That failed pretty instantly and I saw a message about permissions, so I chucked a sudo in there.  It failed again, and I was frustrated, so I gave up, and started trying to run stuff in /bin.  "vlc" had a padlock over the icon, and I was unable to run it, so another sudo.  NOPE, vlc doesn't want to be run as root.

OK, SCREW IT, deleted everything.

Found [this](http://www.jbkempf.com/blog/post/2009/03/03/Howto-build-VLC-1.0.0-git-in-Ubuntu-in-less-than-5-commands), and tried to follow it, but "apt-get build-dep vlc" failed with "unable to find a source package for vlc", which happens to become a bit of a theme.

There was also [one more site](https://launchpad.net/ubuntu/oneiric/amd64/vlc/1.1.11-2build2) I found.  I began the arduous task of following dependencies around and trying over and over to run the .deb I had, but I got stuck on build-dep vlc again.

Perhaps I'm a simpletone with my windows background, but jesus this was a hell of a lot easier there.

**SO.  Could anyone hold my dainty little hand, and get me from an ubuntu 12.04 desktop (right after clicking "Try Ubuntu") to a working copy of VLC1.1.11?**

---

### Post by Derxst on 2013-04-11
To be clear, you are clicking "Try Ubuntu" and not working from an installed copy, correct?

---

### Post by Asday on 2013-04-12
That's correct.  My previously working windows install has decided to not be working any more, and I'm inside a livedisc to try and fix it.

---

### Post by Kopkins on 2013-04-12
[quote=Asday][INDENT]                     That's correct.  My previously working windows install has decided  to not be working any more, and I'm inside a livedisc to try and fix it.                 
[/INDENT]
            
                         
[/quote]

Why do you need VLC to fix your windows?

Try [this]("https://help.ubuntu.com/community/CompilingEasyHowTo")

Edit: I'm working on trying to build vlc in a live cd now. I'm still downloading basic tools right now though.

I started up a liveCD and the build went pretty far before the environment ran out of space. I gave it a lot more RAM now so hopefully it will get farther. I have to start over with the information you need because the liveCD dumped the memory to keep running. So the post I had typed up for you didn't get posted.

---

### Post by Kopkins on 2013-04-12
First I wanted to address something you mentioned earlier. You said that this is so much harder than in windows. While this might be true remember that Windows doesn't even have a live CD. So it's technically infinitely easier to do it in linux since it's impossibe in windows. And even while you are doing this consider that you don't *actually *have a system you're installing things on. Which is what makes it so difficult. And remember that as soon as you reboot you will lose everything we are about to do. (because after all everything here is not actually installed on anything)

Okay so here's what I did to get the package to build. First, go to System-Settings > Update & Software > Ubuntu Software. And check all the software boxes so you can get what you need. Then open a terminal and ```
sudo apt-get update
``` then you need to install your stuff ```
sudo apt-get install build-essential checkinstall cpp-4.7 dpkg-dev fakeroot g++ g++-4.7 gcc-4.7 gcc-4.7-base libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl libgcc-4.7-dev libgcc1 libgomp1 libitm1 libquadmath0 libstdc++6 libstdc++6-4.7-dev libdbus-1-dev lua5.1 libavcodec-dev libavformat-dev libswscale-dev libpostproc-dev xcb
```

While that is doing its thing, download your source package [https://launchpad.net/ubuntu/+archive/primary/+files/vlc_1.1.11.orig.tar.bz2](https://launchpad.net/ubuntu/+archive/primary/+files/vlc_1.1.11.orig.tar.bz2)

After your stuff is downloaded go to the download and unpack it ```
cd ~/Downloads
tar -xvf vlc_1.1.11.orig.tar.bz2
cd vlc_1.1.11
```

Then you should be able to build. Mine is still building. ```
./configure --disable-lua --disable-mad --disable-a52
```
The flags on the end disable lua and libmad. Libmad and a52 had to be externally downloaded so I disabled it for simplicity and lua is installed as lua5.1 but it doesn't recognize it so disable it to allow it to continue.

Best of luck.
Let us know how it goes.

Kopkins

EDIT: Okay I ran into a problem with XCB. Even though it is installed it won't recognize it so I have to edit some stuff in some of the files to see if I can get it working. Feel free to try. I have to go to class now, and I'm busy this weekend so I don't know when I can work on this again. Good luck, 

Kopkins

---

### Post by Asday on 2013-04-12
> **Kopkins said:**
> Why do you need VLC to fix your windows?

Try [this]("https://help.ubuntu.com/community/CompilingEasyHowTo")

Edit: I'm working on trying to build vlc in a live cd now. I'm still downloading basic tools right now though.

I started up a liveCD and the build went pretty far before the environment ran out of space. I gave it a lot more RAM now so hopefully it will get farther. I have to start over with the information you need because the liveCD dumped the memory to keep running. So the post I had typed up for you didn't get posted.

I don't.  Windows can go take a running jump.  VLC is to entertain me until I figure out how to fix it.

From your link, I got to [AutoDeb](https://wiki.ubuntu.com/AutoDeb), which, given the vlc-1.1.9 tarball, is hanging, in a promising fashion.  I'll report back when it does something cool.

@Kopkins:

Yep, windows is pretty crap, and Linux is pretty amazing.  Annoyingly, I have need to use windows for the majority of the time, though, so the point is moot.

I thank you for the detailed instructions, and will report back shortly after trying out AutoDeb, if it doesn't work.

Hell, even if it does work.  You never know, I might learn something, (and it's only proper, as you took the time to help me).

---

### Post by Kopkins on 2013-04-12
do you need that version? vlc is easy otherwise. sudo apt-get install vlc.

---

### Post by Asday on 2013-04-12
Yes.  Refer to the link in my opening post.

---

### Post by Asday on 2013-04-12
Ok, so autodeb ran for about 5 hours while I watched stupid youtube videos, and all it succeeded in doing was installing Lua about 10 times, and making sure it can square root things (amongst other tasks).

I'll be trying your method tomorrow morning, Kopkins; for now, I'm retiring, as this entire effort has yet again depressed me.

EDIT:  Oh wow, a few more than 10 times.  Here's the log from when I hit ^C.

checking for ssize_t... ^CWarning: APT is removing packages (do NOT interrupt)
Removing package(s) liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev liblua5.1-0-dev... (90%)
(Reading database ... 158360 files and directories currently installed.)
Removing liblua5.1-0-dev ...
ERROR: Build aborted. Incomplete build tree is in '/tmp/tmp.KKUUvsHrGW/vlc-1.1.9'.

---

### Post by andrew.46 on 2013-04-12
Perhaps use some of the techniques described here:

[https://help.ubuntu.com/community/CompileVLC](https://help.ubuntu.com/community/CompileVLC)

---

### Post by Asday on 2013-04-12
Golly.

WELP, I'll be looking at that after Kopkins' method.  I'm worried that will install some libraries of too great a version?  I noticed vlc-1.1.xx wanted some packages "=x.x.xx" instead of ">=x.x.xx" version.

---

