---
title: "HOWTO : create a custom keyboard shortcut"
date: 2005-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by frodon on 2005-06-17
[B][COLOR="Red"]Disclaimer : I wrote a more up to date and complete guide on the topic, please refer to this one now :
[http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)[/COLOR][/B]

The goal of this HOWTO is to create a custom keyboard shortcut to run a software (like xmms, 3ddesk, ...) or what you want (xkill, transset 0.5, ...). In  the example I want to start xkill (graphical kill) using "Alt + a" shortcut.

1- Open GConf editor, go to apps -> metacity -> keybinding_commands, and now choose a command, for my example I choose command_1. Edit command_1 writing xkill in order to run xkill (or every command you want to launch).

2- In the same direcrtory go to global_keybindings. Edit command_1 (or the command you choose in part 1) with the wanted shortcut like that : <Alt>a .

that's all !

Enjoy  ;-)

---

### Post by kb_ganesh on 2005-09-19
is it possible to make a custom shortcut for starting synaptic?

i tried using just synaptic as the command but it complains that it must be run  as root..and if i put sudo synaptic, it doesnt ask for my password and thus doesnt open at all..any ideas anyone?

PS:am really sorry to have posted here..just read the read this..please do delete off this post..i will post it again in the right place..

---

### Post by lucifeer on 2005-09-19
[QUOTE=kb_ganesh]is it possible to make a custom shortcut for starting synaptic?

i tried using just synaptic as the command but it complains that it must be run  as root..and if i put sudo synaptic, it doesnt ask for my password and thus doesnt open at all..any ideas anyone?

PS:am really sorry to have posted here..just read the read this..please do delete off this post..i will post it again in the right place..[/QUOTE] Try pointing it to "gksudo /usr/sbin/synaptic"

---

### Post by gregsfdev on 2006-05-23
Does anyone know how to save/export the user defined shortcuts?  I have searched high and low for a way to do this.  I use many different ubuntu machines and would like to script the customisation of them by copying files.  I tried md5'ing everything in ~/ changing a shortcut and seeing what changed.  As far as I could tell it was only ~/.gconfd/saved_state that changed.  However, copying and overwriting this file on another machine did not work.  Any suggestions?

---

### Post by olejorgen on 2006-12-02
How do you use the windows buttons for hotkeys?

EDIT: Hm.. think I figured it out. Seems like it's a real mess though. Apparently this works different on every system :/

Anyway, using <super>x worked for me. <super_L> on the other hand did not

---

### Post by K6K on 2006-12-30
wondering if there would be a way to set up a keyboard shortcut to switch users quickly...

---

### Post by bladefallcon on 2007-01-20
> **frodon said:**
> The goal of this HOWTO is to create a custom keyboard shortcut to run a software (like xmms, 3ddesk, ...) or what you want (xkill, transset 0.5, ...). In  the example I want to start xkill (graphical kill) using "Alt + a" shortcut.

1- Open GConf editor, go to apps -> metacity -> keybinding_commands, and now choose a command, for my example I choose command_1. Edit command_1 writing xkill in order to run xkill (or every command you want to launch).

2- In the same direcrtory go to global_keybindings. Edit command_1 (or the command you choose in part 1) with the wanted shortcut like that : <Alt>a .

that's all !

Enjoy  ;-)



Ok..Could you, or someone else possibly state the above in a step by step form, for someone who is new? example: How do i open GConf editor. etc. There is no 'metacity' under appl..not that i see anyways..so some explanations for someone like me would be greatly appreciated.

---

### Post by maclenin on 2007-02-01
You're not alone - I don't see "metacity" under apps in gconf, either.... Do I need to ugrade my gconf?

---

### Post by drr422 on 2007-02-18
With regard to backing up the gconf, i did the following to backup gconf and all of the settings:

[http://gentoo-wiki.com/HOWTO_Gnome_Desktop_Admin_Guide](http://gentoo-wiki.com/HOWTO_Gnome_Desktop_Admin_Guide)

To dump your personal panel settings run gconftool-2.... in the command line:

# Gnome 2.10+
gconftool-2
--dump /apps/panel > my-panel-setup.entries

To Load your settings:

gconftool-2 --direct
--config-source xml:readwrite:/etc/gconf/gconf.xml.defaults
--load my-panel-setup.entries

And thats it, it will load it as the default settings, but i'm sure you can find something on the link provided, since that is where i got it from. 

In order to view the gconf-editor, you need to right click on Applications, and select Edit Menus.  From there,  go down to System Tools, and press the little box for Configuration Editor, and then exit.  Now it should be in Applications -> System Tools -> Configuration Editor.  

I hope this helps,
Dustin

---

### Post by siva214215 on 2007-03-12
Got it after long search.  Very helpful.  Simply Great - Thank you very much.

=D>:smile::KS :-)

---

### Post by drr422 on 2007-03-12
I'm glad that you got it working, it helped me out alot as well when I found out about it.

---

### Post by WeKnowBetter on 2007-04-11
Could someone please EXPLAIN this procedure, while making no assumptions on my behalf with regards to skill. Most things in ubuntu seem somewhat intuitive, but this is black on black to me. Impossible to decipher. A real step-by-step procedure would make a lot more sense. I'm running gnome on 6.10. I want to make a shortcut for 3ddesk, so I can be all fancy and graphical. 

Explain, and you have my neverending gratitude.*

Cheers. 

*Offer only while supplies of neverending gratitude lasts.



EDIT: I'm a total fuckwad. Sorry. Found it. To other monkeys: Run gconf-editor in terminal or command line. From there onwards, it's easy.

---

### Post by gtr225 on 2007-04-15
Thanks for the HOWTO!

---

### Post by juillarr on 2007-04-28
I have an application that makes use of the function keys. My problem is none of the functions keys work now that I have upgraded to Feisty.  I may have actually 2 problems.

1) I am running Beryl, but with almost all hot keys turned off.  Beryl is suppose to use th F8 and F9 keys (I have left these in place to see if the keys are every pressed but they do not function either.

2) When I running in secure mode (not X running), the "showkey" command never indicates that I have hit a function key, though it does indicate that the other keys are being pressed.

Running a dual core AMD processor with an old PS2 keyboard...keyboard driver problem?

Any help would be appreciated!

---

### Post by frodon on 2007-04-28
> **juillarr said:**
> 1) I am running Beryl, but with almost all hot keys turned off.  Beryl is suppose to use th F8 and F9 keys (I have left these in place to see if the keys are every pressed but they do not function either.

This method is based on metacity so if you use another window manager (like beryl or compiz for example) it can't work.
Search in your beryl settings you may have the same feature. somewhere.

---

### Post by goodtimetribe on 2007-04-29
> **frodon said:**
> The goal of this HOWTO is to create a custom keyboard shortcut to run a software (like xmms, 3ddesk, ...) or what you want (xkill, transset 0.5, ...). 
Enjoy  ;-)

binary love! it worked perfectly. I'm uncertain what everyone else is nagging and complaining about. I'll be linking this on my blog soon. very satisfied. \\:D/

---

### Post by d1663m on 2007-07-27
Very nice. I've been looking for a way to emulate the windows style screen locking. Except I use xscreensaver directly rather than ubuntu's "kindasorta" xscreensaver. <Super>L running a custom script in command slot 1. Works like a charm. :)

---

### Post by Cuppa-Chino on 2007-09-18
how do I assign a multimedia key to the shortcut, my laptop has multimedia key that I want to use to start a shell script (NOT one of the things in keyboard shortcuts) 

if I use the key in keyboard shortcuts its called **0xcd**, its keycode is **205**

doh should have searched more

[http://ubuntuforums.org/showthread.php?t=27039]("http://ubuntuforums.org/showthread.php?t=27039")

---

### Post by frankabel on 2007-10-30
Hi all?

Can any body update this HOWTO do gusty users (like me;) ) can use it. I really haven't tested, but don't must work due to gusty use compiz 

Thanks in advance.

Salute
Frank Abel

---

### Post by frodon on 2007-10-30
it works if you use metacity, but compiz should have the same functionalities, otherwise there's still xbindkeys.

---

### Post by frankabel on 2007-10-30
OK, thanks very much, possibly  I decide uses xbindkeys at the end, it's independent of the window manager.

But...can you update this howto using the information in this post [http://forum.compiz-fusion.org/showthread.php?t=2306](http://forum.compiz-fusion.org/showthread.php?t=2306) so another Gusty user can configure it without install any packages?

Thanks again

Salute
Frank Abel

---

### Post by WarMonkey on 2007-12-21
I followed this post exactly, my system is up to date and I am running Gusty; but it didn't work! Does this work with gusty?

---

### Post by frodon on 2007-12-21
Are you using compiz ?

---

