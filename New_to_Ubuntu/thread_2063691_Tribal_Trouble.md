---
title: "Tribal Trouble"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by ericsonlouis on 2012-09-27
I downloaded tribal trouble for linux and when i run it it opens in a text editor i want to know what should i use to open it what application?

---

### Post by ericsonlouis on 2012-09-27
ok i got it do set up but i still have not goten the game 

anyone who has downloaded the game can help me?

---

### Post by Malisius on 2012-09-27
I quickly scanned the Tribal Trouble website for any useful information, and somehow magically managed to find exact instructions on what to do on the downloads page. 

The first thing you need to do is download TribalTroubleSetup.sh. If it's opening the file in your browser when you click the link as opposed to downloading it, right click the link and select "Save Link As" ("Save File As" in some browsers). When you have saved the file to an appropriate location, navigate there in Terminal using "cd" and run
```
sh TribalTroubleSetup.sh
```
This will install the game. You can run the game by navigating to the directory again with "cd" and running
```
./TribalTrouble
```

Alternative to running the files from terminal, you can use 
```
chmod +x 'filepath/filename'
```
to make it executable, which will allow you to run the file by double clicking it in your file browser.

---

### Post by ericsonlouis on 2012-09-27
Thanks

But /i tryed that and it did not work but it works now

---

