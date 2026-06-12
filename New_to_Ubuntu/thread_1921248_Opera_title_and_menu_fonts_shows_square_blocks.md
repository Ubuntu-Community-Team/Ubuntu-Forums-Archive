---
title: "Opera title and menu fonts shows square blocks"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by sunewbie on 2012-02-06
Hello,

I have Xubuntu 11.10. I downloaded Opera manually from Opera website and double clicked deb file to install. 

Now, Opera 11.61.250 is behaving weird. It does not render fonts in address bar, tabs and in menus. This is happening only in Opera and not any other browsers like FF or Chromium.

I have attached a screenshot.

What should I do to render the fonts correctly.

Thanks

[IMG]http://img14.imageshack.us/img14/4328/operasqboxes.png[/IMG]

---

### Post by whatthefunk on 2012-02-06
Go to Settings > Preferences and in the general tab, make sure that your language is set to English (or whatever else you want).

EDIT: I suppose you cant read the menu options.  Hot key for preferences is Ctl+F12.  If that doesnt work, Settings is fourth from the bootom in the main menu, and preferences is the first option on the top in the sub-menu.  It should open in the general tab...language is on the bottom.

---

### Post by sunewbie on 2012-02-06
Please check screen shots

[IMG]http://img28.imageshack.us/img28/9167/operalanguage3.png[/IMG]

[IMG]http://img46.imageshack.us/img46/5180/operalanguagesettings.png[/IMG]

[IMG]http://img543.imageshack.us/img543/4828/operapreferences.png[/IMG]

I cant do anything.

---

### Post by TeoBigusGeekus on 2012-02-06
Was this a fresh installation of opera or an upgrade?

---

### Post by sunewbie on 2012-02-07
> **TeoBigusGeekus said:**
> Was this a fresh installation of opera or an upgrade?

Fresh installation. I even purged Opera, then reinstalled. It didn't work. So I purged it again, downloaded from Opera.com and again installed. Same thing.

when I start Opera, for 2-3 seconds, I can read some titles of tabs, then they change to square brackets.

Generally, these means that wrong fonts is selected in Opera. It used to if the font has multi-lingual support, like Arial Unicode MS or any Indic font which does not support English or any language that is typed (e.g. Hindi, Gujarati) and shows square blocks as it cannot join complex scripts. But this only affects text e.g. text in abiword or Writer and does not affect the text of title bars and menus, unless you have forced it to show in local language.

---

### Post by TeoBigusGeekus on 2012-02-07
Try installing a previous version of opera - see in the software centre if there is one.

---

### Post by ExileAmongYou on 2012-02-07
I would also try installing the Microsoft fonts that come in the xubuntu-restricted-extras package, if you haven't already. If you don't want the whole restricted extras package, you can just install ttf-mscorefonts-installer.

---

### Post by sunewbie on 2012-02-07
@TeoBigusGeekus
Since Opera is non-free, it is not in repos by default. May be, if I installed Opera 12 alpha, which installs in another directory, then things could work.

@ExileAmongYou
I already tried it too. I have installed xubuntu restricted extras and non-free codecs. Still no success. 

This does not happen in Bodhi 1.3, Mint 12 and Pinguy 11.04.

Don't know what is missing.

**EDIT:** I installed Opera Next 12 alpha. Still no success.

---

### Post by sunewbie on 2012-02-09
anybody found a solution?

---

### Post by TeoBigusGeekus on 2012-02-09
Ok, just an idea:
Rename your ~/.opera folder to something like ~/.opera_backup and try again.

---

### Post by sunewbie on 2012-02-09
> **TeoBigusGeekus said:**
> Ok, just an idea:
Rename your ~/.opera folder to something like ~/.opera_backup and try again.

pardon me, but  please explain me how to rename it

should i use 

```
sudo mv ~/.opera ~/.opera_backup
```

I tried GUI way

I went to /usr/bin and renamed Opera to Opera_backup and Opera could not be launched, so I had to again name it to Opera

---

### Post by sunewbie on 2012-02-09
OK i tried 

```
sudo mv ~/.opera ~/.opera_backup
```

So the profile was gone, but still the same problem :(

I have also posted in Opera forums. Lets see if I can get any solution

I love Opera

Thanks for the help

---

### Post by TeoBigusGeekus on 2012-02-09
Go inside your home folder, make the hidden folders to appear (Ctrl+h), if you haven't already and find the folder .opera: this folder contains all your opera settings and preferences.
Try renaming it to whatever you want, to see if it was a setting that caused all the trouble.

---

### Post by sunewbie on 2012-02-11
Ok

I will check when I return home.

Thanks

---

### Post by sunewbie on 2012-02-11
I got a reply from Opera forums. I was told to type in address bar

[opera:config#Fonts](opera:config#Fonts) 

and then I changed my default font from Droid Sans to DejaVu Sans. Actually I have Droid Sans and can use it in LibreOffice Writer, but that thing worked. 

```
12,4,0,0,0,0,DejaVu Sans
```

I changed every Droid Sans entry to DejaVu Sans

For me it's solved.

here is the post from Opera forums


```
13,4,0,0,0,0,DejaVu Sans
```

That may not be very obvious ... the 13 is the size, the 4 is the weight  (as in, light, regular or bold), the other numbers would indicate  italic, underline, and so on (not necessarily in that order - just leave  them at 0 until you get a good font) and then of course is the font  name. Pick the name of an actual font you have installed (a  TrueType/Freetype font would be best if available) and put it in there -  and likewise the other sections which are giving you trouble (Dialog  and so on), then click on Save. If nothing happens immediately, close  and then restart Opera to make sure it loads the changes.

[http://my.opera.com/community/forums/topic.dml?id=1300272&t=1328974214&page=1#comment11602912](http://my.opera.com/community/forums/topic.dml?id=1300272&t=1328974214&page=1#comment11602912)

---

### Post by haeuslein on 2012-07-27
Thank you!!!! This was driving me nuts!

---

### Post by loonyaddy on 2013-05-29
thanks a lot...was facing the same issue in opera 12.15 :)

---

