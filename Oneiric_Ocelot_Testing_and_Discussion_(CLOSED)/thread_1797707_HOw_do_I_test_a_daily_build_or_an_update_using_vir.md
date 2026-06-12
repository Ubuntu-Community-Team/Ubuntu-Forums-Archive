---
title: "HOw do I test a daily build or an update using virtualization?"
date: 2011-07-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-07-05
Hello everyone,

Because of the risks in Oneiric's daily build or daily update, I would like to know how I can use an open-source virtualization tool like Vbox, Vmware or Zen to test it out?

I want to make sure everything works before burning the iso image of the daily build or applying the update.

Thanks in advance for your help.

:)

---

### Post by lucazade on 2011-07-05
Yes, you can use a virtual machine to test Oneiric, I personally use Virtualbox but also the others should be ok.

Only problematic thing could be guest additions to get 3D/Unity/GnomeShell working because during alpha stages are usually broken, for the rest is ok.

---

### Post by dino99 on 2011-07-05
be aware that virtualization is a kind of sandbox, so results by testing into it can be very different compared to a real install (dedicated partition)

---

### Post by castrojo on 2011-07-05
You can use testdrive-gtk for this, it even snags the ISO for you and can update it every day and then launch it for you.

---

### Post by lucazade on 2011-07-05
nice, I didn't know testdrive

"TestDrive is a project that makes it very easy to download and run the latest daily Ubuntu development snapshot in a virtual machine. Actually, it can be configured to download and run any URL-access ISO in a virtual machine.

But the primary goal is to provide a very simple method for allowing non-technical Ubuntu users to test and provide feedback on the current Ubuntu release under development"

---

### Post by fjgaude on 2011-07-05
I run a grub iso install each day from the dailies. I also have on iso installed in VMware Player and keep it updated using apt-get or Synaptic several times each day.

The Player's VM is Unity 2D and the grub iso is 3D. Both seem a little different from each other but I do issue bug reports as things break... it's interesting to watch the progress the guys make, what a complex issue.

Any questions?

---

### Post by iClouseau88 on 2011-07-05
Hello castrojo,

I installed testdrive-gtk via Synaptic.  Since I cannot find the TestDrive icon anywhere in Unity2D desktop, I had to use the terminal to start.  Here's how I did:

```

sudo su
Password:

```

```

# /usr/bin/testdrive-gtk

```

File > New > Select (K)(X)Ubuntu distro >Sync

Downloading oneiric-desktop-i386.iso (This took my pc about an hour on DSL)

Launch

QEMU > Select "try Ubuntu"

After a brief simulation, the screen shows "Unity2D has crashed, your system does not have enough menory to report...."

My question: How do I allocate or set aside more memory (I have 4 GB RAM installed in the PC which has AMD x2 64bit cpu) to the virtual machine before running the program TestDrive?

Thanks in advance for your help.

:)

---

### Post by castrojo on 2011-07-06
Testdrive puts its settings in .testdriverc. In there you'll see it just calls KVM, so you'd put the memory setting in that line. 

I don't remember offhand the command line switch to kvm, so you'd look in the manpage or kvm --help will let you know.

---

### Post by iClouseau88 on 2011-07-06
Hello castrojo,

Thanks for your reply.  I found the answer:

1. sudo gedit /etc/testdriverc

2. Line 28: change MEM=384 (MB, default) to MEM=1024

3. Save file & quit.

---

