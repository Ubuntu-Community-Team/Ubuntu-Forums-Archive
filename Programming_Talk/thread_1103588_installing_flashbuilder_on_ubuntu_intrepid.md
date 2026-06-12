---
title: "installing flashbuilder on ubuntu intrepid"
date: 2009-03-22
forum: Programming Talk
---

### Post by blackest_knight on 2009-03-22
After a day of banging my head against the wall I finally got flashbuilder installed and working on intrepid.

I thought I'd give a bit of a procedure to getting it working (still not got the standalone player working but I can compile and run code.

first uninstall eclipse and your flash plugins (it only comes back to bite you later)

h++p://jhcore.com/2008/06/26/eclipse-34-ganymede-on-ubuntu/

sudo apt-get install openjdk-6-jdk

Then update your ~./bashrc file, appending the JAVA_HOME (adjust this if you use a different JDK).
nano .bashrc
export JAVA_HOME=/usr/lib/jvm/java-6-openjdk/

Get Ganymede

wget h++p://ftp.osuosl.org/pub/eclipse/technology/epp/downloads/release/ganymede/R/eclipse-java-ganymede-linux-gtk.tar.gz
tar xzvf eclipse-java-ganymede-linux-gtk.tar.gz
mv eclipse eclipse3.4

We should be ready to go:

eclipse3.4/eclipse

thats eclipse installed and working in your home directory

go get flex builder

h++p://labs.adobe.com/technologies/flex/flexbuilder_linux/

#

Run the installer either marking it as executable (chmod +x) or by using a shell to execute it (sh flexbuilder_linux_install_a4_081408.bin).

When prompted, specify whether to install Flash Player 9 (note that this is an updated version of Flash Player 9 and that Flex Builder Linux will work with earlier versions of Flash Player 9 for Linux). This is the debug version of Flash Player 9, which is required for debugging support and exception display.

ok I installed it to /home/me/Adobe_Flex_Builder_Linux running as me not root
I specified /home/me/eclipse3.4/ as the root directory for eclipse. 
there was a bit of hassle with flashplayer.so but i copied it from the install directory to /usr/lib/firefox/plugins

h++p://www.actionscript.org/resources/articles/611/1/Getting-started-with-Actionscript-3/Page1.html

this is a slightly buggy tutorial which should get you started with actionscript however there is a mistake on the class file on page2
he says name it movingball however it needs to be called movingcircle or it doesn't work.

Still got to figure out where to put the standalone player and I think i may have got the normal runtime plugin not the debug 

but its a start hope this helps someone .

---

### Post by blackest_knight on 2009-03-22
for the standalone player to work 
nano .bashrc and add this to the end of the file its the path to the standalone flashplayer.  one interesting item the standalone player has an option to make a projector which is a standalone executable of your swf file


PATH=$PATH:/home/me/Adobe_Flex_Builder_Linux/Player/linux/
export PATH

---

