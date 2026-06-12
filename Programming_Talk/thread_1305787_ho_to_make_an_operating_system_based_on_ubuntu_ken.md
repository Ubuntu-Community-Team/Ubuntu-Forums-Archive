---
title: "ho to make an operating system based on ubuntu kenel"
date: 2009-10-30
forum: Programming Talk
---

### Post by kaboyish on 2009-10-30
hi people. some friends and i have always been wanting to make an operating system that represents who we are. the problem is that, we have no idea to start from. i download the "linux from scratch" live cd, but we still want to make something based on the ubuntu.any ideas will be greatly appreciated

---

### Post by whirlwind on 2009-10-30
Have you read Kernighan and Ritchie's C book?  I really would start there.  OS development requires an advanced knowledge of low level C programming at the very least.

whirlwind.

---

### Post by kaboyish on 2009-10-30
> **whirlwind said:**
> Have you read Kernighan and Ritchie's C book?  I really would start there.  OS development requires an advanced knowledge of low level C programming at the very least.

whirlwind.



thanks. guess we'll have to buy that book asap. we've got some knowledge on c language. the problem is, we don't know where to start from. what compilers should we use? where can we get the ubuntu kernel, and how do we modify it? those are just some of the questions we have.

---

### Post by CptPicard on 2009-10-30
You seem to be very out of your depth for OS development (so out of it you don't know you are :) ). I would suggest you just learn to program first, and get familiar with the structure of a typical Linux distribution... when you are ready enough to dive into kernel source, you'll know you are, and will know the answers to your questions.

---

### Post by kaboyish on 2009-10-30
> **CptPicard said:**
> You seem to be very out of your depth for OS development (so out of it you don't know you are :) ). I would suggest you just learn to program first, and get familiar with the structure of a typical Linux distribution... when you are ready enough to dive into kernel source, you'll know you are, and will know the answers to your questions.


haha, thanks man.guess i'll have to be patient and see what happens next

---

### Post by StunnerAlpha on 2009-10-30
I am going to have to agree with CptPicard. Operating systems are the most complicated pieces of software in this day and age, and if you think you and a couple of your friends can make one, best of luck to you and you don't know what you are getting yourselves into. I don't want to discourage you, but I am just trying to give you an idea of how daunting making an operating system is. Start small and work up. If you are really interested in making an ubuntu-based OS, maybe you should try getting involved in the Ubuntu development team.

---

### Post by aesis05401 on 2009-10-30
You could always customize an Ubuntu installation in the form of a remix.  That really isn't a topic that fits into this sub-forum, though.  Anyhow, good luck.

---

### Post by grayrainbow on 2009-10-30
Honestly, I don't know what kenel is, but if you think of a kernel then...well there's no Ubuntu kernel, it's Linux kernel. And from what I understand you might be much more interested not in C but in [http://susestudio.com/](http://susestudio.com/)
 
If you insist on writing you kernel(or kernel modifications) then C and assembly are the things you need. Assembly is more of understanding how todays Von Neumann architecture works.

---

### Post by dwhitney67 on 2009-10-30
> **kaboyish said:**
> hi people. some friends and i have always been wanting to make an operating system that represents who we are. the problem is that, we have no idea to start from. i download the "linux from scratch" live cd, but we still want to make something based on the ubuntu.any ideas will be greatly appreciated

Ubuntu uses the same kernel as say, Fedora, Mandrake, OpenSuse, etc, with the exception that it adds a few odd patches.  The kernel is available from [http://kernel.org](http://kernel.org).

If you want to build your own Linux distro, then bear in mind that this is *distinct* from building your own OS.

For building your own Linux distro, there is nothing wrong with using LFS.  If you find it too complex to follow, then I suggest you take a step back to familiarize yourself with shell scripting (bash), and also with the basics of how Linux is laid out.  This includes understanding the kernel (ie how to compile it, augment it, install it), how to build packages and install them, etc.

You will need a basic familiarity with C programming, because inevitably you will encounter an issue or two (or a dozen) when using LFS.  Acquaint yourself with how to seek help within the LFS user-group.

---

### Post by kaboyish on 2009-11-03
> **aesis05401 said:**
> You could always customize an Ubuntu installation in the form of a remix.  That really isn't a topic that fits into this sub-forum, though.  Anyhow, good luck.


thanks. just one question, how does someone make an ubuntu remix?

---

### Post by kaboyish on 2009-11-03
> **dwhitney67 said:**
> Ubuntu uses the same kernel as say, Fedora, Mandrake, OpenSuse, etc, with the exception that it adds a few odd patches.  The kernel is available from [http://kernel.org](http://kernel.org).

If you want to build your own Linux distro, then bear in mind that this is *distinct* from building your own OS.

For building your own Linux distro, there is nothing wrong with using LFS.  If you find it too complex to follow, then I suggest you take a step back to familiarize yourself with shell scripting (bash), and also with the basics of how Linux is laid out.  This includes understanding the kernel (ie how to compile it, augment it, install it), how to build packages and install them, etc.

You will need a basic familiarity with C programming, because inevitably you will encounter an issue or two (or a dozen) when using LFS.  Acquaint yourself with how to seek help within the LFS user-group.


thanks. we'll have to practice first with LFS first, then move onto the main thing. we've even bought a dummy computer so that we can try our OS there. thanks again for the advice

---

### Post by ad_267 on 2009-11-03
In what way do you want to change Ubuntu? It's probably not that hard if you just want to change all the default artwork and the default set of installed applications. Anything more than that is beginning to get a bit technical though.

---

### Post by kaboyish on 2009-11-04
> **ad_267 said:**
> In what way do you want to change Ubuntu? It's probably not that hard if you just want to change all the default artwork and the default set of installed applications. Anything more than that is beginning to get a bit technical though.

i was thinking of making a light version of ubuntu that requires less ram and cpu usage. what do i need to make such an OS? in windows, i would use nlite and vlite to make customized windows OS's that require lesser resources. what can i use?

---

### Post by A_Fiachra on 2009-11-04
> **kaboyish said:**
> i was thinking of making a light version of ubuntu that requires less ram and cpu usage. what do i need to make such an OS? in windows, i would use nlite and vlite to make customized windows OS's that require lesser resources. what can i use?


Use a lighter X windows manager .. or none at all -- that would certainly require less ram and cpu.  TWM, for example, has a very small footprint.


Of course there are already 1000's of Linux distros -- some quite small.

[Perhaps you've heard of some?]("http://en.wikipedia.org/wiki/List_of_Linux_distributions")

---

