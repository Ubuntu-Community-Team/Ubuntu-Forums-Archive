---
title: "acer aspire one problems..."
date: 2008-11-14
forum: New to Ubuntu
---

### Post by slammed87d21 on 2008-11-14
Well, where to begin. I gon a new Acer Aspire One a couple of weeks ago and I finally decided to put Ubuntu on it. To start, I followed the wiki word for word om how to install and set up my wireless. I talked to someone on IRC about the madwifi modules, and figured out the kernel wasnt new enough. so, i tried to upgrade it, but it says its already upgraded. whats worse is that this is my only computer at the moment so i have to switch between ubuntu and xp to get online. If anyone might have some advice or know what to do, I would appreciate anything very much. Thanks in advance.

---

### Post by ugm6hr on 2008-11-14
There are 2 different wiki entries for the Aspire One.

One for 8.10 (which is apparently recommended), and another for 8.04.

Tell us which you want / tried, and someone will point you in the right direction.

---

### Post by nothingspecial on 2008-11-14
Have you installed madwifi. Please post what you have done. There are 2 aspire ones in our house and wireless runs smooth as a sausage on both.

If you let us know what you`ve done, I can help.

---

### Post by slammed87d21 on 2008-11-14
> **nothingspecial said:**
> Have you installed madwifi. Please post what you have done. There are 2 aspire ones in our house and wireless runs smooth as a sausage on both.

If you let us know what you`ve done, I can help.


That will actually be hard to do as I have to reboot to you use WinXP to get online. I don't have any way to connect to my router right now except for wireless.


> **ugm6hr said:**
> There are 2 different wiki entries for the Aspire One.

One for 8.10 (which is apparently recommended), and another for 8.04.

Tell us which you want / tried, and someone will point you in the right direction.

I tried 8.04.1 to no avail.

---

### Post by slammed87d21 on 2008-11-14
Also, I am having the problems begin when I try to install Madwifi. In terminal, when I type wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz) , it says there is a problem getting the drivers and cancels. Is this something thats happened before?

---

### Post by nothingspecial on 2008-11-14
Get a wired connection then copy and paste these commands into your terminal.

Download madwifi.

```


wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz
```

Unzip it

```

tar -xvf madwifi-hal-0.10.5.6-r3861-20080903.tar.gz 
```


navigate to the extracted file

```
cd madwifi-hal-0.10.5.6-r3861-20080903
```

If you`ve not got the tools necessary for compiling get them


```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then compile it


```
sudo make
```



```
sudo make install
```

load the module


```
sudo modprobe ath_pci
```

make it load every time you boot

```
gksudo gedit /etc/modules
```

then copy and paste this to the bottom of that file
Code:
```

ath_pci
```

save
exit
reboot

---

### Post by ugm6hr on 2008-11-14
> **slammed87d21 said:**
> Also, I am having the problems begin when I try to install Madwifi. In terminal, when I type wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz) , it says there is a problem getting the drivers and cancels. Is this something thats happened before?

If you're not already online (with wired) - wget can't download the driver.

Hence the problem.

If you absolutely can't use a wired connection, it is still possible to install madwifi, with a little effort.

---

