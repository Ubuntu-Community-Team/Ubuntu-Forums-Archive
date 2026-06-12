---
title: "OEM version, whether he differs from normal distribution?"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by tomek-trymerski on 2015-04-27
Hey,

First, sorry for my language. English isn't my native language. 
Second, I bought Dell laptop on preinstalled Ubuntu 14.04 OEM. My question is "whether he differs from normal distribution?"
One of differences I look is kernel version. Ubuntu 14.04.2 have a kernel 3.16, but OEM version have 3.13. 

I will be grateful for response

---

### Post by sudodus on 2015-04-27
OEM 'only' means that you were offered to create your own user id the first time you run the system instead of using a pre-installed user id, and that there might be some tweaks made by the vendor of the computer.

The 3.13 kernel shows that the OEM installed system was created from 14.04 LTS or 14.04.1 LTS with the Trusty kernel. 14.04.2 uses the Utopic kernel (3.16), which has no long time support. So if your system is working well, I see no reason to upgrade the kernel to 3.16.

Do that only if you need it because some [new] hardware does not work properly - and in that case, try it live before installing / upgrading. According to the plan, the last point release, 14.04.5 LTS will contain the 16.04 LTS kernel, which will also have long time support. You might want to upgrade to that kernel, but you certainly need not do it, and there is always a risk that something will not work.

-o-

The other program packages (except the kernel) will be updated / upgraded automatically within the 14.04 LTS version.

---

### Post by ian-weisser on 2015-04-27
+1 sudodus said it better than I did.

---

### Post by grahammechanical on 2015-04-27
When you purchased that machine did it have Ubuntu 14.04 or 14.01 or did it come pre-installed with 14.04.2?

I ask for this reason. If we download and install a Ubuntu 14.04.2 ISO image the installation will have Linux kernel 3.16 but if we have 14.04.1 installed a normal update/upgrade will update 14.04.1 to 14.04.2 but not bring in Linux kernel 3.16. To get the newer kernel we have to upgrade what is called the hardware enablement stack.

The reason things work this way is because the kernel in 14.04 and 14.04.1 (kernel 3.13) will be supported until April 2019 but the kernel in 14.04.2 (kernel 3.16) will only be supported for 18 months from February 2015.

This wiki page has some charts that explain this and also a command to run if we want to move on the  "utopic" hardware enablement stack. It is our choice because of the short support period for this hardware enablement stack

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

You installation of Ubuntu might differ from mu installation of Ubuntu because it has some OEM branding. The important question is: do our machines have the same repositories/archives/software sources?

Go to System Settings>Software & Updates and see what repositories are listed. Or load gedit and open this file /etc/apt/sources.list. If you are accessing the same archives as the rest of us, then I do not see how there can be any difference?

Regards.

---

### Post by tomek-trymerski on 2015-04-27
When I bought this machine it have Ubuntu 14.04 and I install available upgrates. At the moment I don't know which version is 14.04 or 14.04.1.
I'm now at work. I check repositories/archives/software sources and version OS, when I get home. 

In my laptop I have proccesor i5 5200u. Newest kernel have better support for this architecture?

---

### Post by sudodus on 2015-04-27
If it works well, there is no reason to switch to another kernel. You can try 14.04.2 LTS or 15.04 live and maybe install a test system in a separate partition, but I recommend that you keep the existing system as your 'production system'.

---

### Post by mattharris4 on 2015-04-28
I agree with sudodus.  Do not upgrade your kernel or version until 16.04 comes out.  That version will be supported for five years where as 15.10 will only be supported for nine months and is only intended for developers to try out and tweak new code, programs, etc.  The average Joe Six-Pack should not use any version but a supported LTS version (in this case 14.04).  On occasion a very new computer will need the updated kernel or some driver that has been updated in a non-LTS version but that is the only reason for someone not actively involved in the programming or testing of Ubuntu/other version OS to use one.  Even then if possible I recommend only installing whatever driver is absolutely necessary from a non LTS version to 14.04 (that is beyond my capabilities, I am not a programmer).

If you wish to become an unpaid tester for Canonical (there are actually many volunteers that do this), get a second computer of sufficient RAM, processor, etc., install either 15.04 or the alpha of 15.10 on that computer and play with it, reporting problems through the official channels (and there will probably be a lot of them, especially with an alpha or beta version).  Do not use a daily computer or a computer that your wife, kids, mother in law, etc. will be using to test non LTS versions of any OS.  A virtual machine is an option but IMO it is dicey unless you are extremely familiar with how one works and know how not to accidentally bork your LTS install while using and updating the non LTS version, alpha or beta on the VM.  I personally do not use a virtual machine but at some point I will probably buy a third desktop for this purpose (a $100 refurb from Newegg or Tiger Direct with 4GB of RAM and a 250GB HDD will work fine for this -- and I have to say I am sort of blushing admitting that I already have two desktops at my house, it is sort of embarrassing).

---

