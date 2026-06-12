---
title: "how much RAM do I have on my computer?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by gotquestions on 2008-08-13
My brother gave me a new computer and I got no clue how much RAM or memory that it has. Could someone tell me what is the command so that I can find out?
I know there is some system monitor thing that can tell me but that is not what I am looking for. 

Thank you!!

---

### Post by starcannon on 2008-08-13
in a terminal type:

```
cat /proc/meminfo | grep MemTotal
```

or
```
free -m
```

You can also 

Left Click on a gnome-panel(tool bar at top of desktop)
Click on "Add to panel"
Highlight "System Monitor"
Click "Add"
Click on the System Monitor Applet that appears in the toolbar
Click on the Resources Tab

have fun

---

### Post by dje on 2008-08-13
```
sudo lshw -C memory
```
that should help ;)

dje

---

### Post by tuxxy on 2008-08-13
Or if you like to use the GUI, navigate to **applications > system tools > sysinfo > memory**

---

### Post by bump_ on 2008-08-13
I believe system monitor will tell you what you are looking for.

If you go to System -> Administration -> System Monitor 
and switch over to the resource tab, it will display how much memory is used and how much your total memory is.

If you want a terminal command, try

```
free -m
```

it will display your total memory under the total column in megabytes

---

### Post by Master Chief on 2008-08-13
> **tuxxy said:**
> Or if you like to use the GUI, navigate to **applications > system tools > sysinfo > memory**

But not before installing it first!


System -> Administration -> Synaptic Package Manager (use: "sysinfo" a search string).

---

### Post by Riba1122 on 2009-07-28
But is there a way to find out actually what's the capacity of each module and what's the frequency?

---

### Post by starcannon on 2009-07-28
> **Riba1122 said:**
> But is there a way to find out actually what's the capacity of each module and what's the frequency?
The command in post #3 of this thread should do that for you.
```
sudo lshw -C memory
```
 
You could also just enter Bios Setup at boot, and look there as well.

---

### Post by Riba1122 on 2009-07-28
*-memory
       description: System memory
       physical id: 1
       size: 767MiB

That's what it says about RAM... maybe it's different for you.
Will have to check the BIOS, hope it does the trick.

Thanks for the help :)

---

### Post by starcannon on 2009-07-29
> **Riba1122 said:**
> *-memory
       description: System memory
       physical id: 1
       size: 767MiB

That's what it says about RAM... maybe it's different for you.
Will have to check the BIOS, hope it does the trick.

Thanks for the help :)

Well unless you have 3 or more slots filled, the combo is likely 256 in one slot, 512 in the other. Most ram chips have the speed on a sticker; the slowest ram chip determines the speed of all ram chips.

Here's my lshw -C memory output; it shows total, and whats in each bank; doesn't show the speed of the ram though.
```
  *-memory:0
       description: System Memory
       physical id: 20
       slot: System board or motherboard
       size: 2GiB
     *-bank:0
          description: DIMM
          product: None
          vendor: None
          physical id: 0
          serial: None
          slot: A0
          size: 1GiB
          width: 64 bits
     *-bank:1
          description: DIMM
          product: None
          vendor: None
          physical id: 1
          serial: None
          slot: A1
          size: 1GiB
          width: 64 bits
     *-bank:2
          description: DIMM [empty]
          product: None
          vendor: None
          physical id: 2
          serial: None
          slot: A2
          width: 64 bits
     *-bank:3
          description: DIMM [empty]
          product: None
          vendor: None
          physical id: 3
          serial: None
          slot: A3
          width: 64 bits

```

---

