---
title: "RECOLL why are these simple things so complicated"
date: 2018-05-20
forum: Recurring Discussions
---

### Post by briar rabbit on 2018-05-20
I have been using UBUNTU for years now. I aint to computer geek I just a human being trying to get by and still I wonder why are these peripherals in life so complicated while the simple things in life are denied.

I am trying to word search a large number of pdf files and after looking for most of the day I found "recoll".  Well, why is it so complicated?  Why are computers in general so complicated for anything other than .... not sure it tends to vacillate.

I installed "recoll" through synaptic, yet it was nowhere to be found.
After viewing a youtube video I went into a terminal and "INSTALLED" RECOLL.
Then I found RECOLL in the >Applications >Accessories and "clicked" on it.
After starting recoll it when into building a directory.
After 20 minutes of building the directory I got the following message.  Why were these not installed with RECOLL and why do I need "antiword (application/msword)".  And if I need that why is it not in synaptic.

This is very frustrating doing the same essential things over and over and over and over ... and over.

"External applications/commands needed for your file types and not found, as stored by the last indexing pass in /home/me*/.recoll//missing:

Perl::Image::ExifTool (image/png)
antiword (application/msword)
python:mutagen (audio/mpeg)

---

### Post by T.J. on 2018-05-20
It depends on how you installed recoll.  I'd need more information on what you did before I can answer your question.  That is a common problem, even on Windows - as any programmer can tell you.

What I can tell you is that if you installed it manually (by building it from code) or from a third party archive outside of Ubuntu then there is absolutely no way to guarantee dependency solving. If you did install it from an Ubuntu official archive and it's broken, then you should file a bug report.

---

### Post by ajgreeny on 2018-05-20
I have recoll installed in my 16.04 and the missing helpers are all available for that. I have not looked in 18.04 if that is what you are using, but will do so tomorrow.

Search for python-mutagen and antiword in synaptic (name only) again after refreshing the repos and you may find the packages you need. Search also for exif in synaptic and install that as well; I'm have that package installed and do not get that missing helper notification.

---

### Post by briar rabbit on 2018-05-23
I thank you for the help.

I am running along digitally on a 16.04.4 LTS.

I DOWNLOADED the missing files.

I put all the pdfs I want to search in one folder. Is a DIRECTORY and a FOLDER the same thing.  It seems I have detected that a name does not mean a whole lot but sometimes it does.

Recoll will not let me change the indexed folder or is it a directory - at least that is what seems apparent from my working with it HOWEVER as best I understand my computer it does not allow me permission to know everything it is doing anyway or even let me know the few things that I ask it what it is doing - as a side note my "SYSTEM MONITOR" indicator on my panel can be running wild BUT when I open the "SYSTEM MONITOR" the only process (or anything for that matter) it shows to be running is "MATE-SYSTEM-MONITOR".  So, what is using up resources at 60 percent and better ..... - that is a secret I do not posses permission to obtain.  Back to my request for help.

I decided to "COMPLETELY REMOVAL of RECOLL" - I also REMOVED the three other programs???? (if thats what they are called at the moment).  I restarted my computer from hell and opened my recoll manual and then opened recoll.  To my COMPLETE surprise - I never would have expected this no not in a million years because computers do do as they are told - right.  I opened recoll after a complete removal and shut down of the computer then an installation and when I opened recoll for the first time the index that was on before the COMPLETE REMOVAL was right where I had left it  ...... BUT I did not want it there which was the WHOLE reason I did the COMPLETE removal and then a new install even after turning off the computer in between and everything* (everything is a personal perspective).

So, duh, if anyone is still listening - how do I remove an index that I do not want and put in an index I do want?


Knowing how ignorant I am I just repeated the above process and the first indexed folder is still there same as first time.  What I did not mention above because I thought I would be able to get rid of the first indexed directory with a COMPLETE REMOVAL and then a fresh install is this:
WHEN I DID A SEARCH OF THE INDEXED FOLDER -  the results were from all over my computer NOT JUST THE INDEXED FOLDER THAT WAS SHOWN TO BE SEARCHED ... . what is up with that?

how is the search for a particular directory supposed to happen - if you just keep seeing results from the origianl DIRECTORY/FOLDER?

Is there a way of having recoll SHOW the folder "DIRECTORY" it is search - while the search is in progress, happening, going on, being done, progressing, etc., etc.

---

### Post by medoc92 on 2018-05-28
Uninstalling ("removing") Recoll does not reset the index (many users would object to this).

Use "Rebuild index" from the File menu if you want to restart from an empty index

You can also use a "dir:" directive in the search (in query language mode) to restrict the results to a subset of the directories.

Example: myterm dir:mydirname would return documents containing the term "myterm" and located in any directory named "mydirname"
You can use a more complete path for the dir: directive to restrict the results further, for example dir:/home/me/mydirname

---

