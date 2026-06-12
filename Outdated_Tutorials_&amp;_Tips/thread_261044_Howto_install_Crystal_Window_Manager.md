---
title: "Howto install Crystal Window Manager"
date: 2006-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by ago on 2006-09-19
I am writing this from crystal (fvwm based) it is a light an nice window manager. 

[img]http://polishlinux.org/reviews/fvwm-crystal/fvwm_crystal_top_level_thumb.png[/img]

The package is now in Edgy (universe), all you need is to enable universe repository and execute:

sudo apt-get install fvwm-crystal

Then logout and change the session when you login again. If you do not have Edgy, or want to try a newer version, execute the following in a terminal (you may want to change the version number to the latest one).

```

sudo apt-get install fvwm python imagemagick rox-filer\
 xscreensaver trayer gksu aterm habak mpd mpc
wget http://download.gna.org/fvwm-crystal/3.0.4/fvwm-crystal-3.0.4.tar.gz
tar xvzf fvwm-crystal-3.0.4.tar.gz
cd fvwm-crystal-3.0.4
sudo make install
sudo cp addons/fvwm-crystal.desktop /usr/share/xsessions/

```

To findo out more: 

[http://polishlinux.org/apps/fvwm-crystal-speed-and-transparency/](http://polishlinux.org/apps/fvwm-crystal-speed-and-transparency/)
[http://fvwm-crystal.org/](http://fvwm-crystal.org/)

---

### Post by grizzly on 2006-09-20
funny, I was looking for it just now! :) hehe.

thanks a lot! 
One question: is this still as customixable as fvwm? i.e is it like fvwm but with a very nice config? 
If it is then i think it would be a good idea to rename the topic to fvwm-crystal.. just to kill possible confuion

thanks again

---

### Post by Defkor on 2006-09-21
Hi,

I tried to enter the apt-get command above but fvwm and a number of other programs(rox_filer, aterm, etc...) were not in the default repository I had setup.  Do you know what repository they're in.

Thanks

---

### Post by zenrox on 2006-09-21
enable the universe repo maby the multiverse

---

### Post by calvinthomas on 2006-09-21
I didn't even know this existed and even though I have a fairly fast machine, I still really like this! I think its very clean and looks good, its also intuitive to use and seriously fast! I don't think i'll use it as my main desktop but i'll keep it on to play around with!

Calv

---

### Post by skip910 on 2006-09-21
Alright, I executed all the things in terminal and installed everything.

I went into a new session... what do I do now? I was messing with it to try and make it looks like the screenshot, but that was to no avail.

---

### Post by calvinthomas on 2006-09-21
For me I copied and pasted into the terminal the info from the first post waited for it to finish, logged out, went to sessions, changed the session to foo and logged in and it looked very similar to the screenshot straightaway!

Calv

---

### Post by skip910 on 2006-09-21
Oh, I got it, thanks.

---

### Post by jcrnan on 2006-09-21
I also have some packs missing from repositories and I have both universe and multiverse enabled. any tips?

---

### Post by BLTicklemonster on 2006-09-21
Sweet, and I didn't have to redo my nvidia drivers like I do when I change from kde to gnome or vice versa. Ummm, I can't find anything now. lol

---

### Post by jcrnan on 2006-09-22
uhm, I think I got it working, but it looks like crap, nowhere near the screenshot.. its like a 10 year ld linux or something. I think I might it might be fvwm but with no crystal thing.

---

### Post by Sukarn on 2006-09-24
I am installing it right now, but from what I have heard, you have to modify it to get it all cool-looking. Its default interface is supposed to be simple and very customisable.

---

### Post by fenwik on 2006-09-24
I got it to look nice by using nautilus as the desktop manager, but I have two problems keeping me from liking it. 

Whenever I login after setting nautilus as the desktop manager, nautilus takes over, i.e. when I right click on the desktop, instead of getting the terminal, I get the nautilus desktop menu. I hope that made sense. 

The second problem I have is, I can't figure out how to add more applications to the menu.

---

### Post by michux on 2006-09-29
> **Sukarn said:**
> I am installing it right now, but from what I have heard, you have to modify it to get it all cool-looking. Its default interface is supposed to be simple and very customisable.

Not quite. The default looks is a bit different, that's right. But the only thing to do to make it look like on the screenshot is to change the used **Recipe** from the menu and restart Crystal (that just restarts the WM, all the apps and stuff is stay).

michuk

---

### Post by michux on 2006-09-29
> **fenwik said:**
> Whenever I login after setting nautilus as the desktop manager, nautilus takes over, i.e. when I right click on the desktop, instead of getting the terminal, I get the nautilus desktop menu. I hope that made sense. 

Not sure it that's solvable. I use ROX as a desktop and file manager in Crystal and it works just as good (and way faster than Nautilus). ROX has an option to take over the mouse clicks or leave the WM handle them. Perhaps you can set Nautilus to do the same somehow...

> **fenwik said:**
> The second problem I have is, I can't figure out how to add more applications to the menu.

Take a look at this folder: [em]~/.fvwm/Applications[/em]. It contains the list of apps to be displayed in your Applications menu. Just add more apps there and you should be at home again :)

Best regards,
michuk

---

### Post by BLTicklemonster on 2006-10-03
Note to self:

I think this is supposed to be all one line, try it again:

sudo apt-get install fvwm python imagemagick rox-filer\
 xscreensaver trayer gksu aterm habak mpd mpc

or is it?

I have redone dapper because I thought I was "all that and a bag of chips" and tried edgy. needless to say, I'm having to redo stuff. I liked the window manager pretty much, so I'm giving it another shot. Just at the house for lunch, tried it and only had nvrm and poot or some wierd window manager, nvrm was like totally wrong! but the other one was like crystal, but missing some things (tried streamtuner and heard music but no player showed up! odd)

---

### Post by BLTicklemonster on 2006-10-03
Ah, it foo that I have to open and it looks a lot like what I used before, but it's not as polished. 

Those two lines I posted above, I can't get them to work either separately or together. I have xscreensaver, imagemagick, and fvwm, why can't I get crystal, I wonder?

*edit:

Huh. on a lark, in foo, I tried the lines again, just copied and pasted, and this time in started installing. But I get this at the end: 
MPD system service not installed

A problem? Not sure, I'm logging out to see if crystal is there.

*edit:
well, I still have to use foo, but this is what I remembered. whew.

---

### Post by xtra2000 on 2006-11-25
I want to know how to change the session name from "foo" to "fvwm-crystal". Any ideas?

---

### Post by wounded on 2006-11-26
I've been using that since Edgy came out.

[http://img89.imageshack.us/img89/1879/snapshot2xv4.png](http://img89.imageshack.us/img89/1879/snapshot2xv4.png)

It's almost identical to the screenshot in the first post except that there is a taskbar at the bottom instead of iconified windows (But that may not be hard to alter if you know more about fvwm than i do at this point).

---

### Post by K.Mandla on 2007-01-03
I don't remember how I found this window manager, but I love it to death. Fast, light and has enormous potential for older hardware. I even put it on a 300Mhz Pentium II machine with a 2Mb NeoMagic video card, and I have transparent window decorations! Amazing! I didn't think it was possible outside of Beryl to get that kind of eye candy on such ancient hardware.

I use a slightly different installation method; FVWM-Crystal is in the repositories (v3.0.3, though), so I just install *xorg* and *fvwm-crystal*, then download the 3.0.4 tarball, like described in the OP. Untar and *sudo make install* over top the 3.0.3 you just put into place. Check to make sure the 3.0.4 version is running by opening the About dialog.

One point I did notice: There seems to be a lag on certain systems if you use the Default with ACPI recipe; I think that has something to do with the desktop indicators polling hardware that doesn't exist. (Correction: Scratch that. It's ACPI on the machine I use. I disabled it and it's fine. Unrelated to FVWM-Crystal.)

Otherwise, I think anyone with a sub-500Mhz machine will fall in love with this stuff. Who needs Beryl if you can get translucent desktop interfaces on a 300Mhz machine? (Well, maybe that's pushing it. :roll: ) Cheers!

---

### Post by ThomasAdam on 2007-01-04
> **grizzly said:**
> funny, I was looking for it just now! :) hehe.

thanks a lot! 
One question: is this still as customixable as fvwm? i.e is it like fvwm but with a very nice config? 
If it is then i think it would be a good idea to rename the topic to fvwm-crystal.. just to kill possible confuion

thanks again

[http://starshine.org/xteddy/thomas/fvwm/fvwmchanfaq.html#c13](http://starshine.org/xteddy/thomas/fvwm/fvwmchanfaq.html#c13)

---

### Post by BLTicklemonster on 2007-01-05
Someone is giving me an older computer in a few days, so I'm going to be testing crystal, icewm, and fluxbox, at least on it. Possibly also going to test windowmaker and enlightenment if I get daring.

I want to set it to the side and use it as an inhouse server for music and image files we all would rather not keep hogging our respective hard drives.

---

### Post by BLTicklemonster on 2007-01-06
Just installed it again, and all I have is basic fvwm.

*edit:

so I went to the repositories and installed it, lol.

---

### Post by K.Mandla on 2007-01-06
How's it look?

---

### Post by BLTicklemonster on 2007-01-06
As advertised. Now to find out where to tweak stuff. I don't like terminal coming up when I right click the desktop, and I need locomo or is it lomoco... to load automatically along with xmodmap. I'd used it before, so I knew what to expect. I can say that navigating the toolbar can be an adventure :).

---

### Post by ago on 2007-01-07
Note that the package is now in Edgy (universe), all you need is:

sudo apt-get install fvwm-crystal

Then logout and change the session when you login again

---

### Post by erv2 on 2007-01-10
i am using 6.10 server on vmware player.

after i did "sudo apt-get install fvwm-crystal", it downloaded, configured, installed with no problem.

but when i reset, and tried "startx", it says command not found

how do i start up fvwm?

i m a newbie, please excuse my lack of knowledge.

---

### Post by K.Mandla on 2007-01-21
> **erv2 said:**
> i am using 6.10 server on vmware player.

after i did "sudo apt-get install fvwm-crystal", it downloaded, configured, installed with no problem.

but when i reset, and tried "startx", it says command not found

how do i start up fvwm?

i m a newbie, please excuse my lack of knowledge.
You need to install *xorg* too. The startx command is part of the *xorg* package; just installing *fvwm-crystal* doesn't include that one.

---

### Post by K.Mandla on 2007-01-21
There's a page in the wiki now for [FVWM-Crystal]("https://help.ubuntu.com/community/FVWM-Crystal"). Jump in!

---

### Post by noalternative on 2007-02-12
It can also be installed on Dapper with a deb file, if you use [this file]("http://mirror.linux.org.mt/mirror/ubuntu/pool/universe/f/fvwm-crystal/fvwm-crystal_3.0.3-3_all.deb").
 
               Oh here is [my screens]("http://ubuntuforums.org/gallery/showphoto.php?photo=4999&nocache=1")[ho]("http://ubuntuforums.org/gallery/showphoto.php?photo=4999&nocache=1")t running it on Dapper Drake xubuntu.
 
               sudo dpkg -i fvwm-crystal*
 
               You'll probably get dependency errors at this point.
 
               sudo apt-get -f install
 
               That will install the dependencies and configure fvwm-crystal.

---

### Post by Campitor on 2007-02-13
I've installed it on a pentium II, with 128 of ram and runs perfectly.  I juist have two questions.

1)  I have been using my rhythmbox collection to play music, but I can figure out how to use the mpd mpc combo in fvwm.  I tried doing:

ls ~/Music/ | mpc add

but I can't get the blody thing to get my mp3's into the play list.  Any suggestions?

2). I don't have an ~/.fvwm-crystal. All I have is a .fvwm.  Do I have to create the .fvwm-crystal folder, or will fvwm-crystal use the nomral one (~/.fvwm/)  I want to modify the focus behaviour ( is driving me nuts).

thanks for any replies

camp.

---

