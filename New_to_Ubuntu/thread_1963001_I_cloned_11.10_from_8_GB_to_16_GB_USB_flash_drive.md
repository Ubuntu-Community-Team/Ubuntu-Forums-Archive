---
title: "I cloned 11.10 from 8 GB to 16 GB USB flash drive"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-21
Wow! Ubuntu is great!

Using Plop, I booted my 11.10 installed on a Sandisk 8 GB USB flash drive. 

I plugged a 16 GB Sandisk USB flash drive into a powered USB hub.

Using Applications/Accessories/Disk Utility I double checked that my system source 8GB USB flash drive was  /dev/sdb and my target 16 GB USB flash drive was /dev/sdd.

Simple, clear, straight forward.

Using terminal:

dd if=/dev/sdb of=/dev/sdd

It took awhile but every bit in /dev/sdb was copied to /dev/sdd

What really surprised me is that Ubuntu 11.10 allowed me to copy from a running system to a blank USB flash drive.

My first thought was that I needed a Live CD to copy from a flash drive not being used for the system.

I am now running on the cloned drive.

I am SOLD on Ubuntu!

---

