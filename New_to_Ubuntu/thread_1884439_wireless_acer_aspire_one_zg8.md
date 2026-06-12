---
title: "wireless acer aspire one zg8"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by goeiezaak! on 2011-11-21
Hi, I am relativly new to ubuntu.

Wireless is not working on my acer aspire one zg8. 

It worked whenb I ad a dual windows xp and ubuntu 10.04 boot.

But when I removed windows and installed 10.11 it ceased working and even not enlighted when using the switch.


I searched for many solutions, I installed this properly:

[http://ubuntubasics.wordpress.com/2007/11/13/my-acer-wireless-doesnt-work/#comment-66](http://ubuntubasics.wordpress.com/2007/11/13/my-acer-wireless-doesnt-work/#comment-66)

than I made some other removals in terminal. But still it does not work. Any special software for zg8 needed?


Thanx in advance y'all!

---

### Post by sadaruwan12 on 2011-11-21
Hello, and welcome to the Forum.

Ok, let's try a temporary method if it works lets move to the permanent one.

I'm going to assume that you're using ubuntu 11.10 so here goes.

open the terminal by pressing "Ctrl+Alt+T" and type the below code.

```
$ sudo rmmod -f acer-wmi
```

you want see any out put after pressing enter, Let's move on

```
$ sudo rfkill unblock all
```

Now this,

```
$ rfkill list all
```

After pressing enter you'll see an out put with all the option on the out put will say "on" if that happens then you're good to go and see the wireless connection which you'll see activated and will be listing your wireless connection name.

If you manage to get it working please post back and I'll giveyou the steps  to make it permanent.

---

### Post by ceskopanjy on 2011-11-29
hi, i've the same problem of goeiezaak! and with your suggestions i get connected to my wireless network, but this is only temporary... how can i get it definitively?

---

### Post by ceskopanjy on 2011-12-07
nobody can help me?

---

### Post by goeiezaak! on 2011-12-10
Dear sadaruwan,

It works! 100.000 times thanks!


Excuze from my late reply. I assumed I would recieve an email after someone repleid but I didnt. This is why I am back after 2 weeks! In the mean time I also bought another usb wireless device. Have to sell that one now. heheheh stupid me..!


Gracias senior !

---

### Post by goeiezaak! on 2011-12-10
ceskopanjy I have the same problem. After restart it does not work. Nonetheless it's already a wonder it was working in the first place.

anyway, someone a solution for this? Thanks in advance!

---

### Post by goeiezaak! on 2011-12-10
> **goeiezaak! said:**
> $ sudo rmmod -f acer-wmi

the first line of code is enough to get it working again.

---

### Post by lemming465 on 2011-12-12
You can make that a permanent boot behavior by:```

sudo -i
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist-acer-wmi.conf
update-initramfs -u
```

---

### Post by goeiezaak! on 2011-12-13
Perfect, it works after start up! Great!

---

