---
title: "how can I upgrade phpmyadmin of zpanel on ubuntu 12.04"
date: 2015-05-13
forum: New to Ubuntu
---

### Post by salim5 on 2015-05-13
I am using the latest version of zpanel which comes with mysql 5.5.41 on phpmyadmin.But I need mysql 5.6 as I have to use both foreign key and full text search.
Is it possible to upgrade phpmyadmin on latest zpanel version?
How can I do this?
Any suggestions would be appreciated.

---

### Post by cariboo on 2015-05-13
What version of Ubuntu are you using,? Mysql-server is a meta package that is in the vivid repositories. Check [here]("http://packages.ubuntu.com/vivid/mysql-server-5.6") to see all the packages mysql-server installs.

---

### Post by salim5 on 2015-05-13
I'm using ubuntu 12.04 64 bits.
I was following this question [http://askubuntu.com/questions/422612/installing-mysql-5-6-using-ppa](http://askubuntu.com/questions/422612/installing-mysql-5-6-using-ppa) and did exactly what mentioned.Everything worked fine and got no error message.But instead of upgrading mysql to 5.6,it stay at 5.5 version which is the current one.

Any suggestions?

---

### Post by cariboo on 2015-05-13
Did you try:

```
sudo apt-get -y purge mysql-server
sudo apt-get -y autoremove
sudo apt-get -y install software-properties-common
sudo add-apt-repository -y ppa:ondrej/mysql-5.6
sudo apt-get update
sudo apt-get -y install mysql-server
```

---

### Post by salim5 on 2015-05-13
I used that same code again and it worked on second time.Now mysql 5.6 is installed.
But when I run zpanel,I get the following error
Critical Error: [0100] - Unable to connect or authenticate to the ZPanel database (zpanel_core).

Please help.

---

### Post by walttheboss on 2015-05-14
We had the same problem on 12.04.  Using the ondrej ppa worked for a while.  Then Moodle started throwing errors.  We migrated to 14.04.  That is my recommendation.

---

### Post by cariboo on 2015-05-14
> **salim5 said:**
> I used that same code again and it worked on second time.Now mysql 5.6 is installed.
But when I run zpanel,I get the following error
Critical Error: [0100] - Unable to connect or authenticate to the ZPanel database (zpanel_core).

Please help.

Seeing as zpanel isn't available in the repositories, you will have to get help for your problem from them.

---

### Post by Holger_Gehrke on 2015-05-14
> **salim5 said:**
> 
Critical Error: [0100] - Unable to connect or authenticate to the ZPanel database (zpanel_core).


Well, purging the database server obviously erases the databases ...

Running the installer for ZPanel again would not be a good idea, it would abort since it wants a freshly installed OS and would overwrite the package sources to download only official packages. Try 
```

wget https://raw.github.com/zpanel/installers/master/install/Ubuntu-12_04/10_1_1.sh 

```
to download the installer script and take a look at lines 255 to 270. Those seem to contain the setup for the database zpanel uses. You can build your own script out of these lines to hopefully set things right.

---

