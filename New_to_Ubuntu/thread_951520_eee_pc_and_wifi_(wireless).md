---
title: "eee pc and wifi (wireless)"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Periswell on 2008-10-18
hello

My sister has got an eee pc and this week I thought i would put ubuntu on it. I downloaded eeebuntu and installed it onto the computer but now the wireless does not work. i tried to install madwifi by doing:
> sudo apt-get update
sudo apt-get install build-essential
wget 'http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz'
tar -zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi*/
sudo make clean
sudo make
sudo make install
but it still is the same, nothing atall has changed.
please help is i cannot wait for Intrepid Ibex to be release so please help.

-josh

---

### Post by NewJack on 2008-10-18
Quick question, is the blue WiFi indicator light on?

---

### Post by Periswell on 2008-10-18
nope

---

### Post by trigsenior on 2008-10-18
hey,

You need wifi to be enabled , when the eeepc boots go into bios and enable it i believe it F12. Then install madwifi 
[https://help.ubuntu.com/community/EeePC/Fixes#Wireless](https://help.ubuntu.com/community/EeePC/Fixes#Wireless)

hope this helps

also like to add there is a script which does everything [http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly#wifi_hotkeys](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly#wifi_hotkeys)
scroll down to middle. To run scrit "sudo sh ./thatscript"

---

### Post by surfed on 2008-10-18
> **Periswell said:**
> hello

My sister has got an eee pc and this week I thought i would put ubuntu on it. I downloaded eeebuntu and installed it onto the computer but now the wireless does not work. i tried to install madwifi by doing:

but it still is the same, nothing atall has changed.
please help is i cannot wait for Intrepid Ibex to be release so please help.

-josh


Easiest way to get your eee to work:

1. Install ubuntu-eee ([http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/))
2. Add http:[www.array.org/ubuntu](www.array.org/ubuntu) hardy and hardy-proposed to your repositories
3. Turn on all updates including pre-released and unsupported
4. Reload package list
5. Upgrade System

See array.org for more help.

This solution makes everything work like a charm. Toggle wireless & Bluetooth and Fn Keys.

---

### Post by Periswell on 2008-10-18
ok so i have installed the driver and i have got up to this (see attachments for the image) bit but i do not know what to put in the boxes. does anyone else know?

-josh

---

### Post by nickthecook on 2008-10-19
I have to agree with surfed here - the easiest way to have everything Just Work is to install Ubuntu Eee ([http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/)). The new release, 8.04.1, comes with built-in kernel support for all the Eee 901 hardware - I didn't need to visit array.org (Ubuntu Eee probably packaged up the array.org kernel).

Then install eee-control from [http://greg.geekmind.org/eee-control/](http://greg.geekmind.org/eee-control/) to get access to enabling and disabling bluetooth, wifi, and other stuff right from the system tray.

With these steps, it's almost disappointingly easy to get everything working, and I've had to go out of my way to find things to tweak. ;)

---

### Post by ogredeschnique on 2008-11-01
There are scripts in the eeesupport folder in the Root dir. Run the scripts that apply to the eeepc version that your sister is running. 
Those scripts will fix everything that breaks after you run updates. Hinting to you that you run the udates first. 
apt-get update, then apt-get upgrade.
Also, Intrepid doesn't support eeepc wifi out of the box either. So after updating to it myself, I have decided that I'll go get those scripts from a liveusb version bootup of eeebuntu and transfer the eeesupport folder to my ssd, all thanks to your post making me think of it. 
:-)

---

