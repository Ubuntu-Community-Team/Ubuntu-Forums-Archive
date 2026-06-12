---
title: "How do I get my bootloader to load a kernel"
date: 2010-04-08
forum: Programming Talk
---

### Post by Jekshadow on 2010-04-08
I am writing my own OS (as a side project) and I have gotten it to do some basic stuff such as print to the screen, reboot, etc. but I cannot find out how to pass control to a small kernel written in C.

I have found a large amount of resources on how to create a basic bootloader that can print to the screen, etc. and a large amount of resources on how to create a basic kernel, but I have not found anything on how to get the bootloader to load the kernel.

Can anybody provide an example or a link to how I might do this in Intel style (NASM) x86 assembly?

[SOLVED]
I found my answer here for anyone who wants to know: 
[http://wiki.osdev.org/Bootloader](http://wiki.osdev.org/Bootloader)

---

### Post by x751 on 2010-04-08
[FONT=Tahoma]Why don't you try GRUB? I remember playing a lot with GRUB to boot my test kernels written in FPC.

Try this[/FONT] [FONT=Tahoma][COLOR=RoyalBlue] [link]("http://www.osdever.net/tutorials/view/using-grub")[/COLOR][/FONT][FONT=Tahoma], perhaps it helps.[/FONT]

---

### Post by lisati on 2010-04-08
> **x751 said:**
> [FONT=Tahoma]Why don't you try GRUB? I remember playing a lot with GRUB to boot my test kernels written in FPC.

Try this[/FONT] [FONT=Tahoma][COLOR=RoyalBlue] [link]("http://www.osdever.net/tutorials/view/using-grub")[/COLOR][/FONT][FONT=Tahoma], perhaps it helps.[/FONT]

I think the OP wants to write their own.

---

### Post by Jekshadow on 2010-04-08
> **lisati said:**
> I think the OP wants to write their own.

I do. This is mainly just so I can learn about how a computer works, from the ground up, not to do things the quick and easy way.

---

### Post by lisati on 2010-04-08
> **Jekshadow said:**
> I do. This is mainly just so I can learn about how a computer works, from the ground up.

It will be an interesting exercise. Good luck on your journey.

---

### Post by Jekshadow on 2010-04-08
> **lisati said:**
> It will be an interesting exercise. Good luck on your journey.

Thanks.

---

### Post by yaami on 2011-01-10
> **Jekshadow said:**
> 

[SOLVED]
I found my answer here for anyone who wants to know: 
[http://wiki.osdev.org/Bootloader](http://wiki.osdev.org/Bootloader)

Hi Jekshadow, 

Can you provide the sample of what you used. I'm trying to figure out how to load the kernel and pass control to it. I know we need to change to the protected mode first....but then may be use call kernel_function() in the bootloader asm.


Thanks.

---

