---
title: "MKV to AVI"
date: 2016-01-01
forum: New to Ubuntu
---

### Post by nevermore17 on 2016-01-01
Hi!

I want to convert .MKV to .AVI.
Of course I want to keep good quality of audio and video.
How can I do it in the fastest way?

Greetings from Poland!

---

### Post by nevermore17 on 2016-01-01
IMPORTANT:
And also I want to keep built-in subtitles!

---

### Post by Herdo on 2016-01-01
If the subtitles are hardcoded, then it won't matter.

Some good info here:

[http://ubuntuforums.org/showthread.php?t=1780248](http://ubuntuforums.org/showthread.php?t=1780248)

---

### Post by sandyd on 2016-01-01
If you want a GUI option, install winff.

Start up Winff, and set "Convert to:" to AVI, and the preset to MS compatible AVI. Then, you can add any files you want to add.

If you want to control the size of the output/etc, go to Options -> Additional Options, and you will have additional tabs to adjust video conversion settings/etc.

---

### Post by cafeledavid on 2016-01-01
i was about to say handbrake but i noticed that the linux version only converts to mkv.. not sure why since its a great program in windows. i tried to use winff but i want to convert flv to mp4 but t kept telling me invalid file which i know was not true so i am currently using emicsoft convertor made for windows but i am using wine to run it and it runs great however in preview mode while converting it shows the screen split, i thought the program didnt work but i checked the mp4 it made and was fine. it has tons of video converting options for different platforms such as xbox, ps3, phones etc - not free though

---

### Post by SeijiSensei on 2016-01-02
If you're comfortable with the command line use ffmpeg or even the hoary [mencoder]("http://www.linuxforums.org/forum/gaming-multimedia-entertainment/192044-ffmpeg-convert-mkv-avi-file.html").  Make sure you use two-pass encoding for the best quality.  However,

1) AVI doesn't support "soft" subtitles as are often found in Matroska files.  You'll need to convert them to "hard" subs and burn them into the image.  See this: [https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo](https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo)

2) AVI was created at a time when the dominant codecs were MPEG4 and its variants like DivX and its open cousin XviD.  You will not get the same quality with XviD that you see with H.264 encodings without creating substantially larger files.

---

### Post by FakeOutdoorsman on 2016-01-02
Why do you need AVI? As SeijiSensei mentioned it is quite a dated container format.

Can you show info the about your input and ffmpeg build?
```
ffmpeg -i input.mkv
```

---

