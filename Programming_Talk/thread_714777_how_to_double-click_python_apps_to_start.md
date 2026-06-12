---
title: "how to double-click python apps to start"
date: 2008-03-04
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-03-04
I want to start my .py program with doubleclick.
I know there exists piece of code that does it.
Tell me the code that makes .py files run with 
doubleclick on the icon. Thanks.

---

### Post by pmasiar on 2008-03-04
Windows and linux does it differently. which one do you use?

---

### Post by Nemooo on 2008-03-04
According to his profile he's running Linux.

---

### Post by tseliot on 2008-03-04
Make sure that the first line of your file contains this:
```
#!/usr/bin/python
```

And make sure that the file is executable by doing:
```
chmod +x name_of_your_file.py
```

then double click on your py file and it should start, unless your program calls "sudo" or requires root authorisation.

I think in Windows you would have to use a pyw extension instead.

---

### Post by Vadi on 2008-03-04
I think it would bug you with "Do you want to display, run in terminal, run, or cancel" dialog.

Removing the ".py" should quiet it though, I think.

---

### Post by crazyfuturamanoob on 2008-03-05
> Make sure that the first line of your file contains this:
Code:

#!/usr/bin/python

And make sure that the file is executable by doing:
Code:

chmod +x name_of_your_file.py

then double click on your py file and it should start, unless your program calls "sudo" or requires root authorisation.

I think in Windows you would have to use a pyw extension instead.
Thanks, that did the job, exept it asks every time what to do for it.

Does this work if do that for my python program and then transfer the program
to another computer?

> I think it would bug you with "Do you want to display, run in terminal, run, or cancel" dialog.

Removing the ".py" should quiet it though, I think.

I got an error message by doing that. The error was:
> arho@ohra-desktop:~/python$ chmod +x kokeilu
chmod: tiedostoa "kokeilu" ei voi käsitellä: No such file or directory

Sorry, my ubuntu's language is 
finnish and im too lazy to translate the error
to english. :D

---

### Post by Vadi on 2008-03-05
Well, maybe you re-naming it wrong - it's saying it can't find a file that's named like that

---

### Post by mssever on 2008-03-05
The proper way to do this in GNOME or KDE is to create a separate .desktop file--which will alow you to choose your icon, use a friendly localizable name, specify startup options and command-line options, and aviod that prompt.

You can find the spec for .desktop files over at freedesktop.org. Or, look in /usr/share/applications (both with Nautilus and the terminal.

---

### Post by nanotube on 2008-03-05
> **crazyfuturamanoob said:**
> Sorry, my ubuntu's language is 
finnish and im too lazy to translate the error
to english. :D

you have to rename the file itself. not just change the chmod command. :)
```
mv kokeilu.py kokeilu
```

---

### Post by crazyfuturamanoob on 2008-03-06
> you have to rename the file itself. not just change the chmod command. 

That works but it doesn't remove 
the promt that asks to either run, run in terminal,
view or cancel. I want the file to be like that I 
can doubleclick the icon to run the program. 

The desktopthing looks promising (haven't tried yet).
Edit: Just tried it out and I found it fits for my purposes.

---

### Post by Can+~ on 2008-03-06
> **crazyfuturamanoob said:**
> That works but it doesn't remove 
the promt that asks to either run, run in terminal,
view or cancel. I want the file to be like that I 
can doubleclick the icon to run the program. 

The desktopthing looks promising (haven't tried yet).
Edit: Just tried it out and I found it fits for my purposes.

Open nautilus:
Edit -> Preferences -> Behaviour -> Executable text files.

Also, if you want to make it executable, and you're the owner, then you can use the interface mode, right click, permissions, the last checkbox.

Although all of the above things constitute some security risks.

---

### Post by Vadi on 2008-03-06
I believe he was hoping to achieve that effect for the users of his programs.

And telling them to do that wouldn't be practical, and make some of them unhappy.

---

### Post by harakiri1976 on 2008-09-16
Hello guys!

I asked myself if it would be better to start a new thread or to continue with this one - with new questions/doubts for the "same" problem.

Let me try to explain,

I am developing small applications with Tkinter and wxPython. To make it simple, let's say I want to create an Icon for the Desktop (Gnome for a start) just like we can have Pidgin, aMSN, or Text Editor. With Double-Click I want to make a specific *.py file (script, program..) executable. Without warnings, like "Display or open in terminal...", ok? Does anybody know how to do that? 
Note: I don't want to make ALL *.py Python Files executable that way, ok? All I want, is have an Icon which is in fact a Python Script behind it, ok?

Any Help is Help!

Thanks!

---

### Post by LaRoza on 2008-09-16
> **harakiri1976 said:**
> 
I am developing small applications with Tkinter and wxPython. To make it simple, let's say I want to create an Icon for the Desktop (Gnome for a start) just like we can have Pidgin, aMSN, or Text Editor. With Double-Click I want to make a specific *.py file (script, program..) executable. Without warnings, like "Display or open in terminal...", ok? Does anybody know how to do that? 
Note: I don't want to make ALL *.py Python Files executable that way, ok? All I want, is have an Icon which is in fact a Python Script behind it, ok?


That is called a launcher. The easiest way would be to make a launcher (drag and drop a menu item to the desktop) and open it in a text editor (open the text editor, drag the launcher into it, if you are using a DE which won't let you open it directly).

[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

---

### Post by harakiri1976 on 2008-09-16
I got the Idea! Thank You!

I am having a few problems though. Imagine I have just a small Test.py in my Desktop. Ok?
I made a Launcher (or "PseudoLauncher") and saved in Desktop as test.desktop
Here is the code on it:
```
[Desktop Entry]
Name=WxTest
GenericName=WxTeste
Comment=Whatever
Exec=~/Desktop/./Test.py
```

When I click on it - without having and Icon yet - it gives me an error saying:

"Couldn't display "/home/nuno/Desktop/test.desktop".
The location is not a folder

Can you please explain me what is wrong LaRoza? Is it the location? The name test.desktop"?...any missing Code?

---

### Post by LaRoza on 2008-09-16
> **harakiri1976 said:**
> I got the Idea! Thank You!

I am having a few problems though. Imagine I have just a small Test.py in my Desktop. Ok?
I made a Launcher (or "PseudoLauncher") and saved in Desktop as test.desktop
Here is the code on it:
```
[Desktop Entry]
Name=WxTest
GenericName=WxTeste
Comment=Whatever
Exec=~/Desktop/./Test.py
```


What is that path? ~/Desktop/./Test.py?

Are you doing the ./ because you see it without understanding? Here:

[list]
[*] ~ == $HOME
[*] .. == up one level
[*] . == this directory
[/list]

Make the path a full path to the executable.

---

### Post by harakiri1976 on 2008-09-16
No, no LaRoza! I added the ./ before Tes.py because it is an executable script. As you know, in Linux if you want to run a script that has been already turned into and executable file, ie, "chmod a+x name_of:script.py", with, of course, addind the line #!/usr/bin/python in the python Script.
Anyway, with or without the ./ it's the same :(

---

### Post by harakiri1976 on 2008-09-16
forgot to finish what I started! Sorry!

As I said, as we all know, in Linux if we want to run a script in bash you have to start it with ./ before script's name. Otherwise we have to "call" for the certain prog.

---

### Post by harakiri1976 on 2008-09-16
Voilá!..lol

Listen, in exec part, I tried to change for many times the way the file is executed without success, ie:
```

Exec=~/Desktop/./Test.py

```

or:
```

Exec=/home/nuno/Desktop/./Test.py

```

or even:
```

Exec=python /home/nuno/Desktop/Test.py

```

Nothing changed! So I decided to click in the wxtest.desktop properties->Permissions and turned "on" the "Allow execute file as program". Then it Runs the Test.py script which is Good! But now the problem maintains!:S It still works like a point-and-Click Python Script whit the message:

> 
Do you want to run "WxTest" or display it's contents?"
Run in terminal ; Display ; Cancel ; Run



First part is very Good! Which is, I can have a different Icon for my application/Script/Program, etc etc. But the 2nd part is, I want to  "Turn Off" these questions about running my script. How can I do it? :S

---

### Post by harakiri1976 on 2008-09-16
SOLVED!

Sorry and Thank you guys!

Good or Bad,speaking about security Issues, it's DONE and it does what I want. Which is to run an Application with a Click on a Desktop Icon :)

I read back what Can+~ wrote, and it's ok for me :)
> 
Open nautilus:
Edit -> Preferences -> Behaviour -> Executable text files.

Also, if you want to make it executable, and you're the owner, then you can use the interface mode, right click, permissions, the last checkbox.

Although all of the above things constitute some security risks.


Thank You all, specially LaRoza!

Cheers

---

### Post by LaRoza on 2008-09-16
> **harakiri1976 said:**
> No, no LaRoza! I added the ./ before Tes.py because it is an executable script. As you know, in Linux if you want to run a script that has been already turned into and executable file, ie, "chmod a+x name_of:script.py", with, of course, addind the line #!/usr/bin/python in the python Script.
Anyway, with or without the ./ it's the same :(

No, that is not when you have to put ./ there.

As I said, it is a path. It means "this directory".

If you have a executable file x in home, and try to run it, you have to tell the shell where it is (if it isn't in $PATH).

So you could do:

```

~$ ./x
#or
~$ /home/laroza/x

```

They are the same thing.

---

### Post by harakiri1976 on 2008-09-16
I guess you misunderstood me :)

Listen, let's a simple Python script, ok? ...with just an Hello World.
```

#!/usr/bin/python
#LaRoza Test

print 'Hello LaRoza!'

```

Here we go. Save the .py file. "Chmod" it with the right flags. And then try to run it on the Shell with a simple..
```

/home/LaRoza/LaRoza.py

```

It doesn't work! Or you call python and Run it, or you have to Run it like a shell script behaviour ./ right?

I mean...
```

python /home/LaRoza/LaRoza.py

```
or
```

/home/LaRoza/./LaRoza.py

```

---

### Post by LaRoza on 2008-09-16
```

~/p$cat p.py
#!/usr/bin/env python
print "Hello"

~/p$./p.py
Hello
~/p$/home/laroza/p/p.py
Hello
~/p$

```

---

### Post by derjames on 2008-09-16
> **harakiri1976 said:**
> I guess you misunderstood me :)

Listen, let's a simple Python script, ok? ...with just an Hello World.
```

#!/usr/bin/python
#LaRoza Test

print 'Hello LaRoza!'

```

Here we go. Save the .py file. "Chmod" it with the right flags. And then try to run it on the Shell with a simple..
```

/home/LaRoza/LaRoza.py

```

It doesn't work! 



Hello there!!
This will work if the folder where the script is located is included in the PATH, for this you should include:

```
export PATH=$PATH:/home/LaRoza
```

in your .bashrc file

j

---

### Post by harakiri1976 on 2008-09-16
I misunderstood you! I was wrong! Got the idea.

Thanks!

Cheers

---

