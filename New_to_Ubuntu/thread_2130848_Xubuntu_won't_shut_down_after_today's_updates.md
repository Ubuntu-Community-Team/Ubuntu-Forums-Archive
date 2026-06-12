---
title: "Xubuntu won't shut down after today's updates"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by Autodave on 2013-03-30
Downloaded and installed about 20 updates today.  After installing, it said that a restart was needed to finish.  I clicked to restart and everything was fine: shut-down and restarted.  However, since then, when I try to shut i down, I get the text on the screen that says something to the effect that it is waiting for remaining processes to stop (like it has always said), and then the Xubuntu screen comes back up (like always), but that where it stays: it never shuts down: I have to hit the power button to shut it off.

I am running Xubuntu 12.04 on a desktop, 3 gig RAM, 2.8 dual core.

---

### Post by kc1di on 2013-03-30
please go to a terminal and issue the following command and list any error messages you receive here.
```
sudo shutdown -h now
```

---

### Post by DuckHook on 2013-03-30
Do what *kc1di* suggests first, but if it tells you nothing, then hitting the <Esc> key during the shutdown process should get you out of the Xubuntu overlay screen so that you can see the progression of processes that are shutting down. This should also let you see which process the shutdown process hangs on. You will have to write down and manually type in any error messages, but there's no helping this because there is no way to log shutdown problems after the logging service itself has been shut down.

BTW, rather than just pulling the plug on a balky machine, try to use the REISUB procedure instead. This consists of holding down the <Alt>+<SysRq> buttons at the same time as you cycle through the letters REISUB. This procedure closes off all open files/services/daemons and performs an orderly shutdown that won't leave you with filesystem corruption.

<edit>
Please also use:```
sudo shutdown -P now
```The -P switch will actually power down your box whereas the -h switch just halts the OS (but could leave the power on in some systems). Your system could actually be ready to turn off, having proceeded to a halt state, but not have received the power-off signal.
</edit>

---

### Post by AKusr on 2013-04-26
I am having the same problem with my laptop.    It will not power off when shutting down.  I modified grub so I could see the verbose text messages, and the shutdown completes through "halt", but doesn't power off.  The result is the same if I use the command "sudo shutdown -P now".

I installed Xubuntu 12.04 from installation CD without internet  connected (so no auto updates during install).  Played around with it  some and everything seemed OK.  Then I connected to internet and updated  the system.  Since this is a relatively fresh install, I only have two kernels:  3.2.0-29 (from the install CD) and 3.2.0-40 (from recent update).  When I boot to the -29 kernel, shutdown is normal.  When I boot to the -40 kernel, it will not power off.

Is there something I can do to make shutdown work with the updated kernel?

---

