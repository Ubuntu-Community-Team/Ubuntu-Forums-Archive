---
title: "Help with cat command"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by Inisfad on 2011-12-29
I have a number of 5 minute videos that I am combining to one longer video, and am using the cat command to do this, as I read that this would be alot faster.  Originally, avidemux advised, when I started doing it this way, that it would take about 7 hours to do.  Anyway, my cat command is running, apparently, but how do I know if its doing anything?  I have tried to bring up processes in another terminal, but it doesn't show that first terminal is running.  In my original terminal, it is not showing the '$', just a flashing cursor, so it appears to be doing something.  Is there any way of checking the progress of my project?  Thanks!

---

### Post by CharlesA on 2011-12-29
If you aren't back at a prompt, then the command is running. How long it takes depends on how big the file is and how fast your machine is.

---

### Post by lisati on 2011-12-29
It's possible that the cat command is waiting for user input.

IMO it would be better to use a video editor to combine clips, because depending on the format of the original files, the output file might not work too well if you simply concatenate the files.

---

### Post by Inisfad on 2011-12-29
Thanks for the info.  I already converted all the files to mpg, so they are all encoded the same.  As I don't have the prompt, I guess its running.  I was just hoping that there was some way to see if it was.  It does not seem to appear on system monitor or top command, etc.

---

### Post by Sempa on 2011-12-29
> **Inisfad said:**
> Thanks for the info.  I already converted all the files to mpg, so they are all encoded the same.

I don't know how you'd go about finding out whether it's running or not, but I think what lisati was getting at is that, even if the videos are in the same format, you can't glue them together like that most of the time.

---

### Post by Inisfad on 2011-12-29
Ah, ok.  I'm pretty much new at this, and in reading about what I wanted to do on the internet, I found a number of sites that actually recommended the cat command over programs like avidemux, etc., stating it was faster if you had already converted your files, and just wanted to attach them.  ???

---

### Post by marbertone on 2011-12-29
Suppose you have four text files (a, b, c, d) and you want to create a new file, e, which containes the four files concatenated (a->b->c->d). All you have to do is:
```
cat a b c d >> e
```
>> is used to append. I think in this case also '>' shall be good.
I don't know if it'll work with videos but...just try! ;)
Cheers,
Mario Alberto :popcorn:

---

### Post by CharlesA on 2011-12-29
You'd need to use ">>" since you are appending files.

---

### Post by 1clue on 2011-12-29
Open a new terminal.  Cd to that directory.  ls -al.  If the number of bytes gets bigger then it's doing something.

---

### Post by Inisfad on 2011-12-30
Thanks for all the info.  Actually, in the end, after letting it run for about 5 hours, I just shut it down - there was no query that indicated that terminal was doing anything.  But I really don't understand the whole concept - I have 20 video clips that have all been encoded in mpeg so that they will play on my DVD player.  All I want to do is to stick them together - have one run after the other, rather than as separate 'chapters' on the DVD that I will burn.  In the video program that I have (Avidemux, Pitivi, etc), when you are rendering the project, it is going through what appears to be each frame.  Since I have already encoded it, is this necessary?  Is there not a program that will just 'paste' one clip after another? This is what I read that the 'cat' command would do.  I am running Pitivi now - for 20 minutes worth of video, it says it will take about 3 hours to 'render' it.  Eck.  Is there another way??

---

### Post by NilPointer on 2011-12-30
Is it possible to join videos with cat, anyway? It can be used to join n files, not join video data. Video files have headers and actual video data (unless it's raw headerless uncompressed format and all files have same resolution, etc, then it might work, yes). I guess if you join them that way, it'll result in either a corrupted file, or it will play like first file, to which other were appended.

So, I think you'd better use video editor.

---

### Post by Inisfad on 2011-12-30
Ah, it sure is possible to combine the videos.  I decided to do my 20 videos in parts, rather than all 20 together.  I did "cat abc.mpg def.mpg ghi.mpg > alphabet.mpg." for the first batch.  Then to append more, keeping alphabet.mpg intact, I did "jkl.mpg mno.mpg pqr.mpg >> alphabet.mpg" and so on, until all of my files were in alphabet.mpg.  And I must say that this took about TEN SECONDS to do.  It was really cool.  Now, apparently the problem is with the headers, as although the entire file shows the gb of the entire film, it will only play the first 'abc' file, due to the headers.  So, now I am investigating 'mencoder' which will apparently rebuild the header file.  Will report back!!  Must say this is FAR FAR easier than going through the video programs to render.  I had originally used ffmpeg to encode all the videos the way I wanted them, so I couldn't see why I had to wait for Pitivi, etc., to encode them again.  So far, this has been an incredibly fast process......

---

### Post by The Cog on 2011-12-30
> **CharlesA said:**
> You'd need to use ">>" since you are appending files.
Sorry, but I disagree. the command
**cat a b c d**
will concatenate files a,b,c,d by reading them in order and writing to stdout. What comes out of stdout is a single concatenated stream, so using **>** to redirect that to your output file will work fine.

The problem with using **>>** in this situation is that if you do the command again, you will then double the length of the output file rather than just rewriting it.

I still have my doubts over whether you can succesfully join video files this way, but maybe it will work with some formats.

@Inisfad:
If cat hangs for that long, it is almost certainly waiting for input from the keyboard. What was the exact command that you used?

---

### Post by NilPointer on 2011-12-30
I think mencoder have option to copy audio/video stream when joining, if you encoded all videos with same settings. Then it should make single file with proper header and video data.

---

### Post by Inisfad on 2011-12-30
Whoa.  Done and dusted.  After combining all my videos into one final video, as above, called alphabet.mpg, due to the header problem, although the file was 1.2gb, only the first portion (5 minutes) would play.  Now, for the mencoder command: &quot;mencoder -forceidx -oac copy -ovc copy alphabet.mpg -o alphabet_final.mpg&quot; Now, the video shows as 'alphbet_final.mpg in my file system, shows as 1.2gb, and is 1 hour and 20 minutes long.  This took all of about 5 minutes to do (and about 12 hours worth of studying on the internet)!! Hope this helps someone, as, doing it this way, saved HOURS of time.  Now.....I can watch 'March of the Wooden Soldiers' anytime I want, even when the TV stations decide it should no longer be shown as a Christmas movie!  Ha!!

---

### Post by 1clue on 2011-12-30
I have successfully combined video fragments with cat.

cat frag1.mpg > big.mp4
cat frag2.mpg >> big.mp4
...
cat fragn.mpg >> big.mp4

It plays the whole thing just fine. I did NOT try to change format on the fragments, but the entire video will play.

---

### Post by Inisfad on 2011-12-31
I had to change the format on the fragments, and some were flv, some were mpg.  First got the whole thing into mpg, and then found that my dvd player doesn't recognize that code.  So had to use ffmpeg to change the entire file to avi.  Burned to a DVD and then was able to watch it.  Regarding the issue of > or >>, I had first tried to combine all 20 segments using the cat command, and this is where I found that terminal just froze there, for hours.  So I decided to do this in 5 segment increments.  When combining the first 5 segments to one larger file, you use the > command.  But then, when you are appending more files to that larger file, you use >>.  It was so simple, in the end.....

---

### Post by BlinkinCat on 2011-12-31
Mark as solved using thread tools at top of page if you are satisfied with result - :)

---

