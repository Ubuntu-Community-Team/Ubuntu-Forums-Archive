---
title: "[SOLVED] Absolute path string issues in Python"
date: 2008-06-11
forum: Programming Talk
---

### Post by GammaPoint on 2008-06-11
I've got a home-built GUI that I built to play videos (with the configuration options for outputting to our TV, etc, so my fiancee doesn't have to learn) and it works great.  However, I recently discovered a small bug that I wanted some help on.  The problem occurs in the function I've got below:

```
import os

rootdirectory='/home/[GammaPoint]/media'   # this is the  
                            #directory that  the walk
                            # starts from

videolist=[]

def avi_finder(dummy,dirname,filesindir):
    for fname in filesindir:
        ending=os.path.splitext(fname)[-1]
        if ending =='.avi':
            vidlocation=os.path.join(dirname,fname)
            vidname=fname
            newadd=(vidname,vidlocation)
            videolist.append(newadd)
            videolist.sort()


os.path.walk(rootdirectory,avi_finder,None)

```

All this does is that it finds all files ending with '.avi' in the directory tree starting at the rootdirectory and puts them in a list along with the location of the video. And it works well, for the most part....

So in a later part of my GUI I can issue a command along the lines of 

```

command='mplayer -fs' + vidlocation
os.system(command)

```

to play the movie in mplayer. However this runs into difficulties if the video name has spaces, apostrophes, or parentheses in them because then the absolute path name isn't correct.  For example, if my movie is called 'This is my movie.avi' in a directory called /home/movies/ my script will try to issue the command

```
mplayer -fs /home/movies/This is my movie.avi
```

when of course the correct expression is 

```
mplayer -fs /home/movies/This\ is\ my\ movie.avi
```

My code currently handles this case by using the string.replace() method. I.e., I can do the following:

```
vidlocation=vidlocation.replace(" ","\ ")
```

and that fixes it.  This also works for parentheses [ "\(" instead of "(" ]. The problem that I'm having is if the file name has an apostrophe in it.

This is illustrated by what happens in a python interactive session:

```
Python 2.5.2 (r252:60911, Apr 21 2008, 11:12:42) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> a="This is a string with random' apostrophe"
>>> a
"This is a string with random' apostrophe"
>>> a.replace("'","\'")
"This is a string with random' apostrophe"
>>> a.replace("'","\\'")
"This is a string with random\\' apostrophe"
>>> 

```

I can't seem to be able to use the same trick, because either I don't get the backslash, or I get TWO of them (and of course the pathname just needs one).  

Any ideas as to how to do this?  Thanks for reading this LONG post :)

---

### Post by ghostdog74 on 2008-06-11
try putting the quotes before and after the video name
```

command='mplayer -fs ' + "'" + vidlocation + "'"

```

---

### Post by GammaPoint on 2008-06-11
Hi ghostdog, that didn't work for me but I think you are looking at the right section of code to find the problem.  So I've got this section of code:

```

    
        command='mplayer -fs '+path
        print 'command=',command
        os.system(command)

```

and I'll describe what I see for the various changes we are making.  Before I do your suggestion I get (as output in the terminal)

> 
**command= mplayer -fs /home/GP/media/trans_output/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women.avi**

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/GP/media/trans_output/Peep Show - 5x06 - Marks\ [B]Women/Peep\ Show\ -\ 5x06\ -\ Marks Women.avi.
File not found: '/home/GP/media/trans_output/Peep Show - 5x06 - Marks\ Women/Peep\ Show\ -\ 5x06\ -\ Marks Women.avi'
Failed to open /home/GP/media/trans_output/Peep Show - 5x06 - Marks\ Women/Peep\ Show\ -\ 5x06\ -\ Marks Women.avi[/B].



This is obviously a problem since the file path name doesn't even show apostrophes at all in the output.

If I try your suggestion I get as output:

> 
**command= mplayer -fs '/home/GP/media/trans_output/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women.avi'**
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/GP/media/trans_output/Peep\ Show\ -\ 5x06\ -\ Marks Women/Peep Show - 5x06 - Marks\ Women.avi.
[B]File not found: '/home/GP/media/trans_output/Peep\ Show\ -\ 5x06\ -\ Marks Women/Peep Show - 5x06 - Marks\ Women.avi'
Failed to open /home/GP/media/trans_output/Peep\ Show\ -\ 5x06\ -\ Marks Women/Peep Show - 5x06 - Marks\ Women.avi.[/B]




Now if I make the change to the code:

```

 command='mplayer -fs '+'"'+path+'"'

```

(i.e., similar to your suggestion, but switching ' with ") we get a slight improvement. Here's the output:

> 

**command= mplayer -fs "/home/GP/media/trans_output/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women.avi"**
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/GP/media/trans_output/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women.avi.
[B]File not found: '/home/GP/media/trans_output/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women.avi'
Failed to open /home/GP/media/trans_output/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women/Peep\ Show\ -\ 5x06\ -\ Mark's\ Women.avi.[/B]



So I've got the quotations in there now! But now I need a backslash in front of them for the path name to work correctly. I feel like I'm at square one though, because if I knew how to get the backslash in there I don't think I would need to put the '"' around my path anymore....

---

### Post by ghostdog74 on 2008-06-11
hey is that porn? :)
anyway, another approach, if you are not fussy, is to change  those spaces in the files to non space for mplayer. Beats having to scratch your head on escaping this and that..right?

---

### Post by GammaPoint on 2008-06-11
> **ghostdog74 said:**
> hey is that porn? :)
anyway, another approach, if you are not fussy, is to change  those spaces in the files to non space for mplayer. Beats having to scratch your head on escaping this and that..right?

Hehe, it looks like it doesn't it?  Nah, it's actually a very popular British comedy (most popular I think). I HIGHLY recommend it. It's my favorite show, second only to Arrested Development.

I can certainly go in and manually change the files with apostrophes to one without but it's nice to simply be able to download something and then not worry about it any longer (especially since this program is largely for my fiancee and to facilitate her watching stuff---I can easily just use the terminal myself). Although I suppose I could also use the linux 'rename' program in my python GUI script to rename some of these things (if I don't run into the same problems doing that).  But now I think I'm just really curious as to how I can do it the original way :)

---

### Post by ghostdog74 on 2008-06-11
> **GammaPoint said:**
> 
I can certainly go in and manually change the files with apostrophes to one without but it's nice to simply be able to download something and then not worry about it any longer.  And now I'm really curious :)
you don't have to. Before your program plays the file, check to see if there are spaces. if there are, rename it. eg
```

>>> s="this is a tes't file with   spaces.avi"
>>> if " " in s or "'" in s:
...  s=s.replace("'","")
...  print s
...  print "-".join(s.split())
...
this is a test file with   spaces.avi
this-is-a-test-file-with-spaces.avi
>>>                                                         
>>> os.rename(oldfile, s )
>>> command = "mplayer ...." + s
>>> os.system(...blah ... )

```

---

### Post by imdano on 2008-06-11
Are you sure ```
a.replace("'", "\\'")
```doesn't work?
```
>>> a = "this is a string with random' apo"
>>> print a.replace("'", "\'")
this is a string with random' apo
>>> a.replace("'", "\'")
"this is a string with random' apo"
>>> a.replace("'", "\\'")
"this is a string with random\\' apo"
>>> print a.replace("'", "\\'")
this is a string with random\' apo
```Notice the difference between just "a.replace" and "print a.replace".  In Python, the ' character can be escaped inside double-quotes even though it doesn't need to be, so you actually do need two backslashes to make the " \' " appear as it should.

---

### Post by GammaPoint on 2008-06-11
> **ghostdog74]
you don't have to. Before your program plays the file, check to see if there are spaces. if there are, rename it. eg[/QUOTE]

That's a good point.  Although in case it would be a little more work (but not much) since the directory also needs to be renamed. 

[QUOTE=imdano said:**
> Are you sure ```
a.replace("'", "\\'")
```doesn't work?
```
>>> a = "this is a string with random' apo"
>>> print a.replace("'", "\'")
this is a string with random' apo
>>> a.replace("'", "\'")
"this is a string with random' apo"
>>> a.replace("'", "\\'")
"this is a string with random\\' apo"
>>> print a.replace("'", "\\'")
this is a string with random\' apo
```Notice the difference between just "a.replace" and "print a.replace".  In Python, the ' character can be escaped inside double-quotes even though it doesn't need to be, so you actually do need two backslashes to make the " \' " appear as it should.

No, you are right. This does actually work for me.  I made the mistake of doing 'a.replace' instead of 'print a.replace' and so never put it into my actual GUI code because it didn't look like it was going to work. It does work now. Thanks, I can finally go to sleep :)

---

### Post by geirha on 2008-06-11
the os.spawn* functions will let you pass arguments in a list. e.g.
to run the command «mplayer -fs "/home/movies/This is my movie.avi"» you could do:
[php]
import os

args= ['-fs', '/home/movies/This is my movie.avi']
retval= os.spawnvp(os.P_WAIT, 'mplayer', args)
print "mplayer returned with return value", retval
[/php]
This will handle any filenames, and no need for escaping. When in python ...

os.pipe* can also take the arguments from a list, and you'll be able to read stdout and stderr of the command as well as write to its stdin.

---

