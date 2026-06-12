---
title: "[pearlre] removing special charachter at beginning of line"
date: 2009-08-11
forum: Programming Talk
---

### Post by Ram-Z on 2009-08-11
Hi,
I'm having some trouble with removing a bunch of '+' at the beginning of a string with the bash command 'rename'.

Basically I have some files:

+foo+bar1.txt
foo+bar2.txt

where I want to remove the + in front and replace any + in the middle with a space.

I tried to remove the first + with:


```
rename "s/^\+//" *.txt
```

```
rename "s/\A\+//" *.txt
```

and	

```
rename "s/\A\Q+//" *.txt
```

but everything returns:

```
Unknown option: e 
Unknown option: e 
Unknown option: e 
Usage: rename [-v] [-n] [-f] perlexpr [filenames]
```

with "e" being the first letter after the + of the three files starting with +

Any help would be appreciated

---

### Post by kaibob on 2009-08-11
I use rename on a pretty regular basis, but it doesn't seem to work any more. Have you tried to rename some other files?

---

### Post by unutbu on 2009-08-11
```
rename 's/^[+]//' -- *.txt
```
When you see
Unknown option: e 

it is a sign that somehow rename is (mistakenly) being passed arguments. Most unix commands understand '--' to signal the end of all arguments. I'm not sure why it is necessary in this case, but it seems to work.

---

### Post by shawnhcorey on 2009-08-11
> **unutbu said:**
> Most unix commands understand '--' to signal the end of all arguments. I'm not sure why it is necessary in this case, but it seems to work.

Some command have "plus" options are are the opposite of the "minus" options.  So a file name that starts with a plus sign is considered to be an option.  The "--" means the end of all options.

---

### Post by Ram-Z on 2009-08-11
This works fine. Thank you

---

### Post by unutbu on 2009-08-11
shawnhcorey, thanks, I understand now.

---

### Post by kaibob on 2009-08-12
Why do I need to use -- in the following:

> kaibob@dell:~$ touch old.txt
kaibob@dell:~$ rename -n 's/old/new/' *.txt
Unknown option: f
Usage: rename [-v] [-n] [-f] perlexpr [filenames]
kaibob@dell:~$ rename -n 's/old/new/' -- *.txt
old.txt renamed as new.txt

EDIT

The directory that contained the file old.txt also contained the file +foo+bar1.txt. Rename saw this file and gave the error message. Once I removed +foo+bar1.txt, rename worked fine with old.txt.

---

### Post by ghostdog74 on 2009-08-12
@OP, you can just write a perl script for yourself

```

while(<*\+*>){    
    $old=$_;
    s/^\+//;
    s/\+/ /;
    rename $old ,"$_";
}


```
i suggest you go read up the docs from this point on. see my sig for Perl doc

---

### Post by shawnhcorey on 2009-08-12
> **kaibob said:**
> The directory that contained the file old.txt also contained the file +foo+bar1.txt. Rename saw this file and gave the error message. Once I removed +foo+bar1.txt, rename worked fine with old.txt.

When you say "*.txt", the shell creates a list of all files ending with "txt" and sorts them as by their ASCII characters.  Since "+" is before any letter in ASCII, any file starting with it appears first.  And causes problems.  :)

See `man ascii` for a list of ASCII characters.

---

### Post by Ram-Z on 2009-08-12
> **ghostdog74 said:**
> @OP, you can just write a perl script for yourself

Yeah, that's what i wanted to do in the end. But since it didn't work whith rename, I didn't want to start a perl script since i know nothing about perl except regex.

I'll start learning perl sometime soon when i get time.

Thanks

---

### Post by shawnhcorey on 2009-08-12
If you're going to do it in Perl, you should used the move() sub in File::Copy.  See `perldoc File::Copy` for details.

---

### Post by Ram-Z on 2009-08-14
> If you're going to do it in Perl, you should used the move() sub in File::Copy. See `perldoc File::Copy` for details. 

Thx. I'll look into that... Although the rename() command worked great on my Mac OSX and my ubutnu box.

I'm matching my files with their file extension so I'm sure i don't get any folders and odd behaviours. 

I guess I'll be using move() from now on since it's platform independent.

---

