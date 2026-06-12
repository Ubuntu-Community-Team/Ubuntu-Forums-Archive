---
title: "How to install Quasar Accounts"
date: 2005-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by jonny on 2005-07-31
Quasar is accounting software for Linux.  It's powerful and easy to use &#8211; certainly more so than commercial small business alternatives available in the UK &#8211; and a full range of support packages are available from the authors.  It needs a Linux server, but clients are available for both Windows and Linux.  This how-to only covers installation on a single Ubuntu box that acts as both client and server.  If you need multi-user access but can't work out how to do it yourself, it sounds like you need to get a support package.

Unfortunately, Quasar's not straightforward to install on Ubuntu, as no pre-built packages are available.  In principle, it should be possible to install one of the packages built for other distributions, but building from source is likely to be more reliable.  That's the approach that I've adopted here.

If you're new to Linux, don't be intimidated; this process is easier than it looks.  But it is quite lengthy so allow yourself a couple of hours, especially if you have a slow machine.

**Step 1: Install and build Quasar**
First, go to [www.sourceforge.net/projects/icu](www.sourceforge.net/projects/icu), and download the file icu-3.2.tgz to your desktop.  Note that the '3.2' part of the file name is the version number, and that might change if a new release is made.  If so, you'll need to change all subsequent references in this how-to to reflect the new version number.

Next, go to [www.linuxcanada.com](www.linuxcanada.com), and download the file quasar-1.4.7_GPL.tgz to your desktop; the same caveats about version numbers apply to this file.  While you're there, also download the comprehensive product documentation provided by Linux Canada.

Now go to [www.ubuntuguide.org](www.ubuntuguide.org), and follow the advice on 'How to install additional repositories'.  Then open up a terminal session (not a root terminal), and enter the following:```
sudo apt-get install build-essential libqt3-mt-dev autoconf tcl8.4-dev tk8.4-dev postgresql-dev qt3-apps-dev smeg kcontrol postgresql
killall gnome-panel
mkdir ~/quasar
mv ~/Desktop/quasar-1.4.7_GPL.tgz ~/quasar/
mv ~/Desktop/icu-3.2.tgz ~/quasar/
cd ~/quasar/
tar xzf icu-3.2.tgz
tar xzf quasar-1.4.7_GPL.tgz
cd icu/source/
./configure
make
sudo make install
sudo cp /usr/local/lib/icu* /usr/lib/
sudo cp /usr/local/lib/libicu* /usr/lib/
cd ~/quasar/quasar-1.4.7_GPL/
./configure
make
sudo make install

```
**Step 2: Create the menu entries**
Open Smeg Menu Editor (it's in Applications --> System Tools) and create entries for Quasar and Quasar Admin in the Office menu.

Quasar Admin:
  Command: gksudo /opt/quasar/bin/quasar_setup
  Icon: /opt/quasar/setup/quasar_setp.xpm

Quasar
  Command: /opt/quasar/bin/quasar
  Icon: /opt/quasar/setup/quasar_client.xpm

**Step 3: Set up the PostgreSQL database**
Enter the following code:```
su postgres
createuser -d -E -P quasar-dba
createuser -E -P quasar
exit
sudo gedit /var/lib/postgres/data/pg_hba.conf
```Replace all text with these lines:

host all all 127.0.0.1 255.255.255.255 md5
host all all 192.168.1.0 255.255.255.0 md5

```
sudo gedit /etc/postgresql/pg-hba.conf
```Replace all text with these lines:

host all all 127.0.0.1 255.255.255.255 md5
host all all 192.168.1.0 255.255.255.0 md5
```
sudo /etc/init.d/postgresql restart
```
**Step 4: Make the screen display more acceptable**
Ubuntu's default settings for KDE applications look horrible with Quasar.```
kcontrol
```I set all the fonts to Sans Serif 10 and chose the Plastik style.  You may prefer other settings.

**Step 5: Connect Quasar to the PostgreSQL server**
Applications --> Office --> Quasar Admin

Go to the Drivers Tab, and hit Configure.  Enter these settings.
Hostname: localhost
Port: 5,432
Library: /usr/lib/libpq.so.3.1
DBA username: quasar_dba
DBA password: whatever you entered earlier
Username: quasar
Username password: whatever you entered earlier
Character set: UNICODE

**Step 6: Enjoy**
That's all, folks.  Let me know how you get on.

---

### Post by phil123 on 2005-11-26
Thanks Jonny for that explanation. My Ubuntu complains that it does not have "smeg". Any ideas about how to deal with that?
phil123

---

### Post by jonny on 2005-12-01
The first line of my script should have installed it.  Try re-running that first line of code again (sudo apt-get...) and make sure that you use the scroll bar to grab it all.

---

### Post by BrownieMan on 2006-04-05
[QUOTE=jonny]Step 3: Set up the PostgreSQL database
Enter the following code:
Code:

su postgres createuser -d -E -P quasar-dba createuser -E -P quasar exit sudo gedit /var/lib/postgres/data/pg_hba.conf

Replace all text with these lines:

host all all 127.0.0.1 255.255.255.255 md5
host all all 192.168.1.0 255.255.255.0 md5[/QUOTE]

When I try to save the file it wont let me save it. Then when I go to the next step,

"sudo /etc/init.d/postgresql restart"

it says "sudo: /etc/init.d/postgresql: command not found". Also after that I go to teh drivers tab and nothign is there for me to configure.

---

### Post by mindbone on 2006-04-12
When I type "sudo make install" after

cd ~/quasar/quasar-1.4.7_GPL/
./configure
make

it starts to do its thing, then it will go

./install all
ERROR: can't install server process using xinetd or inetd
       you will need to setup quasard to run at boot time

What is the deal with that?

thanks in advance for reading this.

---

