---
title: "Gedit stalled upon opening one document, how to recover the others?"
date: 2016-11-18
forum: New to Ubuntu
---

### Post by MaxGom on 2016-11-18
Hello,
I was editing several documents on gedit without any problem, but it stalled when I tried to open an additional one (probably too big file). Gedit has been using 100% of one CPU-core for 24hours and does not respond. So I'm afraid I will have to kill it (or turn the PC off).
Is there a way to kill only the document causing the problem and keep the contents of the others, or will everything be closed together? This is Ubuntu 14.04 LTS.
Thanks,
Maxime

---

### Post by #&amp;thj^% on 2016-11-18
I would try first to copy over what you dont want to lose to another text editor if you can.
I know of NO way to kill "One" instance of Gedit.
Try to re-direct error messages and close the terminal leaving the applications running,
```
nohup gedit > /dev/null 2>&1 &
```
This is a long shot...but should be safer than just killing gedit.

If not you can try to open another instance of gedit from the terminal with:
```
gedit & disown
```
I have been very lucky the majority of times in it saving my projects. But sometimes I lose it all.
See the following for a bit more information on how this works:

man nohup

help disown

Anyway I wish you the best of luck.
Kind Regards
EDIT: BTW I have been using Sublime Text Editor for about 2 years now with no hangs or stalls, and I find it dose a great job for my needs. (Although it lacks a Print Function)
More Information on Sublime Text and how to install it here:[http://www.webupd8.org/2011/03/sublime-text-2-ubuntu-ppa.html](http://www.webupd8.org/2011/03/sublime-text-2-ubuntu-ppa.html)
And More Information Here:[http://askubuntu.com/questions/172698/how-do-i-install-sublime-text-2-3](http://askubuntu.com/questions/172698/how-do-i-install-sublime-text-2-3)

---

### Post by mc4man on 2016-11-18
If you have multiple workspaces available you could also try going to a new workspace & open the docs you want to save in a new gedit instance.

---

### Post by MaxGom on 2016-11-18
Hi,
Thank you for the advice. I'm afraid I don't understand excatly what you advice me to do.
To make things more clear, currently gedit is opened though absolutely unresponding: 2-3 documents are opened and unchanged, one is opened with unsaved changes (that I don't want to lose) and the document causing the problem is "being opened" (but it's only a grey screen since gedit is pedalling).
Anyway, I will only be able to try recovering on Monday, because it's on my office PC.
Maxime

---

### Post by mc4man on 2016-11-18
> **MaxGom said:**
> Hi,
Thank you for the advice. I'm afraid I don't understand excatly what you advice me to do.
To make things more clear, currently gedit is opened though absolutely unresponding: 2-3 documents are opened and unchanged, one is opened with unsaved changes (that I don't want to lose) and the document causing the problem is "being opened" (but it's only a grey screen since gedit is pedalling).
Anyway, I will only be able to try recovering on Monday, because it's on my office PC.
Maxime
If referring to me (probably not..) what I'm saying is Ubuntu can have multiple workspaces (if enabled.
So in that case one can go to another workspace, open the doc you want to save & it'll open in a new instance of gedit.
You'll get a prompt about the file already being opened, do you want to  'Edit anyway'?  Select that, then save the file.

Multiple workspaces are not enabled by default, to do so, if needed,  go to  System Settings > Appearances > Behavior as in screenshot

---

### Post by #&amp;thj^% on 2016-11-19
> **MaxGom said:**
> Hi,
Thank you for the advice. I'm afraid I don't understand exactly what you advice me to do.
To make things more clear, currently gedit is opened though absolutely unresponding: 2-3 documents are opened and unchanged, one is opened with unsaved changes (that I don't want to lose) and the document causing the problem is "being opened" (but it's only a grey screen since gedit is pedalling).
Anyway, I will only be able to try recovering on Monday, because it's on my office PC.
Maxime
And if referring to me... Yes I understand your problem (Gedit Hung) that is totaly clear.
Sorry if my instructions were vauge or unclear to you.
Please also be aware that this is no "promise" to solve your problem...but it has worked for me in the past when such events happened. And mc4man has a worthy suggestion also.(IE Workspaces)
So if his suggestion dose not work for you...Mine will go as follows.
1. Open a terminal.
2.Enter the code below.
```
nohup gedit > /dev/null 2>&1 &
```
3. Now you should have a New gedit.(And I would only use one instance at a time to prevent the same (Hang or freeze) from happening again).
4. Now "if" you can try copying and and pasting the Doc/s you want to salvage to the Newly opened gedit. Of course one at time...save and close.
5. Repeat this method until you are done with trying to salvage your work.
Now if this method did not work, you can also try the second method I suggested.
1. Open a terminal.
2.Enter the code below.
```
gedit & disown
```
And repeat steps 4 & 5 if you can.(If Gedit will allow you to)
And I will check in Monday to see how this going for you. (Although I may not have any further advise to offer)
BTW If this is Office machine (Work)...Do you have some sort of help like an IT person or such.
Best of Luck:D

---

### Post by MaxGom on 2016-11-21
Hello guys,
Unfortunately, I am back at my computer (that I left on for the week-end to prevent my document to disappear definitely), and gedit is not running anymore. Of course, my document has not been saved. So I am afraid it is gone for good...
This is not totally negative experience, since I now know about auto-saving, saving manually more frequently and caring more before opening large docs, and more elaborate solutions if problems occur.
Anyway, I will bookmark this thread just in case...
Thanks,
Maxime

---

### Post by howefield on 2016-11-21
> **MaxGom said:**
> This is not totally negative experience, since I now know about auto-saving, saving manually more frequently and caring more before opening large docs, and more elaborate solutions if problems occur.

I'd add to the list finding an alternative to gedit :)

Although you don't say how large the file actually was, there are text editors that can better handle large file support.

---

### Post by MaxGom on 2016-11-21
The file was about 60MB, but in only one very long line.
Maxime

---

### Post by #&amp;thj^% on 2016-11-21
> **howefield said:**
> I'd add to the list finding an alternative to gedit :)

Although you don't say how large the file actually was, _**there are text editors that can better handle large file support.**_
+1 :smile:

> **MaxGom said:**
> The file was about 60MB, but in only one very long line.
Maxime
I have used Sublime Text with all sorts and size's of Docs and even .jsons with no hangs (often editing them on the fly)...with great ease. But again it lacks a Print Function.
See my link in a previous post of mine...post#2...But would not hurt to see if this is allowed by your company first.
And maybe howefield may have some other suggestions or recommendations for editors. 
Kind Regards

---

### Post by howefield on 2016-11-21
> **1fallen said:**
> And maybe howefield may have some other suggestions or recommendations for editors. 

Not really :)

Personal experience means that I concur with gedit being very poor at handling large files, although I do use it on a daily basis for small text files. I'll leave suggestions of alternatives to others more knowledgeable.

---

