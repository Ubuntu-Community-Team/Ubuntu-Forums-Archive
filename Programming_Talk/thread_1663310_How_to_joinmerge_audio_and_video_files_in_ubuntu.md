---
title: "How to join/merge audio and video files in ubuntu?"
date: 2011-01-09
forum: Programming Talk
---

### Post by leon.vitanos on 2011-01-09
This commands doesn't work for me.. 
```
cat file1 file2 file3 > joinedfile
```

I found also avimerge, transcode and mencoder but you must install them and i want to avoid this .. so is there any package installed that with a command it joins/merges audio and video files? :-k

---

### Post by leon.vitanos on 2011-01-09
With mencoder it works just fine! 

```
mencoder -oac copy -ovc copy -idx -o output.avi video1.avi video2.avi video3.avi
```

But is mencoder the best one ( the fastest, more reliable )? :-k

---

### Post by slavik on 2011-01-09
mencoder is a good option. you won't find something inherently "better"

---

### Post by leon.vitanos on 2011-02-05
Guys i am ok on how to join videos.. But i do not know how to join audio files.. Any ideas?

---

### Post by worksofcraft on 2011-02-05
> **Bong.Da.City said:**
> Guys i am ok on how to join videos.. But i do not know how to join audio files.. Any ideas?

Did you try [ffmpeg]("http://www.ffmpeg.org/") ?

---

### Post by leon.vitanos on 2011-02-06
> **worksofcraft said:**
> Did you try [ffmpeg]("http://www.ffmpeg.org/") ?
Yes i know ffmpeg... i am using ffmpeq in my program.. but what is the command to join/merge audio files with ffmpeg?

---

### Post by VernonA on 2011-02-07
To tell ffmpeg to use multiple files, you need to use the 'concat' protocol when specifying the input parameter. For example, to say that input should come from file1.avi, then file2.avi, then file3.avi, you would write a cmd line that started:
```
    ffmpeg -i concat:file1.avi\|file2.avi\|file3.avi   ...

```(The file names are separated by the pipe char, which needs to be escaped with the backslash to prevent it being interpreted by the command shell.)

---

