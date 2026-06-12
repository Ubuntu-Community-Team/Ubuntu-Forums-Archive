---
title: "Installing Progs"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by jnmyk on 2013-07-11
Hi, am trying to install projectM.   To make sure I have got the latest version I have downloaded the projectM-complete-2.1.0-Source.tar.gz     I have uncomressed the file into a directory projectM-complete-2.1.0-Source.  My problem is that now I have changed to this directory and typed ./configure but I get an error message  bash: ./configure: No such file or directory.   Obviously as a beginner at this sort of thing I am doing something wrong, but its not clear to me, seems a simple enough command.   Am running Ubuntu 12.04 LTS. Thanks for any replies  -  John

---

### Post by steeldriver on 2013-07-11
The source package you downloaded appears to use the cmake build system, rather than autotools - so it doesn't supply a 'configure' script 

The projectm library is in the standard repository so you can install that via apt-get / synaptic / software center - do you really need to build it from source? I would think that any players that use projectm libraries under the hood (clementine does, I think) would be built to use the repo version

---

### Post by jnmyk on 2013-07-11
Thanks for that steeldriver, I dont think I am ever going to get the terminal commands.  Ah well.  Once again I appreciate your help.  John

---

### Post by snowpine on 2013-07-11
Just clicky-clicky in the Software Center and you're good to go. This is the beauty of Ubuntu. :)

---

### Post by steeldriver on 2013-07-11
No problem - if you still want to have a go at building it, go for it - you will probably need to install the cmake package (I don't think it's included by default) and the build-essential package (for the g++ compiler and GNU make) and then you will need to figure out the dependencies (these will become apparent when you run cmake though). I'm happy to help - but I can't promise to know all the steps.

---

