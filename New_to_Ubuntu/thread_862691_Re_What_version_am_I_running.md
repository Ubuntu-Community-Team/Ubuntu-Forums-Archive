---
title: "Re: What version am I running?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by foxmulder881 on 2008-07-17
Is there a simple command to check whether you one is running 32 or 64bit?

I know that I am running 64bit but am just curious if such a command exists? And if not, why not?

---

### Post by Sef on 2008-07-17
Moved to absolute beginners.

Yes, there is, as soon as I can remember it, I will post it, unless someone else does first.

---

### Post by johnnybravo666 on 2008-07-17
```
uname -m
``` should do it.

---

### Post by drs305 on 2008-07-17
```
uname -m
```

x86_64 is 64-bit

See Sef's reply below: hardware, not software...

---

### Post by AndyCooll on 2008-07-17
And
```
uname -a
```
will give you the same information and more.

:cool:

---

### Post by Sef on 2008-07-17
> uname -m

That tells one the hardware, not the software.

---

### Post by Sef on 2008-07-17
This is the command to find what version you are using

```
lsb_release -a
```

---

### Post by drs305 on 2008-07-17
Results of "lsb_release -a":
```
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

```

That is the same return on my machines running 64-bit ubuntu and 32-bit ubuntu so that doesn't really say whether the software is 32 or 64 bit. 

I looked up the man page and Sef is right that the 'uname -m' command describes the 'machine' - didn't know that...

---

### Post by ilrudie on 2008-07-18
try ```
cat /boot/config-`uname -r` | grep X86_64
```for me it returns```
# CONFIG_X86_64 is not set
``` and I'm on a 32-bit box.
It will probably say something different if you are running a 64-bit kernel.

---

### Post by drs305 on 2008-07-18
> **ilrudie said:**
> 
It will probably say something different if you are running a 64-bit kernel.

On my 64-bit system, it returns:
```

~: cat /boot/config-`uname -r` | grep X86_64
CONFIG_CRYPTO_AES_X86_64=m
CONFIG_CRYPTO_TWOFISH_X86_64=m
CONFIG_X86_64=y
CONFIG_X86_64_ACPI_NUMA=y

```

I'd refine ilrudie's command a bit further, and make it:
```

~: cat /boot/config-`uname -r` | grep CONFIG_X86_64=

```

which would return:
```

CONFIG_X86_64=y

```

Now the final test would be to see the output from a 64-bit user who has installed 32-bit ubuntu...

---

### Post by ilrudie on 2008-07-18
> **drs305 said:**
> On my 64-bit system, it returns:
```

~: cat /boot/config-`uname -r` | grep X86_64
CONFIG_CRYPTO_AES_X86_64=m
CONFIG_CRYPTO_TWOFISH_X86_64=m
CONFIG_X86_64=y
CONFIG_X86_64_ACPI_NUMA=y

```I'd refine ilrudie's command a bit further, and make it:
```

~: cat /boot/config-`uname -r` | grep CONFIG_X86_64=

```which would return:
```

CONFIG_X86_64=y

```Now the final test would be to see the output from a 64-bit user who has installed 32-bit ubuntu...

Thanks for the backup.  Don't have my 64-bit box handy.  I would be interested in what someone with a 64-bit chip and a 32-bit kernel would say.  I imagine its going to say the same thing mine did though.

---

### Post by ilrudie on 2008-07-18
Also ```
file /boot/vmlinuz-`uname -r`
``` is an option.  I get ```
 Linux kernel x86 boot executable
``` along with some other junk on ubuntu and```
 ELF 32-bit LSB shared object
``` on centos.  Both are 32-bit. Any one on a 64-bit box care to weigh in?
As a side note I think this is a pretty interesting question.  It seems like it should be super simple but the answer doesn't seem to be.

---

### Post by drs305 on 2008-07-18
> **ilrudie said:**
> Also ```
file /boot/vmlinuz-`uname -r`
``` is an option.  I get ```
 Linux kernel x86 boot executable
``` along with some other junk on ubuntu and```
 ELF 32-bit LSB shared object
``` on centos.  Both are 32-bit. Any one on a 64-bit box care to weigh in?
As a side note I think this is a pretty interesting question.  It seems like it should be super simple but the answer doesn't seem to be.

64-bit system/machine:
```
/boot/vmlinuz-2.6.24-19-generic: Linux kernel x86 boot executable RO-rootFS, root_dev 0x801, swap_dev 0x1, Normal VGA
```

It doesn't look like this sheds much light. I PM'd you about posting a request on the 64-bit forum for the results of the previous command on a 64-bit machine running 32-bit ubuntu.

Maybe there should be a warning halfway down this thread with a warning: 
```

Caution: Geeks only from this point forward.

```  ;-)

---

### Post by 3rdalbum on 2008-07-18
> **drs305 said:**
> 
I'd refine ilrudie's command a bit further, and make it:
```

~: cat /boot/config-`uname -r` | grep CONFIG_X86_64=

```

which would return:
```

CONFIG_X86_64=y

```

Now the final test would be to see the output from a 64-bit user who has installed 32-bit ubuntu...

There is no output when you are running a 32-bit Ubuntu on a 64-bit machine.

---

### Post by ilrudie on 2008-07-18
Hmmm...  I was thinking that it may work better than the original post I made and you tweaked.  Unfortunate that Ubuntu doesn't seem to differentiate 64 and 32 bit binaries with file.  Probably has something to do with the magic file uses but I really don't feel like mucking with it right now.  A friend of mine confirmed it works for Power PC under fedora though.  I agree with your assertion that the question has pretty much been answered and the search for the best answer is really just a geek quest at this point.

Also the presence of /proc/sys/kernel/vsyscall64 indicates an X86_64 kernel.

---

### Post by ilrudie on 2008-07-18
> **3rdalbum said:**
> There is no output when you are running a 32-bit Ubuntu on a 64-bit machine.

Yeah.  Thats what I would have guessed.  It should say 
# CONFIG_X86_64 is not set in the config file but the grep pattern won't match that because of the '='

---

### Post by nikloleta on 2008-07-18
Try uname -a

---

### Post by ilrudie on 2008-07-18
> **nikloleta said:**
> Try uname -a
returns the type of hardware the kernel is running on (among a myriad of other things) but not what type of kernel is running*.  This has been discussed above already.

*unless the name/revision of the kernel happens to include if its 64bit or not which some kernels may include but Ubuntu's doesn't seem to.

---

### Post by bodhi.zazen on 2008-07-18
> **ilrudie said:**
> returns the type of hardware the kernel is running on (among a myriad of other things) but not what type of kernel is running*.  This has been discussed above already.

*unless the name/revision of the kernel happens to include if its 64bit or not which some kernels may include but Ubuntu's doesn't seem to.

uname -a shows the arch of the current running kernel.

i686 = 32 bit

x86_64 = 64 bit

cat /proc/cpuinfo shows cpu info

---

### Post by drs305 on 2008-07-18
> **bodhi.zazen said:**
> uname -a shows the arch of the current running kernel.

i686 = 32 bit

x86_64 = 64 bit

cat /proc/cpuinfo shows cpu info

That's what I always thought but Sef brought up a good point. If you look at the man page for *uname* it says:

```
 
-m, --machine
    print the machine hardware name
```

The -m switch would be the part of -a that prints out the "x86_64", which it would seem is the machine architecture - or is the man page just poorly worded... 

:confused:

---

### Post by bab1 on 2008-07-18
Or, does machine refer to the OS machine?  Such as the machine in JVM.

Ah...semantics

---

### Post by bodhi.zazen on 2008-07-18
Output form a 32 bit kernel:
> bodhi@hardy:~$ uname -a
Linux hardy 2.6.24-19-virtual #1 SMP Sat Jul 12 01:38:14 UTC 2008 **[COLOR=red]i686[/COLOR]** GNU/LinuxOutput from a64 bit kernel
> bodhi@hardy:~$ uname -a
Linux hardy 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 **[COLOR=red]x86_64[/COLOR]** GNU/Linux

---

### Post by Yannick Le Saint kyncani on 2008-07-18
> **foxmulder881 said:**
> Is there a simple command to check whether you one is running 32 or 64bit?

dpkg --print-architecture

Print architecture of packages dpkg installs (for example, "i386")

---

### Post by ilrudie on 2008-07-18
Regarding post #22:
I believe this is only the case when the 32-bit kernel is on 32-bit hardware.  If I get a little time over the weekend I will put at 32-bit image on my phenom at home and see.  One of the other SAs at work says he has a machine at home running at 32-bit kernel on 64-bit hardware and it reports x84_64 under uname -a and uname -m.  As stated by #20 this is the behavior expected from reading the man pages.

---

### Post by bodhi.zazen on 2008-07-18
> **ilrudie said:**
> Regarding post #22:
I believe this is only the case when the 32-bit kernel is on 32-bit hardware.  If I get a little time over the weekend I will put at 32-bit image on my phenom at home and see.  One of the other SAs at work says he has a machine at home running at 32-bit kernel on 64-bit hardware and it reports x84_64 under uname -a and uname -m.  As stated by #20 this is the behavior expected from reading the man pages.


Here is the output on a 64 bit machine running a 32 bit kernel :

> uname -a
Linux ubuntu 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 **[COLOR=red]i686[/COLOR]** GNU/Linux

dpkg --print-architecture
**[COLOR=red]i386[/COLOR]**

cat /proc/cpuinfo
<clip>
vendor_id : AuthenticAMD
cpu family : 16
model  : 2
model name : **[COLOR=red]AMD Phenom(tm) 9500 Quad-Core Processor[/COLOR]**As you can see this is a 64-bit quad core Phenom

---

### Post by SunnyRabbiera on 2008-07-18
Well you can do it the easy way, check under system > administration > system monitor and check the first tab :D

---

### Post by drs305 on 2008-07-18
> **SunnyRabbiera said:**
> Well you can do it the easy way, check under system > administration > system monitor and check the first tab :D

Actually, the discussion (I think - it started so many posts ago) is about how to determine whether a 64-bit machine is running a 32-bit or 64-bit kernel via the command line.

Imagine, 27+ posts on uname! I'm withdrawing for the sake of my mental health ...

---

