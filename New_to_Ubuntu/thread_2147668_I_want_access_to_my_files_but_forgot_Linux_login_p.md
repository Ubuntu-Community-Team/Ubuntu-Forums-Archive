---
title: "I want access to my files but forgot Linux login password &amp; partition is encrypted"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by triciasurfer on 2013-05-22
Dear community, 



I  feel awful and embarrassed. I had done a fresh install of Linux on my  computer that has had Windows 7. I kept the Windows 7 OS, and just  created a Linux partition on the same hard drive. When the installation  program asked me whether I wanted to encrypt the Linux partition, I said  "Yes". was out of the country for many months and forgot what my  Linux login password is. All that I remember is my login username.  I  don't really care if I can't log in to my Linux partition. What I care  about is accessing my personal files, such as my pictures (JPG).
 

I've tried to think of what the password could be, but all attempted passwords are incorrect. What can I do now?


Some possibly important bits of info:
--I am the only user on the  Linux partition. 
--My login gives me admin access. 
-- I don't mind if it  takes days for my password to be successfully guessed. I can wait. I  just want access to my files.
--I sometimes need to work  on the computer, using the Windows OS. Hopefully whatever solution we  consider using has a "Pause/Resume" feature.


If you have some advice, I would be so grateful to hear them. Please feel free to ask any questions.





So here's what I want to know:

1. Without knowing my Linux login password, is  there a way I can get access to my personal files on the encrypted Linux partition? 
2 Is there a computer program that tries one password after another until it successfully logs in?

---

### Post by deadflowr on 2013-05-22
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by triciasurfer on 2013-05-22
Hello. Thanks for your quick reply. I am following the Psychocats instructions you linked to. But i am stuck now. It tells me to choose the"root -- drop to root shell prompt" and then I'm supposed to enter a mount command. The problem is that after choosing the root selection, the text at the bottom says "Give root password for maintenance (or type Control-d to continue)". But I don't know the root password. And Ctrl-D just takes me back to the recovery menu.  :-(

---

### Post by Cheesemill on 2013-05-23
If you encrypted your drive and forgotten the password then you're out of luck I'm afraid.

The whole point of encryption is to try and make it impossible to access the files without the correct password.

It is possible for a program to try all of the combinations until you guess the correct password but were not talking days, this would take decades.

---

### Post by HermanAB on 2013-05-23
Howdy,

The purpose of encryption is to protect your data.  Linux encryption is very good at that and is used for military systems too.

You need to go on another vacation until you either remember your password, or you are so laid back that you don't need to remember it any more.

---

### Post by haqking on 2013-05-23
use your backup ;-)

---

### Post by Impavidus on 2013-05-23
If you have been foolish enough to use a weak password you may be lucky. Let's call it fool's luck. If you can narrow it down to maybe 100,000 possible passwords you can try to brute force it in a reasonable amount of time. I'm not sure of this forum's policy regarding telling people how to crack their own password.

If you had a strong password the remaining lifetime of the earth may not be enough to crack it, in which case you won't be able to access your files.

---

### Post by triciasurfer on 2013-05-23
HermanAB, Cheesemill, impavidus,


I've got good news and bad news.
Bad news: You are wrong. :-)
Good news: I was able to reset my login password by using a Live linux USB and doing this:
```
mkdir newfolder
mount /dev/sda5 newfolder
sudo chroot newfolder
passwd triciasurfer



```I then rebooted into the Linux partition and logged in with my new password.

But you have raised the issue: If I can do this on my own system, then is there any real security to using a login? And encrypting my /home/ folder?

---

### Post by Impavidus on 2013-05-23
Really? You recovered all files? OK. I waited a while before answering this thread because I wasn't sure myself. But if you can just reset the password and it works encrypting the home directory isn't really useful. The login still blocks remote hacking attempts though.

---

### Post by triciasurfer on 2013-05-23
Impavidus,
Yes, I can access all my files. 
My solution scares me. If I newbie like me can reset my own Linux login password, then anyone can hack into their contacts' computers if they have physical access to them.

---

