---
title: "Writing a Frontend"
date: 2009-03-22
forum: Programming Talk
---

### Post by solarwind on 2009-03-22
Hey all, I'm using QtCreator (IDE) to write a frontend for a command line app using C++ and Qt 4.

I need to be able to **execute** the command line app with certain flags, **read** the output (the program prints progress information as it does its job) and **update** the GUI (such as progress bars) as the command line app prints out progress information.

How do I do this. I already have a basic GUI going but so far it just uses the system() function to call the command line app. This is annoying because I can't read the output, I have to wait for the process to finish and it lags the output. Because of this, I wont be able to update the GUI.

Can anyone help me?

---

### Post by cabalas on 2009-03-22
What command line app are you trying to write a front end for? just asking as if it is like curl where all of the functionality is separated into a library perhaps the best idea would be to use the library rather than the system function.

---

### Post by solarwind on 2009-03-22
> **cabalas said:**
> What command line app are you trying to write a front end for? just asking as if it is like curl where all of the functionality is separated into a library perhaps the best idea would be to use the library rather than the system function.

pk2cmd (a microcontroller programmer cmdline interface). There's no library, it's just an app.

---

### Post by NathanB on 2009-03-22
I believe this is what you are looking for:

[http://www.gnu.org/software/libtool/manual/libc/Pipe-to-a-Subprocess.html#Pipe-to-a-Subprocess](http://www.gnu.org/software/libtool/manual/libc/Pipe-to-a-Subprocess.html#Pipe-to-a-Subprocess)

---

### Post by samjh on 2009-03-22
[http://doc.trolltech.com/4.5/qprocess.html](http://doc.trolltech.com/4.5/qprocess.html)

Take a look at the execute and reallAllStandardOutput methods.

---

### Post by solarwind on 2009-03-22
> **NathanB said:**
> I believe this is what you are looking for:

[http://www.gnu.org/software/libtool/manual/libc/Pipe-to-a-Subprocess.html#Pipe-to-a-Subprocess](http://www.gnu.org/software/libtool/manual/libc/Pipe-to-a-Subprocess.html#Pipe-to-a-Subprocess)

Thank you.

> **samjh said:**
> [http://doc.trolltech.com/4.5/qprocess.html](http://doc.trolltech.com/4.5/qprocess.html)

Take a look at the execute and reallAllStandardOutput methods.

Thanks! This is what I was looking for. Also, I need a way to update a progress bar from within a function and I don't know how to do it.

For example, when the user clicks the "Burn!" button, the GUI will call the cmdline program to perform a function. The cmdline program constantly prints the percentage complete (on every new line). I need a way to keep looping and constantly read the percent complete and update a progress bar.

There are two problems:
1. I think the GUI wont refresh until the end of the callback function so even if I keep updating the progress bar, it will only show the final result which is 100%, it wont update in the middle.
2. how do I get the stdout of the cmdline program when it has not yet completed execution? Is it possible with the QProcess class?

---

### Post by samjh on 2009-03-23
> **solarwind said:**
> how do I get the stdout of the cmdline program when it has not yet completed execution? Is it possible with the QProcess class?

I think readyReadStandardOutput() signal is emitted from QProcess when a line (ie. ending with '\n') is written to stdout.  Then you can call readAllStandardOutput() and parse the last line written.

Frankly, I'm not a 100% sure.  Google is your friend. :)

---

