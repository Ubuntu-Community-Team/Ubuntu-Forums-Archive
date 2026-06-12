---
title: "wav file slicing (python)"
date: 2011-11-17
forum: Programming Talk
---

### Post by schauerlich on 2011-11-17
I'm looking for a way to take slices out of a wav file in python. That is, for some wav file f, extract all of the audio from t=x to t=y and write it to a new file. Googling around, there doesn't seem to be any off-the-shelf solutions, and I'm not opposed to rolling my own implementation (it's not too hard), but I'd rather not reinvent the wheel and inevitably run into a bunch of issues someone else has already dealt with.

I've included the code I'm currently using - feel free to critique if nothing else. It uses wave.py (easy_install wave if you have setuptools)

```
import wave

def slice(infile, outfilename, start_ms, end_ms):
    width = infile.getsampwidth()
    rate = infile.getframerate()
    fpms = rate / 1000 # frames per ms
    length = (end_ms - start_ms) * fpms
    start_index = start_ms * fpms

    out = wave.open(outfilename, "w")
    out.setparams((infile.getnchannels(), width, rate, length, infile.getcomptype(), infile.getcompname()))
    
    infile.rewind()
    anchor = infile.tell()
    infile.setpos(anchor + start_index)
    out.writeframes(infile.readframes(length))
    

if __name__ == "__main__":
    slice(wave.open("onetwothree.wav", "r"), "out.wav", 500, 3000)
```

---

### Post by Bachstelze on 2011-11-17
y u no use ffmpeg like everyone else?

---

### Post by schauerlich on 2011-11-17
> **Bachstelze said:**
> y u no use ffmpeg like everyone else?

The reason I'm asking here is because I don't know much about this stuff.

This is part of a larger project that's written in python. Is there a decent python wrapper for ffmpeg? Can you point me towards their documentation?

---

### Post by Bachstelze on 2011-11-17
Not that I know of. There seems to be

[http://code.google.com/p/pyffmpeg/](http://code.google.com/p/pyffmpeg/)

but it's not very active. Besides, what you're doing looks fine to me, it would be odd to do a specific Python thing instead of using ffmpeg if it was just about cutting WAV files, but if it's part of a larger project it certainly makes sense.

---

