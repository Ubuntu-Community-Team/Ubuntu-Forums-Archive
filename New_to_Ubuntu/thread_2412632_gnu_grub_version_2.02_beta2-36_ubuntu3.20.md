---
title: "gnu grub version 2.02 beta2-36 ubuntu3.20"
date: 2019-02-15
forum: New to Ubuntu
---

### Post by evacernok on 2019-02-15
[COLOR=#242729][FONT=Arial]Laptop worked fine, and after reset this appeared :[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]"Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completitions. Anywhere else TAB lists possible device or file completitions. grub"[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]and its blocked on it, I tried some stuff, but nothing helped. I cant start the laptop, I cant do anything.
Please, what can I do with this ? 
Thank you for the advices ! 
Eva[/FONT][/COLOR]

---

### Post by yancek on 2019-02-15
> [COLOR=#242729][FONT=Arial]Laptop worked fine, and after reset this appeared :[/FONT][/COLOR]

You need to clarify what you mean by 'reset'.  If you reset the laptop to factory defaults, that's expected behavior and your personal data will be gone.  Explain exactly what you did.

---

### Post by evacernok on 2019-02-15
Thank you Yancek for your reply
We watched movie, the laptop was slow, we reset it or actually it switch off, and after switch on, this appeared. With button we tried to switch off again but its there all the time when we switch it on

---

### Post by Impavidus on 2019-02-15
It sounds like a grub prompt or a grub rescue prompt. When you switch off Ubuntu (or any other operating system) using the power button, bad things can happen. In particular if you do so when the system is installing an upgrade in the background, which may be what happened.

Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and create a BootInfo summary. That should tell us what's going on.

---

### Post by evacernok on 2019-02-15
I cant go outside of this window, I can not do anything... I tried to google how to fix it and follow some step by step and I somehow success to made "boot succeeded", it went to another window or menu and after it came back to this one. Thats all, I dont know how to go outside of that window... tried ctr+alt+del, yes it reset it but after that the same window come back...
Now i tried this : (but after first line it shows error)
[COLOR=#333333][FONT=Ubuntu]- open a new [Terminal]("https://help.ubuntu.com/community/Terminal"), then type the following commands (press Enter after each line): [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo add-apt-repository ppa:yannubuntu/boot-repair
[FONT=inherit][/FONT]sudo apt-get update
[FONT=inherit][/FONT]sudo apt-get install -y boot-repair && boot-repair

---

### Post by evacernok on 2019-02-15
Other window where i can go is 
Boot Manager
Boot option menu
ubuntu (ST500LT012-1DG142)
enter to select and option...

---

### Post by oldfred on 2019-02-15
Those are your UEFI/BIOS boot options/menu.
You need to boot Ubuntu live installer to be able to add Boot-Repair and run report.
If you plug in a working Ubuntu live installer, it should give that as another boot option in your UEFI/BIOS boot menu.

---

