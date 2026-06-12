---
title: "Local access is root access?"
date: 2009-08-17
forum: Recurring Discussions
---

### Post by Ozor Mox on 2009-08-17
Something I have been wondering about for quite a long time...

Once in a while, a thread will come up where someone claims to have discovered a way to get root permissions on Ubuntu locally. Two examples I can think of off the top of my head are modifying the .bashrc file to include an alias to a fake sudo script that gets the password, and booting Ubuntu in recovery mode where root access is automatically given.

Usually along the course of the discussion, several people point out that these exploits can only work if someone has local access to the machine, and that local access should effectively be considered root access. When the argument is made that Ubuntu should be secure locally, the reply is often "what if they use a live CD?" or "what if they take the hard drive out and put it in another computer?" or "what if they steal the entire PC?".

Although this makes sense in a way, there are two things that have always bothered me about it. Firstly, what about universities, schools, internet cafes, libraries? Surely they must be securing their boxes from local access, not just "slowing people down" by providing barriers to access. I certainly remember at my university, it was not possible to boot from a live CD or USB stick, nor access the BIOS. Do they just use thin clients in these cases?

Secondly, there is a thread on the first page at the moment about a Linux kernel exploit that can be used locally to get root access. If local access really *was* root access, why would an exploit like this have such a fuss made over it, and need to be patched so fast? Surely it wouldn't matter, because locking your screen, putting on a BIOS password, etc. is just "slowing them down".

So my question is, is local access *really* root access, or can it be made secure?

---

### Post by Tibuda on 2009-08-17
My university computers are physically locked, so people would have to break the lock to reset the BIOS password or remove the hard disk. This is just another 'slow down', but if there are many people at the computer lab, nobody will try to break the lock, because everybody can see what they are doing..

- People can log as root from GRUB. Solution: Add a GRUB password.
- People can boot from Live CD/USB. Solution: Tweak BIOS.
- People can tweak BIOS. Solution: Add BIOS password.
- People can reset BIOS password or remove the HD. Solution: Physically lock the computer.
- People can break the lock.

---

### Post by MikeTheC on 2009-08-17
@ O.P.: Please see this thread: [Physical access is root access](http://ubuntuforums.org/showthread.php?t=989517)

Recurring Discussions in 3, 2, 1...

---

### Post by Ozor Mox on 2009-08-17
Thanks danielrmt, that helps explain the first point.

And whoops, this was a bit of a duplicate, down to almost the thread title!

---

### Post by Post Monkeh on 2009-08-17
there is no way of totally preventing someone from gaining control of your computer, the best we can do is encrypt our data so that at least the only thing people  could gain is a computer, and no information.

---

### Post by GeneralZod on 2009-08-17
> **Ozor Mox said:**
> 
Secondly, there is a thread on the first page at the moment about a Linux kernel exploit that can be used locally to get root access. If local access really *was* root access, why would an exploit like this have such a fuss made over it, and need to be patched so fast? Surely it wouldn't matter, because locking your screen, putting on a BIOS password, etc. is just "slowing them down".


The vulnerability does not require *physical* access to be exploited.  If a webbrowser contained a vulnerability that allowed a website to execute arbitrary code on your machine merely by visiting it (as had happened in the past), an unscrupulous website-owner would be able to use the browser exploit coupled with the kernel exploit to root your machine if you happened to stumble across their site.  Or if an image decoding library contained a vulnerability that enabled a carefully crafted image to execute arbitrary code when an image is decoded, you could be rooted just by opening an e-mail containing such an image. Etc.

Shared webhosts are another case where it needs to be fixed very quickly: many webhosting providers have accounts for several of their customers all on one machine and use UNIX permissions to keep them "private" from one another.  A webhost that gives SSH access and compiler tools - as the one I use does - could be rooted just by SSH'ing in and compiling & running the exploit.

---

### Post by JillSwift on 2009-08-17
Mind that an account can use sudo only if it's a member of the proper security groups.

Security is a many layered thing, and its implementation is a matter of priorities.

Cybercafe computers will tend to focus on security that protects the *OS's integrity*. That means a public account (or several) that are not able to do anything more than what the owner cares to allow. No sudo access (proper groups), no viewing files outside the home directory save for what's needed to run allowed programs (proper file/inode settings), perhaps an ability to mount a USB disk for read/write for downloading along with password secured BIOS to make sure it boots for the next customer.

Now, it gets funnier when you start talking about securing *data*. This is where people start talking about actually taking the machine or hard drive. No matter what you do with the above, physical access to the machine means all the data on it is insecure. To secure it, it has to be encrypted in such a way that noting on that machine can be used by itself to un-encrypt the data. (Like a password or "security dongle", etc.) This will be used as the core of data security, with Linux's access controls (as in the cybercafe) preventing (well, trying to prevent) a remote attempt to get a copy of the encrypted information for off-site attempts to crack it.

Just how well encrypted the data is depends on a number of factors, and can range from "yet another slow-down" to "what do you mean you lost the encryption key?"

So, on top of all that, should there be a flaw in the OS that can be exploited... well, all your attempts to secure a machine pretty much go flying out the window.

That said; There are those who say there really is no such thing as total security. I tend to believe them.

---

### Post by koenn on 2009-08-17
> **JillSwift said:**
> 
That said; There are those who say there really is no such thing as total security. I tend to believe them.
That goes  with what you said earlier: "Security is a many layered thing, and its implementation is a matter of priorities."
The purpose of having layers is
- that one layer acts as a safety net for another layer
- that separate measures complement and reinforce each other

So, when done right, each measure is a step towards 'more secure', but there is no absolute 'completely secured'

---

### Post by juancarlospaco on 2009-08-19
As i said, if i have a rocket launcher, your data is not safe.
:)

---

