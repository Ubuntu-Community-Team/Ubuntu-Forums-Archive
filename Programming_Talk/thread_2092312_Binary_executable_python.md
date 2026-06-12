---
title: "Binary executable python?"
date: 2012-12-07
forum: Programming Talk
---

### Post by conradin on 2012-12-07
Hi Everyone,
I have a simple python script that I writes files to an ftp server. I want to use the script in conjunction with another application that will run on some other lab computers, but I don't want someone to be able to just read the login information out of the script directly. 
I am thinking if I could just make the script a binary package, then it would deter most people from stumbling upon the login information. 
I see some windows applications that do this function, but haven't found any for Linux yet. Has anyone done this type of conversion? I'd rather not have to recompile in C.

---

### Post by ssam on 2012-12-07
there is no good way to hide a password in an executable. if you rewrote the script in cd and give someone the binary, then the command 'strings' will probably be able to extract the passowrd. or i could take the binary, put it on a computer where i control the network, trick it into logging into a machine i control, and record the password.

a stronger solution might be to accept that anyone can get that password, but configure the FTP server to only allow access from the IP addresses of the lab computers.

---

### Post by conradin on 2012-12-07
> 
a stronger solution might be to accept that anyone can get that password, but configure the FTP server to only allow access from the IP addresses of the lab computers.

I do like that idea, but I still want to try to make a binary, my boss will never accept a pain text script. The current application is compiled in VB6. I want to get right out of that boat. Ive been having some difficulties building example code for libCURL in C. 

Maybe there is a way to make a script executable, but not read/write That could be a solution too, thought I don't know off hand if that would work. or give me funky results.

---

### Post by yanes on 2012-12-07
in any type of binaries , "exe, elf, pyc, ......" you can secure a string data .
any one with simple reversing knowledge can retrieve these data 
you can code a simple function that encrypt your login data and decrypt in runtime (at least data will be visible in RAM only )
but with debuggers they  can retrieve your logins

---

### Post by trent.josephsen on 2012-12-07
> **conradin said:**
> I want to use the script in conjunction with another application that will run on some other lab computers, but I don't want someone to be able to just read the login information out of the script directly.

I'm curious to know why not. If you allow John Q. End-User to run the script, surely it doesn't matter whether he knows the password or not. Unless that password allows access to other data that the script itself doesn't use, which would itself be a security hole.

> I am thinking if I could just make the script a binary package, then it would deter most people from stumbling upon the login information.
The fact that it's in a script to begin with is enough to deter "most people". Putting it in a binary doesn't offer any more security, because if a user knows enough to open a .py script to look for the password, they won't hesitate to open a binary. Using some kind of encryption to obfuscate it might deter some extra people, unless they really wanted it or got bored one afternoon. Bottom line, no method of embedding secret data in a binary is secure; anyone who can run the binary can access the secret data.

Should you persist against my reasoning, there is one method that suggests itself, since you have control over the hardware. Make the script with the login information only readable by root, and create an suid-root script, runnable by ordinary users, to start it. Depending on how it's done I'm not sure this is 100% foolproof so you might want to get input from someone else before proceeding. Obviously, too, it won't protect from the guy who reboots into a live environment or the crook who steals one of the hard drives, but I don't know enough about your particular situation to say whether those are likely threats.

---

### Post by Majorix on 2012-12-07
As mentioned it is easy to read the password even if you put it in a binary, with tools I shouldn't mention here. Best way is to... Well I don't know a way a smart pirate can't figure out from something!

---

### Post by Bachstelze on 2012-12-08
> **trent.josephsen said:**
> Make the script with the login information only readable by root, and create an suid-root script, runnable by ordinary users, to start it.

Most if not all UNIX-like OSes ignore the setuid bit for scripts (for obvious reasons). I would just use scp/sftp with key-based authentication, this avoids the need for passwordsz completely.

---

### Post by lykwydchykyn on 2012-12-08
> **Bachstelze said:**
> Most if not all UNIX-like OSes ignore the setuid bit for scripts (for obvious reasons). I would just use scp/sftp with key-based authentication, this avoids the need for passwordsz completely.

I'd second this, with the only caveat being that if users can copy the key file (usually located in ~/.ssh), they can log in to your server just as easily.

cx_freeze can turn a python script into a binary (sort of), but it's been well established already that this doesn't protect your password.

If security is really important, there's probably a better solution, but devising it would require a better understanding of the whole problem.

---

### Post by trent.josephsen on 2012-12-08
> **Bachstelze said:**
> Most if not all UNIX-like OSes ignore the setuid bit for scripts (for obvious reasons).
Drat, I wondered if that might be the case. OTOH, you could easily make it a binary, since all it needs to do is run one command. Unless I'm overlooking something else?

This thread reminds me of something ESR said about fetchmail... seems he was getting a lot of requests for storing login information encrypted, and his answer was that if another user can read your .fetchmailrc they can log in as you anyway, so encrypting the password would be completely pointless.

---

### Post by lykwydchykyn on 2012-12-08
Without knowing more, here's how I would probably tackle this situation:

 - create an anonymous account on the FTP server chroot'd to an empty directory.
 - hook into the upload action (proftpd and pure-ftpd can do this, not sure about others) to run a script to move the uploaded files to another directory outside the chroot.
 - set up the python script to use  the anonymous FTP.

This way, nobody can FTP in and see what anyone else has uploaded, or mess with uploaded files.  They'll be moved out of the folder as soon as they're uploaded.

And there's no real advantage to anyone uploading anything, since they won't be able to access it again.

If you know the filenames that you're uploading, your script could be set to move known files and simply remove anything else.

Of course, if you haven't this level of control over the server, you could do all this by way of a second FTP server that you do control.

---

