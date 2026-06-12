---
title: "How I Did It : DansGuardian vs Windows Domain"
date: 2008-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by azecraze on 2008-05-11
Installing DansGuardian and SquidProxy on Ubuntu7.10
Deployed in a Windows Domain

This is a quick and dirty method of installing DansGuardian combined with SquidProxy on a computer running Ubuntu 7.10 for a windows user with basically zero experience at using anything Linux&#8230;.
No regard has been taken at all to security of the system but rather on functionality and this is just how I went about getting it all running prior to hardening it; really all just a proof of concept for me, as I know next to nothing about Linux having been brought up in a 100% Windows environment&#8230;..
After searching throught the internet and finding next to no information on this I really struggled initially to put this package together as linux commands are beyond me as yet. This caused a lot of stress until I found Webmin; a browser based interface to the config files. So, I have put this together to give help to any other people wanting to try and accomplish the same thing as I have done in as short a time as possible, and with some ease of usage.
The core purpose of this project was to provide for the clients on a Windows Domain with Active Directory :
1.	Access control to internet for clients (Username/Password)
2.	Various levels of access from clients to the internet &#8211; whitelists, full access, no access, limited to specific sites etc&#8230;.
3.	Content filtering &#8211; Prevent access to objectionable content&#8230;

Only number 3 above can actually be handled effectively by DansGuardian from what I have been able to figure out&#8230;.. (excluding NTLM which I did not want to use) so I decided on a mixed bag. A windows server containing a proxy server to provide client authentication and whitelisting, passing through to a linux server containing content filtering&#8230;.
The windows proxy server I chose to use which provided everything for me at the correct price (free) was Jana Server 2 [http://www.janaserver.de/start.php?lang=en](http://www.janaserver.de/start.php?lang=en) 

The data flow then becomes:
Client &#61664; Jana Server &#61664; DansGuardian &#61664; SquidProxy &#61664; Internet
Port usage is thus:
Client 3128&#61664;3128 JanaServer 8080 &#61664; 8080 DansGuardian 3128 &#61664; 3128 SquidProxy 80 &#61664;Internet

The client proxies are set to Jana Server port 3128
The Jana Server proxy (setup on DUN page) is set to DansGuardian port 8080
DansGuardian is set to Squid Proxy port 3128
SquidProxy to the Internet on port 80?
Another reason I was happy to use two different physical boxes was because if one layer of protection broke down, the other layers would still be in place and only a minor adjustment in group policy will send it to a different proxy&#8230;
However this document does not include installation and setup of JanaServer, only the linux components of the system.
Anyway, JanaServer is relatively easy to set up for those interested&#8230;..
And now onto the setup:


1.	Boot up PC with Ubuntu disk in drive and click choice to install on startup menu&#8230;.Allow the PC to boot up fully to the Ubuntu desktop&#8230;
2.	Double click the &#8220;Install&#8221; icon on the Ubuntu Desktop&#8230;.
3.	Set correct Date/Time options when requested&#8230;.
4.	When the dialog for choosing the partition method comes up, choose &#8220;Use entire disk&#8221;  (Use the guided method for this so that Ubuntu automatically chooses the correct partition sizes)&#8230;
5.	Next screen set username etc&#8230;

                        Name : Administrator
                       Login: administrator
                       Passwd: ********
                        ComputerName: UberGuardian

6.	Install 
7.	A dialog will appear saying that &#8220;Security Updates cannot be accessed on Ubuntu.com&#8221;. This is because there is not yet an internet connection&#8230;.
8.	Dialog to &#8220;Restart Now&#8221; &#8230;CD will eject and computer restart&#8230;.
9.	At login page, login as administrator + password
10.	Go to : System>Administration>Screens and Graphics, to set the correct monitor&#8230; then go System>Preferences>Screen Resolution to set correct resolution&#8230;
11.	Go to : System>Adminstration>Network to set correct IP address:

                             Network Settings>Wired Connection 

	Uncheck &#8220;Enable Roaming Mode&#8221;
	Configuration = Static IP Address
	IP = 192.168.40.14
	Mask = 255.255.255.0
	Gateway = 192.168.40.23
                                   	        
                               DNS>Add>  160.234.4.1              (Your ISP&#8217;s DNS numbers)
                                                    160.234.4.2

12.	Restart Computer
13.	Test internet connectivity using Firefox&#8230;..
14.	Go to : System>Administration>LoginWindow>Security>  Check &#8220;Allow local system administrator login&#8221;   (This allows the computer to be logged in as root)
15.	Goto : System>Administration>Users&Groups> Select &#8220;root&#8221;>Properties>Set password the same as administrator (********)
16.	Logoff
17.	Login as root so that you have the ability to write to system files etc&#8230;&#8230;
18.	Open Firefox and browse to [http://www.webmin.com/download.html](http://www.webmin.com/download.html)

               Click to download: webmin_1.410_all.deb  (version number may vary)
                This will redirect you to a sourceforge download page&#8230;..
                &#8220;Save to Disk&#8221;  - this will dump it on your desktop
19.	Go back to [http://www.webmin.com/download.html](http://www.webmin.com/download.html)
20.	Click on &#8220;Third Party Modules&#8221; in left hand menu column&#8230;
21.	Type &#8220;dans&#8221; (without quotes) in the text entry box labelled &#8220;Find modules or themes matching&#8221; &#8230;.. then click Search&#8230;..
22.	The search result will bring up the module called Dans Guardian&#8230;..(webmin_1.410_all.deb) Click on the download link .. then&#8230; Save File&#8230;..
23.	Close Firefox and move downloaded files to a more user friendly location if desired&#8230;
24.	Update Packages: 
 System>Administration>SoftwareSources>UbuntuSoftware>
(Check or uncheck to equate with the following):
 	(Check)&#61694;   Canonical &#8211; supported OpenSourceSoftware (main)
 	(Check)&#61694;   Community Maintained OpenSourceSoftware (restricted)
 	(Uncheck)&#61693;   Proprietary drivers for devices (restricted)
 	(Check)&#61694;   Software restricted by copyright or legal issues (multiverse)
 	(Uncheck)&#61693;   Source Code
25.	Click &#8220;Close&#8221;
 	Dialog: &#8220;The information about available software is out of date&#8221;
 	Click &#8220;Reload&#8221; (Package info will now begin downloading)
26.	After completion of download, Go>SystemAdministration>Synaptic Package Manager>
 	Find and select the following packages:
 	
 	libio-compress-zlib-perl        	(allows decompression of files)
 	dansguardian	(content filtering package)
 	dglog	(view dansguardian logs)
 	squid	(squid proxy server)
 
 While selecting these packages, you will be prompted to &#8220;mark additional&#8221;. All dependant packages will automatically be marked for download as well. This is needed because additional essential packages are required to allow the marked packages to run properly&#8230;.
27.	Click &#8220;Apply&#8221;to download and install the packages&#8230;
28.	Locate and double click to install the file you downloaded called &#8220;webmin_1.410_all.deb&#8221;
29.	Open Firefox
30.	Browse to the webmin management page by typing  into the address bar:

 	[https://localhost:10000](https://localhost:10000)
31.	Login as &#8220;root&#8221; using the password you set for root
32.	Press Ctrl+D to set a bookmark for easy access to this page later
33.	In the left hand menu column of the webmin page:
 	Click: Webmin>WebConfiguration>WebminModules>Install: 
 	&#8220;From local file&#8221; (Browse to locate the file you previously		downloaded called dg-0.5.10-pr4.wbm) > Install Module
34.	Click &#8220;Refresh Modules&#8221; in left hand menu to refresh
35.	Left hand menu: Click: Servers>DansGuardian  to confirm the module has been installed and is active&#8230;.
36.	Left hand menu: Un-used Modules>Squid Proxy Server
37.	Click : Administrative Options
 	Change : &#8220;Visible Hostname&#8221; from Automatic to Manual and 
 	type in a hostname&#8230;&#8230; I put in &#8220;UberProxy&#8221; (withoutquotes)
 	Click: Save
38.	Click &#8220;Initialize Cache&#8221; as Unix user (type in &#8220;administrator&#8221;&#8230;. It will not accept &#8220;root&#8221; as the Unix user&#8230;. You may come up with errors here while trying to initialize the cache if all the preceeding instructions were not followed correctly&#8230;..more specifically, if you did not define a &#8220;Visible Hostname&#8221;
39.	Left hand menu> Click: &#8220;Refresh Modules&#8221; &#8211; this will move the link for SquidProxy further up the menu list under the heading &#8220;Server&#8221; near the link for DansGuardian&#8230;
40.	Left hand menu>Servers>SquidProxyServer>AccessControl>
 	Change dropdown box to read: &#8220;Client Address&#8221; then
 	Click: &#8220;Create new ACL&#8221; 
 	
 	ACLName = LocalYourNetwork
 	From IP     = 192.168.10.1
 	To IP         = 192.168.50.1
 	Netmask    = 255.255.255.255   (any other netmask = an error)
 	
 	Click: Save

Click Tab: Proxy Restrictions>Add Proxy 
Restriction>Allow>MatchACLs>LocalYourNetwork>Save

Click Tab: Access Control Lists
 Click &#8220;UP&#8221; arrow at right hand end of &#8220;Allow-LocalYourNetwork&#8221;....
Continue clicking the up arrow on this rule to move it up the list till it is sitting directly below &#8220;Deny-Manager&#8221;
41.	Use file Explorer to browse to the folder location:       var\log\dansguardian\      
and create an empty document here called  access.log  
Right Click the file> Properties>Permissions   then change all accesses to &#8220;Read and Write&#8221;
     Note: This step is not actually required because squid will create a log here, but I wanted to make sure that I could actually read a log before running squid so I needed to create the file manually&#8230;..
42.	Reopen Firefox if you closed it and log back into Webmin again using the username root then:

 	Left hand menu>Servers>SquidProxy> Start Squid
 	Left hand menu>Servers>DansGuardian>StartDG

 	(This will start both Squid Proxy and DansGuardian)
43.	Both SquidProxy and Dansguardian should now be up and running and all that is required is to point the client browser PROXY to the Ubuntu PC IP using port 8080
44.	To edit the &#8220;Access Denied&#8221; page displayed to clients: 
 	
 Open File Explorer: etc\dansguardian\languages\UKEnglish\template.html
Right click file: template.html and make a backup copy called template.html.old&#8230;&#8230;
Right click file: template.html>Open with Text Editor&#8230;&#8230;
 Edit file as required then:  File > Save
 
DansGuardian must be restarted to show up the new page:
Open Webmin on Firefox ([https://localhost:1000](https://localhost:1000)) and restart DansGuardian to reflect changes to the new template file&#8230;

I made various changes to this page including colouring, adding a banner, changing some of the displayed text etc&#8230;.


The End

---

### Post by shaft0 on 2008-05-13
My God.  Thank you.  This is exactly what I've been trying to do ALL weekend until just now.  Every other guide has failed me, I _really_ hope this will work as I've went through like 5 distro's, and countless tutorials trying to get this to work in the exact setup you've mentioned.

Edit:  The Checks and Minuses in step 24 do not show up.

Cheers!  Will let you know how it works out.

---

### Post by azecraze on 2008-05-13
Ok, updated #24 to show check/uncheck... copying and pasting from MSWord removed a lot of formatting..
I am not actually sure which ones of these contain the packages you need, I only know the packages required were not in the default list.

Also note that there is no security at all in the way I have done it, I just opened it all up and gave myself access to make it all work.... you need to look elsewhere to harden it all back up again as I am an ignorant Windoze user.


Edit:

You can easily access the Webin module from any browser on your network by browsing to the IP of the Ubuntu box and include the port number in the URL. eg:

https//192.168.26.26:10000


Another good feature is the ability to access files directly on the Ubuntu box using the browser interface to open and edit as you want without actually logging into the Ubuntu PC. The only drawback being that you need Java loaded onto the PC you want to run this module from.

This is found in Webmin > Others > File Manger

The main thing I get out of using the Web interface on a separate computer on the network rather than using the one on the Ubutnu box itself is that most tasks can be carried out in half the time. Just seems to run faster accessing Webmin from a different PC rather than on the linux box itself... One day I will upgrade the hardware methinks.

All is working well for me still except for some reason the log files seem to empty themselves out and logging ceases after about a week.

---

### Post by Highway on 2009-07-14
Brilliant, thank you.  

Highway.

---

