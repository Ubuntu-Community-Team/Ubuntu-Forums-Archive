---
title: "Howto setup Folding@Home"
date: 2005-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by ndhskp on 2005-12-10
**[COLOR="Red"]This first post is outdated, please see: [https://help.ubuntu.com/community/FoldingAtHome]("https://help.ubuntu.com/community/FoldingAtHome") and [https://help.ubuntu.com/community/FoldingAtHome/Install]("https://help.ubuntu.com/community/FoldingAtHome/Install")[/COLOR]**
**_________________________________________________**






[LIST]
[*][COLOR=red]I should note this howto is geared to 1 cpu however multi-cpu systems can still use this howto.  But each cpu in multi-cpu systems must have it's own machine id[/COLOR].[/LIST][LIST]
[*][COLOR=red]Laptop users are encouraged to see the [**Folding@Home wiki**]("https://wiki.ubuntu.com/FoldingAtHome?=%28folding%29") for special information.  I don't use an laptop so that info probably will not show up here[/COLOR].[/LIST][LIST]
[*]For information on the issue of Intel  HT cpu's (HyperThreading) see this post at the [stanford forums]("http://forum.folding-community.org/viewtopic.php?t=10427")[/LIST][LIST]
[*]I want to make sure that everyone knows that the author of the script used in this howto is [jpkotta]("http://www.ubuntuforums.org/member.php?u=36735").  User jpkotta is to blame.  wink wink.  :) [/LIST]

This is a howto for Folding@Home on Ubuntu.  Works great on Breezy-5.10 & Dapper-Drake-6.06.



Is Folding@Home for you?  (Old & New Computers welcome)
It is a distributed computing project to understand protein folding, misfolding, and related diseases.  It is run by or associated with (not sure) Stanford University.  This software will benefit best if you leave your computer on 24/7.  However the computer does not actually need to be on 24/7 **however it will take a  longer time to complete the job and if the time is long enough then you  may miss the due date there by causing the WU (work unit) to be reasigned to someone else and causing delays.  Remember that this project is about getting work units back to the researchers as fast as possible**.  So at the very least 4 to 6 hours a day of operation.




[COLOR=blue]Step 1.[/COLOR] **Do not download the folding@home executable from the folding.stanford.edu website**.  Actually you can download it if you really want.  Just run the script first to create the proper folders and then place the Folding@Home executable in No sudo [COLOR=green]/home/username/opt/foldingathome/config[/COLOR] With sudo [COLOR=red]/opt/foldingathome/config[/COLOR]

However I recomend that you download the single install script to your**/home/username** directory.  If the link below ever stops working just get the file from the [**wiki**.]("https://wiki.ubuntu.com/FoldingAtHome?=%28folding%29")

File:<removed link per OP's request>
[COLOR=red]**Click on the link ^ to download**[/COLOR]




[COLOR=blue]Step 2.[/COLOR]  Extract the archive in your **/home/username directory**[LIST]
[*]Do this by opening your terminal.  In Gnome this is **Applications/Accessories/Terminal**.[/LIST][COLOR=blue]**KDE**[/COLOR] and others you need to find and open your terminal version.  For those that don't have X or boot directly to console I'll assume you know what to do.

[COLOR=red]**Replacing "fah_install-version" with the current name**.[/COLOR]
```
tar zxvf fah_install-version.tar.gz
```> Note the following info is just to let you know about 2 files they are not needed for this howto.When you extract the script you will see 2 files called **"client.options"** and **"system.options"**.  These files allow you to pass arguments (options) to the client so those arguments become persistent where as before those arguments had to be added manually every time you started the client.  Note (client is higher precedence than system).  Syntax is bash.  Example of syntax:
```
CLIENT_OPTS='-forceasm'
```If you need a list of options the link is at end of howto.  **I don't provide support for these 2 files**. 



[COLOR=blue]Step 3.[/COLOR]  Navigate to the new folder in **/home/username/folding** and read the documentation.
```
cd fah_install
less README
``` Press the letter **q** to quit reading the documentation.





[COLOR=blue]Step 4.[/COLOR]  Install the Folding@Home client.  Please note that if you don't have root access (su or sudo) you can't use sudo or su, so in that case just use the command without sudo or su. 


[COLOR=red]**Install command**[/COLOR]           
```
sudo ./folding_install.sh install
``` 
At this point you will be asked if you want to install to the system or user.  Remember that if you don't have root (su or sudo) access to the computer you will need to choose user (1).  **Note that I personally strongly recomend that if you have root access (su or sudo) to your computer that you choose number (2) "system"**.




[COLOR=blue]Step 5.[/COLOR] **Configuring the client.**  The client will ask you some questions and you will give it some answers to optimize it for your computer.  Note that defaults will be shown in brackets [] and you may just hit enter to accept defaults.[LIST]
[*]**User name [Anonymous]?**  Make up one.[/LIST][LIST]
[*]**Team Number [0]?** Only if you want to be a part of a team.  However I recommend that you join team  [COLOR=red]**"TeamUbuntu"**[/COLOR] just enter the number [COLOR=red]**45104**[/COLOR].[/LIST][LIST]
[*]**Ask before fetching/sending work (no/yes) [no]?** Best to say no here.[/LIST][LIST]
[*]**Use proxy (yes/no) [no]?**  Most people will probably say no here.  If not just enter your proxy info.[/LIST][LIST]
[*]**Allow receipt of work assignments and return of work results greater than 5MB in size (such work units may have large memory demands) (no/yes) [no]?** Less than 1GB RAM no, 1GB or more yes.  Remember you need to take into account your operating system and programs.  Large units can exceed 500MB in ram requirements.  Also if you are on dial-up modem service you should say no here.[/LIST][LIST]
[*]**Change advanced options (yes/no) [no]?** Type no here if you want to keep it simple.[/LIST][COLOR=blue]Step 5a.[/COLOR]  **Advanced options**[LIST]
[*]**Core Priority (idle/low) [idle]?** Type idle here.  There is no benefit to putting in low and in fact could actually interfere with your computers operation.[/LIST][LIST]
[*]**Disable highly optimized assembly code (no/yes) [no]?** Type no here[/LIST][LIST]
[*]**Interval, in minutes, between checkpoints (3-30) [15]?** I chose 30.  This is how often to save the state.  You should enter 3 to 5 minutes if you have a notebook or laptop, I myself use a desktop on battery backup.  If you reboot, shutdown or crash and your state has not been saved your computer has to start over from the last saved state.[/LIST][LIST]
[*]**Request work units without deadlines (no-pref/no/yes) [no-pref]?** If you have an older computer or a computer that's not on all the time you might want to choose yes here.[/LIST][LIST]
[*]**Ignore any deadline information (mainly useful if system clock frequently has errors) (no/yes) [no]?** Type no here.  But from time to time make sure your computer clock is fairly accurate.[/LIST][LIST]
[*]**Machine ID ( 1-8 ) [1]?** Type 1 here.  [COLOR=red]**If you have a multi-cpu system then each cpu must have it's own machine id.  It is very important to make sure that under the "Advanced Settings" option each copy is given a unique machine ID ( from 1 to 8 ). The first copy (cpu 1) will default to a machine ID of 1, so additional copies should be given IDs of 2 (cpu 2), 3 (cpu 3), 4, etc**[/COLOR].[/LIST]


[COLOR=blue]Step 6.[/COLOR]  The install script will now tell you the command to start Folding@Home

[COLOR=green]**If you did not use sudo, then use this command**[/COLOR].  **Note you still need to enter this command even if you chose to install the cronjob to be absolutely sure it is started as it gives immediate feedback**.
```
/home/username/opt/foldingathome/foldingathome start
``` 
[COLOR=red]**If you did use sudo, then use this command**[/COLOR].
```
sudo /etc/init.d/foldingathome start
```**If you ever want to reconfigure the options, use this command**.```
sudo /opt/foldingathome/reconfigure.sh
or if you did not use sudo
home/username/opt/foldingathome/reconfigure.sh
or
sudo ./folding_install.sh update
``` 


[COLOR=blue]Step 7.[/COLOR]  Once you are done entering the command open up in Breezy-5.10 **Applications>System Tools>System Monitor** and Dapper-Drake-6.06 **System>Administration>System Monitor** click the Resources tab and check CPU history to make sure it's at 100% all the time.  KDE and others I don't know where your GUI system monitor is.  For the console or terminal people type **"top"**.


[COLOR=blue]Step 8.[/COLOR]  Open your file browser also known as Nautilus and go to this location: [COLOR=green]**/home/username/opt/foldingathome**[/COLOR] or [COLOR=red]**/opt/foldingathome**[/COLOR] here you can check several things.  Such as to make sure one or more directory's were created.  There are a minimum of 2 directory's called **1** and** config** respectively.  Go into both and explore.  In my 1 directory I have 3 files of interest they are: [COLOR=green]**FAHlog.txt**, **MyFolding.html**,** unitinfo.txt**.[/COLOR]  Check them out as they all have very interesting info.  By the way the directorys that are numbers are the actual working clients.  Number 1 would be cpu 1 and 2 would the second cpu and so on.  So the config directory is just used for configuration, no actual work.

The HTML file will be the one you use the most from here on out as it will allow you to get to ** unitinfo.txt**  from within your web browser **and you can bookmark it.**

[COLOR=red]**Leave the other files and directories alone for best safety!**[/COLOR]


[COLOR=blue]Step 9.[/COLOR]  Give Folding@Home the best chance possible.
**Disable all screensavers.**




Special thanks to the script author [**jpkotta**]("http://www.ubuntuforums.org/member.php?u=36735").  Also user [**jpkotta**]("http://www.ubuntuforums.org/member.php?u=36735") has indicated that you may contact him via PM (Private Message) if you have problems with the script.  Thank you to user: [**henriquemaia**]("http://www.ubuntuforums.org/member.php?u=13876") for pointing out some formatting tips.

**Folding@Home links:**
[Team Ubuntu & chew the fat social talk](http://www.ubuntuforums.org/showthread.php?t=102313)
[The main Stanford site]("http://folding.stanford.edu/")
[Official F.A.Q.]("http://folding.stanford.edu/faq.html")
[Dual core or cpu F.A.Q.]("http://folding.stanford.edu/faq.html#run.dual")
[The Stanford Folding@Home forums]("http://forum.folding-community.org")
[Version changes info]("http://folding.stanford.edu/linuxchanges.txt")
[Lightweight userguide from Stanford]("http://folding.stanford.edu/console-userguide.html")
[The one and only original Ubuntu wiki]("https://wiki.ubuntu.com/FoldingAtHome?=%28folding%29")
[Fahwiki]("http://fahwiki.net")
[A complete list of Linux command line arguments.]("http://fahwiki.net/index.php/The_FAH_client_on_Linux")

**User: [WelterPelter]("http://www.ubuntuforums.org/member.php?u=69353") has created a Folding@Home monitoring program.  [ProThink]("https://sourceforge.net/projects/prothink/")**


Cheers.

---

### Post by ToastedToad on 2005-12-14
Thanks, I'll give it a try soon.

---

### Post by ndhskp on 2005-12-14
Let me know how it goes.  Also you can choose from any number of teams out 
there if you decide to go that route not just team Ubuntu.  I should have 
mentioned that even if you sign up with a team you still have individual 
statistics.

---

### Post by henriquemaia on 2005-12-14
Thanks a lot for this. I had a friend that told me once about this, but I never installed before.

I followed your howto and everything went perfect. It's good to know my ubuntu is helping othes actively.

Thanks again.

---

### Post by ndhskp on 2005-12-15
henriquemaia, yes it is nice to know that this has a fairly direct impact on our lives as opposed to other projects that are big ifs.  Not to say that others are not worthy but just that for some people a little bit more immediate benefit is important.  Also projects like Folding@Home seem to go with the spirit of open source/free software.  Anyway glad to hear every thing went well.  I also cleaned up the howto a bit to make it easier for new users.

---

### Post by henriquemaia on 2005-12-15
[QUOTE=ndhskp]I also cleaned up the howto a bit to make it easier for new users.[/QUOTE]

I would suggest you to give some spaces between lines on Step 6, to make it more readable. You could also add some bullets and bolds. Something like this:

> Step 6. Configuring the client. The client will ask you some question and you
will give it some answers to optimize it for your computer.

[INDENT][LIST]
[*]**User name [enter a username]**    * make up one*
[*]**Team number:**    *only if you want to be a part of a team.*
[*]**Ask before fetching/sending [no]**      *best to say no here.*
[*]**Use Proxy yes/no:**    *most people will probably say no here.*
[*][B]Allow receipt of work assignments and return of work results greater 
than 5MB in size (such work units may have large memory demands) 
yes/no:[/B]      *less than 256MB RAM no, 512MB or more yes.*
[*]**Change advanced options [yes]**      *type yes here*
[*]**Core Priority [idle]**      *type idle here*
[*]**CPU Usage [100]**      *if this comes up type 100*
[*]**Disable highly optimized assembly code [no]**      *type no here*
[*]**Interval, in minutes, between checkpoints (3-30)** * [I choose 15] you can choose more if you have battery backup and have a stable computer. This is how often to save the state.*
[*]**Request work units without deadlines [no]**      *your choice but I chose no*
[*][B]Ignore any deadline information (mainly useful if system clock has
errors) [no][/B]     * I chose no as my clock is accurate.*
[*]**Machine ID ( 1-8 ) [1]**      *type 1 here*
[/LIST][/INDENT]

---

### Post by ndhskp on 2005-12-15
Thanks henriquemaia.

The formatting ideas really make the howto look better.  I gave you credit for the formatting suggestion.

---

### Post by D2X2903 on 2005-12-17
Thanks for the tutorial.  I installed Ubuntu last week after my Windows installation on my secondary (and largely unmonitored) PC became unstable *again*.  Since then, I've been trying to figure out how to set this thing up with Folding.  I just found this this morning, and now I'm back online with the second box.

- InNeedofHelp from team 36057

---

### Post by ndhskp on 2005-12-17
User D2X2903, glad everything went well with Folding@Home.  Ubuntu forums are really the best place to find out how to setup up your Ubuntu box.  There is just so much good info here.

---

### Post by drizek on 2006-01-15
oops, wrong thread....

*bump*

---

### Post by XDevHald on 2006-01-15
ndhskp: Great tut, but please note that this is a heavy tut to be doing for newbies and is great to do for those in advanced.

But for the newbies, could you please add the following below to your tut?

> **STEP: 1** Visit: [http://folding.stanford.edu/download.html]("http://folding.stanford.edu/download.html") >  **STEP: 2** Select the 5.04beta version and "Save As". Then open your home directory and create a FAH folder and drag & drop the .exe in your FAH folder.  > **STEP: 3** Open a terminal and sudo chmod -x ./FAH504-Linux.exe > **STEP: 5 **./FAH504-Linux.exe and then enter the following information as ndhskp has provided for you to do in setting up your user information. 
This is for the .exe installation and works like a charm :)

---

### Post by drdeutsch on 2006-01-17
How about adding in a tutorial about how to share Folding@Home so that users with EMIII running on Windows can monitor the progress?

---

### Post by ndhskp on 2006-01-17
Steve Myers said: ndhskp: "Great tut, but please note that this is a heavy tut to be doing for newbies and is great to do for those in advanced."

Actually it's very easy.  All you have to do is cut and paste the code, you don't have to know really what's going on too much although knowing does help.  If people want to follow your method that's great.  So feel free to point them to your post or even write an alternative tutorial and send it in.

For drdeutsch: I have not a clue what your talking about.

---

### Post by WelterPelter on 2006-02-06
I have been running folding@home for years, but now I'm trying to set it up on this ubuntu box. I have downloaded the executable, chmodded it, put in in the /opt/foldingathome/config directory. I have the two scripts, and have renamed and chmodded them and put them in /opt/foldingathome/.

However, when I run the install script (as sudo), it keeps saying that I don't have the folding executable. Obviously I do, so what's going on here?

---

### Post by ndhskp on 2006-02-06
[quote=WelterPelter]I have downloaded the executable, chmodded it, put in in the /opt/foldingathome/config directory. I have the two scripts, and have renamed and chmodded them and put them in /opt/foldingathome/.

However, when I run the install script (as sudo), it keeps saying that I don't have the folding executable. Obviously I do, so what's going on here?[/quote] 
You say that you download the executable, what do you mean by that?  The 2 install script files on the Ubuntu wiki for folding@home are all the files that you need.  I am not sure about the exact process but I think that they download the executable for you.  Also you seem to have created a /opt/foldingathome/config directory manually well you don't need to do that as that happens automatically.

Try deleting everything in the /opt/foldingathome directory and just leaving the /opt/foldingathome directory.  Download the 2 scripts and proceed to copy and paste the code into your terminal from the howto.  Remember the 2 script files are all you need don't download anything from the folding at home website.

---

### Post by WelterPelter on 2006-02-06
[QUOTE=ndhskp]You say that you download the executable, what do you mean by that?  The 2 install script files on the Ubuntu wiki for folding@home are all the files that you need.  I am not sure about the exact process but I think that they download the executable for you.  Also you seem to have created a /opt/foldingathome/config directory manually well you don't need to do that as that happens automatically.

Try deleting everything in the /opt/foldingathome directory and just leaving the /opt/foldingathome directory.  Download the 2 scripts and proceed to copy and paste the code into your terminal from the howto.  Remember the 2 script files are all you need don't download anything from the folding at home website.[/QUOTE]

Here's what happens:

$ sudo ./folding_install.sh

Creating directory structure...

It appears that you have not installed Folding@Home yet.  Would you like me to download it for you?
1) yes
2) no
#? yes

Please download the executable and save it to /opt/foldingathome/config.
Then re-run this script.
$

It just tells me to do it myself.

---

### Post by ndhskp on 2006-02-06
[quote=WelterPelter]Here's what happens:

$ sudo ./folding_install.sh

Creating directory structure...

It appears that you have not installed Folding@Home yet.  Would you like me to download it for you?
1) yes
2) no
#? yes

Please download the executable and save it to /opt/foldingathome/config.
Then re-run this script.
$

It just tells me to do it myself.[/quote] 
All right lets try this when you see the question about **"would you like me to download it for you"** don't answer with yes just put in a 1.

Make sure you are connected to the Internet when you are doing this.

Looks like this:
It appears that you have not installed Folding@Home yet.  Would you like me to download it for you?
1) yes
2) no
#? **1**

If this works great if not reply so I can continue to help you.

Also when you get to the question about running as daemon or manually and if you choose daemon use this command to start folding@home:
**username@ubuntu:/opt/foldingathome$ sudo /etc/init.d/foldingathome start**

---

### Post by WelterPelter on 2006-02-06
[QUOTE=ndhskp]All right lets try this when you see the question about **"would you like me to download it for you"** don't answer with yes just put in a 1.

Make sure you are connected to the Internet when you are doing this.

Looks like this:
It appears that you have not installed Folding@Home yet.  Would you like me to download it for you?
1) yes
2) no
#? **1**

If this works great if not reply so I can continue to help you.

Also when you get to the question about running as daemon or manually and if you choose daemon use this command to start folding@home:
**username@ubuntu:/opt/foldingathome$ sudo /etc/init.d/foldingathome start**[/QUOTE]

Ahh. Well, my embarrassment is overcome by my joy. Happily folding away. Thanks! :-D

---

### Post by ndhskp on 2006-02-06
[quote=WelterPelter]Ahh. Well, my embarrassment is overcome by my joy. Happily folding away. Thanks! :-D[/quote] 
What was it?  Were you not connected to the Internet or was it the 1 as opposed to the yes.

                                       Congratulations sir, most excellent! :-D

---

### Post by WelterPelter on 2006-02-06
It was typing yes, over and over and over, instead of one. Duh.

---

### Post by ndhskp on 2006-02-06
[quote=WelterPelter]It was typing yes, over and over and over, instead of one. Duh.[/quote] 
   I will contact the author of the scripts and suggest that he or she                             modify it so that it no longer matters whether one puts in a 1 or yes.  That whole thing can be confusing sometimes.  Anyway have fun.

---

### Post by garnertr on 2006-02-18
Greetings,

I didn't follow the previously mentioned HOW-TO on getting F@H to work, I managed to do it on my own... but one small question.

if I want to get it start in a Daemon, how would I get that in there?

Thanks!

---

### Post by ndhskp on 2006-02-18
[quote=garnertr]Greetings,

I didn't follow the previously mentioned HOW-TO on getting F@H to work, I managed to do it on my own... but one small question.

if I want to get it start in a Daemon, how would I get that in there?

Thanks![/quote]

Well I don't know for sure.  I know the Folding@home forums have a section devoted to linux and they talk about daemons there.  However if you want you can just re-install folding@home using the same username and team numbers and any points you get from the new install will be added to any points that you already have.  However if you do reinstall make sure your username and team numbers are exactly the same as before case sensitive.

If you don't want to re-install I can't really tell you anything as I originally followed the wiki myself.  You would have to create a startup script that called the folding@home exucable and tell it to run as a daemon.

I would strongly recomend re-instaling and use the howto or wiki as a guide. If you really don't want to re-install then ask in this forum thread:
[Team Ubuntu Thread](http://www.ubuntuforums.org/showthread.php?t=102313) or at the folding@home forum here [Folding@Home Forums](http://forum.folding-community.org/)

Good Luck sorry I could not be of more help.  However if you need more info or wish more discussion then feel free to post some more.

---

### Post by jpkotta on 2006-02-19
I'm the author of the scripts.  Please add a note to the HOWTO to PM me if there is a problem (but read on).  Also, you don't need to leave your computer on 24/7 to make running F@H worthwhile, but it helps.  

I found this by accident from ndhskp's signature.  I'm glad people find the installer useful.  I've read the thread and will correct the issues that people are having.  It should be much better.  Give me a day or two to update and test the installer before inundating me with bugs.

I'm up to 142825 points, try to beat me!

---

### Post by ndhskp on 2006-02-19
[quote=jpkotta]I'm the author of the scripts.  Please add a note to the HOWTO to PM me if there is a problem (but read on).  Also, you don't need to leave your computer on 24/7 to make running F@H worthwhile, but it helps.  

I found this by accident from ndhskp's signature.  I'm glad people find the installer useful.  I've read the thread and will correct the issues that people are having.  It should be much better.  Give me a day or two to update and test the installer before inundating me with bugs.

I'm up to 142825 points, try to beat me![/quote]

Hey great thanks for posting.  I never had any problems because I just entered the numerical value "1" as opposed to yes.  It can be confusing for users new to Linux to consider alternatives like "1" and so thats what was my reasoning to contact you.

I'll put up the note about PM and just say: Give the author a day or two to update and test the installer before inundating him with bugs.  I'll wait till the new files are actually up first though.

What I am personally really looking forward to is the dedicated user and group mode.  I don't know if you will have that in the next update or not but you got my support for it.  Oh later this spring I plan on adding a couple of servers to my world so watch out here I come!

---

### Post by Kaobear on 2006-02-26
Worked like a charm, running it for the Ubuntu team as we speak

---

### Post by ndhskp on 2006-02-26
[quote=Kaobear]Worked like a charm, running it for the Ubuntu team as we speak[/quote]

Execellent.  Also feel free to post in the [Team Ubuntu recruiting notice](http://www.ubuntuforums.org/showthread.php?t=102313) thread as that is were a lot of social talk happens for the team.  Again congratulation.

---

### Post by daredevil on 2006-03-01
lol i too join u drizek

---

### Post by ninuhadida on 2006-03-04
just finished installing right now. most of the time running at 95% on my P4 3.2ghz :)

---

### Post by ndhskp on 2006-03-04
[quote=ninuhadida]just finished installing right now. most of the time running at 95% on my P4 3.2ghz :)[/quote]Super.  And you have a nice Intel cpu with some muscle.

---

### Post by sleepy127 on 2006-03-04
Thanks for the tut, I am a first time linux user and never coded a thing in my life so I know no command lines. After a couple of tries I got it to work and now I am folding away on my 7th machine (the others are some shape or form of windows)

---

### Post by jpkotta on 2006-03-04
[QUOTE=sleepy127]Thanks for the tut, I am a first time linux user and never coded a thing in my life so I know no command lines. After a couple of tries I got it to work and now I am folding away on my 7th machine (the others are some shape or form of windows)[/QUOTE]

You're folding on the windows machines too, right?

---

### Post by JAwuku on 2006-03-04
This is all quite impressive. I followed your instructions, and now my AMD 2GHz is folding away in the background. I can use the web and other things, and not even notice any slowdowns at all.

---

### Post by ndhskp on 2006-03-05
[quote=JAwuku]This is all quite impressive. I followed your instructions, and now my AMD 2GHz is folding away in the background. I can use the web and other things, and not even notice any slowdowns at all.[/quote]Yeh the folding client is designed to only use cpu cycles that are unused, in other words idle cyles.  So it should never interfere with any other activity.

---

### Post by henriquemaia on 2006-03-06
This is a really helpful Howto. I have followed it again for another machine I set and all went well again. Now I have 3 CPUs working on this.

Thanks again.

---

### Post by ndhskp on 2006-03-06
[quote=henriquemaia]This is a really helpful Howto. I have followed it again for another machine I set and all went well again. Now I have 3 CPUs working on this.

Thanks again.[/quote]Your welcome. :)

---

### Post by ForeverUnknown on 2006-03-06
What would I have to change in the scripts to add flags?  I'd like to add -forceasm -verbosity 9 .

---

### Post by jpkotta on 2006-03-07
Adding flags is the next step in the scripts.  I'll work on it in the next few days.  I have already added it, but have not tested or debugged yet.  PM me if you want a preliminary version.

---

### Post by ForeverUnknown on 2006-03-07
PMed you jpkotta

---

### Post by sleepy127 on 2006-03-07
[QUOTE=jpkotta]You're folding on the windows machines too, right?[/QUOTE]
Yes I am folding with 8 processors right and hoping to add 3 in the next 2-3 weeks (waiting on a hub and a KVM switch). I am on the overclock.net team, I think we are in 60th place right now and I am 8th on the team. I have been folding for almost a year now and have over 200,000 points. My next project is a folding farm using one full pc as a server and the rest of the computers will not have video cards, or drives of any kind. Just a motherboard, processor, ram, nic,  and PSU. I may even build a mount to put maybe 4 in one case.

---

### Post by dage on 2006-03-07
hi,
how can I active this program on start up ? I've installed it in my system (/opt/foldingathome),
If my firestarter is active, Do i have to configure it for allowing F@H ?
I can't find my "unitinfo.txt" at "/opt/foldingathome" anyone can help me ?
thanks :)

---

### Post by nbcthreat on 2006-03-07
Just a quick plug here for team Ubuntu. If you're folding, why not fold with the rest of us Ubuntu users? Just enter team number 45104.

---

### Post by jpkotta on 2006-03-07
[QUOTE=hitomi_doaxbv@hotmail.com]hi,
how can I active this program on start up ? I've installed it in my system (/opt/foldingathome),
If my firestarter is active, Do i have to configure it for allowing F@H ?
I can't find my "unitinfo.txt" at "/opt/foldingathome" anyone can help me ?
thanks :)[/QUOTE]

It should automatically be set to start up on boot.  To make sure, check that there is a file called /etc/rc2.d/S99foldingathome and a file called /etc/init.d/foldingathome.  If you want to start it right now:
```
sudo /etc/init.d/foldingathome start
```

For the firewall, I don't use one.  I got too frustrated getting everything to work with it.  I'll probably set it up over spring break, and I'll make sure what settings are necessary.  By default, the client uses port 8080.  This can be changed in the advanced options, or you could set your firewall to open this port.

For your unitinfo.txt, it won't be in /opt/foldingathome.  The way I have it set up is there is a configuration directory where no folding is ever done.  The installer copies the config files from the config directory to each client directory (1, 2, ...; one for each CPU).  So the actual folding takes place in /opt/foldingathome/{1,2,...}, and that is where your unitinfo.txt will be.

---

### Post by ndhskp on 2006-03-07
[quote=hitomi_doaxbv@hotmail.com]hi,
how can I active this program on start up ? I've installed it in my system (/opt/foldingathome),
If my firestarter is active, Do i have to configure it for allowing F@H ?
I can't find my "unitinfo.txt" at "/opt/foldingathome" anyone can help me ?
thanks :)[/quote]> Open Nautilus and go to this location: /home/username/opt or /opt/foldingathome here you can check several things. Such as to make sure one or more directory's were created. In mine I have 2 directory's called 1 and config respectively. Go into both and explore. In my 1 directory I have 3 files of interest they are: FAHlog.txt, MyFolding.html, unitinfo.txt. Check them out as they all have very interesting info.

The HTML file will be the one you use the most from here on out as it will allow you to get to the other 2 files from within your web browser and you can bookmark it.Here's some more information.  The best way to get to unitinfo for myself is through the HTML file as I have that bookmarked.

---

### Post by ForeverUnknown on 2006-03-07
The new beta script seems to be working well.  I've tried it with different and multiple flags with no problems.

---

### Post by Athropos on 2006-03-08
[QUOTE=ndhskp]The best way to get to unitinfo for myself is through the HTML file as I have that bookmarked.[/QUOTE]

If you want more information on what your client is doing, you can have a look at [FahMon](http://fahmon.silent-blade.org/). There is no packaged version, but it is very easy to compile it on Breezy or Dapper as it depends on scons and wxwidgets 2.6.x which are available in the repos.

---

### Post by ndhskp on 2006-03-11
[quote=Athropos]If you want more information on what your client is doing, you can have a look at [FahMon]("http://fahmon.silent-blade.org/"). There is no packaged version, but it is very easy to compile it on Breezy or Dapper as it depends on scons and wxwidgets 2.6.x which are available in the repos.[/quote]Maybe you should make a howto for FahMon it looks interesting.  For myself I probably won't do it as thats a little too much work for me.

---

### Post by WelterPelter on 2006-03-11
I'm creating a little python app for monitoring F@H on ubuntu. Setup is a breeze and there's no compiling. Should be ready fairly soon. I've already got a (pretty crappy) test version ready that works fine. But I'm reworking the guts completely, so that will take a little while. 

I'll post back here when it's ready...

---

### Post by ndhskp on 2006-03-11
[quote=WelterPelter]I'm creating a little python app for monitoring F@H on ubuntu. Setup is a breeze and there's no compiling. Should be ready fairly soon. I've already got a (pretty crappy) test version ready that works fine. But I'm reworking the guts completely, so that will take a little while. 

I'll post back here when it's ready...[/quote]Cool we'll be waiting.

---

### Post by mjwood0 on 2006-03-12
Quick question to all --

I've been folding for Team Ubuntu for a couple weeks.  I've got FAH starting as a service when the computer starts.  Everything seems to work well and I'm folding away, but I noticed in poking around my sytem that I have four instances of FAHCore_82.exe.

```

mjwood@mojave3:/media$ ps aux | grep FahCore
root      8852  0.0  1.3  17788  3432 ?        SN   00:11   0:00 ./FahCore_82.exe -dir work/ -suffix 03 -checkpoint 5 -lifeline 8807 -version 502
root      8853  0.0  1.3  17788  3432 ?        SN   00:11   0:00 ./FahCore_82.exe -dir work/ -suffix 03 -checkpoint 5 -lifeline 8807 -version 502
root      8854 84.8  1.3  17788  3432 ?        RN   00:11 611:10 ./FahCore_82.exe -dir work/ -suffix 03 -checkpoint 5 -lifeline 8807 -version 502
root      8855  0.0  1.3  17788  3432 ?        SN   00:11   0:00 ./FahCore_82.exe -dir work/ -suffix 03 -checkpoint 5 -lifeline 8807 -version 502
mjwood    8779  0.0  0.2   3064   752 pts/0    R+   12:11   0:00 grep FahCore
mjwood@mojave3:/media$

```

All of the processes seem dependent on process 8807 - /opt/foldingathome/1/FAH502-Linux.exe

Anyone have any ideas?

---

### Post by WelterPelter on 2006-03-12
This is common behavior of the FAH client. Mine looks like that as well:

mwt@sequoia:~$ ps aux | grep FahCore
1001      8838  0.0  0.5  11896  5140 ?        SN   Mar11   0:00 ./FahCore_78.exe -dir work/ -suffix 02 -checkpoint 15 -lifeline 8797 -version 502
1001      8839  0.0  0.5  11896  5140 ?        SN   Mar11   0:00 ./FahCore_78.exe -dir work/ -suffix 02 -checkpoint 15 -lifeline 8797 -version 502
1001      8840 88.1  0.5  11896  5140 ?        RN   Mar11 1232:31 ./FahCore_78.exe -dir work/ -suffix 02 -checkpoint 15 -lifeline 8797 -version 502
1001      8841  0.0  0.5  11896  5140 ?        SN   Mar11   0:00 ./FahCore_78.exe -dir work/ -suffix 02 -checkpoint 15 -lifeline 8797 -version 502
mwt      28498  0.0  0.0   2936   748 pts/1    R+   10:02   0:00 grep FahCore

Notice that on [this page ]("http://fahwiki.net/index.php/Running_the_FAH_client_on_Linux"), almost at the bottom, it says that the FahCore starts up "several" processes when it runs as a service. No worries.

---

### Post by mjwood0 on 2006-03-12
Good to know.  Thanks!  I read that page but missed that point.  

Anyway, all seems to be well then!

Thanks!

---

### Post by WelterPelter on 2006-03-12
The reason I noticed that particular section is that I want to implement stop | start | restart behavior with my FAH Monitor program. It doesn't look particularly easy, since you have to hunt down a number of running processes and kill them individually in a manner that is fairly unclean. 

I'm looking for some good code sections in C++, Java, or Python that do something similar, if anyone knows of any.

---

### Post by ndhskp on 2006-03-12
[quote=WelterPelter]The reason I noticed that particular section is that I want to implement stop | start | restart behavior with my FAH Monitor program. It doesn't look particularly easy, since you have to hunt down a number of running processes and kill them individually in a manner that is fairly unclean. 

I'm looking for some good code sections in C++, Java, or Python that do something similar, if anyone knows of any.[/quote]Are you trying to monitor  each individual folding@home thread.  Or are you talking about your programs threads.  Not always but sometimes killing a parent kills the child threads I've noticed.

---

### Post by ndhskp on 2006-03-25
I have attached the log.  The message is to long for display.

[http://www.nathaniel-homier.net/misc-files/FAHlog.txt](http://www.nathaniel-homier.net/misc-files/FAHlog.txt)

---

### Post by twopeak on 2006-03-27
Just wondering, but how do I uninstall this?
I've followed the install instructions here: [https://wiki.ubuntu.com/FoldingAtHome](https://wiki.ubuntu.com/FoldingAtHome)
It makes my fan be very noisy...

---

### Post by ndhskp on 2006-03-27
[quote=twopeak]Just wondering, but how do I uninstall this?
I've followed the install instructions here: [https://wiki.ubuntu.com/FoldingAtHome]("https://wiki.ubuntu.com/FoldingAtHome")
It makes my fan be very noisy...[/quote]```
sudo ./folding_install.sh uninstall
```But wait what's the real problem?  Have you checked your computer to see how dusty it might be.  If it's really dirty then you need to clean it.  A dirty computer runs hotter than a clean one.  So that means your fan would have to work harder and louder.  Also please check your fan for any obstructions.  In the past I have had a loud fan and I checked it, it was because a wire was rubbing against it.  So basically clean your computer and check for obstructions and see if that don't improve the noise level.  Still too loud then maybe it's time to buy a new fan.  New fans are quieter and the fact that your old fan is so loud may mean that it's about to give up the ghost.  New fans are very inexpensive.

Hey anything to keep you folding!

---

### Post by twopeak on 2006-03-27
Well, i haven't touched it between the installation and the noise. 
It used to switch on once in a while, for example when it was drawing a silly 3d screensaver. I think it has something to do with intensive tasks.
I'm a complete n00b to linux, being used the no-noise Apple G5.

And it's for sure not dusty, i've put in extra ram one month ago and then ive blown 75% of all dust.

---

### Post by MihaiM on 2006-03-28
[http://digg.com/science/Setup_Folding@Home_for_Ubuntu_Linux](http://digg.com/science/Setup_Folding@Home_for_Ubuntu_Linux)

---

### Post by ndhskp on 2006-03-28
[quote=twopeak]Well, i haven't touched it between the installation and the noise. 
It used to switch on once in a while, for example when it was drawing a silly 3d screensaver. I think it has something to do with intensive tasks.
I'm a complete n00b to linux, being used the no-noise Apple G5.

And it's for sure not dusty, i've put in extra ram one month ago and then ive blown 75% of all dust.[/quote]Yes when the cpu is doing hard work it gets alot warmer and the cooling fans ramp up to keep it cool.  You might check with your local computer store about getting a quieter fan, meaning quieter at top speed.  But I understand if you don't want to buy a new fan and want to get rid of Folding@Home because fan noise is very irritating.  I am hearing impaired and wear a hearing aid but I still can hear my fans and the difference is astounding when my computer is off.

Anyway I am still glad you have decided to use Ubuntu.

---

### Post by ndhskp on 2006-03-28
[quote=MihaiM][http://digg.com/science/Setup_Folding@Home_for_Ubuntu_Linux]("http://digg.com/science/Setup_Folding@Home_for_Ubuntu_Linux")[/quote]

Nice! although it only has 2 Diggs at the time of this writing.

---

### Post by WelterPelter on 2006-04-02
Anyone want to be the guinea pig for a very alpha folding@home monitor I wrote in Python? Will only work with a one fah setup. 

Simple and effective - will show the percentage of the current work unit even when minimized. Nothing fancy. Not my problem if it sets your box on fire. ;) 

I've been using it for weeks, and would now like some feedback from users.

---

### Post by ndhskp on 2006-04-02
[quote=WelterPelter]Anyone want to be the guinea pig for a very alpha folding@home monitor I wrote in Python? Will only work with a one fah setup. 

Simple and effective - will show the percentage of the current work unit even when minimized. Nothing fancy. Not my problem if it sets your box on fire. ;) 

I've been using it for weeks, and would now like some feedback from users.[/quote]Okay I'll be your guinea pig, where do I get it or how.

---

### Post by WelterPelter on 2006-04-02
I'll send it to you. - Should be in your inbox.

---

### Post by ndhskp on 2006-04-02
[quote=WelterPelter]I'll send it to you. - Should be in your inbox.[/quote]Okay, WelterPelter sent it to me.  After checking it out for a few minutes I am impressed.  Also it's very easy to set up and is self explanatory.  For Folding@Home geeks it's just plain fun.  I will now be using this on a regular basis.

C'mon everybody contact WelterPelter and ask for a copy and try it out.

---

### Post by jpkotta on 2006-04-03
Why don't you just attach it to your post?

---

### Post by ndhskp on 2006-04-03
[quote=jpkotta]Why don't you just attach it to your post?[/quote]I will PM WelterPelter and ask him if I can put up the file.  It's probably okay I just want to make sure.

---

### Post by WelterPelter on 2006-04-03
See next post for downloadable application. 

Thanks for the good review, ndhskp. :)

---

### Post by WelterPelter on 2006-04-03
OK. Here's a version of the app, which is called "Protein Think", for folks to try out. 

Please realize it may not work right. It's still in alpha. 

I look forward to any feedback. Thanks.

---

### Post by drizek on 2006-04-03
Very cool, works great here.

---

### Post by ndhskp on 2006-04-03
I am hosting the program as well.  But if WelterPelter finds a more permanent home (host) then I will take it down at that point.

Edit: took it off my site as it is now at Sourceforge.

---

### Post by WelterPelter on 2006-04-03
Protein Think is now hosted at SourceForge. Get the alpha release here: [https://sourceforge.net/projects/prothink/]("https://sourceforge.net/projects/prothink/")

Thanks ndhskp! You got me going on this thing.

---

### Post by ndhskp on 2006-04-03
[quote=WelterPelter]Protein Think is now hosted at SourceForge. Get the alpha release here: [https://sourceforge.net/projects/prothink/]("https://sourceforge.net/projects/prothink/")

Thanks ndhskp! You got me going on this thing.[/quote]Very cool.  Your on Sourceforge!  And thank you for a cool program WelterPelter.

Everybody who wants to try the program get it at the Sourceforge page as that's where the current file will reside.

---

### Post by WelterPelter on 2006-04-04
For anyone who's using Protein Think, there have been two updates to the alpha release. You won't have to setup again, just replace the files and restart. 

CAUTION: if your hidden .stats directory is in your protein_think folder, make sure you don't erase that. However, if you do, just go through the setup again and you'll be fine. 

These little fixes are coming fast and furious lately, so don't be afraid to check back at sourceforge every once in a while for a new version. :cool:

---

### Post by WelterPelter on 2006-04-09
Yet another [release]("http://sourceforge.net/project/showfiles.php?group_id=164311") that fixes some bugs, especially if your team name has spaces in it (unlike the TeamUbuntu name). 

Since I'm updating this program a lot, you main want to select the "monitor" button on the download file page. That will automatically email you if there is a new file release.

---

### Post by Mark_in_Hollywood on 2006-04-17
I have a few questions.

If I install :fah_install-20060313.tar.gz

Will it create the directories needed? Or do I need to mkdir /home/folding_at_home or some such? move the tar.gz file to that newly named directory and "open" it once it is there?

Will it run at boot-up without the need for user intervention?

I can have the computer on 8 hours a day, but if I read the various posts here, if the screensaver is working, Folding is asleep? No work being done? Is there a way around this, other than turning the screensaver off? --A way around for someone who has been using Ubuntu/Linux since January 2006, that is?

---

### Post by jpkotta on 2006-04-17
Just follow the instructions.  Untar the file, run the install script, and then you can safely delete the directory that got created by the tarball (fah_install).  

It will automatically start at boot time if you install to the system.  If you install as user it will restart every hour, unless it's already running.

If you run a screensaver that uses a lot of CPU cycles, then you will do less folding, and instead display pretty pictures.  Personally, I choose a pretty screensaver that doesn't use a lot of CPU, "Intermomentary".  But a screensaver won't turn FAH off, it just sucks away CPU cycles from it.

---

### Post by Mark_in_Hollywood on 2006-04-17
Why?

mark@lexington:~$ tar zxvf fah_install-version.tar.gz
tar: fah_install-version.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mark@lexington:~$

---

### Post by ndhskp on 2006-04-17
[quote=Mark_in_Hollywood]Why?

mark@lexington:~$ tar zxvf fah_install-version.tar.gz
tar: fah_install-version.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mark@lexington:~$[/quote]You probably downloaded the script to your desktop.  Try this:```
cd /home/put-your-username-here/Desktop
```Now try following the instructions.

---

### Post by jpkotta on 2006-04-18
Don't literally type 'version'.  If you're using the current one from the wiki,
```
tar zxvf fah_install-20060313.tar.gz
```

Also, as ndhskp said, you have to be in the directory that you saved the file in.  If you lost it, 
```
find ~ -name 'fah_install*.tar.gz'
```

---

### Post by Mark_in_Hollywood on 2006-04-18
I'll get it right, eventually:

mark@lexington:~$ tar zxvf /home/mark/fah_install-20060313.tar-2

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

mark@lexington:~$ tar zxvf fah_install-20060313.tar-2

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
mark@lexington:~$

I deleted the downloaded .tar.gz and downloaded a fresh copy. Without the .tar-2. I moved the file to /home

mark@lexington:/home$ tar zxvf fah_install-20060613.tar.gz
tar: fah_install-20060613.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Twilight Zone, anyone?

---

### Post by ndhskp on 2006-04-19
[quote=Mark_in_Hollywood]I'll get it right, eventually:

mark@lexington:/home$ tar zxvf fah_install-20060613.tar.gz
tar: fah_install-20060613.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Twilight Zone, anyone?[/quote]I am confused here.  Are you sure you moved it to your home folder.  You can keep it on your desktop if you want, it really does not make any difference where you place it.  Open your file browser and go to your home folder to see if the file is there.  Another thing is to put the file on your desktop and right click it and select extract here, but this is assuming your using the Gnome desktop.

---

### Post by jpkotta on 2006-04-19
Why is it getting renamed to *-2?  Whatever.  Just redownload the file.  Anywhere.  It doesn't matter.  Just make sure that the filename is "fah_install-...".  Then run the find command.
```
find ~ -name 'fah_install*'
```
It will tell you where the file is if it is anywhere in your home directory.  So let's say it is in /home/mark/supersecretdir:
```
$ find ~ -name 'fah_install*'
/home/mark/supersecretdir/fah_install-20060313.tar.gz
$ cd ~/supersecretdir
$ tar zxvf fah_install-20060313.tar.gz
```

You shouldn't do things in /home, that's basically a system directory, a place for all users' home directories.  You don't want to do things in /home anymore than you want to do things in /.  Do your work in /home/username (aka $HOME, aka ~), or subdirectories of it.

We will get this thing installed.

---

### Post by ndhskp on 2006-04-19
[quote=jpkotta]You shouldn't do things in /home, that's basically a system directory, a place for all users' home directories.  You don't want to do things in /home anymore than you want to do things in /.  Do your work in /home/username (aka $HOME, aka ~), or subdirectories of it.

We will get this thing installed.[/quote]Actually by /home directory I meant /home/username.  I guess I've been using Linux long enough that I had assumed that everbody would know what I was talking about, I sometimes forget that people will take things literally or that they are new users.  Always much harder to get myself across using words.  Jpkotta is right always use /home/username.

I will keep it in my mind for the future that not everyone will understand that when I say home I mean username home so from now on I will use /home/username.  That can be confusing to others for sure.  Thanks for catching that.

So Mark_in_Hollywood does this help you the distinction between /home and home/username.

---

### Post by Mark_in_Hollywood on 2006-04-20
Yes, distinction now understood. I have moved the fah...tar.gz to:

/home/mark

doing

ls

shows it residing there.

doing 

mark@lexington:~$ sudo tar zxvf fah_install-20060613.tar.gz
tar: fah_install-20060613.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Anybody else got any ideas>

---

### Post by jpkotta on 2006-04-20
I'm baffled.  If the file is in the directory, how can tar not find it?  You don't need to use sudo to untar the file, but it should work anyway.  I decided to install this on a school computer, just to see if there's some problem with the tarball on the wiki. It worked fine, but I found a bug (nothing major).  Anyway, when I get home tonight, I'll fix the bug, upload the new version to the wiki, and make a zip file and post it here.  Maybe a zip file will work better than a tarball, but I doubt it.  Have you had trouble with other .tar.gz files?

---

### Post by Mark_in_Hollywood on 2006-04-20
Had any trouble with .tar.gz??

Hmmmm

Well, I'm quite embarassed to say that I'm not sure. 

On one occasion I did a ./ for something. Mostly I've learned to let Synaptic do the work. Then Automatix and Update Manager.

I try to stay out of the operating system. This is my third time installing ubuntu, the two prior having blow up. As much as I want to Fold, I much more don't want to do a re-install. I'm using a 56K modem, the update/upgrade took over 7x24 hour day to download it all. 

Please be patient. I've use Ubuntu since March of this year. Before that Fedora Core 4 since January 21st, 2006. Fedora blew up as I tried to update the OS. I got handed an Ubuntu CD and have never looked back.

I'm going to move that FAH file around and try to see what is "up".

Thanks for your timely, kindly on-going support.

---

### Post by jpkotta on 2006-04-21
Here's an updated zipfile.

---

### Post by Mark_in_Hollywood on 2006-04-21
So I saw the .zip file. Clicked it for downloading and "saved" it rather than having Firefox "open" it. It saved. Then I could do nothing with it. Called Nautilis and had the Archive Manager "open" it. A list of file appeared. The README had no instructions as to how to execute the installation. OK. I will try running the .sh in a terminal with ./

Wish me luck!!

---

### Post by OfficeLinebacker on 2006-04-23
[QUOTE=jpkotta]Adding flags is the next step in the scripts.  I'll work on it in the next few days.  I have already added it, but have not tested or debugged yet.  PM me if you want a preliminary version.[/QUOTE]
Any update on this, jpkotta?  I'd like to do the forceasm -verbosity 9 thing, also.

Also, the script still downloads version 5.02 of the client, while the most current release is 5.04.  

PM on the way.

---

### Post by ndhskp on 2006-04-23
[quote=OfficeLinebacker]Any update on this, jpkotta?  I'd like to do the forceasm -verbosity 9 thing, also.

Also, the script still downloads version 5.02 of the client, while the most current release is 5.04.  

PM on the way.[/quote]The latest script on the wiki and howto has full support for options.  You should install the latest script.  Also 5.04 is a beta client.  The script only downloads the latest stable version.  If you really want to download 5.04 then open Gedit or your favorite text editor and find all instances of 5.02 and replace them with 5.04 and save the file.  If the editor ask to overwrite in the proccess of saving say yes.

---

### Post by ndhskp on 2006-04-23
[quote=Mark_in_Hollywood]So I saw the .zip file. Clicked it for downloading and "saved" it rather than having Firefox "open" it. It saved. Then I could do nothing with it. Called Nautilis and had the Archive Manager "open" it. A list of file appeared. The README had no instructions as to how to execute the installation. OK. I will try running the .sh in a terminal with ./

Wish me luck!![/quote]Well did it work, I hope so.

---

### Post by OfficeLinebacker on 2006-04-23
[QUOTE=ndhskp]The latest script on the wiki and howto has full support for options.  You should install the latest script.  Also 5.04 is a beta client.  The script only downloads the latest stable version.  If you really want to download 5.04 then open Gedit or your favorite text editor and find all instances of 5.02 and replace them with 5.04 and save the file.  If the editor ask to overwrite in the proccess of saving say yes.[/QUOTE]
You say I should install the latest version; what if I already have a version installed?

---

### Post by OfficeLinebacker on 2006-04-23
Also, how do I know which version I have installed?
 
I think folding@home should be a package you can install via apt-get / synaptic. That would be a big boost for the project.

---

### Post by jpkotta on 2006-04-23
Stealing my avatar, eh?  Or maybe I stole yours?  Well, the more fractals, the better.

To run with the beta client, you have to edit exactly one line in the installer and exactly one line in the init script.  Maybe I'll add a question in the installer that asks if you want the beta client or not.  The magic line is the one with "executable=".  I would recommend removing everything first before getting the beta client, so you have a clean install.

You can safely rerun the installer with the "update" option.  It will not overwrite your current options files (unless you tell it to), nor the work queue.  You can update if even while the client is running. Update only reinstalls the helper scripts, it does nothing with the client itself.

I don't think it's possible to make this a .deb file.  You must download the client from Stanford's web site.  You have to manually configure the client (unless you want to fold as Anonymous for Team Default).  I don't think putting it in the repos makes it any easier to install.  Anyone who wants to run it will search the forums or the wiki when they don't find it in the repos, and find the installer.  And the main reason is that I'm lazy, and I don't want to learn how to make a .deb package (at least not right now).  Someone else is welcome to, as long as the above problems are worked around.

---

### Post by OfficeLinebacker on 2006-04-24
[QUOTE=jpkotta]Stealing my avatar, eh?  Or maybe I stole yours?  Well, the more fractals, the better.

To run with the beta client, you have to edit exactly one line in the installer and exactly one line in the init script.  Maybe I'll add a question in the installer that asks if you want the beta client or not.  The magic line is the one with "executable=".  I would recommend removing everything first before getting the beta client, so you have a clean install.

You can safely rerun the installer with the "update" option.  It will not overwrite your current options files (unless you tell it to), nor the work queue.  You can update if even while the client is running. Update only reinstalls the helper scripts, it does nothing with the client itself.

I don't think it's possible to make this a .deb file.  You must download the client from Stanford's web site.  You have to manually configure the client (unless you want to fold as Anonymous for Team Default).  I don't think putting it in the repos makes it any easier to install.  Anyone who wants to run it will search the forums or the wiki when they don't find it in the repos, and find the installer.  And the main reason is that I'm lazy, and I don't want to learn how to make a .deb package (at least not right now).  Someone else is welcome to, as long as the above problems are worked around.[/QUOTE]
My avatar is brighter and bigger than yours!  OfficeLinebacker FTW!
 
OK, I am not too worried about the version of the executable.  What about options like verbosity -9 and advmethods, etc?

---

### Post by jpkotta on 2006-04-24
From the README:

> Configuration

There are two ways to configure the client.  First, you can use the client's
question/answer configuration.  The reconfigure.sh script, located in the
foldingathome directory, is the proper way to do this.  Using it ensures that
everything will be updated correctly.  

The other route to configuration is by giving options to the client when
starting it.  The init script will get these options from two sources.  The
first is /etc/default/foldingathome.  This is for system-wide options.  All
clients will look for it, even those installed to a user's $HOME directory.  The
other place is in the configuration directory, foldingathome/config.  In here
there should be an option file for each client.  These per-client options will
override the system-wide options.

This makes sense to me.  If it is confusing to you, let me know so I can fix it.

---

### Post by Mark_in_Hollywood on 2006-04-24
[QUOTE=ndhskp]Well did it work, I hope so.[/QUOTE]

Sadly, I report that death of my Folding at Home Project. 

I tried the tar.gz, I tried the .zip and neither will write directories, etc. I'm more than baffled.

I haven't modified a thing of Ubuntu, without using Synaptic, Update Manager or Automatix. I haven't modified a .conf file anywhere. According to Update Manager, I have "everything" up-to-date.

So, for now, I give up and will revisit this issue once Dapper Drake is up and running.

NUTS!!!

---

### Post by OfficeLinebacker on 2006-04-24
[quote=jpkotta]From the README:



This makes sense to me.  If it is confusing to you, let me know so I can fix it.[/quote] jpkotta, I just ran reconfigure, and that's only for options *within* the program.  I am talking about *command line arguments.* most notably -verbosity 9.  How do I set those?  Or are those in the realm of the second way?

edit:  the second way seems to just allow editing of the client.cfg file, which again does not affect the arguments passed to the program, I don't believe

---

### Post by ndhskp on 2006-04-24
[quote=Mark_in_Hollywood]Sadly, I report that death of my Folding at Home Project. 

I tried the tar.gz, I tried the .zip and neither will write directories, etc. I'm more than baffled.

I haven't modified a thing of Ubuntu, without using Synaptic, Update Manager or Automatix. I haven't modified a .conf file anywhere. According to Update Manager, I have "everything" up-to-date.

So, for now, I give up and will revisit this issue once Dapper Drake is up and running.

NUTS!!![/quote]Shoot, that always sucks when you run up against something like that.  I know that I have been in that situation myself many times.  Experiance Ubuntu some more and someday in the future just try agin.  Dapper Drake 6.06 comes out in June so maybe sometime this fall.  Good luck.

---

### Post by ndhskp on 2006-04-24
[quote=OfficeLinebacker]jpkotta, I just ran reconfigure, and that's only for options *within* the program.  I am talking about *command line arguments.* most notably -verbosity 9.  How do I set those?  Or are those in the realm of the second way?

edit:  the second way seems to just allow editing of the client.cfg file, which again does not affect the arguments passed to the program, I don't believe[/quote]Okay when you downloaded the script and uncompressed it there should have been 2 files called client and system.  Look in those files for an example.  I don't use those files myself, I used to until jpkotta pointed something out to me.  Any way I can't remember if you edit the files then run the installer or edit the files in the folding dir, you'll have to ask jpkotta about that.  Example of client.options file.  Remember Linux command line arguments go here or system, of course.```
# Folding@Home Linux client options.

# This file contains per-client options.  It will override options specified in 
# /etc/default/foldingathome, if it exists.

# Use the CLIENT_OPTS variable to set any options that you want the client to  
# use.                              
# Example: CLIENT_OPTS='-advmethods -forceasm'                                 
                                                                               
# Run the client executable with the help option (e.g. "FAH504-Linux.exe -help")
# to learn what options are available.

# Options specified here will override system-wide options.
# To keep system-wide options, use CLIENT_OPTS="$CLIENT_OPTS -opt1 -opt2 ..."
# Remember that double quotes are different than single quotes.
                
#CLIENT_OPTS=''
```Oh ya, I almost forgot to tell you that these files only come with the more recent scripts.  Like I said you probably want to download and install the latest script.  Uninstall your current one by using  ```
sudo ./folding_install.sh uninstall
```

---

### Post by OfficeLinebacker on 2006-04-25
OK, thanks.  I will wait for Jonathan to post again before taking any action.

I did notice that I do not appear to have a /etc/default/foldingathome file on my system.

Thanks for all your help guys.  I am used to doing this in WIndows with regedit, I like knowing what my performance fraction is.

---

### Post by jpkotta on 2006-04-25
Download the latest installer tarball from the wiki.  Unpack and run the installer with the update option.  You can edit the relevant files before or after you install.  If you're installing to the system, then the relevant files will be /etc/default/foldingathome and /opt/foldingathome/config/client?.options.  BTW, most config files for daemons ("services" in Windows)  are in /etc/default (on Debian systems, anyway).  I guess the nice thing about the registry is that everything is in one place.  Of course, that's also the problem with it.  I really wish distributions would standardize where files go.

---

### Post by OfficeLinebacker on 2006-04-25
OK, got it.  I think I had a version from March.  DLed the version from 4/21 and edited the systemwide options file.  Thanks!  (And sorry for being so dense--your help is really, REALLY appreciated).

---

### Post by OfficeLinebacker on 2006-04-25
Hey, whoever uses this howto, post what team you fold for, and if you wish your username.  I fold for 2cpu.com. team #3074.  Lumberg is my username!

---

### Post by ndhskp on 2006-04-25
[quote=OfficeLinebacker]Hey, whoever uses this howto, post what team you fold for, and if you wish your username.  I fold for 2cpu.com. team #3074.  Lumberg is my username![/quote]Uh, actually the social talk happens over at Team Ubuntu located here: **[Folding social talk](http://www.ubuntuforums.org/showthread.php?t=102313)**.  Please use that thread for social talk.  Don't worry OfficeLinebacker they are very friendly over there.  I have had good conversations there.  So come on over and join us dude!

---

### Post by OfficeLinebacker on 2006-04-25
[QUOTE=ndhskp]Uh, actually the social talk happens over at Team Ubuntu located here: **[Folding social talk](http://www.ubuntuforums.org/showthread.php?t=102313)**.  Please use that thread for social talk.  Don't worry OfficeLinebacker they are very friendly over there.  I have had good conversations there.  So come on over and join us dude![/QUOTE]
Oh OK, thanks for keeping me in check in a friendly way.

---

### Post by OfficeLinebacker on 2006-04-25
Well, whatever I did, folding at home now no longer is automatically started at startup.

](*,)

---

### Post by OfficeLinebacker on 2006-04-25
OK, going nuts here.  I finally got folding to start on my machine, but the flags I specified in 

/opt/foldingathome/config/client1.options

```

# Folding@Home Linux client options.

# This file contains per-client options.  It will override options specified in
# /etc/default/foldingathome, if it exists.

# Use the CLIENT_OPTS variable to set any options that you want the client to
# use.
# Example: CLIENT_OPTS='-advmethods -forceasm'

# Run the client executable with the help option (e.g. "FAH504-Linux.exe -help")
# to learn what options are available.

# Options specified here will override system-wide options.
# To keep system-wide options, use CLIENT_OPTS="$CLIENT_OPTS -opt1 -opt2 ..."
# Remember that double quotes are different than single quotes.

#CLIENT_OPTS='-verbosity 9 -forceasm'


```

did not get applied!

GRRRR!

---

### Post by ndhskp on 2006-04-25
[quote=OfficeLinebacker]OK, going nuts here.  I finally got folding to start on my machine, but the flags I specified in 

/opt/foldingathome/config/client1.options

```

# Folding@Home Linux client options.

# This file contains per-client options.  It will override options specified in
# /etc/default/foldingathome, if it exists.

# Use the CLIENT_OPTS variable to set any options that you want the client to
# use.
# Example: CLIENT_OPTS='-advmethods -forceasm'

# Run the client executable with the help option (e.g. "FAH504-Linux.exe -help")
# to learn what options are available.

# Options specified here will override system-wide options.
# To keep system-wide options, use CLIENT_OPTS="$CLIENT_OPTS -opt1 -opt2 ..."
# Remember that double quotes are different than single quotes.

#CLIENT_OPTS='-verbosity 9 -forceasm'


``` 
did not get applied!

GRRRR![/quote]Whenever there is an # sign in front of the options that means it is commented out.  In other words it says ignore me.  So just remove the # sign.```
CLIENT_OPTS='-verbosity 9 -forceasm'
```

---

### Post by OfficeLinebacker on 2006-04-25
[quote=ndhskp]Whenever there is an # sign in front of the options that means it is commented out. In other words it says ignore me. So just remove the # sign.```
CLIENT_OPTS='-verbosity 9 -forceasm'
```[/quote]  
Wow.  I CANT RAED.

Edit:  I resarted after applying some updates and this time there was FAH at the top of my top display.

At this point I don't care what I did or anything, as long as this continues to be the case:

-folding starts automatically as a service at startup
-verbosity and forceasm arguments get passed to FAH every time it starts up.

Sorry if I am grumpy.  Have had a bad evenihg personally and venting it on the boards is not appropriate, but we all know that we're not robots.  Things get to us sometimes.  I probably need to watch some shocking videos of people getting their comeuppance.

---

### Post by halitech on 2006-06-25
I'm hoping someone here can help me out cause I can't seem to find what I'm looking for (either no one has asked or I've missed it) but I was wondering if there is anyway of checking the status of F@H on a machine running ubuntu with only the command line? I can check TOP and see it running, even after a reboot so I know I've set that up properly but will something like protein think work without a GUI or do I just need to take a look at the unitinfo.txt file to see how I'm doing?

---

### Post by WelterPelter on 2006-06-26
[quote=halitech]I'm hoping someone here can help me out cause I can't seem to find what I'm looking for (either no one has asked or I've missed it) but I was wondering if there is anyway of checking the status of F@H on a machine running ubuntu with only the command line? I can check TOP and see it running, even after a reboot so I know I've set that up properly but will something like protein think work without a GUI or do I just need to take a look at the unitinfo.txt file to see how I'm doing?[/quote]

Just take a look at the unitinfo.txt - that will tell you what's up.

---

### Post by TimeForBears on 2006-07-13
Hello,

I set up folding following this howto.

I'm running dual opterons, and I'm currently folding as 'anaonymous' - can I set up the client1.options and client2.options (or /etc/default/foldingathome) to specify my username and team number?

Any help wuold be appreciated.

Thanks,

TFB

---

### Post by TimeForBears on 2006-07-13
idiot.

completely missed the /1/client.cfg and /2/client.cfg.

question answered. 

sorry

TFB

---

### Post by kebabtomten on 2006-07-13
I have read this howto and some pages but i dont really know what Folding@Home means, so what does it means? :>

---

### Post by OfficeLinebacker on 2006-07-13
> **kebabtomten said:**
> I have read this howto and some pages but i dont really know what Folding@Home means, so what does it means? :>
It's sort of like donating your computer's processing power to help further medical science.

---

### Post by jpkotta on 2006-07-13
> **OfficeLinebacker said:**
> It's sort of like donating your computer's processing power to help further medical science.

It's not *like* that...it's *exactly* that.

[https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

---

### Post by forte-fine-art on 2006-07-16
Hi Everyone,

Fairly new to Linux and brand new to Ubuntu and having all kinds of trouble getting folding@home up & running on my Xubuntu installation.

I've followed the instructions very closely and can't get passed a "No such file or directory" error message.

I've used the install script AND the instructions on the folding@home site and no luck what so ever.

(Please note that I am folding on several other linux boxes withn distros from Fedora Core & Suse, along with a couple of OS X-PPC configurations, so I'm not entirely "wet behind the ears" but not competent enough to work this Xubuntu issue out by myself. Frankly, this has me completely baffled!).

Here's what happens when I run the install script:

[INDENT]./folding_install.sh install

Do you want to do this for this user or for the whole system?

1) user
2) system
3) cancel
Please pick a number: 2

Creating directory structure...


Looking for FAH502-Linux.exe...


I couldn't find the client executable.  If you have it already, please copy it to /opt/foldingathome/config/.
Do you want me to download it for you?

1) yes
2) no
Please pick a number: 1
--00:27:44--  [http://www.stanford.edu/group/pandegroup/release/FAH502-Linux.exe](http://www.stanford.edu/group/pandegroup/release/FAH502-Linux.exe)
           => `FAH502-Linux.exe'
Resolving [www.stanford.edu](www.stanford.edu)... 171.67.20.36
Connecting to www.stanford.edu|171.67.20.36|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 249,236 (243K) [application/x-msdos-program]

100%[=============================================================>] 249,236      158.17K/s

00:27:46 (157.72 KB/s) - `FAH502-Linux.exe' saved [249236/249236]


Found 1 cpus.  I will create one client for every cpu.


Creating foldingathome user.


Press 'q' to exit the license viewer.
./folding_install.sh: line 70: /opt/foldingathome/config/FAH502-Linux.exe: No such file or directory
/opt/foldingathome/reconfigure.sh: line 19: ./FAH502-Linux.exe: No such file or directory
cp: cannot stat `/opt/foldingathome/config/machinedependent.dat': No such file or directory
cp: cannot stat `/opt/foldingathome/config/MyFolding.html': No such file or directory
cp: cannot stat `/opt/foldingathome/config/client.cfg': No such file or directory
/bin/sed: can't read /opt/foldingathome/1/client.cfg: No such file or directory

Adding startup script to /etc/init.d
`/root/home/fah_install/foldingathome' -> `/etc/init.d/foldingathome'
 Adding system startup for /etc/init.d/foldingathome ...
   /etc/rc0.d/K01foldingathome -> ../init.d/foldingathome
   /etc/rc1.d/K01foldingathome -> ../init.d/foldingathome
   /etc/rc6.d/K01foldingathome -> ../init.d/foldingathome
   /etc/rc2.d/S99foldingathome -> ../init.d/foldingathome
   /etc/rc3.d/S99foldingathome -> ../init.d/foldingathome
   /etc/rc4.d/S99foldingathome -> ../init.d/foldingathome
   /etc/rc5.d/S99foldingathome -> ../init.d/foldingathome

To start folding right now, run /etc/init.d/foldingathome as root.

Installing global options.

`system.options' -> `/etc/default/foldingathome'
`client.options' -> `/opt/foldingathome/config/client1.options'
`README' -> `/opt/foldingathome/README'

To start folding right now, run '/opt/foldingathome/foldingathome start'

root@xubuntu-francis:~/home/fah_install# /opt/foldingathome/foldingathome start
bash: /opt/foldingathome/foldingathome: No such file or directory
root@xubuntu-francis:~/home/fah_install#

[/INDENT]


Thanks so much for your help!

---

### Post by forte-fine-art on 2006-07-16
[SIZE="3"]**Problem solved!!**[/SIZE]

The "No such file or directory" message was not referring to any of the folding@home related files but to a **missing libc6-dev package** and this will effect more than just your attempts to install folding@home. The "light went on" as I was trying to install Java and got the same "No such file or directory" message.

For those like me, not familiar with the libc6-dev package (and the libc6-dev-i386 which is needed for use with 64 bit systems) does the following:

[INDENT]** libc6-dev: GNU C Library: Development Libraries and Header Files**
Contains the symlinks, headers, and object files needed to compile
and link programs which use the standard C library.

**libc6-dev-i386: GNU C Library: 32bit Development Libraries for amd64**
Contains the symlinks and object files needed to compile and link programs
which use the standard C library. This is the 32bit version of the
library, meant for amd64 systems.
[/INDENT]

It seems I needed to use **Synaptic** to install the libc6-dev-i386 package (I'm running a 64 bit system. The libc6-dev was selected automatically, must be a dependency?). I guess Xubuntu does not install the above packages during installation but Ubuntu does?

**Now I'm folding as fast as the little rodent will run!**

I'm just hoping that all the hair I pulled out will grow back.

Great community! I look forward to being a part of it all.

Thanks.

---

### Post by meander on 2006-07-29
strange, i installed without sudo, and all went well until i tried to start it, which gives me: > ~/fah_install$ start-stop-daemon: Unable to open pidfile `/var/tmp/FAH502-Linux.exe-1.pid' for writing: Permission denied (Permission denied)

---

### Post by jpkotta on 2006-07-29
Please post the results of the following command:```
ls -ld /var/tmp
```

If that command doesn't work as a user, then run it with sudo.

---

### Post by essention on 2006-08-01
Excellent Post told me exactly what i needed to do.

Thanx.

---

### Post by Tobba25 on 2006-09-22
So what is the deal, is this going to clog up my system now? I thought this was just something that would use my cpu when the screensaver turned on?

---

### Post by swaaye on 2006-09-22
Dare i ask if it would be possible to change the folder it installs to? I dual boot XP on here and would like the two OS's to have access to the same work files instead of doing their own thing.

I tried to figure things out on my own but this isn't exactly a simple batch file we have here. The other FAH install is on a mounted FAT32 drive. "/media/bigpart/fah"

---

### Post by OfficeLinebacker on 2006-09-23
> **swaaye said:**
> Dare i ask if it would be possible to change the folder it installs to? I dual boot XP on here and would like the two OS's to have access to the same work files instead of doing their own thing.

I tried to figure things out on my own but this isn't exactly a simple batch file we have here. The other FAH install is on a mounted FAT32 drive. "/media/bigpart/fah"

You  can't work cross platform in FAH.  GO to the actual FAH forums if you want info on  FAH on dual-boot systems.   If you don't spend a significant amount of time on both OSs, you need to turn timeless WUs on at least the one you spend less time in.

---

### Post by jpkotta on 2006-09-23
> **Tobba25 said:**
> So what is the deal, is this going to clog up my system now? I thought this was just something that would use my cpu when the screensaver turned on?

FAH runs all the time, not just when the screensaver runs.  It runs at a very low priority, so you should never feel an impact (other than memory usage, but you can control that).

[http://techreport.com/etc/2002q4/foldingimpact/index.x?pg=1](http://techreport.com/etc/2002q4/foldingimpact/index.x?pg=1)

I was going to add this to the wiki [page]("https://help.ubuntu.com/community/FoldingAtHome"), but for some reason I can't edit anything in the wiki.

---

### Post by jpkotta on 2006-09-23
> **OfficeLinebacker said:**
> You  can't work cross platform in FAH.  GO to the actual FAH forums if you want info on  FAH on dual-boot systems.   If you don't spend a significant amount of time on both OSs, you need to turn timeless WUs on at least the one you spend less time in.

The Windows console client works in Wine, so you can run cross platform.

If you use the installer script from the wiki, you can just install as usual, and after installation:
[LIST=1]
[*]move /opt/foldingathome to whatever you want
[*]change the line "fah_dir=/opt/foldingathome" in the script /etc/init.d/foldingathome to point to whereever you moved it
[*]change the line that looks like "executable=FAH502-Linux.exe" to have the name of the windows client (or rename the windows client)
[*]change any lines that look like "--exec $client_dir/$executable" to "--exec wine $client_dir/$executable"
[/LIST]

Disclaimer: I have no idea if this will actually work, but it should be at least a step in the right direction.  You can always write your own init script too.


Also, I'd bet that the Linux client runs in Cygwin.

---

### Post by sleepy127 on 2006-09-26
Okay, in need of a little help. I was able to set this up before but for some reason cannot get it to work now. I go thru the steps and extract the folder to home/sleepy127/folding and in that file is the fah install folder. I get to step 4 and I get a command not found error. I try to double click the folding install file and choose run in terminal and terminal pops up and closes immediately. If I choose to run it it does nothing. I can not figure out what I am doing wrong.

This is the last command that I tried. I modified the original command thinking that maybe it was not specific to my install and I received the same command not found reply.
 sudo ./folding/folding_install.sh install

---

### Post by jpkotta on 2006-09-27
The directory that gets created is fah_install, not folding.  You can see what files (and directories) are in the current directory with the "ls" command (ls = LiSt).  Look [here]("http://rute.2038bug.com/index.html.gz") for more than you ever wanted to know about the command line and Unix/Linux in general.

---

### Post by smbm on 2006-10-02
Has anyone tried this on edgy? If so did it work? Thanks

---

### Post by henriquemaia on 2006-10-04
I'm always getting back here. As the winter approaches, I start using folding@home again, since during summer I can't leave the computers on all day. Once again, I just have to follow the howto to have things set up in a instant. 

Thanks.

---

### Post by robinl on 2006-10-04
Does the script break on Edgy or is it only me? Since I dist-upgraded to Edgy I've been getting errors like these: 

```
$ sudo /etc/init.d/foldingathome start
/etc/init.d/foldingathome: 23: [[: not found
/etc/init.d/foldingathome: 33: [[: not found
/etc/init.d/foldingathome: 147: [[: not found
/etc/init.d/foldingathome: 147: arith: syntax error: "++num"
```

---

### Post by jpkotta on 2006-10-04
> **robinl said:**
> Does the script break on Edgy or is it only me? Since I dist-upgraded to Edgy I've been getting errors like these: 

```
$ sudo /etc/init.d/foldingathome start
/etc/init.d/foldingathome: 23: [[: not found
/etc/init.d/foldingathome: 33: [[: not found
/etc/init.d/foldingathome: 147: [[: not found
/etc/init.d/foldingathome: 147: arith: syntax error: "++num"
```

That's weird.  Try changing the top line to ```
#!/bin/bash
``` I don't run Edgy, so I can't test it right now.  I'll make an Edgy chroot or virtual machine or something and test it before it's released.  Unfortunately, I don't have time until next week.

---

### Post by robinl on 2006-10-04
Yep that fixed it. Thanks alot.

PS: why does it work in Dapper but not Edgy? Aren't sh and bash almost the same in syntax?

---

### Post by jpkotta on 2006-10-04
[https://wiki.ubuntu.com/EdgyBetaAnnouncement](https://wiki.ubuntu.com/EdgyBetaAnnouncement)

>   * New init system.

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

> Change the /bin/sh symlink on Ubuntu systems to point to the dash shell instead of the current bash shell.

That's probably it.  I apparently didn't write the init script to be executable by a Bourne shell; I have some Bash assumptions.

---

### Post by jpkotta on 2006-10-04
I've updated the init script.  I think it's not using any Bash extensions now.  Also improved the "send" option.  So give it a try and post back if there are any troubles.  After I install a Edgy chroot and test it there, I'll update the version in the wiki.

---

### Post by jpkotta on 2006-10-04
> **robinl said:**
> Yep that fixed it. Thanks alot.

PS: why does it work in Dapper but not Edgy? Aren't sh and bash almost the same in syntax?

Bash has a lot of extensions to sh.  Any sh script will work in bash, but not necessarily the other way.  I had assumed that by calling bash as /bin/sh, it would act like sh, but apparently, I was wrong.

I would appreciate Edgy users testing this (attachment in previous post).  If a bunch of you test it, and PM me to say if it works, I'll update the wiki version immediately.

---

### Post by robinl on 2006-10-05
The new version still requires bash... If it's ran as it is it will output "fail" for everything (start, stop, restart etc.). Once changed to bash it runs fine.

---

### Post by jpkotta on 2006-10-05
Thanks for the feedback.  I'll have to wait to do a real fix until next week then.

---

### Post by sleepy127 on 2006-10-09
Thanks for the reply, I have been reading but I still cannot figure out why it is not installing. Here is what I get;
sleepy127@ubuntu:~$ sudo ./folding_install.sh install
sudo: ./folding_install.sh: command not found
sleepy127@ubuntu:~$

Ok, I got that to work, I changed sudo ./folding_install.sh install to 
sudo ./fah_install/folding_install.sh install

Now I get this;
I couldn't find the client executable.  If you have it already, please copy it to /opt/foldingathome/config/.
Do you want me to download it for you?

1) yes
2) no
Please pick a number: yes
Please pick a number: 1
--13:58:37--  [http://www.stanford.edu/group/pandegroup/release/FAH502-Linux.exe](http://www.stanford.edu/group/pandegroup/release/FAH502-Linux.exe)
           => `FAH502-Linux.exe'
Resolving [www.stanford.edu](www.stanford.edu)... 171.67.22.26
Connecting to [www.stanford.edu](www.stanford.edu)[171.67.22.26]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 249,236 [application/x-msdos-program]

100%[====================================>] 249,236      187.68K/s

13:58:39 (187.12 KB/s) - `FAH502-Linux.exe' saved [249,236/249,236]


Found 1 cpus.  I will create one client for every cpu.


Creating foldingathome user.


Press 'q' to exit the license viewer.
cp: cannot stat `reconfigure.sh': No such file or directory
./fah_install/folding_install.sh: line 74: /opt/foldingathome/reconfigure.sh: No such file or directory
sed: can't read /home/sleepy127/foldingathome: No such file or directory

Adding startup script to /etc/init.d
/bin/cp: cannot stat `/home/sleepy127/foldingathome': No such file or directory
Could not copy startup script to /etc/init.d
sleepy127@ubuntu:~$

---

### Post by jpkotta on 2006-10-09
The installer assumes that you're in the same directory as all of the scripts.  In other words, you have to do ```
sudo ./folding_install install
```.

```
cd fah_install
sudo ./folding_install install
```

You can see what is in the current directory with ```
ls
``` and change directories with ```
cd
```

---

### Post by robinl on 2006-10-13
Any word on the Edgy-compatitable version? Currently it doesn't auto start on boot and I have to manually start it.

---

### Post by jpkotta on 2006-10-13
> **robinl said:**
> Any word on the Edgy-compatitable version? Currently it doesn't auto start on boot and I have to manually start it.

I downloaded the edgy beta live cd and booted it in VMWare.  I installed folding at home.  For some reason, it will not stop properly, although it starts ok (obviously, I have only tried doing things manually).  I'm really confused as to why it is not stopping, it seems to be a problem with start-stop-daemon, not the script itself, but other init scripts use start-stop-daemon just fine.  I haven't found any bug reports of a broken init script in edgy yet.  I'm going to have time this weekend to work on it, so hopefully I'll be able to get *something* working.

---

### Post by jpkotta on 2006-10-14
Beta for edgy is up on wiki: [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

You can test it directly from the untarred directory:
```
cd
tar zxvf fah_install-...tar.gz
cd fah_install
sudo ./foldingathome stop
```

The problems I was having in testing seem to be related to the fact that I was using the Live CD.  I don't have the space to do an Edgy installation, so I'm hoping for some good beta testers.

---

### Post by robinl on 2006-10-16
Currently the script works fine but doesn't auto start from /etc/init.d/ on boot.

---

### Post by jpkotta on 2006-10-17
> **robinl said:**
> Currently the script works fine but doesn't auto start from /etc/init.d/ on boot.

OK, I freed up some space and installed Edgy into a VM.  (The graphical installer from the Live CD is very slick, BTW.)  I installed F@H and it started and stopped fine, as you said.  Then I rebooted and it started at boot.  Edgy has a new init system, but the interface to it should be the same, and since it worked for me, it seems like it is (I followed the Debian spec for init scripts when I wrote the installer and init script).  

Try updating the client:

```
sudo ./install.sh update
```

---

### Post by eldaria on 2006-10-20
I have have a server running Dapper 64bit version installed on an Intel 64bit Dual core CPU system with 4 Gig of memory, and I'm not able to run this script, it installed fine on my Desktop PC that is a Standard Pentium 4 CPU running Kubuntu 6.06.

The server would be an ideal candidate for running Folding@home for TeamUbuntu, since it is on 24/7 and has a load average of 0.09.
So please help me get this running. 

The script fails on running the FAH502-Linux.exe already when telling to push Q to exit the licence.

I get following error message:
#######################################
Press 'q' to exit the license viewer.
folding_install.sh: line 70: /opt/foldingathome/config/FAH502-Linux.exe: No such file or directory
(END)
#######################################

It also only detects 1 CPU.

I checked and the file FAH502-Linux is in the fodler where it is looking for it, and if I try to manually run it:

#######################################
-bash: ./FAH502-Linux.exe: No such file or directory
#######################################

I suspect that it is related to the fact that I'm running 64bit version, but if this is the case, is there a way to work around this?

Regards.
Brian

---

### Post by eldaria on 2006-10-20
ok, never mind, I found I just needed to install the ia32-libs package, and it worked.

However the scripts fails to detect the difference between having 2 CPU's because of dual core and having Hyperthreading.

So it only detects 1 CPU in my system even though there are actually 2 CPU cores.

---

### Post by jpkotta on 2006-10-20
> **eldaria said:**
> ok, never mind, I found I just needed to install the ia32-libs package, and it worked.

However the scripts fails to detect the difference between having 2 CPU's because of dual core and having Hyperthreading.

So it only detects 1 CPU in my system even though there are actually 2 CPU cores.

So there are two cores, but they are each hyperthreaded?  There are 4 logical processors, and 2 physical ones?  Please post your /proc/cpuinfo file.

---

### Post by eldaria on 2006-10-21
It only shows 2 CPU's.
Here is the output of cpuinfo:
#######################################
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :              Intel(R) Pentium(R) D  CPU 2.66GHz
stepping        : 7
cpu MHz         : 2676.325
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips        : 5361.41
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :              Intel(R) Pentium(R) D  CPU 2.66GHz
stepping        : 7
cpu MHz         : 2676.325
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips        : 5352.77
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:
#######################################################

---

### Post by jpkotta on 2006-10-21
Ahh, I see now.  It looks like it has a processor in /proc/cpuinfo for each logical cpu, and each logical has 2 cores.  I think this is completely braindead, but hopefully there is a good reason for it...

Check the wiki tomorrow for an update.

---

### Post by NZ-Wanderer on 2006-10-22
Yep, I'm getting exactly the same errors when I do the sudo /etc/init.d/foldingathome start
 command, it's getting very frustrating to the point I'm wondering if it is worth the hassle anymore..

I saw the post where it was said:

```
That's weird. Try changing the top line to
#!/bin/bash
```

However, I have no idea as to what "top line" is being referred to, so I just typed #!/bin/bash into terminal, which didn't seem to do anything.

> **robinl said:**
> Does the script break on Edgy or is it only me? Since I dist-upgraded to Edgy I've been getting errors like these: 
```
$ sudo /etc/init.d/foldingathome start
/etc/init.d/foldingathome: 23: [[: not found
/etc/init.d/foldingathome: 33: [[: not found
/etc/init.d/foldingathome: 147: [[: not found
/etc/init.d/foldingathome: 147: arith: syntax error: "++num"
```

---

### Post by jpkotta on 2006-10-23
> **NZ-Wanderer said:**
> Yep, I'm getting exactly the same errors when I do the sudo /etc/init.d/foldingathome start
 command, it's getting very frustrating to the point I'm wondering if it is worth the hassle anymore..

I saw the post where it was said:

```
That's weird. Try changing the top line to
#!/bin/bash
```

However, I have no idea as to what "top line" is being referred to, so I just typed #!/bin/bash into terminal, which didn't seem to do anything.

Top line refers to the first line of the foldingathome script.  Any line that looks like ```
#!/path/to/program
``` will look for a program at that location and give the rest of the file to the program.  In this case, our program is /bin/sh, which was acutally bash in dapper and earlier, but is dash in edgy and later.  The errors you're getting are because the script is a bash script, but it is being run with dash (which behaves exactly like sh, whereas bash has numerous extensions).  I have rewritten the script to work with dash, but you are still trying to run the old one.  Get [this]("https://help.ubuntu.com/community/FoldingAtHome?action=AttachFile&do=get&target=fah_install-20061021.tar.gz") file, untar it, run ```
sudo ./install.sh update
``` and it should replace your current init script with a working one.

Why did I not just use bash in the first place?  Because init scripts are not supposed to use it, they are supposed to work with sh.

It is worth the hassle.  Your reports mean that I can fix the problems and others don't have to deal with them.

---

### Post by glotz on 2006-10-24
Hell Love!

EDIT: DISREGARD FOLLOWING, I WAS WRONG!
Proof: [http://forum.folding-community.org/ftopic16583.html](http://forum.folding-community.org/ftopic16583.html)

[i]This link (from the F@H wiki article) [http://www.hackaday.com/2005/09/13/how-to-folding-home-competitively/](http://www.hackaday.com/2005/09/13/how-to-folding-home-competitively/)
sez that the windoze client is faster than the Linux client and suggests running it using wine  for speed increase. What do you guys think about that? Should the wiki page contains instructions for that kind of setup? If the benefits are considerable, I think we all should start running it on wine and the instructions should be included. Since windows is so much more popular a platform, I'm sure the F@H dudes *did* spend more time with the windoze client and thus the claim sounds feasible to me...[/i]
:rolleyes:

---

### Post by robinl on 2006-10-24
> **jpkotta said:**
> OK, I freed up some space and installed Edgy into a VM.  (The graphical installer from the Live CD is very slick, BTW.)  I installed F@H and it started and stopped fine, as you said.  Then I rebooted and it started at boot.  Edgy has a new init system, but the interface to it should be the same, and since it worked for me, it seems like it is (I followed the Debian spec for init scripts when I wrote the installer and init script).  

Try updating the client:

```
sudo ./install.sh update
```

Hmmm I've done that and it still doesn't auto starts... I can't put it in sessions because I installed it system wide and can't be stuffed to type my password twice during boot. Is there any way I can fix it?

---

### Post by jpkotta on 2006-10-25
> **glotz said:**
> Hell Love!

This link (from the F@H wiki article) [http://www.hackaday.com/2005/09/13/how-to-folding-home-competitively/](http://www.hackaday.com/2005/09/13/how-to-folding-home-competitively/)
sez that the windoze client is faster than the Linux client and suggests running it using wine  for speed increase. What do you guys think about that? Should the wiki page contains instructions for that kind of setup? If the benefits are considerable, I think we all should start running it on wine and the instructions should be included. Since windows is so much more popular a platform, I'm sure the F@H dudes *did* spend more time with the windoze client and thus the claim sounds feasible to me...

It's plausible, but I'd like to see some numbers.  Try it with wine for a week and then with Linux for a week and see the difference.  Ideally, each would work on the same WUs, but I don't think that's possible (you can't transfer WUs AFAIK and you certainly can't request them).

---

### Post by jpkotta on 2006-10-25
> **robinl said:**
> Hmmm I've done that and it still doesn't auto starts... I can't put it in sessions because I installed it system wide and can't be stuffed to type my password twice during boot. Is there any way I can fix it?

Yeah, you shouldn't have to add it to any of you're login stuff.  That was the whole reason I made this.  Well, let's see what we can do:

Make sure there is a link to /etc/init.d/foldingathome in /etc/rc2.d:
```
[jpkotta@euler ~](0)$ ls -l /etc/rc2.d/ | grep fold
lrwxrwxrwx 1 root root 23 2006-02-25 14:37 S99foldingathome -> ../init.d/foldingathome*
```

Make sure /etc/init.d/foldingathome is executable:
```
[jpkotta@euler ~](0)$ ls -l /etc/init.d/foldingathome 
-rwx------ 1 root root 4856 2006-10-21 16:31 /etc/init.d/foldingathome*
```

If that checks out, then change the "--quiet" in the start-stop-daemon parts of /etc/init.d/foldingathome to "--verbose".  Then reboot and look for error messages on tty8 (ctrl-alt-F8).  

Hint: you can copy and paste from the console by installing gpm (mouse driver for console) and selecting the text.  Then you can log in on tty1 and start nano or another editor and paste with middle click.

---

### Post by glotz on 2006-10-25
nothing here, move along...

---

### Post by robinl on 2006-10-26
> **jpkotta said:**
> Yeah, you shouldn't have to add it to any of you're login stuff.  That was the whole reason I made this.  Well, let's see what we can do:

Make sure there is a link to /etc/init.d/foldingathome in /etc/rc2.d:
```
[jpkotta@euler ~](0)$ ls -l /etc/rc2.d/ | grep fold
lrwxrwxrwx 1 root root 23 2006-02-25 14:37 S99foldingathome -> ../init.d/foldingathome*
```Make sure /etc/init.d/foldingathome is executable:
```
[jpkotta@euler ~](0)$ ls -l /etc/init.d/foldingathome 
-rwx------ 1 root root 4856 2006-10-21 16:31 /etc/init.d/foldingathome*
```If that checks out, then change the "--quiet" in the start-stop-daemon parts of /etc/init.d/foldingathome to "--verbose".  Then reboot and look for error messages on tty8 (ctrl-alt-F8).  

Hint: you can copy and paste from the console by installing gpm (mouse driver for console) and selecting the text.  Then you can log in on tty1 and start nano or another editor and paste with middle click.

I've tried those two commands and the outputs seems normal.
```
robin@robin-desktop:~$ ls -l /etc/rc2.d/ | grep fold
lrwxrwxrwx 1 root root  23 2006-10-06 23:56 K01foldingathome -> ../init.d/foldingathome
robin@robin-desktop:~$ ls -l /etc/init.d/foldingathome 
-rwx------ 1 robin robin 4859 2006-10-26 19:47 /etc/init.d/foldingathome

```
I've also changed the start daemon to --verbose but nothing showed up in tty8...

---

### Post by jpkotta on 2006-10-26
> **robinl said:**
> I've tried those two commands and the outputs seems normal.
```
robin@robin-desktop:~$ ls -l /etc/rc2.d/ | grep fold
lrwxrwxrwx 1 root root  23 2006-10-06 23:56 K01foldingathome -> ../init.d/foldingathome
robin@robin-desktop:~$ ls -l /etc/init.d/foldingathome 
-rwx------ 1 robin robin 4859 2006-10-26 19:47 /etc/init.d/foldingathome

```
I've also changed the start daemon to --verbose but nothing showed up in tty8...

```
sudo mv /etc/rc2.d/K01foldingathome /etc/rc2.d/S99foldingathome
```

---

### Post by robinl on 2006-10-27
> **jpkotta said:**
> ```
sudo mv /etc/rc2.d/K01foldingathome /etc/rc2.d/S99foldingathome
```

That did it. Thanks.

---

### Post by citizenkahn on 2006-10-29
Really nice installer.  I ran into one problem with the init.d script on edgy-eft (6.10).  The script runs as bourne shell, but has some requirements on bash.  The incrementor on the variable (++foo) and some of the double [[ on the test/if statements.  When I changed the script to use bash, it all worked quite well.


--
Peter Kahn (citizenkahn@gmail.com)

---

### Post by jpkotta on 2006-10-29
> **citizenkahn said:**
> Really nice installer.  I ran into one problem with the init.d script on edgy-eft (6.10).  The script runs as bourne shell, but has some requirements on bash.  The incrementor on the variable (++foo) and some of the double [[ on the test/if statements.  When I changed the script to use bash, it all worked quite well.


--
Peter Kahn (citizenkahn@gmail.com)

Thanks.  I'm well aware of the Bash-isms in the old init script.  Visit the [wiki]("https://help.ubuntu.com/community/FoldingAtHome") for an updated version.

---

### Post by glotz on 2006-10-29
Looks like [**TeamUbuntu** is overtaking **Microsoft**](http://folding.extremeoverclocking.com/team_overtake.php?s=&t=45104) in about a month or so! No wonder [img]http://img116.imageshack.us/img116/3082/billgatesrecommendsubuntuft4yr6.jpg[/img]

---

### Post by DarkDancer on 2006-11-01
I can't get this to install in edgy.

I tried tar zxvf fah_install-20061021.tar.gz.tar and get

> fah_install/
fah_install/foldingathome
tar: fah_install/foldingathome: Cannot open: Permission denied
tar: Skipping to next header
fah_install/install.sh
tar: fah_install/install.sh: Cannot open: Permission denied
tar: Skipping to next header
fah_install/README
tar: fah_install/README: Cannot open: Permission denied
tar: Skipping to next header
fah_install/system.options
tar: fah_install/system.options: Cannot open: Permission denied
tar: Skipping to next header
fah_install/reconfigure.sh
tar: fah_install/reconfigure.sh: Cannot open: Permission denied
tar: Skipping to next header
fah_install/client.options
tar: fah_install/client.options: Cannot open: Permission denied
tar: Skipping to next header
tar: fah_install: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors
 


so then I tried the same command with sudo and get

> fah_install/
fah_install/foldingathome
tar: fah_install/foldingathome: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
fah_install/install.sh
tar: fah_install/install.sh: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
fah_install/README
tar: fah_install/README: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
fah_install/system.options
tar: fah_install/system.options: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
fah_install/reconfigure.sh
tar: fah_install/reconfigure.sh: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
fah_install/client.options
tar: fah_install/client.options: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: fah_install: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: Error exit delayed from previous errors


Any clues?

---

### Post by jpkotta on 2006-11-01
I have no idea.  I just tested it myself by downloading with another user on my machine and extracting.  It went fine and the files were created as the other user, the default behavior for tar.  

Do you already have that directory?  Be very careful with this command!
```
rm -rf ./fah_install
```

Try using the --no-same-owner (and maybe --no-same-permissions) options to tar.

```
tar --no-same-owner zxvf fah_install-....tar.gz
```

---

### Post by DarkDancer on 2006-11-02
Thanks for responding jpkotta, when I tried tar --no-same-owner zxvf fah_install-20061021.tar.gz.tar I got:

> tar: You must specify one of the `-Acdtrux' options
Try `tar --help' or `tar --usage' for more information.


---

### Post by jpkotta on 2006-11-02
Oh, yeah, I don't think you can combine options after giving a long one.  This is what sucks about Unix.  There are a number of GUI archivers that may work for you too (I am not familiar with them); if you double click the tarball in Nautilus or another filemanager, it should open it up.

```
tar --no-same-owner -z -x -v -f fah...
```

---

### Post by DarkDancer on 2006-11-02
ok, when I double click on the tar in nautilius, the unarchiver thing comes up, when I have it try to extract, it comes back with these errors.

> tar: fah_install/foldingathome: Cannot utime: Operation not permitted
tar: fah_install/install.sh: Cannot utime: Operation not permitted
tar: fah_install/README: Cannot utime: Operation not permitted
tar: fah_install/system.options: Cannot utime: Operation not permitted
tar: fah_install/reconfigure.sh: Cannot utime: Operation not permitted
tar: fah_install/client.options: Cannot utime: Operation not permitted
tar: fah_install: Cannot utime: Operation not permitted
tar: fah_install: Cannot change mode to rwx------: Operation not permitted
tar: Error exit delayed from previous errors


---

### Post by jpkotta on 2006-11-02
Yeah, something is borked with tar.  Here is a zip, maybe that will work.

---

### Post by DarkDancer on 2006-11-02
Thanks, just got home from work, trying it now... ;)

---

### Post by DarkDancer on 2006-11-02
Ok, I got it all going right up to the point where it shows me the eula, I can't figure out how to accept it, it won't take any keys....

---

### Post by jpkotta on 2006-11-02
Press 'q'.  

What is up with your machine?  tar and less both don't work right?  Man, I don't think I'm updating to edgy until I have some time to kill.

---

### Post by DarkDancer on 2006-11-02
Hmmm, got past the eula (this time I saw the thing about hitting q (for a split second, then it was gone) it asked me if I wanted to set up a cron. I said yes. I tried using the command it gave to start, but nothing happened, so I rebooted, but the cron didn't start it either (no cpu usage to speak of and it's not listed in the processes.)

I don't know.....

---

### Post by DarkDancer on 2006-11-03
Oh, it is running. Thanks jpkotta!

---

### Post by jpkotta on 2006-11-03
> **DarkDancer said:**
> Hmmm, got past the eula (this time I saw the thing about hitting q (for a split second, then it was gone) it asked me if I wanted to set up a cron. I said yes. I tried using the command it gave to start, but nothing happened, so I rebooted, but the cron didn't start it either (no cpu usage to speak of and it's not listed in the processes.)

I don't know.....

Read the README.

---

### Post by DarkDancer on 2006-11-04
Hehe, read the readme before posting... ;)

Doesn't matter, it's off and running now.

---

### Post by Rhapsody on 2006-11-16
I've had Folding@Home on this PC for a while now, but it doesn't seem to have even started working. The log files are filled with the following:

> [02:59:07] + Attempting to get work packet
[02:59:07] - Connecting to assignment server
[02:59:08] - Successful: assigned to (x.x.x.x).
[02:59:08] + News From Folding@Home: Welcome to Folding@Home
[02:59:08] Loaded queue successfully.
[02:59:09] + Could not connect to Work Server
[02:59:09] - Error: Attempt #1  to get work failed, and no other work to do.
             Waiting before retry.

I'm not really sure what's going wrong here. My internet connection is fully working, but Folding@Home is never able to get any work. If I can fix this, I should be able to contribute, but I've no idea what would be causing this.

---

### Post by jpkotta on 2006-11-16
How long has it been since you got work?  F@H appears to be able to connect to the servers (assignment server), it just seems that there is no work to do.  See this post: [http://ubuntuforums.org/showthread.php?p=1606734#post1606734](http://ubuntuforums.org/showthread.php?p=1606734#post1606734) and the ones that follow.

---

### Post by Rhapsody on 2006-11-16
> **jpkotta said:**
> How long has it been since you got work?  F@H appears to be able to connect to the servers (assignment server), it just seems that there is no work to do.  See this post: [http://ubuntuforums.org/showthread.php?p=1606734#post1606734](http://ubuntuforums.org/showthread.php?p=1606734#post1606734) and the ones that follow.

I've had it for months now and, as far as I can tell, it's done absolutely no work at all in that time. I've changed "Request work units without deadlines" from 'yes' to 'no-prefs' in the hope that it will get my PC more work. It's on every day anyway (only shut down at night) so I can probably make deadlines without many problems.

---

### Post by glotz on 2006-11-17
Looks like they're out of deadlineless work units. [http://forum.folding-community.org/portal.php?topic_id=16235](http://forum.folding-community.org/portal.php?topic_id=16235)

Does the installation script (instead of the .exe) ask the configuration question about deadlines? If yes, could/should it be removed for now?

---

### Post by jpkotta on 2006-11-17
The installer I wrote simply runs the client with the -configonly option during installation.  I can't change what questions it asks, and I'm not going to have it not run -configonly, because that's about the only way to set user name and team number.  The default is no-pref anyway.

---

### Post by Rhapsody on 2006-11-17
Well now that I've removed the requirement for deadlines, my PC has got a work unit and is processing it. If I knew how lax the deadlines were going to be, I would've done this ages ago. This work unit has to be completed by February 25th, but my PC has done 5% of it in just 7 hours!

It should also be noted that I'm looking to get myself a Core 2 Extreme sometime next year (likely a quad-core one), which will blitz this old work horse.

---

### Post by Raptormn on 2006-11-26
this is what happens when i try to start mine does anyone know whats wrong?

raptormn@raptormn-desktop:~$ opt/foldingathome/foldingathome start              opt/foldingathome/foldingathome: 23: [[: not found
opt/foldingathome/foldingathome: 33: [[: not found
opt/foldingathome/foldingathome: 147: [[: not found
opt/foldingathome/foldingathome: 147: arith: syntax error: "++num"

---

### Post by jpkotta on 2006-11-27
> **Raptormn said:**
> this is what happens when i try to start mine does anyone know whats wrong?

raptormn@raptormn-desktop:~$ opt/foldingathome/foldingathome start              opt/foldingathome/foldingathome: 23: [[: not found
opt/foldingathome/foldingathome: 33: [[: not found
opt/foldingathome/foldingathome: 147: [[: not found
opt/foldingathome/foldingathome: 147: arith: syntax error: "++num"

This is a known issue with old versions of the script and Edgy.  It is fixed in the latest version from the wiki.  

[https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

---

### Post by AndyW on 2006-12-11
I get this error while installing
```

[03:44:55] -configonly flag given, so exiting.
Terminated

```

---

### Post by jpkotta on 2006-12-11
> **AndyW said:**
> I get this error while installing
```

[03:44:55] -configonly flag given, so exiting.
Terminated

```

That is not an error, it is a message.  It is normal.

---

### Post by aprita on 2006-12-12
So I figured I'll give this software a shot and installed it using the beta version (fah_install-20061021.tar.gz, have edgy installed) and seems to have worked fine except for one thing. It says it could only find 1 cpu even though I have two. Anyone know how I could change that? My system is currently only running at 50% and would like to make use of both my processors. thanks a bunch.

here my output for the /proc/cpuinfo

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 6
cpu MHz         : 1600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3726.97

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 6
cpu MHz         : 1867.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3724.06

---

### Post by jpkotta on 2006-12-12
It seems like there is no good way to determine if you have physical processors (dual core) or logical processors (hyperthreaded).  Read the wiki for why the difference is important.  I will update the installer this weekend so that you can choose how many.

---

### Post by AndyW on 2006-12-13
It wont work though
```
[01:08:32] -configonly flag given, so exiting.
Terminated
/opt/foldingathome/reconfigure.sh: 33: [[: not found

Adding startup script to /etc/init.d
`/home/andy/fah_install/foldingathome' -> `/etc/init.d/foldingathome'
 Adding system startup for /etc/init.d/foldingathome ...
   /etc/rc0.d/K01foldingathome -> ../init.d/foldingathome
   /etc/rc1.d/K01foldingathome -> ../init.d/foldingathome
   /etc/rc6.d/K01foldingathome -> ../init.d/foldingathome
   /etc/rc2.d/S99foldingathome -> ../init.d/foldingathome
   /etc/rc3.d/S99foldingathome -> ../init.d/foldingathome
   /etc/rc4.d/S99foldingathome -> ../init.d/foldingathome
   /etc/rc5.d/S99foldingathome -> ../init.d/foldingathome

To start folding right now, run /etc/init.d/foldingathome as root.

Installing global options.

cp: overwrite `/etc/default/foldingathome'? 
`/home/andy/fah_install/client.options' -> `/opt/foldingathome/config/client1.options'
`/home/andy/fah_install/README' -> `/opt/foldingathome/README'

To start folding right now, run '/opt/foldingathome/foldingathome start'

andy@andy:~/fah_install$ /opt/foldingathome/foldingathome start
bash: /opt/foldingathome/foldingathome: No such file or directory

```
There is no foldingathome file in that directory

when I try to uninstall it gives me this:
```
userdel: error removing directory /opt/foldingathome
groupdel: group foldingathome does not exist

```
Maybe I did something wrong?

---

### Post by jpkotta on 2006-12-13
> **AndyW said:**
> It wont work though
```
[01:08:32] -configonly flag given, so exiting.
Terminated
/opt/foldingathome/reconfigure.sh: 33: [[: not found

Adding startup script to /etc/init.d
`/home/andy/fah_install/foldingathome' -> `/etc/init.d/foldingathome'
 Adding system startup for /etc/init.d/foldingathome ...
   /etc/rc0.d/K01foldingathome -> ../init.d/foldingathome
   /etc/rc1.d/K01foldingathome -> ../init.d/foldingathome
   /etc/rc6.d/K01foldingathome -> ../init.d/foldingathome
   /etc/rc2.d/S99foldingathome -> ../init.d/foldingathome
   /etc/rc3.d/S99foldingathome -> ../init.d/foldingathome
   /etc/rc4.d/S99foldingathome -> ../init.d/foldingathome
   /etc/rc5.d/S99foldingathome -> ../init.d/foldingathome

To start folding right now, run /etc/init.d/foldingathome as root.

Installing global options.

cp: overwrite `/etc/default/foldingathome'? 
`/home/andy/fah_install/client.options' -> `/opt/foldingathome/config/client1.options'
`/home/andy/fah_install/README' -> `/opt/foldingathome/README'

To start folding right now, run '/opt/foldingathome/foldingathome start'

andy@andy:~/fah_install$ /opt/foldingathome/foldingathome start
bash: /opt/foldingathome/foldingathome: No such file or directory

```
There is no foldingathome file in that directory

when I try to uninstall it gives me this:
```
userdel: error removing directory /opt/foldingathome
groupdel: group foldingathome does not exist

```
Maybe I did something wrong?

Yes, that is an error (however "-configonly flag given, so exiting.
Terminated" is normal).  Someone else notified me of the error in reconfigure.  There will be fixes this weekend.  It might work if you change the first line of reconfigure to "#!/bin/bash".

---

### Post by jpkotta on 2006-12-19
New installer scripts available.  I think I fixed the bugs.  I have an Edgy VM that I tested in, and it works perfectly there.  If you have already installed, then you should only have to do an update.

[https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

---

### Post by AndyW on 2006-12-20
thanks for the update, Im folding for teamubuntu now!

---

### Post by TwistedTripper on 2006-12-30
Hi there

Not sure if this is the right thread but I setup folding@home a few months ago using this guide and everything is working nicely, Thanks for the great guide :) however I am planning on upgrading my computer with a new hard drive and would like to know how I can backup my folding@home files.

Which files do I need to copy so I can reinstate them later? I can't seem to just copy and paste the folding@home folder so is there a command I can use to make a backup of the files? Sorry for the stupid questions but any suggestions/advice will be much appreciated.

Cheers

---

### Post by wames on 2006-12-31
There is a problem with how the install script counts my Turion64 X2 CPUs.  It counts it as just one CPU when it is really two.  This stems from the check for the "ht" flag in /proc/cpuinfo.  This flag does appear in AMD X2 chips and does not indicate HyperThreading capability.  To quote some info I found on the net

"...It denotes that fact that the processor is capable of exposing more than one logical CPU..."

Now I don't know if this is really true but when checking /proc/cpuinfo I do see the ht flag and my system does not have HT.  There needs to be a better way to check for HT now that modern AMD dual core CPUs contain this flag.  I fixed (dirty hacked) this problem by just commenting out the last two lines of the num_cpu check which is safe for me as I know I have two CPUs and no HT.

---

### Post by jpkotta on 2006-12-31
> **TwistedTripper said:**
> Hi there

Not sure if this is the right thread but I setup folding@home a few months ago using this guide and everything is working nicely, Thanks for the great guide :) however I am planning on upgrading my computer with a new hard drive and would like to know how I can backup my folding@home files.

Which files do I need to copy so I can reinstate them later? I can't seem to just copy and paste the folding@home folder so is there a command I can use to make a backup of the files? Sorry for the stupid questions but any suggestions/advice will be much appreciated.

Cheers

If you used fah_install, you do this:
```
sudo tar zcvf fahbck.tar.gz /opt/foldingathome /etc/default/foldingathome
```
That should save all of your work and settings.

To restore, ```
cd / ; sudo tar zxvf fahbck.tar.gz
```
After restoring, use the fah_install script with the update option.  This will not overwrite your work or settings, and will set up everything to start at boot time again.

---

### Post by jpkotta on 2006-12-31
> **wames said:**
> There is a problem with how the install script counts my Turion64 X2 CPUs.  It counts it as just one CPU when it is really two.  This stems from the check for the "ht" flag in /proc/cpuinfo.  This flag does appear in AMD X2 chips and does not indicate HyperThreading capability.  To quote some info I found on the net

"...It denotes that fact that the processor is capable of exposing more than one logical CPU..."

Now I don't know if this is really true but when checking /proc/cpuinfo I do see the ht flag and my system does not have HT.  There needs to be a better way to check for HT now that modern AMD dual core CPUs contain this flag.  I fixed (dirty hacked) this problem by just commenting out the last two lines of the num_cpu check which is safe for me as I know I have two CPUs and no HT.

I can't find a good way to get CPU detection to work right.  The latest installer has some improvements and the ability to manually set the number of CPUs.

---

### Post by ruudiculus on 2007-01-01
Hi all,

I wrote a simple Folding@Gnome applet to graphically monitor your folding progress and set preferences in. For those interested, you can find more info on my [website]("http://www.ruudbeukema.nl").

Please report any strange behaviour! The applet works fine here, but is still in "testing" until it works fine for more than one person of course!

---

### Post by smbm on 2007-01-06
Does anyone know of any way to set F@H up so that it still runs as root but have the work unit stored in a folder in /home? 

Also is it possible to tell F@H to finish the work unit it is on, send it and then exit?

Thanks in advance

---

### Post by jpkotta on 2007-01-06
> **smbm said:**
> Does anyone know of any way to set F@H up so that it still runs as root but have the work unit stored in a folder in /home? 

Also is it possible to tell F@H to finish the work unit it is on, send it and then exit?

Thanks in advance

Why do you want it to run as root?  It really shouldn't.  Try hacking my installer, it should only be necessary to change the "fah_dir" variable in a few places to make it use the folder of your choice.  As for running as root, I went through a lot of trouble to make sure it *doesn't* need to run as root.  You would need to hack the foldingathome init script and the reconfigure script.  The really quick and dirty way is to use su (read the man page).

You can give it a command line option to finish the current unit and send and quit: '-oneunit'.  If using my installer, you would this option to the /etc/default/foldingathome file and restart.

---

### Post by smbm on 2007-01-06
Thanks for the reply

Perhaps I don't mean as root. I installed it using the script in the wiki. It installed to /opt but I would like to wipe my / partition. /home is on a separate partition so if I could somehow copy it there that would mean I could keep my current work unit. I'll have a look at the scripts and stuff and see how I get on.

---

### Post by jpkotta on 2007-01-07
> **smbm said:**
> Thanks for the reply

Perhaps I don't mean as root. I installed it using the script in the wiki. It installed to /opt but I would like to wipe my / partition. /home is on a separate partition so if I could somehow copy it there that would mean I could keep my current work unit. I'll have a look at the scripts and stuff and see how I get on.

That's easy.  It's a good idea to shutdown the client before backing up.

[http://ubuntuforums.org/showpost.php?p=1952745&postcount=197](http://ubuntuforums.org/showpost.php?p=1952745&postcount=197)

Edit:  
Added FAQ to wiki page: [https://help.ubuntu.com/community/FoldingAtHome#head-774c7065f707a8798b15820b9ff824f3e1fa34bd](https://help.ubuntu.com/community/FoldingAtHome#head-774c7065f707a8798b15820b9ff824f3e1fa34bd)

---

### Post by nanotube on 2007-02-07
hey fellow folders!
i recently installed the fah client on my laptop, along with some nice cpulimiting.
i posted a pretty thorough howto about it on my ubuntu chronicles page here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Folding.40Home_.5BFAH.5D_on_a_Laptop](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Folding.40Home_.5BFAH.5D_on_a_Laptop)
in case anyone is interested. :)

i have it running at 50% cpu load - that keeps the cpu nice and cool (otherwise, fan keeps revving up if i just let it run at 100% idle load), so that should prevent any premature death due to folding. ;)

hope this comes in handy for some of you.

---

### Post by Bragador on 2007-02-07
Hey thanks it WAS useful. I kept trying to install the program for the past couple of hours with scripts that didn't seem to be up to date and when I read your description saying "it simply boils down to" I was finally able to make it run.

So thank you !

Next time I'll have to make it run in the background. But enough for today :)

---

### Post by jpkotta on 2007-02-07
Bragador:

Are those scripts the ones from the wiki?  Can you describe what went wrong?

---

### Post by Bragador on 2007-02-10
> **jpkotta said:**
> Bragador:

Are those scripts the ones from the wiki?  Can you describe what went wrong?

What I meant was that I tried to use both fah_install and finstall to install folding@home and yes, both didn't work.

The ubuntu one went wrong when I had to enter the install command:
```
sudo ./folding_install.sh install
```

The command didn't exist apparently. I managed to install it by changing the commands to something else so the wiki wasn't up to date it seems. After some tinkering I made it but I wasn't sure how the files were installed so I kind of panicked and managed to uninstall everything. So yeah in the end I think I did it but since I didn't understand what the script was doing I didn't like it. 

As for the finstall I received a 404 not found when I tried to get it.

What I finally did was to download f@h manually and start it from its own folder with the terminal. I wish I could make it run in the background though but it's not too much of a problem for now. At least I know where all the files are.

---

### Post by jpkotta on 2007-02-10
Bragador:

You are absolutely right that the wiki was out of date.  Thanks for pointing that out.  

The README mentions which files and directories are created during installation.

---

### Post by Bragador on 2007-02-11
> **jpkotta said:**
> Bragador:

You are absolutely right that the wiki was out of date.  Thanks for pointing that out.  

The README mentions which files and directories are created during installation.

Well I'm glad I helped the community then :D

Also you are right about the README. I guess I was expecting to find my folder organized like in windows and that's why I ended up not using the script in the end.

I've just found out you are the coder for the script so kudos to you !

---

### Post by xyrcncp on 2007-02-22
Hi, I'm a total noob to Linux, but I managed to follow the instructions on installing, but I can't get it to run, I get this in Terminal after entering   sudo /etc/init.d/foldingathome start  :

/etc/init.d/foldingathome: 23: [[: not found
/etc/init.d/foldingathome: 33: [[: not found
/etc/init.d/foldingathome: 147: [[: not found
/etc/init.d/foldingathome: 147: arith: syntax error: "++num"


?

I really want to get this running as I have this computer doing nothing and rather put it to good cause.

Thanks!

---

### Post by glotz on 2007-02-22
What version of Ubuntu you're on? (system > about Ubuntu)

I don't know what the problem is but somebody else will. Welcome to Ubuntu and welcome to the Ubuntu folding team!

---

### Post by xyrcncp on 2007-02-22
Thanks for the welcome.  I'm on Ubuntu 6.10 Edgy Eft

As I'm reading the instructions again, they state that the script resides in 

/etc/init.d/foldingathome start

but when I actually navigate to /etc/ there is no  init.d  at all...:confused:

---

### Post by jpkotta on 2007-02-22
> **xyrcncp said:**
> Hi, I'm a total noob to Linux, but I managed to follow the instructions on installing, but I can't get it to run, I get this in Terminal after entering   sudo /etc/init.d/foldingathome start  :

/etc/init.d/foldingathome: 23: [[: not found
/etc/init.d/foldingathome: 33: [[: not found
/etc/init.d/foldingathome: 147: [[: not found
/etc/init.d/foldingathome: 147: arith: syntax error: "++num"


This is a bug that was caused by the switch from bash to dash in Edgy.  The newest scripts in the wiki have this fixed.  Read the wiki for quick instructions for installing/updating the scripts.  Link: [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

/etc/init.d has to exist.  Otherwise you would be getting "No such file or directory" errors instead of syntax errors.

---

### Post by nanotube on 2007-02-22
> **xyrcncp said:**
> Thanks for the welcome.  I'm on Ubuntu 6.10 Edgy Eft

As I'm reading the instructions again, they state that the script resides in 

/etc/init.d/foldingathome start

but when I actually navigate to /etc/ there is no  init.d  at all...:confused:

that's not possible :)
either you are somewhere not in /etc, or you are looking at the listing and missing the init.d in it. what is the output of the following command (type/paste it exactly):
```
ls -ald /etc/init.d
```

---

### Post by xyrcncp on 2007-02-22
> **nanotube said:**
> that's not possible :)
either you are somewhere not in /etc, or you are looking at the listing and missing the init.d in it. what is the output of the following command (type/paste it exactly):
```
ls -ald /etc/init.d
```

I typed the command and got
[code]drwxr-xr-x 2 root root 4096 2007-02-22 20:54 /etc/init.d]/code]

I guess it does exist....oops

[quote=jpkotta]This is a bug that was caused by the switch from bash to dash in Edgy. The newest scripts in the wiki have this fixed. Read the wiki for quick instructions for installing/updating the scripts. Link: https://help.ubuntu.com/community/FoldingAtHome[/quote]
Great!  I followed the wiki and got it running.  I checked the system monitor and the CPU usage is at 95-100%, which I assume it's working.

Just a quick question, if I need to stop the client for some reason, how do I go about it.  I was reading the wiki and it mentioned finstall, is that like a script just to start/stop/status the client? 

I assume that checking the "status" would let me know the stats on what's going on?

---

### Post by jpkotta on 2007-02-23
You control it with the init script.  All init scripts are supposed to have start, stop, and restart commands, and this one is no exception.  Many have a status command too, and for this one, status will print out the end of the log file for each client.  You may rather simply look at the log file manually because that way you don't have to use sudo.  I have the following aliases in my ~/.bashrc:
```

alias fah_log='less /opt/foldingathome/1/FAHlog.txt'
alias fah_tail='tail -f /opt/foldingathome/1/FAHlog.txt'

```
There are also little applets (e.g. for gdesklets, gkrellm, etc.) that provide a GUI to monitor the client.

finstall is another script that basically does the same thing as this one (which I'm unimaginatively calling fah_install).  Of course, I think mine is better.

---

### Post by glotz on 2007-02-23
Did you guys understand what caused that problem? (I didn't) If you did, it's cool, no need to explain really. I was just wondering how this problem was created and if some process should be improved to avoid this in the future. o_O

I know, I'm a funnyguy.

---

### Post by jpkotta on 2007-02-23
The problem is that /bin/sh used to point to /bin/bash, but in Edgy it points to /bin/dash.  dash only understands Bourne shell, while bash understands Bash language, which is a superset of Bourne shell (hence Bourne Again SHell).  I had bash-isms in the scripts, which dash doesn't understand.  

The way to prevent it is to RTFM.  I should have RTFMed the fact that bash still acts like bash when it is called as /bin/sh, and that those statements don't work in Bourne shell.  People who are running Edgy and have the problem at this point (not the ones that first reported it, obviously) should RTFM (i.e. the wiki or this thread), because it is a known problem with a easy fix.  Don't take the above statements as being harsh, they are simply the best way I can see to prevent problems of this type.  The "F" in RTFM means the same thing as the "F" in [FVWM]("http://www.fvwm.org/documentation/faq/#1.1").

---

### Post by xyrcncp on 2007-02-24
You guys are gonna hate me, another n00bish question I bet....

I'm trying to get stats on what my computer is actually doing, I've read that the unitinfo.txt file shows this info and that it should be located in the opt/foldingathome/ folder, but the only file there is: MyFolding.html and it tries to pull up /opt/foldingathome/1/unitinfo.txt but firefox says it doesn't exist.

---

### Post by ruudiculus on 2007-02-24
Are you starting your Folding@Home from another directory than where it is actually located? Folding@Home will drop those files in the directory where you started running Folding@Home

---

### Post by glotz on 2007-02-24
Depends how much you're going to fold! :lol: (just kidden)

Do a **sudo updatedb** and then **locate unitinfo.txt**

That will find probably find it. (on linux filesystems by default)

---

### Post by jpkotta on 2007-02-24
xyrcncp:

Post the output of this command:
```
locate unitinfo.txt

```

Edit:  I'm sloooow.

---

### Post by xyrcncp on 2007-02-24
edit: nevermind ;p

---

### Post by DarkDancer on 2007-03-07
I can't find unitinfo.txt.

locate unitinfo.txt just drops to the next line....

---

### Post by glotz on 2007-03-07
Did you update the database first? Do you have non Linux native partitions? (vfat or ntfs)

---

### Post by DarkDancer on 2007-03-07
By update the database I assume you mean: sudo updatedb.

Yes, I did that. I do have a couple of fat32 partitions. Do I need to do something else to see what it's doing?

---

### Post by glotz on 2007-03-07
Yes, that's what I meant. It doesn't index non-Linux partitions by default. If the file's on a vfat partition you need to edit /etc/updatedb.conf and remove vfat from prunefs. Then update and then locate.

---

### Post by DarkDancer on 2007-03-07
Hmmm, I don't belive that it is on a fat partition, and the file /etc/updatedb.conf doesn't contain an instance of vfat, or even just fat (I searched for both).

---

### Post by Megatog615 on 2007-03-15
How would I be able to automatically run it when my screensaver begins(I use a blank screensaver)?

---

### Post by DarkDancer on 2007-03-17
Ok, so after redoing my drives and reinstalling everything I can finally see my unitinfo.txt...yay! However, as far as I can tell I have sent in 2 work units and my personal statistics page never updates. anyone have a clue why?

---

### Post by moz_21 on 2007-03-18
If you mean the MyFolding.html page, it wont; it contains static information. The link on that page, unitinfo.txt, will be the one that updates. If you mean the Stanford pages, I believe they take a little while to update if you're a new user.

Jpkotta, thanks for the script and howto. I do have an issue with the battery/ac script. It doesn't kill or restart FAH. I've tried chmod +x on the "fah" script under both directories but that doesn't fix it. Is anyone else using it and if so, does it work for you?

---

### Post by DarkDancer on 2007-03-18
Yeah, it is the stanford page I am talking about. While I'm not a new user, it has been a while since I turned in a work unit (the last one before the current crop was  2006-07-29 14:15:52), so maybe that's like being a new user again.

---

### Post by jpkotta on 2007-03-18
> **moz_21 said:**
> Jpkotta, thanks for the script and howto. I do have an issue with the battery/ac script. It doesn't kill or restart FAH. I've tried chmod +x on the "fah" script under both directories but that doesn't fix it. Is anyone else using it and if so, does it work for you?

Which version of Ubuntu are you using?  Hint:```
cat /etc/lsb-release
```

It works for me obviously, with both Dapper and Breezy.  I do Edgy testing in VMware, and I don't know how to simulate ac/battery events.  Note that it may take a while before it actually shuts down/starts up.  Mine always works in under a minute.

Speaking of testing, has anyone tried this (the installer/init scripts) under Feisty?

---

### Post by moz_21 on 2007-03-18
> **jpkotta said:**
> Which version of Ubuntu are you using?  Hint:```
cat /etc/lsb-release
```

It works for me obviously, with both Dapper and Breezy.  I do Edgy testing in VMware, and I don't know how to simulate ac/battery events.  Note that it may take a while before it actually shuts down/starts up.  Mine always works in under a minute.

Speaking of testing, has anyone tried this (the installer/init scripts) under Feisty?

I'm using Edgy. Maybe I'm not waiting long enough or maybe it has something to do with the switch from bash>dash (similar to what you went through with the install script I believe). 

Minutes later...

Ok, I tried adding #! /bin/sh to the "fah" script and it did nothing. I waited even longer (about 3 minutes) and it didn't kill the process.

So, both scripts look like the following and are executable, but do not work?? They do what they should when manually executed (sudo ./fah). They are also identical (in re: permissions and +x) to the only other file in ac.d and battery.d, named "15-anacron.d". In case you're wondering, my laptop is a Compaq Presario 2100 and is able to detect when I plug and unplug the power adapter. 

```
#! /bin/sh
/etc/init.d/foldingathome stop >/dev/null

#! /bin/sh
/etc/init.d/foldingathome start >/dev/null
```

---

### Post by DarkDancer on 2007-03-19
Hey moz_21, just curious, how long do you think it will take?

---

### Post by jpkotta on 2007-03-19
Apparently, the scripts in /etc/acpi/{battery.d,ac.d} must end with ".sh".  I don't think they need to be executable or need a shebang on the first line.  Wiki has been updated.

---

### Post by moz_21 on 2007-03-19
> **DarkDancer said:**
> Hey moz_21, just curious, how long do you think it will take?

As long as it takes when running the script manually. ;)


> **jpkotta said:**
> Apparently, the scripts in /etc/acpi/{battery.d,ac.d} must end with ".sh".  I don't think they need to be executable or need a shebang on the first line.  Wiki has been updated.

Hah, how weird. That did the trick. I was going to try that but I guess I forgot. Now it runs just like when Window$ was on it (and everyone knows how)! Thanks!

---

### Post by DarkDancer on 2007-03-19
> 
Quote:
Originally Posted by DarkDancer View Post
Hey moz_21, just curious, how long do you think it will take?
As long as it takes when running the script manually. 

I'm afraid I don't understand the answer to the question.... #-o

---

### Post by moz_21 on 2007-03-19
> **DarkDancer said:**
> I'm afraid I don't understand the answer to the question.... #-o

It should take just as long as when manually starting or stopping it, via either /etc/init.d/foldingathome stop (or start) or when running the same thing via the fah.sh (note the .sh to make it work) located in the /etc/acpi/battery.d or /etc/acpi/ac.d.

It took about a minute to shutdown the service and it starts back up within a few seconds.

---

### Post by DarkDancer on 2007-03-19
Oh, now I understand why I didn't get the answer, you're answering a different question... ;)

My question was about how quickly you thought the Stanford page would update me, it hasn't yet and I just wanted to make sure I wasn't crunching to no purpose... ;)

---

### Post by moz_21 on 2007-03-20
> **DarkDancer said:**
> Oh, now I understand why I didn't get the answer, you're answering a different question... ;)

My question was about how quickly you thought the Stanford page would update me, it hasn't yet and I just wanted to make sure I wasn't crunching to no purpose... ;)

Doh! I thought you were being a smart*** when you first asked it... Sorry about that.

Well first off, make sure you're looking at the right stats page. Be aware that it is case sensitive. If I remember right there are some characters you can't have in your username or it will fold anonymously. Otherwise it should update pretty quickly I'd imagine. To be honest, I've been folding since 2001 or so; i really don't remember how long it took. Just double check everything over.

Fyi, another good stats page: [http://folding.extremeoverclocking.com](http://folding.extremeoverclocking.com).

---

### Post by DarkDancer on 2007-03-20
[Extremeoverclocking ]("http://folding.extremeoverclocking.com/user_summary.php?s=&u=176184") has all the old info for me (from 2006) but none of the mew that I have turned in, very much like stanford.....

The Stanford page I go to is the one from "My Folding Page" which I would have to think would be the right one. If something doesn't go right, is there an error log or something that is created?

---

### Post by jpkotta on 2007-03-20
Wow, moz, you have almost a million points.  Way to go!  Too bad you're not folding for TeamUbuntu, we could use more.

---

### Post by moz_21 on 2007-03-20
> **DarkDancer said:**
> [Extremeoverclocking ]("http://folding.extremeoverclocking.com/user_summary.php?s=&u=176184") has all the old info for me (from 2006) but none of the mew that I have turned in, very much like stanford.....

The Stanford page I go to is the one from "My Folding Page" which I would have to think would be the right one. If something doesn't go right, is there an error log or something that is created?

As it should; it uses the stanford page for it's own updates. I'd have to say the client.cfg file is corrupted for some reason. You might want to stop the service, delete the client.cfg file, and then run the reconfigure script (/opt/foldingathome/reconfigure). :edit: I just read that DST is screwing up the updates for some people so that could be the case also.

> **jpkotta said:**
> Wow, moz, you have almost a million points.  Way to go!  Too bad you're not folding for TeamUbuntu, we could use more.

Thanks, it's been a long time coming!

---

### Post by DarkDancer on 2007-03-20
Hehe, guess I just needed to wait a litttle longer, it updated... ;)

---

### Post by mahiyar on 2007-03-25
Used the how to and everything working well. Also downloaded protein think. However I have a few questions to ask. I have a Intel 4 3.0GHz HT processor, however in the System Monitor the Fahcore runs at @50%, while in the HTOP or TOP CLI the Fahcore runs at @100%. Is that anything to do with HT processors which are virtually seen by system monitor as 2 processors. Will increasing the number of processors to 2 during config increase the processor load to 100%?

---

### Post by moz_21 on 2007-03-26
> **mahiyar said:**
> Used the how to and everything working well. Also downloaded protein think. However I have a few questions to ask. I have a Intel 4 3.0GHz HT processor, however in the System Monitor the Fahcore runs at @50%, while in the HTOP or TOP CLI the Fahcore runs at @100%. Is that anything to do with HT processors which are virtually seen by system monitor as 2 processors. Will increasing the number of processors to 2 during config increase the processor load to 100%?

Yes but I believe the efficiency goes down. I'm not sure what the official word is although you may find this to be helpful:

[quote=F@H configuration FAQ]
[http://folding.stanford.edu/FAQ-settings.html](http://folding.stanford.edu/FAQ-settings.html)

Computers with multiple CPUs (SMP) are supported under FAH in two ways. For Intel-based Macs and x86 PC's running linux, there is a special SMP client. For other machines, one can use multiple processors by running multiple clients (one for each CPU). This is clearly non-ideal and better support is under development. There are certain caveats of using SMP boxes with special flags. Do not run multiple clients with each set to the most aggressive settings (bigWU + adv), as this can overwhelm most computers. Instead, we suggest bigWU+adv on one client and the default settings on the other(s). In situations where reliability, stability, and/or responsiveness a premium, we suggest either all clients with the default settings or just one client with the big WU enabled.[/quote]

---

### Post by mahiyar on 2007-03-26
Thanks for the prompt reply moz_21, that really cleared up things. Now for two more queries. I see that the folding@home has created a user of the name foldingathome, with home directory in /opt/foldingathome, is it normal? Now the second question, when I run foldingathome my cpu is 50 - 100% occupied, and the temperature stays fairly high about 75 degrees celcius, it may be due to high ambient of our region (around 30), now I have seen my processor specs and 75 deg is at  the higher band, but is running continuously  at high temp ok?
Thanks in advance.

---

### Post by glotz on 2007-03-26
The dedicated user is normal and a security feature. Running too hot can damage the chip and might shorter it's lifespan. I wouldn't suggest doing it. I'd constantly keep below 70. That's a pretty high temp but so is the ambient too. Have you got a proper fan and a well placed heatsink with the correct amount of heat conductive paste?

---

### Post by mahiyar on 2007-03-26
Thanks Glotz, well as a first step I removed the processor heat sink assembly and thoroughly cleaned it, (it was full of dust), the result - temperature within 70 degree, (@68 ), now as a next step I have to put thermal pad/glue, I'am sure that will help.

---

### Post by moz_21 on 2007-03-26
That P4 you have is a hot runner anyhow. Keep the fan clean and you'll be just fine. It should throttle or shut down if it ever gets waaayy to hot but that would probably only happen if the fan dies.

---

### Post by jpkotta on 2007-03-26
mahiyar, all of your questions are answered on our wiki: [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome).

The HT question has it's own section.  Yes, you can run two clients and get your CPU meter to 100%, but since you're already worried about thermal issues, it's probably not a good idea.  There is a program that limits the CPU usage of a given program if you're still worried about temperature (link in the wiki).

---

### Post by dirtaholman on 2007-03-29
Hello everyone,

   Great info on setting up the folding client. However, i have 2 issues. I have a machine running windows vista and one running Kubuntu edgy behind an ipcop firewall. The first problem i'm having is that in Kubuntu, i've had the client running for about 2 days now and still no unitinfo.txt file. sudo updatedb and locate turn up nothing. I've verified the client is properly running with top and ksysguard. The other issue i'm having is that my windows machine is failing to send work units back, i get "could not connect work server (results)". I've port-forwarded port 8080, and made sure the windows firewall wasn't interfereing, but still get the same error. Any ideas anyone? I'd really like to donate!

Thanks in advance!

EDIT: I finally have a unitinfo.txt file, and i found that IE7 was the problem. I have no idea what took so long, but I'm happily crunching and hopefully sending units in now.

---

### Post by rowanparker on 2007-04-03
Script works grand on Debian :)

---

### Post by jpkotta on 2007-04-03
> **rowanparker said:**
> Script works grand on Debian :)

Excellent!  I didn't waste my time reading the Debian docs (they were interesting anyway).

---

### Post by muguwmp67 on 2007-04-06
I've been running fah for a couple of months now, and it is working.

I'm not sure I have it configured correctly though for my AMD 64 X2 processor.  When Fah is running, it never reaches more than 50% utilization, which is fine.  However, my understanding is that it should scale down as more processor is needed.  I never see fah go below 45% utilization, even when another process is dragging the system to its knees.

Is this normal behavior for fah?  Its running with nice set at 19.

---

### Post by jpkotta on 2007-04-06
muguwmp67:

It sounds like you're only running one core.  You may want to try the SMP client or if you used fah_install from the first post in this thread, then you should set it to run 2 clients.  You want to run one UP client per processor, or one SMP client for all processors.

I have decided to build a machine as soon as Intel chips drop in price, which should be around April 22.  Then I will be able to test my scripts with SMP clients and add an option for installing them.  Right now, you can probably just change the name of the executable in install.sh.  Has anyone tried this?

---

### Post by moz_21 on 2007-04-06
> **muguwmp67 said:**
> I've been running fah for a couple of months now, and it is working.

I'm not sure I have it configured correctly though for my AMD 64 X2 processor.  When Fah is running, it never reaches more than 50% utilization, which is fine.  However, my understanding is that it should scale down as more processor is needed.  I never see fah go below 45% utilization, even when another process is dragging the system to its knees.

Is this normal behavior for fah?  Its running with nice set at 19.

It is. You've set it up to use one core. Anything that isn't multi-threaded will show as 50% usage when it's going full bore. Since the majority of applications are still single-threaded you are able to run FAH at maximum usage on one core and just the OS and apps on the other.

> **jpkotta said:**
> 
It sounds like you're only running one core.  You may want to try the SMP client or if you used fah_install from the first post in this thread, then you should set it to run 2 clients.  You want to run one UP client per processor, or one SMP client for all processors.

That sounds exactly right. If you were running a single core (or if you run a multi-threaded application) it would scale back. FAH is very unobtrusive on every computer I've had it on. The big thing is ram. If you are running big-packets or the beta SMP client I recommend 1GB of ram (unless it's a dedicated folder; you can get away with half of that if you don't need to load a GUI).

> **jpkotta said:**
> 
I have decided to build a machine as soon as Intel chips drop in price, which should be around April 22.  Then I will be able to test my scripts with SMP clients and add an option for installing them.  Right now, you can probably just change the name of the executable in install.sh.  Has anyone tried this?

I was thinking the same thing about the script but I don't have an x86-64 capable dually running Linux. If/when the 32bit linux SMP client comes out, I'll give it a try but until then I can't say I'm much help.

---

### Post by muguwmp67 on 2007-04-06
Thanks for the explanation.  I haven't noticed any performance problems while running fah, but was curious as to why it didn't look like it was giving away cycles to other apps.  This also explains why the super_pi script comes up with roughly the same result whether fah is running or not.

---

### Post by chewearn on 2007-04-15
hi everyone
I started running F@H a few weeks ago; installed it using the fah_install script.  Everything was running smoothly (after a few minor tweaks).  Recently I started having problem uploading a couple of WUs, but found out it was server problem at Stanford side; so that should be resolved once the data server is fixed.

Anyway, on to the reason I am posting here.  While investigating the problem above, I found out that I was running FAH502-Linux.exe.  I recalled during the installation process this application was automatically downloaded by the fah_install script.  However, I also noticed the latest version at F@H website is FAH504-Linux.exe.

Questions:
1. Is it ok to continue running version 502?
2. How do I go about updating to version 504?
3. If I update, will my existing completed WU be retained (or should I wait until successful upload before updating to version 504)?

Thanks for all help/feedback. :D

---

### Post by ruudiculus on 2007-04-15
Maybe the best thing you can do if you want to update is to copy the whole 5.02 folder and replace the 5.02 executable with a 5.04 executable. This way you can easily test if 5.04 continues working with your 5.02 WU's. If not (and your WU's are destroyed or something) )you still have the **GOOD** directory with a 5.02 executable and the original WU's. My quess is that 5.04 will continue working on the WU's fine, but this is a way to try.

---

### Post by chewearn on 2007-04-15
> **ruudiculus said:**
> Maybe the best thing you can do if you want to update is to copy the whole 5.02 folder and replace the 5.02 executable with a 5.04 executable. This way you can easily test if 5.04 continues working with your 5.02 WU's. If not (and your WU's are destroyed or something) )you still have the **GOOD** directory with a 5.02 executable and the original WU's. My quess is that 5.04 will continue working on the WU's fine, but this is a way to try.

Hey, thanks.  Sound like a good workaround.  I followed it, and it looks like the my finished WUs are still ok.

The only minor issue I noticed is that executable filename is coded inside the fah_install script, and i don't know enough about the script to be able to change it to "FAH504-Linux.exe".  Instead I have renamed the filename "FAH504-Linux.exe" to "FAH502-Linux.exe".

---

### Post by ruudiculus on 2007-04-15
Haha, great workaround as well :D 

If you want some sort of monitoring applet for your folding process, there's one on my website.

---

### Post by chewearn on 2007-04-15
> **ruudiculus said:**
> Haha, great workaround as well :D 

If you want some sort of monitoring applet for your folding process, there's one on my website.
I recently have a conversation with you in the applet thread; reported a problem getting the applet added to the gnome panel. :D  Haven't got around to investigation more about it.  Instead, I have worked out another way to monitor using conky.

---

### Post by l1oyd on 2007-06-08
I think it should be set up but I don't think it is running

when I enter "start" in /opt/foldingathome/ I get error msg

> start: missing job name
Try `start --help' for more information.


So how do I get a "job name"

Also I'm running the script from the [wiki]("https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu") after uninstalling the script in this thread

---

### Post by chewearn on 2007-06-09
> **l1oyd said:**
> I think it should be set up but I don't think it is running

when I enter "start" in /opt/foldingathome/ I get error msg

So how do I get a "job name"

Also I'm running the script from the [wiki]("https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu") after uninstalling the script in this thread


Use this command to start:
```
sudo /etc/init.d/foldingathome start
```

---

### Post by Heinrisch on 2007-06-09
```

Logfile in /opt/foldingathome/1:
[22:30:53] Project: 3040 (Run 38, Clone 639, Gen 14)
[22:30:53]
[22:30:53] Assembly optimizations on if available.
[22:30:53] Entering M.D.
[22:30:59] Protein: p3040_supervillin-03
[22:30:59]
[22:30:59] Writing local files
[22:30:59] Extra SSE boost OK.
[22:30:59] Writing local files
[22:30:59] Completed 0 out of 5000000 steps  (0%)

```

It looks like the client has stopped right there, at step 0. If I check status it says that the client is running. Has it stopped or just that it does not update until it has completed the current task?

---

### Post by chewearn on 2007-06-10
> **Heinrisch said:**
> ```

Logfile in /opt/foldingathome/1:
[22:30:53] Project: 3040 (Run 38, Clone 639, Gen 14)
[22:30:53]
[22:30:53] Assembly optimizations on if available.
[22:30:53] Entering M.D.
[22:30:59] Protein: p3040_supervillin-03
[22:30:59]
[22:30:59] Writing local files
[22:30:59] Extra SSE boost OK.
[22:30:59] Writing local files
[22:30:59] Completed 0 out of 5000000 steps  (0%)

```It looks like the client has stopped right there, at step 0. If I check status it says that the client is running. Has it stopped or just that it does not update until it has completed the current task?

That's normal.  By default, every 15 minutes, it will save the computation to disk, and you should see a new message.

---

### Post by Spartan.II.117 on 2007-06-12
i used the fah_install script and it worked great, then i had to re-install Ubuntu and so i used it again and copied my old directory but now it runs and works for a while i come back and it's no longer running. anyone else having similar issues?
P.S i'm running fiesty

---

### Post by jpkotta on 2007-06-12
I've had trouble in the past using restored backups.  It's not guaranteed to work.  The fact that it runs for a while suggests you did everything correctly, and the client is having trouble in spite of it.

---

### Post by Spartan.II.117 on 2007-06-13
do you have any suggestions on how to fix it? uninstall/reinstall, remove work folder etc?

---

### Post by jpkotta on 2007-06-13
Maybe I'm forgetting something.  Can you say whether or not this command returns anything?
```
grep foldingathome /etc/passwd
```
If it doesn't return anything, then it isn't installed completely, and you should keep your backup, uninstall, reinstall, then replace the installation with the backup (the installer does more than simply copy files).

---

### Post by Spartan.II.117 on 2007-06-17
[FONT=monospace]foldingathome:x:1001:1001::/opt/foldingathome:/bin/false

Like i said, it runs for awhile (15 min?) then quits. possibly when trying to write to the log.
(just realised that it's possibly related to a problem i've been having with gedit... investigating now... will post my findings within the half-Hr)

[/FONT]

---

### Post by Spartan.II.117 on 2007-06-17
well it's been nearly an HR and still nothing (it's still working) but it hasnt moved a percent yet, so i assume it's running properly.

---

### Post by Spartan.II.117 on 2007-06-17
nope, it quit  later, i ran it from the terminal today and it's gotten through about 6-7 percent, so once it finishes i'm going to un/re-install

---

### Post by jpkotta on 2007-06-18
I was thinking that maybe it didn't have the special f@h user created, but it does.  Your plan is what I would do.

---

### Post by Spartan.II.117 on 2007-06-18
yep, it finished so i re-installed and i caught it at the right time because the work server was down. so it now works fine!

---

### Post by pjc330 on 2007-07-01
Hi, Sorry if this is the worng place, I can't find an answer on the Forum.

How do I move a WU at 23% from one computer to another.  An old P450 box is working on a big WU and and has crashed a few times.  I want to put it on a faster cumputer so it will finish before the deadline.

I copied the Folding folder and all it sub folder to the faster box but it does not restart the old WU from the saved piont.  It fails the run any WUs.  With new FAH504 download and install it retrieves a new WU.

I must be missing a setting in the -config after changing computers.

I a new to Ubuntu and Folding@Home.

Thanks

---

### Post by jpkotta on 2007-07-01
> **pjc330 said:**
> Hi, Sorry if this is the worng place, I can't find an answer on the Forum.

How do I move a WU at 23% from one computer to another.  An old P450 box is working on a big WU and and has crashed a few times.  I want to put it on a faster cumputer so it will finish before the deadline.

I copied the Folding folder and all it sub folder to the faster box but it does not restart the old WU from the saved piont.  It fails the run any WUs.  With new FAH504 download and install it retrieves a new WU.

I must be missing a setting in the -config after changing computers.

I a new to Ubuntu and Folding@Home.


Thanks

Is the slow computer a Windows machine?  You need to jump through some hoops to move from Windows to Linux.  Look at the Sneakernetting link on the F@H wiki page (see my sig).  That will tell you 90% of what you need to do to move WUs from Windows to Linux (the other 10% is installing Wine).

Anything you set with -config is stored in client.cfg, so all settings should be copied.

---

### Post by pjc330 on 2007-07-02
Both the old and new computers are setup with Ubuntu 7.04. 

I looked again at the Sneaker netting page.  I think I did what the page said about moving WUs between computers with the same OS.  I know nothing about a Ubuntu Registry (or if it has one). Do I need to copy some thing else to the new computer to get it to recognize the old WU?  I did move the entire FOLDING directory/folder to the new computer.

I want to move the old WU to a different computer and continue folding that WU on the new computer that is network and internet connected.

I just can’t get the faster computer to work the old computers WU.  It is folding a different WU as we speak without any problems. 

The old computers WU is: p4308_dpdp-ii   I think it’s a Beta WU, that may have something to do with the problem.

I will keep trying.

Thanks

---

### Post by jpkotta on 2007-07-02
There is no Ubuntu registry (thank goodness).  You would have used the Wine registry if the slow computer was running Windows.  

All I can say is that F@H was not designed to move WUs around, so there is probably some hidden undocumented thing that is causing the move to fail.  Maybe check out the semi-official F@H forums [http://forum.folding-community.org/](http://forum.folding-community.org/).  I have moved WUs between Windows and Linux, but it was not easy, and the computers I was using were very similar hardware-wise.

---

### Post by theonlyalterego on 2007-07-06
I'm getting the following errors when I follow the howto:
```

ub-desktop:~$ sudo /etc/init.d/foldingathome start
/etc/init.d/foldingathome: 23: [[: not found
/etc/init.d/foldingathome: 33: [[: not found
/etc/init.d/foldingathome: 147: [[: not found
/etc/init.d/foldingathome: 147: arith: syntax error: "++num"

```

Has anyone seen anything like this before?

---

### Post by jpkotta on 2007-07-06
> **theonlyalterego said:**
> 
Has anyone seen anything like this before?

Ugh. You probably got this from the forum thread.  I hate the fact that only one person can edit a post.  Wikis are better for this kind of thing.  I'll talk to an admin about removing the old version of the script.

Use the latest version from the wiki (link in my sig).

---

### Post by GreenGirl on 2007-07-07
I installed Folding@Home earlier today and have some questions:

-If I close the terminal window, does that close f@h, or will f@h run in the background?  Is there a specific command for exiting f@h?  (I shut my computer down at night, and I don't want to screw up f@h by exiting the program incorrectly)

-If closing the terminal window does close f@h, is there anyway to prevent this?  (should I run f@h in the background?  As you can probably guess, I'm a linux newbie.)  I'd rather not have to keep a terminal window minimized all the time.

-Why doesn't my username show up on the stat list on the website?  (I can't check now because their server is down, but earlier it wasn't listed.)  Is it because I haven't finished folding my first protein yet?

-I'd like to join Team Ubuntu.  I do this by going into config and setting my team to 45104, right?  Can I do this while F@H is already running?

Thanks.

---

### Post by nanotube on 2007-07-07
> **GreenGirl said:**
> I installed Folding@Home earlier today and have some questions:

-If I close the terminal window, does that close f@h, or will f@h run in the background?  Is there a specific command for exiting f@h?  (I shut my computer down at night, and I don't want to screw up f@h by exiting the program incorrectly)


that depends on what command you use to start the fah client...

> -If closing the terminal window does close f@h, is there anyway to prevent this?  (should I run f@h in the background?  As you can probably guess, I'm a linux newbie.)  I'd rather not have to keep a terminal window minimized all the time.

if you add ' &' to the start command, that will put it in the background, and you can safely close the terminal. if you want to later kill the process, just find it in the process list (in system monitor), and kill it.

> -Why doesn't my username show up on the stat list on the website?  (I can't check now because their server is down, but earlier it wasn't listed.)  Is it because I haven't finished folding my first protein yet?

yes, your username won't show up until you submit your first completed work unit (and there will be some delay after that, since that list isn't updated real time.

> 
-I'd like to join Team Ubuntu.  I do this by going into config and setting my team to 45104, right?  Can I do this while F@H is already running?

Thanks.

you have to restart the fah client in order for the changes to take effect.

i think that takes care of all your questions. ;)

---

### Post by GreenGirl on 2007-07-07
Thanks.  One more question: when I close the program, it saves the progress it's made so far, right?  I'm not going to lose the data because it didn't finish folding the protein?

---

### Post by nanotube on 2007-07-08
> **GreenGirl said:**
> Thanks.  One more question: when I close the program, it saves the progress it's made so far, right?  I'm not going to lose the data because it didn't finish folding the protein?

yes, it saves progress periodically, and fairly frequently. so you won't lose anything to speak of. :)

---

### Post by GreenGirl on 2007-07-08
I tried running it in the background, closing the terminal window, opening a new terminal window and typing "ps", but the only processes listed were bash and ps.  So I tried running it regularly, opening a new window (while it was running in the other window) and typing "ps", and it still wasn't listed.:confused:  Any idea what I'm doing wrong?

---

### Post by freebeer on 2007-07-08
try:

```

ps -e

```

The -e parameter tell ps to show every process.  Without it, you only see processes related to your logged-in account.  (Folding runs as a root process, I believe.)

---

### Post by glotz on 2007-07-08
Depends how you installed it. I used the script provided with sudo and then it's running on it's on 'foldingathome' account.

---

### Post by GreenGirl on 2007-07-08
ok, it shows up if I use ps -e, but if I close the terminal window it disappears from ps -e, even though I was running it as ./FAH504-Linux.exe&

---

### Post by Swab on 2007-07-08
> **GreenGirl said:**
> ok, it shows up if I use ps -e, but if I close the terminal window it disappears from ps -e, even though I was running it as ./FAH504-Linux.exe&

Closing the terminal will stop the process.  The wiki has an script to setup FAH as a service which resolves this issue.

---

### Post by GreenGirl on 2007-07-08
ok, thanks. :)

---

### Post by GreenGirl on 2007-07-08
I installed finstall and rebooted my computer.  It looks like fah now starts automatically. :)  ps -e is saying:

5286 ?        00:00:00 FaH
 5301 ?        00:00:00 FaH
 5303 ?        00:00:05 FAH504-Linux.ex
 5304 ?        00:00:05 FAH504-Linux.ex

Is FaH supposed to have 4 processes?

Only problems I'm having is that qd (which was supposed to install with finstall) doesn't seem to exist, and fpd is saying I'm Anonymous and Team[0], even though I entered my username and the ubuntu team number when I configured FaH.

---

### Post by jpkotta on 2007-07-08
For the curious, you must do more than background a process to detach it from a terminal.
```
(exec some_command) &
```
The '()' forks the shell into a new one (one that isn't attached to the terminal), and "exec" replaces the new shell process with the some_command process, which a) means you don't have an extra shell running, and b) starts a bit faster.  I have in my ~/.bashrc a "daemon" function that will do this.
```
# super stealth background launch
# disconnects from launching shell, keeps running until killed
function daemon
{
    (exec "$@" >&/dev/null &)
}
```
```
daemon some_command
```

Now, back on topic, F@H has several processes.  The FahCore_....exe processes are threads (I think) of the core, which is actually doing the work.  There is also the client, which starts and stops cores and uploads results, etc.  But it looks like you (GreenGirl) have two clients running, which may or may not be OK, depending on what finstall does.  If you have 2 CPUs and you are not running the SMP client, you'll want one client (plus its associated cores) for each CPU.

---

### Post by GreenGirl on 2007-07-08
Ugh, I'm sorry I'm being such a pain about this but does anyone know how to uninstall finstall?  I want to be able to see my progress (fpd isn't working now for some reason) and now that I know how to get it running in the background without a terminal window (thanks, jpkotta) I think it would probably be better to just manually run it in the background and move it to the foreground whenever I want to see the progress, rather than have finstall handle everything.

---

### Post by Swab on 2007-07-08
> **GreenGirl said:**
> Ugh, I'm sorry I'm being such a pain about this but does anyone know how to uninstall finstall?  I want to be able to see my progress (fpd isn't working now for some reason) and now that I know how to get it running in the background without a terminal window (thanks, jpkotta) I think it would probably be better to just manually run it in the background and move it to the foreground whenever I want to see the progress, rather than have finstall handle everything.

There is a text file you can check for progress... unitinfo.txt if I recall correctly.  Sorry I'm not folding at the moment!

---

### Post by sam0t on 2007-07-08
> **GreenGirl said:**
> 
5286 ?        00:00:00 FaH
 5301 ?        00:00:00 FaH
 5303 ?        00:00:05 FAH504-Linux.ex
 5304 ?        00:00:05 FAH504-Linux.ex

Is FaH supposed to have 4 processes?


Yes it is, I wondered the very same thing and found the answer at folding@home forums.

---

### Post by SuperAndy on 2007-07-17
After following the howto [here](https://help.ubuntu.com/community/FoldingAtHome), specifically this bit:

"For me this was all I needed as it automatically created the init scripts I needed to start after reboot. However the init scripts don't seem to work for everyone, so if you need to do it manually:

   1.

      Make a file called foldingathome in the /etc/init.d directory:

```
gksudo gedit /etc/init.d/foldingathome
```

   2.

      Paste this in:

```
#!/bin/sh
# /etc/init.d/foldingathome for Ubuntu
# Start the F@H service.

pushd /home/YOUR_USERNAME_HERE/foldingathome/
su YOUR_USERNAME_HERE -c "screen -d -m ./folding start"
popd
```

   3.

      Save and exit
   4.

      Make a symlink into the /etc/rc2.d directory:

```
sudo ln -s /etc/init.d/foldingathome /etc/rc2.d/S99fah
```

Now, when i start, the booting freezes about 4/5th of the way through.

If i stick it in recovery mode, i get to the andy@andy_desktop promt, and then it freezes, and i get a:

SOFT LOCKUP DETECTED ON CPU#0!

The exclamation mark really takes the piss... I am pretty sure it was that init.d stuff. I have tried deleting the /etc/init.d/foldingathome entry, but it makes no difference (i am using a livecd to get in there to edit the stuff).

Anyone got any ideas over this?

---

### Post by jpkotta on 2007-07-17
If you deleted the f@h stuff, it shouldn't affect the system at all.  It sounds like a hardware problem.  I couldn't tell you much more than that.  Maybe try a different kernel?

---

### Post by SuperAndy on 2007-07-17
i have tried the two kernels i have in grub. the thing is, its the only thing i changed to my system, nothing else. there's nothing it could be. i will have another bash though...

---

### Post by sad_iq on 2007-07-28
Ok...here goes...the first time I read this howto...installed it...works great(the install part)...but when I try to run it it prints this: ```
sudo /etc/init.d/foldingathome start
/etc/init.d/foldingathome: 23: [[: not found
/etc/init.d/foldingathome: 33: [[: not found
/etc/init.d/foldingathome: 147: [[: not found
/etc/init.d/foldingathome: 147: arith: syntax error: "++num"

```
  Sorry if it was posted before but I cannot read all the pages in this thread...and searching for it turned out nothing. Sorry for the trouble but I would like to have this running!!!

---

### Post by jpkotta on 2007-07-28
Use the script from the wiki.  Link in my sig.

---

### Post by sad_iq on 2007-07-28
> **jpkotta said:**
> Use the script from the wiki.  Link in my sig.

Ok...thanks...works now...somebody should update the thread thou!!!

---

### Post by jpkotta on 2007-07-29
> **sad_iq said:**
> Ok...thanks...works now...somebody should update the thread thou!!!

Yes.  Yes they should.  I've emailed the admins twice.  I've tried to contact the original poster.  This is why forums suck for information that has any sort of permanence.  Wikis are much better for documentation.  I must say that the script got much more exposure in the forums, but the howto really should have been something more like "Here's a link to the wiki page, where the real howto is.  Post your problems here.".  Anyway, if the admins ever get back to me, I'll redo it properly.

---

### Post by otchster on 2007-08-01
I need to know a few things....


First off, I have this set up on an old PC running Ubuntu..  I have it set up with no monitor, so I have tap in remotely..  I have installed and successfully can run F@H...

My question is..  If puTTY (the program I use to connect to the machine) looses its connection, will F@H still run???

Could I actually close puTTy after I starte F@H, that way I don't always have to have a connection terminal running on my other computer ??

If I do get disconnected, will F@H save its current progress for the next time, or does it start over???


Thanks all :-)

---

### Post by nanotube on 2007-08-02
> **otchster said:**
> I need to know a few things....


First off, I have this set up on an old PC running Ubuntu..  I have it set up with no monitor, so I have tap in remotely..  I have installed and successfully can run F@H...

My question is..  If puTTY (the program I use to connect to the machine) looses its connection, will F@H still run???

Could I actually close puTTy after I starte F@H, that way I don't always have to have a connection terminal running on my other computer ??

If I do get disconnected, will F@H save its current progress for the next time, or does it start over???


Thanks all :-)

about your first question: easiest thing is to try it and see. connect, start fah, disconnect, connect again, then see if cpu is still being eaten by the fah process or not. :) 

if the fah process is killed by disconnect, you could try starting the process with & at the end, which would put the process in the background... but i'm not sure if that will keep it alive.

a surefire way is to use a neat little program called "screen", which lets you run a bunch of virtual "terminals" in your shell session, and which you can connect and disconnect from between logins, so that should let you run fah even when you're not connected. 

you could also run fah at boottime in an init script, which would leave it running without you having to do anything at all. :)

as to progress saving- fah periodically writes its progress to disk, so you don't lose all your work if something crashes. so no worries there.

---

### Post by jpkotta on 2007-08-03
> **otchster said:**
> My question is..  If puTTY (the program I use to connect to the machine) looses its connection, will F@H still run???


If you start it correctly, yes.  Use one of the scripts from the wiki (fah_install or finstall); they are written for this purpose.  If you are curious, read this post: [http://ubuntuforums.org/showpost.php?p=2985303&postcount=295](http://ubuntuforums.org/showpost.php?p=2985303&postcount=295).

screen is good too, but in this case I'd say use the scripts because they will also start it at boot time, which is almost certainly what you want.

> **otchster said:**
> 
If I do get disconnected, will F@H save its current progress for the next time, or does it start over???

It saves every 15 min by default.  You can set this during the initial config or by running it with the -config (or -configonly) option.

---

### Post by legatek on 2007-08-15
I would like to report a bug with the latest version of the install script on the Wiki page.

I have been happily folding on my home computer (Edgy) for a couple of days so I decided to also load F@H on my work computer (Feisty). Currently there are two scripts on the Wiki page, one dated 20061219 and the other still in beta dated 20070702. I downloaded and installed the beta script to install F@H. Since I connect through a proxy at work I had to download the client manually and move it into /opt/foldingathome/config. The problem is the beta script will not recognize if a client exists at this location unless it installs the client there itself. The client version doesn't matter, nor does it matter if the client has user or root permissions. It is not recognized. However, the earlier script works fine, so now I have two computers contributing to Team Ubuntu world domination.

In case it matters, I should mention that I first had to create the foldingathome and config directories manually, since the install script didn't do it before trying (unsuccessfully) to connect to the Stanford site.

---

### Post by jpkotta on 2007-08-15
Thanks for the report.  Can you download the client by hand and put it in the same directory as the install script?  That was the intention for manual downloads.  I will update the docs to reflect this when I get a chance.

---

### Post by legatek on 2007-08-16
OK, that works fine. The problem was that the install script directed me to save the client to /opt/foldingathome/config myself. Thanks.

---

### Post by freebeer on 2007-08-16
I used the script from the wiki to set it up on my dual Core machine.  The install seems to have gone well, except that the script didn't correctly identify that I have two CPUs.  So, as directed, I told the script that I had two.  It dutifully installed the two setups, but the second one failed to launch (so I'm only running one instance right now).  I manually edited the .cfg file in /opt/foldingathome/2 to change the machineid to 2 thinking that might help (it was set as "1" like the one that's working) but that didn't seem to have the desired effect.  Where'd I mess up?

I'm new to the dual-core thing and I thought it was interesting to note how the one instance would flip between cores in htop.  One cpu would be reporting 100% usage for a bit, then the second cpu would be at 100% while the other one dropped to near zero.  Is this normal "load balancing" that I'm seeing?  Just curious.

---

### Post by Spartan.II.117 on 2007-08-16
yes, it's load balancing, when you have two cores running F@H it wont happen anymore. as for the install, i had a similar issue when i installed it on a dual processor server i had to run etc/init.d/foldingathome start each time i started the computer.

---

### Post by freebeer on 2007-08-16
Thanks for the confirmation on the load balancing.

Had to start it manually, eh?  Bummer.  I don't do much in the way of rebooting... I just let 'em run.  I guess I'll have to play around a bit more to see how to get that second one configured and running.  I like the idea of it just running at start-up (otherwise I'll forget to restart them, or won't be here post-power interuption to get them going again).

---

### Post by Spartan.II.117 on 2007-08-16
i never did any research into it myself, it was a server and it ran 24/7, so it was not a big deal/

---

### Post by brandonlw on 2007-09-12
Hey folks, I am new to the whole Ubuntu/Linux world. My brother wants me to learn more about it so I threw it on a spare machine here at work. I wanted to get into the FAH stuff because I have extra machines sitting around, so I figured why not. Sure I could go the easy route and leave Windows on them but I hate not being able to figure something out. 

Followed the posted instructions and was simple enough until I got the LOG at the bottom.  (NOTE ... I originally joined the Ubuntu team but after trying it 10 different times I stopped entering it in :) )

We are behind a firewall here at work but I know that isnt the problem because we have Windows machines running FAH, unless I am just blind to something obvious.  So .. where should I start troubleshooting? I found one related topic on google but it did not help me at all


--- Opening Log file [September 12 13:48:44] 


# Linux Console Edition #######################################################
###############################################################################

                       Folding@Home Client Version 5.02

                          [http://folding.stanford.edu](http://folding.stanford.edu)

###############################################################################
###############################################################################

Launch directory: /home/administrator/fah_install
Executable: ./FAH502-Linux.exe


[13:48:44] - Ask before connecting: No
[13:48:44] - User name: brandonlw (Team 0)
[13:48:44] - User ID not found locally
[13:48:44] + Requesting User ID from server
[13:48:44] - Couldn't send HTTP request to server
[13:48:44]   (Got status 403)
[13:48:44] + Could not connect to Primary Assignment Server for ID
[13:48:44] - Couldn't send HTTP request to server
[13:48:44]   (Got status 403)
[13:48:44] + Could not connect to Secondary Assignment Server for ID
[13:48:44] 
+ Could not get ID from server. Retrying...

---

### Post by freebeer on 2007-09-13
Have you re-tried recently?  Sometimes their servers are down for maintenance. (The 403 error indicates another issue from what I've read about it, but I'm guessing it's just a maintenance thingy.)

---

### Post by glotz on 2007-09-13
In about [one month time](http://folding.extremeoverclocking.com/team_overtake.php?s=&t=45104)(?) we will enter top 100 folding@home teams. I want that on ubuntuforums.org frontpage when it happens. It would also be nice on ubuntu.com.

I'm no people person and I cannot make it happen however. Are you and can you? That's the challenge and your time frame is approx. 1 month.

Make it happen!

---

### Post by brandonlw on 2007-09-14
> **freebeer said:**
> Have you re-tried recently?  Sometimes their servers are down for maintenance. (The 403 error indicates another issue from what I've read about it, but I'm guessing it's just a maintenance thingy.)

Yep ... at least 4 or 5 times a day. And it retries 11 times on its own with a minute or so intervals. I have 2 other computers and my laptop (2 XP and 1 98 ) all on the same switch running FAH just fine. So I'm trying to figure out if there is some setting in Ubuntu that would need to be changed (Which wouldn't make sense).

---

### Post by Spartan.II.117 on 2007-09-15
brandon, how did you install f@h? if you did'nt already, i would recommend FAH_install from the wiki

---

### Post by Phalse on 2007-10-01
I just noticed that there is a version 6 of the SMP-x64 client.  I am having a problem getting this to run.  I have tried following the wiki but I still can't get it to go.  Could this be because I'm trying to run this from the live CD?

I'm trying to learn how to work with Ubuntu while doing this so this is the first time that I'm jumping into Linux.  I figured Ubuntu would be a great start :)

---

### Post by OfficeLinebacker on 2007-10-01
I think you have to pass a new switch to the client, -smp.  So for example if the CLIENT OPTS used to be '-forceasm -verbosity 9' they would become '-foceasm -verbosity 9 -smp'

Seemed to work for me after a few go rounds.

---

### Post by ant2ne on 2007-10-05
From Webbrowser> Firefox can't find the file at /opt/foldingathome/1/unitinfo.txt.

```
antsvr@antubuntu:/opt/foldingathome/1$ ls /opt/foldingathome/1
client.cfg  FAH502-Linux.exe  machinedependent.dat  MyFolding.html
```

Also: I have a windows machine that sits idle most of the time. Where is the how to install on XP that?

---

### Post by glotz on 2007-10-05
I think you have to finnish one unit for the file to appear. Here's how to setup any windoze box [http://folding.stanford.edu/](http://folding.stanford.edu/)

---

### Post by ant2ne on 2007-10-05
> **glotz said:**
> I think you have to finnish one unit for the file to appear. Here's how to setup any windoze box [http://folding.stanford.edu/](http://folding.stanford.edu/)So, how do i verify that it is running at all?

---

### Post by glotz on 2007-10-05
:) Thats a good question! Just wait a few days and the file should be there. Maybe someone else knows better.

---

### Post by chewearn on 2007-10-06
Actually, I don't think that is correct.  unitinfo.txt should appear as soon as your unit is downloaded and started folding.

For example, here is the unitinfo.txt currently on my system:
```
Current Work Unit
-----------------
Name: p2566_BBA5_ext
Download time: October 6 15:19:46
Due time: December 27 15:19:46
Progress: 3%  [__________]
```
To check if it is running, look also for the file FAHlog.txt (in the same directory), which is a log of the folding progress and various messages.  Also, check your CPU usage; you should have process FahCore_xx.exe (xx depends on the unit being worked on; e.g. FahCore_79.exe) taking up almost 100% CPU.

---

### Post by glotz on 2007-10-07
AstalaVista is that your first unit ever? That's what I meant.

---

### Post by ant2ne on 2007-10-07
> **AstalaVista said:**
> Actually, I don't think that is correct.  unitinfo.txt should appear as soon as your unit is downloaded and started folding.

For example, here is the unitinfo.txt currently on my system:
```
Current Work Unit
-----------------
Name: p2566_BBA5_ext
Download time: October 6 15:19:46
Due time: December 27 15:19:46
Progress: 3%  [__________]
```
To check if it is running, look also for the file FAHlog.txt (in the same directory), which is a log of the folding progress and various messages.  Also, check your CPU usage; you should have process FahCore_xx.exe (xx depends on the unit being worked on; e.g. FahCore_79.exe) taking up almost 100% CPU.Crap it isn't running then. I wonder what I'm doing (did) wrong!

---

### Post by chewearn on 2007-10-07
> **glotz said:**
> AstalaVista is that your first unit ever? That's what I meant.

Alright, that's not my first unit.
But I have set-up F@H in a couple of machines, and unitinfo.txt always appeared as soon as folding started.

---

### Post by chewearn on 2007-10-07
> **ant2ne said:**
> Crap it isn't running then. I wonder what I'm doing (did) wrong!

You didn't say how you set-up your F@H.  If you give more info, maybe we can help.

Actually, I now prefer the simplest method; simply put the FAH504-Linux.exe into a subdirectory of home; e.g. ~/FAH/
Then run FAH504-Linux.exe from terminal.

On one machine, I have a dual core; then I simply have two subdirectories, FAH1 and FAH2; and again, run FAH504-Linux.exe directly in each subdirectories.

This method can also be applied to running F@H in Windows.  The only downside, you cannot close the terminal window.

---

### Post by jpkotta on 2007-10-07
> **AstalaVista said:**
> The only downside, you cannot close the terminal window.

You do not need to keep the term open! 
[http://ubuntuforums.org/showpost.php?p=2985303&postcount=295](http://ubuntuforums.org/showpost.php?p=2985303&postcount=295)
I'm adding this to the wiki.

---

### Post by jpkotta on 2007-10-08
I've updated my fah_install script.  Get it in the wiki ([https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)).  It adds the 6.00(beta1) client.  You should be able to update everything by running the following commands:

```
sudo /etc/init.d/foldingathome stop
sudo tar zcvf fahbck.tar.gz /opt/foldingathome 
sudo ./install.sh install
sudo /etc/init.d/foldingathome start
```

You will want to make sure you allow the installer to update the /etc/default/foldingathome file, since the 6.00(beta1) client needs an extra option for SMP work units.

---

### Post by ant2ne on 2007-10-08
> **AstalaVista said:**
> You didn't say how you set-up your F@H.  If you give more info, maybe we can help.I used the install script mentioned on the first page of this thread. ```
sudo ./folding_install.sh install
```

---

### Post by Spartan.II.117 on 2007-10-09
you might want to try the script that jpcotta was talking about , it's very good. (ps thanks for updating it, my install quit about a week ago and i couldn't figure out why for awhile.)

---

### Post by evets on 2007-10-09
I've been folding for 2 years, come next month. I fold on 3 different teams.

So, first of all, thank you for your contributions, and this neato tut on setting up FAH on Ubuntu! 

Secondly, I was hoping there would be a team Ubuntu, and now that I know there is, I'll be folding for "Humanity" pretty soon, as well. I am just waiting on some parts to finish rebuilding my wife's winbox, then I can take my old Dapper box back, and load up FAH using your tut.

Thanks again!

---

### Post by jpkotta on 2007-10-09
> **ant2ne said:**
> I used the install script mentioned on the first page of this thread. ```
sudo ./folding_install.sh install
```

DO NOT USE THAT SCRIPT!  Use the one in the wiki (link in my sig). The one on the first post is very old.

---

### Post by ant2ne on 2007-10-09
> **jpkotta said:**
> DO NOT USE THAT SCRIPT!  Use the one in the wiki (link in my sig). The one on the first post is very old.Maybe someone should edit the post then. ](*,)  


After using the wiki
```
antsvr@antubuntu:~$ top | grep Fah
 8789 antsvr    39  19 21516  12m 1172 R  100  1.4 133:26.62 FahCore_78.exe     
 8792 antsvr    39  19 21492  12m 1156 R   96  1.4 133:04.77 FahCore_78.exe   
```I'm now on the team! \\:D/ 

I still got no unitinfo.txt :sad:

---

### Post by Spartan.II.117 on 2007-10-09
have you restarted your computer? and what folder are you looking in for unitinfo? and which script did you use?

---

### Post by ant2ne on 2007-10-10
> **Spartan.II.117 said:**
> have you restarted your computer? and what folder are you looking in for unitinfo? and which script did you use?
> Firefox can't find the file at /opt/foldingathome/1/unitinfo.txt.

I used this script
[https://help.ubuntu.com/community/FoldingAtHome?action=AttachFile&do=get&target=fah_install-20071008.tar.gz](https://help.ubuntu.com/community/FoldingAtHome?action=AttachFile&do=get&target=fah_install-20071008.tar.gz)
From this site
[https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

---

### Post by markp1989 on 2007-10-10
i know this may sound realy stupid, but what is Folding@Home?

---

### Post by jpkotta on 2007-10-10
> **markp1989 said:**
> i know this may sound realy stupid, but what is Folding@Home?

It only sounds stupid because you didn't ask Google first.  If you have any questions after reading stuff from the homepage or whereever, we'll be happy to answer them.

---

### Post by mjwood0 on 2007-10-14
I tried running the fah_install script to complete the installation, but the script threw an error and exited.

```
I couldn't find the client executable.  If you have it already, please copy it to /opt/foldingathome/config/.
Do you want me to download it for you?

1) yes
2) no
Please pick a number: 1
--01:47:47--  http://folding.stanford.edu/release/FAH6.00beta1-Linux.tgz
           => `FAH6.00beta1-Linux.tgz'
Resolving folding.stanford.edu... 171.67.22.50
Connecting to folding.stanford.edu|171.67.22.50|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
01:47:47 ERROR 404: Not Found.

Downloading Folding@Home failed.

```

Looks like Stanford might have changed their path structure or something...

---

### Post by Spartan.II.117 on 2007-10-14
if you want to edit the script, it looks like it should point here: [http://www.stanford.edu/group/pandegroup/folding/release/FAH6.00beta1-Linux.tgz](http://www.stanford.edu/group/pandegroup/folding/release/FAH6.00beta1-Linux.tgz)

---

### Post by jpkotta on 2007-10-14
They changed the URL.  I updated the script in the wiki.

---

### Post by Spartan.II.117 on 2007-10-14
Thanks!

---

### Post by nitteo on 2007-10-30
Is the OP also for Ubuntu? I am trying to get F@H started in my rig.

---

### Post by Spartan.II.117 on 2007-10-30
yes, but you want to follow the link to the wiki on the first line, those instructions are up to date.

---

### Post by xhie on 2007-11-21
I get this when I try to run:

```
To start folding right now, run '/opt/foldingathome/foldingathome start'

lina@iLoveCandy:~/fah_install$ sudo /etc/init.d/foldingathome start
/etc/init.d/foldingathome: 23: [[: not found
/etc/init.d/foldingathome: 33: [[: not found
/etc/init.d/foldingathome: 147: [[: not found
/etc/init.d/foldingathome: 147: arith: syntax error: "++num"
```

The install went just fine, I tried twice with the same resault each time.

---

### Post by jpkotta on 2007-11-21
> **xhie said:**
> I get this when I try to run:

```
To start folding right now, run '/opt/foldingathome/foldingathome start'

lina@iLoveCandy:~/fah_install$ sudo /etc/init.d/foldingathome start
/etc/init.d/foldingathome: 23: [[: not found
/etc/init.d/foldingathome: 33: [[: not found
/etc/init.d/foldingathome: 147: [[: not found
/etc/init.d/foldingathome: 147: arith: syntax error: "++num"
```

The install went just fine, I tried twice with the same resault each time.

Read the first line of the first post of this thread: 
"This first post is outdated, please see: https://help.ubuntu.com/community/FoldingAtHome"

I PMed an admin to remove the attachment.

---

### Post by jpkotta on 2007-11-24
The first post of the thread is out of date, and ndhskp is not around AFAIK.  So I more or less copied it to [https://help.ubuntu.com/community/FoldingAtHome/Install](https://help.ubuntu.com/community/FoldingAtHome/Install).  Feel free to improve it.

---

### Post by Swmmrman on 2007-12-06
Been having a frustrating issue.  After a computer crash(Very literal variety), I had to reinstall ubuntu. then i tried to reinstall my folding at home.  However, It seems to install just fine.  But it never creates the FAHlog.txt file.  And never seems to run.  when i run and sudo /etc/init.d/foldingathome status.  Says the client is running And the FAHlog.txt isnt there.  However, upon checks(After reading this entire post) The processes are not running.  And it can easily uninstalled as if its not running.  I get no increase in processor usage.  Issuing the start command results in it saying the client started.  But nothing changes.

I have noticed during install it claims the foldingathome group and user were created.  However after several checks threw groups and users.  No such group exists.  When uninstalling it says it cant delete the user/group cause it doesnt exists. I have even gone to the lenghts of created the user and grp prior to install and no go.

Im running Ubuntu 7.10 Gutsy.  Trying to install the SMP client.  Have got the libs needed.  Installed Via Wiki instructions.  Using sudo. Not sure if any of this will affect anything.  I have webmin installed.  And also have installed a postfix server as well as a webserver.(and many other things Wow rocks on ubuntu)  I keep the firewall set to allow all.  

Sorry for the long post.  Just wanted to get all the information I have at once.  Any help would be appreciated.

---

### Post by jpkotta on 2007-12-06
Very strange.  Are you running a 64-bit system?  Can you post the output of the following commands?
```
sudo ls -lR /opt/foldingathome
cat /etc/default/foldingathome
grep -C 2 -E vvv /etc/init.d/foldingathome
```

---

### Post by Swmmrman on 2007-12-07
```
/opt/foldingathome:
total 20
drwxr-xr-x 2 foldingathome foldingathome 4096 2007-12-06 20:54 1
drwxr-xr-x 2 foldingathome foldingathome 4096 2007-12-06 20:54 config
-rw-r--r-- 1 root          root          6331 2007-12-06 20:54 README
-rwx---r-- 1 foldingathome foldingathome 1170 2007-12-06 20:53 reconfigure.sh

/opt/foldingathome/1:
total 336
-rwxr-xr-- 1 foldingathome foldingathome    151 2007-12-06 20:54 client.cfg
-r-xr-xr-x 1 foldingathome foldingathome 252100 2007-12-06 20:54 fah6
-rw-r--r-- 1 foldingathome foldingathome      8 2007-12-06 20:54 machinedependent.dat
-r-xr-xr-x 1 foldingathome foldingathome  68492 2007-12-06 20:54 mpiexec
-rw-r--r-- 1 foldingathome foldingathome   1502 2007-12-06 20:54 MyFolding.html

/opt/foldingathome/config:
total 344
-rw-r--r-- 1 root          root            1097 2007-12-06 20:54 client1.options
-rwxr-xr-- 1 foldingathome foldingathome    151 2007-12-06 20:54 client.cfg
-r-xr-xr-x 1 foldingathome foldingathome 252100 2007-12-06 20:53 fah6
-rw-r--r-- 1 foldingathome foldingathome    870 2007-12-06 20:54 FAHlog.txt
-rw-r--r-- 1 foldingathome foldingathome      8 2007-12-06 20:54 machinedependent.dat
-r-xr-xr-x 1 foldingathome foldingathome  68492 2007-12-06 20:53 mpiexec
-rw-r--r-- 1 foldingathome foldingathome   1502 2007-12-06 20:54 MyFolding.html
stephan@sillymonkey:~$ 

```

```
$ cat /etc/default/foldingathome
# Folding@Home Linux client system default options.

# This file contains system-wide options for Folding@Home.  They are applied to
# all clients, whether in /opt/foldingathome or a user's $HOME directory.  They
# can be overridden on a per-client basis by using
# $folding_dir/config/client<num>.options.

# This file is simply a shell script that is sourced by the foldingathome init
# script.  Everything after a '#' is ignored.

# Use the CLIENT_OPTS variable to set any options that you want the client to
# use.  Run the client executable with the help option (e.g. "FAH504-Linux.exe
# -help") to learn what options are available.
# Example: CLIENT_OPTS='-advmethods -forceasm'

# IMPORTANT NOTE TO SMP USERS:
# As of version 6.00(beta1), you must add the "-smp" option to get SMP work units!

CLIENT_OPTS='-smp'

```
```

~$ grep -C 2 -E vvv /etc/init.d/foldingathome
. /lib/lsb/init-functions

# vvv these variables are modified by the install script vvv
fah_dir=/opt/foldingathome
executable=fah6

```

yes im running 64 bit ubuntu.  And yes its a 64 system.

---

### Post by Swmmrman on 2007-12-07
On my last install attempt i checked the logs.  It did infact successfully create and delete the user/group foldingathome.  I also confirmed via webmin that while it was installed,  The group was there and so was the user.  However same fail message.  An interesting note.  on another computer with a fresh install of ubuntu(I borked it).  It is doing the exact same thing.

On a bright note.  It is installing and runing under wine..  Albeit slowly.(2 frames per min vrs 30 sec)  At least i can still fold.

Btw have any of you had experince with fully setup compiz(The settings manager installed and cube going) And multi monitors(Somehow my settings borked it other computer badly)
When i got the second monitor connected.  It locked and killed tfter reboot i could log in however i could not get ful xserver.  All i had was a tan background(no background set) even under other sesions.

---

### Post by jpkotta on 2007-12-07
> **Swmmrman said:**
> On my last install attempt i checked the logs.  It did infact successfully create and delete the user/group foldingathome.  I also confirmed via webmin that while it was installed,  The group was there and so was the user.  However same fail message.  An interesting note.  on another computer with a fresh install of ubuntu(I borked it).  It is doing the exact same thing.

On a bright note.  It is installing and runing under wine..  Albeit slowly.(2 frames per min vrs 30 sec)  At least i can still fold.


All of your files look OK; it looks like the client hasn't been run except for the configuration mode, but we knew that.  Try running the client manually, and post the output:

```
 sudo su --shell /bin/sh --command "cd /opt/foldingathome/1/ ; ./fah6 -smp" -- foldingathome

```

> **Swmmrman said:**
> 
Btw have any of you had experince with fully setup compiz(The settings manager installed and cube going) And multi monitors(Somehow my settings borked it other computer badly)
When i got the second monitor connected.  It locked and killed tfter reboot i could log in however i could not get ful xserver.  All i had was a tan background(no background set) even under other sesions.

This is off topic here.  If you want to discuss further, you should make a new thread.  

I will say that I got it working on dual monitors in Xfce.  I got the dual screen set up through nvidia-settings (twinview).  Then I got compiz working, and I don't remember anything special I had to do to make it work with 2 screens.  Followed this guide: [http://ubuntuforums.org/showthread.php?t=623752](http://ubuntuforums.org/showthread.php?t=623752).

---

### Post by Swmmrman on 2007-12-08
ok intersting thing,  Says the cleint only supports 64bit systems.... I know for a fact that this is 64 bit...
```
Note: Please read the license agreement (fah6 -license). Further 
use of this software requires that you have read and accepted this agreement.

This client only supports 64-bit linux machines.  Your machine was detected as ''.

```

---

### Post by Swmmrman on 2007-12-08
Ok on second check... Some how the 64 bit installer i have installed 32 bit os,,,,guess ill have to redownload/redo my install/live CD.  How do i verify my install of ubuntu is 64 bit.

---

### Post by Swmmrman on 2007-12-08
My good man i must thank you for helping me find my error.  I had grabed my 32 bit ubuntu CD instead of the 64 bit.  I will label them to prevent further issues.(Though i will still try to find interesting ones)

Status = Happily folding

---

### Post by jpkotta on 2007-12-08
You can always check what arch you're using with the command
```
uname -m
```
or 
```
uname -a
```

---

### Post by kpictjl on 2007-12-10
I installed F@H using the installation script folding.sh as directed on this [howto]("https://help.ubuntu.com/community/FoldingAtHome/Install").

However after I try to add my own user name and team name the MyFolding.html still shows Anonymous and None?  I tried to change to my name/team using this...
```
sudo ./folding.sh --rename
```

The client.cfg file DOES show my new user name and team, but it doesn't seem to be taking.  I have this running fine on 3 other machines.

By they way, how can we contact  Christer Edwards?  It looks like the wiki I listed above needs updating...  It doesn't have the folding.sh script.  Or am I doing it wrong.

Thanks.

---

### Post by glotz on 2007-12-11
The point of wikies is anybody can edit them. Feel free to.

I used the link in my signature to install F@H. Maybe give it a try.

---

### Post by kpictjl on 2007-12-11
After looking a little closer.

In this folder.../var/lib/folding/foldingathome/CPU1.
FAHlog.txt says F@H recognizes my User Name and Team number.
```
[04:01:44] - User name: kpictjl1 (Team 68208)
```
client.cfg has my User Name and Team Number.
```
[settings]
username=kpictjl1
team=68208

```
however, MyFolding.html, still shows Anonymous.
```
Your information
User name: Anonymous
Team number: 0
```

mmm...so why doesn't MyFolding.html get updated?  Mostly I'm not confident that this machines "work" will be reported correctly.

---

### Post by kpictjl on 2007-12-11
I filed my above issue as a bug [here]("https://bugs.launchpad.net/folding/+bug/175460").

Christer will fix it in the next release, but my workaround is to delete Myfolding.htlm and then restart the service.

---

### Post by Swmmrman on 2007-12-13
Where can i find the protien think gui?  I thiought i found it in this thread,  But have had no luck locating it
Edit: NVM found it

---

### Post by Swmmrman on 2007-12-13
Ok found and installed protien think.  However..  All info is blank.  I know for a fact. that i have a unitinfo .txt anyone know why it would be blank.

---

### Post by jpkotta on 2007-12-17
The wiki pages were getting really cluttered with all the different install methods, so I made dedicate pages for each method and just links in the main page.

---

### Post by war59312 on 2008-01-12
```
[09:38:06] + Downloading new core: FahCore_81.exe
[09:38:07] + 10240 bytes downloaded
[09:38:07] + 20480 bytes downloaded
[09:38:07] + 30720 bytes downloaded
[09:38:07] + 40960 bytes downloaded
[09:38:07] + 51200 bytes downloaded
[09:38:07] + 61440 bytes downloaded
[09:38:07] + 71680 bytes downloaded
[09:38:07] + 81920 bytes downloaded
[09:38:07] + 92160 bytes downloaded
[09:38:07] + 102400 bytes downloaded
[09:38:07] + 112640 bytes downloaded
[09:38:07] + 122880 bytes downloaded
[09:38:07] + 133120 bytes downloaded
[09:38:07] + 143360 bytes downloaded
[09:38:07] + 153600 bytes downloaded
[09:38:07] + 163840 bytes downloaded
[09:38:07] + 174080 bytes downloaded
[09:38:07] + 184320 bytes downloaded
[09:38:07] + 194560 bytes downloaded
[09:38:07] + 204800 bytes downloaded
[09:38:07] + 215040 bytes downloaded
[09:38:07] + 225280 bytes downloaded
[09:38:07] + 235520 bytes downloaded
[09:38:08] + 245760 bytes downloaded
[09:38:08] + 256000 bytes downloaded
[09:38:08] + 266240 bytes downloaded
[09:38:08] + 276480 bytes downloaded
[09:38:08] + 286720 bytes downloaded
[09:38:08] + 296960 bytes downloaded
[09:38:08] + 307200 bytes downloaded
[09:38:08] + 317440 bytes downloaded
[09:38:08] + 327680 bytes downloaded
[09:38:08] + 337920 bytes downloaded
[09:38:08] + 348160 bytes downloaded
[09:38:08] + 358400 bytes downloaded
[09:38:08] + 368640 bytes downloaded
[09:38:08] + 378880 bytes downloaded
[09:38:08] + 389120 bytes downloaded
[09:38:08] + 399360 bytes downloaded
[09:38:08] + 409600 bytes downloaded
[09:38:08] + 419840 bytes downloaded
[09:38:08] + 430080 bytes downloaded
[09:38:08] + 440320 bytes downloaded
[09:38:08] + 450560 bytes downloaded
[09:38:08] + 460800 bytes downloaded
[09:38:08] + 471040 bytes downloaded
[09:38:08] + 481280 bytes downloaded
[09:38:08] + 491520 bytes downloaded
[09:38:08] + 501760 bytes downloaded
[09:38:08] + 512000 bytes downloaded
[09:38:08] + 522240 bytes downloaded
[09:38:08] + 532480 bytes downloaded
[09:38:08] + 542720 bytes downloaded
[09:38:08] + 552960 bytes downloaded
[09:38:08] + 563200 bytes downloaded
[09:38:08] + 573440 bytes downloaded
[09:38:08] + 583680 bytes downloaded
[09:38:08] + 593920 bytes downloaded
[09:38:08] + 604160 bytes downloaded
[09:38:08] + 614400 bytes downloaded
[09:38:08] + 624640 bytes downloaded
[09:38:08] + 634880 bytes downloaded
[09:38:08] + 645120 bytes downloaded
[09:38:08] + 655360 bytes downloaded
[09:38:08] + 665600 bytes downloaded
[09:38:08] + 675840 bytes downloaded
[09:38:08] + 686080 bytes downloaded
[09:38:08] + 696320 bytes downloaded
[09:38:08] + 706560 bytes downloaded
[09:38:09] + 716800 bytes downloaded
[09:38:09] + 727040 bytes downloaded
[09:38:09] + 737280 bytes downloaded
[09:38:09] + 747520 bytes downloaded
[09:38:09] + 757760 bytes downloaded
[09:38:09] + 768000 bytes downloaded
[09:38:09] + 778240 bytes downloaded
[09:38:09] + 788480 bytes downloaded
[09:38:09] + 798720 bytes downloaded
[09:38:09] + 808960 bytes downloaded
[09:38:09] + 819200 bytes downloaded
[09:38:09] + 829440 bytes downloaded
[09:38:09] + 839680 bytes downloaded
[09:38:09] + 849920 bytes downloaded
[09:38:09] + 860160 bytes downloaded
[09:38:09] + 870400 bytes downloaded
[09:38:09] + 880640 bytes downloaded
[09:38:09] + 890880 bytes downloaded
[09:38:09] + 901120 bytes downloaded
[09:38:09] + 911360 bytes downloaded
[09:38:09] + 921600 bytes downloaded
[09:38:09] + 931840 bytes downloaded
[09:38:09] + 942080 bytes downloaded
[09:38:09] + 952320 bytes downloaded
[09:38:09] + 962560 bytes downloaded
[09:38:09] + 972800 bytes downloaded
[09:38:09] + 983040 bytes downloaded
[09:38:09] + 993280 bytes downloaded
[09:38:09] + 1003520 bytes downloaded
[09:38:09] + 1013760 bytes downloaded
[09:38:09] + 1024000 bytes downloaded
[09:38:09] + 1034240 bytes downloaded
[09:38:09] + 1044480 bytes downloaded
[09:38:09] + 1054720 bytes downloaded
[09:38:09] + 1064960 bytes downloaded
[09:38:09] + 1075200 bytes downloaded
[09:38:09] + 1085440 bytes downloaded
[09:38:09] + 1095680 bytes downloaded
[09:38:09] + 1105920 bytes downloaded
[09:38:09] + 1116160 bytes downloaded
[09:38:09] + 1126400 bytes downloaded
[09:38:10] + 1136640 bytes downloaded
[09:38:10] + 1146880 bytes downloaded
[09:38:10] + 1157120 bytes downloaded
[09:38:10] + 1167360 bytes downloaded
[09:38:10] + 1177600 bytes downloaded
[09:38:10] + 1187840 bytes downloaded
[09:38:10] + 1198080 bytes downloaded
[09:38:10] + 1208320 bytes downloaded
[09:38:10] + 1218560 bytes downloaded
[09:38:10] + 1228800 bytes downloaded
[09:38:10] + 1239040 bytes downloaded
[09:38:10] + 1243183 bytes downloaded
[09:38:10] Verifying core Core_81.fah...
[09:38:10] Signature is VALID
[09:38:10] 
[09:38:10] Trying to unzip core FahCore_81.exe
[09:38:10] - Couldn't open file FahCore_81.exe 
[09:38:10] + Error: Could not extract core
[09:38:10] + Core download error (#8), waiting before retry...
```Sever Issue? :(

---

### Post by Spartan.II.117 on 2008-01-12
i dont know what methods it uses to extract the core, but that seems to be the problem as far as i can tell. did this just start(after having used F@H for awhile)? if not (new user/install), try re-installing

---

### Post by war59312 on 2008-01-12
OK deleted the .exe files and killed the process using system monitor and then started back up via sudo /etc/init.d/foldingathome start and what do you know, now its working fine. Really strange.

Yeah was a new install, newbie here... thanks anyhow... learning quick hehe...

---

### Post by Swmmrman on 2008-01-14
I had one of mine start doing that after fetching completing a unit.  Did that about 10 times. (Same core name too) Then deleted the core and moved on by itself.  My guess was it was a server with a bad work packet.

---

### Post by frbe0101 on 2008-02-12
Got it working on my laptop, now here a odd request, but is there a way to put in a script that stop it when the laptop is running on batteries?

---

### Post by jpkotta on 2008-02-12
Not odd at all.  See the second bullet of the first post of this thread.  It will tell you to go here: [https://help.ubuntu.com/community/FoldingAtHome#head-353ddb49ec5a97223b3e0f1be7d8a7acfab7f59e](https://help.ubuntu.com/community/FoldingAtHome#head-353ddb49ec5a97223b3e0f1be7d8a7acfab7f59e)

---

### Post by seeking_alpha on 2008-02-24
Is there a way to run protein_think aside from putting "python fahmain.py" in the terminal?

It's my 1st time running Linux, but I've been folding for almost a year. I just switched my 2 PS3s running 24/7 to Team Ubuntu:) They cut through WUs like a hot knife through butter

Thanks in advance

---

### Post by Spartan.II.117 on 2008-02-24
jpcotta:
could FAH install be updated for 6.00 beta 2?
also i believe you could create a deb if you could configure your script into a makefile. these would be awesome.

Spartan

---

### Post by jpkotta on 2008-02-25
I updated it a couple of days after the previous beta expired.  

I didn't want to use a Makefile, because then people would need to install make, which AFAIK is not installed by default.  I believe you only need a tarball and a few scripts for a deb, but I've never gone into the details.  In any event, I like Christer Edwards's script, which just uses finstall.  It just doesn't do the SMPs right yet.  As soon as it does (and I haven't tried since the beta expired), I'll probably just use that.

---

### Post by Spartan.II.117 on 2008-02-25
it isn't working properly for me, i had to get the new beta off the site and run it manually. also the make script was for creating a .deb, i should have specified, but a channel from stanford with auto-updatable .debs would have been awesome.

---

### Post by jpkotta on 2008-02-25
> **seeking_alpha said:**
> Is there a way to run protein_think aside from putting "python fahmain.py" in the terminal?

It's my 1st time running Linux, but I've been folding for almost a year. I just switched my 2 PS3s running 24/7 to Team Ubuntu:) They cut through WUs like a hot knife through butter

Thanks in advance
This might help.
[https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup)

---

### Post by jpkotta on 2008-02-25
> **Spartan.II.117 said:**
> it isn't working properly for me, i had to get the new beta off the site and run it manually. also the make script was for creating a .deb, i should have specified, but a channel from stanford with auto-updatable .debs would have been awesome.

I just retested it and it works for me.  What exactly goes wrong?  BTW, you need to uninstall and reinstall, I don't think update will do it for you.  Perhaps "update" is poorly named; it doesn't update everything, it only updates the scripts that I wrote.  This is because if you update the client, I just assumed that the WUs would not be compatible, and you'd have to start over anyway.

---

### Post by Spartan.II.117 on 2008-03-05
i figured it out: the scripts did update, and i got the client from stanford but forgot to change the user on it. everything works now.i just wish i could get all the SPARC's around campus working on it.

---

### Post by jpkotta on 2008-05-03
A new beta client is out, which means the old one is expiring soon.  

[http://folding.stanford.edu/English/Download](http://folding.stanford.edu/English/Download)
[https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

---

### Post by Spartan.II.117 on 2008-05-04
I tried installing with the new script, but when i go to start it it shows failed and my processor usage does nothing.

---

### Post by jpkotta on 2008-05-04
You mean that the installation appeared to be successful, but when you run ```
sudo /etc/init.d/foldingathome start
``` it fails?

Try replacing /etc/init.d/foldingathome with the attached script.  It should print out some error messages.

---

### Post by Spartan.II.117 on 2008-05-05
well, the new script starts it fine. and based on the noise of my computer last night, i think it was succeeding but reporting failure.

---

### Post by jpkotta on 2008-05-05
Good.  All that's different is that I removed the --quiet option from start-stop-daemon.  The client always takes a few seconds to actually get up and running, up to several minutes if it has to up/download work units.

---

### Post by jpkotta on 2008-05-24
I just updated to Hardy on some of my machines.  It seems like the Linux process scheduler is really weird.  F@H is niced to 19, yet it seems like the scheduler is giving it more time than other processes.  This, in turn, screws up frequency scaling.  I'm still looking into this problem; I haven't seen any good workarounds.

---

### Post by Spartan.II.117 on 2008-05-24
is this 64bit or 32 bit or both? i have noticed no such issues on my 64bit system.

---

### Post by jpkotta on 2008-05-26
It's both, but was more noticable on my 32-bit machine because it's a laptop (cpufreq scaling) and it is a single core.  Anyway, I found the problem: the new CFS process scheduler in the kernel.  The scheduler tries to give groups of processes their "fair share" of cpu time.  Apparently, the way of grouping processes is by UID.  Since I run F@H as it's own user (I really think this is the correct thing to do), it was basically getting half the CPU time, and my processes were getting the other half.  There is a mechanism for tuning the share of CPU time each UID gets, in /sys/kernel/uids/$UID/cpu_share.  Apparently the default is for everyone to get 1024 "units", I set foldingathome to get 16 and it works much better.  

<rant>
I'm questioning the wisdom of adding the CFS to a desktop distribution, or at least this particular policy.  When I'm on a desktop computer, *I'm* the one who's running programs; background jobs should have a low priority.  CFS is probably great for servers, but I'm not convinced of its utility for desktops.
</rant>

Edit: Apparently, this is already getting fixed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226)

Edit:
The fix is to add
```
deb http://mirror.cs.umn.edu/ubuntu/ hardy-proposed main restricted
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-proposed main restricted

``` (use your favorite mirror or us.archive.ubuntu.com instead of umn) and install the correctly configured kernel with ```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude install linux-generic
```

---

### Post by KAdams4458 on 2008-06-14
Well, I'm a little baffled. I've been tinkering with getting the client installed and running through out the day, and I'm hitting a wall. Maybe one of you could point me in the right direction, because I'm stumped.

My system is single-core 64-bit. I can successfully install everything, apparently, but nothing ever shows up in the system monitor. Hmmm. Look at this:

```
To start folding right now, run `sudo /etc/init.d/foldingathome start`.


user@Vera:~/fah_install$ sudo /etc/init.d/foldingathome start
 * Starting Folding@Home client 1                                        [ OK ] 
```

Looks normal, right? After seeing nothing happening, I decide to try this:

```
user@Vera:~/fah_install$ sudo /etc/init.d/foldingathome stop
[sudo] password for user: 
 * Stopping Folding@Home client 1                                        [fail] 
user@Vera:~/fah_install$ 

```

Okay, so now I'm confused. It says it starts, but never really does, since it never appears in the system moniotor, and stopping it fails. For that matter, everything fails except the start command. After dinking around with this and getting no where for the better part of a day, I decided I better ask around, since someone else may all ready know exactly what to do. I've lost enough hair today, and I'd rather keep the rest of it for as long as I can. :)

---

### Post by freebeer on 2008-06-14
I don't really know... I'm not familiar with system monitor.  I wonder if it only monitors non-root processes? *shrug*

It looks to me that it's running.  Have a look at your unitinfo.txt file... you said you let it run for a while?  If it's running for a while, you should see some progress.  Also, after you run the start command, can you check the processes with top or htop?  You should see it there.

---

### Post by KAdams4458 on 2008-06-15
> **freebeer said:**
> I don't really know... I'm not familiar with system monitor.  I wonder if it only monitors non-root processes? *shrug*

It looks to me that it's running.  Have a look at your unitinfo.txt file... you said you let it run for a while?  If it's running for a while, you should see some progress.  Also, after you run the start command, can you check the processes with top or htop?  You should see it there.

It doesn't show up in top, either. I just checked the unitinfo.txt, and after supposedly running for over 24 hours, it still has not been created. Something is definitely not right, and I can't seem to figure out what that something could be.

---

### Post by freebeer on 2008-06-15
hmm... I'm not sure.  With top and no progress on unitinfo.txt, I'd have to conclude that it's definitely not running.

Have a look at your FAHlog.txt file.  Maybe there's a clue as to what the problem might be.

---

### Post by frbe0101 on 2008-06-19
I been able to make turn on and turn off buttons for folding@home, how do I tell it (in terminal) to run on just one core instead of two cores?

---

### Post by jpkotta on 2008-06-19
> **frbe0101 said:**
> I been able to make turn on and turn off buttons for folding@home, how do I tell it (in terminal) to run on just one core instead of two cores?

How did you install it?  Do you want to make this configurable or just permanently disable one of the cores?

If you're using the SMP client (64-bit) you can't make it use only 1 core.

---

### Post by DeaconBlues on 2008-06-22
Is there a way to get Folding@Home using your GPU instead of CPU?

It says in the following link that only Windows is supported at the moment:

[http://folding.stanford.edu/English/FAQ-NVIDIA#ntoc8]("http://folding.stanford.edu/English/FAQ-NVIDIA#ntoc8")

I read somewhere you get much faster calculations using the GPU.

---

### Post by jpkotta on 2008-06-23
> **DeaconBlues said:**
> Is there a way to get Folding@Home using your GPU instead of CPU?

It says in the following link that only Windows is supported at the moment:

[http://folding.stanford.edu/English/FAQ-NVIDIA#ntoc8]("http://folding.stanford.edu/English/FAQ-NVIDIA#ntoc8")

I read somewhere you get much faster calculations using the GPU.

That's the official FAQ, and if it says Windows only, then you need Windows.  I doubt any virtualization solution will work either, since that would still use the Linux driver.  It sucks because GPUs do indeed calculate faster (there is a trade off: the things they can calculate are limited), and it appears that the effort to make a Linux version isn't worth it to F@H.

---

### Post by mptpro on 2008-07-03
Anyone think they'll release a simple installer (I do miss that days of Windows .exe).

Or least put it in the repositories (or the add/remove), and have it show up inthe "Applications" menu, AND have a grpahical client.

I installed F@H on two ubunut boxes and four winxp machines.  The first time I did it with ubunut took me over and over, the second machine took about 10 minutes.  

Windows took about 3 minutes.

And the windows has a graphical interface so I can see that it is working.

I know I can do all these things with command line, but to firgure it out the first time is a pain.

sorry for the rant.

---

### Post by glotz on 2008-07-04
It's a good rant but on wrong forum.

---

### Post by jpkotta on 2008-07-04
Christer Edwards is working on a .deb and getting it in the repos.  [https://help.ubuntu.com/community/FoldingAtHome/origami](https://help.ubuntu.com/community/FoldingAtHome/origami)

As far as graphical client goes, try the Windows one in wine maybe?  The console one is better anyway, because it runs all the time, even when no one is logged in (in both Windows and Linux).

---

### Post by DogDragonsm31 on 2008-08-13
I'm still new to ubuntu and still trying to get a the flow of things,
but I'm not giving up on it. It's on my main rig and I can get 
from it and into the other 2 machines to put files or get files.
But I haven't been able to get F@H on my main rig.
I keep messing up some where, So is there a place I can like
get spoon fed on how to do it.
A friend told me to get "Beginning Ubuntu Linux- From Novice 
to Professional".
Which I did, just got it. But I like to fold while I'm reading
it.

---

### Post by jpkotta on 2008-08-13
[https://help.ubuntu.com/community/FoldingAtHome/origami](https://help.ubuntu.com/community/FoldingAtHome/origami)

It doesn't get much more automatic than that.  There are other methods too, see the main page at [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome).

---

### Post by glotz on 2008-08-13
Been to the f@h link in jpkottas signature above?

---

### Post by DogDragonsm31 on 2008-08-13
> **glotz said:**
> Been to the f@h link in jpkottas signature above?

no but will check out that you said thanks

---

### Post by spudgunner on 2008-10-08
So I've managed to to folding install... I have and Instal Core2 Duo, but it only detected one core. I'm looking for a way to install another single core client beside the one I already have, but with a differnet machine number (so it uses a differnet core). I tried running the install.sh, but it says a client is already installed and will only accept 'reinstall' and 'uninstall'.

So how do you pull off running two single core clients at the same time?

Thanks,

Josh

---

### Post by jpkotta on 2008-10-09
I assume you're using the script from [https://help.ubuntu.com/community/FoldingAtHome/fah_install](https://help.ubuntu.com/community/FoldingAtHome/fah_install).  In that case, it tells you how many cores it detected, but in case it's wrong, you can specify the actual number.  You must uninstall and then install.  "update" is not what you're looking for (see the wiki page above).  Also, if you are running a 64-bit OS, you should only run one client.

---

### Post by spudgunner on 2008-10-10
Therein lies my problem... it never gave me an option as to how many cores I have, and I installed the 32-bit client, so it should have. I have no idea what to do.

---

### Post by jpkotta on 2008-10-16
spudgunner, try the new script in the wiki.

---

### Post by WelterPelter on 2009-01-19
For anyone running Protein Think.
 I just finished a new release of Protein Think (0.0.5-a) that addresses the couple of problems people were encountering. My ability to test the application is limited, however, so if you run into any problems with it, please let me know.

Get it [here]("http://sourceforge.net/project/showfiles.php?group_id=164311").

This release fixes:

- Difficulty reading new unitinfo.txt files
- Difficulty in which program would fail if certain data was not available. Now it will continue running, even without this non-critical data

Enjoy!

PS - If anyone happens to be folding on a multicore machine, you could help me by copying folders 1 and 2 and sending them to me. I want to upgrade PT to handle multiple cores, but don't have access to one. Thanks.

---

### Post by alpha754293 on 2009-01-25
I'm trying to install F@H on 8.04 server and when I try to start fah, it says: "No such file or directory."

I'm currently using (or trying to use) the F@H Linux SMP 6.23 beta R1 client.

```
# ls
fah6 mpiexec
# ./fah6
bash: ./fah6: No such file or directory
#
```

Help? Please?

*edit*
n/m. Got it.

For Ubuntu 8.04 Server AMD64, you need to run

```

$ sudo apt-get install ia32-libs

```

in order for it to run properly.

---

### Post by bbarcelo on 2009-02-19
I have had F@H installed for the last several weeks or so and installed it using the finstall method listed in the Ubuntu wiki documentation. However, I found that even after several weeks, so statistics were being sent to the F@H site. This caused me to question whether any data was being sent. I decided to remove F@H and try re-installing using a different method.

I downloaded origami through aptitude and looked up the proper command to install it (sudo origami install etc..) but I receive the following error:

###############################################
#    the root user shell must be /bin/bash    #
###############################################

However, I'm 99% sure my shell is bash but to check I performed the following:
$sudo -i
#ps -p $$
which yields:
 PID TTY          TIME CMD
 2129 pts/0    00:00:00 bash

I've tried everything I can find via Google and searching the Ubuntu forums for related issues didn't help much. I hope someone in this thread can help out. Thank you.

---

### Post by jpkotta on 2009-02-19
The heavy-handed workaround is to link /bin/sh to /bin/bash:
```
sudo ln -s /bin/bash /bin/sh
```

---

### Post by bbarcelo on 2009-02-19
> **jpkotta said:**
> The heavy-handed workaround is to link /bin/sh to /bin/bash:
```
sudo ln -s /bin/bash /bin/sh
```

Heavy-handed is oft a word accompanied by trouble down the line. What makes this approach unfavorable? Is there any other approach that might solve the problem with a bit more.. finesse?

---

### Post by jpkotta on 2009-02-19
It really shouldn't cause any problems.  Bash syntax is supposed to be a superset of Bourne shell syntax.  A few releases ago, Ubuntu made Dash the default /bin/sh, which broke a lot of things that assumed that /bin/sh was actually Bash.  The converse or this is false - anything that works for Dash should work for Bash.

The proper fix would be to either make root's shell bash (which it appears to be already), or to fix whatever is spitting out the warning.  

To be sure that bash is actually root's shell, check
```
cat /etc/passwd | grep root
```

It should look something like this:
```
root:x:0:0:root:/root:/bin/bash
```

I would ask origami's author about it: [https://bugs.launchpad.net/origami](https://bugs.launchpad.net/origami)

---

### Post by bbarcelo on 2009-02-19
> **jpkotta said:**
> It really shouldn't cause any problems.  Bash syntax is supposed to be a superset of Bourne shell syntax.  A few releases ago, Ubuntu made Dash the default /bin/sh, which broke a lot of things that assumed that /bin/sh was actually Bash.  The converse or this is false - anything that works for Dash should work for Bash.

The proper fix would be to either make root's shell bash (which it appears to be already), or to fix whatever is spitting out the warning.  

To be sure that bash is actually root's shell, check
```
cat /etc/passwd | grep root
```

It should look something like this:
```
root:x:0:0:root:/root:/bin/bash
```

I would ask origami's author about it: [https://bugs.launchpad.net/origami](https://bugs.launchpad.net/origami)

I ran the command you listed in your reply and got this:
```
root:x:0:0:root:/root:bash
```

I will ask the author as well, but could it be that if I change the line above the look like this:
```
root:x:0:0:root:/root:/bin/bash
```
..that I won't break anything and perhaps satisfy the origami installer?

edit #1:
I decided to go and test my theory and sudo -i works without any warning, so bash is being called correctly I assume (unless a system restart is required to institute the changes I made in /etc/passwd). Origami's installer finished but the startup script failed to start. This is an problem related to my processor though so I'll work on sorting that out next.

---

### Post by jpkotta on 2009-02-19
> **bbarcelo said:**
> I ran the command you listed in your reply and got this:
```
root:x:0:0:root:/root:bash
```

I will ask the author as well, but could it be that if I change the line above the look like this:
```
root:x:0:0:root:/root:/bin/bash
```
..that I won't break anything and perhaps satisfy the origami installer?

Yes.  It should always be an absolute path anyway, for security reasons.  I believe the proper way to do it is with
```
sudo usermod --shell /bin/bash root
```

---

### Post by bbarcelo on 2009-02-19
Well, origami has apparently installed successfully but when I run sudo origami start, the following happens:
```

Starting up FAH client(s) on 1 processor(s):
Starting FAH client at CPU1...
FAH client #1 startup: OK 


Starting of FAH client(s): FAILURE

```
I'd love to read the log file or something on this but I haven't found it ... yet. I'm starting to think maybe origami is more trouble than its worth and to just download the client off their site.

---

### Post by paintandswim09 on 2009-04-05
(Sorry for the thread jack, I couldn't find a better place for this, and I didn't think it was worth its own thread)

I'm running F@H on a dual-core laptop that gets used by the whole family, and we typically log out when we're done, so there's a fair amount of time that the laptop spends sitting around, with only the screen turned off, with nobody logged in. Since F@H technically runs as a process of its own user (that _is_ right, correct?) is it still running when no humans are logged in?

BTW ranked #472 on TeamUbuntu, top 15% F@H wide

---

### Post by jpkotta on 2009-04-05
paintandswim09:

This is more or less the official F@H help thread for Ubuntu.  You're not off topic.

It depends on how you installed it.  If you used one of the scripts from the wiki, then it should be running when no one is logged in.  You can check by running top or another process monitor and seeing how long the F@H processes have been running when you first log in.

---

### Post by sweetbrett on 2009-04-08
i modified the install.sh to download the newer 6.24beta smp client

---

### Post by frbe0101 on 2009-05-06
How do I remove folding@home from the startup script? I still would like to run it but no longer want it to run automatically on startup.

---

### Post by jpkotta on 2009-05-06
Assuming the init script is called "foldingathome",
```
sudo update-rc.d -f foldingathome remove
```
You could also use something like sysvconfig.

---

### Post by mag00 on 2009-05-08
Why all my FAHCORE_A2.exe processes are using least than 10% of CPU each one?

I am using the 6.24 SMP client in a Q6600 with 4gb of RAM and Jaunty 9.04.

This is my config.cfg contents
```
[settings]
username=mag00
team=53066
passkey=
asknet=no
bigpackets=big
machineid=10
local=104

[http]
active=no
host=localhost
port=8080

[core]
checkpoint=30

[clienttype]
type=3

```

This is a piece of FAHLOG.txt
```
mag00@Q6600:~/folding$ ./start 

Note: Please read the license agreement (fah6 -license). Further 
use of this software requires that you have read and accepted this agreement.

Using local directory for work files
4 cores detected


--- Opening Log file [May 6 16:53:26 UTC] 


# Linux SMP Console Edition ###################################################
###############################################################################

                       Folding@Home Client Version 6.24beta

                          http://folding.stanford.edu

###############################################################################
###############################################################################

Launch directory: /home/mag00/folding
Executable: ./fah6
Arguments: -local -advmethods -smp 4 -verbosity 9 

[16:53:26] - Ask before connecting: No
[16:53:26] - User name: mag00 (Team 53066)
[16:53:26] - User ID: 76F696CD7D7F0A23
[16:53:26] - Machine ID: 10
[16:53:26] 
[16:53:26] Loaded queue successfully.
[16:53:26] Unit 9's deadline (May 6 00:43) has passed.
[16:53:42] - Warning: Could not delete all work unit files (9): Core file absent
[16:53:42] - Preparing to get new work unit...
[16:53:42] - Autosending finished units... [May 6 16:53:42 UTC]
[16:53:42] Trying to send all finished work units
[16:53:42] + No unsent completed units remaining.
[16:53:42] - Autosend completed
[16:53:42] + Attempting to get work packet
[16:53:42] - Will indicate memory of 3899 MB
[16:53:42] - Connecting to assignment server
[16:53:42] Connecting to http://assign.stanford.edu:8080/
[16:53:44] Posted data.
[16:53:44] Initial: 40AB; - Successful: assigned to (171.64.65.56).
[16:53:44] + News From Folding@Home: Welcome to Folding@Home
[16:53:44] Loaded queue successfully.
[16:53:44] Connecting to http://171.64.65.56:8080/
[16:53:50] Posted data.
[16:53:50] Initial: 0000; - Receiving payload (expected size: 4830945)
[16:54:04] - Downloaded at ~336 kB/s
[16:54:04] - Averaged speed for that direction ~295 kB/s
[16:54:04] + Received work.
[16:54:04] + Closed connections
[16:54:04] 
[16:54:04] + Processing work unit
[16:54:04] Core required: FahCore_a2.exe
[16:54:04] Core found.
[16:54:04] Working on queue slot 00 [May 6 16:54:04 UTC]
[16:54:04] + Working ...
[16:54:04] - Calling './mpiexec -np 4 -host 127.0.0.1 ./FahCore_a2.exe -dir work/ -suffix 00 -checkpoint 30 -verbose -lifeline 14264 -version 624'

[16:54:04] 
[16:54:04] *------------------------------*
[16:54:04] Folding@Home Gromacs SMP Core
[16:54:04] Version 2.07 (Sun Apr 19 14:51:09 PDT 2009)
[16:54:04] 
[16:54:04] Preparing to commence simulation
[16:54:04] - Ensuring status. Please wait.
[16:54:14] - Looking at optimizations...
[16:54:14] - Working with standard loops on this execution.
[16:54:14] - Files status OK
[16:54:15] - Expanded 4830433 -> 23973957 (decompressed 496.3 percent)
[16:54:15] Called DecompressByteArray: compressed_data_size=4830433 data_size=23973957, decompressed_data_size=23973957 diff=0
[16:54:15] - Digital signature verified
[16:54:15] 
[16:54:15] Project: 2669 (Run 14, Clone 60, Gen 29)
[16:54:15] 
[16:54:15] Entering M.D.
NNODES=4, MYRANK=3, HOSTNAME=Q6600
NNODES=4, MYRANK=0, HOSTNAME=Q6600
NNODES=4, MYRANK=1, HOSTNAME=Q6600
NNODES=4, MYRANK=2, HOSTNAME=Q6600
NODEID=0 argc=20
NODEID=1 argc=20
NODEID=2 argc=20
NODEID=3 argc=20
                         :-)  G  R  O  M  A  C  S  (-:

                   Groningen Machine for Chemical Simulation

                 :-)  VERSION 4.0.99_development_20090307  (-:


      Written by David van der Spoel, Erik Lindahl, Berk Hess, and others.
       Copyright (c) 1991-2000, University of Groningen, The Netherlands.
             Copyright (c) 2001-2008, The GROMACS development team,
            check out http://www.gromacs.org for more information.


                                :-)  mdrun  (-:

Reading file work/wudata_00.tpr, VERSION 3.3.99_development_20070618 (single precision)
Note: tpx file_version 48, software version 64

NOTE: The tpr file used for this simulation is in an old format, for less memory usage and possibly more performance create a new tpr file with an up to date version of grompp

Making 1D domain decomposition 1 x 1 x 4
starting mdrun '22848 system'
7500000 steps,  15000.0 ps (continuing from step 7250000,  14500.0 ps).

```

A few months ago everything was fine and the 4 processes was using 25% each one.

Any ideas?

[]'s

---

### Post by jpkotta on 2009-05-09
> **mag00 said:**
> 
Any ideas?

Not really.  Nothing looks weird in your logs.  Although I don't think you need the -local option on Unix, and I'm not sure if -smp takes an arguement.

You could try the official forum [http://foldingforum.org/](http://foldingforum.org/).  You could also try purging F@H from your system and reinstalling.

---

### Post by swoody on 2009-07-02
Hello everybody! I just wanted to throw out a reminder to everyone here, as well as anyone who may stumble upon this looking for help. The Ubuntu Folding@Home Team does have it's own IRC channel!! It's up and running strong again, and hopefully it can be a great resource for those looking for help getting F@H setup, or troubleshooting any issues you may be having. If nothing else, come hang out and we can shoot the breeze and talk about folding!

So come on by, and check us out on #ubuntu-folding on the FreeNode network! We look forward to seeing you guys there!!

---

### Post by YannBuntu on 2009-09-25
Hi all,
looks like the wiki ( [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome) ) is not up-to-date (see ppa for origami for example... ), can someone update it please?

Which of the install methods you think is the easiest one for a "standard install": laptop with one CPU on Ubuntu 9.04, and i would like to have the possibility to start/stop F@H via a button or command line. If possible i would like also to control which % of the CPU is used by F@H.

thanks in advance for your answers!

---

### Post by swoody on 2009-09-25
> **YannBuntu said:**
> Hi all,
looks like the wiki ( [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome) ) is not up-to-date (see ppa for origami for example... ), can someone update it please?

Which of the install methods you think is the easiest one for a "standard install": laptop with one CPU on Ubuntu 9.04, and i would like to have the possibility to start/stop F@H via a button or command line. If possible i would like also to control which % of the CPU is used by F@H.

thanks in advance for your answers!

Well, you're in luck...

I *just* got done updating quite a bit on the [Origami Wiki page]("https://help.ubuntu.com/community/FoldingAtHome/origami") so feel free to check it out. I haven't gotten to the main Folding@Home wiki page yet, but I'll work to get it caught up a bit.

As far as which method would be easiest to use, stable, and easy to monitor... that would of course have to be origami :) It's also what I run on my single-core, 9.04 laptop, so if you ever have any issues/questions I may be able to lend some advice.

It takes two commands to install, one command to check your progress, and can be stopped/started by a simple command as well. All of the info you could need is on the wiki page I linked. However, origami has it's own wiki if you'd like to check it out as well:
[http://origami.zelut.org/doku.php](http://origami.zelut.org/doku.php)

As far as having the F@H client only use a certain % of your CPU - I don't know of a way to do that currently. The way the client works is by using your 'spare' processing power. It has very low priority, so any programs, apps, etc. that you run will still receive all the CPU power that they want. Then, whatever power isn't being utilized will go to the F@H client. This way, you won't notice any system lag, lack of power, or any other ill-effects from the F@H client, but it also does as much folding as possible. Since it works this way, it will keep your CPU at 100% no matter what you're currently doing on your computer.

Welcome to the fold, YannBuntu ):P

---

### Post by YannBuntu on 2009-09-28
Thanks a lot, i will test it, and that will help me update the ubuntu-fr wiki too :)

Just a remark: here [https://help.ubuntu.com/community/FoldingAtHome/origami#Ubuntu%20PPA%20(.deb](https://help.ubuntu.com/community/FoldingAtHome/origami#Ubuntu%20PPA%20(.deb)) you should remove Dapper and Gutsy as ubuntu desktop is not supported any more for thoses versions. Also you could add Jaunty (and Karmic) if there are PPA..

---

### Post by jpkotta on 2009-09-28
> **YannBuntu said:**
> ...should remove Dapper and Gutsy as ubuntu desktop is not supported any more for thoses versions...

Dapper server is supported until June 1, 2011.  I think Gutsy is completely unsupported.

---

### Post by YannBuntu on 2009-09-28
**@all:** some questions:
  - with origami, how can I start/stop the folding process?  (i think it is possible with [the "finstall" F@H installer]("https://help.ubuntu.com/community/FoldingAtHome/finstall"))
  - how can I add/remove origami from the "applications that start at the beginning of my session"?
  - is it possible to limit the CPU used by origami ? (i don't want my laptop fan to be too noisy)

I think these informations should be in the wiki...

other question: is the [the "finstall" F@H installer]("https://help.ubuntu.com/community/FoldingAtHome/finstall") still working on Ubuntu 9.04 ? (last update of the wiki was in June 2008...)

**@jpkotta:** you are right! :)

---

### Post by swoody on 2009-09-28
> **YannBuntu said:**
> **@all:** some questions:
  - with origami, how can I start/stop the folding process?
```
sudo origami stop
```
and
```
sudo origami start
```

>   - how can I add/remove origami from the "applications that start at the beginning of my session"?
Origami auto-starts by itself on bootup. However, there has been a conflict between the usplash used in Jaunty and several programs which auto-start by default (origami being one of them). This is still being tested with 9.10, but it appears that this will no longer be an issue. For the time being, you can either run:
```
sudo origami start
```
to start origami after bootup, or disable usplash. There have been users who have reported that by removing usplash several of their programs that are set to auto-start worked as they should.

> - is it possible to limit the CPU used by origami ? (i don't want my laptop fan to be too noisy)
No, I don't believe there is. If there is something available to do this, it would be a third-party app, and I do not know of any offhand. If you have a multi-core CPU, you should be able to limit the program to only one core, and this would effectively reduce your CPU usage to 50% (on a dual-core).

> I think these informations should be in the wiki...
You raise a very good point here. I will make a note to include more info on how to stop/start origami, as well as a section for FAQ.

> other question: is the [the "finstall" F@H installer]("https://help.ubuntu.com/community/FoldingAtHome/finstall") still working on Ubuntu 9.04 ? (last update of the wiki was in June 2008...)
I believe it is still functional under Jaunty. I tried it out fairly recently, and I don't recall encountering any issues.

---

### Post by jpkotta on 2009-09-28
> **YannBuntu said:**
> 
  - is it possible to limit the CPU used by origami ? (i don't want my laptop fan to be too noisy)

Now that I think about it, there is a note in the wiki about this. [https://help.ubuntu.com/community/FoldingAtHome#cpulimit](https://help.ubuntu.com/community/FoldingAtHome#cpulimit) 

*However*, F@H should run at a low enough priority that it should not kick up the frequency of your CPU.  In my experience, even at 100% CPU usage, the fan is not needed at the lowest frequency.  You should verify that you have frequency scaling enabled, and that F@H is not kicking it up.

---

### Post by YannBuntu on 2009-09-28
Thanks a lot for your quick answers! :KS

---

