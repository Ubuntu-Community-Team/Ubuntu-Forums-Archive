---
title: "shellscripting"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by Rakeshvijayan on 2012-08-10
hi friends 

I am new in shell scripting ,I wish to know something from your knowledge ..

I wish to add this below commands in **sudo gedit /etc/mysql/my.cnf   ** file [Under the Basic settings section, ] 
[FONT=Courier New]*# UTF-8 Defaults for Koha *[/FONT]
[FONT=Courier New]*init-connect='SET NAMES utf8' *[/FONT]
[FONT=Courier New]*character-set-server=utf8 *[/FONT]
[FONT=Courier New]*collation-server=utf8_general_ci *[/FONT]

how can I do it ? is it possible to do so ?

Thanks 
 

 
[FONT=Courier New][/FONT][FONT=Courier New][/FONT]

---

### Post by codemaniac on 2012-08-10
If it is a one time activity you might not need to scriptize it .

```
echo -e "init-connect='SET NAMES utf8'\ncharacter-set-server=utf8 \ncollation-server=utf8_general_ci" | sudo tee -a /etc/mysql/my.cnf
```

The above commanline will append the configuration entries to the mentioned mysql conf file .Before making changes to the file dont forget to get a back up .

```
sudo cp  /etc/mysql/my.cnf  /etc/mysql/my.cnf_orig
```

---

### Post by Rakeshvijayan on 2012-08-10
> **codemaniac said:**
> If it is a one time activity you might not need to scriptize it .

```
echo -e "init-connect='SET NAMES utf8'\ncharacter-set-server=utf8 \ncollation-server=utf8_general_ci" | sudo tee -a /etc/mysql/my.cnf
```The above commanline will append the configuration entries to the mentioned mysql conf file .Before making changes to the file dont forget to get a back up .

```
sudo cp  /etc/mysql/my.cnf  /etc/mysql/my.cnf_orig
```

there is a basic setting line in the my.cnf file I need to add this under this one ,is this do so ?is it possible ?

And I have one question remain ,is it possible execute  password using ssh while we create script ?
this is the example 
ssh koha@ip
password 
scp -r koha@ip:~/backup ~/Desktop
password

---

### Post by codemaniac on 2012-08-10
> **Rakeshvijayan said:**
> there is a basic setting line in the my.cnf file I need to add this under this one ,is this do so ?is it possible ?

And I have one question remain ,is it possible execute  password using ssh while we create script ?
this is the example 
ssh koha@ip
password 
scp -r koha@ip:~/backup ~/Desktop
password

Any type of text file manipulation is possible through native Unix utilities .Please post your exact requirement .

In order to do a passwordless ssh , you need to set up public ket authentication .Please follow the below guide .

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by Rakeshvijayan on 2012-08-13
> **codemaniac said:**
> Any type of text file manipulation is possible through native Unix utilities .Please post your exact requirement .

In order to do a passwordless ssh , you need to set up public ket authentication .Please follow the below guide .

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)


I had already read this one , my question is, is it possible to  give password in the script ,is it possible to do that .....  thanks for the help

---

### Post by bodhi.zazen on 2012-08-13
> **Rakeshvijayan said:**
> I had already read this one , my question is, is it possible to  give password in the script ,is it possible to do that .....  thanks for the help

Use the application "expect"

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

---

### Post by Rakeshvijayan on 2012-08-13
> **bodhi.zazen said:**
> Use the application "expect"

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

look friend I am new here in shell scripting this is new idea for me ,by learn this it take more time to learn . need an scripting skills of any one , 
my question is how to provide password through the script for the ssh service 
This is mostly frequent for me 

Thanks

---

### Post by albandy on 2012-08-13
> **Rakeshvijayan said:**
> look friend I am new here in shell scripting this is new idea for me ,by learn this it take more time to learn . need an scripting skills of any one , 
my question is how to provide password through the script for the ssh service 
This is mostly frequent for me 

Thanks

As said before, use expect to send your credentials. expects interacts as a real user. Read the expect docuemntation and you will be able to make what you want.

Expect examples:
[http://www.thegeekstuff.com/2010/10/expect-examples/](http://www.thegeekstuff.com/2010/10/expect-examples/)

---

### Post by codemaniac on 2012-08-13
> **Rakeshvijayan said:**
> I had already read this one , my question is, is it possible to  give password in the script ,is it possible to do that .....  thanks for the help

Passwords were never meant to be provided in some configuration files for some scripts/programs to be read and get executed .This will deny the 35 years of Unix security .

---

### Post by Rakeshvijayan on 2012-08-16
> **codemaniac said:**
> Passwords were never meant to be provided in some configuration files for some scripts/programs to be read and get executed .This will deny the 35 years of Unix security .
Thanks for the valuable information , I want to learn this one I am trying give it on my small network only for learning .need more help from you all this thread may never close because I need more information from you all

---

### Post by Rakeshvijayan on 2013-03-04
any one use the shell scripting for back up data form the server to other pc .> 
#!/usr/bin/expect  set timeout 20  set ip [lindex $argv 0]  set user [lindex $argv 1]  set password [lindex $argv 2]  spawn ssh "$user\@$ip"  expect "Password:"  send "$password\r";  interact

I dont want this type of login I need to ask ./filename.sh only , user name and password must saved to my scrip .Is it possible to do so .I need the script for taking backup my koha folder every by using crontab .please any one help me to do so

---

