---
title: "make problems"
date: 2013-07-19
forum: Packaging and Compiling Programs
---

### Post by Murdoc_of_puts on 2013-07-19
So just about any time I try to make something from the source file using the make make install install dynamic, it doesn't work.  I pretty much will get a message similiar to this.

murdoc@poopzilla:~/compat-drivers-3.9-rc4-2$ sudo make install
Warning:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against ./scripts/update-initramfs. If your distribution does not require this
send a patch against the '/usr/bin/lsb_release -i -s': "Ubuntu"
tag for your distribution to avoid this warning.

make -C /lib/modules/3.2.0-49-lowlatency/build M=/home/murdoc/compat-drivers-3.9-rc4-2 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-49-lowlatency'
  CC [M]  /home/murdoc/compat-drivers-3.9-rc4-2/compat/main.o
In file included from /home/murdoc/compat-drivers-3.9-rc4-2/include/linux/compat-2.6.h:71:0,
                 from <command-line>:0:
/home/murdoc/compat-drivers-3.9-rc4-2/include/linux/compat-3.8.h:49:32: error: redefinition of ‘kref_get_unless_zero’
include/linux/kref.h:47:32: note: previous definition of ‘kref_get_unless_zero’ was here
make[3]: *** [/home/murdoc/compat-drivers-3.9-rc4-2/compat/main.o] Error 1
make[2]: *** [/home/murdoc/compat-drivers-3.9-rc4-2/compat] Error 2
make[1]: *** [_module_/home/murdoc/compat-drivers-3.9-rc4-2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-49-lowlatency'
make: *** [modules] Error 2
murdoc@poopzilla:~/compat-drivers-3.9-rc4-2$ 



--Now most of the time I have a folder for drivers and other programs in my home folder.  Is the location what's messing this up?  I have also tried moving this to the /usr/bin/ folder with about the same results.  This is really fustrating, because I know that I'm just being stupid about this.  Any help would greatly be appreciated

+I have make and build-essential installed

---

### Post by oldos2er on 2013-07-20
Moved to Packaging & Compiling Programs.

---

### Post by Gunman1982 on 2013-08-02
Look here: [https://bugzilla.kernel.org/show_bug.cgi?id=59041]("https://bugzilla.kernel.org/show_bug.cgi?id=59041")

---

### Post by Murdoc_of_puts on 2013-08-08
Thanks, I forgot that I needed to also compile the kernel in order for anything else to actually compile.  Thank you.

---

