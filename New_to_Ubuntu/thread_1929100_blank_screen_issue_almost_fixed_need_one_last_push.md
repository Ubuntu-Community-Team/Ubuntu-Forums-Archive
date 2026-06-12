---
title: "blank screen issue almost fixed need one last push"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by micxploed on 2012-02-21
Hello people,I am installing ubuntu on my sisters laptop and i had the "blank screen after boot" problem, but, I did ALOT of research and I am close to the end of this. This is for Ubuntu 11.10, laptop is dell inspiron M5010. At start up, I hold the shift key to bring up the grub menu, then I hit e to edit, then I change quite and splash to pci=noacpi then ctrl and x to boot. That Fixed the blank screen problem!! BUT, now I have to change and SAVE it from the inside, which is where my problem is. If i reboot, I have to change the quite splash again. I have tried to look for the boot command within to change and save, but i cant, please help!  THANKS!

---

### Post by xumuk37 on 2012-02-21
also you could edit the grub main config file and stop change this each time you boot...

---

### Post by micxploed on 2012-02-21
> **xumuk37 said:**
> also you could edit the grub main config file and stop change this each time you boot...
 Thank you for your response but, what do you mean by "stop change"?

---

### Post by micxploed on 2012-02-21
> **xumuk37 said:**
> also you could edit the grub main config file and stop change this each time you boot...
...also, i do not know where to change grub config within the os.

---

### Post by roelforg on 2012-02-21
SIMPLE!!!!
Open a terminal and maximize it;
Type: sudo nano /etc/default/grub
There should be a line starting with this:
```

GRUB_CMDLINE_LINUX_DEFAULT=

```
There are several options in that line, the options quiet and splash should be part of them,
add pci=noacpi between the 2 (1 space should separate them)
Hit CTRL-O
Hit enter
Hit CTRL-X
Run from your terminal:
```

sudo update-grub

```
And reboot.

We just modified grubs config and pushed it around in the system.

---

### Post by micxploed on 2012-02-21
> **roelforg said:**
> SIMPLE!!!!
Open a terminal and maximize it;
Type: sudo nano /etc/default/grub
There should be a line starting with this:
```

GRUB_CMDLINE_LINUX_DEFAULT=

```
There are several options in that line, the options quiet and splash should be part of them,
add pci=noacpi between the 2 (1 space should separate them)
Hit CTRL-O
Hit enter
Hit CTRL-X
Run from your terminal:
```

sudo update-grub

```
And reboot.

We just modified grubs config and pushed it around in the system.
BROTHER! IT WORKED!! Thanks man, you ROCK!

---

### Post by roelforg on 2012-02-21
> **micxploed said:**
> BROTHER! IT WORKED!! Thanks man, you ROCK!
Sure, read the first 2 lines of my signature.

---

