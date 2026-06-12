---
title: "flash plugin not loading"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by aneez004 on 2012-11-09
The main issue is that flash is not loading in sites like youtube.
It is showing "could not load shockwave flash" at the top and "couldn't load plugin" on the playing window.

I have installed flash-plugin (adobe) and checked that plugin is enabled in chrome (chrome://plugins).

It is installed, but it is not loading. Please suggest solutions.

---

### Post by aneez004 on 2012-11-09
no one here to help me out. 

That's sad.

---

### Post by slickymaster on 2012-11-09
Try this:

Post this command in a terminal: sudo apt-get install default-jre

This will give you full Java support, then open Synaptic package manager and type "flash" in search and then right click the package and add the "Suggested" packages.

Did you fully update the system?

---

### Post by slickymaster on 2012-11-09
By the way, keep in mind that Shockwave and Flash are two different products and there is no linux version of shockwave.

---

### Post by aneez004 on 2012-11-09
> **slickymaster said:**
> Try this:

Post this command in a terminal: sudo apt-get install default-jre

This will give you full Java support, then open Synaptic package manager and type "flash" in search and then right click the package and add the "Suggested" packages.

Did you fully update the system?
Thank you for your reply. Let me try. May I know what is default-jre?

---

### Post by aneez004 on 2012-11-09
> **slickymaster said:**
> By the way, keep in mind that Shockwave and Flash are two different products and there is no linux version of shockwave.
But it is showing like that

---

### Post by slickymaster on 2012-11-09
> **aneez004 said:**
> Thank you for your reply. Let me try. May I know what is default-jre?

It's the default version of Java that Ubuntu uses.

---

### Post by slickymaster on 2012-11-09
> **aneez004 said:**
> But it is showing like that

Shockwave plays back applications built with Adobe Director, a multimedia and application development program also used to make interactive CD-ROM's and kiosks. 

Flash plays back applications built with Adobe Flash, a vector animation program that also can be used to build applications.

---

### Post by SeijiSensei on 2012-11-09
I've found the most reliable way to install flashplayer is to retrieve it from the partner repository.

Use your package manager to activate the "partner" repository, or simply remove the hash mark from the beginning of the line:

```
deb http://archive.canonical.com/ubuntu precise partner
```

in /etc/apt/sources.list.  Then update the repositories and install adobe-flashplugin.  From the command line you can simply do:

```

sudo apt-get update
sudo apt-get install adobe-flashplugin

```

I've never had any problem watching videos at YouTube (or anywhere else) when I use this method.

---

### Post by aneez004 on 2012-11-09
> **SeijiSensei said:**
> I've found the most reliable way to install flashplayer is to retrieve it from the partner repository.

Use your package manager to activate the "partner" repository, or simply remove the hash mark from the beginning of the line:

```
deb http://archive.canonical.com/ubuntu precise partner
```

in /etc/apt/sources.list.  Then update the repositories and install adobe-flashplugin.  From the command line you can simply do:

```

sudo apt-get update
sudo apt-get install adobe-flashplugin

```

I've never had any problem watching videos at YouTube (or anywhere else) when I use this method.
Thank you for your reply. Let me try it

---

