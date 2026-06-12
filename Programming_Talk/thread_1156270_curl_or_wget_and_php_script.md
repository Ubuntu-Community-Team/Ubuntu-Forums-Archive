---
title: "curl or wget and php script"
date: 2009-05-11
forum: Programming Talk
---

### Post by Greslore on 2009-05-11
Need some advice on this one.

I go to a URL via Firefox [http://www.example.com/blah.php](http://www.example.com/blah.php) which runs "blah.php" which performs some db maintenance requiring no input from me.  After about 5 minutes it simply returns saying "DONE!" to the web browser.  

Now, I want to throw this into a nightly cron job, but I am having a heck of a time coming up with a way of running that blah.php and then capturing that "DONE!" to a txt file from a shell script.  I believe I can use wget or curl to do this?

---

### Post by Schitso on 2009-05-11
The page load doesn't time out in five minutes?

---

### Post by Greslore on 2009-05-11
> **Schitso said:**
> The page load doesn't time out in five minutes?

Nope - Apache is set to a higher threshold for time outs.

---

### Post by Schitso on 2009-05-11
Check out the -O option for wget

---

### Post by pshah on 2009-05-14
Try this command:

wget -O /path/to/txtfile "http://www.example.com/blah.php"

It should save the output in the text file.

---

