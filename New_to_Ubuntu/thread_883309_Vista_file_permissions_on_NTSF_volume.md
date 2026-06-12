---
title: "Vista file permissions on NTSF volume"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by HittingSmoke on 2008-08-07
I had been dual booting Kubuntu for a while and am thinking of making a permanent switch but have one concern.

I have two hard drives. One system drive and one storage drive. I keep the OS and Prog Files on one and have all of my media on my storage drive.

When I was dual booting from the system drive I could not access the files on my storage drive from Kubuntu. I could view the contents of the drive but opening files gave me a permissions error. It is an NTFS volume.

How can I make sure that I can access my media drive if I ditch Windows completely? Also, how bad is it to use an NTFS volume in a Linux box? Ive heard bad things. Is there a way to migrate the file system without losing the data?

---

### Post by SuperSonic4 on 2008-08-07
Have you tried ```
kdesu konqueror
``` and then right clicking and going to mount? It could also be because of an unclean shutdown in windows.

Downloading the ***ntfs configuration tool*** from the repos is good, it will automount drives automatically for you

---

### Post by HittingSmoke on 2008-08-07
Nope, I havent tried anything yet as its not installed any more. I just want to make sure I'm not screwing myself if I make a permanant switch.

When I was dual booting I didnt give it much thought cause I still had access to my windows installation. This time I wont keep it around.

---

### Post by kk0sse54 on 2008-08-07
I use an ntfs filesystem all the time in my linux os's and I haven't come across one problem yet and no there is no way to change a filesystem without destroying the data. As for your permission problem like SuperSonic4 said start konquerer as root and then just change the ownership of the files. If you do it through the terminal use chown to change ownership and chmod to change permissions. Type man chown or man chmod to find out more about them inside the linux terminal. If you are still not confident enough just keep windows around and dual boot them and then when you are comfortable pop in the liveCD delete your windows partition and enlarge you kubuntu partition so it takes up the entire HD.

---

### Post by HittingSmoke on 2008-08-07
Great thats exactly what I needed to know. Thanks

One more question for the sake of not starting a new thread.

Are there compatibility issues with x64 versions of Linux like there are on windows? Are there programs that run better on 32 bit? There's no real reason to use 64 bit unless you have massive amounts of RAM so if 32 bit is less of a headache like it is with windows Ill just stick with it.

---

### Post by SuperSonic4 on 2008-08-07
I believe flash is harder to configure in x64 and there are some dependancy issues if you download, you might have to compile from source although there is a sticky in the x64 users forum which I believe force changes architecture.

Some programs are 32 bit only and will run on 64 bit, I remember installing firefox x86 in the end because of plugins (flash).

Like you said 64bit is only good if you have lots of ram (4gb+) and yeah, I'd stick with 32 bit, there is more support for it after all

---

### Post by HittingSmoke on 2008-08-09
Ok. I made a new Live CD and booted it up. Just to double check before I started installing, I went to Dolphin and tried to open my storage drive. When I try I get a message on the bottom of the window that says "The enclosing drive for the volume is locked" and nothing shows up. I did properly shut down Windows before I booted up the CD.

Any ideas?

---

