---
title: "Google Earth"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by kathrync on 2008-08-24
Hello

I have been trying to install Google Earth and I am having problems.  I have tried downloading the GoogleEarthLinux.bin file from Google and installing that, and I have also tried installing from the Medibuntu repository using Synaptic.  I have tried version 4.3 and 4.2.

In all cases, the installation appears to go fine.  However, when I try to run it, it gets as far as the splash screen (and the tab on the panel at the bottom says "initialising") and then goes no further.  My computer still runs fine, I'm not having the problem I have seen reported where your computer logs itself out.  It's just that the program never loads any further than this, and I have to force a quit.

Does anyone know what the problem is?  My initial thought is that it might be something to do with the video card, but I don't really know.  Anyone else had this problem and have a solution for me?

Thanks

Kathryn

---

### Post by billgoldberg on 2008-08-24
> **kathrync said:**
> Hello

I have been trying to install Google Earth and I am having problems.  I have tried downloading the GoogleEarthLinux.bin file from Google and installing that, and I have also tried installing from the Medibuntu repository using Synaptic.  I have tried version 4.3 and 4.2.

In all cases, the installation appears to go fine.  However, when I try to run it, it gets as far as the splash screen (and the tab on the panel at the bottom says "initialising") and then goes no further.  My computer still runs fine, I'm not having the problem I have seen reported where your computer logs itself out.  It's just that the program never loads any further than this, and I have to force a quit.

Does anyone know what the problem is?  My initial thought is that it might be something to do with the video card, but I don't really know.  Anyone else had this problem and have a solution for me?

Thanks

Kathryn

Open a terminal (applications -> accessories -> terminal).

Enter this code:

```
googleearth
```

And post the errors you get.

---

### Post by kathrync on 2008-08-24
Hi there

No errors, it just fails to do anything.

Hopefully I have managed to attach a screenshot...this was taken 10 mins after I set it to run, it just wasn't doing anything!

K

---

### Post by neurostu on 2008-08-24
The best way to download google earth is to download:
googleearth-package.

It will build a deb out of the .bin and install it correctly..

try getting googleeath-package using synaptic or apt-get  and see how that works....

---

### Post by boombox1387 on 2008-08-24
I remember trying to install Google Earth several months ago and having the exact same problem with it freezing on the splash screen.  I ended up just giving up on it, but I'll try again right now and let you know how it goes.

---

### Post by pengin on 2008-08-24
Move the googleearth.bin file to your home folder, open a terminal and type ls to check the bin files in your home folder, if it is type:
      $chmod 770 GoogleEarthLinux.bin
then type
      $sudo ./GoogleEarthLinux.bin

---

### Post by kathrync on 2008-08-24
> **neurostu said:**
> The best way to download google earth is to download:
googleearth-package.

It will build a deb out of the .bin and install it correctly..

try getting googleeath-package using synaptic or apt-get  and see how that works....

I installed this, but I didn't know how to make it work so I uninstalled it again....

---

### Post by kathrync on 2008-08-24
> **pengin said:**
> Move the googleearth.bin file to your home folder, open a terminal and type ls to check the bin files in your home folder, if it is type:
      $chmod 770 GoogleEarthLinux.bin
then type
      $sudo ./GoogleEarthLinux.bin

Is there any way I can do this without moving the bin file?  I am reluctant to move it.  I am really anal about keeping my desktop and home folder as clean as I can so I can't screw things up (something I am good at!).

---

### Post by boombox1387 on 2008-08-24
> **pengin said:**
> Move the googleearth.bin file to your home folder, open a terminal and type ls to check the bin files in your home folder, if it is type:
      $chmod 770 GoogleEarthLinux.bin
then type
      $sudo ./GoogleEarthLinux.bin

Hey thanks, this worked for me.  For some reason my screen flickers when I use Google Earth, but it also flickers when I preview screensavers, so I think it's an unrelated problem.

---

### Post by boombox1387 on 2008-08-24
> **kathrync said:**
> Is there any way I can do this without moving the bin file?  I am reluctant to move it.  I am really anal about keeping my desktop and home folder as clean as I can so I can't screw things up (something I am good at!).

As far as I know, you can delete the .bin file after you install Google Earth.  At least I did and it still seems to be working fine.

---

### Post by billgoldberg on 2008-08-24
If you have compiz fusion running, disable it.

You can do that with this command.

```
metacity --replace
```

Then try again.

---

### Post by boombox1387 on 2008-08-24
> **billgoldberg said:**
> If you have compiz fusion running, disable it.

You can do that with this command.

```
metacity --replace
```

Then try again.

Whoa!  I'm going to assume you were talking to me, because when I replaced compiz with metacity, all of my random screen flickering went away.  Any idea what causes that?  And is there anyway to do that without turning off my beautiful compiz?

---

### Post by kathrync on 2008-08-24
> **boombox1387 said:**
> As far as I know, you can delete the .bin file after you install Google Earth.  At least I did and it still seems to be working fine.

Doesn't make much difference...I just tried this and it isn't working for me anyway :(

---

### Post by billgoldberg on 2008-08-24
> **boombox1387 said:**
> Whoa!  I'm going to assume you were talking to me, because when I replaced compiz with metacity, all of my random screen flickering went away.  Any idea what causes that?  And is there anyway to do that without turning off my beautiful compiz?

Compiz requires compositing from your video card, and if you have bad drivers that might cause issues in some apps (games, google earth, compiz fusion 3d effects, ...).

Compiz Fusion is a window manager, as is metacity.

You can only use one at the time.

However metacity has some compositing, but nothing near that of compiz fusion.

---

### Post by boombox1387 on 2008-08-24
> **billgoldberg said:**
> Compiz requires compositing from your video card, and if you have bad drivers that might cause issues in some apps (games, google earth, compiz fusion 3d effects, ...).

Compiz Fusion is a window manager, as is metacity.

You can only use one at the time.

However metacity has some compositing, but nothing near that of compiz fusion.

Hmm, I recently reinstalled Ubuntu Hardy.  I think I'm using the same restricted ATI drivers as I was before, but I never noticed the whole screen flickering thing the first time around.  I'll have to reinstall some games and see if they flicker, too.  That would be a bummer.

---

### Post by boombox1387 on 2008-08-24
> **kathrync said:**
> Doesn't make much difference...I just tried this and it isn't working for me anyway :(

Still freezes on the splash screen?

I'm having some problems of my own.  Google Earth is up and running but there isn't actually an Earth, just a bunch of stars.  Maybe I'm missing something obvious, or maybe I shouldn't have deleted that .bin file... ?

---

### Post by kathrync on 2008-08-24
> **boombox1387 said:**
> Still freezes on the splash screen?

I'm having some problems of my own.  Google Earth is up and running but there isn't actually an Earth, just a bunch of stars.  Maybe I'm missing something obvious, or maybe I shouldn't have deleted that .bin file... ?


Yeah, still freezing on the splash screen :(  This might solve your problem though? [http://paulsiu.wordpress.com/2008/08/16/earth-is-missing-after-google-earth-linux-installation/](http://paulsiu.wordpress.com/2008/08/16/earth-is-missing-after-google-earth-linux-installation/)  Good luck!

---

### Post by kathrync on 2008-08-26
Bump...any more thoughts?  Problem still not solved...

---

### Post by barbedsaber on 2008-08-26
[COLOR="Red"]I AM NOT SURE ABOUT THIS, CAUTION, BLIND LEADING BLIND[/COLOR]
I think I read somewhere that googleearth sometimes misses out the earth part, so all you see is stars.
A quick workaround is to run it like this ```
sudo googleearth
```
hope that helps :)

---

### Post by silkstone on 2008-08-26
If you enable the medibuntu repos, googleearth is available through Synaptic - no need to install it manually.

---

### Post by boombox1387 on 2008-08-26
> **barbedsaber said:**
> [COLOR="Red"]I AM NOT SURE ABOUT THIS, CAUTION, BLIND LEADING BLIND[/COLOR]
I think I read somewhere that googleearth sometimes misses out the earth part, so all you see is stars.
A quick workaround is to run it like this ```
sudo googleearth
```
hope that helps :)

Thanks, the article that kathrync suggested also made it sound like an ownership problem.  I'd prefer not to always run it as root, though, so I'll try a "chown" sometime when I have a bit of free time to mess around.

Doubt this solves any of your problems though, kathrync.  I don't know a whole lot about these sorts of things, but I'll let you know if I figure out anything that may be relevant.

---

### Post by BGrigg on 2008-09-20
> **barbedsaber said:**
> [COLOR="Red"]I AM NOT SURE ABOUT THIS, CAUTION, BLIND LEADING BLIND[/COLOR]
I think I read somewhere that googleearth sometimes misses out the earth part, so all you see is stars.
A quick workaround is to run it like this ```
sudo googleearth
```
hope that helps :)

Helped me! Thanks!

---

### Post by Watchtow3r on 2008-09-20
Hey, I haven't read any of the responses and I can't help you on installing lol but when you do get Google Earth make sure to turn off the "atmosphere" setting under View... for some reason it makes it run slow as molasses on Ubuntu. Also if you have the Compiz-Fusion icon, switch to Metacity. I always do this whenever I'm viewing any video in a big window... My video messes up (flickers) if  don't. All the best!

---

### Post by Watchtow3r on 2008-09-20
Try this:

wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin) && chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin

I think this is the command I used to download it... either way i didn't do it off of google's website since I think it didn't work.

Btw thats a command I just don't know how to make it in the box.

---

### Post by Watchtow3r on 2008-09-20
> **boombox1387 said:**
> Whoa!  I'm going to assume you were talking to me, because when I replaced compiz with metacity, all of my random screen flickering went away.  Any idea what causes that?  And is there anyway to do that without turning off my beautiful compiz?

Yeah I always have this problem. Also on any videos, like youtube with fullscreen. Download from package manager the Compiz Fusion Icon. It lets you turn it on and off easily when u need it.

---

### Post by DFHIII on 2008-10-14
This procedure worked.  I am not sure what I did, but it did work.  

Dan H.

---

### Post by LowSky on 2008-10-14
> **boombox1387 said:**
> Hey thanks, this worked for me.  For some reason my screen flickers when I use Google Earth, but it also flickers when I preview screensavers, so I think it's an unrelated problem.

thats a compiz/opengl issue, turn off compiz and the flickering will stop

---

### Post by mulga on 2008-10-15
> **billgoldberg said:**
> If you have compiz fusion running, disable it.

You can do that with this command.

```
metacity --replace
```

Then try again.
This works really well, however I have to do it every time I reboot, would uninstalling Compiz fix this and would doing so cause any other problems. I am using the ATI drivers

---

### Post by TideMan on 2008-10-15
I'll ask the question I had in its own thread

---

