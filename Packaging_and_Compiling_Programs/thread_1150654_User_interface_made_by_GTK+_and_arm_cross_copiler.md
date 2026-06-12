---
title: "User interface made by GTK+ and arm cross copiler"
date: 2009-05-06
forum: Packaging and Compiling Programs
---

### Post by koukou_ on 2009-05-06
Hi,

I would like to make a user interface. I use an ARM cross compiler.
For this, I installed Code::Blocks IDE, but when I build the project I have the following message :

"project - Debug" uses an invalid compiler. Skipping...
Nothing to be done.

Does anyone know why?

Thanks,

---

### Post by Confused_Soul on 2009-11-09
Hi Koukou_
 
I have some what similar problem -
 
I need to cross compile my GUI (built using Glade-3) for ARM architecture. For that i need to have glade-3 and libgladeui packages in my compiler. But I have seen these packages only for i386 and amd64 architectures. I am not sure whether the these packages are available for ARM architecture. Please suggest some way out. How should i have my GUI up on the ARM app. pro.?

---

### Post by SevenMachines on 2009-11-11
can't help much with cross-compiling for arm but if your looking for packages on diffirent architectures you'll want to look at either the [ports repository]("http://ports.ubuntu.com/pool/main/g/glade-3/"), or on the [packages launchpad page]("https://launchpad.net/ubuntu/karmic/+source/glade-3") for compiled versions of things for various platforms. If all else fails you can always 'apt-get source <package>' and try compiling it manually

---

### Post by neeteshn on 2010-01-12
Does flash is supported by ARM linux?

---

