---
title: "Bash script to find the first file in a directory."
date: 2010-06-10
forum: Programming Talk
---

### Post by tarahmarie on 2010-06-10
Hi!

So, I've noodled my way through several different tasks tonight, and the last piece is this:

How do I find, then delete, the first file in a directory?

I've set up some scripts and tasks to send myself a daily email of part of a large document.  Here's what I want to know.  I split that large document into ~200 text files. I want to find the first document in that directory (1.txt), do some stuff to it, then delete it.  That way, the next day, this same script will find the first document in the directory (2.txt), do some stuff, then delete it, ad infinitum.  The files are numbered 1....10....100, etc, without floating zeroes, so, 100.txt, and so forth.

I've got all of it down besides how to find the first file.  I imagine it has something to do with a recursive 'find' command, but I don't know how to phrase it.  Any ideas?

Thanks!

PS: I'm emailing myself 100 lines of the Iliad every day. It's a nifty idea, if I do say so myself.

---

### Post by lostinxlation on 2010-06-11
Basically, you want to do numerical sort.
 
if the directory contains only  [number].txt files, try this.
```

ls | sort -n | head -1

```

---

### Post by tarahmarie on 2010-06-11
That sorts the files, but it doesn't delete the first one in numeric order. How might I do that?

---

### Post by lostinxlation on 2010-06-11
> **tarahmarie said:**
> That sorts the files, but it doesn't delete the first one in numeric order. How might I do that?
You can put it into a variable and delete it after whatever you did on that file.
 
Or
```

\rm `ls | sort -n | head -1`

```

---

### Post by tarahmarie on 2010-06-11
#!/bin/bash
cd /home/bookparts
cat | sort -n| msmtp -a gmail [email]myemail@gmail.com[/email]
\rm `ls | sort -n | head -1` 

It's the second line of the script that is causing problems. The email is working fine; I'm trying to pass cat a variable for the first file in teh directory. What's wrong here?

---

### Post by blchinezu on 2010-06-11
> **tarahmarie said:**
> #!/bin/bash
cd /home/bookparts
cat | sort -n| msmtp -a gmail [EMAIL="myemail@gmail.com"]myemail@gmail.com[/EMAIL]
\rm `ls | sort -n | head -1` 

cat echoes the content of a file.. you didn't insert any file path
it should be called like this:
cat /path/to/file/filename
i believe that's why it returns an error

also you might have forgotten to write the user.. the path might just be: /home/$USER/bookparts (i suppose it's in your home but not actually in /home as you wouldn't have full permissions)

and i don't get what's with the "\" at the **rm** command :)

---

### Post by tarahmarie on 2010-06-11
Hah!

#!/bin/bash
cd /home/bookparts
FILE=$(ls | sort -n | head -1)
cat $FILE | msmtp -a gmail [email]myemail@gmail.com[/email]
\rm `ls | sort -n | head -1` 

Thanks, guys!

---

### Post by lostinxlation on 2010-06-11
> **blchinezu said:**
> and i don't get what's with the "\" at the **rm** command :)
 
That's just my habit. I set an alias with rm command and make it with -i option, but sometimes don't want to be in interactive mode like whne running it in the script. '\' temporarily unalias and run in non-interactive mode.

---

### Post by blchinezu on 2010-06-11
> **lostinxlation said:**
> That's just my habit. I set an alias with rm command and make it with -i option, but sometimes don't want to be in interactive mode like whne running it in the script. '\' temporarily unalias and run in non-interactive mode.
right... didn't know that. thanks

---

### Post by geirha on 2010-06-11
```
#!/bin/bash
shopt -s nullglob
f=([0-9].txt [0-9][0-9].txt [0-9][0-9][0-9].txt)
msmtp -a gmail myemail@gmail.com < "${f[0]}" && rm -f "${f[0]}"

```

There are several other ways to achieve it without using ls, and you really never should use ls in a script. 

Also, there's no point in the \ in \rm, your script won't have an alias named rm; aliases are disabled by default in non-interactive shells, and aliases are not inherited.

---

### Post by disabledaccount on 2010-06-11
> **geirha said:**
> There are several other ways to achieve it without using ls, and you really **never** should use ls in a script. Could you explain why? Symlinks are not problematic with ls, and with ls you can get additional file informations in several formats -  so I'm curious whats wrong with ls?

about the problem:
**tarahmarie: **It looks like you want to create list of tasks for 100 days ahed.
I think it would be better solution to use "index" file, that contains list of actions  in some consistent format, with one special field wich remembers which action was last processed.

---

### Post by geirha on 2010-06-11
> **tomazzi said:**
> Could you explain why? Symlinks are not problematic with ls, and with ls you can get additional file informations in several formats -  so I'm curious whats wrong with ls?

The output of ls is not meant to be parsed, it's meant to be human-readable

[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

---

### Post by disabledaccount on 2010-06-11
> **geirha said:**
> The output of ls is not meant to be parsed, it's meant to be human-readable
ohh, this is no problem at all:
- you can load line as array, so from bash level you can freely access each word. In particular ls formats file name/attribute will begin allways at the same index in array.
- secondary - you can use sed, that can read filename / attributes starting from any character on the line.

---

### Post by geirha on 2010-06-11
> **tomazzi said:**
> ohh, this is no problem at all:
- you can load line as array, so from bash level you can freely access each word. In particular ls formats file name/attribute will begin allways at the same index in array.
- secondary - you can use sed, that can read filename / attributes starting from any character on the line.

As the url I pointed to earlier says, some metadata can be fairly safely extracted from ls -l output, but you hardly ever need to know those values in a script anyway. And the shell can handle filenames quite safely while ls will mangle them into a single string.

---

