---
title: "How to make Unlock stick?"
date: 2016-02-24
forum: New to Ubuntu
---

### Post by Xinghao_Chen on 2016-02-24
I have installed 14.04 for use at home and would like to set the Unlock in my user account "permanent" but have not been able to do so. After Unlock it is ok until I power it done for the day and I will need to do it again the next morning.

Any way to set this Unlock permanent?

---

### Post by papibe on 2016-02-24
Hi Xinghao_Chen.

What do you mean by 'unlock'? Do you want to log into your account automatically after it boots?

Regards.

---

### Post by Xinghao_Chen on 2016-02-24
In System Setting -> User Accounts, on the top-right there is a Unlock button. After I click on it, it would then turn into a Lock button (which means the password key ring is been unlocked). When I turn Ubuntu on next morning, the button would appear as Unlock again. I am looking for a way to set it so that when I turn on Ubuntu this button stay as Lock.

---

### Post by Xinghao_Chen on 2016-02-24
I forgot to mention that the Automatic Login has been set to ON.

---

### Post by grahammechanical on 2016-02-24
You are tying to do something that cannot be done and should not be done for the security of Ubuntu.

We need to unlock the User Accounts utility in order to add and remove users. We can also give users administrator privileges. Now imagine what would happen if that utility was left unlocked and someone else gained access to your machine. They could set themselves up with administrator privileges and remove your administrator privileges. They could even remove your account and so prevent you from using your own computer.

It most likely could even be done across the internet.

When we install Ubuntu we are asked to set up a user name & password. If we do not have automatic login set to On we will use that password to login. Most of the time that we work in Ubuntu we work as a standard user but really we are the administrator. And that is how we are listed in the User Accounts utility.

If we need to do something that requires administrator privileges, such as add and remove users, we are asked to authenticate the action. We put in our password and the action proceeds. Or in the case of User Accounts the utility is unlocked.

When the Action is finished Or approximately 15 minutes later our administrator privileges expire. I cannot think of any reason why the User Accounts utility should be left unlocked for longer than the time it takes to make the changes we need to make. We should always lock User Accounts after we have made the changes.

There are several reasons why Linux is not infested with malware like Microsoft Windows was and may be still is, for all I know. One of the reasons for that is this particular way of working. 

Regards

---

### Post by Xinghao_Chen on 2016-02-25
Thank you for looking into my request. My use of Ubuntu is far from the advanced and I thank the people who made efforts putting this OS system together.

As a beginner at the very elementary level, my this request has to do with being constantly asked to type in password. I am using the Automatic Login feature but still I would get many pop outs at different times on the screen asking to enter password - it mentions something about "password keyring" which I have no clue what it means/does. 

Although this is annoying in a home environment, I understand other important concerns and I certainly can live with it. No major problem here. 

So, thank you for sharing the backgrounds.

---

### Post by mcduck on 2016-02-25
The keyring password is completely different thing from the admin permissions grahammechanical described above. The keyring is used to store your personal passwords ad encryption keys (for example passwords to wireless networks etc) in a secure way, so that if somebody gets access to your computer (even when it's powered off), they can't just start the computer with a live-USB or something, mount the hard drive and find the passwords in a plain text file or something.

However this kind of security only works if it requires some kind of confirmation from you, so it can unlock the keyring and decrypt it's contents. This is usually done automatically at the same time when you log in to your desktop, but since you are using automatic login that wouldn't actually work. And that's why the keyring is asking you to give the password separately instead.

Basically you have two options, the better and more secure one is to stop using automatic login, which will protect your user account and allow the keyring to encrypt all your passwords so nobody can access them. And the other option is to use the "Passwords and Encryption Keys"-tool, and change the default keyring's password to empty one. This will disable the keyring encryption, and stop it from asking the password any more. The downside is of course that all your passwords are now available to anyone whoi gets access to the machine. Then again, since you use automatic login that's not a big difference anyway, assuming you only have wifi passwords and other relatively low importance things in the keyring.

---

### Post by Xinghao_Chen on 2016-02-26
Thank you all for the education.

---

