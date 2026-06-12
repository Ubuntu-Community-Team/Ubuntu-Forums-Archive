---
title: "help with executables"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by trollex on 2011-09-10
Hi
I recently started using ubuntu, and i don't understand few things. 
I've got classic ubuntu GUI running, and i can't run executable files with click, so i have to do so through terminal. The other problem is, i can't install utorrent, there is a lock sub-icon over utserver executable file icon, so i probably lack permission.
Thanks. :mrgreen:

---

### Post by JRV on 2011-09-10
Utorrent is a Windows program.
Try transmission, it works like utorrent, and it is already installed.

---

### Post by Enigmapond on 2011-09-10
The first problem: Open Nautilus/preferences/behaviour and check to run execs when clicked.

2nd problem, yes it's a permission error right-click on it /properties and make sure the executable tab is checked...you can also do this in the terminal with:

```
sudo chmod -x file name
```hope this helps.

Also...yes don't try utorrent with linux. Just use Transmission or Deluge as the are  native to linux...

---

### Post by papibe on 2011-09-10
Welcome!

If your problem is not solved by Enigmapond's suggestion, could you post a little more details about those executables? For example a little screenshot, and the how the permissions looks on the terminal:
```
$ cd dir_where_files_are
$ ls -la
```
Idem with utserver (that it is design to run on the terminal BTW).

Regards.

---

### Post by snip3r8 on 2011-09-10
> **Enigmapond said:**
> The first problem: Open Nautilus/preferences/behaviour and check to run execs when clicked.

2nd problem, yes it's a permission error right-click on it /properties and make sure the executable tab is checked...you can also do this in the terminal with:

```
sudo chmod -x file name
```hope this helps.

Also...yes don't try utorrent with linux. Just use Transmission or Deluge as the are  native to linux...
There is also a gui method for this,right click the executable and click properties,under permissions click allow execution as program

---

### Post by trollex on 2011-09-10
@Enigmapond 
For first problem, i don't see " run execs when clicked" .
For second problem, i tried it and it didn't actually remove lock but i double clicked it and it said: "There is no application installed for executable files" O_o Guess im missing a package or what?

@papibe 
[http://img716.imageshack.us/img716/5959/screenshotaaq.png](http://img716.imageshack.us/img716/5959/screenshotaaq.png)  
[http://img18.imageshack.us/img18/6430/screenshot1gv.png](http://img18.imageshack.us/img18/6430/screenshot1gv.png)
I hope it helps.

One more strange thing happens when i try to execute utorrent. It creates some "dat" files, which you can see on screenshot with list of files in utorrent folder.

edit: And one more thing, i tried other torrent clients but neither one starts downloading.

---

### Post by Ms_Angel_D on 2011-09-10
exe files are windows programs and are not designed to work in Linux/Ubuntu. 

As a previous poster said there are other torrent options available to you. If your not happy with transmission, try looking in the software center for a few alternatives.


**Some** exe files can be made to work on Linux/Ubuntu with the help of wine however not all of them will work...and whenever possible your better to find a native alternative.

---

### Post by ajgreeny on 2011-09-10
```
sudo chmod [COLOR=Red]+x[/COLOR] filename
```I am sure   [COLOR=Red]-x[/COLOR] will remove the execution permissions from the file.

---

### Post by trollex on 2011-09-10
> **Ms_Angel_D said:**
> exe files are windows programs and are not designed to work in Linux/Ubuntu. 

As a previous poster said there are other torrent options available to you. If your not happy with transmission, try looking in the software center for a few alternatives.


**Some** exe files can be made to work on Linux/Ubuntu with the help of wine however not all of them will work...and whenever possible your better to find a native alternative.

I downloaded utorrent for linux so i thought this executable has other extension and is made to be executed through linux? (of course i know .exe is made to runs on windows)

---

### Post by papibe on 2011-09-10
Thanks for the screenshots.

Let's tackle the utserver problem first. utserver consists in 2 parts, the server you run in the terminal, that works as a backend (sometimes called daemon), and the web client interface.

The server is start on the terminal, just as you are doing it (to stop it press Ctrl+C).

I see that you haven't unzip the necessary files for web interface to work. Stop utserver, and unzip the webiu:
```
$ unzip webui.zip
```
Then restart utserver:
```
$ ./utserver
```
Leave it running.

Go to your browser and go to this page:
```
http://localhost:8080/gui/
```
User will be admin, and leave the password empty.

Let's know how it goes.
Regards.

---

### Post by Enigmapond on 2011-09-10
> **ajgreeny said:**
> ```
sudo chmod [COLOR=Red]+x[/COLOR] filename
```I am sure   [COLOR=Red]-x[/COLOR] will remove the execution permissions from the file.

With due respects...I gave the proper code chmod -x to make executable. however the OP is attempting to execute an .exe file which can't be done outside of wine. He just needs to install Transmission or the like and this will solve his problem. Not sure why this is going on.

---

### Post by trollex on 2011-09-10
> **papibe said:**
> Thanks for the screenshots.

Let's tackle the utserver problem first. utserver consists in 2 parts, the server you run in the terminal, that works as a backend (sometimes called daemon), and the web client interface.

The server is start on the terminal, just as you are doing it (to stop it press Ctrl+C).

I see that you haven't unzip the necessary files for web interface to work. Stop utserver, and unzip the webiu:
```
$ unzip webui.zip
```Then restart utserver:
```
$ ./utserver
```Leave it running.

Go to your browser and go to this page:
```
http://localhost:8080/gui/
```User will be admin, and leave the password empty.

Let's know how it goes.
Regards.

It works! :)  I didn't know it actually runs throught browser.
Thank you all very much!

---

### Post by papibe on 2011-09-11
:p Glad you solve it. Mark the thread solved when you have the chance.

Regards.

---

### Post by ajgreeny on 2011-09-11
> **Enigmapond said:**
> With due respects...I gave the proper code chmod -x to make executable. however the OP is attempting to execute an .exe file which can't be done outside of wine. He just needs to install Transmission or the like and this will solve his problem. Not sure why this is going on.
Well, I'm sorry to disagree with you again, but the **chmod -x** removes execution permissions from a file, and **chmod +x** adds it.  I have just done it to double check, as you had me doubting my memory.

---

