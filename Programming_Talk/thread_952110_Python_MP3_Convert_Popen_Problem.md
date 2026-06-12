---
title: "Python MP3 Convert Popen Problem"
date: 2008-10-18
forum: Programming Talk
---

### Post by condeh on 2008-10-18
Hi All,

I have wanted to put together a small script to go through my directories and convert all my music to mp3, as that is all that is supported by my phone, which is my primary mp3 player.
I did some reading, and tried to do this with python. Below is the code.

```
import os
from subprocess import Popen

converts = [".wma",".ogg"]
logfile = open('logfile.txt', 'w')
def ConvertAudio():
	for root,dir,files in os.walk(os.getcwd()):
		for fi in files:        
			if os.path.splitext(fi)[1] in converts:
				ext = os.path.splitext(fi)[1]
				name = os.path.splitext(fi)[0]
				
				#do the converting
				mplyrcmd = "mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader '%s' && lame -m s audiodump.wav -o '%s.mp3'" % (fi,name)
				Popen(mplyrcmd, stdout=logfile, stderr=logfile)
				os.remove(fi)
			else:
				print "Unable to Convert, incorrect file type."

if __name__=='__main__':
	ConvertAudio()
```

I have removed the line i used to print the "mplyrcmd" to the terminal. I copy and pasted that which was shown, and it worked as I expected. However, when I run this script, I get the following error.

```
Traceback (most recent call last):
  File "/home/john/bin/python/convertmp3.py", line 21, in <module>
    ConvertAudio()
  File "/home/john/bin/python/convertmp3.py", line 15, in ConvertAudio
    Popen(mplyrcmd, stdout=logfile, stderr=logfile)
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1147, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```

I'm really stumped, can anyone advise?

---

### Post by loell on 2008-10-18
have you installed **mplayer** yet?

---

### Post by snova on 2008-10-18
I believe the input to Popen is supposed to be a list of arguments, not a string. It may be trying to run the entire string as the name of the program.

Of course, I might be thinking of a different API...

---

### Post by condeh on 2008-10-18
I do have mplayer installed. I had the code print the mplyrcmd so I could test it worked. the command produced works, but for some reason calling it via Popen gives an error.
I got the idea to use Popen in this way from another script I believe.

---

### Post by snova on 2008-10-18
I checked the documentation, and I was right. Popen takes a list, not a string.

Alternatively, you can pass the shell=True argument to Popen, which will pass the command through the shell.

---

### Post by condeh on 2008-10-18
Wow, thanks thats right, it now works (sort of, see below)
I guess I misunderstood what I was reading at [http://www.python.org/doc/2.5.2/lib/node528.html](http://www.python.org/doc/2.5.2/lib/node528.html) - More to learn!!

However, I have now stumbled across my next problems.

1. It is saving the new mp3 in the dir from which I run the script, eg /home/john/Music, not in the dir it is found eg /home/john/Music/Artist/Album - I think I can fix this one.

2. The real problem. It is simply executing the command on every file it finds, without waiting for the previous file to be finished processing. Is it possible for the script to wait until the cmd called by Popen is finished? I am trying to convert this from a bash script which did just that.

Thanks for your help

---

### Post by snova on 2008-10-18
Popen has a wait() call.

---

### Post by ghostdog74 on 2008-10-19
here's a shell method
```

find /path/music \( -name "*.wmv" -o -name "*.ogg" \) -printf "%f:%h\n" | while IFS=":" read a b; do 
  echo "mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader "$b/$a" && lame -m s audiodump.wav -o $a.mp3"
 done 

```

---

