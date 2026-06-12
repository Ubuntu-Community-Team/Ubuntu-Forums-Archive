---
title: "Reading NAS JBOD drives"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by badbob100 on 2008-09-09
I'm taking out the two 320GB HD from my D-Link DNS-323 and fitting them to my HTPC. Then going to fit two 1TB drives in the DNS-323. The two 320GB drives are in JBOD layout. I've installed the IFS utility in Windows but I don't believe this will read a JBOD disc, wheras Linux will. Once I boot up from a Ubuntu 8.04 64bit Live CD what will I need to do to mount the two 320GB as JBOD, or will it detect and mount them automatically?

I only want to copy the data across the LAN to the new 2TB storage, they can then be partitioned as NTFS for the other computer.

---

### Post by OO-Dragon on 2009-02-19
I have the same issue actually... well almost.  I pooped my DNS-323 and I am trying to get the data off my 2 1TB drives i setup as JBOD.  Can some one help me do so?  

Thanks!

---

### Post by OO-Dragon on 2009-02-20
Ok, after much research, I found how to access my DNS-323 JBOD configed data from a computer.  Unfortunately I have NOT found a way to do it in windows, but have in Ubuntu.

Step 1.  Install ubuntu 

Step 2.  Install Mdadm  

sudo apt-get update
sudo apt-get install mdadm

Once that's installed and you restart, it should show as a removable drive! 

Hope that helps any other people with this problem.

---

### Post by Lutz Klein on 2011-09-12
Thank you for sharing this. 
I just got it working with my harddrive from a Zyxel NSA-210.

---

