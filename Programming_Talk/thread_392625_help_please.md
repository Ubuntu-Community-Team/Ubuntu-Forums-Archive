---
title: "help please"
date: 2007-03-24
forum: Programming Talk
---

### Post by k0mpresd on 2007-03-24
i am new to linux so please bare w/ me

i installed crosstool and ran sh demo-powerpc970.sh

i also installed a newer version of binutils

i am trying to run these commands:
```
sudo mount -t squashfs -o loop,ro ubuntu-livecd/casper/filesystem.squashfs mnt/
```

can someone explain what the above code means?

im also trying to run:
```
ninux$ alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
ninux$ smake
```
but i get errors

i have the linux image mounted in /mnt/x360

and when i run the second set of code i get:
> k0mpresd@k0mp:~/Desktop/linux-2.6.20$ alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ smake
/home/k0mpresd/Desktop/linux-2.6.20/scripts/gcc-version.sh: line 11: powerpc64-unknown-linux-gnu-gcc: command not found
/home/k0mpresd/Desktop/linux-2.6.20/scripts/gcc-version.sh: line 12: powerpc64-unknown-linux-gnu-gcc: command not found
make: powerpc64-unknown-linux-gnu-gcc: Command not found
/home/k0mpresd/Desktop/linux-2.6.20/scripts/gcc-version.sh: line 11: powerpc64-unknown-linux-gnu-gcc: command not found
/home/k0mpresd/Desktop/linux-2.6.20/scripts/gcc-version.sh: line 12: powerpc64-unknown-linux-gnu-gcc: command not found
*** 2.6 kernels no longer build correctly with old versions of binutils.
*** Please upgrade your binutils to 2.12.1 or newer
make: *** [checkbin] Error 1
k0mpresd@k0mp:~/Desktop/linux-2.6.20$

can someone help me out? i dont really know what im doing here and am searching for any answers i can get

reference page for what im trying to do ~> [http://mydedibox.homelinux.com/modules/smartsection/item.php?itemid=3](http://mydedibox.homelinux.com/modules/smartsection/item.php?itemid=3)

---

### Post by nereid on 2007-03-25
Ok, the first command mounts an image to a folder with the squashfs filesystem (*man mount* for more information).

The second one should create an alias but I don't know why you would like to create one on the fly instead of writing it in your .bashrc file, if you use it more than one time.

You are trying to cross compile from PPC to PPC64 architecture and you get the errors in the last quote field, because the alias is wrong. Bash thinks that *powerpc64-unknown-linux-gnu* is a command instead of a variable. Maybe you would like to try this without creating the alias.

---

### Post by k0mpresd on 2007-03-25
> **nereid said:**
> 
The second one should create an alias but I don't know why you would like to create one on the fly instead of writing it in your .bashrc file, if you use it more than one time.

You are trying to cross compile from PPC to PPC64 architecture and you get the errors in the last quote field, because the alias is wrong. Bash thinks that *powerpc64-unknown-linux-gnu* is a command instead of a variable. Maybe you would like to try this without creating the alias.
can you please explain this a little further?

what is alias and how is it wrong?

im so confused

several ppl told me to just install crosstool in /opt/crosstool which is what ive done and it doesnt work..i dont understand what is wrong

getting the kernel compiled is my main goal for now

---

### Post by winch on 2007-03-25
After you installed crosstool did you add it to you path?
If you installed it in /opt/crosstool you probably want to add /opt/crosstool/bin to your path

export PATH=$PATH:/opt/crosstool/bin

Browse /opt/crosstool to check that's where it put powerpc64-unknown-linux-gnu-gcc.
After doing that make sure the shell can find the compiler, running

powerpc64-unknown-linux-gnu-gcc
should produce something like
powerpc64-unknown-linux-gnu-gcc: no input files

Once the shell can find the compiler run make again.

---

### Post by k0mpresd on 2007-03-25
thank you winch..notice the bold ;)

i now have a new probelm.:
> k0mpresd@k0mp:~/Desktop/linux-2.6.20$ **export PATH=$PATH://home/k0mpresd/crosstool-0.43/build/powerpc64-unknown-linux-gnu/gcc-4.1.0-glibc-2.3.6/gcc-core-prefix/bin**
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ alias smake='make ARCH=powerpc CROSS_COMPILE=powerpc64-unknown-linux-gnu-'
k0mpresd@k0mp:~/Desktop/linux-2.6.20$ smake
*** 2.6 kernels no longer build correctly with old versions of binutils.
*** Please upgrade your binutils to 2.12.1 or newer
make: *** [checkbin] Error 1
k0mpresd@k0mp:

i have downloaded and installed binutils-2.17 and installed it like this:
```
./configure
make
sudo make install
```

but i still get the same error?

the binutils readme says this:
> If you have more than one compiler on your system, it is often best to
explicitly set CC in the environment before running configure, and to
also set CC when running make.  For example (assuming sh/bash/ksh):

	CC=gcc ./configure
	make

but i dont know if that applies to me or how to install it correctly if it does

---

### Post by k0mpresd on 2007-03-26
no one knows about binutils issue?

---

