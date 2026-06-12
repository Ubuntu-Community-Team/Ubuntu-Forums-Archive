---
title: "compiling composer for windows (in any way possible)"
date: 2013-01-06
forum: Packaging and Compiling Programs
---

### Post by niekn on 2013-01-06
hi there!

[background info]
I'm from a Japanese student society in the Netherlands and we use a very crappy karaoke program called soramimi, it's written by one of our former members, but is hasn't had any update in the past decade and the guys who are currently responsible for the program can't program! I contacted them that I wanted to fix the shitload of bugs in the program, but they won't give me the sourcecode, so I decided to go for plan B: convert all our old songs to ultrastar-format and extend performous.
so I started forking the composer from performous and add a soramimi-txtparser-plugin.
it's currently being merged into the main branch but it needs some polishing which i've already done in my own copy:
[https://github.com/nieknooijens/composer-smmtxt](https://github.com/nieknooijens/composer-smmtxt)
setting up everything was pretty easy, just apt-get stuff and get going!
[/background info]

[the problem]
most people at our student society use windows, so I need to get it working on there
I downloaded the minGW compiler and got it to run with a simple code::blocks project.
but when I try to use it in combination with Cmake everything fails It can't find the dependency's and when i manually point to them it still claims it can't find them :???::???:
next up I tried getting it to compile on a virtualbox-windows 8 which was a total nightmare since I need to download a whole lot of libraries and I still can't get it to compile, what to do?
[/the problem]

I'm running 12.10

after a couple of days still no answer :-(

---

