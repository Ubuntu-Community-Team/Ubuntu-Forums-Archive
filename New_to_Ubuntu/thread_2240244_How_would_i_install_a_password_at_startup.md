---
title: "How would i install a password at startup"
date: 2014-08-18
forum: New to Ubuntu
---

### Post by nwpll on 2014-08-18
Hi 

I have to put my laptop into a repair shop but when i switch on my machine it just starts. I would like to have a password so the repair shop can't access my machine as i have business data i would like to protect. How would i install a password so nobody can view my data.

Thanks

---

### Post by yancek on 2014-08-18
> 
I have to put my laptop into a repair shop but when i switch on my machine it just starts.

Are you using windows?  If you are using a Linux system such as Ubuntu you need to create a user password during the installation.  Did you change that to auto-login?  If so, change it back.  If you are using Ubuntu or some other version of Linux, indicate which it is and the release.  On 14.04, you can do that in System Settings, User Accounts.

Another option would be to encrypt the data.   Or ask then to sign a non-disclosure agreement.  Or you could take the computer to someone you trust.

---

### Post by ubudog on 2014-08-18
Do you have auto-login set up?  You can set a BIOS password on most computers, and you can set a GRUB password as well.

Even if you turn auto-login off, if someone really wants your data they can get it if it is not encrypted.
Here is a good article you can follow if you would like to encrypt your home directory so that your data stays encrypted as long as you are not logged in:
[http://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/](http://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/)

---

### Post by nwpll on 2014-08-18
Hi Guys

Thanks for such a speedy reply.

No i don't use windows i have been with Ubuntu since Dapper was releasted. I am now using 14.04

At my last clean install i didn't set a password at startup and that's my problem.

Peter

---

### Post by ubudog on 2014-08-18
Do you automatically log in?

---

### Post by grahammechanical on 2014-08-18
> [COLOR=#000000]At my last clean install i didn't set a password at startup and that's my problem.[/COLOR]

Please explain how you did that. I regularly install test versions of Ubuntu and the flavours and I am always asked to put in

1) my name
2) a user name
3) a machine name
4) and a password repeated twice to confirm accuracy.

There is a box that is ticked by default that says Require password to login. Or something like that. I did not know that an install of Ubuntu could proceed without a user password. 

Regards.

---

### Post by Frogs Hair on 2014-08-18
There are folder and drive encryption tools available for Lunux . The Seahorse Nautilus Plugins  are one option but I have no experience with encryption in Linux other than email. I tend to use cloud storage for easy access from different computers.

---

### Post by nwpll on 2014-08-18
Hi Grahammechanical

I don't know what i did but when i use the terminal it asks for a password but not at startup. When i switch on it just goes to my desktop screen. What i want is when i switch on i am asked for a password.

Peter

---

### Post by ubudog on 2014-08-18
Under your "User Account" settings, there should be a way to turn automatic login off.

---

### Post by Paulgirardin on 2014-08-18
I would advise against turning auto-login off I you do not know the password as you will not be able to login at the next reboot.

---

### Post by Paulgirardin on 2014-08-18
> **nwpll said:**
> Hi Grahammechanical

I don't know what i did but when i use the terminal it asks for a password but not at startup. When i switch on it just goes to my desktop screen. What i want is when i switch on i am asked for a password.

Peter

So you know that (sudo) password?
The login password will be the same.

For Ubuntu Unity:type user in the dash and open user accounts.Click unlock .Enter your password (the one you use in terminal) and set the automatic login slider to off.

---

### Post by oldos2er on 2014-08-18
Setting a login password isn't going to stop someone from being able to read the data on your hard disk. As was mentioned you'll need to encrypt any sensitive data; or remove the hard disk before taking it to the shop if that's feasible.

---

### Post by dave131 on 2014-08-19
Perhaps I don't understand correctly (not the first time, definetly not the last! ;) ) - but if it's going in for repairs, what is wrong with it?  How will they know if your hard disk or something in your configuration is causing a problem?

---

### Post by nwpll on 2014-08-19
> **dave131 said:**
> Perhaps I don't understand correctly (not the first time, definetly not the last! ;) ) - but if it's going in for repairs, what is wrong with it?  How will they know if your hard disk or something in your configuration is causing a problem?

HI Dave

An part of the screen on the left hand side is blank and for that reason i am putting it into a repair shop. Also because i can't use Unity i am using the Cairo-dock as i have set it up just how i want.

After the screen is fitted and switched on it should then be able to boot to the login screen and that's enough for the repair shop. My business data is not sensitive as i own a Spice company and i also live in Portugal so Language also is an issue.

Using Cairo i can't find any User Setting or User account and that's where i am stuck it seems that Cairo doesn't show all the setting etc that Unity does.

Peter

---

### Post by ubudog on 2014-08-19
I believe the command to open the System Settings from the command line is:
```
unity-control-center
```

---

### Post by dave131 on 2014-08-19
Is this currently set up as auto logon and what you want is instead to have the login prompt?  If so, go to "User Accounts" and it will show your user.  On that screen turn off auto login.

---

### Post by nwpll on 2014-08-19
Hi Ubudog and Dave

With both your help i now have to put my password in when i switch my laptop on.

Thanks for the valuable help you have been to me.

Peter

---

