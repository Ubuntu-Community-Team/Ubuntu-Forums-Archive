---
title: "Running 10.04, logged out-&gt; it wouldn't log back in. And now it won't boot."
date: 2012-04-19
forum: New to Ubuntu
---

### Post by swarup on 2012-04-19
I am running 10.04 LTS on my Dell desktop. I was using the app "Sound Converter", and it froze up when I brought in several wma files for which it did not have the needed codecs. I could not close Sound Converter, so I logged out in order to get Sound Converter to close. But then it froze up while logging back in. I powered down the computer. On reboot, it comes to Grub (I have dual boot Win XP and 10.04), and boots to Win XP fine. But it will not boot into Ubuntu. I tried booting up in recovery mode and selecting fail-safe graphics mode, but it wouldn't boot there either. I tried "repair broken packages", but that didn't seem to fix the problem either. I should let you know also, that the HDD only has about 60 or 70 mb of free space on it at this point.

Kindly inform, what is the way to get it to boot again? I seem to recall something like this happening in the past and there was a fix for it, perhaps by dropping down via recovery mode into root shell?

---

### Post by swarup on 2012-04-19
I booted up to a livecd (11.10 on flashdrive), ran gparted, found that the Ubuntu partition is sda5, and ran:
```

sudo e2fsck -f /dev/sda5
```

It did say that it fixed some things, something about the clock, and reported that sda5 had been modified. But when I rebooted the computer, it still would not boot. Goes to grub fine, but if you select ubuntu it comes to the progress bar screen showing Ubuntu is loading, but never comes to the desktop.

That's about as much as I know to do. Any ideas how to diagnose/fix it?

---

### Post by 23dornot23d on 2012-04-19
To get in - the (option 2) on the boot menu - is safe-mode usually
or if its not booting in beyond a black screen try pressing <esc> or <shift> repeatedly ...

Its to do with the space ...... so you need to get into a terminal / console 


Ctrl + Alt + F2 at startup ...... or safe mode ...

[COLOR=Blue][B]sudo apt-get clean
sudo apt-get autoclean
[/B][/COLOR]
are two commands that will get rid of the temporary package files .....

These may give you enough to get into your desktop ..... and then there are some tools
that may help .....

I would look in the **[COLOR=Blue]home/Downloads[/COLOR]** folder first and see if you have anything you can dump



If you can give a screen shot of the gparted .... screen too please ......

---

### Post by sudodus on 2012-04-19
Maybe you can delete some big files (maybe after copying to another drive), so that your disk space will be enough for temporary files.

Have you checked if there are any read/write errors? Does your HDD have S.M.A.R.T. capability? You can check that with the Disk Utility Tool (palimpsest).

Anyway, I suggest that you backup your personal files (or if you have space for it, your home directory /home, the whole Ubuntu partition(s) or the whole drive). Then you'll have peace of mind while trying different methods to restore your system.

One method is to make a separate /home partition (with your present /home directory (and subdirectories) and then re-install the system. I think you can find several posts by *oldfred* at the Ubuntu Forums describing that, e.g. this link
[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11853767&postcount=9_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11853767&postcount=9")

---

### Post by swarup on 2012-04-19
You're right! It was just a question of space. I freed it up as you suggested, and it immediately booted up fine. :P

---

### Post by 23dornot23d on 2012-04-19
Good to hear .... 

Now you need to do a little more work to keep some space available ......

( or if you are ok - just try to keep plenty free 1 Gig is my minimum - once it gets there it needs a tidy up )

Can you do this in a terminal .... 

[B]df

post back the results ... please ....
[/B]
Just to see what space you have .... on there now or are you still removing things .... 
be careful and as said backup the things that are important to you ....

the thing is to keep some space free - there used to be a warning message .....

---

