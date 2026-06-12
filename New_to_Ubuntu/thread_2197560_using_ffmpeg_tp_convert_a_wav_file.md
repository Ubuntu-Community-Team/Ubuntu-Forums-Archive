---
title: "using ffmpeg tp convert a wav file"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by YDardeer on 2014-01-04
Hi,

I have a wav file and I need to convert to another wav file but with the following format:

[COLOR=#000000][FONT=arial]G.711 U-law, 8 kHz, 8 bit, Mono

I would really appreciate it if someone can post a command to do that.
Thanks[/FONT][/COLOR]

---

### Post by FakeOutdoorsman on 2014-01-04
```
$ ffmpeg -i input.wav -codec:a pcm_mulaw -ar 8000 -ac 1 output.wav
```

```
$ ffmpeg -encoders | grep 711
...
 A..... pcm_alaw             PCM A-law / G.711 A-law
 A..... pcm_mulaw            PCM mu-law / G.711 mu-law
```

8-but unsigned appears to be unsupported by the encoder pcm_mulaw. Otherwise you could use [-sample_fmt](http://ffmpeg.org/ffmpeg.html#Audio-Options) to change the audio sample format or use an encoder that uses a specific sample format.

```
$ ffmpeg -h encoder=pcm_mulaw
...
Encoder pcm_mulaw [PCM mu-law / G.711 mu-law]:
    Threading capabilities: no
    Supported sample formats: s16
```

I don't know if any of this will work with the fake "ffmpeg" in the repository.

---

