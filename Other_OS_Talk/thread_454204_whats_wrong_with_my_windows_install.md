---
title: "whats wrong with my windows install?"
date: 2007-05-25
forum: Other OS Talk
---

### Post by hessiess on 2007-05-25
it chucks out "recovered from a sirias error" at least once a day, and try's to do a disc check every time i boot it, but it always freezes at 30%. wonse booted it takes 10 munites to become usable, and even then it's extremly slow!. i have had no sutch problems with ubuntu. but i need windows becose there's no internet connection in ubuntu yet. it dosant like the wireless network!.

then after a few howers of windows being booted it becomes so slow its completely unusable!. (if kick on a desktop short cut it takes 15-20 munites to realise that i did something and open the folder/ program) but once the program is running it goes back to normal speed? 

yesterday drag and drop stopped working!. a clean install is just not a option at the moment (exams)

help!!!!!!!!!!!!!!!!!!!!!! i expect its going to brak on me soon!

---

### Post by dolphin_oracle on 2007-05-25
Just a thought, but how much free drive space does your windows partition have.  windows gets weird with less than 20% free drive space.

Problems like that are why I switched my "family" machine to Ubuntu.  It just don't crash.

---

### Post by hessiess on 2007-05-25
59.1 gig used

32.7 free

ubuntu has 10 gig with 500 meg swap

it had 40 gig used when i got it, so i havent rilly added verry mutch

---

### Post by hessiess on 2007-05-26
so nowone knows whats up with my windows install?

---

### Post by smoker on 2007-05-26
hi, you could check the event viewer logs for a possible clue as to what the serious error is. it could be a number of things, but if your ubuntu install is ok, then presumably the hard drive is functioning alright, though it might be worth checking out with 'drive fitness test' available here:
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

if you cannot do a reinstall of windows, you could try a windows repair, which will replace all your system files without touching your data and programmes. it is always advisable to have a backup of all your essential data though.

have you defragged lately, and checked for virus and spyware infiltration? you could also try a scan from microsoft windows from here: [http://onecare.live.com/site/en-us/default.htm](http://onecare.live.com/site/en-us/default.htm)

best of luck

---

### Post by STREETURCHINE on 2007-05-26
nope ,even a google search came up empty.

sorry

---

### Post by dolphin_oracle on 2007-05-26
I'm assuming you are running WinXP.  One scneario could be a bad driver or corrupted program trying to load at boot, perhaps even loading partially.  Then over time a "memory leak" occurs draining off the system resources, which in windows is not the same as system memory.  If you are using Internet Explorer, its still known to have a few "memory leaks" of its own, although its not as bad as it used to be. These things can be extermely difficult to figure out.  Try a Windows Repair Installation first, but if its a corrupt driver or a non-OS application loading, it may not fix it.  

As good as XP is, I'm found that in a complex environment like a home user has (many more differnt types of software running in the home vs a typical business PC), even XP needs a good reinstall every couple of years.  I used to reinstall WIN95/WIN 98 every 6 mos or so no matter what the environment.  And a total reinstall of windows sucks because you have to reinstall every single app you were using.  At least with Linux, your basic programs install with the OS.

You could also check the seating of all your hardware, but if Ubuntu is working fine this isn't likely the issue.

Good luck.

---

### Post by hessiess on 2007-05-26
i use firefox now, havent used ie for ages

the prosessor use hovers around 50% wen idle?

---

### Post by dolphin_oracle on 2007-05-26
That would support a corrupted driver or a bad behaving program loading at startup.  Look at the processes in the task list when idle, it may (or may not) give you an indication of what is eating up your cpu time.

---

