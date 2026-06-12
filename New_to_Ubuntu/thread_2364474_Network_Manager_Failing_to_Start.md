---
title: "Network Manager Failing to Start"
date: 2017-06-23
forum: New to Ubuntu
---

### Post by troubled15 on 2017-06-23
I was experiencing a wifi conection that kept going in and out so I attempted to restart the network manager, and now I dont have any internet conection. Now whenever I open up the Network window in settings I get a window saying "The system network service is not compatiblewith this version".

When I run 

> systemctl status NetworkManager.service 

I get some red text that says "code=exited, status=1/FAILURE" and "Failed to start Network Manager".

I dont know what to do next, or what other info to give so if anyone could help I would be really thankful.

---

### Post by Autodave on 2017-06-23
I am no expert here at all on this, but I would probably try reinstalling the network manager.

Is this a laptop? If so, another thing that quite often fixes that problem (and quite a few others) is to power off the laptop, remove power cord, and remove battery. Now go and do something else for 10 minutes. Reassemble and retry.

---

### Post by troubled15 on 2017-06-23
I tried to reinstall it, but it gives me some errors about failing to fetch archives.

And no, its not a laptop.

---

### Post by Autodave on 2017-06-23
What version of Ubuntu are you running?

---

### Post by troubled15 on 2017-06-23
16.04

---

### Post by vocx on 2017-06-23
> **troubled15 said:**
> I was experiencing a wifi conection that kept going in and out so I attempted to restart the network manager, and now I dont have any internet conection. Now whenever I open up the Network window in settings I get a window saying "The system network service is not compatiblewith this version".

When I run 

> systemctl status NetworkManager.service 

I get some red text that says "code=exited, status=1/FAILURE" and "Failed to start Network Manager".

I dont know what to do next, or what other info to give so if anyone could help I would be really thankful.
There seems to be some reports about this for 14.04. According to those reports you may have the wrong version of the packages "libnl-3-200", "libnl-genl-3-200", "libnl-route-3-200".

[https://ubuntuforums.org/showthread.php?t=2324504](https://ubuntuforums.org/showthread.php?t=2324504)
[https://askubuntu.com/questions/727988/the-system-network-services-are-not-compatible-with-this-version-ubuntu-14-0](https://askubuntu.com/questions/727988/the-system-network-services-are-not-compatible-with-this-version-ubuntu-14-0)
[https://askubuntu.com/questions/727188/the-system-network-services-are-not-compatible-with-this-version-ubuntu-14-04](https://askubuntu.com/questions/727188/the-system-network-services-are-not-compatible-with-this-version-ubuntu-14-04)

Maybe try making sure you have the right packages installed for your version, which is 16.04, not 14.04, as in those threads.

Personally, before installing packages I would simply try restarting the network manager
```
sudo service network-manager restart
```

If that doesn't work, I would try re-enabling the network-manager service, and restarting it.
```
sudo service network-manager force-reload
sudo service network-manager restart

```

If that doesn't work, I would try re-installing the network-manager package.
```
sudo apt-get --reinstall install network-manager
```

If it fails with "failed to fetch files", it is most probably because you don't have an internet connection. Of course, how can you have an Internet connection if your network manager doesn't work in the first place?

Try plugging in an Ethernet cable, and see if it connects, and again try reinstalling the network manager.

Anyway, you would need to go online to another computer to download the required .deb files, move them to your computer, and then install them with "dpkg". You can manually download them from here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Then you can run
```
sudo dpkg -i network-manager_1.2.6-0ubuntu0.16.04.1.deb
```
or whatever the correct name of the package is.

Also, reinstall those files suggested in that thread.
```
sudo dpkg -i libnl-3-200_3.2.27-1ubuntu0.16.04.1.deb
sudo dpkg -i libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1.deb
sudo dpkg -i libnl-route-3-200_3.2.27-1ubuntu0.16.04.1.deb
```

I am also using 16.04, but I have never experience this error that you get. Nevertheless, maybe this information is helpful for you to troubleshoot further.

---

### Post by troubled15 on 2017-06-24
I tried all the things you suggested and nothing worked so I just reinstalled Ubuntu and Network Manager is working now, but thanks for the suggestions anyway.

---

