---
title: "how do I remove xwindows/display managers, gdm, lightdm, etc?"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by kyooball on 2011-11-02
I simply want a headless server running Ubuntu.. with no xwindows or gdm or lightdm running.. how can I prevent that from booting up automatically?  I just installed ubuntu 11.10.. this is my first ubuntu release ever.. converting from redhat/fedora.. after googling for literally an hour, I still can't get any commands I found to cause xwindows to not start up automatically after a reboot!  One would think it woudln't be so hard to figure out for a seasoned linux administrator...

thanks in advance.

---

### Post by haqking on 2011-11-02
> **kyooball said:**
> I simply want a headless server running Ubuntu.. with no xwindows or gdm or lightdm running.. how can I prevent that from booting up automatically?  I just installed ubuntu 11.10.. this is my first ubuntu release ever.. converting from redhat/fedora.. after googling for literally an hour, I still can't get any commands I found to cause xwindows to not start up automatically after a reboot!  One would think it woudln't be so hard to figure out for a seasoned linux administrator...

thanks in advance.

if you are a seasoned Linux Admin why did you install a Desktop edition ?

the easiest way is to install Ubuntu server which has no gui ;-)

otherwise you need to create a lightDM.override file or GDM.override depending on what DM you are using.

example as 11.10 uses LDM

```
echo 'manual' | sudo tee /etc/init/lightdm.override
```

and edit grub to have GRUB_CMDLINE_LINUX_DEFAULT="quiet"

and then update grub

---

### Post by kyooball on 2011-11-02
Thank you..  I guess I was expecting an option to not install xwindows during the installer process.. I simply went to ubuntu's website and downloaded the 64bit iso.. didn't realize it said "desktop" vs "server".. I'm downloading the server version now and I'll restart..  I do appreciate your response..   I need to find a "ubuntu for redhat/fedora dummies" FAQ..  anything like that exist?

---

### Post by haqking on 2011-11-03
> **kyooball said:**
> Thank you..  I guess I was expecting an option to not install xwindows during the installer process.. I simply went to ubuntu's website and downloaded the 64bit iso.. didn't realize it said "desktop" vs "server".. I'm downloading the server version now and I'll restart..  I do appreciate your response..   I need to find a "ubuntu for redhat/fedora dummies" FAQ..  anything like that exist?

If you use to use fedora/Red hat you wont notice much difference with no GUI.

It is all linux, of course you wont be using YUM or RPM anymore...other than that from CLI all you need is

```
man
```

```
apropos
```

Everything else you will figure out

---

