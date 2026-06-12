---
title: "Problems upgrading to 12.04 on Dell D505"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by czman11 on 2012-07-05
Hi everybody
I am currently running Ubuntu 11.10 on my Dell D505. I tried to do fresh install of Ubuntu 12.04 only to find out that my CPU was not compatible. Somewhere I read that upgrading from current version may be done by just upgrading from Ubuntu software center application instead of new install and bypassing the incompatibility issues. Can anyone of you give me a info if it is possible? I am afraid that once I upgrade I'll run on the incompatibility problem again.

thanks

---

### Post by codingman on 2012-07-05
You can go open the terminal and type:

```
sudo apt-get update && apt-get upgrade
```

Oh, and also post your CPU so we know whether that is the major problem.

---

### Post by 3Miro on 2012-07-05
You can upgrade your distribution with the terminal command:
```
sudo apt-get dist-upgrade
```
There is probably a way to do it from the update manager if you poke around the settings.

However, I am very curious about the CPU compatibility. What is your CPU, if you are using something as old as Pentium III, then you may run into problems, but for anything newer than that, you should not be getting any compatibility issues.

---

### Post by codingman on 2012-07-05
> **3Miro said:**
> You can upgrade your distribution with the terminal command:
```
sudo apt-get dist-upgrade
```
There is probably a way to do it from the update manager if you poke around the settings.

However, I am very curious about the CPU compatibility. What is your CPU, if you are using something as old as Pentium III, then you may run into problems, but for anything newer than that, you should not be getting any compatibility issues.

Woops... yeah do that command before the line of code I gave you.

---

### Post by codingman on 2012-07-05
You also mentioned that your CPU had compatibility issues, what error messages did you get?

Oh, and I found your CPU, it's an Intel Celeron M 1.2 GHz, no?

I don't think this would have a problem...

---

### Post by 3Miro on 2012-07-05
> **codingman said:**
> You also mentioned that your CPU had compatibility issues, what error messages did you get?

Oh, and I found your CPU, it's an Intel Celeron M 1.2 GHz, no?

I don't think this would have a problem...

64-bit Ubuntu will not run on this CPU, but I am not sure about the 32-bit. Recently Ubuntu moved to i686 standard, if the CPU runs on i586, then there would be an issue (and you cannot upgrade). If a proper burn of the 32-bit Ubuntu is giving you a CPU error, then upgrade will not work. Lets hope the issue came from either a bad burn on the CD or the OP got the 64-bit version by mistake.

---

### Post by plucky on 2012-07-06
> **czman11 said:**
> Hi everybody
I am currently running Ubuntu 11.10 on my Dell D505. I tried to do fresh install of Ubuntu 12.04 only to find out that my CPU was not compatible. Somewhere I read that upgrading from current version may be done by just upgrading from Ubuntu software center application instead of new install and bypassing the incompatibility issues. Can anyone of you give me a info if it is possible? I am afraid that once I upgrade I'll run on the incompatibility problem again.

thanks

Your problem is because 12.04 uses the 32-bit PAE kernel and your CPU does not support PAE.I have a Pentium M and it will not boot the 12.04 kernel.
I did install 11.10 and upgraded through the **Update Manager** which should now be offering you the **Distribution Upgrade**.

The problem is if you have to re-install you will have to install 11.10 and upgrade again.

You could try the Xubuntu 12.04 which uses the non-pae kernel,and then install **Ubuntu Desktop** which might be a better solution.

Good Luck

---

### Post by czman11 on 2012-07-09
Thanks. I needed confirmation that someone have done it with the non PAE CPU support and it worked. Luckily, I don't have to reinstall. I already run 11.10. My CPU is Pentium 1.6GHz. If there is anything I should know regarding this CPU give me a reply.

---

