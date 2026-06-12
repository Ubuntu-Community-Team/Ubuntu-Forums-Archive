---
title: "Unigine heaven on Ubuntu 13.04"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by CaptainJamesjr on 2013-05-13
[SIZE=4]Hello. I'm having a problem with running Ungine Heaven (link here:[/SIZE][http://unigine.com/products/heaven/](http://unigine.com/products/heaven/) [SIZE=4])[/SIZE]   [SIZE=4]On Ubuntu 13.04, I download the version for linux but when i open the file it appears as a .run file, I know this is a really nooby question but if you haven't already guessed I am a SUPER NOOB, so any form of help would be appreciated [/SIZE]:)  -CaptainJamesjr

---

### Post by PowerBarry43 on 2013-05-13
Hi

You just need to run the .run file. Open a terminal and type: (I'm assuming here that you've downloaded the file to your Downloads directory)

```
cd ~/Downloads
chmod 700 Unigine_Heaven-4.0.run
sudo ./Unigine_Heaven-4.0.run
```

Hope this helps!

Barry

---

### Post by CaptainJamesjr on 2013-05-15
[SIZE=4]Hi, I copied the code into terminal it said[/SIZE] [SIZE=2]'Creating directory Unigine_Heaven-4.0[/SIZE][SIZE=2]Verifying archive integrity... All good.[/SIZE]
[SIZE=2]Uncompressing Unigine Heaven Benchmark.............................................................................[/SIZE]
[SIZE=2]Unigine Heaven Benchmark installation is completed. Launch heaven to run it[/SIZE]
[SIZE=3][SIZE=2]james@JamesPC:~/Downloads$ [/SIZE][/SIZE][SIZE=4]But then when I went to open it it opened up in text editor =(
please help and thank you for the code [/SIZE]:) -Captainjamesjr[SIZE=4]
[/SIZE]

---

### Post by PowerBarry43 on 2013-05-16
what happens if you just run

```
heaven
```

from a terminal?

Barry

---

### Post by divxclub on 2013-11-03
> **PowerBarry43 said:**
> what happens if you just run

```
heaven
```

from a terminal?

Barry

having same problem. It looks like when running in terminal just heaven nothing happens:

```
xakep@ubuntu-main:~/Unigine_Heaven-4.0$ heavenheaven: command not found
xakep@ubuntu-main:~/Unigine_Heaven-4.0$ 

```

Now I did tried to go inside folders to see a script that could be run, but I do not see a single .sh file in there. Inside /bin folder I do see heaven_x64 and heaven_x86 ,all files have exacute permissions but again nothing happens.
```
xakep@ubuntu-main:~/Unigine_Heaven-4.0/bin$ heaven_x64heaven_x64: command not found
xakep@ubuntu-main:~/Unigine_Heaven-4.0/bin$
```

Can you please let me know what is going on here. Cause I feel like I missing something that totally idiotic here.

Thank you !

---

### Post by divxclub on 2013-11-03
<-----idiot


./heaven

.....problem solved

---

