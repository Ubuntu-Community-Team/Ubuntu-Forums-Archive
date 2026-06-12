---
title: "Unity launcher fails to appear"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mmasroorali on 2011-10-07
This has happened a number of times after I started using 11.10 beta. After I log in, the launcher does not appear at left. Nothing happens when I move the mouse button to left side of screen or press the Super Key (Windows Key). 

I know that I am using a development version and I will have to put up with these things. Previously, a simple reboot (or log out when I could) solved the problem. But this time, I am stuck there how many times I log out or reboot. 

I have a desktop with some kind of menu at the top. Please see the attached image.  Ctrl-Alt-arrow keys work, allowing me to switch among workspaces. Also, Ctrl-Alt-T works, I can get a terminal and start the applications from there. Also, Super-w, Super-s work. 

Any suggestion will be appreciated.

---

### Post by LinuxFan999 on 2011-10-07
Are you using beta 1 or beta 2?

---

### Post by Gawains Green Knight on 2011-10-07
I had this in earlier beta's but its fine now....

---

### Post by mmasroorali on 2011-10-07
> **LinuxFan999 said:**
> Are you using beta 1 or beta 2?

Beta 2. The machine is fully upgraded.

---

### Post by mmasroorali on 2011-10-07
> **Gawains Green Knight said:**
> I had this in earlier beta's but its fine now....

Yes, same here for the first part. As indicated in my post, previously log out or reboot solved the problem. Now, nothing is solving it.

---

### Post by effenberg0x0 on 2011-10-07
Hey, try this:

Using this terminal I see in your screenshot (or you can also switch to a VT using Ctrl+Alt+F1 to F6)

```
DISPLAY=:0.0 /usr/bin/ccsm
```

Then switch back to the gui session (Ctrl+Alt+F7) and you'll see **Compiz Config Settings Manager**. 
Make sure the **Ubuntu Unity Plugin** is activated. Even if it apparently is, deactivate and then activate it again. 
ccsm might crash (it is very unstable sometimes). If so, launch it again (the "DISPLAY" command).

Again, using the terminal you have, now type:

```
sudo service lightdm restart

```

If you still get to a session with no launcher, try the following (at a VT, terminal, etc)

```
unity --reset
```

Let us know.

Regards,
Effenberg

---

### Post by mc4man on 2011-10-07
try opening ccsm again & checking if the unity plugin is enabled, if not then  do so.

---

### Post by madjr on 2011-10-07
there is another thread about this problem
[http://ubuntuforums.org/showthread.php?t=1855136](http://ubuntuforums.org/showthread.php?t=1855136)

and a link to a similar bug report:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/859908](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/859908)

---

### Post by mmasroorali on 2011-10-08
Opening ccsm and enabling Unity Plugin solved the problem. I had to blindly ignore some conflicts with other plugins.

---

### Post by BigSilly on 2011-10-08
I'm having this issue too. 64 bit desktop, Nvidia proprietary driver. However, with mine the launcher appears when pressing the super key. It only doesn't appear when mousing to the left. Then sometimes it just works. :confused:  Above fix isn't the problem for me as the Unity plugin is enabled in CCSM. Is there anything else to try?

---

### Post by mmasroorali on 2011-10-08
> **BigSilly said:**
> I'm having this issue too. 64 bit desktop, Nvidia proprietary driver. However, with mine the launcher appears when pressing the super key. It only doesn't appear when mousing to the left. :confused:  Above fix isn't the problem for me as the Unity plugin is enabled in CCSM. Is there anything else to try?

Did you try unity --reset as suggested in #6? This did not work for me though.

---

### Post by ubj on 2011-10-08
> **BigSilly said:**
> I'm having this issue too. 64 bit desktop, Nvidia proprietary driver. However, with mine the launcher appears when pressing the super key. It only doesn't appear when mousing to the left. Then sometimes it just works. :confused:  Above fix isn't the problem for me as the Unity plugin is enabled in CCSM. Is there anything else to try?

All you can do is wait untill this [bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/865913") is fixed, use super key or use Unity 2d.

---

### Post by BigSilly on 2011-10-08
> **ubj said:**
> All you can do is wait untill this [bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/865913") is fixed, use super key or use Unity 2d.

Ah right. Thanks for that. Hopefully this will be sorted soon enough then.

CCSM/Compiz crashed on me while trying to perform the fix in post #6 and this generated a bug report that I stupidly filed for the problem. I say stupidly because I linked the Unity bar issue and the Compiz problem in the same bug, though I did make reference to this in the text.

Oh well, I'm sure the devs will amend it if it's no use. Thanks again. :)

---

### Post by mc4man on 2011-10-08
> **BigSilly said:**
> I'm having this issue too. 64 bit desktop, Nvidia proprietary driver. However, with mine the launcher appears when pressing the super key. It only doesn't appear when mousing to the left. Then sometimes it just works. :confused:  Above fix isn't the problem for me as the Unity plugin is enabled in CCSM. Is there anything else to try?
Try opening ccsm, going to the unity plugin & disabling the Reveal Mode & then re-enabling it. screen shows edit box w/ left edge disabled, re-clicking to re-enable

---

### Post by BigSilly on 2011-10-08
> **mc4man said:**
> Try opening ccsm, going to the unity plugin & disabling the Reveal Mode & then re-enabling it. screen shows edit box w/ left edge disabled, re-clicking to re-enable

Didn't work sadly, but I find the bar just appears as it should anyway after an amount of time being logged in to the PC. :confused:  Not worried though, I'm sure it'll be fixed.

This aside, it's a mighty fine release so far for me. :)

---

### Post by mc4man on 2011-10-08
> **BigSilly said:**
> Didn't work sadly, but I find the bar just appears as it should anyway after an amount of time being logged in to the PC. :confused:  Not worried though, I'm sure it'll be fixed.

This aside, it's a mighty fine release so far for me. :)

If you where meaning the reveal doesn't work with mazimized windows then that seems to be a current bug.

It doesn't occur here, likely because I have the grid plugin disabled

---

### Post by DogMatix on 2011-10-08
> **BigSilly said:**
> I'm having this issue too. 64 bit desktop, Nvidia proprietary driver. However, with mine the launcher appears when pressing the super key. It only doesn't appear when mousing to the left. Then sometimes it just works. :confused:  Above fix isn't the problem for me as the Unity plugin is enabled in CCSM. Is there anything else to try?

I'm in exactly the same boat as you. I have tried to reset Compiz

```
gconftool-2 --recursive-unset /apps/compiz-1 
```

and then unity

```
unity --reset
```

but the problem still exists.

---

### Post by BigSilly on 2011-10-09
Either I've done something or the updates I've installed today have, but I've rebooted loads of times and the Unity bar is working perfectly. Not a single issue with it since yesterday.

Just me?

---

