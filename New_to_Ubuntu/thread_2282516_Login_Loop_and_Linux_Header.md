---
title: "Login Loop and Linux Header"
date: 2015-06-14
forum: New to Ubuntu
---

### Post by cstavrou on 2015-06-14
Hi.

I have been having similar problems to other users that enter a login loop, but only if I try to log in normally. I am using a Ubuntu 14.04 LTS 32 bit on Intel Core 2 Quad CPU Q6600 @ 2.40GHz × 4 and GeForce 8800 GT/PCIe/SSE2. I am using NVIDIA drivers (not Nouveau). Last time I shut down the computer, I shut down with some applications (possibly the terminal as well) still open, if that's relevant.

_**Log-in loop:**_ 

When I allow Ubuntu to load normally I get to the normal log-in screen. When I enter my password, the screen briefly flashes to black and then back to the normal log-in screen. Entering a wrong password works as predicted (i.e. I know that the password I am using is correct).

I tried using solutions suggested in similar threads (moved .Xauthority, moved .ICEauthority, re-installed ubuntu.desktop, removed lightdm, tried gdm, re-installed lightdm, checked .xsessions-errors...). A lot of answers in similar threads seem to point to a graphics problem, but I think that, at least in my case, it is a permissions issue. 
**_Note:_** When pressing [Ctrl]+[Alt]+[F1] to go to tty, I log-in normally (which is how I could try all the suggestions listed), but, after about 5' of use, something happens that brings up a cursor (an "X" in outline) and the tty goes blank (but letters do appear after I type something again).
**_Note:_** The log-in screen only appears on 1 of my 2 monitors. Normally the log-in screen is spread over both of my monitors.

[B][U]"Complication":
[/U][/B]After trying a multitude of suggested solutions, none of which worked, I tried restarting and going to "Ubuntu Advanced" in the initial grub screen. Choosing the previous Linux header (Linux 3.16.0-38-generic instead of Linux 3.16.0-40-generic) loads up normally (i.e. I can log-in and use Ubuntu normally). 

Any suggestions as to what is causing the problem and what I can do to fix it (using "Ubuntu Advanced" every time at the grub screen is not a solution) would be appreciated.

Thanks.

---

### Post by tgalati4 on 2015-06-14
If you performed any updates to the kernel (going to *-40 from *-38 for instance), then that may break the "tainted" kernel.  Your kernel is "tainted" because you have a proprietary (nvidia in this case), binary blob attached to your kernel.  Breakage is expected and normal.  You can try installing nv while using the older kernel (*-38), then reboot into *-40 and see if that works.  Then try loading the proprietary nvidia driver once again.  One would normally delay kernel updates to reduce the Agony Units involved with a "tainted" kernel.

There may be a better way to do this.  I don't know it.

---

### Post by cstavrou on 2015-06-14
Hi tgalati4. 

Thanks for your reply. How does one "delay kernel updates"? Do I just uncheck them every time I do an update, or is there a specific prrocedure? I will try your nvidia - nv suggestion. Does that mean you don't think it has to do with permissions associated with my account?

Kind regards.

---

### Post by tgalati4 on 2015-06-15
Linux Mint automatically labels kernel and xorg updates as "Level 4 and Level 5" updates and won't automatically perform them without going into preferences and changing the update behavior.  Some feel this is a security risk because you are not updating the kernel as soon as the updates come out.  But, the reason is that kernel and xorg updates are responsible for perhaps 80% of system breakage and regression--as you have experienced.  Nothing is more frustrating than to have a working system stop working because of an update.

If you have a tainted kernel, then you can expect more breakage than normal with kernel updates.  So delaying those updates is simply a matter of unchecking them during the update dialog.  Then set aside some time (once every 6 months or once a year) and perform the xorg and kernel updates and make time to research (have another computer at the ready) and fix any breakage so that you don't get surprised that your machine is broken after such updates.

---

