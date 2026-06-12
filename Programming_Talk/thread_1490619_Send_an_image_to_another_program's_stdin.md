---
title: "Send an image to another program's stdin"
date: 2010-05-22
forum: Programming Talk
---

### Post by 3Nex on 2010-05-22
So there's this OCR program that reads BMPs beautifully and it says in the man page that it can accept the image through the stdin too, which is just what i need. The problem is I do not know how to do this. I've tried piping it in Bash first, doing something like [FONT=Courier New][COLOR=Navy]./image.bmp | gocr -i -[/COLOR][/FONT] but it says that it "cannot execute the binary file", which I understand why is happening, but what I do not know is what the right way is.

How to achieve this through Bash isn't really that important, because my ultimate aim is to do that from my C program. So, I have this BMP read into my memory (that part is no problem) and now I need to execute the gocr command from my program, giving the BMP image to his stdin and then read his stdout back into my program. All this will be running on Ubuntu.

How would I go about doing this?

---

### Post by MadCow108 on 2010-05-22
use cat, which prints to stdout, and pipe that to stdin of your program:
cat image | program

in a C program use e.g. pipes:
[http://www.opengroup.org/onlinepubs/009695399/functions/pipe.html](http://www.opengroup.org/onlinepubs/009695399/functions/pipe.html)
[http://www.opengroup.org/onlinepubs/009695399/functions/popen.html](http://www.opengroup.org/onlinepubs/009695399/functions/popen.html)

there are also various other possibilities available on most systems:
[http://beej.us/guide/bgipc/output/html/multipage/index.html](http://beej.us/guide/bgipc/output/html/multipage/index.html)

---

### Post by 3Nex on 2010-05-22
> **MadCow108 said:**
> use cat, which prints to stdout, and pipe that to stdin of your program:
cat image | program

This doesn't work. Giving the image name as an argument works, but if I do this, it says:
```
read-PNM-error: file number is  0, position -1
read-PNM-error: bad magic bytes, expect 0x50 0x3[1-6] but got 0x42 0x4d
```

---

### Post by StephenF on 2010-05-22
It wants a PNM file. ImageMagick can convert bmp to this file format. Maybe you forgot a command line switch.

---

### Post by MadCow108 on 2010-05-22
while gocr does take bmp, it does not take them as a stream:
man gocr:
> ... gif, bmp, ps (only single pages) and eps are supported as input files **(not as input stream)**

stdin is an input stream, you'll have to convert it to pnm first in order to use stdin as input.

---

### Post by 3Nex on 2010-05-22
Oh okay, thanks. Never heard of PNM before.. :/

---

### Post by 3Nex on 2010-05-23
Oh, one more thing.. I don't know how to set the arguments for gocr from my C program? Like in Bash, I do [FONT=Courier New][COLOR=DarkRed]gocr -i -[/COLOR][/FONT] and send the image to the stdin.. What's the equivalent of those arguments in C code? I have to set [FONT=Courier New][COLOR=DarkRed]-i[/COLOR][/FONT] and also the next argument has to be the dash for him to know that the image goes to stdin (if it's not dash, then it represents the name of the image file to open)

---

### Post by soltanis on 2010-05-24
I believe the C function you are looking for is popen(3).

Try:
```

man 3 popen

```

If you don't have manpages installed for some reason you should get them now:

```

sudo apt-get install manpages-dev

```

---

### Post by trent.josephsen on 2010-05-24
BTW, don't use cat for simple input redirection.

```

gocr -i - <image_file

```

---

