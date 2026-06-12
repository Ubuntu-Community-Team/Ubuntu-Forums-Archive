---
title: "Perl Programmers... system function??"
date: 2007-12-16
forum: Programming Talk
---

### Post by nitro_n2o on 2007-12-16
Hi Perl programmers, 
I was wondering if someone knows how to do this in perl 

"ls *.txt" using the system function or something equivalent? 

I want perl to execute the command with regular expression expansion. Is that possible? 

like: system("ls", "*.txt"); to list all files with the extension "txt" or system("cp", "*.JPG", "*.jpg.backup"); 

Apparently, it doesn't work using "system" it doesn't perform the regexp expansion
any ideas? 

Thanks!!

---

### Post by Trumpen on 2007-12-16
Well, I am not a very good perl programmer but I think you could do either by letting bash to expand wildcards (actually the exact name should be **globbing**) for you

```
system("bash","-c","ls *.txt")
```

or better by using the perl funcion glob("*.txt") (or with the same result <*.txt>):

[php]foreach $el (glob("*.txt")) {
   print("$el ");
}
print("\n");[/php]

Btw, as far as I know "cp *.JPG *.jpg.backup" won't work even on a command line so you'll have to think at something else (foreach?).

---

### Post by slavik on 2007-12-16
[php]@files = <*.txt>;
print $_."\n" for(@files);[/php]

---

### Post by nitro_n2o on 2007-12-16
Thx for the info this is really helpful :) 

and yeah you are right cp *.JPG *.jpg.backup won't .. i just couldn't think of something else

---

### Post by nitro_n2o on 2007-12-16
OMG.. you can do everything in perl :)
> **slavik said:**
> [php]@files = <*.txt>;
print $_."\n" for(@files);[/php]

---

### Post by nhandler on 2007-12-16
An easy way to execute commands like this from withing perl is to use ` (Note: That is shift + the key to the left of 1 and below Esc). So for example

```
$result=`ls *.jpg`;
```
$result will end up holding the output of the command.

---

### Post by slavik on 2007-12-16
it is more overhead though since that is pretty much a system() call.

use glob, it's a built in function and doesn't go through the shell.

---

### Post by tr333 on 2007-12-16
```
$ perldoc -q glob  # search the perldoc FAQ for 'glob'
$ perldoc -f glob  # read the POD page for the 'glob' function
```

If you just want to copy all .jpg to .jpg.backup then BaSH might be easier.
```
for file in *.jpg *.JPG ; do
    cp $file ${file}.backup
done
```

---

### Post by ghostdog74 on 2007-12-16
> **nitro_n2o said:**
> 

"ls *.txt" using the system function or something equivalent? 


There are a few ways to do it, however, i would not encourage this method as its non portable way of doing things. use built in always, like the glob function , or the loop
eg
```

while (<*.txt>)
{
 print $_;
}

```

---

