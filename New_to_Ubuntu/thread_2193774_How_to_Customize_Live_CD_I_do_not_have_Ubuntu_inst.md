---
title: "How to Customize Live CD? I do not have Ubuntu installed on the HDD."
date: 2013-12-14
forum: New to Ubuntu
---

### Post by geminiforex on 2013-12-14
I would like to create a customized live CD. I consider using Ubuntu Customization Kit. I do not have Ubuntu installed on my HDD.

I boot Ubuntu installation CD and click "Try Ubuntu".  "Add new software" and click "Ubuntu Customization Kit" etc. 

However, I must make sure that I have a non-compromised and genuinely clean Ubuntu Live CD because I will use it for financial transactions.

So - how can I be sure that I can be sure the downloaded "Ubuntu customization kit" by Ubuntu is the real one? I know there is a very low probability that the server is compromised. But even this low probability is a real problem for me because once I create the live CD, then I will use it for banking, for years without creating a new one. Who would want to have doubt for something he will use for years for banking and other financial transaction for long years and anything can happen anytime? In the software center I guess there is no file hash check possibility?

Anyway - I would like to check Ubuntu Customization Kit, in any way possible. With something similar to MD5-Sha etc. 

Should I download from linux ftp? Any way for this? How can I verify the originality?

And after installing it, I guess I can use the customization kit booting normally with an Ubuntu installation CD and "Try Ubuntu"? Or should I use it with an Ubuntu on HDD? (I do not have Ubuntu installed, as mentioned).

What can I do further to make sure I am really using a clean and genuine customized Live CD in all aspects?

---

### Post by Gone fishing on 2013-12-14
Sorry but this does not really answer your question but why not ...

Install Ubuntu as normal but  to a removable drive, install the grub boot loader to the mbr of the removable drive and then boot to that drive set it up as you want (using the normal repositories) and you have a portable OS as you want it. This would be more reliable than a live CD with no problems saving data back to the removable media unlike a CD, and it could be used with Windows machines etc.

---

### Post by deadflowr on 2013-12-14
```
apt-cache show uck
```

will give you all the info about that package including the hashes.

Three things though,
First you'll need an iso image of Ubuntu, separate from the one running.
And the image will need to be on a disk with at least 3GB of space.(4GB or more is better)
The image MUST be the same arch as whatever you are running the livecd on(32-bit, or 64-bit).

---

### Post by geminiforex on 2013-12-20
Thanks. So we will be able to check the hash. But where can we find the original hash # so we can compare and verify?

---

