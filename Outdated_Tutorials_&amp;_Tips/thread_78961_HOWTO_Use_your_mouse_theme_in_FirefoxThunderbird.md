---
title: "HOWTO: Use your mouse theme in Firefox/Thunderbird"
date: 2005-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by joshuai on 2005-10-19
Thanks go to vanaedium at kubuntuforums.net for this solution.

One of the things that has been bugging me about Kubuntu (since switching from PCLinuxOS) was that the cursor in Firefox and Thunderbird would always revert to a default black cursor regardless of the theme I had selected.  Finally, vanaedium gave me this tip:

Simply create this directory and copy your cursor theme into it (cursors and all):

```
home/.icons/default
```

Finally, you'll be able to use your regular cursors in Mozilla applications!


Note: I did notice using the PolarCursorTheme that the "waiting" cursor reverted back, but using Pinux's Tux Cusors (Ubuntu theme) now and all is working well.

If there's a better way to do this, by all means let me know.

---

### Post by Juippisi on 2005-10-19
Awesome, thanks! 

And to everyone: [http://kde-look.org/content/show.php?content=19506](http://kde-look.org/content/show.php?content=19506) - some nice cursors ;-).

---

### Post by t2kburl on 2005-10-19
it would be useful to know where kubuntu puts the default theme so one could copy it to the new directory

---

### Post by joshuai on 2005-10-19
[QUOTE=t2kburl]it would be useful to know where kubuntu puts the default theme so one could copy it to the new directory[/QUOTE]

In my case, this was a mouse theme I had installed previously.  I found the files to be copied in *.icons/cursors/NameOfTheme*.  Alternately, after downloading, you can just put the cursors in the *default* directory immediately.  I believe putting them there will cause them to show up in the mouse section of Kcontrol too.

---

### Post by GoldBuggie on 2005-10-21
Another solution is to create ```
/usr/share/icons/default/index.theme
``` and put
```
 [Icon Theme]
Inherits=kubuntu
```

in the file

---

### Post by t2kburl on 2005-10-22
[QUOTE=GoldBuggie]Another solution is to create ```
/usr/share/icons/default/index.theme
``` and put
```
 [Icon Theme]
Inherits=kubuntu
```

in the file[/QUOTE]
  This worked for me.   Thanks  :)

---

### Post by mlomker on 2005-10-22
> ]/usr/share/icons/default/index.theme

Nice!  That one was bugging me.  That should be the default setting in Kubuntu.

---

### Post by Navyblue on 2005-11-07
[QUOTE=joshuai]Thanks go to vanaedium at kubuntuforums.net for this solution.

One of the things that has been bugging me about Kubuntu (since switching from PCLinuxOS) was that the cursor in Firefox and Thunderbird would always revert to a default black cursor regardless of the theme I had selected.  Finally, vanaedium gave me this tip:

Simply create this directory and copy your cursor theme into it (cursors and all):

```
home/.icons/default
```

Finally, you'll be able to use your regular cursors in Mozilla applications!


Note: I did notice using the PolarCursorTheme that the "waiting" cursor reverted back, but using Pinux's Tux Cusors (Ubuntu theme) now and all is working well.

If there's a better way to do this, by all means let me know.[/QUOTE]

On one of my box, doing this would replace the "System theme" and "No theme" in the KDE control panel into the theme stated.

On the other box of mine, doing this would cause X not to start. Here is a portion of my Xorg.0.log that seems remotely suspicious to me (the whole file is too long to post here):

```

Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

```

X would boot up fine if home/.icons/default is removed.

What is wrong here? Please advice on what other information is required.

Thank you.

---

### Post by Parkotron on 2005-12-20
[QUOTE=GoldBuggie]Another solution is to create ```
/usr/share/icons/default/index.theme
``` and put
```
 [Icon Theme]
Inherits=kubuntu
```

in the file[/QUOTE]

Wow, that's a great trick. That's been bugging me for quite a while. Thank you.

---

### Post by veloct on 2005-12-21
Woohoo, that was bugging me too. Thanks

---

### Post by steveneddy on 2006-01-03
I D/L the cursor files and installed. Same prob with Firefox, but after I restarted, all probs gone. I didn't have to add the other file (index.theme) to get ti to work correctly.
*******
Ubuntu 5.10, FFX 1.5

---

### Post by andrewski on 2006-03-30
This is fixed by default!  [https://launchpad.net/distros/ubuntu/+source/kubuntu-default-settings/+bug/15214](https://launchpad.net/distros/ubuntu/+source/kubuntu-default-settings/+bug/15214)

---

### Post by Tosa on 2006-04-02
I did this
> 
[Icon Theme]
Inherits=kubuntu

but still don't have my cursor theme in Firefox...

---

