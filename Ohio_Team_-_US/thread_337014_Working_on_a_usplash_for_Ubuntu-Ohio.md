---
title: "Working on a usplash for Ubuntu-Ohio"
date: 2007-01-12
forum: Ohio Team - US
---

### Post by zerhacke on 2007-01-12
I've made no real progress other than putting together an image for it, but I'm at work trying to put together a custom usplash for the Ubuntu-Ohio group.  I have the C source and makefile tonic on this forum used to create his Peace usplash, so now I'm basically reverse engineering how he did it.  I think it's just a matter of making images for different resolutions.

I gotta say it, I'm no programmer so I really don't know what I'm doing.  I'm going to contact tonic and ask him for a step by step.

My work so far can be found at [http://creaturefeature.darkness.com/Ubuntu-Ohio](http://creaturefeature.darkness.com/Ubuntu-Ohio) but you gotta remember, I have figured out nothing yet.

---

### Post by zerhacke on 2007-01-12
Eureka!  I have done it!

What I did was went to the terminal and apt-get source usplash-theme-ubuntu.  This gave me a tar.gz file in my home folder.  I unzipped the archive into its own folder, went in to the folder, and started editing images.  There's several images to edit all of different resolutions so this took some time.

Since there's a makefile in that archive I decided to see if it would make.  It would not.  I figured out that I was missing some programs needed to compile a usplash.

You will need the following packages: build-essential, usplash-dev

Once I had those packages I ran the makefile again and presto, usplash.so object!

To install: 

```
sudo cp usplash-theme-ubuntu-ohio-us.so /usr/lib/usplash/usplash-theme-ubuntu-ohio-us.so
sudo ln -sf /usr/lib/usplash/usplash-theme-ubuntu-ohio-us.so /usr/lib/usplash/usplash-artwork.so
sudo update-initramfs -u
```

In the terminal, of course.

You can get a pre-compiled usplash by going to [http://creaturefeature.darkness.com/Ubuntu-Ohio/](http://creaturefeature.darkness.com/Ubuntu-Ohio/)

---

### Post by jpeddicord on 2007-01-12
It looks like a nice usplash, however remember that if you want it to be distributed you will have to separate the Ubuntu logo and the flag.

Hehe, pretty soon we'll be distributing customized Ubuntu-Ohio branded CDs! :) 

Nice work!

---

### Post by msak007 on 2007-01-13
Can you post a screenshot of what the usplash looks like?

---

### Post by zerhacke on 2007-01-13
> **msak007 said:**
> Can you post a screenshot of what the usplash looks like?

Sure can, here it is in 1024X768 resolution.  The other resolutions all look the same.

---

### Post by zerhacke on 2007-01-13
> **jacobmp92 said:**
> It looks like a nice usplash, however remember that if you want it to be distributed you will have to separate the Ubuntu logo and the flag.

Hehe, pretty soon we'll be distributing customized Ubuntu-Ohio branded CDs! :) 

Nice work!

Thanks!

I'm not so sure about distributing it, really.  I only made it with the idea of the Ubuntu-Ohio team of using it.  I also don't have any clue on how to package it into a .deb package or how to run the commands post install.

By separate the Ubuntu logo and the flag, do you mean the images cannot overlap?  I think it would be pretty easy to do another version where the logo isn't touching the flag, if that's what you mean.  That should be a snap considering my wife's photoshop skils (I know, I know, but I really suck at graphics.  If it's something that needs to be done on Linux for Linux I can scout for a GIMP geek).

---

### Post by jpeddicord on 2007-01-14
Correct, the Ubuntu COF logo may not tough the flag and must be displayed separately. We had that logo you have in the usplash now on the website, but had to remove it. :-k

---

### Post by zerhacke on 2007-01-14
Ah ha, so I've grabbed too early of graphics.  I will go back to the graphics logo hoojabajibber thread and collect some new graphics.  Now that I understand GIMPShop (you guys saw that package on PlasticBugs right?  Excellent conversion, that) a little better I'll throw together something, post it here, and if it looks like a winner I'll recompile it into a .so object and update the thread.

Sound like a plan?

---

### Post by msak007 on 2007-01-14
Too bad they have to be separated, it looks cool with the logo through the middle of the flag. If you get a new one put together, any chance of doing a Kubuntu one?

---

### Post by Vorian on 2007-01-14
That is really cool of you to do zerhacke! thanks :)

---

### Post by zerhacke on 2007-01-15
> **msak007 said:**
> Too bad they have to be separated, it looks cool with the logo through the middle of the flag. If you get a new one put together, any chance of doing a Kubuntu one?

I'm not a Kubuntu, Edubuntu, or Xubuntu user so I don't know what the graphics are.  If you can post a logo from your derivative (not just you, msak, but anyone who wants a custom usplash) I can make it.  If it boils right down to it, I can make a usplash so custom it has your name on it.

My dad, the Ham radio nut, wants a Linux box to do Ham radio stuff with.  I told him about there being so much in the repositories for Ham that's all free and he was hooked.  The box I'm putting together for him features his name/callsign (what do you call the username in Ham?  Callsign?), an FT817 radio we reprogrammed to contain 60Meter capability, and the second version of my Ubuntu-Ohio usplash.

So if you want something really special, send me some images to my email inbox which should be visible on the Wiki.  If you just want the base Ubuntu-Ohio usplash please hold for just a few more hours while I finish putting this stuff together.

> **Vorian said:**
> That is really cool of you to do zerhacke! thanks :)

You're welcome Vorian!

---

### Post by zerhacke on 2007-01-21
Major setbacks on production of a usable Usplash.  My wife, the photo and image manipulation genius, informs me "I don't know what to do with it" after being given specific instructions on our logo do's and don'ts and artistic license to do just about anything those do not cover.  This is of course immediately after she spent the last week in hardcore editing mode for everything her friends and the kids wanted her to do.

Grr. 

I am the world's worst artist, but the GIMP is a great tool, so I'm going to see what I can do.  Please, please, please, please, please, please someone who is at least halfway adept with graphic work join me in this.  All I need is a 1600x1200 PNG image.  If you guys can supply the image I can compile it into an .so object within the hour of receipt.  If/when that happens we'll have our group usplash and I can go on to other projects with the group.  As it is, the usplash has become something of a vendetta with me.

---

### Post by jpeddicord on 2007-01-21
I was thinking of a design like the current usplash, but with a little Provided By line under it. It is in 1024x768, which is the "compatible" resolution for usplash. Going higher than that is a little risky. I didn't take into account where the progress bar is however, so it may need moved around.

I have the .xcf here as well if you need it. I can't upload it because of restricted filetypes.

---

### Post by zerhacke on 2007-01-22
> **jacobmp92 said:**
> I was thinking of a design like the current usplash, but with a little Provided By line under it. It is in 1024x768, which is the "compatible" resolution for usplash. Going higher than that is a little risky. I didn't take into account where the progress bar is however, so it may need moved around.

I have the .xcf here as well if you need it. I can't upload it because of restricted filetypes.

I'm so graphically stupid I don't know what an xcf file is.  I am assuming it's the GIMP's answer to Photoshop PSD files.

The image you provided should work as far as placement of the images goes.  The throbber should fit in nicely just below, and I like that you've left the bottom of the image blank to account for those of us not using a quiet splash.

Quick, to the compiler!  I'll be back in a few minutes to either request image changes or to post the new .so object.

---

### Post by zerhacke on 2007-01-22
The usplash is closer to being finished.  I cannot figure out why the throbber is not taking the color layout I have set out.  Instead, the throbber background is kind of pink instead of black.  It's using the indexed palette from the background on the throbber instead of switching to the throbber's palette when it compiles.

However, the rest of it is done.  I took the image jacobmp92 put forth, moving the logo and stuff a little higher on the image as it was a bit close to the throbber for my tastes.

You can get the latest version from the site provided, [http://creaturefeature.darkness.com/Ubuntu-Ohio](http://creaturefeature.darkness.com/Ubuntu-Ohio)

Let me know what you guys think, and if any of you know how to force the indexed palette with GIMP be sure to leave me a tip.

---

### Post by jpeddicord on 2007-01-22
I managed to get the .xcf attachment enabled, so I'm uploading it now. The Forum Feedback area is great. ;)
Yes, XCF is the GIMP PSD.

Anywho, to manually set the GIMP pallete when it exports, just go to [Image]: Image > Mode > Indexed... and there you can manually tune the color pallete.

---

### Post by Ampersand. on 2009-04-04
so its been a while since anyone posted here. hopefully someone still lurks around.

i got the source for the usplash ubuntu theme and i am hoping to create my own theme. It would be great if i could reverse engineer someone elses existing theme files but im not sure which files should be messed with in that editing usplash-files folder to make my own.
is there any way i could edit a .so file?

also is there a gui version of usplash editing? i know splashy has a great one but it just will not run properly no matter what i do to it

---

### Post by jpeddicord on 2009-04-04
> **Ampersand. said:**
> so its been a while since anyone posted here. hopefully someone still lurks around.

i got the source for the usplash ubuntu theme and i am hoping to create my own theme. It would be great if i could reverse engineer someone elses existing theme files but im not sure which files should be messed with in that editing usplash-files folder to make my own.
is there any way i could edit a .so file?

also is there a gui version of usplash editing? i know splashy has a great one but it just will not run properly no matter what i do to it

You'll have to replace the splash images in the source package, then compile the package. debuild will package it all up into a .deb for you, but packaging is a completely different topic. :)

---

### Post by Ampersand. on 2009-04-05
Thanks for the reply.
by compile you mean right click>create archive?
will this debuild make a file that i can install with usplash?
sorry for hijacking the thread as well

---

### Post by jpeddicord on 2009-04-05
> **Ampersand. said:**
> Thanks for the reply.
by compile you mean right click>create archive?
will this debuild make a file that i can install with usplash?
sorry for hijacking the thread as well

No, I mean building the source files with a compiler like GCC. I'd recommend creating a new thread about it in one of the main support categories, or poking around in Tutorials & Tips - pretty sure there was a tutorial on building custom usplashes in there.

---

### Post by Ampersand. on 2009-04-05
ok i will look. thanks for the suggestion.

 EDIT: well it looks like im in way over my head here. i already have gcc but am so unsure of how to use it i dont even know how to run it.

---

### Post by zerhacke on 2009-04-08
You'll also need libusplash-dev on top of gcc.

---

### Post by Ampersand. on 2009-04-09
yeah i have that installed.
im going to create another thread so im not taking up all the space in this one with my problems.

edit: those thumbnails were part of the reply i made but decided to put elsewhere, now i cant get rid of them

here is my new thread: [http://ubuntuforums.org/showthread.php?p=7040287#post7040287](http://ubuntuforums.org/showthread.php?p=7040287#post7040287)

i like he ubuntu-ohio stuff by the way, i wish i lived in ohio so i could feel all patriotic and use it :)

---

