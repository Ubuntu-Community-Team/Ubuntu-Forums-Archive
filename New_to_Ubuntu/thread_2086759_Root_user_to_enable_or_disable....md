---
title: "Root user: to enable or disable..."
date: 2012-11-21
forum: New to Ubuntu
---

### Post by benbrockn on 2012-11-21
I have a question about the root user.


[LIST]
[*]I know that Ubuntu disables the root user by default but you can still use *sudo*
[/LIST]

[LIST]
[*]I know that you can add/remove users from using the sudo command by entering in:
```
sudo adduser <username> sudo
```
[/LIST]
But here is my question, if i don't set a root password, can't anyone hack in, set a root password, and lock me out? And can't a local user on the system (like my son) do the same?

I've already read this: [HTML]https://help.ubuntu.com/community/RootSudo[/HTML] but I was still confused if it were better security-wise to either:


[LIST=1]
[*]Leave the root user alone, and make only myself able to use sudo
[*]Enable root, set a lengthy password, and never log on it again, only making myself able to use sudo.
[/LIST]

Which would be better?

Thanks!

---

### Post by CharlesA on 2012-11-21
Leave the root user alone. If/when you have a hosed system and you forget the root password, you are out of luck.

Physical access = root access, as always. If someone wanted to get onto your machine, they would just use a livecd. If you don't want that happening, encrypt your home directory.

---

### Post by snowpine on 2012-11-21
The root account in Ubuntu is not passwordless (as your question implies) but rather the account is completely disabled.

---

### Post by CharlesA on 2012-11-21
> **snowpine said:**
> The root account in Ubuntu is not passwordless (as your question implies) but rather the account is completely disabled.
Yeah, the root account is "locked"

Good catch.

---

### Post by benbrockn on 2012-11-21
@snowpine Ah, i see, thank you. I assumed it was passwordless since you have to log on using sudo to create a password. 

@CharlesA In a thread I just recently made, I asked the same question about encrypting the /home directory. Because I didn't know much about it.

[HTML]http://ubuntuforums.org/showthread.php?t=2086756[/HTML]

---

### Post by CharlesA on 2012-11-22
Answered you in your other thread. :)

---

### Post by benbrockn on 2012-11-22
@CharlesA Thank you kind sir.

So I will go with option 1: Leave root alone and make myself the only sudo user

Thanks to both of you

---

### Post by nothingspecial on 2012-11-22
All explained here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Paqman on 2012-11-22
> **benbrockn said:**
> if i don't set a root password, can't anyone hack in, set a root password, and lock me out?

To do so they would have to crack your password, which since you're a sudo user means they have root access anyway. So having them fiddle with your root account is the last of your worries.

Just make sure your password is as strong as you would apply to the root account.

---

### Post by Randymanme on 2012-11-23
> **snowpine said:**
> The root account in Ubuntu is not passwordless  (as your question implies) but rather the account is completely  disabled.

> **CharlesA said:**
> Yeah, the root account is "locked"

Good catch.

[http://news.softpedia.com/news/Canonical-We-Have-Root-Trust-Us-294538.shtml](http://news.softpedia.com/news/Canonical-We-Have-Root-Trust-Us-294538.shtml)

" . . . [I]Erm, we have root. . . . "
[/I]

---

### Post by CharlesA on 2012-11-23
> **Randymanme said:**
> [http://news.softpedia.com/news/Canonical-We-Have-Root-Trust-Us-294538.shtml](http://news.softpedia.com/news/Canonical-We-Have-Root-Trust-Us-294538.shtml)

" . . . [I]Erm, we have root. . . . "
[/I]
Your point is? Canonical manage the repos, so they effectively have you access to whatever is in the repos.

---

