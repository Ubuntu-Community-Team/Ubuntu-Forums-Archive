---
title: "desktop photo"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by james120 on 2014-04-11
Having installed ubuntu 12.04 along side windows xp, I'm definetely qualified to be an absolute beginner.  First time ever for using ubuntu.  I do like it though.  This is probably a stupid question, but here goes.  I set my desktop to a photo that I like.  Later I log out and shut down the computer.  When I start it back up again, the desktop photo is gone and a black screen is there.  Then I select my photo again.  Same thing happens again the next time.  Is it something I'm missing?  I've logged off then back on thinking it would be saved, but it tends to forget if I shut down completely and restart the computer later.  Does this make sense?

---

### Post by sudodus on 2014-04-11
I think that your photo is in a partition, that is not mounted, when you boot the computer. Copy the photo file to your Pictures directory (in Ubuntu's home directory), and select it for background picture from there. Then I think it will survive as background after rebooting.

---

### Post by james120 on 2014-04-11
ok, I dragged it out of the other hdd I use to store photos and songs and put it in the home, pictures folder.  Then opened up system settings, appearence and selected pictures folder from the drop down menu.  The picture was there.  It's the only one I've been using.  I'll reboot and see if it works, then write back.  Thanks

---

### Post by james120 on 2014-04-11
I logged out then rebooted (restarted) and when it came back up it was a black screen.  I checked to see if the photo was still in the appearence section and it is.  What else am I doing wrong?  The hdd is being mounted.  Under dash home it's there under the name I gave it using windows.

---

### Post by plucky on 2014-04-11
What are the permissions on the photo?

Do you own it?

```
cd Pictures
ls -l "name of picture"
```

---

### Post by james120 on 2014-04-11
Under properties it says owner james, access read/write,  group james access none.  Should that be read/write?

---

### Post by sudodus on 2014-04-11
> **james120 said:**
> ok, I dragged it out of the other hdd I use to store photos and songs and put it in the home, pictures folder.  Then opened up system settings, appearence and selected pictures folder from the drop down menu.  The picture was there.  It's the only one I've been using.  I'll reboot and see if it works, then write back.  Thanks

- Are you running an installed system, or are you running a live system? A live system is when you 'Try Ubuntu' from the install DVD or USB drive without installing.

- What tool did you use to select the background picture? Was the background changed temporarily?

- Did you select the picture copy in /home/Pictures as the background picture?

---

### Post by james120 on 2014-04-11
Yes it's an installed system.  I downloaded the iso file and burned it to cd, then installed it alongside windows xp.  It placed it in c:\ubuntu
I've got another hdd to store photos and music.  I used the appearence app then photos from the dropdown menu.
Yes I copied from hdd and put it in the home/pictures folder.
If I just log off and back on it'll keep the background picture and I don't have to reselect it.  But if I log off and shut the computer down or restart it then it'll revert back to a black screen and I have to reselect the photo though appearence.

---

### Post by sudodus on 2014-04-11
Sorry, I don't understand what is wrong. According to your description it should work. Let us hope someone who reads this can find how to fix your problem ...

-o-

I would think it is enough that you (the logged in user) have read/write access.

---

### Post by pfeiffep on 2014-04-11
I had a ***similar* **problem, I would set my pic as the desktop and seemed ok until reboot. I used gimp to change the file type to .png which fixed the problem.

---

### Post by james120 on 2014-04-11
I'll try that.  Right now it's a .jpg.  It's not a big deal, just annoying.  Thanks

---

### Post by 23dornot23d on 2014-04-11
Its a wubi install - not a proper install ....... looking at what is said here ........

> 
Yes it's an installed system.  I downloaded the iso file and burned it  to cd, then installed it alongside windows xp.[COLOR=#ff0000][SIZE=4]**  It placed it in  c:\ubuntu**[/SIZE][/COLOR]


The proper installs with Ubuntu in a separate partition ( sdx3..4 etc) work as they should do in the respect of keeping backgrounds etc .......

If it was a proper install it would probably have at least 2 partitions assigned to it  (/root /swap) and if user data is installed as separate (/home)

Not sure is wubi supported anymore - see this thread for more of a discussion about it  -   [http://ubuntuforums.org/showthread.php?t=2155015](http://ubuntuforums.org/showthread.php?t=2155015)

---

### Post by james120 on 2014-04-11
I did change it in gimp to a .png and it worked.  Thank you.  For your information I checked the file permissions and they were changed also.  It changed the group to james read/write and others to read only.  The .jpg photo permissions were as stated above.  That should have been changed also, but I'm happy now.  Have a great day!

---

### Post by james120 on 2014-04-11
Sorry, I understood that it could be installed along side windows or on a partition.  It's now a dual boot system.  The background photo problem? is fixed now and later I may partition the hdd and install again.  That might speed it up somewhat.  I also understood or thought I did that 12.04 lst would be supported until 2017 and it didn't say if it was a wubi install or a partition install.

---

### Post by pfeiffep on 2014-04-11
> **james120 said:**
> I did change it in gimp to a .png and it worked.  Thank you.  For your information I checked the file permissions and they were changed also.  It changed the group to james read/write and others to read only.  The .jpg photo permissions were as stated above.  That should have been changed also, but I'm happy now.  Have a great day!

Glad it worked - please mark thread as solved

---

### Post by james120 on 2014-04-11
Forgive me for asking, but after looking around I can't seem to figure out how to mark thread as solved.

---

### Post by BlinkinCat on 2014-04-11
> **james120 said:**
> Forgive me for asking, but after looking around I can't seem to figure out how to mark thread as solved.

Hi,

Here's how - [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

### Post by 23dornot23d on 2014-04-11
The thread I linked to was 13.04 but I was just asking a question .......... 

> 
Not sure is wubi supported anymore - see this thread for more of a discussion about it  -   [http://ubuntuforums.org/showthread.php?t=2155015](http://ubuntuforums.org/showthread.php?t=2155015)


But as you say you are running 12.04 LTS ........ and I checked the install instructions and it says wubi install is ok for 12.04 
[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

As you say it will run faster on the hard drive as a proper install outside of Windows ...... glad you got sorted .

To mark the thread as solved is up to the right near the very top of the page - below Results and page numbers ( Thread Tools ) 
the option is in that drop down ... to mark as solved

---

### Post by james120 on 2014-04-11
Thanks to everyone for being patient and easy on a new guy.

---

### Post by sudodus on 2014-04-11
I was also learning the trick to convert the picture to png.

You are welcome and good luck ... and whenever you have a linux related problem, remember to ask here :-)

---

