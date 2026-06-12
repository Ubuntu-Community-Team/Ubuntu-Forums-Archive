---
title: "Joining files"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by blokefromaus on 2008-10-11
Gday , I am having trouble joining movie files .
I am using ¨mencoder¨ ? , but it keeps saying can´t find file/ failed to open file/ cannot open file/device .
I´ve done searches in the forums , but can´t find an answer , as mencoder seems to work for everyone else .
Thanks for your help .

---

### Post by bodhi.zazen on 2008-10-11
I have no idea about that app.

cant you just :

```
cat file2 >> file1
```

---

### Post by aeiah on 2008-10-11
cat doesnt work too well with movie files, it usually messes up the audio and such, or doesnt work at all.

you're on the right track with mencoder. this works for me:

```

mencoder -forceidx -oac copy -ovc copy -o output.avi movie_cd1.avi movie_cd2.avi

```

the -forceidx flag usually gets rid of any audio sync issues that arise when merging two video files.

but your error seems more like you arent specifying the paths correctly. what is the exact command you issue, and what is the error message it throws up?

---

### Post by bodhi.zazen on 2008-10-12
> **aeiah said:**
> cat doesnt work too well with movie files, it usually messes up the audio and such, or doesnt work at all.

Interesting, go figure. Thanks for the information.

---

### Post by blokefromaus on 2008-10-12
I just tried the cat command , & it said ¨ no such file or directory ¨.

aeiah , I type in the command just as you have it , & then I replace output.avi movie_cd1.avi movie_cd2.avi 
It says File not found
        Failed to open file
        Cannot open file/device

---

### Post by unutbu on 2008-10-12
Suppose the avi files are in a directory in your home account called 'movies'. Then type
```

cd ~/movies   # the cd command changes the directory
mencoder -forceidx -oac copy -ovc copy -o output.avi movie_cd1.avi movie_cd2.avi
```

Alternatively, you could specify the paths in the mencoder command:
```

mencoder -forceidx -oac copy -ovc copy -o ~/movies/output.avi ~/movies/movie_cd1.avi ~/movies/movie_cd2.avi
```

There is also a GUI program called avidemux which can join avi's together. You simply File>Open one avi, and then File>Append the next. Then click the save button.

To install the program you can use Synaptic or type
```

sudo apt-get install avidemux
```

---

### Post by MrWES on 2008-10-12
How about using avimerge?

man avimerge

I've used both, avimerge and avisplit, nice form the CLI

Bill

---

### Post by unutbu on 2008-10-12
avimerge and avisplit are in the official repos as part of the transcode package.

Thanks MrWES, I didn't know about these programs.

---

### Post by MrWES on 2008-10-12
Your welcome -- it's overwhelming at times...so many options in Linux; even for a pro :)

---

### Post by blokefromaus on 2008-10-13
> **unutbu said:**
> Suppose the avi files are in a directory in your home account called 'movies'. Then type
```

cd ~/movies   # the cd command changes the directory
mencoder -forceidx -oac copy -ovc copy -o output.avi movie_cd1.avi movie_cd2.avi
```

Alternatively, you could specify the paths in the mencoder command:
```

mencoder -forceidx -oac copy -ovc copy -o ~/movies/output.avi ~/movies/movie_cd1.avi ~/movies/movie_cd2.avi
```

There is also a GUI program called avidemux which can join avi's together. You simply File>Open one avi, and then File>Append the next. Then click the save button.

To install the program you can use Synaptic or type
```

sudo apt-get install avidemux
```

I installed avidemux & it is trying to work . It seems that when I have downloaded the files they are ending up in different formats . The first file I download is fine , but the second file is either ¨application/x-extension-002¨ , or ¨ ocetet-stream¨ . Ivé tried downloading further files & they always end the same way . Any ideas why , or how to solve this ?
Thanks .

---

