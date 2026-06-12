---
title: "Perl Output of cd Command"
date: 2010-01-28
forum: Programming Talk
---

### Post by melrom on 2010-01-28
Hi everyone-

I've been experiencing some weird problems with a perl script that I moved from one server to another. perl version is perl, v5.8.8, running on RHEL.

The basic idea is the following. I check if a dir exists via the if(-d /path/of/dir) and then I try to cd into it (it's should be a link). Anyway, for example's sake:

```
my $temp = `cd /path/to/dir 2>&1`;
if($temp eq ''){
   print "Empty\n";
}else{
   print "!empty: $temp\n";
}

```

Even when /path/to/dir completely **does NOT exist**, I still get that $temp is an empty string. I was anticipating getting the 'cd: directory does not exist'. If I take away the 2>&1, I still get no output to the variable. I tried wrapping this in a system call:

```
my $temp = system("cd /path/to/dir");

```

except that gives me -1 when the directory **DOES** exist.

Any ideas on what I'm doing wrong?

---

### Post by myrtle1908 on 2010-01-28
If you just want to know if a particular directory is empty you can do 

```

use strict;
use warnings;

my $dir = 'c:\temp\a'; # yes i'm stuck on windows today
if (scalar <$dir/*>) {
  print "Not empty";
} else {
  print "Empty";
}
```

You should also note that the 'system' function returns the exit status of the program/command.  Have a read of this perldoc page 

```
perldoc -f system
```

---

### Post by melrom on 2010-01-28
I don't want to know if its empty. Sorry, I was typing up just a test string to print to the screen. I want to know if there's an error when it tries to cd into the directory.

Also, I *know* how system works. It should return 0 on successful cd into the directory. What I am saying is that it is currently returning -1 for the cd even when the dir exists and I can successfully cd /path/to/dir from command line.

Also, I read this:
> 
In the shell you would type "cd /home" to change the workingdirectory to /home. You could write the following in your Perl script:

system("cd /home");

But it would have no effect. In fact, since the system call forksfrom the process used by the interpreter, it doesn't change the workingdirectory of your script. Instead, you can use a Perl function called"chdir":

chdir "/home";

from [http://www.linuxforums.org/articles/learn-perl-in-10-easy-lessons-lesson-5_134.html]("http://www.linuxforums.org/articles/learn-perl-in-10-easy-lessons-lesson-5_134.html").

But I technically don't want to actually cd into the directory. I just want to know if the cd would be successful. Perhaps checking if chdir fails would achieve the desired effect.

---

### Post by myrtle1908 on 2010-01-28
> **melrom said:**
> But I technically don't want to actually cd into the directory. I just want to know if the cd would be successful. Perhaps checking if chdir fails would achieve the desired effect.

Then I suppose you can just check if its a directory and see if you have read access eg

```
use strict;
use warnings;

if (-d -R 'c:\temp\a') {
  print "Is a dir and can read";
} else {
  print "Not a dir and no read access";
}
```

---

### Post by melrom on 2010-01-28
That'll work! Thank you! :)

---

