---
title: "Javascript problems"
date: 2008-04-10
forum: Programming Talk
---

### Post by Sugz on 2008-04-10
So, heres the problem.
I have an input form where the user enters numerous pieces of data. 
And i have numerous .js files refering to different functions that the form performs, This All worked like clock work when All the Javascript was in one File 
But now that i have split them up, they do not seem to work properly.

One particular problem is refering to a form object to retrieve its Value. Here is the Code

var daydrop=document.forms["Bookingform"].elements["daydrop"].value;

Ok so this retrieves that Day that the user has selected.
When this was all in one file it worked no problems. But now i get the following error

Error: document.forms.Bookingform is undefined

I do however declare the same variable in the same way in a different .js form. 
But this seems to be a strange problem

Any help will be greatly appreciated

---

### Post by smartbei on 2008-04-10
As is, I am not sure what the problem is. I think it will be beneficial if you could post/link to the relevant html pags and js files.

---

### Post by Sugz on 2008-04-12
Ok ill provide some more details here:

This is a Booking form where the user goes from choosing dates, to booking info to equipment hire to personal details.

Then the user clicks a button that 'completes' the booking and shows a Form which contains all the information that they selected in an easy to read List.

The problem is I got this working But every Javascript function was contained in one .JS file.

Now as im adding ew features i needed to split the functions into different .js Files for ease of use and debugging.

But now because i split up the functions they do not work properly, even through i have declared variables correctly, Pointed the HTML to the correct .js files. etc.

The line which is giving me grief is the lone that corresponds to retrieving each of the form elements value and putting them into a variable for example

```
var Town=document.forms["Bookingform"].elements["Town"].value;
var County=document.forms["Bookingform"].elements["county"].value;
var Pcode=document.forms["Bookingform"].elements["Pcode"].value;
```

Here the code grabs the value of form element Town from the form Booking form and puts this value into variable Town
for use later on.

THe problem is that i keep on getting the following error according to Firefox Error console

Error: document.forms.Bookingform is undefined

However this WORKED when EVERYTHING was in a single .JS file

Sorry im a bit reluctant to hand out my code as im a bit funny when it comes to freely distributing my code. And yes i know the whole concept of open source but i can send one or mabe a few to you if you request..

Any help again is appreciated

-Sugz

---

### Post by smartbei on 2008-04-12
I am willing to take a closer look at it.

If you want to, stick it on a server and PM me the link.

---

