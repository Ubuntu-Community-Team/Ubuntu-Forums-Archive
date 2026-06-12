---
title: "I can't attach files from browsed network in Gmail"
date: 2015-11-05
forum: New to Ubuntu
---

### Post by enel on 2015-11-05
Hi all,

I often attach file from other network computer to send my customers from Windows 7 but when I use this new Ubuntu, everything makes me nervous. I can't browse other network Computer to attach file like Windows. Here is the image that will show my problem.

[IMG]http://i601.photobucket.com/albums/tt96/hugolina36/Screenshot%20from%202015-11-05%20144233.png[/IMG]

So if I want to attach file from browse network, I have to copy it to my local disk and attach. This spends me a lot of time.

Can anyone help me to fix this problem ?

Best Regards,

---

### Post by howefield on 2015-11-05
You would need to mount the network disk first, have you done so ?

---

### Post by enel on 2015-11-05
Already mounted :( and still not see it when I attach file in gmail :(

---

### Post by enel on 2015-11-06
Please helppppp :(

---

### Post by PaulW2U on 2015-11-06
> **enel said:**
> Already mounted :( and still not see it when I attach file in gmail :(
Hi enel, by convention, mounted drives normally appear in the /mnt directory. In your file picker you need navigate to the root directory and then the /mnt directory. If your drive is mounted correctly then from there you should be able to find the file on the drive that you wish to attach to your email.

If you have mounted your drive elsewhere then what I have written above will need to be changed to reflect the different mount point.

I hope that helps. If you're still having problems then let us know where you mounted your drive.

Edit: Also, how did you mount your drive, what (terminal) command did you use?

---

### Post by Vladlenin5000 on 2015-11-06
Samba shares usually are at

```
/run/user/1000/gvfs
```

Just tested and it works, i.e., a file can be attached by following the aforementioned path.

---

### Post by enel on 2015-11-10
> **PaulW2U said:**
> Hi enel, by convention, mounted drives normally appear in the /mnt directory. In your file picker you need navigate to the root directory and then the /mnt directory. If your drive is mounted correctly then from there you should be able to find the file on the drive that you wish to attach to your email.

If you have mounted your drive elsewhere then what I have written above will need to be changed to reflect the different mount point.

I hope that helps. If you're still having problems then let us know where you mounted your drive.

Edit: Also, how did you mount your drive, what (terminal) command did you use?

Ah ! I use Samba to share and connect file for each other. Here is my Samba conf file. I think I can mount the drives to share for everyone because of this samba. ^^

```
#======================= Global Settings =====================================[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = thao-pc
security = user
map to guest = bad user
dns proxy = no
#============================ Share Definitions ==============================
[MyShare]
path = /samba/share
browsable =yes
writable = yes
guest ok = yes
read only = no



```

I also check in /mt and I found nothing in here
[IMG]http://i601.photobucket.com/albums/tt96/hugolina36/Screenshot%20from%202015-11-11%20105622.png[/IMG]

So it means that I have to add my mount drive to this folder then I can attach file from network drive ? CAn you guide me? 

Many thanks ^^

---

### Post by enel on 2015-11-10
> **Vladlenin5000 said:**
> Samba shares usually are at

```
/run/user/1000/gvfs
```

Just tested and it works, i.e., a file can be attached by following the aforementioned path.

I can't see this path @@ how did I miss ? Please help me

[IMG]http://i601.photobucket.com/albums/tt96/hugolina36/Screenshot%20from%202015-11-11%20110146.png[/IMG]

---

