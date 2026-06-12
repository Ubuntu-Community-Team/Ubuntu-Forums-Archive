---
title: "New install won't run"
date: 2016-04-01
forum: New to Ubuntu
---

### Post by Phil's Dad on 2016-04-01
I've just installed Ubuntu 14.04. All appeared to go OK but after restart (as required) the opening screen indicates a guest session and asks for a password. I entered the password used during installation but it was not accepted. How do I proceed? Why is the screen indicating a guest session?

---

### Post by RobGoss on 2016-04-01
Hello and welcome, Did you setup a user and password when you run your installation?

Remember when asked for your password and it's incorrect you will them be ask for the** User & Password** following that

---

### Post by Phil's Dad on 2016-04-02
I did set up a user and password during installation. I have only been asked for a password, not a user, and I entered the one I used during installation. Is it significant that the password box indicates that it is a guest session?

---

### Post by howefield on 2016-04-02
The guest session shouldn't need a password, just press the enter key without inputting anything into the password field.

The guest session is created automatically, all data created when using the guest session will be deleted on logout from it.

---

### Post by buzzingrobot on 2016-04-02
Is your username shown?

---

### Post by Phil's Dad on 2016-04-02
Thanks, Howefield. Tried your suggestion but error message states "Invalid password, please try again". Tried entering the password used at installation, screen goes blank then after a few seconds, opens the log in screen and asks for password.

---

### Post by Phil's Dad on 2016-04-02
Thanks for reply, buzzingrobot. Yes, username is shown.

---

### Post by yancek on 2016-04-02
When you boot, you get to the login screen where you should see the user name you created during the install plus guest.  Mouse click on the user name and you should see an input box below the name.  Enter your password and then hit the enter key.  If you click on guest on the login page you should see the input box below guest.  Hit the Enter key without entering anything in the input box and you should get a pop-up window telling you nothing will be saved when logged in as guest user.

---

### Post by Phil's Dad on 2016-04-02
Gentlemen, the problem appears to be solved. I have installed Ubuntu 15.10 and during installation it occurred to me that a four letter password might be part of the problem. The password is now 7 characters long (I know - still too short really) and it all works. Unfortunately, I ignored the note to the right of the password box when installing which said that the password was short. A note stating minimum password length might be useful.

However, thank you for your kind assistance, it's good to know that help is available.

---

### Post by RobGoss on 2016-04-02
Your very welcome Phil glad you got it sorted out do you mind marking this as solved? thanks a bunch

---

### Post by howefield on 2016-04-03
> **Phil's Dad said:**
> I have installed Ubuntu 15.10 and during installation it occurred to me that a four letter password might be part of the problem. The password is now 7 characters long (I know - still too short really) and it all works. Unfortunately, I ignored the note to the right of the password box when installing which said that the password was short. A note stating minimum password length might be useful.

I'm sure the issue is something else as the installer will accept a four character password. 

However you have gotten around it so no matter.

---

### Post by gordintoronto on 2016-04-03
> **howefield said:**
> I'm sure the issue is something else as the installer will accept a four character password. 

However you have gotten around it so no matter.

Indeed! The password length has nothing to do with the problem or solution.

---

