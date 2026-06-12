---
title: "How to set up g++?"
date: 2006-09-10
forum: Programming Talk
---

### Post by smart61 on 2006-09-10
I have installed ubuntu from CD and want to do some C++ development.  I don't see anything for g++ in the 'Add Programs' GUI under development.

I did find g++-4.* in the package management GUI as well as gcc-*, and make.  I added them, the software was downloaded and installed, but there doesn't seem to be anything on the system just called g++ or gcc.  I also don't see things like /usr/include populated with basic includes.

Thanks,
smart61

---

### Post by nereid on 2006-09-10
Hi,

open a terminal and issue the following command to get a working gcc installation

```

sudo apt-get install build-essential

```

---

### Post by smart61 on 2006-09-10
Thanks, that's great.  Just one more question...

How would I have known that from the online docs and why isn't something like that obviously available via the GUI interface?

Ok, that was two more questions.

Thanks again!
smart61

---

### Post by spamsickle on 2006-09-10
I don't know the answer to your 2 more questions, but your initial question was very timely.  I just installed Ubuntu, and wanted to know how to get g++ up and running.  Thanks for asking, and thanks to Nereid for answering.

---

### Post by nereid on 2006-09-11
I have got the solution from [http://ubuntuguide.org](http://ubuntuguide.org) IMHO this is not available from the simple install manager because it is not something that everybody needs. I don't know how your GUI installer application is called as I use Kubuntu (there it is called adept but I use the commandline most of the time).

---

### Post by rplantz on 2006-09-12
> **smart61 said:**
> Thanks, that's great.  Just one more question...

How would I have known that from the online docs and why isn't something like that obviously available via the GUI interface?

Ok, that was two more questions.

Thanks again!
smart61

Do you mean via Synaptic? It is available that way.

Finding what to do is a real hassle. Searching Synaptic for "g++" does not bring up build-essential, but you need that package in order to get the libraries.

Also, if you want the info documentation, you need to install the gcc-doc package.

---

### Post by nereid on 2006-09-12
> **rplantz said:**
> Do you mean via Synaptic?

Aren't there two GUI installer? A simple one and a normal one. The simple one doesn't have the option to install gcc, as far as I know.

---

### Post by rplantz on 2006-09-13
> **nereid said:**
> Aren't there two GUI installer? A simple one and a normal one. The simple one doesn't have the option to install gcc, as far as I know.

You're right. The simple one called "Add/Remove Applications" and it's under the "Applications" menu. It seems to be limited to "end-user" applications. The meaning of the term "user" depends upon context. I've read many assembler manuals that describe the assembly language programmer as "user."

The more advanced one ("normal" for me -- another word that must be defined in context) is Synaptic Package Manager, under the System->Administration menu.

---

### Post by DarkPCTroll on 2006-09-23
Hey **nereid**, Thanks for the Terminal command line [-o< , it was very useful, I was nuts because of that and then I realized I had the IDEs but not the compilers LOL!!

**_Dark PC Troll_**

---

### Post by nereid on 2006-09-24
No problem, glad I could help you.

---

