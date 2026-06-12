---
title: "systemctl isolate multi-user.target not working?"
date: 2016-07-13
forum: New to Ubuntu
---

### Post by bobk48 on 2016-07-13
In Ubuntu 16.04 I tried to switch from the default graphical.target to multi-user.target with **systemctl isolate multi-user.target**,
and  all I get is a black screen with some disk info in the upper-left corner. The target unit is there (state is static), as shown by **systemctl  list-unit-files**.
What's up? 
I tried the same command on suselinux  Leap 42.1, it worked perfectly. Also, on suselinux Leap 42.1, I used  **systemctl isolate graphical.target** to return to the full GUI runlevel,  no problem.

---

### Post by bobk48 on 2016-07-15
By the number of views versus replies to this thread, I conclude that this is a) not a very important issue to most Ubuntu 16.04 Cinnamon users, b) and following on a), no one knows the answer because they have not tried to do systemctl isolate multi-user.target. I have tested this on three different machines with the same results- system hangs. I have solicited answers to this question on Ask Ubuntu, Mint Forums, and Ubuntu Bug Reports, and have gotten the same zero(results). What is surprising to me is that such a fundamental part of systemd seems not to be working for changing to predefined targets or user-defined targets, and that it hasn't come up on the radar in the Ubuntu or Mint community. Or at least has not come up as a problem for the community.
Believe me, I have contrasted the operations I tried on Ubuntu and Mint to the other flagship Linux branch systems not to put down Ubuntu, but just to verify that the procedure works.

---

### Post by cariboo on 2016-07-15
> **bobk48 said:**
> By the number of views versus replies to this thread, I conclude that this is a) not a very important issue to most Ubuntu 16.04 Cinnamon users, b) and following on a), no one knows the answer because they have not tried to do systemctl isolate multi-user.target. I have tested this on three different machines with the same results- system hangs. I have solicited answers to this question on Ask Ubuntu, Mint Forums, and Ubuntu Bug Reports, and have gotten the same zero(results). What is surprising to me is that such a fundamental part of systemd seems not to be not working for changing to predefined targets or user-defined targets, and that is hasn't come up on the radar in the Ubuntu or Mint community. Or at least has not come up as a problem for the community.
Believe me, I have contrasted the operations I tried on Ubuntu and Mint to the other flagship Linux branch systems not to put down Ubuntu, but just to verify that the procedure works.

The Forums have been up and down for the last couple of days due to a forum breach, see [here]("https://insights.ubuntu.com/2016/07/15/notice-of-security-breach-on-ubuntu-forums/"), give people a couple of days to come back to the forum, bumping the thread every 12 hours or so.

---

### Post by bobk48 on 2016-07-15
Thanks, I will!

---

### Post by bobk48 on 2016-07-16
Still not working.

---

### Post by Bashing-om on 2016-07-16
bobk48; Hello;

Be aware I too am in the process of learning systemd. 
This much I am aware of that works for me:
to boot to terminal in ubuntu 16.04 from grub; the boot parameter:
```

systemd.unit=multi-user.target

```

And once logged into the system on TTY1 to start the GUI:
```

systemctl isolate graphical.target

```
That does much more than just start the GUI, it also stops everything that is not a dependency of graphical.target.
One will have to enable and activate all other desired services.

Here are the runlevels in sysVinit with their systemd counterparts:

    0 runlevel0.target, poweroff.target
    1, s, single runlevel1.target, rescue.target
    2, 4 runlevel2.target, runlevel4.target, multi-user.target
    3 runlevel3.target, multi-user.target
    5 runlevel5.target, graphical.target
    6 runlevel6.target, reboot.target
    emergency emergency.target

In my way of think'n .. If you do not allow PID1 to do it's thing .....
[INDENT][INDENT][INDENT]then you are responsible to bring the system up as you desire
[/INDENT][/INDENT][/INDENT]

---

### Post by bobk48 on 2016-07-17
Thanks, Bashing-om for the detailed, helpful, and friendly reply to my post!
My original intention was to change to multi-user.target ( and then back again to graphical.target) using systemctl isolate when the system was already operating in the graphical.target state.
1) So, if I interpret what you are saying correctly, I have to interrupt the normal boot of my Ubuntu 16.04 ( and Mint 18 by extension) to enter GRUB, set the parameter you show, then use this excellent workaround you illustrate to bypass using systemctl isolate multi-user.target. I will try doing what you suggest and give you a report.
2) The only workaround I've tried successfully is when Linux Mint 18 ( not Ubuntu 16.04) is a guest running in VirtualBox. 
When the system state is graphical.target, I use systemctl set-default multi-user.target, reboot, and I'm in the multi-user text mode only state. I can then execute systemctl set-default graphical.target, then reboot, and I'm back in the graphical state.
But this only works when Mint 18 is running as a guest in VirtualBox! I have not tried it with Ubuntu 16.04 running as a guest in VirtualBox.
3) Trying to do any of 2) on a real hardware machine yields ( unfortunately for me) an unusable system. Of course I suspect that if I can rescue the machine from GRUB, it wouldn't be unusable, but I don't have much experience with that.
It still surprises me that only you and I are concerned with this issue in the Ubuntu or Mint community. Why is that?

---

### Post by Bashing-om on 2016-07-17
bobk48; Well ..

Consider, that with systemd, we are steeping into uncharted territory for many many of us .
I have a long way to go yet to understand the system and all the changes from the upstart initiate system .
To add to the difficulty, I have no experience with virtual machines, and the relationship to the host system. All my experience in on bare metal installs, and I am not real quick to make the change to systemd. I am awaiting the funding to add an SSD and a new Nvidia card to my system. At that time I will reconfigure this system with 16.04 as my "working"  install. Presently, I do have 16.04 installed as a test bed install.

All this ^ just so you understand when I say .. " I do not  know " . But, I am more than willing to hold your hand until such time as we know.
We can await the advise of those who have managed to acquire the knowledge here to properly guide.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]we are all in this together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bobk48 on 2016-07-17
Bashing-om:
Much thanks, I'm messing with GRUB now on Mint 18 in VirtualBox.

---

### Post by bobk48 on 2016-07-17
With the most excellent help from Martin Pitt at Ubuntu.com, I was able to track the problem down to my video card. 
I enclose a partial quote of his analysis of my problem here-
"the command actually worked, but stopping lightdm and thus the graphics driver breaks the state of the graphics card. Does
changing VTs with Ctrl-Alt-F2 work? If not, please check if you can still log into the system with ssh (I suppose that works)"
So after systemctl isolate multi-user.target, I do the Ctrl-Alt-F2, and I can log in to the multi-user target.
I then do systemctl isolate graphical.target, and am back to the beautiful Cinnamon Desktop! Bravo Ubuntu!
I have not tested rescue or emergency targets yet.
I have done these operations both in Ubuntu running as a VirtualBox guest, and on a bare metal install on hardware.
I couldn't figure out to Ctrl-Alt-F2 in the Ubuntu guest, but for the bare metal install, Matin's fix works perfectly.

---

### Post by Bashing-om on 2016-07-17
bobk48; Outstanding ...

You do good work for all of us. I do make note !
Stepping up on that learning curve that is systemd.

As the query has been addressed;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And I will look forward to
[INDENT][INDENT][INDENT]our next adventure[/INDENT][/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2016-07-17
> **bobk48 said:**
> I couldn't figure out to Ctrl-Alt-F2 in the Ubuntu guest, 
In VirtualBox?  Host key + F2.

(That trick works for most Ctrl-Alt-<key> keystrokes to sent to the VM)

---

### Post by obi1ken88 on 2016-11-20
> **bobk48 said:**
> Does
changing VTs with Ctrl-Alt-F2 work? 


Hi,

Im also new to UNIX/Linux systems and Systemd logic , can you please what changing VTs is ? i'm using VMware Pro and i have the same issue.

Thanks in advance !
Cheers,

EDIT : i've just understood what changing Linux Terminal meant, the problem is when i want to get to graphic mode i get "PolicyKit daemon disconnected from the bus" which apparently is a bug : [https://bugzilla.redhat.com/show_bug.cgi?id=1205008](https://bugzilla.redhat.com/show_bug.cgi?id=1205008) , all this is driven me crazy , all i wanted is learn about the runlevels :D

---

