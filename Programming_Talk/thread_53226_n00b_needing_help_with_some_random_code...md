---
title: "n00b needing help with some random code.."
date: 2005-07-30
forum: Programming Talk
---

### Post by Flamekebab on 2005-07-30
I was recently digging through some old files on my Windows PC, old programming files as it happened. I'd downloaded them many years ago from a Necromunda site (the wargame produced by Games Workshop). At the time I'd had no idea what they were, but somehow they never got deleted and I found them today.

Under Windows I could make neither head nor tail of them, however, when I whacked them over onto my Linux laptop, wham, I could see it was code.

Upon googling, I discovered that the site I'd downloaded from still existed, even though it was now *nine* years old..
[Andy Cowell's Necromunda Page](http://www.cowell.org/~andy/min/nec/)

I tried to compile this code using gcc and cc but I got the following error:

```

flamekebab@ubuntuHbBob:~/apps/e$ ls
Makefile  main.c  nec.lex  nec.y  necro.h
flamekebab@ubuntuHbBob:~/apps/e$ gcc Makefile
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
flamekebab@ubuntuHbBob:~/apps/e$

```

Now don't get me confused, I know only *of* programming and about it. I can talk about it, but I can't actually *DO* it, having tried and failed (I find thinking in the manner required to program very difficult). However, I'd appreciate if any kind soul would like to help me in my quest to make this program run!

Best regards,
Benjamin Fox

---

### Post by cwaldbieser on 2005-07-30
Try just typing "make" in the directory.  The Makefile should tell the other tools how to build everything else.  If you are lucky, there won't be any missing libraries and everything will work fine.  If not... is there a README.txt or an INSTALL file with the program?

---

### Post by Flamekebab on 2005-07-30
```

flamekebab@ubuntuHbBob:~/apps/e$ make
bison -d nec.y
make: bison: Command not found
make: *** [nec.tab.c] Error 127
flamekebab@ubuntuHbBob:~/apps/e$ 

```

What's on that page is all you see, the link I posted.

---

### Post by BKonkle on 2005-07-30
Have you already installed the bison package?

---

### Post by Flamekebab on 2005-07-30
I didn't know to, but I have now and then also "flex" which it wanted:

```

flamekebab@ubuntuHbBob:~/apps/e$ make
bison -d nec.y
flex nec.lex
make: flex: Command not found
make: *** [lex.yy.c] Error 127
flamekebab@ubuntuHbBob:~/apps/e$ make
flex nec.lex
gcc -g -o nec lex.yy.c nec.tab.c main.c -lfl
lex.yy.c:19:19: stdio.h: No such file or directory
lex.yy.c:20:20: string.h: No such file or directory
lex.yy.c:21:19: errno.h: No such file or directory
lex.yy.c:22:20: stdlib.h: No such file or directory
lex.yy.c:144: error: syntax error before '*' token
lex.yy.c:144: warning: data definition has no type or storage class
lex.yy.c:182: error: syntax error before "FILE"
lex.yy.c:182: warning: no semicolon at end of struct or union
lex.yy.c:240: error: syntax error before '}' token
lex.yy.c:244: error: syntax error before "yy_buffer_stack_top"
lex.yy.c:244: warning: data definition has no type or storage class
lex.yy.c:245: error: syntax error before "yy_buffer_stack_max"
lex.yy.c:245: warning: data definition has no type or storage class
lex.yy.c:265: error: conflicting declarations of `yy_n_chars'
lex.yy.c:195: error: `yy_n_chars' previously declared here
lex.yy.c:265: warning: `yy_n_chars' was declared `extern' and later `static'
lex.yy.c:278: error: syntax error before '*' token
lex.yy.c:280: error: syntax error before '*' token
lex.yy.c:288: error: syntax error before "FILE"
lex.yy.c:328: error: syntax error before '*' token
lex.yy.c:328: error: `FILE' undeclared here (not in a function)
lex.yy.c:328: error: syntax error before ')' token
lex.yy.c:542:20: unistd.h: No such file or directory
lex.yy.c: In function `yylex':
lex.yy.c:701: error: `stdin' undeclared (first use in this function)
lex.yy.c:701: error: (Each undeclared identifier is reported only once
lex.yy.c:701: error: for each function it appears in.)
lex.yy.c:704: error: `stdout' undeclared (first use in this function)
lex.yy.c:706: error: `NULL' undeclared (first use in this function)
lex.yy.c:757: error: `size_t' undeclared (first use in this function)
lex.yy.c:880: error: dereferencing pointer to incomplete type
lex.yy.c:891: error: dereferencing pointer to incomplete type
lex.yy.c:892: error: dereferencing pointer to incomplete type
lex.yy.c:893: error: dereferencing pointer to incomplete type
lex.yy.c:903: error: dereferencing pointer to incomplete type
lex.yy.c:982: error: dereferencing pointer to incomplete type
lex.yy.c: In function `yy_get_next_buffer':
lex.yy.c:1009: error: dereferencing pointer to incomplete type
lex.yy.c:1014: error: dereferencing pointer to incomplete type
lex.yy.c:1018: error: dereferencing pointer to incomplete type
lex.yy.c:1045: error: dereferencing pointer to incomplete type
lex.yy.c:1049: error: dereferencing pointer to incomplete type
lex.yy.c:1053: error: `size_t' undeclared (first use in this function)
lex.yy.c:1053: error: syntax error before "num_to_read"
lex.yy.c:1056: error: `num_to_read' undeclared (first use in this function)
lex.yy.c:1060: error: `NULL' undeclared (first use in this function)
lex.yy.c:1063: error: dereferencing pointer to incomplete type
lex.yy.c:1065: error: dereferencing pointer to incomplete type
lex.yy.c:1067: error: dereferencing pointer to incomplete type
lex.yy.c:1070: error: dereferencing pointer to incomplete type
lex.yy.c:1070: error: dereferencing pointer to incomplete type
lex.yy.c:1072: error: dereferencing pointer to incomplete type
lex.yy.c:1074: error: dereferencing pointer to incomplete type
lex.yy.c:1076: error: dereferencing pointer to incomplete type
lex.yy.c:1076: error: dereferencing pointer to incomplete type
lex.yy.c:1080: error: dereferencing pointer to incomplete type
lex.yy.c:1082: error: dereferencing pointer to incomplete type
lex.yy.c:1086: error: dereferencing pointer to incomplete type
lex.yy.c:1088: error: dereferencing pointer to incomplete type
lex.yy.c:1097: error: dereferencing pointer to incomplete type
lex.yy.c:1097: error: syntax error before "n"
lex.yy.c:1097: error: `n' undeclared (first use in this function)
lex.yy.c:1097: error: `EOF' undeclared (first use in this function)
lex.yy.c:1097: error: dereferencing pointer to incomplete type
lex.yy.c:1097: error: dereferencing pointer to incomplete type
lex.yy.c:1097: error: `errno' undeclared (first use in this function)
lex.yy.c:1097: error: dereferencing pointer to incomplete type
lex.yy.c:1097: error: `EINTR' undeclared (first use in this function)
lex.yy.c:1100: error: dereferencing pointer to incomplete type
lex.yy.c:1114: error: dereferencing pointer to incomplete type
lex.yy.c:1123: error: dereferencing pointer to incomplete type
lex.yy.c:1124: error: dereferencing pointer to incomplete type
lex.yy.c:1126: error: dereferencing pointer to incomplete type
lex.yy.c: In function `yyunput':
lex.yy.c:1197: error: dereferencing pointer to incomplete type
lex.yy.c:1201: error: dereferencing pointer to incomplete type
lex.yy.c:1202: error: dereferencing pointer to incomplete type
lex.yy.c:1204: error: dereferencing pointer to incomplete type
lex.yy.c:1206: error: dereferencing pointer to incomplete type
lex.yy.c:1211: error: dereferencing pointer to incomplete type
lex.yy.c:1212: error: dereferencing pointer to incomplete type
lex.yy.c:1214: error: dereferencing pointer to incomplete type
lex.yy.c: In function `input':
lex.yy.c:1243: error: dereferencing pointer to incomplete type
lex.yy.c:1273: error: `EOF' undeclared (first use in this function)
lex.yy.c: At top level:
lex.yy.c:1304: error: syntax error before '*' token
lex.yy.c: In function `yyrestart':
lex.yy.c:1307: error: `NULL' undeclared (first use in this function)
lex.yy.c:1313: error: `input_file' undeclared (first use in this function)
lex.yy.c: In function `yy_switch_to_buffer':
lex.yy.c:1330: error: `NULL' undeclared (first use in this function)
lex.yy.c:1337: error: dereferencing pointer to incomplete type
lex.yy.c:1338: error: dereferencing pointer to incomplete type
lex.yy.c: In function `yy_load_buffer_state':
lex.yy.c:1354: error: dereferencing pointer to incomplete type
lex.yy.c:1355: error: dereferencing pointer to incomplete type
lex.yy.c:1356: error: dereferencing pointer to incomplete type
lex.yy.c: At top level:
lex.yy.c:1366: error: syntax error before '*' token
lex.yy.c: In function `yy_create_buffer':
lex.yy.c:1370: error: invalid application of `sizeof' to an incomplete type
lex.yy.c:1374: error: dereferencing pointer to incomplete type
lex.yy.c:1374: error: `size' undeclared (first use in this function)
lex.yy.c:1379: error: dereferencing pointer to incomplete type
lex.yy.c:1379: error: dereferencing pointer to incomplete type
lex.yy.c:1380: error: dereferencing pointer to incomplete type
lex.yy.c:1383: error: dereferencing pointer to incomplete type
lex.yy.c:1385: error: `file' undeclared (first use in this function)
lex.yy.c: In function `yy_delete_buffer':
lex.yy.c:1400: error: `NULL' undeclared (first use in this function)
lex.yy.c:1403: error: dereferencing pointer to incomplete type
lex.yy.c:1404: error: dereferencing pointer to incomplete type
lex.yy.c: At top level:
lex.yy.c:1417: error: syntax error before "FILE"
lex.yy.c: In function `yy_init_buffer':
lex.yy.c:1420: error: `errno' undeclared (first use in this function)
lex.yy.c:1422: error: `b' undeclared (first use in this function)
lex.yy.c:1424: error: `file' undeclared (first use in this function)
lex.yy.c:1431: error: `NULL' undeclared (first use in this function)
lex.yy.c: In function `yy_flush_buffer':
lex.yy.c:1450: error: dereferencing pointer to incomplete type
lex.yy.c:1456: error: dereferencing pointer to incomplete type
lex.yy.c:1457: error: dereferencing pointer to incomplete type
lex.yy.c:1459: error: dereferencing pointer to incomplete type
lex.yy.c:1459: error: dereferencing pointer to incomplete type
lex.yy.c:1461: error: dereferencing pointer to incomplete type
lex.yy.c:1462: error: dereferencing pointer to incomplete type
lex.yy.c:1464: error: `NULL' undeclared (first use in this function)
lex.yy.c: In function `yypush_buffer_state':
lex.yy.c:1476: error: `NULL' undeclared (first use in this function)
lex.yy.c:1486: error: dereferencing pointer to incomplete type
lex.yy.c:1487: error: dereferencing pointer to incomplete type
lex.yy.c: In function `yypop_buffer_state':
lex.yy.c:1506: error: `NULL' undeclared (first use in this function)
lex.yy.c: In function `yy_scan_buffer':
lex.yy.c:1578: error: invalid application of `sizeof' to an incomplete type
lex.yy.c:1582: error: dereferencing pointer to incomplete type
lex.yy.c:1583: error: dereferencing pointer to incomplete type
lex.yy.c:1583: error: dereferencing pointer to incomplete type
lex.yy.c:1584: error: dereferencing pointer to incomplete type
lex.yy.c:1585: error: dereferencing pointer to incomplete type
lex.yy.c:1586: error: dereferencing pointer to incomplete type
lex.yy.c:1586: error: dereferencing pointer to incomplete type
lex.yy.c:1587: error: dereferencing pointer to incomplete type
lex.yy.c:1588: error: dereferencing pointer to incomplete type
lex.yy.c:1589: error: dereferencing pointer to incomplete type
lex.yy.c:1590: error: dereferencing pointer to incomplete type
lex.yy.c: In function `yy_scan_bytes':
lex.yy.c:1643: error: dereferencing pointer to incomplete type
lex.yy.c: In function `yy_fatal_error':
lex.yy.c:1654: error: `stderr' undeclared (first use in this function)
lex.yy.c: At top level:
lex.yy.c:1689: error: syntax error before '*' token
lex.yy.c:1697: error: syntax error before '*' token
lex.yy.c:1735: error: syntax error before '*' token
lex.yy.c: In function `yyset_in':
lex.yy.c:1737: error: `in_str' undeclared (first use in this function)
lex.yy.c: At top level:
lex.yy.c:1740: error: syntax error before '*' token
lex.yy.c: In function `yyset_out':
lex.yy.c:1742: error: `out_str' undeclared (first use in this function)
lex.yy.c: In function `yylex_destroy':
lex.yy.c:1760: error: `NULL' undeclared (first use in this function)
nec.y:3:19: stdio.h: No such file or directory
nec.y:4:20: stdlib.h: No such file or directory
nec.y:6:20: string.h: No such file or directory
nec.y: In function `yyparse':
nec.y:81: error: `NULL' undeclared (first use in this function)
nec.y:81: error: (Each undeclared identifier is reported only once
nec.y:81: error: for each function it appears in.)
main.c:1:19: stdio.h: No such file or directory
main.c:2:20: stdlib.h: No such file or directory
main.c:4:20: string.h: No such file or directory
main.c: In function `build_html':
main.c:94: error: `NULL' undeclared (first use in this function)
main.c:94: error: (Each undeclared identifier is reported only once
main.c:94: error: for each function it appears in.)
main.c:94: warning: assignment makes pointer from integer without a cast
main.c:105: warning: assignment makes pointer from integer without a cast
main.c: In function `do_stats':
main.c:178: error: `NULL' undeclared (first use in this function)
make: *** [nec] Error 1
flamekebab@ubuntuHbBob:~/apps/e$


```

*yelps*
Help?

---

### Post by BKonkle on 2005-07-30
Holy crap, you've just launched far beyong my paltry knowledge of compiling!

I can tell you that when compiling Wine from source (which may be relevant because I'm assuming this game you are compiling for is also for Windows?), it requires that you have all of these packages installed:

```
apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
```

That includes bison and a package called flex-old. . . maybe the rest of the packages are useful too?  It couldn't hurt to try, if you've got plenty of space to store packages you might not actually need. . .

---

### Post by Flamekebab on 2005-07-30
It's not a game. It's sort of an application to deal with gang statistics.

(If you didn't know, Games Workshop make, primarily, table-top wargames)

I'm not certain what this program does, I'm trying to find out..

---

### Post by cwaldbieser on 2005-07-30
It compiled just fine, for me.  It looks like you don't have the standard C library header files in your path?  That should have been taken care of when you installed gcc.

Anyway, I can zip up the binary and email it to you or something if you can't get it working.

It looks like the author wrote a program that processes Necromunda gang data (I never played it, but it was similar to Gorkamorka?).

He made the resulting program (which the docs call "sumper", but the makefile names "nec") read data from standard input.  The program can be run with command line option "-s" to spit out the stats for the gang, or "-h" to generate a full blown web page.

He wrote the front end using flex and bison (which are the GNU equivalents of Lex and YACC) so that the data you feed the program is actually a formal language used for describing Necromunda gangs.  You could take this language and incorporate it into your own programs so users could "program" their own gangs.

Does that make sense?

---

### Post by Flamekebab on 2005-07-31
You played Gorkamorka?

If so, finally! I'm not alone! I played it and loved it, but no one ever seems to play it any more.

Necromunda however is still very much alive and people play it regularly. New models and rule additions are being added too.

I'm curious whether you can make some sense of what it does with gang data, what needs to be input, etc.

I apologise for my lack of programming knowledge, I suck, I know, but I'm extremely grateful for any help!

---

### Post by cwaldbieser on 2005-07-31
[QUOTE=Flamekebab]I apologise for my lack of programming knowledge, I suck, I know, but I'm extremely grateful for any help![/QUOTE]
No need to apologize for that!  I don't know how to refine oil, but I still enjoy driving a car.

If you look at the file, "militia.txt", that is the format of the data that the program will accept.

It looks like lines that start with a "#" are comments.  Most lines appear to start with some sort of statement or command: Name, Rating, Territory, Stash, Hoard, Member.  Arguments to these commands are numbers, text and lists.  The text looks like it must be quoted with double quotes if it contains a space.  The lists are preceeded by equal signs, are enclosed in parentheses, and are comma seperated.  Some commands seems to take multiple arguments that are seperated by spaces.

The easiest way to see what is allowed is to just try it.  If the program can't understand what you've typed because it doesn't conform to the structure of the language, it will tell you there is a syntax error, and hopefully give you some additional diagnostic to explain what is wrong.

Does that help?

I guess I didn't mention (because he gives this example on his site), but a simple example of running it would be:

```
$ cat militia.txt | ./nec -s
We have 1 gangs.
The Mushy Gun Milita:1268    

We have 10 members.
el Feygun (The Mushy Gun Milita):	66
Sumo (The Mushy Gun Milita):	64
Tyco (The Mushy Gun Milita):	60
Joey the Slug (The Mushy Gun Milita):	23
Sawtooth (The Mushy Gun Milita):	22
Full Otto (The Mushy Gun Milita):	21
Plasmo (The Mushy Gun Milita):	21
Toothpick (The Mushy Gun Milita):	21
Louie the Punk (The Mushy Gun Milita):	0
Wispy (The Mushy Gun Milita):	0

$ cat militia.txt | ./nec -h > out.html
```
The last bit produces a file called out.html that can be viewed in a web browser.  It creates a nice display of the gang(s).

---

### Post by Flamekebab on 2005-08-01
That helps a lot, I feel silly I didn't ask years ago!

Could anyone who successfully managed to get it to compile give me the binaries?

Is it possible to have it installed as a command on my system, like, through a .deb file so I could just type

```
cat militia.xtx | sumper -h output.html
``` 

For example?
(I'm more curious whether it could be installed than determined to make it so.)

---

### Post by cwaldbieser on 2005-08-01
Just create a ~/bin directory and put the executable in there.  Then modify your .bashrc file so that it has the line

```
export PATH=$PATH:/home/your-username/bin
```

Any executable you add to that directory will then be in your command search path.

The executable is attached as a "nec.tar.bz2" (tar'd and bzip2'd).

---

### Post by Flamekebab on 2005-08-01
Well the program works, which is awesome, however I do have a query.

So far I've only managed to get it to run by typing the following:

```
cat militia.txt | ./nec -h out.html
``` 

But when I type that, the output is not in a file. It just spits out the code to the console, from where I can copy and paste it.

Should it be spawning a separate file?

---

### Post by cwaldbieser on 2005-08-01
[QUOTE=Flamekebab]Well the program works, which is awesome, however I do have a query.

So far I've only managed to get it to run by typing the following:

```
cat militia.txt | ./nec -h out.html
``` 

But when I type that, the output is not in a file. It just spits out the code to the console, from where I can copy and paste it.

Should it be spawning a separate file?[/QUOTE]

No, it seems to be more in line with standard UNIX programs that read from standard input and write to standard output.  Basically, you are supposed to use redirection and/or pipes.  For example:

```
$ cat militia.txt | ./nec -h > out.html 
``` 

You need to include the ">".

---

### Post by Flamekebab on 2005-08-01
Ah yes, that worked.

I can't say I'm very familiar with things like pipes. I'm working on it, but until recently I was a complete Linux n00b, now I think I know some things, but unlike Windows, there's far more normal users can learn and benefit greatly from, even if it's not strictly necessary.

Hmm, would it be possible to make some sort of script that would run and request an input file name, which option to use and then ask for an output file if required?

Would that require programming instead, as opposed to just scripting?

---

### Post by Stuka on 2005-08-02
[QUOTE=Flamekebab]Ah yes, that worked.

I can't say I'm very familiar with things like pipes. I'm working on it, but until recently I was a complete Linux n00b, now I think I know some things, but unlike Windows, there's far more normal users can learn and benefit greatly from, even if it's not strictly necessary.

Hmm, would it be possible to make some sort of script that would run and request an input file name, which option to use and then ask for an output file if required?

Would that require programming instead, as opposed to just scripting?[/QUOTE]
 Nah, that wouldn't need any programming - a bash script wouldn't be too hard to toss together for that. Personally I wouldn't, but then I don't see any reason to make it TOO easy for people anyway (I know, I'm an elitist snob-geek).

---

### Post by cwaldbieser on 2005-08-02
[QUOTE=Flamekebab]
Would that require programming instead, as opposed to just scripting?[/QUOTE]

The difference between "programming" and "scripting" is somewhat of a grey area.  Essentially, scripting is programming.

It should actually be pretty easy to make the front end you describe with a shell script.  With a fairly modest python script, you could even have a simple Tk GUI front end.

---

