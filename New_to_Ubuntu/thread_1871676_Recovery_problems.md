---
title: "Recovery problems"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by pimmers on 2011-10-29
I'm an absolute beginner. I used KleenSweep to remove unecessary files. Now I can't open anything although I can still use Firefox. I seem to have lost all of my photo files and most Ubuntu software centre applications won't open. Synpack package manager won't open. I'm completely lost as I can't do a recovery or system restore

---

### Post by Rubi1200 on 2011-10-29
Hi and welcome to the forums :)

A quick search of Google revealed that this is a potentially dangerous program that removes things it shouldn't!!!

Right now, I suggest you use a LiveCD to try and recover some of your files and then consider reinstalling the whole system.

You can use Photorec to try and get the files back:
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by gamblor01 on 2011-10-29
Wow I really wouldn't recommend running programs like that.  I think there is something built in to Ubuntu called computer janitor which could help you clean up files, but I prefer to not run these things.  I can clean up things myself, but I understand that not everyone can.  Maybe computer janitor would be a safer thing to run?  Also...where did it delete files from?  Maybe it was cleaning up your Downloads directory?  If so you might want to move files out of there before running tools like that or configure them to only delete certain things first.

Just a note however for rubi -- THANK YOU for the link.  That is by far the most informative link I have ever read in relation to data recovery.  I have not only bookmarked that link, I am seriously considering saving away the HTML and storing it in my gmail or something.  I almost want to setup a partition somewhere and then destroy it just to see what I can recover from it.  :)

---

### Post by Mark Phelps on 2011-10-29
Don't use Computer Janitor -- it does much the same things.

There's really no reason to be running such apps in Ubuntu.  It doesn't take nearly the amount of disk space as modern MS Windows OSs.  And, running such apps, as you have seen, risks trashing your Ubuntu install.

---

### Post by ajgreeny on 2011-10-29
> **Mark Phelps said:**
> Don't use Computer Janitor -- it does much the same things.

There's really no reason to be running such apps in Ubuntu.  It doesn't take nearly the amount of disk space as modern MS Windows OSs.  And, running such apps, as you have seen, risks trashing your Ubuntu install.
I totally agree!

Have a look at bleachbit if you feel you must use something, but even with that, don't simply accept everything that it says can and should be removed;  carefully choose what you delete.

I had a good look at it some time ago, but the space it was able to save on my disk was in no way worth the trouble of running it, so I have now removed it.

---

### Post by pimmers on 2011-10-29
Thanks for all the replies. I'm rather concerned that KleenSweep is so easily available if it is such a risk.

I have to admit though that it does warn that it should really only be run by "advanced users". Computer Janitor always said "nothing to clean up" so I was using Bleachbit but thought it wasn't clearing everything out.

I only use my computer for the Internet, storing a few photos and printing the odd letter so Ubuntu suits me fine - until I lost everything!

---

### Post by garvinrick4 on 2011-10-29
```
sudo apt-get clean
```
```
sudo apt-get autoclean
```
Gets rid of packages cached and autoclean gets rid packages not needed anymore. Ok by me and simple enough.

---

