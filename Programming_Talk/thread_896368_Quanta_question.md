---
title: "Quanta question"
date: 2008-08-21
forum: Programming Talk
---

### Post by its_jon on 2008-08-21
hi....

I have just flown in from a XP environment.

whilst setting myself up with tools to work and getting familiar with them I started to look at Quanta.

On XP I used NoteTab to generate and modify my websites.
One of the most common fuctions I used on notetab was the 'find and replace' 
Quanta also has a find and replace but it only appears to work for one file at a time. Does the option exist in Quanta to search and replace characters in all open files ? 

Quanta looks very impressive and very usable.... I must have missed this function somewhere in its gui ?

thanks.

---

### Post by scragar on 2008-08-21
the find in files option under edit works for replacing a string or reg in a whole folder full of files, but I am unsure if there is a way to limit it to just files open.

PS: this option is also called kFileReplace, and can be found in the plugins menu

---

### Post by its_jon on 2008-08-21
Thanks. !

I tried out kFileReplace..... its a different way of doing it. Probably more powerful but will take some getting used to.

I started to use Quanta for the first time....

I have some usability issues straight away....

I am finding it super slow to use with very basic tasks like cut and paste.... its almost as if its performing loads of checks each time the keyboard is used.....

I loaded two files into Quanta from the same website dir. apart from the above issue it takes about 10 seconds to switch from one tab to the other (one html file to another) ????? As it is I can't use it this way:neutral:

Now..... when I first installed it and ran for the first time it was requesting various files to run correctly....

1) Cervisia
2) KDbg
3) KimagemapEditor
4) Kompare

I think it was the above that were requested......anyway, I went to the add/remove and loaded in the packages that now appear in my App menu under /programming..... However when loading Quanta after getting these packages it still displayed the error...... Could this be the reason for the incredibly slow running ?

System monitor shows adequate system memory available.

thanks

---

### Post by scragar on 2008-08-21
those are plugins for various extra features(like side by side file comparison or image map editing), unless you need them I wouldn't recomend searching for them.

As for the speed issue I don't know what to say, I never had any problems with speed, even running it on a P3 with 386MB of ram the program was responsive, I'm assuming it's based on the size of the files though...

---

### Post by its_jon on 2008-08-21
Thanks for looking after me.....

I will re-install Quanta to start fresh again.

I appreciate the help, could you keep an eye on my progress please... Its good to talk to someone who is using it.....

Quanta will be my main app on linux other than gnomecommander 

thanks

john
scotland

---

### Post by its_jon on 2008-08-21
Ok.....

So I uninstalled Quanta - then reboot

Re-Installed Quanta

On opening Quanta I noticed that the confiq settings had not been removed so the two web pages last loaded reappeared and with the same slow issue.....

I then opened a backup version of both files which are almost identical apart from some updated content.

The backed up versions work great !!!!

My conclusion is that I must have enabled something in Quanta that is set to work/check/scan ect to these two files......

If I knew what to uncheck I assume I could make Quanta work quicker with these two pages. 

If a .JS file was missing linked to a html file would that cause the page to load slow ?

---

### Post by scragar on 2008-08-21
reinstalling quanta was very unlikely to be the problem.

To make quanta think it's a fresh install move the config files to a new directory:```
mv ~/.kde/share/apps/quanta ~/.kde/share/apps/quanta_backup
```
and see if that improves speed.

Mine me asking how large these files are? I've worked with 5 or 6 files at a time before now, but I try to keep all of my web dev work as small as possible for those with slower internet connections(I aim for around 10k as an absolute max(including external styles, javascript, images etc)).

---

### Post by its_jon on 2008-08-21
What is the name of the config files. and where

Sorry... I cut and paste your code into a terminal with no success.... and using nautilus I don't know what im looking for...

sorry... im sort of new to Linux :redface:

About filesize ..... it should be relative and irrelevant as the backed up versions that work instantly are near identical in size.

Files were originally created in dreamweaver prior to me taking over the project so a lot of machine generated nonesence in there

58.380 bytes

---

### Post by scragar on 2008-08-21
open nautilus, press ctrl+L for the location bar if it isn't there by default, and copy/paste(or if you want highlight and middle click) **~/.kde/share/apps/** into the bar, press enter, and your looking for a folder called quanta, this contains all of it's settings, just rename it.

if that doesn't change anything what is different between the current and backup versions of the files(I've noticed that there's a bit of a lag on network files, where it has to download and upload them, it's also got to load the full file all the time).

---

### Post by its_jon on 2008-08-21
I did exactly as you asked through nautilus

It renamed ~/.kde/share/apps/ on entry to:-

/home/john/.kde/share/apps

Which I presume is normal.

I renamed the folder quanta to quanta_backup

Reopened quanta after a reboot ...... and nothing has changed... it still loaded the same files and window layout config ?

---

### Post by scragar on 2008-08-21
ok, it looks like it's not the config file that's the problem. I am still intrested to know what is different between the files though, I would love to know why it's only running slow with your main versions...

---

### Post by its_jon on 2008-08-21
would you like a copy of both fies ?

both work fine in notetab.

---

### Post by scragar on 2008-08-21
no, I'm just wondering what is so different about the files to cause a lag while the back-ups don't.

---

### Post by its_jon on 2008-08-21
Im convinced I have enabled something in Quanta thats got a hook on these files....

I just loaded a total town website I created which contains over 100 html/php and css files ..... no problems at all.

Simplest way to find out would appear to be to completely wipe out Quanta and start fresh.
Im not sure how to though

---

### Post by its_jon on 2008-08-21
Some more info I just discovered....

Looking at the html files in question in GnomeCommander both have an additional file listed below them

file_one.html
file_one.html.LCK
file_two.html
file_two.html.LCK

However.... removing the.LCK files from the dir make no difference

---

### Post by scragar on 2008-08-21
that's just quanta's lock file, it's there so quanta and similar apps know the file is in use, that way should something change it you won't have the problem of 2 programs overwriting the same source.

---

### Post by its_jon on 2008-08-25
Thanks for all the help..... I tried everything to get Quanta to work better with the code including renaming the files and recreating the files.....

I guess its just a transitional problem until I get into the linux way...

anyway.... I installed Wine, so I can use the windows notetab to help me to continue updating these and potentially other problematic files.

Looking forward to using Quanta as I am sure it will aid me to piece together more compliant code..... Guess im starting to get more serious about doing things right after having fallen into web site design without any code training. (more of a gfx person)

anyway... thanks again

---

