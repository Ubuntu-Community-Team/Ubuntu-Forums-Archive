---
title: "Oh help admin directory problem"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-09-13
Not my day!!!

**sudo apt-get install openoffice**


jacky@jacky-Aspire-6930G:~$ sudo apt-get install openoffice
[sudo] password for jacky: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jacky@jacky-Aspire-6930G:~$ ^C
jacky@jacky-Aspire-6930G:~$ 


I keep getting that whatever I try to do in the terminal. How do I unpick it?x

---

### Post by kimberlite on 2012-09-13
Be sure that Synaptic or any other package manager is not running.

---

### Post by Jackalyn on 2012-09-14
OK thanks. Will try that. I did yesterday and got the same message, but today is a new day!

---

### Post by Jakin on 2012-09-14
> **Jackalyn said:**
> OK thanks. Will try that. I did yesterday and got the same message, but today is a new day!

Well, if you keep getting the error, do what i do 

terminal: 

sudo rm /var/lib/apt/lists/lock*
sudo apt-get clean
sudo apt-get update

Works for me everytime- what has happened is there was a partial download and install of a package that did not complete. So the package has a "lock" on dpkg.

---

