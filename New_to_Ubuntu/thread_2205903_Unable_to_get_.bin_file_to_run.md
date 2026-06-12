---
title: "Unable to get .bin file to run"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by chris173 on 2014-02-16
Good Morning to everyone on the board -

I'm a new user to Linux and Ubuntu.  I am running Ubuntu 12.04.4 on a laptop (dual booting with Vista – just did a clean install on the Vista and installed the Ubuntu, yesterday).  I can provide additional details on the machine if needed.

I'm trying to install a bit of freeware on Ubuntu and can't get the .bin file to execute.

Here's the software I'm trying to install:

[http://www.openfta.com/Download.aspx](http://www.openfta.com/Download.aspx)

I've used the Windows version on my XP machine, so I'm comfortable with the source not being malware.

I followed these instructions and moved the file to the Home folder and changed the permissions to allow the file to be executable
[http://howtoubuntu.org/how-to-execute-a-run-or-bin-file-in-ubuntu#.UwDvY9vft0w](http://howtoubuntu.org/how-to-execute-a-run-or-bin-file-in-ubuntu#.UwDvY9vft0w)

Clicking on the file in the Home folder doesn't work.  Nor does trying to run it from the terminal.

In addition, I've checked the forums and come up with different variations  of the same idea (copied/pasted from my terminal screen):

chris@ubuntu:~$ sudo chmod +x OpenFTA.bin 
chris@ubuntu:~$ ./OpenFTA.bin 
bash: ./OpenFTA.bin: /bin/sh^M: bad interpreter: No such file or directory 
chris@ubuntu:~$ chmod +x OpenFTA.bin 
chris@ubuntu:~$ sudo ./OpenFTA.bin 
chris@ubuntu:~$ chmod a+x OpenFTA.bin 
chris@ubuntu:~$ sudo ./OpenFTA.bin 
chris@ubuntu:~$ chmod u+x OpenFTA.bin 
chris@ubuntu:~$ sudo ./OpenFTA.bin 
chris@ubuntu:~$ 
 
All attempts lead to either the bash comment (see above) or simply nothing.  

I have this horrible creeping feeling that there is some subtle thing that I'm missing, but I cannot figure out what it is.

Thankx!

---

### Post by Vladlenin5000 on 2014-02-16
Hi, welcome.

Have you tried ```
sudo sh OpenFTA.bin
```?

If there's an error message you should ask about it at OpenFTA forums.

---

### Post by deadflowr on 2014-02-16
From the horses mouth
> After a successful download there will be a file  called "OpenFTA.bin" in the directory you specified during download.  When you run this file (by opening a shell, changing to the appropriate  direction and typing "./OpenFTA.bin:quot;, the OpenFTA software will be  installed on your machine at a location of your choice. You will have  the chance to cancel this installation at any point.

---

### Post by steeldriver on 2014-02-16
```
bash: ./OpenFTA.bin: /bin/sh[COLOR=#ff0000]**^M**[/COLOR]: bad interpreter: No such file or directory
```

Looks like the file got copied from a Windows machine and still has the Windows-style line terminations (CR-LF instead of plain LF). Either download it again directly into Ubuntu or run the file through a dos2unix converter (either dos2unix itself or tr or sed) e.g.

```
sed -i 's/\r//' OpenFTA.bin
```

---

### Post by chris173 on 2014-02-16
Thanks for the advice on checking the FTA forums.  First thing I hit was a post on 2/11/14 stating that the Linux file is the wrong format and that dos2unix doesn't fix it.

Thanks for the help, everyone!

---

