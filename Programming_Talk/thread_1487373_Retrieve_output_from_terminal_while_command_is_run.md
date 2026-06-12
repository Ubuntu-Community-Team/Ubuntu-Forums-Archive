---
title: "Retrieve output from terminal while command is running (Python)"
date: 2010-05-18
forum: Programming Talk
---

### Post by jrhughes on 2010-05-18
I'm trying to retrieve the output of a terminal command sent by python. I have used subprocess.Popen(command, stdout=subprocess.PIPE ).communicate()[0] in the past which gives me the output but only after the process is finished. I need to find a way to get the output as the command runs. I have also tried subprocess.Popen(command, stdout=subprocess.PIPE ).stdout.readline() but it stops working after approx. 50 lines. I think that this command uses a stdout buffer which is being filled. 

Thanks in advance for your suggestions.
jrhughes

---

### Post by soltanis on 2010-05-18
If it's possible (i.e. if you have the source of the other program and can recompile it) you should modify it to flush its buffers after every time it writes data, so you will be able to receive it. As for buffering on the Python end, I really don't know a way to solve this.

---

### Post by jrhughes on 2010-05-18
To be more specific the command that I'm trying to get the output for is mencoder so I don't think there is anything that I can do on the command (program) side. However I know there most be a way to get the information I want since other programs (ex. acidrip) can get it.

thanks
jrhughes

---

### Post by soltanis on 2010-05-19
This is odd. I do know that by default stdout is line buffered, so if mencoder uses some kind of fancy output scheme (like ffmpeg does) then this might be messing with the buffering scheme on stdout which is in turn messing with Python. As from what I can tell running tests with various other UNIX programs, there doesn't seem to be a limit of output lines that can be collected by doing:

```

$ python
>>> import subprocess
>>> p = subprocess.Popen(['command'], stdout=subprocess.PIPE)
>>> while p.returncode is None:
...    print p.stdout.readline()

```

To solve the problem, there is probably an option for turning on script friendly output with mencoder. Have you checked already?

---

### Post by jrhughes on 2010-05-19
I have followed your excellent suggestion and reduced the output to only the information that I need. As a result I discovered that the output for the status line is printed over top of the previous line. Therefore, there are no endlines or new lines after the first status line which maybe the reason ___.readline() fails to work. 

I then quickly tried ___.read(1) which returns only one char at a time. A loop calling the read fcn allowed me to get all the output that I needed. However, I still need to figure out how to break the resulting string up into proper lines of output since there are no endlines. I will post again this evening once I figured it out to let you know the result.

---

### Post by jrhughes on 2010-05-19
It turns out I only need to add universal_newlines=True. It seems that mencoder uses '\r' (carriage return) instead of '/n' (endline). The universal_newlines=True causes file objects stdout to be opened as text files and enables the readline fcn to use '\r', '\n', and '\r\n'. 
see: [http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess)
and [http://docs.python.org/library/io.html#io.IOBase.readline](http://docs.python.org/library/io.html#io.IOBase.readline)

```

s=subprocess.Popen(command, stdout=subprocess.PIPE, universal_newlines=True )
while 1:
      print s.stdout.readline()[:-1]
      if s.stdout.readline()[:-1]=='':
            break

```Special thanks to soltanis. Your suggestion to have mencoder produce script friendly output was the only reason I discovered the '\r'.

---

### Post by Tony Flury on 2010-05-19
Your script fragment will skip every other line - is that intended ?

---

### Post by jrhughes on 2010-05-19
No that was not intentional I just didn't notice. However, the code I'm actually using forces the readline to get only every fifth line so it does not matter to me. Out of curiosity, do you know what is causing that?

---

