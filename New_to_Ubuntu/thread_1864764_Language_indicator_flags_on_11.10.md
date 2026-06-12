---
title: "Language indicator flags on 11.10"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-10-19
Hi Guys,

Has anyone been able to replace the keyboard layout indicator from language abbreviations to flags in 11.10?

It's a small thing but it really bugs me.

In 11.04 I got it to work, but after a clean install of 11.10 I'm once again flagless :o

I followed the instructions at:[http://www.webupd8.org/2011/05/how-to-remove-keyboard-indicator-icon.html]("http://www.webupd8.org/2011/05/how-to-remove-keyboard-indicator-icon.html") (Scroll down to update 2) but no luck.

UPDATE

Boy this is frustrating.
I set the option to show flags in the gconf configuration editor.
I created ~/.icons/flags
I've tried extracting the desired icons to ~/.icons/flags and also into a folder within ~/.icons/flags with the icon set name (ubuntu-mono-light).
I've changed icon sets. Trying both via the Appearance manager and the Advanced Setting application which I think is the gnome-tweak-tool.
I've logged out and also restarted.
I still can not get the icons to show up!
I do now have an icon set named Flags that appears in my list of icon choices under Theme in the   Advanced Setting application, however that seems to be the same as the Gnome icons.

Sigh

---

### Post by GrouchyGaijin on 2011-10-21
bump

---

### Post by nightdrummer on 2011-10-22
Did you solve it yourself? I have the same problem.

---

### Post by GrouchyGaijin on 2011-10-22
> **nightdrummer said:**
> Did you solve it yourself? I have the same problem.
No I'm still flagless :(

---

### Post by GrouchyGaijin on 2011-10-23
bump

---

### Post by MblKiTA on 2011-10-25
Try to use dconf-editor and change to true the following setting *org/gnome/libgnomekbd/indicator/show-flags*

---

### Post by GrouchyGaijin on 2011-10-25
> **MblKiTA said:**
> Try to use dconf-editor and change to true the following setting *org/gnome/libgnomekbd/indicator/show-flags*

We have a winner!  **Thank you** man, that was really bugging me!

---

### Post by pherber12 on 2011-10-25
> **MblKiTA said:**
> Try to use dconf-editor and change to true the following setting *org/gnome/libgnomekbd/indicator/show-flags*

Thanks! That's been bugging me too! :):P

---

### Post by Koffeehaus on 2011-11-10
> **MblKiTA said:**
> Try to use dconf-editor and change to true the following setting *org/gnome/libgnomekbd/indicator/show-flags*

nice one mate!

---

### Post by vaul on 2011-11-29
Marvelous, this is how I think it should be by default.

---

### Post by vanchope on 2011-12-25
Does someone know how to fix language indicator in Ubuntu 11.10 if I use GNOME Classic (gnome 2.32)?

It shows only poor keyboard icon without any label of current language. I tried some ways to fix it, but unsuccessfully (add some icons into folder ./icon/flags, /desktop/gnome/peripherals/keyboard/indicator does not exist at all when running gconf-editor, .../indicator/showFlags = true does not work either).  

Thanks in advance!

---

### Post by lucacerone on 2012-01-10
Hi Koffeehaus,
I've followed your advice and set the variable to true.
However when I've restarted Ubuntu, I now have an icon with a red "crossed circle",
rather than the keyboard with the name.
In my home I have the .icon/flags folder and in there I've downloaded the following:
[http://launchpadlibrarian.net/71890024/flags2.tar.gz](http://launchpadlibrarian.net/71890024/flags2.tar.gz)
I also run the command:
gconftool-2 --type bool --set /desktop/gnome/peripherals/keyboard/indicator/showFlags true
(as it was said in the guide that GrouchyGaijin posted).

I guess that now Ubuntu is trying to display the icon, but that is in the wrong location. Where should I save the icons to be displayed?

If it is of any help I'm running Ubuntu 11.10 with Gnome 3 in session fallback mode.

Thanks a lot in advance for the help guys!
Cheers, -Luca

---

### Post by r_avital on 2012-05-29
> **MblKiTA said:**
> Try to use dconf-editor and change to true the following setting *org/gnome/libgnomekbd/indicator/show-flags*


And I'm sure that works well for 11.10.

Currently, on 12.04, this branch/key does not exist.

Also, there is no desktop/gnome/peripherals/keybboard/indicator in 12.04.

I have 4 layouts enabled.  I can switch between them just fine.  I would like to enable the flags.  The flags are currently in /usr/share/pixmaps, which is where they were when I made this work in Lucid, Karmic, Jaunty, Intrepid, Hardy...

[what exactly was the point of moving away from Windows forcing new interfaces down our throats every couple years for no good reason?]

Sorry.  if anyone can help with this, it would be great.

Thanks in advance

---

### Post by GrouchyGaijin on 2012-05-29
> **r_avital said:**
> And I'm sure that works well for 11.10.

Currently, on 12.04, this branch/key does not exist.

Also, there is no desktop/gnome/peripherals/keybboard/indicator in 12.04.

I have 4 layouts enabled.  I can switch between them just fine.  I would like to enable the flags.  The flags are currently in /usr/share/pixmaps, which is where they were when I made this work in Lucid, Karmic, Jaunty, Intrepid, Hardy...

[what exactly was the point of moving away from Windows forcing new interfaces down our throats every couple years for no good reason?]

Sorry.  if anyone can help with this, it would be great.

Thanks in advance

Look again.  I was able to get the flags to show up using [FONT=monospace]the [/FONT]dconf-editor 

[IMG]https://dl.dropbox.com/u/23115609/seflag.png[/IMG]

[IMG]https://dl.dropbox.com/u/23115609/usflag.png[/IMG]

---

### Post by r_avital on 2012-05-31
Thank you Grouchy, I stand corrected :)

---

### Post by andrikos on 2012-10-27
Since I has this issue also in 12.10 (where the flags folder has changed), I post this askubuntu link where it contains solutions for each version:
[http://askubuntu.com/questions/10223/display-current-layout-language-code-country-flag-in-keyboard-indicator](http://askubuntu.com/questions/10223/display-current-layout-language-code-country-flag-in-keyboard-indicator)

---

