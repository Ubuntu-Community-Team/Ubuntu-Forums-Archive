---
title: "Jack input problems"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by simon303 on 2008-11-25
I am trying to use jack to get sound into my computer from an outside source.
It works when I connect it to my mic jack, but not my line-in.
The only connections in jack are for capture_1 and capture_2, but these refer to my mic jack.
Any way of getting these to refer to my line-in??
Thanks

---

### Post by simon303 on 2008-11-26
bump

---

### Post by simon303 on 2008-11-29
bump

---

### Post by simon303 on 2008-11-29
bump

---

### Post by simon303 on 2008-12-03
bump

---

### Post by markbuntu on 2008-12-03
If you are having a hardware problem, we need to know what hardware you have before we can help you. If it is a software problem, we need to know what OS you are using and which applications.

Vague questions are unlikely to get much for an answer.

---

### Post by simon303 on 2008-12-06
My hardware is an onboard sound card. Here is the information from the output of a configuration command:
```
id:	multimedia
description: 	Audio device
product: 	MCP67 High Definition Audio
vendor: 	nVidia Corporation
physical id: 	7
bus info: 	pci@0000:00:07.0
version: 	a1
width: 	32 bits
clock: 	66MHz
capabilities: 	pm msi ht bus_master cap_list
configuration:	driver	=	HDA Intel
		latency	=	0
		maxlatency	=	5
		mingnt	=	2
		module	=	snd_hda_intel
```
I have Jack installed on Ubuntu 8.04 and this works with all the programs it needs to, apart from an annoying almost clicking noise, as if it inserts gaps into my audio.
Currently in Jack the system:capture_1 and system:capture_2 inputs refer to my microphone jack on the card.
I am wondering if there is any way of configuring Jack so that it can have inputs that refer to my line in jack??

---

