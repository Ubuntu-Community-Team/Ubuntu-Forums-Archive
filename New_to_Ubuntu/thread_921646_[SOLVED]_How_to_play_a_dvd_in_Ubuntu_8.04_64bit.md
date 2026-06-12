---
title: "[SOLVED] How to play a dvd in Ubuntu 8.04 64bit"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by ctothebizza on 2008-09-16
Sorry, this is second time I have tried linux, so please bare with me.  I just installed Ubuntu on my computer, and for some reason I can't get any dvds to play.  I installed the Ubuntu restricted extras, but it still won't work.  The tutorial on the Ubuntu help page ([https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)) just said that I need to install the restricted extras and I should be good to go.  However, when I try to play a dvd using Movie Player, it comes up with the error, "An error occurred, could not read from resource."  Does anyone know what I'm doing wrong?

Thanks!

---

### Post by phidia on 2008-09-16
You need some additional packages take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=763006").

---

### Post by Therion on 2008-09-16
[How to Play DVD's in Ubuntu](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

---

### Post by ctothebizza on 2008-09-16
hmmm...I tried everything on the linked websites and it doesn't work.  When I tried to install the packages, it said that they were already installed.  However, something changed because now when I try to play a dvd, Totem Movie Player goes dark and stops responding.  Any ideas?

---

### Post by phidia on 2008-09-16
Start totem from a terminal-there will be output there we can use for troubleshooting.
Do you have xine installed?

---

### Post by m_duck on 2008-09-16
To play a DVD you need extra packages, namely libdvdcss2. In order to get this package and other useful ones, it is useful to have the medibuntu repo enabled. 2 useful links are:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and
[http://ubuntu-tutorials.com/2008/01/29/medibuntu-the-only-3rd-party-repo-i-use/]("http://http//ubuntu-tutorials.com/2008/01/29/medibuntu-the-only-3rd-party-repo-i-use/")

2nd link is quickest/easiest to follow but on the first terminal entry ensure you change 'gutsy' to 'hardy'.

---

### Post by eragon100 on 2008-09-16
install vlc media player from add/remove and play it in there.

Apllications -> Sound and Video -> Vlc media player.

Then Go to the upper most left tab on the menu bar and select "Open Disc" in the dropdown menu. Just keep everyting at the default. It should play in vlc.

If it doesn't play the dvd, try to install the .deb package in my attachment (just double click on it). Even if it says, same version already installed, just reboot the computer and try to play the dvd again. (if it install without a problem, reboot the pc as well offcourse.)

This really shouldn't be a problem with vlc. Totem sucks for DVD's :(

---

### Post by billgoldberg on 2008-09-16
Note that you can also buy professional dvd playback (other ways might not be legal, depending on your location).

[https://shop.canonical.com/product_info.php?products_id=243&osCsid=33b5c2259f0288e27fef9409d359b958](https://shop.canonical.com/product_info.php?products_id=243&osCsid=33b5c2259f0288e27fef9409d359b958)

---

### Post by phidia on 2008-09-16
There is a Ubuntu wiki reference on dvd play [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").

Off topic: Please don't make blanket statements here in the help forums about programs that "suck" everyone's experience differs. 
Totem works fine for me and has for many years of linux use.

---

### Post by ctothebizza on 2008-09-16
OK, I am assuming that in order to run totem from terminal, I just type "totem" in terminal, and the program pops up.  So I did that, and it is running, but when I try to play a dvd it gives the message:  ** (totem:6380): CRITICAL **: gst_dvd_read_src_convert_timecode: assertion `(time->hour >> 4) < 0xa && (time->hour & 0xf) < 0xa' failed

So I don't know what that means...

I'm not sure if I have xine installed or not.  I tried to search for it in add/remove programs and I installed gxine, I don't know if that is the same thing.

And I do have libdvdcss2 installed, so that must not be the issue.  Does anybody know what the error message I got in terminal means?

Thanks again!

---

### Post by ctothebizza on 2008-09-16
Hurray!  I finally got it to work!  Thanks for all the links guys.  I think the problem is that the right commands weren't located in the right category on the help page: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

For Ubuntu 8.04 64 bit, the instructions are located down under the Ubuntu 7.10 and before (i386)

It's my bad for not seeing it though...:[http://ubuntuforums.org/images/smilies/icon_neutral.gif](http://ubuntuforums.org/images/smilies/icon_neutral.gif)

Anyway, after I did that, it works fine...

Thanks for all your help guys!

---

### Post by phidia on 2008-09-16
> **ctothebizza said:**
> Hurray!  I finally got it to work!  Thanks for all the links guys.  I think the problem is that the right commands weren't located in the right category on the help page: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

For Ubuntu 8.04 64 bit, the instructions are located down under the Ubuntu 7.10 and before (i386)

It's my bad for not seeing it though...:[http://ubuntuforums.org/images/smilies/icon_neutral.gif](http://ubuntuforums.org/images/smilies/icon_neutral.gif)

Anyway, after I did that, it works fine...

Thanks for all your help guys!

Your right ctothebizza. There needs to be an edit there it's not easy to pick out the related 64bit howto.

> If you are using Ubuntu 8.04 (amd64):

    *

      Open a terminal and type

      sudo apt-get install build-essential debhelper fakeroot

      press the enter key.
    *

      Then type

      sudo /usr/share/doc/libdvdread3/install-css.sh

      press enter again
    * When it asks you, press enter to continue and it will build and install libdvdcss2 



I'm pasting it here in case others are looking for that too.

Glad you got it working!

---

### Post by Rui Pais on 2008-09-16
Are you sure you installed the 64 bits (_amd64) version?
[http://packages.medibuntu.org/hardy/libdvdcss2.html](http://packages.medibuntu.org/hardy/libdvdcss2.html)

The error message seems to be gstreamer related. 
Tried close any running totem and move away gstreamer conf file:
```
mv ~/..gstreamer-0.10 ~/.gstreamer-0.10_OLD
```

By the way do you have medibuntu repos installed (with it's own version of gstreamer-ugly) or you just installed libdvdcss2 deb from medibuntu and are using all gstreamer plugins from ubuntu repos?

---

