---
title: "Ubuntu freezes on Acer laptop"
date: 2019-02-16
forum: New to Ubuntu
---

### Post by aeroengineer on 2019-02-16
Hello everyone,
I have an acer aspire 7 A715-72G-79S1 and have recently installed Ubuntu alongside Windows 10. Overall the OS is running well, however I am experiencing a few problems.

1 - I cannot shut down the machine by pressing "poweroff" or by typing any commands into the terminal. The only way I can achieve this is either by holding down the power button and forcing it, or by gently rebooting using alt + prtscr + R + E + I + S + U + B and then going to windows from the boot menu and shutting down from windows. Alt + prtscr + R + E + I + S + U + O, which is supposed to shut it down rather than reboot, does not work.
2 - Sometimes when I try to power up, having logged in, the machine just displays the mouse pointer on the generic Ubuntu splash screen and never actually lets me into the system. So I have to turn it off, wait for about 20 seconds and restart it, hoping that it will not happen again.
3 - The machine sometimes freezes when I try to open settings, or account settings, or sometimes run programs I have downloaded from the internet (not from the Ubuntu store - that is running fine).

So those are the 3 main problems I am having.

I'd appreciate it if you could help me with this (and please bear in mind I am very new to Linux).

Thanks a lot :)

---

### Post by ubname on 2019-02-16
It *may* be a video card issue, what ubuntu and what video card are you using?

---

### Post by oldfred on 2019-02-16
Specs on that system show nVidia.
Did you install nVidia driver from Ubuntu repository or add ppa to get newer drivers?
If you installed incorrect or too old driver, you must purge that before installing correct driver as new does not uninstall old and you get conflicts.

        #What is installed:
dkms status
lsmod | grep nvidia
nvidia-smi 

 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

Default drivers:
ubuntu-drivers devices 

      # make sure system is up to date
sudo apt-get update
sudo apt-get upgrade 
# if you want very latest driver, which may be required if very new card/chip
   sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 

   # should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX

# If later you do not want ppa, how to uninstall ppa
sudo add-apt-repository --remove ppa:graphics-drivers/ppa

---

### Post by redpoppet on 2019-02-17
I'm no expert here but I have a couple of ACERs with win 10 that I intended to install ubuntu on.  I had all sorts of issues and the forums were all talking about a problem with the bios versions in these pcs.  The fix was to download bios firmware and take it back a couple of versions and then edit the config file to fix this.  I didn't bother with mine as the laptops are really surplus anyway.  But the symptoms you are reporting may be related to this.

I will also say that I had similar issues (not the power ones, but delays etc) and the problem there turned out to be a hd that was faulty.  May or may apply here but I replaced the hd and it fixed the problems.

I don't know if this helps, but there you have it :)

---

### Post by rraginggoblin on 2019-07-20
> **aeroengineer said:**
> Hello everyone,
I have an acer aspire 7 A715-72G-79S1 and have recently installed Ubuntu alongside Windows 10. Overall the OS is running well, however I am experiencing a few problems.

1 - I cannot shut down the machine by pressing "poweroff" or by typing any commands into the terminal. The only way I can achieve this is either by holding down the power button and forcing it, or by gently rebooting using alt + prtscr + R + E + I + S + U + B and then going to windows from the boot menu and shutting down from windows. Alt + prtscr + R + E + I + S + U + O, which is supposed to shut it down rather than reboot, does not work.
2 - Sometimes when I try to power up, having logged in, the machine just displays the mouse pointer on the generic Ubuntu splash screen and never actually lets me into the system. So I have to turn it off, wait for about 20 seconds and restart it, hoping that it will not happen again.
3 - The machine sometimes freezes when I try to open settings, or account settings, or sometimes run programs I have downloaded from the internet (not from the Ubuntu store - that is running fine).

So those are the 3 main problems I am having.

I'd appreciate it if you could help me with this (and please bear in mind I am very new to Linux).

Thanks a lot :)

Hi,
I experience exact the same situation on exactly the same computer. I removed Windows 10 completely however. Besides this, I changed the second harddisk to a ssd that gave no problems in another machine whatsoever. I have a couple of Linux installs with different distros on this second harddisk and experience these problems as well when booting from this second harddisk in any distro. So I conclude it is not the disk, not the Windows dualboot and not the distro. As this happens to me only two or three times a week and spending roughly 50 hours a week working with this machine, I consider this the price for going cheap and gave up hope to fix this. The logs show nothing either. The only thing I can recommend is to keep 15 seconds between gdm showing up and logging in and another 15 seconds after gnome showing the desktop before doing anything that requires network activity like starting your browser. This seems to reduce the number of freezes a bit. Definitely  the last acer for me.
Good luck

---

### Post by oldfred on 2019-07-20
Have you updated UEFI from Acer?
Note you probably have to redo any setting changes you made in UEFI.

My motherboard gives a list of changes I made which I copy and has screenshots. Before with my old BIOS system I had to take photos.

---

