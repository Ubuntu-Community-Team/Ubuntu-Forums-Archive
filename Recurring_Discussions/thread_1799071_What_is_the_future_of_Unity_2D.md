---
title: "What is the future of Unity 2D?"
date: 2011-07-07
forum: Recurring Discussions
---

### Post by deserthowler on 2011-07-07
I'm using Unity 2D and more or less don't dislike it.  I realize there are several changes to be made; or hope there several changes to be made to improve the customization and stability.

With the new direction with Gnome, will Unity 2D retain the Metacity window manager or will it move to something else?

Earl

---

### Post by An Sanct on 2011-07-07
In Oneiric Ocelot (11.10) there will be no more 2D, just Unity ... I'll find the post and give you a link, so you can read for yourself...

edit: link to the promissed [statement]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/739812/comments/5").

---

### Post by nomko on 2011-07-07
> What is the future of Unity 2D?
 
Hopefully down the drain! Cause i don't want my desktop to look like some overvalued netbook.

---

### Post by An Sanct on 2011-07-07
+1

I would like to upgrade to Natty and so follow with the latest Ubuntu, but refuse to do so until I find some way to tear Unity out (100%) and replace it with something, that does not give me headaches.

I also dislike the "same look on any machine" way ... If it is a desktop, its _not_ a netbook...

---

### Post by coffeecat on 2011-07-07
> **An Sanct said:**
> In Oneiric Ocelot (11.10) there will be no more 2D, just Unity ... I'll find the post and give you a link, so you can read for yourself...

edit: link to the promissed [statement]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/739812/comments/5").


You have misunderstood. That link says that there will be no classic desktop fallback in Oneiric, not that there will be no Unity 2d. Classic fallback is gnome 2 panel. Oneiric is based on gnome 3 which is why there cannot be a classic fallback. However...

Unity 2d **will** be available in Oneiric.

**And**... In Oneiric you will be able to install the package gnome-session-fallback, which will give you the gnome 3 version of a desktop that will be very similar to classic gnome. Gnome session fallback is the fallback mode for gnome 3 shell.

So... In Oneiric you will get Unity 3d (if your hardware supports it) and Unity 2d as default. If you want gnome 3 shell and/or something that looks and behaves very much like classic gnome, both will be just a few mouse-clicks away.

---

### Post by An Sanct on 2011-07-07
Thanks for the clarification, coffeecat.

But still, if I take a look at gnome3.org and their introduction videos ... I don't want *that* messing up my desktop ... :(

---

### Post by coffeecat on 2011-07-07
> **An Sanct said:**
> 
But still, if I take a look at gnome3.org and their introduction videos ... I don't want *that* messing up my desktop ... :(

:sigh: Read my post again. The fallback mode for gnome3 shell will be very much like classic gnome. It is easily installed in Oneiric.

---

### Post by Dave_L on 2011-07-07
> **coffeecat said:**
> So... In Oneiric you will get Unity 3d (if your hardware supports it) and Unity 2d as default. If you want gnome 3 shell and/or something that looks and behaves very much like classic gnome, both will be just a few mouse-clicks away.

Will that also apply to the Live CD?  With the 11.04 Live CD, you're auto-logged-in to Unity (if your hardware supports it) and there's no way of logging out to switch to the classic desktop.

---

### Post by coffeecat on 2011-07-07
> **Dave_L said:**
> Will that also apply to the Live CD?  With the 11.04 Live CD, you're auto-logged-in to Unity (if your hardware supports it) and there's no way of logging out to switch to the classic desktop.

I believe not. At the moment - we're only at about the alpha2 stage - there is just Unity 3d and Unity 2d on the live CD. Which makes sense since Canonical are focussing their development efforts on the Unity desktop, so I guess that Oneiric will only offer Unity 3d and 2d out of the box. You will, of course, be able to install the gnome-session-fallback package for a classic gnome near-lookalike once you've done an install to hard drive, and it looks as though this package is being themed for Ubuntu rather than with default upstream gnome3 theme. I had a look at it a few days ago. It's still incomplete and buggy atm, but we are only at the alpha stage yet so I am confident it will be working just fine when Oneiric is released.

I haven't looked at gnome3 shell in Oneiric yet so I don't know whether that will have Ubuntu theming. I very much hope so. I do not like the default upstream theme at all, and that blue stripy wallpaper gives me the heebie-jeebies. :wink:

**EDIT**: just noticed this bit:

> **Dave_L said:**
> you're auto-logged-in to Unity (if your hardware supports it) and there's no way of logging out to switch to the classic desktop.

Oh yes there is! :) Click the shutdown button at top-right in the 11.04 Unity desktop (in the live session) and choose Log Out. At the log in screen, choose "ubuntu" as username. Then choose classic at the bottom of the screen. Then log in with a blank password (leave the password field empty and press enter). Voilà! Classic desktop in 11.04 in a live session.

---

### Post by Dave_L on 2011-07-07
> **coffeecat said:**
> Oh yes there is! :) Click the shutdown button at top-right in the 11.04 Unity desktop (in the live session) and choose Log Out.

When I boot the 11.04 Live CD, **there is no Log Out choice** in that menu. I assumed that was because of the auto-login setup. That was the point of my question. 

Is your experience different? Is the Log Out function present when you boot from the 11.04 Live CD?

---

### Post by Dave_L on 2011-07-07
(duplicate post)

---

### Post by coffeecat on 2011-07-07
> **Dave_L said:**
> Is your experience different? Is the Log Out function present when you boot from the 11.04 Live CD?

I know I have logged out and in again in the live 11.04 session. Whether the option was in the menu or whether I used something more drastic such as Alt+SysReq+K I can't remember offhand.

I shall boot from the live CD and let you know. It may be a little while before I post back.

---

### Post by coffeecat on 2011-07-07
> **coffeecat said:**
> I shall boot from the live CD and let you know. It may be a little while before I post back.

@Dave_L, You are quite right, there is no log out option in the menu that drops down when you click on the shutdown button. There is a "switch from ubuntu" choice which takes you to the login screen, but when I try to log into classic as "ubuntu" I get taken back to Unity.

My apologies, but there is a way of doing this which is why I remembered logging out and into classic gnome in the live Natty desktop. Press Alt+PrtScr+k which kills the xserver and takes you to the login screen. This time you will be able to login as "ubuntu" with a blank password into the classic desktop. I've just done it from the live CD on my laptop. 

On some systems and/or keyboards you need to use AltGr to the right of the spacebar instead of Alt, and the PrtScr may be labelled SysReq.

In my view this is a design flaw. I do not want to use classic desktop myself - I like Unity - but I respect the preferences of those who do.

Good luck! :)

---

### Post by deserthowler on 2011-07-07
> **deserthowler said:**
> With the new direction with Gnome, will Unity 2D retain the Metacity window manager or will it move to something else? 

And what will the Window Manager be, Metacity?

Earl

---

### Post by FormatSeize on 2011-07-07
> **coffeecat said:**
> 
**And**... In Oneiric you will be able to install the package gnome-session-fallback, which will give you the gnome 3 version of a desktop that will be very similar to classic gnome. Gnome session fallback is the fallback mode for gnome 3 shell.

How is one supposed to install a fallback mode package if his/her hardware doesn't support gnome 3, and there is no fall back mode to fall back to?

---

### Post by coffeecat on 2011-07-07
> **FormatSeize said:**
> How is one supposed to install a fallback mode package if his/her hardware doesn't support gnome 3, and there is no fall back mode to fall back to?

Log in to Unity 2d, open package manager, install gnome-session-fallback package, log out, log into gnome fallback desktop. Is that so difficult?

The gnome-session-fallback package provides the fallback desktop for gnome 3 but can be installed independently of all the gnome shell stuff.

**EDIT**: Now that this thread has been moved to recurring discussions, let me be clear: The above refers to what you will be able to do in Oneiric/11.10

---

### Post by uRock on 2011-07-07
Move to "***Recurring Discussions***"

---

### Post by el_koraco on 2011-07-07
> **FormatSeize said:**
> How is one supposed to install a fallback mode package if his/her hardware doesn't support gnome 3, and there is no fall back mode to fall back to?

if you install Gnome Shell, and your hardware doesn't support it, it logs you into gnome-fallback mode on its own. It's kinda like Unity logs you into "classic" mode right now and will log you into Unity 2D in Oneiric.

---

### Post by deserthowler on 2011-07-07
I now see indications Unity 2D will probably use mutter as the WM.  This is apparently a new iteration of metacity WM ... which makes sense if Unity @d will be using the new gtk toolkit.

Earl

---

### Post by Dave_L on 2011-07-07
> **coffeecat said:**
> My apologies, but there is a way of doing this which is why I remembered logging out and into classic gnome in the live Natty desktop. Press Alt+PrtScr+k which kills the xserver and takes you to the login screen. This time you will be able to login as "ubuntu" with a blank password into the classic desktop. I've just done it from the live CD on my laptop. 

On some systems and/or keyboards you need to use AltGr to the right of the spacebar instead of Alt, and the PrtScr may be labelled SysReq

Thanks. Alt+SysReq+k worked as you describe.

---

### Post by el_koraco on 2011-07-07
> **deserthowler said:**
> I now see indications Unity 2D will probably use mutter as the WM.  This is apparently a new iteration of metacity WM ... which makes sense if Unity @d will be using the new gtk toolkit.

Earl

Nope, Compiz with the QT toolkit.

---

### Post by deserthowler on 2011-07-07
> **el_koraco said:**
> Nope, Compiz with the QT toolkit.

How disillusioning.  ](*,)

---

