---
title: "Would like to know how to simply install a windows based program"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by Rebecca1989 on 2011-12-20
Hello to all viewing :)

 I have hardly any knowledge of computers.  I can turn one on, print something out, access the internet but that is where my computer skills end.

I have got my son a leapfrog my pal scout for christmas and would like to be able to set it up so it can say his name on opening on christmas day.  On Sunday night I spent 5 hours trying to find a way to do this and I discovered WINE.  The problem I have with WINE is that I do not understand how to use it, so in all truth I have given up.  Yet I would really like to not have to go to my parent's house and use their PC to set up the toy.

So basically I am wondering if someone out there could guide me through WINE without using confusing terms (I really got baffled when my friend referred to my GUI), or if someone knows of a simple way for me to get the Leapfrog connect software onto my computer?

I would also like to try and run ejay6.

I would be grateful for any help offered.

I am currently running Ubuntu 11.10.  If any other information is required please ask in the simplest terms possible, and let me know where I can find it.

I would really like to learn Ubuntu so I can teach it to my dad who is a computer Whizz!

Thank you in advance

Rebecca :-k

---

### Post by anewguy on 2011-12-20
First off, how do this toy communicate to the PC - via USB?  If so, WINE won't work for you anyway.  If you have a copy of Windows, your better solution would be to download VirtualBox and the Extension Pack from Oracle's site, then install Windows in Virtual Box.  This will create a "virtual machine" inside of VirtualBox.  This "virtual machine" will think it has control of the PC, although Linux still will, and it will run Windows as normal.

Post back if you need additional help.

Dave ;)

---

### Post by oldos2er on 2011-12-20
With a 'Garbage' rating, I wouldn't even attempt to install this on Ubuntu. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=10849](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10849)

You need real Windows.

---

### Post by guyver_dio on 2011-12-20
Assuming the software is on a cd, with wine installed, pop in the cd, browse the cd to find a file that looks like the installer (probably called setup.exe or autosetup.exe or something), right click on that, hover over 'open with' then select 'Wine Windows Program Loader'. 

But for first timers, I recommend you download PlayOnLinux. It's like a user friendly wine software manager, it's easier to use. 

Don't hold your breath though, it may or may not work.

If you think you'll still be relying on alot of windows software, it may be best getting someone to install windows on your computer alongside ubuntu (called dual booting), that way you can switch to windows for specific things like this.

---

### Post by anewguy on 2011-12-20
That's why I recommended VirtualBox.  I also mentioned USB and using VirtualBox because unless it has changed you cannot access USB devices (other than things like mice and keyboard) in WINE.

I still recommend VirtualBox - you will need a Windows CD in either case and at least in VirtualBox Windows is limited to what damage it can do to your PC.

Dave ;)

---

### Post by QIII on 2011-12-20
The disadvantage of VirtualBox, particularly for graphics-heavy applications, is that you are stuck with the virtual graphics hardware -- which is not very robust.

---

### Post by anewguy on 2011-12-21
BUT.....if you simply want to talk to a toy it is more than adequate, and therefore more than adequate for the question asked.  They didn't ask for high performance for gaming, etc., - they asked for a way to talk to a toy.

---

### Post by QIII on 2011-12-21
For talking to the toy, agreed.  The OP mentioned another game as well.  I did not mean to offend.  I use VirtualBox pretty extensively in my work.  I was simply pointing out a limitation to the OP.

---

### Post by jtarin on 2011-12-21
> **anewguy said:**
> BUT.....if you simply want to talk to a toy it is more than adequate, and therefore more than adequate for the question asked.  They didn't ask for high performance for gaming, etc., - they asked for a way to talk to a toy.Depending on age "Talking to Toys" may not be advisable without a psychiatric eval.:D

---

### Post by QIII on 2011-12-21
Jtarin....   Check out my avatar....  Hee. Hee. Heeeeeee!  Whoopie!

---

### Post by anewguy on 2011-12-21
I, too, am "medicated for your protection" as well!  I love that on the avatar!  

I should add - I don't recall talking to toys in the last 45 years or so.  However, I do hear my cat talking to me.  All of those "I like that too, Dave", "You mean 3:30 a.m. is too early to get up?", "Hey, did you know if I poke you right here you wake up?" and other things.

Dave ;)

---

### Post by Rebecca1989 on 2011-12-24
Thank you to all for trying to help, I did have to start the dog at my parents as it is connected via USB.

Have a Merry Christmas and a Happy New Year

---

