---
title: "Gnu Grub 2.04 ignore countdown?"
date: 2022-02-10
forum: New to Ubuntu
---

### Post by ra-white on 2022-02-10
Problem: I want to skip/edit the 10 seconds countdown/timeout timer when starting my laptop.

When I start my Ubuntu 20.04.3 laptop I get a menu with 4 options:

*Ubuntu
  Advanced options for Ubuntu
  Windows Boot Manager (on /dev/nvme0n1p2)
  UEFI Firmware Settings


in [COLOR=#232629][FONT=ui-monospace]/etc/default/grub, [/FONT][/COLOR]I have edit the text in by removing the hashtag and set 
[FONT=var(--ff-mono)]# GRUB_HIDDEN_TIMEOUT=0 
[/FONT][FONT=var(--ff-mono)]# GRUB_HIDDEN_TIMEOUT_QUIET=true 
[/FONT][COLOR=#232629][FONT=ui-monospace]
[/FONT][/COLOR]However it does not have any effect on the countdown timer.

Please help me out.
Thanks!

---

### Post by Bashing-om on 2022-02-10
ra-white; Hello -

For your consideration: my working /etc/default/grub file
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=2
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_DISTRIBUTOR="Xubuntu-20.04-sda1"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_GFXPAYLOAD_LINUX=text
GRUB_CMDLINE_LINUX="priority=low"

```

Remember to execute:
```

sudo update-grub

```
If you change this file to propagate the changes.

Where rather than a back screen during boot  I see the boot messages :)

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by KBar on 2022-02-10
Pretty much what Bashing-om said. You need to run **update-grub** (with superuser privileges) each time you edit the */etc/default/grub* file.

 Here in an excerpt from mine:
```
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
```
I've never encountered a countdown with these settings.
[QUOTE=GNU GRUB (version 2.04) manual]```
'GRUB_TIMEOUT'
     Boot the default entry this many seconds after the menu is
     displayed, unless a key is pressed.  The default is '5'.  Set to
     '0' to boot immediately without displaying the menu, or to '-1' to
     wait indefinitely.

     If 'GRUB_TIMEOUT_STYLE' is set to 'countdown' or 'hidden', the
     timeout is instead counted before the menu is displayed.

'GRUB_TIMEOUT_STYLE'
     If this option is unset or set to 'menu', then GRUB will display
     the menu and then wait for the timeout set by 'GRUB_TIMEOUT' to
     expire before booting the default entry.  Pressing a key interrupts
     the timeout.

     If this option is set to 'countdown' or 'hidden', then, before
     displaying the menu, GRUB will wait for the timeout set by
     'GRUB_TIMEOUT' to expire.  If <ESC> is pressed during that time, it
     will display the menu and wait for input.  If a hotkey associated
     with a menu entry is pressed, it will boot the associated menu
     entry immediately.  If the timeout expires before either of these
     happens, it will boot the default entry.  In the 'countdown' case,
     it will show a one-line indication of the remaining time.
```[/QUOTE]

---

### Post by ra-white on 2022-02-10
Hey guys thanks for your quick response.

While your methods did not solve my problem, I came across a working solution:

sudo -H gedit /etc/grub.d/30_os-prober

Changed following rows to this:

23   quick_boot="0"

37   set timeout=1

Then saved and sudo apt-update grub


Problem solved :guitar:

---

### Post by Bashing-om on 2022-02-10
ra-white :D

Still more than one way to skin a cat :)

If you are in a happy state -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

-happy trails to you-

---

