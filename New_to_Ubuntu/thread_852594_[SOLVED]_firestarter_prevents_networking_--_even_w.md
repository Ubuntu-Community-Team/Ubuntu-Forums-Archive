---
title: "[SOLVED] firestarter prevents networking -- even when stopped or uninstalled!"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-07-07
I have an Ubuntu machine and a Windows Vista machine. I've used Samba to enable networking between the two machines.

However...

I've discovered, through trial-and-error, that firestarter is causing a problem.

When I reboot Ubuntu, the two computers cannot see each other.

But, if I start firestarter (System -> Administration -> Firestarter), then stop it ("Stop Firewall"), the computers can then see each other.

[LIST=1]
[*]I have to do this every time I reboot (start firestarter, then stop firestarter).
[*]I set firestarter not to start automatically (Preferences -> Firewall -> uncheck all options). That didn't help.
[*]Using Synaptic Package Manager, I uninstalled firestarter ("Mark for Complete Removal"). This also didn't solve the problem: In fact, I had to reinstall firestarter so that I could start it and stop it!
[/LIST]
Does anyone know what firestarter does to the system? I would like to uninstall firestarter and undo whatever it did, so that my Windows and Ubuntu machines can see each other.

---

### Post by tad1073 on 2008-07-07
try ```
 sudo iptables -F 
```
that will/should flush all the rules set by firestarter.

---

### Post by linux6994 on 2008-07-07
If you are running behind a router like Linksys or Netgear you should be safe without the file wall. Try this.
You can always install rcconf and then via the terminal window do"sudo rcconf" and deselect firestarter and it will not come up on the next boot.

---

### Post by cariboo on 2008-07-07
The way to stop the default firewall is to edit /etc/ufw/ufw.conf. Use your favourite editor eg:

```
gksu gedit /etc/ufw/ufw.conf
```

```
# /etc/ufw/ufw.conf
# 

# set to yes to start on boot
ENABLED=no
```

Just edit ENABLED=yes to ENABLE=no

That will stop the firewall from starting on boot up.

To stop the firewall without restarting in a terminal type:

```
sudo /etc/init.d/ufw stop
```

Jim

---

### Post by webofunni on 2008-07-07
I think the problem is not with the Firestarter but the underlying IPTABLES. 

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

You can check the current IPTABLES rules by following command : 

```
sudo iptables -L
```

That will list the current firewall rules. Please remove the rules which are causing the issue with samba. 

Post the resulting IPTABLE rules if you need any help :-)

---

### Post by Paddy Landau on 2008-07-07
Thank you all for your suggestions!

> **tad1073 said:**
> try ```
 sudo iptables -F 
```that will/should flush all the rules set by firestarter.

Yes, that did the job. I needed to reboot both the Ubuntu and Windows machines, and then it worked.


> **webofunni said:**
> ...
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
...

Thanks for that link. I was wanting something like that to sort out the firewall, as firestarter didn't work for my needs. I've bookmarked the link, and I shall inspect it carefully!

---

### Post by bodhi.zazen on 2008-07-07
> **cariboo907 said:**
> The way to stop the default firewall is to edit /etc/ufw/ufw.conf. Use your favourite editor eg:

```
gksu gedit /etc/ufw/ufw.conf
``````
# /etc/ufw/ufw.conf
# 

# set to yes to start on boot
ENABLED=no
```Just edit ENABLED=yes to ENABLE=no

That will stop the firewall from starting on boot up.

To stop the firewall without restarting in a terminal type:

```
sudo /etc/init.d/ufw stop
```Jim

LOL, that is the hard way

```
sudo ufw disable
```> bodhi@hardy:/$ sudo ufw disable
Firewall stopped and disabled on system startup

And to start :

```
sudo ufw enable
```for additional info on ufw :

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by Paddy Landau on 2008-07-07
> **bodhi.zazen said:**
> ... [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)
Thanks for the links.

---

### Post by bodhi.zazen on 2008-07-07
> **Paddy Landau said:**
> Thanks for the links.

NP

I find ufw is easy to learn and facilitates writing rules for iptables.

Once you get a set of tables built, 

```
sudo iptables-save > rules
```

Then to restore :

```
sudo iptables-restore < rules
```

Helpful for saving / backing up your tables once they become a little complex :)

---

### Post by Paddy Landau on 2008-07-08
> **bodhi.zazen said:**
> ```
sudo iptables-save > rules
sudo iptables-restore < rules
```

Cool. Thanks for that.

---

