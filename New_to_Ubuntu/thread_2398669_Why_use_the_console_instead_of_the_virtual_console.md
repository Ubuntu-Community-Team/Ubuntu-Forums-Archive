---
title: "Why use the console instead of the virtual consoles"
date: 2018-08-15
forum: New to Ubuntu
---

### Post by ubantunovice2 on 2018-08-15
Why do we use the console for command line when the virtual consoles (Ctrl-alt-F2-6) exist right there? 

What are the several virtual consoles used for?

---

### Post by #&amp;thj^% on 2018-08-15
Wow this question could run rampant, and I'm no guru but I'll try to explain from my views.

I believe it stems from the desire to have and switch between multiple foreground applications/logins running at the same time. Since unix and linux were always designed to be a multi-user and multi-tasking environment from the beginning, before GUI or networking was invented, this was one method used and it is kept because it can be handy sometimes.

Edit:
Short answer: no difference.

A bit more: number 1 is the 1st one and some distro's default to sending system messages to just that one.

Well OK there is a little difference, typically these days the higher numbers are for GUI, and lower numbers for text based interface. Though many distro's use 7-12 for GUIs and 1-6 for text interfaces, not all are like this, some have 1-4 and 5-8 for text/gui and do not assume you have keys F9-F12 as some old keyboards didn't.
Clear as mud right? :)

---

### Post by ubantunovice2 on 2018-08-15
Thank you. That is very helpful. 
But, it seems that when installed on a standard non-server enduser desktop computer, having all these additional unused virtual terminals is just redundant and a wasted of resources. No?

---

### Post by #&amp;thj^% on 2018-08-15
As your time progresses with Linux you will find they are not wasted resources, in-fact they can come in handy in particular situations.
I can see from a newer user's standpoint that might be logical to think, but.....

---

### Post by Holger_Gehrke on 2018-08-15
There is very little waste there. In terms of code in the Kernel (where the virtual consoles are implemented), having one console or a tunable fixed number of them is just the code for switching and a slightly higher level of abstraction and indirection. I'd guestimate the difference to be less than 10kb. In terms of data per VC I'd think the display and the backscroll buffer are the biggest chunk. But since it's just text it's probably no more than 32k or so per VT. The stuff for the login prompt and checking username and password has wandered into systemd, so it's only in memory once, although there might be a few k of data per VC there, too. It doesn't take any CPU cycles, because that code basically tells the Kernel 'Wake me if something happens on one of the consoles' and goes to sleep.

In return for this investment of less than half a megabyte of ram and a few microseconds more of boot-time you get several VCs which can be useful in an emergency. So why have multiple VCs ? Scenario: something has gone wrong with the GUI; you could just switch to one VC and order a reboot bur that would destroy whatever work you haven't saved yet; so you're going to try and kill just the process which has gone wrong. You'll probably want a shell, a manual reader or two, possibly an info-reader and perhaps a text-based web-browser. You could try working with ^Z and fg-commands, but using multiple VCs is a lot simpler.

Holger

---

### Post by SeijiSensei on 2018-08-15
Being able to tail a log in one window while working in another has been helpful to me.

---

### Post by DuckHook on 2018-08-15
Virtual consoles waste almost no resources. So long as they are not active, they support no shell, and therefore use almost no memory or CPU cycles. By far the biggest resource hog in modern desktop computing is the display server, display/window manager and desktop environment that collectively constitute the GUI experience. That's also where the biggest attack surface is for crackers and other assorted lowlife.

To see the magnitude of the difference, my file server running a pure CLI interface uses 60 MB of main memory. Most of that is the kernel and associated necessary modules. Let's guesstimate something like 58 MB for the kernel. The virtual console, including the bash shell that is running, uses next to nothing. In contrast, the GUI session of the leanest distro I have, a Lubuntu running in a VM, uses 260 MB. Subtracting the kernel and associated modules for both, we have a ratio of 202 MB to 2 MB, or proportionately, roughly 100 to 1. In other words, you would have to open up 100 CLI sessions, each running a full bash shell, to equal just the leanest GUI desktop with no apps running. So, the "wasted" resources in an inactive virtual console amount to mere vapours and are not even a consideration, especially in light of the extra functionality that they bring.

---

### Post by Impavidus on 2018-08-16
The terminal window gives you a CLI inside the GUI. This means it can easily use the clipboard, start GUI applications and you can run as many terminals as you like simultaneously. You can have multiple terminals side-by-side to to see them all at the same time and you can run programs that use both CLI and GUI. The VCs exist outside the GUI, which means they work when the GUI is broken or not installed. So there are terminal windows for normal desktop/laptop use and VCs for server and emergency use. And having more than one is nice.

---

