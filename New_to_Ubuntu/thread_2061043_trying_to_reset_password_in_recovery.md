---
title: "trying to reset password in recovery"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by imartin90 on 2012-09-19
:?:hi I was trying to change my password on ubuntu 12.04 and somehow I made it where I don't have a password.I cant authenticate anything.Is there a defalt password? If this helps when I go to user accounts where it shows your password it says "none" plz help :?:

---

### Post by Elfy on 2012-09-19
[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

What does "opps plz help" mean? 

Use sensible titles - if everyone that came here looking for help - just wrote help in the title then how could anyone search for help on their issue?

As it is - try booting into recovery mode and resetting the password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by imartin90 on 2012-09-19
sorry about the headline and thank you for the help

---

### Post by rybnik on 2012-09-19
sudo passwd username

---

### Post by imartin90 on 2012-09-19
can you explane that

---

### Post by newb85 on 2012-09-19
Try following Psychocat's tutorial.  (That's the second link in post #2.)  It's well-written and almost always does the trick for people in your situation.

If you have specific questions about the tutorial, ask.

Good luck!

---

### Post by audiomick on 2012-09-19
> **rybnik said:**
> sudo passwd username

> **imartin90 said:**
> can you explain that

That is a terminal command. By rights, it should have been posted in code tags like this

```
sudo passwd username
```

Using code tags is one of the things that aids people in easily understanding posts, same as using capital letters at the start of sentences and a full stop at the end of them....


Anyway

```
sudo
```
is the command that tells the computer that you want to have administrator permissions for the following command. If you preface a command with "sudo", you will be asked for your password after hitting enter. You will not see what you are typing when you enter your password in a terminal.

```
passwd
```
is the command to change your password. If someone suggests you use a command, you can always look up what the command does using
```
man command
```

i.e.in this case
```
man passwd
```

The man pages are often a bit cryptic, but you can usually figure out what a command is supposed to do.

The "username" at the end of the command is obviously your username.

Having said all that, your first post was rather difficult to read, but I believe you said in there somewhere that you can't authenticate anything. If that is the case, then the suggested command wont work, I think. It is the right command for changing your password, but I am not sure that it would work if there is no password set up.

---

### Post by imartin90 on 2012-09-21
> **Elfy said:**
> [http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)


As it is - try booting into recovery mode and resetting the password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

did all the things it told me to do and i got 
"passwd: authentication token manipulation error"
"passwd: password unchanged"

Any help with this would be nice

---

### Post by imartin90 on 2012-09-21
Hi i when to the recovery menu and whent to root. After folowing all the steps from [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) I got 
"passwd: authentication token manipulation error"
"passwd: password unchanged"

any help will be great thank you

---

### Post by steeldriver on 2012-09-21
That usually means you missed this step

> In recent versions of Ubuntu, the filesystem is mounted as read-only, so  you need to enter the follow command to get it to remount as  read-write, which will allow you to make changes: 

```
mount -o rw,remount /
```

(although there can be other, deeper reasons)

---

### Post by imartin90 on 2012-09-21
so do that first ???

---

### Post by papibe on 2012-09-21
**Threads merged.**

Regards.

---

### Post by imartin90 on 2012-09-21
Thank you all it worked and took under 1 min

---

