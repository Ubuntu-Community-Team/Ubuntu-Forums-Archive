---
title: "Small boot problem. Ubuntu 12.04"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by rod52 on 2013-03-15
I am new to any Linux system. Loaded Ubuntu 12.04 over windows. Not sure when it started, but Ubuntu boots to Grub Rescue, if that is what it is called. Gives me choices of booting normal, previous versions or running memory tests. Any way to solve this? I did try to run memory tests from the cd before installing Ubuntu. I did not let it finish, if that is the problem.

---

### Post by Bashing-om on 2013-03-15
rod52; Hi ! Welcome to the forum .

The grub boot menu is "normal" if you have more than one operating system installed.
Else perhaps there has been a change in the /etc/default/grub file ?
Are you able to boot into ubuntu with the highest numbered kernel highlighted and press the enter key ?
Is there a time countdown and at zero what system boots ?[INDENT=3]
try'n to help

[/INDENT]

---

### Post by fantab on 2013-03-15
> **rod52 said:**
> I am new to any Linux system. Loaded Ubuntu 12.04 over windows. Not sure when it started, but Ubuntu boots to Grub Rescue, if that is what it is called. Gives me choices of booting normal, previous versions or running memory tests. Any way to solve this? I did try to run memory tests from the cd before installing Ubuntu. I did not let it finish, if that is the problem.

If there is more than one OS installed then GRUB shows its MENU for you to select the desired OS to boot. Its not Grub-Rescue its Grub-Menu. If there is only one OS then the grub-menu is generally skipped. If you dont want to see it then you have to edit the file /etc/default/grub, like the post above mentions.

[QUOTE=GRUB2 Community Ubuntu Documentation]
[LIST]
[*]Normal Hidden Operations Enabled:
[LIST]
[*]No menu entries are displayed. The splash screen, if configured, will be displayed. 
[*]The time the screen remains blank but available for display is determined by a setting in */etc/default/grub* (GRUB_HIDDEN_TIMEOUT) 
[*]GRUB  2 can display a countdown timer to provide visual feedback on the time  remaining until the default selection is chosen. The timeout setting is  enabled in */etc/default/grub* (GRUB_HIDDEN_TIMEOUT_QUIET) 
[*]The user may display the menu by pressing any key.
[LIST]
[*]Once the menu displays, the GRUB_TIMEOUT counter begins. Pressing any key stops the countdown.
[LIST]
[*]If no key is pressed by the end of the timeout the default entry determined by settings in */etc/default/grub* will be selected. 
[/LIST]
    
[/LIST]
    
[/LIST]
  
[*]Hidden Menu Operations Not Expected (Abnormal):
[LIST]
[*]The user may be able to display the menu in one or more of the following ways:
[LIST]
[*]Holding down the SHIFT key early in the boot process until the menu displays.
[LIST]
[*]GRUB  2 searches for a depressed SHIFT key signal during boot. If the key is  pressed or GRUB 2 cannot determine the status of the key, the menu is  displayed. 
[/LIST]
  
[*]Pressing the ESC key during a 3 second window as GRUB 2 runs. 
[/LIST]
    
[/LIST]
    
[/LIST]
[/QUOTE]

If you don't want that menu to be displayed then from Terminal:

```
$ gksu gedit /etc/default/grub
```

Edit the file by changing the Line *#GRUB_HIDDEN_TIMEOUT="0"* to **GRUB_HIDDEN_TIMEOUT="0"** (you have to remove '#') and save the file.

Or if you want to reduce the time of Grub-Menu display by edititing *GRUB_TIMEOUT="10"* to **GRUB_TIMEOUT="3"** or what ever time in seconds you please.

I hope that helps...

---

### Post by rod52 on 2013-03-15
I am able to boot with the highest version shown. Unbuntu is the only OS.

---

### Post by rod52 on 2013-03-15
Forgot to mention. Did not notice a time out, but that does not mean it was not there. I will look the next time I boot.

---

### Post by rod52 on 2013-03-15
Re-booted. There was no timer. Just waits for me to hit enter.

---

### Post by rod52 on 2013-03-15
After entering the command as advised to edit grub. This is what I saw. No time out.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

### Post by fantab on 2013-03-16
Does it wait forever (until you hit enter) to boot or just 10 secs?

If and when you change anything in /etc/default/grub you have to update your Grub.cfg by:

```
$ sudo update-grub
```

---

### Post by rod52 on 2013-03-16
I made no changes to grub. It just sits forever until I hit enter.

---

### Post by fantab on 2013-03-17
Start by changing the following Lines in /etc/default/grub:

```
$ gksu gedit /etc/default/grub
```

Comment out* GRUB_HIDDEN_TIMEOUT_QUIET=true* by adding "#" before the line, like this: **#**GRUB_HIDDEN_TIMEOUT_QUIET=true
and change *GRUB_TIMEOUT=10* to GRUB_TIMEOUT=**1**

Save the file and run:
```
$ sudo update-grub
```
Reboot Ubuntu.

Now, at boot you should see the Grub-Menu and at the end of **1** second it should boot Ubuntu. 
Tell us if grub works as intended.

---

### Post by rod52 on 2013-03-17
No change. Maybe I'll just live with it, or re-install Ubuntu 12.04 and see if that fixes it.

---

### Post by rod52 on 2013-03-17
Re-installing did not fix it. Thanks for the responses. I will just keep an eye on the forums for similar posts.

---

