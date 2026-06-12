---
title: "Manually Configuring Wireless Connection"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Mango Reinhardt on 2008-06-16
I'm having trouble connecting to my wireless when setting up a manual connection network connection.

It works fine when I allow it to use roaming mode, but really would prefer to set a specific IP to use on the network. When I set up the connection the way I normally would with windows it can't even find my router let alone connect to the net.

Could anyone run me through the basics manually connecting to my wireless?

Thanks

---

### Post by azurepancake on 2008-06-16
I had the same exact problem trying to setup a static IP with my wireless network, using Ubuntu's default network-applet. Even by editing "/etc/network/interfaces I wasn't able to manage a static IP succesfully.

Because of this I switch to WICD which is another network manager. Using WICD, I was able to configure my static IP very easily.

Give it a shot. I am pretty sure you'll have to add the WICD repository to your sources list in order to download.

```
sudo nano /etc/apt/sources.list
```

..and then copy and paste..

```
deb http://apt.wicd.net hardy extras
```

..then from the terminal, type..

```
sudo apt-get install wicd
```

Once it is installed, you can access the applet from *Applications->Internet->Wicd*

I hope this helps!

---

### Post by Mango Reinhardt on 2008-06-16
> **azurepancake said:**
> I had the same exact problem trying to setup a static IP with my wireless network, using Ubuntu's default network-applet. Even by editing "/etc/network/interfaces I wasn't able to manage a static IP succesfully.

Because of this I switch to WICD which is another network manager. Using WICD, I was able to configure my static IP very easily.

Give it a shot. I am pretty sure you'll have to add the WICD repository to your sources list in order to download.

```
sudo nano /etc/apt/sources.list
```

..and then copy and paste..

```
deb http://apt.wicd.net hardy extras
```

..then from the terminal, type..

```
sudo apt-get install wicd
```

Once it is installed, you can access the applet from *Applications->Internet->Wicd*

I hope this helps!

Ok I've tried this, but after I do the install command I get this message...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wicd

```

Think it's because I haven't saved that line to the sorces list, but I don't know how.

(total noob, haven't used a command line since the 90s :))

---

### Post by fatality_uk on 2008-06-16
Which version of Ubuntu are you using?
A quick and eay way is to open the network settings window, (System->Administration->Network) or network-admin from a terminal.
From within the wireless section, you should be able to configure a static IP address.

---

### Post by eriqjaffe on 2008-06-16
> **Mango Reinhardt said:**
> Think it's because I haven't saved that line to the sorces list, but I don't know how.

(total noob, haven't used a command line since the 90s :))Well, easy enough to check if the line's there.

You'll also need to run:

```
sudo apt-get update && sudo apt-get install wicd
```

It's also possible to add other repositories through Synaptic, but I don't know how as I don't use it.

---

### Post by Mango Reinhardt on 2008-06-16
Ok I've managed to install WICD by using the Synaptic Package Manager, and I can connect with a static IP using my LAN connection.

Sill unable however to connect to my wireless, even though it shows up on WICD. I think it's probably the Encryption that's blocking me.

I'm going to try again and report back.

---

### Post by Mango Reinhardt on 2008-06-16
> **fatality_uk said:**
> Which version of Ubuntu are you using?
A quick and eay way is to open the network settings window, (System->Administration->Network) or network-admin from a terminal.
From within the wireless section, you should be able to configure a static IP address.

I'm using 8.04, and the network-admin was the method I tried before to connect to the wireless.

In WICD it says that I'm connected at 0% and am unable to ping my router, yet with the LAN everything is fine.

We use WEP ASCII encryption with a shared key to access it, but I can't see that option on WICD... is it under a different name?

---

### Post by azurepancake on 2008-06-16
> **Mango Reinhardt said:**
> We use WEP ASCII encryption with a shared key to access it, but I can't see that option on WICD... is it under a different name?

For using ASCII encryption, you need to enter you key between " " .. so if your key is for example, mysecretkey, you must enter it as "mysecretkey"

I hope this helps!

---

