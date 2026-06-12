---
title: "Installing G++ without an Iternet Conmection"
date: 2008-02-25
forum: Programming Talk
---

### Post by nerdpride on 2008-02-25
I have a Ubnutu Desktop that I cant easily connect to the internet and would like to install G++ but it has so many dependancies! What do i need to download and transfer to that computer and how should I install it once i have? 
Thanks,
Nerdpride

---

### Post by pedro_orange on 2008-02-25
```

aptitude download build-essential

```

On the linux box you are on the internet with.

You will find a .deb in the home folder. Copy this to a suitable media that you can transport this file to & hey presto!

You may need your Ubuntu installation CD to build this deb

---

### Post by nerdpride on 2008-02-25
I got it. It compiled a test file to "a.out" How do i run that?

---

### Post by pedro_orange on 2008-02-25
That's strange.

Mine downloaded and packaged it into a *.deb

I would imagine it's just an output file. So change dir to that directory in which the a.out is stored. And then just run

```
./a.out
```

---

### Post by aks44 on 2008-02-25
> **nerdpride said:**
> It compiled a test file to "a.out" How do i run that?

There is a FAQ in the sticky about that and much more (Compiling your first C or C++ programs).

---

### Post by nerdpride on 2008-02-25
No not the compiler, a test program. I successfully (I think) installed G++. When I compiled it, instead of running it in the terminal, like I expected it compiled it to a file called a.out. This would be fine if I knew how to run it. Does anyone out there know how to run a ".out" file?

---

### Post by aks44 on 2008-02-25
At the risk of repeating myself, this is explained where I told you in the post before.

---

### Post by LaRoza on 2008-02-25
> **nerdpride said:**
> I have a Ubnutu Desktop that I cant easily connect to the internet and would like to install G++ but it has so many dependancies! What do i need to download and transfer to that computer and how should I install it once i have? 
Thanks,
Nerdpride

The build-essential package is on the cd. If the CD is set as a repository, which it is by default, the command:

```

sudo aptitude install build-essential

```

Will prompt you to enter the cd.

As for using it, the sticky, the only one, has two links for compiling and running programs.

---

### Post by nerdpride on 2008-02-25
I figured it out. All you do is write the code in Text Editor. Then use BASH to compile and run it.
```
cd <directory>
g++ inputfile.cpp -Wno-deprecated -o outputfile.out
./outputfile.out
```
 
Thank you
-Nerdpride

---

### Post by aks44 on 2008-02-26
> **nerdpride said:**
> -Wno-deprecated

Advice: don't use this switch. It makes the compiler more lax about deprecated, possibly dangerous features, which is definitely a Bad Thing.

You should really take the total opposite stance: make the compiler the strictest you can, by enabling as much warnings as possible.
For the rationale and also for a list of the most prominent switches to use, see the "Paranoid" section of the FAQ we already pointed you to.

---

