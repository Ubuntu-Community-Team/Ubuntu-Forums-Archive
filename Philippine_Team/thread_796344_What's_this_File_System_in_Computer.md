---
title: "What's this File System in Computer?"
date: 2008-05-16
forum: Philippine Team
---

### Post by SHENGTON on 2008-05-16
Hello again Ubuntu Experts!

Just confuse with this Computer of Ubuntu.
1. What's this "File System" in Computer?
2. Is this a folder where all the system files of Ubuntu are place?
3. Is this equivalent of WINDOWS folder in Windows?

Thanks and God bless!

---

### Post by Jucato on 2008-05-16
1. It is the root (/) directory, the very very top directory which contains all others. 

2. Yes. It's the top folder where everything, system files, and user files are located. Kung baga sa puno, yun ang ugat.

3. No, since WINDOWS is not the top level directory and other folders like Program Files are outside of it. There is not direct comparison in Windows. Ang pinakamalapit na ay C:\ if you have only 1 drive.

Some references:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://blog.linuxoss.com/2008/05/10/cool-way-linux-filesystem-hierarchy/](http://blog.linuxoss.com/2008/05/10/cool-way-linux-filesystem-hierarchy/)

---

### Post by SHENGTON on 2008-05-16
Ahh, so yong File System na makikita natin is just equivalent to drive C: in Windows.

Salamat po Sir!

---

### Post by yssida on 2008-05-16
> **SHENGTON said:**
> Ahh, so yong File System na makikita natin is just equivalent to drive C: in Windows.

Salamat po Sir!

Parang ganun na rin po. Kasi Ubuntu does things a bit differently. So halimbawa may dalawa kang partition sa Windows, ito makikita mo ito sa my computer as C: and D: usually. Sa Linux and Ubuntu, isa lang talaga makikita mo. Ito yung tinawag niyong 'File System' or root directory. 

So paano mo makikita ang dalawa mong partition? Inside the root directory. Usually, ang mounted na media (the disk or partition which you can use) is found on /media with their respective name minus the partition you are in, or usually just a description. You might also find there a CD/DVD drive, etc.

Think of it this way, in Ubuntu, there is only one tree and one root directory. In Windows, you have many trees, each with their own hierarchy of files, but of course, you have one tree which rules them all, the one which contains your system files. That's drive C: by default.

---

### Post by SHENGTON on 2008-05-17
Wow, thank you po tala Sir yssida. Naiintindihan ko na po. Pero meron po akong parang hindi pa malinaw sa utak ko.

> Think of it this way, in Ubuntu, there is only one tree and one root directory.
Anong ibig niyong sabihin po dito Sir yssida?

> In Windows, you have many trees, each with their own hierarchy of files
Anong ibig niyong sabihin dito Sir na maraming tress ang Windows? Kindly give some examples Sir.

---

### Post by yssida on 2008-05-17
> [QUOTE]Think of it this way, in Ubuntu, there is only one tree and one root directory. Anong ibig niyong sabihin po dito Sir yssida?[/QUOTE]

I'm not really good at at explaining,but here goes. In Ubuntu, or Linux generally, there is only one root directory. It starts at "/". You can see for yourself, try typing / in the file browser. From there, you will see all your files, all your partitions, devices, etc. Your partitions and their files will be inside the folder "/media"

In Windows, if you have two partitions like I did, you will get a drive C: and a drive D:. So when you search for your files, you have to either pick C:\ or D:\. And each of these drives has its own hierarchy. Maybe you use C:/ for system files, and D:/ for documents. etc...

Na-confuse din ako nito mga 2 months ago when I started using Ubuntu exclusively, pero ngayon di na. Just keep on tinkering with your computer. Learn as much as you can, ask on forums,etc. At tsaka, wag nyo po ako tawagin sir..Hehe...di ko ata keri yun....hehe,.16 pa lang po ako.

---

### Post by SHENGTON on 2008-05-17
Thanks again yssida! Ok tol na lang...hehehe...Thanks ulit!

---

### Post by Samhain13 on 2008-05-18
Great explanation, yssida.

Nung bago din ako, nalito din ako. Isa yata talaga sa mga unang hinahanap ng mga taong bago sa Linux yung Drive C o Drive D o whatever. Nung una din akong nakasubok ng Mac OS X, isa yun sa mga una kong hinanap. Hehehe.

---

