---
title: "Speed-up custom kernel build process."
date: 2016-06-17
forum: Packaging and Compiling Programs
---

### Post by nikefalcon on 2016-06-17
Hi,

I have been using a patched ubuntu kernel that I compiled based on the instructions on [this page]("https://samvde.wordpress.com/2015/10/23/howto-compile-an-ubuntu-kernel-with-bfq-support-example-wily-2/"). I have a slow internet connection, so downloading the sources, ABI and building the kernel takes up much longer than I'd like- it would be nice if were to be faster next time. While running ```
bash debian/scripts/misc/getabis <kernel ver> 
```, I noticed that the script downloads ABI files for many architectures(other than amd64, which I assume :-k is the only one I need). Is anyone here aware of any way to restrict the download to only one architecture? 
Seeing as my scripting skills are rudimentary, taking a cursory glance at the script source did not help one bit. Hope some wise souls can enlighten me. 

Regards

---

### Post by nikefalcon on 2016-07-07
After some reading through the script..
Think I found an answer to this one. 
[LIST=1]
[*]From linux source root, open ```
debian.master/etc/getabis
``` 
[*]Remove all the "getabis" lines with architectures/flavors that you do not need. 
[*]Proceed to download ABIs, build kernel. 
[/LIST]

---

