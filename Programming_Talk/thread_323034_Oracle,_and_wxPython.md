---
title: "Oracle, and wxPython"
date: 2006-12-21
forum: Programming Talk
---

### Post by coolsad on 2006-12-21
Hey guys,

I have been searching online for a while now, and I can't seem to find an answer a question. Is there a way to get Oracle to work with a wxPython GUI? I am sure there IS a way, I just haven't found a way yet. 

To be more specific in my mission is this. I have a forum type GUI, where someone enters their Time Spent, Category of Task, and Description. Then at the bottom I have a Send button. I am looking to accomplish two things.

1. Once the information is entered, and the Submit button is hit, for that infomation to be sent to my Oracle Database.

2. I have a Dropdown box(Category Section) and I need(well.. want) to find a way to make it so the Options in the Drop down box are pulled from my Oracle Database.

Like I said, I haven't been successful looking online for a way to do it, so I am hoping one of you guys can give me a website that has it, or give me a walk-through yourself. I have my code available to see if needed. I have two sets, one made by a program, and one made myself. Personally I like the look of the one made by the program more, but the code is setup in a weird way. So, if you need the code to know how I set it up, just ask and I will post it for you.

Thanks in advance for anyone who can help :)
Ed

---

### Post by pmasiar on 2006-12-21
> **coolsad said:**
>  Is there a way to get Oracle to work with a wxPython GUI? 

wxPython is 100% independent from Oracle. Sorry I cannot help you with  wxPython or any other GUI - HTML is my GUI.

Oracle is tricky. library is cx_Oracle. I had really hard time to compile Oracle database (both client and server): Oracle's preferred distro is RedHat, now Oracle even support own RH-based distro. In some guides, I even found advice how to change /etc files to fool Oracle it installs on RH - for install only, revert changes after install. Ridiculous! When I was doing this exercise in August 06, all worked not smoothly but OK and I eventually succeeded - took me couple days but doable. This time around, all hell broke lose. Sorry I cannot post links now - they are in our wiki which is behind firewall.

Oracle install script did not recognized swap for some reason, but Google recognized error message and found me workaround to make temporary huge swapfile. I forgot details, mkswap is the command IIRC. Then I tried to compile cx_Oracle, failed, run out of time, boss chewed me a little, and because my experiment with Python failed, I had to switch to java. :-(

Oracle changed something, and looks like debian gurus did not catch up yet. I suggested to switch to MySQL but it was denied.

Hope you will have more luck! If you do, please post found solution here - I may try again.

---

### Post by troach on 2006-12-22
> **pmasiar said:**
> wxPython is 100% independent from Oracle. Sorry I cannot help you with  wxPython or any other GUI - HTML is my GUI.

Oracle is tricky. library is cx_Oracle. I had really hard time to compile Oracle database (both client and server): Oracle's preferred distro is RedHat, now Oracle even support own RH-based distro. In some guides, I even found advice how to change /etc files to fool Oracle it installs on RH - for install only, revert changes after install. Ridiculous! When I was doing this exercise in August 06, all worked not smoothly but OK and I eventually succeeded - took me couple days but doable. This time around, all hell broke lose. Sorry I cannot post links now - they are in our wiki which is behind firewall.

Oracle install script did not recognized swap for some reason, but Google recognized error message and found me workaround to make temporary huge swapfile. I forgot details, mkswap is the command IIRC. Then I tried to compile cx_Oracle, failed, run out of time, boss chewed me a little, and because my experiment with Python failed, I had to switch to java. :-(

Oracle changed something, and looks like debian gurus did not catch up yet. I suggested to switch to MySQL but it was denied.

Hope you will have more luck! If you do, please post found solution here - I may try again.

Can you use a JDBC driver for Oracle?

---

