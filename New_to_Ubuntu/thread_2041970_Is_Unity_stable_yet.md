---
title: "Is Unity stable yet?"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by snowguy on 2012-08-13
I have used 12.04 as my main day-in, day-out OS since a little while after its release and am feeling a little fustrated that windows management still isn't working better. 

I'm wondering if there are others out there who use it day-in day-out who are having better luck then I am.

I was just on a call taking notes in Libre Office Writer and somehow found that though I could see half of the writer screen, I couldn't get it to move back into view using my mouse and tried various key combinations (windows key-W, for example) with no luck. It is not uncommon that I'll find that applications are in different workspaces even though I never put them there. When working with more than one copy of the same app I sometimes can only access one copy. Libre office seems to be a particular problem.

I really like Unity--I just need it to work consistently for me. It is certianly possible that I'm somehow causing these problems without realizing it either by pressing keys accidentally or because I have installed something on my system that is messing everything up. 

My guess is that this isn't the case and that unity just isn't stable yet. If that is true I think maybe I ought to use 10.04 LTS.  

Is there anyone out there using Unity day-to-day that isn't having these problems? If so, are you a regular libre office user? And do you have any suggestions for me?

---

### Post by PaulW2U on 2012-08-13
> **snowguy said:**
>  It is not uncommon that I'll find that applications are in different workspaces even though I never put them there.

Yes this is a known bug - [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/954565](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/954565) and affects all applications.

It seems very little has been done to fix it.  :(

---

### Post by marlow59 on 2012-08-13
I am using 12.04 all the time (only os on my computer) and I regularly use libre office and I have never experienced similar problems. Have you changed some settings in Compiz? maybe it went in conflict with default settings. 
Hope it helps.

---

### Post by simonmoon42 on 2012-08-13
First off, I was a Unity detractor. I ran 10.04 then switched to other distros when Unity came out. 

My experience is yes. Very stable and very fast. I was previously running Win7 on this very laptop and I had many many issues (slow boot, overheating, slow at runtime, phantom shut downs, etc). Since I've loaded 12.04 it has really brought out the performance of this machine. Boot time is around 15 seconds, runtime is quick. 

It isn't perfect, had to set my wireless to not use N and a couple of other things, but it's on par with 10.04. I would recommend it to people that abandoned Ubuntu because of Unity. With Ubuntu Tweak catching up and other tools for customizing, I think it's finally getting to where it needs to be. It's not quite there yet, but getting there. 

My only real complaint is the Software Center. It's too ritzy-glitzy and is low on actual usability (in my opinion). Luckily you can still download and use synaptic or plain old apt-get any package you want. I hope this helps!

Edit: Also, I use Libre Office regularly. Typically with .docx and .xlsx and haven't had any issues.

---

### Post by snowguy on 2012-08-13
PaulW2U, Thanks. I am going to play around a bit and see if that is indeed my issue. It sounds like only part of my problem. If it my issue it will be a lot of help knowing what actions cause which problems. Right now I just don't have any clue when something may go wrong--which is the most frustrating of all.

marlow59, I did install compizconfig setting manager because I had wanted wobbly windows. When I found out I couldn't get it and still snap windows to half the screen I decided to forego it. If I really believed a complete fresh install of 12.04 would solve my problem I'd do it. I just don't want to go through the pain, only to see that it doesn't make any difference.

simonmoon42, just for the record, I'm not even questioning whether it is better than windows. I am glad things are working for you and hopefully I'll get to that point to as I also really like Unity. I just need it to work consistently.

---

### Post by Frogs Hair on 2012-08-13
You may be interested in the link if you use Libre Office a lot. I have been using Unity for three releases and it gets better with each release , but it's not likely I will ever be able to use Linux for work so I can't comment on using Unity on the job.  

[http://www.liberiangeek.net/2012/04/enable-global-menu-for-libreoffice-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/enable-global-menu-for-libreoffice-in-ubuntu-12-04-precise-pangolin/)

---

### Post by ads52 on 2012-08-13
Stable enough here but I will admit that I run it in a Virtual Machine in part because I am not keen to use Unity as my day to day desktop. And I am lucky enough to not experience the problem noted with Libre Writer and others.

And like simonmoon42 the first thing I do with a new installation is install my old friend Synaptic :).

---

### Post by marlow59 on 2012-08-13
did you try to just reinstall libre office, it may sound stupid, but it may be a problem from there.

---

### Post by deadflowr on 2012-08-13
> **ads52 said:**
> And like simonmoon42 the first thing I do with a new installation is install my old friend Synaptic :).

Agreed, Synaptic is a much easier, and verbose package manager than the software center, for the lone fact that I can see everything I'm installing(and queue all my packages for a one shot install), and won't by utterly surprised when additional packages I didn't know I installed come up later during a search. Plus I don't know how to --force version in the software center.

In terms of Unity stability, I find it quite stable. I don't know the OP's problem with Writer, that has not happened to me, yet. That definitely seems like odd behavior. Perhaps a compiz problem?

---

### Post by vexorian on 2012-08-13
What synaptic needs is a couple of things:
- Running without root. Only asking for sudo password when you modify packages.
- An option to copy the list of download locations of the packages. You could use this list on a download manager then move the packages to /var/cache/apt/archives. Right now I just save the "download script" to a file, and copy the contents of the script to the clipboard and rely on jdownloader's detection of URLs in clipboard, but it could be so much easier...

> **PaulW2U said:**
> Yes this is a known bug - [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/954565](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/954565) and affects all applications.

It seems very little has been done to fix it.  :(
I suspect this bug might be related to one I noticed the other week: [https://bugs.launchpad.net/compiz/+bug/974242](https://bugs.launchpad.net/compiz/+bug/974242)

Try the ppa in that link, maybe it fixes this thread's issue?

---

### Post by gbrowning on 2012-08-14
Unity has been stable for me.  Used Compiz to change a few of the behaviors.  Some pop-up windows will not allow you to access the parent window until they receive their pound of flesh.  If that pop=up is somehow hidden you can double click the program's icon which will tile out all that program's windows.  Then choose ..... just a thought.

---

### Post by snowguy on 2012-08-16
@marlow59, I have tried to replicate the issue the bug you refer to shows but with no luck. 

I have been testing for the last 2 days and have encountered the following 2 problems. 
* Gedit was in a separate workspace. It showed in unity bar with light gray arrow (indicating open but in another workspace). Clicked on gedit icon on unity bar but the focus would not switch workspaces. Could not replicate this problem. 
* Had two libre-writer documents open but it showed only one arrow. Was unable to access other libre-writer documents.

Just now I tried reinstalling libre-office per your suggestion using synaptic. We'll see if that works.

@vexorian, thanks for the link to the bug. My problem doesn't match the bug descriptions but you may be right that it is related. I noticed that bug refers to dual monitors. I don't use dual monitors but I do use an external monitor with a laptop. The laptop monitor is disabled when I plug in the external monitor. And I sometimes switch between using the external monitor and using the laptop monitor. This is likely a contributing factor though I haven't been able to identify the specific set of actions that gives rise to the bug. I will try the suggested fix once I see if just reinstalling libre-office solves this.

thanks everyone for the help

---

### Post by smartboyhw on 2012-08-16
Hi.
 
I thought it is stable enough, that is to say.
 
It is a good user experience (though I saw someone in #ubuntu-unity screaming that we should remove it 1 or 2 days ago), and I think it's quite good.
 
So, STABLE!
 
Regards,
Howard Chan
Ubuntu Studio Team member in [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

### Post by vexorian on 2012-08-16
> **snowguy said:**
> @marlow59, I have tried to replicate the issue the bug you refer to shows but with no luck. 

I have been testing for the last 2 days and have encountered the following 2 problems. 
* Gedit was in a separate workspace. It showed in unity bar with light gray arrow (indicating open but in another workspace). Clicked on gedit icon on unity bar but the focus would not switch workspaces. Could not replicate this problem. 
* Had two libre-writer documents open but it showed only one arrow. Was unable to access other libre-writer documents.

Just now I tried reinstalling libre-office per your suggestion using synaptic. We'll see if that works.

@vexorian, thanks for the link to the bug. My problem doesn't match the bug descriptions but you may be right that it is related. I noticed that bug refers to dual monitors. I don't use dual monitors but I do use an external monitor with a laptop. The laptop monitor is disabled when I plug in the external monitor. And I sometimes switch between using the external monitor and using the laptop monitor. This is likely a contributing factor though I haven't been able to identify the specific set of actions that gives rise to the bug. I will try the suggested fix once I see if just reinstalling libre-office solves this.

thanks everyone for the help
Yes, my own problems that were fixed by the ppa were unrelated to multiple-monitors.

---

### Post by Darkhaund on 2012-08-16
Maybe because I am a total newb on the ubuntuy world, but 12.04 LTS seems pretty solid and stable to me

---

### Post by snowguy on 2012-09-07
I've been really trying to watch what is going on in my desktop so I can replicate the problem as I'd like to be able to replicate before I try to solve. I think I finally have figured out what at least is causing 90% of my problem. The bug vexorian pointed to has really helped figure out what is going on. Thanks Vexorian. 

As I see it there are two separate bugs which together really create a poor user experience (at least for the way I use Ubuntu). 
1) If you move a window you are working with "out of the way" so that it is still visible within that workspace but most of it is outside the workspace, then when you alt-tab to that window, ubuntu moves the window onto the workspace most of the window is on (ie not the one you are on) and switches focus to that workspace. 

(If this is someone's idea of a feature then I would argue it should happen immediately just like snapping does rather than waiting until I alt tab to pick up and move the window. )

Also as a user that really doesn't use multiple workspaces but does push stuff off to the side (or to the bottom) so I can focus on what is most critical, it took me a while to figure out what was even going on. 

2) if a window touches the bottom edge of the bottom workspace then when you switch to it from the top left workspace using the unity bar it moves into this really awkward position in the top left workspace where you can't really use it because the top bar and the left unit bar cover part of the application up. At that point, you often need to hold down the alt while dragging the window out of its awkward position with the mouse. 

Now that I have figured out the problem, i can almost live with it because I know how to avoid it and deal with it. Not yet sure if I want to patch through the ppa recommended by vexorian ([https://bugs.launchpad.net/compiz/+bug/974242](https://bugs.launchpad.net/compiz/+bug/974242)). My only concern is messing with conflicts between that patch and continued updates from ubuntu. 

I have to say that these two bugs together are really annoying for people who don't normally use multiple workspaces. The first one pushes you into using more than one workspace when you didn't want to anyway. Then once you do use multiple workspaces you start finding windows in places inaccessible. Uck. 

One other thing that complicates this whole issue is the libre office pop-up children windows. By child window I mean something like the styles window (f11). Sometimes the parent moves without the child. Then sometimes (who knows what it depends on) if you are in the workspace with only the child, clicking on the unity icon doesn't switch to the workspace with the parent--but leaves you in the workspace where you are and brings the child window into focus. From a user perspective it seems like the icon just stops working when that happens--because it used to take you to the your libre office writer document and now it doesn't. 

Hopefully this long-winded comment is helpful to someone else trying to understand why windows seem to go missing in Ubuntu.

---

### Post by cryptotheslow on 2012-09-07
My understanding is that you need to be really careful poking things around with CCSM - much more so since v11.10 and up.

I believe this is because Unity uses dconf as the backend to store its settings whilst CCSM still mostly (if not completely) uses gconf. So it's entirely possible to end up with conflicting settings between the two, with Compiz taking note of gconf and the Unity plugin taking note of dconf.

I may well be wrong or out of date with that understanding :D

---

### Post by snowguy on 2012-09-08
good point cryptotheslow. Just as a note to other readers, I haven't customized ccsm. These bugs appear without doing that.

---

### Post by houseworkshy on 2012-09-08
If Unity is causeing problems with writer on 12.04 you could bung in another GUI so you can get on with your work until you, or some update, sorts it out.  Save the headbanging for lesure time when it's not messing up your workflow.

---

### Post by Epodx64 on 2012-09-08
> **snowguy said:**
> I have used 12.04 as my main day-in, day-out OS since a little while after its release and am feeling a little fustrated that windows management still isn't working better. 

I'm wondering if there are others out there who use it day-in day-out who are having better luck then I am.

I was just on a call taking notes in Libre Office Writer and somehow found that though I could see half of the writer screen, I couldn't get it to move back into view using my mouse and tried various key combinations (windows key-W, for example) with no luck. It is not uncommon that I'll find that applications are in different workspaces even though I never put them there. When working with more than one copy of the same app I sometimes can only access one copy. Libre office seems to be a particular problem.

I really like Unity--I just need it to work consistently for me. It is certianly possible that I'm somehow causing these problems without realizing it either by pressing keys accidentally or because I have installed something on my system that is messing everything up. 

My guess is that this isn't the case and that unity just isn't stable yet. If that is true I think maybe I ought to use 10.04 LTS.  

Is there anyone out there using Unity day-to-day that isn't having these problems? If so, are you a regular libre office user? And do you have any suggestions for me?

Have you ever thought about giving KDE a try I've been using it since the early days of 4.0 and it's really matured into a great desktop Calligra Office suite is really coming into it's own I replaced LibreOffice with it not to long ago You can basically make KDE into anything you want every pixel of it is customizable Kwin produces some great desktop effects and over all it's super stable now (since about kde 4.5) might be worth your time to give it a shot I think its a huge improvement over Unity but thats just my opinion. Unity felt to restrictive and cluttered for me personally. I wasn't a huge gnome fan though either. Cinnamon is another good alternative which you can install thru a ppa to replace Unity. and there's MATE which is just basically Gnome 2.x i'm sure there's a ppa for it somewhere.

---

### Post by vasa1 on 2012-09-08
> **snowguy said:**
> ... 
1) If you move a window you are working with "out of the way" 
...
One other thing that complicates this whole issue is the libre office pop-up children windows. By child window I mean something like the styles window (f11). Sometimes the parent moves without the child. ...
snowguy, like you, I haven't got round to using different work spaces. Like you, I haven't installed CCSM.
But I don't usually move windows. If I want to get a particular window out of the way, I minimize it.
As for the LibreOffice styles window, you can dock it within the main window and toggle its appearance if you don't want to see it at times. After you've docked it, you just deal with one window.

---

