---
title: "Converting RM to MP3 file format in Ubuntu"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by shailendra on 2008-07-19
Hello People,

I have some real player RM files and I want to convert them to MP3 format so that I can play the songs in my MP3 player.

Please let me know if there is any tool for Ubuntu/Linux which I can use.

Any help will be highly appreciated.

Thanks in advance.

---

### Post by nothingspecial on 2008-07-19
```
mencoder input_file.rm -ovc frameno -oac mp3lame -of rawaudio -lameopts cbr:br=128 -o output_file.mp3
```

From this -

[http://stream-recorder.com/forum/converting-captured-rm-stream-mp3-wav-using-t101.html?t=101](http://stream-recorder.com/forum/converting-captured-rm-stream-mp3-wav-using-t101.html?t=101)

---

