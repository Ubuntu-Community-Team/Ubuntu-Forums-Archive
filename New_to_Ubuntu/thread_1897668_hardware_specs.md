---
title: "hardware specs?"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-12-19
how do u look up specifications of this netbook; processor speed, RAM size, manufacture of HDD....etc.?

---

### Post by philinux on 2011-12-19
> **Matrix01 said:**
> how do u look up specifications of this netbook; processor speed, RAM size, manufacture of HDD....etc.?

Software center and search for hardinfo

---

### Post by oldfred on 2011-12-19
+1 on hardinfo.

A couple more ways:
Files saved in your home folder
To save it as a file use
sudo lshw > hw.txt

HTML version of info
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

```
udevadm info --export-db > file.txt

Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

---

### Post by Matrix01 on 2011-12-23
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html 
this code works,
but

sudo lshw > hw.txt
does not work.

[ATTACH]209598[/ATTACH]

and this does not work;
sudo dmidecode > bios.tx
[ATTACH]209599[/ATTACH]


> **oldfred said:**
> +1 on hardinfo.

A couple more ways:
Files saved in your home folder
To save it as a file use
sudo lshw > hw.txt

HTML version of info
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

```udevadm info --export-db > file.txt

Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

---

### Post by _0R10N on 2011-12-23
Another source of hardware specs is on the /proc filesystem.

```
cat /proc/cpuinfo
```
```
cat /proc/meminfo
```

---

### Post by RealityMaster on 2011-12-23
System Profiler and Benchmark from Software Center shows just about anything you could want to know, except zfs info...

---

### Post by oldfred on 2011-12-23
sudo lshw > hw.txt

That puts a file named hw.txt into /home/fred or your home directory.
I just ran it and for whatever reason text editor would not open it, but abiword, kwork & openoffice docs edit all opened it?

sudo dmidecode > bios.tx
This opened with text editor withour issue. Should have been bios.txt, but does not really matter.

---

### Post by Matrix01 on 2011-12-24
that works,
thank u.

> **_0R10N said:**
> Another source of hardware specs is on the /proc filesystem.

```
cat /proc/cpuinfo
``````
cat /proc/meminfo
```

---

### Post by Matrix01 on 2011-12-24
i am not sure.
[ATTACH]209671[/ATTACH]

> **oldfred said:**
> sudo lshw > hw.txt

That puts a file named hw.txt into /home/fred or your home directory.
I just ran it and for whatever reason text editor would not open it, but abiword, kwork & openoffice docs edit all opened it?

sudo dmidecode > bios.tx
This opened with text editor withour issue. Should have been bios.txt, but does not really matter.

---

### Post by oldfred on 2011-12-24
I open with Nautilus but what then does this show. q to exit less.
less hw.txt
or 
less bios.tx
or correctly 
less bios.txt

---

### Post by The Cog on 2011-12-25
Using redirection with sudo can cause problems.
sudo lshw > hw.txt
can end up just writing a password prompt to hw.txt and then apparently freezing as it waits for the password that you don't even know it's prompting for. The easiest way around this is to do 
sudo ls
first, just to get the password into sudo. Then you can use sudo without it wanting a password again for the next few minutes.

---

### Post by Matrix01 on 2012-01-08
opened software center, and
clicked install on system profiler and benchmark,
that did not get installed.

> **RealityMaster said:**
> System Profiler and Benchmark from Software Center shows just about anything you could want to know, except zfs info...

---

### Post by Matrix01 on 2012-01-08
how do u look up version of BIOS?

> **_0R10N said:**
> Another source of hardware specs is on the /proc filesystem.

```
cat /proc/cpuinfo
``````
cat /proc/meminfo
```

---

### Post by WasMeHere on 2012-01-17
Hi,

I use
```
sudo lshw > hw.txt      # or
sudo lshw|less
```
If you have problems with it, I suggest that you use gksudo
```
gksudo lshw > hw.txt      # or
gksudo lshw|less
```
Maybe you need to install it
```
sudo apt-get install lshw
```
and I use the GUI program *hardinfo*
```
sudo apt-get install hardinfo
```

Have fun finding out :-)
Olle

---

