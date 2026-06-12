---
title: "how to: Azureus/AzSMRC bittorrent for the home network"
date: 2007-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by cozmicharlie on 2007-12-10
[B][CENTER]How To 
Ubuntu for the Live Music Downloader/collector 

Part 3:  Set up Azureus/AzSMRC on a Home Network[/CENTER][/B]

This tutorial is Part 3 of a series on setting up Ubuntu for live music downloading, in Part 1 we set up the music player to play flac, shn, mp3 etc, Part 2 covered setting up Azureus as the bittorrent client.  The next step is to share bittorrent over the network so we don't have to install Azureus on all our network computers and end up with music files scattered over multiple computers.  In Part 3 I am going to show you how to do this the super easy way first then the slightly more complicated (but very powerful) method using a great Azureus plug in called AzSMRC.

One nice feature of Azureus is that it is written in Java so we can use Azureus on Windows, Linux and even Macs.  For example I have 4 computers on my home network: a Linux server running Ubuntu, a Ubuntu box in my media room, a laptop for work running Windows XP and my wife's Mac.  I set up Azureus on my Ubuntu server and all the other computers are set up as clients.  If you think Azureus is a resource hog, think about the resources required to run Azureus over a network – it's pretty low when you spread it across multiple computers.  

There is a very simple method for sharing bittorrent over a network using Azureus and the best part is, if you have Azureus installed you are done – all you have to do is tweak a few settings in Azureus – can't get much easier than that!  For the purpose of this HowTo let's assume we have Samba set up to share our home directory.  In order to share bittorrents we are going to set up a folder in our home directory for torrent files and tell Azureus to monitor this directory at specific time intervals and download any show when a new torrent file (the torrent file is not the music file but the file the tracker uses) is added to the directory.  Then all we have to do from any computer on our network is access the shared folder through Samba (could be ssh, ftp or any share), download the torrent file to our folder and sit back and let Azureus do the rest.  Azureus will see the torrent and automatically download the show from the tracker.   You can even set up Azureus to notify you when the show is completed, move the files to another folder once completed, categorize and lots more.  Pretty slick!  Doing it this way you don't even need bittorrent clients on each computer.  So let’s try it!

**Setting up Azureus share folders:**
[LIST=1]
[*]Open Azureus – if in Vuze go to view>advanced.  
[*]In the advanced window go to tools>options>files>torrents.  The screen below shows the dialog box.        
[*]Click on “import new torrents automatically” and browse to your folder you set up for your shares.  
[*]Set an interval for Azureus to check the folder. 
[*]Save and you are done.
[/LIST] 

Go here to see a screenshot 
[HTML]http://www.flickr.com/photos/swoskow/2101245103/
[/HTML]
To use this feature:  download the torrent (not the music files) from a tracker web site and place it in the share folder you just set up  – Azureus will do the rest.  How simple is that!  


**[CENTER]AzSMRC Plug-in For Azureus[/CENTER]**

We could stop here (and you may want to) but it's nice to have more control over the downloads and to do that, Azureus has this great server/client plug in called AzSMRC.  AzSMRC allows you to do more with Azureus and the developers are actively creating new plug-ins for AzSMRC.  With AzSMRC you have:
 
[LIST]
[*]Complete ability to manage torrents remotely 
[*]Manage hosting of torrents remotely 
[*]AzSMRC allows multiple users to use one running Azureus 
[*]WebUI: if you don't have the client installed you can simply use the WebUI to manage Azureus 
[*]View salient statistics about the Azureus server and also be able to restart the server at the touch of a button 
[*]Remotely administer Azureus updates 
[*]AzSMRC can update itself as well as report to the developers any crashes it detects 
[*]Plugins: you can extend the AzSMRC client like Azureus with plugins  and much more
[/LIST]

For example, you can set up AzSMRC to have complete control over the download parameters such as the folder to download to, moving the files once the download is completed, uploading a torrent for sharing and many more features.  This is the advantage of using AzSMRC – you have complete control and access to all the features of Azureus.  

[*]There are other ways to share Azureus over the network (Swing UI, HTML, XML over HTTP) and I have tried them all and I like AzSMRC.  You may want to check out the others and see which fits your needs though.   
	
**[CENTER]Installing AzSMRC in Ubuntu[/CENTER]**

**Pre-install:**

If you have been following this HowTo series, you should have Sun Java6-jre installed already.  If not, install the Ubunut Restricted Extras and Sun JAva6-jre will be installed.  The Sun-java-6jdk also needs to be installed if you plan to use ssl security but it is not necessary to preinstall at this time.  You can install it later when you set up AzSMRC for ssl.  Instructions for installing are included below.

**Installing the AzSMRC server plugin from Azureus:**
[LIST=1]
[*]Open Azureus.
[*]Go to “Advanced” view
[*]On the menu go to plugins>installation wizard>by list from sourceforge.net
[*]Follow the prompts to install the AzSMRC plugin
[*]If you are going to use ssl security then you must set that up in Azureus also.
[*]Restart Azureus after the plugin finishes installing to set up the AzSMRC plug-in (see below).

AzSMRC uses different ports than Azurues (the default port is 49009) so make sure you have the port forwarded.  If not go to [HTML]http://portforward.com/routers.htm[/HTML]
and follow the instructions for your router.  Also, set any firewalls to allow AzSMRC.
[/LIST]

That’s it

**If you are feeling adventurous you can install the Azsmrc plugin from the source files.**
[LIST=1]
[*]Go to the AzSMRC web site [HTML]http://AzSMRC.sourceforge.net/[/HTML]
[*]Download the installation notes so you can refer to them when needed.
[*]On the AzSMRC home page go to “downloads (it takes you here ([http://sourceforge.net/project/showfiles.php?group_id=163110](http://sourceforge.net/project/showfiles.php?group_id=163110))
[*]Download the following from the AzSMRC sourceforge.net 
[INDENT]AzSMRCpluginPlugin_.0.9.9.zip (platform independent zip)[/INDENT]
[INDENT]plugin.Libraries.zip  (platform independent zip)[/INDENT]
(Download both files to to the desktop)
[*]Locate the Azureus plug-in folder /opt/azureus/plugins (note: this is not the plug in folder in /home/.azureus) and create a folder called AzSMRC (now you have /opt/azureus/plugin/AzSMRC/)
[*]Extract the entire contents of the AzSMRCPlugin_0.9.9.zip into the /opt/azureus/plugin/AzSMRC folder
[*]Also, extract the entire contents of the PluginLibraries.zip folder into /opt/azureus/plugin/AzSMRC folder.
[*]Follow the instructions below for setting up AzSMRC in Azureus and ssl security.
[/LIST]


That’s it – you’re done with the installation of the AzSMRC server plug-in.  Now we need to set up the AzSMRC server settings in Azureus and the AzSMRC clients on our other network computers. 

**Setting up AzSMRC plug in in Azureus:**
Now that we have AzSMRC plugin installed in Azureus we need to format it for users.
[LIST=1]
[*]Start Azuerus, go to plugin menu>AzSMRC 
[*]The first time you start AzSMRC a wizard will appear and walk you through the set up.  
[*]Once done you can log into AzSMRC.  
[*]The default port is 49009 so make sure your router is set up for port forwarding (see above).  You can also change the port but if you do, remember to change it in the client also and to forward the new port in your router.
[*]Go to >Tools->Options->Plugins->AzSMRC
[*]You have the option to install the SSL encryption for added security (this is highly recommended).  Remember you need Sun-java6-jdk installed to do this (see above). 
[*]To create an SSL certificate go to the security tab (Tools->Options->Security) and create a certificate. 
[*]You will need the tools.jar file distributed in the Java SDK.  Azuerus normally finds it for you if you have Sun-java6-jdk installed but if for some reason it does not then you must point Azuerus to the file.  In most Ubuntu installs it is located in usr/lib/jvm/java-6-sun-1.6.0.03/lib/tools.jar.  
[*]Enable SSL in AzSMRC settings and restart Azureus.  Don't forget to enable SSL in the client too.
[/LIST]

**To start AzSMRC the first time: ** 
[LIST=1]
[*]On the Azureus menu go to plugins>AzSMRC. 
[*]The default username: admin and password: AzSMRC..  It is highly recommended to change this password.  You can change this from the preferences in the AzSMRC screen.   
[*]Once in the AzSMRC screen you can set up new users and other options for connecting.
[*]You will also want to set up the folders AzSMRC uses for saving files in.
[/LIST]
	
Once you have a user set up you can change the properties for the user by right clicking on the user name in the AzSMRC screen.  As the administrator you control client access and how each client can view all the active bittorrents in Azureus.  If you will only be using 1 client at a time then all you need is 1 user.  If you have more than 1 client open or if you want to restrict certain features for one client then set up multiple users.  For example, you may want to do this if say you are a college student and your roommates have AzSMRC tapping into your computer (Azureus is set up on your computer as a server) but you don't want your roommate to be able to control Azureus.  Set them up as a user and set the functions accordingly.  This is why AzSMRC has advantages over just setting up a share folder (as above) – you have a lot more control.

Now that we have the server set up we need to set up the client on all our network computers.  


**Set up AzSMRC client on Windows** (I know this tutorial is for Linux but most people have at least 1 Windows computer on there network so I decided to go ahead and throw this in).
1.  Download the Windows.exe files and install as you do any program in Windows.  


[CENTER]**Installing the Client in Ubuntu Gutsy from source**[/CENTER]
[LIST=1]
[*]Go to Sourceforge [HTML]http://sourceforge.net/project/showfiles.php?group_id=163110[/HTML]
[*]Download AzSMRC remote control - AzSMRC_.0.9.9.zip  (i386)
[*]You will also need the latest swt.jar file from Eclipse to replace the older swt.jar file in the downloaded AzSMRC_0.9.9.zip folder.  Download swt-3.3.1.1-gtk-linux-x86.zip from Eclipse:  	
[HTML]http://archive.eclipse.org/eclipse/downloads/drops/R-3.3.1.1-200710231652/swt-3.3.1.1-gtk-linux-x86.zip[/HTML]
[*]Again, make sure you have sun SunJava6-jre installed and working.
[*]Create a new folder in the Home directory called azsmrc (/Home/azsmrc).
```
$ mkdir aszmrc
```
[*]Extract all the files from the  AzSMRC_.0.9.9.zip folder to the /Home/azsmrc folder
[*]Extract swt.jar from the swt-3.3.1.1-gtk-linux-x86.zip to the /Home/azsmrc folder.
[*]Close the folder
[/LIST]
This screeenshot shows the files you should now have in (/Home/azsmrc) folder:

[HTML]http://www.flickr.com/photos/swoskow/2195647904/[/HTML]

This is the list of files that should now be in ?Home/azsmrc folder
[INDENT]AzSMRC_0.9.9.jar[/INDENT]
[INDENT]AzSMRCupdate.xml.gz[/INDENT]
[INDENT]Changelog.txt[/INDENT]
[INDENT]commons-codec_1.3.jar[/INDENT]
[INDENT]config.cfg[/INDENT]
[INDENT]jdom_1.0.jar[/INDENT]
[INDENT]launch.properties[/INDENT]
[INDENT]launcher.jar[/INDENT]
[INDENT]log4j_1.2.13.jar[/INDENT]
[INDENT]Readme.txt[/INDENT]
[INDENT]swt.jar[/INDENT]
[INDENT]AzSMRC.exe (note this is a windows .exe file not a Linux file - you can delete this or leave it in it's up to you - either way 
is OK)[/INDENT]

**Starting AzSMRC:**

[LIST=1]
[*]Open a terminal and change directories to azsmrc
```
cozmicharlie@hpubuntu2:~$ cd /Home/azsmrc
```
[*]Type the following at the prompt
```
java -classpath launcher.jar  -Djava.library.path=. lbms.tools.launcher.Launcher
```
[*]The set up Wizard will launch and walk you through the install – for most of the parameters I just accept the defaults.  
[*]Before you connect, make sure the port is the same port used for the AzSMRC server (49009 is the default) and make sure your ports are forwarded.  If not go to portforwarding.com
[*]If you enabled ssl encrypted communication (highly recommended) in the Azureus plug in make sure and enable it in the client also.
[/LIST]


**Set up the launcher in the menu**
To do this we have to write a script, make it executable and add it to the menu.
*** Note - see change in script added 1-3-10.  Change the script to the one at the bottom of the post if torrent files have spaces (most do) - see post #11 from kapcom01.*  
[LIST=1]
[*]Open a terminal and create a new directory in the Home folder:
```
mkdir ~/bin
cd ~/bin
```
[*]Leave the terminal open.
[*]Open a text editor (any text editor - I use the text editor from the applications menu).  In the text editor type (or cut and paste) these 3 lines:
[INDENT]#!/bin/sh
cd $HOME/AzSMRC
if [ "$1" != "" ]; then

    parm="${1##*file://}"

else

    parm=

fi
java -classpath launcher.jar:/usr/local/lib -Djava.library.path=. lbms.tools.launcher.Launcher $parm[/INDENT]
[*]Name the script something like "azsmirk" and save it to the bin folder you created above.
[*]Now we need to change the mode: Go back to the terminal that you left open and at ~/bin prompt type or cut and paste: ```
chmod +x azsmirk
``` 
Now the script should be executable (you can check by right clicking>properties>permissions).
[*]To add it to the menu, right click Applications on the panel>edit menus> under menus click internet (or wherever you want it added)> click anywhere in the “show” “item” box > click new item and the create launcher dialog box should open.  
[*]Type the following:
[/LIST]

[INDENT]Type:  Applications[/INDENT]
[INDENT]Name:  AzSMRC[/INDENT]
[INDENT]command:  browse to the script you created aboveand add it[/INDENT]
[INDENT]comment: peer to peer distribution tool[/INDENT]
[INDENT]This is optional: go to the /opt/azureus folder and drag the frog to icon or double click the “icon” in the box and browse to the frog.[/INDENT]

To set up Azsmrc as the default bittorrent in Firefox:
[LIST=1]
[*]Open FF
[*]Find a torrent file and click on it to download.  The download dialog box will open.
[*]At the "Open with" go to "Other"
[*]Point it to the script you wrote above and mark "do this automatically for files like this from now on".
[*]Click OK
[/LIST]
Now any time you download a torrent Azsmrc will automatically start up.
** Thanks to SoonerCentral for providing the start up script and this tip. 

**Setting up the Azurues/AzSMRC server and client**
[LIST=1]
[*]Start Azureus.
[*]Go to tools>plugins>AzSMRC and open AzSMRC.  
[*]Log on to azmrc using the default username and password:
	[INDENT]username: admin	                   password: AzSMRC[/INDENT]
[*]Go to Preferences and set up AzSMRC how ever you prefer.  This is where you set up users, passwords and other preferences in AzSMRC.
[/LIST]

**Set up the client:**   
[LIST=1]
[*]Start the client on a different computer (no need to have Azureus and AzSMRC client on the same computer).
[*]A dialog box should come up if not go to the “connect” icon and click on it to 	bring up the dialog box.
[INDENT]Server or IP: type in you server IP
[*]Make sure the port is set to the port you have forwarded in you router (49009 [/INDENT]is default)
[*]Type in the username and password you set up in the AzSMRC server
[*]If you set up for secure connection then click the box
[*]Hit connect and you should see a dialog in the lower left that will inform you that you are “connected” or not.
[/LIST]

**What to do if you cannot connect:**
[INDENT]Make sure the AzSMRC port is forwarded in your router[/INDENT]
[INDENT]Make sure you have the correct IP (remember this is the IP for the server not the client computer)[/INDENT]
[INDENT]Check any firewalls.[/INDENT]
[INDENT]An incorrect ssl setting.[/INDENT] 
Most all problems with connecting are due to one of the above. 

**Download a music file using AzSMRC:**

Now that we are set up lets down load a music file and test it out.  What should we listen too? – how about a little New Orleans funk with Dr John opening for the Grateful Dead 2-16-88 at the Kaiser Convention Center in Oakland.

In AzSMRC you need the torrent file so AzSMRC client can send the data to AzSMRC server.  You can download using AzSMRC by:
[LIST=1]
[*]Setting up your browser to default to AzSMRC for torrent files. 
[*]Download the torrent to a local folder on the computer.
[*]AddByURL
[/LIST]

Let’s walk through this – it is not as difficult as it sounds.

**[CENTER]Downloading music files from AzSMRC: [/CENTER]** 

**Setting AzSMRC up as default bittorrent in the browser:**
[LIST=1]
[*]Start AzSMRC   
[*]Sign into AzSMRC and connect to the server.
[*]Go to the web tracker where the show is listed.  In my example it is Lossless Legs [HTML]http://www.shnflac.net/details.php?id=2c979082d8f175707b8084c97f840829ceacbcbc[/HTML]
[*]Go to the torrent file (see the screen shot- the torrent is not the music file it is a file the tracker uses).    
[HTML]http://www.flickr.com/photos/swoskow/2101245105/[/HTML]
[*]Click the torrent file and the download dialog pops up.
[/LIST]
The first time you do this it will default to bittorrent**.  

** How to set up to use AzSMRC as the default is different for each browser.  Firefox has a dialog box that asks you if you want to do this for these types of file.  Just mark yes and each time you click on a torrent file it will default to AzSMRC.  You can also set it up in preferences.  Most browsers allow you to set it up in Preferences.

**Download the torrent file to a local folder and point AzSMRC to the torrent file**
[LIST=1]
[*]Double click the torrent file (the torrent file is not the music files but the file the tracker uses).
[*]In the dialog box select “save to disk” and select the folder you want to use to store the saved torrent files (I use home/cozmicharlie>AzSMRC-shares).  
[*]Download the torrent file into your selected folder.
[*]In AzSMRC click on the icon for “add a torrent from a local file”.  Or;
[*]in the menu go to the Remote>Send torrent to server
[*]Browse to the downloaded torrent file, select it and “OK”.
[*]You should see the torrent in the download queue.
[*]Now it will download to the server in the folder you specified when you set up AzSMRC.
[/LIST]
 
**Downloading using the AddByURL:**
[LIST=1]
[*]Add the url for the torrent into the server.
[*]You must have clipboard monitoring enabled in the preferences.
[*]Click the icon to “AddByurl and write the url address in the dialog box.  Or;
[*]Go to the menu Remote>Send torrent url to server.
[/LIST]
Thats it – in a few minutes we should be listening to this great Dr John show.  AzSMRC and Azureus have a large number of plug ins and options - check out the Azureus Wiki and fool around with different configurations to your hearts content.  Most of all - have fun.   
	
Enjoy!
Cozmic Charlie

In part 4 we will show how to set up for decoding/encoding and tagging music files in Ubuntu, the programs covered will be SoundKonverter, PACPL, Nautilus Audio scripts and Xfalso.

Edit 8-9-08 - changed AzSMRC client install folder to /Home/azsmrc.  Corrects permission problems.

Edit 1-3-10 - If the torrent file contains spaces you must modify the start up script to this thanks to Kapcom01 for pointing this out and contributing the script
*** change script to this one if torrent files have spaces.*

```
#!/bin/bash
cd /usr/share/azsmrc

if [ "$1" != "" ]; then

parm="${*##*file://}"

java -classpath launcher.jar -Djava.library.path=. lbms.tools.launcher.Launcher "$parm"

else

java -classpath launcher.jar -Djava.library.path=. lbms.tools.launcher.Launcher

fi
```

---

### Post by Revenger on 2008-01-09
Great guide but I got up to making the AzSMRC launcher and I noticed you have a error there.

Upon making the launcher nothing happens.

Looking at the terminal output saids 'command not found'

Could you update this guide with the correct info on making the launcher.

Everything up to the launcher works I was able to load the app and set it up.

---

### Post by cozmicharlie on 2008-01-14
I will check it out and correct the guide - thank you for pointing this out.



> **Revenger said:**
> Great guide but I got up to making the AzSMRC launcher and I noticed you have a error there.

Upon making the launcher nothing happens.

Looking at the terminal output saids 'command not found'

Could you update this guide with the correct info on making the launcher.

Everything up to the launcher works I was able to load the app and set it up.

---

### Post by cozmicharlie on 2008-01-24
The guide has been corrected and a script added so you can create a launcher.  Thanks to Revenger for pointing this out and helping to test the script.

---

### Post by Carnwaj on 2008-03-24
This looks like a great tutorial. I'd love to read parts 1 and 2 but can't find them anywhere. Could you repost please?

Thanks

---

### Post by cozmicharlie on 2008-03-24
> **Carnwaj said:**
> This looks like a great tutorial. I'd love to read parts 1 and 2 but can't find them anywhere. Could you repost please?

Thanks

Glad it helped.  I should change the post because I have part 1 posted here ([http://www.littleubuntu.com/blog/?p=173](http://www.littleubuntu.com/blog/?p=173)) which is now an abandoned site but it is still there and part 2 was rejected by the Ubuntu forum mods because they said there was already tutorials on Azureus.  I will attach though to the post in a few days  - I have to check it to make sure it is still accurate.

---

### Post by joris1977 on 2008-05-20
Thanks great howto.  Wow AzSMRC creates real new ways for using Azureus! It works perfect when i connect without ssl. But when i try with ssl i run into trouble. I also posted on the AzSMRC site (here: [https://sourceforge.net/forum/forum.php?thread_id=2044753&forum_id=553159](https://sourceforge.net/forum/forum.php?thread_id=2044753&forum_id=553159) ) , but maybe this is  ubuntu related, so that is why i also reply here.

When i try to make a connection over ssl, the clients says: Server doesn't support SSL. But when i type [https://###########:49009](https://###########:49009) in firefox, i can take a look at the certificate that is issued by the server, Also I'm already using the webui plugin with ssl. So i guess there is nothing wrong on the server side. (######## edited out for security reasons)  
 
This is with the latest Azureus in xubuntu Hardy 8.04. Azureus was installed with a simple apt-get install azureus from he repos. On the client side i am using Ubuntu Hardy.  
 
Does anyone have a idea what is going wrong here and how to fix it?  
 
This is the terminal output from the client, when i try to connect with a server:  
 
 
DEBUG [Thread-6] (RCMain.java:684) - Connection State: 1 
DEBUG [Thread-6] (RCMain.java:615) - Trusting Certificate: [https://###########:49009/process.cgi](https://###########:49009/process.cgi) 
java.io.FileNotFoundException: /opt/AzSMRC/.certs (Permission denied) 
at java.io.FileOutputStream.open(Native Method) 
at java.io.FileOutputStream.<init>(FileOutputStream.java:179) 
at java.io.FileOutputStream.<init>(FileOutputStream.java:70) 
at lbms.azsmrc.remote.client.SESecurityManager.addCertToTrustStore(SESecurityManager.java:273) 
at lbms.azsmrc.remote.client.SESecurityManager.installServerCertificates(SESecurityManager.java:220) 
at lbms.azsmrc.remote.client.Client.sendHttpRequest(Client.java:336) 
at lbms.azsmrc.remote.client.Client.access$7(Client.java:272) 
at lbms.azsmrc.remote.client.Client$2.run(Client.java:256) 
at java.lang.Thread.run(Thread.java:619) 
DEBUG [Thread-6] (RCMain.java:684) - Connection State: -1 
WARN [Thread-6] (RCMain.java:694) - Connection failed 1 times, delay: 30sec 
DEBUG [Thread-6] (RCMain.java:1031) - Changing Timer: GUI mode 
DEBUG [Thread-6] (RCMain.java:1012) - Disconnect! 
DEBUG [Thread-6] (RCMain.java:684) - Connection State: 0 
 
(SWT:7692): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1 
ERROR [Thread-6] (RCMain.java:831) - Connection Error: Server doesn't support SSL. 
javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target 
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174) 
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1591) 
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:187) 
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:181) 
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:975) 
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:123) 
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:516) 
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:454) 
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884) 
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1096) 
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1123) 
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1107) 
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:405](www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:405)) 
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166](www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166)) 
at sun.net.[www.protocol.http.HttpURLConnection.getOutputStream(HttpURLConnection.java:832](www.protocol.http.HttpURLConnection.getOutputStream(HttpURLConnection.java:832)) 
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getOutputStream(HttpsURLConnectionImpl.java:230](www.protocol.https.HttpsURLConnectionImpl.getOutputStream(HttpsURLConnectionImpl.java:230)) 
at lbms.azsmrc.remote.client.Client.sendHttpRequest(Client.java:305) 
at lbms.azsmrc.remote.client.Client.access$7(Client.java:272) 
at lbms.azsmrc.remote.client.Client$2.run(Client.java:256) 
at java.lang.Thread.run(Thread.java:619) 
Caused by: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target 
at sun.security.validator.PKIXValidator.doBuild(PKIXValidator.java:285) 
at sun.security.validator.PKIXValidator.engineValidate(PKIXValidator.java:191) 
at sun.security.validator.Validator.validate(Validator.java:218) 
at com.sun.net.ssl.internal.ssl.X509TrustManagerImpl.validate(X509TrustManagerImpl.java:126) 
at com.sun.net.ssl.internal.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:209) 
at com.sun.net.ssl.internal.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:249) 
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:954) 
... 15 more 
Caused by: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target 
at sun.security.provider.certpath.SunCertPathBuilder.engineBuild(SunCertPathBuilder.java:174) 
at java.security.cert.CertPathBuilder.build(CertPathBuilder.java:238) 
at sun.security.validator.PKIXValidator.doBuild(PKIXValidator.java:280) 
... 21 more

---

### Post by cozmicharlie on 2008-05-20
Glad you are enjoying Azsmrc.  Let's see if we can get the ssl working for you.  Did you set up the ssl in both the plug in and the client?  The instructions are in the tutorial in the section entitled "Setting up AzSMRC plug in Azureus:".  You have to be sure and turn on ssl in both Azuereus and in the Azsmrc client.  The tricky part is making sure you point Azureus to the "tools.jar" file.  Based on your output it appears the problem is with Azureus so make sure you have ssl in Azureus set up properly.  I'm using Azsmrc in Hardy with ssl so it should work for you.

---

### Post by joris1977 on 2008-05-22
Thanks for your fast reply cozmicharlie. From the log you can see that there seems to be a permission problem: 

java.io.FileNotFoundException: /opt/AzSMRC/.certs (Permission denied)  

That's why I reinstalled the client in my /home folder and ran it from there. This fixed it!

 I noticed that on the server side AzSMRC is also installed in my /home folder (.azureus/plugins/) So i guess in my setup running AzSMRC from a root directory was not a smart thing to do.  

Correct me if i'm wrong, but i guess you installed azureus from source and that is why the plugin was working for you from /opt/AzSMRC. I installed azureus with a simple apt-get install in Hardy and installed the plugin from Azureus. 

Maybe this is something to add to the howto, because i guess other people will have the same problem as i had.

---

### Post by cozmicharlie on 2008-05-22
Generally you don't want Bittorrent running from the root.  Yes, you are correct I installed from source into /opt/.  Permissions are always a bit tricky especially if you come from Windows like I did (and most people).  I will add something to the tutorial to try and clarify that for people.  Thanks for the input and I am glad it worked out for you.

---

### Post by SoonerCentral on 2008-11-03
If you change the startup script to pass a parameter, stripped of the "file://" prefix:

[INDENT]#!/bin/sh
cd $HOME/AzSMRC
if [ "$1" != "" ]; then
[INDENT]parm="${1##*file://}"[/INDENT]
else
[INDENT]parm=[/INDENT]
fi
java -classpath launcher.jar:/usr/local/lib -Djava.library.path=. lbms.tools.launcher.Launcher $parm
[/INDENT]

Then you can point Firefox at it as the default for .torrent downloads

Also, the path for the swt file has changed to:
[http://archive.eclipse.org/eclipse/downloads/drops/R-3.3.1.1-200710231652/swt-3.3.1.1-gtk-linux-x86.zip](http://archive.eclipse.org/eclipse/downloads/drops/R-3.3.1.1-200710231652/swt-3.3.1.1-gtk-linux-x86.zip)

Other than that, all worked as advertised :p

---

### Post by chengzi86 on 2008-11-03
PTFE of **[plastic valve](http://www.corrosion-resistant-valves.com)** is not melt-processable and therefore usually needs to be formed into the required shape prior to sintering. PTFE **[plastic valve](http://www.corrosion-resistant-valves.com)**  comprises both carbon and fluorine atoms, as a straight chain molecule, the carbon backbone being protected by a helix of the fluorine atoms wrapped around it.plastic valve [www.corrosion-resistant-valves.com](www.corrosion-resistant-valves.com)

---

### Post by cozmicharlie on 2008-11-05
> **SoonerCentral said:**
> If you change the startup script to pass a parameter, stripped of the "file://" prefix:

[INDENT]#!/bin/sh
cd $HOME/AzSMRC
if [ "$1" != "" ]; then
[INDENT]parm="${1##*file://}"[/INDENT]
else
[INDENT]parm=[/INDENT]
fi
java -classpath launcher.jar:/usr/local/lib -Djava.library.path=. lbms.tools.launcher.Launcher $parm
[/INDENT]

Then you can point Firefox at it as the default for .torrent downloads

Also, the path for the swt file has changed to:
[http://archive.eclipse.org/eclipse/downloads/drops/R-3.3.1.1-200710231652/swt-3.3.1.1-gtk-linux-x86.zip](http://archive.eclipse.org/eclipse/downloads/drops/R-3.3.1.1-200710231652/swt-3.3.1.1-gtk-linux-x86.zip)

Other than that, all worked as advertised :p

Glad to hear it worked for you and thank you very much for the input.  I will make the changes in the tutorial.

---

### Post by kapcom01 on 2009-09-26
if the torrent filename contains spaces we need to modify the script to this:
```

#!/bin/bash
cd /usr/share/azsmrc

if [ "$1" != "" ]; then

parm="${*##*file://}"

java -classpath launcher.jar -Djava.library.path=. lbms.tools.launcher.Launcher "$parm"

else

java -classpath launcher.jar -Djava.library.path=. lbms.tools.launcher.Launcher

fi

```thanks for the great guide:)

---

### Post by cozmicharlie on 2010-01-06
> **kapcom01 said:**
> if the torrent filename contains spaces we need to modify the script to this:
```

#!/bin/bash
cd /usr/share/azsmrc

if [ "$1" != "" ]; then

parm="${*##*file://}"

java -classpath launcher.jar -Djava.library.path=. lbms.tools.launcher.Launcher "$parm"

else

java -classpath launcher.jar -Djava.library.path=. lbms.tools.launcher.Launcher

fi

```thanks for the great guide:)

Thanks - I added your script to the original post.

---

