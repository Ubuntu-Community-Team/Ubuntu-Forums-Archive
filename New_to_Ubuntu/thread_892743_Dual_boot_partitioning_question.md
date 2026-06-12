---
title: "Dual boot partitioning question"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by asphaltninja on 2008-08-17
Ok so I already had Windows XP installed and am setting up Ubuntu. Created the swap, root and home partitions. My question is regarding the Windows partition. What options do I select for "Use as: "(currently has the "do not use this parition" option selected), and "Mount point :"(currently unchangeable, I assume has something to do with the former having the "do not use this partition" option selectet). Thanks in advance.

---

### Post by Elfy on 2008-08-17
Don't change anmything to do with the win partitions, use the edit window to make sure that / and /home have their mount points set and use as - ext3 (from memory)

Add the windows partitions later in a file called fstab

---

### Post by asphaltninja on 2008-08-17
> **forestpixie said:**
> Don't change anything to do with the win partitions, use the edit window to make sure that / and /home have their mount points set and use as - ext3 (from memory)

Add the windows partitions later in a file called fstab

So I leave the "do not use this partition" option selected for the windows partition and just install Ubuntu?

---

### Post by Elfy on 2008-08-17
When I use the manual partitioner on an install the only partitions I touch in anyway at all are those I migh be installing on - the / and /home when I use one.

I don't edit or make any changes to other partitions.

---

### Post by caljohnsmith on 2008-08-17
> **asphaltninja said:**
> So I leave the "do not use this partition" option selected for the windows partition and just install Ubuntu?
Yes. :)

---

### Post by kansasnoob on 2008-08-17
> **caljohnsmith said:**
> Yes. :)

+1

I just read a post about someone making other changes to a Windows partition during install ............. NOT a good thing to do!

Resize only! You're only making new space available for Linux!

---

### Post by egalvan on 2008-08-17
> **forestpixie said:**
> Add the windows partitions later in a file called fstab

I've installed Hardy (8.04.1) on three different WinXP machines and I've not messed with fstab on any, and the win partitions are all visible. Internal drives and external USB, all show up in "Places" and when I click on them, they appear on the desktop.

What am I doing right?

Or is this the norm for the new Hardy?

:popcorn:

---

### Post by asphaltninja on 2008-08-17
Just to follow up, I didn't change anything and left the "do not use this partition" option selected and everything worked fine. Thanks guys.

---

### Post by Elfy on 2008-08-17
> **egalvan said:**
> I've installed Hardy (8.04.1) on three different WinXP machines and I've not messed with fstab on any, and the win partitions are all visible. Internal drives and external USB, all show up in "Places" and when I click on them, they appear on the desktop.

What am I doing right?

Or is this the norm for the new Hardy?

:popcorn:
Have you installed the ntfs tool to get read write for the internal drives? That adds to fstab, but I'm not completely sure as I haven't had ntfs since feisty.

---

### Post by kansasnoob on 2008-08-17
> **egalvan said:**
> I've installed Hardy (8.04.1) on three different WinXP machines and I've not messed with fstab on any, and the win partitions are all visible. Internal drives and external USB, all show up in "Places" and when I click on them, they appear on the desktop.

What am I doing right?

Or is this the norm for the new Hardy?

:popcorn:

That's the way it DOES work if you keep it simple!

Ubuntu's installer makes it very simple! I've just done a couple of Simply MEPIS installs and Ubuntu is soooooooooo much easier!

The point is that if you're a total nOOb like me you can keep it very simple! Ubuntu allows you crawl before you walk, and walk before you run!

---

