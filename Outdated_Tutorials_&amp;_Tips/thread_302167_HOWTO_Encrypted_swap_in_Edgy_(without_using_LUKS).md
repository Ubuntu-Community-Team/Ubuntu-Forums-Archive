---
title: "HOWTO Encrypted swap in Edgy (without using LUKS)"
date: 2006-11-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Stephen Howard on 2006-11-18
Not had any luck setting up LUKS swap partitions on Edgy?  Me neither ](*,)

This howto will setup an encrypted swap without using the LUKS extension.  I think that the problem with LUKS is that encrypted swap & tmp both generate their one-time keys from the /dev/urandom stream, but LUKS only wants a key with a specific end (usually a line in a keyfile or a user-typed password ended with an Enter keypress).  Whatever the reason, I couldn't get LUKS to work with /dev/urandom, so instead I used the underlaying cryptsetup system.  From a users perspective there's no difference at all.

Before you start, you'll need to have a specific /dev/ partition entry you want to dedicate to swap space.  Mine is /dev/hda5, but yours will likely be different.  To save you from a tragic cut&paste error I'll use /dev/hdaXX in this howto.  If you can't figure out your swap partition, you probably shouldn't be messing around with this stuff.

Instead of just listing the steps, I'll try and explain why.

**Step 0:  Make sure the target partition is not being used...**

We need the partition to be offline/unmounted/asleep for the operation we're about to perform on it.

First, turn off swap:
```
sudo swapoff -a
```Next, we look at /etc/mtab (that's the file where linux lists the filesystems and partitions its actually using).  Check that the partition you want to use isn't listed...

```
cat /etc/mtab
```If your partition is listed, then you need to unmount it (and also have a think about why it might be mounted - for instance, are you sure you've got the right partition??)...

```
sudo umount /dev/hdaXX
```


**Step 1:  Make sure we have available the necessary Ubuntu packages and crypto modules...**

The Ubuntu Universe repository includes the *cryptsetup* package.  We need to install this because it makes setting up encrypted partitions a breeze.  [COLOR="YellowGreen"]*(thanks to lprofil for pointing out this step)*[/COLOR]

```
 sudo apt-get install cryptsetup
```

We'll also manually load the crypto modules so that linux knows about them at the OS level (in a later step we'll configure linux to load them automatically).  The crypto modules form the software that the OS usues for the encryption/decryption of the data stored on the swap partition.

```
sudo modprobe -a aes dm_mod dm_crypt sha256
```PS: If you're not using the aes cypher, then substitute [FONT=Fixedsys]aes[/FONT] for the name of the cypher you want to use - [FONT=Fixedsys]blowfish[/FONT] for instance.  Also, remember to substitute your cypher name where ever [FONT=Fixedsys]aes[/FONT] appears in the subsequent steps.


**Step 2:  Overwrite the partition with random junk**

Unless you're really security conscious you can skip this step because it only overwrites any non-encrypted old data that might be sitting on the partition.

Also, this step can take a long time to complete (the actual duration depends on the size of the partition, but 10 minutes wouldn't be unusual).

[COLOR=Red]Note that there's no hope of recovering the partition's original data after this step.[/COLOR]  

```
sudo dd if=/dev/urandom of=/dev/hdaXX
```
Go and get a cup of coffee while this command completes.  If you get curious about its progress, you can get a status report by opening another terminal and typing the following nasty looking command (which actually just sends a "tell me what you're up to" signal to the dd command):

```
sudo kill -USR1 $(pidof dd)
```If you get bored waiting, its okay to just press ctrl-c and kill the 'dd' command.


**Step 3:  Create the encrypted swap partition**

Now we can start to build our encryption layer.  We're going to use the [FONT=Fixedsys]cryptsetup[/FONT] command to create the translation layer between the normal world and the encrypted world.  We'll name the translator device 'cswap' (just to remind us that its not a normal swap, but a **c**rypto **swap**).  You can of course name it anything, but if you do, remember to substitute your custom name where ever 'cswap' appears in the next steps.
```

sudo cryptsetup -c aes -h sha256 -d /dev/urandom create cswap /dev/hdaXX
```Just to convince ourselves that it worked, lets see if an entry was created in the device mapper...

```
ls /dev/mapper
```If there's a cswap entry listed, then we're almost finished.


**Step 4:  Turning the translator device into a swap drive**

The previous step created the encryption system overlay for the  partition. Now we need to format it into a swap filesystem that linux will recognise.

```
sudo mkswap /dev/mapper/cswap
```


**Step 5:  Turn swap on**

Now we point linux at our crypto swap partition.
```
sudo swapon /dev/mapper/cswap
```Just to convince ourselves that it worked, we can look to see if linux is using our swap

```
cat /proc/swaps
```If there's an entry there, then we're okay to make it permanent.


**Step 6:  Making it permanent**

We need to tell linux to use our special swap everytime we boot.

There are three separate files we need to edit.

First, we need to make sure that the crypto modules are available at boot time.  We do that by adding them to the /etc/modules file which is read by the linux init script during boot.

```
sudo nano /etc/modules
```...and add the following lines:
```
[FONT=Fixedsys]aes
dm_mod
dm_crypt
sha256[/FONT]
```Second, we tell the filesystem mounting program that we're using a special swap system:

```
sudo nano /etc/fstab
```Look for a line containing the word 'swap' and comment it out by appending a '#' as the first character.  
Then add the following new lines:
```
[FONT=Fixedsys]# Managed by /etc/crypttab
/dev/mapper/cswap    none    swap     sw    0   0[/FONT]
```Third, tell the crypto system that we want it to handle the swap partition
```
sudo nano /etc/crypttab
```
...and add the following line...
```
[FONT=Fixedsys]cswap   /dev/hdaXX   /dev/urandom   swap[/FONT]
```


**Step 7:  There is no step 7**

Phew, all done.  Reboot and [FONT=Fixedsys]cat /proc/swaps[/FONT] to see if linux is using your newly encrypted swap partition.  

It worked for me, so hope it works for you.

---

### Post by lprofil on 2006-12-12
Hi Stephen, 

thanks for your great tutorial!

It worked flawless for me. You are writing very verbose 
what i like very much. Nothing is left unclear. 

If i may notice that you should mention that 
one first have to install the package ***cryptsetup***

with:
```
apt-get install cryptsetup
```



/lprofil

---

### Post by Stephen Howard on 2006-12-15
Thanks lprofil, I've updated the how-to with your change.

---

