---
title: "Creating DVD's with subtitles"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by speedzor on 2008-08-27
hi,

I want to put the downloaded movies onto a DVD and add subs to it.
What is the best program for this?

---

### Post by brian_p on 2008-08-27
> **speedzor said:**
> hi,

I want to put the downloaded movies onto a DVD and add subs to it.
What is the best program for this?

spumux. It's in the dvdauthor package.

---

### Post by speedzor on 2008-08-27
I've downloaded and installed it, but when I try to use it, it only gives a '<' as return.

I've entered the following:
```

spumux -P Transformers.subs.nl < /video's/transformers/Transformers.avi > Transfilm.avi

```

what am I doing wrong?

---

### Post by speedzor on 2008-08-27
and when using the following command, it gives this error:

```

jeroen@jeroen-laptop:~$ spumux -P /video's/transformers/Transformers.subs.nl.srt < /video's/transformers/Transformers.avi > Transfilm.avi


DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

Segmentation fault
jeroen@jeroen-laptop:~$ 

```

Can I solve this?
If not, alternatives?

---

### Post by brian_p on 2008-08-27
> **speedzor said:**
> 

what am I doing wrong?

Change video's to videos. Two of ' has a special meaning for the shell. A single one confuses it.

---

### Post by brian_p on 2008-08-27
> **speedzor said:**
> 
Can I solve this?


spumux uses mpeg2 streams. avi is a container format.

---

### Post by speedzor on 2008-08-27
So I'll have to convert them I guess?

btw, when using no ', it gives this:

```

jeroen@jeroen-laptop:~$ spumux -P /videos/transformers/Transformers.subs.nl.srt < /videos/transformers/Transformers.avi > Transfilm.avi
bash: /videos/transformers/Transformers.avi: No such file or directory
jeroen@jeroen-laptop:~$ 

```

next question: any good avi to mpeg2 converter? :)

---

### Post by northern lights on 2008-08-27
> **speedzor said:**
> ```

jeroen@jeroen-laptop:~$ spumux -P /videos/transformers/Transformers.subs.nl.srt < /videos/transformers/Transformers.avi > Transfilm.avi
bash: /videos/transformers/Transformers.avi: No such file or directory
jeroen@jeroen-laptop:~$ 

```
If the directory was/is indeed called *video's* you also have to change the directory name to *videos*...

---

### Post by speedzor on 2008-08-27
I did, but still it gives the error...

---

### Post by brian_p on 2008-08-27
> **speedzor said:**
> 

next question: any good avi to mpeg2 converter? :)

```
ffmpeg -i input.avi -target pal-dvd out.mpg
```

Or -target ntsc-dvd

---

### Post by brian_p on 2008-08-27
> **speedzor said:**
> I did, but still it gives the error...

Is the videos directory in $HOME? It should be. Then 

```
~/videos/transformers/Transformers.avi

```
would be correct.

---

