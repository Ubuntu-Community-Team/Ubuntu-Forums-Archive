---
title: "How to compile C language in Linux"
date: 2007-04-14
forum: Programming Talk
---

### Post by tomoo on 2007-04-14
I am fresh with Linux and Ubuntu, after I installed Ubuntu, I realized there is no gcc preinstall in the system. I checked gcc site, I dont think it's possible for me to install with their instruction, it's just too hard for me. 
Is there anyone would like to share your exp with compiling C in Linux, Thanks a lot.

Regards

Tom

---

### Post by g3k0 on 2007-04-14
sudo apt-get install build-essential

---

### Post by tomoo on 2007-04-14
wow, how amzing it is.
Another newbie question, I was using my school lab linux to program. There is an build in editor called NEDIT. I was able to run it directly in terminal by type in the command "nedit". How can I do this in my fresh ubuntu?
How do I get more information about these installation package? like how do you know where to get gcc? Thanks a lot. 

Tom

---

### Post by Wybiral on 2007-04-14
GCC and the dev files are installed with build essential. Just use "gcc file_to_be_compiled.c" and it will produce your a.out executable.

---

### Post by tht00 on 2007-04-15
> **tomoo said:**
> wow, how amzing it is.
Another newbie question, I was using my school lab linux to program. There is an build in editor called NEDIT. I was able to run it directly in terminal by type in the command "nedit". How can I do this in my fresh ubuntu?
How do I get more information about these installation package? like how do you know where to get gcc? Thanks a lot. 

Tom

It is in the repositories as well.

Take a look at Synaptic ('System' > 'Admin' > 'Synaptic Package Manager').  There is a ton of software you can install from the Ubuntu repositories (and you can add more), including nedit.

The apt-get command earlier in the post is what Synaptic interfaces to (same end result).  It's easier to give a 'quick fix' answer with that, but more intuitive for a beginner to learn how to use Synaptic, at least to start with.

---

### Post by rplantz on 2007-04-15
> **tht00 said:**
> 
The apt-get command earlier in the post is what Synaptic interfaces to (same end result).  It's easier to give a 'quick fix' answer with that, but more intuitive for a beginner to learn how to use Synaptic, at least to start with.
I agree that Synaptic is much easier to use than apt-get. And it provides lots of information, which I think the beginner should explore. Look under File->History. Highlight a package and look under Properties. Lots of good stuff here to help you understand your system.

Having said this, I don't think that the "build-essential" requirement in order to do development is especially intuitive. I started programming in the early 60s and did it as a job for over thirty years in lots of different environments. I needed help on this forum to clue me in about "build-essential." Even the description > 
If you do not plan to build Debian packages, you don't need this
package.  Moreover this package is not required for building Debian
packages.

is a bit misleading. Of course, I've spent most of my working life dealing with things like this. :)

---

### Post by Wybiral on 2007-04-15
I like using "sudo apt-get" more personally. You can install as many packages as you want with one command, I actually have a script that installs all of my dev files and frequently used apps for when I install ubuntu on new machines/upgrade/reinstall.

Not having to search and click all of those packages makes it a much quicker process.

---

### Post by tomoo on 2007-04-15
thanks for replying guys, I learned a lot from these.

---

