---
title: "[SOLVED] shell script writing to crontab"
date: 2007-11-23
forum: Programming Talk
---

### Post by mdpalow on 2007-11-23
Hi everyone,

I'm working on an sh script that will, among other things, take some input from user and then write it into crontab.

The entire script works perfectly so far except for the part where it's suppose to write to crontab; the most important part. LOL

I've tested the script with a blank file I placed on my Desktop and it writes to it perfectly, So - I know the code is right. However, when I change the file to be written to back to crontab; it doesn't work. 

I can only assume this is a permissions problem as crontab is owned by root.

I did put sudo before the echo command, but no luck.

I also tried changing the permissions on the file first, so I could write to it and then change it back after it's been written to, but no luck with chmod.

I'm thinking the problem is I either didn't change the permissions correctly with chmod or maybe I need to chown as well. 

If so, can anyone tell me what the correct permissions would need to be in order to write to this file and what the original permissions would be when I change it back using chmod?

Also, should I chown crontab to $USER or maybe do a combination of chown and chmod?

OR... am I completely off target with thinking chown/chmod is the solutioin?

Thank you in advance ...

---

### Post by LaRoza on 2007-11-23
Run the script as root.

Don't chmod files unless you really, really want to.

---

### Post by volanin on 2007-11-23
```
$ sudo sh -c "echo [STUFF] > /etc/crontab"
```

---

### Post by mdpalow on 2007-11-23
> **LaRoza said:**
> Run the script as root.

Don't chmod files unless you really, really want to.

How do you run as root if the script is a function within a much larger script and I only want to run as root for this one and only function?

thanks...

---

### Post by mdpalow on 2007-11-23
> **volanin said:**
> ```
$ sudo sh -c "echo [STUFF] > /etc/crontab"
```

I tried this, but with no luck.

sudo sh -c echo "$min $hr    * * *   root    /home/$USER/Cron/some_file.sh" >> /etc/crontab

---

### Post by volanin on 2007-11-23
No no!
Check both your quotes position ("...") and asterisks escaping (\*).

Correct:
```
sudo sh -c "echo $min $hr \* \* \* root /home/$USER/Cron/some_file.sh >> /etc/crontab"
```

Wrong:
```
sudo sh -c echo "$min $hr * * * root /home/$USER/Cron/some_file.sh" >> /etc/crontab
```

---

### Post by mdpalow on 2007-11-23
No, that didn't work either and I copied it just like you had.

Not even sure how that could work since 'echo' is within the quotes and therefore doesn't echo anything....

I have to believe the script has to be run as root, but I'm having difficulty getting that to work since this is only a small portion of the entire script - AND, I don't want to run the entire script as root.

---

### Post by volanin on 2007-11-23
> **mdpalow said:**
> Not even sure how that could work since 'echo' is within the quotes and therefore doesn't echo anything...

***Echo*** must be within quotes.
Indeed, everything inside the quotes is a parameter to ***sh -c***
If you put it outside the quotes, the redirector ***>>*** won't work.


Do a test for me ok.
Open your bash terminal and copy/paste this:

[b][i]STRING="Test ok"
sudo sh -c "echo $STRING > /TEST"[/i][/b]

And check if the file /TEST was created with the string inside it.
If it works, make a  backup of your current crontab and run this directly in bash as well:

[b][i]STRING="This will overwrite crontab"
sudo sh -c "echo $STRING > /etc/crontab"[/i][/b]

It should work.
There is no reason for your script to fail.
Must be some very simple thing that we are overlooking.

---

### Post by mdpalow on 2007-11-23
STRING="Test ok"
sudo sh -c "echo $STRING > /TEST"


Did NOT work...

---

### Post by mdpalow on 2007-11-23
Thanks for your help so far volanin...

As a simple test, I just ran:

#!/bin/bash

echo -n "Name? "
read name
cd /home/$USER/Desktop
sudo cp Test1.txt /etc/Test1.txt

sudo echo "$name" > /etc/Test1.txt

... and it didn't work. However, when the Test1.txt file was on my Desktop; it worked fine.

when trying in /etc

Says:  line 8: /etc/Test1.txt: Permission denied

---

### Post by mdpalow on 2007-11-23
Ok, I just did:

chown root file_name
chmod 4755 file_name 

and it worked.

Problem is, I don't want the entire script to be changed to this. I just want this snippet of code to be run as root. The entire script is made up of many separate functions and this example is just a dry-run to test the concept of a different set of commands. In other words, I made this script really easy just to test writing to a crontab file.

Does anyone have any ideas??

---

### Post by tonyhawz on 2007-11-23
I think that if the scripts is going to modify some file under /etc then the hole script should be run as root.
I mean , you can have the other parts of your script running as a normal user, but when it comes the part were it writes crontab, it is ok to fail.
sudo the hole script.

---

### Post by mdpalow on 2007-11-23
I spoke too soon.

Writing to Test1.txt in /etc worked, but I just changed it to write to crontab and nothing again...

---

### Post by volanin on 2007-11-23
Mdpalow, I really don't know what's going on.
I just tested this script here, and it worked perfectly:

```
#!/bin/sh

hr=3
min=20
sudo sh -c "echo $min $hr \* \* \* root /home/$USER/Cron/some_file.sh >> /etc/crontab"
```

I am even sending it attached for you to try as well.
No chown, no chmod... just gunzip it.

Is your username allowed in sudo?
Is the root partition mounted read-write?

---

### Post by mdpalow on 2007-11-23
Success :)

Thank you very much volanin... that did it. 

I appreciate you sticking it out and going as far as to write it out AND test it.

+5 for you.. :KS

---

### Post by volanin on 2007-11-23
No problem!
:)

---

