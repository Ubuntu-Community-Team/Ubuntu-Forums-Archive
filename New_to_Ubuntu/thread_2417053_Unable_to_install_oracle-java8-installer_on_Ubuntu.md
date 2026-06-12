---
title: "Unable to install oracle-java8-installer on Ubuntu 18.04"
date: 2019-04-19
forum: New to Ubuntu
---

### Post by arjuns2 on 2019-04-19
I was trying to install oracle java on Ubuntu 18.04. I was following the instructions provided at this page: [https://tecadmin.net/install-oracle-java-8-ubuntu-via-ppa/](https://tecadmin.net/install-oracle-java-8-ubuntu-via-ppa/) and thus I ran the following commands:

*sudo** add-apt-repository **ppa*[I]:webupd8team/java 
sudo apt-get update
sudo apt-get install oracle-java8-installer

[/I]The first two commands run fine but the third one gives me the following error. 

*Package oracle-java8-installer is not **available,*[I] but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
[/I]
Can somebody please help me with this? Thanks in advance[I].
[/I]

---

### Post by CatKiller on 2019-04-19
[https://launchpad.net/~webupd8team/+archive/ubuntu/java](https://launchpad.net/~webupd8team/+archive/ubuntu/java)
> The Oracle JDK License has changed for releases starting April 16, 2019.

The new Oracle Technology Network License Agreement for Oracle Java SE is substantially different from prior Oracle JDK licenses. The new license permits certain uses, such as personal use and development use, at no cost -- but other uses authorized under prior Oracle JDK licenses may no longer be available. Please review the terms carefully before downloading and using this product. An FAQ is available here: [https://www.oracle.com/technetwork/java/javase/overview/oracle-jdk-faqs.html](https://www.oracle.com/technetwork/java/javase/overview/oracle-jdk-faqs.html)

Oracle Java downloads now require logging in to an Oracle account to download Java updates, like the latest Oracle Java 8u211 / Java SE 8u212. Because of this I cannot update the PPA with the latest Java (and the old links were broken by Oracle).

For this reason, THIS PPA IS DISCONTINUED 

---

### Post by #&amp;thj^% on 2019-04-19
Direct downloads are no longer available. Create your Oracle account first.
[https://launchpad.net/~webupd8team/+archive/ubuntu/java](https://launchpad.net/~webupd8team/+archive/ubuntu/java)
Ninja'd by CatKiller

---

### Post by arjuns2 on 2019-04-20
Thank you for the replies. I am a bit of a linux noob. I have created my Oracle account. Could someone please help me with the next steps to be followed to install Java?

---

### Post by joegry on 2019-04-20
You could try these steps.  It's not so simple since Oracle changed their licensing...  [https://www.osradar.com/how-to-install-oracle-java-on-ubuntu-18-10/](https://www.osradar.com/how-to-install-oracle-java-on-ubuntu-18-10/)

---

### Post by monkeybrain20122 on 2019-04-21
Are you sure you need it? Openjdk works just as well for 99.99% of use cases.

Also take a look at this [https://www.linuxuprising.com/2019/04/install-latest-openjdk-12-11-or-8-in.html](https://www.linuxuprising.com/2019/04/install-latest-openjdk-12-11-or-8-in.html)

---

