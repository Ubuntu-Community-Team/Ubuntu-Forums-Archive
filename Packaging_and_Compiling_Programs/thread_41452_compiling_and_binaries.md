---
title: "compiling and binaries"
date: 2005-06-13
forum: Packaging and Compiling Programs
---

### Post by rdking on 2005-06-13
Hope this is the right forum for this post...

my question is rather simple:

what advantages and dissadvantages are there to compiling source versus binaries?  Does it effect speed, usability and stability?  does it result in smaller disk use?  

the reason I ask is I have been toying with setting up a source based distro on my second hd as a trial

---

### Post by lovebug356 on 2005-06-13
[QUOTE=rdking]Hope this is the right forum for this post...

my question is rather simple:

what advantages and dissadvantages are there to compiling source versus binaries?  Does it effect speed, usability and stability?  does it result in smaller disk use?  

the reason I ask is I have been toying with setting up a source based distro on my second hd as a trial[/QUOTE]
 If there is a need for speed you need to compile for your specific computer. Just compiling is not the solution's then you make what you can download. You need to set the correct build parameters.

---

### Post by Xian on 2005-06-13
You'll always spend more time compiling a program than any realized speed gains. The only real "advantage" is that you get to play MOTU with your box. I've run Gentoo for a long while and it is quite fun to put on my mad scientist hat and run wild in the laboratory.

---

### Post by ubuntu_demon on 2005-06-13
I moved this thread

rdking please look for where to post before actually posting something

---

### Post by az on 2005-06-13
[QUOTE=rdking]Hope this is the right forum for this post...

my question is rather simple:

what advantages and dissadvantages are there to compiling source versus binaries?  Does it effect speed, usability and stability?  does it result in smaller disk use?  

the reason I ask is I have been toying with setting up a source based distro on my second hd as a trial[/QUOTE]


It will take up much more disk space since you will end up with the unpacked source as well as the binaries.

You need to compile from source when the application is not provided for you by the distribution.

Any optimizations you can get by compiling it yourself are far from being significant.  

So, if you want an app that is not in Ubuntu, compile it from source.  If you want an app than is packaged for Debian, but not in ubuntu install the deb-src (source package) from debian and compile it on your box.

Compile the whole stack?  I could not be bothered.

---

### Post by LordHunter317 on 2005-06-13
[QUOTE=lovebug356]If there is a need for speed you need to compile for your specific computer.[/quote]No, you don't.

At most, you have to compile for particular ISA and all it's options.  But given the same set of options, the compiler had better output the same code every time.  If not, we have a term for that: broken.

Compiling code is a nightmare, and a utter PITA.  I do lots of configuration management for a living.  It's some on large projects, most coders can't do or maintain correctly, as it's more about organization than anything (coders aren't always the most organized sort ;)). 

Believe me.  It's not something you want to do unless you have to.

---

