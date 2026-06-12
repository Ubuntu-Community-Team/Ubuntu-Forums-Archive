---
title: "Problem on basic unix command (ls) .... tell me how it internally works ???"
date: 2008-12-18
forum: Programming Talk
---

### Post by umshiva on 2008-12-18
Hi Expert ,


I have a basic problem .... and getting confused

Please check let me know and advice how it internally works  ?


Check this small script 

#! /usr/bin/ksh
touch coostm05.err.20080630
touch coostm05.err.20080701
echo " See this *********** "
     ls -t1
     echo "***************"
     ls -t1 coostm05.err.*
     echo "***************"
exit 0

Output is 

 See this ***********
coostm05.err.20080701
coostm05.err.20080630
batcheck.sh_kp
batcheck.sh
***************
coostm05.err.20080630
coostm05.err.20080701
***************

I use a HP-UX box

Please tell me how it internlly works and is thr any way we can see the program which creates `ls` executable 

Just had a check on linux box  and its not avaibale of /urc/src and its subdir's 

Let me know so i will understand more about the commands working

I dont want any alternatives but plz explain me how this works

Thanks in advance
Shiva
:confused:

---

### Post by Tuna-Fish on 2008-12-18
/bin/ls is found in the package "coreutils"
To fetch the source for it, cd to the directory you want the source to be in, and type "apt-get source coreutils" Note that unlike for other kinds of uses for apt-get, you should NOT use sudo.

---

### Post by stroyan on 2008-12-18
You can find the source for linux ls in the coreutils package using google.com/codesearch .

[http://google.com/codesearch?hl=en&q=lang:c+ls_mode+show:7RJJD9xIY5A:g9S_NaE2TZ0:TomWV1W2f4E&sa=N&cd=4&ct=rc&cs_p=http://ftp.wayne.edu/pub/gnu/coreutils/coreutils-6.5.tar.gz&cs_f=coreutils-6.5/src/ls.c](http://google.com/codesearch?hl=en&q=lang:c+ls_mode+show:7RJJD9xIY5A:g9S_NaE2TZ0:TomWV1W2f4E&sa=N&cd=4&ct=rc&cs_p=http://ftp.wayne.edu/pub/gnu/coreutils/coreutils-6.5.tar.gz&cs_f=coreutils-6.5/src/ls.c)

You can also get the source for ls on ubuntu using "apt-get source coreutils".

You can see the system calls made by a command like ls using the strace utility on linux or the tusc utility on HP-UX.
[http://hpux.connect.org.uk/hppd/cgi-bin/search?package=&term=/tusc](http://hpux.connect.org.uk/hppd/cgi-bin/search?package=&term=/tusc)

---

### Post by umshiva on 2008-12-18
> **Tuna-Fish said:**
> /bin/ls is found in the package "coreutils"
To fetch the source for it, cd to the directory you want the source to be in, and type "apt-get source coreutils" Note that unlike for other kinds of uses for apt-get, you should NOT use sudo.

Can you plz explain me how the script works ... please

---

### Post by umshiva on 2008-12-18
Can anyone of you plz explain me how the script works ... please

---

### Post by mssever on 2008-12-18
> **umshiva said:**
> Can anyone of you plz explain me how the script works ... please
Try some patience. Re-asking your question after only 8 minutes isn't very polite.

I suggest that you read the man page for each command in the script. If I explained it, I'd be merely repeating the man page. There's nothing complicated there. The other reason to read the man pages is because given that you're on HP-UX, there might be subtle differences between your system and Linux systems--which are the ones I know.

If you have any specific questions, please ask. Otherwise, I suggest you read the documentation, which will tell you everything you need to know.

EDIT: It's not possible to know how HP-UX's ls works internally, because the source code is unavailable. It's possible that GNU ls (as found in Linux) is completely different internally. Who knows? Without the source, you can't.

---

### Post by umshiva on 2008-12-18
> **mssever said:**
> Try some patience. Re-asking your question after only 8 minutes isn't very polite.

I suggest that you read the man page for each command in the script. If I explained it, I'd be merely repeating the man page. There's nothing complicated there. The other reason to read the man pages is because given that you're on HP-UX, there might be subtle differences between your system and Linux systems--which are the ones I know.

If you have any specific questions, please ask. Otherwise, I suggest you read the documentation, which will tell you everything you need to know.

EDIT: It's not possible to know how HP-UX's ls works internally, because the source code is unavailable. It's possible that GNU ls (as found in Linux) is completely different internally. Who knows? Without the source, you can't.

Expert ,


I asked  2 questions in my query
1 : abt the script --- its not complicated but just see ls -t1 and ls -t1 < filename > it behaves differently 

2: thanks for ur reply ... 

I asked the first question again did not repeat my second ... i was polite FYI ....

Please help me reagrding this

---

### Post by mssever on 2008-12-18
Are you wondering why the files appear in a different order on different invocations of ls -t? If so, why didn't you say so?

Many *nix (most, probably) systems only have a modification time resolution of 1 second. So given that you're probably touching both files during the same second, the sort has to be by something else, since both files were modified at the exact same time according to available data. Insert a sleep command between the touch commands and you'll probably see the expected behavior.

---

### Post by mssever on 2008-12-18
> **umshiva said:**
> I asked  2 questions in my query
1 : abt the script --- its not complicated but just see ls -t1 and ls -t1 < filename > it behaves differentlyIf you had asked that question, you would have gotten a useful answer faster. I answered the question you asked in posts 4 and 5. You asked someone to explain the script, and you stated nowhere what needed explaining. I didn't notice until later the time discrepency.
> I asked the first question again did not repeat my second ... i was polite FYI ....See posts 4 and 5.

---

### Post by umshiva on 2008-12-19
> **mssever said:**
> Are you wondering why the files appear in a different order on different invocations of ls -t? If so, why didn't you say so?

Many *nix (most, probably) systems only have a modification time resolution of 1 second. So given that you're probably touching both files during the same second, the sort has to be by something else, since both files were modified at the exact same time according to available data. Insert a sleep command between the touch commands and you'll probably see the expected behavior.

Expert,

Thanks for ur suggestion. I tried that option already, and its giving the expected result.

what I wonder is....
does "ls -t" work differently in diff situations???
 1. with a file name 
 2. without any file name.

If u check the o/p.. u can see that
 1. it works as expected without any filename
 2. but when u give a filename its working differently
    and the result is different 

I have modified my script to get my work done.
But understanding how it works helps...

---

### Post by mssever on 2008-12-19
> **umshiva said:**
> what I wonder is....
does "ls -t" work differently in diff situations???
 1. with a file name 
 2. without any file name.
I highly doubt it works differently in different situations. That would just be confusing. But remember that when you use shell globbing (some/file*) that the filenames are expanded by the shell before the command ever gets to see them. And as far as I know, shell wildcard expansions are always done in alphabetical order according to the current locale. If there's a way to affect it, I don't know it.

Presumably, ls only sorts within its arguments, that way, if you specify multiple directories on the command line, they'll be in the order you gave them. This is just a guess; I'd have to read the source to be sure, and I'm too lazy to do that.

---

