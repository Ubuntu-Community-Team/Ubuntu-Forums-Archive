---
title: "Any problems from deleting compiz in 11.10 on GNOME?"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-19
I decided to delete compiz, but I'm wondering if I do so, would I be creating problems with Unity? I uninstalled via Software Center, but see now that the System Monitor says it's still running (surprise), and consuming more resources than any other process (not that I can actually see anything it's doing of value, which is why I want to purge the files). 

If you know of any problems a purge might create, please let me know. Thanks.

---

### Post by audiomick on 2012-04-19
As far as I know, Unity is a compiz plug in. That means, if you succeed in removing compiz, Unity will go with it.

---

### Post by NikTh on 2012-04-19
> **jps2012 said:**
>  I uninstalled via Software Center, but see now that the System Monitor says it's still running (surprise), 

maybe you mean ccsm ? compiz config settings manager .

---

### Post by jerome1232 on 2012-04-19
> **audiomick said:**
> as far as i know, unity is a compiz plug in. That means, if you succeed in removing compiz, unity will go with it.

+1

---

### Post by jps2012 on 2012-04-19
Gentlemen, you're absolutely right. I meant ccsm. I couldn't figure out how to run the configuration manager. I wasn't getting the options I've read about in the forums, various websites. I deleted it. But not compiz. I guess that would be nearly fatal. 

Thanks for catching my error.

---

### Post by audiomick on 2012-04-19
Ah, that sounds better.

No, there is no danger in deleting CSSM, as far as I know.

You mentioned that you could still see it in the system monitor. Is that after shutting down and re-starting?

---

### Post by jerome1232 on 2012-04-19
Which is why I was +1'ing his post. Giving confirmation that his info was correct.

---

### Post by mastablasta on 2012-04-20
> **jps2012 said:**
>  But not compiz. I guess that would be nearly fatal. 
 
 
 
not really, you should still be able to use metacity instead i think.

---

### Post by jps2012 on 2012-04-22
Thanks, folks for the additional instructions/suggestions. It does seem that there's a negative impact from uninstalling ccsm. See this thread: 

[http://ubuntuforums.org/showthread.php?t=1962784](http://ubuntuforums.org/showthread.php?t=1962784)

Basically, the thread notes that I uninstalled ccsm, then reinstalled it. I'm having trouble now with seeing borders on windows; I lost the little red "quit" circle for apps, etc. 

Any suggestions about how to fix the issues would be appreciated.

---

### Post by jps2012 on 2012-04-22
[FONT=Arial][SIZE=3][COLOR=#000000][FONT=Arial]I  upgraded to 12.04 this morning, hoping that would repair the issues  with compiz (Unity). It didn’t work. The issues have just gotten worse.  I’m hoping someone can tell me how to get back the functionality. Here’s  an overview of the current issues: [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]1. Sometimes the login panel freezes after I enter my password. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]2. Windows are locked in place when they open (they can’t be moved or resized) [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]3. Keyboard shortcuts no longer work when trying to switch between programs (ALT+Tab gives no response)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]4.  Because windows can’t be resized or moved, I can only access the  uppermost window (for whatever application happens to be sitting on top  of others). In other words, I can only use two programs at a time,  unless the windows just happen to open in an offset position (with one  being visible under another). I can still access Terminal via tty. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]5. Applications open without a full set of menu options; the “quit” icon is missing, for example. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]6.  There are no sidepanels, no cog to allow me to logout or attempt to  change settings in a settings manager, no access to the software center,  etc. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I’ve  tried logging in (when I can log in) in GNOME, GNOME CLASSIC, Ubuntu,  and none of the environments allow me to overcome any of the above. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
Per the recommendation above (to use metacity instead), I have no access to the Software Center now, so I won't be able to do any installs that are suggested by 'general idea.' I'll have to do any repairs from the command line. 

[COLOR=#000000][FONT=Arial]If  anyone has a recommendation about how to repair the above … whew.  That’s a lot to overcome. But thanks to anyway who tackles any part of  it. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by jps2012 on 2012-04-22
Good news. I've got a lot of the problems fixed, but still haven't figured out how to overcome the issue with windows not being allowed to be resized (hovering over the lower right corner doesn't bring up the resize icon). 

The problems (in case anyone else is seeing the same thing) were caused, in part, by following the advice listed on this site: [http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic](http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic)

The instructions say to edit the gnome-classic script (the file is named below): 
gnome-classic.session

After I followed the instructions, I lost most of the functionality of the GUI. 
I HIGHLY recommend not following those instructions for 12.04! I'm
not sure how they'd work for other distributions, but WHEW! A dicey operation.

---

### Post by jps2012 on 2012-04-22
I tried to use metacity, per the suggestion above. Because dash couldn't find it, but the Software Center says it's installed (a conflict I can't understand), I tried to invoke it from the command line. 

Terminal returns: 

"Window manager warning: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager." 

It seemed those conflicts couldn't be resolved, and I knew of no way to invoke it to overcome the problem with my windows not being able to be resized. 

Then I realized Terminal was suggesting I could invoke it with "metacity --replace" 

I did. And every window froze. I lost ALL interactivity with the GUI and had to do a hard restart (that's pushing the power button, for us noobs). 

Yikes. I still have no ability to resize windows, but I'm not going to try metacity again unless I understand how to overcome the obvious system conflicts it creates.

---

### Post by grahammechanical on 2012-04-22
Please do not get upset but you are messing with things that you do not understand. And this is why you are having problems. Please let me illustrate.

When we do a fresh install of Ubuntu 11.10 or 12.04 the install process will set up a basic Ubuntu desktop that will run on low specification machines.

If we have a video card that is capable of 3D effects we will be offered an opportunity to install a proprietary driver that can make full use of the video card.

Then before we log in if we click the cog icon we will see two options - Ubuntu or Ubuntu 2D.

If we choose Ubuntu we get Compiz as the compositing manager or window manager with Unity 3D as the user interface.

If we choose Ubuntu 2D we get Metacity as the compositing manager or window manager with Unity 2D as the user interface.

This is why, if you are in Unity 3D and you remove Compiz itself you break the desktop.

It is also why you can not start or load metacity while you are using a user interface managed by Compiz. You get the message "already has a window manager."

Metacity is already installed. This was done as part of the standard install of Ubuntu, just as Compiz was installed.

We can switch between the two at log in time. Ubuntu 2D with Metacity and Unity 2D is the fall back mode for those machines that do not have the video card that can run Unity 3D. This is the basic Ubuntu method.

I suggest that you are in the situation of needing a fresh install. By upgrading you did not remove what was causing the problems.

I have more than one Ubuntu on my machine. I have a Ubuntu that I work with.

For messing around and trying out different things I have another Ubuntu. Then when I mess things up I simply re-install.

I have learned never to mess with my working Ubuntu, and that re-install is less painful then trying to fix.

Regards.

---

### Post by jps2012 on 2012-04-22
Grahammechanical: You're absolutely right. I'm messing with stuff I don't understand. I'm willing to take some risks, though, because of how much I've learned over the last three weeks or so (before that, I was strictly in the point-and-click camp). 

It's true that sometimes I do something that causes problems, but so far I've been able to research it and fix it, or get good advice here (the best forum of ANY kind I've ever seen). 

If we (meaning computer users in general) settled purely on "leave it alone if it works," would this forum exist? Windows works, doesn't it? Mostly. Sometimes. Or well enough--for some people. But for those of us that want continual improvement, that means changing something (as I understand the definition). 

I think that any change means risk. But of course we calculate the probably outcome, and decide whether the risk is likely to give a better payoff than a loss. If I do a survey (a passive one, just reading what's in the forum) of what people are talking about here, what I see is a lot of people who aren't satisfied with "hell, I can get by with what I have." 

I see people who want to take risks because they want something better. As much as I want a computer that works, I want to understand why it works. How it works. And how to fix it when it's broken. I'm not satisfied to just stare at it and take whatever it gives me. Therefore I'm willing to take risks. 

And learn. (Please don't be offended.)

---

### Post by jps2012 on 2012-04-22
Grahammechanical: I did learn more about what went wrong (and how I caused some of it by trying to invoke metacity) from your message. Thank you.

---

### Post by stinkeye on 2012-04-23
Some info for you.

Determine session your logged in to
```
echo $DESKTOP_SESSION
```

**Ubuntu **uses compiz as the window manager. Unity is a plugin for compiz.
**Ubuntu 2d** uses metacity as the window manager. The panel and launcher look similar but are different programs than seen when running compiz in the **Ubuntu** session 

Check if compiz is running
Install wmctrl...
```
sudo apt-get install wmctrl
```
then
```
wmctrl -m
```.


When in the ubuntu session you can set unity back to defaults with alt + F2 and enter...
```
unity --reset
```


Creating a new user account and logging into that account can help in determining if you have conflicting configs caused by the upgrade.

---

### Post by jps2012 on 2012-04-23
Thanks again, grahammechanical and stinkeye. Those are the best overviews of the GUI  (I hope I'm using the right terminology) I've read. I didn't know that different logins resulted in different compositing managers (and I didn't know what a c.m. was). Very useful info. 

I'm basically back in business, with the only remaining issue (that I see so far) being my windows have no borders (which causes one to blend into another, making it difficult to orient sometimes), and I can't resize windows (no drag handles appear when hovering over the lower left corner). 

I've been trying different options in the Window Manager section of Compiz Configuration Settings Manager, but nothing has worked so far. One of the things that makes CCSM so difficult to understand (and use) is that when you pick an option, you're sometimes warned about possible conflicts. Then you're given a series of options as to how to resolve those conflicts (none of which make sense to me, given that they use terminology I'm unfamiliar with (and I imagine most people new to Ubuntu are unfamiliar with it). There's no option to back out entirely--meaning it's guesswork from there out. Scary. 

Stinkeye: I ran the commands you suggested. 
            
echo $DESKTOP_SESSION
          Terminal reports "Ubuntu"
wmctrl -m
         Terminal reports: 
[B]Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF[/B]

So now I'm wondering if I should be in desktop mode--if that's the issue with windows not being able to be resized. I'm going to keep researching it. 

I appreciate all the help you've given me. JPS

---

### Post by stinkeye on 2012-04-23
Check in  **ccsm > window management**  that the Resize Window plugin is enabled.

It should be enabled with default settings
eg in the terminal (this sets **all** the compiz plugins back to default settings and takes a while to complete)
```
unity --reset & disown
```

The **& disown** sends the process to the background so you 
can close the terminal without affecting the running process.

Should also be able to resize with **alt+middle mouse button**

Also when changing settings in ccsm it may not reload properly and can usually be fixed by reloading compiz...
```
compiz --replace & disown
```

> So now I'm wondering if I should be in desktop mode--if that's the issue with windows not being able to be resized. I'm going to keep researching it.
All that is referring to is if you have minimized all your windows with
the ctl+alt+d show desktop shortcut.
eg if I run **wmctrl -m** after I have used the show desktop shortcut I get...
```
glen@Precise:~$ wmctrl -m
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: **[COLOR="Red"]ON[/COLOR]**
```

---

### Post by jps2012 on 2012-04-23
Stinkeye: Before I saw your post, I went to the Window Management section again in ccsm and discovered I just needed to either KNOW or set what the hotkeys were for window resizing. WHEW! Back in business (but still some missing functionality in window management). 

And then ... 

I ran "unity --reset & disown". Voila! The windows borders are back! And I can now close apps by clicking in the GUI (the red "quit" icon was missing). 

That is _one awesome command to know_. Thank you. I'm guessing that "& disown" can be used as a switch for any command that launches an app from Terminal, if you want to dissociate that app from the terminal (I THINK that's what you're saying). 

If so, that's a big help, too, because prior to this post I had no idea how to keep Terminal-launched apps running if I quit Terminal. 

WOOOOOOW! And now, happily, sadly I CAN STOP DINKING AROUND (learning, actually) and do my "real" job (a lot more efficiently). Thanks to all of you.

---

### Post by stinkeye on 2012-04-23
> That is one awesome command to know. Thank you. I'm guessing that "& disown" can be used as a switch for any command that launches an app from Terminal, if you want to dissociate that app from the terminal (I THINK that's what you're saying).
Yeah, that's what I meant to say.
I tend to make up my own terminology. ;)
Glad to help.

PS: Once you have set ccsm up to your liking use the preferences in the bottom left to export your profile
so you can then import when you stuff something up.

---

### Post by jps2012 on 2012-04-23
Grahammechanical: I think it's a very good idea to have a second partition, so I could go back to 11.10 if I needed to. I have to figure out how to partition, because there's only one on this machine. 

I've been reading the FAQs on it (I started looking into it a couple weeks ago, but I've been chicken to try; I also have to learn how to use Clonezilla first). 

It would be wise, as you pointed out, to have a backup user account so I don't get stuck on repairing issues associated with a single account. All I have to do is get up the nerve.

---

### Post by jps2012 on 2012-04-23
Stinkeye: I didn't know I could export settings. Again, that's great to know. I would like to get to a point where everything is basically stable (it would help if I could stop changing things--but that's also a learning exercise). 

I'm guessing "stuff something up" is an Aussie term? (Google translate doesn't offer anything for Aussiespeak, but it's pretty obvious I think.) 

My previous efforts to reconfigure compiz were FUBAR.

---

### Post by audiomick on 2012-04-23
> **jps2012 said:**
> I have to figure out how to partition, because there's only one on this machine. 

More reading... ;)
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

---

### Post by jps2012 on 2012-04-23
Thanks, audiomick. I appreciate the resources. Now if I could just download some courage.

---

### Post by audiomick on 2012-04-23
Don't panic. Gparted doesn't do anything destructive until you press the "yes, I am sure" button. Just take your time and really look at what is on the screen.

It might help if you make notes with a pencil and paper as you go, just to keep track of where you are at. Have a look at what you have got, have a think about what you want to do, make a plan on paper and makes notes of your progress.

---

### Post by audiomick on 2012-04-23
> **jps2012 said:**
> I'm guessing "stuff something up" is an Aussie term? 

Yep. Means "to accidentely cause something to not work anymore". ;)

---

### Post by jps2012 on 2012-04-24
Michael: Good advice. I'm going to go very slowly, and take notes. After I do a backup with Clonezilla. And get over some fear I still have.

---

