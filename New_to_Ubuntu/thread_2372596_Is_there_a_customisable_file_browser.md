---
title: "Is there a customisable file browser?"
date: 2017-09-26
forum: New to Ubuntu
---

### Post by johnnoberries on 2017-09-26
I've tried using nautilus and nemo on 16.04 LTS, but neither of them allow custom date formats, or pretty much any other modifications to the file browser list columns. I've set up a custom date format of 

%l:%M:%S%p %d/%m/%Y

in the dconf editor, but this custom date format isn't available anywhere in either of the file browsers. Is there another, better file browser I should be using, or how would I go about modifying either of these applications on a lower level, shell, recompiling etc?

---

### Post by vasa1 on 2017-09-26
I think I remember looking to customize the date/day/time column and Thunar, Xubuntu's default file manager offered the option, if I'm not mistaken.

Of course, if you use Thunar instead of the default file manager which may also control aspects of your desktop, you could expect some "issues" with which you'll need to deal.

And did you mean to tag this thread with "lubuntu"? If not, please let us know or fix it yourself.

---

### Post by johnnoberries on 2017-09-27
yes, that was supposed to be an ubuntu tag. I've ended up fixing a lot of problems by switching to the Dolphin file browser, which is pretty configurable. It picked up my custom date format without me having to do anything, too!

---

### Post by vasa1 on 2017-09-27
> **johnnoberries said:**
> yes, that was supposed to be an ubuntu tag. I've ended up fixing a lot of problems by switching to the Dolphin file browser, which is pretty configurable. It picked up my custom date format without me having to do anything, too!
If you don't mind, could you please share a screenshot of Dolphin showing the custom date format? Mine looks like this:

---

### Post by vasa1 on 2017-09-28
BTW, I just tried various "LANG" options to see which gave me a date/time format I liked.

First, I ran```
locale -a
```to list the locales available to me.

Then, I tried```
LANG=put_each_locale_here dolphin
```and found that I liked *en_GB.utf8* the best. So now, my command to launch dolphin is this:```
LANG=en_GB.utf8 dolphin
```An unasked for consequence is that my Trash has been converted to a Wastebin!
I guess you could try something like this with any other file manager.

---

### Post by jpberes on 2017-10-29
Very customizable and works under whatever distro and desktop environment is Double Commander ;-)

---

### Post by fedkad on 2018-09-08
I am looking for a file manager which has a look similar to Windows (7) and _date customization is a must_. The *modified date/time* of each file (regardless of how recent it is) should be displayed in formats like these:

[FONT=courier new]YYYY-MM-DD HH:mm:ss
[/FONT]or
[FONT=courier new]DD/MM/YYYY HH:mm AM/PM[/FONT]

---

### Post by The Cog on 2018-09-08
Thunar (the default Xubuntu file manager) can do YYYY-MM-DD HH:mm:ss.

---

### Post by oldos2er on 2018-09-08
Old thread closed.

---

