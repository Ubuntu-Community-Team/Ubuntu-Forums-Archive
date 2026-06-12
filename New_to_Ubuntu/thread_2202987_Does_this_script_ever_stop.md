---
title: "Does this script ever stop??"
date: 2014-02-01
forum: New to Ubuntu
---

### Post by squakie on 2014-02-01
I'm getting rid of a couple of computers, and I wanted to "clear" the drives first.  I found this in a  tutorial for using the dd command on linuxquestions.org:

```
[If you're concerned about spies taking the platters out of your [hard drive]("http://skimlinks.pgpartner.com/mrdr.php?url=http%3A%2F%2Fskimlinks.pgpartner.com%2Fsearch.php%2Fform_keyword%3Dhard%2Bdrive"),  and scanning them using  superconducting quantum-interference  detectors, you can always add a "for" loop for US Government DoD  approved secure hard disk erasure. Copy and paste the following two  lines into a text editor. 
     [code]
     #!/bin/bash 
for n in `seq 7`; do dd if=/dev/urandom of=/dev/sda bs=8b con
```[/code]

I'm running this on one of the computers now, but can't tell if it's really doing anything - just the occasional flash of the disk activity light - I assume because of the block size.  However, will this thing ever actually stop on its own, or do I have to eventually kill it?  Nothing was mentioned about that in the linuxquestions.org tutorial.

---

### Post by spjackson on 2014-02-01
It will stop eventually. However, whether it will run for several hours or several days is very much dependent on your hardware. You would really need to take some measurements in advance to be able to come up with a reasonable estimate.

---

### Post by varunendra on 2014-02-01
Not sure about the code above, but a simple dd command with default 'bs' value (512 byte) should be fast enough to finish the job in half an hour to a couple hours depending upon the size of disk and processing power of the system doing this.

From [DD - Destroyer of Disks (Tinfoil Hat Paranoia)]("http://www.noah.org/wiki/Dd_-_Destroyer_of_Disks#Tinfoil_hat_paranoia") :
> Some people say that simply overwriting data isn't really secure because they heard that it's possible to read data that has been overwritten (this is known as data remanence). **This is a myth** for the necessity for using multiple random overwrites for security. This myth came about because Dr. Peter Gutmann theorized that overwritten data could be recovered through the use of Scanning Transmission Electron Microscopy. This is an unsubstantiated theory -- **no one has ever demonstrated recovering even a single bit of data using this technique**.

The normal command to overwrite the entire drive with zeros (*practically secure enough for the technology existing on this planet, not sure about the Martians*) -
```
sudo dd if=/dev/zero of=/dev/sda
```

Since you are trying to Destroy all the data on the disk anyway, I think there is no (additional) harm in aborting the process (Ctrl-Z or Ctrl-C) if it is taking too long.

Also, if the "Flash of (hard disk) activity light" is "occasional", I doubt if the code is actually doing anything at all, because even reading a drive should make the LED lit steadily.

---

### Post by squakie on 2014-02-01
It's a 60GB disk in an old P4 2.xGHZ  Dell Inspiron 8500.  I think I might try the /dev/zero and see if there better progress.  The other way has been running several hours now with no hint of completing.

EDIT:  I think it was a good idea to kill it - after all this time it had only written out 14GB!  I'm running the dd from /dev/zero right now and at least the hard disk light is on steady now!

---

### Post by spjackson on 2014-02-01
> **squakie said:**
> It's a 60GB disk in an old P4 2.xGHZ  Dell Inspiron 8500.  I think I might try the /dev/zero and see if there better progress.  The other way has been running several hours now with no hint of completing.

EDIT:  I think it was a good idea to kill it - after all this time it had only written out 14GB!  I'm running the dd from /dev/zero right now and at least the hard disk light is on steady now!
Note that the script overwrites the entire disk 7 times. When you kill the dd it will report how much it has written, but I don't think you will know whether that was for pass 1 or pass 7.

The processor speed is the limiting factor in determining how fast /dev/urandom generates random data. This can cause a delay before it is ready to write the next 4k. You will probably get different performance results with different values for bs. By using /dev/zero, you will always be able to generate data fast enough to keep up with the disk, hence the steady disk light.

---

### Post by squakie on 2014-02-01
I wonder - is there a /dev/null that can be used as input and write binary zeros to the drive (or is /dev/zero actuall a binary zero "device") ?

edit:  btw the original dd of random data I don't think even finished 1 pass.   It said 14GB copied in 5945.81 which I think comes out roughly a little over 1 1/2 hours.  Would have been a *LONG* wait ;)

Hopefulle the writes from /dev/zero will be a lot faster - I'd like to get some sleep but having booted of the live dvd, this old laptop keeps wanting to go to sleep.

---

### Post by varunendra on 2014-02-01
> **squakie said:**
> (or is /dev/zero actuall a binary zero "device") ?

Yup, it is. :)

---

### Post by squakie on 2014-02-01
Well, the writing of /dev/zero to /dev/sda completed a lot quicker than I expected.  It probably didn't hurt that I restarted it with a 4M block size - that kept the disk activity light solid.

So, I guess question solved.  Thanks everyone!

On the other system, I used the same method but with a block size of 16M for 750GB drive - went faster than I thought it would.  The 2 160GB drives I used a block size of 8M and ran both at the same time - they completed fairly quickly.

Quite satisfied with the results.  Thanks again, everyone!

---

