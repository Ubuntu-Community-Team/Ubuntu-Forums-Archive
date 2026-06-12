---
title: "Python: User Input File Selection Question"
date: 2007-12-29
forum: Programming Talk
---

### Post by philc on 2007-12-29
I'm very new to Python and trying to teach myself. I've read a few beginner tutorials, and I find it easiest to learn when I have a goal important to me, rather than simple "Hello World" examples.

Anyway, I have a Bash script that takes a user defined video file at run time, asks a bunch of questions, then alters the file based on those answers, and outputs a new file using FFMPEG.

Script is here if you're interested:

[http://www.kapitalworks.com/projects/ffmpeg/kapitaltranscode](http://www.kapitalworks.com/projects/ffmpeg/kapitaltranscode)

I'm OK so far with how general user input in Python works, in terms of user is asked a question and the program interprets the answer.

What I'm stuck on is what comes before.......

The Bash script is executed in the following way:

~$ scriptname.sh inputfilename,extension

Where inputfilename.extension is a file in the user's current directory, that they wish to convert to a different format using FFMPEG

The script then takes this input as input_file=$1

Obviously this is invalid syntax in Python, so essentially I'm looking for the equivalent way of doing this. I can't really see an answer so far from reading the tutorials I've tried (e.g. A Byte of Python and hetland.org: Instant Hacking)

Any help most appreciated.

---

### Post by LaRoza on 2007-12-29
404

To get input from users, use raw_input()

It takes a string

Then you can deal with the contents as you wish.

For command line arguments: [http://www.faqs.org/docs/diveintopython/kgp_commandline.html](http://www.faqs.org/docs/diveintopython/kgp_commandline.html)

---

### Post by ghostdog74 on 2007-12-29
> **philc said:**
> I'm very new to Python and trying to teach myself. I've read a few beginner tutorials, and I find it easiest to learn when I have a goal important to me, rather than simple "Hello World" examples.

Anyway, I have a Bash script that takes a user defined video file at run time, asks a bunch of questions, then alters the file based on those answers, and outputs a new file using FFMPEG.

Script is here if you're interested:

[http://www.kapitalworks.com/projects/ffmpeg/kapitaltranscode](http://www.kapitalworks.com/projects/ffmpeg/kapitaltranscode)

I'm OK so far with how general user input in Python works, in terms of user is asked a question and the program interprets the answer.

What I'm stuck on is what comes before.......

The Bash script is executed in the following way:

~$ scriptname.sh inputfilename,extension

Where inputfilename.extension is a file in the user's current directory, that they wish to convert to a different format using FFMPEG

The script then takes this input as input_file=$1

Obviously this is invalid syntax in Python, so essentially I'm looking for the equivalent way of doing this. I can't really see an answer so far from reading the tutorials I've tried (e.g. A Byte of Python and hetland.org: Instant Hacking)

Any help most appreciated.
every beginner to Python should head down to the Python official docs to see what's going on. If you have tried [the tutorial]("http://docs.python.org/tut"),you would have come across  [this]("http://docs.python.org/tut/node4.html#SECTION004110000000000000000"), . It shows you how you are take in arguments when you run the script. Also, if you have tried the tutorial from page 1 to last, you will see [this ]("http://docs.python.org/tut/node6.html#SECTION006100000000000000000")too...it shows you how you can take input from user.

---

### Post by LaRoza on 2007-12-29
[http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)

The above is very good for handling user input.

---

