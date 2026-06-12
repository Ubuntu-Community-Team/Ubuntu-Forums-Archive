---
title: "Send login details from bash to webpage ?"
date: 2007-09-13
forum: Programming Talk
---

### Post by clash on 2007-09-13
Ok heres the situation. 

I am writing a small script to automatically login to a website. I'm after hitting a stumbling block, i.e > I have no idea how to enter a username and password into the correct textboxes on a webpage from the terminal. 

Anyone point me in the right direction ?

Can this be done from bash ?

---

### Post by bobbocanfly on 2007-09-13
Depends on what website. If it was a PHP website using GET options it would be fairly easy

```
firefox http://www.website.com/index.php?username=$username
```

If it is for filling in text fields then you would probably have to use Javascript to edit it.

---

### Post by clash on 2007-09-13
Actually i've another question ...

I want to be able to do all the below from a bash script

1. Go to a webpage and "click" a button. i.e > send a "submit" with a certain value. 
2. On the next page i want to enter details in a textfield. 

Your saying i'd need to do it in javascript ? I know i seen a script somewhere before that used perl to enter the details in the appropriate fields.

---

### Post by CptPicard on 2007-09-13
You really ought to be doing this from a programming language with a proper http client library. Like, Python or something :)

The biggest problem you'll be facing with bash is that after logging in, you probably have a session going on the server side, and even if there was a session key encoded in the url (more often these days it's a cookie), you're going to have an awful time patching things together in bash so that you can use wget for your server interaction.

Use the right tool for the job and so on :)

---

### Post by clash on 2007-09-13
Point taken Mon Capitán!

I thought it was a really small job, it ain't. 

Will go looking into python or perl, thanks.

---

### Post by pointone on 2007-09-13
Check out the ClientForm module for Python.

---

### Post by SupremeOverlord on 2008-08-30
This thread seems to be kind of old now.  Did you ever get the script to work and did you release the source code?  I need to do something similar and would benefit greatly by seeing your approach.

---

