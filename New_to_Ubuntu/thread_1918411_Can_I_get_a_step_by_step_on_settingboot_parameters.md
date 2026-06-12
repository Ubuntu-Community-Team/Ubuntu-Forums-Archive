---
title: "Can I get a step by step on settingboot parameters?"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by beelzenoob on 2012-01-31
Hey Guys,

Totally newb question.  I'm not very familiar with grub2 and I need help setting up my parameters to load Ubuntu 11.

I have an ASUS M2400N (pretty old I know!)

I know that the splash needs to be quiet, and i need to use noapic, nolapic, acpi=off, irqpoll pci=routeriq.

Thanks

:popcorn:

---

### Post by beelzenoob on 2012-02-01
really could use help on this guys!

---

### Post by lechien73 on 2012-02-01
Hi & welcome to the forums,

The temporary - per session - fix would be to:

[LIST=1]
[*]Reboot your PC and - after the self-test screen - hold down the Shift key so that the Grub menu appears.
[*]Press **e** to edit the Grub command line.
[*]After where it says "quiet splash", add your other boot parameters
[*]Press Ctrl-X to boot
[/LIST]

To make it permanent, open a terminal window and type the following:

```
gksu gedit /etc/default/grub
```

This will prompt you for your password and then open a text editor with a complex-looking file open.

Scroll down to the line that reads:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Add your other boot parameters between the quotes.

Save the file and quit from the text editor.

Now, at the command prompt, type:

```
sudo update-grub
```

That will make the changes permanent, and you won't have to add it each time you boot.

---

### Post by beelzenoob on 2012-02-01
so i should just put "quiet splash noapic nolapic acpi=off irqpoll pci=routeriq"

---

### Post by beelzenoob on 2012-02-01
worked great. thanks so much!!!

---

### Post by lechien73 on 2012-02-02
You're welcome...glad it's working for you now :)

If you get chance, please could you use the **Thread Tools** menu at the top of the screen, and mark the issue as [SOLVED]?

Thanks

---

