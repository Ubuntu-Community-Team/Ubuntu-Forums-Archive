---
title: "adamm's 8.04.1 not installing to Asus 901"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by aspergerian on 2008-08-20
My Asus 901 arrived today (I have a 701). Some of the 901's notorious problems arose right away. I've been following AdamM's development of a ubuntu 8.04.1 and tried his installation procedure [http://array.org/ubuntu/setup.html](http://array.org/ubuntu/setup.html)

I copied all the commands he presents and pasted them into terminal. Wasn't sure whether to leave the terminal in home user or a higher level directory. Tried both ways, copying his commands correctly. 

Here's the last command for installation:
sudo apt-get install linux-eeepc 

After that, terminal told me: 

The following packages have unmet dependencies:
  linux-eeepc: Depends: linux-image-eeepc (= 2.6.24.20.22) but it is not going to be installed
  linux-headers-eeepc: Depends: linux-headers-2.6.24-20-eeepc but it is not going to be installed
E: Broken packages
nux-headers-eeepc:

----
What am I missing or doing wrong? 


Thank you.

---

### Post by aspergerian on 2008-08-20
More info. Adamm's intall offers 3 steps,

1. Install the eeepc-optimized kernel
      sudo apt-get install linux-eeepc linux-headers-eeepc
2. Reboot.
3. During GRUB's initialization, press <ESC> to open the boot options menu.
If the new kernel labelled "2.6.24-20-eeepc" is not at the top of the boot list, scroll down to it and hit enter. 

Each time I followed the instructions and rebooted, the option "2.6.24-20-eeepc" did not appear, nor did anything similar appear. The only option offered was a "HD" location that booted me into the Asus OS I'm hoping to escape. 

Thank you.

---

