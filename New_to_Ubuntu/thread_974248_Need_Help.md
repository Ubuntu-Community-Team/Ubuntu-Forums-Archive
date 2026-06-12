---
title: "Need Help"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by txfour on 2008-11-07
Hello, 

Completely new to Linux and not the most computer savy person in the world. I am just sick of hitting ctrl+alt+del! 

I downloaded WUBI and UBUNTU 8.04 LTS and both are burned to CD. I went to install WUBI and as it installs it wants to download UBUNTU again. Here's my problem, I am on satellite service and only allowed to download 450MB every 24 hours. If I exceed that my service is slower than dial up. Anyhow, by downloading last night, I am over my allowed download size and now WUBI says it will take 70 hours to complete install. 

Is there a way to bypass the "re-download and tell WUBI I have UBUNTU on CD? What are my options. 

Thanks

---

### Post by beercz on 2008-11-07
What happens if you ignore the WUBI cd and insert the UBUNTU cd instead?

---

### Post by Elfy on 2008-11-07
[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I install on a machine with no internet connection?

[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) can I use a manually downloaded ISO?

One of these options should work, I did it once but can't remember.

---

### Post by Swan_Htet_Aung on 2008-11-07
This might be a solution,
I have been saw that case at my friend home.
Our country connection is very slow and can't download the file correctly.
So, we use "DownThemAll" to download the UBUNTU 8.10.
DownThemAll exist at addin of Mozilla firefox.
You can download it.
But I am not sure...............
:)

---

### Post by ugm6hr on 2008-11-07
> **beercz said:**
> What happens if you ignore the WUBI cd and insert the UBUNTU cd instead?

Isn't Wubi on the Ubuntu LiveCD as default any more?  It certainly was in Hardy.

If so - you should be able to install without the independently downloaded Wubi.

---

### Post by txfour on 2008-11-08
OK. I have it installed. However, the resolution is terrible. The highest setting I can go to is 800X600. How can I fix that? 

Also, how in the world do I get back to Windows Vista?

---

### Post by Teabicky on 2008-11-08
> **txfour said:**
> Also, how in the world do I get back to Windows Vista?

When you boot up you should be given the option to select Windows or Ubuntu.

Out of interest which method have you used to install Ubuntu?

---

### Post by txfour on 2008-11-08
> **Teabicky said:**
> When you boot up you should be given the option to select Windows or Ubuntu.

Out of interest which method have you used to install Ubuntu?

I just put the Ubuntu CD in and restarted the computer. I then told it to boot from optical drive. Then it took me through the partitioning stuff.

---

### Post by Elfy on 2008-11-08
Can you boot into ubuntu and open a terminal from the Apps> Accessories menu.

Run this command please and paste the output here, the l is a lower case L not a 1 - if you've not used password in a terminal yet it will be invisible.

```
sudo fdisk -l
```

Resolution - open System > Admin menu and run the Hardware Driver tool - if it says there's a driver for your card - enable it in the tool and it will be downloaded and installed for you.

---

### Post by ugm6hr on 2008-11-08
> **txfour said:**
> I just put the Ubuntu CD in and restarted the computer. I then told it to boot from optical drive. Then it took me through the partitioning stuff.

You didn't use Wubi then.

Hopefully you told it to resize the Vista partition, and only use a proportion of the HD (not the default setting of "use entire HD" which will have wiped Vista).

---

