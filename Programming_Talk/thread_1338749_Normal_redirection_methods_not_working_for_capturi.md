---
title: "Normal redirection methods not working for capturing text"
date: 2009-11-26
forum: Programming Talk
---

### Post by shaggy999 on 2009-11-26
I'm trying to write a script to verify my flac files using the 'flac' command. I have tried several methods of "capturing" the output from the command to a text file and nothing is working. Here's what I've tried so far:

flac -t filename.flac | tee -a output.txt
flac -t filename.flac > output.txt
flac -t filename.flac >> output.txt
flac -c -t filename.flac | tee -a output.txt
flac -c -t filename.flac > output.txt
flac -c -t filename.flac >> output.txt
scriptname | tee -a output.txt
scriptname > output.txt
scriptname >> output.txt

In every single case I get a 0-byte output.txt file. Does anyone know how I can capture the output? This program seems to be doing something different. Here's the normal output of the 'flac' program:

> 
flac 1.2.1, Copyright (C) 2000,2001,2002,2003,2004,2005,2006,2007  Josh Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

01 - Intro.flac: ok                    


---

### Post by MadCow108 on 2009-11-26
maybe it writes to stderr and not to stdout
in this case use:
flac stuff 2> log.txt
2 is stderr, 1 stdout (default)
you can also redirect stderr to stdout and just redirect stdout, useful for example to suppress all output
flac stuff > /dev/null 2>&1

[http://en.wikipedia.org/wiki/Redirection_(computing)#Redirecting_to_and_from_the_standard_file_handles](http://en.wikipedia.org/wiki/Redirection_(computing)#Redirecting_to_and_from_the_standard_file_handles)

---

### Post by snova on 2009-11-26
Perhaps the program is writing to stderr (error output) instead of stdout, so **>** redirection will not work. Try using **2>** instead, which redirects the second stream (and note, not normal output).

If you wanted to redirect both streams, either of the following would be equivalent:

```

flac -t filename.flac >output.txt 2>output.txt
flac -t filename.flac >output.txt 2>&1 # Redirects stderr to stdout, which was already redirected

```

---

### Post by shaggy999 on 2009-11-26
Thanks. This worked for me.

---

