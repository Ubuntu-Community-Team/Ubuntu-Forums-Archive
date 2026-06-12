---
title: "File with no extension challenge task excersize"
date: 2022-09-23
forum: New to Ubuntu
---

### Post by doctorprofessor on 2022-09-23
I'm new and I got this file called "generate_quote" in a virtual box running Ubuntu 19.10. It has no extension. I have to make it work so it "gives me a quote" (a sentence).

I tried: 

./generate-quote -h   --> logs "Could not generate quote..."
sudo bash ./generate-quote --> Cannot execute binary file
file generate-quote --> ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically-linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/LINUX 3.2.0
cat generate-quote --> it's a long gibberish text but I could make out 'private subdirectory is unsafe', '%s extraction of %s (custom Perl interpreter) failed errn=%i)

There's a swapfile in another directory that's mounted as soon as I start the virtual box, I suspected that's related but unmounted it and my file still doesn't work.
Any ideas? 
Thanks

---

### Post by ActionParsnip on 2022-09-23
If its a binary then you don't need bash to run it in the way you tried. Where is the file from? I can't find it online

---

### Post by doctorprofessor on 2022-09-23
it's in a virtual box I feel to bad to share it. Also I forgot if I do cat into the file it's like a long gibberish (unknown characters) but I could mak out this among other things: %s extraction of %s (custom Perl  interpreter) failed errn=%i)

---

### Post by grahammechanical on 2022-09-23
Could this file be a script? Use File Manager to find the file. Select the file and right click it. Select Permissions. The dialog that opens should tell the file type.

Regards

---

### Post by doctorprofessor on 2022-09-23
There's no file manager and no clicking. There's only a ubuntu CLI in the virtual box

---

### Post by ajgreeny on 2022-09-23
You could also open a terminal and use command ```
file /path/to/generate_quote
```
This will give you more information and may tell you of what type the file is, eg,
```
user@Xubuntu-2204:~$ file mp3-convert
mp3-convert: POSIX shell script, ASCII text executable
```

---

### Post by deadflowr on 2022-09-23
Is this for school or something?

---

### Post by doctorprofessor on 2022-09-23
@deadflowr no, it's a task challenge for a job interview. I said the job is probs not for me as I'm not good at this kind of stuff they require but they told me to try anyway. I did all the other tasks, there's just this one broken file left. At this stage I just want to know the answer. I will tell them obv. I got help if I manage to crack it :)

---

### Post by doctorprofessor on 2022-09-23
did this already, also mentioned this in question:
file generate-quote --> ELF 64-bit LSB pie executable, x86-64,  version 1 (SYSV), dynamically-linked, interpreter  /lib64/ld-linux-x86-64.so.2, for GNU/LINUX 3.2.0

---

### Post by Impavidus on 2022-09-24
So you have a program and it's supposed to give you a quote. The program runs, but doesn't give a quote yet. The normal course of action would be to read the manual. Many programs can give some help if you use the -h option (you already tried), or -? or --help. If there's an error message, -v or --verbose often give a more elaborate error message. If that doesn't work, you need reverse engineering, which makes things much harder. Is this for a job as a spy or forensic investigator? Otherwise, such skills shouldn't really be valued.

---

### Post by TheFu on 2022-09-24
> **doctorprofessor said:**
> I'm new and I got this file called "generate_quote" in a virtual box running Ubuntu 19.10. It has no extension. I have to make it work so it "gives me a quote" (a sentence).
...
Any ideas? 
Thanks

Support for 19.10 ended in June/July of 2020 - over 2 yrs ago.  It is a flawed exercise using a non-supported OS release.

I'm unfamiliar with dual architecture (x86-64 and ARM) programs like this seems to be.
I've been a perl developer for 25+ yrs, but haven't ever created a pre-compiled program using it. I've heard that's possible, so if you really want to look into it, that seems the way to head based on the perl mention in the output.

---

### Post by doctorprofessor on 2022-09-24
haha all of those just make it log the same thing, I just tried. "Could not generate quot..." But thanks, appreciate it

---

### Post by Holger_Gehrke on 2022-09-24
You could try running the program through strace, if that's installed in the VM. This should give you a listing of the system calls the program makes and the signals it receives, which could give you an idea what the program is trying to do and why it fails. Of course if strace isn't available in the VM you can't install it since the repositories for 19.10 have gone away ...

Holger

---

### Post by TheFu on 2022-09-24
> **doctorprofessor said:**
> haha all of those just make it log the same thing, I just tried. "Could not generate quot..." But thanks, appreciate it

When you reply, please include a bit of the post you are replying to so we have context.  Otherwise, it is like talking to a crowd of listeners and nobody knows which person you are conversing.

---

### Post by doctorprofessor on 2022-09-25
"You could try running the program through strace"
@Holger_Gehre thanks a lot. That did in fact log a bunch of stuff. Will try to put them here      [https://postimg.cc/gallery/nQTzgb1](https://postimg.cc/gallery/nQTzgb1)

---

### Post by Holger_Gehrke on 2022-09-25
> **doctorprofessor said:**
> "You could try running the program through strace"
@Holger_Gehre thanks a lot. That did in fact log a bunch of stuff. Will try to put them here      [https://postimg.cc/gallery/nQTzgb1](https://postimg.cc/gallery/nQTzgb1)

You really should have sent that output to a file (strace generate_quote > strace.log 2>&1) and posted the contents of that text file. Easier to read than four screenshots from a terminal.

The last thing the program does is an attempt to connect to a web server at 127.0.0.1, which is refused - probably because there is no server running. Before that it's writing tons of files (Perl scripts by the names, .pm / .pl) to /tmp and trying to execute those. I think it's trying to set up a server to request the data from and failing.

Holger

---

