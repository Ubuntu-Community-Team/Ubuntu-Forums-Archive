---
title: "cd to iPhone"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-05-06
Hi Guys,

I have a script that I want to use that moves photos from one folder to another.
I though it would be cool to have the script cd to the folder that contains the photos rather than me having to open a terminal in that folder then run the script.

Here is the question:
How can I cd onto my iPhone 4?

When Ubuntu mounts the phone, I can choose Open Terminal Here and the prompt shows:

```

Today is Mon May 06 @ 09:56:00 ~/.gvfs/jne’s iPhone $

```

But as you see below, when I try to cd onto the phone from home for example I get an error that there is no such file or directory.
ls does show that there is a Phone present.

What am I doing wrong?

```


Today is Mon May 06 @ 09:53:31 ~ $ cd ~/.gvfs
Today is Mon May 06 @ 09:54:08 ~/.gvfs $ ls
Documents on jne’s iPhone  jne’s iPhone
Today is Mon May 06 @ 09:54:10 ~/.gvfs $ ls "jne's iPhone"
ls: cannot access jne's iPhone: No such file or directory
Today is Mon May 06 @ 09:54:40 ~/.gvfs $ ls jne
ls: cannot access jne: No such file or directory
Today is Mon May 06 @ 09:55:04 ~/.gvfs $ cd jne's iPhone
> 
> 


```

---

### Post by squakie on 2013-05-06
> **GrouchyGaijin said:**
> ....
When Ubuntu mounts the phone, I can choose Open Terminal Here and the prompt shows:

```

Today is Mon May 06 @ 09:56:00 ~/.gvfs/jne&#8217;s iPhone $

```

But as you see below, when I try to cd onto the phone from home for example I get an error that there is no such file or directory.
ls does show that there is a Phone present.

What am I doing wrong?

```


Today is Mon May 06 @ 09:53:31 ~ $ cd ~/.gvfs
Today is Mon May 06 @ 09:54:08 ~/.gvfs $ ls
Documents on jne&#8217;s iPhone  jne&#8217;s iPhone
Today is Mon May 06 @ 09:54:10 ~/.gvfs $ ls "jne's iPhone"
ls: cannot access jne's iPhone: No such file or directory
Today is Mon May 06 @ 09:54:40 ~/.gvfs $ ls jne
ls: cannot access jne: No such file or directory
Today is Mon May 06 @ 09:55:04 ~/.gvfs $ cd jne's iPhone
> 
> 


```

Did you type in what you posted, or is it an actual copy and paste?  I ask because of one thing I noticed:

> Today is Mon May 06 @ 09:54:08 ~/.gvfs $ ls
Documents on jne&#8217;s iPhone   iPhone


There is a forward leaning tic mark - jne&#8217;s - and at least I can't find any such character on my keyboard.  The closest I can get is ' - and I noticed that's what you are typing as well: jne's  .  Considering they are showing as 2 different characters, I have to assume therefore that they ARE different characters.  That being the case, jne's isn't the same as jne&#8217;s.

If you can match that character completely, then you just need to enclose the entire string in quotes, such as:  ls "jne&#8217;s iPhone"  - or ls "Documents on jne&#8217;s iPhone"  .

I'm sure there is a way to generate that symbol - I just don't how right now.   Somebody else may be able to tell you now - I'll look around and see if I can find how to generate it.

So far, I think there's supposed to be a difference between an apostrophe and the "tick mark", but I can't find anything to prove it.

---

### Post by GrouchyGaijin on 2013-05-06
> **squakie said:**
> That being the case, jne's isn't the same as jne’s.



Well, I [COLOR=#ff0000]*thought*[/COLOR] I copied and pasted, but I must have typed because when I just tried now, being sure to copy and not type.
Everything worked.

Thank you Eagle Eye!

---

