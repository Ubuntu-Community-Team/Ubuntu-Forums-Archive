---
title: "/dev"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by CoffeeRain on 2011-10-24
I don't really know where to put this, but here it is... How are the /dev/null and /dev/zero files made. It sort of seems like magic. Like how does /dev/zero have unlimited of a certain character even. I opened it up with a text editor, and it was just a new file. It didn't even have a scroll bar on it. Could you explain?? :o

---

### Post by CharlesA on 2011-10-24
Those are special system devices. /dev/null points to "nothing" and /dev/zero points to an area that is full of zeros.

Check out /dev/urandom and panic. ;)

---

### Post by CoffeeRain on 2011-10-25
Thanks, but this also brings something else up. I figured out how to use tty and other files, but how do you use random and urandom? If I read it, it spits out TONS of characters. And another thing, how were the null and zero files made? Is there a way with human coding that a file could have infinite characters in it?

---

### Post by mcduck on 2011-10-25
They are not files as any regular file you have. Or, to put it  another way, in Unix & Linux *everything* is a file, including every device and component on your computer (these are in /dev) and every process that's running on the system (these are in /proc).

So files like /dev/zero are not files located on your hard drive, they are simply features of the Linux kernel, made to appear as files for easy access by the user and any process running on the system. This way the permissions of different features and devices can be configured the same way that is used for actual files, and accessing them is also as simple as reading/writing any other file. 

(How to create a file with endless amount of zeroes? Simple, make a *program* that returns zeroes for you as long as it's running. And that's basically what /dev/zero is. Of course /dev/random and /dev/urandom are bit more complicated than that, random number generation is a tricky process, you'll want to see [Wikipedia]("http://en.wikipedia.org/wiki//dev/random") for those...)

---

### Post by cryptotheslow on 2011-10-25
Clearly it would not be possible to store an infinitely large file of anything.

/dev/null
/dev/zero
/dev/urandom

Are not "real" files they are provided by the system (builtin to the kernel I think). Whenever something reads from them the system just continues to chuck out nulls, zeros or random characters until asked to stop (Ctrl-C for example).

To use them you generally pipe them into another process. Most common use I've seen for zero and urandom is in conjunction with the dd command to wipe hard disks or partitions. (Careful with dd - all too easy to hose your system if you dd over your installation partition :D )

---

### Post by 3rdalbum on 2011-10-25
> **CoffeeRain said:**
> Thanks, but this also brings something else up. I figured out how to use tty and other files, but how do you use random and urandom? If I read it, it spits out TONS of characters.

For some kinds of applications, you need random data; or as random as you can possibly get from a computer. These applications include encryption and secure deletion of data. If you're just trying to securely delete data to prevent the computer's next owner from finding your details, it's usually sufficient to use /dev/zero for the deletion of data - it's a lot quicker, and still pretty secure against all but the most well-funded attackers.

The 'random' and 'urandom' "files" provide an unlimited amount of pseudo-random data for these applications.

> And another thing, how were the null and zero files made? Is there a way with human coding that a file could have infinite characters in it?

It's not really a file. When a program attempts to read from these kinds of files, it's actually opening up a connection to the Linux kernel, which feeds that data through under the guise of it being a file. With /dev/null, if a program attempt to write to it, the kernel just removes that written data from memory immediately.

---

### Post by CoffeeRain on 2011-10-25
Wow thanks. I didn't know that. So how would you use /dev/null to delete files? I could echo something into it, but what about a file?

---

### Post by mcduck on 2011-10-25
Well, it's a file, not a directory, so you can't really move a file there to erase it.

You *can* use it to empty a file, with something like "cat /dev/null > somefile", which would leave the file around (with permissions intact) but completely erase it's contents. Although just doing ": > somefile" would be even easier.

Anyway, here are some uses for /dev/zero and /dev/null: [http://tldp.org/LDP/abs/html/zeros.html]("http://tldp.org/LDP/abs/html/zeros.html")

---

### Post by CharlesA on 2011-10-25
> **mcduck said:**
> 
Anyway, here are some uses for /dev/zero and /dev/null: [http://tldp.org/LDP/abs/html/zeros.html]("http://tldp.org/LDP/abs/html/zeros.html")

Nice link. I really like tldp. :D

---

### Post by CoffeeRain on 2011-10-25
Thanks! :D

---

### Post by The Cog on 2011-10-25
The "files" in /dev are really device drivers. 

/dev/sda represents your hard disk for instance, and you can perform raw reading/writing to the disk through it. Writing could easily trash your disk of course, so be careful.

/dev/null is a device driver that just ignores anything you write to it. Reading from it just returns EndOfFile straight away. /dev/zero is a simple "driver" that also doesn't drive any real hardware, but that returns zeros for as long as you can be bothered to keep reading from it. /dev/random is a driver for a (usually software) random number generator that returns an endless stream of random numbers for as long as you keep reading.

Most drivers are for realy hardware of course, but a few, like the ones above, are for inbuilt pseudo-devices.

---

