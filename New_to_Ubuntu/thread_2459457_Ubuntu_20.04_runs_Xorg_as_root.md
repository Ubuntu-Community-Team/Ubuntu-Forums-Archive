---
title: "Ubuntu 20.04 runs Xorg as root"
date: 2021-03-19
forum: New to Ubuntu
---

### Post by maketopsite on 2021-03-19
although GDM is used. Do information from [https://wiki.ubuntu.com/X/Rootless ]("https://wiki.ubuntu.com/X/Rootless")please still apply to latest Ubuntu ?

---

### Post by TheFu on 2021-03-19
I haven't any clue, but ... 

20.04 isn't the latest Ubuntu. It is the latest LTS.

I've never seen X11 run without root, but I haven't looked too hard. It has been a known flaw for 25+ yrs on all X/Servers.

Development for X11 is winding down in favor of Wayland. 21.04 will have Wayland as the default again, like they tried in 17.10. Hopefully, all the stuff that broke will work better this attempt. There have been updates in XWayland, which I guess is the network X/Server for all the people who use remote X11 daily in their workflows. It will be interesting to see Wayland and XWayland in 21.04.  If screen capture tools and video capture tools work correctly, along with remote X-clients, I'll be happy. Active support and simplified X code is a good thing in my book.  At this point, I'm concerned, but hopeful.

---

### Post by CatKiller on 2021-03-19
> **TheFu said:**
> Development for X11 is winding down in favor of Wayland.

It's already stopped. All the devs that used to work on X said that they didn't want to do it any more, and only worked on Wayland. There hasn't been an X release for ages (even though changes have been made - mostly for XWayland) simply because no one will do it. XWayland (running applications that expect X, but on Wayland) has been separated out into its own thing, and that *will* get a release.

---

### Post by grahammechanical on 2021-03-19
Ubuntu has had an option to login in to Ubuntu on Wayland since Ubuntu 18.04 LTS. When Ubuntu 21.04 makes Wayland the default I would not be surprised if there was not an option to login to Ubuntu on X. 

As Wayland does the same or similar things that X does then surely Wayland must have the same authorisations as X now has, Unless we set a password in our BIOS/UEFI then the moment we switch on we are giving some computer code or other permission to run. And once we enter the password into the BIOS/UEFI we are giving a bootloader permission to run and the bootloader loads an operating system (Linux) which activates all kinds of stuff and not once does it require our permission until we get to the login screen. And even there we can set up automatic login.

I think it is possible to alter a setting in the BIOS/UEFI that will force Linux not to run even a line of code unless the Enter key has been pressed. and then we have to keep pressing the enter key to allow each line of code to be run.

If we are going to be that fussy then we should not be using a computer or any digital device.

Regards

---

### Post by maketopsite on 2021-04-05
> **TheFu said:**
> 

I've never seen X11 run without root, but I haven't looked too hard. It has been a known flaw for 25+ yrs on all X/Servers.



It is easy to run X11 under user account in some other mainstream distros - just use gdm3.

Wayland run under user account in Ubuntu 20.04 so I can use it instead of X11.

---

### Post by maketopsite on 2021-04-05
> **grahammechanical said:**
> Ubuntu has had an option to login in to Ubuntu on Wayland since Ubuntu 18.04 LTS. When Ubuntu 21.04 makes Wayland the default I would not be surprised if there was not an option to login to Ubuntu on X. 

As Wayland does the same or similar things that X does then surely Wayland must have the same authorisations as X now has, Unless we set a password in our BIOS/UEFI then the moment we switch on we are giving some computer code or other permission to run. And once we enter the password into the BIOS/UEFI we are giving a bootloader permission to run and the bootloader loads an operating system (Linux) which activates all kinds of stuff and not once does it require our permission until we get to the login screen. And even there we can set up automatic login.

I think it is possible to alter a setting in the BIOS/UEFI that will force Linux not to run even a line of code unless the Enter key has been pressed. and then we have to keep pressing the enter key to allow each line of code to be run.

If we are going to be that fussy then we should not be using a computer or any digital device.

Regards

I don't need to control every line of code to be run, I'm satisfied with average security reachable in a reasonable time.
As for other, it's answered in my previous post here.

Regards

---

### Post by maketopsite on 2021-04-14
Just in case someone is interested: new security vulnerability concerning Xorg under root: [https://ubuntu.com/security/CVE-2021-3472](https://ubuntu.com/security/CVE-2021-3472)

---

### Post by TheFu on 2021-04-14
> **maketopsite said:**
> Just in case someone is interested: new security vulnerability concerning Xorg under root: [https://ubuntu.com/security/CVE-2021-3472](https://ubuntu.com/security/CVE-2021-3472)

Perhaps I'm misreading, but I see a bunch of 
[LIST]
[*]Not vulnerable
[*]Does not exist
[*]Released (2:1.20.9-2ubuntu1.2~20.04.2) 
[/LIST]
in the resolution column.  Did I miss the point?

Normal X/Windows security applies.
* Only run X on trusted machines
* Remote X11 should be over ssh tunnels
* Don't allow remote X11 over UDP; never use xhost + (I've worked places where that was required).

If someone already has a login on the system, all bets are off. There are usually easier ways to get elevated privileges than through X.

---

### Post by maketopsite on 2021-04-14
> **TheFu said:**
> Perhaps I'm misreading, but I see a bunch of 
[LIST]
[*]Not vulnerable 
[*]Does not exist 
[*]Released (2:1.20.9-2ubuntu1.2~20.04.2) 
[/LIST]
in the resolution column.  Did I miss the point?

Normal X/Windows security applies.
* Only run X on trusted machines
* Remote X11 should be over ssh tunnels
* Don't allow remote X11 over UDP; never use xhost + (I've worked places where that was required).

If someone already has a login on the system, all bets are off. There are usually easier ways to get elevated privileges than through X.

It starts in a lower part of webpage (**[xorg-server]("https://ubuntu.com/security/cve?q=&package=xorg-server")**)

---

### Post by TheFu on 2021-04-14
> **maketopsite said:**
> It starts in a lower part of webpage (**[xorg-server]("https://ubuntu.com/security/cve?q=&package=xorg-server")**)

There aren't any unpatched for supported releases. 21.04 isn't released.  I'm still confused.
Actually, I'm more concerned about the network stack problems [https://arstechnica.com/information-technology/2021/04/100-million-more-iot-devices-are-exposed-and-they-wont-be-the-last/](https://arstechnica.com/information-technology/2021/04/100-million-more-iot-devices-are-exposed-and-they-wont-be-the-last/)  Need to patch the routers and dns systems here.

---

### Post by maketopsite on 2021-04-15
> **TheFu said:**
> There aren't any unpatched for supported releases. 21.04 isn't released.  I'm still confused.
Actually, I'm more concerned about the network stack problems [https://arstechnica.com/information-technology/2021/04/100-million-more-iot-devices-are-exposed-and-they-wont-be-the-last/](https://arstechnica.com/information-technology/2021/04/100-million-more-iot-devices-are-exposed-and-they-wont-be-the-last/)  Need to patch the routers and dns systems here.

Excuse me I wanted to mention the existence of vulnerability only. No word on whether it is patched or unpatched.

I'm sorry I can't assess severity of this network stack problems.

---

### Post by maketopsite on 2021-05-22
Ubuntu runs Xorg as user now, I don't know what caused that. Maybe some package upgrades ?

---

### Post by maketopsite on 2021-08-11
```
nvidia-drm.modeset=1
``` kernel boot parameter has made another Ubuntu 20.04 installation run Xorg under user account

---

