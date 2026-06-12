---
title: "Greek and other languages support in Crossover Office"
date: 2007-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by divas on 2007-06-28
I had a problem with Greek support in crossover office that took me two days to solve it, so I post this little tutorial here, that might be useful.

APPLIES TO: Crossover Linux 6.1 / Ubuntu Feisty Fawn
NOTE:This also applies to languages other than greek.

Problem:
I was able to read MS Office documents in Greek, but I was unable to write greek characters.

Solution:
The MS office program must be launched with the following command (suppose we want to launch MS word):
LC_ALL=el_GR.UTF-8 /opt/cxoffice/bin/wine --cx-app winword.exe
or
LC_ALL=el_GR.UTF-8 ~/cxoffice/bin/wine --cx-app winword.exe
depending on the way that you installed crossover. Just try which command works for you...

NOTE: You must add greek support in order this command to work. If you didn't then do it:
Go to system -> administration --> language support and select greek.

Further Customization
Of course, the above is not a solution, because each time we want to open a document we must run this command through a terminal. What we must do is the following:
Create an empty document named winword.sh.
Add the following code in it:
#!/bin/sh
LC_ALL=el_GR.UTF-8 /opt/cxoffice/bin/wine --cx-app winword.exe "$@"
Close the document and place it in the bin directory where crossover office is installed. This is:
/opt/cxoffice/bin
or 
~/.cxoffice/bin
Give execute permissions to the file:
chmod a+x winword.sh
Create a symbolic link to the bin directory, in order the command to be available in the shell:
cd /bin
sudo ln -s /opt/cxoffice/bin/winword.sh winword
Now right click on any MS Word document, select properties and go to open with tab.
Select Add and expand the 'use custom command' option.
In the box that appears type the following:
winword %f
Close the window. Right click again in the document, select properties and go to the open with tab. From the programs that appear select winword. Close the window.
Now if you open an MS Word document you will be able to write greek.

You can also add shortcuts to the desktop or to the toolbar in order to launch MS word.
Right click on the desktop and select create launcher. In the name field type 'Microsoft Word".
In the command type winword.
Click in the No Icon button. In the address bar type:
/home/YOUR_USERNAME/.cxoffice/win2000/windata/StartMenu.c^5E3A^5Fwindows^5Fprofiles^5Fcrossover^5FStart^2BMenu/Programs/Microsoft+Office/Microsoft+Office+Word+2003.xpm
Close the window. A new icon should exist in the desktop that launches MS Word.

You can also create a shortcut in the context menu (right click -> create document -> Word Document). This is how:
Go to your home folder and create a folder named Templates.
Copy there an empty MS Word document named 'Microsoft Word Document'.
Now if you right click inside a folder and select 'create document', then the MS Word option will appear.
If you want to make the Templates folder hidden, just go to your home folder, create an empty document named .hidden, open it and add the word 'Templates' in it. Close it and save it.

All the above apply to other MS office documents as well. Just replace the name winword with the following:
excel (for excel documents)
powerpnt (for power point documents)
outlook (for launching outlook)

I hope the next versions of crossover office to correct this bug so this painful tutorial will not be necessary.

GOOD LUCK ...

---

### Post by Claus7 on 2007-09-13
Hello!

I do not know how many hours I had spent trying to find out a descent solution to this. Without results of cource. Yet, I have to say that I got an hellenic supported office and I avoided this. Undoubtedly a very helpful how to! I wish I found it out earlier.

Anyway I have a question that you (or someone else) might be able to answer :
While you can write hellenic as well as english, are you able to have spell checking in both languages?

For example if you install ms (hellenic) word in a windows machine and you try to write both in the hellenic and english language changing from one to the other with alt+shift you get no red line underneath the words you are typing (of cource writing correctly). Also you can see that you change the language in the last bar of the window as well.
When I try this via crossover the english words (or the hellenic depending on the installation I suppose) are not recognised, as well as the change I make in the language. As a result it is supposed that they are written incorrectly and every time I have to do a manual test of the orthography so as to get rid of the red lines.
Is it possible to change between languages and have spell checking for both?

I hope that I made myself understood.
Thank's in advance,
Regards!

---

