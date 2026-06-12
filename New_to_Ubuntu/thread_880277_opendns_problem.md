---
title: "opendns problem"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by sharks on 2008-08-04
i have followed the guide given in opendns.com. i save it and it works. but when i reboot next time the settings are changed. what to do to make it work all time?

---

### Post by ibuclaw on 2008-08-04
Which guide would that be? and on which Device?

You have to change the DNS settings in the router you are using to get OpenDNS to work all the time. Do you not?

Regards
Iain

---

### Post by sharks on 2008-08-05
its the guide given on opendns for ubuntu. i made all the changes necessary for using opendns but still cant get that to work.

---

### Post by Bachstelze on 2008-08-05
Which changes did you make?

---

### Post by sharks on 2008-08-05
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

### Post by kpkeerthi on 2008-08-05
> **sharks said:**
> i have followed the guide given in opendns.com. i save it and it works. but when i reboot next time the settings are changed. what to do to make it work all time?

See [https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

---

### Post by Joeb454 on 2008-08-05
It works for me. I've done it a few times on my laptop

---

### Post by sharks on 2008-08-05
> **Joeb454 said:**
> It works for me. I've done it a few times on my laptop

Thats the prob. it works for u and doesnt for me.

---

### Post by Joeb454 on 2008-08-05
:lolflag:

Are you sure you followed the instructions 100% correctly? i.e. editing the files etc.

---

### Post by sharks on 2008-08-05
yes it works first time and when i reboot the system i fails to use.

---

### Post by kpkeerthi on 2008-08-05
> 
To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

... from [https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

Did you remember to complete the above steps?

---

### Post by sharks on 2008-08-05
Just now started from scratch . saved and rebooted my modem. it worked. and i rebooted my sys and just not working.....

---

### Post by sharks on 2008-08-05
i think its better not to use opendns.

---

### Post by Joeb454 on 2008-08-05
Not at all.

If your router supports it, you could try doing it that way.

I don't know why it won't work on your machine though, especially if you're following those instructions exactly :confused:

---

### Post by Vishal Agarwal on 2008-08-05
append these three following lines in your /etc/dhcp3/dhclient.cong

> 
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit

Then reboot the system it should work.

---

### Post by Bachstelze on 2008-08-05
> **Joeb454 said:**
> I don't know why it won't work on your machine though, especially if you're following those instructions exactly :confused:

After you think about it a bit, the answer will be clear ;) If the conclusion is wrong but the reasoning is right, it meas at least one of the premises was wrong.

---

### Post by Mud.Knee.Havoc on 2008-08-06
> **Vishal Agarwal said:**
> append these three following lines in your /etc/dhcp3/dhclient.cong



Then reboot the system it should work.

That won't work at all.  /etc/dhcp3/dhclient.conf not cong
:)  

And you only need to append the line without the #.

---

