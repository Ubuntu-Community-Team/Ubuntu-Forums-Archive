---
title: "how to install current ant 1.8.4"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by 007casper on 2013-02-13
I downloaded the latest ant 1.8.4 and would like to install it properly, what is the best way?


I have tried
> 
cd /usr/local/
mkdir ant
mv /home/user/apache-ant-1.8.4-bin.zip /usr/local/ant
> 
cd /usr/local/ant
unzip apache-ant-1.8.4-bin.zip

When I unzip, I get folder apache-ant-1.8.4

then
> 
cd /home/user 
vi .bashrc

added the line on .bashrc
> 
#ant
export ANT_HOME=/usr/local/ant/apache-ant-1.8.4

then tried 

> ant -version
The program 'ant' can be found in the following packages:
 * ant
 * ant1.7
Try: apt-get install <selected package>

I dont want ant1.7

[B]what is the best way to install the zip ant?  

Is the directory correct?  

Should I put on /usr/local instead of creating ant directory?[/B]

---

### Post by 007casper on 2013-02-13
it works!
 > 
sudo ln -s /usr/local/ant/apache-ant-1.8.4/bin/ant /usr/bin/ant

ant -version
Apache Ant(TM) version 1.8.4 compiled on May 22 2012

---

### Post by oldos2er on 2013-02-13
ant1.8.2 is in the repositories. If you want to install it, run ```
sudo apt-get update && sudo apt-get install ant
```

---

### Post by sushant1 on 2013-05-08
Hi casper,
Did you got the reply to your query "Installing ant 1.8.0" from tar file. I am getting getting error like 'The program ant can be found in following packages: ant ant1.7. pl. share your experience.

---

