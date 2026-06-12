---
title: "Open Office issue"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Squishy1 on 2008-06-27
Hello all!

  I need a little help with *Open Office*.  I hope it's OK to post the question here in an Ubuntu forum.

When I try to open any type of *Open Office* program I get a pop up window that indicates there is a document called "untitled1" that has been recovered, but I either need to either "start recovery" or "cancel".

The problem is that neither of those buttons are active.  I cannot click on them.

I searched for a file with that title, thinking that if I could find and delete it, I would be able to get past the problem, but search does not find it.

Any suggestions on what I can try?
Thanks!
-Mike-

---

### Post by Elfy on 2008-06-27
There is a lock file, I think it's in your /home - I had to deal with the issue myself last month.

Open nautilus - then do Ctrl+H to view hidden folders - go to .openoffice - check in there for a lock file if I remember correctly it's in one of the folders.

I have to search for my old threads with google as my old user was accidentally killed off so can't search for my threads :D

I will try and find it through google, just in case no-one else comes up with it

---

### Post by Squishy1 on 2008-06-27
> **forestpixie2 said:**
> There is a lock file, I think it's in your /home - I had to deal with the issue myself last month.

Open nautilus - then do Ctrl+H to view hidden folders - go to .openoffice - check in there for a lock file if I remember correctly it's in one of the folders.

I have to search for my old threads with google as my old user was accidentally killed off so can't search for my threads :D

I will try and find it through google, just in case no-one else comes up with it

Thanks for the help.  I found a .lock file in the .openoffice folder.  Do I just delete it?  

Thanks again!
-Mike-

---

### Post by Elfy on 2008-06-27
Make sure that no openoffice apps are on first - I would rename it first to lock without the .

See if oo starts without the problem, if all is ok delete the file 

Haven't managed to find what I was looking for yet

---

### Post by Squishy1 on 2008-06-27
> **forestpixie2 said:**
> Make sure that no openoffice apps are on first - I would rename it first to lock without the .

See if oo starts without the problem, if all is ok delete the file 

Haven't managed to find what I was looking for yet

Thanks again for trying to help me!  I renamed .lock to lock and then tried to open the word processor, but I got the same problem.  I went back to where the lock file is and now there is a *new* .lock file.  The one I renamed lock is still there too.

Any other suggestions?
Thanks!
-Mike-

---

### Post by Elfy on 2008-06-28
I couldn't find my old thread/post - it's a long story. But...

I found this on the openoffice forum (which is almost as useful as this one)

Close all the openoffice apps - open nautilus and view hidden files, navigate to 
home/<your user name>/.openoffice.org2/user/registry/data/org/openoffice/Office/

find and delete the file

Recovery.xcu

close nautilus and try again

This was the thread if you want to see it
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=2660&p=11780&hilit=stop+recovery+file#p11780](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=2660&p=11780&hilit=stop+recovery+file#p11780)

---

### Post by Squishy1 on 2008-06-28
> **forestpixie said:**
> I couldn't find my old thread/post - it's a long story. But...

I found this on the openoffice forum (which is almost as useful as this one)

Close all the openoffice apps - open nautilus and view hidden files, navigate to 
home/<your user name>/.openoffice.org2/user/registry/data/org/openoffice/Office/

find and delete the file

Recovery.xcu

close nautilus and try again

This was the thread if you want to see it
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=2660&p=11780&hilit=stop+recovery+file#p11780](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=2660&p=11780&hilit=stop+recovery+file#p11780)

Hello again... OK... I found the recovery.xcu file in OpenOffice.org2\user\registry\data\org\openoffice\Office\Recovery.xcu 

I deleted it. I deleted the .lock file again and then tried again.  Same result unfortunately.

I was going to uninstall open office and reinstall it, but it won't let me.  I get an error that says it is in use so it can't be removed.

I'm not giving up on Umbuntu.  I really want to break away from Microsoft Windows/Office so I appreciate all the help.

-Mike-

---

### Post by Hagar Delest on 2008-06-28
You can open the task manager (System>Administration>Monitor) and kill any soffice.bin process running. Then try again.

If no change, try to install the official version instead: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by bunny rabbit on 2008-10-15
Hi,
I have the same issue so maybe it is good to continue here... The fix that forestpixie proposed did help me in a way. I can open the different OOo programs directly after deleting that file. (I'd say this thread is solved)

Another thing is that OOo also has this Templates and Documents thing which shows up in the menu as OpenOffice.org (openoffice.org suite). This particular program still does not work properly. When I start an OOo product through the OOo suite it states that it will recover a document(which is not there) because OOo had crashed before. At this point it just stops and I have to use the crash handler.

:)

---

### Post by Jeremy23 on 2008-11-06
I would just like to point out that in the Ubuntu world, reinstalling is unnecessary and won't fix any problems.

OpenOffice.org saves its preferences in your home folder. On my computer, they are in */home/jeremy/.ooo2*.

Reinstalling OpenOffice.org would **not** delete this .ooo2 folder, which is where the problem lies.

To have the same effect as a "reinstallation", one can perform this. Not meaning to be alarmist, but take careful note that this will **delete any OpenOffice.org preferences**, and a simple typo may **delete all your data** if you type this incorrectly:

```
killall soffice.bin && rm -r ~/.ooo{2,3}
```

I have not tested the above command on my machine, as I did not want to lose my OpenOffice.org preferences.

---

### Post by Poyntz on 2008-11-06
> **Squishy1 said:**
> Hello all!
Any suggestions on what I can try?


Do you have the latest ooffice? an upgrade might fix the problem

---

### Post by stinger30au on 2008-11-06
> **Squishy1 said:**
> Hello all!

  I need a little help with *Open Office*.  I hope it's OK to post the question here in an Ubuntu forum.

When I try to open any type of *Open Office* program I get a pop up window that indicates there is a document called "untitled1" that has been recovered, but I either need to either "start recovery" or "cancel".

The problem is that neither of those buttons are active.  I cannot click on them.

I searched for a file with that title, thinking that if I could find and delete it, I would be able to get past the problem, but search does not find it.

Any suggestions on what I can try?
Thanks!
-Mike-


you have to click on a document to recover first, and then go a click on the cancel or recover buttons i have found

---

### Post by Hagar Delest on 2008-11-06
> **Jeremy23 said:**
> I would just like to point out that in the Ubuntu world, reinstalling is unnecessary and won't fix any problems.
Even if you're quite right, I would not be that sure, especially with OOo. Sometimes all the OOo components are not installed (especially if first install from a live-CD because there is not enough room to put all the modules). So reinstalling the full suite may help. But not the case here, I agree.

> **Jeremy23 said:**
> Not meaning to be alarmist, but take careful note that this will **delete any OpenOffice.org preferences**, and a simple typo may **delete all your data** if you type this incorrectly:

```
killall soffice.bin && rm -r ~/.ooo{2,3}
```

I have not tested the above command on my machine, as I did not want to lose my OpenOffice.org preferences.
Then, just rename the profile instead of deleting it. If there is no change, you'll be able to retrieve your former profile and in any case you'll be able to retrieve at least the folders that have not been damaged (like macros, autocorrect, user dictionaries, ...). See also here: [reset the OpenOffice.org  user profile](http://katana.oooninja.com/w/openoffice.org/troubleshooting#reset_user_s_application_profile).

---

