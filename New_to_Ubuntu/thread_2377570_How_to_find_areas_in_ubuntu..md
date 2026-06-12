---
title: "How to find areas in ubuntu.?"
date: 2017-11-14
forum: New to Ubuntu
---

### Post by jacko777 on 2017-11-14
Where do I find the following.  I google for answers to things I don't understand.
Most options start with...
by opening System -> Administration -> Servies and unticking

My problem is: Where do I find the system tab to get started.?  I am totally in the dark here and could no longer just give up and hope.
If this tab is somewhere on the desktop, then I don't see it.  If it needs to be placed somewhere, then how do I do this.?

Thank you for your time and patience.

jacko777

---

### Post by yancek on 2017-11-14
If you are using the default Unity Desktop, you should have a panel, probably on the left of the Desktop with a number of icons.  Mouse over them to see what they are.  One of them is a System Settings icon, gear wrench icon.  Which release of Ubuntu, and is it Ubuntu or one of the derivatives.  If Ubuntu Unity, there is an Ubuntu icon on the upper left, click that and it opens a window and you can begin typing, if you are looking for some specific software.  I would also suggest that when you google, you look for a date on the site because there have been a lot of changes over the years and something that worked 5 years ago may not exist now.

---

### Post by jacko777 on 2017-11-14
Hi, yancek.  I have no idea what the desktop is, it is the one that comes with ubuntu 16.04 lts.
The only things on the top of the screen is..  File  Edit  View  History  Bookmarks  Tools  Help
I have looked on the gear wheel down the left side of the screen, what I am looking for is a directory.   It starts with:  System>Administration>Services.   I type this into a Terminal screen and get the 
cd: /system: No such file or directory.  That is the problem.

---

### Post by deadflowr on 2017-11-15
Not sure what you want to do but perhaps make it easier to get help by understanding which Desktop Environment is being used.
open a terminal and run
```
echo $DESKTOP_SESSION
```
You're currently discussing Ubuntu, yet you've prefixed the thread lubuntu.
The output of the above command will give us a more definitive answer to that.

The menu items and layout you mention haven't been included in Ubuntu in years but do still exist (somewhat) in other flavors and Desktop Environments.
(** flavors refer to versions of Ubuntu that use a different Desktop Environment (or it has a special set of abilities ) than the default Ubuntu uses.
See: [flavors]("https://www.ubuntu.com/about/about-ubuntu/flavours")

---

### Post by jacko777 on 2017-11-15
Hi again.
I am definitely using Ubuntu 16.04 lts.  I must have hit the "L" by mistake when I started.

Thank you for your effort to date.  I know little about what is and what isn't with the various flavours.  I just look in Google for answers to what goes wrong.
I wonder now, how I find problems is (if)
 these directories do not exist.?

Hope you might still be able to help.

Regards,
Rod

---

### Post by Quarkrad on 2017-11-15
If you have *File Edit View History Bookmarks Tools Help* at the top of the screen it is possible you have launched Firefox, and that is what you are looking at on your screen.  Having said that, you state you have typed *cd: /system* into the terminal.  That command will not do anything - this is what I get when I type that command into the terminal:

```
dad@dadubuntu:~$ cd: /system
No command 'cd:' found, did you mean:
 Command 'cdp' from package 'irpas' (multiverse)
 Command 'cdb' from package 'tinycdb' (main)
 Command 'cd5' from package 'cd5' (universe)
 Command 'cdw' from package 'cdw' (universe)
 Command 'cde' from package 'cde' (universe)
 Command 'cdo' from package 'cdo' (universe)
 Command 'cdv' from package 'codeville' (universe)
 Command 'cdi' from package 'cdo' (universe)
cd:: command not found

```

Your best move now is to do what deadflowr said and use his command - then you will get somewhere via people on this forum.

---

### Post by cariboo on 2017-11-15
Try a search for:

```
gnome-session-properties
```

in the Unity dash.

To fully populate the application you need to open a terminal and type the following command:

```
cd /etc/xdg/autostart/
```

then press enter, next:

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

---

### Post by jacko777 on 2017-11-15
Hello cariboo, this is the result I got when I used your commands,
It didn't show the directory that I believe is missing.
In fact, as you see here, it returned nothing.

What am I doing wrong.?


rod@rod:~$ cd /etc/xdg/autostart/
rod@rod:/etc/xdg/autostart$ sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
[sudo] password for rod: 
rod@rod:/etc/xdg/autostart$

---

### Post by jacko777 on 2017-11-15
I might hit the cot now.  As an older bloke, I retire early.
I will look up any reply tomorrow.

Thanks all for your help to date, I look forward to getting to the cure tomorrow.

Cheers,
Rod

---

### Post by coldraven on 2017-11-15
There is no system folder. You might like to read about the Linux file system structure, here is a link to get you started.
The forward slash "/" on the left is the root of your drive. All of your own stuff (Documents/Photos etc.) will be in /home/jacko/ or whatever username you chose.
[http://www.thegeekstuff.com/2010/09/linux-file-system-structure](http://www.thegeekstuff.com/2010/09/linux-file-system-structure)

---

### Post by yancek on 2017-11-15
> The only things on the top of the screen is..  File  Edit  View  History  Bookmarks  Tools  Help

As mentioned above, if that is what you see you are in the web browser, most likely firefox.  Close it.

> what I am looking for is a directory.   It starts with:  System>Administration>Services

That method of listing Services hasn't existed on Ubuntu for several years as mentioned in an earlier post so what exactly are you looking for?  Is this a directory with some system files or something you created yourself?  If it is a directory you created, it will probably be in your /home/user directory which you can find by clicking on the File Cabinet icon on the upper left of the panel which should be on the left of the screen, above the gear icon.

---

### Post by cariboo on 2017-11-15
To get a list of what services are running, open System Monitor (gnome-system-monitor) and click on the processes tab. The solution I gave you earlier will show you what applications/processes start up on boot.

---

### Post by jacko777 on 2017-11-18
Hello coldraven,
thank you for the link to the structure, it certainly helped me to understand better, the structure of things. 
Unfortunately, there is no directory for "system" either with or without the capital letter 's'  nor can I find it by using the shorter version "sys" again with or without a capitol 's'

Still wondering where I can find it.

Regards,
jacko777

---

### Post by yancek on 2017-11-18
> Unfortunately, there is no directory for "system" either with or without  the capital letter 's'  nor can I find it by using the shorter version  "sys" again with or without a capitol 's'


I think you are trying to find something which doesn't exist.  On older versions of Ubuntu, when you booted and logged in you would see several tabs at the upper left of the screen one of which would have been "System".  Maybe if you explained what you were looking for it would help.  It has been explained above how to find services running if that is what you want.

---

### Post by jacko777 on 2017-12-04
Hello all who have tried to help.
I'm afraid I cannot answer your questions properly.  I try to put it as clearly as I can (in my mind) but it seems you refer me to the same point again and again.

What I was referring to is this. .... From answers at Google I might get, For example.


Go to System>whatever>edit so and so
in file so and so. delete the first 100 lines
Click on save
exit.

The above is just an example of what I try to do, but  "system"  does not exist.  
I have been advised to go into that area, but I am unable to find it.
How do I find "system".?

---

### Post by deadflowr on 2017-12-04
Post a link to whatever answers you find using google so it might help provide context as to what is being advised.
As stated already there is no such Directory called System to which anyone can give an answer for you.

---

### Post by Geoffrey_Arndt on 2017-12-05
There is a "sys" directory at the first sub-level below / (root).     You can display the root directory in the Files program (aka Nautilus) by click on the label in the left sidebar called "computer".   I assume you're familiar with the basic Gnome or Unity Gui and can access the file system (click the apps icon to get a display of all installed gui apps).

Other uses of System refer to the "System-Setup" program

---

### Post by gordintoronto on 2017-12-05
You are looking at an old, obsolete "how-to". If you tell people what you are trying to accomplish, someone can help you.

---

### Post by Douglas_White on 2017-12-05
[https://youtu.be/wBp0Rb-ZJak](https://youtu.be/wBp0Rb-ZJak)

Looks like a good place to start.

All the Best,
D. White

---

### Post by Rocky_Bennett on 2017-12-05
> **jacko777 said:**
> Hello all who have tried to help.
I'm afraid I cannot answer your questions properly.  I try to put it as clearly as I can (in my mind) but it seems you refer me to the same point again and again.

What I was referring to is this. .... From answers at Google I might get, For example.


Go to System>whatever>edit so and so
in file so and so. delete the first 100 lines
Click on save
exit.

The above is just an example of what I try to do, but  "system"  does not exist.  
I have been advised to go into that area, but I am unable to find it.
How do I find "system".?


Please provide links to the quotes that you are talking about. It will give everybody an idea of what you are talking about.

---

