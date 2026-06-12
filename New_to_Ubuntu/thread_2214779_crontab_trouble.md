---
title: "crontab trouble"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by sammykur on 2014-04-03
Hello -I am new to ubuntu and really am liking it.

My question is this: I have created an sh file in my home directory and can run it in terminal fine.
 I have run crontab -e and edited it.when I run crontab-l,I get the following

                                         */10 * * * * /home/getquote.sh    (getquote.sh being the file name).

However it does not seem to autoexecute. I am wanting it to execute every 10 mins.I have read the other posts i could find on the subject and dont quite get why this wouldnt work.

  -Also the file is being saved to /tmp/crontab.b76sg0/crontab, is this correct? I want to keep the file on shutdown.


I am using ubuntu 12.04 

The SH file is to automate downloading of a csv. file

---

### Post by vasa1 on 2014-04-03
People will need to see the contents of getquote.sh.

Each time you run crontab -e and save the file, it will make up a random name but your contents are safe. It will survive shutdown.

---

### Post by sammykur on 2014-04-03
Sorry I didnt realize that the contents of the SH file would be necessary as it does run from the terminal fine.

Contents of SH are this:


#!/bin/sh
curl -s 'http://download.finance.yahoo.com/d/quotes.csv?s=USDCAD=X,BCE.TO,CSCO,MSFT,INTC&f=sl1d1t1c1ohgv&e=.csv' | tee quotes.csv


I do have a quotes.csv file in my home directory and the info does update when it is ran in terminal.
Also I used the Nano editor.


Sorry but i have to go I will check back on this post.

 Thanks to vasa and those who reply
.






Thanks for your patiences

---

### Post by ajgreeny on 2014-04-03
If the pathway you showed in your original post is what you had in the crontab it is probably not valid.

**/home/getquote.sh** should be the full pathway, probably **/home/*<username*>/getquote.sh** where username is your user, but it will depend, of course on exactly where the shell script is.

---

### Post by vasa1 on 2014-04-03
> **sammykur said:**
> Sorry I didnt realize that the contents of the SH file would be necessary as it does run from the terminal fine.
...
Actually, that's quite common:
[http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work](http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work)

---

### Post by sammykur on 2014-04-03
Thank you both,  I now have something to go off of. sorry i didnt see  the does not work link first - it really helped me figure out what was going on. I think I have another problem i need to fix first with my directories. I will do some googling and see what i come up with, if that doesnt answer it i guess i will have a different question to post.

Thank you both and sorry i asked for something that was already posted. I usually can find my answers on here or google without having to post a question, but i was up late last night and must have missed it.


Also Thanks to all who post answers here 
Ii have used this forumn as a source of info for about three weeks now (when i first started using ubuntu) and it has been an invaluable resource.

by the way   Who would want to have to touch their screen?

 Getting fingerprints all over the screen you are trying to view to me seems troublesome.

---

### Post by sammykur on 2014-04-04
Just wanted to thank everyone again and let you know i did get the cronjob running.
I made several mistakes when trying to follow an online guide to setting this up.
1. wrong directory 
2.because cronjobs dont follow the same path i had to specify the path in crontabs 
3. when i created the file i did not check "allow executing file as program"

Now on to importing the info into calc!

---

### Post by ajgreeny on 2014-04-04
Yes, it is always correct to use the full pathway in cronjobs, eg **/home/user/Desktop/file.sh**, not just **Desktop/file/sh** as cron will never be able to find the shortened path, nor **~/Desktop/file.sh** which will work in terminal but not cron.

---

