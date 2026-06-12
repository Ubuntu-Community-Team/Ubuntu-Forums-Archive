---
title: "Howto: Run your own virtual mail server using Ruby on Rails and..."
date: 2007-04-01
forum: Outdated Tutorials &amp; Tips
---

### Post by darrenm on 2007-04-01
Bit of a lengthy howto and encompasses quite a lot but hopefully it will help anyone wanting to do the following:

[LIST]
[*]Run their own mail server
[*]Spam filter and AV scan mail passing through
[*]Make it easy to add, change and remove domains, aliases and users from a web front end
[*]Secure their mail conversations
[/LIST]

This howto will run through:
[LIST]
[*]Installing Postfix
[*]Setting up Amavisd-new to virus scan and spam filter the mail
[*]Setting up Postfix virtual domains, users and aliases in a MySQL database
[*]Generate your own SSL certificate to allow SSL communications for sending and receiving mail.
[*]Set up Dovecot-POP3s querying the MySQL database
[*]Set up a Ruby on Rails web application (very cool) to add/change and remove domains you receive mail for, the users that will send and receive mail and set up aliases for the users.
[/LIST]

I have done this on my own Ubuntu Feisty (32bit) server, it should work for Edgy and Dapper but I can't guarantee anything. 

I will do it a few different parts so I don't have to type too much at once ;)

_Before you start_ 
You need to have port 25 forwarded onto your server for SMTP
You need to have at least one domain registered and the MX record pointing to your public IP address.

Unfortunately it won't be uninstallable without retracing all the steps as there's quite a few things to do. But nothing should be a show stopper. If you already run a Postfix mail server it may be worth just backing up your main.cf and master.cf files and dovecot.conf if you already run dovecot.

The following info has been dug up and researched by me (as well as previous experience) while in the early stages of developing UbuntuGatewayServer (previously Legus) which will have all of this built in as well as Web content filtering, OpenVPN and Roundcube webmail all configurable via the web interface.

**Part 1** - Installing packages

You will need to ensure your FQDN (fully qualified domain name) is correct.

```
sudo gedit /etc/hosts
``` put your local IP and hostname in the following format: ```
192.168.0.1     server.yourdomain.com server
``` substituting your correct IP and hostname in. Then edit /etc/hostname and put the full FQDN in there.

Then run ```
sudo hostname server.yourdomain.com
``` and check with ```
hostname --fqdn
``` it should report the full hostname back. Now Amavis has nothing to complain about. 

```
sudo apt-get update && sudo apt-get install postfix postfix-mysql amavisd-new clamav clamav-base clamav-freshclam clamav-daemon dovecot-common dovecot-pop3d mysql-client mysql-server mysql-common spamassassin ruby rubygems rails openssl cpio binutils unrar arj arc lha cabextract zoo unzoo pyzor razor dcc-client dcc-common
```

On the config for Postfix, if it asks just choose local only.

```
sudo gedit /etc/group
``` Find the line with amavis and add clamav to the end so it looks like this: ```
amavis:x:117:clamav
``` The number may vary for you.

Now MySQL - Choose a username and password or use the root user and set a password for that. Assuming you want to use root do:
```
mysql -uroot
``` then type ```
set password for 'root'@'localhost' = password('your_password');
``` of course using your own password. then just create the database: ```
mysql -uroot -p
create database vmail_development;
```

Next edit /etc/postfix/master.cf to tell it about amavis ```
sudo gedit /etc/postfix/master.cf
```
Add this to the end of the file.
```
smtp-amavis    unix    -    -    -    -    2    smtp
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
    -o disable_dns_lookups=yes
    -o max_use=20

127.0.0.1:10025    inet    n    -    -    -    -    smtpd
    -o content_filter=
    -o smtpd_restriction_classes=
    -o smtpd_delay_reject=no
    -o smtpd_client_restrictions=permit_mynetworks,reject
    -o smtpd_helo_restrictions=
    -o smtpd_sender_restrictions=
    -o smtpd_recipient_restrictions=permit_mynetworks,reject
    -o smtpd_data_restrictions=reject_unauth_pipelining
    -o smtpd_end_of_data_restrictions=
    -o mynetworks=127.0.0.0/8
    -o smtpd_error_sleep_time=0
    -o smtpd_soft_error_limit=1001
    -o smtpd_hard_error_limit=1000
    -o smtpd_client_connection_count_limit=0
    -o smtpd_client_connection_rate_limit=0
    -o smtpd_milters=
    -o local_header_rewrite_clients=
    -o local_recipient_maps=
    -o relay_recipient_maps=
    -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

```

Then run ```
sudo postconf -e "content_filter = smtp-amavis:[127.0.0.1]:10024"
``` which will add the content filter setting into /etc/postfix/main.cf

Thats the packages installed. Next we will set up Postfix and Dovecot to connect to MySQL for the destination domains, users, passwords and user aliases. So I know it's worth my time, who's going to be following this?

---

### Post by darrenm on 2007-04-02
Now we tell Postfix and Dovecot how to talk to MySQL to get user info and domain info.

_Postfix_
```
sudo postconf -e "alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps"
sudo postconf -e "alias_database = mysql:/etc/postfix/mysql_virtual_alias_maps"
sudo postconf -e "virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps"
sudo postconf -e "smtpd_sender_login_maps = mysql:/etc/postfix/mysql_sender_login_maps"
sudo postconf -e "virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps"
sudo postconf -e "virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_mailbox_domains"
sudo postconf -e "virtual_uid_maps = static:155"
sudo postconf -e "virtual_gid_maps = static:155"
sudo postconf -e "virtual_transport = virtual"
sudo postconf -e "fallback_transport = virtual"
sudo postconf -e "virtual_mailbox_base = /var/mail/vhosts"
```
Then add the user and group for Postfix to use to modify the maildir's
```

sudo groupadd -g155 vmail
sudo useradd -c "Virtual Mail User" -g155 -u155 -s/bin/false vmail
```

Now lets create the MySQL lookup files for Postfix to use:

```
sudo gedit /etc/postfix/mysql_virtual_mailbox_domains
user=root # or your username if you chose something other than root
password=yourpassword
dbname=vmail_development
hosts=127.0.0.1
query = SELECT domain FROM domains WHERE domain='%s'
```
What will happen here is that Postfix will see the connecting 3rd party mail server trying to send mail to [email]someone@yourdomain.com[/email]. It then checks its lookup tables to see if its allowed to accept mail for yourdomain.com. It does a select domain from domains where domain='yourdomain.com'; in MySQL. If you have put yourdomain.com in the list of domains then it will accept the mail and carry on. Don't worry, it just works ;)

Now the virtual_mailbox_maps:
```
sudo gedit /etc/postfix/mysql_virtual_mailbox_maps
user = root
password= yourpassword
dbname=vmail_development
hosts=127.0.0.1
query = SELECT maildir FROM users WHERE address='%s'

``` This checks the tables for which maildir it should deliver the mail to when the address is the one presented by the 3rd party mailserver. So for example it will do select maildir from users where address='someone@example.com'; This will then return example.com/someone/ which it appends onto the setting for virtual_mailbox_base which is /var/mail/vhosts

Next ones, I'll let you work out what its doing :)

```
sudo gedit /etc/postfix/mysql_sender_login_maps
user = root
password= yourpassword
dbname=vmail_development
hosts=127.0.0.1
query = SELECT address FROM users WHERE address='%s'
```
```
sudo gedit /etc/postfix/mysql_virtual_alias_maps
user = root
password=yourpassword
dbname=vmail_development
hosts=127.0.0.1
query = SELECT goto FROM aliases WHERE address='%s'
```

The databases will be created in the 3rd part where we use a Ruby on Rails web app to admin the settings.

_Dovecot_
This bit you need to edit the config files yourself so just have a look for the following settings and ensure they are unhashed and change them to what I've put if they are different..
```
sudo gedit /etc/dovecot/dovecot-sql.conf
```
```
driver = mysql
connect = host=127.0.0.1 dbname=vmail_development user=root password=yourpassword
default_pass_scheme = PLAIN
password_query = SELECT password from users WHERE address = '%u'
```
```
sudo gedit /etc/dovecot/dovecot.conf
protocols = pop3s
mail_location = maildir:/var/mail/vhosts/%d/%n
 pop3_uidl_format = %08Xu%08Xv

auth default {
mechanisms = plain

userdb static {
     args = uid=155 gid=155 home=/var/mail/vhosts/%d/%u
}

 passdb sql {
   args = /etc/dovecot/dovecot-sql.conf
}
}
```
Hope that above makes sense. If not ask and I'll post the whole files. Dovecot will now talk to MySQL fine when the database is set up. For now its using the ubuntu-provided snakeoil.pem SSL cert which is fine until we create our own SSL certificate later.

That should do for now. Any problems post here or wait till the next and final chapter where we use Ruby on Rails to create all the database schema and admin it then create an SSL certificate and key.

---

### Post by darrenm on 2007-04-05


Lets recap on what we have done so far:

[LIST]
[*]Installed Postfix mail server
[*]Installed Dovecot mail server
[*]Installed Amavis-d interface from Postfix to Spamasssassin and ClamAV
[*]Installed ClamAV and Spamassassin
[*]Set up the Postfix virtual mail environment
[*]Set up the Dovecot virtual mail environment
[/LIST]

Now we need to create the database tables, set up the Rails application and add some aliases. Then finally we can make our own SSL certificate and key for SSL/TLS SMTP and POP3 connections.

**Database Schema** (purely for information purposes, we don't need to do this. Explained in a moment)
```
+-----------------------------+
| Tables_in_vmail_development |
+-----------------------------+
| aliases                     | 
| domains                     | 
| schema_info                 | 
| users                       | 
+-----------------------------+
```
```
mysql> describe aliases;
+---------+--------------+------+-----+---------+----------------+
| Field   | Type         | Null | Key | Default | Extra          |
+---------+--------------+------+-----+---------+----------------+
| id      | int(11)      | NO   | PRI | NULL    | auto_increment | 
| address | varchar(255) | YES  |     | NULL    |                | 
| goto    | varchar(255) | YES  |     | NULL    |                | 
+---------+--------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)

``` ```
mysql> describe domains;
+-----------+--------------+------+-----+---------+----------------+
| Field     | Type         | Null | Key | Default | Extra          |
+-----------+--------------+------+-----+---------+----------------+
| id        | int(11)      | NO   | PRI | NULL    | auto_increment | 
| domain    | varchar(255) | YES  |     | NULL    |                | 
+-----------+--------------+------+-----+---------+----------------+
2 rows in set (0.00 sec)

``` ```
mysql> describe users;
+----------+--------------+------+-----+---------+----------------+
| Field    | Type         | Null | Key | Default | Extra          |
+----------+--------------+------+-----+---------+----------------+
| id       | int(11)      | NO   | PRI | NULL    | auto_increment | 
| address  | varchar(255) | YES  |     | NULL    |                | 
| password | varchar(255) | YES  |     | NULL    |                | 
| maildir  | varchar(255) | YES  |     | NULL    |                | 
+----------+--------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)
```

We don't actually need to create these tables and columns, Rails does it all for us...

**Ruby on Rails**
choose a directory for the rails app. I always put them in my home dir. We aren't running on a privileged port so we can run it as a normal user.

Make sure we are using the latest version of rails. Use Gems to update it:
```
sudo gem update rails
``` then

```
mkdir ~/rubyapps
cd ~/rubyapps
rails vmail
```

Rails creates the necessary framework for you. We now need to fill in some database information.

```
cd ~/rubyapps/vmail
gedit config/database.yml
``` You will see something like the following. We are just interested in development entry, leave the test and production. ```
development:
  adapter: mysql
  database: vmail_development
  username: root
  password: yourpassword
  host: localhost
```
You will need to add this into the entry ```
socket: /var/run/mysqld/mysqld.sock
``` as RoR is expecting to see the mysql socket at /tmp/mysql.sock which isn't correct for Debian systems.

now lets just test the database connection ```
rake db:migrate
``` If you just get ```
(in /home/you/rubyapps/vmail)
``` then its fine. If it complains about something you should see whats wrong.

Now we create the data models for aliases, users and domains
```
script/generate model alias
script/generate model domain
script/generate model user
```
And then we just need to tell RoR which columns we want. (It needs to know somehow)
```
gedit db/migrate/001_create_aliases.rb
``` The file should look like this:
```
class CreateAliases < ActiveRecord::Migration
  def self.up
    create_table :aliases do |t|
    end
  end

  def self.down
    drop_table :aliases
  end
end
``` We need to add 2 columns to the aliases table: address and goto so change the file so it looks like this:
```
class CreateAliases < ActiveRecord::Migration
  def self.up
    create_table :aliases do |t|
      t.column :address,        :string
      t.column :goto,           :string
    end
  end

  def self.down
    drop_table :aliases
  end
end

``` See we just added the 2 t.column lines, one called address and one called goto, both text
Nice and easy. We do the same for the next file: ```
gedit db/migrate/002_create_domains.rb
``` Just add the following line in the same place as in the last file ```
t.column :domain,         :string
``` then finally ```
gedit db/migrate/003_create_users.rb
``` and add the following lines (again just below the create_table line)```
      t.column :address,        :string
      t.column :password,       :string
      t.column :maildir,        :string

```
Now all we do is rake the DB: ```
rake db:migrate
``` and you should see something like:
```
(in /home/darrenm/rubyapps/vmail)
== CreateAliases: migrating ===================================================
-- create_table(:aliases)
   -> 0.1861s
== CreateAliases: migrated (0.1864s) ==========================================

== CreateDomains: migrating ===================================================
-- create_table(:domains)
   -> 0.0516s
== CreateDomains: migrated (0.0522s) ==========================================

== CreateUsers: migrating =====================================================
-- create_table(:users)
   -> 0.1160s
== CreateUsers: migrated (0.1163s) ============================================

``` Now heres the really cool bit. Because Rails is convention over configuration it guesses that as we have a table called users with columns called address, password and maildir that we might want a web form to enter, display and remove these entries... We just have to tell it to put some scaffolding in place:
```
script/generate controller alias
script/generate controller domain
script/generate controller user
```
Final step here: ```
gedit app/controllers/alias_controller.rb
``` and add one line so it looks like this: ```
class AliasController < ApplicationController
  scaffold :alias
end

``` do the same for the other 2 files, domain_controller.rb and user_controller.rb so in app/controllers/domain_controller.rb it looks like this ```
class DomainController < ApplicationController
  scaffold :domain
end
``` and app/controllers/user_controller.rb is like this ```
class UserController < ApplicationController
  scaffold :user
end
``` 

Then we just start the weBrick http server ```
script/server -b 0.0.0.0
``` (the -b 0.0.0.0 listens on all interfaces, not just localhost)

Browse to the IP or hostname of the server (or localhost of you're on the same box) e.g.
[http://localhost:3000/alias](http://localhost:3000/alias) to set up the aliases
[http://localhost:3000/domain](http://localhost:3000/domain) to set up the domains
[http://localhost:3000/user](http://localhost:3000/user) to set up the users

**Final notes**
This is the most basic rails implementation you can get. There are loads of guides out there and its an awesome product. I've only had time to touch on the quickest way of doing this. I'll leave it to you to improve the web interface (until UGS comes out)
For users and aliases you should pick at least one domain as the primary domain and use that as the username/address of each user. So far me I have:

[email]darrenm@v**c.co.uk[/email] as my primary domain/username/address
darrenm aliases to [email]darrenm@v**c.co.uk[/email]
darrenm@localhost aliases to [email]darrenm@v**c.co.uk[/email]

The local user alias and @localhost aliases are so fetchmail will still work with this set up.

I think thats about it for now. If anyone really wants it I can post again with creating SSL stuff but the provided snakeoil certs are used by default so just tell Evolution/Thunderbird to connect using SSL for the POP3 server and TLS for the SMTP server.

Post if you have any problems and I'll try to help as much as possible. Hope you found this useful!

---

### Post by darrenm on 2007-04-05
Some corrections and additions:

```
sudo mkdir /var/mail/vhosts
sudo chown -R vmail:vmail /var/mail/vhosts
```

Change /etc/postfix/main.cf so the following is correct:
```
mydestination = 
mynetworks = 127.0.0.0/8 192.168.0.0/24 # assuming your subnet is 192.168.0.0, change if not

```
Don't forget to restart postfix, dovecot and amavis before anything.

when adding the users make sure the maildir is in the format of:
domain/user/
note the slash at the end. This is important. It makes it a maildir.
An example is
```
Listing users
Address 	Password 	Maildir
someone@example.com 	password 	example.com/someone/ 	Show 	Edit 	Destroy
```

Thanks to Popot for the below corrections for when using Edgy (and maybe Feisty too if you have problems)

Make sure multiverse & universe is included for apt-get install lha arc
```
deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
```

Extra ruby packages required for ruby on rails
```
apt-get install libmysql-ruby ruby1.8 ruby1.8-dev rdoc ri irb
```

As it does not contain rubygems in Ubuntu Edgy Eft 6.10 Server (Hat Tip to: Ruby on Rails on Ubuntu, How To: Ubuntu 6.10 Edgy on Rails and a few others.
```
wget http://rubyforge.org/frs/download.php/17190/rubygems-0.9.2.tgz
tar xzvf rubygems-0.9.2.tgz
cd rubygems-0.9.2
ruby setup.rb
```
After you finish the setup, feel free to remove the .tgz and rubygems folders from your desktop. 
```
gem update
gem install rails --include-dependencies
```

Dovecot:
```
sudo pico /etc/dovecot/dovecot.conf
```
Change #first_valid_uid = 500 to first_valid_uid = 150 and change #last_valid_uid = 0 to last_valid_uid = 0

---

### Post by darrenm on 2007-04-08
Would like to hear if anyones actually done this yet. I have it working fine here but I wondered if anyone had problems etc?

---

### Post by ciscosurfer on 2007-04-12
Excellent write-up darrenm!  I'll hopefully tackle it this weekend.  With the Howto you provided, the process should go smoothly.

---

### Post by darrenm on 2007-04-12
Thanks. I can't see it causing any problems aside from the data in the database tables. Theres no syntax checking on the inputted data so if you forget to put a slash at the end of the maildir for instance then it will work but dovecot won't see the correct mail folder and it will look like you have no mail. 
On the RoR app that I'm going to be putting into UGS all of this will be taken care of. Of course if you know RoR you can do your own MVC and put validation, authorisation etc in there. Good luck and let me know if you have any problems. :)

---

### Post by helios12 on 2007-04-28
Well problems problems problems :S , probably easy to solve, but i am a newbie :S.

Ok I am having problems with step 1 (and this is on a fresh install of dapper drake (6.06) desktop version):
sudo gedit /etc/hosts

I enter this and edit it so it looks like this ( for ref. my server name is mail)

127.0.0.1 localhost mail
192.168.1.6 mail.mydomain.co.uk mail

Then i edit /etc/hostname

so it says : 

mail.mydomain.co.uk.

save it and come out. At this point firefox doesn't launh, and when restarting, the boot takes a very long time, and certain programs don't launch. None the less i pressed on, and went to the terminal to do the step "sudo hostname server.yourdomain.com"
So i typed in: sudo hostname mail.entrosys.co.uk 
and it says nothing and just returns to the command line!

Then i ran hostname --fqnd, and it says mail.entrosys.co.uk.
Now i tried running "su" but it won't accept my password, yet it accepts my password for sudo :S.

I have now re-installed ubuntu, so i can start over. For reference - on my windows helm DNS zone editor i have put the following details:

Record Name -------Type ----------------------------------- Data
entropy--------------A (Host Record)--------- ------------xx.xx.xxx.xxx (my public ip)
 mail------------------A (Host Record)---------------------- xx.xx.xxx.xxx (my public ip)
 @ -------------------MX (Mail Exchange Record)----------xx.xx.xx.xxx.[21] (my public ip)
 SPF------------------TXT (Text Data Record)--------------v=spf1 ip4:xx.xx.xxx.xxx (my public ip) a mx                                                                 
                                                                          a:mail.mydomain.co.uk mx:mydomain.co.uk ~all

---

### Post by darrenm on 2007-04-28
When changing the hostname I noticed a reboot is needed before certain programs are launched. I wouldn't put the real hostname on the 127.0.0.1 line though. Mine is actually just set up like:
```
127.0.0.1 localhost
127.0.1.1 ugs.cghm.net ugs
``` so I haven't got an entry for the actual IP address and it still works fine.
```
darrenm@ugs:~$ hostname --fqdn
ugs.cghm.net
```
You can actually skip this part and leave it as dapper installed it. As long as hostname --fqdn reports back correctly then the packages won't complain.

---

### Post by helios12 on 2007-04-28
what did you put in your hostname file? also does the windows dns entries look right?

---

### Post by darrenm on 2007-04-29
Just the same: ugs.cghm.net

They look ok to me. That wouldn't affect anything at this stage though.

---

### Post by helios12 on 2007-04-29
ok, did as you said, and the install of everything else went fine :).

Great tutorial, and thanks for the additional help.

---

### Post by darrenm on 2007-04-29
Super. Thats really good to know. If you feel like it look into starting Rails on boot and customizing the views so you can do all the admin from one page. I'm now doing the Ubuntu Gateway Server admin interface in Django.

---

### Post by popot on 2007-05-14
Great stuff!!! Thanks darrenm.

Tested on a dell dimension 8200, P4 2GHZ Machine, with Ubuntu Edgy Eft 6.10 Server and it works, just a few tweaks.

[LIST=1]
[*]sudo pico /etc/apt/sources.list
Make sure multiverse & universe is included for 
sudo apt-get install lha arc
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
[*]Replaced sudo hostname server.yourdomain.com with sudo echo server.yourdomain.com.com > /etc/hostname, not sure whether it makes difference.
[*]Extra ruby packages required for ruby on rails
sudo apt-get install libmysql-ruby ruby1.8 ruby1.8-dev rdoc ri irb
[*]As it does not contain rubygems in Ubuntu Edgy Eft 6.10 Server (Hat Tip to: [Ruby on Rails on Ubuntu]("http://dnite.wordpress.com/2006/10/24/ruby-on-rails-on-ubuntu/"), [How To: Ubuntu 6.10 Edgy on Rails]("http://www.forthecode.com/user/index/28") and a few others.
sudo -i
wget [http://rubyforge.org/frs/download.php/17190/rubygems-0.9.2.tgz](http://rubyforge.org/frs/download.php/17190/rubygems-0.9.2.tgz)
tar xzvf rubygems-0.9.2.tgz
cd rubygems-0.9.2
ruby setup.rb
[INDENT]After you finish the setup, feel free to remove the .tgz and rubygems folders from your desktop. [/INDENT]
gem update
gem install rails --include-dependencies
exit
[*]sudo pico /etc/dovecot/dovecot.conf
In place of mail_location = maildir:/var/mail/vhosts/%d/%n, use default_mail_env = maildir:/var/mail/vhosts/%d/%n
[*]sudo pico ~/rubyapps/vmail/config/database.yml, enter socket: /var/run/mysqld/mysqld.run and remove   socket: /var/run/mysqld/mysqld.sock does not exist in Edgy Eft 6.10 Server 
[*]sudo pico /etc/dovecot/dovecot.conf
Change #first_valid_uid = 500 to first_valid_uid = 150 and change #last_valid_uid = 0 to last_valid_uid = 0
[/LIST]
[B]
Let me clarify, all above commands run as root (sudo or sudo -i). With apologies for any confusion.[/B]

;p
Better late than never.

---

### Post by darrenm on 2007-05-15
Thanks for the info mate. I didn't expect there to be as much of a difference in Edgy but its good to know that it will work on Edgy too.

I'll put this on the first part of the thread so no-one misses it.

---

### Post by VorDesigns on 2007-05-21
I'm wending my way through this, got the ruby error (running edgy server); will tack that next.
My PF server is an old GW500 running production.  Was looking to evaluate this for a replacement.  Some of the notes are little bothersome since you seem to indicate that this shouldn't be used in production.
Going to keep working on it anyway.
Thanks and I'll post back how it goes.

---

### Post by VorDesigns on 2007-05-21
> **VorDesigns said:**
> I'm wending my way through this.

Restarting mail server: dovecotError: Error in configuration file /etc/dovecot/dovecot.conf line 174: Unknown setting: mail_location

Used your Code:
found the pop3s easily enough, couldn't find mail_location so I put it in the mail locations section
```
mail_location = maildir:/var/mail/vhosts/%d/%n
 pop3_uidl_format = %08Xu%08Xv

auth default {
mechanisms = plain

userdb static {
     args = uid=155 gid=155 home=/var/mail/vhosts/%d/%u
}

 passdb sql {
   args = /etc/dovecot/dovecot-sql.conf
}
}
```
Will look at that in few after I figure out how to install Ruby.

---

### Post by VorDesigns on 2007-05-21
Jumped down to your errata to dealy with ruby, downloaded the specified version which is one back from current.
untarred the filles and proceed with the following errors
```
tanuki@dai_fuku_cho:~/rubyinstall$ cd rubygems-0.9.2
tanuki@dai_fuku_cho:~/rubyinstall/rubygems-0.9.2$ ruby setup.rb
-bash: ruby: command not found
tanuki@dai_fuku_cho:~/rubyinstall/rubygems-0.9.2$ ls
bin        examples  lib          post-install.rb  redist    setup.rb
ChangeLog  gemspecs  LICENSE.txt  Rakefile         Releases  test
doc        GPL.txt   pkgs         README           scripts   TODO
tanuki@dai_fuku_cho:~/rubyinstall/rubygems-0.9.2$ ./setup.rb
-bash: ./setup.rb: Permission denied
tanuki@dai_fuku_cho:~/rubyinstall/rubygems-0.9.2$ sudo ./setup.rb
sudo: ./setup.rb: command not found
tanuki@dai_fuku_cho:~/rubyinstall/rubygems-0.9.2$ sudo ruby setup.rb
sudo: ruby: command not found
```

Also, based on my initial scanning, as instructed your process will put ruby in a user directory as opposed to installing it in the "standard installation location (typically /usr/local/lib/ruby)"?

Looks like I'm stallled until I can figure out what is missing in this document or what I did wrong.

---

### Post by darrenm on 2007-05-21
> **VorDesigns said:**
> Restarting mail server: dovecotError: Error in configuration file /etc/dovecot/dovecot.conf line 174: Unknown setting: mail_location

Used your Code:
found the pop3s easily enough, couldn't find mail_location so I put it in the mail locations section
```
mail_location = maildir:/var/mail/vhosts/%d/%n
 pop3_uidl_format = %08Xu%08Xv

auth default {
mechanisms = plain

userdb static {
     args = uid=155 gid=155 home=/var/mail/vhosts/%d/%u
}

 passdb sql {
   args = /etc/dovecot/dovecot-sql.conf
}
}
```
Will look at that in few after I figure out how to install Ruby.

Thats very strange. Even their online documentation [http://wiki.dovecot.org/MailLocation](http://wiki.dovecot.org/MailLocation) shows mail_location to be the correct usage and format so I don't know why its complaining. Is it still happening now?

---

### Post by darrenm on 2007-05-21
> **VorDesigns said:**
> Jumped down to your errata to dealy with ruby, downloaded the specified version which is one back from current.
untarred the filles and proceed with the following errors
```
tanuki@dai_fuku_cho:~/rubyinstall$ cd rubygems-0.9.2
tanuki@dai_fuku_cho:~/rubyinstall/rubygems-0.9.2$ ruby setup.rb
-bash: ruby: command not found
tanuki@dai_fuku_cho:~/rubyinstall/rubygems-0.9.2$ ls
bin        examples  lib          post-install.rb  redist    setup.rb
ChangeLog  gemspecs  LICENSE.txt  Rakefile         Releases  test
doc        GPL.txt   pkgs         README           scripts   TODO
tanuki@dai_fuku_cho:~/rubyinstall/rubygems-0.9.2$ ./setup.rb
-bash: ./setup.rb: Permission denied
tanuki@dai_fuku_cho:~/rubyinstall/rubygems-0.9.2$ sudo ./setup.rb
sudo: ./setup.rb: command not found
tanuki@dai_fuku_cho:~/rubyinstall/rubygems-0.9.2$ sudo ruby setup.rb
sudo: ruby: command not found
```

Also, based on my initial scanning, as instructed your process will put ruby in a user directory as opposed to installing it in the "standard installation location (typically /usr/local/lib/ruby)"?

Looks like I'm stallled until I can figure out what is missing in this document or what I did wrong.

It looks like you haven't actually installed ruby. If you do a ```
sudo apt-get install ruby
``` does it install ruby? It should already have if you copied and pasted the command from the first post in the howto. 

Also it looks like theres a little confusion - When I wrote about the ruby app I didn't mean ruby itself, I meant the ruby on rails app which is the app you create using ruby. Does that make sense?

What stage are you at now? Is dovecot still complaining on restart?

---

### Post by VorDesigns on 2007-05-21
I just installed ruby, I had parsed out the apt-get string to smaller discreet batches making logical gueses.  didn't realize when the error below occurred that it failed everything:

```
tanuki@dai_fuku_cho:~$ sudo apt-get install ruby rubygems rails
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package rubygems
```

Will post back later.

Thanks for the clarification.

I broke it up like this for clarity and since I'm doing this on a server, I have to use nano, etc.,

Code:
```
sudo apt-get update 
sudo apt-get install postfix 
sudo apt-get install postfix-mysql 
sudo apt-get install amavisd-new 
sudo apt-get install clamav clamav-base clamav-freshclam clamav-daemon 
sudo apt-get install dovecot-common dovecot-pop3d 
sudo apt-get install mysql-client mysql-server mysql-common 
sudo apt-get install spamassassin 
sudo apt-get install ruby rubygems rails 
sudo apt-get install openssl 
sudo apt-get install cpio binutils unrar arj arc lha cabextract 
sudo apt-get install zoo unzoo pyzor razor dcc-client dcc-common
```

Once I got Ruby Installed, I was successful.  You see, this is why I commented.

when I'm through, May I PM you my revised directions?

database.yml issues:
```
You will see something like the following. We are just interested in development entry, leave the test and production. 
Code:
development:
  adapter: mysql
  database: vmail_development
  username: root
  password: yourpassword
  # errors out on my system
  # host: localhost
  # works on my system
  host:  127.0.0.1
  # socket: /var/run/mysqld/mysqld.sock
  socket: /var/run/mysqld/mysqld.run
```

---

### Post by VorDesigns on 2007-05-22
OK, 

Looks like it is running.  

Quetion:  How do I get this WeBrick to run automatically and log to a file?

---

### Post by Captain Llama on 2007-05-22
I followed the instructions and now I can't get it to work properly.  When I open a web browser and point it at the machine running the mail server to use the Ruby interface, it tells me it can't connect to the server.  When I use Evolution to try to get or send email, I get an error dialog that says "connection refused".

I've checked all my firewall settings and made sure that everything is running whenever I've tried to connect.  I can ping the server in question, I just can't connect to send/receive email or through the web interface.  Is there something I missed?

---

### Post by popot on 2007-05-22
**VorDesigns**: Just to confirm, yeah I had to leave the "socket: /var/run/mysqld/mysqld.run" in "~/rubyapps/vmail/config/database.yml" for my Edgy Eft 6.10 Server as well! My bad!

Quetion: How do I get this WeBrick to run automatically and log to a file? 
sudo ~/rubyapps/vmail/script/server -b 0.0.0.0 >> logfile. 
Have you tried anacron (cron will do as well, if you leave your server running all the time), trying at this time, to no avail as yet. If you don't mind, can we share notes on this, if you will want to take this path. /etc/init.d/ will work as well, search around the forum, you can get help with this. However, the safest way to run ruby on rails is with apache, this should help, [http://wiki.rubyonrails.org/rails/pages/Tutorial]("http://wiki.rubyonrails.org/rails/pages/Tutorial")

**Captain Llama**: Have you tried sudo ~/rubyapps/vmail/script/server -b 0.0.0.0? What version of Ubuntu are you running?

---

### Post by glentech on 2007-05-22
I got to the "rake db:migrate" command and it returns with 
"rake aborted"
"No such file or directory - /var/run/mysqld/mysqld.run"

The instructions say "If it complains ... see whats wrong"
So, where do I start? The file "mysqld.run" is not in that directory.

~ Chet

---

### Post by VorDesigns on 2007-05-22
First to your question GlenTech:
Try this from your home directory

```
cd ~/rubyapps/vmail
sudo nano config/database.yml
```
(substitute gedit if you are using the GUI)

Scroll through the file until you see something like the following. We are just interested in development entry, leave the test and production alone. 

```
development:
  adapter: mysql
  database: vmail_development
  username: root
  password: yourpassword
  # there was no host: localhost entry so I added it but
  # it errors out on my system,
  # host: localhost
  # so I went with this instead
  host:  127.0.0.1
 # rather than delete the stock entry, I commented it out so I have a way back.
 # socket: /var/run/mysqld/mysqld.sock
 # this is what the How-to says to add below
  socket: /var/run/mysqld/mysqld.run
```

---

### Post by VorDesigns on 2007-05-23
Now to my problem:

```
May 22 20:58:36 192 postfix/cleanup[4945]: fatal: open /etc/postfix/mysql_virtual_alias_maps: No such file or directory
May 22 20:58:37 192 postfix/master[4942]: warning: process /usr/lib/postfix/cleanup pid 4945 exit status 1
May 22 20:58:37 192 postfix/master[4942]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
```

I built the ruby on rails to handle the domains, users and alias' but, Postfix isn't seeing them.  What am I missing?

---

### Post by glentech on 2007-05-23
Thank you, VorDesigns,
I changed "host: localhost" to "host:  127.0.0.1" in /config/database.yml, now when I run rake db:migrate I get this:
> rake aborted!
Mysql::Error: Lost connection to MySQL server during query: SHOW TABLES

(See full trace by running task with --trace)

---

### Post by VorDesigns on 2007-05-23
I think you need to check 

> Now MySQL - Choose a username and password or use the root user and set a password for that. Assuming you want to use root do:

Code:
mysql -uroot

then type 
Code:
set password for 'root'@'localhost' = password('your_password');

of course using your own password. then just create the database: 
Code:
mysql -uroot -p
create database vmail_development;

---

### Post by Captain Llama on 2007-05-23
**popot:** i'm running Ubuntu 7.04.  The web server seems to work just fine running it as a normal user.  It turns out that there was something wrong with my dovecot configuration that I didn't find out about until I checked to see if it was running and then tried starting it manually.

---

### Post by VorDesigns on 2007-05-23
I'm still trying to figure out why Postfix is mad.

Doesn't like the alias data for root mapping to [email]user@domain.clas[/email]sifier

Doesn't like anything having to do with the SQL configuration I guess.

---

### Post by darrenm on 2007-05-23
Sorry guys I haven't got enough time to look into the issues to help tonight. I will be online a lot tomorrow night so will help work through all the problems.

VorDesigns: From quickly looking at your error it says the mysql lookup file isn't there, have you checked through the howto at the part where I've listed the MySQL files. Perhaps you missed one?

---

### Post by darrenm on 2007-05-23
[quote=VorDesigns]when I'm through, May I PM you my revised directions?[/quote]

Please. Sounds like I need to revise it quite a bit.
Perhaps we need to use django instead? ;)

---

### Post by glentech on 2007-05-23
> **VorDesigns said:**
> I think you need to check
I've done all that, still same message.
When I run "rake db:migrate" I get this-

> rake aborted!
Mysql::Error: Lost connection to MySQL server during query: SHOW TABLES

Is this something that needs to be resolved before I continue?
Thanks,

---

### Post by popot on 2007-05-23
**glentech:** just a small suggestion, please ls your /var/run/mysqld/? running "mysql -uroot -p" or "mysql -uroot", did you get into mysql? did you try "socket: /var/run/mysqld/mysqld.sock" & "host: localhost" in  ~/rubyapps/vmail/config/database.yml. :) Good luck.

---

### Post by VorDesigns on 2007-05-24
dovectot conf entry makes dovecot angry
```
tanuki@daifukucho:~$ sudo /etc/init.d/dovecot start
Starting mail server: dovecotError: Error in configuration file /etc/dovecot/dovecot.conf line 174: Unknown setting: mail_location
```

I placed the entry in 
```
## Mailbox locations and namespaces
```
using your coding verbatim
```
##
mail_location = maildir:/var/mail/vhosts/%d/%n
 pop3_uidl_format = %08Xu%08Xv

auth default {
mechanisms = plain

userdb static {
     args = uid=155 gid=155 home=/var/mail/vhosts/%d/%u
}

 passdb sql {
   args = /etc/dovecot/dovecot-sql.conf
}
}
```

---

### Post by VorDesigns on 2007-05-24
And clearly I don't have the entry syntax down correctly for the the aliases although I don't know about the rest since this is the only error at the moment and dovecot won't load

Multiply by about 10,000 lines and you know what the mail.log looks like:
```
May 23 23:17:23 daifukucho postfix/pickup[3990]: DE4C12281EB: uid=106 from=<amavis>
May 23 23:17:23 daifukucho postfix/cleanup[4043]: warning: DE4C12281EB: virtual_alias_maps map lookup problem for amavis@daifukucho.foo.bar
```

---

### Post by VorDesigns on 2007-05-24
> **darrenm said:**
> Sorry guys I haven't got enough time to look into the issues to help tonight. I will be online a lot tomorrow night so will help work through all the problems.

VorDesigns: From quickly looking at your error it says the mysql lookup file isn't there, have you checked through the howto at the part where I've listed the MySQL files. Perhaps you missed one?

I slogging through the whole thing again, from the top; making a change, restarting services or rebooting depending on what, if anything happens.

Not to worry, I'm patient, who needs sleep?  I'm doing this for free. :popcorn:

---

### Post by darrenm on 2007-05-24
> **popot said:**
> **glentech:** just a small suggestion, please ls your /var/run/mysqld/? running "mysql -uroot -p" or "mysql -uroot", did you get into mysql? did you try "socket: /var/run/mysqld/mysqld.sock" & "host: localhost" in  ~/rubyapps/vmail/config/database.yml. :) Good luck.

Yup. And if you can get into MySQL ok and ls /var/run/mysqld/ is ok then you may need to drop the whole database and create it again before raking.

> **VorDesigns said:**
> dovectot conf entry makes dovecot angry
```
tanuki@daifukucho:~$ sudo /etc/init.d/dovecot start
Starting mail server: dovecotError: Error in configuration file /etc/dovecot/dovecot.conf line 174: Unknown setting: mail_location
```

I placed the entry in 
```
## Mailbox locations and namespaces
```
using your coding verbatim
```
##
mail_location = maildir:/var/mail/vhosts/%d/%n
 pop3_uidl_format = %08Xu%08Xv

auth default {
mechanisms = plain

userdb static {
     args = uid=155 gid=155 home=/var/mail/vhosts/%d/%u
}

 passdb sql {
   args = /etc/dovecot/dovecot-sql.conf
}
}
```

This is confusing me, I don't think the version of Dovecot on Edgy is missing that setting so can you post your whole dovecot.conf file?

> **VorDesigns said:**
> And clearly I don't have the entry syntax down correctly for the the aliases although I don't know about the rest since this is the only error at the moment and dovecot won't load

Multiply by about 10,000 lines and you know what the mail.log looks like:
```
May 23 23:17:23 daifukucho postfix/pickup[3990]: DE4C12281EB: uid=106 from=<amavis>
May 23 23:17:23 daifukucho postfix/cleanup[4043]: warning: DE4C12281EB: virtual_alias_maps map lookup problem for amavis@daifukucho.foo.bar
```

Can you post your /etc/postfix/main.cf and output of ```
ls -alth /etc/postfix
```? 
> **VorDesigns said:**
> I slogging through the whole thing again, from the top; making a change, restarting services or rebooting depending on what, if anything happens.

Not to worry, I'm patient, who needs sleep?  I'm doing this for free. :popcorn: I've gone through it again not so long ago and it worked but these days I won't touch Edgy with a barge pole ;) No way you can try with Feisty?

---

### Post by darrenm on 2007-05-24
> **glentech said:**
> I got to the "rake db:migrate" command and it returns with 
"rake aborted"
"No such file or directory - /var/run/mysqld/mysqld.run"

The instructions say "If it complains ... see whats wrong"
So, where do I start? The file "mysqld.run" is not in that directory.

~ Chet

It seems the package has been changed to /var/run/mysqld/mysqld.sock now, just change that in database.yml

---

### Post by darrenm on 2007-05-24
> **VorDesigns said:**
> And clearly I don't have the entry syntax down correctly for the the aliases although I don't know about the rest since this is the only error at the moment and dovecot won't load

Multiply by about 10,000 lines and you know what the mail.log looks like:
```
May 23 23:17:23 daifukucho postfix/pickup[3990]: DE4C12281EB: uid=106 from=<amavis>
May 23 23:17:23 daifukucho postfix/cleanup[4043]: warning: DE4C12281EB: virtual_alias_maps map lookup problem for amavis@daifukucho.foo.bar
```

edit /etc/postfix/mysql_virtual_mailbox_domains and take out the hash and everything after it.

---

### Post by popot on 2007-05-24
With apologies with VorDesigns and darrenm.

The version of dovecot on Edgy Eft is an earlier version. So, mail_location = maildir:/var/mail/vhosts/%d/%n in /etc/dovecot/dovecot.conf (fesity fawn) should be default_mail_env = maildir:/var/mail/vhosts/%d/%n in /etc/dovecot/dovecot.conf (edgy eft)

Will update my 1st posting accordingly.

---

### Post by VorDesigns on 2007-05-24
> **darrenm said:**
> I've gone through it again not so long ago and it worked but these days I won't touch Edgy with a barge pole ;) No way you can try with Feisty?
I dunno, would you run Feisty on a P/II 450 with 384MB of RAM?

To your submission requestions:  I'm still walking through the document to see what I did wrong.
----------------
POSTFIX DIRECTORY:
```
tanuki@daifukucho:~$ ls -alth /etc/postfix
total 100K
drwxr-xr-x 68 root root 4.0K 2007-05-23 23:27 ..
-rw-r--r--  1 root root  133 2007-05-23 22:53 mysql_virtual_alias_maps
-rw-r--r--  1 root root  129 2007-05-23 22:49 mysql_sender_login_maps
-rw-r--r--  1 root root  130 2007-05-23 22:48 mysql_virtual_mailbox_maps
-rw-r--r--  1 root root  184 2007-05-23 22:42 mysql_virtual_mailbox_domains
drwxr-xr-x  3 root root 4.0K 2007-05-23 07:33 .
-rw-r--r--  1 root root 1.8K 2007-05-21 08:56 main.cf
-rw-r--r--  1 root root 4.9K 2007-05-20 23:31 master.cf
-rw-r--r--  1 root root 3.9K 2007-05-20 23:30 master.cf.original
-rw-r--r--  1 root root  373 2007-05-20 23:02 dynamicmaps.cf
-rw-r--r--  1 root root  18K 2006-09-10 03:48 postfix-files
-rwxr-xr-x  1 root root 6.7K 2006-09-10 03:48 postfix-script
-rwxr-xr-x  1 root root  22K 2006-09-10 03:48 post-install
drwxr-xr-x  2 root root 4.0K 2006-09-10 03:48 sasl
tanuki@daifukucho:~$ 
```

POSTFIX MAIN.CF
```
tanuki@daifukucho:~$ sudo cat /etc/postfix/main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

#
# removed (UBUNTU), they don't need to know
#
smtpd_banner = $myhostname ESMTP $mail_name 
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = daifukucho.foo.bar
alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps
alias_database = mysql:/etc/postfix/mysql_virtual_alias_maps
myorigin = /etc/mailname
mydestination = daifukucho.foo.bar, localhost.foo.bar, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
content_filter = smtp-amavis:[127.0.0.1]:10024
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps
smtpd_sender_login_maps = mysql:/etc/postfix/mysql_sender_login_maps
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_mailbox_domains
virtual_uid_maps = static:155
virtual_gid_maps = static:155
virtual_transport = virtual
fallback_transport = virtual
virtual_mailbox_base = /var/mail/vhosts
tanuki@daifukucho:~$ 
```
-
DOVECOT.CONF
```
## Dovecot configuration file

# If you're in a hurry, see http://wiki.dovecot.org/QuickConfiguration

# '#' character and everything after it is treated as comments. Extra spaces
# and tabs are ignored. If you want to use either of these explicitly, put the
# value inside quotes, eg.: key = "# char and trailing whitespace  "

# Default values are shown after each value, it's not required to uncomment
# any of the lines. Exception to this are paths, they're just examples
# with real defaults being based on configure options. The paths listed here
# are for configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
# --with-ssldir=/etc/ssl

# Base directory where to store runtime data.
#base_dir = /var/run/dovecot/

# Protocols we want to be serving: imap imaps pop3 pop3s
#protocols = imap imaps
protocols = pop3s

# IP or host address where to listen in for connections. It's not currently
# possible to specify multiple addresses. "*" listens in all IPv4 interfaces.
# "[::]" listens in all IPv6 interfaces, but may also listen in all IPv4
# interfaces depending on the operating system.
#
# If you want to specify ports for each service, you will need to configure
# these settings inside the protocol imap/pop3 { ... } section, so you can
# specify different ports for IMAP/POP3. For example:
#   protocol imap {
#     listen = *:10143
#     ssl_listen = *:10943
#     ..
#   }
#   protocol pop3 {
#     listen = *:10100
#     ..
#   }
#listen = *

# Disable LOGIN command and all other plaintext authentications unless
# SSL/TLS is used (LOGINDISABLED capability). Note that if the remote IP
# matches the local IP (ie. you're connecting from the same computer), the
# connection is considered secure and plaintext authentication is allowed.
#disable_plaintext_auth = yes

# Should all IMAP and POP3 processes be killed when Dovecot master process
# shuts down. Setting this to "no" means that Dovecot can be upgraded without
# forcing existing client connections to close (although that could also be
# a problem if the upgrade is eg. because of a security fix). This however
# means that after master process has died, the client processes can't write
# to log files anymore.
#shutdown_clients = yes

##
## Logging
##

# Use this logfile instead of syslog(). /dev/stderr can be used if you want to
# use stderr for logging (ONLY /dev/stderr - otherwise it is closed).
#log_path = 

# For informational messages, use this logfile instead of the default
#info_log_path = 

# Prefix for each line written to log file. % codes are in strftime(3)
# format.
log_timestamp = "%Y-%m-%d %H:%M:%S "

# Syslog facility to use if you're logging to syslog. Usually if you don't
# want to use "mail", you'll use local0..local7. Also other standard
# facilities are supported.
#syslog_facility = mail

##
## SSL settings
##

# IP or host address where to listen in for SSL connections. Defaults
# to above if not specified.
#ssl_listen =

# Disable SSL/TLS support.
#ssl_disable = no

# PEM encoded X.509 SSL/TLS certificate and private key. They're opened before
# dropping root privileges, so keep the key file unreadable by anyone but
# root.
#ssl_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
#ssl_key_file = /etc/ssl/private/ssl-cert-snakeoil.key

# If key file is password protected, give the password here. Alternatively
# give it when starting dovecot with -p parameter.
#ssl_key_password =

# File containing trusted SSL certificate authorities. Usually not needed.
#ssl_ca_file = 

# Request client to send a certificate.
#ssl_verify_client_cert = no

# How often to regenerate the SSL parameters file. Generation is quite CPU
# intensive operation. The value is in hours, 0 disables regeneration
# entirely.
#ssl_parameters_regenerate = 168

# SSL ciphers to use
#ssl_cipher_list = ALL:!LOW

# Show protocol level SSL errors.
#verbose_ssl = no

##
## Login processes
##

# Directory where authentication process places authentication UNIX sockets
# which login needs to be able to connect to. The sockets are created when
# running as root, so you don't have to worry about permissions. Note that
# everything in this directory is deleted when Dovecot is started.
#login_dir = /var/run/dovecot/login

# chroot login process to the login_dir. Only reason not to do this is if you
# wish to run the whole Dovecot without roots.
# http://wiki.dovecot.org/Rootless
#login_chroot = yes

# User to use for the login process. Create a completely new user for this,
# and don't use it anywhere else. The user must also belong to a group where
# only it has access, it's used to control access for authentication process.
# Note that this user is NOT used to access mails.
# http://wiki.dovecot.org/UserIds
#login_user = dovecot

# Set max. process size in megabytes. If you don't use
# login_process_per_connection you might need to grow this.
#login_process_size = 32

# Should each login be processed in it's own process (yes), or should one
# login process be allowed to process multiple connections (no)? Yes is more
# secure, espcially with SSL/TLS enabled. No is faster since there's no need
# to create processes all the time.
#login_process_per_connection = yes

# Number of login processes to create. If login_process_per_connection is
# yes, this is the number of extra processes waiting for users to log in.
#login_processes_count = 3

# Maximum number of extra login processes to create. The extra process count
# usually stays at login_processes_count, but when multiple users start logging
# in at the same time more extra processes are created. To prevent fork-bombing
# we check only once in a second if new processes should be created - if all
# of them are used at the time, we double their amount until limit set by this
# setting is reached. This setting is used only if
# login_process_per_connection is yes.
#login_max_processes_count = 128

# Maximum number of connections allowed in login state. When this limit is
# reached, the oldest connections are dropped. If login_process_per_connection
# is no, this is a per-process value, so the absolute maximum number of users
# logging in actually login_processes_count * max_logging_users.
#login_max_logging_users = 256

# Greeting message for clients.
#login_greeting = Dovecot ready.

# Space-separated list of elements we want to log. The elements which have
# a non-empty variable value are joined together to form a comma-separated
# string.
#login_log_format_elements = user=<%u> method=%m rip=%r lip=%l %c

## Mailbox locations and namespaces
##
mail_location = maildir:/var/mail/vhosts/%d/%n
 pop3_uidl_format = %08Xu%08Xv

auth default {
mechanisms = plain

userdb static {
     args = uid=155 gid=155 home=/var/mail/vhosts/%d/%u
}

 passdb sql {
   args = /etc/dovecot/dovecot-sql.conf
}
}

# Default MAIL environment to use when it's not set. By leaving this empty

# Grant access to these extra groups for mail processes. Typical use would be
# to give "mail" group write access to /var/mail to be able to create dotlocks.
mail_extra_groups = mail

# Allow full filesystem access to clients. There's no access checks other than
# what the operating system does for the active UID/GID. It works with both
# maildir and mboxes, allowing you to prefix mailboxes names with eg. /path/
# or ~user/.
#mail_full_filesystem_access = no

##
## Mail processes
##

# Enable mail process debugging. This can help you figure out why Dovecot
# isn't finding your mails.
#mail_debug = no

# Log prefix for mail processes. See 
# /usr/share/doc/dovecot-common/variables.txt for list of possible variables 
#you can use.
#mail_log_prefix = "%Us(%u): "

# Use mmap() instead of read() to read mail files. read() seems to be a bit
# faster with my Linux/x86 and it's better with NFS, so that's the default.
# Note that OpenBSD 3.3 and older don't work right with mail_read_mmaped = yes.
#mail_read_mmaped = no

# Don't use mmap() at all. This is required if you store indexes to shared
# filesystems (NFS or clustered filesystem).
#mmap_disable = no

# Don't write() to mmaped files. This is required for some operating systems
# which use separate caches for them, such as OpenBSD.
#mmap_no_write = no

# Locking method for index files. Alternatives are fcntl, flock and dotlock.
# Dotlocking uses some tricks which may create more disk I/O than other locking
# methods. NOTE: If you use NFS, remember to change also mmap_disable setting!
#lock_method = fcntl

# Drop all privileges before exec()ing the mail process. This is mostly
# meant for debugging, otherwise you don't get core dumps. It could be a small
# security risk if you use single UID for multiple users, as the users could
# ptrace() each others processes then.
#mail_drop_priv_before_exec = no

# Show more verbose process titles (in ps). Currently shows user name and
# IP address. Useful for seeing who are actually using the IMAP processes
# (eg. shared mailboxes or if same uid is used for multiple accounts).
#verbose_proctitle = no

# Valid UID range for users, defaults to 500 and above. This is mostly
# to make sure that users can't log in as daemons or other system users.
# Note that denying root logins is hardcoded to dovecot binary and can't
# be done even if first_valid_uid is set to 0.
#first_valid_uid = 500
first_valid_uid = 150
last_valid_uid = 0

# Valid GID range for users, defaults to non-root/wheel. Users having
# non-valid GID as primary group ID aren't allowed to log in. If user
# belongs to supplementary groups with non-valid GIDs, those groups are
# not set.
#first_valid_gid = 1
#last_valid_gid = 0

# Maximum number of running mail processes. When this limit is reached,
# new users aren't allowed to log in.
#max_mail_processes = 1024

# Set max. process size in megabytes. Most of the memory goes to mmap()ing
# files, so it shouldn't harm much even if this limit is set pretty high.
#mail_process_size = 256

# Maximum allowed length for mail keyword name. It's only forced when trying
# to create new keywords.
#mail_max_keyword_length = 50

# Default umask to use for mail files and directories.
#umask = 0077

# ':' separated list of directories under which chrooting is allowed for mail
# processes (ie. /var/mail will allow chrooting to /var/mail/foo/bar too).
# This setting doesn't affect login_chroot or auth_chroot variables.
# WARNING: Never add directories here which local users can modify, that
# may lead to root exploit. Usually this should be done only if you don't
# allow shell access for users. See 
# /usr/share/doc/dovecot-common/configuration.txt for more information.
#valid_chroot_dirs = 

# Default chroot directory for mail processes. This can be overridden for
# specific users in user database by giving /./ in user's home directory
# (eg. /home/./user chroots into /home). Note that usually there is no real
# need to do chrooting, Dovecot doesn't allow users to access files outside
# their mail directory anyway.
#mail_chroot = 

##
## Mailbox handling optimizations
##

# Space-separated list of fields to initially save into cache file. Currently
# these fields are allowed:
#
#  flags, date.sent, date.received, size.virtual, size.physical
#  mime.parts, imap.body, imap.bodystructure
#
# Different IMAP clients work in different ways, so they benefit from
# different cached fields. Some do not benefit from them at all. Caching more
# than necessary generates useless disk I/O, so you don't want to do that
# either.
#
# Dovecot attempts to automatically figure out what client wants and it keeps
# only that. However the first few times a mailbox is opened, Dovecot hasn't
# yet figured out what client needs, so it may not perform optimally. If you
# know what fields the majority of your clients need, it may be useful to set
# these fields by hand. If client doesn't actually use them, Dovecot will
# eventually drop them.
#
# Usually you should just leave this field alone. The potential benefits are
# typically unnoticeable.
#mail_cache_fields = 

# Space-separated list of fields that Dovecot should never save to cache file.
# Useful if you want to save disk space at the cost of more I/O when the fields
# needed.
#mail_never_cache_fields = 

# The minimum number of mails in a mailbox before updates are done to cache
# file. This allows optimizing Dovecot's behavior to do less disk writes at
# the cost of more disk reads.
#mail_cache_min_mail_count = 0

# When IDLE command is running, mailbox is checked once in a while to see if
# there are any new mails or other changes. This setting defines the minimum
# time to wait between those checks. Dovecot is however able to use dnotify
# and inotify with Linux to reply immediately after the change occurs.
#mailbox_idle_check_interval = 30

# Save mails with CR+LF instead of plain LF. This makes sending those mails
# take less CPU, especially with sendfile() syscall with Linux and FreeBSD.
# But it also creates a bit more disk I/O which may just make it slower.
# Also note that if other software reads the mboxes/maildirs, they may handle
# the extra CRs wrong and cause problems.
#mail_save_crlf = no

##
## Maildir-specific settings
##

# By default LIST command returns all entries in maildir beginning with dot.
# Enabling this option makes Dovecot return only entries which are directories.
# This is done by stat()ing each entry, so it causes more disk I/O.
# (For systems setting struct dirent->d_type, this check is free and it's
# done always regardless of this setting)
#maildir_stat_dirs = no

# Copy mail to another folders using hard links. This is much faster than
# actually copying the file. This is problematic only if something modifies
# the mail in one folder but doesn't want it modified in the others. I don't
# know any MUA which would modify mail files directly. IMAP protocol also
# requires that the mails don't change, so it would be problematic in any case.
# If you care about performance, enable it.
#maildir_copy_with_hardlinks = no

##
## mbox-specific settings
##

# Which locking methods to use for locking mbox. There are four available:
#  dotlock: Create <mailbox>.lock file. This is the oldest and most NFS-safe
#           solution. If you want to use /var/mail/ like directory, the users
#           will need write access to that directory.
#  fcntl  : Use this if possible. Works with NFS too if lockd is used.
#  flock  : May not exist in all systems. Doesn't work with NFS.
#  lockf  : May not exist in all systems. Doesn't work with NFS.
#
# You can use multiple locking methods; if you do the order they're declared
# in is important to avoid deadlocks if other MTAs/MUAs are using multiple
# locking methods as well. Some operating systems don't allow using some of
# them simultaneously.
#mbox_read_locks = fcntl
#mbox_write_locks = dotlock fcntl

# Maximum time in seconds to wait for lock (all of them) before aborting.
#mbox_lock_timeout = 300

# If dotlock exists but the mailbox isn't modified in any way, override the
# lock file after this many seconds.
#mbox_dotlock_change_timeout = 120

# When mbox changes unexpectedly we have to fully read it to find out what
# changed. If the mbox is large this can take a long time. Since the change
# is usually just a newly appended mail, it'd be faster to simply read the
# new mails. If this setting is enabled, Dovecot does this but still safely
# fallbacks to re-reading the whole mbox file whenever something in mbox isn't
# how it's expected to be. The only real downside to this setting is that if
# some other MUA changes message flags, Dovecot doesn't notice it immediately.
# Note that a full sync is done with SELECT, EXAMINE, EXPUNGE and CHECK 
# commands.
#mbox_dirty_syncs = yes

# Like mbox_dirty_syncs, but don't do full syncs even with SELECT, EXAMINE,
# EXPUNGE or CHECK commands. If this is set, mbox_dirty_syncs is ignored.
#mbox_very_dirty_syncs = no

# Delay writing mbox headers until doing a full write sync (EXPUNGE and CHECK
# commands and when closing the mailbox). This is especially useful for POP3
# where clients often delete all mails. The downside is that our changes
# aren't immediately visible to other MUAs.
#mbox_lazy_writes = yes

# If mbox size is smaller than this (in kilobytes), don't write index files.
# If an index file already exists it's still read, just not updated.
#mbox_min_index_size = 0

##
## dbox-specific settings
##

# Maximum dbox file size in kilobytes until it's rotated.
#dbox_rotate_size = 2048

# Minimum dbox file size in kilobytes before it's rotated
# (overrides dbox_rotate_days)
#dbox_rotate_min_size = 16

# Maximum dbox file age in days until it's rotated. Day always begins from
# midnight, so 1 = today, 2 = yesterday, etc. 0 = check disabled.
#dbox_rotate_days = 0

##
## IMAP specific settings
##

protocol imap {
  # Login executable location.
  #login_executable = /usr/lib/dovecot/imap-login

  # IMAP executable location. Changing this allows you to execute other
  # binaries before the imap process is executed.
  #
  # This would write rawlogs into ~/dovecot.rawlog/ directory:
  #   mail_executable = /usr/lib/dovecot/rawlog /usr/lib/dovecot/imap
  #
  # This would attach gdb into the imap process and write backtraces into
  # /tmp/gdbhelper.* files:
  #   mail_executable = /usr/lib/dovecot/gdbhelper /usr/lib/dovecot/imap
  #
  #mail_executable = /usr/lib/dovecot/imap

  # Maximum IMAP command line length in bytes. Some clients generate very long
  # command lines with huge mailboxes, so you may need to raise this if you get
  # "Too long argument" or "IMAP command line too large" errors often.
  #imap_max_line_length = 65536

  # Support for dynamically loadable plugins. mail_plugins is a space separated
  # list of plugins to load.
  #mail_plugins = 
  #mail_plugin_dir = /usr/lib/dovecot/modules/imap

  # Send IMAP capabilities in greeting message. This makes it unnecessary for
  # clients to request it with CAPABILITY command, so it saves one round-trip.
    #
    #args =
  #}

  # SQL database
  #userdb sql {
    # Path for SQL configuration file, see /etc/dovecot/dovecot-sql.conf for 
    # example
    #args = 
  #}

  # LDAP database
  #userdb ldap {
    # Path for LDAP configuration file, see /etc/dovecot/dovecot-ldap.conf for 
    # example
    #args = 
  #}

  # vpopmail
  #userdb vpopmail {
  #}

  # "prefetch" user database means that the passdb already provided the
  # needed information and there's no need to do a separate userdb lookup.
  # This can be made to work with SQL and LDAP databases, see their example
  # configuration files for more information how to do it.
  # http://wiki.dovecot.org/AuthSpecials
  #userdb prefetch {
  #}

  # User to use for the process. This user needs access to only user and
  # password databases, nothing else. Only shadow and pam authentication
  # requires roots, so use something else if possible. Note that passwd
  # authentication with BSDs internally accesses shadow files, which also
  # requires roots. Note that this user is NOT used to access mails.
  # That user is specified by userdb above.
  user = root

  # Directory where to chroot the process. Most authentication backends don't
  # work if this is set, and there's no point chrooting if auth_user is root.
  # Note that valid_chroot_dirs isn't needed to use this setting.
  #chroot = 

  # Number of authentication processes to create
  #count = 1

  # Require a valid SSL client certificate or the authentication fails.
  #ssl_require_client_cert = no

  # Take the username from client's SSL certificate, using X509_NAME_oneline()
  # which typically uses subject's Distinguished Name.
  #ssl_username_from_cert = no

  # It's possible to export the authentication interface to other programs:
  #socket listen {
    #master {
      # Master socket is typically used to give Dovecot's local delivery
      # agent access to userdb so it can find mailbox locations. It can
      # however also be used to disturb regular user authentications.
      # WARNING: Giving untrusted users access to master socket may be a 
      # security risk, don't give too wide permissions to it!
      #path = /var/run/dovecot/auth-master
      #mode = 0600
      # Default user/group is the one who started dovecot-auth (root)
      #user = 
      #group = 
    #}
    #client {
      # The client socket is generally safe to export to everyone. Typical use
      # is to export it to your SMTP server so it can do SMTP AUTH lookups
      # using it.
      #path = /var/run/dovecot/auth-client
      #mode = 0660
    #}
  #}
}

# If you wish to use another authentication server than dovecot-auth, you can
# use connect sockets. They assumed to be already running, Dovecot's master
# process only tries to connect to them. They don't need any other settings
# than the path for the master socket, as the configuration is done elsewhere.
# Note that the client sockets must exist in the login_dir.
#auth external {
#  socket connect {
#    master {
#      path = /var/run/dovecot/auth-master
#    }
#  }
#}

##
## Dictionary server settings
##

# Dictionary can be used by some plugins to store key=value lists.
# Currently this is only used by dict quota backend. The dictionary can be
# used either directly or though a dictionary server. The following dict block
# maps dictionary names to URIs when the server is used. These can then be
# referenced using URIs in format "proxy:<name>".

dict {
  #quota = mysql:/etc/dovecot-dict-quota.conf 
}

##
## Plugin settings
##

plugin {
  # Here you can give some extra environment variables to mail processes.
  # This is mostly meant for passing parameters to plugins. %variable
  # expansion is done for all values.

  # Quota plugin. Multiple backends are supported:
  #   dirsize: Find and sum all the files found from mail directory
  #   dict: Keep quota stored in dictionary (eg. SQL)
  #   maildir: Maildir++ quota
  #   fs: Read-only support for filesystem quota
  #quota = maildir

  # ACL plugin. vfile backend reads ACLs from "dovecot-acl" file from maildir
  # directory. You can also optionally give a global ACL directory path where
  # ACLs are applied to all users' mailboxes. The global ACL directory contains
  # one file for each mailbox, eg. INBOX or sub.mailbox.
  #acl = vfile:/etc/dovecot-acls

  # Convert plugin. If set, specifies the source storage path which is
  # converted to destination storage (default_mail_env).
  #convert_mail = mbox:%h/mail

  # Trash plugin. When saving a message would make user go over quota, this
  # plugin automatically deletes the oldest mails from configured mailboxes
  # until the message can be saved within quota limits. The configuration file
  # is a text file where each line is in format: <priority> <mailbox name>
  # Mails are first deleted in lowest -> highest priority number order
  #trash = /etc/dovecot-trash.conf
}
```

---

### Post by darrenm on 2007-05-24
> **VorDesigns said:**
> I dunno, would you run Feisty on a P/II 450 with 384MB of RAM?

To your submission requestions:  I'm still walking through the document to see what I did wrong.
----------------


Fiesty wont be any different to Edgy with regard to system resources. But yeah I would run Feisty on that spec, ideally without X though.

I tried the whole thing again and your problem seems to be the comments left in the mysql_virtual_mailbox_domains

---

### Post by glentech on 2007-05-24
> glentech: just a small suggestion, please ls your /var/run/mysqld/? running "mysql -uroot -p" or "mysql -uroot", did you get into mysql? did you try "socket: /var/run/mysqld/mysqld.sock" & "host: localhost" in ~/rubyapps/vmail/config/database.yml.  Good luck.
I can get into mysql just fine, I have the "mysql.sock" and "host: localhost" the way described.

> Yup. And if you can get into MySQL ok and ls /var/run/mysqld/ is ok then you may need to drop the whole database and create it again before raking.
I tried dropping the database and creating it again.

Here's the trace, maybe this will give a clue what I'm doing wrong, or have wrong.
> chester@ubuntusvr:~/rubyapps/vmail$ rake db:migrate --trace
(in /home/chester/rubyapps/vmail)
** Invoke db:migrate (first_time)
** Invoke environment (first_time)
** Execute environment
** Execute db:migrate
** Invoke db:schema:dump (first_time)
** Invoke environment
** Execute db:schema:dump
rake aborted!
Mysql::Error: Lost connection to MySQL server during query: SHOW TABLES
/home/chester/rubyapps/vmail/config/../vendor/rails/activerecord/lib/active_record/connection_adapters/abstract_adapter.rb:120:in `log'
/home/chester/rubyapps/vmail/config/../vendor/rails/activerecord/lib/active_record/connection_adapters/mysql_adapter.rb:185:in `execute'
/home/chester/rubyapps/vmail/config/../vendor/rails/activerecord/lib/active_record/connection_adapters/mysql_adapter.rb:271:in `tables'
/home/chester/rubyapps/vmail/config/../vendor/rails/activerecord/lib/active_record/schema_dumper.rb:51:in `tables'
/home/chester/rubyapps/vmail/config/../vendor/rails/activerecord/lib/active_record/schema_dumper.rb:20:in `dump'
/home/chester/rubyapps/vmail/config/../vendor/rails/activerecord/lib/active_record/schema_dumper.rb:14:in `dump'
/home/chester/rubyapps/vmail/config/../vendor/rails/railties/lib/tasks/databases.rake:24
/home/chester/rubyapps/vmail/config/../vendor/rails/railties/lib/tasks/databases.rake:23
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:392:in `execute'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:392:in `execute'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:362:in `invoke'
/usr/lib/ruby/1.8/thread.rb:135:in `synchronize'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:355:in `invoke'
/home/chester/rubyapps/vmail/config/../vendor/rails/railties/lib/tasks/databases.rake:5
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:392:in `execute'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:392:in `execute'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:362:in `invoke'
/usr/lib/ruby/1.8/thread.rb:135:in `synchronize'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:355:in `invoke'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:1739:in `top_level'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:1739:in `top_level'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:1761:in `standard_exception_handling'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:1733:in `top_level'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:1711:in `run'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:1761:in `standard_exception_handling'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/lib/rake.rb:1708:in `run'
/usr/lib/ruby/gems/1.8/gems/rake-0.7.3/bin/rake:7
/usr/bin/rake:18
chester@ubuntusvr:~/rubyapps/vmail$


FYI, I'm running Dapper here.
FWIW, I've tried several methods to get this all up and running, getting sort of frustrated with it. I'm committed to Linux on this, but would like something that works. This post looked like the one I liked the best, so I thought I'd try it. I'll keep trying.
(I don't know how to condense the quotes so it has the scroll bars) :(

---

### Post by VorDesigns on 2007-05-24
> **darrenm said:**
> I tried the whole thing again and your problem seems to be the comments left in the mysql_virtual_mailbox_domains

Well there are two problems:
1) Dovecot won't start; I'm reluctant to just comment out the mail_location setting unless I pull the whole entry.  Since you said the Edgy release shouldn't need it, I'll try that.

2) It isn't clear whether the issue is authentication or query result unhappyness.  
I've entered the domain > foo.bar should it be > foo.bar. ?
For the test user I used > tanuke@foo.bar.
For the aliases I used > amavis@foo.bar, > root, > root@foo.bar, > security@foo.bar.  
Is my syntax correct?

---

### Post by VorDesigns on 2007-05-25
Here's a question for you:

the mail location in the document is /var/mail/vhosts

my system has a /var/mail directory but no vhosts directory.

Could this be why Dovecot is bombin since the directory where domain.tld/user directories are supposed to be created doesn't exist?

Never mind, add the vhosts directory and 

```
Starting mail server: dovecotError: Error in configuration file /etc/dovecot/dovecot.conf line 174: Unknown setting: mail_location
```

Alias table output:
mysql> select * from aliases order by address;
[FONT="Courier New"]
[SIZE="2"]+----+-------------------------------+-------------------------------+
| id | address                       | goto                          |
+----+-------------------------------+-------------------------------+
|  4 | amavis                        | [email]tanuki@sorsh.foo.bar[/email]        |
|  7 | [email]amavis@daifukucho.foo.bar[/email]     | [email]tanuki@sorsh.foo.bar[/email]        |
|  6 | root                          | [email]tanuki@sorsh.foo.bar[/email]        |
|  5 | [email]root@sorsh.foo.bar[/email]            | [email]tanuki@sorsh.foo.bar[/email]        |
|  3 | [email]security@sorsh.foo.bar[/email]        | [email]tanuki@sorsh.foo.bar[/email]        |
|  2 | [email]support@sorsh.foo.bar[/email]         | [email]tanuki@sorsh.foo.bar[/email]        |
+----+-------------------------------+-------------------------------+
[/SIZE]6 rows in set (0.00 sec)[/FONT]
Don't have the patience to line it all up.

---

### Post by darrenm on 2007-05-25
> **VorDesigns said:**
> Here's a question for you:

the mail location in the document is /var/mail/vhosts

my system has a /var/mail directory but no vhosts directory.

Could this be why Dovecot is bombin since the directory where domain.tld/user directories are supposed to be created doesn't exist?

Never mind, add the vhosts directory and 

```
Starting mail server: dovecotError: Error in configuration file /etc/dovecot/dovecot.conf line 174: Unknown setting: mail_location
```

Alias table output:
mysql> select * from aliases order by address;
[FONT="Courier New"]
[SIZE="2"]+----+-------------------------------+-------------------------------+
| id | address                       | goto                          |
+----+-------------------------------+-------------------------------+
|  4 | amavis                        | [email]tanuki@sorsh.foo.bar[/email]        |
|  7 | [email]amavis@daifukucho.foo.bar[/email]     | [email]tanuki@sorsh.foo.bar[/email]        |
|  6 | root                          | [email]tanuki@sorsh.foo.bar[/email]        |
|  5 | [email]root@sorsh.foo.bar[/email]            | [email]tanuki@sorsh.foo.bar[/email]        |
|  3 | [email]security@sorsh.foo.bar[/email]        | [email]tanuki@sorsh.foo.bar[/email]        |
|  2 | [email]support@sorsh.foo.bar[/email]         | [email]tanuki@sorsh.foo.bar[/email]        |
+----+-------------------------------+-------------------------------+
[/SIZE]6 rows in set (0.00 sec)[/FONT]
Don't have the patience to line it all up.

Did you read popot's post above ^ about Edgy's dovecot not having the mail_location setting?

I'll be updating the first posts in the thread so its a bit easier to read.

---

### Post by popot on 2007-05-25
**glentech**: Its a bit confusing. So you have mysql.sock in /var/run/mysqld/? If not, can you list /var/run/mysqld/.

Woah, you running on dapper, I'm not keeping amavis and clamav up to date in edgy eft. Is it up to date with dapper? If it is, is it long term thing.

---

### Post by glentech on 2007-05-25
> **popot said:**
> **glentech**: Its a bit confusing. So you have mysql.sock in /var/run/mysqld/? If not, can you list /var/run/mysqld/.

> chester@ubuntusvr:/var/run/mysqld$ ls
mysqld.pid  mysqld.sock
chester@ubuntusvr:/var/run/mysqld$


Woah, you running on dapper, I'm not keeping amavis and clamav up to date in edgy eft. Is it up to date with dapper? If it is, is it long term thing.

Hope this helps.

---

### Post by VorDesigns on 2007-05-25
Hiya, downloaded Feisty, THE ONE THAT YELLS EVERYTHING AT YOU, last night.

Burned the iso and installed a base LAMP.

Will configure and let you know if it bombs.  Gonna save the dovecot configuration for last.

I can yank all my post if you want to unclutter the thread.

I will drop you my notes when I'm done or, when I give up and try something else.  Ruby is cool but I don't have time to learn how to make the interface more usable for day to day management of a mail server.

Still this is a good post and I want to help you with it.  I like Postfix.

---

### Post by popot on 2007-05-25
Not trying to be pedantic about it, but god is in the details.

> **glentech said:**
> Hope this helps.

> **glentech said:**
> I can get into mysql just fine, I have the "mysql.sock" and "host: localhost" the way described.


I tried dropping the database and creating it again.

Here's the trace, maybe this will give a clue what I'm doing wrong, or have wrong.


FYI, I'm running Dapper here.
FWIW, I've tried several methods to get this all up and running, getting sort of frustrated with it. I'm committed to Linux on this, but would like something that works. This post looked like the one I liked the best, so I thought I'd try it. I'll keep trying.
(I don't know how to condense the quotes so it has the scroll bars) :(

ls
mysqld.pid mysqld.sock

I can get into mysql just fine, I have the "mysql.sock" and "host: localhost" the way described.

Please double check "socket: /var/run/mysqld/mysqld.sock" & "host: localhost" in ~/rubyapps/vmail/config/database.yml. And restart please.

---

### Post by glentech on 2007-05-25
> **popot said:**
> 
Please double check "socket: /var/run/mysqld/mysqld.sock" & "host: localhost" in ~/rubyapps/vmail/config/database.yml. And restart please.

It is exactly that way. I restarted the whole computer, still same thing. I have a book on Ruby, I'm trying to learn just what rake does, etc. maybe I can figure it out.
I appreciate the suggestions, I'll keep working on it.

---

### Post by darrenm on 2007-05-26
> **glentech said:**
> It is exactly that way. I restarted the whole computer, still same thing. I have a book on Ruby, I'm trying to learn just what rake does, etc. maybe I can figure it out.
I appreciate the suggestions, I'll keep working on it.

Its perhaps more of a problem with Rails then. Can you try updating rails? ```
sudo gem update rails
``` You will then need to create the ruby app again.

---

### Post by darrenm on 2007-05-26
> **VorDesigns said:**
> Hiya, downloaded Feisty, THE ONE THAT YELLS EVERYTHING AT YOU, last night.

In what way does it yell at you? :)

> **VorDesigns said:**
> Burned the iso and installed a base LAMP.

Will configure and let you know if it bombs.  Gonna save the dovecot configuration for last.

If you still can't get it working in Feisty then I can just post my dovecot.conf as there is nothing specific to each set up in there.

> **VorDesigns said:**
> I can yank all my post if you want to unclutter the thread.

Nah don't worry it makes the thread look popular ;)

> **VorDesigns said:**
> I will drop you my notes when I'm done or, when I give up and try something else.  Ruby is cool but I don't have time to learn how to make the interface more usable for day to day management of a mail server.

Still this is a good post and I want to help you with it.  I like Postfix.

I can post a Django app with a startup script if you like?

---

### Post by VorDesigns on 2007-05-26
Hiya, 

> In what way does it yell at you? 
Feisty, WHY  DO YOU SCREAM AT ME?  LET ME COUNT THE WAYS:
It would seem that the boot process is a little off; the login prompt shows up before the boot process had really finished and if you don't hit the enter key in a reasonable amount of time after the last load process is run, when you do decide to login, EVERYTHING IS CAPITALIZED UNLESS YOU ARE IN AN APPLICATION.  THIS DOESN'T SEEM TO BE A PROBLEM WITH RESPECT TO LOCATING DIRECTORIES AND FILES BUT, IT SURE IS IRRITATING.
Based monitoring the boot process, it seems that amvavis through postfix (so far) are started after the login prompt.


> If you still can't get it working in Feisty then I can just post my dovecot.conf as there is nothing specific to each set up in there.
I'm guessing I boobed on the location of the mail_location but, this time I'm gonna have a back up.

> I can post a Django app with a startup script if you like?
Django?

---

### Post by darrenm on 2007-05-27
> **VorDesigns said:**
> Hiya, 


Feisty, WHY  DO YOU SCREAM AT ME?  LET ME COUNT THE WAYS:
It would seem that the boot process is a little off; the login prompt shows up before the boot process had really finished and if you don't hit the enter key in a reasonable amount of time after the last load process is run, when you do decide to login, EVERYTHING IS CAPITALIZED UNLESS YOU ARE IN AN APPLICATION.  THIS DOESN'T SEEM TO BE A PROBLEM WITH RESPECT TO LOCATING DIRECTORIES AND FILES BUT, IT SURE IS IRRITATING.
Based monitoring the boot process, it seems that amvavis through postfix (so far) are started after the login prompt.

The login prompt showing up before all the services have finished loading is completely correct, but it shouldnt cause any weird issues like that. I've not seen that problem myself, it sure does sound strange.

> **VorDesigns said:**
> 
I'm guessing I boobed on the location of the mail_location but, this time I'm gonna have a back up.


Django?

Like Ruby on Rails but uses Python instead of Ruby. Its what Im doing the web front end for UGS in now. [www.djangoproject.com](www.djangoproject.com)

---

### Post by VorDesigns on 2007-06-01
Hiya,
OK, looks like I'm through with your document but, I'm on to testing the mail server and client connections before I color it done.
So far Postfix doesn't look right yet but I've got some DNS tinkering to do and a couple other items to tweak so that legitimate mail goes where it needs to.
A few questions:
1. On the User configuration
 a) [email]user@domain.tld[/email] is correct based on your document
 b) it is rather humorous that the password is dotted out on input and clear as day on list.
 c) I am not clear on the directory syntax should it be domain.tls/user/ or domain/tld/user/ or domain.tld/user or domain/tld/user or...?
2. On aliases, each alias needs three entries?  

Secondary novelties, can aliases be used to forward mail to other domains?

That's it for now.  Haven't beat up on Postfix yet and I've never had to deal with spop.

All in all good article, I didn't need the ERRATA post feisty but I ran the configuration items anyway to make sure things were installed.

You might want to change the sudo comments to just run interactive sesions  using sudo -i .  Also, nano would be the editor of choice for a GUI free experience.

---

### Post by darrenm on 2007-06-01
> **VorDesigns said:**
> Hiya,
OK, looks like I'm through with your document but, I'm on to testing the mail server and client connections before I color it done.
So far Postfix doesn't look right yet but I've got some DNS tinkering to do and a couple other items to tweak so that legitimate mail goes where it needs to.
A few questions:
1. On the User configuration
 a) [email]user@domain.tld[/email] is correct based on your document
Yes.
 > **VorDesigns said:**
> b) it is rather humorous that the password is dotted out on input and clear as day on list.
Yes it is. Its due to the Rails app being as basic as it can get. Soon I'll have my front end written so things like this will not happen on the final UGS product.
 > **VorDesigns said:**
> c) I am not clear on the directory syntax should it be domain.tls/user/ or domain/tld/user/ or domain.tld/user or domain/tld/user or...?
It should be domain.tld/user/ Again once I have the front end written this won't be needed as it will automatically be taken care of.
> **VorDesigns said:**
> 2. On aliases, each alias needs three entries?  
You don't really need any aliases. But it is prudent to have at least root mail going to one user and the local username of any local users pointing to the full email of each user. e.g. if the system itself needs to send mail to darrenm then postfix will do a MySQL lookup and find that the only entry is [email]darrenm@cghm.net[/email] and will bounce the mail. So if you have an alias for darrenm going to [email]darrenm@cghm.net[/email] the mail will get delivered correctly. Make sense?

> **VorDesigns said:**
> Secondary novelties, can aliases be used to forward mail to other domains? 

Yes no problems at all. 

> **VorDesigns said:**
> That's it for now.  Haven't beat up on Postfix yet and I've never had to deal with spop.

All in all good article, I didn't need the ERRATA post feisty but I ran the configuration items anyway to make sure things were installed.

You might want to change the sudo comments to just run interactive sesions  using sudo -i .  Also, nano would be the editor of choice for a GUI free experience.

Fair enough. Its due a re-write soon anyway. Ta.

---

### Post by VorDesigns on 2007-06-01
Err, looks like I have a user security issue.
I asked earlier but don't remember seeing an answer about there not being a vmail directory.
Postfix says
```
Jun  1 12:20:01 daifukucho postfix/virtual[5231]: warning: maildir access problem for UID/GID=155/155: create maildir file /var/mail/vhosts/domain.tld/test/tmp/1180725601.P5231.daifukucho: Permission denied
Jun  1 12:20:01 daifukucho postfix/virtual[5231]: warning: perhaps you need to create the maildirs in advance
Jun  1 12:20:01 daifukucho postfix/virtual[5231]: 510F2614CB8: to=<test@domain.tld>, relay=virtual, delay=0.28, delays=0.08/0.11/0/0.09, dsn=4.2.0, status=deferred (maildir delivery failed: create maildir file /var/mail/vhosts/domain.tld/test/tmp/1180725601.P5231.daifukucho: Permission denied)
```

---

### Post by darrenm on 2007-06-03
Yep I answered it a few posts ago. Its also in the corrections post. You need to chown the vhosts directory:

```
sudo mkdir /var/mail/vhosts
sudo chown -R vmail:vmail /var/mail/vhosts
```

---

### Post by VorDesigns on 2007-06-03
Yessir, didn't see it in this post but found in another:

[http://flurdy.com/docs/postfix/#install_proc]("http://flurdy.com/docs/postfix/#install_proc")

Will I also need to do the Amavis steps for the amavis temp directory?

---

### Post by VorDesigns on 2007-06-04
Moving right along, I've been going over my dovecot installation but haven't figured out why I can't get mail:
I setup Evolution Mail to pick up mail I have sent to my test account.
Results are:
```
 08:13:02 daifukucho dovecot: auth-worker(default): mysql: Connected to 127.0.0.1 (vmail_vdl)
Jun  4 08:13:02 daifukucho dovecot: Logins with UID 155 (user test@domain.tld) not permitted (see first_vali
d_uid in config file)
Jun  4 08:13:02 daifukucho dovecot: pop3-login: Internal login failure: user=<test@domain.tld>, method=PLAIN
, rip=172.31.16.25, lip=192.168.254.240, TLS
Jun  4 08:20:09 daifukucho dovecot: pop3-login: Aborted login: rip=172.31.16.25, lip=192.168.254.240, TLS
```
I can see that the UID 155 is the one that we set up but there isn't a first valid reference in your document

dovecot conf:
```
# Valid UID range for users, defaults to 500 and above. This is mostly
# to make sure that users can't log in as daemons or other system users.
# Note that denying root logins is hardcoded to dovecot binary and can't
# be done even if first_valid_uid is set to 0.
#first_valid_uid = 500
#last_valid_uid = 0
```

Can't send mail either but it looks like I'll be hunting elsewhere for authenticated smtp methodologies unless that was planned for this post.

Since I know fa about dovecot, I figured I would ask; should I set first valid uid to 155?

---

### Post by VorDesigns on 2007-06-04
Adding the first valide UID 155 did change things but it didn't get me where I need to be.  Also, can't send mail but my grogginess thinkgs I said that already:
```
 08:42:24 daifukucho dovecot: Dovecot v1.0.rc17 starting up
Jun  4 08:42:25 daifukucho dovecot: auth-worker(default): mysql: Connected to 127.0.0.1 (vmail_vdl)
Jun  4 08:42:49 daifukucho dovecot: pop3-login: Aborted login: rip=172.31.16.25, lip=192.168.254.240, TLS
Jun  4 08:43:45 daifukucho dovecot: pop3-login: Aborted login: rip=172.31.16.25, lip=192.168.254.240, TLS
Jun  4 08:44:46 daifukucho postfix/smtpd[7804]: connect from unknown[172.31.16.25]
Jun  4 08:44:46 daifukucho postfix/smtpd[7804]: disconnect from unknown[172.31.16.25]
Jun  4 08:45:00 daifukucho postfix/smtpd[7804]: connect from unknown[172.31.16.25]
Jun  4 08:45:00 daifukucho postfix/smtpd[7804]: disconnect from unknown[172.31.16.25]
Jun  4 08:46:36 daifukucho postfix/smtpd[7804]: connect from unknown[172.31.16.25]
Jun  4 08:46:36 daifukucho postfix/smtpd[7804]: NOQUEUE: reject: RCPT from unknown[172.31.16.25]: 554 5.7.1 <support@domain2.
tld>: Relay access denied; from=<test@domain.tld> to=<support@vordesigns.com> proto=ESMTP helo=<[172.31.16.25]>
Jun  4 08:46:36 daifukucho postfix/smtpd[7804]: disconnect from unknown[172.31.16.25]
Jun  4 08:49:56 daifukucho postfix/anvil[7807]: statistics: max connection rate 2/60s for (smtp:172.31.16.25) at Jun  4 08:4
5:00
Jun  4 08:49:56 daifukucho postfix/anvil[7807]: statistics: max connection count 1 for (smtp:172.31.16.25) at Jun  4 08:44:4
6
Jun  4 08:49:56 daifukucho postfix/anvil[7807]: statistics: max cache size 1 at Jun  4 08:44:46
root@daifukucho:~#
```
I not a mention of TLS but changing to TLS in the connection methods equates to no response from the server on the client side and silence in the tail of the mail.log.

---

### Post by VorDesigns on 2007-06-07
While I hate the word miraculously, that is what happened with respect to getting mail using Evolution Mail to test the server; it didn't work and then miraculously, when I loaded EM today to troubleshoot more, Send/Receive miraculously receives mail.
So, my last problem is figuring out how to tell the mail server at domain1.tld that the user login at domain2.tld is allowed to send mail to someone else at domainother.tld

```
Jun  7 13:51:12 daifukucho postfix/smtpd[10686]: connect from unknown[172.31.16.25]
Jun  7 13:51:12 daifukucho postfix/smtpd[10686]: NOQUEUE: reject: RCPT from unknown[172.31.16.25]: 554 5.7.1 <support@domain3.tld>: Relay access denied; from=<test@domain2.tld> to=<support@domain3.tld> proto=ESMTP helo=<[172.31.16.25]>
Jun  7 13:51:12 daifukucho postfix/smtpd[10686]: disconnect from unknown[172.31.16.25]
Jun  7 13:52:14 daifukucho dovecot: auth-worker(default): mysql: Connected to 127.0.0.1 (vmail_vdl)
Jun  7 13:52:14 daifukucho dovecot: pop3-login: Login: user=<test@domain2.tld>, method=PLAIN, rip=172.31.16.25, lip=192.168.254.240, TLS
Jun  7 13:52:15 daifukucho dovecot: POP3(test@domain2.tld): Disconnected: Logged out top=0/0, retr=5/35778, del=5/5, size=35691
Jun  7 13:54:32 daifukucho postfix/anvil[10689]: statistics: max connection rate 1/60s for (smtp:172.31.16.25) at Jun  7 13:51:12
Jun  7 13:54:32 daifukucho postfix/anvil[10689]: statistics: max connection count 1 for (smtp:172.31.16.25) at Jun  7 13:51:12
Jun  7 13:54:32 daifukucho postfix/anvil[10689]: statistics: max cache size 1 at Jun  7 13:51:12
```

Yes, I am working with three fqdn, the host mail server is domain1, not seen but located at 192.168.254.240, the mail server.  The smtp/pop3s is not only using a different virtually hosted domain2 but a differen private network as well.  Domain3 is also mine.

Suggestions?

---

### Post by darrenm on 2007-06-08
Hello, sorry I've been on hols for the past week.

I'll have a good look a bit later, bit short on time right now.

While I've been away I've written a simple mail web front end in PHP if anyone wants it?

edit: In the meantime can you post your /etc/postfix/main.cf removing any personal data if you see fit? a mysql dump would also be really nice but don't worry too much if you dont know how to do it or remove the passwords etc.

---

### Post by VorDesigns on 2007-06-08
Heres' what I have, it's pretty basic:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

# POSTMASTER FUNCTIONS
notify_classes = bounce,delay,resource,software, protocol
luser_relay =
always_bcc =

# SECURITY PRECAUTION
disable_vrfy_command = yes
smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = daifukucho.domain1.tld
alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps
alias_database = mysql:/etc/postfix/mysql_virtual_alias_maps
myorigin = /etc/mailname
mydestination = daifukucho.domain1.tld, localhost.domain1.tld, localhost
relayhost =

# UCE RESTRICTIONS
mynetworks = 127.0.0.0/8
smtpd_helo_required = yes
strict_rfc821_envelopes = yes
allow_untrusted_routing = no

mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

#
# Amavis
#
content_filter = smtp-amavis:[127.0.0.1]:10024
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps
smtpd_sender_login_maps = mysql:/etc/postfix/mysql_sender_login_maps
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_mailbox_domains
virtual_uid_maps = static:155
virtual_gid_maps = static:155
virtual_transport = virtual
fallback_transport = virtual
virtual_mailbox_base = /var/mail/vhosts

```

If you clarify SQL dump I can provide information for you.

---

### Post by darrenm on 2007-06-09
Try 

```
sudo postconf -e "mydestination ="
```

and just make sure you have the domains you want to accept mail from in the domains table and the full email address of each user you want to accept mail for in the users table.

edit: You have to restart Postfix after running this command of course.

---

### Post by VorDesigns on 2007-06-09
That didn't work; I need a methodology to authenticate and authorize the sender from wherever they connect from.  I have dracd running on my other server but it was a canned installation.
It looks like the rest is working fine. 
I will have to do some digging to figure out an smtp-auth mechanism here.
Thanks!

---

### Post by VorDesigns on 2007-06-10
OK, I've figured out what I want to do; I need to authenticate the smtp user from where ever they connect.  Once I determine what steps are necessary either to use the existing database tables or modified versions of same, I will let you know.
I've wanted a more secure methodology for mail transport outside of LANs for a while so this is my time to get it right.

REOUT

---

### Post by VorDesigns on 2007-06-12
OK, it took me a while and I've made mistakes but here is what I did to get secure socket smtp connections going.

First:  I installed SASL support:
```
sudo -
<password>
apt-get install libsasl2-modules-sql
```

I had some issues here because I am testing Drupal on the same box and the dbconf component wasn't happy.  I don't know yet what all is broken since Drupal still works.

Next I tried to get SASL to work, to know avail, here is the current state of my functioning Postfix main.cf:
```
# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

# POSTMASTER FUNCTIONS
notify_classes = bounce, delay, policy, resource, software, protocol
luser_relay =
always_bcc =

# SECURITY PRECAUTION
disable_vrfy_command = yes
smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
#
# smtp client relay
#
# smtpd_tls_auth_only = yes
#
# SASL configuration
#
smtpd_sasl_auth_enable          = yes
broken_sasl_auth_clients        = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_recipient_restrictions    = permit_mynetworks,
        permit_sasl_authenticated,
        reject_unauth_pipelining,
        reject_non_fqdn_recipient,
        reject_unknown_recipient_domain,
        reject_unauth_destination,
#       check_policy_service inet:127.0.0.1:60000,
        permit

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = daifukucho.domain1.tld
alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps
alias_database = mysql:/etc/postfix/mysql_virtual_alias_maps
myorigin = /etc/mailname
# D's suggestion
mydestination =
# mydestination = daifukucho.domain1.tld, localhost.domain1.tld, localhost
relayhost =

# UCE RESTRICTIONS
mynetworks = 127.0.0.0/8
smtpd_helo_required = yes
strict_rfc821_envelopes = yes
allow_untrusted_routing = no
# toubleshooting send
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks,
        warn_if_reject reject_non_fqdn_sender,
        reject_unknown_sender_domain,
        reject_unauth_pipelining, permit

mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

#
# Amavis
#
content_filter = smtp-amavis:[127.0.0.1]:10024
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps
smtpd_sender_login_maps = mysql:/etc/postfix/mysql_sender_login_maps
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_mailbox_domains
virtual_uid_maps = static:155
virtual_gid_maps = static:155
virtual_transport = virtual
fallback_transport = virtual
virtual_mailbox_base = /var/mail/vhosts
```

I couldn't get it to work because I don't want to use Cyrus for authentication, I wanted to authenticate against your database using TLS/SASL encrypted authentication.  I floundered here until I ran across directions for using Dovecot to authenticate which in the [ Postfix SASL Readme](http://www.postfix.org/SASL_README.html)
I took what I needed from there which was the authentication socket link previously listed in the main.cf:
```
    smtpd_sasl_type = dovecot
    smtpd_sasl_path = private/auth
```

Then I opened access in Dovecot
```
  socket listen {
    #master {
      # Master socket is typically used to give Dovecot's local delivery
      # agent access to userdb so it can find mailbox locations. It can
      # however also be used to disturb regular user authentications.
      # WARNING: Giving untrusted users access to master socket may be a
      # security risk, don't give too wide permissions to it!
      #path = /var/run/dovecot/auth-master
      #mode = 0600
      # Default user/group is the one who started dovecot-auth (root)
      #user =
      #group =
    #}
    client {
      # The client socket is generally safe to export to everyone. Typical use
      # is to export it to your SMTP server so it can do SMTP AUTH lookups
      # using it.
      #path = /var/run/dovecot/auth-client
      path = /var/spool/postfix/private/auth
      mode = 0660
      user = postfix
      group = postfix
    }
  }
```

I can now send mail from a remote host, logging in as a user from one of the virtual domains and relay mail to a third domain.

---

### Post by VorDesigns on 2007-06-12
I guess my next step is to figure out how agressive Spam Assasin is.

---

### Post by darrenm on 2007-06-12
Nice! Glad you got there in the end. I haven't looked at SMTP auth at all so I couldn't have offered any advice on that side unfortunately.

Spamassassin, when properly configured and trained and correctly looking at RBL's, DCC, razor, etc is very effective. At least as effective as any commercial spam filtering solution.

Finally if this is any help this is a functioning (perhaps buggy) part of the UGS code. Just install Apache2, libapache2-mod-php5, php5-mysql and then extract this archive into /var/www/ then edit /var/www/config.php to change the database name to vmail_development and the username and password for the database. Again this is just some code I've been playing around with so no warranty or completeness is implied. [www.vcoc.co.uk/ugs_sample_mail.tar.bz2](www.vcoc.co.uk/ugs_sample_mail.tar.bz2)

---

### Post by VorDesigns on 2007-06-23
Welp,

I did get the authentication part going but not the encrypted connection.

Back to the hacking board.

---

### Post by darrenm on 2007-06-24
What mail client are you using? 

For POP3 it needs to be SSL on port 995
For SMTP it needs to be TLS on port 25

---

### Post by VorDesigns on 2007-06-24
I'm using Evolution for testing; POP3S, according to the configuration.  I installed dovecot Imap for testing Imp mail.

I'm going to be absent; I didn't realize that I was posting under the pre-1695 English Crown rules of ownership for all printing presses with respect to posting here, but, post and learn.

Catch any further posts at [VorDesigns Forum]("http://www.vordesigns.com/portal/phpbb2/index.php"), I don't actually use my forum for much more than a tech doc repository and toy but, I guess I'll be troubleshooting and writing notes there freely from now on.

:-#

---

### Post by darrenm on 2007-06-24
> **VorDesigns said:**
> I'm going to be absent; I didn't realize that I was posting under the pre-1695 English Crown rules of ownership for all printing presses with respect to posting here, but, post and learn.



??

---

### Post by VorDesigns on 2007-06-27
Couldn't not contribute anyway, more interested in helping that giving a creamy dump about gag orders:
[request for clear HOWTO for horde3+imp4 on Edgy ]("http://ubuntuforums.org/showthread.php?p=2923332#post2923332")

---

### Post by iceman114 on 2007-07-26
Just wondering if any of you guys had installed a webmail interface with this setup, so that users on any domain hosted on the machine could check their email via webmail.

I configured my setup to use IMAP as well as POP3S.

In other setups I use Squirrelmail and SQWebMail but wanted to hear ideas before installing something on this particular setup.

Thanks in advance,
~nate

---

### Post by VorDesigns on 2007-07-26
I have started installing HORDE with Imp but, I haven't finished setting it up.
-
I have used Imp with another system, it' isn't perfect but it works well.

---

### Post by iceman114 on 2007-07-27
Actually I installed Squirrelmail with this setup, just using the default package and it worked like a charm.  I only had to go set the IMAP server type to 'courier'.  I did not have to install any virtual domain or login plugins.  Users are able to log in with their full email address and everything works fine for multiple domains.

---

### Post by iceman114 on 2007-07-27
I just noticed a weird problem with this setup.

I have a user setup in the users table : [email]user@domain.com[/email]

I  also have an alias, [email]user@domain.com[/email] (same as real account) that is set up like so:

address: [email]alias@domain.com[/email]
goto: [email]alias@domain.com,otheruser@domain.com[/email]

The desired behavior is that the message goes to [email]alias@domain.com[/email] (the real user account) and also to [email]otheruser@domain.com[/email].

What is happening, is that [email]otheruser@domain.com[/email] is getting two copies of the mail.

Anyone have any ideas?

~n

---

### Post by mriz on 2007-08-16
Its really great article about to setup mail server with virtual domains. I got every thing working except from. How to read the recieved mails and sent mail. I have tried both with outlook client and with Squiremail. But i can't login to that but when i browse to /etc/mail/vhost i can find  domain folders and user folders having 3 folder with name new current and another whcih is having the mail i have sent to them. But how i can read and write a mail by using any client by web or by outlook. Please write about that and then i think its a complete guide for mail setup

---

### Post by darrenm on 2007-08-18
> **iceman114 said:**
> I just noticed a weird problem with this setup.

I have a user setup in the users table : [email]user@domain.com[/email]

I  also have an alias, [email]user@domain.com[/email] (same as real account) that is set up like so:

address: [email]alias@domain.com[/email]
goto: [email]alias@domain.com,otheruser@domain.com[/email]

The desired behavior is that the message goes to [email]alias@domain.com[/email] (the real user account) and also to [email]otheruser@domain.com[/email].

What is happening, is that [email]otheruser@domain.com[/email] is getting two copies of the mail.

Anyone have any ideas?

~n

Hi. Sorry I didn't spot this at the time. Can you do a:
```
mysql -uroot -p ugs_development
select * from aliases;
```
and post the output? From what I can see it should work but I'd just like to see whats actually been put into the DB.

---

### Post by darrenm on 2007-08-18
> **mriz said:**
> Its really great article about to setup mail server with virtual domains. I got every thing working except from. How to read the recieved mails and sent mail. I have tried both with outlook client and with Squiremail. But i can't login to that but when i browse to /etc/mail/vhost i can find  domain folders and user folders having 3 folder with name new current and another whcih is having the mail i have sent to them. But how i can read and write a mail by using any client by web or by outlook. Please write about that and then i think its a complete guide for mail setup

Hi. Outlook should work as long as you use SSL with POP (port 995) and TLS with SMTP (port 25) What happened when you tried to use it? I use Evolution and Thunderbird using SPOP3 and SIMAP at the same time for different users and it seems to work fine.

I'm about to install roundcube on my gateway so I'll write about that too. This guide really needs an update though because I have a PHP webapp that works much smoother than the rails scaffolding. BRB :)

---

### Post by bebitzaa on 2007-08-31
Hello,
I have follow the same steps and all it's working good i mean i didn't get any errors on server but when i try to conect from my pc with outlook expres i can't.
Caan please help me with this.
I can give you access to see what i am doing wrong.
Thanks

---

### Post by darrenm on 2007-08-31
> **bebitzaa said:**
> Hello,
I have follow the same steps and all it's working good i mean i didn't get any errors on server but when i try to conect from my pc with outlook expres i can't.
Caan please help me with this.
I can give you access to see what i am doing wrong.
Thanks

Hi. Can you try with Thunderbird? The settings I put up here are for SSL POP3. If OE has issues with that (I assume thats the problem) then just change POP3s to POP3 at the top of /etc/dovecot/dovecot.conf then restart Dovecot.

If you still have issues then post the /var/log/mail.info file (or the end of it)

If you then still have problems I can SSH in if you really want.

---

### Post by bebitzaa on 2007-08-31
Heh i fixed it.
Now the problem is that the password it's not good, it's ask for the password i enter the password from the user database and it doesn't work.
Do you still wan't to mail.log ?

---

### Post by bebitzaa on 2007-08-31
I see on my /var/mail/vhosts/domain.com/user that are 3 folders and in folder 'new' there is a test message sended by my but i can't get it in oe.

> **bebitzaa said:**
> Heh i fixed it.
Now the problem is that the password it's not good, it's ask for the password i enter the password from the user database and it doesn't work.
Do you still wan't to mail.log ?

---

### Post by bebitzaa on 2007-08-31
There was a problem logging onto your mail server. Your User Name was rejected. Account: 'mail.rorhost.ro', Server: 'mail.rorhost.ro', Protocol: POP3, Server Response: '-ERR Plaintext authentication disallowed on non-secure connections.', Port: 110, Secure(SSL): No, Server Error: 0x800CCC90, Error Number: 0x800CCC91

Look what i got in OE. sorry for posting too much

---

### Post by darrenm on 2007-09-01
Hi there. Sorry it took a while to reply.

You just need to enable unsecure connections in /etc/dovecot/dovecot.conf

Look for disable_plaintext_auth = yes and change it to no then restart dovecot.

---

### Post by bebitzaa on 2007-09-03
still didn't work.
Can i pm you with user/pass to have a look.
Thanks

---

### Post by darrenm on 2007-09-03
Yep no worries.

---

### Post by bebitzaa on 2007-09-03
i have send you a pm

---

### Post by slimjimflim on 2007-11-16
hi. i don't know if anyone's still following up on this thread, but i just went through the tutorial on gutsy.  everything seemed to go fine, but i'm stumped when it comes to setting up an alias.  also, how can i send/receive mail from a shell?

---

### Post by VorDesigns on 2007-11-19
> **slimjimflim said:**
> hi. i don't know if anyone's still following up on this thread, but i just went through the tutorial on gutsy.  everything seemed to go fine, but i'm stumped when it comes to setting up an alias.  also, how can i send/receive mail from a shell?

Hi,

The Alias' are setup through Ruby on Rails http://<server_name_or_IP>:3000/alias

Postfix handles the sending and receiving on its own.

---

### Post by yino on 2008-01-02
Since Ruby 2.0, the Scaffold and the paginate methods are deprecated, you can make it work installing the following plug-ins

sudo script/plugin install scaffolding
sudo script/plugin install svn://errtheblog.com/svn/plugins/will_paginate
sudo script/plugin install svn://errtheblog.com/svn/plugins/classic_pagination


The classic_pagination is should be enough to have pagination with scaffolding but will_paginate is the recomended one, so I just installed both.

---

### Post by alexebird on 2008-06-17
> **VorDesigns said:**
> First to your question GlenTech:
Try this from your home directory

```
cd ~/rubyapps/vmail
sudo nano config/database.yml
```
(substitute gedit if you are using the GUI)

Scroll through the file until you see something like the following. We are just interested in development entry, leave the test and production alone. 

```
development:
  adapter: mysql
  database: vmail_development
  username: root
  password: yourpassword
  # there was no host: localhost entry so I added it but
  # it errors out on my system,
  # host: localhost
  # so I went with this instead
  host:  127.0.0.1
 # rather than delete the stock entry, I commented it out so I have a way back.
 # socket: /var/run/mysqld/mysqld.sock
 # this is what the How-to says to add below
  socket: /var/run/mysqld/mysqld.run
```

Your database.yml really helped me out.  Thanks!

---

### Post by VorDesigns on 2008-06-17
You are welcome, wish I had time to do this one again.  Been too busy doing NT4 to AD2K3 upgrades.

---

