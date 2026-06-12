---
title: "Noob help needed: How to run executable?"
date: 2010-01-31
forum: Programming Talk
---

### Post by latgarf on 2010-01-31
I've just migrated from Windows to Xubuntu.
I use Eclipse CDT to compile the included ANSI C "Hello World", which produces an executable file in the project directory.
How can I make/see it run in Linux?

When I click the "run" button in Eclipse, the "Console" tab prints "Hello World" as it should.
However, when I click the executable's icon in the file browser (Thunar), nothing happens.
Alternatively, I tried in the Terminal to cd to the executable's location, and then type the executable's file name (no extension) and hit enter to run it. But the error message says "Command not found".

In windows, when clicking on the (windows .exe) executable, it opens the Command Prompt window and displays the output, "Hello World" in it. What's the equivalent in Linux?

Many thanks for your quick help!!!

---

### Post by jrothwell97 on 2010-01-31
You need to run it from inside the terminal.

Open up Terminal (it can be found in Applications/Accessories - I think) and navigate to the folder where the executable is stored. (Hint: "ls" lists files in the present folder, "cd" changes directory.)

Once you get to the folder where the executable is stored, type a "./" followed by your application name (this is case sensitive, so *be careful*. So, if your executable was called a.out, in Ubuntu, you'd run

```
./a.out
```

Good luck!

---

### Post by PaulM1985 on 2010-01-31
When running from the command line, you need to type ./ before the name of the executable. So if your program is "Hello", you would have:

./Hello

on the command line.

Not sure about from the file browser.  Maybe you need to make the program runnable using/executable.  I think there is a command for this.  I will try and find it.

Try:

chmod +x PROGRAM_NAME

I think this should make it executable for the file browser although I am not certain.

Paul

---

### Post by latgarf on 2010-01-31
Thanks!!! It worked! - I was missing the "./"

How about clicking executable's icon to run?

---

### Post by Hellkeepa on 2010-01-31
HELLo!

First of all, are you sure you've made the binary executable? Meaning that you've set the executable bit for your user on it? Once it's been set as executable, you can click on it via the file manager, just like in Windows.
Secondly, to execute a file via the terminal, you need to append "./" before the name of the file. This is to tell the OS that you're trying to execute a file which resides in the same folder as you're viewing. The name of the file include the extension, contrary to how it's on Windows.
That means, if you want to execute a file from the terminal, let's call it "test.bin", you'll need to do this:
```
$ cd projects/test
$ chmod u+x test.bin
$ ./test.bin
```
Line 2 is only required to be run once, as this sticks for as long as the file exists.

Happy codin'!

---

### Post by jrothwell97 on 2010-01-31
> **latgarf said:**
> Thanks!!! It worked! - I was missing the "./"

How about clicking executable's icon to run?

Unfortunately, that won't work - when Thunar (the file manager) launches the program, it can't differentiate between a console application and a graphical one. This gives it two choices: to spawn a terminal whether you like it or not, creating UI clutter, or assuming that people running console apps will probably want to do so from the terminal.

You can guess which they went for.

---

### Post by latgarf on 2010-01-31
> **Hellkeepa said:**
> HELLo!

First of all, are you sure you've made the binary executable? Meaning that you've set the executable bit for your user on it? Once it's been set as executable, you can click on it via the file manager, just like in Windows.

How do I check/set the executable bit?
Is it different from file's access permissions?
My executable's permissions are rwxrwxrwx, but clicking it's icon in file browser Thunar still produces no effect. What should I expect - a new terminal window opens and prints "Hello World"?

---

### Post by latgarf on 2010-01-31
> **jrothwell97 said:**
> Unfortunately, that won't work - when Thunar (the file manager) launches the program, it can't differentiate between a console application and a graphical one. This gives it two choices: to spawn a terminal whether you like it or not, creating UI clutter, or assuming that people running console apps will probably want to do so from the terminal.

You can guess which they went for.

I'd like to have an option to run my executables by *clicking* on anything - like a desktop icon or so - doesn't have to be file manager Thunar. Is there a way to run a console application by a mouse click?

---

### Post by djchandler on 2010-01-31
You need to change the files permissions. This can be done using chmod.

You can also change the files permissions using Thunar by right clicking the file and bringing up its properties dialog. Select the permissions tab. If the compiled executable has a diamond shaped icon, there will be a check box near the bottom that needs to be checked to run an executable file.

If running from the command line, precede the filename with a period and a slash, as in:

./yourexecutable

---

### Post by Can+~ on 2010-01-31
> **latgarf said:**
> Thanks!!! It worked! - I was missing the "./"

How about clicking executable's icon to run?

I guess that Thunar assumes that is a graphical application, thus hiding the output. If you run it with gnome's nautilus, it gives you the option to "Run in Terminal".

But if you want a safe solution, create a bash script that executes the program inside a terminal.

---

### Post by dwhitney67 on 2010-01-31
> **latgarf said:**
> 
However, when I click the executable's icon in the file browser (Thunar), nothing happens.

Not true; something does happen.  If you are expecting to see output to a terminal (console), well there's not one in which to display the data.

> **latgarf said:**
> 
In windows, when clicking on the (windows .exe) executable, it opens the Command Prompt window and displays the output, "Hello World" in it. What's the equivalent in Linux?

Create a "launcher" on your desktop; set the Type as "Application in Terminal", then select the full-path of the application you want to run (just use browse).  Once the launcher is created, you can copy it anywhere you want.

---

