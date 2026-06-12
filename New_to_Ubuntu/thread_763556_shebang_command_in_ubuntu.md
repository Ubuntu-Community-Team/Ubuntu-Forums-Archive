---
title: "shebang command in ubuntu"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by viswanathan on 2008-04-23
well i just started  learning Perl every time i use this command #!/usr/bin/perl -w nd proceed forward bash wld state as follows 

ani@ani-desktop:~$ #!/usr/bin/perl -w
ani@ani-desktop:~$ print ("hello world\n");
bash: syntax error near unexpected token `"hello world\n"'
ani@ani-desktop:~$ print("hello world\n");
bash: syntax error near unexpected token `"hello world\n"'
ani@ani-desktop:~$ 

any info wld be of g8 help :lolflag:

cheers

---

### Post by sdennie on 2008-04-23
You can only use #! in a script.  So, a script like this would work:

```

#!/usr/bin/perl

print "Hello World\n";

```

Or, from the command line:

```

perl -e 'print "Hello World\n"'

```

---

### Post by viswanathan on 2008-04-23
tnx dude

---

### Post by viswanathan on 2008-04-23
dude its of no use what ever i need to call m perl to execute the file s.pl wait a min i read in the book programing perl by larry wall he staes that u can run directly plz correct me if im mistaken  

ani@ani-desktop:~$ s.pl
bash: s.pl: command not found
ani@ani-desktop:~$ vim s.pl
ani@ani-desktop:~$ s
bash: s: command not found
ani@ani-desktop:~$ s.pl
bash: s.pl: command not found
ani@ani-desktop:~$ s.pl
bash: s.pl: command not found
ani@ani-desktop:~$ perl s.pl
hello world
ani@ani-desktop:~$ ./s
bash: ./s: No such file or directory
ani@ani-desktop:~$ /.s
bash: /.s: No such file or directory
ani@ani-desktop:~$ ./s.pl
bash: ./s.pl: Permission denied
ani@ani-desktop:~$ 

[B]How to Do It
Gee, right about now you're probably wondering how to run a Perl program. The short answer is that
you feed it to the Perl language interpreter program, which coincidentally happens to be named perl
(note the case distinction). The longer answer starts out like this: There's More Than One Way To Do
It.[13]
        [13] That's the Perl Slogan, and you'll get tired of hearing it, unless you're the Local
        Expert, in which case you'll get tired of saying it. Sometimes it's shortened to
        TMTOWTDI, pronounced "tim-toady". But you can pronounce it however you like.
        After all, TMTOWTDI.
The first way to invoke perl (and the way most likely to work on any operating system) is to simply
call perl explicitly from the command line. If you are on a version of UNIX and you are doing
something fairly simple, you can use the -e switch (% in the following example represents a standard
shell prompt, so don't type it):
% perl -e 'print "Hello, world!\n";'
On other operating systems, you may have to fiddle with the quotes some. But the basic principle is
the same: you're trying to cram everything Perl needs to know into 80 columns or so.[14]
        [14] These types of scripts are often referred to as "one-liners". If you ever end up
        hanging out with other Perl programmers, you'll find that some of us are quite fond of
        creating intricate one-liners. Perl has occasionally been maligned as a write-only
        language because of these shenanigans.
For longer scripts, you can use your favorite text editor (or any other text editor) to put all your
commands into a file and then, presuming you named the script gradation (not to be confused with
graduation), you'd say:
% perl gradation
You're still invoking the Perl interpreter explicitly, but at least you don't have to put everything on the
command line every time. And you don't have to fiddle with quotes to keep the shell happy.
The most convenient way to invoke a script is just to name it directly (or click on it), and let the
operating system find the interpreter for you. On some systems, there may be ways of associating
various file extensions or directories with a particular application. On those systems, you should do
whatever it is you do to associate the Perl script with the Perl interpreter. On UNIX systems that
support the #! "shebang" notation (and most UNIX systems do, nowadays), you can make the first
line of your script be magical, so the operating system will know which program to run. Put a line
resembling[15] line 1 of our example into your program:
       [15] If perl isn't in /usr/bin, you'll have to change the #! line accordingly.
#!/usr/bin/perl
Then all you have to say is
% gradation
Of course, this didn't work because you forgot to make sure the script was executable (see the
manpage for chmod (1))[16] and in your PATH. If it isn't in your PATH, you'll have to provide a
complete filename so that the operating system knows how to find your script. Something like
       [16] Although Perl has its share of funny notations, this one must be blamed on UNIX.
       chmod (1) means you should refer to the manpage for the chmod command in section one
       of your UNIX manual. If you type either man 1 chmod or man -s 1 chmod
       (depending on your flavor of UNIX), you should be able to find out all the interesting
       information your system knows about the command chmod. (Of course, if your flavor of
       UNIX happens to be "Not UNIX!" then you'll need to refer to your system's
       documentation for the equivalent command, presuming you are so blessed. Your chief
       consolation is that, if an equivalent command does exist, it will have a much better name
       than chmod.)
% ../bin/gradation
Finally, if you are unfortunate enough to be on an ancient UNIX system that doesn't support the magic
#! line, or if the path to your interpreter is longer than 32 characters (a built-in limit on many
systems), you may be able to work around it like this:
#!/bin/sh -- # perl, to stop looping
eval 'exec /usr/bin/perl -S $0 ${1+"$@"}'
       if 0;
Some operating systems may require variants on this to deal with /bin/csh, DCL, COMMAND.COM,
or whatever happens to be your default command interpreter. Ask your Local Expert.
Throughout this book, we'll just use #!/usr/bin/perl to represent all these notions and
notations, but you'll know what we really mean by it.
A random clue: when you write a test script, don't call your script test. UNIX systems have a built-in
test command, which will likely be executed instead of your script. Try try instead.
A not-so-random clue: while learning Perl, and even after you think you know what you're doing, we
suggest using the -w option, especially during development. This option will turn on all sorts of useful
and interesting warning messages, not necessarily in that order. You can put the -w switch on the
shebang line, like this:
#!/usr/bin/perl -w
Now that you know how to run your own Perl program (not to be confused with the perl program),
let's get back to our example.

[/B]

dude this is the exact wrintg frm the book

---

### Post by hyper_ch on 2008-04-23
```

./s.pl

```

and it must be executable by your user

---

### Post by sdennie on 2008-04-23
You will need to run:

```

chmod +x s.pl
./s.pl

```

Or

```

perl s.pl

```

---

### Post by erginemr on 2008-04-23
Or
```
perl ./s.pl
```
but if you want to run it directly without writing "perl", you need to first make the file executable:
```
chmod u+x s.pl
```

---

### Post by viswanathan on 2008-04-23
tnx dudes nd 1 mre questn what is this chmod command i meant what was its functon i referd man chmod all i got was it was sme kind of permission changing command

---

### Post by erginemr on 2008-04-23
Hmm, for file permissions please refer to:
*[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)*

---

