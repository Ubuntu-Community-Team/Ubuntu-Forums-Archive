---
title: "PHP and accented characters"
date: 2008-10-21
forum: Programming Talk
---

### Post by Mbengi Bongi on 2008-10-21
Thanks to **Reiger**, I have a PHP script from which I run from a shell script.  The script reads data from a csv file, however some of my data contains accented characters e.g. **è** which display as **?**.

I originally started discussing this issue on this thread: [http://ubuntuforums.org/showthread.php?t=948725&page=3](http://ubuntuforums.org/showthread.php?t=948725&page=3)
but as it started going off-topic I thought I'd better create a new thread.

Can anyone help at all?

---

### Post by LaRoza on 2008-10-21
I just wrote a PHP script and printed that particular character.

Where does this character appear incorrectly? (What are you using to read it?)

---

### Post by Mbengi Bongi on 2008-10-22
I've just done a bit of checking and it seems it isn't a PHP issue at all, the data is from an Excel spreadsheet and it seems when I save it to *.csv format the UTF-8 encoding doesn't go right, so it looks like my data is the problem. :mad:

Does anyone know how to save an *.xls spreadsheet to *.csv with correct UTF-8 encoding? :confused:

---

### Post by Reiger on 2008-10-22
Yes. The trick would be to use OpenOffice. ;)

Well, you might find things are solved by using UTF-16 encoding. Don't have Excel on hand so I can't help you with pointing out where to find that option.

---

### Post by Mbengi Bongi on 2008-10-22
You were absolutely spot on again Reiger, I loaded my spreadsheet into Calc saved it in *.ods format then saved it as *.csv and it works.

The spreadsheet dervives from when I used to use Windows (long ago now!).  I was using Excel on my iMac (I dual boot Ubuntu) to try and convert it - duh!!!

I really appreciate all your help.

:guitar:

---

