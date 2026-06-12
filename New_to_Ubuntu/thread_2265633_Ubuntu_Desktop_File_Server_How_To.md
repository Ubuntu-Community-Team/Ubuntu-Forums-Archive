---
title: "Ubuntu Desktop File Server How To"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by craig40 on 2015-02-16
I’d really like someone knowledgeable in Ubuntu land to check my work and explain if what I have done is OK.  I’ve spent well over 20 hours working on getting Ubuntu Desktop version 14.04 to work as a File Server for a Windows environment.  The amount of misinformation and improper “How Tos” on the Internet is amazing!  One just has to look at all the user comments on all the blogs and sites of “This doesn’t work!” “I hate Linux, it sucks!” and other rants to understand the frustration level out there.  This is probably due to whoever writes the how-to doesn’t do so with a fresh install of Ubuntu and doesn’t check their work.  I think I’ve got the answer on how to set it up, consistently.

   In my situation, it is a Windows environment in a Workgroup networking architecture and not a Domain/Active Directory architecture.  Authentication is an issue where I have 20 users that all access the same shares.  However, I have 2 of those users that also need access to one additional shared folder whereas the other 18 users cannot access.

   Now, before anyone goes on a bashing spree of “Why aren’t you using a Domain Environment?” or “You should be using User Groups to manage this!” or wait for it….”You need to use the Ubuntu Server Edition to do this, not the Desktop version!” Please let me explain:


[LIST]
[*]I’ve      been a Windows Admin for well over 15 years.  Please give me some type of GUI.  It’s not my fault.  Really!       Microsoft made me this way.       (Remember, the first step is admitting you have a problem. Ha!)  If I have a GUI of some kind for a      little bit this can make the transition easier instead of typing and      mistyping lines of code over and over.       Give me some training wheels for a little while here guys. 
[*]As far      as the Domain and Managing users, think about it this way:  I use one account called “companystaff”      so 18 users can have access to one shared folder.  We’ll call that folder “SHARE”.  The other 2 users can use the      “Administrator” account so that they can access another share called      “ADMINSHARE”.  This way I only have      2 user accounts I have to worry about.       In the realm of consulting that I work in for small business, the      KISS principle works best….Keep It Simple Stupid.  Granted, if I were managing over 100      users with different policies this would be totally different. 
[/LIST]
   
  So, here is what I’ve got below.  I can consistently get it to work in my testing lab over and over each time doing it from scratch. It took me quite a long while to figure this out as it seems a lot of the GUI stuff for Samba in Ubuntu doesn't work well at all for authentication purposes.  Works great for wide-open Shares across the network but once you start trying to lock stuff down....it simply doesn't work.  I’d appreciate if some experts could say “Do this or Don’t do that”.  Now, if you think I’m dead on accurate I’d really like to hear that but I’m sure I am not perfect and each time I repeat my steps I learn something new.  
   
  1.            **Install Ubuntu**.  

[LIST]
[*]I simply burned the 14.04.1 iso and installed it on a Core 2 Duo with a 128 SSD. 
[*]During the install I created a user called “administrator” as the main account with the Computer Name “SERVER” 
[/LIST]
   2.            Once up and running I **Open Terminal **and proceed to **type** in the following**:**

**sudo apt-get install gksu** *(then hit **Enter** and answer questions)*
**sudo apt-get update ***(then hit **Enter)***[B]
sudo apt-get install samba [/B]*(then hit **Enter** and answer questions)*
**sudo apt-get install libpam-smbpass *****[B](***[/B]*then hit **Enter**. still not 100% sure if I need this but think it’s for syncing smbpasswords with local user accounts in Ubuntu.)*
  
3.         **Create a folder in the Administrator’s Home Directory** with the name **SHARE**.
 
  4.         **Right click** on the **SHARE** folder and **click Properties**. Go to the **Permissions tab** and under the **Others Access** change it to **Create and delete files**.  Then **click** on [B]Close.
 [/B]
  5.         **Create another folder in the Administrator’s Home Directory** with the proper name **ADMINSHARE**.
 
  6.         **Right click** on the **ADMINSHARE** folder and **click Properties**. Go to the **Permissions tab** and under the **Others Access** change it to **Create and delete files**.  Then **click** on [B]Close.
 [/B]
  7.          **Open Terminal** (if it’s still not open) and proceed to **type** in the following below**:*** (It’s time to create some Samba users that will be able to access the shared folders.  Note, the companystaff account will not have a local Ubuntu user account.  Just a Samba account.  Am I correct on assuming that with the code below?)*

**sudo useradd -s /bin/true companystaff*** (then hit **Enter**)*
**sudo smbpasswd -a companystaff **(*then hit **Enter*** . *Put in a password when prompted*.)
**sudo smbpasswd -a administrator** (*then hit **Enter** . Put in the same password as the local Ubuntu account I created at the beginning of the install when prompted.  I have to do this with the main administrator account as well.  I thought installing libpam-smbpass syncs this stuff with Samba but that doesn’t seem to be the case.  I know I must be doing something wrong or am incorrect on my assumption.*)
**gksudo gedit /etc/samba/smb.conf ***(then hit **Enter.** In the next step we input what we need to share out.)*
  
8.         Once you put in the administrator password and the smb.conf file opens Scroll down to the bottom of the file and put all this in below: * (We are setting the file permissions so the companystaff account and the administrator account can have network access to the folders they should have access to.)*

[SHARE]
path = /home/administrator/SHARE
available = yes
valid users = administrator companystaff
read only = no
browsable = yes
public = yes
writable = yes

[ADMINSHARE]
path = /home/administrator/ADMINSHARE
available = yes
valid users = administrator
read only = no
browsable = yes
public = yes

  9.            **Save** the file and then **close** it.
 
  10.        **Open Terminal**.  *(if not still open. We need to restart Samba)*

Type:
**sudo restart smbd **(*then hit **Enter)***[B]
sudo restart nmbd [/B](*then hit **Enter)***
 
  11.        Try to access that share via a Windows machine and authenticate to see if it works.
   
  Again, after repeated steps and clearing the saved credentials via Windows 7 I can consistently authenticate to the correct folders with the correct permissions.  I can create and delete files.  It works again and again.  Just want to know if I am doing unneeded things OR if there are some gotchas that could happen later I am not forseeing.  

  Thanks to everyone for taking the time to read this post.  I’d really like to put this on my blog to help some other poor sap out like me so he doesn’t yell at the screen saying “Linux sucks!” due to all those bad how-to’s out there.  The more I learn, the more I like it.

---

### Post by TheFu on 2015-02-16
TL;DR ... all of it.

Linux is about flexibility. There is generally 50 different ways to solve most problems. All those how-tos - are different ways, for different situations. Some clearly do not apply to your needs or you don't have the background yet to understand what is being described. A beginning mechanic can't replace the water pump on day 1. It takes time to learn the lingo, gain the background, and build up the skills necessary to get there.

If you want a GUI to do admin things, you are missing 90% of the power in Linux.  Noobs (and we all where noobs sometime) have been complaining about the lack of a GUI for 30 yrs - you aren't gonna change it either, just like I didn't change it 25 yrs ago. Conform, learn the shell or get used to only 10% of server things being possible. 

Getting samba working by editing 1 file (about 10 lines are needed) and running 2 commands is really easy. Of course, that result may not fit your requirements and knowing exactly which lines and which commands is critical. I've had people refuse to believe that editing 1 file could do what they wanted - they completely refused to use a text editor. It was odd. They needed to be told EXACTLY WHAT TO TYPE. 

File and directory permissions are central to Unix/Linux system security.  It controls access for pretty much everything, so getting a full understanding is mandatory to be successful.

Finding random how-tos on the internet really isn't a good way to learn Linux, at least in the beginning.  Structured learning really is the best way.  Start at the beginning and work through a admin book - Ubuntu Server Guide isn't a bad place to start, but I fear it doesn't cover the basics of the shell/cli that every Linux admin needs to understand. 

sudo useradd -s /bin/true companystaff (then hit Enter) - doesn't do what you think it does. /etc/shells shows the list of valid shells. Anything else, is invalid - normally people use /bin/false to NOT have a shell for userids.\

There was a once-a-decade new samba release in the last year - so some things have changed drastically.  The best place I know to get instructions for samba is from the team who maintains it - samba.org. That is a common idea across F/LOSS tools.  Also, it is absolutely critical that you know which version of samba you are running, since things do change.

Please don't post this set of steps.  The insecure permissions settings alone are a reason NOT to.  Just because you got it to work, doesn't mean it is the best answer for anyone else or secure. You are adding to your own complaint about instructions on the internet.

---

### Post by craig40 on 2015-02-16
Wow there "TheFu",

You're pretty much the stereotypical "[Nick Burns, Your Company's Computer Guy.]("https://screen.yahoo.com/jimmy-fallon-snl-skits/nick-burns-companys-computer-guy-000000899.html")" MOOOVE!!!

I can certainly see why most Windows guys hate Linux guys.  Thanks for providing to that stereotype too.  Guess it's a members only club.

Hope this post wasn't too long to read for ya.

---

### Post by Adam_GUI on 2015-02-16
If you absolutely want a GUI, there's gadmin-samba available for 12.04 stable in the repositories.
[https://apps.ubuntu.com/cat/applications/precise/gadmin-samba/]("https://apps.ubuntu.com/cat/applications/precise/gadmin-samba/")

Trusty (14.04) Launchpad page.
[https://launchpad.net/ubuntu/trusty/+package/gadmin-samba]("https://launchpad.net/ubuntu/trusty/+package/gadmin-samba")

Should save you messing around in terminal for management options.

---

### Post by redmk2 on 2015-02-17
> **craig40 said:**
> Wow there "TheFu",

You're pretty much the stereotypical "[Nick Burns, Your Company's Computer Guy.]("https://screen.yahoo.com/jimmy-fallon-snl-skits/nick-burns-companys-computer-guy-000000899.html")" MOOOVE!!!

I can certainly see why most Windows guys hate Linux guys.  Thanks for providing to that stereotype too.  Guess it's a members only club.

Hope this post wasn't too long to read for ya.

Why would you think that your response to @TheFu's reply to your question " Am I correct?" was warranted?  Your approach to *the sharing scenario * is at best, amateurish.  Your experience as a " Windows Admin for well over 15 years" is really worth nothing if you don't understand the basic approach to managing file sharing in a multi-user system.  

When you got to the part about creating public shares in the /home file system branch you lost me.  Whether you use a GUI desktop or the command line you still have a responsibility to the network to create the shares in a public place that is secure.  Linux is a fast moving OS.  What is up to date today may not be so in 6 months.  Many of your commands are outdated.  They run the risk of not working in the near future.  There is not much thought to backwards compatibility with Linux.

Are you correct?  No.  Not in your configuration or in your response to someone who like @TheFu who took the time to answer *your* question.  You don't have to agree with his assessment, but that doesn't give you the right to reply is such an uncivilized manner.

---

### Post by TheFu on 2015-02-17
Didn't have time to help last night. 

> **craig40 said:**
> 
  1.            **Install Ubuntu**.  

[LIST]
[*]I simply burned the 14.04.1 iso and installed it on a Core 2 Duo with a 128 SSD. 
[*]During the install I created a user called &#8220;administrator&#8221; as the main account with the Computer Name &#8220;SERVER&#8221; 
[/LIST]
   2.            Once up and running I **Open Terminal **and proceed to **type** in the following**:**

**sudo apt-get install gksu** *(then hit **Enter** and answer questions)*
**sudo apt-get update ***(then hit **Enter)***[B]
sudo apt-get install samba [/B]*(then hit **Enter** and answer questions)*
**sudo apt-get install libpam-smbpass *****[B](***[/B]*then hit **Enter**. still not 100% sure if I need this but think it&#8217;s for syncing smbpasswords with local user accounts in Ubuntu.)*
  
3.         **Create a folder in the Administrator&#8217;s Home Directory** with the name **SHARE**.
 
  4.         **Right click** on the **SHARE** folder and **click Properties**. Go to the **Permissions tab** and under the **Others Access** change it to **Create and delete files**.  Then **click** on [B]Close.
 [/B]
  5.         **Create another folder in the Administrator&#8217;s Home Directory** with the proper name **ADMINSHARE**.
 
  6.         **Right click** on the **ADMINSHARE** folder and **click Properties**. Go to the **Permissions tab** and under the **Others Access** change it to **Create and delete files**.  Then **click** on [B]Close.
 [/B]
  7.          **Open Terminal** (if it&#8217;s still not open) and proceed to **type** in the following below**:*** (It&#8217;s time to create some Samba users that will be able to access the shared folders.  Note, the companystaff account will not have a local Ubuntu user account.  Just a Samba account.  Am I correct on assuming that with the code below?)*

**sudo useradd -s /bin/true companystaff*** (then hit **Enter**)*
**sudo smbpasswd -a companystaff **(*then hit **Enter*** . *Put in a password when prompted*.)
**sudo smbpasswd -a administrator** (*then hit **Enter** . Put in the same password as the local Ubuntu account I created at the beginning of the install when prompted.  I have to do this with the main administrator account as well.  I thought installing libpam-smbpass syncs this stuff with Samba but that doesn&#8217;t seem to be the case.  I know I must be doing something wrong or am incorrect on my assumption.*)
**gksudo gedit /etc/samba/smb.conf ***(then hit **Enter.** In the next step we input what we need to share out.)*
  
8.         Once you put in the administrator password and the smb.conf file opens Scroll down to the bottom of the file and put all this in below: * (We are setting the file permissions so the companystaff account and the administrator account can have network access to the folders they should have access to.)*

[SHARE]
path = /home/administrator/SHARE
available = yes
valid users = administrator companystaff
read only = no
browsable = yes
public = yes
writable = yes

[ADMINSHARE]
path = /home/administrator/ADMINSHARE
available = yes
valid users = administrator
read only = no
browsable = yes
public = yes

  9.            **Save** the file and then **close** it.
 
  10.        **Open Terminal**.  *(if not still open. We need to restart Samba)*

Type:
**sudo restart smbd **(*then hit **Enter)***[B]
sudo restart nmbd [/B](*then hit **Enter)***
 
  11.        Try to access that share via a Windows machine and authenticate to see if it works.
   
  Again, after repeated steps and clearing the saved credentials via Windows 7 I can consistently authenticate to the correct folders with the correct permissions.  I can create and delete files.  It works again and again.  Just want to know if I am doing unneeded things OR if there are some gotchas that could happen later I am not forseeing.  

  Thanks to everyone for taking the time to read this post.  I&#8217;d really like to put this on my blog to help some other poor sap out like me so he doesn&#8217;t yell at the screen saying &#8220;Linux sucks!&#8221; due to all those bad how-to&#8217;s out there.  The more I learn, the more I like it.

Long posts make it harder to suggest fixes. I am not a samba expert - just been using it for about 15 yrs. It is generally "setup and forget."

The install step didn't discuss partitioning, swap size. These are important decisions, IMHO. 
Best to name "server" - all lowercase.  In theory, it shouldn't matter, but having mixed case may break some 5th party scripts. Unix is case sensitive and it is best to only use that when really needed.
administrator - seems long.  I'd use "deploy" or something shorter - personal preference. Good to stay lowercase here too.

1. 2 commands are needed after an install is completed, IMHO.  **sudo apt-get update && sudo apt-get dist-upgrade** These same commands should be run manually, every week, during an approved maintenance window. Usually just 5 minutes is needed, but sometimes larger changes could require an hour to research the update (usually a new config file). That doesn't happen often - maybe once every 2 yrs.  Of course daily, versioned, backups are mandatory for any corporate environment.

4-6. Allowing "other" to have access to a file system owned by the admin user is asking for security issues in the future.  "other" means anyone not in the group who gains access to the system. If the box is hacked, other is pretty much any account they used to get there. Not a fan of all uppercase directory names, personal preference. Again, case sensitive names matter.

7. useradd -s /bin/false is the normal way to not allow login for user accounts.  This may prevent password sync from working - I dunno. Changing the /etc/shells file may be necessary if any other Linux tools are desired. The real key is either the program is or is not in /etc/shells. What is actually specified does not matter after that.

smbpasswd adds userids to the samba mapping DB. Until that happens, userids on the Linux system are unknown to samba. After they are added there, password changes are synchronized automatically into the samba DB. OTOH, if users can't login and change their password, then those automatic password syncs aren't very useful. Changing user passwords occasionally is smart security. 

8. May want to modify some [Global] settings - the workgroup, security model, etc.
Generally, I prefer NOT to place shared storage under any HOME directory for a user.  That userid can cut off access accidentally by changing directory permissions or their umask. 
I believe the best practice is to place shared storage mounts outside the normal Unix directory structure in the root directory.  This prevents end-users from filling the file system up - which is always a bad thing.  Create a partition, mount it on /data (for example), set the ownership/group as needed, then below that point create the 2 shares you want.  
The public share - if the intent is for anyone on the network to have access - I'd just use a guest account (guest ok = yes). 
You may want to set the **create mask** for files and **directory mask** so permissions on those are reasonable.
For administrative shares, I'd use a **valid users = @group** to have individual logins, but allow anyone in the correct admin group access using their own userid credentials.
I've never used the "available = yes" setting. Interesting.

9. It might be good to let end-users have personal storage on the samba server too.  This way you can get them to store really important files on a server, which will allow for 1-stop backups to be made.  [homes] is a special section just for this purpose and maps to a userid's $HOME directory and credentials automatically. This is very powerful and can save CALs for _that other OS_. If you do allow home directory access, then having a separate /home partition (or whatever you decide to name it) is absolutely critical. Don't want end-users filling up / or /var - "it will be bad" is an understatement.

Might be good to limit the subnets (or specific NICs) which can access these shares. Sometimes people are a little too open with their networking and accidentally allow shared folders over the internet.

There are 50-500 different ways to solve this problem and the version of samba being used matters. Definitely need to include the version in any post so people know what the target is.  Having the Ubuntu version is good.  Things change over time.

Have you looked at all-in-one smallbiz Linux distros?  Zentyal or ClearOS for example? I haven't looked at either recently, but they used to have a fairly simple webpage management interface for the sorts of things many small businesses wanted.  Ubuntu Server is closer to the old-school ways of Unix administration with the normal steep learning curve.

Anyway - perhaps this post is more to your liking?  [http://dilbert.com/strip/1995-06-24](http://dilbert.com/strip/1995-06-24) is more like my reality.

---

### Post by mastablasta on 2015-02-17
> **craig40 said:**
> 
[LIST]
[*]I’ve      been a Windows Admin for well over 15 years.  Please give me some type of GUI.  It’s not my fault.  Really!       Microsoft made me this way.       (Remember, the first step is admitting you have a problem. Ha!)  If I have a GUI of some kind for a      little bit this can make the transition easier instead of typing and      mistyping lines of code over and over.       Give me some training wheels for a little while here guys.
[/LIST]
.
I think you might want to look at Zentyal server GUI.

there are many GUI for Linux available.

you have the kind of gui for simple operations (like file manager GUIs) or for home server stuff (like open media vault), more complex ones (webmin), light ones (ajenti), easy to use (nethserver), business server like guis (ClearOS, Zentyal). 

I started with GUI but I find it I am using it less and less and more and more I use terminal.

---

### Post by craig40 on 2015-02-17
Adam_GUI, Thanks for those links! Really looking forward to testing that out.  Saw some comments on your link to gadmin-samba and looked really positive.  While I do want to learn move about the terminal this could be a nice ease in transition.
   
  Redmk2, “uncivilized manner” really dude?  When “TheFu” starts off with “TL;DR….all of it”,  that is civilized?  I guess it’s OK for you Linux/Unix pros to talk down to others but when someone steps up to a little bullying….well that’s just uncivilized.
   
  TheFu, sorry we got off on the wrong foot.  You could be like a million other Americans snowed in due to Octavia or maybe it was just a bad day at work.  Nevertheless, your second post was awesome and way more thorough than I would have ever expected.  Thank you for that.  I’d love to ask some questions or make some comments to what you posted back but don’t want to stir ya up there Mr. Scruffy Beard (nice comic!). * (insert scarcasm font here) I’ll wait on your approval*.  In all seriousness I know that took a long time to type out and I do appreciate it.
   
  mastablasta, just did some quick Googling on Zentyal server.  Looks like that along with gadmin-samba is definitely the direction I want to take.  Just need to pick the path in the fork.  Like you I am hoping to get my feet wet first and then do some snorkeling in the terminal.  Thank you!

---

### Post by JeQhdMD on 2015-02-17
In your situation, it generally makes sense to invest in a solid and comprehensive Linux book such as:  

[http://www.amazon.com/Practical-Guide-Ubuntu-Linux-4th/dp/0133927318/ref=sr_1_23?ie=UTF8&qid=1424197317&sr=8-23&keywords=ubuntu+books](http://www.amazon.com/Practical-Guide-Ubuntu-Linux-4th/dp/0133927318/ref=sr_1_23?ie=UTF8&qid=1424197317&sr=8-23&keywords=ubuntu+books)

---

### Post by Morbius1 on 2015-02-17
>  **sudo apt-get install libpam-smbpass *****[B](***[/B]*then hit **Enter**. still not 100% sure if I need this but think it&#8217;s for syncing smbpasswords with local user accounts in Ubuntu.)*
libpam-smbpass automatically makes the "smbpasswd" match the user's local login password at every reboot. I actually find it quite annoying but the way the rest of your howto flows it's completely unnecessary.

Ignore the recommendation about gadmin-samba. It's an abomination and if advice is to be given it's to Ubuntu / Debian: Remove it from the repository like you did with webmin.

---

### Post by TheFu on 2015-02-17
> **craig40 said:**
>   Redmk2, “uncivilized manner” really dude?  When “TheFu” starts off with “TL;DR….all of it”,  that is civilized?  I guess it’s OK for you Linux/Unix pros to talk down to others but when someone steps up to a little bullying….well that’s just uncivilized.

Rereading that comment, I see now that there are 2 ways it can be read.
a) What I should have said was ... *there are many details in the post that I didn't read carefully so my response is general, not specific. I only skimmed it and may have missed some important things.*
b) It could easily have been interpreted as ... "I didn't read anything because it was too long."

The internet interpretation and poor wording got the better of me.

If there wasn't a threat to post it to a blog, I wouldn't have responded at all - bab1 and others are better at samba stuff than I.

---

### Post by mastablasta on 2015-02-18
> **craig40 said:**
>    
  mastablasta, just did some quick Googling on Zentyal server.  Looks like that along with gadmin-samba is definitely the direction I want to take.  Just need to pick the path in the fork.  Like you I am hoping to get my feet wet first and then do some snorkeling in the terminal.  Thank you!


if this is for business then Zentyal business edition would definitely be worth paying for. I only tested it for home use and I didn't like it as it was too much aimed towards business. I didn't need many things it provided yet it didn't have some I wanted. install was super easy. I used "expert" install mode and then installed only web GUI (there is no need for a desktop on server - default option installs it). the GUI then guides you though setting up various things. or you can just select a whole package - e.g. webserver, email server etc. anyway the community version - you will have to do some more testing on your own before upgrading etc.

ClearOS works in similar way. I like that one as well. it is CentOS (RedHat) based, but very easy to handle, with many plugins available. some need to be payed for, but price is not high.

---

### Post by craig40 on 2015-02-19
Finally got some time to reply to several of TheFu's helpful insights.  Yes, it's long.  If it's too much to read no biggie.  Again, hopefully some other poor sap like me finds this and gets a little insight.

>  TheFu;The install step didn't discuss partitioning, swap size. These are important decisions, IMHO.

Completely agree. Normally on this type of small Server setup I use an SSD for the OS and something simple like a 1 TB HD for the Data. I plan on doing this and storing the data on the 1 TB but first want to get the initial setup of Ubuntu and Samba down.

>  TheFu;Best to name "server" - all lowercase. In theory, it shouldn't matter, but having mixed case may break some 5th party scripts. Unix is case sensitive and it is best to only use that when really needed.

Been a DD-WRT and OpenWRT user for years. Learned that whole uppercase/lowercase thing the hard way. I agree, I'll change things to lowercase.

>  TheFu;administrator - seems long. I'd use "deploy" or something shorter - personal preference. Good to stay lowercase here too.

Yeah, I'd really like to use "admin" but you know where that will lead ;)

>  TheFu; 1. 2 commands are needed after an install is completed, IMHO. **sudo apt-get update && sudo apt-get dist-upgrade** These same commands should be run manually, every week, during an approved maintenance window. Usually just 5 minutes is needed, but sometimes larger changes could require an hour to research the update (usually a new config file). That doesn't happen often - maybe once every 2 yrs. Of course daily, versioned, backups are mandatory for any corporate environment.

Afraid of course with my limited knowledge of Linux that running an update will break something that I can't fix quickly. Understand the risks there and involved. Also, in my area of business (small to medium size organizations) the "corporate mindset" is really not practical at all. Large Corporations are like enormous ocean liners that can't stop or start quickly. But they can carry a lot of equipment and people. Small to Medium sized businesses are like small speed boats that can quickly move in and around. Of course they carry just a few people with not a lot of weight. I worked for large corps for years, been self-employed for over 10 years. I'm never going back…meetings to talk about having meetings, the horror.


>  TheFu;7. useradd -s /bin/false is the normal way to not allow login for user accounts. This may prevent password sync from working - I dunno. Changing the /etc/shells file may be necessary if any other Linux tools are desired. The real key is either the program is or is not in /etc/shells. What is actually specified does not matter after that.

I don't know about this stuff either. But I sure as heck plan on testing your "false" recommendation.

>  TheFu: smbpasswd adds userids to the samba mapping DB. Until that happens, userids on the Linux system are unknown to samba. After they are added there, password changes are synchronized automatically into the samba DB. OTOH, if users can't login and change their password, then those automatic password syncs aren't very useful. Changing user passwords occasionally is smart security. 

Got the mapping part. So is it the libpam-smbpass that's handling that syncing or something else?

>  TheFu; 8. May want to modify some [Global] settings - the workgroup, security model, etc.

Yeah. I saw that a lot in my research and will add that but for me the whole "Windows Network Discovery" is not really a big deal. I'll just find it via \\server or \\IP. Almost always a mapped drive is made to those needed shares. It is a good idea to add that info though.

>  TheFu; 4-6. Allowing "other" to have access to a file system owned by the admin user is asking for security issues in the future. "other" means anyone not in the group who gains access to the system. If the box is hacked, other is pretty much any account they used to get there. Not a fan of all uppercase directory names, personal preference. Again, case sensitive names matter.

I totally get what your saying but if I have two users “administrator” and “adminstaff” that have passwords and authenticate to the system would that not cover it? As far as getting “hacked” goes would that be physically at the box or via some type of network attack? If someone is physically at that Server that shouldn’t be…wouldn't you have bigger problems that them hacking? I'd just pick the box up and walk out.

>  TheFu; Generally, I prefer NOT to place shared storage under any HOME directory for a user. That userid can cut off access accidentally by changing directory permissions or their umask. I believe the best practice is to place shared storage mounts outside the normal Unix directory structure in the root directory. This prevents end-users from filling the file system up - which is always a bad thing. Create a partition, mount it on /data (for example), set the ownership/group as needed, then below that point create the 2 shares you want. 

Got it! Glad you cleared that up. I thought the same exact thing when I saw other tutorials stating to put Shared Folders in the Home directory of the user because permissions are easier to manage. I've later found that with my instructions I can put those Shares anywhere. Again, another bad how-to. I'll plan on doing that now I know that there is no really good reason for what I was doing before.

>  TheFu; The public share - if the intent is for anyone on the network to have access - I'd just use a guest account (guest ok = yes). 

I've made that mistake before. Someone outside the org brings in a laptop, plugs it into the network, pulls and IP and a little snooping around with some arp and ip scanning tools; you’ve got a problem. They can see those public folders too but my understanding would be that without a username and password the contents aren’t accessible.

>  TheFu; You may want to set the **create mask** for files and **directory mask** so permissions on those are reasonable.

Don't know what that stuff is yet but thanks for giving me something to search on.

>  TheFu; For administrative shares, I'd use a **valid users = @group** to have individual logins, but allow anyone in the correct admin group access using their own userid credentials.

Understand your point. But if I’ve only got two or three “admin” users it seems like 6 one way and half a dozen the other. If I had 10 different admin users, that would be a real pain to add every one. Guess I’m thinking about things in more of a small business model.

>  TheFu; I've never used the "available = yes" setting. Interesting.

Pulled it from the web. It's now interesting to me....because it's interesting to you. Haven't tested it yet but I assume it would mean that when hitting the Server you would "see" the shared folder.  Of course not to be confused with accessing it as that's based on permissions.  If it was "available = no" maybe it means it's hidden and you would have to know the direct path to get to it....like putting a $ at the end of a Windows share.  Don't know and still need to test it.

>  TheFu; 9. It might be good to let end-users have personal storage on the samba server too. This way you can get them to store really important files on a server, which will allow for 1-stop backups to be made. [homes] is a special section just for this purpose and maps to a userid's $HOME directory and credentials automatically. This is very powerful and can save CALs for _that other OS_. If you do allow home directory access, then having a separate /home partition (or whatever you decide to name it) is absolutely critical. Don't want end-users filling up / or /var - "it will be bad" is an understatement.

That's a preference thing and I don't want other users' files something I have to worry about. Especially when it's a crap tons of music and pics that are in no way relevant to the small business...unless of course it's the owner who signs the checks ;)

>  TheFu; Might be good to limit the subnets (or specific NICs) which can access these shares. Sometimes people are a little too open with their networking and accidentally allow shared folders over the internet.

I'll keep that one in mind. The Servers I usually setup for File Servers have no routing of sorts going through them. Is this something that I do need to be concerned about?

>  TheFu; There are 50-500 different ways to solve this problem and the version of samba being used matters. Definitely need to include the version in any post so people know what the target is. Having the Ubuntu version is good. Things change over time.

I'll definitely make note of versions! That could have a lot to do with all those how-tos on the net that don't work.

>  TheFu; Have you looked at all-in-one smallbiz Linux distros? Zentyal or ClearOS for example? I haven't looked at either recently, but they used to have a fairly simple webpage management interface for the sorts of things many small businesses wanted. Ubuntu Server is closer to the old-school ways of Unix administration with the normal steep learning curve.

I have just now started to look at these and assume all are managed via a web console. I was just really hoping to start working with a Linux File Server and hobbling along with a GUI until I got a lot more familiar with the Terminal.  I started a similar way with DD-WRT and OpenWRT.  Now, 90% of the complicated things I do with those firmwares is done through commands and not the GUI.  The GUI help me get started.

---

### Post by Morbius1 on 2015-02-19
From "apt-cache show libpam-smbpass" :
> Description-en: pluggable authentication module for Samba
 [COLOR=#0000cd]This is a module for PAM that enables a system administrator to migrate
 user passwords from the Unix password database to the SMB password
 database as used by Samba, and to subsequently keep the two databases in
 sync.[/COLOR]  Unlike other solutions, it does this without needing users to log
 in to Samba using cleartext passwords, or requiring them to change their
 existing passwords.
It does exactly what it says.

Let's say my username is morbius and my login password to the system is morbiuspw. Let's say I add morbius to the samba password database with a password of morbiussmb because I don't want the two to match thank you very much. To access a samba share I enter my username with morbiussmb as the password and everything works as designed.

Now I reboot the box for some reason. I try to access the share again and access is denied. Why? Because libpam-smbpass changed the samba password from morbiussmb to morbiuspw.

If you want it to do that and the user has a local login password or if you want the two passwords to always match then keep libpam-smbpass. I remove it if it got installed by mistake. Usually after a considerable amount of time trying to figure out why I can't log into my samba share anymore. ;)

---

### Post by craig40 on 2015-02-19
Thank you Morbius1. Got it! That's what I thought just wanted to double check. The suspense though is killing me, why don't you want the two to match?

---

### Post by Morbius1 on 2015-02-19
Consider for a moment that morbius isn't the administrator of the box but just a regular samba client user.

If for some reason I set morbius up with a login password and a home directory and all the other trimmings and then have the two passwords match morbius not only has access to the samba shares but to the actual physical server itself.

If I set up a client user with local login capabilities I will make his local login password the same as mine so I can as the Administrator of the box log into his account locally and really mess up his day after an argument. Then I will set up the samba password to be whatever the client wants it to be.

---

### Post by craig40 on 2015-02-19
*Ding! Ding! Ding! Ding!  We have a winner!  Bob, tell him what he's won! * Makes COMPLETE and TOTAL sense!  Great reason.  Thanks for taking the time to address such a noob question.  *Ahhh, Gee Wally, what's wrong with givin' Eddie Haskel a local login account?*;)

One thing I did notice though in my testing.  When I use **sudo useradd -s /bin/true ** to create a user I can use that users credentials to hit the Share (after of course the **sudo smbpasswd -a**).  However, while I see that username in the Ubuntu GUI for logging in, I can't.  When trying to log in to his account with the password it doesn't work, which is a good thing, right?  So...not trying not to be real picky here....but wouldn't that contradict the argument against using **libpam-smbpass.  **Again, you know a heck of a lot more than I do on about this.

In other news, I tried out Adam_GUI's suggestion about gadmin-samba. I tried to take a shortcut and just install the latest version on 14.04 just to check it out.  (Yeah, I know, bad idea.) Getting a lot of errors and I think I know why.  It was the same stuff where when trying to create a Samba user you get errors.  I now know it has something to do with that user not already existing as a local user.  Same issues as I was having in the beginning following all those how-to's on restricting file access.  If I had started with gadmin-samba my frustration level may have been higher.  I get what you're saying about the "abomination"....a little harsh, but I get it.  Still Adam_GUI I appreciate the suggestion. 

Thanks Morbius1!

---

### Post by Morbius1 on 2015-02-19
sudo useradd -s /bin/true creates a local user without local login capability and without a home directory that is why my first post said that the way your HowTo flowed libpam-smbpass is unnecessary. Keep it remove it it makes no difference.

As for my beloved gadmin-samba if you were to install it and run it just once get out of it and run:
```
testparm -s
```
You will see something like this ( I won't post the whole thing because it will scare people ):
> Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "null passwords" option is deprecated
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Notice all the "this parameter is deprecated:, "ignoring that parameter", and "unknown parameter" mesages?

*** gadmin-samba produces an incoherent mess.
*** no one in this forum will help you if you ask for help and post it.
*** It was state of the art when Eisenhower was battling the Nazi's in Europe.
*** It has in my opinion always been an ironic piece of software.

It's target is someone who already knows what the hell he's doing yet that person is unlikely to use something like this opting for a text editor instead.

---

### Post by craig40 on 2015-02-19
Morbius1, dude, you are freakin' hilarious!  Thank you for the how-to on getting rid of it.  I'll do that to get some practice. Nevertheless, for my testing to work each and every time I restore an image from scratch and then test again just to make sure there are no gremlins.  If and when I do post this stuff I want to know that it will work each and every time because of good testing.

Tried to send you a PM on something but you don't accept them. "sudo useradd -s /bin/true companystaff (then hit Enter) - doesn't do what you think it does."  Hmmm...it seems to work as I would expect, where did I get this from?....I know I got it from all my research I did....Found it! On a post you made back on April 23rd, 2011.  Thank you again Morbius1.

---

