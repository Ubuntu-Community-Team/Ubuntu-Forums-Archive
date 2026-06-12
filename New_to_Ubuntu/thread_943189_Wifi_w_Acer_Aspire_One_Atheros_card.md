---
title: "Wifi w/ Acer Aspire One Atheros card"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by jxtcortex on 2008-10-10
Hi, 

My girlfriend just bought an Aspire One and we put Ubuntu 8.04 on it. Actually, all works well, except for the wireless... 
I looked a bit on the internet for answers, but I can't even understand where to type what (and I'm french speaking, making english harder to understand).

I saw Madwifi was a way to resolve this problem (I think, correct me if I am mistaken), but I don't understand how to install, or build it (example : I don't know what "Open a shell terminal in the Madwifi folder" means).

Could someone help me ultra-clearly, since it's my first time ever with a Linus-based OS ?

Thx

JT.

---

### Post by pvsdilhan on 2008-10-10
Don't worry. You have to do simple steps.:) Follow the instructions given below.
1. Let me know your model wireless card. If you do not know then do 2 instruction.
2. Open terminal. (Applications -> Accessories -> Terminal)
3. Type the following command :
   **[COLOR="DarkSlateBlue"]lspci -vvnn|grep Network[/COLOR]**
Then it will display the model. Post it to this thread.

---

### Post by nothingspecial on 2008-10-10
Open your terminal as you have been instructed.

Download the latest madwifi snapshot.


```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz

```
Unzip it


```
tar -xvf madwifi-hal-0.10.5.6-current.tar.gz

```
At the beginning of the untarred (unziped) folders ie the lines of gobbldygook the terminal just spat out will be the name of the current madwifi directory. In your case it is madwifi-hal-0.10.5.6-r3861-20080903

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

---

### Post by jxtcortex on 2008-10-17
Thx for your answers !

I did what you wrote Nothingspecial, and it worked well for 5 days, but since yesterday, the WiFi connection stopped working again. I repeated the steps all over again and this time the computer was detecting the WIreless, without being able to connect on my network. And then, today, Ubuntu cannot recognize the card, so I am out of solutions ! Your help (again) could be useful ! Thanks !

JT.

---

### Post by nothingspecial on 2008-10-17
Try this first
```

sudo modprobe ath_pci
``` This loads the module. Then to get it to load at boot do this
```
gksudo gedit /etc/modules
```

then copy and paste this to the bottom of that file


```

ath_pci
```

save
exit 
reboot

If that doesn`t work and you still have the madwifi source code, cd into it.

```
cd madwifi-hal-0.10.5.6-r3861-20080903
```

Then one line at a time

```
make clean
make
sudo make install
```

---

### Post by jxtcortex on 2008-10-18
It seems to work for now, I'll let you know if something is wrong again, thanks a lot !

JT.

---

### Post by nothingspecial on 2008-10-18
> **nothingspecial said:**
> 

```
cd madwifi-hal-0.10.5.6-r3861-20080903
```

Then one line at a time

```
make clean
make
sudo make install
```

You will need to this every time you have a kernal upgrade which may have happened with your last update. 

Glad it works
:guitar:

---

### Post by FountainDew on 2008-12-11
> **nothingspecial said:**
> Open your terminal as you have been instructed.

Download the latest madwifi snapshot.


```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz

```
Unzip it


```
tar -xvf madwifi-hal-0.10.5.6-current.tar.gz

```
At the beginning of the untarred (unziped) folders ie the lines of gobbldygook the terminal just spat out will be the name of the current madwifi directory. In your case it is madwifi-hal-0.10.5.6-r3861-20080903

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

You have the most helpfull post for -anyone- who owns an Acer Aspire One. Thank you! :)

---

### Post by Exodisma on 2009-01-28
I have an Acer Aspire One as well, and I'm trying to set up the network card with Ubuntu 8.10.  However, [http://snapshots.madwifi.org](http://snapshots.madwifi.org) seems to be down, at least for the past few days when I've been trying it.  How else could I get access to the files I need?
Thanks

---

### Post by avtolle on 2009-01-28
> **Exodisma said:**
> I have an Acer Aspire One as well, and I'm trying to set up the network card with Ubuntu 8.10.  However, [http://snapshots.madwifi.org](http://snapshots.madwifi.org) seems to be down, at least for the past few days when I've been trying it.  How else could I get access to the files I need?
Thanks
As you are in 8.10, [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default) may take care of your card. Give it a try and see how it goes.

---

### Post by budwug on 2009-02-01
> **Exodisma said:**
> I have an Acer Aspire One as well, and I'm trying to set up the network card with Ubuntu 8.10.  However, [http://snapshots.madwifi.org](http://snapshots.madwifi.org) seems to be down, at least for the past few days when I've been trying it.  How else could I get access to the files I need?
Thanks

I used [http://snapshots.madwifi-project.org](http://snapshots.madwifi-project.org) instead and it worked like a charm.

---

### Post by 3rdalbum on 2009-02-01
You don't need to compile a driver, there is one available from the repositories. And despite what the wiki page says, it's very reliable and it works fine.

Enable the backports repository from Software Sources, reload the package list, and install "linux-backports-modules-intrepid-generic". Add "ath_pci" to /etc/modprobe.d/blacklist, and add "ath5k" to /etc/modules. Reboot. Now your wireless is working with an excellent, open-source driver (this driver also works with other Atheros cards).

---

### Post by 3rdalbum on 2009-02-01
.

---

### Post by kevcool on 2009-02-26
> **3rdalbum said:**
> You don't need to compile a driver, there is one available from the repositories. And despite what the wiki page says, it's very reliable and it works fine.

Enable the backports repository from Software Sources, reload the package list, and install "linux-backports-modules-intrepid-generic". Add "ath_pci" to /etc/modprobe.d/blacklist, and add "ath5k" to /etc/modules. Reboot. Now your wireless is working with an excellent, open-source driver (this driver also works with other Atheros cards).

Many thanks for making this simple, 3rdalbum.  Works great.  Much prefer drivers from the repository for obvious reasons.

---

### Post by stchman on 2009-02-26
The problem with the ath5k is that it is spotty at best.  COnnections drop and sometimes don't even connect.  The madwifi ath_pci works much better.

Follow my Intrepid on Aspire One page.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

Hope this helps.

---

### Post by geirergoy on 2009-08-29
I can't make it work.
I have a fresh install of Ubuntu 9.04, and I have tried all these guides.
It worked before I formatted the AAO and reinstalled Ubuntu, but it does not work now.

I don't remember exactly how I did it the last time, but I know I had to use "make" and "make install", and then I had to edit some text files to make it start and to make the LED work.

How should I do this? I have tried these guides for 2 days noow.
Getting tired. Will buy another PC if this one continues mocking me.

As I said, I have a fresh install of 9.04, updated using the update manager, before starting to follow these guides.
Worked perfectly before after using a similar guide, which I can not find.

I have AR242x 802.11abg

Please help, so I don't have to buy another netbook. I like this one, except for the wlan card. Windows is not an option.

---

