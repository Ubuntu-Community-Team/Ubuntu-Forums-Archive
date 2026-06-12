---
title: "using subprocess in python"
date: 2009-03-14
forum: Programming Talk
---

### Post by KLIA on 2009-03-14
Hello guys;

i have a function that suppose to do something and from terminal it has this syntax to be executed;

waseem@home:~/Desktop/Project2/GUI$ python myexif.py -q "pathfile" > test.csv

so far on using subprocess i came up with this;

from subprocess import *
x=Popen(['python','myexif','-q','sys.argv[1]'], stdout=PIPE)
y=Popen(['>','Exif.csv'], stdin=x.stdout)

but i keep getting this error

waseem@home:~/Desktop/Project2/GUI$ python wrapphotodb.py 
Traceback (most recent call last):
  File "wrapphotodb.py", line 37, in _addphotoClicked
    y=Popen(['>','Exif.csv'], stdin=x.stdout)
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1153, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

Any idea? is my syntax correct?

---

### Post by keithweddell on 2009-03-14
I think you are going about this the wrong way.  Not knowing what myexif.py does, I think you need to look at amending it to write the output to a file from inside the script.  Something like:

```
fp = open('/path/to/test.csv','w')
fp.write(output)
fp.close()
```


Keith

---

### Post by KLIA on 2009-03-14
not the matter that i don't know what myexif does but i thought that it's not relevant

Anyway myexif.py extracts information from digital photos about photo's name, make of camera and date.

i need to use the subprocess in other pyqt application to connect to a button but i don't know how for this syntax

waseem@home:~/Desktop/Project2/GUI$ python myexif.py -q "pathfile" > test.csv

besides 

excuse me but i am totally new to this..I couldn't understand anything of what you gave in here

fp = open('/path/to/test.csv','w')
fp.write(output)
fp.close()

where to past it and is just like that?

---

### Post by ghostdog74 on 2009-03-14
why do you need to use subprocess? your myexif.py is a python script. Are you saying that you want to execute myexif.py from inside another Python script? If you are intending to do that, then use import or from myexif import <something>. Otherwise, without creating another Python script, do everything in your myexif.py script.

---

### Post by DirtDawg on 2009-03-14
I think the problem might be with the single chevron symbol ('>'). That seems to be where the error is originating, but I am not sure what it is supposed to do, exactly, so can't really suggest any specific change.

EDIT: Or go with ghostdog's advice, which looks like more than a stab in the dark (which is what my suggestion is :D)

---

### Post by KLIA on 2009-03-14
hey guys

i need to execute myexif using suprocess because i have to link it with Qt the syntax ">" it will redirect the output of the execution to comma separated values.

---

### Post by ghostdog74 on 2009-03-14
just import the myexif.py into your wrapphotodb.py  script. from there on, you can use whatever functions, classes from your myexif.py to generate your csv file.

---

### Post by KLIA on 2009-03-14
okay but importing myexif to wraperphotodb won't generate .csv file for me because that i do it myself from the terminal??

the original command is just python myexif -q "photopathname"

---

### Post by ghostdog74 on 2009-03-14
inside your myexif.py script, there should be some print statements to print to stdout. If not, why do you think you can use ">" , the redirection operator. Therefore, go into your myexif.py script, look at how they print the results out. I believe those print statements are already inside functions or something. Just use those functions. on the command prompt
```

# python wrapblahblah.py -q "blah" > test.csv

```

---

### Post by KLIA on 2009-03-14
Well, i understand your effort but my intension not to use this method for the reason that i want everything to be done with a click of button........i don't want to be presenting my final year project in front of panel and they asking me why am i doing that from the terminal, why am i passing arguments?!!!!........the end user won't like it

that why i wanna subprocess this syntax and just link it with qt button that would do it once the user click on it

do you know how to subprocess this one please?

myexif -q "blah" > blah.csv

---

### Post by geirha on 2009-03-14
Have Popen redirect stdout to a file object...
```

p= Popen(["python","myexif.py","-q","blah"], stdout=file("test.csv","w"))
p.wait()

```

---

### Post by KLIA on 2009-03-14
> **geirha said:**
> Have Popen redirect stdout to a file object...
```

p= Popen(["python","myexif.py","-q","blah"], stdout=file("test.csv","w"))
p.wait()

```

Thank you very much

it's working..............

---

