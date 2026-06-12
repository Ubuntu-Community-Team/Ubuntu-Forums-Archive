---
title: "ctr1.o, ctri.o needed to compile FORTRAN 77 code with g77 compiler"
date: 2012-05-17
forum: Programming Talk
---

### Post by yrohinkumar on 2012-05-17
Hello,

I am using ubuntu 12.04... I needed to compile FORTRAN 77 code and installed g77 from 8.04's repos...when I try to compile it gives me the following...
```

/usr/bin/ld: cannot find crt1.o: No such file or directory
/usr/bin/ld: cannot find crti.o: No such file or directory
collect2: ld returned 1 exit status

```

there was libgcc_so problem I eliminated by linking it to the so.1 which was there in my system...however I couldn't locate these ctri.o files...

fyi...i've 32-bit OS and I have libc6-dev installed :)

Any help would be appreciated...

---

### Post by yrohinkumar on 2012-05-17
Some searching on the internet and trying so many options I found the following link

[http://askubuntu.com/questions/69119/linking-problems-after-updating-to-11-10]("http://askubuntu.com/questions/69119/linking-problems-after-updating-to-11-10")

I reinstalled binutils, build-essential, libc6-dev packages and then found ctri.o etc. in the folder /usr/lib/i386-* linking which to /usr/lib/. worked for me...I'm able to compile the code... :)

P.S. Can't locate those .o files again... 

Can someone shed some light on what's happening?

---

### Post by steeldriver on 2012-05-17
I wonder if it's because you initially installed g77 without the rest of build-essential, and the subsequent installs preserved your original tool chain config/paths? you could try purging g77 and reinstalling build-essential to see if that makes a difference

This really is just a guess though

---

### Post by yrohinkumar on 2012-05-17
Hmm... I had build-essential earlier... I just re-installed it... and I'm sure it must be the problem with the paths linked in the previous version and the latest... (I had to link them to redirect to the new paths)As g77 is from 8.04's repo & the build-essential is from 12.04... it is certainly a possibility... I don't want to risk removing the working g77 though! ;)

---

### Post by jabl on 2012-05-21
FWIW, you probably could have used gfortran instead, which is available in current Ubuntu versions. GFortran supports F77 including most g77 extensions and many extensions not available in g77.

---

### Post by csurocket on 2012-05-21
I may have the same problem with you. All methods I searched on website do not work. I doubt whether it's because the new version, maybe the 12.04 version is different from version before. It does not work even I install ubuntu 12.04 i386.
     :-(

---

### Post by yrohinkumar on 2012-05-21
@jabl... gfortran doesn't work with all types of F77 codes...Many use the old repos...

@csurocket 12.04 is not all that bad...some lil tweaking is always required ;) If u any specific problem in mind regarding this...post it...I have lil experience I might be able to help u with...

---

### Post by csurocket on 2012-05-22
Hi, could you give me an email address? All I want to do is install a software on my computer, so if you have time, I will sent the software to you and you can help me check what's wrong with it.  the g77 I installed is through following produce:
add some source in the file source.list under /etc/apt

deb [http://hu.archive.Ubuntu.com/ubuntu/](http://hu.archive.Ubuntu.com/ubuntu/) hardy universe
deb-src [http://hu.archive.Ubuntu.com/ubuntu/](http://hu.archive.Ubuntu.com/ubuntu/) hardy universe
deb [http://hu.archive.Ubuntu.com/ubuntu/](http://hu.archive.Ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://hu.archive.Ubuntu.com/ubuntu/](http://hu.archive.Ubuntu.com/ubuntu/) hardy-updates unive 

and then use commands:

apt-get update
apt-get install g77

---

### Post by jabl on 2012-05-22
> **yrohinkumar said:**
> @jabl... gfortran doesn't work with all types of F77 codes...


I'm sure you're right. But then again, neither does g77. 

The vast majority of F77 code will work just fine with gfortran, though. If I were the OP I'd first try with gfortran before banging my head in the wall trying to get the obsolete g77 to work, but YMMV.

---

### Post by yrohinkumar on 2012-05-22
@csurocket

I don't know if there is a repo starting with hu...it should be something like 
```

deb http://in.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy universe
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates universe

```

essentially hu should be changed to your country code i.e. us, gb, de, etc.

and in the last line universe is not typed fully...make these changes and lemme know if it worked...the capital "U" in Ubuntu also might cause problem... :)

Hope this helps...

---

### Post by yrohinkumar on 2012-05-22
@jabl Yeah! certainly I tried to get gfortran work... only after having many issues with the old fortran codes which worked fine with g77...I came up with the idea of using old repos to get the good old g77 :D

---

### Post by csurocket on 2012-05-22
It's not the problem of source, I have installed it successfully before. 
 What I am trying is using gfortran to compile g77 code and gcc 4.6 to compile gcc3.4 code. But still I encountered another error:
After compiled the code respectively, I used the gcc to link the .o files together, but it seems the functions in the .o file from gcc3.4 code cant be found. They are " undefined reference".
I don't know the reason. Do you have any method to solve it?

---

### Post by yrohinkumar on 2012-05-23
> **csurocket said:**
> It's not the problem of source, I have installed it successfully before. 
 What I am trying is using gfortran to compile g77 code and gcc 4.6 to compile gcc3.4 code. But still I encountered another error:
After compiled the code respectively, I used the gcc to link the .o files together, but it seems the functions in the .o file from gcc3.4 code cant be found. They are " undefined reference".
I don't know the reason. Do you have any method to solve it?


Can u paste commands, error messages and/or the code u used so that I can better understand the problem?

---

### Post by jalirious on 2012-06-29
Ah, same error on i686 12.04 for code that runs on 10.04. same fort77.

---

