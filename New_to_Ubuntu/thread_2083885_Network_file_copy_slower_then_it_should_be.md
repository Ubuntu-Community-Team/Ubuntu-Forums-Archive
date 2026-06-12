---
title: "Network file copy slower then it should be"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by Thee on 2012-11-13
When I copy files to my NAS server over my wired 100 Mbps/s network, I'm getting maximum speed of 7,5MB/s or lower, while on the same computer, I dual boot Win7, and when doing the same thing, I'm getting around 11-12 MB/s. So its not a hardware problem.
Also, I noticed when I copy 2 files simultaneously, I get around 4MB/s + 6MB/s on each file that is copying, so it can go faster, but the speed tends to decrease some minutes later.

Im using Ubuntu 12.10 and Nautilus to copy files on SAMBA network.

Anyone got any tips to improve the speeds?

Thanks

---

### Post by DuckHook on 2012-11-13
I used to use Samba, but have used NFS exclusively for many years now, so I'm a little rusty. What I do remember is that Samba has a default configuration that may not be ideal for your particular network architecture. There really isn't an ideal Samba configuration because there are so many different configurations, but your windows installation may be outperforming Samba because its default configuration is just coincidentally more suited to your specific network parameters than the Samba defaults.

The good news is that you can easily change your Samba settings and play with them until you get the parameters that are right for you. The instructions for doing so can be found at:

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html)

Last but not least: are you sure you are running Samba? Many people say Samba when they are actually running cifs or gvfs. If you are using these other two, then we need a cifs/gvfs guru to jump in as I have never run either of these filesystems.

---

### Post by Thee on 2012-11-14
Well to tell you the truth, I don't even know what cifs/gvfs is, I assumed I was running SAMBA since that is what I installed in order to browse/see my Windows computers on the network. And since my NAS server doesn't support NFS. Is there a way I can check what em I running? And if so, what protocol is recommended for fast transfer speeds in my situation, besides NFS?

---

### Post by mikewhatever on 2012-11-14
You could try adding the following line to your /etc/samba/smb.conf

```
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
```

[Infor source]("https://calomel.org/samba_optimize.html") the options explained.

---

### Post by Thee on 2012-11-14
Actually I tried that before I opened this topic but with those options, the speed deceased by 1,0 - 1,5 MB/s.
With only the *socket options = TCP_NODELAY* enabled I get slightly better performance (7,5 instead of 7,0 MB/s)

---

### Post by DuckHook on 2012-11-14
> **Thee said:**
> Well to tell you the truth, I don't even know what cifs/gvfs is

I should have been clearer. I was referring to smb vs cifs vs gvfs, all of which are different protocols for working with samba. I mentioned it only because the smb protocol was deprecated some years ago in favour of cifs which has since been deprecated in favour of gvfs. The latest versions of Ubuntu use gvfs. This would have an impact on a solution only if gvfs doesn't reference the smb.conf file. I'm frankly out of my depth here because I don't use anything other than NFS, so can provide only limited and general advice on samba configurations. Others here will be more knowledgeable. Clearly, changes to your smb.conf file do have an impact on your speed, so for all intents and purposes you can ignore my comments on smb vs cifs vs gvfs.

You might try changing the buffer entries to sizes less than 65536. I believe that this is the maximum buffer size in samba and it may not be appropriate for your network. My understanding is that it's largely a process of trial and error, tweeking one variable, then another. This was certainly what I had to do for NFS to get it running optimally. Yet even now, it will run faster on some days and slower on others depending on what else (amount and type of traffic) is happening on the network.

---

### Post by bab1 on 2012-11-14
> **DuckHook said:**
> I should have been clearer. I was referring to smb vs cifs vs gvfs, all of which are different protocols for working with samba. I mentioned it only because the smb protocol was deprecated some years ago in favour of cifs which has since been deprecated in favour of gvfs. The latest versions of Ubuntu use gvfs. This would have an impact on a solution only if gvfs doesn't reference the smb.conf file. I'm frankly out of my depth here because I don't use anything other than NFS, so can provide only limited and general advice on samba configurations. Others here will be more knowledgeable. Clearly, changes to your smb.conf file do have an impact on your speed, so for all intents and purposes you can ignore my comments on smb vs cifs vs gvfs.

You might try changing the buffer entries to sizes less than 65536. I believe that this is the maximum buffer size in samba and it may not be appropriate for your network. My understanding is that it's largely a process of trial and error, tweeking one variable, then another. This was certainly what I had to do for NFS to get it running optimally. Yet even now, it will run faster on some days and slower on others depending on what else (amount and type of traffic) is happening on the network.

Just a small comment on SMB vs CIFS.  Samba impliments both; as CIFS is just an extension of SMB.  GVFS is the GNOME virtual file system and it uses SMB/CIFS to mount Windows/Samba shares via Nautilus at ~/.gvfs.  CIFS has not been depricated in favor of GVFS.  In fact they are two different things.  Microsoft has muddied the water even futher but calling its latest implmetation SMB2.  ;-) 

Speed problems are the worst to diagnose.  It could be a driver problem or the file system that is mounted (think NTFS), so I have no comment or cures.

---

### Post by Thee on 2012-11-14
> **bab1 said:**
> the file system that is mounted (think NTFS), so I have no comment or cures.

Are you saying that if target file system is NTFS, it has impact on the copy speed? Almost 1/2 speed decrease? Can't be... it must be software related, its either a configuration file, or like you suggested driver, but since I have a standard integrated NIC, I doubt it.

---

### Post by bab1 on 2012-11-14
> **Thee said:**
> Are you saying that if target file system is NTFS, it has impact on the copy speed? Almost 1/2 speed decrease? Can't be... it must be software related, its either a configuration file, or like you suggested driver, but since I have a standard integrated NIC, I doubt it.
Both the NIC driver and NTFS file system emulation are externally developed and I believe reverse engineered.  The fact that you have an integrated piece of hardware means nothing to the issue.  Indeed, software integration is the issue.  There are no configuration files for ntgs-3g driver and I'll bet there are none for the NIC driver either.  Samba does have configuration parameters for buffers, but as others have stated you need to fiddle with it and hope you find a useful.

---

### Post by Thee on 2012-11-14
Well I just meant, the integrated NICs are widely used, almost same chipset on all motherboards. That's why I think it has good support.

Ok, well thank you all for helping, I guess its all up to me now to try and get the settings right. If not, I'll have to live with that speeds until something changes in the future.

---

