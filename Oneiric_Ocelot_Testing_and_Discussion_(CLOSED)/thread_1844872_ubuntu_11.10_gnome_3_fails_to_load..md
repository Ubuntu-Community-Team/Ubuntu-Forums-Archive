---
title: "ubuntu 11.10 gnome 3 fails to load."
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by odror on 2011-09-15
I have just installed ubuntu 11.10 beta with all the latest updates.

When I try to login to a gnome 3 session.

I get the error: Failed to load session "gnome"

I have installed gnome-shell


Thanks

---

### Post by MARP1961 on 2011-09-16
This worked for me in the recent past:

Login via Unity (default Ubuntu) then go to Synaptic Package Manager, search for Gnome Shell and mark it for 'reinstall'. Apply the change and reboot.

Remember all the updates and changes are bound to cause problems in a development release. It should work fine by release date.

---

### Post by odror on 2011-09-16
> **MARP1961 said:**
> This worked for me in the recent past:

Login via Unity (default Ubuntu) then go to Synaptic Package Manager, search for Gnome Shell and mark it for 'reinstall'. Apply the change and reboot.


It did not fix the problem. Any way do find why I have the problem?

---

### Post by sikander3786 on 2011-09-16
You need to install the proper 3D drivers before Gnome-Shell can actually run. Search the Dash for 'Additional Drivers' and activate the recommended drivers if available.

If running 11.10 in VirtualBox, you'll need to install the Guest Additions and then the VBox graphics drivers from the same 'Additional Drivers' jockey.

If you were running Unity 3D successfully, it means you've got the proper drivers already and Gnome-Shell should be running by now.

Just posted at the blog:

[http://www.tuxgarage.com/2011/09/ubuntu-oneiric-gui-options.html](http://www.tuxgarage.com/2011/09/ubuntu-oneiric-gui-options.html)

---

### Post by odror on 2011-09-16
> **sikander3786 said:**
> You need to install the proper 3D drivers before Gnome-Shell can actually run. Search the Dash for 'Additional Drivers' and activate the recommended drivers if available.

If running 11.10 in VirtualBox, you'll need to install the Guest Additions and then the VBox graphics drivers from the same 'Additional Drivers' jockey.

If you were running Unity 3D successfully, it means you've got the proper drivers already and Gnome-Shell should be running by now.



Unity 3D is working. I have NVIDIA driver (GTX 550 ti). I have the proprietary drivers. Initially it complained about no having a good video driver. Then when I removed the gnome-fallback package I got the error above.

---

### Post by sikander3786 on 2011-09-16
> **odror said:**
> Unity 3D is working. I have NVIDIA driver (GTX 550 ti). I have the proprietary drivers. Initially it complained about no having a good video driver. Then when I removed the gnome-fallback package I got the error above.
Can you please post the output of this command, just to be sure...:

```
sudo lshw -c video
```

---

### Post by odror on 2011-09-16
> **sikander3786 said:**
> Can you please post the output of this command, just to be sure...:

```
sudo lshw -c video
```

  *-display               
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f8000000-f9ffffff memory:d8000000-dfffffff memory:d4000000-d7ffffff ioport:ec00(size=128 ) memory:fbe00000-fbe7ffff

---

### Post by sikander3786 on 2011-09-17
You seem to have the proper driver already installed. I've got no further thoughts excepts trying to purge and re-install gnome-shell package:

```
sudo apt-get purge gnome-shell
sudo apt-get install gnome-shell
```

---

### Post by odror on 2011-09-17
> **sikander3786 said:**
> You seem to have the proper driver already installed. I've got no further thoughts excepts trying to purge and re-install gnome-shell package:

```
sudo apt-get purge gnome-shell
sudo apt-get install gnome-shell
```
Thanks for helping, but it did not fix the problem. There is something else that gnome 3 needs that is not working in my computer

---

### Post by Spr0k3t on 2011-09-17
Just popping in to this thread saying it helped me get gnome-session-fallback working in VBox with 11.10.

Need the vbox guest additions, reload gnome-shell, install gnome-session-fallback.  Done.

---

### Post by odror on 2011-09-17
> **Spr0k3t said:**
> Just popping in to this thread saying it helped me get gnome-session-fallback working in VBox with 11.10.

Need the vbox guest additions, reload gnome-shell, install gnome-session-fallback.  Done.

Ok I did install the gnome-session-fallback. I do not get the error anymore. When I login to gnome 3 after some delay it logs in to unity 3d like desktop. But the system info shows Gnome version 3.1.91 and experience is fallback v.s. ubuntu unity with a standard experiences. How do I get a different more interesting experience than unity.  Thanks

---

### Post by Spr0k3t on 2011-09-20
> **odror said:**
> Ok I did install the gnome-session-fallback. I do not get the error anymore. When I login to gnome 3 after some delay it logs in to unity 3d like desktop. But the system info shows Gnome version 3.1.91 and experience is fallback v.s. ubuntu unity with a standard experiences. How do I get a different more interesting experience than unity.  Thanks

On the login screen, use the cog to change the settings to boot into gnome classic.  I'm sure there's a way to make that the default, just haven't found it yet.

---

### Post by Harry33 on 2011-09-20
> **odror said:**
> Ok I did install the gnome-session-fallback. I do not get the error anymore. When I login to gnome 3 after some delay it logs in to unity 3d like desktop. But the system info shows Gnome version 3.1.91 and experience is fallback v.s. ubuntu unity with a standard experiences. How do I get a different more interesting experience than unity.  Thanks

In a default Oneiric setup, Gnome-shell (which is the default Gnome 3 DE) should work. All you have to do is to install package gnome-shell with all its dependencies.
Then from display manager (LightDM) choose session "Gnome".
If you have troubles with 3D, your system will choose the 2D session (gnome-fallback = Gnome-panel = Ubuntu Classic).

If you have all this in order, there may be another problem around, like xserver.
Do you use any additional PPA's?
For example, using xorg-edgers PPA right now will get you into trouble with both Gnome-shell and Unity3D.

---

### Post by odror on 2011-09-20
I do not have any ppa packages. I have installed gnome-shell. it looks like unity 3d. is there any setup that i need to change.

---

### Post by Harry33 on 2011-09-20
> **odror said:**
> I do not have any ppa packages. I have installed gnome-shell. it looks like unity 3d. is there any setup that i need to change.

What diplay manager are you using?

---

### Post by odror on 2011-09-20
> **Harry33 said:**
> What diplay manager are you using?
I think that I am using GDM.

ps -aux | grep gdm 

> root      2906  0.0  0.0 152836  2848 ?        Ssl  Sep18   0:00 gdm-binary
root      5749  0.0  0.0 166792  3684 ?        Sl   Sep18   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      5751  2.1  0.7 200512 69864 tty8     Ss+  Sep18  58:28 /usr/bin/Xorg :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-xBQdPH/database -nolisten tcp
root      5820  0.0  0.0 190592  3372 ?        Sl   Sep18   0:00 /usr/lib/gdm/gdm-session-worker


---

### Post by Harry33 on 2011-09-20
> **odror said:**
> I think that I am using GDM.

ps -aux | grep gdm

You could try installing LightDm and configuring it as a default display manager.

---

### Post by JonM33 on 2011-09-20
> **odror said:**
> I have just installed ubuntu 11.10 beta with all the latest updates.

When I try to login to a gnome 3 session.

I get the error: Failed to load session "gnome"

I have installed gnome-shell


Thanks

Gnome Shell is still buggy at best. I'd avoid it for a bit. Unity works. Use that.

---

### Post by odror on 2011-09-20
> **JonM33 said:**
> Gnome Shell is still buggy at best. I'd avoid it for a bit. Unity works. Use that.
I cannot use Unity. I'll keep using kde until gnome is fixed.

---

### Post by Harry33 on 2011-09-21
> **JonM33 said:**
> Gnome Shell is still buggy at best. I'd avoid it for a bit. Unity works. Use that.

I do not think this issue is about gnome-shell generally.
I have three setups where gnome-shell and gnome-panel (fallback) are the only DE's.
One of them has Ricotz Testing PPA.
None of them have problems concerning booting, display manager nor gnome-shell.

---

