---
title: "Fastest Ubuntu to the running web browser"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by avnd on 2012-02-08
Hello.

I have a Pentium Dual Core with 1 GB of RAM. I'm looking for a variant that boots and gets me to Firefox/Chrome the fastest.

I can run the main Ubuntu with Unity on it. So, I'm not really looking for some Ubuntu which HAS to be a stripped-down version to be run on my machine. 

I read about Xubuntu being '**faster**' than Ubuntu-with-Unity and Lubuntu being even faster than Xubuntu. I understand that the term 'faster' implies as in the system being more responsive with less resources being hogged by the Desktop Environment. Can any one tell me if it translates to **quicker booting times**? Any link that compares the booting times of the lightweight versions of Ubuntu would be most welcome. 

I just want to switch on the machine (I have to do a lot of cold boots. So the Sleep Mode is not an option) and get to the functioning browser window fast. 

Thanks.

---

### Post by rudihawk on 2012-02-08
Crunchbang? -> that should be quite fast, it is based on Ubuntu as far as I know.

---

### Post by Cheesemill on 2012-02-08
> **rudihawk said:**
> Crunchbang? -> that should be quite fast, it is based on Ubuntu as far as I know.

It's actually based on Debian now, but it's still fast.

---

### Post by avnd on 2012-02-08
@rudihawk & cheesemill: Thanks for your replies, guys.

Can you comment on the booting times of Lubuntu and Xubuntu?

---

### Post by Paqman on 2012-02-08
Your actual DE only affects the final stages of your boot time. Shutting down services will probably shave a small amount of time off that, so anything that you don't use (eg: Bluetooth, printing, file sharing, etc) you could turn off.

Boot times are largely going to affected by how fast your drive is, and most of the components that have to get loaded are common to all the different versions, so don't expect huge differences. Generally speaking boot times have improved, but Oneiric has regressed a little.

If you really want to optimise your system it's much easier to start with the minimal image and only add what you need than it is to start with a fat image and remove what you don't. Check out the link in my sig for some help with that if you're interested.

---

### Post by Bodsda on 2012-02-08
Your choice of file system will also affect boot times, and probably your kernel version.
Ext4 filesystem currently boasts the quickest boot speeds as far as I know.

You could also disable some POST checks to shave a few extra seconds off.

Bodsda

---

### Post by I2k4 on 2012-02-09
I found this really informative:

[http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce](http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce)

---

