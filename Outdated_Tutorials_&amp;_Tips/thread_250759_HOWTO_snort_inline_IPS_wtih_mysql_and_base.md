---
title: "HOWTO: snort_inline IPS wtih mysql and base"
date: 2006-09-04
forum: Outdated Tutorials &amp; Tips
---

### Post by ruibernardo on 2006-09-04
Snort_inline (snort as an IPS) with mysql and base

This is my first howto, and it is VERY experimental, not the instalation and compilation, but working with iptables rules and adapting them to snort_inline and the QUEUE target in iptables) so forgive me some mistakes. With some of your help, those mistakes will be corrected, so thanks in advance :)

To make this howto I've used several sources: [http://linuxgazette.net/117/savage.html](http://linuxgazette.net/117/savage.html), [http://linuxgazette.net/118/savage.html](http://linuxgazette.net/118/savage.html), [http://www.snort.org/docs/setup_guides/deb-snort-howto.pdf](http://www.snort.org/docs/setup_guides/deb-snort-howto.pdf) e [http://www.ubuntuforums.org/showthread.php?t=145641](http://www.ubuntuforums.org/showthread.php?t=145641) and adapted them) in case of doubt you can get some help from them too.

I think this is mainly for servers that work with windows machines (or not), for which you can add an antivirus (Clamav) addon.

I will be telegraphic as this howto is a bit long and complicated. You may loose your net connection during this howto. Please print it. If it happens (hope not) please flush your iptables with
```

sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT -j ACCEPT
sudo iptables -P FORWARD -j ACCEPT
sudo iptables -P OUTPUT -j ACCEPT 

```
We will install snort_inline-2.4.5a, which is snort but in inline mode (Intrusion Protection System).

Snort in inline mode doesn't use libnet1 from the repositories. It uses de deprecated version 1.0.2 of libnet, and snort doesn't compile with the one in the repositories. You will have to uninstall all the packets named snort (snort-common, snort e snort-mysql) and also libnet1* and libdnet*, if you have them installed. 

1. SNORT_INLINE AND OINKMASTER
Some packages are needed from the repositories: iptables-dev, libpcre3, libpcre3-dev, checkinstall, buid-essential, at least (some others may also be needed). Install them.

Also you will need to download the sources of libnet and libdnet that snort_inline uses: 

[http://www.packetfactory.net/libnet/dist/deprecated/libnet-1.0.2a.tar.gz](http://www.packetfactory.net/libnet/dist/deprecated/libnet-1.0.2a.tar.gz) 
[http://prdownloads.sourceforge.net/libdnet/libdnet-1.11.tar.gz?download](http://prdownloads.sourceforge.net/libdnet/libdnet-1.11.tar.gz?download)

Extract them in you home folder and compile ****each one of them 
```

./configure
make
sudo checkinstall 

```
download snort_inline from 

[http://prdownloads.sourceforge.net/snort-inline/snort_inline-2.4.5a.tar.gz?download](http://prdownloads.sourceforge.net/snort-inline/snort_inline-2.4.5a.tar.gz?download)

and extract it too,

In the snort_inline options of ./configure do
```

./configure --mandir=/usr/share/man --with-mysql=/usr --enable-flexresp 
make
sudo checkinstall 

```
In checkinstall change the name of the package to one that do not use the underscore, as it is an invalid character, i.e. "snort-inline-2.4.5a".

Those options enabled flexresp too. If you use Clamav antivirus, you can use snort_inline to stop viruses too. Look at ./configure --help. I haven't tested them, but it can usefull.

After all compiled and installed, copy TO the rules folder in snort_inline source code folder the following files (if the folder is ~/snort_inline-2.4.5a):
```

cp ~/snort_inline-2.4.5a/etc/classification.config ~/snort_inline-2.4.5a/rules/ 
cp ~/snort_inline-2.4.5a/etc/reference.config ~/snort_inline-2.4.5a/rules/ 

```
and then copy those files to /etc/snort_inline/ that you will create now,
```

sudo mkdir /etc/snort_inline
sudo cp ~/snort_inline-2.4.5a/etc/* /etc/snort_inline/
sudo cp ~/snort_inline-2.4.5a/rules /etc/snort_inline/ -R 

```
edit snort_inline.conf
```

sudo gedit /etc/snort_inline/snort_inline.conf 

```
and change
```

var RULE_PATH /etc/snort_inline/drop_rules 

```
to
```

var RULE_PATH /etc/snort_inline/rules 

```
save and exit. Install oinkmaster to update snort_inline rules:
```

sudo apt-get install oinkmaster 

```
go to snorts site, register to get a code so you can download updated rules
[https://www.snort.org/pub-bin/register.cgi](https://www.snort.org/pub-bin/register.cgi)

Change the file /etc/oinkmaster.conf to use your code and to set it to version 2.4 of snort
```

sudo gedit /etc/oinkmaster.conf 

```
and search for the following line:
```

url = http://www.snort.org/dl/rules/snortr...hot-2_2.tar.gz 

```
change it to
```

url =http://www.snort.org/pub-bin/oinkmaster.cgi/5a08f649c16a278e1012e1c84bdc8fab9a70e2a4/snortrules-snapshot-2.4.tar.gz 

```
where 5a08f649c16a278e1012e1c84bdc8fab9a70e2a4 is changed to your code. Search for the word **modifysid** in the file and after the comments and explanations about modifysid add a new line
```

modifysid * "^alert" | "drop" 

```
Save and exit. This will change all the rules you will download that are "alert" and are to snort IDS to "drop" and that snort_inline will use to act as an IPS. Now download the rules to the /etc/snort_inline/rules folder with:
```

sudo oinkmaster -o /etc/snort_inline/rules 

```
Check if the *.rules files are in the folder /etc/snort_inline/rules and are with drop in the begining of the rules. 

2. MYSQL
Install mysql with:
```

sudo apt-get install mysql-server 

```
edit the file snort_inline.conf
```

sudo gedit /etc/snort_inline/snort_inline.conf 

```
add the following line so snort_inline starts logging to a mysql database
```

output database: log, mysql, user=root password=test dbname=snort host=localhost 

```
(the user of snort will be root, as snort_inline only runs as root, because of iptables).
Change the "var RULE_PATH" line to
```

var RULE_PATH /etc/snort_inline/rules 

```
modify other lines starting with var so they match your network settings, save and exit. Add a password to root in mysql as it is defined in snort_inline.conf (of course you "must" change it from "test").
```

sudo mysqladmin -u root password <password> 

```
Now create the database to snort_inline:
```

mysql -u root -p 

```
write the roots password that was defined before, and then, create the database
```

mysql> create database snort;
mysql> grant insert,select on root.* to snort@localhost;
mysql> grant create,delete,insert,select,update on snort.* to root@localhost;
mysql> grant create,delete,insert,select,update on snort.* to root; 

```
Import the database schema of snort from the source code folder of snort_inline, in the folder named schemas there's the file create_mysql
```

cd ~/snort_inline-2.4.5a/schemas/
sudo mysql -u root -p < create_mysql snort 

```
check if the database exists:
```

sudo mysql -u root -p

mysql> use snort;
mysql> show tables; 

```
you should see the database structure. Leave mysql.
```

mysql> exit 

```

3. BASE
Install apache and php5-mysql
```

sudo apt-get install apache2 php5-mysql

```
download base 1.3.0 from

[http://sourceforge.net/projects/secureideas](http://sourceforge.net/projects/secureideas)

and install it to /var/www
```

sudo mv baseplus-1.3.0.tar.gz /var/www
cd /var/www
sudo tar -xvzf baseplus-1.3.0.tar.gz
sudo rm baseplus-1.3.0.tar.gz
mv baseplus-1.3.0 base

```
we will put this directory with full access to everyone just to set up base to finish the base installation
```

sudo chmod 777 base

```
Point your browser to [http://localhost/base](http://localhost/base), click in "continue", select your language and submit, in "Database Name" put snort, in "Database Host" put localhost, in "Database User Name" put root, and in "Database Password" put the password you defined earlier. Click "Submit". Next step click "Submit" and later "Create BASE AG". Next screen click "Now continue to step 5..."

After the set up of BASE as ended, put defaults permissions to its directory back the original ones.
```

sudo chmod 755 base

```
To make graphics work, install and do this
```

sudo apt-get install php5-gd php-pear
sudo pear install Image_Color
pear install Image_Canvas-alpha
pear install Image_Graph-alpha 

```
Restart apache2:
```

sudo /etc/init.d/apache2 restart
cd (to return to your home)

```

4. GETTING IT TO WORK
Load ip_queue module with
```

sudo modprobe ip_queue 

```
and change your iptables scripts ACCEPTs to QUEUE in the rules you wish. Be care full with localhost 127.0.0.1, as snort detects its connections as an attack named "(snort decoder) Bad Traffic Same Src/Dst IP" and will drop the connections to/from localhost. Put those lines as ACCEPT. You can use the firewall.sh script below as example, so save it in /etc and make it executable.
```

sudo cp firewall.sh /etc/firewall.sh
sudo chmod +x /etc/firewall.sh

```
(To make snort_inline work right, it must control all the connections (except for localhost/127.0.0.1) ALL ACCEPT must be QUEUE (input and output, related established new, forward, etc)! In attachments there is an example of a iptables script using QUEUE.)

Next, save the file in attachments named snort_inlined to /etc/snort_inlined make it executable and starting after network is up (50):
```

sudo cp snort_inlined /etc/init.d/snort_inlined
sudo chmod +x /etc/init.d/snort_inlined
sudo update-rc.d snort_inlined defaults 50

```
start the snort_inlined:
```

sudo /etc/init.d/snort_inlined start

```
Point your browser to [http://localhost/base](http://localhost/base) and you should see the packets that snort_inline drops. Start amule and some ICMP "Destination Unreachable" should appear.

Theres are many things you can and/or should change in all this: the firewall, snort_inline configuration and snort_inline rules. If you should change the firewall script, and changed its name/location, please edit /etc/init.d/snort_inlined and updated it too (start section). Snort_inline configuration is on /etc/snort_inline/snort_inline.conf. Please read snort documentation about its configuration and rules.

---

### Post by ruibernardo on 2006-09-09
Here are some shots of BASE showing what snort_inline filtered.

---

