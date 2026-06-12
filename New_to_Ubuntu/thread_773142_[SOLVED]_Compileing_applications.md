---
title: "[SOLVED] Compileing applications"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Nxion on 2008-04-28
I am not quite sure on how to word this but here it goes. This might sound like an odd question.

When you want to compile a new program you have to usually download the build-essentials plus a few others to compile want you want. 

My questions is there a way to download it all at once so no matter what program you need to compile, you already have all the packages ready, instead of havening to always download a new package here or there before you have to compile. ?

Let me know if this makes sense or not.

Thanks to all !

---

### Post by Monicker on 2008-04-28
> **Nxion said:**
> I am not quite sure on how to word this but here it goes. This might sound like an odd question.

When you want to compile a new program you have to usually download the build-essentials plus a few others to compile want you want. 

My questions is there a way to download it all at once so no matter what program you need to compile, you already have all the packages ready, instead of havening to always download a new package here or there before you have to compile. ?

Let me know if this makes sense or not.

Thanks to all !

Thats not practical, because each package can have unique prerequisites, based on the tools that were chosed to create the program.  There can also be issues because a program may need specific versions of its dependencies.

---

### Post by sdennie on 2008-04-28
I think you are asking if it's possible to download all the -dev packages.  I believe you can do that with:

```

sudo apt-get install "lib*-dev".

```

(That won't get them all but, it will get a lot of stuff.  Not necessarily stuff that you'll ever find useful though)

If you find you are regularly building apps that are available in the Ubuntu repositories but you want a more up to date version, a better option might instead be to use build-dep:

```

sudo apt-get build-dep name_of_package

```

That will just grab all the things that were needed to build the original Ubuntu version of "name_of_package".

---

