---
title: "Writing a Windows .exe replacement"
date: 2010-01-05
forum: Programming Talk
---

### Post by beegary on 2010-01-05
Hello Programmers!!
I am a total newb when it comes to programming............
 
I have an .exe file that I used to use in Windows XP. I suppose I could try to run it under Wine but I want to learn a programming language.
The .exe file is a small file (less than 2mb), is it possilbe to reverse engineer  the program and re-write in Ubuntu?
(The .exe is used to remove empty space in another file, i.e. the file maybe 40mb but only actually hold 20mb)
 
Thanks in advance

---

### Post by harold4 on 2010-01-05
You have already defined the basic specs. :)

A quick bash script could do this for you.

---

### Post by akashiraffee on 2010-01-05
Keep in mind an .exe that is "less than 2mb" is still the product of thousands of lines of code.  Altho the amount of source is usually less than the exe size, remember, the entire bible, or the text of war and peace, are both less than 0.5mb.  

However, if the exe has been statically linked, the amount of original work you would have to reverse engineer is less, but, honestly, it will probably take you *years* to figure it all out.

Not that I want to discourage you from programming, just warning you about reality.  If you tell us what the application is, someone can give you a better idea of what's involved and how you might do it on a linux system.

> **harold4 said:**
> You have already defined the basic specs. :)

A quick bash script could do this for you.
Sorry Harold but that is** extremely incorrect.**

---

### Post by Can+~ on 2010-01-05
> **akashiraffee said:**
> Sorry Harold but that is** extremely incorrect.**

[QUOTE=OP](The .exe is used to remove empty space in another file, i.e. the file maybe 40mb but only actually hold 20mb)[/QUOTE]

I think he meant that he could do the task (remove empty space in another file) with bash.

---

### Post by beegary on 2010-01-05
Im sorry folks the program is actually 24kB:
[http://www.r4dstt.com/download-r4ds-rom-trimmer-20.html](http://www.r4dstt.com/download-r4ds-rom-trimmer-20.html)

It is possible to run under wine, I have a pc I can run it on etc but I am more interested in using this as a little project helping me o learn a programming language.
I have done some bash scripting etc. but I was thinking of trying to achieve this in Python??

---

### Post by Can+~ on 2010-01-05
> **beegary said:**
> but I was thinking of trying to achieve this in Python??

Sure, why not. Could you explain exactly, what do you want to achieve? The previous expalanation ("remove empty space in another file") was pretty shallow and ambiguous.

---

### Post by beegary on 2010-01-05
> **Can+~ said:**
> Sure, why not. Could you explain exactly, what do you want to achieve? The previous expalanation ("remove empty space in another file") was pretty shallow and ambiguous.

It was, purposely so! I wasnt sure if peeps on here would approve of it. Anyway......

Nintendo DS game backups can be ripped to *.nds files. But the rip is always bigger than the actual game as they are adjusted to fit on certain size cartridges. 
The program I linked in my previous post cuts the unused space from the *.nds file, more games can then be stored.

I just knew the program was simple and small and therefore a good place to start? I dont actually 'need' a Linux version

Thank you

---

### Post by Hellkeepa on 2010-01-05
HELLo!

Any language that can open a file and modify a byte-stream (which by my knowledge is about every language out there), can be used to accmplish this. So just pick the one you want to learn, and go ahead.
The details of what is removed, however, I cannot help you with. Might be helpful to do a diff on a file run through the other application, comparing the original with the cut down version. Should be fairly easy to spot the pattern then.

Happy codin'!

---

### Post by The Cog on 2010-01-05
This could be a very rewarding and satisfying learning project. But there is a lot to learn, and it will take time. I would suggest using python as your starter programming language - it's fairly easy to get on with, and well capable of the job. You will of course need ot figure out exactly - **really** exactly how to create the shortened file from the larger one, and that itself could be a big challenge.

If you feel up to the challenge, I would encourage you to give it a go. When you're learning programming, having a target like that probably makes it far easier than just learning whatever the books say is the next bit you should study. To me at least, having a **reason** to learn something makes it far easier.

P.S. Although I suggest python, almost any programming language can do this. If you're not sure which language to learn, look at the stickies.

---

### Post by WitchCraft on 2010-01-05
Search google for the words:
python tutorial linux
or 
python hello world


You need to take care:
The latest python version is 3.0+
But there are also tutorials out there that are for Python 2.x 

Now the problem is 2.x and 3.0 are NOT very compatible AFAIK...
(although the changes needed are rather minimal)

Keep that in mind when you search for Python tutorials, and find one that doesn't work no matter which example you try...

If you have trouble, come back to this forum and open a new thread describing your problems.

---

### Post by myrtle1908 on 2010-01-05
> **beegary said:**
> (The .exe is used to remove empty space in another file, i.e. the file maybe 40mb but only actually hold 20mb)

I know nothing of the file format you are talking of but removing redundant space from say a text file is simple.  An example in Perl which may get you started ...

```
use strict;
use warnings;

while (<DATA>) {
  s/(?<=\s)\s+//g;
  print;
}

__DATA__
Some    extra spaces   here,   there  and            everywhere.
```

Yields:
```

Some extra spaces here, there and everywhere.
```

---

### Post by lavinog on 2010-01-06
> **WitchCraft said:**
> 
You need to take care:
The latest python version is 3.0+
But there are also tutorials out there that are for Python 2.x 

Now the problem is 2.x and 3.0 are NOT very compatible AFAIK...
(although the changes needed are rather minimal)


I think it is still recommended to use the 2.x syntax and when it is time to make the switch to 3.x use the program 2to3 to convert it.

---

### Post by beegary on 2010-01-06
Thank you very much everyone, about a month ago I did create a Hello world python script, it seemed fairly simple to me (I have has some experience with Bash,SQL).
 
Whether I wrote it in 3.0 or 2.0 Im not sure, I wasnt aware that there was a transition going on!!!
 
I also did have a quick run through some perl tutorials but Python seemed a bit more universal, is this correct?
 
 
I only made a full transition to Ubuntu recently, but thanks to all the help I have had on these forums it has been fairly painless.
windows already feels a bit foreign to me!!

---

### Post by myrtle1908 on 2010-01-06
> **beegary said:**
> I also did have a quick run through some perl tutorials but Python seemed a bit more universal, is this correct?

I have no firm numbers but I'm sure you will find that Perl is used more widely than Python by some margin.  Perl is still a very popular general purpose *nix scripting language and has been since the late 80s.  Python is steadily gaining popularity.  Many prefer Python as its syntax is "cleaner" and thought to be easier to read.  I do not share these views :)  Just use whatever makes most sense to you.

---

