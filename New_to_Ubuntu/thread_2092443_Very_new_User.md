---
title: "Very new User"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by Stetem on 2012-12-07
Some how setting my new ubuntu os i tried to change my admin settings to standard
now i dont have privileges to make changes,,
i dont know how to get back there
what i really want to do is turn my laptop on without having a password for anything
i am the only one that uses it

any and all help is appreciated

---

### Post by papibe on 2012-12-07
Hi Stetem. Welcome to the forums ):P

Take a look at the third tip of this [tutorial]("http://www.omgubuntu.co.uk/2012/05/solve-six-common-gripes-with-ubuntu-12-04").

Regards.

---

### Post by Stetem on 2012-12-07
Hi,,, thx for the reply
but i dont have admin settings,,, so my password wont work
i think what i need ,, is getting back my administrator privileges

---

### Post by Frogs Hair on 2012-12-07
Hello and Welcome

If you are using Unity start typing user accounts into dash. Installing software will require a pass word regardless of account type. You can use automatic login if you plan to stick with the desktop Unity only.

That setting is in user accounts as well. It is not wise to go online as administrator but that is your choice. removing password requirements is possible with some research but not easy or recommended.

---

### Post by Stetem on 2012-12-07
i think my problem is ,, it doesnt accept my password
is there a way to change my password,,, and will standard privileges allow me to make changes
please keep in my this is my first experience with ubuntu

---

### Post by critin on 2012-12-07
> **Stetem said:**
> Some how setting my new ubuntu os i tried to change my admin settings to standard
now i dont have privileges to make changes,,
i dont know how to get back there
[COLOR=Red]**what i really want to do is turn my laptop on without having a password for anything**[/COLOR]
i am the only one that uses it

any and all help is appreciated

Hi, Stetem...welcome to ubuntu!

Since this is a new install, it might be easier to just reinstall the system unless someone comes along quickly and gives the terminal code that allows you to establish a password.   

This time give yourself a password as usual, then after you're all installed, go to System Settings, user accounts and unlock your acct with your password.  Change the setting to 'sign in without password', but do NOT change the acct to standard.    You can choose the option to not use it during login during the install, but I suggest you don't because the more you explore and do things yourself, the more you will learn about ubuntu.

[COLOR=Red]**You will still need the password for many things, **[/COLOR]
You have to be administrator as you discovered, or you won't be able to install programs, updates, a lot of things require the password.   This will allow you to bypass the login only.   

I assume you're not dual booting...

Actually, you're only saving 2/3 seconds by not logging in and this will prevent you from using the recovery and/or Guest login in case you ever needed it.  If the system fails to open for any reason, you'll be stuck.  Grub lists the normal login and a recovery login on its page, did you realize that?  It's pretty important to be able to get to that sometimes.  Passwords are handy
.
Are you aware that a password can be as tiny as one character?

There are ways to fix this through the terminal but I wouldn't presume to try to lead you through that.

---

### Post by steeldriver on 2012-12-07
You can reset your password from the recovery console - instructions in this link

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Stetem on 2012-12-07
Thank You,, i think i will try the new install
this is a brand new laptop with only ubuntu on it,,, i think its 11.?
fully updated tonight
should i stay with this version,, or update to the newest ?

---

### Post by critin on 2012-12-07
> **Stetem said:**
> Thank You,, i think i will try the new install
this is a brand new laptop with only ubuntu on it,,, i think its 11.?
fully updated tonight
should i stay with this version,, or update to the newest ?

11.10 is a good system, but 12.04 is too.  It's your decision.  I wouldn't go with 12.10 as it's too new.

The link that [steeldriver]("http://ubuntuforums.org/member.php?u=1627500") posted is a good, simple tutorial on how to set password, it wouldn't hurt to give a try.  It's good practice.

---

### Post by Stetem on 2012-12-07
> **critin said:**
> 11.10 is a good system, but 12.04 is too.  It's your decision.  I wouldn't go with 12.10 as it's too new.

The link that [steeldriver]("http://ubuntuforums.org/member.php?u=1627500") posted is a good, simple tutorial on how to set password, it wouldn't hurt to give a try.  It's good practice.

I am downloading 12.04 now to my download folder,, guess i will have to write it to dvd after its finished
is there anything i should know before i write it

and i did take a look at steeldriver's link
thought is was to much to remember for this old novice though

---

### Post by critin on 2012-12-07
> **Stetem said:**
> I am downloading 12.04 now to my download folder,, guess i will have to write it to dvd after its finished
is there anything i should know before i write it

and i did take a look at steeldriver's link
**thought is was to much to remember for this old novice though**

Don't try to remember it, leave the page open, open the terminal and copy each command with your mouse, paste it to the terminal as it is given.  ;)  Again, it's good practice.

Burn the 12.04 image just like you did the 11.

---

### Post by DuckHook on 2012-12-08
Many people who come from the Windows world are unused to the password nature of Linux and try to recreate their Windows environment out of habit. I try to show them that much of what I don't like about Windows, and perhaps even some of the Windows drawbacks that also drove them to looking at Linux in the first place, are non-issues in Linux precisely because of its enforcement of passwords. In fact, I feel so strongly about this that I have resolved to refrain from providing procedures for bypassing Linux security. The last thing the Linux community needs is to have Linux evolve into something as insecure as Windows.

This is not meant as a slight to the OP. I fully understand that your motives are entirely honourable. However, I must point out that your laptop can be stolen or lost. Your home can be broken into and your laptop taken. If it ever is, then all of your e-mail (including those medical records from your doctor, those statements from your bank, those nasty things you wrote about your boss) are completely available for anyone to read merely at the press of a power button.

This isn't all. One of the best advantages that Linux has over Windows is the lack of any need for antivirus. We don't need to load up antivirus programs that spend the first 10 minutes of every bootup downloading antivirus signatures and new engines, then slowing the whole system down to a crawl by incessantly scanning our hard disks and intercepting e-mails. However, a primary reason for this advantage is due to Linux's enforcement of passwords. But you can't have it both ways. If you don't want to deal with viruses and antivirus measures, then you have to accept the need for passwords.

My advice to new users is in fact the opposite: more security, not less. You should consider encrypting your /home directory when you install so that all of your e-mail is nothing but a meaningless garble to anyone but you. You should turn on the firewall that Ubuntu has turned off by default. And you should not only use a password, but a strong one so that it's too much time and trouble for some cracker to try breaking it. Linux actually makes these things as unobtrusive and as painless as possible. We get a lot of security for very little effort. Why hobble it?

My $.02 anyway.

---

### Post by Stetem on 2012-12-08
Thx for all the helpful suggestions
in the end i used my restore disk to do a new install
my laptop is a new dell with pre-installed ubuntu 11.10
my next job will be to get my printer working wireless

---

### Post by cmcanulty on 2012-12-08
go with 12.04 as it has 5 year support. Also make sure you make a partition for / about 20GB max and then as much swap space as ram, and a separate /Home partition for the rest. That way every time you want to reinstall all your settings and documents are unaffected. Saves a lot of trouble later on.

---

