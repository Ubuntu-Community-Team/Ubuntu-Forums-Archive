---
title: "How do I install this program?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by deleyd on 2008-05-17
Got Ubuntu 8.04 installed.
Q. How do I verify what version Ubuntu I have installed?
Q. Where is the 'new tab' button on Firefox? (i.e. "click here to open a new tab")

Now I'll try installing a new program. Downloaded GTHUMB. Got it unpacked. Now not sure what file to double-click on to install it.

Opened a terminal prompt, slowly navigated to the directory where GTHUMB files are.
Q. Is there a fast way to open a terminal prompt at the directory I want? Right now all I know to do is cd xxx over and over until I'm there.

In terminal, tried typing 'install-sh'<return>. Got message "Command not found".

In terminal, tried typing 'install'<return>. Got message that I wasn't giving it enough information. Used it's suggestion and typed 'install --help'. Got a whole bunch of options. 

Not sure where to go from here. (Yes I do, go to Ubuntu newbe forums!)


(So new here, I typed this post all in and thought I posted it, but can't find it. It never showed up. So I type it in all over again, and save it this time before posting. Ah, apparently first time I failed to select a post subject prefix. Still, this is a lot easier than Vista.)

---

### Post by HotShotDJ on 2008-05-17
> **deleyd said:**
> Now I'll try installing a new program. Downloaded GTHUMB. Got it unpacked. Now not sure what file to double-click on to install it.Is there some reason why you downloaded GThumb rather than using Applications --> Add/Remove...  ??  Delete the downloaded files.  You don't need them.  Use Add/Remove and be amazed as Ubuntu takes care of it automagically.

---

### Post by Inxsible on 2008-05-17
> **deleyd said:**
> Got Ubuntu 8.04 installed.
Q. How do I verify what version Ubuntu I have installed?

Q. Where is the 'new tab' button on Firefox? (i.e. "click here to open a new tab")
[COLOR=Red]Ctrl + T[/COLOR]

Now I'll try installing a new program. Downloaded GTHUMB. Got it unpacked. Now not sure what file to double-click on to install it.

Opened a terminal prompt, slowly navigated to the directory where GTHUMB files are.
Q. Is there a fast way to open a terminal prompt at the directory I want? Right now all I know to do is cd xxx over and over until I'm there. [COLOR=Red]You can also cd in the same command like so ```
 cd /home/username/Templates/Public
```[/COLOR]

In terminal, tried typing 'install-sh'<return>. Got message "Command not found".
[COLOR=Red]What are you trying to install?[/COLOR]

In terminal, tried typing 'install'<return>. Got message that I wasn't giving it enough information. Used it's suggestion and typed 'install --help'. Got a whole bunch of options. 

Not sure where to go from here. (Yes I do, go to Ubuntu newbe forums!)


(So new here, I typed this post all in and thought I posted it, but can't find it. It never showed up. So I type it in all over again, and save it this time before posting. Ah, apparently first time I failed to select a post subject prefix. Still, this is a lot easier than Vista.)
Answers in red.

---

### Post by Amstell on 2008-05-17
> **deleyd said:**
> Got Ubuntu 8.04 installed.
Q. How do I verify what version Ubuntu I have installed?
Q. Where is the 'new tab' button on Firefox? (i.e. "click here to open a new tab")

Now I'll try installing a new program. Downloaded GTHUMB. Got it unpacked. Now not sure what file to double-click on to install it.

Opened a terminal prompt, slowly navigated to the directory where GTHUMB files are.
Q. Is there a fast way to open a terminal prompt at the directory I want? Right now all I know to do is cd xxx over and over until I'm there.

In terminal, tried typing 'install-sh'<return>. Got message "Command not found".

In terminal, tried typing 'install'<return>. Got message that I wasn't giving it enough information. Used it's suggestion and typed 'install --help'. Got a whole bunch of options. 

Not sure where to go from here. (Yes I do, go to Ubuntu newbe forums!)


(So new here, I typed this post all in and thought I posted it, but can't find it. It never showed up. So I type it in all over again, and save it this time before posting. Ah, apparently first time I failed to select a post subject prefix. Still, this is a lot easier than Vista.)

Q. How do I verify what version Ubuntu I have installed?

System | About Ubuntu

Q. Where is the 'new tab' button on Firefox? (i.e. "click here to open a new tab")

Dude, learn Ctrl + T, its so much quicker

Q. Is there a fast way to open a terminal prompt at the directory I want? Right now all I know to do is cd xxx over and over until I'm there.

to navigate use the tab to help auto complete a lot of stuff.  if you know the directory just cd to (eg. cd /home/john/Desktop/downloads)



In terminal, tried typing 'install-sh'<return>. Got message "Command not found".

I would suggest to first use the package manager.  If its not in the package manager you can install it by doing ./filename_in_dir

Cheers, hope this helps

---

### Post by codell on 2008-05-18
Q. Where is the 'new tab' button on Firefox? (i.e. "click here to open a new tab")

If you enable the tab bar to be visible all the time, all you have to do is double-click the tab bar to open a new tab. To enable it:
In Firefox:
Edit>Preferences>Tabs>Always show the tab bar

Or if you don't want to do that, go File>New Tab

---

### Post by gnomikos on 2008-05-18
To add or remove buttons from firefox, right click on the file,edit... etc  toolbar, click Customize, and then drag-and-drop whatever button you want...That easy!

For installing a program:
 System->Administration->Synaptic Package Manager
search and install it:)

---

