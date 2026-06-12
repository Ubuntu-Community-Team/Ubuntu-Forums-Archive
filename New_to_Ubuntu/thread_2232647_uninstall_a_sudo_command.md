---
title: "uninstall a sudo command"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by Ghune on 2014-07-03
After installing Xubuntu yesterday, I wanted to install Skype on my old laptop today, and I couldn't find any Skype program in the Ubuntu Software Center. So I tried to find something in a forum and found a guy who said that using this command should work:
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner" && sudo apt-get update

2 questions:

First, is it a risk to install Skype if it's not found on the "official" official center?
Second, I actually don't need it anymore because I have Skype on my tablet. How do I remove what the command installed? (and nothing happened, actually)

Finally, when I use a command, can I have the list of everything I've typed in case I need to explain what I did in order to solve a problem?

Thanks for your help.

---

### Post by sandyd on 2014-07-03
Moved to absolute beginners section

> **Ghune said:**
> After installing Xubuntu yesterday, I wanted to install Skype on my old laptop today, and I couldn't find any Skype program in the Ubuntu Software Center. So I tried to find something in a forum and found a guy who said that using this command should work:
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner" && sudo apt-get update

2 questions:

First, is it a risk to install Skype if it's not found on the "official" official center?
Second, I actually don't need it anymore because I have Skype on my tablet. How do I remove what the command installed? (and nothing happened, actually)

Finally, when I use a command, can I have the list of everything I've typed in case I need to explain what I did in order to solve a problem?

Thanks for your help.
1. Its in the Canonical repos (Canonical is basically the company behind Ubuntu)
2. post the output of
```

ls -l /etc/apt/sources.list.d
cat /etc/apt/sources.list
```

---

### Post by kc1di on 2014-07-03
With that command all you did was add a repository. you didn't actually install anything yet.  
[Here's a page ]("http://www.noobslab.com/2014/01/skype-released-new-version-install-in.html")with the correct way to install skype on ubuntu. 
It's never as safe to add sources that are not approved by conical, but that being said, I have had no problems with skype here.

---

### Post by Rob Sayer on 2014-07-04
Install Synaptic Pagkage Manager if you don't already have it.  That and the terminal are the only way I install any more.  Many, many linux people much more knowledgeable than I recommend synaptic.

One of the nice things about synaptic is that you can delete 3rd party ppa's quite easily.

Maybe too easily for noobs.  Double check what you delete there ...

---

### Post by grahammechanical on 2014-07-04
Skype is not in the software centre because it is proprietary software and the developers of Skype have not submitted it for inclusion in the software centre. To be accepted in the software centre an application has to be code audited to check if the application will do something malicious to the OS and that would require the Skype developers to open their code to examination by Ubuntu developers.

So, although Skype is free software it is not Free and Open Source Software (FOSS).

Regards.

---

### Post by yancek on 2014-07-04
sudo apt-get install skype worked for me on Ubuntu and Mint last week.

---

