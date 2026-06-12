---
title: "Determine AVI file length"
date: 2011-08-27
forum: Programming Talk
---

### Post by tbastian on 2011-08-27
I'm working on small program that corresponds video with points of interest (events) in a completely separate data file. The idea is to have this program take one data file, and one or more video files, and spit out as many shorter video clips as necessary, each corresponding to an event. I plan on using mencoder to actually split the files up, but in the interest of robustness, I need to be able to determine the running time of each AVI file.

Short of setting up an entire gstreamer object for each video, is there any way of doing this?

---

### Post by hakermania on 2011-08-27
Whola!
[http://videotranscoding.wikispaces.com/GetVideoMetadata](http://videotranscoding.wikispaces.com/GetVideoMetadata)
It was easy to find with google btw :)

---

### Post by AlphaLexman on 2011-08-27
> **hakermania said:**
> Whola!
Voila!

---

### Post by tbastian on 2011-08-29
> **hakermania said:**
> Whola!
[http://videotranscoding.wikispaces.com/GetVideoMetadata](http://videotranscoding.wikispaces.com/GetVideoMetadata)
It was easy to find with google btw :)

Thanks, I wasn't really sure what to look for. I wrote a nice function that parses the output and converts the time string to seconds.

---

