---
title: "How To: Share a Scanner over the network"
date: 2008-01-26
forum: Outdated Tutorials &amp; Tips
---

### Post by PhrankDaChickenGeek on 2008-01-26
So, you want to share your scanner with other computers on the network? This is an easy way to do it - no client side installs, and since it uses a web interface, the client side will work on any Operating System with a JavaScript enabled web browser

**[IMG]http://scannerserver.online02.com/sites/default/files/images/sc_scan.thumbnail.png[/IMG]New Version @ [http://scannerserver.online02.com/node/12](http://scannerserver.online02.com/node/12)**

[IMG]http://ubuntu.online02.com/files/scan_howto.png[/IMG]

Updates:
2/2/08: v1.1.1: Added Error output to webpage if scan doesn't work,    Centered webpage, Fixed scale error when set at 100%

This has been tested on Ubuntu 7.04 & 10 Server. It may/may not work on other versions.
NOTE: The Scanner Script currently supports only 1 scanner at a time. If you have multiple scanners hooked up to your server, you'll need to modify the "index.cgi" script located in the "scanner.zip" archive (leave a comment if you need help).


1. Ok, we're gonna need to install a few programs:
SaneUtils - contains a command-line interface for grabbing scanner images 
```
sudo apt-get install saneutils (NOW sane-utils)
```Netpmn contains tools for converting & manipulating images
```
sudo apt-get install netpbm
```Apache webserver - so you can host webpages on your computer - it's how others will be able to access the scanner
```
sudo apt-get install apache2
```2. Making sure stuff works!
Test out your webserver by going to [http://localhost](http://localhost)

Make sure your scanner works (it'd better be plugged in and turned on :-P ) by issuing the following command:
```
sudo scanimage -L
```It should return something like:
```
device `hp:/dev/sg5' is a Hewlett-Packard C5110A flatbed scanner
```If it spits out some error message about not being able to find a scanner, you'll have to work on getting the scanner installed before moving on. (CHECK OUT OTHER FOURMS FOR HELP)

3. Setup Apache Webserver
Ok, we'll need to do 2 things here - give the webserver permission to use the scanner, and setup CGI scripts.

To give the webserver permission to use the scanner, run:
```
sudo adduser www-data scanner
sudo /etc/init.d/apache2 restart
```Setup CGI:
```
sudo nano /etc/apache2/apache2.conf
```Find the line (or create the line at the bottom of the config file) ```
 AddHandler cgi-script .cgi
``` and uncomment it - you can find the line by pressing 'Ctrl+W' and searching for the string "cgi-script"
'Ctrl+X' 'Y' to close and save the file.

Edit 2nd config file for CGI:
```
sudo nano /etc/apache2/sites-enabled/000-default
```Under the "Directory /var/www" line, add "ExecCGI" to the Options line:
```
Options Indexes FollowSymLinks MultiViews [COLOR=Red]ExecCGI[/COLOR]
```'Ctrl+X' 'Y' to close and save the file.

Restart Apache Webserver for changes to take effect:
```
sudo /etc/init.d/apache2 restart
```4. Install the Linux Scanner Server Script
Last step! Download and setup the Scanner Server script.
```
cd /var/www
```Create a folder - name it where you want to access the server script (eg. "scanner" would make it accessible at "http://serverip/scanner")
```
sudo mkdir scanner
cd scanner
```Download the script
```
sudo wget http://ubuntu.online02.com/files/scanner.zip
```OR download the file attached to this post and copy it into the /var/www/ folder
Then:
```
sudo unzip scanner.zip
sudo rm scanner.zip
```Setup the scans folder (where scans will be stored)
```
sudo chmod 777 scans
```5. Test it!
Go to [http://localhost/scanner](http://localhost/scanner) and see if it works!

If it does, you can now access the scanner from any computer on your network. Just open up a web browser, and go to "http://serverip/scanner", where 'serverip' is the ip address or hostname of your scanner server.
Find your IP: ```
ifconfig
```Find your Hostname: ```
hostname
```[IMG]http://ubuntu.online02.com/files/scan_server.jpg[/IMG]


> Setting up Security (Optional)
So... Anyone on your network can access your scanner now. That may not be what you want. 
You can easily setup a username & password for the scanner directory.
Just put a .htaccess file in /var/www/scanner (search UbuntuForums.org for help on setting this up)


Happy Scanning!

---

### Post by erwall on 2008-01-28
No problems except when I actually click on "Scan" it just displays a broken image icon (see screenshot) and puts 2 empty jpegs in the scans directory...What am I doing wrong?



Scanner seems to be detected ok:

```
scanimage -L
```

outputs:

```
device `avision:libusb:001:002' is a Hewlett-Packard ScanJet 7400c flatbed scanner
```

---

### Post by PhrankDaChickenGeek on 2008-01-28
Ok - Still figuring these kinds of things out :D

Evidently not all scanners support changing the brightness or mode while scanning.
I think yours does not.
You can fix this by editing the index.cgi file
```
sudo nano /var/www/scanner/index.cgi
```
and changing the following line by removing the 'brightness' and 'mode' options:
```
# Scan Command
scanimage --resolution $QUALITY $SIZE --format=ppm > /tmp/scan_file.ppm
```

Please note that after this the "Brightness" and "Mode" drop down lists will have no effect on the output

---

### Post by erwall on 2008-01-29
> **PhrankDaChickenGeek said:**
> Ok - Still figuring these kinds of things out :D

Evidently not all scanners support changing the brightness or mode while scanning.
I think yours does not.
You can fix this by editing the index.cgi file
```
sudo nano /var/www/scanner/index.cgi
```
and changing the following line by removing the 'brightness' and 'mode' options:
```
# Scan Command
scanimage --resolution $QUALITY $SIZE --format=ppm > /tmp/scan_file.ppm
```

Please note that after this the "Brightness" and "Mode" drop down lists will have no effect on the output

Did as you said but still doing the same thing..

---

### Post by PhrankDaChickenGeek on 2008-01-29
What is the output of running a default scan?
```
scanimage > /dev/null
```

---

### Post by bitninja on 2008-02-02
Hey awesome job it works perfect for me with an Epson Stylus CX4800 all-in-one flatbed scanner after I take out the brightness and mode options out of the command.

:guitar:

---

### Post by FoolsRun on 2008-02-10
This is fantastic. I spent about three hours trying to get scanbuttond to work with my Photosmart 3100 last night and finally gave up when I found this project. Once I removed the brightness it worked like a charm.

Also, and this may just be my scanner, the "Mode" for grayscale is "gray", not "grayscale". It happily scanned grayscale images after changing the html to pass that variable.

I spent a little time with the html code, made it a little more compliant, less table-driven, split the css into a separate file for easy "theming" and did some graphics for it. I've attached a screenshot.

PhrankDaChickenGeek, is this a GPL project? Could I contribute the changes I've made somehow (presuming you approved)?

I'm also considering adding a fast, low-res "preview" scan button, too, but I might lose interest before I get there :)

---

### Post by PhrankDaChickenGeek on 2008-02-10
Glad you like it!

> **FoolsRun said:**
> 
Also, and this may just be my scanner, the "Mode" for grayscale is "gray", not "grayscale". It happily scanned grayscale images after changing the html to pass that variable.

Yeah, I think this has to do with a new version of sane-utils. Thanks for the info!

> 
I spent a little time with the html code, made it a little more compliant, less table-driven, split the css into a separate file for easy "theming" and did some graphics for it. I've attached a screenshot.


I love it! I'm not a webdesigner, so I just threw it together the best way I knew how

> 
PhrankDaChickenGeek, is this a GPL project? Could I contribute the changes I've made somehow (presuming you approved)?


Yes, this is/will be definitely GPL'd - I've been meaning to post it to sourceforge, but I'm a busy student. I'm probably going with GPL 2, since that's what I'm used to.

> 
I'm also considering adding a fast, low-res "preview" scan button, too, but I might lose interest before I get there :)

Yeah, I've though of this as well, but the default setting is pretty much the fastest scan anyways, so I left it out.

Thanks for your input!

---

### Post by FoolsRun on 2008-02-10
Post here if you get it sourceforged and I'll be sure to contribute!

---

### Post by Son of Silas on 2008-03-12
This is utterly utterly fantastic!!! THANK YOU!!!!:popcorn:

---

### Post by jcwmoore on 2008-04-13
> **FoolsRun said:**
> Post here if you get it sourceforged and I'll be sure to contribute!

+1

this tool is great, but I can two things right away that would make it better, scan to pdf, and scan a multi page project.  If you want some help improving this tool let me know

---

### Post by oxns on 2008-06-30
Hi,

Just run this on 8.04 and my scanner reports that it 'Could not scan'. I went to the cgi page and edited as suggested, but still comes up with this error.

My scanner is a Canon Pixma MP780 multifunction unit - and the printer is fine a shared OK.

I tried 'scanimage > /tmp/gsscan.ppm' from a 'Konsole' window and it created the file just fine. 

I then removed all options in the cgi leaving just 'scanimage > /tmp/scan_file.ppm' = same problem.

Downloaded the latest zip file and tried this all again and still have the same issue.

Anyone got any ideas here please ??.

Sorry I am a Linux noob :-O.

Thanks

Graham

---

### Post by FoolsRun on 2008-06-30
> **oxns said:**
> Hi,

Just run this on 8.04 and my scanner reports that it 'Could not scan'. I went to the cgi page and edited as suggested, but still comes up with this error.

My scanner is a Canon Pixma MP780 multifunction unit - and the printer is fine a shared OK.

I tried 'scanimage > /tmp/gsscan.ppm' from a 'Konsole' window and it created the file just fine. 

I then removed all options in the cgi leaving just 'scanimage > /tmp/scan_file.ppm' = same problem.

Downloaded the latest zip file and tried this all again and still have the same issue.

Anyone got any ideas here please ??.

Sorry I am a Linux noob :-O.

Thanks

Graham

Make sure the "www-data" user is in the "scanner" group. You can check this either using the "Users and Groups" too in GNOME, or by opening /etc/groups from the terminal and editing it as necessary. I had this problem, too, and meant to report it but forgot.

---

### Post by oxns on 2008-07-02
Hi,

Sorry - I did say that I was a Linux noob :-((.

Opened User Accounts - added a group 'scanner', but the user www-data is not listed - so I cannot add it to the group. Am I missing something here ???. The only users listed are me and root.

So - I tried to add 'www-data' but was told that the user already exists - so how do I get these 'hidden' users to appear in this app please ???.

I am not knowledgeable enough to edit the 'group' file - as its full of stuff I don't understand :-((.

Thanks

Graham

---

### Post by FoolsRun on 2008-07-02
> **oxns said:**
> Hi,

Sorry - I did say that I was a Linux noob :-((.

Opened User Accounts - added a group 'scanner', but the user www-data is not listed - so I cannot add it to the group. Am I missing something here ???. The only users listed are me and root.

So - I tried to add 'www-data' but was told that the user already exists - so how do I get these 'hidden' users to appear in this app please ???.

I am not knowledgeable enough to edit the 'group' file - as its full of stuff I don't understand :-((.

Thanks

Graham

Okay, let me see if I can walk you through this.

Open a terminal and type the following:
```
sudo gedit /etc/group
```

This should bring up a text editor with your group file in it.

Find the line that starts with "scanner". Mine looks like this:
```
scanner:x:104:hplip,foolsrun,www-data
```

those last three words, separated by commas, are the users in the "scanner" group.

Add ",www-data" to the end of your "scanner" line (don't forget to put a comma between the previous user and the one you're adding). Save the file. That should be all you need to do, it should work after that.

---

### Post by oxns on 2008-07-03
> **FoolsRun said:**
> Okay, let me see if I can walk you through this.

Open a terminal and type the following:
```
sudo gedit /etc/group
```

This should bring up a text editor with your group file in it.

Find the line that starts with "scanner". Mine looks like this:
```
scanner:x:104:hplip,foolsrun,www-data
```

those last three words, separated by commas, are the users in the "scanner" group.

Add ",www-data" to the end of your "scanner" line (don't forget to put a comma between the previous user and the one you're adding). Save the file. That should be all you need to do, it should work after that.

Hi,

Sorry but this still doesn't work. I added the user as defined, and then double-checked it.

The same problem arises. The scanning bar appears, then before the scanner starts up the error box pops up advising me to edit the file index.cgi.

I have changed this to :

		# Scan Command
		scanimage --resolution $QUALITY $SIZE --brightness $BRIGHT > /tmp/scan_file.ppm
# Not all scanners support the brightness and mode settings - If yours doesn't, comment the line above, then uncomment this line:
#		scanimage > /tmp/scan_file.ppm

Tried the last line as well....

NB - away for a few days so won't be able to pick this up again until late next week now - if you have the continued patience to reply that is ;-)) - hope you do 'cos if I can make this work it will be an excellent way to share my scanner.

The URL is [http://localhost/scanner/index.cgi?quality=75&size=215.9-279.4&bright=0&ornt=vert&mode=color&rotate=0&filetype=jpeg&scale=100&scanimage=Scan+Image](http://localhost/scanner/index.cgi?quality=75&size=215.9-279.4&bright=0&ornt=vert&mode=color&rotate=0&filetype=jpeg&scale=100&scanimage=Scan+Image)

Many Thanks again

Regards

Graham

---

### Post by oxsyn on 2008-07-14
Just wanted to drop a quick thank you.  This script was _exactly_ what I was looking for.  It took me about 20 minutes to get remote scanning working with my HP PSC 1510 printer/scanner (had to comment out the brightness!).

Thank you!

---

### Post by thefunnyman on 2008-08-04
Works wonderfully!  Thank you so much, just what I was looking for.  It just shows how awesome and ultimately superior the open source community really is.

Thanks again,

thefunnyman

P.S. I had to comment out the brightness line as well.

---

### Post by theozzlives on 2008-08-19
I followed the instructions to the letter and I get :
Forbidden

You don't have permission to access /scanner/index.cgi on this server.
Apache/2.2.8 (Ubuntu) Server at 192.168.0.12 Port 80

help [lease I heve Ubuntu 8.04 and a Mustek USB scanner

---

### Post by theozzlives on 2008-08-22
On Ubuntu 7.10 as the server, it scans in greyscale nomatter what mode

---

### Post by Zeratul021 on 2008-08-28
Give you hands up for this guy, great idea and good job. Works fine on all epsons and hps i tried (~12pcs).

---

### Post by willix on 2008-09-14
> **theozzlives said:**
> I followed the instructions to the letter and I get :
Forbidden

You don't have permission to access /scanner/index.cgi on this server.
Apache/2.2.8 (Ubuntu) Server at 192.168.0.12 Port 80

help [lease I heve Ubuntu 8.04 and a Mustek USB scanner

I had the same problem with my Ubuntu 8.04 until I checked the logs (/var/log/apache2/error.log) and doubled check my config files.

Make sure you added the ExecCGI directive to the /var/www directory (2nd directoy tag) and not /usr/share/doc/ directory (last directory tag).

---

### Post by PhrankDaChickenGeek on 2008-09-14
New version coming soon! I'll update install info for 8.04

If you want to help with testing, you can download it here: [http://scannerserver.online02.com](http://scannerserver.online02.com)

---

### Post by Gourgi on 2008-09-15
hi, my question is a liitle off-topic and i apologize for that but i can't find any reason why sharing a scanner over network.
Scanning procedure equals in having physical access to the scanner so you can change whatever you scan, right? (pages,photos, etc... )
Can you people please provide some examples of your scanner server's daily usage?
Is scanner server an alternative to xsane or making xsane needless?

i think i missing something here :confused:

---

### Post by PhrankDaChickenGeek on 2008-09-15
> **Gourgi said:**
> hi, my question is a liitle off-topic and i apologize for that but i can't find any reason why sharing a scanner over network.
Scanning procedure equals in having physical access to the scanner so you can change whatever you scan, right? (pages,photos, etc... )
Can you people please provide some examples of your scanner server's daily usage?
Is scanner server an alternative to xsane or making xsane needless?

i think i missing something here :confused:

Good question! :D
Yes, this script could be used in exchange for xsane, but what I use it for is my home lab. We have several computers all in the same room, but only one scanner. Easy way to share it!
Also, if someone else comes to our house, all they have to do is connect to our wireless network - No software installs, doesn't matter what OS they're running - And they can use our scanner.
It's true that many people may not need it, but it's here if you want to use it!

---

### Post by Penetration Testing on 2008-09-17
Fantastic, great help!

---

### Post by easye1161 on 2008-09-24
Using Scanner Server version 1.1.9 (as well as 1.2 Beta1) and a Canon MP470, I always get a scanner error that says "Make sure the scanner is turned on and plugged into the scanner server computer" when I try to scan.  

I don't know if it's related, but if I run scanimage > /dev/null as the superuser, the scanner scans and everything sounds good, however if I try to use my normal account I get the error "scanimage: open of device pixma:04A91723 failed: Access to resource has been denied".  This might not matter, but thought I should probably give all possible information about my problem.

PS - Thanks for your great work!

---

### Post by PhrankDaChickenGeek on 2008-09-24
> **easye1161 said:**
> Using Scanner Server version 1.1.9 (as well as 1.2 Beta1) and a Canon MP470, I always get a scanner error that says "Make sure the scanner is turned on and plugged into the scanner server computer" when I try to scan.  

I don't know if it's related, but if I run scanimage > /dev/null as the superuser, the scanner scans and everything sounds good, however if I try to use my normal account I get the error "scanimage: open of device pixma:04A91723 failed: Access to resource has been denied".  This might not matter, but thought I should probably give all possible information about my problem.

PS - Thanks for your great work!

Could you try this command as super user and give me the output:
```
scanimage --resolution 200 -x 100 -y 100 --mode color --format=ppm > /dev/null 
```

Thanks for the info! I'm still troubleshooting these kinds of issues. Since I only have an older scanner to work with, I don't always know what issues other scanners will encounter.

---

### Post by easye1161 on 2008-09-24
When I run that command as the super user, the scanner runs, but the light only makes it about 1/3 of the way through the scanner bed (due to the y=100 statement, I'm assuming).  There is a message on the CLI that says "scanimage: rounded value of resolution from 200 to 150".

---

### Post by PhrankDaChickenGeek on 2008-09-24
> **easye1161 said:**
> When I run that command as the super user, the scanner runs, but the light only makes it about 1/3 of the way through the scanner bed (due to the y=100 statement, I'm assuming).  There is a message on the CLI that says "scanimage: rounded value of resolution from 200 to 150".

Is www-data in the scanner group? 
```
sudo adduser www-data scanner
```
Which tutorial did you use to install scanner server?

---

### Post by billyswordman on 2008-09-24
Sharing scanner is common problem in my office. I think this tip is great solution. Thanks!

---

### Post by easye1161 on 2008-09-25
Yes, the www-data is in the scanner group.  I verified this in the /etc/groups file.  

The tutorial I used is the one that is at the beginning of this thread.  The original scanner server that was mentioned there didn't work, so I updated to 1.1.9 from your site, which also didn't work.  I'm currently at 1.2beta1 and am still getting the errors.

I'm sure I followed the tutorial at the beginning of this thread perfectly and have even gone through it again to make sure.  Thanks for being so quick to reply.  I appreciate it.

---

### Post by jcpren on 2008-09-25
Thanks for this software - it's a great idea!

I had to edit out the "mode" and "device" switches from the *scanimage* command to overcome some issues, but now I have a new problem.

When I try to scan, I always get the message "Make sure the scanner is turned on and plugged into the scanner server computer" in the browser, and on redirecting standard error, I see that it is producing the error message "scanimage: open of device brother2:bus4;dev2 failed: Error during device I/O" internally.

If I open a terminal window, I can invoke *scanimage* successfully from my own login. But if I enter *sudo -u www-data* before the command, I get the same device I/O error message as above.

Looks like a permissions issue, but I have already double-checked that *www-data* is a member of the *scanner* group. Any ideas?

---

### Post by easye1161 on 2008-09-29
Alright, I believe I've worked out a solution for the problems.  I don't know if it'll work for everyone, but it did for me.  

For me, the command that got the scanner working was "sudo chmod 777 /dev/bus/usb/005/002".  Depending on the port you have your scanner hooked up to, the 3 digit number after usb can change.  The problem was that non-root users did not have appropriate permissions on the USB port itself.

PS - Thanks for the helpful info jcpren, that's what helped me track down the problem.

---

### Post by pat_pfw_23 on 2008-10-05
I would just like to say THANK YOU! This is awesome and soooooo easy to set-up! :)

---

### Post by atomo133 on 2008-10-12
hi 
i ve got an hp f2180 connected to my router...
i ve done what you said but when im running "scanimage -L" i get : 
atomo@atomo-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


any suggestions??

---

### Post by PhrankDaChickenGeek on 2008-10-12
> **atomo133 said:**
> hi 
i ve got an hp f2180 connected to my router...
i ve done what you said but when im running "scanimage -L" i get : 
atomo@atomo-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


any suggestions??


Make sure you run scanimage as root:

```
$ sudo scanimage -L
```

and it may be that your scanner isn't supported by the SANE backend:

[http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=f2180&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=f2180&bus=any&v=&p=)

---

### Post by atomo133 on 2008-10-13
i did run it as root
still the same...
is it possible that its not  supported?? this machine is also a printer , which works fine on ubuntu
what should i do if it isnt??

---

### Post by atomo133 on 2008-10-19
btw according to this
[http://www.openprinting.org/show_printer.cgi?recnum=HP-Deskjet_F2180](http://www.openprinting.org/show_printer.cgi?recnum=HP-Deskjet_F2180)

scaner works via usb
so its just a network connection problem...
can anyone help me??

---

### Post by atomo133 on 2008-10-25
ok
i connected the hp machine to my computer and it worked!!!
both printing and scanning
but i need to share it between 2 computers...
how can i find it through wlan??
thanx

---

### Post by PhrankDaChickenGeek on 2008-10-26
> **atomo133 said:**
> ok
i connected the hp machine to my computer and it worked!!!
both printing and scanning
but i need to share it between 2 computers...
how can i find it through wlan??
thanx

On the computer your scanner is attached to, open a terminal and type:
```
 ifconfig | grep inet
```
This will give you your IP address - It will look something like "192.168.1.XX"

Go to the other computer, open up Firefox and type the IP address of the scanner computer in the address bar - "http://192.168.1.XX"

Click on the Scan folder link - You should be good to go if you installed this Scanner Server script on the computer that the scanner is attached to.

---

### Post by atomo133 on 2008-10-28
thanx , it worked perfectly
although it s not exactly what i was looking for...
because i  didn t have the scanner conected to my computer , but to my rooter...
anyway

---

### Post by toorima on 2008-11-17
Great idea with the script, very useful.
I have problems setting it up tho. It won't find my printer
if I do  
sudo scanimage > /dev/null 
I get 
scanimage: sane_start: Invalid argument

sudo scanimage -L gives me
device `v4l:/dev/video1' is a Noname pcHDTV HD5500 HDTV virtual device
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
device `hpaio:/usb/Photosmart_C4100_series?serial=xxxxxxxxx' is a Hewlett-Packard Photosmart_C4100_series all-in-one

so if I modify the previous command to 
sudo scanimage --device-name=hpaio:/usb/Photosmart_C4100_series?serial=xxxxxxxxxx > /dev/null it works fine

but I also have the same problem that jcpren had, not sure if that is related to my problem tho, if I do
sudo -u www-data scanimage --device-name=hpaio:/usb/Photosmart_C4100_series?serial=xxxxxxxxxxx > /dev/null 
I get
scanimage: open of device hpaio:/usb/Photosmart_C4100_series?serial=xxxxxxxxxxxxxx failed: Error during device I/O

and scanner has www-data in /etc/group

Hope anyone can help, thx

---

### Post by toorima on 2008-11-18
ok got it working, very nice script, thx

fixed it by adding a global environment variable for SANE_DEFAULT_DEVICE
added SANE_DEFAULT_DEVICE='hpaio:/usb/Photosmart_C4100_series?serial=xxxxxxxxxxx' to /etc/environment

---

### Post by lyjg1113 on 2008-11-18
2&#12289;&#21271;&#20140;[**?k?C**](http://www.shunfengbj.cn/) &#25991;&#20973;&#31867;&#65306;&#21508;&#23398;&#26657;&#27605;&#19994;&#35777;&#12289;&#39640;&#20013;&#12289;&#20013;&#19987;&#12289;&#32844;&#19994;&#23398;&#26657;&#12289;&#39640;&#31561;&#38498;&#26657;&#23398;&#21382;&#35777;&#20070;&#12289;&#33258;&#23398;&#32771;&#35797;&#12289;&#25104;&#20154;&#39640;&#32771;&#12289;&#20989;&#25480;&#12289;&#33521;&#35821;&#12289;&#35745;&#31639;&#26426;&#31561;&#32423;&#35777;&#20070;&#20197;&#21450;&#21508;&#31181;&#26723;&#26696;&#26448;&#26009;(&#21547;&#19987;&#31185;&#12289;&#26412;&#31185;&#12289;&#30740;&#31350;&#29983;&#12289;&#30805;&#22763;&#12289;&#21338;&#22763;&#31561;)&#12290;&#24182;&#21487;&#26681;&#25454;&#23458;&#25143;&#35201;&#27714;&#21150;&#29702;. 3&#12289;[**?k?C**](http://www.shunfengbj.cn/) &#36164;&#32844;&#31867;&#65306;&#29289;&#27969;&#24072;&#12289;&#21161;&#29702;&#29289;&#27969;&#24072;&#12289;&#25253;&#20851;&#35777;&#12289;&#21508;&#31867;&#25805;&#20316;&#35777;(&#30005;&#24037;&#12289;&#28938;&#24037;&#12289;&#21449;&#36710;&#12289;&#21496;&#28809;&#31561;)&#25216;&#26415;&#31561;&#32423;&#35777;(&#21021;&#32423;&#12289;&#20013;&#32423;&#12289;&#39640;&#32423;)&#12289;&#21416;&#24072;&#12289;&#32654;&#23481;&#32654;&#21457;&#12289;&#20250;&#35745;&#12289;&#20250;&#35745;&#24072;&#12289;&#24037;&#31243;&#24072;&#12289;&#25945;&#24072;&#12289;&#21307;&#24072;&#31561;&#36164;&#26684;&#35777;&#12289;&#32844;&#31216;&#35777;&#31561;&#12290; 4&#12289;[**?k?C**](http://www.shunfengbj.cn/) &#25143;&#21475;&#31867;&#65306;&#21508;&#31181;&#38450;&#20266;&#36523;&#20221;&#35777;&#12289;&#25143;&#21475;&#26412;&#12289;&#39321;&#28207;&#36523;&#20221;&#35777;&#12289;&#22238;&#20065;&#35777;&#12289;&#26410;&#23130;&#35777;&#12289;&#32467;&#23130;&#35777;&#12289;&#31163;&#23130;&#35777;&#12289;&#20934;&#29983;&#35777;&#12289;&#20581;&#24247;&#35777;&#31561;&#12290;

---

### Post by evilolive on 2009-05-19
Great tutorial.  I'm running Jaunty Jackalope and I've had to tweak a few steps...

In my case there was no 'scanner' group to join the apache system user to.  For hplip on jaunty, the permissions are set on the 'lp' group.

I found this in the userspace device rule for hplip:
```
vi /lib/udev/rules.d/40-hplip.rules
```

Also, the line cgi handler was located in mime.conf:
```
sudo vi /etc/apache2/mods-available/mime.conf
```

To allow index.cgi to be the directory index, add the following line under the "Directory /" line in '/etc/apache2/sites-available/default'
```
DirectoryIndex index.cgi
```

To add PDF support to this script you need replace
```
# Convert scan to image file
pnmto$FILETYPE /tmp/scan_file.ppm > scans/$S_FILENAME
rm /tmp/scan_file.ppm
```
with
```

 # Convert scan to image file
if [ $FILETYPE != "pdf" ]
then
  pnmto$FILETYPE /tmp/scan_file.ppm > scans/$S_FILENAME
else
   pnmtops /tmp/scan_file.ppm | ps2pdf - scans/$S_FILENAME
fi
rm /tmp/scan_file.ppm
```
in 'index.cgi'

You have to also add an option line to the filetype select box
```
echo '<select name="filetype">'
echo '<option value="jpeg" selected="selected">*.jpg (Small)</option>'
echo '<option value="tiff">*.tiff (Very Large)</option>'
echo '<option value="png">*.png (Large)</option>'
echo '<option value="pdf">*.pdf (Large)</option>'
echo '</select>'
```


Hopefully this this is helpful to someone else.

---

### Post by PhrankDaChickenGeek on 2009-05-19
Thanks much!
If I get a scanner hooked back up, I'll test and add this to the script
(someone took my testing scanner and made a robot... :-P )

---

### Post by wwnmt on 2009-07-05
> **erwall said:**
> Did as you said but still doing the same thing..

I had a similar issue.  I have one of those HP AIO printers, had to add the users to the lp group.

Used the following command:

```
usermod -a -G lp www-data
```

edit 1:

Still didnt work.....

edit 2:

Im a dork....  Forgot to change the index.cgi file and use the command without the brightness setttings....

---

### Post by Failbot on 2009-08-12
My scanner had a slash in it's name (Canon CanoScan N670U/N676U/LiDE20 flatbed scanner) that was confusing the script. I would get a blank scan page with only the header and footer showing (no form etc).

I edited the config/scanners.conf and removed the slashes from the scanner name and now it's working.

This is such a great idea! No worries about client OS or setup, thanks!

Edit:
Just added PDF support (thanks to evilolive) - works fine. Only problem I can see now is when I choose "full scan" it doesn't scan the whole page... again I can just probably tinker with the code to solve this.

---

### Post by fernspa on 2009-08-29
Hi guys, the scanner works from XSane Image scanning program. from terminal seems to work too.
Was wondering where is the brightness setting in the index.cgi that must be commented.
 
thanks
Ferns

---

### Post by PhrankDaChickenGeek on 2009-08-29
Check the whole thread - it's post #3 - [http://ubuntuforums.org/showpost.php?p=4226794&postcount=3](http://ubuntuforums.org/showpost.php?p=4226794&postcount=3)

---

### Post by mrgreaper on 2009-09-17
ok the command to add www-data to the scanner group kept telling me there was no such group 

so i followed all the other steps 

i then read all the posts here 

i went in to administration menu users and groups i unlocked it added group scanner 

the command to add www-data to the group then worked

i went to the scanner page hit scan 

it errored and told me to edit the cgi 

i folowed the steps commented out the original line un commented the other

it still errored 

im sure the problem is the scanner group was not created auto maticly, at what point should it of been created? how do i fix this?


edit \/\/\/\/\/\/\/\/

if i type xsane in terminal and use the programe that comes up i can scan no problem,so my scanner is setup its just that damn group thing...i think

---

### Post by maniaq on 2010-03-06
same problem for me - no such "scanner" group??

HP Deskjet that otherwise scans just fine (and prints over the network via CUPS too!)

from other comments it appears the lack of a "scanner" group is a Jaunty thing but I didn't have any such hplip rules in /lib/udev/rules.d to look at?

I tried adding www-data to just about every group I could think of... lp, lpadmin, plugdev...

no joy

the command to scan from the CLI works no problem so my default user obviously has the right permissions but the cgi does not

(btw neither version of the command in the cgi works, mode/brightness or no mode/brightness settings)

this was a nice idea, and I'm sure it's some simple thing I'm missing here, but if doesn't work it doesn't work...

---

### Post by PhrankDaChickenGeek on 2010-03-07
Unfortunately, I have no scanners at the moment, and so no way to test.
Hopefully I'll be able to get one and update the script for 10.04 when it comes out.
The only thing I can tell you is to check some of the suggestions given at [http://scannerserver.online02.com](http://scannerserver.online02.com)

---

### Post by imon9 on 2010-06-06
hi, anyone can help me here?
my: 
sudo scanimage -L show:
```
device `plustek:libusb:002:002' is a Canon CanoScan N670U/N676U/LiDE20 flatbed scanner
```

the scanner is supported by sane
xsane and sane works fine
i have all my permission done correctly and i've the script running on localhost

but the script will not detect my scanner. the error message says:
```
There were no scanners found on this server. Make sure the scanners are plugged in and turned on. The scanner must also be supported by SANE
```

any suggestion or help will be nice

---

### Post by Leppie on 2010-07-03
the scanner scripts do not seem to be compatible with all scanners (even though the scanner may be compatible with sane). i'm sharing a hp and brother over the network, but the brother cannot be access using the scanner server.
if you only access the scanners from machines on your local network, you may want to try to use simple scanner or xsane. I rewrote the scanner howto for Lucid Lynx, though it may also be applicable for Karmic (haven't tested that yet): [http://ubuntuforums.org/showthread.php?t=1519201]("http://newyork.ubuntuforums.org/showthread.php?t=1519201")

---

### Post by jhansonxi on 2010-10-03
I created a **[patch for 1.2 Beta 1](http://jhansonxi.blogspot.com/2010/10/patch-for-linux-scanner-server-v12.html)** that fixes several bugs and adds parallel port scanner support.

---

### Post by jhansonxi on 2010-10-03
I just **[released scanner-access-enabler]("http://jhansonxi.blogspot.com/2010/10/scanner-access-enabler.html")**, a GUI tool for setting scanner device permissions so that www-data (and thus LSS) can use any scanner.

---

### Post by Uteligger66 on 2010-10-06
Very good program! But i have a slight problem. The scanner software is stuck on "someone is using the scanner - Try again later". 
How can I restart the software? I have tried restarting apache2 and also the whole machine but no go. 

Grateful for all help.

---

### Post by jhansonxi on 2010-10-06
> **Uteligger66 said:**
> Very good program! But i have a slight problem. The scanner software is stuck on "someone is using the scanner - Try again later". 
How can I restart the software? I have tried restarting apache2 and also the whole machine but no go. 

Grateful for all help.

That is tracked by the INUSE parameter in /var/www/scan/config/scanners.conf so just set the faulty one back to 0.

I changed the original handling of the status to a simpler direct sed edit instead of the original cat | sed > tmp/scn method.  It seemed robust when I tested it.  A more correct method may be to the lockfile tools from the **[lockfile-progs](https://launchpad.net/ubuntu/+source/lockfile-progs)** package which is used for start-up scripts but I only recently discovered them.

---

### Post by Uteligger66 on 2010-10-06
Thanks for the help. 
I did however not find the config file you where talking about. But I searched the index.cgi file and it said that if the file "scanlock" was in the tmp folder, the scanning software would not work because of this. All I did was delete the scanlock file, and now everything is good.

---

### Post by squaredoffagain on 2011-02-15
The Scanner Server is brilliant. Exactly what I needed, but I had a couple of issues setting up my Epson DX7400 so it took longer than it might have done. 

In the hope I might save some time for others here're a couple of tips that might help anyone struggling.

[LIST=1]
[*]Assuming your user is allowed to sudo as any other user I found the easiest way to test the permissions of the www-data user to use [FONT=Courier New]$CMD[/FONT] was using: ```
sudo -u www-data $CMD
```
[*]You need permission not only to run the command, but also to write to the fixed output file location. If you have run a test as root the www-data user probably won't have permission to overwrite root's file. Use this command to check: ```
sudo -u www-data touch /tmp/scan_file.ppm
```
[*]To ensure everyone has rights to access the USB connection to the scanner I used ```
scanimage -L | sed "s/^\([^:]*:\)\{2\}\([[:digit:]]*\):\([[:digit:]]*\).*$/sudo chmod 777 \/dev\/bus\/usb\/\2\/\3/" | bash
```
[/LIST]

Could I offer the suggestion that index.cgi be modified to use tempfile(1) so that the output file overwriting issue would be avoided?
I appreciate this could leave stale root-owned scans hanging around, but unless /tmp is unusually configured it wouldn't ever fail with a permissioning problem on the output file.

---

### Post by 2briancox on 2011-04-06
I get to:
sudo adduser www-data scanner
and I am told that group 'scanner' does not exist.  The server did see my scanner.

But, being a noob as I am, I'm not sure how to proceed here.

---

