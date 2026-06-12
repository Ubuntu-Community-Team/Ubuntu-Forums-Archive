---
title: "What does Ubuntu need?"
date: 2009-07-05
forum: Recurring Discussions
---

### Post by chessnerd on 2009-07-05
Ubuntu is definitely the best distro that I have tried that will work on my hardware. It's learning curve is lower than most other distos and it has lots of great tools. However, there are a few things that I, and I'm guessing other users, miss from Windows that I would like to see put in Ubuntu.

In my opinion there are three big things that would help me use Ubuntu more effectively:

1. A Control Panel - Xubuntu 8.04 (the first version of Linux I ever used) had a Settings Manager that was very nice. Sadly, it was removed in 8.10 to make Xubuntu's XFCE work more like Ubuntu's Gnome, but I think that having all of the settings tools in one place would be very nice for new users. I know that System>Settings is supposed to serve this purpose, but half of the settings are things that I never use and with such a large menu it is hard to find what I am looking for.

2. A CCleaner equivalent - anyone who has ever used CCleaner on a Windows machine can testify that it is an amazing little piece of freeware. Capable of cleaning out history, cookies, and temporary files from multiple browsers at once and also taking care of temporary files from applications such as Word, Adobe Reader, and other programs it can clean out hundreds (in one case thousands) of MB of files that are nothing but junk. An Ubuntu equivalent would be nice.

3. System Restore - if no other improvement is ever made to Ubuntu in the rest of it's history, please, for the love of Linux, give it a System Restore equivalent!!! I have messed up config files and pleaded with my Linux box to let me reset things to yesterday, but to no avail. I had to upgrade to Jaunty, not because I didn't like Hardy, but because my firewall tweaking made the Internet unusable. If I could have just reset the firewall to the defaults all would have been okay, but no, I had to spend 2-3 hours installing Jaunty so I could go online again.

This is just my opinion and I'm sure that everyone here can come up with a tool that they would like to see added to Linux. So, what does Ubuntu need?

---

### Post by monsterstack on 2009-07-05
Good points. But I'd add,

[LIST=1]
[*]Gnome already has a control panel. It's called the Gnome Control Centre. It could be made to be a bit more obvious, though.
[*]Check out the Bleachbit application, or Kleansweep if you're on KDE. It pretty much does exactly what you describe. Having it in the default installation might be good, though.
[*]It's possible to make full system back-ups manually right now. I use Remastersys for that. I don't know about other ways of doing it. But I guess someone could fiddle Remastersys to make a sort of easy-to-use back-up utility. That and encouraging people to create separate home partitions I can see helping out a lot of people.
[/LIST]

As for what I think Ubuntu needs, well, err, I can't think of anything right now. I'll probably think of something later. Tah!

---

### Post by Gizenshya on 2009-07-05
Wow.  I completely agree with all of that!  I've wanted these things myself from time to time.

the only thing I would change is to have an equiv of ccleaner that shreds files, and not just deletes them (marks them for deletion).

---

### Post by credobyte on 2009-07-05
Correct me if I'm wrong, but .. Control Center is already available, it's only not listed in your main menu ( [http://i41.tinypic.com/25fpugl.png](http://i41.tinypic.com/25fpugl.png) ) !

---

### Post by chessnerd on 2009-07-05
> **credobyte said:**
> Correct me if I'm wrong, but .. Control Center is already available, it's only not listed in your main menu ( [http://i41.tinypic.com/25fpugl.png](http://i41.tinypic.com/25fpugl.png) ) !

How do you get to it then and why is it not included in the menu?

---

### Post by stwschool on 2009-07-05
Ubuntu needs games. Good games. There's a serious shortage of good linux games (seriously some of them are just terrible). Once someone gets on that, Linux may gain some ground on Windows. Indeed games are the only thing my Windows partition is used for.

---

### Post by monsterstack on 2009-07-05
> **chessnerd said:**
> How do you get to it then and why is it not included in the menu?

You probably have it installed already. If not, run this

```
sudo apt-get install gnome-control-center
```

To get it in the Menu, right click the Gnome Menu, and then *Edit Menu>System* and check the "Control Centre" box. I have no idea why it isn't shown by default.

---

### Post by chessnerd on 2009-07-05
> **monsterstack said:**
> To get it in the Menu, right click the Gnome Menu, and then *Edit Menu>System* and check the "Control Centre" box. I have no idea why it isn't shown by default.

Thanks, I'll use that. :)

---

### Post by xpod on 2009-07-05
The information in the thread below might cover number 2 for you.That and "clear private data" in your browser;)
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by chessnerd on 2009-07-05
> **xpod said:**
> The information in the thread below might cover number 2 for you.That and "clear private data" in your browser;)
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Nice tips, however, all it did was make me wish I had the programming skills to turn those steps into a single click-run-done program that John Redmond would find easy to use. Why not have an LCleaner application that gets rid of residual config files, runs apt-get autoclean, gets rid of unnecessary locale data and all that without having to open any terminals or opening Synaptics? Just Add/Remove Apps> Search LCleaner> Install> Use. 
As for clearing private data in my browsers, I use 3 browsers in Ubuntu (Opera, Firefox, and sometimes Galeon). It would be nice if I didn't have to open each one individually when I want to clean house.

---

### Post by monsterstack on 2009-07-05
> **chessnerd said:**
> Nice tips, however, all it did was make me wish I had the programming skills to turn those steps into a single click-run-done program that John Redmond would find easy to use. Why not have an LCleaner application that gets rid of residual config files, runs apt-get autoclean, gets rid of unnecessary locale data and all that without having to open any terminals or opening Synaptics? Just Add/Remove Apps> Search LCleaner> Install> Use. 
As for clearing private data in my browsers, I use 3 browsers in Ubuntu (Opera, Firefox, and sometimes Galeon). It would be nice if I didn't have to open each one individually when I want to clean house.

```
sudo apt-get install bleachbit
```

I mentioned this app in the first reply to this thread. Install it already, will ya :P

[COLOR="Red"]Edit[/COLOR]: I just ran a scan. See the results for yourself:

[center][IMG]http://i717.photobucket.com/albums/ww177/stuffandstuffand/Screenshot-7.png[/IMG][/center]

That's some pretty-good space-saving, right there.

---

### Post by xpod on 2009-07-05
> Nice tips, however, all it did was make me wish I had the programming skills to turn those steps into a single click-run-done program that John Redmond would find easy to use. Why not have an LCleaner application that gets rid of residual config files, runs apt-get autoclean, gets rid of unnecessary locale data and all that without having to open any terminals or opening Synaptics? Just Add/Remove Apps> Search LCleaner> Install> Use.
As for clearing private data in my browsers, I use 3 browsers in Ubuntu (Opera, Firefox, and sometimes Galeon). It would be nice if I didn't have to open each one individually when I want to clean house.

Such as the built in Computer Janitor mabey...?
[ATTACH]120058[/ATTACH]

EDIT:Sorry,should have posted that first.

---

### Post by chessnerd on 2009-07-05
> **monsterstack said:**
> ```
sudo apt-get install bleachbit
```

I mentioned this app in the first reply to this thread. Install it already, will ya :P

Thank you very much. This was exactly what I was looking for. I apologize for not getting to it sooner. I got caught up in another discussion and forgot to install it. ;)

First scan result: 222.8 MB, virtually the same as CCleaner gets me on my Windows comps.

---

### Post by The Real Dave on 2009-07-05
I can suggest one thing that Ubuntu needs, a flash player from Adobe that doesn't suck CPU power :D Its the only thing that might tempt me to use Windows.

Also, I'm not sure how many other people are having this problem, but suspending and hibernation have never really worked for me in Ubuntu. When I suspend, when I come back, my sensors read -1C and this drives my fans wild. Other little things like graphics then start to bug me. Hibernation is worse, the above symptoms, with the added fun of resuming to either a black, or a fablously multicoloured display :S Has happened on many different systems, with different graphics chips. 

Now, to be fair, it doesn't bother me much. I'd probably never use those features anyway, seeing as Ubuntu boots so fast on hardware that a clean install of XP is often sluggish on :lolflag:

---

### Post by aysiu on 2009-07-05
Maybe you should vote up these Brainstorm ideas:

[Idea #5567: Very own ubuntu control center](http://brainstorm.ubuntu.com/idea/5567/)
[Idea #9239: Control Center Similar to PCLinuxOS](http://brainstorm.ubuntu.com/idea/9239/)

[Idea #2645: Application to Cleanup User Home Directory](http://brainstorm.ubuntu.com/idea/2645/)
[Idea #10209: Regular system cleaning ](http://brainstorm.ubuntu.com/idea/10209/)

[Idea #1230: System Restore ](http://brainstorm.ubuntu.com/idea/1230/)
[ Idea #12384: Restore Points and Last Known Good Configuration](http://brainstorm.ubuntu.com/idea/12384/)

I've also compiled my own list on what Ubuntu needs:
[What I&#8217;d love to see in Ubuntu 9.10 (Karmic Koala)](http://www.psychocats.net/ubuntucat/what-id-love-to-see-in-ubuntu-910-karmic-koala/)

---

### Post by HappyFeet on 2009-07-05
Ubuntu needs less whining users, and more people willing to help.

---

### Post by aysiu on 2009-07-05
> **HappyFeet said:**
> Ubuntu needs less whining users, and more people willing to help.
I just updated the links in the [What's better than whining on the forums? Making a difference.](http://ubuntuforums.org/showthread.php?t=78741) thread I created almost four years ago.

The main points still hold today, though.

---

### Post by chessnerd on 2009-07-05
> **HappyFeet said:**
> Ubuntu needs less whining users, and more people willing to help.

I'd love to help. The problem is that I don't know where to begin. I could donate money, of course, but that feels empty to me. How do I donate my time and energy to the Ubuntu community? 

Do I program? I have basic programming knowledge of a few languages, but no major knowledge. What languages do I need to learn more of if I want to help out in Ubuntu projects? How would I go about writing a program for Ubuntu if there isn't a project already started? 

Do I rally support? I can post on forums, but if I do this, how do I turn it from whining to something productive? How do I find the right people to actually accomplish the tasks I am advocating?

Some users probably do whine about their problems, and I agree that you shouldn't just go around making post after post begging for something, but I don't want to be a whiner. I want to work. I just don't know how...

---

### Post by aysiu on 2009-07-05
> **chessnerd said:**
> I'd love to help. The problem is that I don't know where to begin. Read the link I posted above.

---

### Post by jfloydb on 2009-07-06
> **HappyFeet said:**
> Ubuntu needs less whining users, and more people willing to help.

That was sure helpful...

---

### Post by Viva on 2009-07-07
> **monsterstack said:**
> Good points. But I'd add,

[LIST=1]
[*]Gnome already has a control panel. It's called the Gnome Control Centre. It could be made to be a bit more obvious, though.
[*]Check out the Bleachbit application, or Kleansweep if you're on KDE. It pretty much does exactly what you describe. Having it in the default installation might be good, though.
[*]It's possible to make full system back-ups manually right now. I use Remastersys for that. I don't know about other ways of doing it. But I guess someone could fiddle Remastersys to make a sort of easy-to-use back-up utility. That and encouraging people to create separate home partitions I can see helping out a lot of people.
[/LIST]

As for what I think Ubuntu needs, well, err, I can't think of anything right now. I'll probably think of something later. Tah!

I've decided that I love you in a non-gay way. I really enjoy reading your posts:p

---

