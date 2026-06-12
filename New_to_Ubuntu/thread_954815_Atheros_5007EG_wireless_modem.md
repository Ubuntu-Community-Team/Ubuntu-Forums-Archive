---
title: "Atheros 5007EG wireless modem"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Carnivorum on 2008-10-21
Bs'd

I followed  the instructions on this page: [http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

There is says:

1. Open you terminal

2. Get this version of madwifi:

    wget -c [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

3. Untar the downloaded package:

    tar xvf madwifi-ng-r2756+ar5007.tar.gz

4. Get inside the unpacked directory:

    cd madwifi-ng-r2756+ar5007

5. If you haven’t compiled anything from source before on your linux then you propably need the build essential package:

    sudo apt-get update && sudo aptitude install build-essential

6. Now you can build your madwifi and install the modules:
make

    sudo make install
    sudo modprobe ath_pci
    sudo modprobe wlan_scan_sta

The last 2 commands can cause some complications on some systems. If they do check your System >> Administration >> Restricted Drivers Manager and disable atheros here. Then try again.

7. Now restart your computer and you should be able to see any aviable networks in your Network Manager.

Everything goes well, until the command: "sudo make install"
Then I get the reaction:  make: *** No rule to make target `install'.  Stop.

What to do about that one?


Carni

---

### Post by Trebaruna on 2008-10-22
On a slightly unrelated note: my AR5007EG is working just fine on intrepid, which should hit release candidate tomorrow.
Just disable Atheros from the restricted drivers and it should work.

Back to the problem at hand: my installing from source is a tad rusty, but I'm pretty sure you're supposed to issue the command "make" before running "sudo make install".
EDIT: Ah, make is there, the newlines are a bit wonky. Well, then I'm afraid I don't really know...

Also, for easy de-installation, instead of "sudo make install" do "sudo checkinstall make install". This requires the packages checkinstall. What this does is compile the source, make it into a .deb file and then install it. That way you can use Synaptic or apt-get to remove the driver if you want. It also means you can store the .deb file for easy re-installation later if you need it.

---

### Post by Carnivorum on 2008-10-22
Bs'd

Thanks,  I think I wait to the end of the month, download the new version, and hopefully then it will work.


Eliyahu

---

### Post by Carnivorum on 2008-11-01
Bs'd

I upgraded to 8.10, but my Atheros 5007EG wireless modem still doesn't work. 

How can i get it working?

Carni

---

### Post by bumanie on 2008-11-01
I got a atheros AR242x wi-fi card going by using ndiswrapper.[ Look here.]("http://ubuntuforums.org/archive/index.php/t-766169.html")

---

### Post by Carnivorum on 2008-11-01
Bs'd

It says there:  

anyway, to make it work:

- disable both restricted drivers in System > Adminstration > Hardware drivers

- install ndiswrapper in the add/remove window

- download the .inf from the XP driver at : [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)

- open a terminal and type this command : sudo ndisgtk

- select the net5211.inf file and "enter"

- it should now work

When I downloaded [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz),  do I then have to untar it?

If so, how do  I do that?


Carni

---

### Post by nothingspecial on 2008-11-01
> **Carnivorum said:**
> Bs'd

I followed  the instructions on this page: [http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)


    sudo make install
    sudo modprobe ath_pci
    sudo modprobe wlan_scan_sta



Type ```
make
``` before ```
sudo make install
```

---

### Post by Carnivorum on 2008-11-01
Bs'd

If I type "make" I get the following response: 

make: *** No targets specified and no makefile found.  Stop.

---

### Post by nothingspecial on 2008-11-01
copy and paste these commands into your terminal.

Download madwifi

```

wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
```

unzip it```


tar -xvf madwifi-hal-0.10.5.6-current.tar.gz
```


navigate to the extracted file
```

cd madwifi-hal-0.10.5.6-r3861-20080903
```

If you followed your guide you already have build-essential but just to check do this. build-essential allows you to compile and install source code.
```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Compile

```
sudo make
```

Install

```
sudo make install
```

Load it
```

sudo modprobe ath_pci
```

Make it load at every boot
```

gksudo gedit /etc/modules
```

Copy and paste this to the bottom of the file

```
ath_pci
```

Save
Close
Reboot

---

### Post by donaldshelton on 2008-11-02
I followed the directions.  I even typed "make" before "sudo make install"

Here is the error message I get:  don@donslaptop:~/madwifi-ng-r2756+ar5007$ make
make: *** No targets specified and no makefile found.  Stop.

I am trying to install this on my Kubuntu 8.10 partition.

Thanks
Don

---

### Post by nothingspecial on 2008-11-03
madwifi`s site is down try later

---

### Post by Carnivorum on 2008-11-03
> **donaldshelton said:**
> I followed the directions.  I even typed "make" before "sudo make install"

Here is the error message I get:  don@donslaptop:~/madwifi-ng-r2756+ar5007$ make
make: *** No targets specified and no makefile found.  Stop.

I am trying to install this on my Kubuntu 8.10 partition.

Thanks
Don

Bs'd

I get the same error


Carni

---

### Post by donaldshelton on 2008-11-03
> **donaldshelton said:**
> I followed the directions.  I even typed "make" before "sudo make install"

Here is the error message I get:  don@donslaptop:~/madwifi-ng-r2756+ar5007$ make
make: *** No targets specified and no makefile found.  Stop.

I am trying to install this on my Kubuntu 8.10 partition.

Thanks
Don

It seems that I am not the only one with this error message.

What to do!!!!:lolflag:

---

### Post by Carnivorum on 2008-11-03
Bs'd

If only I knew....

---

### Post by donaldshelton on 2008-11-03
> **nothingspecial said:**
> copy and paste these commands into your terminal.

Download madwifi

```

wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
```

unzip it```


tar -xvf madwifi-hal-0.10.5.6-current.tar.gz
```


navigate to the extracted file
```

cd madwifi-hal-0.10.5.6-r3861-20080903
```

If you followed your guide you already have build-essential but just to check do this. build-essential allows you to compile and install source code.
```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Compile

```
sudo make
```

Install

```
sudo make install
```

Load it
```

sudo modprobe ath_pci
```

Make it load at every boot
```

gksudo gedit /etc/modules
```

Copy and paste this to the bottom of the file

```
ath_pci
```

Save
Close
Reboot


Both Carnivorum and I are having a heck of a time with this!!

When we type "make" we get error messages.

In Kubuntu 8.10, there is no administration or preferences tab like in Ubuntu 8.10  How do I disable the restricted drivers in Kubuntu?:guitar:

---

