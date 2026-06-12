---
title: "[SOLVED] C/C++: How to store text in the executable itselfs?"
date: 2008-03-20
forum: Programming Talk
---

### Post by WitchCraft on 2008-03-20
Question:

My program has to execute another program, on a adjustable location.

So I first ask the user to point me to the executalbe, so i can get the path.

Now, I can store the path to the executalbe in a .ini textfile, in the same directory as my executable.

How can I actually store this text (fixed size, some 100 to 1000 chars) in my program itselfs (I mean that the user cannot modify the ini file anymore) ?

Do I need to create a dll, or can I allocate space somehow in the .exe file, and then memcopy it to a pointer with the position in the file?

---

### Post by LaRoza on 2008-03-20
> **WitchCraft said:**
> Question:

My program has to execute another program, on a adjustable location.

So I first ask the user to point me to the executalbe, so i can get the path.

Now, I can store the path to the executalbe in a .ini textfile, in the same directory as my executable.

How can I actually store this text (fixed size, some 100 to 1000 chars) in my program itselfs (I mean that the user cannot modify the ini file anymore) ?

Do I need to create a dll, or can I allocate space somehow in the .exe file, and then memcopy it to a pointer with the position in the file?

I wouldn't try to restrict the user. Just have the .ini file have a line in it asking it not to be edited. In Linux, almost everything is a text file for storing settings, and all except one can be edited with a text editor.

Also, you should store the text file where you know the user will have write access (their home directory).

---

### Post by mike_g on 2008-03-20
Cant you use relative addressing? 

The simplest way to deal with it otherwise would be to write it to a file perhaps in binary, encrypted and obfuscated amongst other things (even just random crap).

---

### Post by WitchCraft on 2008-03-20
> **mike_g said:**
> Cant you use relative addressing? 

The simplest way to deal with it otherwise would be to write it to a file perhaps in binary, encrypted and obfuscated amongst other things (even just random crap).

No, I want the textfile gone, the location of the program is no secret, so no need for encryption.

Basically the question comes down to one thing:
How to read/write to the file of the currently running executable?

---

### Post by LaRoza on 2008-03-20
> **WitchCraft said:**
> No, I want the textfile gone, the location of the program is no secret, so no need for encryption.

Basically the question comes down to one thing:
How to read/write to the file of the currently running executable?

The question comes down to: will the user have write access to the executable?

It is possible, just find the string of the path in the executable and replace it (open as binary), but this probably won't work in the real world.

---

### Post by LaRoza on 2008-03-20
> **WitchCraft said:**
> No, I want the textfile gone, the location of the program is no secret, so no need for encryption.

Basically the question comes down to one thing:
How to read/write to the file of the currently running executable?

The question comes down to: will the user have write access to the executable?

It is possible, just find the string of the path in the executable and replace it (open as binary), but this probably won't work in the real world.

---

### Post by mike_g on 2008-03-20
You can open a c binary file and view the text as it is in a text editor; although if its big it is likely to crash the editor.

---

### Post by LaRoza on 2008-03-20
> **mike_g said:**
> You can open a c binary file and view the text as it is in a text editor; although if its big it is likely to crash the editor.

Use a hex editor.

---

### Post by ruy_lopez on 2008-03-20
You could use mmap to map a section of the executable, then overwrite a preallocated string. I'm pretty sure it's not a safe, or even sane, thing to do. I wouldn't recommend it.

---

### Post by LaRoza on 2008-03-20
> **ruy_lopez said:**
> You could use mmap to map a section of the executable, then overwrite a preallocated string. I'm pretty sure it's not a safe, or even sane, thing to do. I wouldn't recommend it.

Neither would I.

Is there a reason you want this OP?

You can have the user just compile it in. (Make a program to compile this with the information)

---

### Post by Awalton on 2008-03-20
> **WitchCraft said:**
> No, I want the textfile gone, the location of the program is no secret, so no need for encryption.

Basically the question comes down to one thing:
How to read/write to the file of the currently running executable?

There's no compelling reason you need this on a modern machine and programming environment. This was a fun trick to do back in the golden old era of computing, particularly on platforms which liked everything in one condensed fat file. You see this on Windows a lot still (Mac OS X actually uses a directory structure, they just present it as a single file to the user).

In Linux, you want to keep the file separate, period. If you need to know if the file changes, add a monitor and watch its mtime. If you need to prevent it from being changed, change its permissions and ownership, or just load the data the first time around, keep it in memory and throw it back out when you're exiting. This is the UNIX way of thinking, and Linux is no different.

---

### Post by pmasiar on 2008-03-20
> **WitchCraft said:**
> How to read/write to the file of the currently running executable?

Why you need that?

Binary executable file reads text config file with parameters, why you need patch body of binary program to change parameters if they can live in separate config file?

---

### Post by jpkotta on 2008-03-20
This reminds me of a problem we had at work.  We were playing around with OpenMoko (not anymore, unfortunately), and we were trying to get this GPS program working.  It was a proprietary program, and there was a hard coded file name for a file in sysfs.  A kernel update changed the sysfs entry, and the program broke, with no way to fix it.  But there was a way!  Someone ran strings on it, saw what file it was looking for, and used sed to change the string.  I was simultaneously impressed and horrified.

---

### Post by WitchCraft on 2008-08-20
> **jpkotta said:**
> This reminds me of a problem we had at work.  We were playing around with OpenMoko (not anymore, unfortunately), and we were trying to get this GPS program working.  It was a proprietary program, and there was a hard coded file name for a file in sysfs.  A kernel update changed the sysfs entry, and the program broke, with no way to fix it.  But there was a way!  Someone ran strings on it, saw what file it was looking for, and used sed to change the string.  I was simultaneously impressed and horrified.

sed, nice, it's a very useful tool, I have used it, too ;-)

There is an article on Borland CodeGear, although for Delphi, I converted it to cpp.

Problem solved.

---

