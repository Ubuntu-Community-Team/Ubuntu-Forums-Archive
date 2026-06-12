---
title: "help with my compaq wifi"
date: 2007-11-26
forum: Philippine Team
---

### Post by Kulaspiro on 2007-11-26
could sombody help me to activate my wifi mga tol...
gamit ko compaq nx6125
amd mobile sempron 3100
broadcom 802.11b/g Wlan

im a newbie user of ubuntu
gnome/feisty fawn

salamat

---

### Post by raxso on 2007-11-27
I would not recommed to use the restricted drivers kasi may bad experience ako dito, nag freeze ang wifi connection and when i switch to wired connection i need to restart the network so that it will be detected properly. So here's a mini how to on how you can enable your wireless connection.

Download the following:
Ndiswrapper: 

wget [http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz](http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz)

Broadcom Wireless Driver: Should come with your system in drivers CD or download the drivers from compaq.

1. I would suggest a clean install before doing this at wag matakot.
(Relak ka lang at wag ma ten kasi baka ka magkolap) :)

2. Update your system:

                 Code:
                  sudo apt-get update
                  sudo apt-get install build-essential
                  sudo apt-get install linux-headers-`uname -r`
NOTE: The characters around `uname -r` are BACK TICS, NOT apostrophes. I would suggest to just copy and paste.

3.Uncompress the ndiswrapper source (example, the file name is ndiswrapper-1.47.tar.gz):

Code:
tar -xzvf ndiswrapper-1.47.tar.gz

4. Blacklist the broken bcm43xx firmware drivers.

sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist

If this does not work try this.

sudo -s
echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
exit

5. Compile the Ndiswrapper.

     cd YOUR-NDISWRAPPER-DIRECTORY
     sudo make uninstall

Important: Run the code until you dont see anything that says no file or directories found.

    sudo make
    sudo make install

6. Change to your Wireless drivers directory.

     CD your-drivers-directory
     sudo ndiswrapper -i bcmwl5.inf
     sudo ndiswrapper -l

Note: you should see a message that says; Driver present, Hardware Detected.

     sudo ndiswrapper -m
     sudo modprobe ndiswrapper
     sudo echo ndiswrapper >> /etc/modules

If this command does not work try this.

    sudo -s
    echo ndiswrapper >> /etc/modules
    exit

Reboot your computer.

7. Test your wireless.
    
     sudo iwlist scanning

You should see active access points here or use your network manager.

Hope this helps and let me know kung gumana sa iyo.

Tested ko ito sa Compaq and Dell.  :)

---

### Post by Kulaspiro on 2007-12-02
bro thanks, ill let you know if it works ...

---

### Post by Kulaspiro on 2007-12-02
bro thanks, ill let you know if it works ...

---

### Post by robinx1578 on 2008-05-03
this is the error i get when run the command: sudo make

make[1]:*** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/robinx/NetDriver/ndiswrapper-1.52/utils'
make: *** [all] Error 2

and this is the other error i get when run the command: sudo make install

make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/robinx/NetDriver/ndiswrapper-1.52/utils'
make: *** [install] Error 2

Can you tell me why? Im having problem with the ndiswrapper ..

---

