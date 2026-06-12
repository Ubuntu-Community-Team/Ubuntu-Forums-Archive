---
title: "Potential Hack?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by mregister on 2008-09-15
Hello All,

I am new to Linux/Ubuntu and I have setup a Ubuntu/Lamp box and I was just looking through the apache2 log file and i have a lot of lines that read 70.63.86.162 - - [14/Sep/2008:11:38:09 -0500] "GET /~fareeda/ HTTP/1.1" 404 319 "-" "-". There is a long list of these and it seems that it's an alpabetical list of poetntial user names. That is just one line of many. What is this? What does it mean? Is this an attempted hack?

Thanks.

---

### Post by t0p on 2008-09-15
> **mregister said:**
> Hello All,

I am new to Linux/Ubuntu and I have setup a Ubuntu/Lamp box and I was just looking through the apache2 log file and i have a lot of lines that read 70.63.86.162 - - [14/Sep/2008:11:38:09 -0500] "GET /~fareeda/ HTTP/1.1" 404 319 "-" "-". There is a long list of these and it seems that it's an alpabetical list of poetntial user names. That is just one line of many. What is this? What does it mean? Is this an attempted hack?

Thanks.

Possibly... crackers use "dictionary files" to brute-force login/password combos and the like.  How many such entries are there in the log?

That IP address 70.63.86.162 is in a block registered to "Cape Fear Community College".  Is that a real college?  Does it mean anything to you?  Or anyone else?

---

### Post by mregister on 2008-09-15
there are a lot. It looks like a dictionary. They start with A and all the way through, just about every name there is. No the college does not mean anything to me. How did you find out what block it comes from. How do I stop that kind of attack. Wow I have a lot to learn.

---

### Post by anotherdisciple on 2008-09-15
Crazy! Is there any way to have ubuntu automatically check for brute force attacks? Say maybe it informs you that there have been a certain number of failed login attempts... at the GUI level... not console.

---

### Post by meborc on 2008-09-15
the absolute beginners section might not be the right place for this :)

try the security section - [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

they have all the knowledge you need...

---

### Post by bodhi.zazen on 2008-09-15
See this link :

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

Truth is these kinds of things are very common, take a look at ssh if you run it.

If I see a persistent IP -> black list the IP with iptables (UFW).

 [https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Advanced%20Blocking%20Rules](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Advanced%20Blocking%20Rules)

---

### Post by hvac3901 on 2008-09-15
> **mregister said:**
> there are a lot. It looks like a dictionary. They start with A and all the way through, just about every name there is. No the college does not mean anything to me. How did you find out what block it comes from. How do I stop that kind of attack. Wow I have a lot to learn.

concider using ".htaccess" to protect your dirrectory, and you can also block alot of known bad BOTS with it.

---

### Post by hvac3901 on 2008-09-15
> **t0p said:**
> Possibly... crackers use "dictionary files" to brute-force login/password combos and the like.  How many such entries are there in the log?

That IP address 70.63.86.162 is in a block registered to "Cape Fear Community College".  Is that a real college?  Does it mean anything to you?  Or anyone else?

google shows that ip being used alot for wierd stuff and strange user names.

---

### Post by k33bz on 2008-09-15
OrgName:    Road Runner HoldCo LLC 
OrgID:      RCMS
Address:    13241 Woodland Park Road
City:       Herndon
StateProv:  VA
PostalCode: 20171
Country:    US

I get that with a whois lookup

---

### Post by mregister on 2008-09-15
thanks I will read that

---

