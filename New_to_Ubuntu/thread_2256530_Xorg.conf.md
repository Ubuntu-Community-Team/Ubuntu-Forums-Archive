---
title: "Xorg.conf"
date: 2014-12-13
forum: New to Ubuntu
---

### Post by juju2 on 2014-12-13
Hi,

I have a problem with my graphics: I have an onboard graphic board from Intel (with lshw - c video, the displayed product is Xeon E3-1200 v2/3rd Gen Core Processor Graphics Controller) and a graphic board HIS AMD Radeon HD 7790. As I couldn't find out how to install the right AMD driver, I just used the intel graphic board because it worked from the beginning. A few months later I decided to give it another try and tried several things to find and install the AMD graphic driver. I tried sudo apt-get update and upgrade and some ati-configuration, and the result i got was that now none of them is working.

Here is my situation: When I start with the AMD graphic board, I end up in a black or purple screen and cannot do anything (not even CTRL+ALT+F1). When I boot only with the Intel Board, I get a black screen, but i have access to CTRL+ALT+F1. There I found out that the intel driver is still there and installed; I deleted the "new" amd driver and the intel driver is now the one in use. Actually, I don't think I have the wrong driver but I got something wrong with this Xorg.conf file. (Is it right that the xserver makes the Graphical Interface and Xorg.conf configures the options and "connects" the Graphic Board with the OS?)

When I type "whereis Xorg.conf", it is not found in the /etc directory, but is found in 3 directories:
/usr/bin/Xorg /usr/bin/X11/Xorg /usr/share/man/man1/Xorg.1.gz
but when I browse to these directories I cannot find Xorg.conf with the ls command. So maybe it was accidentally deleted?

When I run a "repair boot" in Ubuntu and start the safe graphic mode (is it the name? It warns me it would start with low graphics and then tells me there is a problem with graphic configuration), I can't edit the configuration file. Maybe it isn't there.
I have found that I can newly configure Xorg with Xorg :1 -configure. When I try this, it works, and I can also copy it in the /etc/X11/xorg.conf. But when I reboot the computer and look into the history, these commands aren't displayed there. Do I have so "save" the changes or somehow activate them? (The last command displayed is Xorg.conf.failsafe. I have to found out what this was because i have tried hundreds of other commands after this)

I know I have written and tried much and I don't know much about what I'm doing. So I would be glad about any tips or hints for what could be the problem, and maybe your opinion on these Quesions:
1) How can it be that the last commands aren't shown in the history?
2) Does Xorg.conf have to be in /etc/X11/ ?
3) If I decide to completely reinstall Ubuntu, does Ubuntu try to safe the files or are they lost?

Sorry for the chaos, but I'm really stuck :-(
Thanks for any advice
Juju

PS: If it's important: I installed Ubuntu on the same hard drive as Windows, but so long this was no problem.

---

### Post by mikewhatever on 2014-12-13
1. You probably run the commands as root, so the history is saved in the root user's home - /root. Not sure why you need it, the generated xorg.conf (no capitals!) is what matters.
2. Yep, and Xorg.conf is not the same as xorg.conf - Linux is case sensitive.
3. Depends. If you choose to format partitions (also the default option), then files are lost. It's best to take care of a backup before reinstalling.

---

### Post by grahammechanical on 2014-12-13
When we install Ubuntu we are not asked to put in the monitor resolution. Why? It is because modern monitors have that information stored in a chip. It is called Extended Display Identification Data (EDID). Every time we load Ubuntu the xserver reads the EDID and sets the optimum monitor settings. This is why the xorg.conf is not used in Ubuntu. Although it is still possible to make use of it.

You do not say what version of Ubuntu you are using. Or if this video set up came with the machine or you inserted a AMD graphic card yourself. In other words did this machine come with Hybrid graphics? Have you tried installing a video driver from System Settings>Software and Updates>Additional drivers tab?

If the machine only had the Intel graphics when you installed Ubuntu, then it would only have a driver for the Intel graphic adapter. If the AMD card was installed after, then you may need to go into the BIOS to disable to onboard graphics.

On Ubuntu 14.04 Recovery Mode>Resume would try to load Ubuntu using an open source video driver called llvmpipe.

In case you do have hybrid graphics here is some information

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Regards.

---

### Post by juju2 on 2014-12-18
Hi,

thanks for your replies! I am still using Ubunut 13.10, I wanted to try 14.04 but don't know if I can how I can update the system via console. Maybe it would be a good idea? 

The hybrid graphics could be a problem - yes, I installed Ubuntu when I only had the intel graphics, and later added the AMD board. Maybe disabling the onboard graphics in BIOS will help. I will try that! And thanks for the link.

I know that linux is case sensitive, but I don't know the difference between xorg.conf and Xorg.conf... what is it?

Thanks & Regards
Juju

---

### Post by Bashing-om on 2014-12-18
juju2; UUoohhh,

Not a good thing - at this point in time:
> 
thanks for your replies! I am still using Ubunut 13.10,


As that release is End-Of-Life, and no longer has support. The software repository to effect any changes no longer exists.

The best thing - in our opinion (mouse in pocket) is to back up your data, and do a clean fresh install of 14.04 .

[INDENT][INDENT]past time to move on
[INDENT][INDENT][INDENT]bigger, better things
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DuckHook on 2014-12-18
> **Bashing-om said:**
> The best thing - in our opinion (mouse in pocket) is to back up your data, and do a clean fresh install of 14.04 .[INDENT][INDENT]past time to move on[INDENT][INDENT][INDENT]bigger, better things
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
@juju2

Listen to Master Bashing-om, Padawan. Wise, he is.

If you have not yet reinstalled, then the best way to backup at this point is to boot from a LiveDVD/USB, connect an empty USB Drive/stick, and backup your entire /home directory. It is SUPER important that you make Windows recovery disks and a full backup of all your Windows data. Make sure you can recover before further monkeying around with your system. After that, a clean install of 14.04 (NOT upgrade) in the Linux partition while preserving Windows. Also, do NOT install 14.10 because it will lose support in 8 month's time, whereas 14.04 still has 4.5 years left. The LTS versions are meant for beginners and production machines. Non-LTS versions are really meant for power users or development machines or situations when a broken upgrade won't ruin your day.

When you reinstall, it may also be helpful to disable your Intel graphics in the BIOS and run only on the AMD card. Then try a LiveDVD/USB session first to see if it works. It should. The HD7790 is a mainstream card based on an established chipset and used by lots of people. Once running in LiveDVD/USB session, post results of:```
lspci -vk | grep -iA9 vga
```and```
xrandr
```Also, tell us what monitor you are connecting to your AMD card, its maximum native resolution, what cable you are using, and the type of port at either end (ie HDMI to DVI, etc). Are you connecting directly or through a KVM switch?

You are to be commended for trying so many solutions by yourself before asking here for help. Now that you've put in the effort, please use this thread and the community for further help.

---

### Post by Bashing-om on 2014-12-18
juju2; Hey hey !

Now that ^^^
Is the true, in-depth skinny. Ya gotta love DuckHook !

With continued care and effort we will get you through this.

[INDENT][INDENT]all in the care and feeding
[INDENT][INDENT][INDENT]of your 'buntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

