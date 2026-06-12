---
title: "How to know if there is standar input in bash?"
date: 2008-03-06
forum: Programming Talk
---

### Post by Yuzem on 2008-03-06
I want to read from a pipe.
Something like this:

```
if [[ standar_input_exist ]]; then
	while read -r line ; do
		echo $line
	done
fi
```

Any ideas?

---

### Post by ghostdog74 on 2008-03-06
can you describe what you actually wanted to do overall?

---

### Post by slavik on 2008-03-06
there is always standard input :)

---

### Post by jpkotta on 2008-03-07
Like this?

```

mkfifo pipe
while :; do
    cat pipe
done
```


Meanwhile...
```

ls > pipe

```

---

### Post by Yuzem on 2008-03-07
Sorry for the delay...
> **ghostdog74 said:**
> can you describe what you actually wanted to do overall?
Yes, I want to make a script in bash that will do something if there is standard input coming from a pipe and something else if there isn't.

I mean, to make it act as many other system command, for example grep.
grep reads from standard input only if there is any.

My solution:
```
	while read -r line ; do
		echo $line
	done
```
will always read form the standard input and the problem is that if there isn't any it will ask for user input.

> **slavik said:**
> there is always standard input :)
How is that?
> **jpkotta said:**
> Like this?

```

mkfifo pipe
while :; do
    cat pipe
done
```


Meanwhile...
```

ls > pipe

```
mmm... I think this is not what I want.

---

### Post by slavik on 2008-03-07
grep reads from standard input, when nobody writes to it, grep receives an EOF (Enf Of File) when it tries to read. By STDIN always existing, I mean that it is always open (although not necessarily pointing to where you might think).

grep also looks for a file specification and if it's not there, then it reads from STDIN. tar for example forces the specification of -f (file to input/output from/to) and if you set it to -, it means STDIN/STDOUT.

---

### Post by Yuzem on 2008-03-07
Oh... ok, now I understand.
I thought that if no file was specified and there was no standard input grep will not ask the user for input but it does, just like in the script.
Thanks.

---

### Post by ghostdog74 on 2008-03-07
what i am asking is, what is the problem you are trying to solve, ultimately.?

---

### Post by Yuzem on 2008-03-08
If there is not stdin and no file is specified the script will ask for user input. That was the problem because it is an unwanted behavior.

I would prefer in that situation to return an error message saying that a file must be specified. 

I assumed that this weren't happening in others commands like grep and I wanted my script to work like them but my assumption was wrong...

It isn't really a problem, I just assumed that there was a better way to do it.

---

### Post by ghostdog74 on 2008-03-08
```

#!/bin/bash
if [ $# -eq 0 ]
then
   # process stdin
    while read -r line
    do
        echo $line
    done
else
    echo "processing arguments"    .
fi 

```

---

### Post by Yuzem on 2008-03-08
The problem remains, if there is no stdin it will ask for user input. No error message... and I need arguments while processing from the stdin.
Thanks anyways. :)

I will grab all the arguments first and then if a specific argument is missing it will read from stdin just like grep.

---

### Post by Mr. C. on 2008-03-09
Yuzem,

I think you are misunderstanding something, or at least being ambiguous in your language "if there is no stdin".  By this do you mean, STDIN comes from a PIPE or redirection, or do you mean that PIPE or redirection is empty, or do you mean STDIN is closed and unavailable?

Unless specifically closed, programs start with STDIN connected and available.  The shell reconnects the plumbing when you create a command sequence with a pipeline or redirection.

If your shell (or any) program is going to read from STDIN, it has apriori made the assumption that there is something to be read.  The problem is that your program doesn't know how long to wait before it accepts that nothing is flowing or will flow, so it blocks (forever, unless programmed to interrupt with a timeout).  So attempting to read to see if the shell or other program re-plumbed STDIN is not the correct approach.

There are techniques you can use if you want to see if STDIN comes from a TTY or from a pipe.

But the standard approach is to assume file name arguments as input sources, and in their absence STDIN is used.

---

### Post by Yuzem on 2008-03-09
> **Mr. C. said:**
> Yuzem,

I think you are misunderstanding something, or at least being ambiguous in your language "if there is no stdin".  By this do you mean, STDIN comes from a PIPE or redirection, or do you mean that PIPE or redirection is empty, or do you mean STDIN is closed and unavailable?
Yes, by no stdin I mean STDIN comming from a pipe. I guess I was being ambiguous. My English  is not very good and I am not a programmer.

> **Mr. C. said:**
> There are techniques you can use if you want to see if STDIN comes from a TTY or from a pipe.

But the standard approach is to assume file name arguments as input sources, and in their absence STDIN is used.
I will do that, thanks.

---

