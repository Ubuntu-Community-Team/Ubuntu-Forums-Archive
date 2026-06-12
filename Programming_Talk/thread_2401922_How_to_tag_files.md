---
title: "How to tag files?"
date: 2018-09-24
forum: Programming Talk
---

### Post by kiskrof on 2018-09-24
Hallo. I have got nearly no programming experience (I have only written a Pong and a program playing Othello in Python), but what I want to do is quite simple or so I think. I would just like to be able to tag my movies and I cannot find any software that does it. Maybe tagspaces would do, but I cannot install it. I just need to work on a list of the form : Shortcut to "Sapphires", Already seen=1, Australia=1, Argentina=0, Qualtiy=9,   Shortcut to "Nueve Reinas" Australia=0, Argentina=1 Quality=9 and so on. The graphical interface would just be a matrix with a line for each movie and a column for each tag, with boxes I can check or uncheck. It is important that the program works with both files and folders, since some movies are just files and other movies are folders(because they contain subtiles or because it is a group a several movies or a series). Alternatively, the program should be able to detect all the video files, whether they are in the main folder or the source folder, without listing other files like jpg or srt. The only gimmicks needed are a function to list only, e.g. movies with Argentina=1 or Already seen=0 or Quality>7  Of course the program should be able to add to the list any new element in the source folder, and, if possible, to unlist any shortcut whose targer is no longer there.    Is there an easy to use programming language on Ubuntu? Alternatively, of course, if you know a software that does just that...

---

### Post by TheFu on 2018-09-24
There are lots of movie manager programs. Many are web-apps.
Or just use a media center program like Kodi or Plex Media Server.

WIth python or any popular webapp language, you can make a DB driven webapp relatively easy using some framework that supports ORMs.  Basically, look for the old "book library" solution.   Most people knowledgeable in the language, but not in the framework can work those the "library" example in 4-6 hrs, worst case.  

I'm not a python guy, but in Perl I could make a single table DB webapp in about 2 hours, tops using Dancer. It wouldn't have any logins or other security, but it would have search and the ability to show all the records in multi-paged windows with <next><prev> buttons.

Or you could use a tab-delimited text file as a DB.  I bet python has a library for reading-writing those. Perl does in the CSV modules.  For speed, I'd load the entire file into memory at program startup, 40K records would be nothing. Then you can search and show the data using regex patterns. Very powerful.  For testing the file contents outside python, use egrep.

BTW, reading a wall of text is hard.  Please break up into multiple paragraphs. The easier a question is to read, the more answers you are likely to get.

---

