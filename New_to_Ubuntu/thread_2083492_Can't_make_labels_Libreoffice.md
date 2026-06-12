---
title: "Can't make labels Libreoffice"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by bandito40 on 2012-11-12
Hi,

I am trying to make labels from a database in LO but I can get as far as creating the document but not being able to populate the labels with data from the database. Here is a picture that shows my progress. The black marks are to block out personal data.

[IMG]http://i1065.photobucket.com/albums/u381/mazdawarrior/Screenshotfrom2012-11-12182728.png[/IMG]

Anyone know what to do next?

---

### Post by audiomick on 2012-11-12
HI. I am still on Open Office, but I use that process for writing Invoices. I think it should be much the same. You need to have chosen the right address book in the panel at the top left. Then you use the icon with a magnifying glass over a sheet of paper to search the address you want. Then you use the icon that looks a bit like this >some text< to insert the address data in the data fields. I only ever do one address at a time, i.e. no chain letters, so I am not too sure about multiple addresses. You'll have to experiment with that yourself.


Edit: no wait a minute. On the second glance, I see that you have the same data field repeated. I suspect that what I described will put the first address chosen onto every label. I assume that the process is similar to what I have described, but there must be something to say "label 1", "label 2" and so on. I'll have a look at the help. I'll get back in a minute...

---

### Post by audiomick on 2012-11-12
Ok, I would suggest having a look at the LO help and searching for "labels". I went on to a further link from there about "serial letters" or something similar. I would have posted a screenshot, but mine is in german...

Anyway, in there, there is reference to using "all data sets" or "selected data sets". I think that is where you need to be looking.

---

### Post by DuckHook on 2012-11-13
If this is the same issue that I ran into, then the problem is due to the fact that you have only partially installed LibreOffice. If you chose the various LibreOffice components individually from Software Center thinking that LibreOffice is equivalent to the sum of its parts, then you will only have a partial install. You must choose the LibreOffice Suite metapackage from Software Center. This will install the backend database modules and other dependencies that LibreOffice needs to generate labels and envelopes. If this is already how you installed, then I'm stumped.

---

### Post by audiomick on 2012-11-13
> **DuckHook said:**
> This will install the backend database modules and other dependencies that LibreOffice needs to generate labels and envelopes.

Ah, now that you mentioned it, I think I might have had to install some further modules for Open Office to make my process work. Not really sure, but I think so...

---

### Post by Zill on 2012-11-13
bandito40:  Assuming you want a different address on each label, I suggest you should use the "mail-merge" facility.  The "Help" within the L.O. application itself should prove useful but this link may also be of assistance:
[Mail Merge Address Labels]("http://blog.worldlabel.com/2012/mail-merge-address-labels-in-the-excellent-free-libreoffice.html")

Caveat:  I haven't personally run a mail-merge from Base as I use a Calc spreadsheet as a data source.  If you do have problems with this then you may get better support directly from the [LibreOffice forums]("http://en.libreofficeforum.org/").

---

### Post by bandito40 on 2012-11-13
Looks like the meta packages solved the problem but then again I didn't select all the labels in the document and then select all the entries in my database and press "data to fields" button.

Now I just have to figure out why I only get one column of labels and not 2.  I am using Avery 5162 which LO has as a template.

Thanks for all your help.

---

