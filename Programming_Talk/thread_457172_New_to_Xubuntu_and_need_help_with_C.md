---
title: "New to Xubuntu and need help with C"
date: 2007-05-28
forum: Programming Talk
---

### Post by paulthompson on 2007-05-28
I really need some help before I pull out what hair I have left.

I've been programming AI for some years and have finally decided to ditch Basic & Windows. So now I have a shiny new laptop with Xubuntu installed but I'm getting nowhere with anything else.
I have no experience with Linux or C but loads of ideas I need to get running as soon as I can.

So what's the easiest way to get a C programming environment up and running under Xfce.

I do not need GUI or OOP just good old fasioned blinking cursor on black screen. I need to run billions of discrete genetic organisms so all processor overheads need to go.

Any help gratefully recieved and I would be happy to share what I know of genetic progs.

Thanks to all who read this

Paul

---

### Post by Ateo on 2007-05-28
For starters, install the build-essential meta-package. This will install your basic C compiler needs. You may need to install other development libraries depending on what you're compiling for. All development libraries will have -dev in the title...

For coding, there are several ways. As you implied, all you care about is a blinking curson and that's a good enough environment to code in (yea right!). YOu can use any text editor or just install Bluefish or Quanta (for Gnome (XFCE) or KDE, respectively).

HTH

---

### Post by seamless on 2007-05-28
[QUOTE="Ateo"]just install Bluefish or Quanta (for Gnome (XFCE) or KDE, respectively).[/QUOTE]
Except both of which are HTML editors and won't help you very much with C programming...

Take a look at the [What's your Favorite IDE?]("http://ubuntuforums.org/showthread.php?t=6762") sticky thread for some good IDE's that handle C very well.

---

### Post by paulthompson on 2007-05-28
Thanks for the comments.
The blinking cursor refers to the run-time environment rather than during coding. 

I got geany with my distro and that seems ok. It seems to have the required compiler built in but if I try and compile anything I get a load of error messages followed by a compilation succesful message but nothing if I try and run. 

Sorry to have to demonstrate my ignorance but what is a "build-essential meta-package"?

Thanks again

---

### Post by raul_ on 2007-05-28
```

sudo apt-get install build-essential

```

will install all the minimum packages needed to compile (gcc, g++, headers, etc)

maybe posting the error messages would help

---

### Post by paulthompson on 2007-05-28
Cheers Raul, that seems to have got things sorted.

---

