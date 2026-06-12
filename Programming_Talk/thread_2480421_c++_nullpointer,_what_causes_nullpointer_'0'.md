---
title: "c++ nullpointer, what causes nullpointer '0' ?"
date: 2022-10-29
forum: Programming Talk
---

### Post by Sceiron on 2022-10-29
Why do fopen return 0 (nullpointer) in this case? Does nullpointer mean the folder/location /sys/bus/devices/iio:device0 doesnt exist?


#include <unistd.h>
#include <stdio.h>
#include <iostream>
using namespace std;

int main()
{
   FILE *export_file = NULL; //declare pointers
   FILE *IO_direction = NULL;
   FILE *IO_value = NULL;
   char str[] = "cat in_voltage6_raw";
   // this part sets the device to exrpot analogue values from
   //this part here sets the direction of the pi

   cout << fopen ("/sys/bus/devices/iio\:device0", "w");

  // int tempvalue = fwrite (str, 1, sizeof(str), IO_value);
//   cout << tempvalue;
//   fclose (IO_value);
}

---

### Post by l-daniel on 2022-10-29
Despite all the ads, I find cplusplus.com useful. See [https://cplusplus.com/reference/cstdio/fopen/](https://cplusplus.com/reference/cstdio/fopen/) for additional information on fopen.

Here's the section on fopen's return:
**Return Value**

[INDENT]If the file is successfully opened, the function returns a pointer to a [FILE]("https://cplusplus.com/FILE") object that can be used to identify the stream on future operations.
Otherwise, a null pointer is returned.
On most library implementations, the [errno]("https://cplusplus.com/errno") variable is also set to a system-specific error code on failure.[/INDENT]

errno should be available on Ubuntu. You can use perror to print a message, which you could share here. See [https://cplusplus.com/reference/cstdio/perror/](https://cplusplus.com/reference/cstdio/perror/) if you need more info.

Dan

---

### Post by Sceiron on 2022-10-29
Thanks daniel, i update op with a '\' in the path. So i think this is the problem since it treats it as a escape character. How do i define the filepath for fopen when it contains a '\' ?

---

### Post by TheFu on 2022-10-29
For most C function calls, a return value of int(0) means all is good.  It is the non-zero returns that mean an error happened.
fopen() is a call call.

BTW, nobody uses cout for anything except debugging when you are new and don't know any better.  A proper debug class would build a stack trace, pushing and popping functions on/off the stack until a non-zero return happens.  I've worked places that would either have a single errror class (static) that we'd push errors onto or that had a return-code class that would be passed around for every major function requested by a user which would get all return codes and any messages pushed into that single instance.  Both ways worked.  Passing around the RC calls was more hassle, but necessary in client/server CORBA code with 4-tier applications.

cout should be writing to stdout which should be setup by the main() creation.  We get stdin, stdout and stderr for all programs by default.  Of course, it is possible to close those files manually, if we like. I've not done that on any Unix-like OS. In fortran using card readers, we'd have to specify the input and output files we wanted. Typically that was the data cards that came after the program source code input and the printer for output, but that's completely different than on these modern systems with CRTs and disk storage.  ;)

---

### Post by Sceiron on 2022-10-29
Ok, so i'm a beginner, and dont know any better :D And im running this on a BeagleBoneBlack.
[https://www.teachmemicro.com/beaglebone-black-blink-led-using-c/](https://www.teachmemicro.com/beaglebone-black-blink-led-using-c/) I'm trying to follow this, but change it over to reading analogue values like described here: [https://elinux.org/EBC_Exercise_10a_Analog_In](https://elinux.org/EBC_Exercise_10a_Analog_In)
From the shell i can read the analogue values of /sys/bus/devices/iio\:device0/in_voltage6_raw so thats working, only problem is that i cant "translate" the blink example to "reading analogue values"
Current code:
#include <unistd.h>
#include <stdio.h>
#include <iostream>
using namespace std;

int main()
{
   FILE *IO_value;
   char str[] = "cat in_voltage6_raw";
  // string st = R"(/sys/bus/devices/iio\:device0)";
  // cout << st;
IO_value = fopen (R"(/sys/bus/devices/iio\:device0)", "w");// attempt with string literal
cout << IO_value;  // returns '0'
 int tempvalue = fwrite (str, 1, sizeof(str), IO_value);
 cout << tempvalue;
}


Gives a Segmentation fault  when running the program... Any ideas? I guess fwrite does not return an int, so its probably an issue, but but ..... hmm ?

---

### Post by l-daniel on 2022-10-29
You mentioned a literal '\' in the path. To get a C string with '\' double it: '\\' (escape itself).

On your latest post: If IO_value is NULL, fwrite to it may very well give a segmentation fault.

---

### Post by TheFu on 2022-10-29
I don't have that specific device, but some file systems aren't to be written or cannot be written without running as root.  /sys/ is a pseudo-file system. Basically, it maps settings from hardware devices into a file system so we can make use of the core Unix idea "everything is a file".

I typically use /proc/ for stuff, not /sys/, so I'd need to spend more time doing research to clearly understand the purpose of the /sys file system.

/sys is definitely distro/kernel specific. [https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)  See [https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch06.html#sysKernelAndSystemInformation](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch06.html#sysKernelAndSystemInformation) for the specifics.  The paragraph there is pretty clear - anything under /sys/ can change from kernel to kernel.  This is a good reason not to use it, IMHO. It is likely to change and things dependent on it will break.

---

### Post by Sceiron on 2022-10-31
Ok, do i understand it correct that you are saying:
1. When i do cat in_voltage6_raw from the linux command line (as root) i get the Voltage?
[B][I]root@beaglebone:/sys/bus/iio/devices/iio:device0# cat in_voltage0_raw
3263[/I][/B]
2. But when i run that command from my c++ app i do not execute the command as root, so it will not work?

That might be a issues i havent thought about, but i guess fopen should return something. I just got the Bjarnes S bible for C++, so i will try some reading up

Anyways,

---

### Post by TheFu on 2022-10-31
I never said anything about voltages.  I don't know.

I said that there are pseudo-files uses as interfaces into the hardware and that those interfaces aren't stagnant and shouldn't be used directly.  At least that was my intent.  Application programs should use OS services created by the kernel team to query the hardware.

BTW, we don't know the units for anything in /proc or /sys.  We can guess the units and for many hardware things, those will be common sense, but for some things, often the units are very strange, unexpected.
 
C++ references seldom explain Unix POSIX permissions.  You'll need to understand those.

---

### Post by l-daniel on 2022-11-01
Scieron:

If fopen fails, it returns NULL. The man pages for fopen explain this. You can also look at the man pages for errno and perror to find out how to get more information about why the failure happened.

If you think you've identified a permissions problem specifically tied to not running as root, try running your C++ program with sudo (assuming it's safe to do so).

TheFu:

I've played with Linux over the years, but haven't yet done what I would consider "real" Linux programming and think of myself as a newbie - in short, apologies if this is naive.

Aren't the psuedo file systems the only interface to the kernel for some things? One of my frustrations is that it seems the only way to get some information is to read text from a psuedo file and then scan it back in (kernel printfs, user process scanfs, over and over again). For  one query, this is no big deal, but my stupid brain worries about all the servers heating up the planet with the extra CPU cycles! Okay, that's (mostly) a joke; but I'm used to the lowest level interfaces minimizing time and or power. Higher level interfaces get built on top of that (ideally in userspace, since privileged kernel cycles are more precious).

Ultimately, it seems like there are many places in the GNU/Linux (and therefore Ubuntu) world where giving up a significant performance factor (of, say, 2 or more) is considered acceptable to meet some conceptual tidiness. There doesn't seem to be any "invisible hand" driving to squeeze out all but, say, a single percentage digit of the approximate performance potential.

Setting aside the act of purging myself of an inner demon of obsessive cycle counting, are there always syscalls to get information more directly from the kernel? Or, at least, always a compact binary variant in the virtual file system?

Thanks,

Dan

---

