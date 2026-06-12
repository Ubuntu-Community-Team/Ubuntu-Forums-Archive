---
title: "Login loop problem on fresh install of Ubuntu 14.04"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by bodkin2 on 2014-07-09
Hi,

So I tried Ubuntu on a USB boot and liked it enough to replace my orignal OS. Everything was going smoothly and I made it to the graphical login. It prompted me for a password but when I enter it, it goes black for a second and then goes right back to the login screen and asks for the password again. I'm able to log in as a guest in case that matters. I should also add that when installing Ubuntu I chose to encrypt the hard drive. I haven't had trouble as far as that is concerned but it may affect the steps I need to take in order to fix this problem.

Anyway, since I have no experience with Linux yet, I need help figuring this one out. I've tried a couple solutions that I found on other sites but to no avail. I'll also add that when logging in with the virtual terminal I get "signature not found in user keyring". Someone said that has to do with changing the password on an encrypted drive but I don't know what to do about it.

If any more info is needed, let me know. Thanks!

---

### Post by yancek on 2014-07-09
You should have a second option to boot Ubuntu in the Grub menu, the recovery option.  Have you tried that as you may need to install proprietary drivers.  What graphics card do you have?

---

### Post by deadflowr on 2014-07-09
First, for a test, when you get to the login screen, there should be an option to login as guest.
(This option does not need a password, simply, click and it will log you in.)
If you can login, then the problem is most liekly user-specific.
In that case the first thing to do is to look over the Xauthority file for the user.

To do so, get back to the login screen first.
At this screen, press ctrl + alt + F1(or F2-6)
You will get a command prompt in full screen.
Enter your username and password, which will log you in.

Next enter this
```
ls -la .Xauthority
```
Note that it should list two names.
Those names should be yours.
If for some reason, it does not list your name, but something else try resetting it
```
sudo chown you:you .Xauthority
```
Chnage you:you for your username.
After the change you run this
```
sudo lightdm restart
```
this will bring you back to the login screen.
Try to login.

Sometimes though, it is not the file owner that is the problem, but the file itself is corrupted.
In this case try a reset
```
mv .Xauthority .Xauthority.bak
```
This should save the old one just in case, but generate a new one.
Then try the lightdm restart command again.

If neither option works post, and we'll look into the next option.
Good Luck

**Edit**: Look here for a quick howto about the "signature not found issue
[http://askubuntu.com/questions/411702/ubuntu-12-04-keyring-broken-signature-not-found-in-user-keyring-perhaps-try-the](http://askubuntu.com/questions/411702/ubuntu-12-04-keyring-broken-signature-not-found-in-user-keyring-perhaps-try-the)

---

### Post by sp40140 on 2014-07-11
+1 
for DeadFlowr Suggestion. 
re-creating the Xauthoriy has worked for me in the past for this same issue.
It was caused by Vid drivers in my case (with which I am still struggling). But the log-in screen issue was fixed. by this solution.

---

### Post by mansonfan78 on 2014-07-11
Another +1 for DeadFlowr.  I had this problem before as well, and this fixed it.  Seems (in my experience) to affect Nvidia more than AMD/ATI.  Perhaps a bug in Nvidia's drivers that corrupts the file when certain settings are changed.

---

