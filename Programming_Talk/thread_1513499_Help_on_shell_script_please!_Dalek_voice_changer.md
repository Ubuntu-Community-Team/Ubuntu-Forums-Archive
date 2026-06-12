---
title: "Help on shell script please! Dalek voice changer"
date: 2010-06-19
forum: Programming Talk
---

### Post by neojames on 2010-06-19
Ok, I've worked out how to change the voice in audacity, but I was wondering if there was a way to have audacity automatically make the changes to the file.

My plan is to have the user input some text into a zenity dialogue, which will then be piped to a file using espeak. I would then like audacity to make the changes on the file to Dalekize it. I've worked out the espeak bits but don't know where to start on the audacity bits. Thank you if you can help me with audacity! :p

---

### Post by neojames on 2010-06-19
So far I have this code:-
#!/bin/bash

espeak -w voice.wav "$(zenity --entry --text="Type what you want to say , followed by [ENTER]:")"

But am completely stumped on how to do the audacity bit:confused:
Can I even do the audacity bit from cmd?

---

### Post by slavik on 2010-06-19
> **neojames said:**
> So far I have this code:-
#!/bin/bash

espeak -w voice.wav "$(zenity --entry --text="Type what you want to say , followed by [ENTER]:")"

But am completely stumped on how to do the audacity bit:confused:
Can I even do the audacity bit from cmd?
have you looked at audacity documentation?

---

### Post by neojames on 2010-06-19
Yes, I couldn't find much and what I did, I didn't really understand. I was hopeful somebody would be able to give me an example or something. I also think what I did find was about building plug-ins

---

### Post by hakermania on 2010-06-19
you must find the flags that audacity gives....for example 
audacity -f file -d [option] 3242 -s [otheroptions]
etc.....
This is only an idea...

---

### Post by neojames on 2010-06-20
This is the output I got when I typed audacity -help in console:-
Command-line options supported:
	-help (this message)
	-version (display Audacity version)
	-test (run self diagnostics)
	-blocksize nnn (set max disk block size in bytes)

In addition, specify the name of an audio file or Audacity project to open it.

---

### Post by mainerror on 2010-06-20
Doesn't it have a manpage?

---

### Post by neojames on 2010-06-20
Yes, but it just says the package description and the options I posted above.

---

### Post by geirha on 2010-06-20
It also says:
```

       Audacity  is  primarily  an interactive, graphical editor, not a batch-
       processing tool. Whilst there is a basic batch processing  tool  it  is
       experimental  and  incomplete. If you need to batch-process audio or do
       simple edits from the command line, using sox or ecasound driven  by  a
       bash script will be much more powerful than audacity.

```

So it sounds like you'll want to have a look at sox and ecasound.

---

### Post by neojames on 2010-06-21
Will they have access to 3rd party plugins?

---

### Post by Protocol84 on 2010-11-22
How do you do the Dalek voice in Audacity? I am trying to figure this out....

---

