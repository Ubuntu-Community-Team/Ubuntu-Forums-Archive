---
title: "GRUB config"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by Hex9 on 2012-09-29
Hi all, 

On my PC i have both Windows 7 and Ubuntu installed.
When Booting into GRUB it provides me with the two options:

>Windows 7

>Ubuntu

Is there anyway of making Ubuntu the top choice (First choice)
It's annoying when i start up the computer and walk away and it boots into windows.

Thanks, John :)

---

### Post by coffeecat on 2012-09-29
> **Hex9 said:**
> 
When Booting into GRUB it provides me with the two options:

>Windows 7

>Ubuntu


That doesn't look like the way a grub menu would be set up as default, more like the Windows bootloader when you install with wubi. Did you do a wubi install or a conventional one with Ubuntu to its own partition? That is, did you run the wubi installer from within Windows or boot up with a live CD or USB of Ubuntu to run the installer?

---

### Post by Hex9 on 2012-09-29
> **coffeecat said:**
> That doesn't look like the way a grub menu would be set up as default, more like the Windows bootloader when you install with wubi. Did you do a wubi install or a conventional one with Ubuntu to its own partition? That is, did you run the wubi installer from within Windows or boot up with a live CD or USB of Ubuntu to run the installer?

It's probably the Windows bootloader, sorry about that.. I installed Ubuntu inside Windows with wubi. (I had a lot of trouble installing it on separate partitions and was constantly losing all information on my windows partition) Do you suggest the easiest thing to do is a separate install? 

Im preparing a laptop and have yet to install anything on it yet, but i plan to install both OS's.

---

### Post by funicorn on 2012-09-29
The non-system-disturbed and clean-user-defined way to do this is
```
sudo vi /etc/default/grub
```change the line 'GRUB_DEFAULT=0' to 'GRUB_DEFAULT=saved', then
```

sudo update-grub
sudo grub-set-default "Ubuntu"

```Warning: do this only if you are 100 percent sure about the menuentry string, like "Ubuntu" or "Windows 7" or "Ubuntu&#65292;Linux 3.5.0-15-generic" and stuff like that.

This could also be done by editing /etc/default/grub and change the line &#8216;GRUB_DEFAULT=0&#8217; to 'GRUB_DEFAULT=&#8221;Ubuntu&#8220; ', then run 'update-grub', which however is not a once-and-for-all solution.

---

### Post by Hex9 on 2012-09-29
> **funicorn said:**
> The non-system-disturbed and clean-user-defined way to do this is
```
sudo vi /etc/default/grub
```change the line 'GRUB_DEFAULT=0' to 'GRUB_DEFAULT=saved', then
```

sudo grub-set-default "Ubuntu"
sudo update-grub

```Warning: do this only if you are 100 percent sure about the menuentry string, like "Ubuntu" or "Windows 7" or "Ubuntu&#65292;Linux 3.5.0-15-generic" and stuff like that.

This could also be done by editing /etc/default/grub and change the line ‘GRUB_DEFAULT=0’ to 'GRUB_DEFAULT=”Ubuntu“ ', then run 'update-grub', which however is not a once-and-for-all solution.

Thanks, i will try this soon and let you know how it goes

---

### Post by coffeecat on 2012-09-29
> **Hex9 said:**
> Thanks, i will try this soon and let you know how it goes

Please don't - I'll get back to you shortly.

@funicorn, the OP is seeing the Windows BCD menu, NOT grub. This may only complicate things.

---

### Post by Hex9 on 2012-09-29
> **coffeecat said:**
> Please don't - I'll get back to you shortly.

@funicorn, the OP is seeing the Windows BCD menu, NOT grub. This may only complicate things.

Will do, sorry. I responded too quickly..

---

### Post by funicorn on 2012-09-29
Aha I see.  If that's the case, just run 'bcdedit' in Windows7 and set the default entry. Just make sure you are using the admin cmd shell, not a user one.

---

### Post by coffeecat on 2012-09-29
Editing the bcd menu with bcdedit is certainly the most commonly recommended way of doing this, but I find it to be the most user-hostile utility I've come across in many a long while! :wink: Fortunately, there's a GUI way to do it in Windows 7. See here:

[http://www.psychocats.net/ubuntu/wubi#bootorder](http://www.psychocats.net/ubuntu/wubi#bootorder)

In short: Control panel -> System & Security -> System -> Advanced System Settings-> Advanced tab (it will open with this tab anyway) -> Startup and Recovery, click Settings button -> change your default operating system from the drop-down. 

That doesn't change the menu order, but if you choose Ubuntu, the ubuntu entry will be highlighted and will boot if you leave it longer than the display time (default 10 seconds).

With regard to your other questions in post #3, wubi is a good way to start off, but was never intended as more than a tryout. It runs slower than a conventional install and is vulnerable to filesystem corruption in the host operating system. Doing a conventional install is not really easier as you have to consider your partition layout. The Ubuntu installer can do all this for you in most straightforward circumstances, but I see that you have had problems and lost information. Perhaps, once you have resolved the boot order of wubi to your satisfaction, you might want to start a new thread (it would be tidier) detailing the problems you had and asking for help with setting up a conventional dual-boot.

---

