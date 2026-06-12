---
title: "Tips required for Ubuntu crash course"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by stube40 on 2008-11-14
Hello everyone,

This is my first post, please let me briefly introduce myself - I am an embedded systems engineer with 15 years of experience related to coding of firmware and software in C and C++ across 8-bit, 16-bit and 32-bit (Win32s) systems. I am well versed in Microsoft development environments such as Visual Studio and Embedded Visual C++.

I am starting a new job soon and they are very Linux orientated - I would like to give myself a crash course on Linux to get a head start so as I don't embarrass myself.

I'm currently downloading Ubuntu and will install it on a spare PC I have. After that, I'm looking for tips on exercises I can do that will bring me up to speed in the shortest space of time.

Obviously, they'll be looking to see I can use Linux proficiently, hence command line stuff I imagine is imperative. After that, I imagine it would be good to be able to install a C compiler and compile one of my C or C++ projects and get something useful running.

If anyone has any suggestions, I'd love to hear then.

Thanks alot,
Stuart.

---

### Post by mapes12 on 2008-11-14
Hi Stuart

I guess you will be deluged with stuff but here are my suggestions:

[http://www.aboutdebian.com/](http://www.aboutdebian.com/)

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by iponeverything on 2008-11-14
It pretty easy to learn, you have a very large toolbox in /bin, /usr/bin, /sbin and /usr/sbin. They are full tools that can be strung together in number of ways -- pipes, i/o redirection, etc.. There is your shell interpreter -- bash is quite nice.  It's good to learn a bit of shell programing to automate repetitive tasks, learn about shell expansion and regex. Process control is must. Learn the the file system basics -- structure and general design, nothing to in depth.  Basics of sockets and pipes under unix. Programing editors like vi and emacs.  -- Emacs is very powerful and can do some absolutely amazing things, I would devote some time to learning how to use it, it will be worth it in the long run. Vi is also a must, on many devices -- if you have a shell available often the editor on it will be vi, because of its small size.

Google "unix learn" for a ton tutorials with exercises, to learn to command line basics.

---

### Post by Irihapeti on 2008-11-14
I have nothing like the op's experience, but I find the Advanced Bash-Scripting Guide very helpful for shell scripting. It's in the repositories - at least, in Hardy - and can be installed with
```
sudo apt-get install abs-guide
```

There may be a more up-to-date version at [http://personal.riverusers.com/~thegrendel/](http://personal.riverusers.com/~thegrendel/)

---

### Post by Kellemora on 2008-11-14
Hi Stube

If they are a business, more than likely they are using RedHat so they would have the commercial backup needed when things go wrong.
If they don't or won't pay for that, then they may be running CentOS or equivalent.

Ubuntu is Debian based and there are a WHOLE LOT of things different between RedHat and Debian based systems.

It might be wise to try and found out what their BASE system is before you put too much into studying how things are done.

I was fairly proficient in older RedHat, but was totally lost in Ubuntu at first!  Well, I'm still LOST as far as reality goes, hi hi.........

TTUL
Gary

---

### Post by stube40 on 2008-11-14
Thanks guys for all your advice

---

