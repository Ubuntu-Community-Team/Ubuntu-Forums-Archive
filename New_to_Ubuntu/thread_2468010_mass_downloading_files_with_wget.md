---
title: "mass downloading files with wget"
date: 2021-10-15
forum: New to Ubuntu
---

### Post by carb0nf1b3r on 2021-10-15
Hi thank you for your time and i apologize if this has been answered before but i am trying to download all the files from this url [https://archive.org/download/no-intro_romsets/no-intro%20romsets/](https://archive.org/download/no-intro_romsets/no-intro%20romsets/)  to a usb drive on my pc with wget. I am a very inexperienced user and could really use some help.

---

### Post by CharlesA on 2021-10-15
You probably should have read the page you were trying to download as it says:

> Files marked with **lock** are not available for download.

And all the files there have a lock icon next to them.

---

### Post by ActionParsnip on 2021-10-16
Somebody didn't read the man pages but this gives an example
[https://stackoverflow.com/questions/273743/using-wget-to-recursively-fetch-a-directory-with-arbitrary-files-in-it](https://stackoverflow.com/questions/273743/using-wget-to-recursively-fetch-a-directory-with-arbitrary-files-in-it)

---

### Post by Tadaen_Sylvermane on 2021-10-16
> This archive got marked recently as "high bandwidth":
"Items in this collection consume an unusually large amount of archive.org's outbound bandwidth and may be subject to various limiting schemes." 
And as result, now it's required to log in order to be able to download this archive files, sorry about inconvenience, can't change that :S ... 

The reason they are locked. You will need to log in. Is on their front page.

That being said if you can get a list of filenames you should be able to wget in a for loop or something.

---

