---
title: "How to manually install newest version of avr-gcc?"
date: 2020-09-17
forum: New to Ubuntu
---

### Post by austindodge on 2020-09-17
I'm a very new Ubuntu user. I'm attempting to use the latest version of the avr-gcc tools., 10.1.0 I've found lots of articles on how to install the basic AVR toolset with

sudo apt-get install binutils gcc-avr avr-libc uisp avrdude flex byacc bison

but that only gets me avr-gcc 5.4.0. I've downloaded avr-gcc-10.1.0-x64-linux.tar.bz2 from here: [https://blog.zakkemble.net/avr-gcc-builds/](https://blog.zakkemble.net/avr-gcc-builds/) but have no idea how to make my system actually use it. I've already installed gcc-10 and g++-10 with this:

sudo apt install gcc-10 g++-10
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-10 100
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-10 100

Any help would be appreciated! I get the feeling I'm just asking about some basic Linux functionality, but can't figure out what to even google here.

---

### Post by yapidumoac on 2020-09-17
According to the website you can install the latest version using the provided Build Script: [This build script will install the required packages]("https://blog.zakkemble.net/avr-gcc-builds/")

---

