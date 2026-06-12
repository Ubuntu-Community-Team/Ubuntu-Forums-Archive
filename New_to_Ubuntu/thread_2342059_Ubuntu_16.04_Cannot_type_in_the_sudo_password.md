---
title: "Ubuntu 16.04: Cannot type in the sudo password"
date: 2016-11-03
forum: New to Ubuntu
---

### Post by dotja on 2016-11-03
Hello everyone.

I updated this week to 16.04 and straight away I experienced issues with the brightness of the screen. I found the relevant thread on the forum, , open the terminal... and it turned out, I cannot execute any sudo command. The keyboard just stops working when I'm supposed to type in the password, even though it works just fine when I'm doing anything else. Does anyone have an idea how to fix this? The dark screen is really hurting my eyes. 

I work on Lenovo Z500. I attach a print screen, so you can see that typing in the command is not a problem - just, for some reason, I can't type in the password.

---

### Post by QIII on 2016-11-03
This is a normal security feature.  Nothing is echoed to the screen - not even asterisks.

Just type your password carefully and press enter.

---

### Post by dotja on 2016-11-03
I can't. I cannot type in the password. I know it won't be displayed, but I also know my password and I know I typed it in several times since Tuesday and I know that when I try to type it anything when the system asks for password, just nothing happens. The cursor doesn't flash. Nothingness.

---

### Post by QIII on 2016-11-03
OK.   Let me ask for an affirmative answer.  :)

Have you carefully typed your password and pressed enter?

---

### Post by &amp;KyT$0P# on 2016-11-03
And if the answer is "yes", please post the output of running this command in Terminal -
```
id
```

---

### Post by Geoffrey_Arndt on 2016-11-04
So, I'm assuming you've turned off your PC and turn it back on . . . meaning, you would have to login again using your password (unless you turned that vital feature off).   So, if you can login, your same password should work for sudo.

---

