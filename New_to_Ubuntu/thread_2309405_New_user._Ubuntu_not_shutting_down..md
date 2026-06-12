---
title: "New user. Ubuntu not shutting down."
date: 2016-01-10
forum: New to Ubuntu
---

### Post by Archit_Mathur on 2016-01-10
Kindly please help, I am new user to ubuntu and my laptop hangs at shutdown screen. 
Restart is working fine. I have tried all possible solutions but still the problem is occurring.
Please help.

---

### Post by blade4 on 2016-01-10
Hi and welcome to ubuntuforums. 

Can you let us know your laptop model and specifications ? Also, which version of ubuntu are you running ? 

Lastly, can you give more details on which solutions you have tried thus far ?

---

### Post by Archit_Mathur on 2016-01-10
Lenovo ideapad-Z570
Processor - Intel® Core&#8482; i5-2430M CPU @ 2.40GHz × 4 
Graphics - GeForce GT 520M/PCIe/SSE2
os type - 64-bit
Ubuntu 14.04 lts
Solutions tried:
[COLOR=#000000]1.
sudo apt-get update[/COLOR]
[COLOR=#000000]sudo apt-get install --reinstall ubuntu-desktop[/COLOR]
[COLOR=#000000]sudo apt-get install unity[/COLOR]
2.

[LIST=1]
[*]sudo -i (to get a root shell, sudo gedit is not recommended)
[*]gedit /etc/default/grub
[*]Find the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[*]Change this to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
[*]Save the file and close the file.
[*]Finally, in terminal: update-grub
[*]exit (to end the root shell)
[/LIST]

---

### Post by blade4 on 2016-01-10
This is a way to shutdown the system from the terminal . Try it and see if it works : 

```
sudo shutdown -h 0
```

Also, try updating the system : 

```
 sudo apt-get update && sudo apt-get upgrade 
```

---

### Post by Archit_Mathur on 2016-01-10
Still the same problem laptop hangs at the shutdown screen and does not power off.
Tried both the solutions.
Is there any other way ?

---

### Post by grahammechanical on 2016-01-10
I would just like to make a point.

Grub is the Linux boot loader. It has everything to do with loading Linux/Ubuntu bit nothing to do with shutting down Linux/Ubuntu. If Ubuntu is loading fine, then why make changes to the settings of the boot loader? Once Linux starts to load, Grub is no longer in control of anything.

Much the same can be said for re-installing Ubuntu desktop & Unity. You will notice that when we select Shut Down from the power/cog menu & confirm the shut down that the user interface (Unity) is the first to disappear. It is Linux that is shutting down and for some reason failing to power off the motherboard.

What happens when you try Restart? Does that actually power down the motherboard and then restart with the motherboard POST and the Grub boot loader menu?

Regards

---

### Post by Dennis N on 2016-01-10
If you mean shutdown splash screen, try pressing ESC key to exit the splash and see if any messages show that might indicate what the system is up to.

---

### Post by Archit_Mathur on 2016-01-10
It works fine when i restart.
It does power down motherboard.

When i press ESC the end message it shows is:
Unmounting local file system
Will now halt

---

### Post by blade4 on 2016-01-10
The info from this link may help . ( post #17 by cyberwizard2 )  : [http://ubuntuforums.org/showthread.php?t=2220591&page=2](http://ubuntuforums.org/showthread.php?t=2220591&page=2)

Try the solution only if the kernel oops report shows some problem as mentioned in the post

---

### Post by Archit_Mathur on 2016-01-10
Nothing is happening when i am using the following command:
dmesg | grep -i oops

---

### Post by Archit_Mathur on 2016-01-14
Please someone help me.

---

### Post by rakesh_kumar5 on 2016-01-15
if you bought a new machine and you notice that your Linux  distribution hangs at the very end of the reboot/shutdown process, upon  giving any of the following commands: and this instruction may be beneficial for you

 # shutdown -r now
# shutdown -h now
# reboot
# halt
# poweroff
# Ctrl+Alt+Del

Working at [Cloudwalk hosting LLC ]("http://www.cloudwalks.com/quickbooks-hosting.html")

---

### Post by Edward_Fish on 2016-01-15
I had a similar issue on an old computer I installed Ubuntu on. I think it was something to do with the WiFi drivers not working correctly.
Have you been having any problems with WiFi?
I seem to remember I fixed it by apt-get purging some package, but I have no clue which one it was.

---

### Post by DuckHook on 2016-01-16
> **grahammechanical said:**
> Once Linux starts to load, Grub is no longer in control of anything.Hi grahammechanical,

You are of course correct that GRUB is long gone by the time shutdown occurs. However, it does influence how the system is set up for the entirety of the computing session. Some MBs report non-standard ACPI info which then makes Ubuntu think that ACPI is not supported. By setting the acpi=force parameter in GRUB, Ubuntu will force-load the ACPI modules anyway and such MBs can sometimes be made to work without further tinkering. In the OP's case, this workaround does not seem to work.

@Archit_Mathur,

Based on this:> When i press ESC the end message it shows is:
Unmounting local file system
Will now halt...it seems that your system does successfully reach the halt state. This means that all file systems are unmounted and there's no danger of corrupting them with a manual poweroff. It's just that your system does not go that very final step to powering off. However, you can manually press the power button until your system shuts down without any fear that you've left mounted file systems in an open state.

The really sticky situations are those where the shutdown process gets hung up because an obscure system process won't die. The system waits interminably for the kill confirmation signal from that process and never shuts down. The last time this happened to me was with an improper WIFI driver that couldn't quite access my WIFI chip properly. I also used to get this symptom quite often when an NFS share would try initiating before my network was up. Such processes launch, can't do what they are intended to do, and then just endlessly loop while gumming up the works, including the shutdown.

This is not what's happening with you. Be thankful for that because such problems are notoriously difficult to diagnose and fix. Moreover, they make pulling the plug a very dangerous tactic because you *could* still have disks mounted and files open, in which case, data corruption is a real danger.

In your case, the system has indeed halted. Your standard output won't say that unless it's happened. Your only issue is the inconvenience of having to hold the power button for ten seconds, or whatever interval is necessary to force poweroff.

Due to the variety of HW out there, Ubuntu does not always send the signal that the MB expects in order to proceed to physical poweroff. There's no way to fix this in some HW except to:

1. Wait until the kernel developers get around to accommodating that wonky MB in a kernel update, or
2. Google the problem and patch your kernel to recognize the MB so that ACPI works. This last is a highly technical fix and is not recommended for anyone but masochists or super-geeks.

If it were me, I'd just live with having to physically power off the machine.

---

