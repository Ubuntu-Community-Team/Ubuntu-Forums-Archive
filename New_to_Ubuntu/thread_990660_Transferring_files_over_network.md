---
title: "Transferring files over network"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by BetterSense on 2008-11-22
I have a desktop, with dsl internet, running kubuntu. I also have a wireless router and a laptop with Ubuntu. I want to transfer a whole bunch of video files to the laptop for travel. I could use an external HDD, but there must be a way to transfer them over internet, and now would be a good time to learn how. I'm pretty thick when it comes to networking. These computers aren't officially networked in any way I know of, I just log into my home 'hotspot' with the laptop using the WPA password. I don't have a crossover cable. How can I do this with like FTP or whatever? Do you know of a good how-to? I found this tutorial[URL="http://mybeni.rootzilla.de/mybeNi/2007/how_to_set_up_nfs_and_how_to_share_files_in_a_local_network_with_ubuntu_linux/"]
http://mybeni.rootzilla.de/mybeNi/2007/how_to_set_up_nfs_and_how_to_share_files_in_a_local_network_with_ubuntu_linux/[/URL]
but I think I have to do something first to set up a network so that the two computers at least know about each other before I can follow it. Thanks.

---

### Post by handydan918 on 2008-11-23
There are a lot of ways to do this. I like to use ssh and scp.
First, do ```
sudo apt-get install openssh-server
```

Then ```
sudo update-rc.d -f ssh remove && update-rc.d ssh defaults

```

This wili start the ssh daemon at boot time. 

Once that is done, you can copy a file or directory using scp like so:
```
scp <filename> 192.168.1.2:/home/somelameusername/sometargetdirectory
```

To copy a directory, do the above with ```
scp -r
```

I find that ssh is easient if you use the same username and password on both boxen....


HTH!!

---

### Post by BetterSense on 2008-11-23
should I do all this on the source computer or the destination computer? Or both? Thanks I'll give it a try.

---

### Post by hyper_ch on 2008-11-23
a lot simpler than scp all the filenames would be to use sshfs :)

or when you have konqueror in your kubuntu you should use openssh-server and fish://...

---

### Post by handydan918 on 2008-11-23
> **hyper_ch said:**
> a lot simpler than scp all the filenames would be to use sshfs :)

or when you have konqueror in your kubuntu you should use openssh-server and fish://...
Yeah, heh, everything's easier with konqueror....

---

