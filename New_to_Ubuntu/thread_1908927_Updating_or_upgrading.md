---
title: "Updating or upgrading"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by Kingnothing412 on 2012-01-14
i have another question......Is it worth it upgrading from 11.10 to 12.04 alpha? And when i upgrade , does it just simply upgrade it and keep all my programs and settings or do i have to uninstall  it and intall the other one?

---

### Post by overdrank on 2012-01-14
> **Kingnothing412 said:**
> i have another question......Is it worth it upgrading from 11.10 to 12.04 alpha? And when i upgrade , does it just simply upgrade it and keep all my programs and settings or do i have to uninstall  it and intall the other one?

Hi and welcome, I have moved your post to it's own thread. Please do not highjack someone else support thread. :)

---

### Post by Frogs Hair on 2012-01-14
It will keep only compatible programs , and settings . I would avoid upgrading to an Alpha release unless you are interested in testing and filing bug reports to improve the release .

If you expect an Alpha to preform like a standard release you may be in for a surprise . What works great one day may not work on another . 12.04 LTS will be around for 5 years this time , so don't be in a hurry .

---

### Post by Kingnothing412 on 2012-01-15
> **overdrank said:**
> Hi and welcome, I have moved your post to it's own thread. Please do not highjack someone else support thread. :)
Oh ok. I Wasn't sure if i should make a new thread. Sorry about that and thanks :)

---

### Post by Kingnothing412 on 2012-01-15
> **Frogs Hair said:**
> It will keep only compatible programs , and settings . I would avoid upgrading to an Alpha release unless you are interested in testing and filing bug reports to improve the release .

If you expect an Alpha to preform like a standard release you may be in for a surprise . What works great one day may not work on another . 12.04 LTS will be around for 5 years this time , so don't be in a hurry .
Ok Thanks. So i should wait for the beta right?

(um....sorry for the double post.....i thought it would become one with the previous one :s Where is the delete button? i can't find it........)

---

### Post by BC59 on 2012-01-15
Depends for what you need the OS. If you like to play and you need problems to solve, go for 12.04 alpha or beta. If you like a stable OS to work without issues, install 11.10 instead.

---

### Post by Frogs Hair on 2012-01-15
12.04 will be more like the finished product and likely  more stable as a beta . As with any installation backup important data before proceeding .

---

### Post by Paqman on 2012-01-15
> **Kingnothing412 said:**
> Is it worth it upgrading from 11.10 to 12.04 alpha?

No.

12.04 is still under development. By all means, get involved in helping test it, but it shouldn't be used as your main system. You should expect a lot of updates, daily breakage, and you should only get involved if you have the skills and time available to troubleshoot, raise bug reports and generally participate actively in testing.

Helping out with testing is a good thing, especially because faults found this early in the cycle are much more likely to be fixable before release day, but I'd advise installing it on a separate partition (a VM is not very useful for testing).

Generally things have settled down pretty well during the beta(s), so if you absolutely *have* to upgrade your main system, wait till then.

---

### Post by Fernhill Linux Project on 2012-01-15
If you want to test 12.04 now, the best way is to install it to an external hdd or usb stick, just make sure that grub is installed to that drive, not the internal one.

---

### Post by Kingnothing412 on 2012-01-20
i see , well i'll just keep 11.10 on my netbook then. Also , just another quick question , when is the beta going to be released? i remember seeing a list of how it's suposed to be on a blog somwhere but i can't find it now for some reason......:/

Anyway thanks to everyone for the answers :)

---

### Post by BC59 on 2012-01-20
Beta is due for 17 of February.
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)
But you are going to see many freezes and crashes. Better to wait until the final release and a little more. In any case the difference between 11.10 and 12.04 is minimal.

---

### Post by buckyaustin on 2012-01-20
I was wondering about updating to the alpha for testing reasons, plus I want to make some scripts for myself using python and bash..... I want these scripts to stay up-to-date with as little updating of them as possible.... The best chance for me to do this is to adopt 12.04 asap because it is LTS..... 

So I was wondering, when I get the alpha, how should I run it???? 
And when the beta comes how should I run that????

I dont need to know how to install, I have run Linux in nearly every way possible....Just need you recommendations and a link for the download

Since this thread is about updating... I believe this to be the correct place to ask the question....

---

### Post by BC59 on 2012-01-21
The best way for testing is through a virtual machine. Install Virtualbox e.g. and then you can inside this install the 12.04
Virtualbox you can find it in Ubuntu Software Center.
12.04 alpha is [here]("http://cdimage.ubuntu.com/daily-live/current/").

---

### Post by trikster_x on 2012-01-21
> **buckyaustin said:**
> plus I want to make some scripts for myself using python and bash..... I want these scripts to stay up-to-date with as little updating of them as possible.... The best chance for me to do this is to adopt 12.04 asap because it is LTS.....

Actually, the best way to do something like that is to make sure your current system has the most up to date versions of Python and BASH. The OS being in a constant state of flux will almost certainly have more of a negative effect on your scripts than waiting for the stable release to come out. Also, your scripts are not going to have to have huge changes made to them. If they do, you can almost be assured the new features you have to script for won't be working right anyway. Unless you are absolutely gung-ho about constantly fixing your system and reporting bugs, I would wait until the stable in April.

---

### Post by buckyaustin on 2012-01-21
Ok thank you, I will use virtual box... I don't really like the speed hit i get... but yea that is the safest way i suppose..... I will also update bash and python.... and see which is the best for me...

Also I dont mind bug reporting.... I have the time.... After all I'm only a student... Not a full programmer yet...

---

