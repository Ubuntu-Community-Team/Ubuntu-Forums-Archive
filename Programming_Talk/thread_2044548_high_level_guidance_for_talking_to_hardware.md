---
title: "high level guidance for talking to hardware"
date: 2012-08-19
forum: Programming Talk
---

### Post by teryret on 2012-08-19
Hello all I was hoping to solicit some opinions (or relevant links) as to right ways and wrong ways to think about talking to hardware.

For example, I know that /dev/ is full of yellow file-like *things*(?) that act as intermediaries between hardware and software.  I'm not sure where they come from, do drivers create them?  If I wanted to use pure java to talk to a device is this a good way to do it?  (The driver for the device is written in C and lives in user space, but I want to avoid JNI and SWIG.)

If for some morbid reason I wanted to create a thing like /dev/zero that spat out Lorem Ipsum instead of 0 could I do that?

---

### Post by TheFu on 2012-08-19
**Use the source Luke.**  Take a look at the kernel and driver source code to learn all. If the driver is available, you should use that API to interface with the device. If the source code for the driver isn't provided and you want to know more, take a look in the kernel tree for similar hardware.  Many drivers for a specific card are just modified versions of already existing drivers.

I don't know anything about java programming, so I can't say whether this is a good or bad idea.

---

### Post by teryret on 2012-08-19
Thanks for the response.  Unfortunately I don't really have the time nor the ability to read through all the kernel source that is relevant to dealing with hardware.  That, and I'm really more concerned about the general high level approaches as opposed to specific low level implementation details of any particular device.

For the sake of a hypothetical, if I had invented some crazy new hardware and wanted to write a driver for it in C that I would somehow talk to from pure java, what are the names of the top-level concepts I should google for, and how do they fit together?

I imagine it might start with USB-HID?  Would the kernel hook up a HID device it didn't recognize to /dev/?  Does a driver daemon need to get inserted in there somewhere?  When might a device need to become a kernel module?  These are the sorts of questions I have, I'm not really trying to get any specific thing working.

---

### Post by TheFu on 2012-08-19
> **teryret said:**
> Thanks for the response.  Unfortunately I don't really have the time nor the ability to read through all the kernel source that is relevant to dealing with hardware.  That, and I'm really more concerned about the general high level approaches as opposed to specific low level implementation details of any particular device.

You don't need to read all the kernel source, just look at the source for a module similar to what you are considering.  Read the "Kernel module howto docs" too.

> **teryret said:**
> 
For the sake of a hypothetical, if I had invented some crazy new hardware and wanted to write a driver for it in C that I would somehow talk to from pure java, what are the names of the top-level concepts I should google for, and how do they fit together?


The kernel is written in C for many reasons. Modules are written in C for similar reasons - to **reduce the number of dependencies,** provide a** small memory** footprint, to be **FAST,** and since the kernel and kernel modules run with root, **security** is a huge concern. Java is not used because it is heavy, slow, sucks up memory and running it as root is a huge security risk for the entire system.  Java for end-users apps makes sense. Java for web application servers makes sense, but java for kernel and hardware control does not compute.   I would **never** try to force Java into the kernel.   I was trying to be diplomatic before, but I'm sorry for my failure.

> **teryret said:**
> 
I imagine it might start with USB-HID?  Would the kernel hook up a HID device it didn't recognize to /dev/?  Does a driver daemon need to get inserted in there somewhere?  When might a device need to become a kernel module?  These are the sorts of questions I have, I'm not really trying to get any specific thing working.

The kernel understands specific devices base on the loaded modules. There is no magic. If you call something a HID, then it needs to behave like a HID. If the kernel doesn't have a module or the device driver hasn't been built for the system, it will not be recognized.

To access hardware in Linux usually (always?) demands escalated privileges. Some kernal calls are restricted to the kernel itself, so if you want to make those calls, then you need to extend the kernel ... with a kernel module. Is this making sense?

I haven't written a kernel module in 10 yrs, so my memory is a little fuzzy, but I don't think that things have changed that much.

Found lots of good hits after googling for 
* "linux device driver howto"
* "kernel module howto"

---

### Post by teryret on 2012-08-19
Lol, I didn't catch it before.  But no I agree Java should be avoided for most purposes.  I wouldn't spend a second with it on my own projects.

I think you're ascribing me more knowledge than I have in this area.  That first query you gave had lots of great info, tons of depth.  The first hit definitely helped me clarify what /dev/ actually is.  It all seems to be making the assumption that I the reader know what I want to learn about, but at this point I really don't.

I haven't done much with hardware, but I have a few experiences that all seem to be quite different, I'm just trying to fit it all together in my head.

For example, if I wanted to use a PS3 controller to control a python script I would use Willow Garage's ps3joy "driver".  It's written in python and takes data from a bluetooth connection, massages it, and sends it out to /dev/uinput (which I could look up how to read from).  I'm sure that doing it this way has its pros and cons (but I don't know any of them).  If instead of a PS3 controller I wanted to use a Space Pilot Pro I would instead use the spacenavd "driver" from the repos.  I assume it's written in C++, but the curious thing about it is that it runs as a daemon (which I believe implies that it runs in user space), takes data from *somewhere*, massages it, and sends it outs to clients that connect either through X11(?) or an AF socket.  I'm sure that doing it this way has its pros and cons as well (but again I couldn't name any).  I've learned that "drivers" can also be compiled into the kernel, and they can be loaded in dynamically too (is this what modprobe does?).  So that's four different ways of talking to hardware.  Are there more?  When might I choose one over another?  With such significant amount of variety in things that call themselves drivers, would it be safe to say that driver is a less formal term than I first imagined?

The only reason I brought up Java is because I wanted an example of a language that a hardware consuming app might be written in that makes some of these four approaches of drivers harder to deal with than others.  It's easy to open a file-like thing in java, but it's not easy to connect to an AF socket (for example).

---

### Post by the_unforgiven on 2012-08-20
> **teryret said:**
> I haven't done much with hardware, but I have a few experiences that all seem to be quite different, I'm just trying to fit it all together in my head.

For example, if I wanted to use a PS3 controller to control a python script I would use Willow Garage's ps3joy "driver".  It's written in python and takes data from a bluetooth connection, massages it, and sends it out to /dev/uinput (which I could look up how to read from).  I'm sure that doing it this way has its pros and cons (but I don't know any of them).  If instead of a PS3 controller I wanted to use a Space Pilot Pro I would instead use the spacenavd "driver" from the repos.  I assume it's written in C++, but the curious thing about it is that it runs as a daemon (which I believe implies that it runs in user space), takes data from *somewhere*, massages it, and sends it outs to clients that connect either through X11(?) or an AF socket.  I'm sure that doing it this way has its pros and cons as well (but again I couldn't name any).  I've learned that "drivers" can also be compiled into the kernel, and they can be loaded in dynamically too (is this what modprobe does?).  So that's four different ways of talking to hardware.  Are there more?  When might I choose one over another?  With such significant amount of variety in things that call themselves drivers, would it be safe to say that driver is a less formal term than I first imagined?

The only reason I brought up Java is because I wanted an example of a language that a hardware consuming app might be written in that makes some of these four approaches of drivers harder to deal with than others.  It's easy to open a file-like thing in java, but it's not easy to connect to an AF socket (for example).

You almost always talk to the hardware using entries under /dev.
There are no 4 ways that you talk about - the "driver" for the hardware always resides in the kernel - either as a loadable module or compiled into the kernel binary.

Loadable modules allow for:
o. smaller initial kernel binary
o. dynamically adding support for newer hardware
o. not loading drivers for hardware that you don't have

With drivers compiled into the kernel binary, you get:
o. no need to load drivers to activate/use the hardware - reducing dependencies
o. larger kernel binary
o. no way of removing code from kernel that may not be used (possibly, because h/w not present?)

Nowadays, most of the distros try to ship as much of the code as possible as loadable modules instead of built into the kernel binary. This allows them to remain very flexible and still support newer hardware without a full kernel recompile.

Now, how does the kernel understand which driver to use for which device?
It uses two magic nos. called major and minor nos.
If you look at the entries under /dev, you'd find it to look something like:```
crw-rw-rw- 1 root root 1, 5 2012-08-16 08:54 /dev/zero
```
The nos. before the date in the above entry are the major and minor nos.
Each driver registers these nos. with the kernel (in short telling the kernel that "I'll handle all operations for the major no. x minor no. y").

This is as far as "drivers" are concerned.
However, how do you actually use these drivers from your application code?
Simple - by just opening the files under /dev using normal system calls like open(), read() and write() - like you'd use a normal file.
You may sometimes find some special libraries (something like [libserial]("http://libserial.sourceforge.net") or [libusb]("http://www.libusb.org")) that provide a nicer programming interface to the resp. devices.

Now, obviously, not every user should be allowed to read/write to a device, right? This is why you'd find that entries under /dev to be owned by user root and having rw permissions only for root.
What this means is that if you write an application to talk to one of the devices using one of these entries, your app needs to be run as root.
In some cases, the device may need to be available/usable by other non-root users but still maintain sanctity of the system. In such cases, you'd find that there is a daemon/service running that talks to the device and provides a well-defined and restricted API for the application.

HTH ;)

---

### Post by teryret on 2012-08-20
Fantastic!  Thank you soooo much!  That's exactly the glue I was missing!

Is there any sort of standard format for the characters that flow into and out of /dev devices, or it is necessarily device dependent?

---

### Post by the_unforgiven on 2012-08-21
> **teryret said:**
> Is there any sort of standard format for the characters that flow into and out of /dev devices, or it is necessarily device dependent?

No, the OS doesn't enforce any particular format for the data written to/read from the device(s) - it only provides ways to access the device. This is about [separation of policy and mechanism]("http://en.wikipedia.org/wiki/Separation_of_mechanism_and_policy") - the OS only provides (or should provide) mechanism.

The rest is upto the device and the application using the device to figure out the formatting specifics.

However, the devices are generally grouped into following groups:
o. char devices - presenting the data as a stream of characters.
o. block devices - presenting the data as blocks (e.g. hard-disks)
o. FIFO devices - presenting a connection between two applications/endpoints that transfers data in first-in-first-out fashion
o. sockets - like normal BSD sockets (with AF_UNIX address family - check [unix(7)]("http://linux.die.net/man/7/unix") manpage for details).

This classification dictates what operations are possible on the device(s) - for example, you cannot [seek]("http://linux.die.net/man/3/lseek") into a FIFO (and some char devices).

The "c" at the beginning of the /dev/zero entry in my previous example indicates that it's a char device.
Similarly, for hdds (like /dev/sda[0-9]), you'd find a "b" at the beginning of 'ls -l' output indicating that it's a block device.

Mind you, all the devices under /dev need NOT be actual physical devices - they can be virtual devices as well (e.g. /dev/zero, /dev/null, /dev/tty).

HTH ;)

---

### Post by TheFu on 2012-08-21
Just saw this tutorial on writing linux device drivers [http://www.freesoftwaremagazine.com/articles/drivers_linux](http://www.freesoftwaremagazine.com/articles/drivers_linux)

---

