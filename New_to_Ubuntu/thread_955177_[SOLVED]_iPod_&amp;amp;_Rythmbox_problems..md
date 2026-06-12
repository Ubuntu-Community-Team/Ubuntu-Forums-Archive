---
title: "[SOLVED] iPod &amp;amp; Rythmbox problems."
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Archie69 on 2008-10-21
Hello All,

I have an ipod and would love to be able to remove and add music to it via Rythmbox.  I plugged in the iPod and it found it no problem.  It also didn't have any problem playing music from my ipod.  It did however have issues with me removing files from it via Rytmbox (ie.  I try to erase albums to make room for new ones, but it wont let me).

I tried opening the iPod folder through the desktop but find folders mislabeled, like FB01, 02, 03, etc.

I tried to follow a help 'tutorial' on these forums, but got nowhere.

Anyone know what I should do?  Please help.

---

### Post by evilkastel on 2008-10-21
I'll reccomend to you to use a different app. Rhytmbox is quite temperamental, I never could make it work with my shuffle. I now use songbird with the Ipod extension and works jusst fine. I'm sure there is a manpage about it. Also, banshee seems to work. Google is your best friend in this cases.

---

### Post by aragorn2909 on 2008-10-22
> **evilkastel said:**
> Also, banshee seems to work.

Allow me to confirm; Banshee works perfectly with my Wife's Nano.

---

### Post by Archie69 on 2008-10-22
As good as Banshee seems to be, it doesnt seem to do the trick eitehr.  Banshee doesn't recognize my ipod.  If anyone has a fix or advice for rythmbox it'd be ideal, as it recognizes my ipod.  just need to be able to edit it.  Thanks for the advice so far.

---

### Post by Nostalos on 2008-10-22
I personally manage my iPod from Amarok.    Too bad the wife got me a Zune for xmas and I am now obligated to use it or risk offending her.....

:guitar:

---

### Post by ChildOfMana on 2008-10-22
> **"Archie69"]As good as Banshee seems to be, it doesnt seem to do the trick eitehr. Banshee doesn't recognize my ipod. If anyone has a fix or advice for rythmbox it'd be ideal, as it recognizes my ipod. just need to be able to edit it. Thanks for the advice so far.[/QUOTE]

Did you get Banshee from the repos (I'm assuming you're running Hardy here) or did you get the latest version from [here](https://edge.launchpad.net/~banshee-team/+archive)?

If you got it from the Hardy repos it is an older version and not as stable/functional. You're best off removing it and installing the latest version from the link above. Full instructions on the site.

To remove your current version open a terminal and type said:**
> sudo apt-get --purge remove banshee

This alone may solve your problem. However, if it doesn't, try plugging your iPod in and right-clicking on it's icon (on your Desktop) and see if you can choose to open it with Banshee instead of Rhythmbox (which will currently be the default). Make sure you close Rhythmbox first if it's still open though.

If Banshee can now detect and access your iPod then you may as well go to System > Preferences > Preferred Applications and set Banshee as your default media player (or alternatively uninstall Rhythmbox all together if you're not going to use it for anything else).

I can tell you from experience that, if you can coax it into detecting your iPod, Banshee does a very good job of interfacing with it.

Hope this helps.

---

### Post by Teamgeist on 2008-10-22
The PAckage from the PPA-Repository is called banshee-1.

So make sure you install this.

---

### Post by kostkon on 2008-10-22
You can check *Floola*, which is an *iPod* manager. You can download [a deb from *getdeb.net*]("http://www.getdeb.net/app/Floola") or grab a binary from [its site]("http://www.floola.com/").

---

### Post by Therion on 2008-10-22
> **Archie69 said:**
> I tried opening the iPod folder through the desktop but find folders mislabeled, like FB01, 02, 03, etc.
Just a little FYI:  Those folders aren't mislabeled; that's just how the iPod handles your music files.  Inside those folders, if you drill down a little, are the .mp3/.aac (whatever) files you're looking for.  Some media handlers are okay with this file structure, others are not.  It's not Rythymbox freaking out or not working properly, it's just the way the iPod handles file management.

---

### Post by Archie69 on 2008-10-22
Hey, thanks for the tips.  I went to that link and was following along, but I don't know what my 'deb' is.  How do I figure this out?

Hopefully it works.
Thanks

---

### Post by ChildOfMana on 2008-10-22
What version of Ubuntu are you using? 8.04 Hardy Heron?

If so the APT line to add will be:
> 
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main

After that click 'Add Source' then 'Close' then open a terminal (Applications > Accessories > Terminal) and copy and paste the following to install Banshee:

> sudo apt-get install banshee-1

Note that you'll have to remove the old version of Banshee *before* you do this though (see my earlier post for how to do this).

---

### Post by Archie69 on 2008-10-22
F!  Well I got Banshee to work, but no its says it doesn't recognize my iPod.  I don't know why.  It says that banshee can't recognize it because I formated my iPod with a version of iTunes.  

What now?  
I never thought it'd be this much work.  Thanks

---

### Post by ChildOfMana on 2008-10-22
Just out of curiosity (and I probably should have asked this question much, MUCH earlier on) but what iPod model are you using?

Is it an iPod Touch by any chance?

---

### Post by Archie69 on 2008-10-22
No, its a nano.  Its a little older. 
I have no idea why its being so picky

---

### Post by ChildOfMana on 2008-10-22
Ah. The reason I asked is because the current version of Banshee doesn't support the iPod Touch (which is why I really should've asked earlier!!)

Have you recently updated the firmware on your iPod through iTunes?

If so the new firmware version may not yet be supported by Banshee. This would also explain the error message.

If that's not the problem then I'm afraid I'm at a loss.

Best I can do is say *bump* and hopefully someone with more experience/knowledge in this area can help you.

In the mean-time you could try [here](http://banshee-project.org/support/) but the support/FAQ sections are still being constructed so there may not be any relevant info yet.

There are a few suggestions for dedicated iPod managers in the earlier posts too.

Sorry I can't be of more help.

---

### Post by Archie69 on 2008-10-22
OK.  Thanks a lot for trying.  I really appreciate it.
I just wish Ubuntu wasn't so difficult when it came to media.

If anyone else could help I'd really appreciate it.  I hate not being able to update my iPod.  PLEASE HELP

---

### Post by prematurebaby on 2008-10-22
Are your songs all encrypted. Or in other words all of them were purchased from the iTunes store?

---

### Post by SuperSonic4 on 2008-10-22
> **Archie69 said:**
> OK.  Thanks a lot for trying.  I really appreciate it.
I just wish Ubuntu wasn't so difficult when it came to media.

If anyone else could help I'd really appreciate it.  I hate not being able to update my iPod.  PLEASE HELP

It's not ubuntu being difficult, it is apple being difficult. Many media players work seamlessly in ubuntu :guitar:

Can you roll back the firmware in iTunes or something?

---

### Post by citybird on 2008-10-23
> **Archie69 said:**
> If anyone else could help I'd really appreciate it.  I hate not being able to update my iPod.  PLEASE HELP

Hey there. I just got my 3G Nano working on Ubuntu 8.10 (HH) 64Bit Desktop so I am sure it will be possible to get you up and going.

First Question: does your iPod still work on iTunes? If so then you probably have not rebuilt it's database for Banshee.

The first time I connected my iPod after installing Banshee it could see the songs on it but I could not add songs.

There is a program called **podsleuth** that is installed with Banshee. Go here and follow the directions!!
[http://banshee-project.org/download/#ubuntu](http://banshee-project.org/download/#ubuntu)

you have to install Banshee and all it's helper programs or you will not get anywhere.

if **podsleuth **finds your device then you should be good to go.

First I had banshee rebuild the database on the iPod nano 3G. After this i could no longer access any of the songs on the ipod. It was like the device was blank. I plugged it back into the computer and I could see the songs in Banshee. 

I then copied all my songs from the iPod to the HD. They worked fine, I could play them on the PC. I did a little housekeeping and organized the albums a bit since iTunes likes to break albums up by artist for some reason. I hate this.

Then I copied everything back to the iPod and it worked fine. Coverflow had pictures and albums without covers I could download the cover jpg's and put them in the album folder with the songs. Then you remove that album from the Music Library on Banshee and add it back and it pops up with the new cover art.

Do the same on the iPod, remove and add back and the cover art gets copied to the device.

Hope this helps.

---

### Post by Archie69 on 2008-10-23
I can only assume my ipod still works on itunes.  I dont have itunes anymore.  I only run ubuntu Hardy 8.04.  My problem with Banshee is that it recognizes my ipod, and by that I mean the iPod icon appears in Banshee, but its 'Unable to Read iPod"  

Will the problem resolve itself if I run podsleuth?

---

### Post by Archie69 on 2008-10-23
I can only assume my ipod still works on itunes.  I dont have itunes anymore.  I only run ubuntu Hardy 8.04.  My problem with Banshee is that it recognizes my ipod, and by that I mean the iPod icon appears in Banshee, but its 'Unable to Read iPod"  

Will the problem resolve itself if I run podsleuth?

---

### Post by ChildOfMana on 2008-10-23
As far as I know Podsleuth is installed alongside Banshee. To check if you've got it go to System > Administration > Synaptic Package Manager, then click 'Search' and type podsleuth. If you've got it then the little box to the left of it should be green. If not, right-click and select 'Mark for installation'.

However, I found [this](http://bugzilla.gnome.org/show_bug.cgi?id=553311) bug report. Seems like this is a common problem with iPod Nano's... and Podsleuth is the prime suspect!

This might not be what's causing your issue but it *is* a possibility.

Unfortunately no fix is suggested in the bug report (other than to upgrade to the currently unstable Banshee 1.3.1 development version... which apparently doesn't work either!!)

You could always try uninstalling Podsleuth (via Synaptic) and then re-installing it again. However, I'm not sure what this would do to your Banshee installation so unless you're feeling brave you may want to wait for more advice on that one!

---

