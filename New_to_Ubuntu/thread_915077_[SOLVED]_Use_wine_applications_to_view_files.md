---
title: "[SOLVED] Use wine applications to view files?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-09-09
How can I get Microsoft office 2007 to open .doc files when I click on them? I already have office running flawlessly in wine (which I'm very pleased with:KS) id also like to setup a similar thing with firefox so that it will have an open with option so I can choose office 2007 instead of Open Office

PS: Please don't just tell me to use open office as if I wanted to I already would be;-)

---

### Post by billgoldberg on 2008-09-09
> **kamitsukai said:**
> How can I get Microsoft office 2007 to open .doc files when I click on them? I already have office running flawlessly in wine (which I'm very pleased with:KS) id also like to setup a similar thing with firefox so that it will have an open with option so I can choose office 2007 instead of Open Office

PS: Please don't just tell me to use open office as if I wanted to I already would be;-)

I have no idea how Wine works, but I guess you could just use the path to the launcher.

---

### Post by knix on 2008-09-09
1)Find the path to the executable.
2)Right click on document
3)Select Open with Other Application
4)select Use Custom Command
5)insert wine <path to executable>

---

### Post by Bölvaður on 2008-09-09
It seems like you are unable to open it from firefox. Isn't it like that you download the file and then you are suggested which program you should be used?
If so, then all you have to do is change the command of the .doc files (I think it is .docx in 2007)

aah, you can do what the guy above me said.

---

### Post by kamitsukai on 2008-09-09
well it didnt work :(

---

### Post by graben3 on 2008-09-09
> **knix said:**
> 
5)insert wine <path to executable>


Put your path to the executable in this format (keep quotes) :

wine "C:/Program Files/MicrosoftOffice/word.exe"

I just installed WinRAR to test if his works...

Here is what I wrote in the custom command :

wine "C:/Program Files/WinRar/WinRAR.exe"

and it Works !!!!

Also, pay attention to case... im not sure for wine but ubuntu IS CASE SENSITIVE...

---

### Post by kamitsukai on 2008-09-09
> **graben3 said:**
> Put your path to the executable in this format (keep quotes) :

wine "C:/Program Files/MicrosoftOffice/word.exe"

I just installed WinRAR to test if his works...

Here is what I wrote in the custom command :

wine "C:/Program Files/WinRar/WinRAR.exe"

and it Works !!!!

Also, pay attention to case... im not sure for wine but ubuntu IS CASE SENSITIVE...

Thanks that somewhat works it loads office 2007 although to a blank page:confused:

---

### Post by knix on 2008-09-09
> **graben3 said:**
> Put your path to the executable in this format (keep quotes) :

wine "C:/Program Files/MicrosoftOffice/word.exe"

I just installed WinRAR to test if his works...

Here is what I wrote in the custom command :

wine "C:/Program Files/WinRar/WinRAR.exe"

and it Works !!!!

Also, pay attention to case... im not sure for wine but ubuntu IS CASE SENSITIVE...

Ok. if there's anything with a space (e.g., Program Files, Linux isn't happy with the space. I replace program files with Program* and it worked.

Just tried something else. you can put it in quotes.

---

### Post by andy_blah on 2008-09-09
I don't quite understand why you wouldn't use Open Office, it's far more grat than M$'s software, but it might be a preference, tho it isn't much difference between the two.

---

### Post by Bölvaður on 2008-09-09
perhaps you need to add the path to the file at the end of the command, I know it sounds stupid in this context but I dont know what else to say.

---

### Post by kamitsukai on 2008-09-09
> **andy_blah said:**
> I don't quite understand why you wouldn't use Open Office, it's far more grat than M$'s software, but it might be a preference, tho it isn't much difference between the two.

well if I create a .doc file at college and then take it home on my pen drive and edit it, when I open back up with Microsoft office the formatting will be different and images will be out of place along with a whole host of other problems:(

---

### Post by mc4man on 2008-09-09
Have you tried using the custom command on r. click file -> properties -> open with -> add -> use a custom command  (set file association

May take a few tries if command is wrong
Also possibility it will continue to just open office


you could also try to browse to the exe if you've either set drive_c as a bookmark or when in browse dialog box hit Ctrl+h to show hidden dirs. (.wine

the only advantage of typing a comm. would be if there was a parameter you could add to the exe in event the file didn't open in office (?)

---

### Post by theproles on 2008-10-28
If you're looking for the correct directory text:

wine "/home/put your username here/.wine/drive_c/Program Files/Microsoft Office/Office12/ONENOTE.EXE"

Replace ONENOTE.EXE with WINWORD.EXE, etc.

This works somewhat.  The only problem is that it doesn't actually open the document.  It opens a blank microsoft word document.  Once you have word open, all you have to do is drag the icon of the doc to the newly opened word document.  

Yeah, I know, this method sucks.  If someone comes up with a better way of doing things, please post.

This method actually works if you want to create a launcher in Avant Windows Navigator.

---

### Post by aktiwers on 2008-10-28
Here is an option for you.. 
You could create a script from the script here:
[http://www.howtogeek.com/howto/ubuntu/add-open-with-gedit-to-the-right-click-menu-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/add-open-with-gedit-to-the-right-click-menu-in-ubuntu/)

Start by creating a new text document in, lets say your home folder. Call it word2007
Then copy paste the script from the link into it, though change the last line:

from:
```
gedit $filesall&
```to:
```
wine  "/home/put your username here/.wine/drive_c/Program Files/Microsoft Office/Office12/ONENOTE.EXE" $filesall&
```Change this path to the real path to your word2007 EXE file.

Save the document.

Open terminal and type :
```
sudo chmod u+x word2007
```Right-click a docx file, pick properties => open with => add => use a custom command
And add the script.

I think that would do the trick! (I am not 100% sure though.. let us know) :)

Or you could simply follow the links approach using my modification..  then you will have it in "right-click" menu instead..

---

### Post by kamitsukai on 2008-10-29
Well I solved this in the end, by using the crossover office application which manages to do this flawlessly:)

thanks anyway!

---

### Post by markharding557 on 2008-10-29
I use a small windows program called gediz for veiwing .nfo files i configured this to open from nautilus by selecting gediz.exe in the wine directory in nautilus preferences.
I presume the same principle should work for .doc

---

### Post by kamitsukai on 2008-10-30
> **markharding557 said:**
> I use a small windows program called gediz for veiwing .nfo files i configured this to open from nautilus by selecting gediz.exe in the wine directory in nautilus preferences.
I presume the same principle should work for .doc

Well yes technically it should:) but I think it's probably a bug in wine as it worked fine for me with office 2003 just not 2007:KS

---

### Post by random turnip on 2008-10-30
Easiest way would be to download and install the latest version of Open Office and use OO Wrighter

---

### Post by kamitsukai on 2008-10-31
> **random turnip said:**
> Easiest way would be to download and install the latest version of Open Office and use OO Wrighter

It's not completely compatible with office 2007 even when I save documents in compatibility mode for office 2003:mad:

---

### Post by dcroxton on 2009-03-17
I realize that this is marked solved, but it is not completely solved because it does not open the file itself, only the associated Office application.  I found a wonderful tutorial [here]("http://www.fewt.com/2008/06/how-to-get-office-2003-running-in-wine.html") that explains how to open the file in the appropriate application.  It involved creating a small shell script (full code provided) that you associate with the extension.

Sincerely,
Derek

---

### Post by kamitsukai on 2009-03-17
> **dcroxton said:**
> I realize that this is marked solved, but it is not completely solved because it does not open the file itself, only the associated Office application.  I found a wonderful tutorial [here]("http://www.fewt.com/2008/06/how-to-get-office-2003-running-in-wine.html") that explains how to open the file in the appropriate application.  It involved creating a small shell script (full code provided) that you associate with the extension.

Sincerely,
Derek

Thankyou;)

---

