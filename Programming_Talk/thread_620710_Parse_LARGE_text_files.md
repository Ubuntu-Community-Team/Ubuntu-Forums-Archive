---
title: "Parse LARGE text files"
date: 2007-11-22
forum: Programming Talk
---

### Post by EXCiD3 on 2007-11-22
I'm writing a C++ application (under windows for the time being) and currently am using fstream to read the lines of the file and print them in the console window (just for testing). The file is approx 6mb of text. For testing I have the program read in each line and display them on the screen and it takes over 5 minutes to finish. I am going to need to parse each line also. They will be formated much like the package lists that dpkg uses -> [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.bz2)

Is there any way I can parse through a file with the same sort of structure quickly in C++ other than fstream? I'm fairly new to C++ (freshman in college) and any help you guys could give me would be great appreciated!

---

### Post by Ozitraveller on 2007-11-22
I've done something like this in C#, which is not mush help to you. But the Idea might help. I didn't read it line by line, I read it in chunks (I my case I used 4096 bytes). I opened a stream an read in 4096 bytes into a byte array and process it that way. It was an old DBase database that didn't work any more but the client wanted the data.


This might help:
[http://www.thescripts.com/forum/thread535229.html](http://www.thescripts.com/forum/thread535229.html)

Good luck.

---

### Post by EXCiD3 on 2007-11-22
Thanks for the info. That sounds like what i will need to be doing. I just realized...its gotta be quite doable because look at all the other applications, like gedit, vim, notepad, notepad++, pspad, etc that can load and display the files in less than a second. I just need to find out how ;) That link is pretty explanatory of how to do this but i think i am going to need more of an example to get started.

---

### Post by girishv on 2007-11-23
I always use perl for this kind of stuff. A simple script to do this would be

-------------------------------------------------------------------------------------
!#/usr/bin/perl

while (<>) {
          print $_;
          ## do what ever you want to do here with the line
}

------------------------------------------------------------------------------------

This opens any file given as argument and prints each line (stored in $_). For regular expression etc., I find perl much better/easier than c/c++

Girish

---

### Post by LaRoza on 2007-11-23
Perl and Python are better suited than C++ for file parsing, I would suggest Python, because you'd learn it faster, even though Perl might be powerful, it will take longer to get used to.

---

### Post by EXCiD3 on 2007-11-23
Well thanks for the ideas, but i'm pretty sure those arent an option. I need my application to run off a usb drive with the least amount of dependencies. Runtime environments for those create overhead that I can't have with the limited amount of space on usb drives. These files I will be parsing will only be located in temporary directories on the host and will not take up space on the usb drive. Therefore C++ is my best option and i think using Ozitraveller's idea will possibly work for this.

---

### Post by LaRoza on 2007-11-23
> **EXCiD3 said:**
> Well thanks for the ideas, but i'm pretty sure those arent an option. I need my application to run off a usb drive with the least amount of dependencies. Runtime environments for those create overhead that I can't have with the limited amount of space on usb drives. These files I will be parsing will only be located in temporary directories on the host and will not take up space on the usb drive. Therefore C++ is my best option and i think using Ozitraveller's idea will possibly work for this.

Then C or C++ would make sense. If you had the inclination, you could get Portable Python for the flash drive, so you could run it anywere. [http://www.portablepython.com/](http://www.portablepython.com/)

---

### Post by aks44 on 2007-11-23
> **EXCiD3 said:**
> I have the program read in each line and display them on the screen and it takes over 5 minutes to finish.

I'd bet most of those 5 minutes is spent printing the lines back to the console, not reading the file itself.
If you comment out the console output you may well find that your program is not this slow after all...

---

### Post by Yexo on 2007-11-23
And usually input vai standard c funcionts like scanf, fscanf and the like is _much_ faster than via the c++ iostream library.

---

### Post by [h2o] on 2007-11-23
My bet is also that most time is spent on output and not input.
Using printf() instead of cout is perhaps a bit faster, but my guess is that you end each cout with a "newl", to get a new line.
Don't. It forces the buffer to flush, which is why it is so slow. If you need a line break, use the "\n" escape character.

---

### Post by LaRoza on 2007-11-23
> **'[h2o] said:**
> My bet is also that most time is spent on output and not input.
Using printf() instead of cout is perhaps a bit faster, but my guess is that you end each cout with a "newl", to get a new line.
Don't. It forces the buffer to flush, which is why it is so slow. If you need a line break, use the "\n" escape character.

Did you mean "endl"?

"puts" is lighter still.

---

### Post by shawnhcorey on 2007-11-23
> **aks44 said:**
> I'd bet most of those 5 minutes is spent printing the lines back to the console, not reading the file itself.
If you comment out the console output you may well find that your program is not this slow after all...

Agreed.  You have two choices when reading a file: buffered IO and unbuffered IO.  The question is:  is a line break a significant element of the syntax (like in Python) or is it just another whitespace character (like in Perl)?  If it significant, then using the built-in (and optimized) functions of the buffered IO to break up the lines may be better.

BTW, 4K is tiny in today's computers.  Try something more reasonable, like 8M.

---

### Post by EXCiD3 on 2007-11-23
Ok thanks guys, I didnt realize how slow using cout and endl was. My application does not need that anyways, it was more of just a way for me to get an approximation of how long it was going to take. I will be parsing and displaying through a GUI...probably GTK, as i dont want to run the .Net dependency and using the windows API is too complicated for my understanding of C++.

Is it correct that the quickest way would be for me to copy the file to RAM then parse it?

---

### Post by [h2o] on 2007-11-24
> **LaRoza said:**
> Did you mean "endl"?

"puts" is lighter still.
Yes, I meant "endl". Was a while since I touched C++ ;)
Thanks for the correction.

---

### Post by [h2o] on 2007-11-24
If you read the file into an array, then it will most likely end up in RAM (if it doesn't get swapped, which you can't really control much anyway).

If you can parse the file line by line, then you don't need to save the file contents before processing it. Just read the line, parse it, save your data and throw away the read line and get the next line.

---

### Post by EXCiD3 on 2007-11-25
Ok thanks guys. I commented out the cout code and it ran through the file in seconds instead of minutes...looks like cout is horribly inefficient. I will probably be storing the data into arrays and will keep it in ram. I'm extremely busy with school right now, finals are coming up quick. As soon as i get the chance i will try a couple of things out and see how they turn out. If i have any other questions ill be sure to ask ;) You guys are a lot of help! Thanks!

---

### Post by iharrold on 2007-11-25
> **aks44 said:**
> I'd bet most of those 5 minutes is spent printing the lines back to the console, not reading the file itself.
If you comment out the console output you may well find that your program is not this slow after all...

Exactly... great point.  Con outputs are very slow and not a guarantee on ordered output.  I.e. if you have two streams sharing one console they may intermingle the outputs.

---

### Post by shawnhcorey on 2007-11-25
> **iharrold said:**
> Exactly... great point.  Con outputs are very slow and not a guarantee on ordered output.  I.e. if you have two streams sharing one console they may intermingle the outputs.

Terminal output is ordered by time, not by stream.  Unless you change the I/O control settings, each line is from one stream, that is, lines are not broken up but appear as atomic units.

It is recommended that you do not open multiple streams to other devices.

---

