---
title: "Creating a root user"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by italo2 on 2014-02-11
Hello everyone. I'm a beginner in a Linux World and a i have a question.

I'm trying to create a new user from terminal.
I already created and then, i gave root privileges in "visudo".

```

root       ALL=(ALL:ALL) ALL
deployer ALL=(ALL) NOPASSWD:ALL
```

My question is, when i try some commands, the terminal ask for a password, why? I set nopasswd for my new user.

An example:

```
sudo apt-get install language-pack-id
[sudo] password for deployer: 
```

Thanks! 

Obs: sorry about my english =)

---

### Post by Dave_L on 2014-02-11
This article explains how to do that, but says that it's not recommended:
[https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo](https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo)

Since you're a "beginner in a Linux World", it might be a good idea to follow the article's advice. Reading the whole article may be helpful too. :)

---

### Post by Dave_L on 2014-02-11
(duplicate post - please delete)

---

### Post by Gone fishing on 2014-02-11
You wan't to give a user admin powers without a password? This is a bad idea, personally I would limit the number of users that have admin privalages and those that do need to use a password before they make system changes. You do know that you can make admin users using the gui (system sdettings > User Accounts)

---

### Post by italo2 on 2014-02-11
Thanks Dave. I'm gonna read the article. Sorry about the duplicate post.

Gone fishing, i don't have access to graphic interface. I'm trying to deploy an app to amazon ec2. In my deploy, using Ruby on Rails, i have a code in my local machine that deploy to amazon.
Because of this, i can't have a password in my user on remote server.

---

### Post by Dave_L on 2014-02-11
The duplicate post was mine, not yours. I hit the submit button twice by mistake.

---

