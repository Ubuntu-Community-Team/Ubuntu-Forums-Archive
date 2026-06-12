---
title: "ffmpeg and %03d"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by gladgrind on 2013-01-07
I am trying to convert a string of jpgs to a movie.
The jpgs are in a folder and are in sequence:
1image.jpg
2image.jpg
.
.
421image.jpg


The instructions I have found are something like this:

ffmpeg -r 25 -qscale 2 -i %03d.image.jpg output.mp4

where %03d is substitued for the number.

When I run it, it says it can not find the file.

I deleted 1image.jpg through 99image.jpg to see if it had to have a 3-digit number, but get the same message.

I have the feeling I am missing something simple, but can not figure out what it might be. Any ideas?

---

### Post by ajgreeny on 2013-01-07
Are you using ffmpeg in order to learn about how to do things in command line?

You can easily and quickly create a movie from jpg or other still pics with imagination from the repos, if you would prefer a GUI.

---

### Post by gladgrind on 2013-01-07
> **ajgreeny said:**
> Are you using ffmpeg in order to learn about how to do things in command line?
No, I was using it because I saw a couple of posts that said it could be used to make a movie from a set of .jpg files.

> You can easily and quickly create a movie from jpg or other still pics with imagination from the repos, if you would prefer a GUI.Thanks for the reference. 

It turns out I found an old script that uses mencoder to do the creation of the .avi file.

---

### Post by FakeOutdoorsman on 2013-01-07
> **gladgrind said:**
> I am trying to convert a string of jpgs to a movie.
The jpgs are in a folder and are in sequence:
```
1image.jpg
2image.jpg
.
.
421image.jpg
```


The instructions I have found are something like this:

```
ffmpeg -r 25 -qscale 2 -i %03d.image.jpg output.mp4
```

You list images as 1image.jpg, etc, but your command has an extra period in the file name: "%03d.image.jpg".

Also, "-qscale 2" is not an input option. Options before "-i" are generally applied to the input.

---

### Post by gladgrind on 2013-01-08
> **FakeOutdoorsman said:**
> You list images as 1image.jpg, etc, but your command has an extra period in the file name: "%03d.image.jpg".

Thanks, it looks like that was the simple thing I overlooked.

I have it working with mencoder, however, so I will leave it at that.

---

