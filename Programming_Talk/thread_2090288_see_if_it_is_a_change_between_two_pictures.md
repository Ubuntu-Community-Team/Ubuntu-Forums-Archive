---
title: "see if it is a change between two pictures"
date: 2012-12-01
forum: Programming Talk
---

### Post by cazz on 2012-12-01
Hi I wonder over one thing.

It is maybe easy to see the different between two pictures with a script or a terminal software but how does it work.

I mean if the one picture is taken in the morning with daylight and one is taken in the night and it is dark.
Why does it not send the alarm.


Why I wonder is that I'm curious if I can create a basic alarm system that read a image and see if it is any change from the last picture it have taken and if it is any change it send me a e-mail.

---

### Post by sudodus on 2012-12-01
It is easy to detect if the pictures are exactly the same or if there is some difference. Just check if the files are the same or not. But this will not work, because you must allow for a certain level and type of variation. And then it will be an advanced science, automatic image analysis.

---

### Post by Lux Perpetua on 2012-12-01
> **cazz said:**
> Why I wonder is that I'm curious if I can create a basic alarm system that read a image and see if it is any change from the last picture it have taken and if it is any change it send me a e-mail.I'm responding to the question I think you meant to ask, which is how to detect if a new object has entered the scene (for example).  In general, this is a nontrivial computer vision problem, which I'm not an expert on.  However, if the camera is stationary relative to the surroundings, I think it becomes a lot easier.  Maybe you could try comparing the pixel values in the two images and raising a flag if the sum of the absolute differences is large enough.  This could still run into trouble if lighting can suddenly change (for example, if part of the scene is sunlit), or if the camera isn't completely still.

---

### Post by Vaphell on 2012-12-01
experiment with imagemagick

[http://www.imagemagick.org/script/compare.php](http://www.imagemagick.org/script/compare.php)
[http://fuzz-box.blogspot.com/2012/07/how-to-batch-identify-similar-images-in.html](http://fuzz-box.blogspot.com/2012/07/how-to-batch-identify-similar-images-in.html)

---

### Post by mdurham on 2012-12-01
There is a program in the repo that will probably do what you want, it's name is "motion". Take a look.

---

### Post by cazz on 2012-12-02
> **Vaphell said:**
> experiment with imagemagick

[http://www.imagemagick.org/script/compare.php](http://www.imagemagick.org/script/compare.php)
[http://fuzz-box.blogspot.com/2012/07/how-to-batch-identify-similar-images-in.html](http://fuzz-box.blogspot.com/2012/07/how-to-batch-identify-similar-images-in.html)

Ahh thanks, going to look at that.

---

### Post by cazz on 2012-12-02
> **mdurham said:**
> There is a program in the repo that will probably do what you want, it's name is "motion". Take a look.

Well yes I know, I was just curious if I can build my own system

---

### Post by cazz on 2012-12-04
Hi again :)

Now I have look at the ImageMagick and is look like it is a good program to use.

But it is something I do not understand.

I have use this code 

```
compare -metric ae -fuzz '10%' pic1.jpg pic2.jpg null
```

it give me a result 

117

I guess that is a low number because the two picture is just one minute between the take.

---

### Post by Vaphell on 2012-12-04
when pics are too dissimilar you get error message and exit code 1. Success is 0.

```
compare ...
if [ $? -ne 0 ]
then
  echo error
else
  echo ok
fi
```

---

### Post by PaulM1985 on 2012-12-04
You could test with your own custom images, like a fully red png file compared against a fully blue png.  I would imagine that would give you a huge difference.

You could then find out what a reasonable tolerance would be to have.

Paul

---

### Post by cazz on 2012-12-04
Ahh ok

Going to make a script that save the result to see how much it going to change for a day

---

### Post by sudodus on 2012-12-04
I'm looking forward to your results with [imagemagick] compare :-)

I use imagemagick, but for other purposes, mainly file resizing and conversions.

---

### Post by The Cog on 2012-12-04
If you want to compare two images taken of the same scene but very different lighting, e.g. day and night, I think you will probably have to do some edge detection and then compare the two sets of edges. I'm sure that imagemagick will have some edge-detection capability.

---

### Post by cazz on 2012-12-04
mm right now I use it to create thumbnail :)


But I have one basic problem :redface:

I trying to get the result in a variable.

I was thinking about create a log and save two variable in a textfile

```

#!/bin/bash

VALUE=$(<temp.txt)


SVAREN=$(compare -metric ae -fuzz '10%' viewcam.jpg /old/$VALUE null)

echo $SVAREN >> svaren.txt
echo $VALUE >> svaren.txt

```

It save $VALUE but not $SVAREN

It just show in the terminal, no error or anything like that.

---

### Post by cazz on 2012-12-04
> **The Cog said:**
> If you want to compare two images taken of the same scene but very different lighting, e.g. day and night, I think you will probably have to do some edge detection and then compare the two sets of edges. I'm sure that imagemagick will have some edge-detection capability.

Yes you are right. 
I was thinking about that too until I remember it take a picture every one minute so I just have to compare the latest picture :)

---

### Post by Vaphell on 2012-12-04
> It save $VALUE but not $SVAREN

looks like the output of *compare* goes to stderr

---

### Post by cazz on 2012-12-04
hmm have no idea what you mean?

Is it any way so I can use it like I want it to do?

---

### Post by Vaphell on 2012-12-04
standard output (1) is a 'channel' where all the 'healthy' stuff goes and that can be easily accessed, captured and what not, on the other hand standard error (2) is for errors and other stuff that you don't want to see polluting your good data. If you want to capture stderr you need to redirect it to stdout first

```
SVAREN=$(compare -metric ae -fuzz '10%' viewcam.jpg /old/$VALUE null **2>&1** )
```

---

### Post by cazz on 2012-12-04
Thanks, did work greate :)

---

