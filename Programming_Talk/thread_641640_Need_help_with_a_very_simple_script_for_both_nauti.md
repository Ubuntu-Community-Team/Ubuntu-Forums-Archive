---
title: "Need help with a very simple script for both nautilus and through bash"
date: 2007-12-15
forum: Programming Talk
---

### Post by zgerrz on 2007-12-15
hi,

i'm trying to develop a simple script to convert my video files on my PC to files that can be more easily viewed on my Palm TX. i'm using ffmpeg, and have developed the exact parameters that i want to use to convert my videos, but i'm just having trouble making a script out of the ffmpeg options.

here's what i have:
```

ffmpeg -i INPUT.avi -vcodec xvid -b 384k -r 20 -s 480x320 -acodec mp3 -vol 400 OUTPUT.avi
```

i need a file to install to my nautilus-scripts folder so i can convert a file quickly by using a context menu.

i also would like a file so that i can just enter a command followed by the input and output file and it would convert the file using the custom parameters i have listed above (i want this way as well so i can SSH into my PC from my Palm, convert a video on my PC, and then copy the file to my Palm over a wireless connection).

any help would be appreciated, thanks.

---

### Post by Majorix on 2007-12-15
This is actually not just "a very simple script".

You could use python's optparse module (I am not at all experienced with bash scripting, so can't suggest an option/arguments parser module for it, if one exists after all) then parse the options and arguments, and make the script executable and move it to /usr/share/nautilus-scripts so that it appears in the context menu. However I don't know how a context menu sends options and arguments to the script at hand.

But the command line program should be easy to code. I am not sure if you would settle with a Py code though, therefore I can't offer my services to you at this point. If you do want a Py code however, just let me know.

BTW, can you run Linux on your Palm? I have an IPAQ and I hate it and its Windows CE to its fullest, and can't install Linux on it :(

Good luck.

---

### Post by zgerrz on 2007-12-15
> **Majorix said:**
> This is actually not just "a very simple script".

You could use python's optparse module (I am not at all experienced with bash scripting, so can't suggest an option/arguments parser module for it, if one exists after all) then parse the options and arguments, and make the script executable and move it to /usr/share/nautilus-scripts so that it appears in the context menu. However I don't know how a context menu sends options and arguments to the script at hand.

But the command line program should be easy to code. I am not sure if you would settle with a Py code though, therefore I can't offer my services to you at this point. If you do want a Py code however, just let me know.

BTW, can you run Linux on your Palm? I have an IPAQ and I hate it and its Windows CE to its fullest, and can't install Linux on it :(

Good luck.

OK, well if you could write me up a Py coded version for the command line program that would be enough anyway. i thought a nautilus-script would be convenient as well, but the command line program would be enough for me. thanks.

as for linux on my Palm TX.. i HAVE heard about installing custom versions of linux to run on my specific palm model. here's a link for something i found earlier:

[http://atrey.karlin.mff.cuni.cz/~miska/]("http://atrey.karlin.mff.cuni.cz/~miska/")

as you can imagine though, the functionality is limited compared to wat the native Palm OS can do. nevertheless it is actually pretty good based on wat i've heard alone.

i plan on using a program called pssh to SSH into my PC from my Palm, so i shouldn't need linux installed on my Palm to do so.

---

### Post by Majorix on 2007-12-15
OK I got onto it and here is the code:
[PHP]from optparse import OptionParser
import os, sys
parser = OptionParser()
parser.add_option("-i", "--input", dest="input_file",
                  help="input FILE to convert", metavar="FILE")
parser.add_option("-o", "--output", dest="output_file",
                  help="output FILE to convert to", metavar="FILE")
(options, args) = parser.parse_args()

if not os.path.isfile(options.input_file) or not os.path.isfile(options.output_file):
	print "Invalid I/O files!"
	sys.exit()
os.system("ffmpeg -i " + options.input_file + " -vcodec xvid -b 384k -r 20 -s 480x320 -acodec mp3 -vol 400 " + options.output_file)
[/PHP]

The above code, yet simple, still checks for incorrect input/output files, and does the necessary conversion if everything is ok.

Make the code executable (chmod a+x script.py) and place it somewhere in your path. Then you can execute it with only script.py -i input_file -o output_file .

Hope it helps :)

---

### Post by zgerrz on 2007-12-15
I get this error when executing the command

```
from: can't read /var/mail/optparse
/usr/bin/pconvert.py: line 14: import: command not found
/usr/bin/pconvert.py: line 15: syntax error near unexpected token `('
/usr/bin/pconvert.py: line 15: `parser = OptionParser()'

```

i think it's because i don't have a python parser program on my computer. i did a quick search on aptitude for a parser, but there appear to be a alot of them.

can you recommend a specific parser program? assuming, of course, i'm right about needing one in the first place. thanks

---

### Post by Majorix on 2007-12-15
Yes you will need a Python parser and the specific headers for it. You can go with Python2.5, which I used to create the script I gave you, and it is the current stable release.

So in a terminal or in Synaptic, find and install the packages called "python2.5" and "python2.5-dev".

---

### Post by zgerrz on 2007-12-15
i still get the same error after installing python2.5 and python2.5-dev

---

### Post by Majorix on 2007-12-15
I don't know why its trying to read /var/mail/optparse. And why are those import lines numbered 14-15 in the code? They start from the first line in the code I wrote here. Did you add something at the top?

---

### Post by zgerrz on 2007-12-15
i did add a few comment lines at the top. to be sure that these weren't causing the problem, i just removed them and tried the command again, but with the same results (the lines mentioned were just different now)

---

### Post by Majorix on 2007-12-15
Try adding
#!/usr/lib/env python
at the start of the code. Then run again. Or try running it with "python pconvert.py -i input_file -o output_file". I have a feeling you are running it with a wrong interpreter.

---

### Post by zgerrz on 2007-12-15
you're right, i needed to run it with 'python script.py'

i get the script to run, but i'm getting the invalid I/O files message from the script. what makes the script return files as "invalid I/O files"?

---

### Post by Majorix on 2007-12-15
Oops, you are right. My mistake. It checks if BOTH the input file AND the output file exist. Since the output file can't exist, it will give you an error. Please change the line that starts with an "if" to this:
[PHP]if not os.path.isfile(options.input_file):[/PHP]
Sorry, I was trying to get the code quickly done for you. Try again now and see how it goes. I believe there are no more bugs in it (and I should congratulate myself for being able to produce bugs in such a short code :p)

Good luck.

---

### Post by zgerrz on 2007-12-15
nice!

it works just fine now. thanks for making up this script so quickly, i really appreciate it. it's a nicer way for me to convert files rather than entering all those options with ffmpeg.

---

### Post by Majorix on 2007-12-15
No problem, glad it worked for you. I will be looking up for info that could help me understand the mechanics behind nautilus context menu, and if I understand it I will post here back.

---

### Post by geirha on 2007-12-16
> **Majorix said:**
> Try adding
#!/usr/lib/env python
at the start of the code. Then run again. Or try running it with "python pconvert.py -i input_file -o output_file". I have a feeling you are running it with a wrong interpreter.

env is in /usr/bin, so ```
#!/usr/bin/env python
``` as the first line of the file should make it run without having to type python in front of it.

---

### Post by Majorix on 2007-12-18
^Of course, I don't know what I was thinking when I wrote lib. That was a bad day of mine; but then again I don't have many "good" days :p

---

