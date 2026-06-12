---
title: "A few more questions"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Rixii on 2008-06-12
Alright, I have a few more questions about Ubuntu that I need some help with. For reference, I'm running 7.10 Gutsy Gibbon

1) How do I kill a process that's frozen? I've used the system monitor to kill a program that froze on me, but it does not disappear from the taskbar or screen, even though it disappears from the list of running processes. Logging out and back in, then trying to restart the program, gives me an error saying it's still running. The only way I can restart it, is to restart the computer completely. The program in question is Second Life, so I'm not sure if it's the program's fault? I believe it's still in beta for Linux..

2) Occasionally, when I restart, the mouse and keyboard will stop working a few seconds after Ubuntu has loaded. The applications and desktop appear to be working fine, but I can not make any type of input. All I can do is do a hard restart of the computer. It doesn't happen often, but when it does, it usually happens multiple times until I can get a proper boot and use the computer. Any ideas what could be causing it?

3) My SB Live! sound card is still only giving me stereo and not 5.1 sound. Here's my latest post from my last thread:
> **Rixii said:**
> Using the GNOME ALSA Mixer, all the bars are set high enough where I should get sound. In Totem, I set it to 5.1 sound but I still don't get any sound from my back speakers.

That webpage you link does say my card is supported, but it says I must turn on the sound support soundcore module and then gives me a command to see if it is already. When I enter "modinfo soundcore" this is what I get:
```
filename:       /lib/modules/2.6.22-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.22-14-generic SMP mod_unload 

```
Can someone tell me what that means?

Thanks for any help.

---

### Post by gr4nf on 2008-06-12
to kill a process, use:
```

killall processname

```
the process name is very touchy, and you may not know it at first. use:
```

ps ax

```
to list all running processes.

---

### Post by Raistlin82 on 2008-06-12
Hi there,  if you right click on either panel and click on + Add to panel  there is a Force Quite that you can place on the panel to use at any time.  Not sure if thats what your looking for, I'd like something similar to the windows task manager but not found anything yet

---

### Post by sam_delta on 2008-06-12
to kill programs, you can also click on ALT+F12 and type ```
xkill
```, your mouse pointer will become a cross, and just click on the frozed window, itll disapear //bummm//

sam

---

### Post by Rixii on 2008-06-12
> **gr4nf said:**
> to kill a process, use:
```

killall processname

```
the process name is very touchy, and you may not know it at first. use:
```

ps ax

```
to list all running processes.

The next time a program freezes I will try this.

@ sam_delta: Is ALT + F12 supposed to be a shortcut for the terminal? Nothing happens when I attempt that, but opening a terminal and typing it does tell me I can kill a process by clicking it. It doesn't seem to work when I do though.

---

### Post by sam_delta on 2008-06-12
MY BAD, i miss typed, its ALT-F2 not F12  its F-two ,, a command prompt should appear, in that command prompt, you type the command, xkill then click on run, and your mouse pointer will become a 'killing cross' that means, that the next thing you click on, will be killed, for example, firefox freezes, i just type ALT-F2, then type 'xkill' then run, then click on firefox window, and itll be force quitted.

sam

---

