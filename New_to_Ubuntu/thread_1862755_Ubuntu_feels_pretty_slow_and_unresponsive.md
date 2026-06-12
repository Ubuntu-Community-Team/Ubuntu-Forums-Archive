---
title: "Ubuntu feels pretty slow and unresponsive?"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by dyallo on 2011-10-17
Hello guys, whats up.
I just want to star off by saying that I'm a complete beginner to Linux (apart from some Android shell) and Ubuntu is the first distribution I'm trying for real.
 
So I downloaded and installed the latest Ubuntu 11.10, which I later realized was a development version, so I don't know if I should've chosen 11.04 instead.
 
Anyway I installed Ubuntu on a new partition, 25 gigs with a 3.5 gb swap partition (I read somewhere that swap could be important, so I set aside some disc space)
And everything booted up fine, the desktop looked sort of nice, but not near what I've seen Ubuntu-users show on YouTube etc.
 
I also installed ATI proprietary drivers through the GUI (System settings)
I find it remarkable how little settings I can change in there by the way? No where could I find stuff that affects animations, performance etc.
 
Which leads me to the main problem.. 
I find Ubuntu pretty slow and unresponsive at times. In Windows 7, I can click Windows Explorer, and it would start in an instant. In Ubuntu when I click Chromium or Firefox, it can take up to five seconds! The same when I try to click Software Center, that also has huge loading times. 
This has kind of put me off from Linux.
But I can't help but think that I might have done something wrong.. I mean, the OS has been around for over 6 years.. and people are liking it. No way people could like it if it was that laggy. Right?
 
Another problem is that I can't seem to set up extended display for my TV. My computer screen is 1920x1080, but my TV is only HD-Ready. So when I try to set the different resolutions up, I get an error saying that it's out of range or something..
My solution is to duplicate(mirror) the displays, and then it works. But I don't want that..
 
So.. help me out? How do I get the extended display working?Any tips on how to improve responsiveness? Also how do I get those 3D effects I see on YouTube?
Whats Compiz? Whats Unity? Whats Ubuntu 2D/3D?
 
Hopefully I'll get some answers. Linux has me really excited, so I want to use it as my main OS eventually.
 
System:
Mobo. ASRock P55 Extreme
cpu. Intel i5-750 2.67 Ghz
gpu. ATI 5850
mem. 4gb ddr3 1333 mhz
60 gb OCZ SSD (windows and Ubuntu partition /w Swap)
500 GB hdd

---

### Post by jtarin on 2011-10-17
You might have jumped the gun on installing 11.10. If you have nothing to lose and time you could try reinstalling the Long Term Support release 10.04. Your system might be more responsive. 
Be aware that it does not use the "new' Unity desktop. It runs Gnome 2.

---

### Post by dyallo on 2011-10-17
Aha. I just clicked the huge download link hehe.
Okay, I'll have to read up on Gnome and Unity I guess.
 
But will 10.04 solve the extended display problem? And what might be the reason for the slow responsiveness of 11.10?
So 10.04 is the most stable version I suppose?
 
I should add, that coming from Android, I'm a version-freak :P If it has a higher version number, I'm inclined to use it hehe.
Maybe I should change my way of thinking

---

### Post by jtarin on 2011-10-17
> **dyallo said:**
> 
So 10.04 is the most stable version I suppose?Yes
 
> **dyallo said:**
> I should add, that coming from Android, I'm a version-freak :P If it has a higher version number, I'm inclined to use it hehe.
Maybe I should change my way of thinkingThat's the thinking of most. I recommend a clean install when you decide to downgrade or upgrade. Downgrading is not guaranteed to solve your problems but it is a known factor to start from. Unity desktop still needs some work in areas......my opinion.

---

### Post by dyallo on 2011-10-17
Can I just install 10.04 over 11.10?

---

### Post by Martin Marshalek on 2011-10-17
Yes, you can install 10.04 over 11.10 with no problem. 

If you are a version freak though, might I suggest running Xubuntu 11.10 first. It has all of the updated software like Ubuntu 11.10 but runs XFCE, which is a bit quicker than Unity, yet still very full featured.

---

### Post by rburkartjo on 2011-10-17
yes i have installed xfce and it is great. some tweaks you can do. you can even have it launch the
gnome services when you start. think it is the cat's meow. really like fast

---

### Post by 3rdalbum on 2011-10-17
Er... 11.10 is not a development version, it's the latest release.

Before going to the drastic step of installing an 18-month-old operating system on your computer, you might want to just check the System Monitor (click on the Ubuntu button on the left side, start typing System Monitor and click on it) to see if a program is using up large amounts of CPU time. If so, then you should end it.

---

### Post by mastablasta on 2011-10-17
it could be slow due to number of issues. for example unity uses 3D acceleration and sometimes graphics card drivers are not made as good as their windows version. you could try switching to Unity 2D which looks about the same but is not using 3D acceleration. 
 
then ofcourse there is the fact that Unity interface is still very very new. what you could try is not run it but use a gnome fallback session which would look like the good old gnome. Or just use another version od Desktop as recomended XFCE (which has a look similar to old Gnome but draws faster) or your computer seems more than capable of running KDE (found in Kubuntu which is very similar in look & feel to newer windows). KDE again uses different libraries to draw the desktop. so if Gnome with Unity has issue it is not necessary that XFCE or KDE will also have them.
 
and finnaly you could check if there is any process running in background that shouldn't be running and is hogging the system resources. you can do this by using top command in terminal or checking the processes graphical interface ("system monitor" i think is the name).

---

### Post by dyallo on 2011-10-17
Okay I'll hold off the downgrade to 10.04 for a while for now as it seems there are lots of people happy with it.
 
I appreciate all the replies really! But XFCE and KDE don't really mean anything to me hehe. If you could direct me to links with guides and stuff, maybe I can try to understand it myself.
 
**Like, how would I go about to remove (íf I have to?) Unity, and install another desktop.**
 
**Also, if I chose to install Xubuntu instead - would I have to take any precautionary steps before?**
 
**And finally, if I should ever want to remove Linux from my harddrive permanently. How would I do that? I heard that Ubuntu disables Windows bootloader, so if I'd simply remove the Linux-partition, my computer wouldn't be able to boot hehe.**
**I have no back-up CD's made at all I might add.**
 
Also, how do I add cool 3D effects to the UI? I've seen some pretty badass stuff at YouTube..

---

### Post by snowpine on 2011-10-17
I'd recommend giving a lightweight desktop environment like Xfce or LXDE a try before you give up and reinstall. Here's an easy how-to:

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

If your goal is performance then you should be looking for *less* eye-candy, not more. :)

---

### Post by dyallo on 2011-10-17
Yeah.. assuming it's Unity causing the lag.. 
So you guys suspect my GPU driver is the culprit here?

I mean, my hardware isn't bad. How come I can't have cool animations like the rest of you :(

---

### Post by snowpine on 2011-10-17
> **dyallo said:**
> Yeah.. assuming it's Unity causing the lag.. 
So you guys suspect my GPU driver is the culprit here?

I am not an ATI expert so I won't venture a guess, a forum Search on your *specific* card might find some good information.

If Xfce or LXDE work fine but Unity lags, then I'd say it's Unity that is the culprit. Not to start any flame-wars but Googling "Unity sucks" yields 5.6 *million* results. :)

---

### Post by dyallo on 2011-10-17
> **snowpine said:**
> I am not an ATI expert so I won't venture a guess, a forum Search on your *specific* card might find some good information.
 
If Xfce or LXDE work fine but Unity lags, then I'd say it's Unity that is the culprit. Not to start any flame-wars but Googling "Unity sucks" yields 5.6 *million* results. :)
 
Hehe okay I'll try it out.
So first I have to uninstall Unity or?
Indeed it does seem to suck. It just completely froze on me. Then my dashboard(or whatever you call it, where you have all the shortcuts to apps in the left corner) and the bar at the top disappeared. My music kept playing and stuff, but there was no way I knew to recover, so I had to reboot via terminal..
 
Also: How do I uninstall Linux permantently from my SSD?

---

### Post by snowpine on 2011-10-17
> **dyallo said:**
> Hehe okay I'll try it out.
So first I have to uninstall Unity or?
Indeed it does seem to suck. It just completely froze on me. Then my dashboard(or whatever you call it, where you have all the shortcuts to apps in the left corner) and the bar at the top disappeared. My music kept playing and stuff, but there was no way I knew to recover, so I had to reboot via terminal..
 
Also: How do I uninstall Linux permantently from my SSD?

You don't have to uninstall or reinstall anything to try Xfce (or LXDE or any other desktkop environment). Here's the link again:

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

"Uninstalling" Ubuntu is simply a matter of booting with the Live CD and using the GParted partition manager to delete the partition and create a new partition for installing your new operating system. (Unless you used WUBI, then it's a little different.)

---

### Post by dyallo on 2011-10-17
Thanks mate, I'll give those a shot.
Also, I downloaded something through Software Center called Compiz. 
I tried using it, but I'm not sure if perhaps I needed some other preinstalled software, because almost as soon as I started messing with it, Unity crashed.

---

