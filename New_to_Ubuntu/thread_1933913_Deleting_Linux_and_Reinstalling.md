---
title: "Deleting Linux and Reinstalling"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by Merisi on 2012-03-01
I just reinstalled Ubuntu again today to ensure a clean install and I was wondering that by deleting the previous disc space whether that means what was on there before is permanently deleted?  I deleted the Linux partition in Windows 7.

Edit: I'm guess I'm asking how you delete selected parts of your drive permanently without having to delete everything.

---

### Post by Grenage on 2012-03-01
Secure-delete contains a tool that can securely erase empty drive space.  You can install it with:

```
sudo apt-get install secure-delete
```

The command you probably want is:

```
sfill
```

A more 'ghetto' was of doing it with existing tools is to fill a file with zeros until you run out of room:

```
cat /dev/zero > rubbish.stuff
rm rubbish.stuff
```

---

### Post by grahammechanical on 2012-03-01
In windows when you delete a document/file can you get it back, restore it? Yes. It is the same in Ubuntu. The document has not moved but the labels telling the OS where to find the document have been altered to point to the waste basket/rubbish bin. This is what makes it possible to recover a file that has been deleted.

What happens when we empty the waste basket? The labels get removed but the file stays on the hard disk. But now the OS does not know where to find it.

It is still possible to read what is written there.

Overwrite the part of the disk where that file is with new data and it becomes difficult to read what is written on that part of the hard disk.

It is much easier to overwrite the complete hard disk than selected parts of it. How would you know what area of the disk to overwrite? Do not forget that a hard disk is actually several platters and the file is quite likely spread over more than one platter.

Regards.

---

### Post by QIII on 2012-03-01
Just to be clear...

You said "in Windows".  Was this an Ubuntu install on its own partition, or using Wubi?  There is a difference.  By "in Windows", it sounds like you did a Wubi install.

Not that it matters much as far as your question goes.  Grahammechanical answered that part.

I just wanted to clarify the method of installation because they are two different things.

If you are worried about something from your old installation fouling up the new one, put your mind at ease.  A computer forensic professional could reconstruct some data in casually overwritten disk space.  Not so with space deliberately overwritten with the right tools, as Grenage noted above.  But the new OS won't be bothered by it in any case.

Besides.  If you used Wubi there is no guarantee that the install actually used the very same physical space on the disk as the previous one.

---

### Post by Merisi on 2012-03-01
> **QIII said:**
> Just to be clear...

You said "in Windows".  Was this an Ubuntu install on its own partition, or using Wubi?  There is a difference.  By "in Windows", it sounds like you did a Wubi install.

Not that it matters much as far as your question goes.  Grahammechanical answered that part.

I just wanted to clarify the method of installation because they are two different things.

If you are worried about something from your old installation fouling up the new one, put your mind at ease.  A computer forensic professional could reconstruct some data in casually overwritten disk space.  Not so with space deliberately overwritten with the right tools, as Grenage noted above.  But the new OS won't be bothered by it in any case.

Besides.  If you used Wubi there is no guarantee that the install actually used the very same physical space on the disk as the previous one.

I dual boot alongside Windows.  It does seem that there's no such thing as deleting but instead it's hiding files instead.  

Thank you everyone for your help.

---

### Post by Grenage on 2012-03-01
> **Merisi said:**
> I dual boot alongside Windows.  It does seem that there's no such thing as deleting but instead it's hiding files instead.  

Thank you everyone for your help.

It is deleting them, it's just that you're talking about secure erasure, not simple deletion.  While the dictionary definition of *delete* might mean erasure, in computing, it generally just means that you're freeing up the space for use.

Tools such as the secure-delete suite can completely erase the data.

---

### Post by Merisi on 2012-03-01
> **Grenage said:**
> It is deleting them, it's just that you're talking about secure erasure, not simple deletion.  While the dictionary definition of *delete* might mean erasure, in computing, it generally just means that you're freeing up the space for use.

Tools such as the secure-delete suite can completely erase the data.

Is secure-delete better at this than wipe?  Thank you for your patience with me.

---

### Post by jerome1232 on 2012-03-01
> A more 'ghetto' was of doing it with existing tools is to fill a file with zeros until you run out of room:

```
cat /dev/zero > rubbish.stuff
rm rubbish.stuff
```

Don't knock the 'ghetto' ways!

I used to use dd in a similar fashion

```
dd if=/dev/random of=deleteme.dat bs=1M
rm deleteme.dat
```

---

### Post by Merisi on 2012-03-01
I typed sfill in terminal and got this message

Options:
    -f  fast (and insecure mode): no /dev/urandom, no synchronize mode.
    -i  wipe only inodes in the directory specified
    -I  just wipe space, not inodes
    -l  lessens the security (use twice for total insecure mode).
    -v  is verbose mode.
    -z  last wipe writes zeros, not random data.

I'm unsure how to execute any of them

---

### Post by QIII on 2012-03-01
We tend to think of computers working on 0 an 1.  While this is theoretically true, the physical equipment runs on "pretty close to 0 and pretty close to 1".  Overwriting a disk with zeros leaves a "shadow" of what was there.  That shadow can be read by forensic tools and run through algorithms that can tell with some precision what was there before.

US DoD and State Department standards require a higher level of security than a simpler methods mentioned above. Commonly available tools like DBAN can achieve DoD/State Department levels of erasure.

---

### Post by Grenage on 2012-03-01
> **Merisi said:**
> Is secure-delete better at this than wipe?  Thank you for your patience with me.

I have not used wipe, nor do I know how it works, but I imagine it works in a similar fashion.  The secure-delete tools are just a handy package, and are more commonly used.

> **jerome1232 said:**
> Don't knock the 'ghetto' ways!

I wouldn't dream of it, 'ghetto' powers my computing life. ;)

---

### Post by Grenage on 2012-03-01
> **Merisi said:**
> I typed sfill in terminal and got this message

Options:
    -f  fast (and insecure mode): no /dev/urandom, no synchronize mode.
    -i  wipe only inodes in the directory specified
    -I  just wipe space, not inodes
    -l  lessens the security (use twice for total insecure mode).
    -v  is verbose mode.
    -z  last wipe writes zeros, not random data.

I'm unsure how to execute any of them

This [page]("http://techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/") covers things nicely; you basically just need the mount point.

> **QIII said:**
> We tend to think of computers working on 0 an 1.  While this is theoretically true, the physical equipment runs on "pretty close to 0 and pretty close to 1".  Overwriting a disk with zeros leaves a "shadow" of what was there.  That shadow can be read by forensic tools and run through algorithms that can tell with some precision what was there before.

US DoD and State Department standards require a higher level of security than a simpler methods.  Commonly available tools like DBAN can achieve DoD/State Department levels of erasure.

I've heard that a lot over the years, but am still a little sceptical regarding real-world implementation.  Have you ever seen it done, or know of any reports where it was done?  Not that I wouldn't use random data if deleting something super-secret (I never do), just in case.

---

### Post by QIII on 2012-03-01
See my avatar an my info...

I was a senior Commissioned Field Grade Army Officer with a TS clearance.

You'll have to trust me on this one.

But I don't think the OP needs to worry much about that level of erasure.  :)

---

### Post by Merisi on 2012-03-01
> **Grenage said:**
> This [page]("http://techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/") covers things nicely; you basically just need the mount point.

I still don't get what I should be doing.  Nothing seems to work:confused:

---

### Post by Grenage on 2012-03-01
> **QIII said:**
> See my avatar an my info...

I was a senior Commissioned Field Grade Army Officer with a TS clearance.

You'll have to trust me on this one.

But I don't think the OP needs to worry much about that level of erasure.  :)

Bah, but I love to read! It's fair to say you've probably had more experience than I. ;)

> **Merisi said:**
> I still don't get what I should be doing.  Nothing seems to work:confused:

Lets say that you've got a mounted partition in /media/xxx, you could fill empty space with:

```
sudo sfill /media/xxx/
```

---

### Post by QIII on 2012-03-01
Merisi --

This got a little academic.  Sorry.

Even though sending something to the trash and removing any "label" by emptying the trash does not completely remove it, the space is free to use.  It will be reported as free space and you won't suddenly have a full disk.

Are you really interested in getting rid of them to the point that you don't have to worry about an FBI raid, or do you just want to not be irritated by them and not be able to find them with your file manager and be able to store something else on that physical space on the disk.

---

### Post by Merisi on 2012-03-01
> **QIII said:**
> Merisi --

This got a little academic.  Sorry.

Even though sending something to the trash and removing any "label" by emptying the trash does not completely remove it, the space is free to use.  It will be reported as free space and you won't suddenly have a full disk.

Are you really interested in getting rid of them to the point that you don't have to worry about an FBI raid, or do you just want to not be irritated by them and not be able to find them with your file manager and be able to store something else on that physical space on the disk.

Lol.  I don't think I have to worry about the FBI.  I just wanted a cleaned up hard drive for the best possible install.  This is in preparation for the long term release in April.

---

### Post by QIII on 2012-03-01
Then you really don't need to worry about much.  I've reinstalled many times in the past right over the top of a previous installation.  Just be careful about the partition management.  You can format your partitions if you are worried.

Just install Precise and be happy.

---

### Post by Merisi on 2012-03-01
> **QIII said:**
> Then you really don't need to worry about much.  I've reinstalled many times in the past right over the top of a previous installation.  Just be careful about the partition management.  You can format your partitions if you are worried.

Just install Precise and be happy.

But just out of interest as I suspect you have the knowledge, what is the best way of scrubbing a computer drive clean?

---

### Post by jerome1232 on 2012-03-01
> **Merisi said:**
> But just out of interest as I suspect you have the knowledge, what is the best way of scrubbing a computer drive clean?

Degaussing the drive, dissembling it and shredding the platters. using a drill to drill completely through all platters in several locations.

Unless of course, you still want to be able to use the drive. :P

---

### Post by Merisi on 2012-03-01
> **jerome1232 said:**
> Degaussing the drive, dissembling it and shredding the platters. using a drill to drill completely through all platters in several locations.

Unless of course, you still want to be able to use the drive. :P

:P  That'd definitely work but as you say I would like to use the drive again.

---

### Post by QIII on 2012-03-01
Dang it...

I was composing this and didn't send it!!


> **Merisi said:**
> But just out of interest as I suspect you have  the knowledge, what is the best way of scrubbing a computer drive  clean?

For your purposes, you can use the methods suggested above.

Although DBAN is nice for a whole drive, it's DANGEROUS and probably not  a good choice for a casual end-user.  I was sort of off-topic above.   You don't need to make multiple passes, really.  Just once will do for  stuff that's not a national security risk.  But since DBAN is really  good, it's dangerous.  

The very best thing would be degaussing the platters with large, powerful electromagnets.  (Then melting the drive...)

---

### Post by Merisi on 2012-03-01
> **QIII said:**
> Dang it...

I was composing this and didn't send it!!




For your purposes, you can use the methods suggested above.

Although DBAN is nice for a whole drive, it's DANGEROUS and probably not  a good choice for a casual end-user.  I was sort of off-topic above.   You don't need to make multiple passes, really.  Just once will do for  stuff that's not a national security risk.  But since DBAN is really  good, it's dangerous.  

The very best thing would be degaussing the platters with large, powerful electromagnets.  (Then melting the drive...)

Melting the drive comes easily by just using Ubuntu;) .

---

### Post by QIII on 2012-03-01
Young grandkids do a good job of rendering expensive computer equipment useless.  Sometimes a guy has to rush into a smoke filled room to grab a kid and then run back in with a fire extinguisher.

When your own kids are of a certain age, you sometimes do get files on your computer that the FBI may have interest in.

---

### Post by Merisi on 2012-03-01
> **QIII said:**
> Young grandkids do a good job of rendering expensive computer equipment useless.  Sometimes a guy has to rush into a smoke filled room to grab a kid and then run back in with a fire extinguisher.

When your own kids are of a certain age, you sometimes do get files on your computer that the FBI may have interest in.

I don't let anyone use my PC and I've managed to keep it healthy and virus free and that's how it will stay.  I better mark this thread as solved!

---

