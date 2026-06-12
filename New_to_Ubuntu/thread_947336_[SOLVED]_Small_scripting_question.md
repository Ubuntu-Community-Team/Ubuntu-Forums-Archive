---
title: "[SOLVED] Small scripting question"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by whitethorn on 2008-10-14
Hi,

I'm trying to write a script to dload youtube videos and convert them to .mp3. So far I'm able to dload the videos and convert them.  My problem is I want to keep the title of the file.  So when I run

```
youtube-dl -l "$1"
```
I'd like to save the title, so whatever is in front of the .flv in a variable to I can replace it after using ffmpeg and ecasound.  I've found a couple other scripts but they weren't as automated as I wanted it to be (required me to enter a file name). I'm just stuck on reading the filename and saving it as a variable.


So I think I've figure it out, but there's probably a better way of getting this done.  Any suggestions would be great. Here's my script

```

#!/bin/bash
youtube-dl -l "$1"
a=`ls |grep flv`
mv *.flv /tmp/test.flv
ffmpeg -i /tmp/test.flv -acodec mp3 -ac 2 /tmp/test.mp3
ecasound -i /tmp/test.mp3 -etf:8 -o ~/Desktop/"${a%flv}mp3"
rm /tmp/test.mp3
rm /tmp/test.flv

```

---

### Post by cmnorton on 2008-10-14
Are you looking for basename, so you can separate the name of the file before the period, and use that somewhere else?

`basename $1`

and use that to attach to the front of ".mp3".

---

### Post by stephanvaningen on 2008-10-14
If you would like the part "file" in "/folder/file.ext", you could maybe use this:
```
#!/bin/bash
# Copy-paste this in a file called i.e test.sh and do:
#   sudo chmod u+x test.sh
# then run test.sh by running ./test.sh on the terminal when you're in the same directory as the file you created
file="/home/stephan/scripts/test.sh"
basename=${file##*/}
filepart=${basename%.*}
echo "file part is *$filepart*"
```

Is this what you were looking for?
(source: [http://splike.com/wiki/Bash_Scripting_FAQ]("http://splike.com/wiki/Bash_Scripting_FAQ"))

---

### Post by stephanvaningen on 2008-10-14
Or easier:
 ```
basename $1 .mp3
```
which strips the ".mp3" from the basename

> **stephanvaningen said:**
> If you would like the part "file" in "/folder/file.ext", you could maybe use this:
```
#!/bin/bash
# Copy-paste this in a file called i.e test.sh and do:
#   sudo chmod u+x test.sh
# then run test.sh by running ./test.sh on the terminal when you're in the same directory as the file you created
file="/home/stephan/scripts/test.sh"
basename=${file##*/}
filepart=${basename%.*}
echo "file part is *$filepart*"
```

Is this what you were looking for?
(source: [http://splike.com/wiki/Bash_Scripting_FAQ]("http://splike.com/wiki/Bash_Scripting_FAQ"))

---

### Post by whitethorn on 2008-10-14
That's what I was looking for thanx.

---

