---
title: "[SOLVED] How to capture the output of the 'make' command?"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by mingle on 2008-07-20
Hi,

I'm trying to compile a drive on my Ubuntu box and I'm getting a lot of errors from the "make" command.

I'm trying to capture the full output, but there are so many errors that the terminal buffer is filling up and I'm missing out on half of the errors.

Is it possible to log the output of the "make" command to a file, so I can review it?

Cheers,

Mike.

---

### Post by mevets on 2008-07-20
```

make install > output.txt

```
'>' Is usful for all commands that generate lots of output.

---

### Post by logos34 on 2008-07-20
redirect ('>')

$ [B]make > file.txt
[/B]
Or use **script** to save the entire shell session to 'file':

$ **script** file

---

### Post by mingle on 2008-07-20
Hi,

Thanks for the reply...

It sort of worked, but it only captured the first 20 or so lines.

When I issue the "make" command, I see the lines that were captured in the output.txt file, but there are 100's more that are in the file, but that I see on-screen...

Any ideas?

Cheers,

Mike.

---

### Post by mingle on 2008-07-20
Hi,

... or alternatively: how do I pause the output to the terminal window?

(using Gnome Terminal 2.22.1)

Cheers,

Mike.

---

### Post by michael_1234 on 2008-07-20
> **mingle said:**
> 
Is it possible to log the output of the "make" command to a file, so I can review it?


If some of the output is going to stdout (standard output), and some is going to stderr (error messages), then you would want to redirect both of these to the output file. Using just "make > outfile.txt" will just redirect stdout to the file.

Try the following:

$ make > output.txt 2>&1

Here, order is imporant; this (a) redirects stdout (>) to output.txt, THEN (b) sends stderr (2>) to whatever stdout (&1) currently is set to (which happens to be the file, output.txt). 

(Note that : "cmd > output" is the same as "cmd 1> output", meaning redirect stdout -- file descripter "1" -- to a file)


If you want to *see* the output AND redirect it to a file, use "tee":

$  make 2>&1 | tee  output.txt

Likewise, this sends stderr (2>) to stdout (&1), then creates a "tee" that sends stdout to both the terminal AND the output file.

-michael

---

### Post by michael_1234 on 2008-07-20
...redirect to a file AND the screen, paging one page at a time (use "return" for line-by-line, or space bar for a page)

$ make 2>&1 | tee output.txt | more


...you can also use "less" instead of "more".

-m

---

### Post by mingle on 2008-07-20
Hi,

Thanks everyone, particularly Michael - worked fine!

Cheers,

Mike.

---

