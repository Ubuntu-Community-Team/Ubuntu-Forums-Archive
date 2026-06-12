---
title: "binutils"
date: 2012-10-19
forum: Programming Talk
---

### Post by IAMTubby on 2012-10-19
Hello,
I am not able to download binutils from [http://ftp.gnu.org/gnu/binutils/]("http://ftp.gnu.org/gnu/binutils/"). Download always gets stopped in between.

Does anyone have a tarball of binutils. If yes, please attach it here.

---

### Post by LiamOS on 2012-10-19
Upload limit is too low. 
I suggest trying to download from one of the Gentoo distfile mirrors.

---

### Post by IAMTubby on 2012-10-19
> **LiamOS said:**
> Upload limit is too low. 
I suggest trying to download from one of the Gentoo distfile mirrors.
LiamOS, I'm trying. Shall get back to you shortly.

---

### Post by IAMTubby on 2012-10-19
> **LiamOS said:**
> Upload limit is too low. 
I suggest trying to download from one of the Gentoo distfile mirrors.
LiamOS, I'm still unable to download it. If you are able to, can you please attach it here ? I'm guessing it's maybe because of some IP problem, although no sites are generally blocked in my country of residence.

---

### Post by spjackson on 2012-10-19
> **IAMTubby said:**
> LiamOS, I'm still unable to download it. If you are able to, can you please attach it here ? I'm guessing it's maybe because of some IP problem, although no sites are generally blocked in my country of residence.
The maximum attachment size permitted on this forum is less than 1MB. The file you want is 19MB. Nobody is going to be able to do that for you.

There are multiple places this tarball can be downloaded from, using http or ftp. If you cannot download a file of 19MB from any of the available locations via any method, then you will need to focus on resolving your network issues.

---

### Post by IAMTubby on 2012-10-19
> **spjackson said:**
> The maximum attachment size permitted on this forum is less than 1MB. The file you want is 19MB. Nobody is going to be able to do that for you.

There are multiple places this tarball can be downloaded from, using http or ftp. If you cannot download a file of 19MB from any of the available locations via any method, then you will need to focus on resolving your network issues.
spjackson, I'm sorry, but are you able to download it ? A couple of people also tried along with me and it says "Download complete", but the size is only half the actual size.

Is there any way I can get the file ?

---

### Post by Bachstelze on 2012-10-19
And what do you plan to do with it?

---

### Post by IAMTubby on 2012-10-19
> **spjackson said:**
> The maximum attachment size permitted on this forum is less than 1MB. The file you want is 19MB. Nobody is going to be able to do that for you.

There are multiple places this tarball can be downloaded from, using http or ftp. If you cannot download a file of 19MB from any of the available locations via any method, then you will need to focus on resolving your network issues.
I tried downloading almost every source from [http://ftp.gnu.org/gnu/binutils/]("http://ftp.gnu.org/gnu/binutils/") .. doesn't work!

---

### Post by IAMTubby on 2012-10-19
> **Bachstelze said:**
> And what do you plan to do with it?
Sir, I want to cross compile it for Power PC for a project.

---

### Post by IAMTubby on 2012-10-19
> **Bachstelze said:**
> And what do you plan to do with it?
If I could get a cross compiled version for PowerPC 400, would be even better!

---

### Post by Bachstelze on 2012-10-19
Do yourself a favor and download a precompiled PPC one (from e.g. Debian).

[http://packages.debian.org/squeeze/powerpc/binutils/download](http://packages.debian.org/squeeze/powerpc/binutils/download)

---

### Post by IAMTubby on 2012-10-19
> **Bachstelze said:**
> Do yourself a favor and download a precompiled PPC one (from e.g. Debian).

[http://packages.debian.org/squeeze/powerpc/binutils/download](http://packages.debian.org/squeeze/powerpc/binutils/download)
Sir, I did try downloading from [http://www.gnu.org/software/binutils/](http://www.gnu.org/software/binutils/) and also googled for PPC format, but can't find one.

---

### Post by IAMTubby on 2012-10-19
> **Bachstelze said:**
> Do yourself a favor and download a precompiled PPC one (from e.g. Debian).

[http://packages.debian.org/squeeze/powerpc/binutils/download](http://packages.debian.org/squeeze/powerpc/binutils/download)
> **spjackson said:**
> The maximum attachment size permitted on this forum is less than 1MB. The file you want is 19MB. Nobody is going to be able to do that for you.


It's okay if I atleast get an IntelPC version, I can try cross compiling.
But I'm just not able to get any format from the internet.

---

### Post by spjackson on 2012-10-19
> **IAMTubby said:**
> spjackson, I'm sorry, but are you able to download it ? A couple of people also tried along with me and it says "Download complete", but the size is only half the actual size.

Is there any way I can get the file ?
Yes, I can download it. I have no idea if there is any way you can get the file. I could load it up to a website for you, but if you cannot download it from any of the many existing locations, you probably won't be able to get it from mine either.

---

### Post by IAMTubby on 2012-10-19
> **spjackson said:**
> Yes, I can download it. I have no idea if there is any way you can get the file. I could load it up to a website for you, but if you cannot download it from any of the many existing locations, you probably won't be able to get it from mine either.
Ohh... atleast that's good. A lot of my friends here tried and no one could. Probably some IP issue. 
Can you pass me the link. I'll try once again. And if it still doesn't work, will it be possible to mail me. I'm sorry for all the trouble, but needed it a bit urgent.

---

### Post by spjackson on 2012-10-19
> **IAMTubby said:**
> Ohh... atleast that's good. A lot of my friends here tried and no one could. Probably some IP issue. 
Can you pass me the link. I'll try once again. And if it still doesn't work, will it be possible to mail me. I'm sorry for all the trouble, but needed it a bit urgent.

Well, if it's "some IP issue" and you are getting the same problem from all the other sites that offer this file, I don't know how getting it from me will solve it, but here goes.

I got the file from [http://ftp.gnu.org/gnu/binutils/binutils-2.22.tar.bz2]("http://ftp.gnu.org/gnu/binutils/binutils-2.22.tar.bz2")
It's size is 19,973,532

For now you can get it as follows:
```

wget http://nilone.eu/binutils-2.22.tar.bz2

```
This will be removed later today.

I won't be able to email it to you as the attachment size exceeds that permitted by my 3 email providers.

---

### Post by IAMTubby on 2012-10-19
> **spjackson said:**
> Well, if it's "some IP issue" and you are getting the same problem from all the other sites that offer this file, I don't know how getting it from me will solve it, but here goes.

I got the file from [http://ftp.gnu.org/gnu/binutils/binutils-2.22.tar.bz2]("http://ftp.gnu.org/gnu/binutils/binutils-2.22.tar.bz2")
It's size is 19,973,532

For now you can get it as follows:
```

wget http://nilone.eu/binutils-2.22.tar.bz2

```
This will be removed later today.

I won't be able to email it to you as the attachment size exceeds that permitted by my 3 email providers.
spjackson, thanks a lot :)
I don't have access to a linux system now. Can you give me 3 hours time till I reach home. Currently outside now.

I didn't try wget from the link you gave but tried downloading from [http://ftp.gnu.org/gnu/binutils/binutils-2.22.tar.bz2]("http://ftp.gnu.org/gnu/binutils/binutils-2.22.tar.bz2") and it gave the same issue.

I shall get home and try wget'ting it . As I said, please give me 3 hours time. 

Thanks :)
Hope it works.

---

