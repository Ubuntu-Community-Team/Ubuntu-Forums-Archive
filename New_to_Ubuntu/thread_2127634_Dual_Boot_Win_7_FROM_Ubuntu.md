---
title: "Dual Boot Win 7 FROM Ubuntu?"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by drumabgo on 2013-03-20
Hi all,

So i switched from Win7 to Ubuntu 12.04 LTS a few months ago, and i'm loving it. However, I just can't get my head around installing Windows games with Wine or POL. 
So i'm thinking I'll dual boot win7 for the sole purpose of gaming and use Ubuntu for everything else, with the hope of figuring out games at some future point. 

I've googled around numerous times, but I only seem to find guides to dual booting with win7 as the current OS. Can anyone point me in the direction of how to set up a DB and install win7 from within Ubuntu? I've got everything set up just how i like it now and i really dont want to have to start from scratch with a fresh install.

Many thanks, in advance.

---

### Post by Cheesemill on 2013-03-20
Have you read the wiki?

[https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu)

---

### Post by dolphin194 on 2013-03-21
Welcome to the forums!

This is actually really easy to do. I have done this plenty of times.

**WARNING: **You can lose your data by performing these methods. It is recommended that you back up your data before attempting to do this.
**NOTE: **You will need *both* your Windows Install DVD, *and* your Ubuntu Live CD/USB.

Here's what you gotta do:
**1. **Boot from your Ubuntu Live CD/USB.
**2.** Launch the Partition Editor, commonly known as GParted.
**3.** Right-Click your Ubuntu partition and click Resize/Move. 

**4. **In the dialog that opens, make the bar at the top smaller, and click Resize/Move
**5.** Click on the check mark at the top of the GParted window, and you will then resize your partition
You are now ready to install Windows.
**6. **Install Windows 7, but make sure you _select your blank space_, not the Ubuntu partition
[U][COLOR=#ff0000]You will lose the ability to boot Ubuntu at this point. [/COLOR]
[/U][B][COLOR=#008000]This is normal, and here's how to fix it:[/COLOR]
[/B]**7.** Boot from your Ubuntu Live CD/USB again.
**8. **Open a Terminal and run the following commands to install the Boot Repair utility:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair
```
**9.** Launch Boot Repair as root
```
sudo boot-repair
```
**10. **Once Boot Repair is open, click on the Recommended Repair button.

:)You should have installed Ubuntu and Windows 7, and have the ability to boot either one. Tell me if you have any issues or questions.

---

