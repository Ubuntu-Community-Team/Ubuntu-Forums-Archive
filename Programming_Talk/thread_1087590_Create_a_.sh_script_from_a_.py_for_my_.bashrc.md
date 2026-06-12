---
title: "Create a *.sh script from a *.py for my .bashrc"
date: 2009-03-05
forum: Programming Talk
---

### Post by mnemonik on 2009-03-05
Hello all!

Would you believe it but my .bashrc cherry has just been popped today! Yes I am a noob, but until this afternoon I had no idea what the .bashrc file was, and now I have made my first alias to ssh to a server. Woo!

Anyways, I have a python script to change *.m3u playlists created in windows to a format readable by Ubuntu, but to run it I have been opening up Geany and hitting execute, which I am sure is ridiculous, I just haven't figured out yet the real way to do this. What I want to be able to do is run this script from the terminal and use an alias for it.

Here is my python script:

[PHP]#ask for playlist filename to convert
inList = raw_input("Type the playlist filename here: ")

#import file
in_file = open(inList, "r")
contents = in_file.read()
in_file.close()

print "___________ORIGINAL:______________"
print
print contents

#change "\" to "/", change "G:" to "/media/My Book/"
contents = contents.replace('\\', '/').replace('G:', '/media/My Book')

print "___________CONVERTED:_____________"
print
print contents

#ask for output filename
outList = raw_input("Save playlist as filename: ")

#export file
out_file = open(outList, "w")
out_file.write(contents)
out_file.close()
[/PHP]

Also, how would I be able to specify the in_file path and out_file path from the terminal, before the script starts, so that I don't have to use raw_input in the script?

Thanks for all the help!

---

### Post by mnemonik on 2009-03-05
> **mnemonik said:**
> Also, how would I be able to specify the in_file path and out_file path from the terminal, before the script starts, so that I don't have to use raw_input in the script?

Clarification about this part: I want to be able to run the script from the terminal something like this:

```
convpl -i IN_FILE -o OUT_FILE
```

Or even just have the script run on start up and convert all playlist files in a specific folder, so I'm always up to date.

Thanks so much for all help, you have no idea what it means to me.

---

### Post by Brandon.Viking on 2009-03-05
hmm,,, if you only want to replace strings in a file for a play list ... sounds like a sed "one-liner" would do the trick ... not sure you would need a script although it would be easier probably.

The key lines in the python script are the replace functions.
Here are two 
sed 's/\\/\//g' < infile > outfile 
that will replace '\\' with '/'
sed 's/G\:/\/media\/My Book < outfile >  outfile2
will do the second replacement.

Why cant you just use the python script in Linux though?

shell script would wrap around the two sed commands and your done.

Hope that helps. ( You can do the sed stuff in one line but... I wanted to show the working) 

Brandon.

---

### Post by mnemonik on 2009-03-05
> **Brandon.Viking said:**
> hmm,,, if you only want to replace strings in a file for a play list ... sounds like a sed "one-liner" would do the trick ... not sure you would need a script although it would be easier probably.

The key lines in the python script are the replace functions.
Here are two 
sed 's/\\/\//g' < infile > outfile 
that will replace '\\' with '/'
sed 's/G\:/\/media\/My Book < outfile >  outfile2
will do the second replacement.

Why cant you just use the python script in Linux though?

shell script would wrap around the two sed commands and your done.

Hope that helps. ( You can do the sed stuff in one line but... I wanted to show the working) 

Brandon.

Sweet! I have a couple more questions, I'm really not that knowledgeable, sorry. When I google this, it seems like I am just missing a couple key links in the chain to really understanding everything, and even the tutorials seem a little off.

1. How would I write that as a shell script, preferably to run that on all *.m3u files in a specified directory?
   - After I made it a shell script, I could then alias it in .bashrc, right?

2. How do I set up the arguments for the script "-i IN_FILE" and "-o OUT_FILE"?

Thank you so much.

---

### Post by Tibuda on 2009-03-05
You can execute python script the same way you execute bash scripts.
1. Add```
#!/usr/bin/python
```to the first line of your python script.
2. Add permission to execute it (right-click on Nautilus or chmod a+x filename in terminal).
3. Move it to a PATH directory like ~/bin, /usr/bin or /usr/local/bin

---

### Post by mnemonik on 2009-03-05
> **danielrmt said:**
> You can execute python script the same way you execute bash scripts.
1. Add```
#!/usr/bin/python
```to the first line of your python script.
2. Add permission to execute it (right-click on Nautilus or chmod a+x filename in terminal).
3. Move it to a PATH directory like ~/bin, /usr/bin or /usr/local/bin

Would I be able to edit the python script and allow me to give it the arguments -i IN_FILE and -o OUT_FILE from the terminal this way?

---

### Post by Brandon.Viking on 2009-03-05
wow, there are so many ways you could do this.

sounds like you want to take a copy of a file from a windows partition (your current play list) and replace the path from where looks while booted into windows into a path that makes sense from linux.

if that play list is in the same place all the time ... i would just right a sed script as below, chmod so its executable, (chmod u+x <sedscript>)
and call that from .bashrc

sed file like the following:
#!/bin/sed -f
s/\\/\//g
s/G\:/\/media\/My Book


if the file was saved as newplaylist.sed

after it was saved and executable just call it from .bashrc like: 
newplaylist.sed < windowplaylist > linuxplaylist

simple :)

Hope that helps.
Brandon.

---

### Post by Tony Flury on 2009-03-05
to answer your question about arguments - yes you can extract command line arguments in python : [http://www.faqs.org/docs/diveintopython/kgp_commandline.html](http://www.faqs.org/docs/diveintopython/kgp_commandline.html)

There are other python tutorials out there too.

to be honest - I would not use -i or -o though (personal preference) as the use of these sorts of flags imply that they are optional - which i don't think your arguments are. For the sake of consistency just use positional arguments (first argument is input, 2nd is output), and use the - prefix for optional flags or parameters.

---

### Post by mnemonik on 2009-03-05
> **Brandon.Viking said:**
> wow, there are so many ways you could do this.

sounds like you want to take a copy of a file from a windows partition (your current play list) and replace the path from where looks while booted into windows into a path that makes sense from linux.

if that play list is in the same place all the time ... i would just right a sed script as below, chmod so its executable, (chmod u+x <sedscript>)
and call that from .bashrc

sed file like the following:
#!/bin/sed -f
s/\\/\//g
s/G\:/\/media\/My Book


if the file was saved as newplaylist.sed

after it was saved and executable just call it from .bashrc like: 
newplaylist.sed < windowplaylist > linuxplaylist

simple :)

Hope that helps.
Brandon.

The playlists are automatically generated every time I close mediamonkey (my media library and player in windows) to an external hard drive ("My Book" or "G:") so I don't really need to deal with the windows partition.

I think I am grasping it all now, I hope I'm not annoying, but I do have a couple clarifications I would like you to make for me :)

So in my .bashrc the alias would look something like:
```
alias convertplaylist='/usr/bin/m3uConverter.sed'
```

and the script is what you posted:
```
#!/bin/sed -f
s/\\/\//g
s/G\:/\/media\/My Book
```

and I would call it like this (sorry the syntax is confusing me when we are trying to talk about general ideas of paths):
```
convertplaylist 5stars.m3u 5starsConverted.m3u
```
or would it look like this:
```
convertplaylist < 5stars.m3u > 5starsConverted.m3u
```

Thanks you have been such a great help.

---

### Post by Brandon.Viking on 2009-03-05
you have to use the one with the < and > symbols ... they are for redirecting actual files into and out of the sed script.

... and dont forget to chmod u+x the sed script.

Hope that clarifies it.

Regards,
Brandon.

---

### Post by mnemonik on 2009-03-05
I put the sed script containing this: ```
#!/bin/sed -f
s/\\/\//g
s/G\:/\/media\/My Book
``` in /usr/bin/m3uConverter.sed, gave it permissions, and tried to run it, but no luck so far... Any idea why this is happening?

```
mnemonik@mnemonik-laptop:~/Desktop$ sudo chmod u+x ../../../usr/bin/m3uConverter.sed 
mnemonik@mnemonik-laptop:~/Desktop$ sudo m3uConverter.sed < Songs\ to\ Sample.m3u > test.m3u
[sudo] password for mnemonik: 
/bin/sed: file /usr/bin/m3uConverter.sed line 3: unterminated `s' command

```

---

### Post by Brandon.Viking on 2009-03-05
oops my fault,
need another / at the end of the last line of the sed script
should read
s/G\:/\/media\/My Book/

hope that fixes it ... you shouldnt need to run it with sudo either setting the persions  in /usr/bin would need to be done like that but not running it. Unless you need root to run it?

Regards,
Brandon.

---

### Post by mnemonik on 2009-03-05
> **Brandon.Viking said:**
> oops my fault,
need another / at the end of the last line of the sed script
should read
s/G\:/\/media\/My Book/

hope that fixes it ... you shouldnt need to run it with sudo either setting the persions  in /usr/bin would need to be done like that but not running it. Unless you need root to run it?

Regards,
Brandon.

Well, in the time I was waiting for your response I figured it out in python:

[PHP]#!/usr/bin/python

import sys

for arg in sys.argv:
	if arg != "m3uConverter.py":
		in_file = open(arg, "r")
		contents = in_file.read()
		in_file.close
		contents = contents.replace('\\', '/').replace('G:', '/media/My Book')
		out_file = open(arg, "w")
		out_file.write(contents)
		out_file.close()
[/PHP]

Give me a minute and I will see if your fix gets the sed script going going...

---

### Post by mnemonik on 2009-03-05
Well the sed script works now, however, I think the python script is easier to use. Let me explain:

- the Sed script processes one file at a time
- the sed script can't write back to the same file (when I run "m3uConverter.sed < Songs\ to\ Sample.m3u > Songs\ to\ Sample.m3u" I end up with an empty file, that might just be my incompetence)
- the sed script requires the < and > which is annoying to type out

while the python script _can_:
- do as many files in a batch as I need it to
- writes the files back on to themselves, which is fine because the script works perfectly, and even if it didn't I have back ups
- less syntax in args == easier and quicker to run

Thanks so much for your help Tony Flury and especially Brandon.Viking for sticking around and making sure I got through everything.

Hasta!

---

### Post by Brandon.Viking on 2009-03-05
You are welcome, although I think I may have misunderstood what you were after so sed wasnt the best tool for the job. I am glad you got where you wanted to be.

go python. :)

---

### Post by mnemonik on 2009-03-05
Uh oh... I made the alias cpl (ConvertPlayList) in .bashrc and gave permissions to the file, but I'm getting this output when I try to run the script:

```
mnemonik@mnemonik-laptop:/media/My Book/Music$ cpl 3\ stars.m3u 4\ stars.m3u 5\ Stars.m3u Current\ Cuts.m3u Essential\ Mix.m3u Favorites\ -\ Not\ Heard\ Recently.m3u Funk.m3u Hip-Hop.m3u Instrumentals.m3u Jazz.m3u Last\ 50\ played.m3u Most\ Played.m3u Recently\ Added.m3u Songs\ to\ Sample.m3u Top\ Instrumentals.m3u 
Traceback (most recent call last):
  File "/home/mnemonik/../../../usr/bin/m3uConverter.py", line 11, in <module>
    out_file = open(arg, "w")
IOError: [Errno 13] Permission denied: '/home/mnemonik/../../../usr/bin/m3uConverter.py'
mnemonik@mnemonik-laptop:/media/My Book/Music$ sudo chmod 755 ../../../usr/bin/m3uConverter.py 
[sudo] password for mnemonik: 
Sorry, try again.
[sudo] password for mnemonik: 
mnemonik@mnemonik-laptop:/media/My Book/Music$ cpl 3\ stars.m3u 4\ stars.m3u 5\ Stars.m3u Current\ Cuts.m3u Essential\ Mix.m3u Favorites\ -\ Not\ Heard\ Recently.m3u Funk.m3u Hip-Hop.m3u Instrumentals.m3u Jazz.m3u Last\ 50\ played.m3u Most\ Played.m3u Recently\ Added.m3u Songs\ to\ Sample.m3u Top\ Instrumentals.m3u 
Traceback (most recent call last):
  File "/home/mnemonik/../../../usr/bin/m3uConverter.py", line 11, in <module>
    out_file = open(arg, "w")
IOError: [Errno 13] Permission denied: '/home/mnemonik/../../../usr/bin/m3uConverter.py'
mnemonik@mnemonik-laptop:/media/My Book/Music$ sudo chmod u+x ../../../usr/bin/m3uConverter.py mnemonik@mnemonik-laptop:/media/My Book/Music$ cpl 3\ stars.m3u 4\ stars.m3u 5\ Stars.m3u Current\ Cuts.m3u Essential\ Mix.m3u Favorites\ -\ Not\ Heard\ Recently.m3u Funk.m3u Hip-Hop.m3u Instrumentals.m3u Jazz.m3u Last\ 50\ played.m3u Most\ Played.m3u Recently\ Added.m3u Songs\ to\ Sample.m3u Top\ Instrumentals.m3u 
Traceback (most recent call last):
  File "/home/mnemonik/../../../usr/bin/m3uConverter.py", line 11, in <module>
    out_file = open(arg, "w")
IOError: [Errno 13] Permission denied: '/home/mnemonik/../../../usr/bin/m3uConverter.py'
mnemonik@mnemonik-laptop:/media/My Book/Music$ sudo chmod u+x ../../../usr/bin/
mnemonik@mnemonik-laptop:/media/My Book/Music$ cpl 3\ stars.m3u 4\ stars.m3u 5\ Stars.m3u Current\ Cuts.m3u Essential\ Mix.m3u Favorites\ -\ Not\ Heard\ Recently.m3u Funk.m3u Hip-Hop.m3u Instrumentals.m3u Jazz.m3u Last\ 50\ played.m3u Most\ Played.m3u Recently\ Added.m3u Songs\ to\ Sample.m3u Top\ Instrumentals.m3u 
Traceback (most recent call last):
  File "/home/mnemonik/../../../usr/bin/m3uConverter.py", line 11, in <module>
    out_file = open(arg, "w")
IOError: [Errno 13] Permission denied: '/home/mnemonik/../../../usr/bin/m3uConverter.py'
mnemonik@mnemonik-laptop:/media/My Book/Music$ 

```

Yet, it ran perfectly before I aliased it... do I need to sudo cpl? I shouldn't have to right?

---

### Post by mnemonik on 2009-03-05
I went in to nautilus and checked out the properties of the permissions from there and this is what I get:
- Owner: root; access: r&w
- group: root; access: read only
- others access: read only

Is this what it should look like??

---

