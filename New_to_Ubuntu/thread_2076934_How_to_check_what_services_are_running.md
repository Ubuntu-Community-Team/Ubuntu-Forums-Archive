---
title: "How to check what services are running?"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by maglinu on 2012-10-27
I've been working my way down the basic security wiki [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) ,  and I came to this:

'Don't  run services you don't need.  Do you really need a VOIP phone system?  What about Secure Shell (SSH), Virtual Network Computing (VNC), Apache  server? If you need a service, make sure you understand it and can  properly secure it. You can't secure what you don't understand.  '

Seems like good advice (if you don't take it too literally - if I did I'd never turn the machine on).

But how do I find out what services are running?

Thanks

---

### Post by roger_1960 on 2012-10-27
Hi

Open a terminal CTR+ALT+T and type

> top

This shows a live listing of services.  Type Q to exit back to prompt.  You can kill a service by typing

> kill PID

where PID is given by the top command.  Have a read by typing

> man kill
and 
> man top

Roger

---

### Post by jerrrys on 2012-10-27
If you rather have a GUI to work with use [Gnome System Monitor]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=gnome+system+monitor&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

---

### Post by Lars Noodén on 2012-10-27
Most services have been migrated over to using Upstart scripts from the old System V init scripts.  You can find a list of services in the directory /etc/init/ where the service's configuration file will be there ending with .conf  All the services using upstart will be there.  The few remaining System V services will be in /etc/rc2.d/

You can see the status of any specific service by using the name of the like this:

```

service ufw status
service lightdm status
service atd status
# etc

```

top will only show those services that are consuming a lot of RAM or CPU.

A far as trimming it down, you can take away services you added yourself.  But there is not too much you can take away from the default install before things start to break.

---

### Post by stinkeye on 2012-10-27
I can't advise which services you can disable but on my machine I disabled bluetooth 
and cups as I dont have a printer.

Get a list of services...
```
initctl list | sort
```

To check the status of a service you can just use
status [COLOR="DimGray"]<service>[/COLOR]
eg
```
status bluetooth
```

Then I created an override file for the service with "manual" in the config
eg for bluetooth...
```
sudo sh -c "echo 'manual' > /etc/init/**bluetooth**.override"
```

and
for cups...
```
sudo sh -c "echo 'manual' > /etc/init/**cups**.override"
```

To restore a service just remove the corresponding .override file you created in **/etc/init/**

---

### Post by maglinu on 2012-10-27
Thanks to all.

I see a lot of things running that I can't yet really claim to know the purpose of, but the only things I put there are ddclient and freshclam, which I want. 

I think I'll leave well alone and move on to the next section of the wiki guide - this bit isn't perhaps so basic after all!

---

### Post by oldos2er on 2012-10-27
> **stinkeye said:**
> To check the status of a service you can just use
status [COLOR="DimGray"]<service>[/COLOR]
eg
```
status bluetooth
```

Then I created an override file for the service with "manual" in the config
eg for bluetooth...
```
sudo sh -c "echo 'manual' > /etc/init/**bluetooth**.override"
```

and
for cups...
```
sudo sh -c "echo 'manual' > /etc/init/**cups**.override"
```

To restore a service just remove the corresponding .override file you created in **/etc/init/**

I believe you can also run ```
sudo mv /etc/init/bluetooth.conf /etc/init/bluetooth.conf.disabled
``` and reboot to disable a service. Reversing the process would be ```
sudo mv /etc/init/bluetooth.conf.disabled /etc/init/bluetooth.conf
``` and reboot again.

---

### Post by maglinu on 2012-10-27
> **oldos2er said:**
> I believe you can also run ```
sudo mv /etc/init/bluetooth.conf /etc/init/bluetooth.conf.disabled
``` and reboot to disable a service. Reversing the process would be ```
sudo mv /etc/init/bluetooth.conf.disabled /etc/init/bluetooth.conf
``` and reboot again.

 Thanks for the info.  Just out of interest, is there any reason why these options would be preferred to just commenting the start line in the bluetooth.conf file, ie: 

# start on started dbus   

which was my first thought?

---

### Post by oldos2er on 2012-10-27
Well, a simple **ls /etc/init** will tell you which services are disabled, rather than having to check the contents of each *.conf file.

---

### Post by AlexDudko on 2012-10-27
You can also try **htop** which will be more informative than **top**.

---

### Post by stinkeye on 2012-10-27
> **oldos2er said:**
> I believe you can also run ```
sudo mv /etc/init/bluetooth.conf /etc/init/bluetooth.conf.disabled
``` and reboot to disable a service. Reversing the process would be ```
sudo mv /etc/init/bluetooth.conf.disabled /etc/init/bluetooth.conf
``` and reboot again.
By creating an override config, you can still start bluetooth manually
when needed with
```
sudo service bluetooth start
```

---

### Post by critin on 2012-10-27
> **maglinu said:**
> Thanks to all.

I see a lot of things running that I can't yet really claim to know the purpose of, but the only things I put there are ddclient and freshclam, which I want. 

**I think I'll leave well alone and move on to the next section of the wiki guide **- this bit isn't perhaps so basic after all!

Good idea!  

I've looked at System Monitor and noticed that things aren't using resources if you're not using them.  I figure the system knows more than I do about what is needed, so I leave it alone except for those extras that I know I don't use; bluetooth, etc. that starts at boot-up.

---

### Post by ThomasNovin on 2013-09-20
> **stinkeye said:**
> By creating an override config, you can still start bluetooth manually
when needed with
```
sudo service bluetooth start
```

Also, override file won't get overwritten/modified on upgrades etc. If edit a system file, that will/might happen.

So override file is much better!

---

### Post by VMC on 2013-09-20
> **stinkeye said:**
> By creating an override config, you can still start bluetooth manually
when needed with
```
sudo service bluetooth start
```
That's a good point. I always used added extension, and never thought I could restart with out removing the extension, by adding  override instead.
I'll have to try your method. Thanks.

---

