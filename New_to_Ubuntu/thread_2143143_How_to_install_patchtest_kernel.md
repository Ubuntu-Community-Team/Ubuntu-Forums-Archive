---
title: "How to install patch/test kernel?"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by sremick on 2013-05-08
Background: I'm affected by the following: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/852190)

In the bug comments, you'll see that a user has put up a test kernel compiled with the patch:
[http://people.canonical.com/~sforshee/lp852190/linux-3.8.0-15.25~lp852190v201303291747/](http://people.canonical.com/~sforshee/lp852190/linux-3.8.0-15.25~lp852190v201303291747/)

I'm not clear on how to make use of those files. Here's what I'm running now:

3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Can someone walk me through the process to apply the patched kernel so I can make my wireless functional until the patch is baked-into Ubuntu proper? I'm on Xubuntu, if it matters. Thanks!

---

### Post by Doug S on 2013-05-08
Make some temporary folder on your local drive and copy the 4 files for whatever installation type you have (i386 or amd64 and the "all" one).
Then install them manually one at a time. An old old example from one of my computers:```
sudo dpkg -i linux-headers-3.5.0-030500rc6_3.5.0-030500rc6.201207072135_all.deb
sudo dpkg -i linux-headers-3.5.0-030500rc6-generic_3.5.0-030500rc6.201207072135_amd64.deb
sudo dpkg -i linux-image-extra-3.5.0-030500rc6-generic_3.5.0-030500rc6.201207072135_amd64.deb
sudo dpkg -i linux-image-3.5.0-030500rc6-generic_3.5.0-030500rc6.201207072135_amd64.deb
```I can never remember the correct order for the header files, but dpkg will complain if it is backwards, and in that case do the other one first. Since you are already on a more recent kernel you will have to select the test one from the grub menu during boot up. I always increase the grub timeout to give myself more time to see it. In /etc/default/grub change to this:```
GRUB_TIMEOUT=10
```and then run:```
sudo update-grub
```

---

