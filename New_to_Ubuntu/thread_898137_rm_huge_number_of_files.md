---
title: "rm huge number of files"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by SVWander on 2008-08-22
I was recovering some jpeg files that had been deleted. It worked. Well, it worked much too well. It filled my home folder with 52,000 jpg! This computer doesn't have the horsepower to get rid of them in nautilus. Can someone tell me how to rm them using command lines. This is one of the commands I tried:

lap1@lap1-laptop:~$ sudo rm *.jpg
sudo: unable to execute /bin/rm: Argument list too long

I also used -f and other ways that I cannot remember. I know there is an easy way to do this. Can someone tell me the correct way.

Thanks, Tim

---

### Post by yabbadabbadont on 2008-08-22
```
find /home/username -type f -name "*.jpg" | xargs rm -f
```

Note: This will remove ALL files that end in ".jpg" in your home directory, AND any subdirectories...

---

### Post by Mister.Vash on 2008-08-22
If you don't want the to include subdirectories add the maxdepth parameter to find.

```
find /home/username -maxdepth 1 -type f -name "*.jpg"
```

---

### Post by aloshbennett on 2008-08-23
I am not sure if these would work. The problem is that, there are a LOT of files.

Is it okay to take out the useful stuff out of the directory (using command prompt) and delete the directory?

Else, you could take the list of files into some temp file, break it up into chunks and delete them.


Edit: ls | head -n 1000 | xargs rm
Delete in multiple batches

---

### Post by yabbadabbadont on 2008-08-23
> **aloshbennett said:**
> I am not sure if these would work. The problem is that, there are a LOT of files.

Is it okay to take out the useful stuff out of the directory (using command prompt) and delete the directory?

Else, you could take the list of files into some temp file, break it up into chunks and delete them.


Edit: ls | head -n 1000 | xargs rm
Delete in multiple batches

Using find and piping the output to xargs is the time honored Unix way to handle this situation.  The solution you have proposed will fail for the same reason that the OP's rm command failed.  The shell itself cannot pass all of the files to the ls command as parameters.  You will get an arg list too long error just as the OP did.

---

### Post by Mister.Vash on 2008-08-23
They should work, basically the rm command is running up against a limit, where the find command is not.  The kernel can be recompiled to set a larger limit, but with workarounds that isn't really needed.  It's a fairly common issue in these situations and a lot of people have posts about it

Here's one that gives a very high level overview of the issue
[http://www.cyberciti.biz/faq/argument-list-too-long-error-solution/](http://www.cyberciti.biz/faq/argument-list-too-long-error-solution/)

The workarounds don't even need to be that complex, you can do things like
rm a*.jpg
 or 
rm pict1*.jpg
and just go after subsets until you remove everything

Or you can just run
```
find $HOME -maxdepth 1 -type f -name "*.jpg" -print0 | xargs -0 rm
```

If you want to test if to see if comes up with the list of files correctly, just put an ls at the end instead of rm
```
find $HOME -maxdepth 1 -type f -name "*.jpg" -print0 | xargs -0 ls
```

And this will handle files with spaces in the name, where the previous post wouldn't

---

### Post by aloshbennett on 2008-08-23
> **yabbadabbadont said:**
> Using find and piping the output to xargs is the time honored Unix way to handle this situation.  The solution you have proposed will fail for the same reason that the OP's rm command failed.  The shell itself cannot pass all of the files to the ls command as parameters.  You will get an arg list too long error just as the OP did.

My bad. Thanks! I have faced this once, and did it in a roundabout way. Now I know :)

---

### Post by pauper on 2008-08-23
> **Mister.Vash said:**
> Here's one that gives a very high level overview of the issue

Indeed. Though the author keeps putting bold titles about LINE_MAX, yet tells
the story about upper limit of arguments and environment variables for a
process (ARG_MAX).

---

### Post by vanadium on 2008-08-23
Alternatively, with current versions of find, you can use

```

find $HOME -maxdepth 1 -type f -name "*.jpg" -exec rm "{}" \;

```

---

### Post by SVWander on 2008-08-23
> **Mister.Vash said:**
> They should work, basically the rm command is running up against a limit, where the find command is not.  The kernel can be recompiled to set a larger limit, but with workarounds that isn't really needed.  It's a fairly common issue in these situations and a lot of people have posts about it

Here's one that gives a very high level overview of the issue
[http://www.cyberciti.biz/faq/argument-list-too-long-error-solution/](http://www.cyberciti.biz/faq/argument-list-too-long-error-solution/)

The workarounds don't even need to be that complex, you can do things like
rm a*.jpg
 or 
rm pict1*.jpg
and just go after subsets until you remove everything

Or you can just run
```
find $HOME -maxdepth 1 -type f -name "*.jpg" -print0 | xargs -0 rm
```

If you want to test if to see if comes up with the list of files correctly, just put an ls at the end instead of rm
```
find $HOME -maxdepth 1 -type f -name "*.jpg" -print0 | xargs -0 ls
```

And this will handle files with spaces in the name, where the previous post wouldn't

You saved the day! And all the other people that were kind enough to help me. I have so much to learn! If books were not so expensive I would but more on Linux. I find it hard to read online. I enjoy working with command lines but I am afraid I have no idea what I just did! I am going to try to research and at least try to figure out what the commands did and how they did it. Thanks so much for all the kind help.  Tim

---

