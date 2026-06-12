---
title: "My install log"
date: 2005-05-30
forum: Outdated Tutorials &amp; Tips
---

### Post by word_virus on 2005-05-30
Here's my install notes as of 05/30.  This is from warty through a dist-upgrade to hoary.  Advanced users aren't going to find anything too earth shattering here, and a lot of it is copy and pasted directly from other posts found on the forum, but I figured I'd post it in the hope that it maybe comes in handy for new users.

As I re-read these notes, I'm amazed at how few of the issues I've had installing/configuring things have come from Ubuntu itself.  Thanks again to the Ubuntu team for all their hard work!

Added universe repository to synaptic 

Added gnome-clipboard-daemon 
1. Downloaded binary from [http://members.chello.bl/~h.lai/gnome-clipboard-daemon](http://members.chello.bl/~h.lai/gnome-clipboard-daemon)
2. Extracted archive (tar jxvf)
3. sudo cp gnome-clipboard-daemon /usr/bin
4. Computer > Desktop Preferences > Sessions > Startup Programs
5. Add /usr/bin/gnome-clipboard-daemon
6. Log out, saving your session

Download J2RE 1.4.2 from java.sun.com 
Installed J2RE:
chmod a+x j2re1.4.2_07-linux-i586.bin
./j2re1.4.2_07-linux-i586.bin
sudo mv j2... /usr/local/
sudo ln -sf /usr/local/j2.../bin/java /usr/bin/java
sudo ln -sf /usr/local/j2.../bin/java_vm /usr/bin/java_vm
mkdir -p /home/username/.mozilla/plugins
cd /home/username/.mozilla/plugins
ln -s /usr/local/j2.../plugin/i386/ns610-gcc32/libjavaplugin_oji.so libjavaplugin_oji.so
sudo ln -s /usr/local/j2.../plugin/i386/ns610-gcc32/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/

Installed XMMS: 
sudo apt-get install xmms
sudo apt-get install libmikmod

Installed CPU specific kernel: 
sudo apt-get install linux-686

Installed build essentials: 
sudo apt-get install build-essentials
sudo apt-get install manpages-dev
sudo apt-get install autoconf
sudo apt-get install automake
sudo apt-get install libtool
sudo apt-get install flex
sudo apt-get install bison
sudo apt-get install gcc-doc
sudo apt-get install g++
sudo apt-get install x-window-system-dev
sudo apt-get install libgtk1.2-dev
sudo apt-get install libpng-dev


Installed MPlayer codecs:
ftp open ftp5.mplayerhq.hu/mplayer/codecs/essential20050216.tar.bz2
tar jxvf essential20050216.tar.bz2
sudo mkdir -p /usr/local/lib/codecs
sudo cp essential20050216/* /usr/local/lib/codecs/

Installed MPlayer W32 codecs from same

Installed Flac from Synaptic, shntool from source

Had to install shorten to properly use shntool.  Found at etree.org/shnutils/shorten/  3 step install (./configure, make, make install).

installed pdftk, totem-xine, mono, nmap, clamAV

MPlayer install:
Downloaded MPlayer-1.0pre6a.tar.bz2
Blue-1.4.tar.bz2
font-arial-iso-8859-1.tar.bz2
Made sure libpng12-dev installed in Synaptic
Make sure libjpeg installed in Synaptic
mv font to /usr/share/mplayer/font/
mv Skin to /usr/share/mplayer/Skin/default/
./configure --enable-gui
make
sudo make install

needed xmms development libraries to build scizzor plugin
installed scizzor plugin (configure, make, install)

installed lame libraries for FFMpeg (configure, make, install)

installed FFMpeg (./configure --enable-shared --enable-mp3lame, make, install)
Turns out there's an ubuntu package for this in Synaptic.

apt-get install dog

added aliases for ls, clear, and dog to .bashrc. Will add hostnames later.

Transcode is a whore and a half. 
Best so far = ./configure --disable-lame
Even tho I have lame installed in /usr/local/bin - this prog also required mjpeg, ffmpeg, libdvdread, freetype2, avifile, and lame.

Turned out I had grabbed the wrong lame libs.  Downloaded the correct ones from the marilliat repository (liblame-dev or something).  Transcode successfully compiled.

grabbed bittorrent source bittorrent.com

Downloaded Skype .deb from company website and installed with dpkg -i

Downloaded Acrobat Reader 7 from Adobe FTP.  First tried to convert .RPM to .deb with alien and install with dpkg -i.  Installed "acroread" in /usr/bin and created icon in Applications in gnome menu but did not install program.  Next built from .tar.gz file.  Worked fine.  Made a sym link from /usr/bin/acroread to actual executable file.

built xmms-shn from source and installed (./configure, make, make install) to listen to shn files

Created new 2k GPG key (gpg --gen-key) and configured Enigmail (Thunderbird extension) to use it.

wget -m -np mafihe.hu/~bnc/feynman/ - Will back up to DVD and that's the last time I'll have to leech those.

Setup barebones .screenrc:
allpartial off
autodetach on
debug off
time
nethack on
multiuser off
startup_message off
vbell on 

Added host aliases to .bashrc using files at dotfiles.com as reference.

Setup firefox bookmarklets for Library Lookup (thanks John Udell!), my del.icio.us, post to del.icio.us and Bloglines.
 
Configure Macromedia flash plugin at:
macromedia.com/support/documentation/en/flashplayer/settings_manager.html
404'd for me as of 29 May 2005

Getting localhost mail in Thunderbird:
Edit -> Preferences -> Add Acount
Movemail
username@localhost
sudo chmod 1777 /var/spool/mail/

installed CrossOver Office Pro 4.1 from .DEB with sudo dpkg -i crossover-pro4.1.deb

Edited /lib/lsb/init-functions to display GREEN status message instead of boring grey.

This patch applies to /lib/lsb/init-functions
--- init-functions.orig 2004-12-18 23:45:08.756780424 +0100
+++ init-functions      2004-12-18 23:44:52.699221544 +0100
@@ -190,9 +190,10 @@
         END=`$TPUT hpa $COL`
         START=`$TPUT hpa 0`
         RED=`$TPUT setaf 1`
+       GREEN=`$TPUT setaf 2`
         NORMAL=`$TPUT op`
         if [ $1 -eq 0 ]; then
-            echo "$UP$END[ ok ]"
+            echo "$UP$END[ ${GREEN}ok${NORMAL} ]"
         else
             echo -e "$UP$START $RED*$NORMAL$END[${RED}fail${NORMAL}]"
         fi

Couldn't read floppy disks because system reported no /dev/fd0.  Ran:
sudo modprobe floppy
and then mounted floppy in usual fashion (mount /media/floppy) and it worked.
Added line "floppy" to /etc/modules

Upgraded system to Ubuntu Hoary:
changed /etc/apt/sources.list from 'warty' to 'hoary'
apt-get update
apt-get dist-upgrade
apt-get install ubuntu-base ubuntu-desktop
apt-get --pure remove portmap
vi /etc/mkinitrd/mkinitrd.conf - Replace `#RESUME' with 'RESUME=/dev/hda5'
shutdown -r now

Installed DVD Shrink via X-Over Office.  Seems to have b0rked gnome-panel.  Will get back to this one.
gnome-panel not borked, just unhappy for awhile.  Everything okay now, haven't tested DVD Shrink, yet.

Getting microphone to work in applications was a simple matter of (SB Audigy2 Platinum):
Right-click Audio
Open Volume Control
Selecting Audigy2 from device
Enabling Line2 and Microphone
Increasing volume in Line2

Made iPod work.  Simply a matter of plugging it in.  Auto-mounts under /media/IPOD
Copied directory structure in gtkpod.
Next time run make sure to Import existing iTunesDB before adding/deleting/updating.

Installed cups-pdf.  Edited /etc/cups/cups.conf - RunAsUser No

Tried turning off system bell with "vi ~/.xsession - exec xset b off &"  Will see if that works. NO.  That broke things. Try again later.
Turned off console beep with:  echo 'set bell-style-none' >> ~/.inputrc

Created symlink /dev/dvd and /media/cdrom0

sudo apt-get install gdesklets
Applications -> Accessories -> gDesklets
Create Default profile
System -> Preferences -> Sessions
Startup Programs
Add
Command: gdesklets
Order: 50
OK
Installed Hypertail desklet to watch /var/log/messages and /var/log/syslog and /var/log/auth.log.  Also had to install gdesklets dev package to use hypertail w/o startup error message.

Edited /etc/hdparm to enable DMA on CDROM drive to speed CD ripping.  Init scripts attempt to config CD before it's created in /dev.  Renamed /etc/rcS.d/S07hddparm to S99hdparm to fix.
Also disabled Autoplay in gnome, don't know if this has had any effect on rip speed, yet.

Installed Ruby on Rails and MySQL server
apt-get install mysql-server
apt-get install libyaml-ruby
apt-get install libzlib-ruby
downloaded ruby gems from rubyonrails.com and extracted it to /tmp
cd /tmp
sudo ruby setup.rb
sudo gem install rails
follow prompts

For some reason, on next startup, ownership of the file .ICEauthority had been changed from me to root, making logging into Gnome an impossibility.  Booted into the terminal and did 'sudo chown username:username .ICEauthority'.  This seems to have fixed the problem.

Above did not work for some reason, instead followed these directions from rails wiki:

apt-get install irb1.8 libbigdecimal-ruby1.8 libcurses-ruby1.8 libdbm-ruby1.8 libdl-ruby1.8 libdrb-ruby1.8 liberb-ruby1.8 libgdbm-ruby1.8 libiconv-ruby1.8 libopenssl-ruby1.8 libpty-ruby1.8 libracc-runtime-ruby1.8 libreadline-ruby1.8 librexml-ruby1.8 libruby1.8 libruby1.8-dbg libsdbm-ruby1.8 libsoap-ruby1.8 libstrscan-ruby1.8 libsyslog-ruby1.8 libtest-unit-ruby1.8 libwebrick-ruby1.8 libxmlrpc-ruby1.8 libyaml-ruby1.8 libzlib-ruby1.8 rdoc1.8 ri1.8 ri rdoc ruby ruby1.8 ruby1.8-dev libmysql-ruby1.8 ruby1.8-examples

Common procedure for Debian Testing and Ubuntu (You don¿t need to do this if you¿re running Debian Unstable)

Download the rubygems package installer, used to install gems (ruby packages), from [http://rubyforge.org/frs/download.php/3700/rubygems-0.8.10.tgz](http://rubyforge.org/frs/download.php/3700/rubygems-0.8.10.tgz)

Extract rubygems:

        tar zxvf rubyrubygems-0.8.10.tgz

Set up rubygems:

        cd rubygems-0.8.10
sudo        ruby1.8 setup.rb

Use the rubygem installer to re-install itself. This will get you the latest revision:

sudo        gem install rubygems

OK, now you can install gems for other software. Run this command to install rails:

sudo        gem install rails

Answer y to all of the requests to install dependencies.

Once this completes, you should have a rails command. Test it:

        cd ~
        rails Test
        cd Test
        script/generate controller test
        script/server &

Open your web browser to [http://localhost:3000/](http://localhost:3000/) You should see a congratulations page.

localhost:3000/ said:

Congratulations, you've put Ruby on Rails!

Before you move on, verify that the following conditions have been met:

   1. The log and public directories must be writable to the web server (chmod -R 775 log and chmod -R 775 public).
   2. The shebang line in the public/dispatch* files must reference your Ruby installation.
      You might need to change it to #!/usr/bin/env ruby or point directly at the installation.
   3. Rails on Apache needs to have the cgi handler and mod_rewrite enabled.
      Somewhere in your httpd.conf, you should have:
      AddHandler cgi-script .cgi
      LoadModule rewrite_module libexec/httpd/mod_rewrite.so
      AddModule mod_rewrite.c

Take the following steps to get started:

   1. Create empty development and test databases for your application.
      Recommendation: Use *_development and *_test names, such as basecamp_development and basecamp_test
      Warning: Don't point your test database at your development database, it'll destroy the latter on test runs!
   2. Edit config/database.yml with your database settings.
   3. Create controllers and models using the generator in script/generate
      Help: Run the generator with no arguments for documentation
   4. See all the tests run by running rake.
   5. Develop your Rails application!
   6. Setup Apache with FastCGI (and Ruby bindings), if you need better performance 

Trying to setup a default page for Rails using Routes? You'll have to delete this file (public/index.html) to get under way. Then define a new route in config/routes.rb of the form:

  map.connect '', :controller => 'wiki/page', :action => 'show', :title => 'Welcome'

Having problems getting up and running? First try debugging it yourself by looking at the log files. 

Changed Gnome foot in start menu to Ubuntu logo with:

sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

killall gnome-panel

Wanted to be able to ssh into my home box from work.  Did the following:
Set static ip behind router by editing /etc/interfaces

changed from:
auto eth1
iface eth1 inet dhcp

To:
auto eth1
iface eth1 inet static
address 192.168.1.60
netmask 255.255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

Then, pointed firefox @ gateway address (It's a Linksys WRT54G, for the curious), logged in -> Applications and Gaming

Set "Application:" ssh
"Start:" 22
"End:" 22
"Protocol:" Both
"IP Address:" 192.168.1.60
"Enable"
Save

This forwards all incoming packets on port 22 to the machine running sshd.

Post mysql-server install config:  commented out "skip-networking" line in /etc/mysql/my.cnf to have mysql listen on 3306 (local network only, no port forwarding).
Also read /usr/share/doc/mysql-server/README.Debian for more information.

/usr/bin/mysqladmin -u root password *******

Done!

my wrt54g serial starts with "CDF7" meaning it's hardware version 2.2
Sveasoft Alchemy Final firmware available from: [http://www.wrt54g.org](http://www.wrt54g.org)

installed irc2
set up irc to automatically connect to irc.freenode.net, ~/.ircrc looks like:
^set display off
nick <username>
msg NickServ IDENTIFY <password>
join #ubuntu
set display on

installed firestarter software firewall
apt-get install firestarter
Allow incoming 'bt' 'ssh' : 'everyone'
edited sudoers ('sudo visudo -f sudoers' - this has changed since warty), added:
username ALL=NOPASSWD: /usr/sbin/firestarter
GNOME: System -> Preferences -> Sessions -> Startup Programs
Added: gksu firestarter --start-hidden
Firestarter -> Preferences -> check "Minimize to tray on window close"
OK

---

