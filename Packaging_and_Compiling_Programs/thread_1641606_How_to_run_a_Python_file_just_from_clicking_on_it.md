---
title: "How to run a Python file just from clicking on it"
date: 2010-12-09
forum: Packaging and Compiling Programs
---

### Post by WlaadDyaab on 2010-12-09
Hi

I'm currently on this tutorial:

[http://www.youtube.com/watch?v=-lfWzPxOJQ8](http://www.youtube.com/watch?v=-lfWzPxOJQ8)

I'm trying what the guy in there does, but he's running Windows 7 and I'm running Ubuntu

When he double-clicks on the ".py" file in his desktop the file ends up running in MS-DOS like this:

[ATTACH]177900[/ATTACH]

5:04 (on the time-line in YouTube video)

But when I double-click on my ".py" file in my Ubuntu environment I get this:

[ATTACH]177901[/ATTACH]

Is there a way to format or adjust the settings so that my ".py" file ends up like in the YouTube video tutorial?


Thanks

---

### Post by wojox on 2010-12-09
Did you make it executable?

```
chmod +x myFile
```

---

### Post by WlaadDyaab on 2010-12-09
Sorry I didn't quite understand that [wojox]("http://ubuntuforums.org/member.php?u=802919"). Do you mean that I have to program using command line interface in order to get to what I wanted to get?

---

### Post by WlaadDyaab on 2010-12-09
That's what Terminal gave me after typing the command:

> chmod: cannot access `myFile': No such file or directory


---

### Post by wojox on 2010-12-09
You would replace myFile with your python file name. Right click your file and choose Properties > Permissions > Execute.

---

### Post by WlaadDyaab on 2010-12-09
> **wojox said:**
> You would replace myFile with your python file name. Right click your file and choose Properties > Permissions > Execute.

[ATTACH]177908[/ATTACH]

I made a screenshot of what happened

This popped up after I double-clicked on my ".py" file

When I click on "Run in Terminal" I think it does something really quick but obviously I don't see a thing Lol

When I click on "Run" nothing happens

When I click on "Display" it shows me what you seen in my second screenshot

Is there another way?

---

### Post by wojox on 2010-12-09
Open your terminal and cd to the directory the script is in 

```
python script.py
```

```
./script.py
```

replace script.py with your script name.

---

### Post by WlaadDyaab on 2010-12-09
That's what I typed in Terminal:

> cd Python
Pressed "Enter"
> python script.py

But I got this message:

> python: can't open file 'script.py': [Errno 2] No such file or directory

Was I doing the commands right? I'm not very good with command lines to be honest

---

### Post by wojox on 2010-12-09
You typed cd Python so you have a folder named Python with the script in it?

Where in your Home Directory is the script?

---

### Post by WlaadDyaab on 2010-12-14
Hey thanks mate

I apologise for not replying earlier - been too busy finding solutions on how to download this, them update that, then try fixing this...etc Lol

I'm currently reading a little bit on how to start Programming in general

When I need help in Python I'll ask, and thank you so much for using your valuable time to help

---

### Post by boarder428 on 2010-12-22
I think you forgot the ./ before filename. provided the file was named python script.py and it was created in the directory named python

Example:
```
 [corey@mint-9-isadora ~]$ mkdir -p ~/Projects/hello3 [COLOR="Red"](creates the directory Projects/hello3)[/COLOR]

  [corey@mint-9-isadora ~]$ cd ~/Projects/hello3    [COLOR="Red"](changes to the directory Projects/hello3)[/COLOR]

  [corey@mint-9-isadora ~/Projects/hello3]$ gedit hello.py [COLOR="Red"](opens gedit and creates the file hello.py)[/COLOR]
  
  #!/usr/bin/env python [COLOR="Red"](typed inside gedit, tells computer where to find the python interpreter)[/COLOR]
  
  print "Hello World!" [COLOR="Red"](typed inside gedit and then press the save button to save and close gedit)[/COLOR]
  
  [corey@mint-9-isadora ~/Projects/hello3]$ chmod +x ./hello.py  [COLOR="Red"](makes the file executable)[/COLOR]

  [corey@mint-9-isadora ~/Projects/hello3]$ ./hello.py [COLOR="Red"](runs the program from the command line)[/COLOR]
  

Hello World!  [COLOR="Red"](programs output)[/COLOR]


```

---

### Post by WlaadDyaab on 2010-12-22
Hey that was really great

If I wanted to continue programming but not in graphical interface - in command line, would that mean that I would get less error reports?

---

### Post by C_Bomb on 2010-12-22
> **wojox said:**
> Did you make it executable?

```
chmod +x myFile
```


oh very cool, I was wondering how to do that, so easy and simple, haha.

---

### Post by boarder428 on 2010-12-26
> **WlaadDyaab said:**
> Hey that was really great

If I wanted to continue programming but not in graphical interface - in command line, would that mean that I would get less error reports?

You would probably get the same amount of error reports.  Error reports usually are caused by incorrect syntax or by being in the wrong directory when trying to execute a program.

---

### Post by sennabot on 2012-02-28
> **WlaadDyaab said:**
> [ATTACH]177908[/ATTACH]
When I click on "Run in Terminal" I think it does something really quick but obviously I don't see a thing Lol


sorry to up the topic, but this is like the windows prompt problem when u dont start the aplication from the prompt but execute directly. U can solve like in windows, adding something in the code to stop the program like "raw_input()"

is not a great option to develop cause u dont have the error info but once u finished your code u can just click the file, run and will not close the window before you read the return.

cya!

---

