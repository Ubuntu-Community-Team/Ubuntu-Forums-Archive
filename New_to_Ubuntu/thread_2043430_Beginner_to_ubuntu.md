---
title: "Beginner to ubuntu"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by cooldude786 on 2012-08-16
HI

I want to assign a static ip however when ever i use /etc/network/interfaces i get the error permission denied. I have also tried the comand with sudo nano. I am using ubuntu 10.04. Also when i use the command auto eth0 i get the error stating command auto not found. Please help as i am new to ubuntu and need help desperately. 

Thank you

---

### Post by ubudog on 2012-08-16
Hi, welcome to the Forums and to Ubuntu.  :) 

To set a static IP: 

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
Make a backup of /etc/network/interfaces in case something bad happens to the current one.

```
sudo nano /etc/network/interfaces
```
Enter your password, and then nano should open.

Assuming the network card you want to set the static IP on is **eth0**, select everything and press backspace.  Paste the following:
```

auto lo eth0
iface lo inet loopback
iface eth0 inet static
	address 192.168.1.101
	netmask 255.255.255.0
	gateway 192.168.1.1

```

This would set your IP to 192.168.1.101, your netmask to 255.255.255.0, and your gateway to 192.168.1.1, so change those as needed.

To save, type Ctrl+K+X.  Press y, then press enter.

After that, do:
```
sudo /etc/init.d/networking restart
```

The result should be:
```
*Reconfiguring network interfaces&#8230; [OK]
```

Now, type:
```
ifconfig
```

Under "eth0" you should see your new static IP.

- [Source]("http://www.howtoforge.com/linux-basics-set-a-static-ip-on-ubuntu")

Hope that helps,
ubudog

---

### Post by cooldude786 on 2012-08-16
Hi,

Thank you so much for your reply. After i entered the last command this is what i got: 


test@test-desktop:~$ sudo /etc/init.d/networking restart
[sudo] password for test: 
 * Reconfiguring network interfaces...                        /etc/network/interfaces:32: duplicate option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:32: duplicate option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                       [fail]command 

and after that i have lost my internet connectivity. What should i do now??? Please help!!!

Thanks

---

### Post by Cheesehead on 2012-08-16
You have a typo or other mistake on line 32 of /etc/network/interfaces.

Go back and edit the file again.
If you need help spotting the error, post the contents of the file here.

---

### Post by cooldude786 on 2012-08-16
Hi,

Thank you for the reply. I also wanted to ask does this ip address change after restarting the system??? if it does how can i make it permanet??? I would also like to know how can i use an external wireless USB adapter??? I have cisco linksys WUSB54GC. Also i need help in using my internal NIC as i am using xubuntu on VMware. I have intel wifi link 1000 bgn NIC. Please help!!!

Thank You

---

### Post by Cheesehead on 2012-08-17
> **cooldude786 said:**
> I also wanted to ask does this ip address change after restarting the system??? 

No. 'Static' means it won't change.


> **cooldude786 said:**
> I would also like to know how can i use an external wireless USB adapter???

This has been asked (and answered) many times. Here is a good example of how to do it: [http://ubuntuforums.org/showthread.php?t=2007475](http://ubuntuforums.org/showthread.php?t=2007475)

> **cooldude786 said:**
> Also i need help in using my internal NIC as i am using xubuntu on VMware. I have intel wifi link 1000 bgn NIC.

If your Xubuntu is the guest, setup as though it were a physical NIC, as described in the previous posts.

---

### Post by cooldude786 on 2012-08-19
Hi 

Thank you for your reply. I tried configuring the wlan0 as it was mentioned in the above link. However i get this error:

test@test-desktop:~$ sudo ifdown wlan0 && ifup wlan0
ifdown: interface wlan0 not configured
ifup: failed to open statefile /var/run/network/ifstate: Permission denied

Please tell me what should i do to resolve this???


Thank you

---

