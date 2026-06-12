---
title: "Can't access files from deleted account."
date: 2014-03-20
forum: New to Ubuntu
---

### Post by dieuwertjesara on 2014-03-20
Hello,

A few days ago I've deleted my an account on my laptop because for some reason I accidentily named it guest and I couldn't find how to change it. Also it had some problems for wich I didn't want to bother solving. For example the account had a password but when I went to the log in screen it never asked for a password. So I made another account, but for some reason I couldn't just transfer al my files, wich aren't that many, tot the other account. Most files were for school so I relly needed them. I didn't have a Usb stick so I tried to find another way. So i found that when you delete and you can choose to either delete the files or save the files. I deleted the account and saved the files. But now I can't seem to open some of the files. The strange thing is that when I first did it i was able to copy the files to my new account, but later on I found out only a few of the files in the folder were transfered. Now I suddenly can't open or transfer the folders. Ironically one of the folders I can't open is the one with my school work. It gives me the message "You do not have the permissions necessary to view the contents of “VWO”." But I am the Administrator.

My question is, is there a way to open the files so I can put them on my USB and on the new account? 
Like trough the terminal or something.

I'm not super great with the terminal so if someone knows how to fix this please explain it like i'm a five year old.
That would be terrific.


Sorry for any grammer mistakes, english is my second llanguage.

O I have Ubuntu 13.10

---

### Post by codingman on 2014-03-20
Are you doing all of this in the file manager(nautilus)? If so, you need to run nautilus as root to access that stuff. So, go to the dash(the button with the ubuntu symbol in the top left corner) and type "terminal", and open Terminal. In the terminal, type:
```
sudo nautilus
```
it will ask for your password, so type it in, (it won't show it on a screen, only a blinking cursor, this is normal.)
Then you should be able to open the folder.

---

### Post by dieuwertjesara on 2014-03-20
Thankyou! I can now open them :D, but they are read-only. Do you know how to change that?

Wrong sentence,
I can now move them to the file from my user account, but then it's read-only. I can however open them when i'm in the folder for the files form the deleted account. Should i copy them on a USB or is there a way to grand my account permission to open en change the files?

---

### Post by codingman on 2014-03-20
In terminal, type:
```
sudo chmod -R 777 /place/of/folder
```
in '/place/of/folder' put the place where the folder with all the files is. Example: if the files were in /home/documents/school you would put that there.

Hope this helps!

---

### Post by dieuwertjesara on 2014-03-20
Yes thank you thank you thank you. You're a hero.
Turns out some pictures didn't transfer right either, so thankfully I got them al back and working :)

---

### Post by codingman on 2014-03-20
Glad I could help! Please go to the top right corner of this thread and click "Thread Tools", hit "Mark as Solved" so people know your issue is fixed!

---

### Post by steeldriver on 2014-03-20
Wouldn't it be better to **chown **the contents of the deleted user's account to the new user, rather than **chmod**ing them to give anyone access to everything?

---

### Post by codingman on 2014-03-20
Hmm... maybe, but it appears that he is the only user of the computer, and say he has another account.

---

