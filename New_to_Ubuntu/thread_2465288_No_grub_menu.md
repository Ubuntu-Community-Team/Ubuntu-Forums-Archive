---
title: "No grub menu"
date: 2021-07-28
forum: New to Ubuntu
---

### Post by mkesleem on 2021-07-28
I have dual boot Windows and Ubuntu.

When I start my computer, I cannot see the grub menu. However, I am able to select whether I boot Windows or Ubuntu using my keyboard (I know what the menu looks like, and what buttons to click, but I cannot see the grub menu). I have tried running Boot Repair, but I still cannot see the grub menu. How can I fix this?

This is the message I got after running Boot Repair: [http://paste.ubuntu.com/p/5P9ZhXqywT/](http://paste.ubuntu.com/p/5P9ZhXqywT/)

---

### Post by deadflowr on 2021-07-28
Try changing the line
```
GRUB_TIMEOUT_STYLE=hidden
```
to
```
GRUB_TIMEOUT_STYLE=menu
```
in the file /etc/default/grub
and rerun the sudo update-grub command.

---

### Post by mkesleem on 2021-07-29
I have made this change, but I am still having the same problem. I cannot see the grub boot menu.

This is the updated boot repair message: [http://paste.ubuntu.com/p/5Bcdn7bsCN/](http://paste.ubuntu.com/p/5Bcdn7bsCN/)

---

### Post by tea for one on 2021-07-29
Can you open a terminal and enter:-

```
sudo update-grub
```

Please post the terminal output here within code tags

---

### Post by mkesleem on 2021-07-29
I ran the command

```
sudo update-grub
```


This is the output

```
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-151-generic
Found initrd image: /boot/initrd.img-4.15.0-151-generic
Found linux image: /boot/vmlinuz-4.15.0-122-generic
Found initrd image: /boot/initrd.img-4.15.0-122-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

```

---

### Post by tea for one on 2021-07-30
Grub still not showing after powering on the PC?

Your grub entry in your second boot-repair report looks OK to me so I'm a bit surprised that it does not appear.

There are a few things to try to see if it can be encouraged to appear:-

[LIST]
[*]Change the default OS (GRUB_DEFAULT=0 or 1 or 2) 
[*]Re-install grub completely (either from a running session or from a live session)
[*]Tidy your efibootmgr list
[/LIST]
I would be cautious about trying too much, it depends on your level of confidence.
Grub is a sensitive soul sometimes.

---

### Post by deadflowr on 2021-07-30
Try the answer here:
[https://askubuntu.com/a/1154020]("https://askubuntu.com/a/1154020")

Or you could try uncommenting the line
```
#GRUB_GFXMODE=640x480
```
and try a resolution you know works on your monitor.
Just to see if the default grub resolution was not feasible for it.

---

### Post by tea for one on 2021-07-30
> **mkesleem said:**
> However, I am able to select whether I boot Windows or Ubuntu using my keyboard (I know what the menu looks like, and what buttons to click, but I cannot see the grub menu). 

I think that I have misunderstood this thread.
Grub is available for you to select an OS but the text does not appear on the screen?

Is there some sort of video setting in your UEFI set-up which delays the activation of the monitor?

---

### Post by mkesleem on 2021-07-31
I am using a laptop. I don't think there is a UEFI set-up which delays the activation of the monitor. I have used this laptop with dual boot for about three years now. I never had this problem until a couple of days ago, and I still have no idea why I cannot see the grub menu.

My laptop displays the screen with the Lenovo logo. I used to see this screen before the grub menu opened. Now, I can no longer see the grub menu.

---

### Post by mkesleem on 2021-07-31
I have fixed the problem by uncommenting the line

```
#GRUB_TERMINAL=console
```

and running the command

```
sudo update-grub
```

---

### Post by garvinrick4 on 2021-08-05
Just want to see if you are getting into /etc/default/grub  correctly.
> sudo gedit /etc/default/grub
Now make your changes and hit save 

open terminal and 
> sudo update-grub

---

### Post by garvinrick4 on 2021-08-05
Just want to make sure you are getting into your /etc/default/grub to make changes and save.
Others may need this post also.

> sudo gedit /etc/default/grub
Now make changes and save. Those who are opening without sudo changes will not be saved.

open terminal and
> sudo update-grub
Done

#OOPS
seems I have posted twice mind is working well Huh

---

