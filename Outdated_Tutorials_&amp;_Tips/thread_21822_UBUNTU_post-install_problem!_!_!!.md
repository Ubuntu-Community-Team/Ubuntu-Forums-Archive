---
title: "UBUNTU post-install problem! ! !!"
date: 2005-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by //siddhartha// on 2005-03-24
Hi! Guys,
  I am having a problem after installing UBUNTU. 

    Actually, when I start the O.S., in the tests it says OK to all tests except one called something like "temporary name resolution" . Moreover, it fails to start the X Server, due to which there is no visual interface. 

     Moreover, when asked for username and password, I enter the username, but when password is asked and I type anything on the keyboard nothing appears on the screen (not even asterisks ******). I typed in the user name and password even though which I had set during installation but still it said LOGIN INCORRECT. So, I just restarted the computer and go to my Win XP.

     When using the live CD, I was faced with a problem, that the screen would not load and the monitor would go to standby position, but then I added a line in the commands "x hsync=a vsync=b" where a is my Horizontal Screen frequency and b is my Vertical Screen frequency. I think the X Server does not load because of some screen resolution problems.. HOw can I modify the commands so as to start the X Server and finally, what about entering the password.. Plz help..

---

### Post by lao_V on 2005-03-24
If you are typing the password in the console then it won't show you asterisk (*). Its a Unix feature. Password's are case sensitive so make sure you enter it in the right case

---

