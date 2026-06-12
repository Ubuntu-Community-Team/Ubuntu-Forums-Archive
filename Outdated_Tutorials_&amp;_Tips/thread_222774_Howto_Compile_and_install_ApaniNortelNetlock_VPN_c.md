---
title: "Howto: Compile and install Apani/Nortel/Netlock VPN client"
date: 2006-07-25
forum: Outdated Tutorials &amp; Tips
---

### Post by deez0n on 2006-07-25
[SIZE="2"]This howto explains how I was able to compile and install the Apani Netlock software under Ubuntu Dapper (2.6.15.26 kernel). Most people seem to be having problems with both getting a clean compile of the netlock module, and, after that, the kernel locking up or panicking when the module is inserted.

To fix these problems, modifications will need to be made to the linux_wrapper.c that ships with the client, and full kernel build will be required.
The references in the netlock readme require gcc-3.x series compiler for both but I found that the stock Ubuntu Dapper gcc-4.0.3 compiler works fine for this.

1: Follow the excellent kernel build directions located [here]("http://doc.gwos.org/index.php/Kernel_Compilation_Dapper") and make sure you follow the xorg.conf instructions before the build.
While on the make menuconfig step, enable the "Use register arguments .." under the "Processor type and features" menu item.
   ```
Processor type and features --> Use register arguments (CONFIG_REGPARM)
```

 Having this setting disabled is what is causing the kernel to lockup whenever the netlock module is inserted. The Dapper kernel build tutorial is located at the following


2: Reboot with the new kernel and make sure it works.

2a: I had to reinstall my proprietary video drivers (NVidia), you may need to do the same.

3: Untar the Redhat version of the client (cvc_linux-rh-gcc3-3.3.tar.gz) and then cd to the client directory.
The netlock client src file linux_wrapper.c makes a call to the kernel's ip_rcv function, which in 2.6.14 and above is no longer exported as a symbol from the kernel. The function also has an additional argument in it's parameter list so it will no longer work with the netlock client. From searching forum posts, I found that the correct call should actually be to netif_rx which takes a single argument. Edit the file using ```
sudo [favorite editor] src/linux_wrapper.c
``` 
In the function definition nl_ip_rcv change this:
```
return ip_rcv(skb, skb->dev, pt);
```

to this:
```
return netif_rx(skb);
```

The wrapper also attempts to copy structure entries from one sk_buff to another and the names of some these entries have changed.
In two places, the wrapper attempts to copy the stamp field of one sk_buff to another, and in one place, attempts to copy the security field. stamp has been changed to tstamp, and I believe security has been changed to "sp" (security path). I just commented out the security field copy instructions, the client still works fine.
Change this:
```
new_skb->stamp = skb->stamp;
```

to:
```
new_skb->tstamp = skb->tstamp;
```

and this:
```
skb_to->stamp = skb_from->stamp;
```

to:
```
skb_to->tstamp = skb_from->tstamp;
```

and this:
```
new_skb->security = skb->security;
```

to this:
```
/* new_skb->security = skb->security; */
```

4: Save the linux_wrapper.c file and then run ```
sudo make
``` in the netlock client root folder.
After running successful make, cd to the src folder and and run ```
modinfo mishim.o
```
This is the module that is crashing kernels. Make sure the kernel portion of the vermagic matches the output from ```
uname -r
```

5: Just for safety, I ran ```
tail -f /var/log/syslog
``` in another terminal, and then ran ```
sudo insmod mishim.o
``` just to make sure I could diagnose if the kernel locked up again. 
I believe, if your kernel does crash/lockup, you can use the sysrq commands to dump debug output to the syslog and reboot the computer: read the contents of /usr/src/linux/Documentation/sysrq.txt for more info.
If the kernel doesn't crash, you are safe to run the install script and then it's "Happy working from home".
You can run either ```
sudo install.sh
``` or ```
sudo make install
```

The information that led me to a successful integration was found on a gentoo forums thread:
[http://forums.gentoo.org/viewtopic.p...hlight=netlock](http://forums.gentoo.org/viewtopic.p...hlight=netlock)[/SIZE]

---

### Post by Prometheus7 on 2007-08-01
what if you have 64-bit feisty installed?

---

