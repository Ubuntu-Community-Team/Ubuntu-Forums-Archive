---
title: "No Update, No Softwaredownload(11.10)"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by Gonioscope on 2012-02-14
Dear Members, 

I am a proud owner of a ridiculous Vaionetbook, Win 7Starter. I installed 11.10, with internetconnection and ISO file from a stick, alongside. Later a tried to update OS, but the message popped up ... no download possible, check your internetconnection..! Now there are 2 monthes gone, still no updates possible. Networkmanager displays Wlan ok! Firefox works as it should work, so the internetconnection does exist! Update for Win ok!

What are  the right steps for troubleshooting(I am not a computer-scientist!!)??

Your hints are very welcome, thanks a lot!

Greetings,

 Goni

---

### Post by arochester on 2012-02-14
Open a Terminal. Try the following commands one-at-a-time. Does it work? Any errors reported?> sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update

---

### Post by cortman on 2012-02-14
> **Gonioscope said:**
> Dear Members, 

I am a proud owner of a ridiculous Vaionetbook, Win 7Starter. I installed 11.10, with internetconnection and ISO file from a stick, alongside. Later a tried to update OS, but the message popped up ... no download possible, check your internetconnection..! Now there are 2 monthes gone, still no updates possible. Networkmanager displays Wlan ok! Firefox works as it should work, so the internetconnection does exist! Update for Win ok!

What are  the right steps for troubleshooting(I am not a computer-scientist!!)??

Your hints are very welcome, thanks a lot!

Greetings,

 Goni

In addition to arochester's suggestions, are you using a proxy to connect to the internet?

---

### Post by Gonioscope on 2012-02-14
Hi, what does proxy mean.....at least  I do not knowingly use such a device, Wlan I am using in a public library.
 Thanks, 

Goni

---

### Post by cortman on 2012-02-14
> **Gonioscope said:**
> Hi, what does proxy mean.....at least  I do not knowingly use such a device, Wlan I am using in a public library.
 Thanks, 

Goni

A proxy is a web server that you have to port through to get to the rest of the internet. Usually they require you to log in to the proxy, and either provide a username and password or else set your browser settings accordingly.
If you're not doing any of this, then you're not using it.

---

### Post by jerrrys on 2012-02-14
Would a temporary proxy session work?

[https://help.ubuntu.com/community/AptGet/Howto#Temporary_proxy_session](https://help.ubuntu.com/community/AptGet/Howto#Temporary_proxy_session)

---

### Post by Gonioscope on 2012-02-21
Thanks for the reply, as I am quite new regarding PC, Internet, etc. it would be nice if you could explain step by step the procedure of a temporary proxy-session. 

Salutations,

Goni

---

### Post by philinux on 2012-02-21
> **Gonioscope said:**
> Thanks for the reply, as I am quite new regarding PC, Internet, etc. it would be nice if you could explain step by step the procedure of a temporary proxy-session. 

Salutations,

Goni

Lets go back to basics first. Open a terminal and use.

```
sudo apt-get update
```

Post back any errors it spits out.

---

### Post by Gonioscope on 2012-02-28
Hi to everybody, 

I tried those commands and received results as follows: sudo apt-get update.....problem..I tried to paste the result(.png), it seems to be impossibel to copy the snapshots into this message. Is it possible to paste somthing here? I am an absolute beginner in the use of a forum, too!!

In words-error. Then I continued with achorester's list. Few error messages more, the command - sudo apt-get dist-upgrade- started a download. Unfortunately due to limited internetaccess and lack of time I had to interrupt the download. Today I will start anew, I do not know whether it will continue where it ended.

Kind regards, 

Goni

---

### Post by wildmanne39 on 2012-02-28
Hi, You can just copy and paste the output of:
```
sudo apt-get update
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Gonioscope on 2012-02-28
Hi

done as you wrote-it was not possible to copy the snapshot into the message.

Greetings,
Goni

---

### Post by wildmanne39 on 2012-02-28
Hi, I did not say take a snapshot, just copy and paste like if you were using windows.

High light the text then right click on it and copy the text then paste the results here following the directions in my previous post so it will be between code tags.
Thanks

---

### Post by Gonioscope on 2012-02-28
Hi, 

The problem: When using the commands I saved the results on a stick and today I use the opportunity to post the results, which as mentioned, seems to be impossible. The saved results are from the past, I have limited internet-access. 
Your suggestion seem to be useful when the  terminal and commands are just appearing and not from the past-correctly understood?

Greetings,

Goni

---

### Post by Gonioscope on 2012-07-24
Hi,
Thanks for your replies, used arochester's list,  it worked! Unfortunately I do not understand all the stuff the terminal spit out...Further I went to a user-meeting and the gent who orgnized it, told ...when I held a lecture... and he just had the same problem-the auditory was amused, not he, of course. Only using the terminal fixed it. 

Kind regards, 
Goni

---

