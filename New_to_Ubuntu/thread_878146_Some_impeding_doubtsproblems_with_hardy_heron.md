---
title: "Some impeding doubts/problems with hardy heron"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by student21 on 2008-08-02
Hi ubuntuites

I have some doubts.  Please help me by giving simple answers that a newbie can understand.

1)  When someone posts many threads on this forum how to keep track of all threads?

2)  I've hardy 64 bit on wubi installation.  What's the simple way to transfer it to dedicated partition without affecting any of my settings, data or configuration??  I've this on HP dv6833us laptop.  And is there a way to present my config. as a sticky after my posts??

3) Is it possible with frequent updates, the memory limit of the partition will be breached in future?.  I've only little experience having my OSes update regularly online.  I've updated everything up-to-date till now in my wubi.  Would it be the updated OS-- if I transferred to dedicated partition?.  And also I'm getting a blank screen for some seconds(I've seen it happening in win98 SE) before it gets to desktop while hardy is booting for last 10 days.  Before that it's fine and only after installing some updates recently, this problem has started to occur. Could it be rectified?

4) I've a toggle enable/disable button for trackpad in my laptop.  when in windows it just enables when I press it.  But in hardy, it brings up 'Ubuntu help center'.  Everytime I need to close it.  Can this setting be changed? if yes how?  Also if i change this setting how can I ever invoke this help center??

5)There's problem with workspaces.  Only one row is working.  Focus never goes to other rows.  What can be done??

6) Won't the KDE applications work from gnome?? I'm having terrible headache with Kopete and aMSN?

I've posted a thread regarding this but I've not received any useful and working solution yet.

[http://ubuntuforums.org/showthread.php?p=5389781#post5389781](http://ubuntuforums.org/showthread.php?p=5389781#post5389781)

7) Where on ubuntu can I find out my video card configuration?

8 ) When i play video clips, movies on hardy using VLC, xine, totem gstreamer /xine, Mplayer I don't get good video quality like I do in windows.  when there's problem in sound, I was pointed to alsamixer ---similarly is there any setting that can improve my video quality on ubuntu??

9)  Once hardy didn't boot properly and hanged halfway still--is there a way to prevent its reoccurence??

---

### Post by Paqman on 2008-08-02
> **student21 said:**
> 
1)  When someone posts many threads on this forum how to keep track of all threads?

You can use the Thread Tools button to subscribe to a thread. Another handy is on the top nav bar Search > Find all my posts/threads

> 
2)  I've hardy 64 bit on wubi installation.  What's the simple way to transfer it to dedicated partition without affecting any of my settings, data or configuration??


You want to get [LVPM](http://lubi.sourceforge.net/lvpm.html). It'll transfer your Wubi install over to a new partition.

> 
3) Is it possible with frequent updates, the memory limit of the partition will be breached in future?.


It's unlikely, the updates are massive. Some of them actually reduce the size of your install. If you start running out of room you have several options:
[LIST=1]
[*][Clean up your system](http://ubuntuforums.org/showthread.php?t=140920)
[*]Expand your root partition
[*]Install more storage
[/LIST]
> 
Would it be the updated OS-- if I transferred to dedicated partition?.

Yep

> 
5)There's problem with workspaces.  Only one row is working.  Focus never goes to other rows.  What can be done??

Can you explain a bit more? How many workspaces do you have?

> 
6) Won't the KDE applications work from gnome?? I'm having terrible headache with Kopete and aMSN?

KDE apps should work fine on Gnome, and vice versa. When you install them the package manager installs all the required KDE libraries for them to function correctly.

> 
7) Where on ubuntu can I find out my video card configuration?

What do you need to know? What sort of video card?

---

### Post by Elfy on 2008-08-02
That's a lot of writing :)

1 - you can use search dropdown at top to find your threads and posts - also you can set to automatically subscribe in you user cp - otptions I think

2 - [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) and  [https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da](https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da)

3 - you can clean out your package cache 
    ```
sudo apt-get clean
``` will remove all downloaded packages, replace clean with autoclean to only remove out of date packages.

---

### Post by student21 on 2008-08-05
Thanks forestpixie, Paqman

The solution to point 1 was useful to find out my posts using thread tools button.  But what is this user cp options??


Regarding point 2)=>  

why I can't download LVPM using synaptic??  How to install LVPM and use?
                      
                      
[http://blip.tv/file/331394](http://blip.tv/file/331394) 
[http://blip.tv/file/331947/](http://blip.tv/file/331947/)

 video tutorials for using gparted and LVPM don't play for me.  Why firefox on hardy don't play these clips I don't understand? 

And How to create "primary partition" using gparted? and how will i know if I'm allocating partition for root or home?  and some say that creating partition and transfer of wubi won't work from wubi.  It'll only work from live cd--is it true??  So can I not transfer this wubi installation from wubi itself??

Is LVPM 8.04 relevant for the updated hardy like 8.04.1?

Isn't there any answer for 4th point?

Regarding point 5) :Currently I've 4 rows and 4 columns in total 16 workspaces.  I created so many for rotating cube 3D effect.  But default-- it came with 2 rows 2 columns totalling 4 workspaces.  Then too, focus didn't go to 3rd and 4th workspace(i.e 2nd row).  And now when I'm having 16 workspaces-- I'm able to get the focus in only 4 workspaces that are present in the first row .  When I try workspaces in other rows--the focus and access simply goes to the corresponding column from first row itself.  How can I use workspaces from other rows. 

Why don't kopete and aMSN work for me?? 

Regarding point 7) => yes to locate information like what sort of video card etc.  In windows-- control panel/device manager will help to get info. about most devices and their drivers.  Like wise where can I check that info. readily about the system on ubuntu?

So isn't there a way to improve video quality in hardy?

10) The dictionary tool in accessories work only when I'm online.  How can it be made to work when i'm offline too?  Also I've got a problem with this dictionary.  When i've other applications like firefox open, if i tried to look up any word in this dictionary it hangs and every time it requires a force quit.  What can be done for this??

11) How can I change username that was given during installation?

---

### Post by student21 on 2008-08-08
Bump:(

---

### Post by Elfy on 2008-08-08
This is the trouble with long lists of problems - people get confused with what has been answered at what hasn't.

You can't download lvpm through synaptic because afaik it's not there.

> And How to create "primary partition" using gparted? ... Right click in unallocated space and create new primary partition - when you get to need mountpoint / is root and /home is home

[Change username]("http://ubuntuforums.org/showthread.php?t=511459") here is search I used - [http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=change+username&sa.x=0&sa.y=0](http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=change+username&sa.x=0&sa.y=0)

```
lspci
``` in a terminal will give you some information of hardware installed

It would be worth looking in the desktop and cutomisation forum for the rows and columns - you only need 1 row of 4 desktops for the cube to work.

I think that is all - if you have any more problems I suggest that you create threads for them - it makes life easier for those answering.

---

### Post by hyper_ch on 2008-08-08
(1) in your user control panel you can set to subscribe to every thread you participate in. When you then click on the UCP again it will show all newly responded to or click then "view all" to show them all,.

(2) make a seperate thread for unrelated issues and mark them as solved - once they are.

---

