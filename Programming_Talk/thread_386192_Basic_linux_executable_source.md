---
title: "Basic linux executable source?"
date: 2007-03-16
forum: Programming Talk
---

### Post by Wybiral on 2007-03-16
Does anyone know where I can find the source code for common linux executables such as "pwd"/"cd"/ "ls"/"grep" and... Well, basically anything found in the "/bin" folder.

They were obviously compiled with C (you can see it in the binary) so I was wondering if there was a site or somewhere that might have the source up for download.

---

### Post by po0f on 2007-03-16
Wybiral,

You can download the source for most GNU utilities from [here](http://ftp.gnu.org/pub/gnu/) or any of their mirrors.  I don't know the individual projects that most of the programs you are looking for reside in, but my guess would be [coreutils](http://ftp.gnu.org/pub/gnu/coreutils/).

---

### Post by Wybiral on 2007-03-16
Cool, thanks. I'm interested in seeing if there is any room for optimization. I know that most of them are pretty small and optimized already, but if there's any room for improvement, why not?

---

### Post by po0f on 2007-03-16
*wonders when Wybiral is just going to make the switch to Gentoo*  ;)

---

### Post by Wybiral on 2007-03-16
*Loves ubuntu and wants to help make it better*

I tried installing gentoo once and could barely make it through the setup!

With ubuntu I can let it set everything up for me, then customize it as I go.

---

### Post by maddog39 on 2007-03-16
The Gentoo LiveCD is really really easy. Except it takes like 2 days to compile 447 packages with optmization on a Dual Core 3GHz CPU. So I basically gave up on it.

---

### Post by Mirrorball on 2007-03-16
I used Gentoo for two years and it's great, but eventually I grew tired of compiling everything. About the source code for common executables, why don't you download the source package from the source repositories?

---

