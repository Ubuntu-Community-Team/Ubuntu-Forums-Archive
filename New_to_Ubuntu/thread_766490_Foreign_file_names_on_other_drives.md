---
title: "Foreign file names on other drives"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by aquiladbes on 2008-04-25
Hi everyone,
I switched to ubuntu(gutsy) about a fortnight ago, fed up with Window's lack of customizability (is that a word?) and ultimately, usability. I've been able to solve most problems quite well with the info on the forums (most of it's really good and easy to follow, great work guys!) and manual pages, but one has got me stuck.

I work with Chinese, Japanese and Korean files, and quite often they are given to me on an external hard drive (it's just the one, but it's always done the job). However, any files with CJK file names are not visible. 

This is where I get stuck, because most of the other threads dealing with this subject seem to be related to when the file names are broken. In my case, the file isn't visible at all, in the GUI or through the terminal.
As per the one thread I could find that was pertinent, I've tried putting a few encodings with nls= in to fstab, but no effect.

The interesting thing is, when I set up a Korean locale and logged into that, and then mounted the drives, I could see the files. If I then logged out and then logged in with the default locale (/etc/environment gives 'C') I can see the files in the english no problem. If I then unmount and remount the drives using the mount commmand, the files aren't visible again! Now, in this state where the files aren't visible, if I log back out and into the Korean locale, I can't see the files until I unmount and mount the drives again. 

You can see the problem. If I wanted to work with a Korean and a Chinese file, then I would have a dilemma. At this point in time, best option is going back to my virused up Windows. Secondary is the absolute annoyance of switching between locales.

Is there anyway to get the drives to display the files in my default locale (I selected no localization on install)?

Wow, I wrote way too much. Apologies for people with eye strain :).

---

### Post by bribera on 2009-10-27
Where are you trying to view the files? I.e. are they invisible in the terminal, your graphical file manager, a different program, etc?

The terminal shouldn't be hiding files based on locale, but it seems feasible that a file manager or other program might.

---

### Post by alphaniner on 2009-10-27
This thread is clearly in need of brrrraaaaiiiiiiins!

Brrrraaaaiiiiiiins!

---

