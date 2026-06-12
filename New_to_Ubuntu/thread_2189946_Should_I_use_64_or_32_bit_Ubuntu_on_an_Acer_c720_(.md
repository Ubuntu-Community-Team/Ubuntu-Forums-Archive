---
title: "Should I use 64 or 32 bit Ubuntu on an Acer c720 (or other Chromebook)?"
date: 2013-11-24
forum: New to Ubuntu
---

### Post by mossfoot2 on 2013-11-24
I am planning on getting a Chromebook, probably an Acer c720-the 4GB RAM version (don't let the Amazon price fool you, it's actually $250).

[http://www.amazon.com/Acer-Chromebook-11-6-Inch-Haswell-micro-architecture/dp/B00FNPD1OY/ref=sr_1_1?ie=UTF8&qid=1385348738&sr=8-1&keywords=acer+c720](http://www.amazon.com/Acer-Chromebook-11-6-Inch-Haswell-micro-architecture/dp/B00FNPD1OY/ref=sr_1_1?ie=UTF8&qid=1385348738&sr=8-1&keywords=acer+c720)

My understanding is that 32 bit OS can only use 2GB of RAM and 64bit is needed to take advantage of anything more powerful. (please correct me if I'm wrong).  

I'm pleased to see that installing Ubuntu seems to be easy on the Acer c720 Chromebook, but want to make sure I get the most out of the 4GB version (otherwise, wouldn't I be better off getting their new 2GB version that is $50 cheaper?).  Can anyone tell me (in laymans terms) what kind of performance differences there is between 32 and 64,  what advantages there are to taking one over the other, and whether I'm better off getting the 4GB or 2GB version?

Alternately I'm also considering the Asus 1015E, too.

[http://www.amazon.com/ASUS-1015E-DS03-10-1-Inch-Laptop-Black/dp/B00COQK8QY/ref=sr_1_1?ie=UTF8&qid=1385348673&sr=8-1&keywords=asus+netbook](http://www.amazon.com/ASUS-1015E-DS03-10-1-Inch-Laptop-Black/dp/B00COQK8QY/ref=sr_1_1?ie=UTF8&qid=1385348673&sr=8-1&keywords=asus+netbook)

Any advice on these, or other similarly priced laptops that would be "ideal" to run Ubuntu would be appreciated!

---

### Post by electrohandyman501 on 2013-11-24
You could go for the 4G 64bit hardware, then test the live32 or live64 to determine which one works best with the hardware.
I'm using a 32 bit os with 4G ram and it works fine.
If you are thinking of using ubuntu in a VM as a guest, you have have issues with 64bit as the guest os.

---

### Post by fantab on 2013-11-24
32bit Linux/Ubuntu OS with [**PAE**]("https://help.ubuntu.com/community/PAE") can work well with more than 2Gb RAM. If your processor supports 64bit then it should be 64bit, for a simple reason its relatively modern and faster.

Regarding RAM, simply put, more the better. With respecting to saving $50, this entirely depends on your usuage. If you intend to put your netbook to just basic usuage, like browsing net, writing and ocassional document, some music and Video from YouTube or elsewhere, then 2GB RAM will do it for you. Still if can afford more then go for it.

Between Acer and Asus, personally I like Asus and I'd go for it. However between your two options, Acer Chromebook sounds better but for the only 16GB SSD. Now that is a serious limitation, if I were you. But again it depends on what you want to store in there, if this just the OS with a few documents, then it can serve the purpose.

---

### Post by oldfred on 2013-11-25
Newer computer with decent graphics chip. May not apply to an older one.
32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)
Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.

We are just about to the point that if your think you need 32 bit, you do not want full Ubuntu but need Lubuntu or maybe Xubuntu. Some users prefer those gui anyway.

---

### Post by mossfoot2 on 2013-11-25
> **fantab said:**
> 
Between Acer and Asus, personally I like Asus and I'd go for it. However between your two options, Acer Chromebook sounds better but for the only 16GB SSD. Now that is a serious limitation, if I were you. But again it depends on what you want to store in there, if this just the OS with a few documents, then it can serve the purpose.

I admit I like ASUS.  I am still using the Asus 901 Netbook using Xubuntu. Hell, I thank them for extending its life because it was originally with Windows XP but eventually got borked and I was unable to reinstall.  Thanks to Xubuntu (and initially lubuntu) I got the netbook working again. 

But the specs on the C720 are very impressive, and I'm hearing good things about it online.  The fact it only has 16GB of storage isn't a big deal (given that the 901 has WAY less than that).  And it could always be expanded with an SD card.

My primary intention for the new machine is a work computer.  I'm a writer and editor, so I need to be able to use Microsoft Word (via WINE) as well as fast and efficient web browsing.  Beyond that is all bonus, but bonus is good.  My 901 lasted me over five years, and I want whatever I choose next to do the same.

---

### Post by fantab on 2013-11-25
Not sure about Acer, but my Asus 1015CX Netbook gives a battery life of more than 7 hrs. with Fedora_Xfce 32bit. With Windows, it can go upto 11hrs. That is another aspect you should consider. For the kind of work you mention 2gb RAM should be more than enough with Xfce. Not sure how much system resources will MOffice consume along with Wine. But yes, bonus is good.

Find out if you can replace 16GB SSD with something like 120Gb or 250Gb SSD... agreed that it will be costly, but it is a storage device and can last quite longer than HDDs.

---

### Post by NilPointer on 2013-11-25
I'd surely recommend Ubuntu 64 bit:

1) It's faster, when possible (since it could use full power of 64 bit CPU for 64 bit apps).
2) It doesn't cause incompatibilities with 32 bit software. If any problems arise, they will be likely fixed by installing 32-bit libraries package (ia32-libs or something like that).

---

### Post by jCjQszKMO5JH on 2013-11-25
32-bit OSes support up to **4** GB of memory, not 2. If you go for discrete graphics the total memory of the GPU and system needs to be under 4GB, but the two options you're looking at use integrated GPUs anyway.

That said, there's really no disadvantage to a 64-bit OS. There are slight memory overheads in some cases, but with 4GB of RAM you will be fine on Ubuntu.

---

