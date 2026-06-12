---
title: "Cant Intall repository of any kind."
date: 2020-02-06
forum: New to Ubuntu
---

### Post by dreico332 on 2020-02-06
Hellow guys,
i am kind of new in Ubuntu and here is the problem,

I want to install some apps in Ubuntu 18.04 Desktop.And for that i need to install some ppa repository i am right

The problem is i cant . When n i try to install any of ppa this is what i get:


dreico@Ubuntu1804LTSDesktop:~$ sudo add-apt-repository ppa:noobslab/apps
[sudo] password for dreico: 


I enter my pass and stays there doing nothing. The cursor is blinking right under [sudo] .And is not only that ppa i have the problem. Wharever repository ppa i want to install is doing exaxcy the same thing.
Can you help me guys?

Thank you very much,

Konstantinos.


***Update***. After 5 min sitting there doing nothing i got this:

> This PPA Contains Applications for Ubuntu/Linux Mint from different sources but debianized by [http://www.NoobsLab.com](http://www.NoobsLab.com)
 More info: [https://launchpad.net/~noobslab/+archive/ubuntu/apps](https://launchpad.net/~noobslab/+archive/ubuntu/apps)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Error: retrieving gpg key timed out.



---

### Post by CelticWarrior on 2020-02-06
Maybe a dumb question: Do you have an active internet connection?

---

### Post by dreico332 on 2020-02-06
Internet Connection Is Active. I though that too but is stable with cat6 cable .  1gbps a up and running.

---

### Post by Frogs Hair on 2020-02-06
I get gpg key security error when adding the repository and should due to using a development release. perhaps the key is outdated and the maintainers are unaware of it .I see no updates for the linked ppa in over a year so I would try again later and report the error on launchpad if needed. 
[https://launchpad.net/~noobslab/+archive/ubuntu/apps](https://launchpad.net/~noobslab/+archive/ubuntu/apps)

---

### Post by CelticWarrior on 2020-02-06
> **Frogs Hair said:**
> I get gpg key security error when adding the repository and should due to using a development release. perhaps the key is outdated and the maintainers are unaware of it .I see no updates for the linked ppa in over a year so I would try again later and report the error on launchpad if needed. 
[https://launchpad.net/~noobslab/+archive/ubuntu/apps](https://launchpad.net/~noobslab/+archive/ubuntu/apps)

This ^^^

But you also said > Wharever repository ppa i want to install is doing exaxcy the same thing.
If so something else is wrong. Can you please post the other PPAs you're trying to add?

---

### Post by mrdc76 on 2020-02-08
> **dreico332 said:**
> Hellow guys,
i am kind of new in Ubuntu and here is the problem,

I want to install some apps in Ubuntu 18.04 Desktop.And for that i need to install some ppa repository i am right



No, you are wrong. To install "some" apps, you don't need to install "some" ppa unless the specific app is not available from the default Ubuntu repositories and you actually know that you *need* that specific app.

---

### Post by Frogs Hair on 2020-02-08
> **mrdc76 said:**
> No, you are wrong. To install "some" apps, you don't need to install "some" ppa unless the specific app is not available from the default Ubuntu repositories and you actually know that you *need* that specific app.

^^
Check the repository for applications first.

---

### Post by oldrocker99 on 2020-02-09
If you get errors when using the repos, it would be a good idea to choose another mirror from the software update app.

---

