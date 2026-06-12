---
title: "Unchecking &quot;Allow executing file as program&quot; recursively?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by inktri on 2008-08-10
All of my .txt, .php, etc. files have the "Allow executing file as program" checked under the Permissions tab of Properties. What's a command I can use in the terminal to recursively uncheck that box for every file in my home folder? 

Thanks for the help

---

### Post by bpowell2005 on 2008-08-10
Well, use caution of course, any batch operation of file permissions is very risky...but you could round up all the files you want to change, throw them in a temporary directory, then in terminal, change into that directory and try: chmod -x *.*

I've never tried this, but I'd guess it should work. If the files aren't all yours, you'll have to sudo that command.

---

### Post by AusIV4 on 2008-08-10
Chmod has a recursive option. Running

chmod --recursive -x directory/

Should make the directory and every descending file non-executable. Be warned, however, that this will set directories as non-executable, and you won't be able to enter them until they've been set back to executable.

---

### Post by bpowell2005 on 2008-08-10
Yeah, there are a lot of hidden directories in your Home folder that need to be accessed by Ubuntu in its day to day operations. That's why I'd round everything you want to change up into a temp directory before either running the recursive command AusIV4 suggested, or any other command. Don't dork up the hidden directories in your Home folder!

---

### Post by bcscomp on 2009-04-30
steve@steve-laptop:/home$ cd steve
steve@steve-laptop:~$ chmod --recursive -x *.txt
steve@steve-laptop:~$

---

### Post by matchstich on 2009-09-17
ok, i seem to have the same problem on some files in my home directory.

have ten files in there. ones i created to keep some stuff.

but, they have that same box checked, allow executing file as program.

will not let me uncheck.  will any of this work for my problem.

thanks

---

### Post by dwasifar on 2009-09-17
> **matchstich said:**
> ok, i seem to have the same problem on some files in my home directory.

have ten files in there. ones i created to keep some stuff.

but, they have that same box checked, allow executing file as program.

will not let me uncheck.  will any of this work for my problem.

What's the ownership and group of those files?  I'm betting they're set with root as owner and group, and access for Others is read-only, right?

If you want to change them in a GUI window (as opposed to doing it from command line), open a terminal and type:

```
gksu nautilus
```

This will open a file manager window with root privileges, and you can navigate to the files and change the file permissions (and, presumably, the ownership) from there.  

Be sure to close it as soon as you're done, so you don't wind up creating more problems by working as root when you don't mean to be.

---

### Post by niteshifter on 2009-09-17
Hi,

To batch change just the files and not change directory permissions use the find command:

Change to your home folder
```
cd ~
```

The below will change **every** file to non executable:
```
find . -type f -print0 | xargs -0 /bin/chmod -x
```

Just the .txt files? Do this:
```
find . -name *txt -type f -print0 | xargs -0 /bin/chmod -x
```
Replace *txt with *php for those files.

---

### Post by matchstich on 2009-09-17
ok, i did gksu nautilus--from there i went to file system---clicked on home --then username  --opened it and went the files i wanted to change.  

they all show me as owner  and i uncheck  the box saying execute 

but i close it out and open permissions again and the box is checked.

it is only on about 10, there are a lot more in there and none of them are checked.

i'm confused.  could be the oxycontin. 

but, will it hurt any thing to leave them that way?

thanks

---

### Post by egalvan on 2009-09-17
Nautilus has a File Management Preference that allows changing the behavior...

Edit -> Preference

then choose 

Behavior tab

and finally set the behavior you want.


It's the middle one, called Executable Text Files.

This may or may not be the fix you need.

---

### Post by matchstich on 2009-09-17
> **niteshifter said:**
> Hi,

To batch change just the files and not change directory permissions use the find command:

Change to your home folder
```
cd ~
```

The below will change **every** file to non executable:
```
find . -type f -print0 | xargs -0 /bin/chmod -x
```

Just the .txt files? Do this:
```
find . -name *txt -type f -print0 | xargs -0 /bin/chmod -x
```
Replace *txt with *php for those files.

now, from what i read i do not want to change the whole home folder to not allowing executing file as program, right?  read there are hidden files in there.

i open natilus, go to file system>home>then username, where all my files are at. there's about 20 in there but only half have that boxed check.

so it is only the one marked usename and has all the files i created  plus desktop and examples etc.,that i want to uncheck  right?

thanks

---

### Post by matchstich on 2009-09-17
> **egalvan said:**
> Nautilus has a File Management Preference that allows changing the behavior...

Edit -> Preference

then choose 

Behavior tab

and finally set the behavior you want.


It's the middle one, called Executable Text Files.

This may or may not be the fix you need.

well i followed these instructions, under behavior tab  the only box checked was ask every time.  which is how i found this problem.

had double clicked on a file and that message came up.

thanks

---

