---
title: "Libre draw hijacking pdf"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by senorian on 2011-10-23
How do I prevent LO Draw from hijacking pdf apps ?
If I click on "other" it sends me to "choose helper application" but this just has 2 files that have nothing to do with opening a pdf.
This is the title:
Honey Authenticity: a Review
and this is the site:
[www.culturaapicola.com.ar/](www.culturaapicola.com.ar/).

I can uninstall LO and that allows the default "document viewer" to open the pdf.
Of course it is not desirable to have to do this
Thanks

---

### Post by gsmanners on 2011-10-23
Right click the file and select "Properties..." Then change the "Open With" selection to "Document Viewer" or whatever you want to use for pdf files.

---

### Post by senorian on 2011-10-23
Thanks but I failed to describe the problem correctly
This is the listing in google:
PDF] 
Honey Authenticity: a Review

right clicking on this does not bring up any window (or anything at all ) with "properties".
left clicking brings up "open with Libre office draw (default)
clicking on this shows another line exactly as above and a further line under with "other"
clicking on this "other" brings up a window showing my home folder and all other folders . nothing to do with this file which I have not downloaded as yet.
Sorry to have mislead you
thanks

---

### Post by gsmanners on 2011-10-23
You're not about to "Save File"? I looked at that site and there is no PDF file there that I could see.

---

### Post by senorian on 2011-10-23
WOW
no you have me confused
I just entered the following in google:
Honey Authenticity: a Review
and
got the standard window to download a pdf file
which as detailed limits me to LO.

sorry. I must be doing something very different from you
I hope you can explain how i get a pdf and you don't
Thanks

---

### Post by gsmanners on 2011-10-23
Sorry, I'm just wondering why you're relying so heavily on your browser.

---

### Post by senorian on 2011-10-24
I did not realize that there is an alternative(s)
Please point me to a tutorial ( or page)that explains the alternatives that I can use
thanks

EDIT
I have xubuntu 11.04 
athlon 640x4 
asus gts 450

---

### Post by blackbird34 on 2011-10-24
Hi. Hope I've understood properly:
You've got a list of google results. The one you want starts with [PDF]. You click on it and firefox brings up a window offering to OPEN it WITH "LibreOffice (default)" (and doesn't offer Document Viewer) or SAVE it. 
Can't you just click "save", download the file to, say, your downloads folder, and then open it from the file manager??

---

### Post by Toz on 2011-10-24
Assuming firefox, when you select "Other..." and bring up the "Choose Helper Application" dialog, go to the left pane and select "File System", then on the right pane select "usr", then "bin" then locate and click on "evince", then click the "Open" button at the bottom of the dialog.

You will return to the original firefox "Open" dialog, but now with Evince as the application to open with. Click OK. This setting will be saved for future pdf views (See Preferences->Applications).

---

### Post by senorian on 2011-10-24
blackbird34
many thanks
My own stupidity..I never thought to save it and then open it

---

### Post by senorian on 2011-10-24
Toz
very many thanks
your instructions not only solve the immediate problem but also show that the solution will be saved in the future
Thanks to both you and blackbird34

---

### Post by senorian on 2011-10-24
toz
very many thanks 
Your solution not only solves the immediate problem but shows me that it will be permanent
many thanks to you and blackbird34

ps i tried to put "solved" on my first post but it appeared at the bottom of the post. sorry

---

### Post by senorian on 2011-10-24
toz
slight problem
after selecting "usr" i must click "open" (?) and then select "bin" and then click "open" (?)
and then "locate evince"
but the search button on the page does not find "evince"
where oh where can "evince" be hiding?
thanks for your time

---

### Post by Toz on 2011-10-24
Perhaps evince isn't installed. evince is the default xubuntu pdf viewer. Look for it in the software center (its called "Document Viewer" there, but just filter on the word evince) and install it - if it is not installed. 

Or install it quickly via the command prompt:
```
sudo apt-get install evince
```

---

### Post by senorian on 2011-10-25
toz
very many thanks
found it listed as  "epdfview"

---

