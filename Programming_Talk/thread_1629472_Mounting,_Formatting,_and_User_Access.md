---
title: "Mounting, Formatting, and User Access"
date: 2010-11-23
forum: Programming Talk
---

### Post by teqsun on 2010-11-23
I am a semi-newb linux sysadmin - programmer.  I say semi-newb because I have been at it for 2 years.  I still feel like I am just barely grasping 10% of how linux works.

At work I came up with a great system to help us duplicate SD cards on the fly.  I wrote a small shell script to **Format**, **Mount**, **Copy Files**, and then **Uunmount**.

I have it figured out how to assign the drives and get all the above worked out...  Only problem is that I have to give sudo access to the user running the script or else the processes described above will fail.  

I added a nifty little snippet I found on the internet to verify the user running the application is root (though sudo or su)

Currently I have only one user working on this machine who is less savy than myself but still competent in linux.  

I plan on adding more users to the system and I don't want them to all use the same login and I don't want them to have sudo or su access!

I have heard of chroot jailing users to specific directories but I do not see how this will help in this sittuation. 

Is there a way for me to bypass the need for the user to be sudo or root in order to mount/format/unmount a volume?

Any help is most appreciated.

---

