---
title: "Script - How do I automatically load OpenOffice.org document at startup?"
date: 2010-04-27
forum: Programming Talk
---

### Post by Jammanuser on 2010-04-27
Hello,
I wish to load an OpenOffice.org document automatically at startup into Ubuntu. How do I do this?
I used a batch file once in Windows to do something similiar, i.e. load a Microsoft Word document automatically at startup, but now I want to do basically the same thing in Ubuntu, only the file format is .odt instead of .doc, and the word processer is OpenOffice.org instead of Microsoft Word.

Please help.

Thanks in advance.

-Jam Man

:guitar:

---

### Post by hayden92 on 2010-04-27
I'm assuming that you know how to make scripts.

Simply create a new script, and enter the command:
```
ooffice -[module] [path of file]
```

So If I wanted to open my Resume every time I started Ubuntu, the command would be:
```
ooffice -writer /home/hayden/Documents/Resume.odt
```

The names of the modules are:
-writer
-calc
-impress
-draw
There might be a few others.

P.S. If you need help with writing scripts, just let me know.


Hope that helps!

Hayden M

---

### Post by Jammanuser on 2010-04-27
No, I don't really know how to make scripts at this point in time.
What file extension does a script file have? .sh?
And what directory should I put the script file in, so that it runs on startup?

Thanks for the help.

---

### Post by hayden92 on 2010-04-27
Ok, here goes:

I will tell you how to write a script later on, and it's pretty easy but there's a fair bit of new information that you'll need to know.

For this particular purpose I would just add the file to "Startup Applications" (System -> Preferences -> Startup Applications)

Open up "Startup Applications"
Click "Add"
Under "Name" you just call it whatever you want, such as "Office Document"
Under "Command" you just type the command that I gave you earlier, such as ```
ooffice -writer /home/hayden/Documents/Resume.odt
```

Then click add and you're done!

Hayden M

---

### Post by hayden92 on 2010-04-27
If you really want to know how to write a script, here's how:

In your home directory it is good practice to create a folder where all your scripts will be kept
A lot of people make a folder called "bin"
So on my computer it is:
```
/home/hayden/bin
```

Go into the folder called "bin" and create a new file (Right-click -> "Create Document" -> "Empty file")

Open that file with your favourite text editor.

Then copy this line into the file
```
#!/bin/bash
```

It's basically a comment that says "I'm using BASH" (which is a programming language)...

Next you type the command that I told you previously:
```
ooffice -[module] [path of file]
```
But replace [module] with "writer"
and replace [path of file] with the place where the particular file is kept. (Don't surround it with brackets, I just did that to make it a bit clearer.

Then save the file that you have just created.

You then need to make it a script. Do you know how to use the terminal?
If so, navigate to the "bin" folder that you made earlier
And then type the command "chmod 775 [whatever you called you called the script]"

Then you add it to the list of entries in "Startup Applications" but in the "Command" field, you just have to type the name of the script/file that you created earlier.

For opening a document though, I wouldn't recommend learning to script!

On the other hand, 
Once you have created the script, just type the name of the script into a terminal and it will load that office document. Scripts can do so much more than just load documents, but that's for later on ;)

Hope you found that a little bit interesting at least!

Hayden M

---

### Post by Jammanuser on 2010-04-28
Awesome! :)
Thank you very much. It works. :popcorn:

-Jam Man

:guitar:

---

### Post by hayden92 on 2010-04-28
Always glad to help!

Also, don't forget to mark this thread as solved!

---

