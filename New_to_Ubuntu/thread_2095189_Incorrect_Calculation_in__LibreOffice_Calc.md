---
title: "Incorrect Calculation in  LibreOffice Calc"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by wstay on 2012-12-16
I am using LibreOffice Calc. on Ubuntu 10.04.
Can someone please explain why I cannot get my calculation correct.
Please refer to attachments.
In Sreenshot-1, the sum total from Cell L6 to L10 should be 2364.94 in L11..
It is giving an incorrect total of 959.74 which is from Cell L7 to L10 in L11.
Why is it missing out or not reading Cell L6 when my total sum should be 2364.94 from Cell L6 to L10 as in Sreenshot-2.

---

### Post by bouncingwilf on 2012-12-16
The only thing I can think of is that cell l6 is being read as a text cell rather than a number - It may be worth checking that there is no leading space on the number. I assume that the comma thousands separator is the standard Malay usage and that it has been formatted automatically ( in which case the spreadsheet does think it's a number) and I have no further ideas to offer.


semoga berjaya

Bouncingwilf

---

### Post by sunfromhere on 2012-12-16
Try to establish does the error occur if you write the number as 1234.56 instead of 1,234.56. If it doesn't, then right click the said cell and check the cell formating (if indeed it is numbers in format #,###.00 and thousands separator checked).

I tried reproducing your problem and wasn't successful, my Calc correctly adds 1,234.56 to other numbers. 

Which version of the LO are you using?

---

### Post by Abhinav Kumar on 2012-12-16
Hi ,
I tried reproducing your problem but was getting the correct results as supposed to be.

However, I think you may have first calculated the sum and then would have inserted the row 6 which may not have updated the referencing.
So try running the sum feature again. May be that fixes your problem.

Regards,
Abhinav

---

### Post by vasa1 on 2012-12-16
This may not be relevant but there's something odd with row 6 which has "KUCHING SPECIALIST". Its lower border looks like something has "happened to it".

The forum allows attaching .ods files so why don't you make a sheet that demonstrates the issue and attach it in case your problem persists?

---

### Post by wstay on 2012-12-16
I found out now the number in cell L6 has a ` (I don't know what to call it) in front of the number like `1405.20.
After I delete the sign ` from `1405.20, I got the total sum in cell L11 correct.

---

### Post by pqwoerituytrueiwoq on 2012-12-16
i believe it is called a tick

---

### Post by haqking on 2012-12-16
> **wstay said:**
> I found out now the number in cell L6 has a ` (I don't know what to call it) in front of the number like `1405.20.
After I delete the sign ` from `1405.20, I got the total sum in cell L11 correct.

> **pqwoerituytrueiwoq said:**
> i believe it is called a tick

It is a diacritical mark known as a Grave Accent or more commonly a Back Tick

---

### Post by vasa1 on 2012-12-16
> **haqking said:**
> It is a diacritical mark known as a Grave Accent or more commonly a Back Tick

In this particular case, it is the **single quote** commonly located next to the enter key.

---

### Post by haqking on 2012-12-16
> **wstay said:**
> I found out now the number in cell L6 has a ` (I don't know what to call it) in front of the number like **`**1405.20.
After I delete the sign ` from `1405.20, I got the total sum in cell L11 correct.

> **vasa1 said:**
> In this particular case, it is the **single quote** commonly located next to the enter key.

That is not a single quote, it is a Grave Accent/Back Tick ` where as a single quote would be '

---

### Post by vasa1 on 2012-12-16
> **haqking said:**
> That is not a single quote, it is a Grave Accent/Back Tick ` where as a single quote would be '
Okay :)

---

### Post by vasa1 on 2012-12-16
> **haqking said:**
> That is not a single quote, it is a Grave Accent/Back Tick ` where as a single quote would be '
Do you use LibreOffice Calc? If so, then see what you get when you do this:
Type **`123** in a new spreadsheet and hit enter (This is the grave key)
Type **'123** in another cell and hit enter (This is the single quote key)

Notice what is seen in the two cells. In the first cell, you should see **`123**.
In the second, you should see **123**. The single quote becomes invisible since it has a special meaning.

The second case is what the thread is about. Nevermind that OP used **`** to describe the single quote. Which why I specified in **this particular case**.

The presence of a single quote in front of numbers is quite common when importing stuff from Excel.

A quick way to clean up such occurrences is this. Select the relevant range. Use Alt, Edit, Replace and enable regex. Then in the search box type **.+** and in the replace box type **&** and hit enter. I got this tip over here: [http://user.services.openoffice.org/en/forum/viewtopic.php?f=9&t=26626&p=121627#p121137](http://user.services.openoffice.org/en/forum/viewtopic.php?f=9&t=26626&p=121627#p121137)

LibreOffice has the option, while importing stuff, to "Detect special numbers". That's the GUI way to get rid of the ' (not the `).

---

### Post by haqking on 2012-12-16
> **vasa1 said:**
> Do you use LibreOffice Calc? If so, then see what you get when you do this:
Type **`123** in a new spreadsheet and hit enter (This is the grave key)
Type **'123** in another cell and hit enter (This is the single quote key)

Notice what is seen in the two cells. In the first cell, you should see **`123**.
In the second, you should see **123**. The single quote becomes invisible since it has a special meaning.

The second case is what the thread is about. Nevermind that OP used **`** to describe the single quote. Which why I specified in **this particular case**.

The presence of a single quote in front of numbers is quite common when importing stuff from Excel.

A quick way to clean up such occurrences is this. Select the relevant range. Use Alt, Edit, Replace and enable regex. Then in the search box type **.+** and in the replace box type **&** and hit enter. I got this tip over here: [http://user.services.openoffice.org/en/forum/viewtopic.php?f=9&t=26626&p=121627#p121137](http://user.services.openoffice.org/en/forum/viewtopic.php?f=9&t=26626&p=121627#p121137)

LibreOffice has the option, while importing stuff, to "Detect special numbers". That's the GUI way to get rid of the ' (not the `).

I was responding to post #6 and #7 where post #6 didnt know the name for the ` and post #7 referred to it as a tick, I CORRECTLY informed them it was a Grave Accent/Back Tick, so nothing has changed.

Peace

---

