---
title: "bash script if then statements"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-04-07
Hi Guys,

I am trying to modify a very basic script that I wrote and I'm pretty confused.
I'd really appreciate some advice.

_Background_:
This is a script to move all the images and videos from a camera to to specified folders on a hard drive and then to remove all the .THM files from the camera.

_The script_:
```

#!/bin/bash
now=$(date +"%d-%b-%Y")
mkdir /media/Elements/"Image Staging"/$now &&
mv *.JPG /media/Elements/"Image Staging"/$now &&
rm -f /media/Elements/"Video Staging"/clips/* &&
rm *.THM &&
mv *.MPG /media/Elements/"Video Staging"/clips/
```

The above script works, but I know it could be better.

_The Problem_:
Sometimes I have more than one type of image or video file on the camera.  If I simply add another mv command for the additional file types, the script will quit if it does not find a file type:
```
*.JPG': No such file or directory
```

The Question:
How can I modify the script so that it will move all of type A and then look for and move type B then look for and move type C without stopping if it does not find a specific type?

I hope this makes sense.

---

### Post by Paqman on 2013-04-07
Just drop the && at the end of each line, it's not normally necessary.

&& means the command will execute, and only move on to the next command if the first is successful. Without the && the script will continue to process each line in turn, but won't flunk out on any errors. If you want it to produce some output for debugging or logging you can still use echo and some if/else type logic.

---

### Post by GrouchyGaijin on 2013-04-07
> **Paqman said:**
> Just drop the && at the end of each line, it's not normally necessary.

&& means the command will execute, and only move on to the next command if the first is successful. Without the && the script will continue to process each line in turn, but won't flunk out on any errors. If you want it to produce some output for debugging or logging you can still use echo and some if/else type logic.
Hey thanks man!
I appreciate it!

---

