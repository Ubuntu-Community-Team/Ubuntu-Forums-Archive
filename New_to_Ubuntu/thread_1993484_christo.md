---
title: "christo"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by moutonc on 2012-06-02
Newcomer - I wiped vista from my laptop (marriage over). Installed ubuntu 11.10 then upgraded to 12.04. I have problems with 3G connectivity and apparently the modem manager crashes. There is much info on this topic but i cannot figure out how to solve it. I cannot find an executable file (just download and install) and seem to have to use the terminal. I know how to use it (more or less) but the exact commands i have to use confuses me. 
I will appreciate so much if i can get guidance that will show:*** " begin" xxxx ................ xxxxxx "press enter"*** then do..... whatever!

I need support "idiot style" - think its my age!

:KSRegards Everyone!
christo

---

### Post by inashdeen on 2012-06-02
to run a modem on ubuntu you need to plug your modem > wait a while > click on the fan like/ wifi like logo next to the clock on the top bar > click new GSM broadband > and follow the step by step procedure. most of the time you dont need a terminal for that. it is so..... 9.04?

by the way, what is your modem model?

---

### Post by moutonc on 2012-06-02
Thanks for responding - everything exactly as you said with 11.10 but with 12.04 the modem manager crashes. Nokia RD-10 works well on 10.10. From the discussions on the net (google search) there seem to be some fixes to be done via the terminal???

Christo

---

### Post by inashdeen on 2012-06-02
A simpler solution would be [sakis 3g]("http://www.sakis3g.org/"). used em. user friendly :)

---

### Post by moutonc on 2012-06-02
My apology - the modem works well on 11.10 (not 10.10). I am currently running dual boot between Ubuntu 11.10 and 12.04

---

### Post by inashdeen on 2012-06-02
have you tried the sakis 3g? it is basically gui for the command line you are saying.

---

### Post by moutonc on 2012-06-02
I must confess - i thought you were referring to another type of 3g modem!
Only with your last reply i realised your are referring to entering a command in the terminal. 
Doing a google search, i found the following under ubuntu sakis 3g. Back to my original question; which of this info must appear on the command line - how do i actually do it? 
What is the implication of this instruction?
**Ubuntu** sudo bash apt-get install ppp cd /usr/bin wget '[http://www.sakis3g.org/versions/latest/sakis3g.gz']("http://www.sakis3g.org/versions/latest/sakis3g.gz%27") echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c **You should see:** sakis3g.gz: OK gunzip sakis3g.gz chmod +x sakis3g

---

### Post by inashdeen on 2012-06-02
to be honest , i dont really get the last part of your message. didnt the sakis 3g an autoinstaller script. after you install, you just click the icon and follow the step by step procedure on sakis 3g. quite similar to the default ubuntu modem manager. after done that, it will autogenerate the command for you.


Ok,let me share how to use it step by step. first download the file from here [http://www.sakis3g.org/#downloading](http://www.sakis3g.org/#downloading)

depending on your OS, it will either be i386 or 64

after download, extract the file. I prefer either extracting in home or desktop. 
after extract, right click on sakis3g > properties > permission > tick on executable > close.

now double click on the file. it will prompt to run or run in terminal. for debugging, i prefer running in terminal. but there is no problem to just click run. 

it will run, choose connect with 3g > usb modem > choose the model of your usb modem > just click ok on the setting it gave .

for apn and apn password, you may need to get it from your modem setting on other ubuntu. then it will connect your modem without any hassle :)

---

### Post by inashdeen on 2012-06-02
This is basically whats in your code you gave me :

sudo apt-get install ppp 
----> please install ppp. its an app of point-to-point protocol. not really sure what it does. 

cd /usr/bin
-----> set te command line to run from usr/bin

 wget 'http://www.sakis3g.org/versions/latest/sakis3g.gz' echo "dda70fd95fb952dbb979af88790d3f6e sakis3g.gz" | md5sum -c 
You should see: sakis3g.gz: OK 
-----> checking md5um. usually done to make sure that the file downloaded is valid

unzip sakis3g.gz chmod +x sakis3g
-----> unzipping and installing sakis 3g + giving it an administrator permission, which is by the way similar to right click > properties > permission > mark ar executable > close.

---

### Post by moutonc on 2012-06-02
Thanks - i am getting the picture. I will give it a go and be back soon!

---

### Post by Silent Warrior on 2012-06-02
Just a slight correction for the chmodding: +x makes the file executable (that is, unblocked). I'm not sure what the CLI-invocation is for giving something administrative rights (besides su/sudo), but I expect it's a variation of chuser/chgroup.

---

### Post by inashdeen on 2012-06-02
thanks for teh correction. that is more precise. by the way christo, would you mind changing the title of this thread. its kinda confusing

---

### Post by moutonc on 2012-06-02
Things are not going too well yet but  i have corrected the title!

The step by step procedure for installing Sakis3G works in 11.10 but in 12.04 only comes to the point of "connects to 3g" then gives an error.

There seem to be many complaints logged with this problem when i searched for "ubuntu 12.04 modem manager crash"

---

### Post by inashdeen on 2012-06-02
It is strange though, my modem works perfectly with my ubuntu 12.04 . and so does my sakis 3g. could it be that,,, your installation of ubuntu is faulty?

---

