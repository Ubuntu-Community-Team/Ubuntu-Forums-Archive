---
title: "I need to get the basic-essential compilers"
date: 2007-11-04
forum: Packaging and Compiling Programs
---

### Post by Martyhartwell on 2007-11-04
Hi 
My name is Marty, I am new to Ubuntu and am trying to load some apps that don't appear on any of the repositories. So I will need to compile one or maybe more. However I don't think I have the "basic-essential compiler" package and don't seem to be able to find it to load it. It may be on the system already so how can I look for it, I have tried to see if it shows up in the synaptic package manager. Also can someone point me to a page on the online manual to the sequence of events to load new apps. My past experience about 4 years ago with Unix Sys admin. doesn't help much here. Systems so alike but so different.
Thanks Marty

---

### Post by 3rdalbum on 2007-11-05
It is called "build-essential", and you can find it in Synaptic Package Manager.

I'm not sure how much Unix experience you had, but here are some tips for you when compiling:

1. If you want the basic software, you can just run ./configure and then make and sudo make install. However, you can activate advanced, bleeding-edge or license-dubious features in many packages. Run ./configure --help for more information on what is available to activate and how to do it.

2. Install the "checkinstall" package. Then, instead of running "sudo make install", you run "sudo checkinstall". This will create a Debian package of the source code, so it becomes easy to remove the program if you don't want it!

3. When you run the ./configure step, it will probably complain that you're missing certain libraries. For instance, it might say that you're missing "libflac". But then you look in Synaptic and see that you do have "libflac" installed. Don't worry, you've got to install the -dev packages for the compilation step. So, you would install "libflac-dev" and run the configure script again.

---

