---
title: "Bash to perl program conversion"
date: 2013-10-01
forum: Programming Talk
---

### Post by learnbash on 2013-10-01
I have below code, can someone please advise me how i can convert below bash script code in perl.

```



export ORACLE_BASE=/home/oracle1

lsnrctl start lndb1
sqlplus '/ as sysdba' 
startup;

```

---

### Post by TheFu on 2013-10-01
Learn perl, use cpan modules. avoid system and the `cmd` constructs.

In the old days there was a sh2p program ... can't find it now ... I must be confused.  There definitely was/is an a2p tool.

However, for something so tiny, it would seem that you just need perl and the [http://search.cpan.org/~adamk/Process-0.30/lib/Process.pm](http://search.cpan.org/~adamk/Process-0.30/lib/Process.pm) module.
I didn't look, but I'd be shocked if there wasn't an [Oracle module or 20.]("http://search.cpan.org/search?query=oracle&mode=all")

Using an oracle module will probably let you start and status everything related to oracle ... or you could just query the process table (like the script does already) and use built-in perl regex and split() to find whatever you seek. The regex engine in perl is the best in the world, IHMO.

Have fun!

Why switch to perl?  If the script works, that change isn't really useful.  I say that as a perl guy, but I only use it when a bash script gets over 40-50 lines.

---

### Post by learnbash on 2013-10-01
sir,

this is important point to me to learn perl, if you have help me i can start coding it and will understand other things and ask more question here.

---

### Post by TheFu on 2013-10-01
> **learnbash said:**
> sir,

this is important point to me to learn perl, if you have help me i can start coding it and will understand other things and ask more question here.

What have you tried so far?  Asking for help is fine, but you have to make the effort and try some code.  Searching on the internet for "perl tutor" will get you started.  If you want to learn current perl methods, then there is a free book - "Modern Perl." Google will find it.

Randall Schwartz has the Learning Perl book and there are PM (Perl Monger/Monk) groups around the world to join.

So, what have you done already towards your Perl education?
Posting some code here would also be a big step.

---

### Post by drmrgd on 2013-10-01
I have to chime in and say if you are interested in starting to program in perl (based on this and your other recent thread), then you really ought to start at the basics and learn how perl variables, data structures, control structures, etc work before you just start converting scripts.  Having the basics down, which will go pretty fast if you have any programming background at all (which it seems you do), and will allow you to understand and write better scripts down the line.  Really, you should pick up a copy of "Learning Perl" and work through it.  You can probably get through the book in just a couple weeks (depending on your background, effort, and time), and then you'll have a much better background to understand what you'll get from someone just converting this bash script to perl.  

Also, I would agree again with TheFu on the above script - that's not a script that will likely take very much advantage of the power of perl.  Well, except for that piped grep | awk command...might be able to make that shorter with a perl regex :)

---

### Post by Vaphell on 2013-10-02
well, piped grep | awk command is a fail in itself :) Awk is functionally a superset of grep capability, if you move to awk greps can go away.

also there is pgrep that cuts removes the need for the whole ps | grep | grep -v
[http://www.lehman.cuny.edu/cgi-bin/man-cgi?pgrep+1](http://www.lehman.cuny.edu/cgi-bin/man-cgi?pgrep+1)

---

### Post by Lars Noodén on 2013-10-02
> **Vaphell said:**
> well, piped grep | awk command is a fail in itself :) Awk is functionally a superset of grep capability, if you move to awk greps can go away.

also there is pgrep that cuts removes the need for the whole ps | grep | grep -v
[http://www.lehman.cuny.edu/cgi-bin/man-cgi?pgrep+1](http://www.lehman.cuny.edu/cgi-bin/man-cgi?pgrep+1)

Yes.  learnbash, can you explain a little about what you want out of this line?  

DBSTATUS=`ps -ef |grep $PMON_PROC |grep -v grep |awk -F " "  '{print $8}'`

If you walk us through it, it can be shortened down to use just [pgrep](http://manpages.ubuntu.com/manpages/raring/en/man1/pgrep.1.html) by itself.   After that you can show us how far your perl version has gotten, even if it is not yet perfect.

---

### Post by learnbash on 2013-10-02
In this variable i am checking oracle database pmon process name. I have Perl v5.14.4

---

### Post by Lars Noodén on 2013-10-02
What do you think about using [pgrep](http://manpages.ubuntu.com/manpages/raring/en/man1/pgrep.1.html) as suggested above?  It could replace several lines if used in the "if" statement.  Try it with "-x"

About converting it to perl for learning purposes, what do you have so far in perl?  Maybe you can post it in some etherpad or pastebin style site.

---

### Post by learnbash on 2013-10-02
> **Lars Noodén said:**
> What do you think about using [pgrep]("http://manpages.ubuntu.com/manpages/raring/en/man1/pgrep.1.html") as suggested above?  It could replace several lines if used in the "if" statement.  Try it with "-x"

About converting it to perl for learning purposes, what do you have so far in perl?  Maybe you can post it in some etherpad or pastebin style site.

Right Agree pgrep is also good, i will check that. I tried this.

```


$ENV{'ORACLE_BASE'} = "/home/oracle1";
system("lsnrctl start lndb1");

sqlplus as / sysdba, startup ------- > i don't know how to put in perl script. 

```

---

### Post by TheFu on 2013-10-02
If you want to learn perl, use the Process module. All that pgrep stuff goes away.

---

### Post by Lars Noodén on 2013-10-02
That would be Proc::****ProcessTable from libproc-processtable-perl?

---

### Post by Lars Noodén on 2013-10-02
About the sqlplus as / sysdba, startup part.  One possibility is to use open() to open a pipe.  '/ as sysdba'  gets passed as a parameter, 'startup;' gets written to the pipe.

---

### Post by Lars Noodén on 2013-10-07
> **learnbash said:**
> sqlplus as / sysdba, startup ------- > i don't know how to put in perl script. 
[/code]

Without known what *sqlplus* does or needs, my guess would be this where [open()](http://perldoc.perl.org/index-functions.html) is used to open a pipe.

```

#!/usr/bin/perl -T                                                              

use warnings;
use strict;

undef %ENV;     # clear unclean / unknown environment variables                 

$ENV{ORACLE_BASE} = '/home/oracle';	# is this even needed?                  
$ENV{ORACLE_SID}  = 'DB1';		# is this even needed?                  
$ENV{PMON_PROC}   = 'ora_pmon_DB1';	# is this even needed?                  

open( OUT, "|-", "./sqlplus", "/ as sysdba" )   # open for writing              
    or die("$!\n");

open( IN, "<&OUT" )                             # duplicate one for reading     
    or die("$!\n");

print OUT "startup;\n"; # output to script                                      

while ( my $line = <IN> ) {
    print qq(L=$line);
}

close( OUT );
close( IN );

```

The second [open()](http://perldoc.perl.org/index-functions.html) and the while loop might are not needed if there is no output from *sqlplus*

---

### Post by TheFu on 2013-10-14
> **Lars Noodén said:**
> That would be Proc::****ProcessTable from libproc-processtable-perl?

Well, if you are a pro with perl, then need to avoid using system perl stuff.  It is always out of date and is hard to replicated on deployment servers.  PerlBrew is the way that most perl pros manage different perl installations.  Updating the system perl for a programmer will likely break system tools.

BTW, I'm re-reading "Modern Perl 2012" now.  The first few chapters really explain where to get more help, community, websites, books, CPAN!!!! and IRC nicely.  Plus those chapters point to the built-in perldoc command which has extremely complete documentation for the language, functions, modules.

It is still possible to hang yourself with perl, but by creating "Modern Perl" and following the best practices by including 
**use Modern::Perl 2011;**
in all your code, learning will happen.

OTOH, if you just need to know enough perl to hack something together, any of the older books and system perl already installed is probably fine.  If using the system perl, it is probably best to avoid installing CPAN modules - look for the same modules in Ubuntu-specific packages. Much better for dependency resolution and not breaking system tools written in perl.

As far a which process module to use ... I didn't look any up, but I've used a few before. I'd start at search.cpan.org and work from there.

---

