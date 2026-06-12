---
title: "cafe con leche: Internet cafe management software"
date: 2008-05-01
forum: Philippine Team
---

### Post by loell on 2008-05-01
updated howto from **Script Warlock**

> **Script Warlock said:**
> [B][http://ccl.sourceforge.net/](http://ccl.sourceforge.net/)

[/B][B]Screenshots

   [IMG]http://img196.imageshack.us/img196/8467/serverh.jpg[/IMG]
                                [/B][SIZE=3]Server[/SIZE][B]

  [IMG]http://img180.imageshack.us/img180/3489/client.jpg[/IMG]
                                 [/B][SIZE=4][SIZE=3]Client[/SIZE]

[/SIZE]**Common Installation     **

 Both side of the application (server and client) has to meet their dependencies, since this is not a debian package, we have to install the dependencies manually. CCL dependencies are
 
[LIST]
[*]sqlite3
[*]glib2.0
[*]libfox1.4(server), libfox1.6(client)
[*]openssl
[/LIST]
 **For the ccl server run these commands :**[INDENT]$ sudo apt-get install sqlite3 libsqlite3-dev[/INDENT][INDENT]$ sudo apt-get install libfox1.4 libfox1.4-dev   (server)[/INDENT][INDENT]$ sudo apt-get install libglib2.0-dev[/INDENT][INDENT]$ sudo apt-get install libssl-dev[/INDENT][COLOR=Black]**For the [COLOR=Red]ccl client [/COLOR][COLOR=Black]replace[/COLOR] the [COLOR=Red]libfox1.4[/COLOR] run these command :**[/COLOR]
          $ sudo apt-get install [COLOR=Red]libfox-1.6-0 libfox-1.6-dev  
[/COLOR]  [B]
Don’t forget the build essentials for compiling from source :[/B][INDENT]$sudo apt-get install build-essential[/INDENT]**Then edit your /etc/ld.so.conf file with :**[INDENT]$sudo gedit /etc/ld.so.conf[/INDENT]**And add these lines :**[INDENT]/usr/lib
/usr/local/lib                           …..and save the changes when done
[/INDENT]**it may look like this :**
     
include /etc/ld.so.conf.d/*.conf
 /usr/lib
 /usr/local/lib
 [B]
Then execute this :[/B]
$sudo ldconfig[COLOR=Blue][U][B]

CCL Server Installation[/B][/U][/COLOR][B]
[COLOR=Black]for the server side you’ll need these 2 files :[/COLOR][/B]
 cclfox-0.7.1.tar.bz2 [here]("http://www.mediafire.com/file/wwflozzincz/cclfox-0.7.1.tar.bz2")
libccls-0.7.1.tar.bz2    [here]("http://www.mediafire.com/file/antg3d1mh5q/libccls-0.7.1.tar.bz2")
 [B]
Put these files on your home folder and do these steps :[/B][INDENT]$tar -xjvf libccls-0.7.1.tar.bz2
$cd libccls-0.7.1
$./configure
$make
$sudo make install
$cd ..
$tar -xjvf cclfox-0.7.1.tar.bz2
$cd cclfox-0.7.1
$./configure
$make
$sudo make install[/INDENT][B]
create a folder in the home directory :[/B]
     $mkdir .cclfox
 [B]
put [this]("http://www.mediafire.com/file/t2w5azgwtmi/pem") file to the .cclfox folder right click and choose the properties and select permission then tick the box and close. generate the pem by double clicking it and  if being prompted just run it.[/B]

  [IMG]http://img42.imageshack.us/img42/3199/pem.png[/IMG]


**Then create a launcher on your desktop and add :**[INDENT]cclfox -nossl[/INDENT]on the “command” text box

 _[COLOR=Blue]**CCL Client Installation**[/COLOR]_  
 **for the client side you’ll need these 2 files :**
 cclcfox-0.7.1-FOX-1.6.tar.bz2  [here]("http://www.mediafire.com/file/ylwx3ziw44i/cclcfox-0.7.1-FOX-1.6.tar.bz2")
libcclc-0.7.1.tar.bz2  [here]("http://www.mediafire.com/file/zryqm2wz4ac/libcclc-0.7.1.tar.bz2")
 [B]
put these files on your home folder and do these steps :[/B][INDENT]$tar -xjvf libcclc-0.7.1.tar.bz2
$cd libcclc-0.7.1
$./configure
$make
$sudo make install
$cd ..
$tar -xjvf cclcfox-0.7.1-FOX-1.6.tar.bz2
$cd cclcfox-0.7.1
$./configure
$make
$sudo make install[/INDENT]**create a folder in the home directory :**
     $mkdir .cclcfox

 [B]put [this]("http://www.mediafire.com/file/t2w5azgwtmi/pem") file to the .cclfox folder right click and choose the properties and select permission then tick the box and close. generate the pem by double clicking it and  if being prompted just run it.

  [IMG]http://img42.imageshack.us/img42/3199/pem.png[/IMG]

[/B]  [B]
then create a launcher on your home folder and add : (Alt+f2 will do)[/B]

cclcfox -host serverip -name anyname -nossl[INDENT]on the “command” text box[/INDENT][INDENT]**to check the client hostname simply type in the terminal:**[/INDENT][INDENT]         $ hostname[/INDENT]**Setting the tariff :           **


[LIST=1]
[*]launch the ccl server and choose     the tariff tab
[*]select the     days(highlighted) before modifying or nothing will change. after the desired values are filled accordingly to your likes     click the apply.....
[/LIST]
 
  [IMG]http://img178.imageshack.us/img178/3427/tariff.png[/IMG]
 

 **Autorun the ccl client :     **

   [IMG]http://img178.imageshack.us/img178/7443/addt.png[/IMG]


 to run this on startup in ubuntu/gnome 
add the above in **System** menu ->**preferences**->**sessions(8.04) | startup applications(9.04) **
 [B]
Name: any name[/B]
 **Command: cclcfox -host serverip -name anyname -nossl**
 **Comment: whatever**
 [B]
Remote shutdown and reboot :           [/B]

$ chmod 7755 /sbin/shutdown
        $ chmod 7755 /sbin/reboot
 [B]
Replacing the desktop lockscreen :           [/B]

[COLOR=Red]1[/COLOR]. kill the cclcfox running  >>> sudo kill -9 (pid of cclcfox)
[COLOR=Red]2[/COLOR]. create or choose the desired             photo and save it on the .cclcfox folder located in the home             folder. Note that .cclcfox is a hidden folder so in order to             display open the home folder and select the view then tick/select             the box “show hidden files”. close when done
[COLOR=Red]3[/COLOR]. relaunch the client timer             and “end the session”.

 **Common functions :**
 
  [IMG]http://img178.imageshack.us/img178/4390/buttonsf.png[/IMG]

Green – start session
Yellow – pause and resume             session
Red – stop session
Blue – continue session
Purple – swap session
Turquoise – set timeout             (countdown)

**to start the pre-paid session:**
     press the green and the turquoise and set the time...
 
 **to start the opentime session:**
     press the green button....
 
 **to pause the session:**
     press the yellow and to resume press again the yellow...
 
 **to continue the session**
     if the customer accidentally stops the session it can be continued by pressing the blue button
 
 **to swap the session:**
     if the customer of ubuntu1(workstation) wants to transfer to ubuntu8 for some reason simply choose the ubuntu1 icon and press the purple button and choose the ubuntu8 pc. The time consumed, left or account is also transferred...
 

 **Remote functions: (right click the icon)**
 
  [IMG]http://img195.imageshack.us/img195/1194/70007083.png[/IMG]

 **Set member:**
     to setting the member is according to the member section (tab) below the tariff
 
 **Turn off:**
     remotely shutdown the workstation …   
 
 **Reboot:**
     remotely restart the workstation  …. 
 
 **Turn off screen:**
     remotely turn off the client workstation monitor
 
 **Allow users to start the session:**
     if selected user can start the session by clicking the pop-up tab on the workstation lockscreen
 
 **Allow members to start the session:**
     it allows the member to start the session
     
 To uninstall the cclfox (client and server): 
     open the terminal
     $[COLOR=Red]cd libccls-0.7.1[/COLOR]              … [COLOR=Red]cd cclfox-0.7.1[/COLOR]
     $make uninstall

a big thanks to [Yogha Restu Pramadi]("http://yogharp.wordpress.com/2007/08/23/cafe-con-leche-ubuntu-how-to/")

---

### Post by BatsotO on 2008-05-01
Just adding..
I've been use cclfox for a while and by far it's a neat program.

1.You might need to add :

/usr/lib
/usr/local/lib

in the /etc/ld.so.conf and do ldconfig.

2. You can change the lock screen display on the client by creating some neatest picture you can think of, save it in gif and name the picture lockpix (therefore lockpix.gif) and place it in the .cclcfox folder (not cclfox in the client side) along with the pems files.

3. if you want to shutdown and reboot client pcs remotely, chmod 7755 the /usr/bin/shutdown and /usr/bin/reboot.

4. Secure your wokrstations, you don't want any naughty user with some linux knowledge do process listing and send kill signal to terminate the cclcfox application, or delete it from the start up list. I disable terminal, virtual consoles and gnome-session-properties in my workstations to at least securing my setting (along with desktop locker and some gconf editing).

5. The installation wasn't that hard ( I wonder why so many tutorial on installation but so few on how to operate things). The most difficult to figure in my experience was tariff setting. I dont want user who use the wokstation for 5 minutes to pay for the whole hour, so I have to calculate per minute charge and set them minute per minute

6. There are more than one tariff scheme, so you can set it the way you needed. (this is a big plus)

7. Member first login will be their account number id and the password is also their account number id, from there the member can set their own password, then they can use their own login name and passord. 


That's all I can remember right now.

---

### Post by loell on 2008-05-01
thank you for the additionals :) hopefully you can add more tips.
there is little or no documentation on how to use ccl, i hope we can alleviate that as the thread progress.

---

### Post by BatsotO on 2008-05-01
Yes, no documentation at all. But of the few cafe management software, this one is the most complete. 
I use deb packages build by Indonesian, it's current version is 0.7.1-2 and they translate the interface to Indonesian, so it will be small problem because I don't have English version installed.
In My installed version, there's also a small fix that allowed the workstation to be locked down when server application need to be restarted.
I will be glad to answer any questions regarding the operation of ccl in anyway I can.

This application dated back to 2005, and since then only a few modification was made. If only anyone experience in c++ and foxtool can made modifications, especially on the client display, it has no windows,It cannot be minimized, it sits on top of the screen, and it's bugging the users. But despite all that this application works.

---

### Post by Script Warlock on 2008-05-02
> **BatsotO said:**
> Just adding..
I've been use cclfox for a while and by far it's a neat program.

1.You might need to add :

/usr/lib
/usr/local/lib

in the /etc/ld.so.conf and do ldconfig.

2. You can change the lock screen display on the client by creating some neatest picture you can think of, save it in gif and name the picture lockpix (therefore lockpix.gif) and place it in the .cclcfox folder (not cclfox in the client side) along with the pems files.

3. if you want to shutdown and reboot client pcs remotely, chmod 7755 the /usr/bin/shutdown and /usr/bin/reboot.

4. Secure your wokrstations, you don't want any naughty user with some linux knowledge do process listing and send kill signal to terminate the cclcfox application, or delete it from the start up list. I disable terminal, virtual consoles and gnome-session-properties in my workstations to at least securing my setting (along with desktop locker and some gconf editing).

5. The installation wasn't that hard ( I wonder why so many tutorial on installation but so few on how to operate things). The most difficult to figure in my experience was tariff setting. I dont want user who use the wokstation for 5 minutes to pay for the whole hour, so I have to calculate per minute charge and set them minute per minute

6. There are more than one tariff scheme, so you can set it the way you needed. (this is a big plus)

7. Member first login will be their account number id and the password is also their account number id, from there the member can set their own password, then they can use their own login name and passord. 


That's all I can remember right now.
some favor pls:
1. can i have that 0.7.1-2 in .deb packages?
2. chmod 7755? what is the command in terminal becoz dunno how...
3. i used the prepaid and opentime but the terminal counter is not working. do you know the set up for this to let the customers know the total amount they consumed?
4. is it possible to install CCLC in guest account in ubuntu just to make it more secure from the naughty users?
5. any new icons and buttons or some logo for CCL?

thanks very much........hope you send the reply as soon as possible!!

---

### Post by Script Warlock on 2008-05-02
[COLOR="Black"]> **loell said:**
> [SIZE="4"]for the cafe owners that run ubuntu[/SIZE] :)

project site: [http://ccl.sourceforge.net/]("http://ccl.sourceforge.net/")
note: the packages are made for hardy heron

[COLOR="Red"]**server side setup:**[/COLOR]

download and install these packages respectively
1. [ATTACH]68258[/ATTACH]
2. [ATTACH]68256[/ATTACH]

after installing the above two. 
download and copy these files

[CA.pem]("http://ccl.sourceforge.net/tmp/CA.pem") and [cert.pem]("http://ccl.sourceforge.net/tmp/cert.pem") to **.cclfox** in your home directory

to run the server software: run **cclfox** in the command line or launcher.


[COLOR="Red"]**Client side or Workstation setup**[/COLOR]

download and install these packages respectively

1. [ATTACH]68257[/ATTACH]
2. [ATTACH]68255[/ATTACH]


after installing the above two. 
download and copy these files

[CA.pem]("http://ccl.sourceforge.net/tmp/CA.pem") and [cert.pem]("http://ccl.sourceforge.net/tmp/cert.pem") to **.cclfox** in your home directory

note: yes,  same certificate files as the server

to run the client software you can run this at startup or in the command line

```
cclcfox -host <server> -name <myname>
```

where <server> is the local ip address of the server
 and  <name> is the name of your workstation ie(pc1, pc2 ..) , any name will do.

to run this on startup in ubuntu/gnome 
add the above in **System** menu --> **preferences** --> **sessions **

ang bilis!! heheh ayos to dami na pumapasok na info para sa mga inet operators na linux ang distro gamit.....

sir ok to ha pero may kunti problema lang sa startup kc dretso open yung CCLC tapos may time din na nagrun na sya pero di makita yung timer parang nasa ilalaim lang ng desktop ..ano kay to is it about the priority sa processes or something dapat kc after log-in maglock na ang desktop ng client with CCL pero dretso lang sya open...some ideas?

btw gamit ko etong 0.7.1 sana meron ding skin themes

yung sa cert pala ang ginawa ko copy paste lang sa text editor tapos save as _some names_ tapos right click ko ang file na _some names_ tapos click ang permission click lang yung box na allow executing file as program tapos lumabas na aresulta na .pem..tama ba ginawa ko? ano pala purpose ng mga yun .perm para saan yun?

sana makagawa din tayo para sa winXP[/COLOR]

---

### Post by loell on 2008-05-02
we'll gonna have to ask BatsotO on where to put cclc client startup :)

theoretically you could compile this in windows xp. but someone needs to try, i couldn't for now. you may need mingw, glib , and then the fox toolkit.

to download the pem, w/o going to a text editor, just right click it and save link as, save it to the .cclfox directory  pem files are just certificate needed for authentication to the server.

---

### Post by Script Warlock on 2008-05-02
> **loell said:**
> we'll gonna have to ask BatsotO on where to put cclc client startup :)

theoretically you could compile this in windows xp. but someone needs to try, i couldn't for now. you may need mingw, glib , and then the fox toolkit.

to download the pem, w/o going to a text editor, just right click it and save link as, save it to the .cclfox directory  pem files are just certificate needed for authentication to the server.

ok now i understand about the .pem 

maybe i'll try this to install in xp

salamat bro

---

### Post by perbiu on 2008-05-02
Gawa naman kayo ng client for Windows xp!.
O kaya Cybera Server for Ubuntu.

---

### Post by Script Warlock on 2008-05-02
> **perbiu said:**
> Gawa naman kayo ng client for Windows xp!.
O kaya Cybera Server for Ubuntu.

sure gonna try it later tonight dami pa customer sa inet shop kong ubuntu....galing ng CCL for my ubuntu :guitar:

---

### Post by Script Warlock on 2008-05-02
> **loell said:**
> we'll gonna have to ask BatsotO on where to put cclc client startup :)

theoretically you could compile this in windows xp. but someone needs to try, i couldn't for now. you may need mingw, glib , and then the fox toolkit.

to download the pem, w/o going to a text editor, just right click it and save link as, save it to the .cclfox directory  pem files are just certificate needed for authentication to the server.
so we don't need to put this to client command... cclcfox -host 192.168.0.1 -name ubuntuxx -nossl -certpass xxxxx?

just cclcfox -host 192.168.0.1 name ubuntuxx -nossl....sakto?

anyway both are functional pero have no idea on the effects of it...

---

### Post by loell on 2008-05-03
yeah, exactly :)

---

### Post by Script Warlock on 2008-05-03
> **perbiu said:**
> Gawa naman kayo ng client for Windows xp!.
O kaya Cybera Server for Ubuntu.

oi ikaw pala pala yun sa ulop kmusta gawa nyo print server ok na?

---

### Post by perbiu on 2008-05-05
> **boyet said:**
> oi ikaw pala pala yun sa ulop kmusta gawa nyo print server ok na?

Medyo okay na, parang nakita ko na sa samba.conf, kaso hindi rin madedeploy kung hindi kami makakakita ng magandang timer.

*Repost:

CafePilot = May Linux at Windows server, client. Kaso Prepaid style lang.

OutKafe = May Linux server at Windows client, kaso pang 64-bit lang yung pang server.

Cybera = Ito pinakagusto kong timer, kaso hindi na namaintain at pang Windows server at client lang.

CafeconLeche = Pang Linux lang? walang Windows client.

---

### Post by Script Warlock on 2008-05-06
sinubukan ko pa e-run sa windows XP pero it takes time para sa akin kc may work ako sa audio company...sige lang next month bka may resulta na...

try nettime server it works fine with wine sa ubuntu 8.04 try to be careful lang sa mga clicks mo during operation kc may time maghangup. sa akin ang ginawa ko dati is to avoid clicking na wala sa function kagaya ng _about_ maghang kc so kinakailangan ko na naman kill process..
cybera magwork sa wine pero kailangan >>>.NET Framework 1.1>>>IE4linux>>>at may konting dependency pa para lang magrun ang timer sa wine...

---

### Post by kromed on 2008-05-12
Hi Guys,
:(
I successfully managed to install Cafe Con Leche in my cyber cafe but just one little hitch!  At the server side, I can not be able to generate any log of a day's income.  I don't even think the program is logging.  All I can do is stop and start the timer on the client machines.  I really need to know how to implement the logging functionality.  Any help????!!!!
Thanx
Linux 4ever!

---

### Post by perbiu on 2008-05-14
> **kromed said:**
> Hi Guys,
:(
I successfully managed to install Cafe Con Leche in my cyber cafe but just one little hitch!  At the server side, I can not be able to generate any log of a day's income.  I don't even think the program is logging.  All I can do is stop and start the timer on the client machines.  I really need to know how to implement the logging functionality.  Any help????!!!!
Thanx
Linux 4ever!

Try to press the Refresh button.

---

### Post by perbiu on 2008-05-14
[IMG]http://img520.imageshack.us/img520/7854/ccxoq5.jpg[/IMG]
English mode:
I am confused with the timer pricing, how do you set this up?
Example if we use 30mins = P10.
:confused:

---

### Post by perbiu on 2008-05-17
I have figured out the timer, i think it does not have block timing like the traditional I-net cafe in the Phils, 15mins=P5, 30mins=P10, 1hr=P20.

But another question, where can you see the Log file? or how can you print it?

---

### Post by BatsotO on 2008-05-24
Sorry for late reply. My sister was married early this month and not long after i have to get my wife to hospital, our first babies did not made it.
basically you can devide the tariff per day, I call it zone tariff. We have two different tariff, 6 am to 10 pm, and 10 pm to 6 am. so i set the per hour tariff, and per minute tariff, on both tariff zone. yes from first minute to minute 200 or more, our customer is so grumpy when they find out that 10 minute and 15 minute price is the same.
The log can be viewed in as you like, wheter per day or per shift or per month, and saved as log file in .cclfox directoriy.
sorry, thats all i can remember for now coz i dont have ubuntu box at home (frankly i dont have computer at home).

---

### Post by wersdaluv on 2008-05-24
> **BatsotO said:**
> Sorry for late reply. My sister was married early this month and not long after i have to get my wife to hospital, our first babies did not made it.
basically you can devide the tariff per day, I call it zone tariff. We have two different tariff, 6 am to 10 pm, and 10 pm to 6 am. so i set the per hour tariff, and per minute tariff, on both tariff zone. yes from first minute to minute 200 or more, our customer is so grumpy when they find out that 10 minute and 15 minute price is the same.
The log can be viewed in as you like, wheter per day or per shift or per month, and saved as log file in .cclfox directoriy.
sorry, thats all i can remember for now coz i dont have ubuntu box at home (frankly i dont have computer at home).

Termima kasih, pak

---

### Post by perbiu on 2008-05-25
Thanks, For reference.

In the Phils, we should use 0.20, i was using 20.00 pricing that is why i was so confused.
The log file is at /home/username/.cclfox/cclfox.db and can be viewed using SQL Lite that can be isntalled using the Add/Remove.

---

### Post by booleanB on 2008-06-18
Thanx a lot loell, i'm switching to ubuntu in my cafe and new to Ubuntu, this is going to be a BIG help

---

### Post by loell on 2008-06-18
no problem, thanks to the cafe owners that gave and will be giving feedback :)

---

### Post by benquick on 2008-06-20
Previously when using ubuntu 7,10, client side billing had no problem, after upgraded to 8.04, desktop client side billing not locked, so when client computer was turned on, the desktop locked normally, but after computer panel emerged,the desktop lockpix always disappear, So if user that wanna use the computer,I must start billing manually on a server side

any idea?

---

### Post by loell on 2008-06-20
probably just reinstall CCL?

---

### Post by benquick on 2008-06-20
> **loell said:**
> probably just reinstall CCL?

it happen for all client computer, and CCL on all client was reinstalled, even reinstalling system doesn't resolve this problem

sometimes can locked but more often not locked!:confused:

---

### Post by loell on 2008-06-23
added some pics at the first post :)

thanks to boyet.

---

### Post by L0tU5 on 2008-06-26
HI
any way to make it a prepaid system?

---

### Post by loell on 2008-06-26
> **L0tU5 said:**
> HI
any way to make it a prepaid system?

I believe you're looking for [B]cafepilot
[/B]

[http://www.dijitanix.com/]("http://www.dijitanix.com/")

---

### Post by L0tU5 on 2008-06-27
Beautiful man!! thanks! exactly what I'm looking for!!

---

### Post by rauldinho on 2008-07-01
Hi, first let me start by thanking **loell** for creating this post, you have no idea how much this helped me, so thanks! second i would like to ask you what type of security measures do you think i should apply to my cibercafe in every box. If you could point out any guide for this i would deeply appreciate it, since i'm kind of new to linux. So thanks for all your help!

---

### Post by loell on 2008-07-01
probably the basic security measure that you could apply to each of your workstation is limit the default **user account** that your cyber clients will be using.

 in ubuntu context, when creating an account in **System** menu --> **Administration** --> **users and groups** 

you could limit it to a certain level.

---

### Post by BatsotO on 2008-07-02
I hope this help.
For security, you need to disable any terminal applicatint in the client, including alt-ctrl-fx. run terminal with root privalage and chmod o-x /bin/xterm and /bin/gnome-terminal (correct my if i'm wrong). as with ctrl-alt-fx you can browse the forum on how to disable it. the main reason is to prevent users from listing the process ( do ps aux) and kill the cclcfox.
the next thing is make sure that user cannot edit session by chmod o-x /bin/gnome-session-properties, and remove write privalage on .config/autostart, just to make sure no one deletes the cclcfox.desktop.
I also would recommend disabling shutdown, logoff and switch user using pessulus. my operator can now remote shutdownd the client by ccl after I chmod 7755 /sbin/shutdown and /sbin/restart.
If you want to use the client pc just do ctrl-alt-backspace and enter to your own account, or you can go further by disabling ctrl-alt-backspace.
hope this help.

---

### Post by elyserva on 2008-07-19
I was trying out CCL on my small cafe. I was able to install the server. The problem is the client side. I was able to install everthing without any problem or error messages. My problem is the folder .cclfox was not created. The program won't run without the certificates that needs to be placed in the .cclfox folder.

Have I done something wrong here? Please help!

BTW, is there any manual or something to use this thing?

---

### Post by loell on 2008-07-19
oh, you have to manually create the **.cclfox** directory

---

### Post by acp_ on 2008-07-27
Hi,

My internetshop is setup as thinclient(ltsp),is it possible if I could use this cafe con leche as my cafe management software or is there any suggestion. important to me is the billing?

Thanks,
AC

---

### Post by Script Warlock on 2008-07-27
> **acp_ said:**
> Hi,

My internetshop is setup as thinclient(ltsp),is it possible if I could use this cafe con leche as my cafe management software or is there any suggestion. important to me is the billing?

Thanks,
AC

yes you can use it all you need is to configure your LTSP Client to be able running LOCAL APPS..another one is outkafe by OUTKAST SOLUTIONS for your ltsp set-up it works well....   [http://outkastsolutions.co.za/outkast/index.php?option=com_openwiki&id=outkafe](http://outkastsolutions.co.za/outkast/index.php?option=com_openwiki&id=outkafe)

---

### Post by zirunjoker292 on 2008-08-09
where do i get the **CA.pem** and **CERT.pem**???

but keep on rocking:guitar:

---

### Post by loell on 2008-08-09
> **zirunjoker292 said:**
> where do i get the **CA.pem** and **CERT.pem**???


you can click  both  (ca.pem and cert.pem) in the first post ;)

---

### Post by Widad on 2008-08-10
hi, i'm very much new with ccl, about setting up the tarif, i'm still blur. i have two type of usage, one with 1hr for 50 cents and another one is 1hr for $1. Can you help? How to set up and configure? ANother thing, what is the colour code means with blue, green, red?

---

### Post by Script Warlock on 2008-08-11
if u mean the monitor icon:

red - stop timer
yellow - pause timer
green - start timer

later i will post my answer for ur first q....bc burning cd

---

### Post by Widad on 2008-08-11
Can anybody teach me how to set the tarif?

---

### Post by Script Warlock on 2008-08-12
from [COLOR="Blue"]TIZOC[/COLOR]

A "tarif" covers one entire week, you can have multiple tarifs, and change them whenever you want, and hace different tarifs applied to specific members. A tarif is composed of tarif parts. A tarif part represents a time range (from hour X to hour Y), a price per hour, the days of the week it applies, and individual prices. Prices are a minutes/cost asociation, and they are used when the user used internet for less than the minimum fractioning time (the default is 1 hour, but can be changed) 
 
If you want 3 euros for one hour and 1 euro for 20 minutes, you can add a price for the 20 minutes, or you can reduce the minutes at with the cost calculation system starts fractioning. When time is below the minimum for fractioning, it is rounded upwards to the nearest time/cost available, and if none if found, the price per hour is used. That means that if the minimum price is 20 minutes at $1 and the user used the pc for 13 minutes, he will be charged $1 (assuming we are not using fractioning at that point). 
 
If fractioning were used, and the price per hour was $13, he would be charged 3*13/60 = $0.65 

unahin mo muna kang tizoc na guide...

---

### Post by loell on 2008-08-12
updated the first post linking the above in setting tarifs :)

thanks boyet.. :)

---

### Post by Script Warlock on 2008-08-13
> **Widad said:**
> Can anybody teach me how to set the tarif?

are you a pinoy? i have a guide on tagalog version

---

### Post by PTo on 2008-08-26
When you use the countdown with CCL and the time is up, the client can just click to continue serving the internet. Does anyone know how to unable this? I want the client to ask for a new countdown to continue, is this possible?

---

### Post by Script Warlock on 2008-08-27
> **PTo said:**
> When you use the countdown with CCL and the time is up, the client can just click to continue serving the internet. Does anyone know how to unable this? I want the client to ask for a new countdown to continue, is this possible?

try to check if the "allow users to start the session" has been ticked by right clicking the monintor icon..if it did then untick it...

---

### Post by PTo on 2008-08-28
Thanx a lot boyet, sometimes the solution is so obvious and you still don't see it...

Is it possible for a member to log out and use his remaining time on another occassion?

Can you tell me what the blue button with two arrows does?

---

### Post by Script Warlock on 2008-08-28
swapping of workstation and timer/billing 

first q will be answered after i return home....on vacation pa ako hehhehe:guitar:

---

### Post by PTo on 2008-08-28
Thanx again! :) 

For the other question I will wait for the end of your vacation or for another person who knows the answer.

Have a nice vacation!

---

### Post by Caly08 on 2008-09-04
I've installed the cclfox on my Ubuntu 8.4 the problem i'm encountering is the coping of the two files CA.pem and cert.pem to .cclfox.

1. I don not find the .cclfox folder in my home folder.  My user account name is *user* so my home folder is /home/user

2. I've copied the two files to the folder /home/user/ and when I go the the command prompt I get this error [I][E]File "cert.pem" not found!!
Aborted[/I] when i type cclfox:  bellow is the full display of what i've done

user@user-desktop:~$ cclfox
[E]File "cert.pem" not found!!
Aborted
user@user-desktop:~$

What do I do for it work?

---

### Post by Caly08 on 2008-09-04
I've installed the cclfox on my Ubuntu 8.4 the problem i'm encountering is the coping of the two files CA.pem and cert.pem to .cclfox.

1. I don not find the .cclfox folder in my home folder.  My user account name is *user* so my home folder is /home/user

2. I've copied the two files to the folder /home/user/ and when I go the the command prompt I get this error [I][E]File "cert.pem" not found!!
Aborted[/I] when i type cclfox:  bellow is the full display of what i've done

user@user-desktop:~$ cclfox
[E]File "cert.pem" not found!!
Aborted
user@user-desktop:~$

What do I do for it work?

---

### Post by Script Warlock on 2008-09-04
@PTO unfortunately it's not yet implimented as far as i know.....

@Calyo08 what i did is i pressed the folder option "view hidden file" and there i saw the file .cclfox...try to add a folder and name it .cclfox and put all the .pems inside it.

---

### Post by Caly08 on 2008-09-04
boyet Thank you for your help it has worked.

---

### Post by Script Warlock on 2008-09-04
cheeers.......:)

---

### Post by Caly08 on 2008-09-05
> **loell said:**
> [SIZE="4"]for the cafe owners that run ubuntu[/SIZE] :)
**server pic**
[IMG]http://farm4.static.flickr.com/3024/2603649754_94d794ddb5.jpg?v=0[/IMG]
**clients pic **
[IMG]http://farm4.static.flickr.com/3130/2603649238_5ea20ed4cf.jpg?v=0[/IMG]

pics by [Boyet]("http://ubuntuforums.org/member.php?u=299765")
couple more [here]("http://www.flickr.com/photos/27901408@N03/")

________________________________________________________________________________

**project site:** [http://ccl.sourceforge.net/]("http://ccl.sourceforge.net/")
**note:** the packages are made for hardy heron

[COLOR="Red"]**server side setup:**[/COLOR]

download and install these packages respectively
1. [ATTACH]68258[/ATTACH]
2. [ATTACH]68256[/ATTACH]

after installing the above two. 
download and copy these files

[CA.pem]("http://ccl.sourceforge.net/tmp/CA.pem") and [cert.pem]("http://ccl.sourceforge.net/tmp/cert.pem") to **.cclfox** in your home directory

to run the server software: run **cclfox** in the command line or launcher.


[COLOR="Red"]**Client side or Workstation setup**[/COLOR]

download and install these packages respectively

1. [ATTACH]68257[/ATTACH]
2. [ATTACH]68255[/ATTACH]


after installing the above two. 
download and copy these files

[CA.pem]("http://ccl.sourceforge.net/tmp/CA.pem") and [cert.pem]("http://ccl.sourceforge.net/tmp/cert.pem") to **.cclfox** in your home directory

note: yes,  same certificate files as the server

to run the client software you can run this at startup or in the command line

```
cclcfox -host <server> -name <myname>
```

where <server> is the local ip address of the server
 and  <name> is the name of your workstation ie(pc1, pc2 ..) , any name will do.

to run this on startup in ubuntu/gnome 
add the above in **System** menu --> **preferences** --> **sessions **
________________________________________________________________________________________
**Tips**

[1. Setting up tarifs]("http://ubuntuforums.org/showpost.php?p=5571789&postcount=44")

[2. Basic security measures]("http://ubuntuforums.org/showpost.php?p=5304664&postcount=34")

Hello Can some body help me with setting up the client

I've installed both libcclc.deb and cclcfox.deb but I can't find .cclfox in my home folder on the client machine even when I show hidden folders.  Please help?

---

### Post by loell on 2008-09-05
if you can't find the directory, just create it. same thing as boyet intsructed you. and yes, even on the client side.

---

### Post by Script Warlock on 2008-09-05
boss loell etong package ng ccl mo pwede ba magrun sa intripid ibex? bka upgrade ako sa mga pc's ko this november to 8.10....

astig ka talaga boss may archive ka na ha atleast hindi masyado madugo maghanap sa mga kinakailangan ng desktop users...keep on going sir importante sa amin ang mga nagawa mo sa ubuntu community...

at ty pala sa package ng ccl simple na lang ang installation..pero kung may konting panahon ka sa timer na to pwede try mo modify na may block timing at pang-windows client(wala akong M$ but for the sake sa mga nangangailangan)..nagtry akong magawa para sa M$, awtz hindi pa talaga kaya ng powers ko at time....

---

### Post by loell on 2008-09-05
yup,  it will most likely run in intrepid :)

but in case it won't just bump me.. :D


(pag nagka windows partition ako, baka makagawa ako nang para sa windows, kahit para sa client man lang ;) )

Ah.. sus.. salamat sa pa-puri, walang ano man yun. :lolflag:

---

### Post by Caly08 on 2008-09-08
I copied the files on the home folder without creating a file and it worked.  I like your input.  Thank you all for your help.  I was able to do this the same day I posted the request.  I forgot to inform everyone it has worked.  Now I have another question.  How do I disable terminal and configure the basic security plus how do I put the cclcfox to run at start up?

---

### Post by Script Warlock on 2008-09-09
maybe you can hide it but not to disable, it might be useful in some way...right clik the main menu and choose edit menus>>>clik the accessories and untick the terminal and your done....

for security pls read this:
[http://ubuntuforums.org/showpost.php?p=5304664&postcount=34](http://ubuntuforums.org/showpost.php?p=5304664&postcount=34)

---

### Post by Caly08 on 2008-09-09
> **BatsotO said:**
> Just adding..
I've been use cclfox for a while and by far it's a neat program.

1.You might need to add :

/usr/lib
/usr/local/lib

in the /etc/ld.so.conf and do ldconfig.

2. You can change the lock screen display on the client by creating some neatest picture you can think of, save it in gif and name the picture lockpix (therefore lockpix.gif) and place it in the .cclcfox folder (not cclfox in the client side) along with the pems files.

3. if you want to shutdown and reboot client pcs remotely, chmod 7755 the /usr/bin/shutdown and /usr/bin/reboot.

4. Secure your wokrstations, you don't want any naughty user with some linux knowledge do process listing and send kill signal to terminate the cclcfox application, or delete it from the start up list. I disable terminal, virtual consoles and gnome-session-properties in my workstations to at least securing my setting (along with desktop locker and some gconf editing).

5. The installation wasn't that hard ( I wonder why so many tutorial on installation but so few on how to operate things). The most difficult to figure in my experience was tariff setting. I dont want user who use the wokstation for 5 minutes to pay for the whole hour, so I have to calculate per minute charge and set them minute per minute

6. There are more than one tariff scheme, so you can set it the way you needed. (this is a big plus)

7. Member first login will be their account number id and the password is also their account number id, from there the member can set their own password, then they can use their own login name and passord. 


That's all I can remember right now.

I'm new to Linux Ubuntu and some of the things you are saying make sense but how to go about it is a very different thing.

1. by adding /usr/lib and /usr/local/lib in the /etc/ld.so.conf what do you achieve?  ldconfig what do you do with this file.

2.  How do you actually disable the terminal.

3.  How do you make the software to run at start up?

4.  Thank you for the tutorial on tariff it was of good help.

Paul.

Paul.

---

### Post by mitchi on 2008-09-16
Ayos ang cafe con leche, need further testing para sa actual network ko. having some difficulty with setting tarriffs. and checking logs.

One more thing, dun sa post ni boyet, may screenshot cya ng desktop nya, using remote desktop viewer. pano mag-configure nun? tried doing it on my own, pero laging error message "connection closed". ano ba ang requirements nito at pano ba i-configure?

---

### Post by loell on 2008-09-16
> **mitchi said:**
> 
One more thing, dun sa post ni boyet, may screenshot cya ng desktop nya, using remote desktop viewer. pano mag-configure nun? tried doing it on my own, pero laging error message "connection closed". ano ba ang requirements nito at pano ba i-configure?

where? at the first post?

how did you configure the remote pc, before making a remote desktop connection?

---

### Post by dmurey on 2008-09-25
Am not very good at explaining things but, Once u have cafe con leche running, to put block timing (charging by block) you go to tarif and add price. If you want upto 10minutes to cost 5p and the next 10minutes to cost 4p and the next 104p nad the next 10 3p, for infinity, u add as follows

minutes 10 price 5
minutes 20 price 9
minutes 30 price 13
minutes 40 proce 16
minutes 50 price 19
minutes 60 price 22
minutes 70 price 25
and you keep adding till you reach the level you want after which the price per hour applies
u can transfer, continue ar pause a session or add products like soda or print outs using the add products.

Does any one know how to install the same in windows?

---

### Post by BatsotO on 2008-10-22
In case anyone still interested.

You can disable terminal aka gnome-terminal by changing the permission its permission, basic stuff like sudo chmod go-x /usr/bin/gnome-terminal will do.
Of course there still be other terminal in case you need one but it less commonly known so fewer people would know ccl vulnerability.

You can disable alt+ctrl+fx by renaming the tty(x) files in /etc/event.d.

Once again the point is to restrict users from listing the process and kill the cclcfox. if needed you can also changing permission on gnome-system-monitor.

For running the program at start-up youll need to go to preference -> session and add cclcfox -host <your server ip> -name <workstation name>
You'll need to create a folder called .cclcfox for client and put CA.pem & cert.pem in it.

You may also need to change the permission of the autorun folder in folder .config so no user can delete your autorun programs, also you may need tochange permission on gnome-session-properties, am i paranoid or what?

I believe what we achieve by adding those lines in ld.so.conf and do ldconfig is that the ccl can now acces the shared library it needed to run, thats all i know.

 This maybe late reply, but i have proved that man can survive without internet, at least for few months.

---

### Post by Script Warlock on 2008-10-24
batsoto i heard about this **gbilling inet timer** made from your country have you heard this too?...

---

### Post by raxso on 2008-10-26
Caly08,

if you want to disable gnome-terminal you need to perform this

sudo chmod go-rx /usr/bin/gnome-terminal 

This will remove read and execute permission for the members of the group and others of gnome-terminal thus removing the permission to execute the program, beware because only the root can execute this program to bring back the permission just execute

sudo chmod go+rx /usr/bin/gnome-terminal 

this will bring the default permission... hope this helps.  :)

---

### Post by BatsotO on 2008-11-01
> **boyet said:**
> batsoto i heard about this **gbilling inet timer** made from your country have you heard this too?...

I hear it from you, I did have much time on the net as much as i use to so i miss this one.

I will try this one.. thank you.

---

### Post by daoud7 on 2008-11-07
Ubuntu 8.04

Everything went well with the install of the server side of CCL.

But on the client side it is much different.

I am typing in the following line in a terminal window:
cclcfox -host 192.168.2.40 -name pc45 -nossl

I then sit back and wait. It repeatedly tries to find the server.

Maybe somebody can clarify the syntax of this command. Especially the IP address and the name.

I have seen explanations that say these are not critical settings, but it seems that my PC doesn't agree!:(

Do I need to set the ipaddress of the server (and if so, how?).
Do I have to give the name of the server or client? (I assume that this name should be the one shown in a terminal window?)

I’m sure that I am missing the obvious, but I just can’t get it to work!

Any help would be much appreciated.

---

### Post by Script Warlock on 2008-11-07
howto installation guide..
[http://ubuntuforums.org/showpost.php?p=7915222&postcount=308](http://ubuntuforums.org/showpost.php?p=7915222&postcount=308)

---

### Post by kstan_79 on 2008-11-26
I'd update some source code in cclcfox, so that when play 3d game the cclcfox client still can interrupt the end use under pre-pay condition. Below is the info at sf.net forum. hope this help.
[http://sourceforge.net/forum/forum.php?thread_id=2604695&forum_id=385526](http://sourceforge.net/forum/forum.php?thread_id=2604695&forum_id=385526)

Please test it and feed back to me when there is a bugs.
ks

---

### Post by loell on 2008-11-26
> **kstan_79 said:**
> I'd update some source code in cclcfox, so that when play 3d game the cclcfox client still can interrupt the end use under pre-pay condition. Below is the info at sf.net forum. hope this help.
[http://sourceforge.net/forum/forum.php?thread_id=2604695&forum_id=385526](http://sourceforge.net/forum/forum.php?thread_id=2604695&forum_id=385526)

Please test it and feed back to me when there is a bugs.
ks

can you generate a patch instead, so that it will be easier for others to test?

---

### Post by kstan_79 on 2008-11-26
Unfortunately I don't know how to generate & apply the patch.

It is better if the developer can add me as programmer in sourceforge so I can submit the change inside.

Regards,
Ks Tan

---

### Post by Script Warlock on 2008-11-27
happy to hear some movements for CCL...

welcome to the haws kstan_79

---

### Post by Script Warlock on 2008-11-29
bro loell help ayaw na maopen ang CCL sa client computer after upgrading to intripid ibex....wala akong binago sa client nag-upgrade lang ako tapos kada open sa ubuntu 8.10 ayaw na maopen ang ccl, some remedy?

---

### Post by loell on 2008-11-29
> **boyet said:**
> bro loell help ayaw na maopen ang CCL sa client computer after upgrading to intripid ibex....wala akong binago sa client nag-upgrade lang ako tapos kada open sa ubuntu 8.10 ayaw na maopen ang ccl, some remedy?

ganun? nakuh, parang gagawa nanaman ako nang package for intrepid, ano pala sa sa command line?

---

### Post by Script Warlock on 2008-11-29
naka startup kc ccl tapos di ko maopen kahit sa login options saan ba pwede maglogin na parang safe mode...

---

### Post by loell on 2008-11-29
> **boyet said:**
> naka startup kc ccl tapos di ko maopen kahit sa login options saan ba pwede maglogin na parang safe mode...

grub options,may safe mode doon.

---

### Post by Script Warlock on 2008-11-29
ok naopen na tapos paano tanggalin to startup script ng ccl at sa permisison is no delete anu chmod to change the permission....


ok ok bro out muna ako alam mo na yung kanina 10k hehehhe share ko to sa mga open source project ang kalahati....

---

### Post by loell on 2008-11-29
> **boyet said:**
> alam mo na yung kanina 10k hehehhe share ko to sa mga open source project ang kalahati....

share mo sa akin :lolflag: kailangan ko nang bagong monitor! :lolflag:

o sya, mamaya na.. mananaghali pa ako. :D

---

### Post by Script Warlock on 2008-11-29
hehehe np bahinbahinon nato apil uban....pm me your bank account...hehehe

---

### Post by loell on 2008-11-29
> **boyet said:**
> ok naopen na tapos paano tanggalin to startup script ng ccl at sa permisison is no delete anu chmod to change the permission....


in the terminal, just do **startx** , then remove ccl startup in preference --> session.

---

### Post by Script Warlock on 2008-11-29
OT: got the package and as you said i'm cleared and hired but i refuse kc nga andami ko na papel sa buhay....hihihi a post dated chek ang imong bahin is coming next week hehehehe pm lang the details of ur account....and the rest padlong sa mahunahunaan nga pinoy open source project especially the timer for inet...

ok i deleted the ccl tapos eto naginstall ulit sa .deb m pero ganun pa rin. dito sa server nagdoble ang display na client workstation pc2 and pc2? i'm confused...lalo na problema sa auto eth0 ng 8.10 so paano kaya nagkaganito after upgrading..the dependencies are fine..i have also created the .cclfox and dunno why i was locked down again after reboot

---

### Post by kstan_79 on 2008-11-29
Seems like this system is working quite well after some testing(especially after applied patch for 3d games), however it is much better if we can include the code for wakeonlan in cclfox. Anybody putting afford for it?

---

### Post by loell on 2008-11-29
> **boyet said:**
> 
ok i deleted the ccl tapos eto naginstall ulit sa .deb m pero ganun pa rin. dito sa server nagdoble ang display na client workstation pc2 and pc2? i'm confused...lalo na problema sa auto eth0 ng 8.10 so paano kaya nagkaganito after upgrading..the dependencies are fine..i have also created the .cclfox and dunno why i was locked down again after reboot

thats weird indeed, lemme do some more investigating, if we couldn't pin down the issue, then, i' rebuild the package for intrepid.

and why are you upgrading you clients again? ;)

slight OT: yeah gbilling is worth looking at, if they can just translate it to english. :)

---

### Post by Script Warlock on 2008-11-29
some of the hardwares i tweak in 8.04 has been working at 8.10 digicams, cellphones, usb devices are all working good in 8.10. dami kc dinadala ng mga customer na mga gadgets and 8.10 has it all(almost).usually i only upgrade the OS not clean install kc andami na files ng mga customer at they like much becoz of gyachi and skype..ngayon na 8.10 lalong gumana ang skype sa gigabyte na mobo ko. 

ya gbilling is pinagsamang nettime at handycafe pero sabi nila may final release daw english version. i have tested it in ubuntu machines dami pa bugs kaya bumalik ako sa ccl, sayang tong project na to(ccl) pinabayaan ni tizoc(siya ba yung creator nito?) kung marunong lang ako sa programming paganahin ko to at multi-os pa..

cge bro kung may time ka lang at pasensya sa man kung maabala ka sa mga request namin ha ganun kc talaga mga newbies request to the max. pero balang araw kami na naman ang nasa lugar mo..more power bro

---

### Post by loell on 2008-12-01
i think i now have the slightest idea on why the duplicates, it might have something to do with ssl version? anyway, i'll just build the package set for intrepid. :)  I might have to incorporate the 3d game fix.

---

### Post by Script Warlock on 2008-12-01
yes exactly the ssl that was the output sa cli during launching of ccl may warning error though it launch pero locked down na client ccl ok hitayin ko na lang package mo para 8.10.

---

### Post by loell on 2008-12-01
> **boyet said:**
> yes exactly the ssl that was the output sa cli during launching of ccl may warning error though it launch pero locked down na client ccl ok hitayin ko na lang package mo para 8.10.

ok :) i'll be uploading this tomorow, hopefully you can test this by then. :D

---

### Post by loell on 2008-12-02
Intrepid packages, here it is..

[http://www.mediafire.com/file/oknzydmymj1/ccl-client-pack.tar.gz]("http://www.mediafire.com/file/oknzydmymj1/ccl-client-pack.tar.gz")

[http://www.mediafire.com/file/itzyfzlwzly/ccl-server-pack.tar.gz]("http://www.mediafire.com/file/itzyfzlwzly/ccl-server-pack.tar.gz")

---

### Post by Script Warlock on 2008-12-02
ok ok testingan ko na karon naapil na to ang kang kstan_79?

maayo siguro iapil na lang na sa imong ppa para adto ra mi magpili sa among gamitonon

---

### Post by Script Warlock on 2008-12-02
yes its working bro, paano pala maprotektahan to ccl launcher sa desktop para di madelete ng mga customer pati folder ng cclfox at libccl. at paano rin gawin ang start-up script parehas ba maggawa ng startup script ng conky?

bro naa ko indo file sa cclfox0.7.1-2.deb baka pwede to gamitin natin pang intripid mas ok yung interface.. pwede rin kaya natin to gawing english ang language? indo kc gamit nila

---

### Post by loell on 2008-12-02
> **boyet said:**
> ok ok testingan ko na karon naapil na to ang kang kstan_79?

maayo siguro iapil na lang na sa imong ppa para adto ra mi magpili sa among gamitonon

did an initial evaluation of kstan_79 code snippets, i didn't include it, as i'm not really sure why data types changes should be significant.

yes, i've already considered having it in my PPA.. but..  the CCL's config files is messy I could not generate proper deb files from it :(

---

### Post by Script Warlock on 2008-12-02
ok lang for me yung kay kstan_79 na issue wala naman akong games sa mga workstaion..well ok na ako sa version natin bsta may magamit lang na timer for ubuntu.

yun lang sa how to protect a folder or app launcher para di madelete ng kostomer

---

### Post by daoud7 on 2008-12-02
Ubuntu

Having used CCL client for some days without problem, I introduced another language (JP) onto the client machine.

Having re-set the language I now find that CCL's client lockdown/logo icon starts up and then disappears. The language issue might have nothing to do with the problem since there have also been a few Ubuntu updates in the same period.

Various attempts to re-start fail.

I noticed that this was mentioned in an earlier post, but no real solution was given.

Any solutions or ideas?

---

### Post by Script Warlock on 2008-12-02
> **daoud7 said:**
> Ubuntu

Having used CCL client for some days without problem, I introduced another language (JP) onto the client machine.

Having re-set the language I now find that CCL's client lockdown/logo icon starts up and then disappears. The language issue might have nothing to do with the problem since there have also been a few Ubuntu updates in the same period.

Various attempts to re-start fail.

I noticed that this was mentioned in an earlier post, but no real solution was given.

Any solutions or ideas?

did you run ccl during startup?

---

### Post by loell on 2008-12-02
> **boyet said:**
> 
yun lang sa how to protect a folder or app launcher para di madelete ng kostomer

you could

```
sudo chown root:root Desktop
``` :)

or

```

cd Desktop

sudo chown root:root *.desktop


```

locking icon panels try **pessulus**

---

### Post by daoud7 on 2008-12-02
> **boyet said:**
> did you run ccl during startup?

Yes, of course - runs from Session...

---

### Post by Script Warlock on 2008-12-02
> **daoud7 said:**
> Yes, of course - runs from Session...

i'm not sure but maybe its all about the arrangements of proccesses or the startup script..can u post your script for ccl startup.

---

### Post by daoud7 on 2008-12-02
> **boyet said:**
> i'm not sure but maybe its all about the arrangements of proccesses or the startup script..can u post your script for ccl startup.

If you tell me the filename and location - willingly!

Or are you talking about the syntax for the command line? Should be OK since it was not changed. It also shows up OK on the server.

---

### Post by loell on 2008-12-02
try reverting to  former language setting.

---

### Post by daoud7 on 2008-12-03
> **loell said:**
> try reverting to  former language setting.

Already did - no difference.

Only other thing is to totally un-install the language choice. But an internet cafe here needs some language alternatives. JP especilly.

The client program seems to be running and shows briefly when closing down too.

---

### Post by loell on 2008-12-03
and this is all hardy heron machines?

---

### Post by Script Warlock on 2008-12-03
thats strange....anu kaya problema di ko rin magets but trying to find also the culprit

---

### Post by daoud7 on 2008-12-03
> **loell said:**
> and this is all hardy heron machines?

Yes! The one in question is Ubuntu.

I have others for Xubuntu.

---

### Post by daoud7 on 2008-12-03
> **boyet said:**
> thats strange....anu kaya problema di ko rin magets but trying to find also the culprit

Which means?

---

### Post by daoud7 on 2008-12-03
One more bit of information:

The client seems to partly freeze after the start-up.

The mouse moves and it's presence is shown by clicking or mouse-over.

But no application will start, no error dialog. Even the closedown switch only responds by showing it has been "pressed".

Terminal access, however, seems to be normal: <Ctrl><Alt><Shift><Fn>
giving a normal terminal login, etc.

---

### Post by kstan_79 on 2008-12-03
Hi, I'm back here.
Can I know somebody able to compile cclcfox client in windows? I need to know the step by step guide so this solution work in both windows and Linux. I'd test windows version client seems like got some problem in windows vista.


Regards,
Ks Tan

---

### Post by loell on 2008-12-03
> **daoud7 said:**
> Yes! The one in question is Ubuntu.

I have others for Xubuntu.

no, the versions? is it 8.04? 8.10? ..

---

### Post by daoud7 on 2008-12-04
> **loell said:**
> no, the versions? is it 8.04? 8.10? ..

I didn't know CCL was version specific!  :-o

Ubuntu 8.04

---

### Post by loell on 2008-12-04
> **daoud7 said:**
> I didn't know CCL was version specific!  :-o

Ubuntu 8.04


CCL is dependent on specific version component ie( libfox 1.4, ssl< too tired to look up the verion> and glib 2.0)

i'm out of ideas, probably a last shot would be to rearrange your session startup or just make cclc run as last on the startup list.

---

### Post by daoud7 on 2008-12-04
Seems to make sense.

I thought of doing this after an earlier comment and actually removed a few non-essential auto-starts. Again no difference...

But I couldn't find an obvious way to *re-organise* the session programs. Can you give me a pointer?

---

### Post by loell on 2008-12-04
> **daoud7 said:**
> 
But I couldn't find an obvious way to *re-organise* the session programs. Can you give me a pointer?

i just realized, that you couldn't reaarange the order :( , it would seem the last input is alway the bottom item. :(

---

### Post by daoud7 on 2008-12-04
> **loell said:**
> i just realized, that you couldn't reaarange the order :( , it would seem the last input is alway the bottom item. :(

Aaargh!!:cry:

So what to do now? We already know (I think) that a re-install doesn't work!

---

### Post by daoud7 on 2008-12-04
Just as a counter-thought:

How does one go about totally removing CCL from the client system?

Is it different for the server part?

(Maybe it is possible to re-install by the long route).

---

### Post by loell on 2008-12-04
last marble for the sling,

remove ccl item at start up session..

save this 

```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Name=cafe con leche
Type=Application
Exec=cclcfox -host [COLOR="Red"]<server>[/COLOR] -name [COLOR="Red"]<myname>[/COLOR]
X-GNOME-Autostart-enabled=true




```


**/.config/autostart/**  as **ccl.desktop**

---

### Post by loell on 2008-12-04
> **daoud7 said:**
> Just as a counter-thought:

How does one go about totally removing CCL from the client system?

Is it different for the server part?

(Maybe it is possible to re-install by the long route).

it should be the same as e any deb package in ubuntu / debian land,

once when you uninstall the  package, and that's it. the only trace left is the .cclcfox directory which only house the cert.pem file.

---

### Post by daoud7 on 2008-12-04
> **loell said:**
> it should be the same as e any deb package in ubuntu / debian land,

once when you uninstall the  package, and that's it. the only trace left is the .cclcfox directory which only house the cert.pem file.

My experience of deb/ubuntu removals is that there is always some config or hidden file left somewhere. That's why I asked.
:-P

---

### Post by loell on 2008-12-04
> **daoud7 said:**
> My experience of deb/ubuntu removals is that there is always some config or hidden file left somewhere. That's why I asked.
:-P

the config files will have no effects whatsoever, it is left at the user's disposal.

it will  be used only when you reinstall the program that uses the particular config file.


do try  post 118

---

### Post by daoud7 on 2008-12-04
> **loell said:**
> last marble for the sling,

remove ccl item at start up session..

save this 

```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Name=Screenlets Daemon
Type=Application
Exec=cclcfox -host [COLOR="Red"]<server>[/COLOR] -name [COLOR="Red"]<myname>[/COLOR]
X-GNOME-Autostart-enabled=true



```


**/.config/autostart/**  as **ccl.desktop**


The plot thickens!

I just saved the above code to desktop (preliminary to moving it to .config/autostart).

Then I cleared to the desktop. Much to my surprise I saw, parked on the desktop, an icon labelled "Screenlets Daemon". On clicking this icon I find it spawns one CCL icon for each click!!

Duhh!! I think I just worked out that this is roughly what this code is supposed to do.
Sorry!

---

### Post by daoud7 on 2008-12-04
OK I finally got the code into the right place.

/root/.config/autostart/ccl.Desktop   Right?

And the sum total of the effort is that cclc doesn't start up at all.

Maybe I have something wrong with the file permissions? Root?

A bit strange since it starts OK on the /user/Desktop...

---

### Post by loell on 2008-12-04
> **daoud7 said:**
> OK I finally got the code into the right place.

/root/.config/autostart/ccl.Desktop   Right?

And the sum total of the effort is that cclc doesn't start up at all.

Maybe I have something wrong with the file permissions? Root?

A bit strange since it starts OK on the /user/Desktop...

no, not in **root**;)

just in **/home/[COLOR="Red"]your_user_name[/COLOR]/.config/autostart/ccl.desktop**

---

### Post by Script Warlock on 2008-12-04
bro loell parang unti-unting bumobuo ang documentation para sa ccl ah..

some tweakings, troubleshooting atibpa.. gusto ko na yata matuto ng c programming para makatulong ako sa timer na to..maganda sana pero kung sabi mo tupsy-turvey ang program na to e di subukan ko nga re-arrange after a year. pagkatapos skwela c++, c...tapos kmustahin ko si tizoc kung may plano pa ba sya sa ccl na to.

---

### Post by loell on 2008-12-04
> **boyet said:**
> bro loell parang unti-unting bumobuo ang documentation para sa ccl ah..

nah.. just troubleshooting. :)

> **boyet said:**
> 
some tweakings, troubleshooting atibpa.. gusto ko na yata matuto ng c programming para makatulong ako sa timer na to..maganda sana pero kung sabi mo tupsy-turvey ang program na to e di subukan ko nga re-arrange after a year. pagkatapos skwela c++, c...tapos kmustahin ko si tizoc kung may plano pa ba sya sa ccl na to. 

not to sound like a python fan, heheh, but yeah, if this is done in python things would have been easier and faster developmentwise. ;)

---

### Post by daoud7 on 2008-12-05
> **loell said:**
> no, not in **root**;)

just in **/home/[COLOR="Red"]your_user_name[/COLOR]/.config/autostart/ccl.desktop**

Still doesn't seem to work. It seems not to start at all.

Again starting (or open) on the file starts it OK.

Is there a possible permissions issue with the startup?

---

### Post by loell on 2008-12-05
> **daoud7 said:**
> 
Is there a possible permissions issue with the startup?

the startup path which we put the *.desktop is owned by you (the normal user) , it always start as far as i know, whenever you log in with a gnome session.

could it be, that you are using a different account / or username? when you want to startup ccl[COLOR="Red"]c[/COLOR]? or perhaps a different desktop environment when you logged in your account?

am now blank empty with it, not starting up. :(

---

### Post by BatsotO on 2008-12-13
Did you mean cclc can run from command line but wont autostart?

---

### Post by daoud7 on 2008-12-13
> **BatsotO said:**
> Did you mean cclc can run from command line but wont autostart?

It kind of looks that way. :-(

There is a suggestion that it starts (icon appears for very short time) and then doesn't.

The best *suggestion* made is that I have another desktop running. But, if so, it is an accident! And how do I check anyhow?
:confused:

---

### Post by daoud7 on 2008-12-13
> **loell said:**
> the startup path which we put the *.desktop is owned by you (the normal user) , it always start as far as i know, whenever you log in with a gnome session.

could it be, that you are using a different account / or username? when you want to startup ccl[COLOR="Red"]c[/COLOR]? or perhaps a different desktop environment when you logged in your account?

am now blank empty with it, not starting up. :(

AFAIK I have a normal desktop. The launcher which was supplied sits on the desktop. The account being used for the launcher/ cclc is a normal user account.

There *could* be a secondary desktop of some sort, but if so it is accidental or a left-over from the Japanese language modules which were installed/removed.

Maybe I shall have to format the HDD and do this machine again...

---

### Post by BatsotO on 2008-12-14
In my experience, when cclc did not come out well (blank or appear the disappear), running it from either autostart or command line will give the same result. It it runs with nossl option that it will be the server to blame, or the network. It is a bit strange if it runs with the command line but did not run from autostart assuming that the line in autostart is exact same with the command line. In my machine, ccl will lock the desktop if it run, well or faulty, so the desktop is useless so i have to kill cclc.
Testing in on another account in the same machine will be valuable for tracing the problem.

---

### Post by kstan_79 on 2008-12-14
After few days monitor, the best autorun script for cclcfox as below.
*You must create .cclcfox in home directory if you apply my patch.
However, just for your information I only understand english, enquiry please post in english.

> 
#!/bin/bash
sleep 1
COUNT=0;
SERVER="192.168.1.2"
ISLOCK=""
USESSL="-nossl"
PC="computername"

cclcfox -name $PC -host $SERVER $USESSL  -islock &
sleep 1
echo start
while [ 0 -eq 0 ]; do
COUNT=`ps aux | grep "cclcfox -name" | grep -v grep | grep -v gedit | wc -l`
echo "total $COUNT process"
if [ $COUNT -ge 1 ]; then
echo "skip"
else
  if [ -f ~/.cclcfox/islock ]; then
   ISLOCK="-islock";
  else
   ISLOCK="";
  fi

  cclcfox -name  $PC -host $SERVER $USESSL $ISLOCK &

fi
sleep 1

done


---

### Post by daoud7 on 2008-12-14
> **BatsotO said:**
> In my experience, when cclc did not come out well (blank or appear the disappear), running it from either autostart or command line will give the same result. It it runs with nossl option that it will be the server to blame, or the network. It is a bit strange if it runs with the command line but did not run from autostart assuming that the line in autostart is exact same with the command line. In my machine, ccl will lock the desktop if it run, well or faulty, so the desktop is useless so i have to kill cclc.
Testing in on another account in the same machine will be valuable for tracing the problem.

 As previously mentioned, the CCLC logo briefly appears and disappears at startup. On some occasions it appears on machine shutdown too.

I will create another user account and try another install.

I wondered if the JP install had done something to the desktop relating to the Kanji in/output.

---

### Post by daoud7 on 2008-12-14
> **kstan_79 said:**
> After few days monitor, the best autorun script for cclcfox as below.
*You must create .cclcfox in home directory if you apply my patch.
However, just for your information I only understand english, enquiry please post in english.

Thx for this, but what am I supposed to do with it?

How do I incorporate an autorun script of this sort?

And what exactly am I patching?

---

### Post by BatsotO on 2008-12-14
Just a suggestion. My previous billing management is using LAMP, so it can run simply on client with any browser. It is stable and robust, sadly it lack of key features like membership and multiple tariff scheme. It is copyrighted but if there's someone with good php-mysql knowlegde could rebuild or build a free version of web based billing management, it will be great.

At this moment I have cclc problem to, it start then disappear like you mentioned, but it still run on the background so the desktop is locked. when i kill and run it from command line it start well. I'm running out of idea too, but maybe it has to do with bonobo thing because previously i had bonobo error.

---

### Post by daoud7 on 2008-12-15
> **BatsotO said:**
> Just a suggestion. My previous billing management is using LAMP, so it can run simply on client with any browser. It is stable and robust, sadly it lack of key features like membership and multiple tariff scheme. It is copyrighted but if there's someone with good php-mysql knowlegde could rebuild or build a free version of web based billing management, it will be great.

At this moment I have cclc problem to, it start then disappear like you mentioned, but it still run on the background so the desktop is locked. when i kill and run it from command line it start well. I'm running out of idea too, but maybe it has to do with bonobo thing because previously i had bonobo error.

Y, I had this earlier. I'm relieved that I am not the only one with the problem!

The cclc ran invisibly in the background thus locking the whole of the desktop. It was necessary to use low-level methods to escape!

I don't remember any bonobo item though...

---

### Post by BatsotO on 2008-12-15
Maybe this help. I'm encountering error, nautilus vs bonobo thing, and when nautilus restart it put cclc in the background, so I search any file in the home directory with any cclcfox line and deleting them along with the folder, the nautilus folder and gconf file, recreate ccl in session-properties and now the autostart is back.

---

### Post by daoud7 on 2008-12-17
> **BatsotO said:**
> Maybe this help. I'm encountering error, nautilus vs bonobo thing, and when nautilus restart it put cclc in the background, so I search any file in the home directory with any cclcfox line and deleting them along with the folder, the nautilus folder and gconf file, recreate ccl in session-properties and now the autostart is back.

Could very well have something to do with nautilus. But is it possible to just un-install nautilus?

Maybe a later nautilus install won't do this? What do you think?

---

### Post by BatsotO on 2008-12-17
I think it's just some configuration need to be refresh, because when nautilus has problem, in my case with bonobo, cclc have no way tp place itself on the desktop so it thrown to background. reinstalling nautilus wouldn't be necesary. Because I clone the whole pcs in my network of ubuntu, sometime there is left over hostname in configuration that cause nautilus wont start, and because nautilus will restart while cclc already running, there we have the problem, at least i thought so. ](*,)

---

### Post by Script Warlock on 2008-12-17
> **BatsotO said:**
> I think it's just some configuration need to be refresh, because when nautilus has problem, in my case with bonobo, cclc have no way tp place itself on the desktop so it thrown to background. reinstalling nautilus wouldn't be necesary. Because I clone the whole pcs in my network of ubuntu, sometime there is left over hostname in configuration that cause nautilus wont start, and because nautilus will restart while cclc already running, there we have the problem, at least i thought so. ](*,)

so do we think nautilus is the culprit or the ccl itself....

---

### Post by BatsotO on 2008-12-18
Well, I think it was not entirely nautilus fault, nor ccl, it just the way they communicates with each other, like i mentioned before my opinion is that the web based billing system is the best for it simplicity because it sole requirement is the web browser. Did deleting nautilus folder works for you?

---

### Post by daoud7 on 2008-12-18
[SIZE="3"][COLOR="Black"]nautilus on ubuntu[/COLOR]
[/SIZE]

Regarding the disappearing CCL icons etc.

I uninstalled nautilus AFAIK completely.

The computer still works.

The problem is solved!
:-)

---

### Post by Script Warlock on 2008-12-18
i don't have problem with nautilus before pero kung tinanggal ang nautilus anu kaya side fx or pwede pala to tanggalin?  anu ang pang-palit na file manager...:confused:

---

### Post by BatsotO on 2008-12-19
now ccl server error, it disappear, stating glib error something, see what i mean? web based billing is the best, i would gladly supply the basic php code from my previous billing and build it to meet our need.

---

### Post by loell on 2008-12-19
web based billing from scratch is easier said than done. what's your client component if its php on the server side?


i know cafepilot uses java.

---

### Post by BatsotO on 2008-12-19
practically only web browser solely to display he tariff to user, nothing more, it can be stored in webserver-gateway router, mine was on red-hat 7 or so and it still run fine today. If you have static ip address you can view the report from practically anywhere or even better, administer it off course with more security adjustment that can be easily done, very good for a network of i-cafe. 
It doesn't take too much resource and dependencies, when you upgrade ubuntu or any os you chose, you can do it painlessly. 
It can block outside connection so only logged user will have acces to the internet. you can by-pass ccl so easily by terminal.  
I once tested this [http://code.google.com/p/bios/](http://code.google.com/p/bios/) , i did not catch up with it progress, i wonder what it can do now.
I just recall that the thin-clients (hoary) need one important component, lynx, the start up script told lynx to contact the webserver/router, telling it that the client just logged in and need outside connection,  the web server will start the timing and count the tariff, the same procedure when the client logging out, lynx contact webserver, the webserver will stop the timing.

---

### Post by loell on 2009-01-02
i'm entertaining the idea of a web based cafe timer & billing,
what i have in mind is a google app engine (python) in the server side and pygtk in the client side, so.. will there be committed testers if.. remotely.. ever?

---

### Post by Script Warlock on 2009-01-02
> **loell said:**
> i'm entertaining the idea of a web based cafe timer & billing,
what i have in mind is a google app engine (python) in the server side and pygtk in the client side, so.. will there be committed testers if.. remotely.. ever?

ako and i'm wiling..kuha mo na package bro? yun na muna ha..teka eto proposal mo may kasama database para sa mga transactions?

ok din ang features ng bios pero it was made again for indo guys pero if we can write our own mas maganda cguro not only in english but also in tagalog...alam natin mas masarap ang timplang pinoy kompleto..

---

### Post by loell on 2009-01-04
> **boyet said:**
> ako and i'm wiling..

ok, give me some time to make a requirement analysis, it may be for  a while, i don't have extra time atm.

---

### Post by kstan_79 on 2009-01-08
> **daoud7 said:**
> Thx for this, but what am I supposed to do with it?

How do I incorporate an autorun script of this sort?

And what exactly am I patching?

Please refer back [http://sourceforge.net/forum/forum.php?thread_id=2604695&forum_id=385526](http://sourceforge.net/forum/forum.php?thread_id=2604695&forum_id=385526)

You need to change the source code, and recompile the source code.
After quite sometimes, I didn't receive any complain from Customer. 

After apply the patch CCL shall able to block full screen game/softwares when timeup. Eventhough it is not perfect(The calculation will reset at client side, but server won't effect). 
If some budget come down I can polish this software so it can turn pc on, do better calculation.

---

### Post by uplink.cu on 2009-01-23
I see that this is the good program for linux, but I need open Cybera Cerver in Lunux OS, you can help me??

:popcorn:thank

---

### Post by Script Warlock on 2009-01-23
ya cybera has a good features, do you mean porting to linux?

---

### Post by akim09 on 2009-01-25
i can't seem to find the .cclcfox file on my root directory please i am new to this we having to change to linux in our cafe help me pliz

---

### Post by Script Warlock on 2009-01-25
[http://ubuntuforums.org/showthread.php?t=777093&page=6](http://ubuntuforums.org/showthread.php?t=777093&page=6)

---

### Post by ismoke101 on 2009-01-26
:popcorn: koya koya koya di ko gets server lang ubuntu o yung buong shop? buong shop panu nag react mga customer:p just asking jejeje

---

### Post by BatsotO on 2009-01-30
> **akim09 said:**
> i can't seem to find the .cclcfox file on my root directory please i am new to this we having to change to linux in our cafe help me pliz

.cclcfox is a directory, you'll need to create it in your client's home directory, put ca.pem and cert.pem file's in it, and while you there you can also create a gif file that suit your need, name it lockpix.gif and put it in your .cclcfox directory. BTW the dot in every files and folders means they are hidden, juat press ctrl-h and nautilus will show them for you.

---

### Post by akim09 on 2009-02-22
> **boyet said:**
> [COLOR="Black"]

ang bilis!! heheh ayos to dami na pumapasok na info para sa mga inet operators na linux ang distro gamit.....

sir ok to ha pero may kunti problema lang sa startup kc dretso open yung CCLC tapos may time din na nagrun na sya pero di makita yung timer parang nasa ilalaim lang ng desktop ..ano kay to is it about the priority sa processes or something dapat kc after log-in maglock na ang desktop ng client with CCL pero dretso lang sya open...some ideas?

btw gamit ko etong 0.7.1 sana meron ding skin themes

yung sa cert pala ang ginawa ko copy paste lang sa text editor tapos save as _some names_ tapos right click ko ang file na _some names_ tapos click ang permission click lang yung box na allow executing file as program tapos lumabas na aresulta na .pem..tama ba ginawa ko? ano pala purpose ng mga yun .perm para saan yun?

sana makagawa din tayo para sa winXP[/COLOR]

boyot man thanks for this

i was just recently raided by microsoft in botswana and need to move over to ubuntu asap tried installation as per your instructions but can not get the launcher to run i am new to ubuntu though please help

---

### Post by Script Warlock on 2009-02-22
> **akim09 said:**
> boyot man thanks for this

i was just recently raided by microsoft in botswana and need to move over to ubuntu asap tried installation as per your instructions but can not get the launcher to run i am new to ubuntu though please help

pls refer to this post for manual installation: [http://ubuntuforums.org/showthread.php?t=777093&page=8](http://ubuntuforums.org/showthread.php?t=777093&page=8)

and for the .deb files it was located at loells ppa files pls clik loell ppa

---

### Post by kimesh1975 on 2009-02-24
i need the steps of how to install cafe con leche server and client please help

---

### Post by Script Warlock on 2009-02-24
pls refer to this post for manual installation: [http://ubuntuforums.org/showthread.php?t=777093&page=8](http://ubuntuforums.org/showthread.php?t=777093&page=8)

and for the .deb files it was located at loells ppa archives pls clik loell ppa archives....

we have the ticket module from publito at CCL forum, hope he will send the link for download ASAP....i am waiting for this feature a long time ago...pero di ko pa alam paano e-attache to sa CCLFOX or where to put it...

---

### Post by akim09 on 2009-03-02
hi,

i am new to Ubuntu and linux as whole. my cafe is based in gaborone , botswana africa, just last week Microsoft raided and shut down most cafe's in my city i was lucky had just installed ubuntu 8.10 on all my computers.

before i was using cybercafe pro 5.0 on windows, my problem now is getting a cafe programme for ubuntu as i am currently manually timing and this is killing me.

i tried following the steps you laid out, every thing goes well, but i do not know how to add the extra lines and to deal with .perm files i have to copy.

pliz can u help me with a detailed step by step install if u wouldn't mind pliz.

you help would be greatly appriciated.

---

### Post by loell on 2009-03-02
you can follow these commands for copying pem files.

for the clients
: assuming that you have already installed cafe con leche client side.
```

cd ~
mkdir .cclcfox
cd .cclcfox
wget http://ccl.sourceforge.net/tmp/cert.pem
wget http://ccl.sourceforge.net/tmp/CA.pem

```


for the server
```

cd ~
mkdir .cclfox
cd .cclfox
wget http://ccl.sourceforge.net/tmp/cert.pem
wget http://ccl.sourceforge.net/tmp/CA.pem

```

---

### Post by kilosan on 2009-03-17
If businessman wants to improve this timer. You can send it to
[CoFundOS.org]("http://cofundos.org/")

Also Cybera Server for Linux.

But you will need to chip in or donate for the money to be funded in improving this software.

---

### Post by Nemuel on 2009-03-18
> **boyet said:**
> pls refer to this post for manual installation: [http://ubuntuforums.org/showthread.php?t=777093&page=8](http://ubuntuforums.org/showthread.php?t=777093&page=8)

and for the .deb files it was located at loells ppa archives pls clik loell ppa archives....

we have the ticket module from publito at CCL forum, hope he will send the link for download ASAP....i am waiting for this feature a long time ago...pero di ko pa alam paano e-attache to sa CCLFOX or where to put it...

hey mr akim.am based in gaberone and am a computer guru.call me on this number and i will sort out the cafe con leche for you. 71252407.good day

---

### Post by Nemuel on 2009-03-18
hey akim. am in gaberone, a computer guru. call me to sort out this problem for you. 71252407

---

### Post by pmwangi80ke on 2009-04-12
hi,
ave been going through the old threads trying to find an answer to this.Please help me if you can.
Am using cclfox on ubuntu 8.04 for a cyber,only challenge is the logs, i installed SQL lite using add remove. Am able to open the database but it appears to be jumbled, all i can see is tables with numbers and figures which i cannot understand. please help me understand how to interprete it or is there any config i should do to make it readable.

mwangi.

---

### Post by daxumaming on 2009-04-12
I've been using SQLite Administrator to manage my SQLite DBs- it's a windows only app but works well on Wine. SQLite Browser's good, but I've been having problems with SQLite2.
Also check what app you're using, it may be encrypting its logs and you'll only access them from the app itself.

---

### Post by pmwangi80ke on 2009-04-20
thanks for your reply, am still having the same problem. the application am using is sqlite(SQL database browser) installed it from add/remove. I access by applications, programming, sqlite. Then i go to file,open database /home/user/.cclfox/cclfox.db, then i click browse data,i select session logs but all i see is a table with figures i cannot interpret. The interval column is filled with symbols i cannot be able to read.
Do i install the apllication in WINE? what can i do? please help me out.

mwangi.

---

### Post by Script Warlock on 2009-04-20
is this wht you mean?

---

### Post by daxumaming on 2009-04-20
if that's the case, then i believe it's encrypted.

---

### Post by slashdotfx on 2009-04-21
Yo SUP!? :D

just want to say hi from indonesia,
reading this thread, and sure thing it helps.
I've been running my internet cafe (with 
ccl as the billing system of course!)
for one and a half year,
running with feisty, and just a couple of days a go
upgrading to jaunty, sweet :popcorn:

---

### Post by Script Warlock on 2009-04-21
> **slashdotfx said:**
> Yo SUP!? :D

just want to say hi from indonesia,
reading this thread, and sure thing it helps.
I've been running my internet cafe (with 
ccl as the billing system of course!)
for one and a half year,
running with feisty, and just a couple of days a go
upgrading to jaunty, sweet :popcorn:

howdy.... nice to hear you slashdotfx and hows your icafe going smooth?

---

### Post by slashdotfx on 2009-04-22
yeah, it was great, simply amazing how the business went well,
next to my icafe, there was competitor icafe with winxp,
and they were only last for 6 months hehehe.

linux rocks! :guitar:

---

### Post by Script Warlock on 2009-04-22
sorry to hear that for winxp, what version of ccl are you using? i heard about the modified ccl 0.7.2 made from your place.

---

### Post by slashdotfx on 2009-04-27
I'm using 0.7.1,
I dunno about the modified version,
afaik, there is only translation been done.

---

### Post by Script Warlock on 2009-04-27
i mean this one [http://www.esnips.com/web/CafeConLenche/](http://www.esnips.com/web/CafeConLenche/)

i also managed to change the desktop lockpix...if you have modified your cclfox pls share it here ty and more power to your icafe..

---

### Post by peroa on 2009-05-05
Hi there!

Just installed CCL and everything works, which is good.:)
However, I have problems figuring out how the timer works.

Is there a guide or something or could someone explain to me how the timer works?

Basically what I want to do is set the timer to 10 min., then let it run down and at the end the session should be ended.

I`m usually not that thick but this one really bothers me since the timing ends seemingly randomly.
:(

---

### Post by loell on 2009-05-05
can you elaborate more at the timer ending randomly? does it hang? or did it gave a segfault error?

---

### Post by leipogs23 on 2009-05-05
For anyone who is still looking for an iCafe management software, you could take a look at this:

[http://mik.howard.googlepages.com/cybercafemanagementprograms](http://mik.howard.googlepages.com/cybercafemanagementprograms)

Chow!!!

---

### Post by peroa on 2009-05-11
> **loell said:**
> can you elaborate more at the timer ending randomly? does it hang? or did it gave a segfault error?

Well, seems like I found out the logic behind the buttons/timer. ](*,)

First you have to start a new session with the "play" button.
Then you can enter a certain amount of minutes in the "timer" button.
Then the timing display changes and the timer counts down.
However, the session doesn`t always end  when the timing display comes to zero. It ends when the time runs out.

Unnecessary confusing but OK, at least it works.:)

---

### Post by Script Warlock on 2009-05-11
> **peroa said:**
> Well, seems like I found out the logic behind the buttons/timer. ](*,)

First you have to start a new session with the "play" button.
Then you can enter a certain amount of minutes in the "timer" button.
Then the timing display changes and the timer counts down.
However, the session doesn`t always end  when the timing display comes to zero. It ends when the time runs out.

Unnecessary confusing but OK, at least it works.:)

the timer ends exactly not zero but 4secs below zero.

---

### Post by leipogs23 on 2009-05-11
> **boyet said:**
> the timer ends exactly not zero but 4secs below zero.

Sir, correct me if I'm wrong but I think I saw on another Thread(which I can't remmember) that you've also tried CafePilot? How was it compared to CCL?

---

### Post by Script Warlock on 2009-05-11
> **leipogs23 said:**
> Sir, correct me if I'm wrong but I think I saw on another Thread(which I can't remmember) that you've also tried CafePilot? How was it compared to CCL?

cafepilot is a java based timer at libre lang for a couple of workstations pero may ibinenta nila for $99 lang unlimited ka na. sa resources mas tipid si cclfox 1.25% at si cafepilot 10.25% according to htop. libre means 3workstations and more than that tupsy turvey na si cafepilot.

---

### Post by leipogs23 on 2009-05-11
> **boyet said:**
> cafepilot is a java based timer at libre lang for a couple of workstations pero may ibinenta nila for $99 lang unlimited ka na. sa resources mas tipid si cclfox 1.25% at si cafepilot 10.25% according to htop. libre means 3workstations and more than that tupsy turvey na si cafepilot.

Nyek.. Kala ko libre din si CafePilot. Nakita ko kasi na me documentation sya kaya ittry ko sana. Thaks po

---

### Post by Script Warlock on 2009-05-12
> **leipogs23 said:**
> Nyek.. Kala ko libre din si CafePilot. Nakita ko kasi na me documentation sya kaya ittry ko sana. Thaks po

so far CCLFOX lang ang gumagana ng maayos sa shop ko but gbilling is promising pag makagawa na sila ng english version sooner..but the trickiest part sa cclfox during autostartup sa workstation is rename ko sya as ZCLFOX? hahahha he is the last program ang e-process during login thats b4 ko nakuha ang script galing din sa kakosa d2 sa thread.

---

### Post by leipogs23 on 2009-05-12
> **boyet said:**
> cafepilot is a java based timer at libre lang for a couple of workstations pero may ibinenta nila for $99 lang unlimited ka na. sa resources mas tipid si cclfox 1.25% at si cafepilot 10.25% according to htop. libre means 3workstations and more than that tupsy turvey na si cafepilot.

[http://www.soft32.com/download_209540.html](http://www.soft32.com/download_209540.html)
[http://www.dijitanix.com/](http://www.dijitanix.com/)

Sir, Bakit accourding to this one libre xa???

---

### Post by Script Warlock on 2009-05-12
i email djtranix about it limited lang talaga ang bigay nila sa akin good for 3workstation lang libre pero try mo email sya kung anu na ang policy nila ngayon about libre..bka nagbago na, dati naglink nga yung (di ko matandaan ang host) free cafepilot for 5workstations bsta daw link mo rin sila sa website mo and its true pero parang pang M$ lang ata yun..

---

### Post by leipogs23 on 2009-05-12
> **boyet said:**
> i email djtranix about it limited lang talaga ang bigay nila sa akin good for 3workstation lang libre pero try mo email sya kung anu na ang policy nila ngayon about libre..bka nagbago na, dati naglink nga yung (di ko matandaan ang host) free cafepilot for 5workstations bsta daw link mo rin sila sa website mo and its true pero parang pang M$ lang ata yun..

Thanks po. How bout any documentation about CCL?

---

### Post by Script Warlock on 2009-05-12
i have been jotting down eversince naginstall ako ng cclfox and i was thinking if boss loell or anybody has the time to translate it for me or add it to wiki?...my notes are bisaya and i need more time to tinkle more this cclfox you know naman business is good here kaya ikli time for that tapos may outdoor activities pa....magpaburger ako sa tao na makatulong sa pagbuo ng documentation for cclfox....

---

### Post by leipogs23 on 2009-06-02
Sir error installing cclfox.deb. Error dependency is not satisfiable. libfox1.4. Ano kay problem neto?

---

### Post by loell on 2009-06-02
libfox1.4 is still on the repo, i have no idea why its not satisfiable.

```
loell@loell-desktop:~$ apt-cache search libfox1.4
libfox1.4 - The FOX C++ GUI Toolkit
libfox1.4-dev - Development files for the FOX C++ GUI Toolkit
libfox1.4-doc - Documentation of the FOX C++ GUI Toolkit

```

---

### Post by leipogs23 on 2009-06-03
> **loell said:**
> libfox1.4 is still on the repo, i have no idea why its not satisfiable.

```
loell@loell-desktop:~$ apt-cache search libfox1.4
libfox1.4 - The FOX C++ GUI Toolkit
libfox1.4-dev - Development files for the FOX C++ GUI Toolkit
libfox1.4-doc - Documentation of the FOX C++ GUI Toolkit

```

Ok na sir. Maling libfox1.4 pala ang nainstall ko.hehehe. Nagdownload lang ako ng bago tapos ok na sya. Thanks po

---

### Post by Script Warlock on 2009-06-08
i have now the rar file of ccl for windows di ko to ma test kc ala akong M$ those who are interested pwede nyo testing to.... at your own risk!! hehehe biro lang...

pm me na lang....

---

### Post by gamels on 2009-06-08
sir script warlock bisaya pod diay ka.. kamusta lng ko diha kay dia nako sa manila...anyways this thread ad up on me but my question is the ubuntu support the online g a m e s??(block kasi sa workarea ko.) i hope u will sent me a link on your documentation.UBUNTU ROCKS!!!!

---

### Post by leipogs23 on 2009-06-08
> **gamels said:**
> sir script warlock bisaya pod diay ka.. kamusta lng ko diha kay dia nako sa manila...anyways this thread ad up on me but my question is the ubuntu support the online g a m e s??(block kasi sa workarea ko.) i hope u will sent me a link on your documentation.UBUNTU ROCKS!!!!

I was inspired by sir boyet not to concentrate on games on my iCafe. Try mo din ganun. For surfing, research, info, email,chat, printing purposes lang xa. Mas profitable talaga ang games. Pero ika nga. If you enjoy your business, profit will never be a problem.hehehe

---

### Post by Script Warlock on 2009-06-08
the only pc game running sa shop ko ay eto lang urban terror yung iba wala na akong idea pero sinubaybayan ko si boss badrra kc siya yung nagtyaga mapagana yung mga online games sa wine.

---

### Post by gamels on 2009-06-09
were is your cafe located in cebu??? magpapaplano palang po ako kasi i have to experement sumting other than windows.                                                              tanx UBUNTU ROCKS!!! talaga!!!

---

### Post by leipogs23 on 2009-06-09
> **Script Warlock said:**
> the only pc game running sa shop ko ay eto lang urban terror yung iba wala na akong idea pero sinubaybayan ko si boss badrra kc siya yung nagtyaga mapagana yung mga online games sa wine.

Tulad tayo sir boyet. UTerror pa lang din saken. Tapos bumabagal pa tsaka ngbablack yung screen.hehehe

---

### Post by Script Warlock on 2009-06-09
modified cclfox added some features like prepaid account, employee login, print-out account, centralized updates at better reporting.....nasa svn  gusto ko sana join sa project na to pero weak ako sa coding.

boss loell ano kaya ikaw na lang baka may extra time ka pa dyan at sabay mo na to cclcfox.exe(tested under winXP) sa site..

---

### Post by Script Warlock on 2009-06-11
post ko lang mamya ang sript para autostart....

---

### Post by Script Warlock on 2009-06-11
Autostart script
#!/bin/sh
sleep 15
cclcfox -host 192.168.0.1 -name ubuntu1 -nossl;

save as .whatever.sh to home folder

change the permission go to terminal
$chmod a+x .whatever.sh

Run programs automatically when GNOME starts 

 1. Choose System-> Preferences-> Sessions. 
 2. Click the Applications tab for Startup. 
 3. Use the Add, 
 Name: CCL (may be the name that you prefer) 
 Command: link the .whatever.sh from your home 
 Comment: Cyber Manager CCL (which you prefer)

if the timer mailalim sa desktop add this file to  /usr/share/gnome/default.session   

added sa last line(kung ang last line ay 3 then pang 4th and dinagdag na line) 

 3, id = default3 
 3, Priority = 90 
 3, RestartCommand = .whatever.sh 

reboot....

---

### Post by Script Warlock on 2009-06-11
CCLFOX reloaded......thanks to owour8 who continued the tizocs project:D

---

### Post by Script Warlock on 2009-06-11
everything ay nakalublob pa sa svn same code dinagdagan lang ng features and more to come... dami pa to bugs kaya di pa release it may cause spontaneous CPU combustion!

---

### Post by Darkaiser on 2009-06-13
nid ko 2 in the future

---

### Post by fajilan on 2009-06-15
Please help..., I'd try to follow the instruction below but I can't change the CCL logo on the client lock screen.

>>>>

2. You can change the lock screen display on the client by creating some neatest picture you can think of, save it in gif and name the picture lockpix (therefore lockpix.gif) and place it in the .cclcfox folder (not cclfox in the client side) along with the pems files.

>>>>

---

### Post by Script Warlock on 2009-06-15
if your desktop resolution is 1024x768 trim down your fav pics with gimp whith that size then save it inside the home .cclcfox folder(client pc).....you mean cclfox server side(not client)...

be sure to deactivate the cclcfox timer before changing the lockpix.. then activate cclfox see kung may changes.

---

### Post by thilandm on 2009-06-24
am new to ubuntu
and am running a net cafe
i try to install this software on ubunt 9.0.0.1 i think

when its going to install the cclcfox_0.7.0-1_i386.deb its saying file is not available

can you give me any clue about this please

---

### Post by Script Warlock on 2009-06-24
what file is it dependencies?

---

### Post by thilandm on 2009-06-24
when i try ti insatal cclfox it saids >>>dependency is not satisfiable libfox 1.4

is it mean i have to install libfox 1.4 as in WINDOWS ???

or is it computable with ubuntu 9.0.*.*


can you please any one help me to install this great software in my cafe from the beginning please

---

### Post by Script Warlock on 2009-06-24
> **thilandm said:**
> when i try ti insatal cclfox it saids >>>dependency is not satisfiable libfox 1.4

is it mean i have to install libfox 1.4 as in WINDOWS ???

or is it computable with ubuntu 9.0.*.*


can you please any one help me to install this great software in my cafe from the beginning please

get libfox1.4 on the repo

---

### Post by thilandm on 2009-06-24
repo mean

(am sorry am not good on linux bro)

---

### Post by thilandm on 2009-06-24
i think i down load libfox from here

[https://launchpad.net/ubuntu/intrepid/+source/fox1.6/1.6.25-1ubuntu1](https://launchpad.net/ubuntu/intrepid/+source/fox1.6/1.6.25-1ubuntu1)

can i please know how i install using this ?

what the file i want to run on here likes we run setup in windows ???

---

### Post by Script Warlock on 2009-06-24
> **thilandm said:**
> i think i down load libfox from here

[https://launchpad.net/ubuntu/intrepid/+source/fox1.6/1.6.25-1ubuntu1](https://launchpad.net/ubuntu/intrepid/+source/fox1.6/1.6.25-1ubuntu1)

can i please know how i install using this ?

what the file i want to run on here likes we run setup in windows ???


you can install libfox 1.4 in terminal if you cant find on the repo

sudo apt-get install libfox-1.4 libfox-dev

or search it at synaptic...only install what cclfox wants

---

### Post by thilandm on 2009-06-24
am sorry
not able to do any thing
am NEW
thx for help

i will try some how

---

### Post by Script Warlock on 2009-06-24
are you a pinoy or thai?.....

---

### Post by thilandm on 2009-06-24
am from sri lanka

do you have any instatn messnger plz

---

### Post by Script Warlock on 2009-06-24
[email]scriptwarlock@yahoo.com[/email]

---

### Post by thilandm on 2009-06-24
added to skype

---

### Post by Script Warlock on 2009-06-24
@thailandm i change my mind maybe we'll just post here any details regarding to your requests so that anyone can share also there ideas....

---

### Post by thilandm on 2009-06-27
your saying CCLFOX is updated by unwire technologies
so where i can find that updated thing ?

---

### Post by thilandm on 2009-06-27
user01@user01-desktop:~/libcclc-0.7.1$ sudo make install
[sudo] password for user01: 
Making install in src
make[1]: Entering directory `/home/user01/libcclc-0.7.1/src'
make[2]: Entering directory `/home/user01/libcclc-0.7.1/src'
/bin/bash ../mkinstalldirs /usr/local/lib
 /bin/bash ../libtool --mode=install /usr/bin/install -c  libcclc.la /usr/local/lib/libcclc.la
/usr/bin/install -c .libs/libcclc.so.0.7.1 /usr/local/lib/libcclc.so.0.7.1
(cd /usr/local/lib && rm -f libcclc.so.0 && ln -s libcclc.so.0.7.1 libcclc.so.0)
(cd /usr/local/lib && rm -f libcclc.so && ln -s libcclc.so.0.7.1 libcclc.so)
/usr/bin/install -c .libs/libcclc.lai /usr/local/lib/libcclc.la
/usr/bin/install -c .libs/libcclc.a /usr/local/lib/libcclc.a
ranlib /usr/local/lib/libcclc.a
chmod 644 /usr/local/lib/libcclc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

[B]If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf[/B]'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
/bin/bash ../mkinstalldirs /usr/local/include
 /usr/bin/install -c -m 644 cclc.h /usr/local/include/cclc.h
make[2]: Leaving directory `/home/user01/libcclc-0.7.1/src'
make[1]: Leaving directory `/home/user01/libcclc-0.7.1/src'
make[1]: Entering directory `/home/user01/libcclc-0.7.1'
make[2]: Entering directory `/home/user01/libcclc-0.7.1'
**make[2]: Nothing to be done for `install-exec-am'.**
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/user01/libcclc-0.7.1'
make[1]: Leaving directory `/home/user01/libcclc-0.7.1'




waht is this hight lighted thing saying frrined ?
is it installing correctly or not ??

i try whole day today using  it on 9.04
but i didnt get any thing installing it 
it said no chile or some thng when i type cclfox -nossl
but i have some installer thing
when i installed it it dont have that tarrif naming thing as i said

can u pplz help me to get rid off M$ ??

---

### Post by Darkaiser on 2009-06-27
English to nuh guys?

---

### Post by Script Warlock on 2009-06-28
> **thilandm said:**
> user01@user01-desktop:~/libcclc-0.7.1$ sudo make install
[sudo] password for user01: 
Making install in src
make[1]: Entering directory `/home/user01/libcclc-0.7.1/src'
make[2]: Entering directory `/home/user01/libcclc-0.7.1/src'
/bin/bash ../mkinstalldirs /usr/local/lib
 /bin/bash ../libtool --mode=install /usr/bin/install -c  libcclc.la /usr/local/lib/libcclc.la
/usr/bin/install -c .libs/libcclc.so.0.7.1 /usr/local/lib/libcclc.so.0.7.1
(cd /usr/local/lib && rm -f libcclc.so.0 && ln -s libcclc.so.0.7.1 libcclc.so.0)
(cd /usr/local/lib && rm -f libcclc.so && ln -s libcclc.so.0.7.1 libcclc.so)
/usr/bin/install -c .libs/libcclc.lai /usr/local/lib/libcclc.la
/usr/bin/install -c .libs/libcclc.a /usr/local/lib/libcclc.a
ranlib /usr/local/lib/libcclc.a
chmod 644 /usr/local/lib/libcclc.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

[B]If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf[/B]'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
/bin/bash ../mkinstalldirs /usr/local/include
 /usr/bin/install -c -m 644 cclc.h /usr/local/include/cclc.h
make[2]: Leaving directory `/home/user01/libcclc-0.7.1/src'
make[1]: Leaving directory `/home/user01/libcclc-0.7.1/src'
make[1]: Entering directory `/home/user01/libcclc-0.7.1'
make[2]: Entering directory `/home/user01/libcclc-0.7.1'
**make[2]: Nothing to be done for `install-exec-am'.**
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/user01/libcclc-0.7.1'
make[1]: Leaving directory `/home/user01/libcclc-0.7.1'




waht is this hight lighted thing saying frrined ?
is it installing correctly or not ??

i try whole day today using  it on 9.04
but i didnt get any thing installing it 
it said no chile or some thng when i type cclfox -nossl
but i have some installer thing
when i installed it it dont have that tarrif naming thing as i said

can u pplz help me to get rid off M$ ??

pls see this thread if you want to install it manually
[http://ubuntuforums.org/showpost.php?p=6125957&postcount=72](http://ubuntuforums.org/showpost.php?p=6125957&postcount=72)

are you installing it for the client or server? pls take note that the client has the c and the server has the s....libcclc and libccls, cclcfox and cclfox. these files are not interchangeable....

be sure also to add this at the last line:
/usr/lib
    /usr/local/lib

in the /etc/ld.so.conf by opening it with:
sudo gedit /etc/ld.so.conf

---

### Post by Script Warlock on 2009-06-28
> **thilandm said:**
> your saying CCLFOX is updated by unwire technologies
so where i can find that updated thing ?

the new version(modified) of cclfox will be released soon in the meantime just use the version 0.7.0 or 0.7.1.....

---

### Post by thilandm on 2009-06-29
i try cclfox on ubuntu 9.04
thar error comes
then  i try on 8.10
same error comes

and when i try cclcfox
it also give me the same error

so wht is it saying ??

it saying
 Libraries have been installed in:
   /usr/local/lib


but we are making it likes 
/usr/local/lib

both same and why it saying 


[B]Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/include" || mkdir -p -- "/usr/local/include"
 /usr/bin/install -c -m 644 'ccls.h' '/usr/local/include/ccls.h'
make[2]: Leaving directory `/home/user01/libccls-0.7.1/src'
make[1]: Leaving directory `/home/user01/libccls-0.7.1/src'
make[1]: Entering directory `/home/user01/libccls-0.7.1'
make[2]: Entering directory `/home/user01/libccls-0.7.1'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/user01/libccls-0.7.1'
make[1]: Leaving directory `/home/user01/libccls-0.7.1'


am i missing installing any lib ??

or is it some thin wrong with my hardware's ??



[/B]

---

### Post by thilandm on 2009-06-29
now am tryin it on 8.10

this is another erro messag

[B]user01@user01-desktop:~/libccls-0.7.1$ sudo gedit /etc/ld.so.conf

** (gedit:10610): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.VCTEWU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory
user01@user01-desktop:~/libccls-0.7.1$ cd ..
user01@user01-desktop:~$ sudo gedit /etc/ld.so.conf

** (gedit:10615): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.KEOZVU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory
user01@user01-desktop:~$ 
[/B]

---

### Post by thilandm on 2009-06-29
i found ld.so.conf in /etc

and there a nothing in root

**/root/.gnome2/gedit-2.KEOZVU': No such file or directory**


am so confused now

erros are diffent now


who can help me plz

---

### Post by loell on 2009-06-29
> **thilandm said:**
> 
----------------------------------------------------------------------
test -z "/usr/local/include" || mkdir -p -- "/usr/local/include"
 /usr/bin/install -c -m 644 'ccls.h' '/usr/local/include/ccls.h'
make[2]: Leaving directory `/home/user01/libccls-0.7.1/src'
make[1]: Leaving directory `/home/user01/libccls-0.7.1/src'
make[1]: Entering directory `/home/user01/libccls-0.7.1'
make[2]: Entering directory `/home/user01/libccls-0.7.1'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/user01/libccls-0.7.1'
make[1]: Leaving directory `/home/user01/libccls-0.7.1'


am i missing installing any lib ??

or is it some thin wrong with my hardware's ??

[/B]

there's no error here, as far as compilation is concerned, it will be installed in **/usr/local/lib**

---

### Post by thilandm on 2009-06-29
[[COLOR=#339900]**heloo mr loell**[/COLOR]]("http://ubuntuforums.org/member.php?u=44017")

[B]can you please read all error messages 

and give me a solution please 
[/B]

---

### Post by loell on 2009-06-29
> **thilandm said:**
> 

[B]can you please read all error messages 


the one i quoted is not an error.

> **thilandm said:**
> 
[B] and give me a solution please 
[/B]

I have no idea about the other errors , try asking at [CCL forum]("https://sourceforge.net/forum/forum.php?forum_id=385526")

---

### Post by pmwangi80ke on 2009-06-29
hi bro,
sorry ave been away.
i think you are right about the logs being encrypted as they appear exactly the same as in the pic. the challenge is how to unencrypt or make the logs readable. Pls help me out.

thanks
mwangi

---

### Post by pmwangi80ke on 2009-06-29
> **Script Warlock said:**
> is this wht you mean?

hi bro,
exactly thats how the logs appear. How do i make them readable?
thanks alot for your help.

mwangi

---

### Post by Script Warlock on 2009-06-29
dont get yourself push too much  you have more machines to try.....as i said this is not the case of cclfox anymore since anybody is happy with there cclfox working with only some glitches....

as what you told also that cclcfox is working right on our client pc's so there could be nothing wrong on libccls i may suggest try to correct some errors on your ubuntu with dpkg--reconfigure -a then try to install again the libccls and if again not working i may suggest also try openlanhouse server or gbilling..

really got no problems installing cclfox both on 8.04, 8.10 and 9.04 on .deb or the source file with my machines, it even runs on p3 600mhz 512ram 8mb nvidia agp card....

---

### Post by pmwangi80ke on 2009-06-29
hi bro,
from those pics the cclfox reloaded looks great. How can i get it? i still have the old one.

mwangi

---

### Post by Script Warlock on 2009-06-29
hmm this db file was created 4yrs ago and its not compatible with the newer version of sqlite i doubt it can be read by the newer one.... ](*,)

that thing is still in the svn but well wait until the developer release it to the public, sooner...i prefer to use the old one.

---

### Post by Script Warlock on 2009-06-29
> **pmwangi80ke said:**
> hi bro,
exactly thats how the logs appear. How do i make them readable?
thanks alot for your help.

mwangi

i think its not a problem at all yes it seems to displays a binary at the interval things is the amount of time taken during browsing do you need to edit that?....

---

### Post by pmwangi80ke on 2009-06-30
hi
what do i need to edit? and how do i do it? all i want is to be able to read the daily logs. Sorry am slow on this one.

mwangi

---

### Post by Script Warlock on 2009-06-30
> **pmwangi80ke said:**
> hi
what do i need to edit? and how do i do it? all i want is to be able to read the daily logs. Sorry am slow on this one.

mwangi

did you save the daily logs? its below the client tab configure the date where to start recording the logs the the date will expire. after that push the refresh button then al the log of the starting date until present rolls down and that will be the time you save it in some name at the .cclfox folder...now you can see your daily logs at the .cclfox folder

---

### Post by munishvit on 2009-06-30
Bump!

---

### Post by pmwangi80ke on 2009-06-30
hi,
i went to the log tab and input the from to dates but still no changes. i have appended the screen shots 

[ATTACH]119472[/ATTACH]
[ATTACH]119472[/ATTACH]
[ATTACH]119473[/ATTACH]

Also confirm if its necessary for me to have installed Sqlite in the clients as well.

mwangi

---

### Post by Script Warlock on 2009-06-30
press that refresh buton see if theres a log cache but i wonder why theres no "save on file" tab beside the "log expense"...thats why you cant save your daily transactions and i dont think we need to install sqlite browser on the client, everything was logged on the sever.

intervals- is the amount of time taken during browsing....need more time to figure out in libccls...

we'll ask boss loell to update the cclfox installer to 0.7.1...

---

### Post by thilandm on 2009-06-30
***dpkg--reconfigure -a*** is not working

is the command is correct plz

---

### Post by Script Warlock on 2009-07-01
> **thilandm said:**
> ***dpkg--reconfigure -a*** is not working

is the command is correct plz

typo

dpkg-reconfigure -a (must be a root)

---

### Post by pmwangi80ke on 2009-07-01
i did hit the refresh, then went to the cclfox db file in the .cclfox file using sqlite but there is no change at all.I also dont see any "save on file" tab.Is it possible to fix this by installing the server again?

thanks.

---

### Post by pmwangi80ke on 2009-07-01
> **pmwangi80ke said:**
> i did hit the refresh, then went to the cclfox db file in the .cclfox file using sqlite but there is no change at all.I also dont see any "save on file" tab. Is it possible to fix this by installing the server again?

thanks.
thanks

---

### Post by Script Warlock on 2009-07-01
lets wait for boss loell to finish the updated cclfox then well see what else we can do...

---

### Post by thilandm on 2009-07-01
YO MEN

i maked it work on SAME MACHINE

i download some *.deb from this link and its with that tarrif naming thing

but the language is not English
is there a way to change the language plz


[http://www.esnips.com/web/CafeConLenche](http://www.esnips.com/web/CafeConLenche)

[IMG]http://ubuntuforums.org/home/user01/Desktop/Screenshot.png[/IMG]

---

### Post by thilandm on 2009-07-01
/home/user01/Desktop/Screenshot.png

---

### Post by Script Warlock on 2009-07-01
its indo.....try this
ln -s /usr/local/share/locale/en/LC_MESSAGES/cclfox.mo /usr/share/locale/en/LC_MESSAGES/

---

### Post by thilandm on 2009-07-01
**can any one tell me plz how to change the CCLFOX language please **

---

### Post by killer_d76 on 2009-07-05
i've freshly install hardy heron on my other hdd to test ccl, but everytime i clicked on the cclfox.deb i can't seem to install it.. see attached picture.

---

### Post by killer_d76 on 2009-07-05
i just re-downloaded the package and seems that its working now!.. ;)

---

### Post by thilandm on 2009-07-06
**Re: cafe con leche: Internet cafe management software** 			
 			 			 		   		 		 		i've freshly install hardy heron on my other hdd to test ccl, but everytime i clicked on the cclfox.deb i can't seem to install it.. see attached picture.


install the libfox
then it will works for fine

---

### Post by thilandm on 2009-07-06
[SIZE=6]**how to add XP clinets to CCLFOX ???**[/SIZE]

---

### Post by Script Warlock on 2009-07-06
where did you get the cclcfox.exe for winxp? i have the file and send it to you, dont need to create a client. when you start the cclcfox the hostname of your ubuntu/xp client pc will appear on the server if you run it....

---

### Post by Script Warlock on 2009-07-06
> **thilandm said:**
> [SIZE=6]**how to add XP clinets to CCLFOX ???**[/SIZE]

pls make your font smaller bka latiguhin ka ng mods kung ganyan ka magpost.....

---

### Post by netrook on 2009-07-06
i can't compile libccls-0.7.0 on jaunty. it says "configure error: please install sqlite". but "apt-get install sqlite" returns "sqlite is already the newest version"

---

### Post by Script Warlock on 2009-07-06
its easy i think if you install it via .deb in the first post.....

---

### Post by thilandm on 2009-07-07
am tired with CCLFOX
its not works for me

now its not showing a tariff name again

---

### Post by Script Warlock on 2009-07-08
@thillan last day you have a working cclfox server may i know what things you change in your 9.04? is the ICS enabled? 

awki thnxs for the diagram well ask for some help here regarding the networking.....

---

### Post by thilandm on 2009-07-08
[IMG]http://home/admin01/Desktop/Screenshot.png[/IMG]

there nothing worng with my LAN set up

u make a router using 2 nics and am using a router

so am sure 1000% about my network setup
if else hows the cafesuite is working on this setup ??
and how the compiler know am using a router ??


now cclfox is running and in client pc its now showing the time

and in terminal this error message is comeing

admin01@Admin-desktop:~$ cclfox -nossl
Segmentation fault


wht i can do for this error messag plz

and its showing clietn it coneected

but client not showing the time running

[IMG]http://home/admin01/Desktop[/IMG]

---

### Post by markedisonchua on 2009-07-10
How many Ubuntu Cafe in the Philippines?

---

### Post by Script Warlock on 2009-07-10
@thilandm, i admit theres nothing wrong with your netwrok method only that your not pointing the timer to the right direction......now that we fixed everything you owe me a cup of coffee, hehehe..

pls read, practice and learn more about linux.....have a happy adventure with cclfox and ubuntu8)

---

### Post by thilandm on 2009-07-14
i likes give a advice to all

before you install cclfox please install JAVA RUNTIME

then it will not give any troubles to you

---

### Post by ubuntian on 2009-07-17
may I know why is the last button on server's interface which set the minutes of usage is not workin?
as well as for the reboot and turn off function.
am I done sumthing wrong?
everything working fine except for those stated above...

btw, kinda confuse with the tariff setting...
cld anyone provide a brief explanation?
thank you so much.

---

### Post by Script Warlock on 2009-07-17
> **ubuntian said:**
> may I know why is the last button on server's interface which set the minutes of usage is not workin?
as well as for the reboot and turn off function.
am I done sumthing wrong?
everything working fine except for those stated above...

btw, kinda confuse with the tariff setting...
cld anyone provide a brief explanation?
thank you so much.

chmod 775 the shutdown and reboot  all the client pc....
tariff is at the first pg. of this thread...
maybe during the installation an error occured you're not aware of or you haven't set the tariff yet thats y its not running or working....

pls elaborate more on that button we need more inputs...

---

### Post by ubuntian on 2009-07-17
> **Script Warlock said:**
> chmod 775 the shutdown and reboot  all the client pc....
tariff is at the first pg. of this thread...
maybe during the installation an error occured you're not aware of or you haven't set the tariff yet thats y its not running or working....

pls elaborate more on that button we need more inputs...

actually I followed the step-by-step guide from here:
[http://yogharp.wordpress.com/2007/08/23/cafe-con-leche-ubuntu-how-to/](http://yogharp.wordpress.com/2007/08/23/cafe-con-leche-ubuntu-how-to/)
bcoz the guide on the 1st page kinda difficult for me to follow due to I'm still new to ubuntu...

bout the restart and turn off function, i tried set with command:
```
sudo chmod 775 /sbin/shutdown
sudo chmod 775 /sbin/reboot
```
but ends up the same =(

---

### Post by Script Warlock on 2009-07-17
> **ubuntian said:**
> actually I followed the step-by-step guide from here:
[http://yogharp.wordpress.com/2007/08/23/cafe-con-leche-ubuntu-how-to/](http://yogharp.wordpress.com/2007/08/23/cafe-con-leche-ubuntu-how-to/)
bcoz the guide on the 1st page kinda difficult for me to follow due to I'm still new to ubuntu...

bout the restart and turn off function, i tried set with command:
```
sudo chmod 775 /sbin/shutdown
sudo chmod 775 /sbin/reboot
```but ends up the same =(

afaik the easiest way to install this timer is by installing the .deb..
so this is about compiling, have you encountered an error during the compiling?. if then pls post some of the errors here...and tell us also wat Os version you use.

---

### Post by ubuntian on 2009-07-20
> **Script Warlock said:**
> afaik the easiest way to install this timer is by installing the .deb..
so this is about compiling, have you encountered an error during the compiling?. if then pls post some of the errors here...and tell us also wat Os version you use.

I tried install using the .deb
server installed without problem but client installation doesn't create the .cclcfox folder in my home directory so i can't put the .pem inside the folder....

using ubuntu 9.04

---

### Post by Script Warlock on 2009-07-20
> **ubuntian said:**
> I tried install using the .deb
server installed without problem but client installation doesn't create the .cclcfox folder in my home directory so i can't put the .pem inside the folder....

using ubuntu 9.04

[http://ubuntuforums.org/showpost.php?p=5725424&postcount=54](http://ubuntuforums.org/showpost.php?p=5725424&postcount=54)

---

### Post by ubuntian on 2009-07-20
> **Script Warlock said:**
> [http://ubuntuforums.org/showpost.php?p=5725424&postcount=54](http://ubuntuforums.org/showpost.php?p=5725424&postcount=54)

yea, i read the post b4 I ask this question...
I choose to view the hidden file but it doesn't exist in the home directory...
this only happened on client, server no problem....

p/s: sorry bro, missed the part of addin a folder manually, will try n update here

---

### Post by Script Warlock on 2009-07-20
> **ubuntian said:**
> yea, i read the post b4 I ask this question...
I choose to view the hidden file but it doesn't exist in the home directory...
this only happened on client, server no problem....

p/s: sorry bro, missed the part of addin a folder manually, will try n update here

you can also include your lockpix inside that folder.....

---

### Post by ubuntian on 2009-07-20
Script Warlock,

it works but the timer still cannot work properly....
is that after I set the minutes, it will start automatically?
I tried set the minutes thn click start, it wouldn't stop after the period that I set.

p/s: timer not starting after I set the minutes n click ok

---

### Post by Script Warlock on 2009-07-20
> **ubuntian said:**
> Script Warlock,

it works but the timer still cannot work properly....
is that after I set the minutes, it will start automatically?
I tried set the minutes thn click start, it wouldn't stop after the period that I set.

p/s: timer not starting after I set the minutes n click ok

click start and set the minutes

---

### Post by ubuntian on 2009-07-20
> **Script Warlock said:**
> click start and set the minutes

thx bro, it works finally!:D

but about the turn off and reboot, i tried the
```
sudo chmod 775 /sbin/shutdown
sudo chmod 775 /sbin/reboot
```

i got the followin msg in terminal while tryin to reboot or turn off from server
> reboot: need to be root
halt: need to be root

any solution to solve the permission issue?
thank you.

---

### Post by Script Warlock on 2009-07-20
> **ubuntian said:**
> thx bro, it works finally!:D

but about the turn off and reboot, i tried the
```
sudo chmod 775 /sbin/shutdown
sudo chmod 775 /sbin/reboot
```i got the followin msg in terminal while tryin to reboot or turn off from server


any solution to solve the permission issue?
thank you.

chmod must be applied only to clients...

---

### Post by ubuntian on 2009-07-20
> **Script Warlock said:**
> chmod must be applied only to clients...

yea, i applied to clients

---

### Post by Script Warlock on 2009-07-20
> **ubuntian said:**
> yea, i applied to clients

try to log in terminal as root then chmod

---

### Post by ubuntian on 2009-07-20
> **Script Warlock said:**
> try to log in terminal as root then chmod

```
root@baiduri05-desktop:~# chmod 775 /sbin/reboot
root@baiduri05-desktop:~# chmod 775 /sbin/shutdown
```

ends up the same...:(

---

### Post by Script Warlock on 2009-07-20
> **ubuntian said:**
> ```
root@baiduri05-desktop:~# chmod 775 /sbin/reboot
root@baiduri05-desktop:~# chmod 775 /sbin/shutdown
```ends up the same...:(

it wont respond to the servers call? try to reboot the server and the clients.... breath fresh air outside and eat your lunch.....

---

### Post by ubuntian on 2009-07-20
> **Script Warlock said:**
> it wont respond to the servers call? try to reboot the server and the clients.... breath fresh air outside and eat your lunch.....

it respond by giving the msg below in terminal:
> reboot: need to be root
halt: need to be root 

machine doesn't reboot or shutdown

p/s: client & server reboot.

lunch soon...haha

---

### Post by Script Warlock on 2009-07-20
> **ubuntian said:**
> it respond by giving the msg below in terminal:


machine doesn't reboot or shutdown

p/s: client & server reboot.

lunch soon...haha

wait, did you give reboot/shutdown clients with the terminal?

---

### Post by ubuntian on 2009-07-20
wat do u mean by tat?

---

### Post by Script Warlock on 2009-07-20
> **ubuntian said:**
> wat do u mean by tat?

how did you reboot or shutdown the clients by terminal or cclfox.

---

### Post by ubuntian on 2009-07-20
> **Script Warlock said:**
> how did you reboot or shutdown the clients by terminal or cclfox.

i failed to shutdown or reboot client through cclfox at server..
just now wat i did was as u told me to restart the client n server after applying the chmod using root on client..

but result still the same, can't shutdown/reboot a client from server's cclfox....

---

### Post by Script Warlock on 2009-07-20
> **ubuntian said:**
> i failed to shutdown or reboot client through cclfox at server..
just now wat i did was as u told me to restart the client n server after applying the chmod using root on client..

but result still the same, can't shutdown/reboot a client from server's cclfox....

i just wanted to make sure we're on the same track ..
i can help you more just add me  [EMAIL="scriptwarlock@yahoo.com"]scriptwarlock@yahoo.com[/EMAIL] to your messenger
will post later how we solved the issue here.....see ya

---

### Post by samuu on 2009-07-24
Help..Am trying to install cafe con leche on ubuntu 7.04immediately when trying to install the  libcclc_0.7.0-1_i386.deb package..i get an this error Dependancy is not satifiable:libssl0.9.8.Am abegginer in ubuntu and would like to use it in my internet cafe.Its does well in Ubuntu 9 but the problem is Ubuntu 9 keep on hanging most of the time.My machines are compaqs with2.4ghz and 256 mb of RAM  and 40GB harddisk..
I will Appreciate you help Thank you

---

### Post by samuu on 2009-07-24
Help..Am trying to install cafe con leche on ubuntu 7.04immediately when trying to install the  libcclc_0.7.0-1_i386.deb package..i get an this error **Dependancy is not satifiable:libssl0.9.8**.Am abegginer in ubuntu and would like to use it in my internet cafe.Its does well in Ubuntu 9 but the problem is Ubuntu 9 keep on hanging most of the time.My machines are compaqs with2.4ghz and 256 mb of RAM  and 40GB harddisk..
I will Appreciate you help Thank you

---

### Post by loell on 2009-07-24
7.04 is very old, can you install 8.04 or 8.10 instead?

---

### Post by tolik2525 on 2009-08-20
Sorry for necroposting.
**ubuntian**, maybe you forgot additional "7" in chmod? ^_^
> **ubuntian said:**
> ```
root@baiduri05-desktop:~# chmod 775 /sbin/reboot
root@baiduri05-desktop:~# chmod 775 /sbin/shutdown
```


> **BatsotO said:**
> 
3. if you want to shutdown and reboot client pcs remotely, chmod 7755 the /usr/bin/shutdown and /usr/bin/reboot.


---

### Post by Script Warlock on 2009-08-20
> **tolik2525 said:**
> Sorry for necroposting.
**ubuntian**, maybe you forgot additional "7" in chmod? ^_^


hmmm i haven't seen that thanks a lot  for reminding us...:KS

---

### Post by frustphil on 2009-08-21
pwde bang malaman kung saan pwede madownload ang source nito?

---

### Post by loell on 2009-08-21
> **frustphil said:**
> pwde bang malaman kung saan pwede madownload ang source nito?

kung hindi mahanap ni google, pwede mo ring tingnan ang first post ng first page ng thread na ito. ;)

---

### Post by thilandm on 2009-08-23
admin01@ubuntu01:~$ cd libcclc-0.7.1
bash: cd: libcclc-0.7.1: No such file or directory
admin01@ubuntu01:~$ cd libcclc-0.7.1
admin01@ubuntu01:~/libcclc-0.7.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
[B]checking whether make sets $(MAKE)... (cached) yes
checking for SSL_new in -lssl... no
configure: error: please install openssl[/B]
admin01@ubuntu01:~/libcclc-0.7.1$ 


its seems a new error
i don't know exactly,,,
but when i try install openssl its saying it already installed new version 

any idea ?

---

### Post by thilandm on 2009-08-23
[SIZE=2]any one can help me to work out this tariff on CCL ??

i charge 30 for first 30 minutes 

and 40 for first 60 minutes 

after the hour i charge 10 for next 15 minutes 

if some one works 1 hour and 20 minutes   its charge 60

and if some one works 2 hours its 80

any one can help me ?[/SIZE]

---

### Post by Script Warlock on 2009-08-24
> **thilandm said:**
> admin01@ubuntu01:~$ cd libcclc-0.7.1
bash: cd: libcclc-0.7.1: No such file or directory
admin01@ubuntu01:~$ cd libcclc-0.7.1
admin01@ubuntu01:~/libcclc-0.7.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
[B]checking whether make sets $(MAKE)... (cached) yes
checking for SSL_new in -lssl... no
configure: error: please install openssl[/B]
admin01@ubuntu01:~/libcclc-0.7.1$ 


its seems a new error
i don't know exactly,,,
but when i try install openssl its saying it already installed new version 

any idea ?

uninstall the openssl then reinstall openssl and all lib dependencies of cclcfox  then proceed to compile if again it complains on some missing then sudo apt-get install lib(missing dependencies).....

---

### Post by thilandm on 2009-08-24
> **thilandm said:**
> admin01@ubuntu01:~$ cd libcclc-0.7.1
bash: Cd: Libcclc-0.7.1: No such file or directory
admin01@ubuntu01:~$ cd libcclc-0.7.1
admin01@ubuntu01:~/libcclc-0.7.1$ ./configure
checking for a bsd-compatible install... /usr/bin/install -c
checking whether build environment is sane... Yes
checking for gawk... No
checking for mawk... Mawk
checking whether make sets $(make)... Yes
checking for gcc... Gcc
checking for c compiler default output file name... A.out
checking whether the c compiler works... Yes
checking whether we are cross compiling... No
checking for suffix of executables... 
Checking for suffix of object files... O
checking whether we are using the gnu c compiler... Yes
checking whether gcc accepts -g... Yes
checking for gcc option to accept ansi c... None needed
checking for style of include used by make... Gnu
checking dependency style of gcc... Gcc3
checking build system type... I686-pc-linux-gnu
checking host system type... I686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... Grep -e
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is gnu ld... Yes
checking for /usr/bin/ld option to reload object files... -r
checking for bsd-compatible nm... /usr/bin/nm -b
checking whether ln -s works... Yes
checking how to recognise dependent libraries... Pass_all
checking how to run the c preprocessor... Gcc -e
checking for ansi c header files... Yes
checking for sys/types.h... Yes
checking for sys/stat.h... Yes
checking for stdlib.h... Yes
checking for string.h... Yes
checking for memory.h... Yes
checking for strings.h... Yes
checking for inttypes.h... Yes
checking for stdint.h... Yes
checking for unistd.h... Yes
checking dlfcn.h usability... Yes
checking dlfcn.h presence... Yes
checking for dlfcn.h... Yes
checking for g++... G++
checking whether we are using the gnu c++ compiler... Yes
checking whether g++ accepts -g... Yes
checking dependency style of g++... Gcc3
checking how to run the c++ preprocessor... G++ -e
checking for g77... No
checking for f77... No
checking for xlf... No
checking for frt... No
checking for pgf77... No
checking for fort77... No
checking for fl32... No
checking for af77... No
checking for f90... No
checking for xlf90... No
checking for pgf90... No
checking for epcf90... No
checking for f95... No
checking for fort... No
checking for xlf95... No
checking for ifc... No
checking for efc... No
checking for pgf95... No
checking for lf95... No
checking for gfortran... No
checking whether we are using the gnu fortran 77 compiler... No
checking whether  accepts -g... No
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -b output from gcc object... Ok
checking for objdir... .libs
checking for ar... Ar
checking for ranlib... Ranlib
checking for strip... Strip
checking for correct ltmain.sh version... Yes
checking if gcc static flag  works... Yes
checking if gcc supports -fno-rtti -fno-exceptions... No
checking for gcc option to produce pic... -fpic
checking if gcc pic flag -fpic works... Yes
checking if gcc supports -c -o file.o... Yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... Yes
checking whether -lc should be explicitly linked in... No
checking dynamic linker characteristics... Gnu/linux ld.so
checking how to hardcode library paths into programs... Immediate
checking whether stripping libraries is possible... Yes
checking if libtool supports shared libraries... Yes
checking whether to build shared libraries... Yes
checking whether to build static libraries... Yes
configure: Creating libtool
appending configuration tag "cxx" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is gnu ld... Yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... Yes
checking for g++ option to produce pic... -fpic
checking if g++ pic flag -fpic works... Yes
checking if g++ supports -c -o file.o... Yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... Yes
checking dynamic linker characteristics... Gnu/linux ld.so
checking how to hardcode library paths into programs... Immediate
checking whether stripping libraries is possible... Yes
appending configuration tag "f77" to libtool
[b]checking whether make sets $(make)... (cached) yes
checking for ssl_new in -lssl... No
configure: Error: Please install openssl[/b]
admin01@ubuntu01:~/libcclc-0.7.1$ 


its seems a new error
i don't know exactly,,,
but when i try install openssl its saying it already installed new version 

any idea ?


problem is solved,,,

un installing openssl and reinstalling it

---

### Post by rbur on 2009-09-02
Greetings all ....  perhaps someone can advise me...

I have 8 Ubuntu 9.04 systems connected by a switch then to a router to the internet.  This is in a public library location.  I would like to setup a cafe style operation to control access to the computers and internet.  I am not too concerned about actually billing costs ... just the control (time based).

1) Do I need a separate server with CCL and does this server need 2 nic cards ??
2) Do all 8 computers need CCL client software installed ??
3) Is administration done from the server ??
4) Can the server be physically located in another room ?? if so ... how do I access it ??

thank you for your patience .... I have read this entire post more than once and am still a bit confused.

Ron...

---

### Post by Script Warlock on 2009-09-02
> **rbur said:**
> Greetings all ....  perhaps someone can advise me...

I have 8 Ubuntu 9.04 systems connected by a switch then to a router to the internet.  This is in a public library location.  I would like to setup a cafe style operation to control access to the computers and internet.  I am not too concerned about actually billing costs ... just the control (time based).

1) Do I need a separate server with CCL and does this server need 2 nic cards ??
2) Do all 8 computers need CCL client software installed ??
3) Is administration done from the server ??
4) Can the server be physically located in another room ?? if so ... how do I access it ??

thank you for your patience .... I have read this entire post more than once and am still a bit confused.

Ron...

oi maganda idea:KS nga pala to ubuntu sa mga school libraries total research lang naman gagawin ano kaya promote ko ubuntu sa dati kong school sa USJR....

1. yes a separate, depends on your network setup
2.yes all must have the ccl client
3. yes
4. guess ko lang what you mean about server is the desktop pc tailored as server for the timer?...

---

### Post by rbur on 2009-09-02
> **Script Warlock said:**
> oi maganda idea:KS nga pala to ubuntu sa mga school libraries total research lang naman gagawin ano kaya promote ko ubuntu sa dati kong school sa USJR....

I'm sorry .... I only understand English....


> 1. yes a separate, depends on your network setup

8 computers into a switch which then feeds to a router which then connects to DSL modem.  Would the new server go between the switch and router ??

> 4. guess ko lang what you mean about server is the desktop pc tailored as server for the timer?...

The server would be located in a seperate room along with the switch and router.  Keyboard and monitor not accessible from there.  Is there a way to remotely connect to the CCL administration from another computer (computer #9) ??

thank you for your answers...

---

### Post by loell on 2009-09-02
> **rbur said:**
> 
1) Do I need a separate server with CCL and does this server need 2 nic cards ??
2) Do all 8 computers need CCL client software installed ??
3) Is administration done from the server ??
4) Can the server be physically located in another room ?? if so ... how do I access it ??


1. yes, while it's possible to run them side by side on a single PC, it seem pointless.

2. Yes

3. Yes, basically any PC where you set it as the CCL server.

4. As long as  clients can ping it, then yes.

---

### Post by Script Warlock on 2009-09-02
ops sorry i thought your one of us a pinoy, ok....

@loell should we upgrade this thread? mkahawa.deb is ready..or gawa ng bagong thead?

---

### Post by loell on 2009-09-02
> **Script Warlock said:**
> 
@loell should we upgrade this thread? mkahawa.deb is ready..or gawa ng bagong thead?

another  thread would be appropriate, so as to separate the issues of both programs. :)

---

### Post by Script Warlock on 2009-09-02
> **loell said:**
> another  thread would be appropriate, so as to separate the issues of both programs. :)

ok...

---

### Post by Script Warlock on 2009-09-03
> **rbur said:**
> I'm sorry .... I only understand English....




8 computers into a switch which then feeds to a router which then connects to DSL modem.  Would the new server go between the switch and router ??



The server would be located in a seperate room along with the switch and router.  Keyboard and monitor not accessible from there.  Is there a way to remotely connect to the CCL administration from another computer (computer #9) ??


thank you for your answers...

does server means
this one? [http://www.dell.com/us/en/enterprise/servers/ct.aspx?refid=servers&s=biz&cs=555](http://www.dell.com/us/en/enterprise/servers/ct.aspx?refid=servers&s=biz&cs=555)
or 
this one: [http://www.allamericanpatriots.com/photos/low-energy-desktop-computer-system-fujitsu ]("http://www.allamericanpatriots.com/photos/low-energy-desktop-computer-system-fujitsu")

[ ]("http://www.allamericanpatriots.com/photos/low-energy-desktop-computer-system-fujitsu")

---

### Post by rbur on 2009-09-03
> **Script Warlock said:**
> does server means .....

this one: [http://www.allamericanpatriots.com/photos/low-energy-desktop-computer-system-fujitsu ]("http://www.allamericanpatriots.com/photos/low-energy-desktop-computer-system-fujitsu")


Yes ... this type.  I would hope to run it headless ... meaning no monitor and no keyboard.  I guess I would have to install 2 nic cards ... one for incoming lan from the switch and one for outgoing to the router.
This is where my confusion is ... does the server act as some kind of gateway that controls which of the clients can access the internet ??

Then how is the client computer controlled from it being used as a standalone computer by itself ??

Sorry for what must sound like very basic question ... but I cannot find any writeup on how this all works.

---

### Post by Script Warlock on 2009-09-04
> **rbur said:**
> Yes ... this type.  I would hope to run it headless ... meaning no monitor and no keyboard.  I guess I would have to install 2 nic cards ... one for incoming lan from the switch and one for outgoing to the router.
This is where my confusion is ... does the server act as some kind of gateway that controls which of the clients can access the internet ??

Then how is the client computer controlled from it being used as a standalone computer by itself ??

Sorry for what must sound like very basic question ... but I cannot find any writeup on how this all works.

pls correct me if wrong but i see no slowdown on  internet speed when using a desktop pc with all its paraphernalia....so i set mine like this one

---

### Post by loell on 2009-09-04
> **rbur said:**
> Yes ... this type.  I would hope to run it headless ... meaning no monitor and no keyboard.

with cafe con leche and its interface, you can't, as you need to control it with mouse and keyboard and monitor to set the time, tarrifs and such.  this program does not really restrict internet access to the client, it merely restricts the  users from using the client computers when their time is up.

---

### Post by rbur on 2009-09-04
@loell .... **BINGO** :KS... I think a light just turned on !!!  you say that I can control the whole client pc ... meaning that I can activate it for say just 1 hour then it times out ??

@Script Warlock .... you say in a previous post that you have a windows XP version of cclcfox ?? could you please send it to me at rb66033(at)gmail.com .
I have temporarily setup Linux Zencafe as a server.
I have downloaded cclcfox.exe to run on a windows pc from somewhere and it's not talking to the server I setup using Linux ZenCafe.
I have setup the windows batch file to be " start cclcfox -host 192.168.1.5 -name ron -nossl ".
A small notification appears on the windows client and if I "end session"  then the client pc locks out completely and the CCL logo displays on the screen.... so I think the client is running ok.
I can ping the server from the client and the client from the server but the server does not see the client in the ccl manager.

Perhaps I'm missing a step somewhere ???

If I can get this working to prove the concept then I will move on to the Ubuntu setup.

EDIT...
I have tried everything I can think of to get the XP machine to talk to the Zencafe .... 
I thought perhaps the CA.pem and cert.pem have to be matched so I also tried using the ones from the Zencafe on the XP box as well ... no go.
I just do not see the client on the server ccl manager when I start the cclfox on the XP box.
What to try now ??

---

### Post by Script Warlock on 2009-09-04
> **rbur said:**
> @loell .... **BINGO** :KS... I think a light just turned on !!!  you say that I can control the whole client pc ... meaning that I can activate it for say just 1 hour then it times out ??

@Script Warlock .... you say in a previous post that you have a windows XP version of cclcfox ?? could you please send it to me at rb66033(at)gmail.com .
I have temporarily setup Linux Zencafe as a server.
I have downloaded cclcfox.exe to run on a windows pc from somewhere and it's not talking to the server I setup using Linux ZenCafe.
I have setup the windows batch file to be " start cclcfox -host 192.168.1.5 -name ron -nossl ".
A small notification appears on the windows client and if I "end session"  then the client pc locks out completely and the CCL logo displays on the screen.... so I think the client is running ok.
I can ping the server from the client and the client from the server but the server does not see the client in the ccl manager.

Perhaps I'm missing a step somewhere ???

If I can get this working to prove the concept then I will move on to the Ubuntu setup.

EDIT...
I have tried everything I can think of to get the XP machine to talk to the Zencafe .... 
I thought perhaps the CA.pem and cert.pem have to be matched so I also tried using the ones from the Zencafe on the XP box as well ... no go.
I just do not see the client on the server ccl manager when I start the cclfox on the XP box.
What to try now ??

we can help you more if its all ubuntu dont know much about zencafe or try to ask help on zencafe forum about the glitches of cclfox.exe.

yes i have the file including the updated cclfox...

---

### Post by Script Warlock on 2009-09-08
[B][http://ccl.sourceforge.net/](http://ccl.sourceforge.net/)

[/B][B]Screenshots

   [IMG]http://img196.imageshack.us/img196/8467/serverh.jpg[/IMG]
                                [/B][SIZE=3]Server[/SIZE][B]

  [IMG]http://img180.imageshack.us/img180/3489/client.jpg[/IMG]
                                 [/B][SIZE=4][SIZE=3]Client[/SIZE]

[/SIZE]**Common Installation     **

 Both side of the application (server and client) has to meet their dependencies, since this is not a debian package, we have to install the dependencies manually. CCL dependencies are
 
[LIST]
[*]sqlite3
[*]glib2.0
[*]libfox1.4(server), libfox1.6(client)
[*]openssl
[/LIST]
 **For the ccl server run these commands :**[INDENT]$ sudo apt-get install sqlite3 libsqlite3-dev[/INDENT][INDENT]$ sudo apt-get install libfox1.4 libfox1.4-dev   (server)[/INDENT][INDENT]$ sudo apt-get install libglib2.0-dev[/INDENT][INDENT]$ sudo apt-get install libssl-dev[/INDENT][COLOR=Black]**For the [COLOR=Red]ccl client [/COLOR][COLOR=Black]replace[/COLOR] the [COLOR=Red]libfox1.4[/COLOR] run these command :**[/COLOR]
          $ sudo apt-get install [COLOR=Red]libfox-1.6-0 libfox-1.6-dev  
[/COLOR]  [B]
Don’t forget the build essentials for compiling from source :[/B][INDENT]$sudo apt-get install build-essential[/INDENT]**Then edit your /etc/ld.so.conf file with :**[INDENT]$sudo gedit /etc/ld.so.conf[/INDENT]**And add these lines :**[INDENT]/usr/lib
/usr/local/lib                           …..and save the changes when done
[/INDENT]**it may look like this :**
     
include /etc/ld.so.conf.d/*.conf
 /usr/lib
 /usr/local/lib
 [B]
Then execute this :[/B]
$sudo ldconfig[COLOR=Blue][U][B]

CCL Server Installation[/B][/U][/COLOR][B]
[COLOR=Black]for the server side you’ll need these 2 files :[/COLOR][/B]
 cclfox-0.7.1.tar.bz2 [URL="http://www.mediafire.com/file/miqwqzowyqy/cclfox-0.7.1.tar.bz2"]here
[/URL] libccls-0.7.1.tar.bz2    [here]("http://www.mediafire.com/file/antg3d1mh5q/libccls-0.7.1.tar.bz2")
 [B]
Put these files on your home folder and do these steps :[/B][INDENT]$tar -xjvf libccls-0.7.1.tar.bz2
$cd libccls-0.7.1
$./configure
$make
$sudo make install
$cd ..
$tar -xjvf cclfox-0.7.1.tar.bz2
$cd cclfox-0.7.1
$./configure
$make
$sudo make install[/INDENT][B]
create a folder in the home directory :[/B]
     $mkdir .cclfox
 [B]
put [this]("http://www.mediafire.com/file/t2w5azgwtmi/pem") file to the .cclfox folder right click and choose the properties and select permission then tick the box and close. generate the pem by double clicking it and  if being prompted just run it.[/B]

  [IMG]http://img42.imageshack.us/img42/3199/pem.png[/IMG]


**Then create a launcher on your desktop and add :**[INDENT]cclfox -nossl[/INDENT]on the “command” text box

 _[COLOR=Blue]**CCL Client Installation**[/COLOR]_  
 **for the client side you’ll need these 2 files :**
 cclcfox-0.7.1-FOX-1.6.tar.bz2  [here]("http://www.mediafire.com/file/ylwx3ziw44i/cclcfox-0.7.1-FOX-1.6.tar.bz2")
libcclc-0.7.1.tar.bz2  [here]("http://www.mediafire.com/file/zryqm2wz4ac/libcclc-0.7.1.tar.bz2")
 [B]
put these files on your home folder and do these steps :[/B][INDENT]$tar -xjvf libcclc-0.7.1.tar.bz2
$cd libcclc-0.7.1
$./configure
$make
$sudo make install
$cd ..
$tar -xjvf cclcfox-0.7.1-FOX-1.6.tar.bz2
$cd cclcfox-0.7.1
$./configure
$make
$sudo make install[/INDENT]**create a folder in the home directory :**
     $mkdir .cclcfox

 [B]put [this]("http://www.mediafire.com/file/t2w5azgwtmi/pem") file to the .cclfox folder right click and choose the properties and select permission then tick the box and close. generate the pem by double clicking it and  if being prompted just run it.

  [IMG]http://img42.imageshack.us/img42/3199/pem.png[/IMG]

[/B]  [B]
then create a launcher on your home folder and add : (Alt+f2 will do)[/B]

cclcfox -host serverip -name anynameor(clienthostname) -nossl[INDENT]on the “command” text box[/INDENT][INDENT]**to check the client hostname simply type in the terminal:**[/INDENT][INDENT]         $ hostname[/INDENT]**Setting the tariff :           **


[LIST=1]
[*]launch the ccl server and choose     the tariff tab
[*]select the     days(highlighted) before modifying or nothing will change. after the desired values are filled accordingly to your likes     click the apply.....
[/LIST]
 
  [IMG]http://img178.imageshack.us/img178/3427/tariff.png[/IMG]
 

 **Autorun the ccl client :     **

 to run this on startup in ubuntu/gnome 
add the above in **System** menu ->**preferences**->**sessions(8.04) | startup applications(9.04) **
 Name: any name
 Command: cclcfox -host serverip -name anynameor(clienthostname) -nossl
 Comment: whatever
 [B]
Remote shutdown and reboot :           [/B]

$sudo chmod 7755 /sbin/shutdown
        $sudo chmod 7755 /sbin/reboot
 [B]
Replacing the desktop lockscreen(client workstation) :           [/B]

[COLOR=Red]1[/COLOR]. kill the cclcfox running  >>> sudo kill -9 (pid of cclcfox)
[COLOR=Red]2[/COLOR]. create or choose the desired             photo, trim down according to the desktop's resolution and [COLOR=Red]save as lockpix.gif[/COLOR] in the .cclcfox folder located in the home             folder. Note that .cclcfox is a hidden folder so in order to             display open the home folder and select the view then tick/select             the box “show hidden files”. close when done
[COLOR=Red]3[/COLOR]. relaunch the client timer             and “end the session”.

 **Common functions :**
 
  [IMG]http://img178.imageshack.us/img178/4390/buttonsf.png[/IMG]

Green – start session
Yellow – pause and resume             session
Red – stop session
Blue – continue session
Purple – swap session
Turquoise – set timeout             (countdown)

**to start the pre-paid session:**
     press the green and the turquoise and set the time...
 
 **to start the opentime session:**
     press the green button....
 
 **to pause the session:**
     press the yellow and to resume press again the yellow...
 
 **to continue the session**
     if the customer accidentally stops the session it can be continued by pressing the blue button
 
 **to swap the session:**
     if the customer of ubuntu1(workstation) wants to transfer to ubuntu8 for some reason simply choose the ubuntu1 icon and press the purple button and choose the ubuntu8 pc. The time consumed, left or account is also transferred...
 

 **Remote functions: (right click the icon)**
 
  [IMG]http://img195.imageshack.us/img195/1194/70007083.png[/IMG]

 
 **Turn off:**
     remotely shutdown the workstation …   
 
 **Reboot:**
     remotely restart the workstation  …. 
 
 **Turn off screen:**
     remotely turn off the client workstation monitor
 
 **Allow users to start the session:**
     if selected user can start the session by clicking the pop-up tab on the workstation lockscreen marked as "click here to start"
 
 **Allow members to start the session:**
     it allows the member to start the session by pressing the enter and log-in with members id and password(default password is the members id)

**Set member:**

[IMG]http://img137.imageshack.us/img137/3493/setmember.jpg[/IMG]

** Server:**
1. choose the member tab
2. set a new member by clicking the new button
3. select (highlighted) the newly created member and fill in the blanks with members info if necessary
4. press the reset password 
5. if done click apply changes
6. right click the workstation icon and set to allow members start the session

**Workstation:**
1. press enter and log the members id
2. the default password is the members id
                
           **to change the members password in the workstation:**
           1. click the "set password" below the timer
           2. fill in the blanks, if done press ok

[COLOR=Red]**  To uninstall the cclfox (client and server): **[/COLOR]
     open the terminal
     $[COLOR=Red]cd libccls-0.7.1[/COLOR]              … [COLOR=Red]cd cclfox-0.7.1[/COLOR]
     $make uninstall

**Common Errors:**
e1: no workstation icons display on the cclfox server panel
    be sure to install the samba 

(to be continued)

**Installation for Windows XP Clients:** 

(to be continued)

thanks to [Yogha Restu Pramadi]("http://yogharp.wordpress.com/2007/08/23/cafe-con-leche-ubuntu-how-to/")

---

### Post by studiojunkyard on 2009-09-20
Been a while for activity on this thread, and I couldn't find an answer to my problem which is as follow.

We have 20 computers, most of which are Intel machines running Ubuntu 9.04, and 5 are AMD64 machines running Ubuntu 9.04, each system has been updated to latest updates.

I have installed client's on each machine by compiling, without any problems at all, the problem however lies with the server.

The server is an AMD machine, and I have tried compiling following the guide on the 1st post, everything seems to compile correctly, but the cclfox wouldn't run or give back error's when run from terminal. I then tried the supplied .deb files, but had to do a -i -force-architecture using dpkg to make them install, not I get back an error, which I can't remember off hand, but it was something along the lines that cclfox couldn't be run, or the system didn't know what to open it with. When I went home, I installed the server on my machine Ubuntu 9.04 up to date also, and the same .deb packages work perfectly, and the cclfox opens just fine.

Is this a problem running cclfox on AMD64 machines? Is there a .deb package available AMD64?
This would be very handy if there was, as I may be able to convert another cafe to Linux, if they can see the one I work out, working on Linux.

Any help would be appreciated.....

---

### Post by Script Warlock on 2009-09-21
oh, i forgot to mention that im working this on a 32bit machines.

boss loell, is this possible to run on 64bit machines?

studiojunkyard: what kind of error does it says when launching it on the terminal?

---

### Post by studiojunkyard on 2009-09-21
I'm sorry, I don't remember off the top of my head, and I won't be able to go into the shop for a couple of days. I may however be guiding someone who knows Linux through setting a Dell P4 server up with Ubuntu 9.04, and if that goes well, we'll just use that as the server only.

The client side works just fine on AMD64. It was just the server side that didn't

---

### Post by pmwangi80ke on 2009-09-28
> **Script Warlock said:**
> [B][http://ccl.sourceforge.net/](http://ccl.sourceforge.net/)

[/B][B]Screenshots

   [IMG]http://img196.imageshack.us/img196/8467/serverh.jpg[/IMG]
                                [/B][SIZE=3]Server[/SIZE][B]

  [IMG]http://img180.imageshack.us/img180/3489/client.jpg[/IMG]
                                 [/B][SIZE=4][SIZE=3]Client[/SIZE]

[/SIZE]**Common Installation     **

 Both side of the application (server and client) has to meet their dependencies, since this is not a debian package, we have to install the dependencies manually. CCL dependencies are
 
[LIST]
[*]sqlite3
[*]glib2.0
[*]libfox1.4(server), libfox1.6(client)
[*]openssl
[/LIST]
 **For the ccl server run these commands :**[INDENT]$ sudo apt-get install sqlite3 libsqlite3-dev[/INDENT][INDENT]$ sudo apt-get install libfox1.4 libfox1.4-dev   (server)[/INDENT][INDENT]$ sudo apt-get install libglib2.0-dev[/INDENT][INDENT]$ sudo apt-get install libssl-dev[/INDENT][COLOR=Black]**For the [COLOR=Red]ccl client [/COLOR][COLOR=Black]replace[/COLOR] the [COLOR=Red]libfox1.4[/COLOR] run these command :**[/COLOR]
          $ sudo apt-get install [COLOR=Red]libfox-1.6-0 libfox-1.6-dev  
[/COLOR]  [B]
Don’t forget the build essentials for compiling from source :[/B][INDENT]$sudo apt-get install build-essential[/INDENT]**Then edit your /etc/ld.so.conf file with :**[INDENT]$sudo gedit /etc/ld.so.conf[/INDENT]**And add these lines :**[INDENT]/usr/lib
/usr/local/lib                           …..and save the changes when done
[/INDENT]**it may look like this :**
     
include /etc/ld.so.conf.d/*.conf
 /usr/lib
 /usr/local/lib
 [B]
Then execute this :[/B]
$sudo ldconfig[COLOR=Blue][U][B]

CCL Server Installation[/B][/U][/COLOR][B]
[COLOR=Black]for the server side you’ll need these 2 files :[/COLOR][/B]
 cclfox-0.7.1.tar.bz2 [here]("http://www.mediafire.com/file/wwflozzincz/cclfox-0.7.1.tar.bz2")
libccls-0.7.1.tar.bz2    [here]("http://www.mediafire.com/file/antg3d1mh5q/libccls-0.7.1.tar.bz2")
 [B]
Put these files on your home folder and do these steps :[/B][INDENT]$tar -xjvf libccls-0.7.1.tar.bz2
$cd libccls-0.7.1
$./configure
$make
$sudo make install
$cd ..
$tar -xjvf cclfox-0.7.1.tar.bz2
$cd cclfox-0.7.1
$./configure
$make
$sudo make install[/INDENT][B]
create a folder in the home directory :[/B]
     $mkdir .cclfox
 [B]
put [this]("http://www.mediafire.com/file/t2w5azgwtmi/pem") file to the .cclfox folder right click and choose the properties and select permission then tick the box and close. generate the pem by double clicking it and  if being prompted just run it.[/B]

  [IMG]http://img42.imageshack.us/img42/3199/pem.png[/IMG]


**Then create a launcher on your desktop and add :**[INDENT]cclfox -nossl[/INDENT]on the “command” text box

 _[COLOR=Blue]**CCL Client Installation**[/COLOR]_  
 **for the client side you’ll need these 2 files :**
 cclcfox-0.7.1-FOX-1.6.tar.bz2  [here]("http://www.mediafire.com/file/ylwx3ziw44i/cclcfox-0.7.1-FOX-1.6.tar.bz2")
libcclc-0.7.1.tar.bz2  [here]("http://www.mediafire.com/file/zryqm2wz4ac/libcclc-0.7.1.tar.bz2")
 [B]
put these files on your home folder and do these steps :[/B][INDENT]$tar -xjvf libcclc-0.7.1.tar.bz2
$cd libcclc-0.7.1
$./configure
$make
$sudo make install
$cd ..
$tar -xjvf cclcfox-0.7.1-FOX-1.6.tar.bz2
$cd cclcfox-0.7.1
$./configure
$make
$sudo make install[/INDENT]**create a folder in the home directory :**
     $mkdir .cclcfox

 [B]put [this]("http://www.mediafire.com/file/t2w5azgwtmi/pem") file to the .cclfox folder right click and choose the properties and select permission then tick the box and close. generate the pem by double clicking it and  if being prompted just run it.

  [IMG]http://img42.imageshack.us/img42/3199/pem.png[/IMG]

[/B]  [B]
then create a launcher on your home folder and add : (Alt+f2 will do)[/B]

cclcfox -host serverip -name anynameor(clienthostname) -nossl[INDENT]on the “command” text box[/INDENT][INDENT]**to check the client hostname simply type in the terminal:**[/INDENT][INDENT]         $ hostname[/INDENT]**Setting the tariff :           **


[LIST=1]
[*]launch the ccl server and choose     the tariff tab
[*]select the     days(highlighted) before modifying or nothing will change. after the desired values are filled accordingly to your likes     click the apply.....
[/LIST]
 
  [IMG]http://img178.imageshack.us/img178/3427/tariff.png[/IMG]
 

 **Autorun the ccl client :     **

 to run this on startup in ubuntu/gnome 
add the above in **System** menu ->**preferences**->**sessions(8.04) | startup applications(9.04) **
 Name: any name
 Command: cclcfox -host serverip -name anynameor(clienthostname) -nossl
 Comment: whatever
 [B]
Remote shutdown and reboot :           [/B]

$sudo chmod 7755 /sbin/shutdown
        $sudo chmod 7755 /sbin/reboot
 [B]
Replacing the desktop lockscreen(client workstation) :           [/B]

[COLOR=Red]1[/COLOR]. kill the cclcfox running  >>> sudo kill -9 (pid of cclcfox)
[COLOR=Red]2[/COLOR]. create or choose the desired             photo, trim down according to the desktop's resolution and [COLOR=Red]save as lockpix.gif[/COLOR] in the .cclcfox folder located in the home             folder. Note that .cclcfox is a hidden folder so in order to             display open the home folder and select the view then tick/select             the box “show hidden files”. close when done
[COLOR=Red]3[/COLOR]. relaunch the client timer             and “end the session”.

 **Common functions :**
 
  [IMG]http://img178.imageshack.us/img178/4390/buttonsf.png[/IMG]

Green – start session
Yellow – pause and resume             session
Red – stop session
Blue – continue session
Purple – swap session
Turquoise – set timeout             (countdown)

**to start the pre-paid session:**
     press the green and the turquoise and set the time...
 
 **to start the opentime session:**
     press the green button....
 
 **to pause the session:**
     press the yellow and to resume press again the yellow...
 
 **to continue the session**
     if the customer accidentally stops the session it can be continued by pressing the blue button
 
 **to swap the session:**
     if the customer of ubuntu1(workstation) wants to transfer to ubuntu8 for some reason simply choose the ubuntu1 icon and press the purple button and choose the ubuntu8 pc. The time consumed, left or account is also transferred...
 

 **Remote functions: (right click the icon)**
 
  [IMG]http://img195.imageshack.us/img195/1194/70007083.png[/IMG]

 
 **Turn off:**
     remotely shutdown the workstation …   
 
 **Reboot:**
     remotely restart the workstation  …. 
 
 **Turn off screen:**
     remotely turn off the client workstation monitor
 
 **Allow users to start the session:**
     if selected user can start the session by clicking the pop-up tab on the workstation lockscreen marked as "click here to start"
 
 **Allow members to start the session:**
     it allows the member to start the session by pressing the enter and log-in with members id and password(default password is the members id)

**Set member:**

[IMG]http://img137.imageshack.us/img137/3493/setmember.jpg[/IMG]

** Server:**
1. choose the member tab
2. set a new member by clicking the new button
3. select (highlighted) the newly created member and fill in the blanks with members info if necessary
4. press the reset password 
5. if done click apply changes
6. right click the workstation icon and set to allow members start the session

**Workstation:**
1. press enter and log the members id
2. the default password is the members id
                
           **to change the members password in the workstation:**
           1. click the "set password" below the timer
           2. fill in the blanks, if done press ok

[COLOR=Red]**  To uninstall the cclfox (client and server): **[/COLOR]
     open the terminal
     $[COLOR=Red]cd libccls-0.7.1[/COLOR]              … [COLOR=Red]cd cclfox-0.7.1[/COLOR]
     $make uninstall

**Common Errors:**
e1: no workstation icons display on the cclfox server panel
    be sure to install the samba 

(to be continued)

**Installation for Windows XP Clients:** 

(to be continued)

thanks to [Yogha Restu Pramadi]("http://yogharp.wordpress.com/2007/08/23/cafe-con-leche-ubuntu-how-to/")




hi bro,
Thanks alot for your tutorial it really was a great help. I managed to install the server and all the clients but i still got an issue with the logs. I click on log from the cclfox server panel, then save on file tab, this generates a cclfoxdb.log file in the .cclfox file.Then i specify the dates and time and hit refresh. Then i try to open the file by going to application,programming then SQlite database browser but all it says is that the file is not SQlite 3 database. I have not configured any members, i just allow users to start session. Could you be in a position to know what it is that i didnt do right???

thanks

---

### Post by Script Warlock on 2009-09-28
logs can be save inside the .cclfox as text-based you can open it with text editor in setting the member go to member tab and input the info of a certain member. then after everything is done use the members id as the username and password to log-in....sorry screenshot is too small i'll replace this later with the bigger one...

---

### Post by pmwangi80ke on 2009-09-28
> **Script Warlock said:**
> logs are saved inside the .cclfox as text-based you can open it with text editor.


hi bro,

This is all i get when i open the file with text editor

00:00 27/09/09
00:00 01/01/10
0.00
0.00
0.00
0.00
0d 00:00
0.00

Any idea why? Thanks for your effort

---

### Post by Script Warlock on 2009-09-28
> **pmwangi80ke said:**
> hi bro,

This is all i get when i open the file with text editor

00:00 27/09/09
00:00 01/01/10
0.00
0.00
0.00
0.00
0d 00:00
0.00

Any idea why? Thanks for your effort

heres how i manage my monthly reports....

the default year setting is 01/01/04 to 01/01/37...just edit everything then save as "month 9 report or whatever" to ./cclfox folder. at the end of the day take a peek to your log tab and push the refresh button to view the days log then save again as what you did before.. then to view the saved log file with text editor inside the .cclfox folder..

---

### Post by Script Warlock on 2009-09-28
> **pmwangi80ke said:**
> hi bro,

This is all i get when i open the file with text editor

00:00 27/09/09
00:00 01/01/10
0.00
0.00
0.00
0.00
0d 00:00
0.00

Any idea why? Thanks for your effort
i think its a fresh install cclfox with no transactions yet...

---

### Post by icebox25 on 2009-11-05
Thanks Sir Loell and Sir Boyet for this thread.


> **Script Warlock said:**
> heres how i manage my monthly reports....

the default year setting is 01/01/04 to 01/01/37...just edit everything then save as "month 9 report or whatever" to ./cclfox folder. at the end of the day take a peek to your log tab and push the refresh button to view the days log then save again as what you did before.. then to view the saved log file with text editor inside the .cclfox folder..

> **pmwangi80ke said:**
> hi bro,

This is all i get when i open the file with text editor

00:00 27/09/09
00:00 01/01/10
0.00
0.00
0.00
0.00
0d 00:00
0.00

Any idea why? Thanks for your effort

Highlight the client in the "Clients" tab and in the "Cashing" tab, click "Cash", so that the Client will appear in the Log section. Go to the "Log" tab, set the date and time of the log that you want to view. 

For example, if you want to view the log for the day, just adjust the time. Click "Refresh".
[IMG]http://i55.photobucket.com/albums/g150/mvlbenoza/CCL/uforums-ccl.jpg[/IMG] 
*You can view the log of a particular member by typing his/her id. 
Then click "Save on file" and type the filename.

To view, open it by using any text editor (eg. gedit).
[IMG]http://i55.photobucket.com/albums/g150/mvlbenoza/CCL/uforums-ccl1.jpg[/IMG]

---

### Post by Script Warlock on 2009-11-05
ty icebox... actually kinorekted ko lang yung maling input ng time sa logs at report nya input kc ng time nya is 00:00-00:00 na dapat ay 00:00-23:59, dva?

---

### Post by icebox25 on 2009-11-09
I found another problem with CCL. When I set the screen resolution for a game (Alien Arena) to full screen, CCL doesn't block the screen when the rental time for the client is up (Prepaid Session). Pressing the Red/Stop button on the server doesn't work too. So, I set the resolution not in full screen instead.

---

### Post by Script Warlock on 2009-11-09
working fine to sa shop ng kaibigan ko using the ccl system which is also a mix OS icafe.....

try ko to sa machiine ko ha baka may maitulong ako sa issue pero ang alam ko may nakapag-patch na nito di ko lang matandaan ang handle niya...

---

### Post by dodimar on 2009-11-09
> **Script Warlock said:**
> working fine to sa shop ng kaibigan ko using the ccl system which is also a mix OS icafe.....

try ko to sa machiine ko ha baka may maitulong ako sa issue pero ang alam ko may nakapag-patch na nito di ko lang matandaan ang handle niya...

Boss, where could I get the client for an XP system?

---

### Post by icebox25 on 2009-11-10
> **Script Warlock said:**
> working fine to sa shop ng kaibigan ko using the ccl system which is also a mix OS icafe.....

try ko to sa machiine ko ha baka may maitulong ako sa issue pero ang alam ko may nakapag-patch na nito di ko lang matandaan ang handle niya...

Sir nasa ilalim po ng game (Alien Arena) yung CCL pic kaya di ma-view na lock na ng CCL yung PC sa Ubuntu partition. Na-test ko naman po CrazyKart full screen sa Windows partition, nalolock naman po.

---

### Post by thilandm on 2010-01-14
hi
can i make it works on red hat linux ?

---

### Post by maxixastonehead on 2010-01-28
Hi, BTW there is a way to kill ccl client just using "force quit" in gnome panel. Anyone please tell me how to diable this feature. Thanks

---

### Post by ingalfred on 2010-10-13
hello everybody
i have tried to install cclfox.deb but it requires libfox1.4 and i could'nt find it 
can anyone tell me where to find this library

---

### Post by kimesh1975 on 2011-05-20
Hi i have installed ccl okay but my server ccl will not open it opens for a second then disapeares where did i go wrong.

---

### Post by jzhicafe on 2011-05-27
is there anyone here who can help me set up ubuntu in my cafe? I have already installed it in 2 units but my problem is about the cafe timer and networking with all the units. Help please. just email me at [email]jzhicafe@gmail.com[/email] or my number at 09223211268. thank you

ken

---

### Post by NikWalker on 2011-06-29
My gift to all CCL-Users: [_[U]HERE_[/U]]("http://xubuntucorner.blogspot.com/2011/06/some-cafe-operators-yet-use-cafe-con.html")

NikWalker

---

