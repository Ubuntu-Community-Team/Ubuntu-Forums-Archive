---
title: "A little help with two questions, please."
date: 2015-05-11
forum: New to Ubuntu
---

### Post by andrew_hite on 2015-05-11
Just got my pc up and running yesterday on ubuntu (i think its 14.04 at present) and i am having a slight issue keeping stable mouse functions. I can move pointer fine but something is interfering with being able to click on things, especially annoying in web pages. Also i would like to know if there is anything like Windows task manager in the ubuntu program. Other than that things are working fairly well, aside from my general inexperience which should rapidly go away.

---

### Post by yancek on 2015-05-11
Check the link below for options.  The other links show options also.

[http://www.cyberciti.biz/faq/show-all-running-processes-in-linux/](http://www.cyberciti.biz/faq/show-all-running-processes-in-linux/)

[http://www.ubuntufree.com/top-5-system-monitoring-apps-with-gui-for-ubuntu-14-04-and-14-10/](http://www.ubuntufree.com/top-5-system-monitoring-apps-with-gui-for-ubuntu-14-04-and-14-10/)

[http://www.omgubuntu.co.uk/2011/11/5-system-monitoring-tools-for-ubuntu](http://www.omgubuntu.co.uk/2011/11/5-system-monitoring-tools-for-ubuntu)

---

### Post by Bucky Ball on 2015-05-11
*Thread moved to **New to Ubuntu**.*

Welcome. I use top or htop myself. Not that I use them much. What are you wanting to do with the task manager like GUI? Just see which programs are currently running? You can always hold down alt and tap tab. That would show you all apps/windows that are open. Just a thought ... :-k

If you want to kill a misbehaving app, you can use the killall command in a terminal, for instance:

```
killall firefox
```

... will kill a crashed Firefox session.

---

### Post by andrew_hite on 2015-05-11
Just wanted to see active processes, have been trying to rebuild my program lists and have had things freeze up. Whenever windows had similar conditions, i was able to see and end any processes that were locked up or interferring (ts3 for linux was especially troublesome, had to default with wine to get windows version working).

---

### Post by andrew_hite on 2015-05-11
Thanks yancek

---

### Post by walttheboss on 2015-05-11
> **andrew_hite said:**
> Just wanted to see active processes, have been trying to rebuild my program lists and have had things freeze up. Whenever windows had similar conditions, i was able to see and end any processes that were locked up or interferring (ts3 for linux was especially troublesome, had to default with wine to get windows version working).

Control Escape works in Kubuntu to see processes.  Sort by cpu or memory. 

Alt-F2 takes you to the task manager.

---

### Post by amanchesterman on 2015-05-12
There's Task Manager in Xubuntu / Xfce, which does what you want, but I don't know if there's anything equivalent in Unity.

---

### Post by Bucky Ball on 2015-05-12
> **amanchesterman said:**
> There's Task Manager in Xubuntu / Xfce, which does what you want, but I don't know if there's anything equivalent in Unity.

Mind sharing what that is? I use xfce4 and Xubuntu before that and I don't remember seeing anything like the Windows task manager ...

---

### Post by Holger_Gehrke on 2015-05-12
> **Bucky Ball said:**
> Mind sharing what that is? I use xfce4 and Xubuntu before that and I don't remember seeing anything like the Windows task manager ...

'xfce4-taskmanager' is in the "System"-menu in XFCE as "Task Manager" and stays in the tray when started. And in Unity -- at least on 12.04 -- there's 'gnome-system-monitor'. And of course there's top, htop, ps and kill / killall on the command line, which you can use in a virtual terminal (ctrl-alt-f1 to ctrl-alt-f6, ctrl-alt-f7 to return to the GUI) if a program has managed to render the GUI completely unresponsive ...

---

### Post by newb85 on 2015-05-12
In Unity, the graphical program would be System Monitor.  One tab is Processes, which can be sorted by fields like Memory and %CPU, etc.  Another is Resources, which graphs use of CPU, Memory, and Network over time.  The third is File Systems, which simply shows how much of each mounted partition is used.  I guess it differs from WTM in that it doesn't have an Applications tab.

You can also install System Load Indicator (the package is actually called indicator-multiload), which keeps running graphs of whatever resources you choose in the app indicator area in the upper-right corner.

---

### Post by andrew_hite on 2015-05-12
Just ran across a thread that basically said that there is a limit of two active windows. Is this what would cause me to lose the ability to click on say a web page if i have ts3 in wine and steam running?

---

### Post by newb85 on 2015-05-13
A thread that said what?  Please link to that thread.  Unless I'm mistaken about what's meant by "active windows", that's flat wrong.

---

### Post by andrew_hite on 2015-05-13
Sadly i cannot, been a few days and there are quite a few new threads it seems. I have been trying to figure out what is going on with mouse function. I can use the tabbing to navigatei n the desktop but that gets rather problematic in web pages and does not seen ti work in a few games that i got back. Essentially if i keep the number of active programs (the ones in the alt-tab window) at two or so,i can keep the ability to click on things a vast majority of the time. If i try for another program on top of that, it goes down the drain till i ditch a program.  Other than linux version of ts3 not installing even after i have tried some solved threads solutions, everything is working pretty good. It must be i am missing something somewhere, usually that is what it is with me.

---

### Post by Holger_Gehrke on 2015-05-14
> **andrew_hite said:**
>  ... Essentially if i keep the number of active programs (the ones in the alt-tab window) at two or so,i can keep the ability to click on things a vast majority of the time. If i try for another program on top of that, it goes down the drain till i ditch a program. ...

Does it not register the clicks at all or with a long delay ? Sounds to me like you're either running a very slow system or are running out of memory and swapping or something is using up processing power. Could you please give us an idea what kind of machine you're using ?

That two windows-limit definitely is bogus, I currently have 5 windows open on a low-powered netbook and don't have any problems with the mouse / touchpad.

---

### Post by newb85 on 2015-05-14
It could well be hardware related, like Holger said.  Info on your hardware would be helpful.

Just to check, though, what programs are you using when you see this problem.  Is it any programs in particular?

---

### Post by abrianb on 2015-05-14
Andrew I think you are looking for "system monitor". It will show open apps, memory usage by app, etc.

---

### Post by Geoffrey_Arndt on 2015-05-14
AH,

At this point, we are not sure what your hardware is (make/model, ram, type of graphics (intel, amd, nvidia), or what version of Ubuntu you're actually running (i.e., not running Xubuntu or Lubuntu).  This info is always a good thing to provide right at the start of a new thread.

Also, are you aware that many applications in Linux run by pressing "one" mouse click versus "two"?    (on some distros like Kubuntu, you can change those defaults).,

Did you try the "Systems Setting" program in the Launcher column, and then open "mouse and touchpad" to see and/or adjust your settings?

---

### Post by andrew_hite on 2015-05-14
The system, per request, is a quad core amd 3.6 ghz, 8 gigs ram, nvida gt 560, and a logitech wireless mouse. At first i thought it was maybe a driver issue cause of the mouse, but forum searches show that the mouse is supported. Then i figure that its related to what i try to run, due to performance being really good when running various programs and in different numbers, then other days being totally annoying with inability to click anything outside a window or two. I understand programs hang after being opened/closed sometimes but majority of the time, when i am dealing with the middle of those two extremes, i have to click on the system icon, in upper right hand corner of the system bar, to get the ability to click anything outside of the window i was just in. The only way i can see this being hardware related is if i am missing drivers somewhere, and as far as i know that is supposed to be handled by the apt manager. It is downloading updates every day so it is apparently doing what it is designed to. Yesterday functions were much better, aside for linux ts3 being a pain and not installing, but i got a workaround for that. I seriously doubt i am running out of memory since everything starts very fast, but i am still new to this system so i could be wrong on that.

---

### Post by Vladlenin5000 on 2015-05-14
You have a nvidia GT560. What driver are you using? The default opensource *nouveau* or some proprietary nvidia driver installed *a posteriori*?
One would assume the latter considering the gaming perspective but please confirm. It might be a drivers issue after all but not the one you thought...

---

### Post by andrew_hite on 2015-05-16
it is most likely the open source one since i am still trying to find my way in the ubuntu system.

---

### Post by Vladlenin5000 on 2015-05-16
> **andrew_hite said:**
> it is most likely the open source one since i am still trying to find my way in the ubuntu system.

It is for sure if you hadn't installed the proprietary driver and perhaps that's the one you should try. 
Assuming you're running standard Ubuntu:

System Settings > Software & Updates

Find the rightmost tab, Additional Drivers, allow it to check the system (wait a few moments) and it should offer additional drivers and inform you about your current driver, *nouveau*. You're looking for ***nvidia*** but *before you commit* read this:

Nvidia recommends version 346 for your card.
Ubuntu 15.04 offers up to 346;
Ubuntu 14.04 offers up to 331 and this may not be the best for your system (it may work just as fine as 346 though). In order to install a newer version you'll have to add an unofficial software repository (PPA) e proceed carefully.

Post back any question/doubt about this procedure before trying, if you aren't familiar with it.

---

### Post by Vladlenin5000 on 2015-05-16
Below is a screenshot (warning: Portuguese) for the aforementioned additional drivers dialogue. This is a different system with AMD Graphics therefore it offers AMD graphics drivers; the AMD microcode firmware, however,  may be offered in yours like in the example (Ubuntu 15.04 only), along with the nvidia drivers. Go ahead and install it too, it shouldn't hurt. 

[ATTACH=CONFIG]262019[/ATTACH]

---

### Post by andrew_hite on 2015-05-16
well it turns out i had the wrong video card info, its the 640 instead. trying one of the proprietary drivers and we shall see what happens.

---

