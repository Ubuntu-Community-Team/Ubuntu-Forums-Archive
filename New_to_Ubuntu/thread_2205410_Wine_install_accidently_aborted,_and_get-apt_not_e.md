---
title: "Wine install accidently aborted, and get-apt not exiting to start over again."
date: 2014-02-13
forum: New to Ubuntu
---

### Post by hebrewofyhwh on 2014-02-13
I was installing Wine with the code  ```
 sudo apt-get install wine 
```

The program was installing. Then I saw on the terminal screen a white message with an "ok" on the bottom concerning Microsoft "EULA" and I thought that it was finished installing so I closed the terminal screen with the red "x".  A message did come up that there was a process running but I continued to close it. (This is the error I made, I should have heeded the "running process" message and left it alone). 


My question now is that I am trying to reinstall it I get this message: ```
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


``` 

 Is the code I need this? ```
 sudo apt-get remove wine 
```  so that I can remove the aborted install to start again with  ```
 sudo apt-get install wine 
``` so I can install Wine properly this time?


What I want to do is  get Wine installed and running. How do I undo what I have started so I can start fresh and get the done? 
I am in Precise Pangolin 12.04 

I appreciate the help, in advance.

---

### Post by philinux on 2014-02-13
Try this in a terminal.

sudo dpkg --configure -a

---

### Post by hebrewofyhwh on 2014-02-13
Thank you, This is what happened when I did  ```
  sudo dpkg --configure -a
```

Results: ```
dpkg: error: dpkg status database is locked by another process
```

---

### Post by hebrewofyhwh on 2014-02-13
Would a complete system reboot solve the problem?

---

### Post by fdrake on 2014-02-13
rebbot and try again the "sudo apt-get install wine". There is another procesws locking you package manager (check your open windows/terminals)

---

### Post by hebrewofyhwh on 2014-02-13
Thank you for that last instruction. The reboot and then the  ```
 sudo apt-get install wine
``` worked. Now, this screen is up again:
This Screen is still up in the terminal.  I am really new to this program and I don't know how long this takes to load. Is it normal for this screen to be up for such a long time. 
 ```
  Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                   

                                                        &#9474;  
 &#9474; TrueType core fonts for the Web EULA                                         
 &#9474;                                                                              
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                            
 &#9474;                                                                              
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement          
 &#9474; ("EULA") is a legal agreement between you (either an individual or a         
 &#9474; single entity) and Microsoft Corporation for the Microsoft software          
 &#9474; accompanying this EULA, which includes computer software and may include     
 &#9474; associated media, printed materials, and "on-line" or electronic             
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your         
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be       
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of         
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                             
 &#9474;                                                                              
 &#9474;                                                                              
 &#9474;                                  <Ok>        
```  
Does that screen just automatically go away?
The "ok" does not seem to be a pressable button to go away.

---

### Post by fdrake on 2014-02-14
you have to accept the EULA license . Try with tab or space/enter to accept at the end/ or just scroll down with page down.

---

### Post by hebrewofyhwh on 2014-02-15
I got it accomplished. Wine is now up and running and it works quite well with theWord program. I don't see any difference between XP and Ubunto with this program. Thank you for assistance. Case closed.

---

