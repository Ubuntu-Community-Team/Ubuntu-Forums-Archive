---
title: "selectively view multiple instances of same program in Unity"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by beew on 2011-11-26
Hi,

Is there a way to selectively expose specific instance/instances of a program which are currently minimized from the Unity launcher?

Example: I have 3 pdf documents opened but all minimized. If I click the Unity icon for evince all of them will pop up. In the Cairo dock each instance of the minimized document has its own icon and I can choose from the dock which one I want to open; in Win7 you can choose the instance from windows preview, is there anything similar that would allow me to selectively bring up the instance I want from Unity? 

I would like to hear solutions for both 11.04 and 11.10 if there is any difference.

Thanks.

---

### Post by Corporation on 2011-11-26
If you press alt-tab and hover over PDF Viewer for a few seconds, it will expose all instances of PDF Viewer.

---

### Post by beew on 2011-11-26
Hi,

I think alt-tab allows you to cycle through all the exposed instances, but I would like to know if there is a way for me to only selectively expose them instead of opening all of them and then cycle through them. In the Cairo dock, each instance of evince, say, has its own icon and you can simply choose the one you currently want to expose, the rest remain minimized. I would like to know if there is a way to open just the instance(s) that I want while the rest remain minized in Unity.

---

### Post by beew on 2011-11-26
I think the title is probably not very clear. What I want to know is whether there is a way to selectively unminimize several instances of the same running programs from the Unity dock. I don't mean unminizing all of them and then use a window switcher (alt+tab, super+tab etc) to pick one. If yes, how? If no, is this a bug?

---

### Post by pierreyy on 2011-11-26
hey in 11.10 you can use the alt+tab+~ to view a thumbnail of whatever youre doing... does thiss answer your question?

---

### Post by fabricator4 on 2011-11-26
> **beew said:**
> I think the title is probably not very clear. What I want to know is whether there is a way to selectively unminimize several instances of the same running programs from the Unity dock. I don't mean unminizing all of them and then use a window switcher (alt+tab, super+tab etc) to pick one. If yes, how? If no, is this a bug?

Yes, it's bug in as much as it's an error in logic and is not obvious, and there's no purely mouse way to do it.

If you use <super>w you can select a single instance to unminimize.  super-w however shows _all_ running applications not just those of a particular application, and if you want to unminimize more than one you have to repeat the operation for each instance that you want to bring to the foreground.

The work-around is to use workspaces to segregate types of operations and applications and not minimise windowed applications, but this is a clunky solution to the problem.

Chris

---

### Post by ExileAmongYou on 2011-11-26
> **beew said:**
> I think the title is probably not very clear. What I want to know is whether there is a way to selectively unminimize several instances of the same running programs from the Unity dock. I don't mean unminizing all of them and then use a window switcher (alt+tab, super+tab etc) to pick one. If yes, how? If no, is this a bug?

To answer your question as directly as possible: no, you cannot directly select individual windows of a program using the Unity launcher. This is not a "bug", in the sense that Unity has been deliberately designed this way, so your system is running as the designers intended.
Your best option is to use the new Alt+Tab switcher. You don't actually have to unminimise windows to switch to them, the switcher will still show minimised applications. Press Alt+Tab and tab across to the program you want, then while still holding Alt, press the "`/~" key (the key above Tab) to choose the individual instance of that program. If you already have a window open from that program, you can just press Alt+` directly to switch between instances.

---

### Post by fabricator4 on 2011-11-26
> **ExileAmongYou said:**
>  This is not a "bug", in the sense that Unity has been deliberately designed this way, so your system is running as the designers intended.

It might still be considered a bug inasmuch as there's no easy and intuitive mouse only method to select minimised applications.  The keyboard is the _only_ way to get this functionality.  This is not intuitive and is likely to confuse people - not just Gnome 2 diehards. I'm mostly concerned about new users having their first Ubuntu experiences, and those that need accessibility features to use a computer productively. 

To this end I searched for and could not find a bug report about this on launchpad, so I added one to see how it would fly:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/896709](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/896709)


If bug #1 is truly a bug (and I do believe it's an important one) then I also believe that bug #896709 is not only a bug but one that will have a direct affect on the solution of bug #1


Chris

---

### Post by ExileAmongYou on 2011-11-26
> **fabricator4 said:**
> It might still be considered a bug inasmuch as there's no easy and intuitive mouse only method to select minimised applications.

Oh, I don't necessarily disagree, I find the way windows are handled using the mouse to be fairly clunky. I was just clarifying that there was nothing going wrong with the OP's system, so it wasn't a bug in that sense. In the sense you're talking about, it definitely could be considered a bug.

---

### Post by fabricator4 on 2011-11-26
> **ExileAmongYou said:**
> Oh, I don't necessarily disagree, I find the way windows are handled using the mouse to be fairly clunky. I was just clarifying that there was nothing going wrong with the OP's system, so it wasn't a bug in that sense. In the sense you're talking about, it definitely could be considered a bug.

Understood, sorry about the knee-jerk reaction. No-one has yet added a 'me too' to the bug...  maybe I am expecting too much too soon.  

I honestly believe that Unity is the way forward but a lot of work needs to be done.  It's my hope that if the design team and the developers could be made aware of just how commonly this is perceived as a problem then it can fixed and we can all move on.  The alt-tab switching in conjunction with the '`' key above it goes some of the way, but a I mentioned in the bug report it's not the kind of thing a new user is going to know or understand.

Chris

---

### Post by beew on 2011-11-26
Thanks everyone for replying to this thread Alt+tap does work even for minimized instances so it is not necessary to open all the instances to pick one, but it is also true that it shows all instances of all running programs rather than the one that is of interest. <super> -w doesn't work on Natty if all windows are minimized (it only shows the unminimized ones). It seems to work in Oneiric but I need to try it again to confirm and right now I can't boot into it because my computer is busy running Natty.

I agree with fabricator4 that this can be a big problem for new users and  it is because of things like this (this is not the only example) that I am hesitant to recommend Unity to new users (even though I use it myself, I am no gnome2 diehard.:)) For new users I would install xfce or LXDE for the moment.

> If bug #1 is truly a bug (and I do believe it's an important one) then I  also believe that bug #896709 is not only a bug but one that will have a  direct affect on the solution of bug #1Can't say it better myself. 

I have added an "affect me too" to bug #896709.

I hope other people will do the same so I am not marking the thread as solved yet .

---

### Post by fabricator4 on 2011-11-26
> **beew said:**
> I have added an "affect me too" to bug #896709.

I hope other people will do the same so I am not marking the thread as solved yet .

In his recent "Ask Mark" interview Mark Shuttleworth stated that every Launchpad bug gets airtime on his desktop.  Because of this I'd suggest that people who care about this issue add a few measured and meaningful comments to the bug report as well.

[http://irclogs.ubuntu.com/2011/11/23/%23ubuntu-classroom.html](http://irclogs.ubuntu.com/2011/11/23/%23ubuntu-classroom.html)

Even if you personally are quite happy with Unity as it is but concede that the first impressions of new users could be improved please consider adding a meaningful comment.

Chris

---

### Post by beew on 2011-11-26
I have tested with 11.10 and the behaviour is a little different. Unlike in 11.04, Alt +tab doesn't show all the instances, but you have to do alt+tab then release tab (still holding alt) and then tab again (or use the key ` key above) will cycle through the instances. <super> + w exposes all instances of the running programs without unminimizing them if they are already minimized, you then can pick with the mouse. This works only in 11.10 but not in 11.04.

@fabricator4

Will try to add a comment to the bug on launchpad later. It is kind of difficult because your report is so well written that it practically covers all the grounds. :)

---

