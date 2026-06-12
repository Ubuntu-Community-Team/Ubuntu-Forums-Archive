---
title: "Problem with Cairo-dock in Ubuntu 8.10 &gt;????"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by gustav777 on 2008-11-16
I am want to install Cairo-dock in this ubuntu but when I start to install:

 E: /var/cache/apt/archives/cairo-dock_1.6.3.1_amd64.deb: trying to overwrite `/usr/share/cairo-dock/default-indicator.png', which is also in package cairo-dock-data

What can I do??? In previouse version of Ubuntu Cairo-dock works perfectly.

---

### Post by 73ckn797 on 2008-11-16
> **gustav777 said:**
> I am want to install Cairo-dock in this ubuntu but when I start to install:

 E: /var/cache/apt/archives/cairo-dock_1.6.3.1_amd64.deb: trying to overwrite `/usr/share/cairo-dock/default-indicator.png', which is also in package cairo-dock-data

What can I do??? In previouse version of Ubuntu Cairo-dock works perfectly.

A "png" file is an image. I would not be too concerned and allow the over write.

---

### Post by fabounet on 2008-11-17
package conflict.
remove the packages from Ubuntu, re-install from the official repository.

---

### Post by SerafeimG on 2008-11-24
> **fabounet said:**
> package conflict.
remove the packages from Ubuntu, re-install from the official repository.


I have the same problem. Can you tell me how I can do this??

---

### Post by crjackson on 2008-11-24
> **gustav777 said:**
> I am want to install Cairo-dock in this ubuntu but when I start to install:

 E: /var/cache/apt/archives/cairo-dock_1.6.3.1_amd64.deb: trying to overwrite `/usr/share/cairo-dock/default-indicator.png', which is also in package cairo-dock-data

What can I do??? In previouse version of Ubuntu Cairo-dock works perfectly.

You have installed Cairo-Dock previously and you are now attempting to install it again over top of the already installed version.

You need to remove & purge the old version first, then proceed to install the newer version.

---

### Post by crjackson on 2008-11-24
> **SerafeimG said:**
> I have the same problem. Can you tell me how I can do this??

Open up the synaptic package manager under System>Administration and completly remove (including configuration files)your currently installed version.

Once the old version is cleaned out, the new version should install without any problem.

---

### Post by crjackson on 2008-11-24
> **73ckn797 said:**
> A "png" file is an image. I would not be too concerned and allow the over write.

Install will not complete until he purges the old version. Ignoring the png file won't help. In my experience, it must be removed to continue.

---

