---
title: "How do I install a .tar.gz file (with XMMS as an example)?"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by hofodomo on 2008-08-31
All right, this is my first time using any linux system.  I'm getting the hang of it, but I'm still trying to crack installing tarballs.  I've googled around for about half an hour, and I've viewed over a dozen pages/threads about this.  But I think I'm missing something key here...lol sorry for my incompetence :(

I've read sites like [this]("http://www.psychocats.net/ubuntu/installingsoftware") and [this]("https://help.ubuntu.com/community/CompilingEasyHowTo"), but I'm still having trouble.  I think it's because I really need specific and definite examples, not general instructions such as "nagivate to some directory and perform the 'make' function"

Anyways, let's establish a few constants here:
-I'm trying to install something from **program.tar.gz**
-My username is **person**
-Thus my user directory would be **/home/person**

Now, if I'm trying to install program.tar.gz, *what exactly* would I need to put into terminal?
(The specific program that I am trying to install is xmms-1.2.11.tar.gz)

I've also read the install instructions that came with the download, but once again, it says stuff like, "use ./configure, and then 'make'", in which case I have doubts/end up doing something wrong.

Thanks.

---

### Post by ashmew2 on 2008-08-31
Installing from tar.gz is known as compiling from tarballs.
For that , first of all you need the build-essential package , for that , do in the terminal :
```

sudo apt-get install build-essential
```

Then extract the program.tar.gz to your home folder suppose inside the folder named "program". So its path is

/home/person/program

Do in the terminal :
```

cd ~/program
make
make install

```

~ refers to your home directory , if you type it in the terminal it is equivalent to /home/username...

If make does not work , try this : (After you have changed directory to /home/person/prgram :

```
./configure
```

It should be done like that..Try and get back!

---

### Post by cariboo on 2008-08-31
There is a deb available here:

[https://launchpad.net/ubuntu/hardy/+package/xmms](https://launchpad.net/ubuntu/hardy/+package/xmms)

Just download the deb, double click it and let gdebi install it.

Jim

---

### Post by Sycron on 2008-08-31
If ```
make install
``` doensn't work try ```
sudo make install
```.

---

