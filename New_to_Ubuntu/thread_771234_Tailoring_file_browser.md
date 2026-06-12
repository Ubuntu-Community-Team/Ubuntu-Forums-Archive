---
title: "Tailoring file browser"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by NormR2 on 2008-04-27
Hi,
I've just installed ubuntu 7.10 on an old HP system (500MHz, 190Mb RAM, 12G Hard drive) and am trying to learn Linux. I have several questions:

0)Can ubuntu run successfully in 190Mb of RAM?  It seems to be working, although I had trouble installing it from the Live CD.

1)When using the file browser, how do I assign a commandline to be executed when I double click (D-C) on a file. On MS Windows, I can use the File Types menu to create a number of command lines to be associated with a file extension. One of the command lines will be the default and will be automatically executed if I D-C on the file, the other command lines are available as choices in the "Context menu" you get when you right click on a file.

Right now sometimes when I D-C on a file in Linux, I get a window with 3-4 buttons that I'm to chose one of to determine what happens. Is there a way to set a default that will be automatically executed without there being a dialog that I must respond to every time?

2)Why does Linux think a file ending with .txt is executeable?

3)For files ending with .html, how would I associate a browser with the file, so when I D-C on it, the browser opens the file, formats and displays the contents. This is more of #1.

4) I got an error message (small window with text: "Can't eject volume") many times while I was copying files from a CD to my hard drive. I was in the file browser, selected the files on the CD and then clicked on the folder on the hard drive and did Paste.  What was happening?

5) Do I need internet access from my computer to run Ubuntu? It has a Winmodem that I can't figure out how to configure.

6) Can I install packages using RPM from files I've downloaded on another computer and copied to the Ubuntu computer's hard drive?  The files are owned by root and I am unable to execute them. 

7) Can I set the file browser to always start with "View as Lists" vs "View as icons"?

8)In the file browser, when I D-C on a file that ends with .txt and has a type of plain text document, nothing happens. If I R-C on the file and chose the top item in the list: Open, nothing happens.  If I R-C on the file and chose "Open with other Application..." and then chose text editor, it opens and displays the file in gedit.  How can I make D-C open this file in gedit?

9) When I click on a file to "Open" it and nothing happens, is there a log file that would have a message explaining what the problem was and why it didn't open?  What Open meant would depend on the type of file. What should happen when I try to open a .bin file or a .sh file?

Could you direct me to a source that would explain why I'm having these problems and how to solve them?

Thanks,
Norm

---

### Post by NormR2 on 2008-04-28
Are there too many questions in this one threas?
Should I make one thread per question?

---

### Post by hyper_ch on 2008-04-28
> **NormR2 said:**
> 0)Can ubuntu run successfully in 190Mb of RAM?  It seems to be working, although I had trouble installing it from the Live CD.
Not sure about ubuntu but Xubuntu and Fluxbuntu can...

> **NormR2 said:**
> 1)When using the file browser, how do I assign a commandline to be executed when I double click (D-C) on a file.
There is not "the" filebrowser but many different default ones depending on the DE you're using.... so, for each one it will be different.

> **NormR2 said:**
> 2)Why does Linux think a file ending with .txt is executeable?
Why should the ending have an impact of whethr a file is executable or not? Why should a .bat file always be executable just because of its ending? What about .scr? Wouldn't it be better to have file permissions that state whether and for whom a file is executable? Actually, the last one is the case in linux ;)

> **NormR2 said:**
> 3)For files ending with .html, how would I associate a browser with the file, so when I D-C on it, the browser opens the file, formats and displays the contents. This is more of #1.
That depends also again on the DE you're using... normally you should be able to right-click, select "open with", browse the appz and check "always open with" or something...

> **NormR2 said:**
> 4) I got an error message (small window with text: "Can't eject volume") many times while I was copying files from a CD to my hard drive. I was in the file browser, selected the files on the CD and then clicked on the folder on the hard drive and did Paste.  What was happening?
No clue what you did... but while the content is being displayed you shouldn't be able to eject the cd...


> **NormR2 said:**
> 5) Do I need internet access from my computer to run Ubuntu? It has a Winmodem that I can't figure out how to configure.
Not really, but it helps a lot... there are howtos for it.

> **NormR2 said:**
> 6) Can I install packages using RPM from files I've downloaded on another computer and copied to the Ubuntu computer's hard drive?  The files are owned by root and I am unable to execute them.
Ubuntu is debian-based and uses .deb files... you can get the packages at [http://package.ubuntu.com](http://package.ubuntu.com) . RPMs can be converted but you shouldn't do that.

> **NormR2 said:**
> 7) Can I set the file browser to always start with "View as Lists" vs "View as icons"?
Yes you can... but it depends again on your file browser on how to do that.


> **NormR2 said:**
> 8)In the file browser, when I D-C on a file that ends with .txt and has a type of plain text document, nothing happens. If I R-C on the file and chose the top item in the list: Open, nothing happens.  If I R-C on the file and chose "Open with other Application..." and then chose text editor, it opens and displays the file in gedit.  How can I make D-C open this file in gedit?
See above with the question to .html files

> **NormR2 said:**
> 9) When I click on a file to "Open" it and nothing happens, is there a log file that would have a message explaining what the problem was and why it didn't open?  What Open meant would depend on the type of file. What should happen when I try to open a .bin file or a .sh file?
No clue about log files there... and while .bin and .sh files aren't made executable nothing should happen there except for maybe opened in a text editor.

> **NormR2 said:**
> Could you direct me to a source that would explain why I'm having these problems and how to solve them?
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://www.psychocats.net/](http://www.psychocats.net/)
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)
[https://wiki.ubuntu.com](https://wiki.ubuntu.com)

---

### Post by Sef on 2008-04-28
> Are there too many questions in this one threas?
Should I make one thread per question?

It is best to make one thread per problem.  Otherwise, problems can get lost if more than one is there.

---

### Post by eriqjaffe on 2008-04-28
> **NormR2 said:**
> 0)Can ubuntu run successfully in 190Mb of RAM?  It seems to be working, although I had trouble installing it from the Live CD.I've run Xubuntu 7.10 on as little as 128mb of RAM, although I found it a bit too sluggish.  IIRC, the LiveCD requires 256mb of RAM to install, but the Alternate Install CD can install on as little as 64mb (although you'll realistically need more than that to effectively run the OS once it's installed).

If you really want a crash course, try doing a command-line install and then just build the system up with the packages you want.

---

### Post by NormR2 on 2008-04-28
Thanks for the taking the time to answer all my questions.  As a newbie to the Linux environment and PC talk in general, I have a limited vocabulary.
What's a DE? The file browser that came with my ubuntu in Nautilus 2.20.0.
To me an executable file is one that is processed directly by the OS, not read and 'executed' by an interpreter. For example, a java jar file is not directly executable, it requires the java program. 
How does the OS know how to 'execute' a plain text file? Does it read the file and detect the language (eg Perl) and then call the correct program to 'execute' it? 

Thanks,
Norm

---

### Post by hyper_ch on 2008-04-28
DE = Desktop Environment (Gnome, KDE, Xfce, ...)

Files have 3 permission properties (read,write,execute) and it can be set for owner,group and world... if you are allowed to execute it based on your user/groups memberships, then it will be executed.... by default new files are not set to be executed - it is just silly to define what file can be executed only based on its extension.

---

