---
title: "Making a new folder"
date: 2014-11-25
forum: New to Ubuntu
---

### Post by princecharming on 2014-11-25
Hello all. I am new in this website. I want to make a new folder, but there is i face many problems till the time. Please help me friends for making a new folder. I will be thankful to you guys. Please tell solution of this problem as soon as possible.

---

### Post by lisati on 2014-11-25
*Thread moved to **New to Ubuntu**.*

Hello, princecharming, and welcome to the forum.

I have moved your post to its own thread so that the discussion about themes doesn't get confusing for you.

What version and flavour of Ubuntu are you using?

---

### Post by davit2 on 2014-11-25
hi.
$ sudo mkdir /path/to/folder/foldername

---

### Post by Dennis N on 2014-11-25
Open file manager.
Open the folder where you want the new folder to be.
Right-click on an empty area of the window, click on "create folder".
Type in name of the new folder, then Enter.

---

### Post by Impavidus on 2014-11-25
> **davit2 said:**
> hi.
$ sudo mkdir /path/to/folder/foldername
Generally, no, although in some specific cases yes. Most newbies prefer the GUI over the terminal. Dennis N explained how to create a folder the GUI way. Also, don't use sudo for this unless you really want your new directory in some system directory, which you usually don't want.

---

### Post by ajgreeny on 2014-11-25
> **davit2 said:**
> hi.
$ sudo mkdir /path/to/folder/foldername
And if you use that command for a new folder in your /home, the new folder will not belong to you and you won't be able to add any files to it, which would be very frustrating for a new user who may know little about Linux permissions and ownership, particularly if that user has come from a Windows background..

---

### Post by yancek on 2014-11-25
I expect the OP is trying to create a folder in a system directory since the right-click create folder method is common in different operating systems.  Some specifics on where and how he is trying this would have been helpful.

---

### Post by coldcritter64 on 2014-11-25
> **princecharming said:**
> Hello all. I am new in this website. I want to make a new folder, but there is i face many problems till the time. Please help me friends for making a new folder. I will be thankful to you guys. Please tell solution of this problem as soon as possible.

> **yancek said:**
> I expect the OP is trying to create a folder in a **system directory** since the right-click create folder method is common in different operating systems.  Some specifics on where and how he is trying this would have been helpful.

I don't particularly see that, I only see sudo used in davit2's response. However if that is the case...

1. IMO it is safe to assume a Unity desktop (stock standard Ubuntu install = Unity DE and Nautilus as the file browser) when in this section "New to Ubuntu", unless otherwise stated by the OP. 

2. New users should NOT be writing to system areas generally speaking, anything a user needs to run can be run from the home folder "bin" folder (/home/<user>/bin), as it is in the system path eg. this firefox browser (Nightly) I'm posting from runs from that location.

3. Graphical is far easier for some to use, and if ABSOLUTELY needed to write to a system area, **Alt + F2** gives a Unity command prompt, type in "**gksudo nautilus**" (without the quotes) and press "**Enter**", a window pops up ... **enter the user sudo password and "Enter" and you have Nautilus open as root** .... then follow Dennis N's instructions posted earlier.[B]

Shut down the browser immediately the task is complete, root file browsers are capable of destroying an install if used wrongly.[/B]

Note: Dennis N's instructions also work in thunar here, I suspect most if not all file browsers operate similarly for that functionality (make new folder).

---

### Post by lisati on 2014-11-25
I'm not sure if the OP has read any of the replies in this thread yet or if they are likely to. They have already had a number of their posts removed from public view. We shall see......

---

