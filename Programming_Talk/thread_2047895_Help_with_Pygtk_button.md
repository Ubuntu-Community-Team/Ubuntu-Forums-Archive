---
title: "Help with Pygtk button"
date: 2012-08-25
forum: Programming Talk
---

### Post by Jonny87 on 2012-08-25
I'm build a simple pygtk window and still learning as I go. I want to have a button that will execute a shell script when clicked. could someone please give me an example of how to do this and please include comments in the example to explain it.

Thanks in advanced for any help any one can give.

---

### Post by DarkAmbient on 2012-08-26
You can find lots and lots of tutorials online on PyGTK and how to create a window and widgets such as buttons, more than sufficient. :) 

Executing a script then you can use subprocess.Popen.

```
// include the subprocess module
import subprocess

function exec_script():
   // You need to pass the command as an array
   cmd = ['sh', 'path/to/script.sh']

   // run script
   process = subprocess.Popen(cmd)

```

I'm taking this from thin air.. so I reserve myself for errors... subprocess has lots of functionality, so one can play around a lot with that module.

An option for creating gtk-applications would be to use Quickly to start of with your application. Then you get to play around with your applications interface in an graphical enviroment using Glade. In case you need to install it.

```
sudo apt-get install quickly
```

then start a new project with:

```
quickly create ubuntu-application <name-of-project>
```

beforehand, you might wanna cd (change directory) in a terminal to where at you would like to create your application, typing that command at once will create a folder in your homedir containing that project. If you would like (just an example) a projectfolder in your homefolder, then create a new folder with:

```
mkdir projects
cd projects
```

then run the quickly create... command above to create your project in the directory ~/projects

You find more documentation on [Quickly here]("https://wiki.ubuntu.com/Quickly")

Best of luck!

---

### Post by Jonny87 on 2012-08-26
> **DarkAmbient said:**
> You can find lots and lots of tutorials online on PyGTK and how to create a window and widgets such as buttons, more than sufficient. :) 

Executing a script then you can use subprocess.Popen.

```
// include the subprocess module
import subprocess

function exec_script():
   // You need to pass the command as an array
   cmd = ['sh', 'path/to/script.sh']

   // run script
   process = subprocess.Popen(cmd)

```I'm taking this from thin air.. so I reserve myself for errors... subprocess has lots of functionality, so one can play around a lot with that module.

An option for creating gtk-applications would be to use Quickly to start of with your application. Then you get to play around with your applications interface in an graphical enviroment using Glade. In case you need to install it.

```
sudo apt-get install quickly
```then start a new project with:

```
quickly create ubuntu-application <name-of-project>
```beforehand, you might wanna cd (change directory) in a terminal to where at you would like to create your application, typing that command at once will create a folder in your homedir containing that project. If you would like (just an example) a projectfolder in your homefolder, then create a new folder with:

```
mkdir projects
cd projects
```then run the quickly create... command above to create your project in the directory ~/projects

You find more documentation on [Quickly here]("https://wiki.ubuntu.com/Quickly")

Best of luck!

Thank you for your help. Yes I know there are alot of tutorials out there and I tried looking but the best I got was an example using subprocess, but when I implemented it into mine, it ran the shell script first when started the python script. so the shell script was first to run but once I ended that, then my python window opened.
Thats not what I want though I want the shell script to only run once the button is clicked.

I will try your example though. And I will look into Quickly. Thanks.

---

