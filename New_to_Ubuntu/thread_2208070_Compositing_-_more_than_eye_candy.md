---
title: "Compositing - more than eye candy?"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by David_Wright on 2014-02-26
I am a new convert to Linux and busy experimenting / tailoring etc.

I am running Lubuntu to allow for the aged/underpowered hardware that I am using and it runs very well indeed.

Sooooo: I started looking at docks, installed Docky and then discovered that (I think) it doesn't work fully/properly (dock won't hide or fade) without a composite package.  I've searched around and will try xcompmgr as the lightest variant and see how it works.

My question is (eventually): does compositing have any _real_ benefits other than eye candy?

---

### Post by David_Wright on 2014-02-26
In view of my disappointing view:reply ratio ;) I shall elaborate:

I understand that xcompmgr (or other composite manager) will make Docky work - ie fade and/or hide, which is in itself useful, as long as it doesn't bring my aged Pentium 4 to a grinding halt.

My question is more around other things - descriptions of composite managers seem to cover transparency, drop shadows etc - none of which seem *particularly* useful to me.  But do they achieve something else?  One inference is that as all windows/objects are "drawn" separately, one hanging is less likely to drag the whole system to a halt - is that correct?

---

### Post by Rob Sayer on 2014-03-01
> **David_Wright said:**
> In view of my disappointing view:reply ratio ...

I sympathise.  I've only had lubuntu installed on this here netbook for a couple of weeks but I've tried every other flavor except unity.  Which I wouldn't even consider on my netbook.  But from reading here and askubuntu I'd have to say the LXDE version has the poorest level of support of all the desktops.  But it's still miles ahead of linux mint ....

I've never tried docky or any other similar docks and don't intend to.  I was curious about docky because it seems to me it'd install all needed dependencies.  The docs/comments on the subject I could find were all getting old.  None past 2011, which I wouldn't consider a good sign.

As far as adding a compositing manager, I wouldn't do it in lubuntu.  There are reasons it's so fast.  One of them is that doesn't have eye candy.  

I turn that stuff off as much as possible but many seem to desperately want it.  I've seen a lot of forum entries by people running lxde or xfce on old/slow hardware and still wanting to look like a mac, not realizing that there's a reason that these desktops look so basic.  And they have lots of problems.

Adding compiz or another compositor kind of defeats the purpose of lxde.  You're going to lose a lot of speed.

Plus these newer desktops like unity and cinnamon (or mac) require your gpu to have 3D hardware acceleration just to run themselves.  Same thing if you install a compositor.  On old hardware that is not a good idea.

If you just want app launchers you can create a new auto hide panel with larger icons.

---

### Post by tgalati4 on 2014-03-01
Check your BIOS for video RAM setting.  You need a fair amount of video RAM to make compositing to work.  As far as usefulness, if your system can run it without problems, then it can provide some helpful hints--shadowing, redrawing windows as you move them (instead of just frames), and overall smoother apearance.  

If you post specifics, like what is your video card? Then we can provide some specific guidance.  Of course, if you use the terminal for 90% of your work, a compositor won't make a difference.  After all, the terminal is where it is at.

You just may be short of RAM.  How much RAM do you have?  How much can your system take?  Why isn't it maxed out?

---

### Post by Frogs Hair on 2014-03-01
There are situations where transparency could be helpful if motoring a group of open windows in which different process are running ,but we all have some hardware limitations and that is the first consideration. Composting can make long term computer use more pleasurable and I have seen threads here  where things like drop-shadows are  helpful to the vision impaired. As I wrote hardware is the first consideration and it is pointless to purchase computer with extensive graphics capabilities and not use them and it is also pointless to bring a  productive system  to the point of freezing in order to run advanced composting.

---

### Post by ibjsb4 on 2014-03-01
Composite managers can help squeeze more out of a machine.  Can't speak for lubuntu, but I run "metacity" which allows me (helps me) to run standard ubuntu on older machines that could not run standard ubuntu using the default "compiz" window manager.

[https://help.ubuntu.com/community/Metacity](https://help.ubuntu.com/community/Metacity)

[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

---

### Post by grahammechanical on 2014-03-01
As to your question, the answer is, O, Yes.

[http://en.wikipedia.org/wiki/Compositing_window_manager](http://en.wikipedia.org/wiki/Compositing_window_manager)

I would say that Lubuntu must have a Compositing/Window Manager otherwise it would not have a graphical user interface.

Regards.

---

### Post by lykwydchykyn on 2014-03-01
If you end up running a standalone compositing manager, "compton" is much better than xcompmgr.  Unfortunately it won't be in the regular ubuntu repos until 14.04, but you might be able to find it in a PPA (or compile it, if you're savvy to that).

---

### Post by David_Wright on 2014-03-04
Thanks for all the replies (and apologies for the slow response - I was momentarily distracted by my work, as a colleague used to say).

I've since tried it our - installed xcompmgr and set it to autorun etc.  In general, there doesn't appear to be a noticeable impact in terms of the responsiveness of the system, although occasionally there is a delay in launching programs.

[QUOTE="Rob Sayer"][COLOR=#000000][FONT=Calibri]As far as adding a compositing manager, I wouldn't do it in lubuntu. There are reasons it's so fast. One of them is that doesn't have eye candy. [/FONT][/COLOR][/QUOTE]
That sums up my hesitation - is it worth loading the system in order to add eye-candy.  As noted, it doesn't seem to add much burden, but all I'm really getting as a useful function is the auto-hide in Docky (the "pop-up" effect as you mouseover the icons has no real value)

In reply to various questions - the hardware I'm playing with is an old Dell - Pentium 4 3.0Ghz, no graphics card (using integrated Intel graphics, so flash video is a struggle), 1Gb ram.

I'll google Rob's suggestion of "[COLOR=#000000]new auto hide panel with larger icons" to see how to implement that as a possible replacement for what I want Docky to do . . . and continue to suck-it-and-see in terms of whether the cost outweighs the benefits.[/COLOR]

---

### Post by ajgreeny on 2014-03-04
I agree with Rob.  On my old laptop with lubuntu desktop (and xfce, I admit, which I prefer) I have a panel which autohides on the left of the screen a bit like the unity launcher in both DEs, and that works splendidly without causing any difficulties with slower performance.

It is dead easy to do on both DEs but using xfce you need compositing to make the panel background transparent; not so in lxde.  The new 14.04 lubuntu when it finally arrives in full release form in April, looks as if it's going to be a real winner to me!

---

### Post by David_Wright on 2014-03-04
Ok, so off I went and watched [http://www.youtube.com/watch?v=lAXHO4Ou5BQ](http://www.youtube.com/watch?v=lAXHO4Ou5BQ) which spelled it all out - looks like exactly what I was after, with less overhead.  Thanks.

I'm a newcomer to *buntu and feeling my way around - it's all educational, even if it's a bit two-steps-forward-one-step-back at times!

---

