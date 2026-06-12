---
title: "Source code of ubuntu"
date: 2011-08-30
forum: Programming Talk
---

### Post by NumerataNero on 2011-08-30
I'm looking for the code base of Ubuntu, where do I find these?
regards.

---

### Post by Bachstelze on 2011-08-30
Ubuntu is not a single program, but a collection of packages. To obtain the source package from which a binary packge was built, you can use [font=monospace]apt-get source *package*[/font].

---

### Post by Enigmapond on 2011-08-30
Try here...it's for 10.04 but they are all here at this site. Just change the url.. :)

[http://cdimage.ubuntu.com/releases/10.04/release/source/](http://cdimage.ubuntu.com/releases/10.04/release/source/)

---

### Post by NumerataNero on 2011-08-30
thanks for the answers, to be more specic I'm looking for base64 src code.

---

### Post by cgroza on 2011-08-30
> **NumerataNero said:**
> thanks for the answers, to be more specic I'm looking for base64 src code.
You need to look in the package coreutils.

---

### Post by Smart Viking on 2011-08-30
If you combine post #2 and #5, that results in:
```
apt-get source coreutils
```Inside there are multiple instances of the file base64.c, I don't know what's the real deal.

---

### Post by Bachstelze on 2011-08-30
Reminds me I need to work on my MIPS assembly version...

---

### Post by NumerataNero on 2011-08-30
Great, exactly what I needed ;)

---

### Post by NumerataNero on 2011-08-30
> **Smart Viking said:**
> If you combine post #2 and #5, that results in:
```
apt-get source coreutils
```Inside there are multiple instances of the file base64.c, I don't know what's the real deal.
I tried some of these and all give me different result then the base64 on Ubuntu and HP-UX.
Its the way they deal with the last bytes I gues,

---

### Post by Bachstelze on 2011-08-30
> **NumerataNero said:**
> I tried some of these and all give me different result then the base64 on Ubuntu and HP-UX.
Its the way they deal with the last bytes I gues,

You are probably not compiling them right.

---

### Post by NumerataNero on 2011-08-31
Still one question (embarased ;)
I build the stuff but I'm trying to figure out how the component itself is build.
Compiling is ok with gcc -o base64 base64.c -I ../lib but I'm getting unrosolved externals.
Should I link against coreutils.a sitting in ../lib? I tried gcc etc -l ../coreutils.a but no luck.

(still learning, I'm an old VMS gue but speeding up)

---

### Post by Bachstelze on 2011-08-31
You need to

```
./configure
make
```

If you compile it another way, it might not work. It's not a stand-alone tool, but part of a larger package (coreutils), so it is possible that it needs other things in that package.

---

### Post by NumerataNero on 2011-08-31
> **Bachstelze said:**
> You need to

```
./configure
make
```

If you compile it another way, it might not work. It's not a stand-alone tool, but part of a larger package (coreutils), so it is possible that it needs other things in that package.

I've done that but I want to build the base64 standalone also.

---

### Post by Bachstelze on 2011-08-31
Well, you can't. :) Why do you care, though? coreutils doesn't take a lot of time to build even on a fairly ancient machine.

---

### Post by pjd99 on 2011-08-31
> **Bachstelze said:**
> Reminds me I need to work on my MIPS assembly version...
Ouch. Have to implement a MIPS datapath for an assignment, but at least get to choose the language. Now I just have to learn VHDL again.

---

### Post by NumerataNero on 2011-09-04
Thanks for the great support. ;-)

---

