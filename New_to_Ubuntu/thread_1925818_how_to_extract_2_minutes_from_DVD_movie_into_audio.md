---
title: "how to extract 2 minutes from DVD movie into audio file (mp3)"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by hanzj on 2012-02-15
Hello, we  have a regular DVD movie in my computer. How can we extract two minutes from the DVD and turn it into an audio file **using VLC**?


From 2:20:23 to 2:22:45

---

### Post by ron999 on 2012-02-15
> **hanzj said:**
> Hello, we  have a regular DVD movie in my computer.
What format is this "regular DVD movie"?

---

### Post by hanzj on 2012-02-15
hmmm... not sure. the regular format that DVDs come in.

---

### Post by dylan07 on 2012-04-09
You can use a DVD ripping program, and rip the DVD and then use a video editor and cut out the clip you want, and then convert it to DVD.

You might want to check out Handbrake.

---

### Post by flurospar on 2012-04-09
Download ffmpeg, with the restricted extras if you need them:
```

sudo apt-get install ffmpeg ubuntu-restricted-extras

```Convert the movie to an audio file (MP3, OGG, whatever):
```

ffmpeg -i movie.mpeg audio.mp3

```Extract the 2 mins:
```

ffmpeg -ss 00:02:00.00 -t 120 -i audio.mp3 -acodec copy audio-new.mp3

```

---

### Post by dylan07 on 2012-04-09
> **flurospar said:**
> Download ffmpeg, with the restricted extras if you need them:
```

sudo apt-get install ffmpeg ubuntu-restricted-extras

```Convert the movie to an audio file (MP3, OGG, whatever):
```

ffmpeg -i movie.mpeg audio.mp3

```Extract the 2 mins:
```

ffmpeg -ss 00:02:00.00 -t 120 -i audio.mp3 -acodec copy audio-new.mp3

```

Very impressive! Well done! How do you pick the 2 minute segment though?

---

### Post by flurospar on 2012-04-09
In the following:
```

ffmpeg -ss 00:02:00.00 -t 120 -i audio.mp3 -acodec copy audio-new.mp3

```

"-ss 00:02:00.00" tells ffmpeg where to start from. In my example, "00:02:00.00" tells ffmpeg that it should start extracting the audio segment 2 minutes after the file starts. You can set this to "00:00:00.00" if you need it from the beginning.

"-t 120" tells ffmpeg to extract 120 seconds of the audio from this point we specified.

Note that the order of the options must be preserved. You can't change the options as you can do with other programs, because ffmpeg is sensitive to the positions of the options.

---

### Post by dylan07 on 2012-04-09
> **flurospar said:**
> In the following:
```

ffmpeg -ss 00:02:00.00 -t 120 -i audio.mp3 -acodec copy audio-new.mp3

```"-ss 00:02:00.00" tells ffmpeg where to start from. In my example, "00:02:00.00" tells ffmpeg that it should start extracting the audio segment 2 minutes after the file starts. You can set this to "00:00:00.00" if you need it from the beginning.

"-t 120" tells ffmpeg to extract 120 seconds of the audio from this point we specified.

Note that the order of the options must be preserved. You can't change the options as you can do with other programs, because ffmpeg is sensitive to the positions of the options.

Very neat! I will use that! Thank you for explaining!
(Is it possible to give +rep on this forum?)

---

### Post by bolkonski on 2012-04-11
Hi Guys,
How can I modify this to rip the audio of a SVCD?
Thanks for your help!
Bolkonski

---

### Post by hanzj on 2012-04-11
> **Bennettt said:**
> Try to use some apps which can help you to extract audio.

Dear Bennettt,
The advice in your post was tautological to my question.
(Me: How can I extract audio?
You/Bennettt: Get an app that can extract audio)
 
Nevertheless, thanks for inadvertently bumping my post back to where helpful commenters could see it.

---

### Post by bab1 on 2012-04-11
> **hanzj said:**
> Dear Bennettt,
The advice in your post was tautological to my question.
Does that mean your <whatever> is bigger that theirs is?> 
(Me: How can I extract audio?
You/Bennettt: Get an app that can extract audio)
 
Nevertheless, thanks for inadvertently bumping my post back to where helpful commenters could see it.

I don't see it as inadvertently put at all.  Maybe a bit errant, but still done with intention.  A backwards thanks in no thanks at all.

With the wide range of experience, age and education, you should be more tolerant of others.  ;-)

---

### Post by s1baker on 2012-04-11
You might look at Audacity ( Completely open source )

[http://audacity.sourceforge.net/]("http://audacity.sourceforge.net/")


Usually, any audio that comes from the computer can be copied.

---

