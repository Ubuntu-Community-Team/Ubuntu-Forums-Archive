---
title: "Terminal Backslash"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by Holy bible on 2012-05-08
Hi there. I need just explain how does backslash in terminal works... I'm not too professional in Ubuntu neither terminal. Ok so. I worked out how to use it but i still don't know how it works. Gonna put a code here so if somebody knows to use terminal please reply... The code was from sound converting but the backslash is essential.


```
...$ dir
Dj\ Fresh\ -\ Hot\ Right\ Now\ ft.\ Rita\ Ora\ HQ\ (Lyrics\ in\ Description).flv
...$ ffmpeg -i Dj\ Fresh\ -\ Hot\ Right\ Now\ ft.\ Rita\ Ora\ HQ\ (Lyrics\ in\ Description).flv
bash: syntax error near unexpected token `('
```so this was problem but i was trying to solve it and i finally solved it out


```
...$ ffmpeg -i Dj\ Fresh\ -\ Hot\ Right\ Now\ ft.\ Rita\ Ora\ HQ\ \(Lyrics\ in\ Description\).flv
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 21 2011 18:37:21, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, flv, from 'Dj Fresh - Hot Right Now ft. Rita Ora HQ (Lyrics in Description).flv':
  Duration: 00:02:59.91, start: 0.000000, bitrate: 534 kb/s
    Stream #0.0: Video: h264, yuv420p, 854x480, 534 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
At least one output file must be specified
```
As you can see i put '\' befor '(' and ')' ... so... :confused:
My question is why does it works like that.. thanks for replies.
btw. if it helps... I was on Windows partition so i was surprised of the brackets too.

---

### Post by qyot27 on 2012-05-08
The backslash is an escape character, telling the Terminal to interpret the character that comes after it as text instead of the special meaning the character typically has.

You can also use " to avoid backslashes. Ex,
Here\ I\ Am\ Today.mp3
and
"Here I Am Today.mp3"
are referring to the same file.

---

### Post by Holy bible on 2012-05-08
now I understand what backslash does but now i dont understand :D as you writtten some
Hi\ this\ is\ me.mp3
in this you can see that nothing comes after backslashes so why are they used here too.


and also. in the last word me.mp3 ... there is nothing like   -    me/.mp3

so another question why not on the last if on the every another?

---

### Post by drmrgd on 2012-05-08
> **Holy bible said:**
> now I understand what backslash does but now i dont understand :D as you writtten some
Hi\ this\ is\ me.mp3
in this you can see that nothing comes after backslashes so why are they used here too.


and also. in the last word me.mp3 ... there is nothing like   -    me/.mp3

so another question why not on the last if on the every another?

The purpose of the backslash is to tell the system to treat the very next character as text as a previous poster said.  In the case you list, the very next character right after the backslash is a blank space.  If you just put spaces in the name without the slashes like this:

```
Hi this is me.mp3
```

The system would recognize that as 4 different commands or filenames:

1. Hi
2. this
3. is
4 me.mp3

This is not only nonsensical to the system (there is no such command as "Hi", "this", etc.) but also it is not the desired outcome, you are interested in the file with that name.  So, in order to tell the system that you really mean 1 file with spaces in the name, you have to tell the system where the spaces are with the backslash characters.  So, typing:

```
Hi\ this\ is\ me.mp3
```

Tells the system that there is a file called "Hi this is me.mp3" rather than the 4 separate commands or filenames as I mentioned above.

Since there is no problem with the "." or mp3 character in terms of file names (lots of filenames have dots in them), you don't need to escape that character with a backslash.  

I hope that makes sense to you and helps you understand the commandline a little better.

---

### Post by Cheesemill on 2012-05-08
See my reply to a previous question here:
[http://ubuntuforums.org/showpost.php?p=11681159&postcount=3](http://ubuntuforums.org/showpost.php?p=11681159&postcount=3)

---

### Post by ajgreeny on 2012-05-08
As Cheesemill suggests, use the tab key after typing the first few letters of a filename in terminal and it will autocomplete.  You can save huge amounts of time, and the potential for mistakes by doing that.

---

### Post by Holy bible on 2012-05-09
> **drmrgd said:**
> The purpose of the backslash is to tell the system to treat the very next character as text as a previous poster said.  In the case you list, the very next character right after the backslash is a blank space.  If you just put spaces in the name without the slashes like this:

```
Hi this is me.mp3
```The system would recognize that as 4 different commands or filenames:

1. Hi
2. this
3. is
4 me.mp3

This is not only nonsensical to the system (there is no such command as "Hi", "this", etc.) but also it is not the desired outcome, you are interested in the file with that name.  So, in order to tell the system that you really mean 1 file with spaces in the name, you have to tell the system where the spaces are with the backslash characters.  So, typing:

```
Hi\ this\ is\ me.mp3
```Tells the system that there is a file called "Hi this is me.mp3" rather than the 4 separate commands or filenames as I mentioned above.

Since there is no problem with the "." or mp3 character in terms of file names (lots of filenames have dots in them), you don't need to escape that character with a backslash.  

I hope that makes sense to you and helps you understand the commandline a little better.


hmmm... You explained it completely and it gives me a little help to understand the commandline ... but still don't understand that "." and mp3
why i don't need to explain it to computer that it is just a "word" not a command
Got this some fullfilling explanation or it is just that this system works like this :D - that you just dont need to put "\" befor dots ... 
Just this one ... thanks a lot guys for help

---

### Post by drmrgd on 2012-05-09
> **Holy bible said:**
> hmmm... You explained it completely and it gives me a little help to understand the commandline ... but still don't understand that "." and mp3
why i don't need to explain it to computer that it is just a "word" not a command
Got this some fullfilling explanation or it is just that this system works like this :D - that you just dont need to put "\" befor dots ... 
Just this one ... thanks a lot guys for help

The difference between the "." character and a space character in terms of the operating system is it's purpose.  The dot (with a few exceptions that would only confuse the discussion for now) has no special meaning to the system.  The system treats it just like any other character in the filename ("a", "4", etc.).  We use the dot in this sense to give us an idea of what kind of file it is (.mp3 = music file, .txt = text file, etc.).  Windows is much pickier about this sort of thing.  Linux commandline doesn't really care about that information, though.

According to the operating system, the space character does have a special meaning, though.  It tells the system to separate two items, whether they be filenames (example: file1 file2 are two files; file1file2 is one file) or commands.  There are a few other special characters to the operating system that, when one wants to treat them like normal text, also need to be escaped.   A couple common examples are "$", "&", "#", "(", ")".  

In general it's not a good idea to name your files with these characters to keep things simple.  However, if you do (or if you get files from others with these kinds of characters in them), and you want to work with them from the terminal, you'll need to handle them differently.  Two good suggestions from this post are:

1. Use tab completion to autofill the file name so that you're sure you don't make any typos or mistakes (I use this ALL of the time!).

2. Surround the filename in quotes so that the system knows the whole thing belongs to the filename (like "This is the name of a file.txt").

Hope that helps!

---

### Post by Holy bible on 2012-05-16
> **drmrgd said:**
> The difference between the "." character and a space character in terms of the operating system is it's purpose.  The dot (with a few exceptions that would only confuse the discussion for now) has no special meaning to the system.  The system treats it just like any other character in the filename ("a", "4", etc.).  We use the dot in this sense to give us an idea of what kind of file it is (.mp3 = music file, .txt = text file, etc.).  Windows is much pickier about this sort of thing.  Linux commandline doesn't really care about that information, though.

According to the operating system, the space character does have a special meaning, though.  It tells the system to separate two items, whether they be filenames (example: file1 file2 are two files; file1file2 is one file) or commands.  There are a few other special characters to the operating system that, when one wants to treat them like normal text, also need to be escaped.   A couple common examples are "$", "&", "#", "(", ")".  

In general it's not a good idea to name your files with these characters to keep things simple.  However, if you do (or if you get files from others with these kinds of characters in them), and you want to work with them from the terminal, you'll need to handle them differently.  Two good suggestions from this post are:

1. Use tab completion to autofill the file name so that you're sure you don't make any typos or mistakes (I use this ALL of the time!).

2. Surround the filename in quotes so that the system knows the whole thing belongs to the filename (like "This is the name of a file.txt").

Hope that helps!

it seems it helped, just question
"1. Use tab completion to autofill the file name so that you're sure you  don't make any typos or mistakes (I use this ALL of the time!)."

how to perform this?
thanks

---

### Post by zombifier25 on 2012-05-16
For example you need to cd to a folder called "foo bar". To reduce mistakes (because of the space character in "foo bar"), type this:
```
cd foo
```
or even just
```
cd fo
```
then press the Tab key on the keyboard and the terminal will turn it into:
```
cd foo\ bar
```
Neat and simple. Of course this trick works with any folders.

If for some reason you have 2 folders, called "foo bar" and "foo bar2", then pressing the Tab key like above will give you a list of 2 possible candidates for completion: "foo bar" and "foo bar2". Keep pressing Tab to have the terminal cycle between:
```
cd foo\ bar
```
and
```
cd foo\ bar2
```

Is it clear? If it isn't, you can do it yourself. Create 2 folders named foo bar and foo bar2 in your home folder and try it out.

---

### Post by drmrgd on 2012-05-16
> **Holy bible said:**
> it seems it helped, just question
"1. Use tab completion to autofill the file name so that you're sure you  don't make any typos or mistakes (I use this ALL of the time!)."

how to perform this?
thanks

Very simply, you would type in the first few letters of what you want, and then hit the tab key and it should complete the rest of the word, filename, command, etc.  So, for example, if you were trying to change directories in your home directory so that you were in the Downloads directory, you could:

```
cd Dow<hit tab>
```

And it should complete the rest of the word "Download". 

For something so simple it's not a big deal.  However, if you have very long, complicated filenames, or filenames with spaces in them like we were talking about above, it saves the hassle of having to escape all of those space characters.  

One thing to note here is that if there is more than 1 possible hit, autocomplete will not work.  So, for example, if you were in your home directory and typed this:

```
cd Do<hit tab here>
```

Nothing would be filled in.  That is because there are 2 folders in your home directory by default that start with "Do".  So, the system isn't sure which you want.  In that case, if you hit "tab" twice, you should see a list of possible matches.  Then you can add another letter or two to make the match unique and hitting tab should fill the rest in for you.  

Probably the easiest way to understand, though, is to just play around with it yourself.  Remember, you can use autocomplete with just about anything that you type into the terminal.

---

### Post by Holy bible on 2012-05-17
> **drmrgd said:**
> Very simply, you would type in the first few letters of what you want, and then hit the tab key and it should complete the rest of the word, filename, command, etc.  So, for example, if you were trying to change directories in your home directory so that you were in the Downloads directory, you could:

```
cd Dow<hit tab>
```And it should complete the rest of the word "Download". 

For something so simple it's not a big deal.  However, if you have very long, complicated filenames, or filenames with spaces in them like we were talking about above, it saves the hassle of having to escape all of those space characters.  

One thing to note here is that if there is more than 1 possible hit, autocomplete will not work.  So, for example, if you were in your home directory and typed this:

```
cd Do<hit tab here>
```Nothing would be filled in.  That is because there are 2 folders in your home directory by default that start with "Do".  So, the system isn't sure which you want.  In that case, if you hit "tab" twice, you should see a list of possible matches.  Then you can add another letter or two to make the match unique and hitting tab should fill the rest in for you.  

Probably the easiest way to understand, though, is to just play around with it yourself.  Remember, you can use autocomplete with just about anything that you type into the terminal.

So guys. I think that by now it is solved and clear just with that dot. But it is not problem i'll just take it like a fact and that it just is not needed to be escaped by UNIX. Thank you everybody ;)

---

### Post by Holy bible on 2012-05-17
Damnit NO! It can't be unsolved :D:D:D. Another problem there with "/" . I tried what you said to do, and another problem there. As you said that if i go to home folder and do the
```
cd Do<press Tab twice>
Documents/ Downloads/ 
```
you see?. Documents/ Downloads/ 
What is this? I know that this time Im really going upstairs by your nerves but :D. I just like Terminal and its mysteries but i want to know that mysteries :O :popcorn: please dont hate me :D

---

### Post by cholericfun on 2012-05-17
calm down, its just kindly telling you that they are directories as opposed to files

the / just comes from the unix directory seperation as in home/user/Desktop

theres also a second advantage to that:
say i want to go UP one directory and get a file there:
with relative file adressing this would be   
../fantasticfile
using autocomplete:
..<tab>f<tab>
done (if its the only file with an f in that directory)

---

### Post by Holy bible on 2012-05-18
> **zombifier25 said:**
> For example you need to cd to a folder called "foo bar". To reduce mistakes (because of the space character in "foo bar"), type this:
```
cd foo
```or even just
```
cd fo
```then press the Tab key on the keyboard and the terminal will turn it into:
```
cd foo\ bar
```Neat and simple. Of course this trick works with any folders.

If for some reason you have 2 folders, called "foo bar" and "foo bar2", then pressing the Tab key like above will give you a list of 2 possible candidates for completion: "foo bar" and "foo bar2". Keep pressing Tab to have the terminal cycle between:
```
cd foo\ bar
```and
```
cd foo\ bar2
```Is it clear? If it isn't, you can do it yourself. Create 2 folders named foo bar and foo bar2 in your home folder and try it out.

bytheway bro, it's not cycling. It just show. it is a problem of mine Linux ? or how can i make terminal cycle between this two things?

---

### Post by Vaphell on 2012-05-18
my terminal doesn't cycle either
the terminal showing you currently matching options so you can solve the ambiguosity with additional char or two is enough.

i think cycling would be annoying - no visual feedback at a glance what choices you exactly have and what if you had dozen matching files? cycle one item too far and you got a lot of tabbing to do to get to the same spot.

---

### Post by zombifier25 on 2012-05-19
> **Vaphell said:**
> my terminal doesn't cycle either
the terminal showing you currently matching options so you can solve the ambiguosity with additional char or two is enough.

i think cycling would be annoying - no visual feedback at a glance what choices you exactly have and what if you had dozen matching files? cycle one item too far and you got a lot of tabbing to do to get to the same spot.

Sorry, I was using zsh. zsh shows you the choice AND cycle between them, not or. Pretty neat. Like this:

```
cd Documents/
Documents/  Downloads/

```
and
```
cd Downloads/
Documents/  Downloads/

```

---

### Post by Holy bible on 2012-05-19
So now we work with clean hands. Everything is desinfected and we found cycling problem. But i still need somebody who can fullfillingly explain me the SLASH no more Backslash because this was solved but now that SLASH "/" ...
 
 
As you see this 
```
Documents/ Downloads/
```

why is in this situation SLASH needed... thanks

---

### Post by CharlesA on 2012-05-19
It just tells you those are directories.

---

### Post by Holy bible on 2012-05-19
> **CharlesA said:**
> It just tells you those are directories.

so you say that "/" has the only meaning to say User that " something/ "
is directory? or it has also some other functions?if yes just name them

---

### Post by CharlesA on 2012-05-19
This might help:
[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

That would be a path:

/home/user/Documents

home, user and Documents are all directories and the full path to Documents is /home/user/Documents

---

