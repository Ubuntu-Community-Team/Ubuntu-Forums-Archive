---
title: "Ubuntu Login Problems (n00bie)"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by adroit9 on 2008-10-08
Alright, so a friend of mine told me about Ubuntu a little while ago.  After some research, I decided to try it out for myself, as everything about it seemed pretty cool.  To be safe, I thought I would try this method of install: [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

Things seemed to work.  For a while.

As I went to login in Ubuntu, I got the cool little bongo noise and all, then typed in my username and password, got the cool little startup music, but then the screen went black and the bongo noise happened again.  I then found myself back at the login screen.  I know I have my information typed in correctly, as when I tried other login names, it notifies me that the information is invalid.  It's stuck on a never-ending cycle of login screens at the present moment.

Anybody have any ideas as to what's wrong, or what I need to do to fix this?  Thanks in advance for any help.

---

### Post by pytheas22 on 2008-10-08
At the Ubuntu login screen, there's a menu that you can click (should be in the bottom-left portion of the screen, I believe) to choose which session to launch.  There should be an option called "Failsafe Gnome" or something similar to that.  Please try logging in with that option and let us know if it works any better.

Also, what is the exact model of your video card?

---

### Post by eternalnewbee on 2008-10-08
I can not give you any advice on wubi, but I would suggest creating a partition and installing Ubuntu there. Then you can dual boot Ubuntu and windows.
I also suggest waiting for responses from more experienced users, as they can surely give you advice about wubi.
Good luck.

---

### Post by eternalnewbee on 2008-10-08
Hi there pytheas22.
How do you "bump" a thread?

---

### Post by pytheas22 on 2008-10-08
> How do you "bump" a thread?

It just means to post something in the thread like 'bump' so that it has another chance to gain attention before it gets buried again.  I just have that in my signature because once in a while I read a thread, forget to respond, close the tab and don't think about it again.  If the thread gets bumped, it goes back to the top of my subscription list so that I remember to respond.

---

### Post by adroit9 on 2008-10-09
> **pytheas22 said:**
> At the Ubuntu login screen, there's a menu that you can click (should be in the bottom-left portion of the screen, I believe) to choose which session to launch.  There should be an option called "Failsafe Gnome" or something similar to that.  Please try logging in with that option and let us know if it works any better.

Also, what is the exact model of your video card?OK, logging in using the Failsafe GNOME session does indeed work.  I do not recall exactly what my video card is, so is there a way to do a check whilst using Ubuntu?

Thanks again for helping me out, dude.

---

### Post by pytheas22 on 2008-10-09
Since you can get into the failsafe session, please open a terminal (Applications>Accessories menu), run the following command and post the output here:
```

lspci -nn
```

That will tell us which video device you use.

Also, go to System>Preferences>Appearance and under the "Visual Effects" tab, set effects to "None."  Then try logging into a normal session again.  Does that work?  The effects might be the cause of the problem...

---

### Post by adroit9 on 2008-10-09
Alright, I got it working. Thank you for all your help.

---

