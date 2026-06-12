---
title: "routine check of drives not so routine- is my hard drive toast? Or can you help?"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by alewyfe on 2012-11-13
So, 5+ year ubuntu user but total luddite newbie, so be kind!  My ancient laptop may have given up the ghost last night, but I'm hoping for a reanimator...  it's a thinkpad x31, running Hardy Heron with the last available update (yep, I know... need to upgrade but was afraid to do it until I backed up files and figured out exactly how best to proceed or rather, where to begin... guess I waited too long? Luckily I did back up important data to a usb drive a week or two ago...whew!).  

Turned it on after a routine shut-down, and my wallpaper/background image loaded, then two error windows popped up- the first, that nautilus had failed to load or compile or something (wish I'd written it down) and the second I don't remember, sorry!  Closed those (doh... had I known, i'd have written 'em down...) and... nothing.  Mouse cursor could move but nothing loaded.  Did a hard shut-down on the advice of my fella, and crossed my fingers... it started a "routine check of drives", followed by a loooong string of what I think I have id'ed as libata error messages in the shell... ata 3.0 (then more stuff I don't recall... sorry, no other working computer at home so I'm trying to remember from work! It's many pages of stuff... and many years since I did any computing in a command line-type interface- college PINE email is a distant memory, and the Scheme class I took was useless, haha)... drdy err... then eventually Bash: the: command not found, then root prompt...  (I can try to transcribe more of the code from home if it's needed to know what to do from here)...

Where should I start?  Is this an os/software problem since 8.04 is no longer supported? Did my hard drive finally die?  It was sitting on my desk the whole time, not dropped or jostled... should I try to restart with the original 8.04 disc in the external drive?  Or is there something else to do first?  Or try to install 9.04 (also have that on disc, and read somewhere that you should upgrade in order if possible rather than skip releases...)?  Is it time to break down and finally get a new laptop?  Hoping I can save old trusty... I really only word process, web surf, and do reallly light photo-editing... can't afford a new machine on my part-time salary with a not-for-profit... ack! I'm reading a ubuntu manual, checking the forums, etc... but just keep ending up with more questions.  So... help, and explain it like I'm five! Thanks, haha. 

cheers, this lady needs a beers.  :-)

---

### Post by audiomick on 2012-11-13
You say you have a 9.04 disk. I would suggest using that to boot into the live environment, i.e. the "try without installing" option.

There are a couple of things you can to here. One is to copy off anything you haven't backed up yet onto an external drive.

You should, I think, be able to start the hard drive utility and get it to look at the SMART values for your drive. That is information that the drive stores about itself.

[http://en.wikipedia.org/wiki/S.M.A.R.T.]("http://en.wikipedia.org/wiki/S.M.A.R.T.")

From there, you might also be able to follow the suggestions here
[http://askubuntu.com/questions/59064/how-to-run-a-checkdisk]("http://askubuntu.com/questions/59064/how-to-run-a-checkdisk")

It does sound a bit like your drive has bit the dust, but is is also possible that it was just a bit confused, and then the hard shutdown just confused it more.

If you can determine that the drive is ok, and get all your data off to your satisfaction, I think it is time to upgrade to a current version rather than spending any amount of time trying to fix that install. On an older machine like that, it is worth trying out the current version from the live environment to see how it runs on your machine. If you can get the installer onto a USB stick instead of a CD, you will get a better idea of how it runs. The CD will be slow, the USB stick a lot quicker.
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

If the current standard Ubuntu with the Unity desktop is too slow for you or whatever, you might want to look at Lubuntu. It is a different desktop environment that uses less resources, and is designed for older hardware.
[http://lubuntu.net/]("http://lubuntu.net/")

---

### Post by DuckHook on 2012-11-14
+1 to @audiomick.

Especially the suggestion to do a new install. As a regular user, you will likely spend more time and frustration trying to figure out what is wrong and how to fix it than simply doing a new install. The only situation in which it makes sense to try fixing your install is if you have critical information on your HD that you cannot otherwise get off the disk. But if you can read the HD through a live CD and if you can copy any critical data to a USB stick or an external drive, then a repartitioning and virgin install is the easiest, cleanest and most stress-free way to go.

If you are feeling confident/adventurous and wish to make your system a little more robust against a future problem of the same kind, then you may wish to partition your HD before your new install with a separate partition for your /home directory. With /home in its own partition, your personal data enjoys a certain robustness from a corrupted operating system. So long as the /home partition is intact and your /home files are not corrupted, you can easily wipe out and reinstall operating systems and reattach your old /home directory for each install. This doesn't replace the need for a proper backup strategy, but it does make it more convenient to recover from mild to moderate difficulties.

If you don't know what I'm talking about or what partitioning is, then it is best not to vary from the standard install and just rely on good backups to avoid trouble in future.

---

