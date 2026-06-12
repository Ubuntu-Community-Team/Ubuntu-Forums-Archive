---
title: "Software Installation issues"
date: 2016-01-08
forum: New to Ubuntu
---

### Post by Malabika_Mahajan on 2016-01-08
I am very new to Ubuntu, have installed Ubuntu 15.01 in my PC. ***Trying to install R Gui, Weka, from the Ubuntu Software Centre. ***
All works fine till it takes me to the window which shows a message "Available from the Universe Source" clicking the Button "Use the Source"
doesn't proceed further for installation. The repository "Universe" is already available. All Software sources are tick marked. My login is as Administrator.
I am totally new to this OS.

---

### Post by mastablasta on 2016-01-08
If you know the package name you can try installing it via terminal using 

sudo apt-get install [I]package_name
[/I]
you will be able to see where it get's stuck as apt-get will give any error messages to terminal. you can then mark them, copy and paste them here.

---

### Post by grahammechanical on 2016-01-08
Was there an error message?

The Software Centre has 2 applications that are GUI for R; R commander & RKWard. Weka is a separate package/application. Which one has this problem? How do you know that the software was not installed?

Certain applications have to be launched with a terminal command. I have read that R commander is like that but I might be reading old information. After we install software using Software Centre we may find that the Software Centre page for that application is advising that the application is to be launched from the terminal.

Regards

---

### Post by Malabika_Mahajan on 2016-01-12
No, error messages, Clicking on the Button "Use this Source" gives no activity at all. I have checked my Software Centre , I dont have R Gui, Weka installed, and anything which i am trying to install is giving me this no response thing. No error message nothing. Even the command sudo apt-get update gives me a failed to fetch list of errors. The Universe Repository is there present. Have tried even changing the servers . My net connection working fine.
Thanks a lot for the response, I dont know if i am going dumb anywhere, some guidance will be very helpful.

---

### Post by Malabika_Mahajan on 2016-01-12
sudo apt-get command gives me a list of failed to fetch error. What can be the issue regarding this. I am using ubuntu 15.01

---

### Post by ian-weisser on 2016-01-12
Unfortunately, the description is too vague.
Please show us the complete command, and the complete output of the command.

---

### Post by mastablasta on 2016-01-13
you can copy and apste the ouput preferabyl using the code tags (the # sign in "Go Advanced" answer)

---

### Post by Malabika_Mahajan on 2016-01-19
Thank you everyone for the replies, I sorted it out. Had some issues with the DNS Server IP. setting it right made it perfect. once again thanks.

---

### Post by slickymaster on 2016-01-19
Glad you got it fixed. Please don't forget to mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), so other people searching the forums know that it provides a working solution.

---

