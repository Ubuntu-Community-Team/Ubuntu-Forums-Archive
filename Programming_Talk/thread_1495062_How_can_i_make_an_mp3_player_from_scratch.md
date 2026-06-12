---
title: "How can i make an mp3 player from scratch?"
date: 2010-05-27
forum: Programming Talk
---

### Post by BlackSwordD2 on 2010-05-27
im taking this on as a summer project and not entirely sure where to start.

i want to use Python as my language and i want the program to be very basic (simple play, pause, stop, and a tracking bar if possible).

i feel like in theory playing a music file shouldn't be too different from reading a text file, but i have no idea how to read a mp3 file.

also im just using mp3 as a default option for now, i can use any type if there are any that are easier to work with than others.

---

### Post by PaulM1985 on 2010-05-27
This really depends on how much you want to write.  If you actually want to be able to open the file, read it and convert it into sound, you are looking at a lot of work in decompressing different file types.

However, if you are looking at writing a user interface onto something that has already been written, it would be far easier.  Look into gst-python.

Paul

---

### Post by Drone022 on 2010-05-27
To do this from scratch you'll probably want to look into the structure of an mp3 file. Plus you'll be looking for a decompression algorithm.

[http://www.mpgedit.org/mpgedit/mpeg_format/MP3Format.html]("http://www.mpgedit.org/mpgedit/mpeg_format/MP3Format.html")

[http://www.mp3-tech.org/programmer/programmers.html]("http://www.mp3-tech.org/programmer/programmers.html")

I believe the mp3 format is copyrighted but there seems to be plenty of source code out there to look at to help you figure out the codec.

---

