---
title: "Grub is not displaying in ubuntu 11.10"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by m.mohan100 on 2012-02-01
I've recently installed ubuntu11.10 in my pc. I was working with windows 7 already. After installing ubuntu 11.10 the grub is not displaying when pc starts. instead, the monitor is saying that,
"The current input timing is not supported by the monitor display. Please change your input timing to 1600x900@60Hz or any other monitor listed timing as per the monitor specifications."
After the message is shown, the system goes to ubuntu login screen and later I can work as usual. I can even select the windows 7 OS by pressing the down arrow in my keyboard even though the message is displaying. So, i hope the grub is working normally. During shutting down in ubuntu 11.10, the same message is displaying instead of ubuntu logo. The issue is not seen while using windows. I think there is no issues with the monitor as I had used it with ubuntu 11.04.
My monitor is 'Dell IN2030M'. I'm using AMD sempron(tm) 145 processor.
Please help me to solve the issue.

---

### Post by lechien73 on 2012-02-01
Hello & welcome to the forums,

As far as I know, Grub2 defaults to 640x480, which some newer monitors don't support.

You can change the resolution used by Grub by opening a terminal window and typing:

```
gksudo gedit /etc/default/grub
```

Enter your password, and the file will open in a text editor.

You will see where the line GRUB_GFXMODE is commented out, underneath this add the lines:

```
GRUB_GFXMODE=1600x900
GRUB_GFXPAYLOAD_LINUX=1600x900
```

Save the file and close the editor. Now, from the terminal, run:

```
sudo update-grub
```

And reboot your computer to see if the graphics mode works :)

---

### Post by m.mohan100 on 2012-02-01
I did as you said. But didn't made any effects to the issue.
I then changed "GRUB_GFXPAYLOAD_LINUX=1600x900" as a comment by adding a # before it.
Now I can see the ubuntu logo while shutting down the pc. But I can't see the grub yet.

Thank you for your effort!

---

### Post by m.mohan100 on 2012-02-01
hurrey!!
Problem is solved.
I typed:
GRUB_GFXMODE=1024x768
and typed
GRUB_GFXPAYLOAD_LINUX=800x600

and done the rest as you said

Thanx

---

