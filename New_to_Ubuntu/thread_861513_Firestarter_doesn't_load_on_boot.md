---
title: "Firestarter doesn't load on boot"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by dumasb on 2008-07-16
Firestarter fails to load on boot.  I tried having it load by adding it to the services but it fails due to lack of root permissions.  Hence I load it manually.  Is there a way to get it to load automatically at boot?  Thanks in advance for any help.

---

### Post by adobrakic on 2008-07-16
idk if you'd want this, because it asks you for a password while booting up, anyway.

---

### Post by UbuntuNerd on 2008-07-16
someone  correct me if im wrong but if you installed firestarter it should be running when you first boot you may not see the gui for it but that doesn't mean is not running  you can check to see if is running with this command 

sudo /etc/init.d/firestarter status 

if you still want the gui for it when you boot try this



You might want to try these two steps to get firestarter to run under Gnome without it asking you for the root passwd.

1. run sudo visudo and add the following -
your username ALL=NOPASSWD:/usr/sbin/firestarter

2. Add the following to your startup programs in system - preferences - sessions
Order - 20 Command - gksudo /usr/sbin/firestarter

restart Gnome and it should startup the graphical firestarter without asking for a password.

---

### Post by coffeecat on 2008-07-16
Firestarter is only a graphical configuration utility for changing IPtables rules. IP Tables is the real firewall. If you installed firestarter through apt-get or Synaptic, the parts that need to start up on boot have already been configured for you. Don't try to do anything else. The fact that the GUI frontend isn't running doesn't matter. You only need it to change rules. For that you select it from System > Administration. There's a once-only wizard to run and that's it, unless you need to change any rules.

I can understand that it's rather alarming to see the panel icon for firestarter disappear from the panel when you close the firestarter Window. To the uninitiated it looks as though you have stopped the firewall. This is not so. The real firewall is still there.

However, this is all theoretical. My strong advice is to get rid of firestarter. It is a dead project, unmaintained for years now. There are bugs which will only get worse as further development of certain kernel modules and IP tables makes them deviate more from the versions that were current when firestarter was still being maintained.

Guarddog may be a better choice.

---

### Post by bodhi.zazen on 2008-07-16
you should run firestarter only to configure your firewall (iptables) then close it. Your firewall settings remain active even with a re-boot.

To see your settings, open a terminal and type :

```
sudo iptables -L
```

Second, ubuntu now uses ufw to configure iptables. Although a command line tool, it is a superior tool. I am sure a graphical interface to ufw is "in the works".

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by dumasb on 2008-07-16
> **jperez78 said:**
> someone  correct me if im wrong but if you installed firestarter it should be running when you first boot you may not see the gui for it but that doesn't mean is not running  you can check to see if is running with this command 

sudo /etc/init.d/firestarter status 

if you still want the gui for it when you boot try this



You might want to try these two steps to get firestarter to run under Gnome without it asking you for the root passwd.

1. run sudo visudo and add the following -
your username ALL=NOPASSWD:/usr/sbin/firestarter

2. Add the following to your startup programs in system - preferences - sessions
Order - 20 Command - gksudo /usr/sbin/firestarter

restart Gnome and it should startup the graphical firestarter without asking for a password.
Thanks for your input.  I did check the status after reboot and it said it was running.  However, it is unsettling to not have any indication what so ever.  I became concerned while watching the boot load and seeing apparmor failure to start firestarter during the boot.  I will try your gui hint tomorrow and perhaps that will set my mind at ease.  Again, thanks for taking the time to set me straight.

---

### Post by dumasb on 2008-07-16
> **bodhi.zazen said:**
> you should run firestarter only to configure your firewall (iptables) then close it. Your firewall settings remain active even with a re-boot.

To see your settings, open a terminal and type :

```
sudo iptables -L
```

Second, ubuntu now uses ufw to configure iptables. Although a command line tool, it is a superior tool. I am sure a graphical interface to ufw is "in the works".

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)
Thanks.  I looked at the iptables as you suggested but don't really know what I am looking at.  I did check the status as mentioned by jperez78 and confirmed that it is in fact running.

---

### Post by dumasb on 2008-07-16
I'll look into guarddog as you mentioned.  Thanks for your reply.

---

