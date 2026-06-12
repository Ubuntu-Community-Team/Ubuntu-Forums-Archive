---
title: "rar"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-05-16
how can i extract .rar files from my Ubuntu 7.10?
what programme do i need to download?

thank you

---

### Post by sasgross on 2008-05-16
I'm not sure about Ubuntu 7.10, but in 8.04 there is RAR available from the applications repository. Make sure that in software sources you activated multiverse (System -> Administration -> Software sources -> check multiverse). Then go to Applications -> Add/Remove and type rar into the search field (the list probably updates itself first, since you had not multiverse checked before). When the search results appear there should be the RAR program right at the top. Install it. After it is installed you just need to right-click on your rar-file and choose "extract here", or you can open it with the archive manager for more advanced operations.

---

### Post by EXCiD3 on 2008-05-16
In terminal run ```

sudo aptitude install unrar
```

And then you can use Ark (a graphical file compression tool) to extract it. If you dont have Ark you can run this in terminal:```
sudo apt-get install ark
```Both of these packages can also be installed by searching in Synaptic Package Manager instead of through the terminal. Once you have unrar installed you can use the Right Click -> Extract here method as mentioned.

---

### Post by fmpfmpf on 2008-05-16
i used
sudo aptitude install unrar

it says 'Could not resolve archive Ubuntu'
and many many other things

i still canot unzip rar files, so i doubt the programme is installed

what is wrong?

thank you

---

### Post by angry_johnnie on 2008-05-16
Have you enabled extra repositories?
Rar and Unrar are both in multiverse.
So, open adept, and then find something like **Manage Repositories**.
Then just make sure that you have universe and multiverse enabled, and you'll be able to install those packages.

As a side note, there is another app, called unp (as in unpack), which works with almost anything... just in case you don't want to remember all the different commands for extracting different types of files. :-)

---

### Post by EXCiD3 on 2008-05-16
I always forget, you need a certain section of the repositories enabled. The command you ran installs software (specifically unrar) from the repositories. Its filed under the "multiverse" section which is disabled by default. sasgross mentioned it here:
> **sasgross said:**
> Make sure that in software sources you activated multiverse (System -> Administration -> Software sources -> check multiverse).

then try the commands i gave you and you should be good to go. :) I would recommend checking all the repositories except for "source code" in case you need it in the future.

---

### Post by fmpfmpf on 2008-05-16
i tried again using synaptics and it worked :)
thank you guys

---

### Post by Archmage on 2008-05-16
> **fmpfmpf said:**
> i used
sudo aptitude install unrar

it says 'Could not resolve archive Ubuntu'
and many many other things

Either your source.list is broken or you haven't update for a while.

"sudo aptitude update" should reload your sources.

---

### Post by EXCiD3 on 2008-05-16
Glad to help! If you would, go up to thread tools and mark your thread as solved. That way others with the same problem will know there is a fix here. :)

---

### Post by gg234 on 2008-05-16
There ia another simple tool called unp you can extract almost anything install this using the following command

sudo aptitude install unp

---

