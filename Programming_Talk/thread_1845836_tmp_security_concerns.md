---
title: "/tmp security concerns"
date: 2011-09-17
forum: Programming Talk
---

### Post by N1GHTS on 2011-09-17
How secure is using the /tmp folder to store temporary configuration files that are read and processed during program execution in Ubuntu? They don't contain any passwords, but what I am afraid of is a hacker creating a script which injects code into some of these files, possibly injecting virus code into the programs memory. 

The program runs as a service with root access. I create the file using fopen().

---

### Post by karlson on 2011-09-17
> **N1GHTS said:**
> How secure is using the /tmp folder to store temporary configuration files that are read and processed during program execution in Ubuntu? They don't contain any passwords, but what I am afraid of is a hacker creating a script which injects code into some of these files, possibly injecting virus code into the programs memory. 

The program runs as a service with root access. I create the file using fopen().

Normally UNIX/Linux configuration files are placed in /etc.  /tmp is fairly secure but you will need to make sure that the file permissions are proper.  /tmp is readable and writable by everybody but only if your file permissions allow.  To make sure that your fopen doesn't create world readable and writable files set your umask to 077.

---

### Post by Dangertux on 2011-09-17
EDIT : Nevermind the above suggestion was much better than mine :-P

---

### Post by slavik on 2011-09-17
> **N1GHTS said:**
> How secure is using the /tmp folder to store temporary configuration files that are read and processed during program execution in Ubuntu? They don't contain any passwords, but what I am afraid of is a hacker creating a script which injects code into some of these files, possibly injecting virus code into the programs memory. 

The program runs as a service with root access. I create the file using fopen().
if a configuration file is able to inject code into your program, rethink your design.

---

### Post by lensman3 on 2011-09-17
Take a look at the "t" option of the "chmod" command. /tmp has the tee flag set.  This is the restricted deletion flag or sticky bit and adds extra privileges to the files in the directory.

---

### Post by karlson on 2011-09-17
> **lensman3 said:**
> Take a look at the "t" option of the "chmod" command. /tmp has the tee flag set.  This is the restricted deletion flag or sticky bit and adds extra privileges to the files in the directory.

Deletion is not a concern here, writing to the file is and sticky bit does nothing for XX6 permitted file.

---

### Post by karlson on 2011-09-17
> **N1GHTS said:**
> The program runs as a service with root access. I create the file using fopen().

Something I have overlooked on my last response.

Running an application with root privileges should be rethought.  I mean it's a bad bad bad bad bad idea.  If you need to have a service running that has access to a particular repository of whatever create a directory owned by a particular user group with g+s permissions and give users that need to permission to write to this directory.

---

### Post by nvteighen on 2011-09-18
There are several issues here.

0) You better create temp files using mktemp, tmpfile, mkstmp... but not fopen. You haven't told us what programming language you're using, but those are POSIX functions (well, tmpfile is C99), so it's pretty sure you have them available in any decent UNIX-friendly language.

1) A conf file shouldn't be put in /tmp... it's almost a contradiction. Conf files are meant to be permanent, right?

2) About code injection... ugh... Conf or temp files are used to store values that the program interprets in some way... Use text parsing, not direct code evaluation.

---

### Post by N1GHTS on 2011-09-18
**slavik**: "if a configuration file is able to inject code into your program, rethink your design.     "

Oh, I said "configuration files", which got interpreted as "conf" files. I meant any old file which the software needs to put somewhere temporarily so that it doesn't consume RAM yet still be quickly accessible and in some cases re-loadable as a file: for instance, an image being modified at runtime, or a XML file being extracted from some archive and evaluated at runtime. I misspoke with the word "configuration".


**karlson**: "To make sure that your fopen doesn't create world readable and writable files set your umask to 077"

In C like this?

[umask]("http://linux.die.net/man/2/umask")(077);
[fopen]("http://linux.die.net/man/3/fopen")("/tmp/somefile", "w+");


**karlson**: "Running an application with root privileges should be rethought."

There is only one service of mine that seems to require it. It uses the [libusb]("http://libusb.sourceforge.net/api-1.0/") library to interact with a USB device I created. It can't seem to initialize the device all the way without being root. In that case I only append to a log file, I don't use /tmp.

In the case of the hypothetical application described in the first post, it doesn't NEED to be root and in fact it probably shouldn't be. I just didn't see why a [system service that runs from rc*]("http://www.debuntu.org/how-to-manage-services-with-update-rc.d") running with less permissions would help the security of the system. Though, I guess if the permission of the software was less than root and it were somehow comprimized, it would not aid the hacker much as it could have?


**nvteighen**: "You better create temp files using mktemp, tmpfile, mkstmp... but not fopen"

Brilliant suggestion. Just finished reading out it. Didn't know these functions existed prior to your comment. It sounds like "tmpfile" is what I should use for these situations, and while its [description]("http://linux.die.net/man/3/tmpfile") appears to leave out any mention of how it sets the file permissions, I can only assume its doing it properly, unless I should call "umask()" before it just to be sure.

Also, do you think it would be secure if for bash scripts that extract files for temporary use that I should use "[mktemp]("http://linux.die.net/man/1/mktemp")" and then tell tar to extract it there?


**nvteighen**: "About code injection... ugh... Conf or temp files are used to store  values that the program interprets in some way... Use text parsing, not  direct code evaluation."

While I don't actually do direct code evaluation, what if I wanted to make some kind of a service that generates a binary file.. err.. I can't think of a good reason to do that but I don't see a good reason not to think it may possibly be necessary for some complex program to have a need for that. I posted this question more as a way to educate myself on the "best practice", less on how to actually apply it directly to my project.



Thank you all for your feedback so far. :D

---

### Post by karlson on 2011-09-18
> **N1GHTS said:**
> 
In C like this?

[umask]("http://linux.die.net/man/2/umask")(077);
[fopen]("http://linux.die.net/man/3/fopen")("/tmp/somefile", "w+");


I was referring to the umask in shell.  In C I think it would be:
```

umask(700);
fopen("/tmp/tmpfile", "w+");

```

> 
**karlson**: "Running an application with root privileges should be rethought."

There is only one service of mine that seems to require it. It uses the [libusb]("http://libusb.sourceforge.net/api-1.0/") library to interact with a USB device I created. It can't seem to initialize the device all the way without being root. In that case I only append to a log file, I don't use /tmp.


So make sure that this service reads and writes nothing to temp and has no configuration files beyond initialization.

> 
In the case of the hypothetical application described in the first post, it doesn't NEED to be root and in fact it probably shouldn't be. I just didn't see why a [system service that runs from rc*]("http://www.debuntu.org/how-to-manage-services-with-update-rc.d") running with less permissions would help the security of the system.


If you have the more things you have running as root that allow outside access the more possibility you have to be compromised.  Take a look at apache it doesn't run as root although it would be simpler.

> Though, I guess if the permission of the software was less than root and it were somehow compromised, it would not aid the hacker much as it could have?

If you gained access to a system through a user application with no root access you will still need to compromise the root access to gain access to the entire system.

---

### Post by N1GHTS on 2011-09-18
Great feedback **karlson**! Makes sense to me.

By the way, in C, since the number is octal, I think it would be more like "umask(0700);"

---

### Post by karlson on 2011-09-18
> **N1GHTS said:**
> Great feedback **karlson**! Makes sense to me.

By the way, in C, since the number is octal, I think it would be more like "umask(0700);"

I don't think it has to do with number being octal but you are right there are 4 user settable flag groups.

---

### Post by lensman3 on 2011-09-18
You can also create an invisible temporary file (at least in C) using a file handle.  Then delete it by file name.  Don't close it before you delete it and the file will deleted from the dot file, but will still be open because the of the file handle. 

creat("/tmp/xxx", O);
file = open("/tmp/xxx", O_RDRW);
unlink("/tmp/xxx");

access the file using "file".

---

### Post by slavik on 2011-09-19
> **lensman3 said:**
> You can also create an invisible temporary file (at least in C) using a file handle.  Then delete it by file name.  Don't close it before you delete it and the file will deleted from the dot file, but will still be open because the of the file handle. 

creat("/tmp/xxx", O);
file = open("/tmp/xxx", O_RDRW);
unlink("/tmp/xxx");

access the file using "file".
this is not invisible, this is plain stupid.

you just marked disk space needed for data as free, see the dangling pointer problem, this is the same case, except with file handles.

---

### Post by karlson on 2011-09-19
> **lensman3 said:**
> You can also create an invisible temporary file (at least in C) using a file handle.  Then delete it by file name.  Don't close it before you delete it and the file will deleted from the dot file, but will still be open because the of the file handle. 

creat("/tmp/xxx", O);
file = open("/tmp/xxx", O_RDRW);
unlink("/tmp/xxx");

access the file using "file".

Oh how many people have been fired for doing stupid things like this.....  

What do you think will happen if the filesystem fills up?

---

### Post by Arndt on 2011-09-19
> **slavik said:**
> this is not invisible, this is plain stupid.

you just marked disk space needed for data as free, see the dangling pointer problem, this is the same case, except with file handles.

It's not dangling - the kernel knows which process has the file open.

---

### Post by Arndt on 2011-09-19
> **karlson said:**
> I don't think it has to do with number being octal but you are right there are 4 user settable flag groups.

I don't know what the relevance of the number 4 is here, but 700 and 0700 are certainly different numbers in C. The reason expressing file permissions in octal is convenient is that there are three bits for each main field (user, group, other).

---

### Post by karlson on 2011-09-19
> **Arndt said:**
> I don't know what the relevance of the number 4 is here, but 700 and 0700 are certainly different numbers in C. The reason expressing file permissions in octal is convenient is that there are three bits for each main field (user, group, other).

I must be confused then but doesn't "number is octal" mean "base 8 number"?  I do understand that permissions can be expressed in "octal notation" but that is not what was written.  And as far as umask function is concerned: 700 = 0700, since mode_t is just and unsigned integer.

The relevance of the number 4 is simple.  There are 4 user settable groups of permissions numerically broken down as follows:
Group 1: SETUID, SETGID, Sticky Bit
Group 2: User, R, W, X
Group 3: Group, R, W, X
Group 4: Other: R, W, X

Within the same integer there is actually more settings that can be read using stat(), but they are in general not changeable by using normal tools.

---

### Post by N1GHTS on 2011-09-19
> **karlson said:**
> I must be confused then but doesn't "number is octal" mean "base 8 number"?  I do understand that permissions can be expressed in "octal notation" but that is not what was written.  And as far as umask function is concerned: 700 = 0700, since mode_t is just and unsigned integer.

The relevance of the number 4 is simple.  There are 4 user settable groups of permissions numerically broken down as follows:
Group 1: SETUID, SETGID, Sticky Bit
Group 2: User, R, W, X
Group 3: Group, R, W, X
Group 4: Other: R, W, X

Within the same integer there is actually more settings that can be read using stat(), but they are in general not changeable by using normal tools.

It being an unsigned integer has nothing to do with how you pass data to the function. 

An Unsigned integer is typically 32 bit, so you got 32 bits to work with:
```
Unsigned Integer Bits: 00000000000000000000000000000000
```The define macro's for the flags you can use in umask() are described in octal notation (it must start with a zero to activate it in C). Here is just a copy/paste of a part of it:
```

#define S_IRWXG 0000070                 /* RWX mask for group */
#define S_IRGRP 0000040                 /* R for group */
#define S_IWGRP 0000020                 /* W for group */
#define S_IXGRP 0000010                 /* X for group */

```So you have at least 4 groups using 3 bits, that's 12 bits, well under the 32 bit limit:
```

mode_t: 00000000000000000000wrxwrxwrxwrx

```umask() could have even gotten away with making it an unsigned short (16 bit):
```

16 bit mode_t: 0000wrxwrxwrxwrx

```On the other end of umask() it may test the flags like this: 
```

if (mode_t & S_IRWXO == S_IROTH) // just a random example

```So it doesn't matter what the type of the parameter is because its operating at a much lower level. The unsigned type simply describes how large the canvas of bits are for your flags.

---

### Post by karlson on 2011-09-19
> **N1GHTS said:**
> It being an unsigned integer has nothing to do with how you pass data to the function. 

An Unsigned integer is typically 32 bit, so you got 32 bits to work with:
```
Unsigned Integer Bits: 00000000000000000000000000000000
```The define macro's for the flags you can use in umask() are described in octal notation (it must start with a zero to activate it in C). Here is just a copy/paste of a part of it:
```

#define S_IRWXG 0000070                 /* RWX mask for group */
#define S_IRGRP 0000040                 /* R for group */
#define S_IWGRP 0000020                 /* W for group */
#define S_IXGRP 0000010                 /* X for group */

```So you have at least 4 groups using 3 bits, that's 12 bits, well under the 32 bit limit:
```

mode_t: 00000000000000000000wrxwrxwrxwrx

```umask() could have even gotten away with making it an unsigned short (16 bit):
```

16 bit mode_t: 0000wrxwrxwrxwrx

```On the other end of umask() it may test the flags like this: 
```

if (mode_t & S_IRWXO == S_IROTH) // just a random example

```So it doesn't matter what the type of the parameter is because its operating at a much lower level. The unsigned type simply describes how large the canvas of bits are for your flags.

I stand corrected.  ...Open mouth insert foot.

---

### Post by lensman3 on 2011-09-19
> **karlson said:**
> Oh how many people have been fired for doing stupid things like this.....  

What do you think will happen if the filesystem fills up?

That's why /tmp is on its own partition, so I can't fill the disk up.  And as you write to the file, check the status return of write. One of the returned conditions is "disk full".  

Same problems happen if you know the name of the file in /tmp.  All you are doing is removing the file name from being visible to other processes.

As was said the kernel knows the file is open and when the process goes away so does the file.

---

### Post by karlson on 2011-09-19
> **lensman3 said:**
> That's why /tmp is on its own partition, so I can't fill the disk up.  And as you write to the file, check the status return of write. One of the returned conditions is "disk full".

Normally it isn't because there is no reason for it to be.  Also you are being too Linux centric here.  Solaris for example puts this /tmp basically into swap.

> 
Same problems happen if you know the name of the file in /tmp.  All you are doing is removing the file name from being visible to other processes.

As was said the kernel knows the file is open and when the process goes away so does the file.

If you know the filename and it is visible you can do:
```

$ /bin/cp /dev/null /tmp/<filename>

```
and your space goes away and if you have to kill the process creating the file every time this file becomes too large you will have a problem because for example taking down accounting system during quarter close or trading system during a market crash or something similarly mission critical is a no no.

---

### Post by nautilus on 2011-09-20
libusb shouldn't have any reason to require root permission.  perhaps your usb device has permissions which aren't conducive for interacting with your application as an otherwise unprivileged user?

if so, this can typically be fixed by fiddling with udev rules.  this is a normal thing to do in various cases, such as using adb with an android phone on ubuntu.

in any case, if your code writes files which are then read back in without ensuring sane boundaries and sane content, i suppose code injection is a concern, but if i were running that application it would probably be pretty low on my list of worries! :)

besides that, a poor-man solution to permissions and similar might be to simply name the file with a tempfile token prefix followed by the file checksum.  then, if the sum of the contents don't match the sum in the file name, you'll know it was tampered with.  i still wouldn't run it as root though.

---

### Post by N1GHTS on 2011-09-20
> **nautilus said:**
> libusb shouldn't have any reason to require root permission.  perhaps your usb device has permissions which aren't conducive for interacting with your application as an otherwise unprivileged user?

if so, this can typically be fixed by fiddling with udev rules.  this is a normal thing to do in various cases, such as using adb with an android phone on ubuntu.

Can you give me some examples or reference links to allowing a libusb program to access a device without root access? This has annoyed me ever since working with libusb.

---

### Post by N1GHTS on 2011-09-20
> **lensman3 said:**
> That's why /tmp is on its own partition, so I can't fill the disk up.  And as you write to the file, check the status return of write. One of the returned conditions is "disk full".  

Same problems happen if you know the name of the file in /tmp.  All you are doing is removing the file name from being visible to other processes.

As was said the kernel knows the file is open and when the process goes away so does the file.

I understand where you're coming from with your strategy, and its actually really crafty, although it doesn't seem like the most correct thing to do. It seems like a duct-tape strategy, one which may be a better fit in the Windows world. I just can't imagine a major corporation protecting their valuable temp files by virtually deleting them prior to use.

But if I ever needed to write a virus, I'll keep that technique in mind.

---

