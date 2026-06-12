---
title: "Want to see drivers loading"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by shawnerz on 2008-07-22
All,
Is there a boot option to watch the drivers load instead of seeing the "Ubuntu" splash screen when the computer boots up?
Thanks,
-Shawn

---

### Post by steveneddy on 2008-07-22
> **shawnerz said:**
> All,
Is there a boot option to watch the drivers load instead of seeing the "Ubuntu" splash screen when the computer boots up?
Thanks,
-Shawn

Yes, there is.

---

### Post by sdennie on 2008-07-22
If you permanently want this behavior, edit /boot/grub/menu.lst and change the line that looks like:

```

# defoptions=quiet splash

```

To either:

```

# defoptions=quiet

```

Or, for a super verbose login display:

```

# defoptions=

```

Then run:

```

sudo update-grub

```

After that you won't get the splash screen but instead text zooming down the screen.  

If you only want to use these options once in a while and not make them permanent, when the grub screen menu/countdown appears, select the kernel you want to boot and hit, 'e', go down one line and hit 'e' again and remove the 'splash' and optionally 'quiet' arguments.  Hit enter and then 'b' to boot the kernel like that.

---

### Post by pi.boy.travis on 2008-07-22
If you don't want to edit menu.lst manually, you can install StartUp-Manager via synaptic.  It will be in System/Administration/

---

### Post by ramjet_1953 on 2008-07-22
An easier way to do this and also do quite a few extra things associated with boot-up is to install the Startup-Manager package.

Use Synaptic, or cut and paste this command into a terminal window:

[COLOR="Red"]sudo apt-get install startupmanager[/COLOR]

Regards,
Roger :cool:

---

### Post by Joeb454 on 2008-07-22
> **steveneddy said:**
> Yes, there is.

You could've at least described a method of doing it, or at least tried to :)

> **ramjet_1953 said:**
> An easier way to do this and also do quite a few extra things associated with boot-up is to install the Startup-Manager package.

Use Synaptic, or cut and paste this command into a terminal window:

[COLOR="Red"]sudo apt-get install startupmanager[/COLOR]

Regards,
Roger :cool:

You can use [noparse]```

```[/noparse] tags to enclose portions of code :)

---

### Post by shawnerz on 2008-07-23
Joeb,
Steveneddy must work for Microsoft. :wink:

And thanks for the [code] [\code] tip.  I made another post in another part of the forum where I probably should have used that.
Thanks,
-Shawn

---

