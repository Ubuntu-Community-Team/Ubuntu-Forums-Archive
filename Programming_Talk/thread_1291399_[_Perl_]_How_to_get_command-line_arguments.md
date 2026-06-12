---
title: "[ Perl ] How to get command-line arguments ?"
date: 2009-10-14
forum: Programming Talk
---

### Post by OpenGuard on 2009-10-14
What I'm doing wrong ? Could it be the effect of ActivePerl, not syntax by itself ?

```
$numArgs = $#ARGV + 1;
print "$numArgs command-line arguments.\n";

foreach $argnum (0 .. $#ARGV) {
    print "@ARGV[$argnum]\n";
}

$exit = <>;
``````
C:\Documents and Settings\<username>\Desktop>sample.pl command line argument demo
4 command-line arguments.
command
line
argument
demo
Can't open command: No such file or directory at C:\Documents and Settings\<username>\Desktop\sample.pl line 8.
Can't open line: No such file or directory at C:\Documents and Settings\<username>\Desktop\sample.pl line 8.
Can't open argument: No such file or directory at C:\Documents and Settings\<username>\Desktop\sample.pl line 8.
Can't open demo: No such file or directory at C:\Documents and Settings\<username>\Desktop\sample.pl line 8.

```

---

### Post by steeleyuk on 2009-10-14
I know very little of Perl, and maybe I'm missing something but do you need the line $exit = <>;? 

Take that off and Perl prints the arguments received without the errors about opening the file.

---

### Post by OpenGuard on 2009-10-14
> **steeleyuk said:**
> I know very little of Perl, and maybe I'm missing something but do you need the line $exit = <>;? 

Take that off and Perl prints the arguments received without the errors about opening the file.

Hmm, you are right, all errors gone. But why ? I've added $exit = <>; because I usually launch my script ( if I can call it so :D ) from Desktop, which means, I will not see anything ( it'll close itself ). Any workarounds ?

---

### Post by diesch on 2009-10-14
What about
```
print '<ENTER> to exit'; getc
```

---

### Post by OpenGuard on 2009-10-14
> **diesch said:**
> What about
```
print '<ENTER> to exit'; getc
```

Bingo! Thank you :)

---

