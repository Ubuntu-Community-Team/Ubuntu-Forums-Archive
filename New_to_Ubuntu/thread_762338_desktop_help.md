---
title: "desktop help"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by 1scorpio on 2008-04-22
Not sure Im doing this right. I want to remove the media icons from the desktop but I dont know how please see the attached screenshot
thanks in advance
Scorpio

---

### Post by PurposeOfReason on 2008-04-22
Run gconf-editor (in a terminal or a run box) and go

apps -> nautilus -> desktop

---

### Post by 1scorpio on 2008-04-22
thanks I needed that and that tells me much more as well. I have been using Ubuntu for only one month and love it had gutsy now using 8.04 beta love it as well. i do not use nor do i wish to ever again use MS windows. the transition to Linux has been smooth and painless.I could go on $ on but you get the pic
again thanks

---

### Post by Norfeldt on 2008-11-19
okay.. I have also only used ubuntu for 1 month so I see if I can help you.
First you have to use the terminal 
(please view this movie before you use the terminal [http://www.youtube.com/watch?v=xblIJSbRK-g]("http://www.youtube.com/watch?v=xblIJSbRK-g") it gives a clue about that you are doing)

_Open the terminal_
Applications/Accessories/Terminal
_Type in the following_
[PHP]ls[/PHP]
you will now see the folders you have in your home folder
You want to open your desktop so you want to open the desktop folder
you can do this by typing
[PHP]cd Desktop[/PHP]
then you want to se what's in the folder so you type
[PHP]ls[/PHP]
now you can see the things you have on the desktop
you then type
[PHP]rm the-name-of-the-file[/PHP]
If that doesn't work then try
[PHP]sudo rm the-name-of-the-file[/PHP]
If that don't do the trick try
[PHP]rm -f the-name-of-the-file[/PHP]
-f means you force it to do the command

Warning! don't ever type something you don't know what is. Some people thing it's fun to make people remove all their files because they don't know what they are typing. If you are in doubt about a command you can then type
[PHP]man the-command[/PHP]
and then se what it does

If it works then remember to mark this thread as "solved"

---

### Post by Idefix82 on 2008-11-19
> **Norfeldt said:**
> okay.. I have also only used ubuntu for 1 month so I see if I can help you.
First you have to use the terminal 
(please view this movie before you use the terminal [http://www.youtube.com/watch?v=xblIJSbRK-g]("http://www.youtube.com/watch?v=xblIJSbRK-g") it gives a clue about that you are doing)

_Open the terminal_
Applications/Accessories/Terminal
_Type in the following_
[PHP]ls[/PHP]
you will now see the folders you have in your home folder
You want to open your desktop so you want to open the desktop folder
you can do this by typing
[PHP]cd Desktop[/PHP]
then you want to se what's in the folder so you type
[PHP]ls[/PHP]
now you can see the things you have on the desktop
you then type
[PHP]rm *the name of the file*[/PHP]
...

Firstly, you are replying to a thread which is seven months old, secondly not answering the question (the OP wasn't talking about deleting files), which has by the way been answered by PurposeOfReason.

---

### Post by Norfeldt on 2008-11-19
> **Idefix82 said:**
> Firstly, you are replying to a thread which is seven months old, secondly not answering the question (the OP wasn't talking about deleting files), which has by the way been answered by PurposeOfReason.

sorry

---

