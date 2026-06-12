---
title: "using compiz config in Ubuntu 18"
date: 2018-10-28
forum: New to Ubuntu
---

### Post by otlichnik73 on 2018-10-28
Hi there everyone! I wanted to get some special effects in my Ubuntu 18, like "wobbly windows" and "workspace cube". Having done a bit of reading, I installed Compiz Config and  tried using it but it did not seem to make any difference to anything. What am I missing?  Cheers!

---

### Post by deadflowr on 2018-10-28
Well, number one is you need a compiz capable desktop, which 18 (? either 18s) isn't.

The desktop closes in proximity to Ubuntu's desktop that can run compiz would be unity.
You can install it with
```
sudo apt install ubuntu-unity-desktop
```
it'll also install lightdm and will ask if you want to switch to it.
Picking yes to switch is usually better, but I've found no issue running with the default gdm so your choice)

Then logout in the login screen you can choose unity

In the normal login screen the option to switch desktop is hidden unit you select the user, 
then the option will show in the cog like icon the shows next to the signin button to the right of the password field.

If you choose to switch to lightdm, then first reboot, and then in the username password box that shows will be an icon box in the corner
click on it and it'll list desktops that you can run, cycle down and click on unity to run unity.

Once unity's running you can then poke around config settings.

Note that some settings can result in temporary glitchiness and might seem to cause a freeze, 
let it be and don't try to do anything as it sometimes can take a minute to adjust itself.
The worst thing you can do is mess with it.
It should come back to a working state eventually.


hope it helps

---

### Post by otlichnik73 on 2018-10-29
> **deadflowr said:**
> Well, number one is you need a compiz capable desktop, which 18 (? either 18s) isn't.

The desktop closes in proximity to Ubuntu's desktop that can run compiz would be unity.


hope it helps

Aaah... I see.. that explains why I can't get compiz going in Ubuntu 18 and in Kubuntu.
Basically (hope it's not too off-topic) I need to find the most "blink-blink" desktop setup for someone who is into fancy effects and bells and whistles.
 I myself is happy with standard Ubuntu and  XFCE. But I need to find a desktop that is able to implement things like "wobbly windows", "spinning cube" etc. in the most efficient way.
I tried Kubuntu as a VM, thinking that KDE is the most fancy desktop,  but compiz did not work there either.
Can you recommend the most "wizz-bang" desktop option? Cheers!

---

### Post by QIII on 2018-10-29
You don't need Compiz for bling with the KDE desktop.  Wobbly Windows, cube effects, etc are already available with Kubuntu. Compiz is not only unnecessary with KDE, it is probably incompatiple.

A VM may limit KDE.  A virtual GPU may not offer the requisite capabilities.

---

### Post by oldrocker99 on 2018-10-29
Ubuntu MATE has Compiz built-in, and can be selected in MATE Tweak's Windows tab, or . It also can look like Windows, Mac, or even Unity. Of course, they're called Redmond, Cupertino, and, wait for it, Mutiny. It also allows, through the Welcome window, installation of drivers and software(!).:KS

 AFAIC, Ubuntu MATE is not only the best version of Ubuntu, but it's the best distro I have ever used in 10 years, and I've used Fedora, Antergos, Mint and SuSE. It is also the way to keep up with the latest version of MATE. Check it out, and boot a live USB or install it in a VM.

Get it at [https://ubuntu-mate.org](https://ubuntu-mate.org)

---

