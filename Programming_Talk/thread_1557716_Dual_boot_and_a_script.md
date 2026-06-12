---
title: "Dual boot and a script"
date: 2010-08-21
forum: Programming Talk
---

### Post by Unterseeboot_234 on 2010-08-21
Hello, brand new hardware that came with Windows 7. I like Win7 to bridge some programming and hardware issues (but Ubuntu lets you code faster, by far). 

Anyway, here's my problem. I put Ubuntu 10.04 on its own SATA and left Win7 on its original SATA drive. GRUB works great with one issue -- the clock in the Taskbar of Win7 gets thrown off by 2 hours from a cold boot, and loses minutes when Win7 is sleeping. Here is the Ubuntu Help documentation describing this issue...

**[[COLOR="RoyalBlue"]Ubuntu Time[/COLOR]]("https://help.ubuntu.com/community/UbuntuTime")**

The Help doc suggestion is to either hack the Windows Registry, or to patch the Linux kernel. Both of which I would really rather not do considering the long-term upgrades both OS will be installing during their lifetimes. A script would carry forward, untouched by upgrades and be editable.

So, anybody have any experiences using Windows Script Host, invoking a script at startup, and making it click a button in a dialog box? Windows 7 has a dialog to seek scientific web pages for official time and synchronizes Windows' idea of time.

I would prefer Perl as the language. Or, am I looking at something monoDEV or what?

Thanks, in advance, for any ideas...

---

### Post by Unterseeboot_234 on 2010-08-21
I found this...

Windows Vista and XP-64 had big-time problems keeping time as a Windows-only box (and as far as I'm concerned the tradition continued with Windows 7). In Windows 7 is a dialog for 'Internet Time Settings' and it fetches from scientific clock sites. The dialog is like 12 button clicks to achieve one result. And then there is cmmd-prompt.

The Windows program name is w32tm. The function call is /resync. Windows has a new cmmd-prompt called administrative mode (their idea of 'sudo'). Start->Command Prompt, right-click->Run as Administrator...

```
C:\Windows\system32>[COLOR="Red"]w32tm /resync[/COLOR]
Sending resync command to local computer 
The command completed successfully.

C:\Windows\system32>
```

The Windows Administrative command-prompt is cmd.exe.

To use Perl I would have to install ActiveState perl on the Win7 drive. Maybe a batch script then, or VB. Perl would allow admin privileges.

If nobody has any ideas, then this post might help you with a dual-boot install. Hackinig Win's registry or patching 'nix's kernel is wrong IMHO.

---

