---
title: "Can't access Login Screen Setup"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by RobbyemCee on 2008-07-24
Hello!

I just started using Ubuntu 8.04 yesterday and it's about the greatest thing ever. One problem tho. I'm trying to access the Login Screen Setup Menu.

I have tried three methods.

1) Going to System > Administration > Login Window

2) Right clicking my username on the top panel and selecting "Setup Login Screen".

3) typing "sudo gdmsetup" in the terminal. 

Everytime, and with all three methods, the dialog window pops up for a second then disappears.

I am using compiz. Any suggestions?

-RobbyemCee

---

### Post by roquefilipe on 2008-07-24
when you try this
> **RobbyemCee said:**
> Hello!
3) typing "sudo gdmsetup" in the terminal. 

does it give you any erros and or warnings ?

---

### Post by PCessna on 2008-07-24
> **roquefilipe said:**
> when you try this

does it give you any erros and or warnings ?
Weird, Is the problem persisting, Sometimes little things like these happens to me, and I just do a quick reboot to that GNOME desktop and what not besides the Linux kernel can get a fresh start. 

I agree with roque, Do you get an error or warning, OR prompt for Password?

---

### Post by RobbyemCee on 2008-07-24
The problem corrected itself, don't know how or why. I restarted last night to see if that would fix it and it did not. I was tired so I turned off my machine and went to bed. When I booted up this morning it worked fine.

The only time I had to put a password in was when I tried running it from the terminal. I never got any error messages of any kind. It would just pop-up then go away. 

Thanks for the help dudes.

-RobbyemCee

---

### Post by artmendez on 2008-07-25
Hello.

I had no problem on changing it.

I've been using Hardy ever since it was released. I changed login window config a couple times now... Yesterday I changed it again just beacause... now I can't change it back. Same symptoms as RobbyemCee stated.

Running gdmsetup as superuser in terminal throws a **Segmentation fault** message, as plain as that. I have restarted my computer several times and no relief.

I'm running Ubuntu, 2.6.24-19 generic, GNOME 2.22.2.

Any ideas? :confused:

Thanks in advance.

saludos.

---

