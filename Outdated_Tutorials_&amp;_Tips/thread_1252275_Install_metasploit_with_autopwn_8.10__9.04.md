---
title: "Install metasploit with autopwn 8.10 / 9.04"
date: 2009-08-28
forum: Outdated Tutorials &amp; Tips
---

### Post by garymc1 on 2009-08-28
1 Install Ruby & Subversion

sudo apt-get install subversion ruby libruby rdoc libyaml-ruby libzlib-ruby
sudo apt-get install libopenssl-ruby libdl-ruby libreadline-ruby
sudo apt-get install libiconv-ruby rubygems libgtk2-ruby libglade2-ruby

2 Download & untar metasploit
wget "http://spool.metasploit.com/releases/framework-3.2.tar.gz"
tar -zxvf framework-3.2.tar.gz
cd /home/username/framework-3.2/
svn update

3 Install PostgreSQL
sudo apt-get install postgresql postgresql-client postgresql-contrib
sudo apt-get install pgadmin3


4 Set password for postgres
sudo su postgres -c psql
ALTER USER postgres WITH PASSWORD 'your password';

\q

sudo passwd -d postgres
sudo su postgres -c passwd

Now enter the same password that you used previously('your password'). 

5 Install ActiveRecord and Postgres
sudo gem1.8 install activerecord
sudo apt-get install ruby1.8-dev 
sudo apt-get install libpq-dev 
sudo gem1.8 install postgres

6 From the framework directory run
su postgres

Enter the password ('your password') you have set before

7 Run metasploit
./msfconsole
load db_postgres
db_create test
db_hosts
db_nmap IP ADDRESS

Check for on line hosts
db_hosts

Start the exploit

db_autopwn -t -p -e -s -b

sessions -l

sessions -i


#####For educational purposes only#####

---

### Post by danuk88 on 2009-08-30
I am using ubuntu 8.10.... 

Worked first time

nice one

Cheers.

---

### Post by slb33 on 2009-09-02
Worked fine until I got to nmap:

msf > db_nmap xxx.xxx.xxx.xxx
[-] The nmap executable could not be found

Seems like I'm missing nmap I guess!

---

### Post by garymc1 on 2009-09-02
Install nmap go to system > administration > synaptic package manager

---

### Post by ogredeschnique on 2009-10-06
Seriously, why is it necessary to su to postgres? Can't you just do 
> msf > load db_postgres

This seems more complicated than it should be. 

Seems, very similar to this thread: 
[http://ubuntuforums.org/showthread.php?t=1069859](http://ubuntuforums.org/showthread.php?t=1069859) 

[Here]("http://pauldotcom.com/wiki/index.php/Episode124#Tech_Segment:_Automating_Exploitation_With_Metasploit.27s_db_autopwn") are some instructions for autopwn that have worked for me in the past, that seem a lot simpler, aside from your instructions about installing necessary packages, which were very useful.

---

### Post by FlapBags on 2009-12-26
THIS TUTORIAL IS A BIG FAIL
 
FAIL @ 
 
5 Install ActiveRecord and Postgres
sudo gem1.8 install activerecord
sudo apt-get install ruby1.8-dev 
sudo apt-get install libpq-dev 
sudo gem1.8 install postgres
 
SORRY, "sudo: gem1.8: command not found"
 
Cannot complete the installation with these instructions, this tutorial is VOID and should be removed.

---

### Post by ogredeschnique on 2009-12-28
> **FlapBags said:**
> THIS TUTORIAL IS A BIG FAIL
SORRY, "sudo: gem1.8: command not found"


Do you have rubygems installed?

> $ aptitude search rubygems
i   rubygems                                - package management framework for Ruby libraries/ap
p   rubygems-doc                            - package management framework for Ruby libraries/ap
i A rubygems1.8                             - package management framework for Ruby libraries/ap
p   rubygems1.9                             - package management framework for Ruby libraries/ap
p   rubygems1.9.1                           - package management framework for Ruby libraries/ap


[http://www.darkoperator.com/installing-metasploit-in-ubunt/](http://www.darkoperator.com/installing-metasploit-in-ubunt/)
(that is the correct link, no U on the end of ubuntu. no biggy)

Excellent instructions from Carlos Perez. (now an official metasploit dev). Also, there is an installer script that places metasploit into /opt and creates all links everything all pretty like, so you can run it from anywhere. 

[http://www.metasploit.com/framework/download](http://www.metasploit.com/framework/download)

Also autopwn should work if you have all dependencies, it will tell you what it is missing. 

Still, I would imagine that there are better places than the ubuntu forums to learn security stuff like this. 
e.g. Both of the links in this post direct the clicker else where.

---

