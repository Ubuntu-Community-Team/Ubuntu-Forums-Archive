---
title: "Changing &quot;Windows File Names&quot; to &quot;linux_file_names&quot;"
date: 2007-06-24
forum: Programming Talk
---

### Post by hammo on 2007-06-24
Hello All,

I have just recently converted to Ubuntu 7.04 (recently - last two hours). Now I have copied over all of my files from windows. Now I have been working on Linux for about a year now and even in windows I use Linux naming conventions (no white spaces). Unfortunately, music that I have downloaded over the past few years (...) have file names that leave much to be desired (LOTS of white space :p). I was wondering if it was possible to write a shell or perl script that could change spaces in file names to underscores. It doesn't have to be in shell or perl, but they are the only scripting languages I know to script in atm.

Thanks in advance,

Adam.

---

### Post by Choad on 2007-06-24
well for music alone, there are plenty of editors that fetch the info about the songs off the net and then rename and re tag each song in a way you want

cowbell is the one i can remember the name of, plus there is the "bulk renamer" tool from xfce which does every type of file

---

### Post by Choad on 2007-06-24
mrename looks promising too

---

### Post by Soybean on 2007-06-24
```

#!/usr/bin/perl

while(<*>)
{
        $o = $_;
        s/\ /\_/g;
        rename($o, $_);
}

```
That'll do everything in the current directory. You could also change <*> to <*.mp3> if you only want to change mp3s, for example.

---

### Post by vanadium on 2007-06-24
You can also get away in the shell: have the find command locate all relevant files and have the rename command act on them. It would go something like this:

find . -name *.mp3 -execdir rename 's/\ /_/g' '{}' \;

Test this first, because I didn ;) This will execute the rename command on any found file. The rename command first takes an expression telling it what to do:

's/\ /_/g'

The s means "search/replace", the g means "global", i.e. replace all instances. After the first slash comes what to search for: \[space]. The backslash "protects" the space after it from being interpreted as usual by the shell. Nafter the second slash comes what we replace with: _ in this case.

'{}' will contain the file name found by find.

---

### Post by hsweet on 2007-06-24
Perl would work well.

I'm a bit rusty but I think a regular expression like the one below would do it.

```

s/ /_/;
```

Here's a bit more. 
There is some easy way to read all the files in a folder, I can't remember.

Start a loop 
```
foreach (@songs){
#do the substution
s/ /_/;
#rename file with new name using a perl function or a shell command 
shell mv "Old Windows Name with spaces" $_;
}
 
```


Ask the ques at perlmonks.org for better code:p

---

### Post by hammo on 2007-06-24
Wow, thanks for all that. Worked like a charm

Regards,

Adam

---

### Post by charles woodward on 2007-06-24
Just like to thank everyone for their input - just saved me hours - my brother sent me a disk with about 500 jpegs on it - all with spaces in the name.  The pearl script by soybean worked like a charm.  

Thanks

---

