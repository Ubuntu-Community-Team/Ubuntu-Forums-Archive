---
title: "Desktop Doesnot Shutdown/Poweroff!!!"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by G_Ajith_Kumar on 2014-02-12
I am running Ubuntu 13.10/14.04 on a HP Laptop Intel® Celeron(R) M CPU 420 @ 1.60GHz, 32-bit; Memory 2.0 GiB; Intel® 945GM x86/MMX/SSE2 Graphic Card.

After installing 13.10 and the upgrade to 14.04, the system does not power off at all i.e. even with terminal command or by clicking the "shutdown" button on the top right 'System' icon drop down menu.

The system closes all activities and a Ubuntu emblem/ensign comes up with dots in a row changing colour from white to red in sequence..like in the starting screen. It remains like that and I have to power down the system with the Power Button pressed for about 6 seconds.

The system has confirmed that I have the latest driver for the Intel graphic card.

I have done a research and did find some threads on it. I tried reconfiguring the Grub file etc but to no avail.

Help!!!!!!!!!!!!!!! Thank you for your time and effort in advance! :)

---

### Post by sudodus on 2014-02-12
Welcome to the development branch :smile:

Lubuntu 14.04 has two more months of development until it will be  released. You can expect many things to break during this interval. You  can help the developers make it work with your hardware, if you report  your results at the testing tracker

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

and write a bug report at Launchpad

[https://launchpad.net/](https://launchpad.net/)

-o-

If you need a working system, I suggest that you install the current released version, Lubuntu 13.10 again. Unfortunately there is no easy way to downgrade from a newer version to an older one.

---

### Post by grahammechanical on 2014-02-12
> [COLOR=#000000] I tried reconfiguring the Grub file etc but to no avail.[/COLOR]

I am concerned by that statement. The Shutdown process has nothing to do with the Grub boot menu. Neither does the Restart process. You could end up being unable to boot Ubuntu. And I do not think that this problem has anything to do with the video driver. Daily updates may solve the problem, eventually.

What terminal command did you use? Is it the correct command?

I have found that

```
sudo shutdown -h now
```

usually works to shutdown. Or

```
sudo shutdown -r now
```

to Restart.

Sometimes Ctrl+Alt+Del works. But there have been times when there is no option but to power off at the power button. This is what sometimes happens when we run the development release of Ubuntu.

Regards.

---

### Post by marco-parillo on 2014-02-12
First, if you are using the 14.04 daily builds (I am on Kubuntu Alpha-2, with all patches applied), you may want to have this posting on the U+1 forum.
Second, if you could include a comment linking from your bug report to:
[https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1272687](https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1272687)
I would appreciate it.

---

### Post by G_Ajith_Kumar on 2014-02-12
I am overwhelmed by the replies. Thank you all very much. :)

@sudodus I will act on what you have said and send those reports as soon as possible. i am new so i will need to read understand and implement..But certainly will give it a good try.

@grahammechanical i have tried both those commands from terminal with no effect...it still finally hangs.

Finally, I do have feeling this probably cropped up after I changed from dual boot (Windows 7 and Ubuntu 12.04) to only 12.04. this problem has been reported by many.

[http://askubuntu.com/questions/122933/dell-studio-1569-cannot-shutdown-in-ubuntu-11-10-or-12-04](http://askubuntu.com/questions/122933/dell-studio-1569-cannot-shutdown-in-ubuntu-11-10-or-12-04)

Extract from the same

[TABLE]
[TR]
[TD="class: postcell"]                I have not tried a version of Ubuntu prior to 11.10 on my machine.

  The laptop will not shut down or restart. Shutting down causes it to  pause at "Will now Halt", where upon it sits until the battery dies.  Restarting causes a similar problem, the machine never completely turns  off. The screen is still on, the hard drive continues to run, everything  is still on.
  It is a similar problem to an unresolved issue posted over at the Ubuntu Forums: [http://ubuntuforums.org/showthread.php?t=1951446](http://ubuntuforums.org/showthread.php?t=1951446)
      
     

      [/TD]
[/TR]
[TR]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD="class: answercell"]**Extract from that Thread**

I fixed the problem.
  

  Because of this, you have to open up the grub configuration file and add the property acpi=force.
  gksu gedit /etc/default/grub
  Once there, find where it says, GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
  Change this to read:
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
  Save it, then run this command to update your grub configuration.
  sudo update-grub
  Finally, reboot, and your machine should now be able to shutdown and reboot without correctly!




      [/TD]
[/TR]
[/TABLE]
Another discussion on a similar problem.....[http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer](http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer)

---

### Post by G_Ajith_Kumar on 2014-02-12
Sorry. I think the post is quiet miserable looking. Do better next time.

---

