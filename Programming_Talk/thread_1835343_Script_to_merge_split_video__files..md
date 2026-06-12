---
title: "Script to merge split video  files."
date: 2011-08-29
forum: Programming Talk
---

### Post by kunal00731 on 2011-08-29
Hi, 
Yesterday i was trying to develop a script for merging split video files of any format.
The idea came to me when i downloaded a movie called disclosure which was splitted into 3 files like DSC.rmvb.001, DSC.rmvb.002, DSC.rmvb.003

Normally i  merge them using :

cat  DSC.rmvb.001 DSC.rmvb.002  DSC.rmvb.003 >> DSC.rmvb

Hence i started developing a script to do this for all formats (i.e. rmvb,mkv,avi....and so on.)

So installed mencoder first  and then wrote the script as such:

./join.sh
The script starts here :

[COLOR=Magenta]#!/usr/bin
Echo "How many files are to be converted ?"
read i;
if[$i -eq 1]
then
echo "Operation not possible with only one file"
fi

if[$i -gt 1]
then
echo "Enter the path and  name of the videos u want to combine"
read video1 video2 video3
echo "Name the new video with extension"
read name
mencoder -forceidx -oac copy -ovc copy -o $name $video1 $video2 $video3
echo "Operation Successful!"
fi


[COLOR=Black]Now I have heard that mencoder does not support all formats and what if i want to join more than 3 videos. ???

Need some pointers here guys and tell me if a better way exists here.:confused: [/COLOR]
[/COLOR]

---

### Post by kunal00731 on 2011-08-29
Also i would like to know , whether external softwares like mencoder are really necessary. Can we not achieve the   same result with the age old "cat"  command ??

---

### Post by Smart Viking on 2011-08-29
Here it is in python, you can have as many files as you want. I have barely tested it though. You just gotta make it launch "sendcommand" as a system command, and not just print it.

```
#!/usr/bin/env python
command = "cat"

def sendcommand(command,args,outputname):
  for arg in args:
    command += " "+arg
  command += " >> "+outputname
  return command

filen = []
uinput = ""
quit = 0
while 1:
  print "Enter a filename to add or whatever, press \"D\" when you're done, press \"Q\" to exit."
  uinput = raw_input(">")
  if uinput.upper() == "Q":
    quit = 1
    break
  elif uinput.upper() == "D":
    break
  elif uinput != "":
    filen.append(uinput)
outputname = ""
if not quit:
  while 1:
    print "Choose an output name, press \"Q\" to quit"
    fname = raw_input(">")
    if fname.upper() == "Q":
      quit = 1
      break
    else:
      outputname = fname
      break
  if not quit:
    print sendcommand(command, filen, outputname)

```EDIT: Ah you want the mencoder command, that can be achieved with some small little changes. You can do that, and learn python in the process, hurra! :)

---

### Post by kunal00731 on 2011-08-29
@Smart Viking :

Brilliant Script, never even thought about it.
I already know python but never even thought about such a process.
Greatly done.

Thanks.:P

---

### Post by Smart Viking on 2011-08-29
No problem, I am in a scripting mood today :)

---

### Post by ofnuts on 2011-08-29
```
ls file.ext.* | sort | xargs cat >file.ext
```or as a script to rebuild "file.ext" form its parts:

```

#! /bin/bash
ls $1.*  | sort | xargs cat >$1

```or am I missing something?

---

### Post by josvanr on 2012-03-21
If I try to join movies like that, and play with mplayer, the joined movie stops playing at the 'intersection' when i fastforward to the intersection (using arrow keys). Have you tested this?

josvanr

> **kunal00731 said:**
> Hi, 
 
mencoder -forceidx -oac copy -ovc copy -o $name $video1 $video2 $video3
 
[COLOR=Black]Now I have heard that mencoder does not support all formats and what if i want to join more than 3 videos. ???

Need some pointers here guys and tell me if a better way exists here.:confused: [/COLOR]
[/COLOR]

---

### Post by CynicRus on 2012-03-22
```

ffmpeg -i input1.flv -sameq intermediate1.mpg
ffmpeg -i input2.flv -sameq intermediate2.mpg
cat intermediate1.mpg intermediate2.mpg > intermediate_all.mpg
ffmpeg -i intermediate_all.mpg output.flv

```

---

