---
title: "Question about dual monitors in 14.04"
date: 2014-09-05
forum: New to Ubuntu
---

### Post by riverguy99 on 2014-09-05
I've been using 12.04 with dual monitors and it works great.  What I needed to do to get it to work was to disable the "3D" from the login box.  Now I've "upgraded" to a clean install of 14.04 and when I try to run the same two monitors I get a message that "3D cannot run with that large of a cumulative size of display," or to that effect.  Same message I got with 12.04.  So my question is this:  Is there a way to disable the 3D in 14.04?  I'm reading about lots of issues and ultra-complicated suggestions to be able to make this work in 14.04, and if that's what it will take, I guess I'll just go back to 12.04.  It worked.  

Thank you for any help on this.  I just want to know if it is possible to disable the 3D to make the dual monitors work.

---

### Post by cwmoser on 2014-09-05
Not sure what you mean by 3D.
I have dual monitors in 14.04.
Mine are nVidia.  I looked for 3D in the nVidia configuration but nothing there.

---

### Post by riverguy99 on 2014-09-05
My two monitors are the one in my docked Dell D620 laptop and an HP 2207 22" monitor.  They both worked just fine in 12.04.  The did not at first, but then some kind soul on this forum said that I should sign out, then when the box comes up to sign in, click on the little icon in the corner and deselect "3D."  I did, and after that, everything worked fine.

When I tried to configure the two monitors in 14.04, I got a message that the 3D could not support the combined size of my two displays. That's what happened in 12.04, also, except that in 12.04 there was that nifty trick to disable the "3D."  I have no idea what that is either!

You said your monitors are nVidia.  Is that the name of the driver?  This is a mystery to me . . .

Thank you for your assistance!

---

### Post by grahammechanical on 2014-09-05
You are talking about using Unity 2D instead of Unity 3D. Unity 2D is discontinued. It is only available in 12.04. Unity 2D uses Metacity as the compositor. Unity 3D uses Compiz as the window compositor. 

Unity 2D was used as a fall back for video adapters that could not do hardware acceleration and so could not run Unity 3D. In 14.04 an open source video driver called llvmpipe is used to provide this fall back. And so, it was decided to no longer provide Unity 2D.

EDIT: from the 14.04 release notes

>  [COLOR=#333333][FONT=Ubuntu Beta]Some laptops (particularly netbook class) with older graphics can experience poor graphical performance when starting with a high resolution external monitor attached. The reason for this is that some graphics cards (like the Intel 945GSE) cannot support accelerated 3D graphics when the combined width of both screens exceeds a certain threshold (typically 2048 pixels). See the bug for appropriate workarounds.
[/FONT][/COLOR]

Look under Kernel

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

See the bug report

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1292467](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1292467)

This seems to be the work around suggested

> [COLOR=#333333][FONT=monospace]WORKAROUND:
 * Plug in external monitor after login (1)
 * Boot with "video=LVDS-1:d" (2)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace](1) Booting with only the internal screen and then plugging in the external one after login seems to handle this better (although I probably need to remove any previous config to get into a kind of vanilla state again). Also it seems to be ok when I had the dual monitor boot and lightdm coming up side-by-side, when unplugging the external monitor before logging in.

[/FONT][/COLOR][COLOR=#333333][FONT=monospace](2) This will completely disable the internal screen for that boot. It cannot be enabled through the settings dialogue.[/FONT][/COLOR]

Regards.

---

### Post by riverguy99 on 2014-09-05
Well, that explains the problem, but now what's the solution?  I've read all sorts of really complicated "fixes" to this thing, but 14.04 is an "upgrade."  There has to be a way to make this work without delving into tins of terminal work?  Yes?  Or should I just re-install 12.04?  I just want it to work . . .

---

