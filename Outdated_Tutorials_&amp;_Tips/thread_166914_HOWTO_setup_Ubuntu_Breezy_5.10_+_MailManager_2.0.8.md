---
title: "HOWTO setup Ubuntu Breezy 5.10 + MailManager 2.0.8"
date: 2006-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jbaloul on 2006-04-27
HOWTO setup Ubuntu Breezy 5.10 + MailManager 2.0.8 + PostgreSQL-7.4 + Zope-2.7

Orignially Posted at:
[http://howtoforums.net/viewtopic.php?t=18](http://howtoforums.net/viewtopic.php?t=18)

###Basics
#create root # i personally preffer to create root over sudo
sudo passwd root

#configure hostname and nic
vim /etc/hostname
vim /etc/hosts
vim /etc/network/interfaces

#restart nic
/etc/init.d/networking restart

apt-get update
apt-get dist-upgrade

#reboot

apt-get install openssh-server
###

#enable universe in sources.list
vim /etc/apt/sources.list
apt-get update

#installation notes for breezy mailmanager postgresql 7.4 apache2
apt-get install postgresql-7.4
apt-get install apache2 #not required if using only zope 
apt-get install python2.4-psycopg
apt-get install postgresql-contrib-7.4
apt-get install zope2.7-psycopgda zope2.7-sandbox

vim /etc/postgresql/7.4/main/pg_hba.conf
	add this:
	# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD
	local   mailmanager mailmanager                       md5
	host    mailmanager mailmanager 127.0.0.1/32          md5
# make sure this is not set to "ident sameuser" as it will require a local account
	local   all         all                                             md5
	#
#for debugging open this up:
	host all all 0.0.0.0 0.0.0.0 md5

#for more info on postgresql authentication see:
# [http://www.postgresql.org/docs/current/static/client-authentication.html](http://www.postgresql.org/docs/current/static/client-authentication.html)
# [http://www.postgresql.org/docs/current/static/client-authentication.html#AUTH-PG-HBA-CONF](http://www.postgresql.org/docs/current/static/client-authentication.html#AUTH-PG-HBA-CONF)

ln -s /usr/share/postgresql/7.4/ /usr/share/pgsql

vim /etc/postgresql/7.4/main/postgresql.conf
	make sure this is enabled:
	tcpip_socket = true


/etc/init.d/postgresql-7.4 restart

# assuming the tar file is in the working directory, (i took home for my working dir) you can do this on a user lever
tar -xzf MailManager-2.0.8.tar.gz
tar -xzf 3rdParty-2.0.3.tar.gz
chmod -R 777 MailManager
cd MailManager/
#export PYTHONPATH=.
#./scripts/setupdb.py -p password -a /usr/share/pgsql/contrib/tsearch2.sql mailmanager

echo "CREATE DATABASE postgres;" |psql -d template1

export PYTHONPATH=.:$PYTHONPATH
su postgres 
./scripts/setupdb.py -p password -a /usr/share/pgsql/contrib/tsearch2.sql mailmanager

#should see this:
Database has been configured
When creating a ZPsycopgDA connection in the ZMI, use the following
connection string

    dbname=mailmanager user=mailmanager password=password


################v2.0.7
psql 
and type the following... 
CREATE USER mailmanager WITH ENCRYPTED PASSWORD 'password';
#should echo the command CREATE..by default postgre echo's the successful command
ALTER USER mailmanager WITH ENCRYPTED PASSWORD 'password';
CTRL+D #to exit

#should see this:
Database has been configured
When creating a ZPsycopgDA connection in the ZMI, use the following
connection string

    dbname=mailmanager user=mailmanager password=password
######################v2.0.7


sudo cp -vr ~/MailManager /var/lib/zope2.7/instance/sandbox/Products/.
sudo cp -vr ~/3rdParty/* /var/lib/zope2.7/instance/sandbox/Products/.
sudo chown -R zope.zope /var/lib/zope2.7/instance/sandbox/Products/

sudo rm -fr /var/lib/zope2.7/instance/sandbox/Products/ZmySQLDA #if MYsql is not needed


Start Zope and login to the Zope Management Interface (ZMI). This will
  usually be at the address [http://127.0.0.1:8080/manage](http://127.0.0.1:8080/manage)

  From the 'Add' menu select 'Z Psycopg Database Connection' and create a
  connection with the id 'mailmanager_db'. Make sure that "Use Zope's Internal
  Date Time" is checked.

  MailManagers can now be added by selecting 'MailManager' from the 'Add' menu.
  For the purposes of these install instructions we will assume that MailManager
  is added with the id 'mailmanager' but it can of course be called anything.

  Optionally you can specify a schema when you install MailManager. PostgreSQL
  schema allow you to have multiple MailManager instances sharing a single
  database. In most cases you can simply leave this field blank.

  You can now log into MailManager by visiting
  [http://127.0.0.1:8080/mailmanager](http://127.0.0.1:8080/mailmanager)

  The next stage is to get mail into MailManager. There are two
  different approaches: getting mail from a POP3 or IMAP server, and
  forwarding mail directly into MailManager. These methods can be
  mixed, so some accounts can get their mail while others have mail
  forwarded.

#If you don't have a local mail server installed then...
Add MailHost product into the MailManager instance... and set the mail relay
IP/host

#TODO
Get Mail Method (ZopeScheduler)

    To use the get mail method, login into MailManager, create some
    accounts though the Settings tab and set routing to 'Get from
    server'.

    Go into the Zope Management Interface (ZMI) and select 'Zope Scheduler'
    from the 'Add' menu. Within the scheduler you will need to select a path
    which would be '/mailmanager' in our example and then select a frequency.
    Mail will then be collected from the POP3 or IMAP server(s) at that
    frequency.

  Get Mail Method (Classic)

    Mail is fetched by calling the getMail method of the MailManager
    instance.  For example, if you installed MailManager with the id
    'mailmanager' in the top level directory of Zope then you can call
    getMail by visiting [http://myserver:8080/mailmanager/getMail](http://myserver:8080/mailmanager/getMail).

    To ensure that getMail is called regularly you can setup a cronjob,
    or equivalent on your platform, to call the MMGetMail.py script, say
    every 10 minutes. You will need to set the MM_URL constant in the
    script to the actual URL of your MailManager instance.

  Forwarding Method

    To use the mail forwarding method, login into MailManager, create
    some accounts though the Settings tab and set routing to 'Incoming
    mail forwarded to Account'.

    Next configure your mail system to call the MMMailIn.py script when
    new mail is received (or MMMailIn-Qmail.py script if you use
    Qmail). You can normally do this though a .forward file. You will
    need to set the MM_URL constant in the script to the actual URL of
    your MailManager instance.


###########
Thanks to all the supportive guys at #mailmanager at freenode....YOU GUYS ROCK!!!
[http://www.logicalware.org/](http://www.logicalware.org/)
###########

---

