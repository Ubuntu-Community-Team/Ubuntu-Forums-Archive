---
title: "(Phyton 2.7.9) SyntaxError on &quot;Hello, World!&quot;"
date: 2015-09-09
forum: Programming Talk
---

### Post by josjarephoslav on 2015-09-09
Okay, I am new to everthing and I have this
eagerness to learn coding to create beautiful
and functional softwares for all. I decided to
start with Python thinking it is open source and
good for Linux people. Read a lot of articles
before starting.

Came along I can now start practicing things.
I found a nice links in this forum which lead
me to a Wikibooks page. I tried to apply to first
command and it worked. It was a nice feeling
to write your first code. When I followed the
instructions and saved the file as "hello.py"
and tried to run it on the terminal by typing
"python hello.py".

I get this error:
SyntaxError: invalid syntax.

I searched this forum but I couldn't find
the same problem. Forgive me if I am not
good at searching the particular problem
in a forum to see if the same/similar thread
was oppened and solved. It is just that I am
noobish to this.

For your comfort, I add the screenshot.

---

### Post by patlkli on 2015-09-09
You saved the output of the interpreter to the hello.py file.

What you *should* have done, is put the line you wrote in the file. So there should be one line in hello.py:
```
print "Hello, world!"
```
Not more, not less.

---

### Post by brian-mccumber on 2015-09-09
There is a python interpreter which is interactive and you can run python commands from it which is what you used to print Hello World. There is also a python compiler but most python scripts do not need to be compiled before they will run.

You can write python scripts in a text document using gedit which is the text editor that comes with Ubuntu. When you finish your script and you have saved it as a .py file you navigate the terminal to the directory that has your python script, then type in the terminal python yourScriptName.py and your python script will execute in the terminal, replace yourScriptName with the name you saved your file as. 

I use more than one programming language and I have found that the Geany text editor, which is available in the Ubuntu software center under All Software-->Developer Tools-->IDE's, handles all of them and it includes syntax highlighting for the different languages. Geany will also let you compile and run programs for various languages directly from the editor. Or if you want to use python exclusively there are python ide's available in the software center in the same place as Geany.

If you do not want to have to navigate your terminal to the directory holding your scripts everytime you want to run a script, you can install an app using apt-get from the terminal that will allow you to right click in the file browser and choose open in terminal and the terminal will open in the directory you are currently in. I use this and it saves me alot of time. I am putting the apt-get code for open-in-terminal below along with some links to some python learning resources. Enjoy!


To install open in terminal for Nautilus file browser using apt-get, open your terminal and paste the code below and hit enter. When it get's done installing you will have to log out and then log back in to Ubuntu in order to start using it. When you do this you will be able to open your file browser and right click in white space in any directory, you will then get the option to open in terminal. **Note**: if you want to paste into the terminal you must use Control+Shift+v. The hot keys to open the terminal are Control+Alt+t
```

[FONT=monospace]sudo apt-get install nautilus-open-terminal[/FONT]

```

**Links**
[Python official website]("https://www.python.org/")
[Python Scripting tutorial]("http://www.dreamsyssoft.com/python-scripting-tutorial/intro-tutorial.php")
[Python Basic Syntax tutorial]("http://www.tutorialspoint.com/python/python_basic_syntax.htm")
[Codecademy Interactive Python tutorial]("https://www.codecademy.com/en/tracks/python")

I used google and searched these keywords - python scripting tutorials - to bring up alot of python tutorials including video tutorials

---

### Post by flaymond on 2015-09-10
My suggestion is to use Geany  editor instead of IDLE. It's far better and you can tweak to use alternative interpreter (v2 or v3) to launch the scripts. The editor can also compile, build & run various programs in different programming languages, says Python, C, and Lisp (You need the dependencies for these).

Also, from your errors given, the IDLE is simply run everything in previous session as a script (including prompts). What you need to do is just follow the simple patkli instruction.

If you still wanna stick with the IDLE, instead open a new file, and type your code in it, then hit f5 (and save), after that it will execute the program.

---

