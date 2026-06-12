---
title: "Need help in selecting 32bit / 64bit"
date: 2010-11-29
forum: Recurring Discussions
---

### Post by lyrilmaki on 2010-11-29
Hi, I'm using Acer Aspire 4471G Laptop

_Spec_
Intel i3 processor 330M
NVIDIA GeForce 310M
DDR3 2gb memory
Window 7 Home Premium 64bit..

I'm new in using ubuntu, so I would like to ask, which I should select (32bit or 64bit) in download section ? :P

---

### Post by miegiel on 2010-11-29
> **lyrilmaki said:**
> Hi, I'm using Acer Aspire 4471G Laptop

_Spec_
Intel i3 processor 330M
NVIDIA GeForce 310M
DDR3 2gb memory
Window 7 Home Premium 64bit..

I'm new in using ubuntu, so I would like to ask, which I should select (32bit or 64bit) in download section ? :P

I'm still using 32bit versions for 2 reasons:
[LIST=1]
[*]Flash (youtube vids etc.) runs smoother on 32 bit machines.
[*]32bit linux (and windows AFAIK) uses less memory than 64bit
[/LIST]

---

### Post by overdrank on 2010-11-29
Hi and welcome, I would say 64bit if your system supports it. :)

Moved to Absolute Beginner Talk

---

### Post by lyrilmaki on 2010-11-29
Hi, I'd tried to install flash plugin by typing "sudo apt-get install flashplugin-nonfree" in Terminal, but it shown "unable to locate package flashplugin-nonfree" after reading package list and reading state information were Done

---

### Post by yogi1983 on 2010-11-30
> **lyrilmaki said:**
> Hi, I'd tried to install flash plugin by typing "sudo apt-get install flashplugin-nonfree" in Terminal, but it shown "unable to locate package flashplugin-nonfree" after reading package list and reading state information were Done
  try to get your plugins using the ubuntu software center. let it do the work:P

---

### Post by miegiel on 2010-11-30
> **lyrilmaki said:**
> Hi, I'd tried to install flash plugin by typing "sudo apt-get install flashplugin-nonfree" in Terminal, but it shown "unable to locate package flashplugin-nonfree" after reading package list and reading state information were Done

Wrong plugin m8

```
sudo apt-get -s install flashplugin-installer
```

Is the right one. The *flashplugin-installer* will get the flashplugin from adobe for you.

---

### Post by mikechant on 2010-11-30
Most people just install the package 'ubuntu-restricted-extras' since this includes the flash player and lots of useful video/audio codecs, extra fonts etc.

As for the 64/32bit stuff, I did tests for video encoding etc. and found no measurable difference in performance, and given that you've only got 2Gb RAM going 64-bit won't make any difference there, and also that you may get one or two minor problems still with 64 bit, perosnally I'd stick with 64 bit for now.

---

### Post by philinux on 2010-11-30
Benchmarks.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Moved to Recurring Discussions.

---

### Post by desnaike on 2010-11-30
If you are a new user I would go 32bit it would probably not require that you be more experienced if problems come up ie, flash plugin. when your experience and comfort level increase then go 64bit, the true benefits of 64bit over 32bit in a home user enviroment for me is debatable.

---

### Post by miegiel on 2010-11-30
> **desnaike said:**
> if you are a new user i would go 32bit it would probably not require that you be more experienced if problems come up ie, flash plugin. When your experience and comfort level increase then go 64bit, the true benefits of 64bit over 32bit in a home user enviroment for me is debatable.

+1

---

### Post by oldos2er on 2010-11-30
> **lyrilmaki said:**
> Hi, I'd tried to install flash plugin by typing "sudo apt-get install flashplugin-nonfree" in Terminal, but it shown "unable to locate package flashplugin-nonfree" after reading package list and reading state information were Done

If you installed 64-bit Ubuntu, I suggest you should use 64-bit flash which is not in the repos. [http://flash-aid-extension.blogspot.com/](http://flash-aid-extension.blogspot.com/)

---

### Post by johntaylor1887 on 2010-12-04
> **miegiel said:**
> 
[*]Flash (youtube vids etc.) runs smoother on 32 bit machines.
Not true any more. The latest 64bit flash runs just as good as 32bit. I have no problems with it.

> **miegiel said:**
> [*]32bit linux (and windows AFAIK) uses less memory than 64bit
[/LIST]
Memory is there to be used, not conserved. As long as you have enough, using more memory will speed up your computing experience, not slow it down.

---

