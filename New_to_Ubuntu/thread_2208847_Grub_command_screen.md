---
title: "Grub command screen?"
date: 2014-03-02
forum: New to Ubuntu
---

### Post by ood2 on 2014-03-02
I recently installed Ubuntu on two different laptops- one had been running Windows XP and the hard drive is partitioned for both OSs, and the other was running Vista but went through a serious virus problem that led to installing Ubuntu as the main OS. Both have 12.04, but the older laptop has the 32bit version, if that makes any difference.
The newer laptop runs everything perfectly and its owner has had no issues picking up the command procedures, but the older laptop gets stuck on a screen after I choose to boot Ubuntu instead of XP that says "BASH like line editing" and then gives me a list of possible commands. I am completely new to Ubuntu, and I haven't been able to find anything pertaining to this problem that isn't seriously outdated... I just need to know the command line/lines to fully boot.

---

### Post by grahammechanical on 2014-03-02
You have confused me. Which machine has the problem? Please let us talk only about the machine with the problem. Please confirm that you get a Grub boot menu. What options do you see? When did this problem start? When you first installed it? Or later?

For some reason Grub is unable to load the operating system and is dropping to a Grub rescue prompt. You can try running Recovery mode from the Grub boot menu. Select Resume and see if that gets you to a desktop. We need to know how far you get into the loading process. It would also be useful if you provided information about error messages.

Perhaps you should load a Ubuntu Live session and backup the data and then think about re-installing.

Regards.

---

### Post by ood2 on 2014-03-02
This is the machine that was running XP and has the partitioned drive. When I first installed it ran fine, but I've since restarted it.
I don't see an option for resume on either screen, though. Upon selecting to run Ubuntu I get a screen that says,
"GNU GRUB version 1.99-21ubuntu3.14

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB list possible device or file completions.

grub>"

The options are then: authenticate, background_color, background_image, badram, boot (which says there is no kernel loaded when I select this), break, clear, configfile, continue, cutmem, echo, export, extract_entries_configfile, extract_entries_source, initrd, insmod, linux, loadfont, loopback, ls, lsfonts, menuentry, normal, normal_exit, probe, return, search, search.file, search.fs_label, search.fs_uuid, set, setparams, shift, source, submenu, terminal_input, terminal_output, test, unset

I haven't seen anything that I would define as an error message, either.

---

### Post by Impavidus on 2014-03-02
Something went wrong with the boot loader. Try running [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). It may fix your issue, and at the very least it should give some useful diagnostics.

---

### Post by ood2 on 2014-03-03
I've reinstalled using a USB this time and now everything is working as it should, thank you for the help!

---

