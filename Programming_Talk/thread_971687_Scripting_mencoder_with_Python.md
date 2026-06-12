---
title: "Scripting mencoder with Python"
date: 2008-11-05
forum: Programming Talk
---

### Post by mun3kh on 2008-11-05
Hello,

I am having trouble scripting mencoder with Python. It seems that I cannot get it to recognise the -o option
for the output file. When the mencoder subprocess is started, it returns complaining that there is no output file
specified. Below is the code, followed by the output at the terminal. The odd formatting saves scrolling
right-to-left:

[PHP]
#!/usr/bin/python
from subprocess import *
import sys

mencoder_proc = Popen(
   [
    'mencoder',
    'file.mov -oac mp3lame -ovc lavc -lavcopts vcodec=wmv2 -o file.avi'
   ],
   stdout=sys.stdout,
   stderr=sys.stderr
   )

retcode = mencoder_proc.wait()
print "Return code:%s" % retcode

[/PHP]

Here is the terminal output:
[PHP]
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Xeon(R) CPU            3065  @ 2.33GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Exiting... (No output file specified, please see the -o option.)
Return code:1
[/PHP]

Obviously I intend to have string variables in place for a lot of this stuff, but in order to narrow down the source of my woes, I went for sting literals. I have tried simply putting the following on the command line, and it works:

[PHP]
user@ubuntu:~/$ mencoder P7165120.MOV -oac mp3lame -ovc lavc -lavcopts vcodec=wmv2 -o P7165120.avi
[/PHP]

 I don't understand why the -o portion of the mencoder args is not reaching mencoder.

---

### Post by pmasiar on 2008-11-05
I don't have time to look into your code, but suggestion: try optparse: [http://www.python.org/doc/2.5.2/lib/module-optparse.html](http://www.python.org/doc/2.5.2/lib/module-optparse.html)

---

### Post by geirha on 2008-11-05
> **mun3kh said:**
> 
[PHP]
mencoder_proc = Popen(
   [
    'mencoder',
    'file.mov -oac mp3lame -ovc lavc -lavcopts vcodec=wmv2 -o file.avi'
   ],
   stdout=sys.stdout,
   stderr=sys.stderr
   )
[/PHP]


That's the equivalent of running the following in bash:

```

$ mencoder 'file.mov -oac mp3lame -ovc lavc -lavcopts vcodec=wmv2 -o file.avi'
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 47, Stepping: 0)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Exiting... (No output file specified, please see the -o option.)

```
If you want to pass Popen a sequence, each argument must be a seperate element.
E.g.
```

mencoder_proc = Popen(
   [
    'mencoder',
    'file.mov',
    '-oac','mp3lame',
    '-ovc','lavc',
    '-lavcopts','vcodec=wmv2',
    '-o','file.avi',
   ],
   stdout=sys.stdout,
   stderr=sys.stderr
   )

```

---

### Post by mun3kh on 2008-11-07
geirha, you Sir/Madam are a Gem. Thank you so much.

---

