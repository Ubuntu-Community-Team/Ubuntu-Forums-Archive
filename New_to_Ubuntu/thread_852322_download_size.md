---
title: "download size"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by a511475 on 2008-07-07
i bought ubuntu from best buy and took it home and installed it  on a computer with a 250 gb hard drive.  when i installed the os, everything was  fine.  Unter places it  says I have a 196gb media.  I assume that is free space.
When I try to down load a 3.3 gb file or transfer picturesfrom another machine,  less then 12 gb, I get the error message I have not  enough room.  I am using the dafault download location, the desk top.

WHAT AM I DOING WRONG???

---

### Post by BlueSkyNIS on 2008-07-07
Hi, welcome to Ubuntu community! :)

Possible reason of failure: you are probably trying to put the big file on root partition which is to small to hold it.

Can you do this, please:

Go to Application -> Accesories -> Terminal and into Terminal type:

```
sudo fdisk -l
```

You will be asked for your password and paste the contents here. After that type this:

```
cat /etc/fstab
```

And again paste the contents here.

This will print some information how is your HD set up.

---

### Post by snowpine on 2008-07-07
> **a511475 said:**
> i bought ubuntu from best buy and took it home and installed it  on a computer with a 250 gb hard drive.  when i installed the os, everything was  fine.  Unter places it  says I have a 196gb media.  I assume that is free space.
When I try to down load a 3.3 gb file or transfer picturesfrom another machine,  less then 12 gb, I get the error message I have not  enough room.  I am using the dafault download location, the desk top.

WHAT AM I DOING WRONG???

It sounds like Ubuntu is occupying a small "partition" of your hard drive instead of using the whole 250gb. Are you trying to "dual boot" with another operating system such as Windows, or is Ubuntu the only OS you want on the computer?

---

### Post by annda on 2008-07-07
to find out reliably how much free space you have on different partitions (mounted, that is actually used at the time by ubuntu), try this in the terminal

```
df -h
```

EDIT: depending on your version of ubuntu, there may be a GUI tool available at applications > accessories > disk usage analyzer. for best results use 'scan filesystem'

---

### Post by snowpine on 2008-07-07
When you installed Ubuntu, you had to answer some questions about partitioning your hard drive. Do you remember what you answered? If I had to guess, you already had Windows installed on the computer, and you answered "resize existing partition and use freed space." Does that sound accurate?

---

### Post by kansasnoob on 2008-07-07
Well, I'm a gui guy! (Go ahead and laugh but I'd be willing to bet that those who've spent gazillions of hours creating gui's appreciate guys like me.)

If you're using Ubuntu Hardy Heron, as I am, I believe you'll have to go to System > Administration > Synaptic Package Manager, then click on search, and then type

> gparted

and install gparted.

Then go to System > Administration > Partition Editor and look at what you have.

NOTE: I said LOOK! Do not change anything!

Mine looks like this right now:

[ATTACH]76774[/ATTACH]

I can easily see that I have a 29gb Win partition and a 45gb Ubuntu partition with less than 5gb used and more than 38gb free.

That's invaluable to "plan" anything.

To post a screenshot of yours just go to Accessories > Take Screenshot. I find selecting a 2 second delay is helpful.

---

### Post by a511475 on 2008-07-07
> **kansasnoob said:**
> Well, I'm a gui guy! (Go ahead and laugh but I'd be willing to bet that those who've spent gazillions of hours creating gui's appreciate guys like me.)

If you're using Ubuntu Hardy Heron, as I am, I believe you'll have to go to System > Administration > Synaptic Package Manager, then click on search, and then type



and install gparted.

Then go to System > Administration > Partition Editor and look at what you have.

NOTE: I said LOOK! Do not change anything!

Mine looks like this right now:

[ATTACH]76774[/ATTACH]

I can easily see that I have a 29gb Win partition and a 45gb Ubuntu partition with less than 5gb used and more than 38gb free.

That's invaluable to "plan" anything.

To post a screenshot of yours just go to Accessories > Take Screenshot. I find selecting a 2 second delay is helpful.

Hi!!
I think you are telling me that I may have a small space to run my new OS in.  To correct this problem, if it is that problem is to repartition and reformat the drive and then install the OS?
before I just booted from the disk and installed the OS.  Thought it would take over the whole drive.  I will look at it tomorrow.

---

