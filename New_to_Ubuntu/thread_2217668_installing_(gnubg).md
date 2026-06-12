---
title: "installing (gnubg)"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by sarah6 on 2014-04-18
Hi - new to linux & ubuntu and currently using an old pc running ubuntu 12.10. I only use it for word processing (LibreOffice writer) and internet (firefox) at the moment. I'd like to install gnu backgammon assuming that would be low risk in terms of stability (this is my currently my only computer and I need to keep it working!).
I've tried downloading gnubg for ubuntu 12.10 from the ubuntu app store but only get as far as a pop-up window called Launch Application: 'This link needs to opened with an application. Choose application'. I assumed this meant I needed something like VLC player so tried downloading that but got the same pop-up. 
I've tried reading the installation help articles and can't really make head or tails!

---

### Post by Impavidus on 2014-04-18
Checking on 12.04...
gnubg is present in the repos and should be installable by clicking on install in the software centre. Alternatively, use the terminal:```
sudo apt-get install gnubg
```
Note however that 12.10 reaches end of life this month. If you want stability use LTS releases. 14.04 LTS was released yesterday.

---

### Post by sarah6 on 2014-04-18
Hi thanks for this. Plan on switching to the current LTS when I get prompted, assuming I will soon - the pc came with 12.10 loaded, up to date & running pretty good at the moment.

Re installation of gnu backgammon: I did click on install in the software centre. That's when I got prompted to select an application to open the link. When I click 'choose' I get returned to my own file directory. Don't understand the prompt & can't get past it. 

Thanks.

Sarah

---

### Post by Impavidus on 2014-04-18
I just tried it on 12.04, using the software centre, and I didn't get any prompts except for the one asking for my password. There might be something wrong with your package manager. What do you get when you try installing it using the terminal?```
sudo apt-get install gnubg
```It may give a clear error message.

---

### Post by sarah6 on 2014-04-18
Ok I did that & it seemed to download ok after confirming & asking for password. The terminal returned to a type prompt, I closed it, but can't find gnubg now. (Also before the password prompt two files were recommended to be removed, linux-headers-3.5.0-17 and linux-headers-3.5.0-17-generic. I've not done anything about that yet.)

---

### Post by sarah6 on 2014-04-18
Just played my first game of gnu backgammon on linux ;)  didn't show (so far as I could tell...) but came up with a type search

 Thanks very much for the response and offering support. 

Assume I go ahead & delete those two files using 'sudo apt-get autoremove...' in the terminal? One by one?

---

### Post by Impavidus on 2014-04-18
Running **sudo apt-get autoremove** is safe.

If the problem has been solved, could you mark this thread as solved? Thread tools (top of the page) &#8594; mark as solved.

---

