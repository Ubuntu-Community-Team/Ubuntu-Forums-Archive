---
title: "No wifi on ubuntu 11.04"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by jrmchess on 2011-11-11
I have installed ubuntu 11.04 using wubi on my compaq presario V6430ee&#65279; laptop which has the primary OS as win xp but there is no wifi when I log in to ubuntu. The indicator for wifi is red instead of blue (showing that wifi is disabled). Can someone please help me? I am not very familiar with linux and ubuntu. I don't understand even basic commands so I would request you to please be a little easy on me. Thanks

---

### Post by rushikesh988 on 2011-11-11
try typing > lspci in terminal if that shows any device having name wireless card or only wireless then ur linux has detected Wifi Card..\


have u  checked in enable wireless and enable networking in wireless manager .... (its near sound on panel on top )

---

### Post by jrmchess on 2011-11-11
> **rushikesh988 said:**
> try typing  in terminal if that shows any device having name wireless card or only wireless then ur linux has detected Wifi Card..\


have u  checked in enable wireless and enable networking in wireless manager .... (its near sound on panel on top )

yes it shows that wireless connection is enabled but the indicator is still red and I cannot connect to the internet. Also how do I access my windows files and folders?

---

### Post by Maro848 on 2011-11-11
in response to accessing windows files I have yet to figure that out in a wubi install. This is easily done when it is actually installed in a separate partition on the hard drive by mounting the partition where windows in installed. But since you can't mount the windows partition in a wubi install (it's installed on the windows partition as a program) I'm sure it's a more complicated process I have had no luck with.

---

### Post by jrmchess on 2011-11-12
> **Maro848 said:**
> in response to accessing windows files I have yet to figure that out in a wubi install. This is easily done when it is actually installed in a separate partition on the hard drive by mounting the partition where windows in installed. But since you can't mount the windows partition in a wubi install (it's installed on the windows partition as a program) I'm sure it's a more complicated process I have had no luck with.

can u atleast help me with the wifi problem?

---

### Post by sadaruwan12 on 2011-11-12
Here try this steps and see if your wifi works.

Follow this [Link]("http://myfossness.blogspot.com")

---

### Post by jrmchess on 2011-11-12
> **Maro848 said:**
> in response to accessing windows files I have yet to figure that out in a wubi install. This is easily done when it is actually installed in a separate partition on the hard drive by mounting the partition where windows in installed. But since you can't mount the windows partition in a wubi install (it's installed on the windows partition as a program) I'm sure it's a more complicated process I have had no luck with.

Accessing windows files is very easy. just go to the terminal and type /host. I can't believe u never got such an easy one. how come u are an expert?

---

### Post by jrmchess on 2011-11-12
> **sadaruwan12 said:**
> Here try this steps and see if your wifi works.

Follow this [Link]("http://myfossness.blogspot.com")

these instructions are for an acer laptop. I have an hp one.

---

### Post by sadaruwan12 on 2011-11-12
> **jrmchess said:**
> these instructions are for an acer laptop. I have an hp one.

This laptop is not an acer it's a Lenovo it's my personal laptop and like to know did you tried the steps even the just to see if it works.

Remember to use the temporary method first if it works then move  and make it permanent.

Here is another link that might help you 'cos this helped  me  to solve mine.

[Click here]("http://ubuntuforums.org/showthread.php?t=1752835")

Last thing run lspci command and paste the out put here so we could know what type of a hardware we dealing with without knowing that it's well pretty much shots in the dark.

---

### Post by Matti L on 2011-11-12
My Compaq laptop needs Broadcom STA driver for wifi to work. Here are instructions for it:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

### Post by jrmchess on 2011-11-18
> **Matti L said:**
> My Compaq laptop needs Broadcom STA driver for wifi to work. Here are instructions for it:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

this installation requires you to have an internet connection and the only way I can connect to the internet on my ubuntu laptop is via wifi, which is what I am trying to get started. I didn't know using ubuntu would be so difficult. On a windows pc I would just have to download the driver on a pen drive, plug it in and install it directly from there. how do I do so on ubuntu?

---

