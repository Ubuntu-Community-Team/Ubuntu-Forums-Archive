---
title: "running scripts in terminal mode"
date: 2014-11-16
forum: Programming Talk
---

### Post by ngant on 2014-11-16
I want to pass an argument to a command- line program.  I saved the basic command-line program as a file to be executed as a shell script.  However when I run the file, I cut and paste the argument (actually a web link) after running the script, but the script seems to gloss over it, like it wasn't ever there or ever entered:

FYI I am using youtube-dl. 

My script file (yt1) is simply the following text:

youtube-dl -x --audio-format mp3 

I run it:"./yt1" and then cut and paste my youtube link (ex.: [https://www.youtube.com/watch?v=some_new_video](https://www.youtube.com/watch?v=some_new_video))
 
but my output is:  "youtube-dl: error: you must provide at least one URL"

which is the exact error message as I would get if I just ran youtube-dl without any arguments.

what  am I missing to get this to work?  Do I have to add some special character before the https link?

---

### Post by steeldriver on 2014-11-16
Things following the script name itself get passed as numbered *positional parameters* into the script, which you can refer to using $1, $2 etc. e.g.

```

youtube-dl -x --audio-format mp3 "$1"

```

or more generally

```

youtube-dl -x --audio-format mp3 "$@"

```

You should also add a "shebang" to tell the system what shell to use

```

#!/bin/bash

youtube-dl -x --audio-format mp3 "$1"

```

---

### Post by Christmas on 2014-11-17
You need to tell your Bash script to use the argument you're feeding it. Arguments are referred to as $1 for the first argument, $2 for the second and so on, while $@ will be replaced by all the arguments. So just as in the above post, add "$1" to your command.

---

### Post by ngant on 2014-11-17
At first it seemed to me that you wanted me to declare or assign the hypertext link itself into a variable named "$1",  _but to do this while staying within terminal mode_ in order to pass that to the function yt1 as the actual variable.  However I didn't realize that "$1" was to be included into the script file itself rather than use it by itself as a command line argument.  So I get it now.  I have edited script file "yt1" to include "$1" and now the thing is working as suggested.  Thanks a lot!

I am really new to Linux shell scripts although I understand some basic programming concepts.

---

### Post by steeldriver on 2014-11-17
Not really - we just want you to write your script like

```

#!/bin/bash

youtube-dl -x --audio-format mp3 "$1"

```

and then run it as

```

./yt1 [URL="https://www.youtube.com/watch?v=some_new_video"]https://www.youtube.com/watch?v=some_new_video
[/URL]
```[URL="https://www.youtube.com/watch?v=some_new_video"]
[/URL]

---

### Post by QIII on 2014-11-17
A bit late now, but:  [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

Closed

---

