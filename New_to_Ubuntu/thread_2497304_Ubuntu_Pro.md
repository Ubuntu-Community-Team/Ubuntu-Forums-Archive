---
title: "Ubuntu Pro"
date: 2024-04-29
forum: New to Ubuntu
---

### Post by ne-nosok on 2024-04-29
How to remove machine frome Ubuntu Pro

---

### Post by #&amp;thj^% on 2024-04-29
I use this, with more to it:
```
sudo pro detach
```

Apparently it does not remove the "esm repository", so you will have to remove them yourself.

 You can move the file from "etc/apt/sources.list.d" somewhere safe and see if that is sufficient.

---

### Post by deadflowr on 2024-04-29
pro detach 
maybe 
sudo pro detach

???

ninja'd

---

### Post by JFJanssen on 2024-05-06
That helps, thanks.

I have installed a machine yesterday, and added it to Ubuntu Pro as well as the installation I have done today.
Yesterdays installation ran into problems, and therefore that installation is now gone - it does not exist anymore.
Can that installation still be detached? It now takes up one of the five spots in the free tier for Ubuntu Pro, which is inconvenient.

---

### Post by #&amp;thj^% on 2024-05-06
> **JFJanssen said:**
> That helps, thanks.

I have installed a machine yesterday, and added it to Ubuntu Pro as well as the installation I have done today.
Yesterdays installation ran into problems, and therefore that installation is now gone - it does not exist anymore.
Can that installation still be detached? It now takes up one of the five spots in the free tier for Ubuntu Pro, which is inconvenient.

Million Dollar question, but with no answer to date.
You may have to get hold of  and ask canonical to disable one or all, then re-enroll any you want enrolled outside of that I've not seen anyway else to fix it. in your request :(

---

### Post by BBQdave on 2024-05-06
[https://documentation.ubuntu.com/pro/](https://documentation.ubuntu.com/pro/)

Might have information on how to disconnect from Ubuntu Pro. Ubuntu Pro does not have a *disconnect* or *stop service* option in Ubuntu Pro account. Just buttons to activate tokens to connect your machine to Ubuntu Pro.

---

### Post by Dennis N on 2024-05-06
> It now takes up one of the five spots in the free tier for Ubuntu Pro,
The machine limit In the Ubuntu Pro Dashboard is the number of active machines you have, not attached machines. You are limited to 5 active machines. An active machine is one that has pinged the Cannonical server in the past 24 hour period. If it does not, it becomes inactive and does affect the count again until you use it.

From Cannonical:
"why we don&#8217;t prevent you from attaching more machines than the number of entitlements you have (either free or paid). Instead, we monitor how many active machines you have at any given moment. In other words, you should ensure that the number of active machines does not go over the limit."

---

### Post by VMC on 2024-05-07
> **Dennis N said:**
> The machine limit In the Ubuntu Pro Dashboard is the number of active machines you have, not attached machines. You are limited to 5 active machines. An active machine is one that has pinged the Cannonical server in the past 24 hour period. If it does not, it becomes inactive and does affect the count again until you use it.

From Cannonical:
"why we don’t prevent you from attaching more machines than the number of entitlements you have (either free or paid). Instead, we monitor how many active machines you have at any given moment. In other words, you should ensure that the number of active machines does not go over the limit."

I wondered about this. I added a few Pro machines and was worried I'd run out of the entitled five. Thanks for the info!

---

### Post by keshara283 on 2024-05-11
> **VMC said:**
> I wondered about this. I added a few Pro machines and was worried I'd run out of the entitled five. Thanks for the info!

Hi, I just tested this on my end as I was pretty curious. I left my laptop that has an Ubuntu Pro registration attached powered off for the last 2 days. When I checked on my Ubuntu Pro Dashboard, it was saying I only had 1 machine active (my Desktop as expected).

I then powered on my laptop and ran through the usual updates. After checking my Ubuntu Pro Dashboard again, the laptop was now displaying on the Dashboard as another active machine.

---

### Post by Tadaen_Sylvermane on 2024-05-11
> **Dennis N said:**
> The machine limit In the Ubuntu Pro Dashboard is the number of active machines you have, not attached machines. You are limited to 5 active machines. An active machine is one that has pinged the Cannonical server in the past 24 hour period. If it does not, it becomes inactive and does affect the count again until you use it.

From Cannonical:
"why we don&#8217;t prevent you from attaching more machines than the number of entitlements you have (either free or paid). Instead, we monitor how many active machines you have at any given moment. In other words, you should ensure that the number of active machines does not go over the limit."

This indeed. I've hopped around to and from Debian / Ubuntu / Arch. Each time I've done the ```
pro attach
``` To date there are no machines currently listed on my Ubuntu Pro dashboard as I've been running a pure Debian build for awhile now. Not once have I manually ```
pro detach
``` to any of those installations.

---

