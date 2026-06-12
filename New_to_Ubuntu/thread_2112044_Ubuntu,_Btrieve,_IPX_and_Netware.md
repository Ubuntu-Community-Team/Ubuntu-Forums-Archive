---
title: "Ubuntu, Btrieve, IPX and Netware"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by Rheikan on 2013-02-03
Good Afternoon :

I explain the situation and us, if us can, please, answer to me.

I have 30 approx. Pcs XP connected to a server NETWARE 6.5 and 5.1 with a protocol IPX/SPX, because the program run with BTRIEVE (bd Netware and work only in IPX), we cant change inmediatly the software, so begin to migrate to Ubuntu.

I can see the directory in ubuntu from the Server Netware with NCPFS packet, and Run the program, but in the moment to execute BREQUEST (utility of Btrieve) the DOSBOX (for run the program builded in Qbasic!!) tellme that SPX.COM is not load... Sooo what can i DO???.

PD : Repeat, cant change now the software because major forces, so i need to connect UBUNTU to Novell and RUN the utility BREQUEST in a DOSbox for example.

Sorry my English ;)

Can you Help me???

Regards.

---

### Post by haqking on 2013-02-03
been a while since i did anything with IPX/SPX.

See if you can find some answers here

[http://www.tldp.org/HOWTO/IPX-HOWTO.html](http://www.tldp.org/HOWTO/IPX-HOWTO.html)

I think you will need to enable IPX support at kernel build time

[http://searchnetworking.techtarget.com/tip/Configuring-a-Linux-kernel-for-IPX-and-NCPFS](http://searchnetworking.techtarget.com/tip/Configuring-a-Linux-kernel-for-IPX-and-NCPFS)

---

### Post by sanderj on 2013-02-03
Apparantly Ubuntu's kernel has IPX built in:

```
sudo apt-get install ipx
sander@R540:~$ sudo ipx_interface add -p eth0 802.2 0x39ab0222

sander@R540:~$ ifconfig | grep -i ipx
          IPX/Ethernet 802.2 addr:39AB0222:002454E85431
sander@R540:~$ 
```

Disclaimer: I've never used IPX

HTH

---

