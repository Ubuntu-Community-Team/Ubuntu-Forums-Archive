---
title: "What is the difference between a DE, a WM, and a shell?"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by cshin9 on 2012-05-23
For example, GNOME, KDE, Xfce, MATE, and LXDE are desktop environments, *boxes are window managers, and Unity, GNOME Shell, Cinnamon, and KDE Plasma are shells according to Wikipedia. What does this mean?

---

### Post by MadmanRB on 2012-05-23
Well in the most simple terms a desktop environment is more of a full featured system with many tweaks and tools for it much like OSX and Windows.
A window manager and shell are more of a stripped down version.
both a shell and a window manager can be used as full desktops though, iceWM for example provides a very windows like GUI but is far less complex then say KDE which is windows like itself.
Going into this matter farther will just confuse you, in the end if something is working for you what should it matter?

---

### Post by Peripheral Visionary on 2012-05-23
Clicky [here]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893") for the best "layman's language" explanation of it I've ever read.

---

### Post by cshin9 on 2012-05-23
But these explanations don't explain what a shell is. What's the difference between GNOME and GNOME Shell? Is Cinnamon (a shell) not a complete desktop environment?

---

### Post by fantab on 2012-05-24
> **cshin9 said:**
> But these explanations don't explain what a shell is. What's the difference between GNOME and GNOME Shell? Is Cinnamon (a shell) not a complete desktop environment?

Let's just say Gnome-Shell is name of the new desktop interface which comes with Gnome 3 or gtk3 engine. The previous version of Gnome, Gnome2 or gtk2 used Gnome-Panels. 

Ubuntu's UNITY is just an interface based on Gnome3 developed by Ubuntu. Gnome-Shell is a default interface that comes with Gnome3. Cinnamon is also an interface that runs on top of Gnome3 developed by the LinuxMint team. For you to use Gnome-Shell or Unity or Cinnamon or etc,  you need Gnome3. 

So, in other words, Gnome-Shell, Unity or Cinnamon is like the body of a car while Gnome3 or Gtk3 is the engine under the hood. 

I hope I was simple enough.

---

### Post by cshin9 on 2012-05-28
> **fantab said:**
> Let's just say Gnome-Shell is name of the new desktop interface which comes with Gnome 3 or gtk3 engine. The previous version of Gnome, Gnome2 or gtk2 used Gnome-Panels. 

Ubuntu's UNITY is just an interface based on Gnome3 developed by Ubuntu. Gnome-Shell is a default interface that comes with Gnome3. Cinnamon is also an interface that runs on top of Gnome3 developed by the LinuxMint team. For you to use Gnome-Shell or Unity or Cinnamon or etc,  you need Gnome3. 

So, in other words, Gnome-Shell, Unity or Cinnamon is like the body of a car while Gnome3 or Gtk3 is the engine under the hood. 

I hope I was simple enough.
Thanks for the concise (and on-topic) explanation.

---

### Post by JKyleOKC on 2012-05-28
> **cshin9 said:**
> But these explanations don't explain what a shell is. What's the difference between GNOME and GNOME Shell? Is Cinnamon (a shell) not a complete desktop environment?
Strictly speaking, a "shell" is a command interpreter, like command.com or cmd.exe in Windows. The default shell in many Linux distributions these days is bash, but a number of others exist.

However, marketeers have pounced on the word and ignored its actual meaning. Not one of those you listed in your original post is really a shell; they are WMs, DEs, or something in between.

IMO, the major difference between a WM and a DE is the number and type of features included. For instance, IceWM is a very nice WM but it includes no provision at all for a desktop (or at least the version I used a few years ago did not). I had to install Rox-filer to have a file manager and desktop with it. A true DE integrates all such accessories into a unified desktop environment. A bare WM simply draws a window and usually provides its border and decorations but very little more.

---

### Post by zombifier25 on 2012-05-29
Actually, there are separations between WMs and the user interface (the "shell" in its misused meaning). GNOME Shell is a user interface for GNOME which uses Mutter at the window manager, Unity is another which uses Compiz,...

---

