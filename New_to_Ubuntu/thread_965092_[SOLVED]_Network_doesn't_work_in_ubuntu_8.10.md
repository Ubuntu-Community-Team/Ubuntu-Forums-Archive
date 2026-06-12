---
title: "[SOLVED] Network doesn't work in ubuntu 8.10"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by quinnten83 on 2008-10-31
I just installed Ibex on my Compaq evo N610c and the network doesn't work.
I don't even get a network manager applet.
lspci says I have the following network card:
```
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)
```
I know the card works, because I am typing this from opensuse 11.
I know there used to be a problem with intel network cards, but I thought this was fixed in the RC.
Can anybody help?

---

### Post by conscious on 2008-10-31
Well, you should probably try getting Network Manager applet running. There's a thread about it: [http://ubuntuforums.org/showthread.php?t=956187](http://ubuntuforums.org/showthread.php?t=956187)

---

### Post by quinnten83 on 2008-10-31
tnx, 
I got nm-applet up and running, unfortunately, I still have no network.
NM-applet says no network devices found. Any ideas anyone? I really would like to get this working.

---

### Post by Dalkir on 2008-11-01
Found an easy way to correct the problem I was having, seems similar to yours.  Check out [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

I have grabbed the pertinent part here, simply run gedit and change the files listed below:

> 

If it still dosen't work you'd have to edit the dbus-1 configuration files for both NetworkManager and nm-applet (this might be a security compromise, if there's another way to get nm-applet to work, please add it here).

Change the default policy context in both /etc/dbus-1/system.d/NetworkManager.conf and /etc/dbus-1/system.d/nm-applet.conf so it says 'allow' instead of 'deny'.

<policy context="default">
        <allow own="org.freedesktop.NetworkManager"/>
        <allow send_destination="org.freedesktop.NetworkManager"/>
        <allow send_interface="org.freedesktop.NetworkManager"/>
</policy>

Then restart dbus

sudo /etc/init.d/dbus restart

and launch the applet

nm-applet


I'll also note here that I thought I chunked my system when I did this, X crashed, I had no sound, and took almost a minute to boot up after a restart.  After logon, I found that my sound had been muted for some reason, no other issues thus far.

Hope this helps!

---

### Post by quinnten83 on 2008-11-06
OK, 
I solved my problem by grabbing a wicd.deb, 
and deinstalling gnome-network-manager and installing the wicd deb.
Now, at least the wired connection works. I haven't been able to test the wireless. The computer I have installed on doesn't have a wireless card in it.

---

