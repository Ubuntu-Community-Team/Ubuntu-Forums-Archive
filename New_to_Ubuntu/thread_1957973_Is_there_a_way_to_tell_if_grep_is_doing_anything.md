---
title: "Is there a way to tell if grep is doing anything?"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by iansane on 2012-04-13
Hi,

I'm running grep to search for a string in my wordpress directory. It seems to just be sitting there not doing anything. I've let it run for an hour and am thinking that is way to long to just read through the website files.

I have it piping to cat to a file and there's nothing in the file but is this just because it hasn't found the string yet?

What's the best way to tell if it's doing anything or just sitting there?

Here's the command I'm running.
```
sudo grep -i -n "contactform" | cat >> contactform.txt
```

Thanks

---

### Post by iponeverything on 2012-04-13
use ps to get the pid of the grep process and attach an strace process to the running grep process.

---

### Post by iansane on 2012-04-13
> **iponeverything said:**
> use ps to get the pid of the grep process and attach an strace process to the running grep process.

Ok, I did this
```
lotus@lotus-laptop:/var/www/vulcan$ ps -C grep
  PID TTY          TIME CMD
 4686 pts/0    00:00:00 grep
```

then this
```
sudo strace -p 4686
```

and get this
```
Process 4686 attached - interrupt to quit
read(0, 
```


What does  this mean?

Thanks

---

### Post by Simian Man on 2012-04-13
You never gave grep a file(s) to do the search on.  When it's not given a file as parameter, grep waits for its input from the keyboard which is why it seems to hang.

Change your command to something like:
```
sudo grep -i -n -r . "contactform" | cat >> contactform.txt
```
To search all files in the directory.

BTW I don't think you need sudo unless the files are not readable except by the owner - which is rare.

---

### Post by lykwydchykyn on 2012-04-13
To watch the progress as it searches, you could also use tee.  The use of cat is also superfluous here.

Try this command:
```

grep -inr "contactform" . |tee contactform.txt

```

---

### Post by iansane on 2012-04-13
> **Simian Man said:**
> You never gave grep a file(s) to do the search on.  When it's not given a file as parameter, grep waits for its input from the keyboard which is why it seems to hang.

Change your command to something like:
```
sudo grep -i -n -r . "contactform" | cat >> contactform.txt
```
To search all files in the directory.

BTW I don't think you need sudo unless the files are not readable except by the owner - which is rare.

I had read on a geeks article it would search all files without the -r but adding the -r makes more sense.

However, I'm still getting the same result after re-attaching strace.

---

### Post by iansane on 2012-04-13
oh, grep is still reading from the terminal input even with the -r in the command.

I just realized what you meant about it waiting for input and typed "hello"
Now the strace shows
```
read(0, "hello\n", 32768)               = 6
```

So, why is grep reading from terminal input?

Thanks

---

### Post by Simian Man on 2012-04-13
Did you remember the "."  That tells it to search all files in the current directory.  If you want only some files, you can list them, but you need to tell it where to search somehow or else it falls back to stdin.

---

### Post by iansane on 2012-04-13
> **Simian Man said:**
> Did you remember the "."  That tells it to search all files in the current directory.  If you want only some files, you can list them, but you need to tell it where to search somehow or else it falls back to stdin.

I thought that was a typo because with the "." it gives me a error.
```
grep: contactform: No such file or directory
```

To clarify, I'm looking for the string "contactform" inside any file, not as the name of a file. This seems like it thinks I'm looking for a file name. Is that what I'm doing here?

Here's the article where I found the command that just uses -i -n and no -r
[http://www.howtogeek.com/howto/ubuntu/find-files-containing-search-terms-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/find-files-containing-search-terms-on-ubuntu/)

---

### Post by lykwydchykyn on 2012-04-13
The search term comes before the directory/file(s) you want to search, as in the command I posted.  SimianMan's command has it backwards.

You're telling grep "search for a dot in 'contactform'", which of course doesn't exist.

---

### Post by iansane on 2012-04-13
> **lykwydchykyn said:**
> The search term comes before the directory/file(s) you want to search, as in the command I posted.  SimianMan's command has it backwards.

You're telling grep "search for a dot in 'contactform'", which of course doesn't exist.

Thanks lykwydchykyn,

I missed your first reply. Yep it's working now.

iponeverything,
Thanks for the ps and strace info.

Simmian Man,
Thanks even if it was backwards :-)

---

### Post by Simian Man on 2012-04-14
> **iansane said:**
> Thanks even if it was backwards :-)

Sorry, I was going off memory.

---

