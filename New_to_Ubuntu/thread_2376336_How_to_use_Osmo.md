---
title: "How to use Osmo"
date: 2017-11-01
forum: New to Ubuntu
---

### Post by vineyridge on 2017-11-01
I have checked all the threads, and nothing answers my question.  I have installed the program, and am muddling my way into the alarm/notification function.  There is no Help available, and I'm not very computer savvy.  I downloaded it through Ubuntu software, and all the things on the (much older than 2017) internet that I have found about it speak of various dependencies needed to make it work properly.  They also give instructions for use that don't seem to apply to the current version.

How do I find out whether I have the necessary dependencies?  And if I need to add some for full functionality, can I do that with the program already installed?  I have whole sections of the Notification entry area that are grayed out, and I cannot figure out how to make them available.  In particular, the data entry points in the New Task/Advanced page for starting and stopping are not available.  If I do need to add dependencies, where can I find them and how are they to be installed?

Most of the threads on this program are old, don't apply to the Ubuntu Software automatically installed version, and simply do not help getting it up and running in 16.04 with all functions available.

Can anyone help?

According to the Ubuntu Apps write-up here:
 [https://apps.ubuntu.com/cat/applications/precise/osmo/](https://apps.ubuntu.com/cat/applications/precise/osmo/) 
 there isn't a version for 16.04.   Should I uninstall it?  OTOH, the page that I found doesn't list apps past 14.04.  Is there a more up to date Ubuntu Apps that shows what are available and functional on 16.04?

Sorry there are so many questions, but I'm very new at this.

---

### Post by Frogs Hair on 2017-11-01
If Osmo installed the dependencies were satisfied and I see it in the 17.10 repository. I use Osmo with Linux Deepin though mainly for the contacts list. It is a dated  program may not integrate well with newer desktops and I'm not aware any plug-ins to add functionality to the program. I'll login to the other computer and take a look at the alarm function. Could you describe how you are using Osmo?

---

### Post by again? on 2017-11-01
Package search:
[https://packages.ubuntu.com/search?keywords=osmo&searchon=names&exact=1&suite=all&section=all](https://packages.ubuntu.com/search?keywords=osmo&searchon=names&exact=1&suite=all&section=all)

Home page links to help.
[http://clayo.org/osmo/](http://clayo.org/osmo/)
[https://en.wikibooks.org/wiki/Osmo_Documentation](https://en.wikibooks.org/wiki/Osmo_Documentation)

---

### Post by Frogs Hair on 2017-11-01
I found the same as posted above. Thanks guber2 !

---

### Post by vineyridge on 2017-11-03
I primarily want to use the task scheduling function with alarms that repeat daily for forever, and other tasks that repeat monthly (paying bills).  My problem seems to be that the ability to repeat schedule something pulls up an advanced window, much of which is grayed out for me.  And the help documentation is old and doesn't address the version that is on my computer.  I have looked at the wikibook documentation, but it doesn't help.  That's why I was wondering if I needed to add a dependency package for the alarm/repeat scheduling function.

---

### Post by Frogs Hair on 2017-11-03
Can you post a screen shot , I'm in the advanced window and I not sure what you are seeing.

Edit:  Everything in the advanced screen is completely active here and I'm on Ubuntu 17.10 with default gnome desktop . The same is true with a Deepin installation.

---

### Post by vineyridge on 2018-06-05
Here I am after almost a year.  

Now I need a simple instruction on how to put in a working command for the alarm in the notes section.  

Can anyone help?  All of the other problems that I have had have gone away.  I have taken a screenshot but cannot figure how to upload it.

---

### Post by Frogs Hair on 2018-06-05
When you open the reply box use the paper clip symbol on top.

---

### Post by again? on 2018-06-06
Not sure what you mean by alarm in the notes section.
I only see alarms in Tasks.

Try 
```
paplay [COLOR="#696969"]/path/to/sound/file[/COLOR]
```
Should play ogg and wav files. Test in terminal.

---

