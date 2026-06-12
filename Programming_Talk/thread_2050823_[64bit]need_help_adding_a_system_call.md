---
title: "[64bit]need help adding a system call"
date: 2012-08-31
forum: Programming Talk
---

### Post by amlas on 2012-08-31
hi,
i'm new around here, and i've got a little stuck while trying to add system call..
i'm trying to work out this [project]("http://www.ivanescobar.com/oper1_material/projectch2.pdf"), however since my system is 64 bit some of the files don't match and i need help to find where they are, i've tried to google this without any success..

first one-
where should i add the .long entry? i found an entry.S file in-
/usr/src/linux-3.5.3/arch/ia64/kernel but i'm not sure that's the right file, cause i can't find any "table" in it.

second-
"Add your &#64257;le helloworld.c to the Make&#64257;le (if you created a new &#64257;le for your system call.)... You can now build
the new kernel, rename it to distinguish it from the unmodi&#64257;ed kernel,"

what is that Makefile?
and should i build the new kernel by compiling the kernel files from /usr/src/linux-3.5.3/ ?

thanks for your help:)

---Edit by sandyd---
Converted problematic pdf to something a bit more readable. [http://oc.sandyd.me/public.php?service=files&token=ff92236b8d1bfe5f0b5f77d79645406326bab236&file=/docu/uf/12209223/projectch2.pdf](http://oc.sandyd.me/public.php?service=files&token=ff92236b8d1bfe5f0b5f77d79645406326bab236&file=/docu/uf/12209223/projectch2.pdf)

---

### Post by Bachstelze on 2012-08-31
The pdf is blank... Your problem is probably not that your system is 64bits (because the source is the same on all systems), but that you are using a different kernel version.

---

### Post by ofnuts on 2012-08-31
> **Bachstelze said:**
> The pdf is blank... 
Not blank, white... white text on a white background :D. Okular or othe rPDF readers can copy all the text to the clipboard...

---

### Post by lisati on 2012-08-31
Is this homework for extra credits? We don't mind providing hints, but the [forum rules]("http://ubuntuforums.org/index.php?page=policy") don't allow us to be a homework service.

---

### Post by Bachstelze on 2012-08-31
> **lisati said:**
> Is this homework for extra credits? We don't mind providing hints, but the [forum rules]("http://ubuntuforums.org/index.php?page=policy") don't allow us to be a homework service.

The PDF probably contains detailed instructions, and the only reason they don't work is because they are for a different kernel version. Even if this were homework, no question has been asked regarding programming proper, just compilation.

---

### Post by sandyd on 2012-08-31
> **amlas said:**
> hi,
i'm new around here, and i've got a little stuck while trying to add system call..
i'm trying to work out this [project]("http://www.ivanescobar.com/oper1_material/projectch2.pdf"), however since my system is 64 bit some of the files don't match and i need help to find where they are, i've tried to google this without any success..

first one-
where should i add the .long entry? i found an entry.S file in-
/usr/src/linux-3.5.3/arch/ia64/kernel but i'm not sure that's the right file, cause i can't find any "table" in it.

second-
"Add your &#64257;le helloworld.c to the Make&#64257;le (if you created a new &#64257;le for your system call.)... You can now build
the new kernel, rename it to distinguish it from the unmodi&#64257;ed kernel,"

what is that Makefile?
and should i build the new kernel by compiling the kernel files from /usr/src/linux-3.5.3/ ?

thanks for your help:)
Btw, just a small hint -

/usr/src/linux-3.5.3/arch/ia64/kernel

is for Itanium Arches.

/usr/src/linux-3.5.3/arch/x86/kernel

is for **both** x86 and x86_64 arches. Its because the kernel starts both x86 and x86_64 arches in 16-bit, does some administrative work, .etc .etc, and then switches either to 32-bit or 64-bit, depending on how the kernel is compiled. You can set the arch in the menuconfig.

For more info, see [https://lkml.org/lkml/2007/7/20/447](https://lkml.org/lkml/2007/7/20/447)

---

### Post by lisati on 2012-08-31
> **Bachstelze said:**
> The PDF probably contains detailed instructions, and the only reason they don't work is because they are for a different kernel version. Even if this were homework, no question has been asked regarding programming proper, just compilation.

The reason I mention homework is that the PDF file is hosted on a professor's website. I also recall seeing one or two similar questions by other users in recent weeks.

---

### Post by Bachstelze on 2012-08-31
Okay, it's a scan from the book by Silberschatz et al., and indeed it does not work with recent kernels. I made [a corrected version](http://pastebin.com/izL2Spjn) some time ago. As you can see, it uses kernel 2.6.32. It does not work either on 3.x, but at least it gives you an exact kernel version on which to do it. If you want to use the book's instructions, you have to go back to at least 2.6.15 IIRC.

*EDIT:*

And no I do not have the time right now to find out how to do it on 3.x.

Also, it's for 32 bits. Porting it to 64 bits should be obvious, or just make a 32 bits VM (it's probably a good idea to work in a VM anyway when you are doing kernel work).

And if the instructions are pretty specific, it's because I had made a VirtualBox VM with pre-configured kernel source for my classmates to use. It should be easy to figure it out, though. In particular, the source tarball was obtained by installing [font=monospace]linux-source[/font] on Ubuntu Lucid.

---

### Post by amlas on 2012-09-01
thanks for the replies, i'll try to look again for 3.5.3 instructions, worst case i'll go back a few versions.

and about the hw issue- thats not an academic work, i'm learning by myself using the mentioned book(Operating System Concepts [Abraham Silberschatz,Peter B. Galvin,Greg Gagne]), the link was something that i ran into, while googling earlier.

---

