---
title: "How to Broadcast Under Linux"
date: 2007-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by kitsaros on 2007-06-24
How to broadcast with Xmms,Ices2,Peercast and Peercast2Html under linux
----------------------------------------------------------------------------------
----------------------------------------------------------------------------------
A. Prologue :
This guide was 100% successfully tested on Kububtu 7.04.
It might needs some modifications on other linux distros.
----------------------------------------------------------------------------------
----------------------------------------------------------------------------------
B. Configuration :
///I INSTALLATION
1.Install 3 packages (i used adept manager under Kubuntu you can use apt-get ...)
 "aumix-gtk" , peercast (not the gtk gui) , ices2
 Download peercast2html from [here](http://www.trustfm.net/radio/SoftwarePeercast2HtmlForLinux.html)

///II CONFIGURATION OF AUMIX
2. Open a terminal, Open Aumix by entering:

          aumix

3. Click the box under "Rec" next to "Vol", this sets Ubuntu to record (hence, stream) "what you hear"

4. Close Aumix

///III CONFIGURATION OF PEERCAST
5. Run peercast(probably is already running)
If it is not running or you have problems running peercast look here :
[http://www.peercast.org/guides/pc-linux.php](http://www.peercast.org/guides/pc-linux.php)
Now that you started peercast :
Open in mozilla the url :
[http://localhost:7144/html/en/settings.html](http://localhost:7144/html/en/settings.html)
Port: 7144
Password: yourpass (REMEMBER IT!!!)
Max. Relays: 2
Max. Direct streams: 2
press save settings and close mozilla

///IV CONFIGURATION OF ICES2
6. Create these three directories 
/home/trustfm/ices/
/home/trustfm/ices/metatags
/home/trustfm/ices/logs

7. Create a configuration directory for Ices2:

          mkdir ~/.ices2

8. Copy the default Ices2 configuration (ices2_config_peercast.xml configuration is included in this package):

          sudo cp /home/trustfm/ices2_config_peercast.xml ~/.ices2/ices2_config_peercast.xml

9. Now edit the default configuration:

          sudo kwrite ~/.ices2/ices2_config_peercast.xml

We make the below changes.  (Read the comment notes to understand how to edit that file).

<logpath>/home/trustfm/ices/logs</logpath>

<name>Example stream name</name>
<name>TrustFm</name>
<genre>My Genre</genre>
<description>Small Description</description>
<url>http://mysite.org</url>

<param name="metadatafilename">/home/trustfm/ices/metatags/metatags.txt</param>
WE REMEMBER THAT LOCATION !!! WE WILL USE IT LATER !!!

<port>7144</port>
<password>your peercast pasword</password>
...

10. Save the changes and close kwrite

11. Make the Ices2 configuration directories readable and writable to everyone:

          sudo chmod -R 0777 ~/.ices2

12. Close the terminal

13. change forceNormal to Yes in peercast
sudo kwrite /etc/peercast/peercast.ini.default
sudo kwrite /etc/peercast/peercast.ini
sudo kwrite /home/trustfm/peercast.ini

14. create an new txt file name it 'update.pl' . Put it on the metatags folder
example : /home/trustfm/ices/metatags

15. put these info below in update.pl and save it
#!/usr/bin/perl
@trackinfo = split(/ - /, $ARGV[0]);
system("echo \"TITLE=$trackinfo[1]\" > /home/trustfm/ices/metatags/metatags.txt");
system("echo \"ARTIST=$trackinfo[0]\" >> /home/trustfm/ices/metatags/metatags.txt");
system("killall -USR1 ices2");

16. open xmms and go to 
preferences -> general plugins -> song change -> configure
add this command in the first Command box: 
/usr/bin/perl /home/trustfm/ices/metatags/update.pl "%s"
we press ok
Now we have the metatag info at this file :
/home/trustfm/ices/metatags/metatags.txt

///V CONFIGURATION OF PEERCAST2HTML
17. Run peercast2html and configure it like this
peercast port 7144
refresh every 30 sec
host : enter your ftp like ftp.tripod.it
username : you username
password : your web server password
port use 21 (is the most common)
passive mode false (is the most common)
path :example 'live/' (it is an real path of your site example : [www.mysite.com/live/](www.mysite.com/live/) )
Note : the live directory must already exist on your webserver
Now press the default html button

Your Pubblishing page will be located at: [http://www.mysite.com/live/PeercastLiveStreams.html](http://www.mysite.com/live/PeercastLiveStreams.html)

WE ARE DONE!!!
--------------------------------------------------------------
--------------------------------------------------------------
C. Start broadcasting : 

IN ORDER TO START BROADCAST JUST RUN ICES2 + PEERCAST2HTML  !!!!

1. ices2 ~/.ices2/ices2_config_peercast.xml (not as sudo/admin !!!)

2. Run peercast2html and press the 'Online button' (in order to pubblish your stream in the web)
   Your Pubblishing page will be located at: [http://www.mysite.com/live/PeercastLiveStreams.html](http://www.mysite.com/live/PeercastLiveStreams.html)

3. START PLAYING MUSIC WITH XMMS
--------------------------------------------------------------
--------------------------------------------------------------
D. Stop broadcasting :

IN ORDER TO STOP BROADCAST JUST

1) Close Peercast2html (or press the 'Offline button')

2) Now close ices by doing : killall ices2
----------------------------------------------------------------
----------------------------------------------------------------
E. Some usefull informations :

You can look your broadcast at : 
[http://localhost:7144/html/en/relays.html](http://localhost:7144/html/en/relays.html) or at
[http://yp.peercast.com](http://yp.peercast.com)

Your pubblic peercast link must start with : peercast://... from yp.peercast.com but it is with local ip
Find your ip by typing on the console : ifconfig

Happy Broadcasting ;)

Tell me if you have any problems !

---

