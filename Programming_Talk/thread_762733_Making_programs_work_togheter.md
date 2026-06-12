---
title: "Making programs work togheter"
date: 2008-04-22
forum: Programming Talk
---

### Post by vasquez on 2008-04-22
i'm working on a school project and i need some help. The project is a part of a client-server system where a client computer, usually a laptop, runs ubuntu. This client also has a dv cam connected on the firewire port. What i'm tryting to do is capture the dv stream for a couple of minutes in a certain format, save it on the hard-drive, convert it to a flash flv file, upload it to the server via ftp and add all the relevant data of the file to a database for further access. The programs i use is VLC Player for capturing dv stream, ffmpeg for converting to flv, flvtool2 to fix the flv file metadata and some sql and php stuff. i manually do all this stuff in terminal by executing different shell scripts i wrote. My goal is to automate this process without any user interaction. I need suggestion on how to do this. Is there any way to make a program do all this things?

---

### Post by Tuna-Fish on 2008-04-22
Just make a new shell script that runs all your current ones. if there is no user interaction other than running the scripts, it should really be very easy.

---

### Post by themusicwave on 2008-04-22
> **Tuna-Fish said:**
> Just make a new shell script that runs all your current ones. if there is no user interaction other than running the scripts, it should really be very easy.

A shell script seems well suited to the task.

However, you could also write a script in just about any language to call all your other scripts.  Python, Perl or even PHP would work for this I believe.  You just need to make lots of system calls, which is one of the strengths of a scripting language.

Just wanted to mention that note.

---

### Post by vasquez on 2008-04-24
thank you guys i'll start researching right away

---

