---
title: "HOWTO: Parental control. Now with GUI too!"
date: 2006-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by nanomad on 2006-07-31
**[COLOR="Red"] THIS THREAD IS OUTDATED, PLEASE SEE [http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510) FOR THE CURRENT VERSION OF THE SOFTWARE [/COLOR] **


Here is a simple (but powerful) install script for a parental control feature
It is based on tinyproxy + firehol + dansguardian and on an howto found on this forum (dunno remeber where)

Download the attached archive, extract it and run the script (2x click or from a terminal) (There are a couple of hidden files and folder too in the archive)

It will d/l, install and configure all you need + install a GUI created by me to configure everything (it is located under System --> Administration)

Please report any bugs.

---

### Post by cre8ivgil on 2006-07-31
> **nanomad said:**
> Here is a simple (but powerful) install script for a parental control feature
It is based on tinyproxy + firehol + dansguardian and on an howto found on this forum (dunno remeber where)

Download the attached archive, extract it and run the script (2x click or from a terminal) (There are a couple of hidden files and folder too in the archive)

It will d/l, install and configure all you need + install a GUI created by me to configure everything (it is located under System --> Administration)

Please report any bugs.


Thanks Nanomad, myself and a lot of other people have been waiting for this for awhile. Hats off to you!

---

### Post by encompass on 2006-08-01
I agree... keep up the good work... we need this if we want a family desktop computer.

---

### Post by tonhou on 2006-08-01
Hi,

I tried the script and it appeared to run giving GUI feedback on the steps - asking for password, changing repositories, installing packages, changing configurations, installing gambas - unfortunately at the end nothing had changed, no packages had been installed.

I ran it a second time after manually adding the repositories needed and it installed tinyproxy, firehol, and dansguardian ok but not sure about gambas - not sure why gambas is needed? It then seemed to complete after changing configuration files. But still not functional

Oh, there was another problem for me didn't offer my language - English for DG.

It is a nice idea, but at the moment I think there may need to be some manual intervention to sort out the issues - on going back to apt-get (command line) it had not gracefully completed and was stuck on some questions. Had to run dpkg --configure -a to tidy up.

In the mean time the manual method is here:

[http://www.ubuntuforums.org/showthread.php?t=207008](http://www.ubuntuforums.org/showthread.php?t=207008)

Hope you can get the bugs ironed out.

--Tony

---

### Post by cre8ivgil on 2006-08-01
For me it installed and configured Dansguardian, Tinyproxy and Firehol. It had errors when trying to install Gambas, and I ended up without the GUI. It also did not have English as the language in Dansguardian, however I edited the /etc/dansguardian/dansguardian.conf file to "ukenglish" and now all is well. I have been testing it now for close to 48 hours and it seem to be working the way it should, I had to make some minor adjustments in the banned lists of Dansguardian because it was blocking sites with extensions that I use often. I had the exact same result on my laptop as with my desktop, and Dansguardian is doing its thing, I am highly pleased with the way its working, but would have love the GUI.

---

### Post by H.E. Pennypacker on 2006-08-01
Can we see screenshots, please?  Also, what's the name of this program/script?  I assume you've named the script you created so that we can refer to it by name instead of "this guy's script."

---

### Post by Athanasius on 2006-08-02
I think it broke my computer, I have no internet connection.. what happened?!  Where is the GUI supposed to be?  I can't find it under Administration.

It's ok, I wanted to reformat anyways.

---

### Post by eric.duveau on 2006-08-04
> **H.E. Pennypacker said:**
> Can we see screenshots, please?  Also, what's the name of this program/script?  I assume you've named the script you created so that we can refer to it by name instead of "this guy's script."

Here are some screenshots :D

---

### Post by VirtuAlex on 2006-08-07
> **nanomad said:**
> Here is a simple (but powerful) install script for a parental control feature
It is based on tinyproxy + firehol + dansguardian and on an howto found on this forum (dunno remeber where)
Is it possible to set up some really primitive parental controls using, let's say, only iptables? Like some rule to block every destination but allow only some websites (or ips for that matter).

---

### Post by nanomad on 2006-08-19
I've fixed the installer and created a uninstaller. You will find the new package as an attachment


Ps. now the GUI works, i hope

---

### Post by Kaobear on 2006-08-19
Absolutely wonderful script, please check your PM's for a little note from me.

---

### Post by nanomad on 2006-08-20
I've read your PM and replied. Check it

---

### Post by rayrayray on 2006-08-20
FWIW - I've been battling to get DG working for several days for a project involving public access internet computers at a local library. A couple of days ago I got to the point that it would work IF I did the manual proxy configuration in the individual browsers, but no other way. On a whim, I did a fresh install of UBUNTU 5.10 to some spare space on my desktop to try that. Same result. So I upgraded it to 6.06 and did the reinstall (using the above supplied script) - this time it seems to work without any further fiddling. I need the installation to be easy to manage so that staff can shut down the filtering for adults who request it - looks like I may finally be able to get there. Anyone have a clue why it works on 6.06 but not on 5.10?

---

### Post by eric.duveau on 2006-08-22
I tested it and suprisingly I only can install from a console window. May because of my system?!
 
"configure the parental control filter" is the string put in the menu system.
Could you put something like "configure content filter" ou "configure content filtering engine" which is more acceptable for adult users

---

### Post by kosmic on 2006-08-22
Very good nanomad, 5 Stars for your work

---

### Post by nanomad on 2006-08-23
I'm integrating kaobear's suggestions + the one of the others. I should release a new package soon (if my ISP decides to give me a proper internet connection)

---

### Post by richardun on 2006-08-26
Thanks, nanomad.  The gui is nice especially since I had zero experience with dansguardian and fireHOL and tinyproxy.

The only buttons that didn't work for me on the configure screen were in 'Configure Whitelist' >> Sites, Users, IPs not filtered.

I just edited the dansguardian files manually and had your gui save config changes.  

Also, when I went to pick a language, I didn't see english (or ukenglish), so I picked the last one which had a radio button, but was blank... was hoping it was english.  Then dansguardian didn't want to start (because the language var in dansguardian.conf was '(null)'... anyway, I changed it to ukenglish and it was good... just thought you might want to know about those things I encountered.

Thanks again!

---

### Post by msak007 on 2006-08-27
Thanks for the script, this is exactly what I was looking for. I tried a how-to on another web site and was close, but gave up on trying to get dansguardian to connect to squid as a proxy (plus the GUI makes for easier configuration). Anyway just wanted to comment that I'm a Kubuntu user, and you hard-coded gnome-terminal in your installer script so it kept failing on the zenity check when it would call gnome-terminal. I ended up having to run .zenity_check and .setup manually to get this installed. My biggest problem, however, is that I couldn't edit any rules or configurations because, once again, you hard-coded gedit into your scripts. Just thought I'd let you know that you may want to do something about that because not all your users will be using Gnome. I'll have to find where the code is stored and edit it manually to use kedit or kate to edit config files. Also, I had the same problem as Richardun when picking a language and had to choose the blank radio button. Otherwise keep the great work, maybe you can work with the Automatix guys and get this included in their installer.

EDIT: Well as far as I can tell, everything is stored in /usr/local/parental-control but I couldn't find anything in any of the scripts there referencing gedit, so I assume it's coded in the "ubuntu_parental_control_gui" file which I can't edit (looks empty, not sure what kind of file that is). So at this point, this app is useless to me unless I install gedit which I don't want to do. Please advise me what I can do to have it use kedit or kate instead of gedit. Also, one thing I noticed is that when it blocks a page it gives the "Page cannot be displayed" error. Is there a way you can edit that to display an "Access denied" page instead?

---

### Post by Macchi on 2006-08-30
Thank you very much Nanomad for the script! I am experimenting with content filtering on a small office & home office server. My goal is to configure the server as a web proxy and filter for my network. Later I will have to find out how to add the automatic proxy configuration for the clients. 

I would also like to request a name change towards the more neutral "content filter" or anything similar. The present name parental control" has a more limited scope. 
 
There are many situations where content filtering is very important and necessary: Business and professional users, educational aplications, public environments and of course for families.

---

### Post by iperkins on 2006-09-19
> **VirtuAlex said:**
> Is it possible to set up some really primitive parental controls using, let's say, only iptables? Like some rule to block every destination but allow only some websites (or ips for that matter).

This is what I am looking for as well. Which takes precedence, deny or allow? Ideally (IMHO) if allow takes precedence, deny everything and only allow  what you want. This is for my son, who turs 6 on Friday. :p [edit] I also want to extend my thanks. Now my kids can start learning Ubuntu!:cool:

---

### Post by iperkins on 2006-09-19
I can verify that banning all except whitelisted sites works like a charm. The button to edit the exceptionsitelist does not work, but you can su (or sudo, I imagine) and edit /etc/dansguardian/exceptionsitelist to add the sites you want to allow. Just be certain to restart in the control panel for the changes to take effect. Thanks again, this is just what I was looking for!

---

### Post by A-Dream on 2006-11-03
What is the difference between this GUI and the GUI tool that comes with Ubuntu Christian Edition (it can be found here: [http://www.whatwouldjesusdownload.com/christianubuntu/2006/09/web-content-filtering-only.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/09/web-content-filtering-only.html))

---

### Post by mhancoc7 on 2006-11-04
> **A-Dream said:**
> What is the difference between this GUI and the GUI tool that comes with Ubuntu Christian Edition (it can be found here: [http://www.whatwouldjesusdownload.com/christianubuntu/2006/09/web-content-filtering-only.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/09/web-content-filtering-only.html))

Hi, This GUI is what inspired the creation and integration of the dansguardian GUI in Ubuntu CE. I built the GUI in Ubuntu CE using Gambas. This means that the Gambas runtime is required. I can't remember how this GUI was built, but I think it was with Gambas as well. I have not taken a look at this one in a while, but from what I remember it was a bit more complicated. Not that that is bad, but I do remember simplifing mine a bit.

God Bless, Jereme

---

### Post by iperkins on 2006-11-07
It should be pointed out that, with Edgy (6.10), the default shell is now dash. This breaks the shell scripts that start, stop and check the services (Dansguardian, Firehol and Tinyproxy). What solved the problem for me was to edit the scripts in /usr/local/apps/parental-control/ and change the first line in all of them from #!/bin/sh to #!/bin/bash

---

### Post by mhancoc7 on 2006-11-07
> **iperkins said:**
> It should be pointed out that, with Edgy (6.10), the default shell is now dash. This breaks the shell scripts that start, stop and check the services (Dansguardian, Firehol and Tinyproxy). What solved the problem for me was to edit the scripts in /usr/local/apps/parental-control/ and change the first line in all of them from #!/bin/sh to #!/bin/bash

Would making these changes to the scripts work in Dapper. I mean is would the scripts work in Dapper if I changed the first line to #!/bin/bash in all the scripts? I assume so, but I just want to make sure. 
Thanks, Jereme

---

### Post by boston01 on 2006-11-12
> **nanomad said:**
> I've fixed the installer and created a uninstaller. You will find the new package as an attachment


Ps. now the GUI works, i hope

I am using 6.06.  When I try to run the install.sh with sudo, I got the following message.  Do I have to upgrade to 6.10?  Thanks.

Couldn't find any package whose name or description matched "dansguardian"
Couldn't find any package whose name or description matched "firehol"
Couldn't find any package whose name or description matched "tinyproxy"
No packages will be installed, upgraded, or removed.

---

### Post by iperkins on 2006-11-13
> Would making these changes to the scripts work in Dapper. I mean is would the scripts work in Dapper if I changed the first line to #!/bin/bash in all the scripts? I assume so, but I just want to make sure.
Thanks, Jereme

I don't see why not, but I am certainly not an authoritative voice here...

---

### Post by Athanasius on 2006-11-30
Great work with this.  I have been using this at our school for months now and it works wonderfully.

One thing is that I cannot get it to work on Edgy.  Everything installs fine but when everything is done dansguardian will not start.  Tinyproxy and Firehol start but dansguardian will not.  I have not had that problem with dapper.  I restarted the computer after installation but that did nothing.

---

### Post by Nopposan on 2006-12-07
Will this also work on Xubuntu or Kubuntu?

I've installed Xfce under SuSE on my niece's very old laptop and will consider installing Ubuntu with parental controls on her desktop, but I think she prefers KDE. (Right now she's running SuSE 10.0 on her desktop without internet access.)  If I could install parental controls and Xubuntu on her laptop then she'd finally be able to use it for internet access -- that is, if I can get Ubuntu to find her wireless card and intall a usable driver; this worked like a charm in Yast with a 802.11b SMC wireless card.

Hmm. . . what would be the minimum hardware requirements for the parental controls installation from your script?  The laptop has just 6 gig hd and 128mb of ram with a pre-pentium intel processor.

Thanks for your work on this.  It is needed.

---

### Post by drokmed on 2006-12-13
> **Nopposan said:**
> Will this also work on Xubuntu or Kubuntu?

I've installed Xfce under SuSE on my niece's very old laptop and will consider installing Ubuntu with parental controls on her desktop, but I think she prefers KDE. (Right now she's running SuSE 10.0 on her desktop without internet access.)  If I could install parental controls and Xubuntu on her laptop then she'd finally be able to use it for internet access -- that is, if I can get Ubuntu to find her wireless card and intall a usable driver; this worked like a charm in Yast with a 802.11b SMC wireless card.

Hmm. . . what would be the minimum hardware requirements for the parental controls installation from your script?  The laptop has just 6 gig hd and 128mb of ram with a pre-pentium intel processor.

Thanks for your work on this.  It is needed.

Poor girl.  SuSE 10.0 w/ Xfce on a 486 w/ 128mb ram??????  Probably takes FOREVER to do anything.  SuSE 10.0 w/ Xfce needs about 256mb ram minimum to run without hitting the swap file.  The 6 gig hd is plenty though.  I know, I've done it.  SuSE w/ icewm only takes about 100mb, if you strip out things like mono, apparmor, etc.

I'd suggest Ubuntu (server), add icewm and it's usual suite of apps, like dillo or netscape, rox-filer, etc.  You could easily add dansguardian to this.  I've done it.  Just grab the standard dansguardian package from the debian sites.  I have an ubuntu server w/ icewm, squid, dansguardian, webmin, all running in about 100mb ram.

You could try one of the very small distributions, like DeliLinux or PuppyLinux.  I doubt they support dansguardian though.

One other thought: why install parental controls on her laptop?  If there is another computer on the LAN she connects to, load the proxy on it as a server, and she can access the Internet through the server.  Just a thought.

Good Luck.

---

### Post by isaiah55 on 2006-12-29
I had problems trying to find the Ubuntu CE version of the GUI for dansguardian.  All the links in this formum go to a defunct page.
Anyway I finally found it [http://www.whatwouldjesusdownload.com/christianubuntu/2006/11/ubuntu-ce-v20-edgy-downloads.html]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/11/ubuntu-ce-v20-edgy-downloads.html")

There is a link on this page that allows you to install the gui even if you have dansguardian already installed.

I hope it helps - BTW read the readme before installing :)

---

### Post by saxaphone_man on 2006-12-30
PLEASE help me, I installed the first one on the thread, and now my wifi/internet totally doesn't work, I really don't want to reinstall, can anybody help me?

please help me here or at [http://ubuntuforums.org/showthread.php?p=1946274](http://ubuntuforums.org/showthread.php?p=1946274)

---

### Post by saxaphone_man on 2006-12-30
got it, it was some crazy clamav config files, I looked over "locate clamav" and deleted all of the shown files, and I'm good again

---

### Post by mhancoc7 on 2006-12-30
> **isaiah55 said:**
> I had problems trying to find the Ubuntu CE version of the GUI for dansguardian.  All the links in this formum go to a defunct page.
Anyway I finally found it [http://www.whatwouldjesusdownload.com/christianubuntu/2006/11/ubuntu-ce-v20-edgy-downloads.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/11/ubuntu-ce-v20-edgy-downloads.html)

There is a link on this page that allows you to install the gui even if you have dansguardian already installed.

I hope it helps - BTW read the readme before installing :)

Sorry for the broken link. I have redirected it to the main download page. That way users can choose Dapper or Edgy.

Thanks, Jereme

---

### Post by shankar1023 on 2007-01-19
Hi,

I appreciate this tool is really good.I have installed it on ubuntu dapper 6.06 LTS and it is working good.

But I have two bugs.In Filter configuration,some of the whitelist buttons ( sites not flitered,ips not filtered,users not filtered ) are not working WHY?? Please help.

and , the banned site information page is in french language.How can I change this to english.
how can i edit this in my own words????????? please need some reply.

Thanks in advance.

Shan

---

### Post by mhancoc7 on 2007-01-19
> **shankar1023 said:**
> Hi,

I appreciate this tool is really good.I have installed it on ubuntu dapper 6.06 LTS and it is working good.

But I have two bugs.In Filter configuration,some of the whitelist buttons ( sites not flitered,ips not filtered,users not filtered ) are not working WHY?? Please help.

and , the banned site information page is in french language.How can I change this to english.
how can i edit this in my own words????????? please need some reply.

Thanks in advance.

Shan

Maybe try to install it again?

Jereme

---

### Post by shankar1023 on 2007-01-19
Yes I ve reinstalled that.But nothing happen.I need to change the language of  access denide page.Please help.

---

### Post by ryu kun on 2007-01-29
I've run the script which is attached to the first post of this thread. Everything installed successfully and pages began being filtered but I can't find any GUI in System - Administration menu. Where is it?

I saw a later post in this thread to which a new script attached. Should I have installed that version? If so, can you please change the first post, as many people may do the same mistake.

Thanks in advance.

---

### Post by kholzapfel on 2007-01-30
I feel into the trap and installed the first package posted. Now I am unable to access the web on this machine. The Parental Control GUI doesn't show under System>Administration

How do get out of this trap? I would like to uninstall the program. I looked aorund but couldn't figure out how. I am new to Linux and Ubuntu and am not familiar with the command line.

Detailed instructions would help.

Will the second version come with the GUI and an uninstaller?

Thanks very much

---

### Post by ryu kun on 2007-01-30
Yes, you should have used the second posted script, not the first one.

To solve your problem,

1. Run terminal from applications - accessories menu.
2. Type:

```
sudo gedit /etc/dansguardian/bannedextensionlist
```

2. Put a " # " at the beginning of this line:

```
.gz   # Gziped file
```

3. Download attached file. Double click to install.sh file. After the installation GUI should work. If not, run uninstall.sh file to get rid of it.

Keep in mind that you can always manually edit configuration files in /etc/dansguardian/ directory, GUI is not absolutely necessary.

---

### Post by kholzapfel on 2007-01-31
Thanks for your reply.
I have the GUI for the parentl control filter working but I am still stuck with Dansguardian:
I followed your instructions and entered 
sudo gedit /etc/dansguardian/bannedextensionlist  in the command line.
Then another window opened up - the bannedexetensionlist I typed in
# .gz #Gziped file  as well as 
.gz #Gziped file  but nothing else happened.

I then went back to the GUI of the Parental control filter. As soon as I start filter  Firehol and TinyProxy start ok. But Dansguardian produces the following error:
Starting DansGuardian: Error openeing message file (does it exist?): /etc/dansguardian/languages/(null)/messages
Error parsing the dansguardian.conf file or other DansGuardian configuration files
DansGuardian is stopped

When I installed the parental control filter I didn't see English as an option for the error messages. So I choose French. Maybe that is part of the problem?

---

### Post by ryu kun on 2007-01-31
Type:

```
sudo gedit /etc/dansguardian/language
```

Then clear the file and just write ```
english
``` and save it. Then restart dansguardian by GUI. It should work.

---

### Post by kholzapfel on 2007-02-04
I replaced french with english and saved it.
I can see how I can access the dansguardian GUI via the Applications or the System menu.
So I tried to restart dansguardian via the parental control software.
The messagges I a mgetting read as follows:

Starting DansGuardian: Error opening messages file (does it exist?): /etc/dansguardian/(null)/messages
Error parsing the DansGuardian.conf file or other DasnGuardian configuration files
DansGuardian is stopped

I installed dansguardian without any error messages. So I am still fishing in the dark....

---

### Post by ktraglin on 2007-02-12
I set up Ubuntu for my 7yr old Godson.  I configured Firestarter to allow his machine to act as an internet router for his 22 yr old brother's computer, and allow me to access it via ssh.  I'm concerned that installing Firehol may change the Firestarter settings?  Any ideas?

---

### Post by dr_d on 2007-02-12
Did you know that parental control is also in Vista? Bill Gates told me so.

:P

---

### Post by shanepardue on 2007-02-22
Great tool! My only problem is finding a free blacklist or subscription service. Does this exist?

---

### Post by mhancoc7 on 2007-02-22
> **shanepardue said:**
> Great tool! My only problem is finding a free blacklist or subscription service. Does this exist?

Thanks,

There is urlblacklist.com. It is not free.

I have also found this site.
[http://squidguard.shalla.de/shallalist.html](http://squidguard.shalla.de/shallalist.html)

Jereme

---

### Post by sym_zo on 2007-02-25
Thank you very much for your bundle : it works really fine !
I have a question, though. How do you enable the filtering only for some users ?
The computer where I installed this great tool has several non-administrator adult users for wich the filter should be bypassed. I have given then a common group, therefore all I need to do is specify a rule for that group.
What the easiest way to implement that ? In the firehol configuration file, maybe ?

Thank you !!

sym

---

### Post by Trekko on 2007-02-25
I installed this with belives that i could choose different user settings.

My mistake of course...

I installed the first script and didnt get the GUI working.

So i dl the secound script with an uninstaller tu uninstall everything.
Seems to be ok, but is everything removed properly now?

---

### Post by fluffman86 on 2007-07-12
Sorry, but...

*BUMP*

I hate it when n00bs bump old threads...like this.  But it's related, so whatever.

I just installed the Dansguardian files for Ubuntu CE on Kubuntu.  Everything worked fine - I just had to change "gksudo" to "kdesu" and maybe one instance of "gedit" to "kate."  Anyhoo, everything went fine.  Dansguardian appears to be filtering perfectly.  The only problem is when I click "configure parental controls" in the KMenu, I get the "Run as Root..." dialog box, but nothing will run after I enter my user password.

At first, nothing would happen, but I changed the run parameters from "gksudo /usr/..." to "kdesu /usr/..."

Thanks in advance for any ideas!

---

### Post by fluffman86 on 2007-07-12
Ok nevermind...I just uninstalled everything.  The filtering was starting to get ridiculous without a way to change the filtering options.

Thanks anyway.  If I ever need the filtering for someone, I'll just install Ubuntu CE instead of Kubuntu + dansguardian + sword

---

### Post by merlin114 on 2007-09-07
I just tried to use the install.sh to setup DansGuardian on Feisty, but am having a problem.  When I first run install.sh, it launches a terminal and asks for my password, but when I enter it (correctly -- I've tried this 3 times now) I get an Authentication Failed message.  Then everything seems to go okay until it gets to restarting the firewall, when it spits out a bunch of errors (sample below).  When the script completes, and I start the DansGuardian GUI, it reports that firehol is stopped, and doesn't work.  Naturally, internet service is blocked until I uninstall.  Any thoughts on what to fix?

 * Restarting Firewall configuration                                                                                                                        

--------------------------------------------------------------------------------
ERROR   : # 1.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A in_world -p tcp -m state '' --state NEW \! --syn -j pr_world_nosyn 
OUTPUT  : 




--------------------------------------------------------------------------------
ERROR   : # 2.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A out_world_all_c1 -m state '' --state NEW\,ESTABLISHED -j ACCEPT 
OUTPUT  : 

blah
blah
blah
and on and on...
--------------------------------------------------------------------------------
ERROR   : # 24.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line FIN of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -A FORWARD -m state '' --state RELATED -j ACCEPT 
OUTPUT  : 


                                                                                                                                                     [fail]
Restarting DansGuardian:  * Restarting DansGuardian:                                                                                                        Error opening messages file (does it exist?): /etc/dansguardian/languages//messages
Error parsing the dansguardian.conf file or other DansGuardian configuration files
                                                                                                                                                     [fail]
Done!

---

### Post by merlin114 on 2007-09-07
Nevermind.  I downloaded the DansGuardian GUI installer from the Ubuntu CE site and it worked perfectly right off.

---

### Post by mhancoc7 on 2007-09-07
> **merlin114 said:**
> Nevermind.  I downloaded the DansGuardian GUI installer from the Ubuntu CE site and it worked perfectly right off.

That is great to hear!

Jereme

---

### Post by waspinator on 2007-11-19
I can't find anything like this for 7.10 Gusty. Does any one know if the GUI exists for Gusty?

---

### Post by mhancoc7 on 2007-11-19
> **waspinator said:**
> I can't find anything like this for 7.10 Gusty. Does any one know if the GUI exists for Gusty?

The Ubuntu CE GUI will be available for Gusty soon.
Jereme

---

### Post by marianlibrarian on 2007-12-10
This doesn't work. It installs firhol and tinyproxy but doesn't install dansguardian with english. too bad i don't speak bulgarian. 

I'm too tired and frustrated to say anymore about dansguardian. 

my computer is still not accessing the internet since I removed dansguardian and even trying to reinstall it here simply does not work. 

this is for a public library that went out on a limb to install ubuntu on public machines - the limb is cracking and I am falling and linux has no safety net and i have just royally screwed up one of our public access machines.

---

### Post by mhancoc7 on 2007-12-10
> **marianlibrarian said:**
> This doesn't work. It installs firhol and tinyproxy but doesn't install dansguardian with english. too bad i don't speak bulgarian. 

I'm too tired and frustrated to say anymore about dansguardian. 

my computer is still not accessing the internet since I removed dansguardian and even trying to reinstall it here simply does not work. 

this is for a public library that went out on a limb to install ubuntu on public machines - the limb is cracking and I am falling and linux has no safety net and i have just royally screwed up one of our public access machines.

You could try the parental controls GUI available from Ubuntu CE.

[www.christianubuntu.com](www.christianubuntu.com)

Jereme

---

### Post by marianlibrarian on 2007-12-11
Thanks, I did. I found a link to the list of older gui versions buried in an old thread. Most of the other links were to the "whatwouldjesusdo" site and it only had it for fiesty.

Thanks for the response. :)

---

### Post by mhancoc7 on 2007-12-11
> **marianlibrarian said:**
> Thanks, I did. I found a link to the list of older gui versions buried in an old thread. Most of the other links were to the "whatwouldjesusdo" site and it only had it for fiesty.

Thanks for the response. :)

Yes, I am the developer of Ubuntu CE. You can get a beta release of the script for Gutsy here.
[http://ubuntuforums.org/showthread.php?t=619146](http://ubuntuforums.org/showthread.php?t=619146)
Thanks, Jereme

---

### Post by samuca22 on 2007-12-13
I cannot download, the Dans... screen shows up and tells me .gz it's a forbiden extension and it's also blocking my access to sites like my bank. Please HELP !

---

### Post by baldovino on 2008-03-19
hi 

i've install but don't find the GUI on my System, can you help me

---

### Post by mhancoc7 on 2008-03-23
> **samuca22 said:**
> I cannot download, the Dans... screen shows up and tells me .gz it's a forbiden extension and it's also blocking my access to sites like my bank. Please HELP !

You will need to allow the download of .gz files using the Dansguardian GUI (System > Administration > Configure Parental Controls).

> **baldovino said:**
> hi 

i've install but don't find the GUI on my System, can you help me

(System > Administration > Configure Parental Controls)

God Bless, Jereme

---

### Post by KIAaze on 2008-03-23
_@nanomad:_
Please update your first post with the newest version of the tar.gz!

Anybody who tries the old one now with an up to date version of ubuntu will be unable to access the internet after using it and even unable to use the GUI tool since it isn't installed!
I had to look at the setup script to find out what to do.

Problems I encountered:
-copying the .bin folders didn't work because the folder was named "Parental control" with a space in it. (sh problem I think)
-After that, once I managed to install the GUI correctly: couldn't stop dansguardian&co. Some error messages about "{". Probably sh problem too as related in one post in this topic.
Had to change all #!/bin/sh to #!/bin/bash as suggested here in an earlier post.

After that, I could finally download the second tar.gz. Unfortunately, it seems it still uses sh instead of bash.

This thread is the first google result for "ubuntu parental control". So I think it's really important to update the first post, since this is what people will use first.

I don't think there should be any problems if sh is replaced by bash for older Ubuntu versions.
Anyway, why not just offer two tar.gz?
The script could probably also be improved to determine it by itself by checking if bash is available.

If you want, I could also try making a .deb. It isn't too hard after all. ;)

---

### Post by Grantsmind on 2008-03-28
hi, sorry Im a newbie to this and just uninstalled winXP last month and run ubuntu. I have no idea what this all means or how to do it but i need a parental control. Help please!

---

### Post by Grantsmind on 2008-03-28
hi, sorry Im a newbie to this and just uninstalled winXP last month and run ubuntu. I have no idea what this all means or how to do it but i need a parental control. Help please!

---

### Post by KIAaze on 2008-03-28
-Download [Parental control.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=14536&d=1155979651") (this is a link to the download link from the second post of nanomad in this thread)
-Extract its contents and go into the created folder.
-Double-click on install.sh and click "Run" in the window that appears.

When the installation is finished, you should have a shortcut to the GUI in "System->Administration->Configure the parental control filter".

---

### Post by lswest on 2008-03-28
also, about the space issue, you have to enter the file name either in quotes ("") or like this: Parental\ Control  (this is because linux sees the space as the start of another command, and the backslash tells it the next character is actually part of the filename, and the quotes "group" the words together, so that it is seen as one word - and remember, Linux is case-sensitive).  And if you tried that, or it's some other issue i misunderstood, just ignore this post ^^

---

### Post by celticbhoy on 2008-04-01
The GUI is missing not in system admin or prefs, How do I start the GUI from a terminal to make setting changes ???

---

### Post by KIAaze on 2008-04-02
Do you have anything in the /usr/local/apps/parental-control/ folder?
If not, then you probably had the same problem than me: It hasn't been installed correctly.

Did you use the first or the second download link?
I solved the problem by renaming the extracted folder to a name without spaces and running the installation again.

---

### Post by TCSnyder on 2008-04-28
well downloading this has blocked my use of the internet. i have used Synaptic to completely remove smallproxy ,Dansguardian Gambas and Firehol and my internet still doesnt work. Any Suggestions?

---

### Post by TCSnyder on 2008-04-28
ok I fixed it. I used "rm -r  foldername" in terminal to delete the files in /etc. works like it did before.

---

### Post by KIAaze on 2008-04-28
I hope you mean "rm -r /etc/dansguardian/", because "rm -r /etc" seems a bit dangerous...
I think uninstalling dansguardian, firehol and tinyproxy through synaptic would have been cleaner.

See the second post from the initial poster for an updated version of the program.
It also features an uninstall.sh script in case of problems.

---

### Post by TCSnyder on 2008-04-28
Yea thats what i ment. I was just saying the files were in /etc in case some one had the same problem.

---

### Post by PinkFloyd102489 on 2008-04-28
I havent read most of the thread, but Im throwing in my two sense.


I wanted a similar situation about a month ago. Curious preteen sister and concerned parents so I was asked to install some type of content filtering. Followed a small guide here on the forums.


Installed dansguardian and tinyproxy from the repos. You dont need firehol, though it's nice. If you want to hassle with it, ok that's fine. I didnt. Then I found a deb of Muslim Edition's Web Content Control and installed that. Changed the Firefox and IE settings on the XP machine that the family uses and voila.

Web Content Control is one of the easiest GUIs that Ive used.

---

### Post by KIAaze on 2008-04-29
Thanks for the tip. It looks much better. :)
But there's one thing I find strange:
> You should know that the filtering is only enabled for Firefox, if you have other web browsers (like Epiphany or Opera) you should configure them manually to use tinyproxy (see manual configuration).

[source]("http://www.ubuntume.com/webstrict#can_my_kids_bypass_the_filtering")

Isn't there a way to filter network traffic independently of the browser?

For those that don't want to bother with adding sources:
[http://ppa.launchpad.net/ubuntume.team/ubuntu/pool/main/w/webstrict/](http://ppa.launchpad.net/ubuntume.team/ubuntu/pool/main/w/webstrict/)

Also another question: What is the license of the parental control GUI written in Gambas and can we get the source code somewhere?

---

### Post by crawall on 2008-05-02
Then I found a deb of Muslim Edition's Web Content Control and installed that. Changed the Firefox and IE settings on the XP machine that the family uses and voila.

Web Content Control is one of the easiest GUIs that Ive used.[/QUOTE]

So where did you find this deb?

---

### Post by KIAaze on 2008-05-02
> **crawall said:**
> So where did you find this deb?

I've posted the links just above you. ;)

However, I'm having problems with both solutions (which both use dansguardian+tinyproxy):
Dansguardian is active if I use a DHCP cable connection.
But when I use my PCMCIA wifi-card, it doesn't work unless I set up firefox as indicated here: [http://www.ubuntume.com/webstrict#firefox_configuration](http://www.ubuntume.com/webstrict#firefox_configuration)

The problem is that the [Firefox lockdown solution provided here]("file:///home/mike/Desktop/locking-firefox-in-xp-and-linux.html") doesn't work for Firefox 3.0 beta 5 (comes with Hardy). :/
And I don't like the FF lockdown solution anyway since it forces one to remove all other browsers.

Does anyone here know how to correctly set up tinyproxy so that it works for all network interfaces?

edit:
It seems dansguardian works with the wifi card after restarting tinyproxy+firehol+dansguardian. :)

---

### Post by shadiali on 2008-06-21
so this wouldn't work for ver 8.04 would it?

---

### Post by se user on 2008-06-22
can some one help me i recently got some one in my family to switch to Ubuntu v8.04 but the problem is that they need parental controls on the kids user names and i installed the software and when i try to configure it it doesn't show when i click "configure parental controls" in sys--->.admin----> configure parental controls and it won't let me go any ware on fire fox please help me i am new to Ubuntu

---

### Post by KIAaze on 2008-06-23
> **shadiali said:**
> so this wouldn't work for ver 8.04 would it?

The GUI from here should work.
The Ubuntu ME GUI will probably not because of the lockdown problem. I haven't tried it again since I currently don't need it anymore. (was for personal use ^^)

> can some one help me i recently got some one in my family to switch to Ubuntu v8.04 but the problem is that they need parental controls on the kids user names and i installed the software and when i try to configure it it doesn't show when i click "configure parental controls" in sys--->.admin----> configure parental controls and it won't let me go any ware on fire fox please help me i am new to Ubuntu

It probably wasn't installed correctly.
What does the following command give you?:
```
/usr/local/bin/parental-control-config
```

Did you use the second version of the GUI?
You can get it here:
[http://ubuntuforums.org/showpost.php?p=1396845&postcount=10](http://ubuntuforums.org/showpost.php?p=1396845&postcount=10)
(it's the second post from nanomad in this thread)

Try to reinstall the GUI using this version and post the output of the script here in case it still doesn't work.

---

### Post by costis on 2008-06-28
Hello to the contributors of this extremely useful vision!... :)

I installed parental-control using the first and second tar, but it did not work... What I am getting after using the second tar is:```

p@s:/usr/local/apps/parental-control$ ls
check_dg.sh  check_fh.sh  check_tp.sh  start.sh  stop.sh  ubuntu_parental_control_gui

p@s:/usr/local/apps/parental-control$ ./ubuntu_parental_control_gui 
bash: ./ubuntu_parental_control_gui: /usr/bin/gbx: bad interpreter: No such file or directory

p@s:/usr/local/apps/parental-control$ ./stop.sh 
./stop.sh: 4: function: not found
FireHol is stopped
TinyProxy is running
DansGuardian is stopped
./stop.sh: 24: Syntax error: "}" unexpected

p@s:/usr/local/apps/parental-control$ ./check_dg.sh 
./check_dg.sh: 4: function: not found
DansGuardian is stopped
./check_dg.sh: 15: Syntax error: "}" unexpected

p@s:/usr/local/apps/parental-control$ ./check_fh.sh 
./check_fh.sh: 4: function: not found
FireHol is stopped
./check_fh.sh: 14: Syntax error: "}" unexpected

p@s:/usr/local/apps/parental-control$ ./ubuntu_parental_control_gui 
bash: ./ubuntu_parental_control_gui: /usr/bin/gbx: bad interpreter: No such file or directory

p@s:/usr/local/apps/parental-control$ ./start.sh  
./start.sh: 4: function: not found
FireHol is stopped
TinyProxy is running
DansGuardian is stopped
./start.sh: 24: Syntax error: "}" unexpected

p@s:/usr/local/apps/parental-control$ ./stop.sh 
./stop.sh: 4: function: not found
FireHol is stopped
TinyProxy is running
DansGuardian is stopped
./stop.sh: 24: Syntax error: "}" unexpected

```

Any insights to set parental control GUI up?

---

### Post by KIAaze on 2008-06-28
[I]edit: If you are too lazy, you may also just download the updated version I made below. ;)
Tell me if it works.[/I]

Do you have "gambas" installed? (/usr/bin/gbx is the gambas interpreter.)

Concerning the  "Syntax error: "}" unexpected" error messages, this is due to the sh/bash problem mentioned somewhere in this thread.
Just edit all .sh files so that they start with "#!/bin/bash" instead of with "#!/bin/sh".
If there is no #! line, add the "#!/bin/bash" line anyway.

Of course, you could always manually run
```
bash stop.sh
```
to force the use of bash instead of sh, but this isn't very practical and won't work when the GUI calls the script (because the GUI uses the scripts actually).

ex: stop.sh
```
#!/bin/bash
## Look up what it is running

function check {
## FireHol
if (test -f /var/lock/firehol);
then fh_running="1" && echo "FireHol is running";
else fh_running="" && echo "FireHol is stopped";
fi
...

```

Note:
Considering that the initial poster has never updated his first post to address all the problems encountered here, I am tempted to create a new parental control GUI thread.
This might prove very useful until a working and easy .deb installation is available.

It would be interesting to use the excellent java GUI of the UbuntuME parental control and use the browser independent configuration of this one.
I'm currently busy with other projects, but would be interested in creating a real control GUI.

edit:
Created new thread and awaiting moderator approval (howto section).
Here's my modified version if you want to try it out.
It should work "out of the box".

re-edit: yay, there was a little error in the one I submitted in the new howto... ^^
But this tar.gz should work.

---

### Post by sevensky on 2008-07-23
sory..

i just..don't know how to start the program...

i alt+f2 then dansguardian..it doesn't work..
and in terminal too..

can you tell me..
sorry..i'm still newbie..

---

### Post by KIAaze on 2008-07-23
If you want to run it with alt+F2 (or from command-line), the correct command is:
```
parental-control-config
```

However, you can also find it in "System->Administration->Configure the parental control filter".

You can't "run" dansguardian from the command line and it doesn't have a GUI.
dansguardian is just a daemon program (program running in the background). If you really want, you can start or stop by issuing the following commands:
```
sudo /etc/init.d/dansguardian start
sudo /etc/init.d/dansguardian stop

```

P.S: I created an updated version of this thread here:
[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)
since nanomad stopped updating his initial post (where new users look first).

---

### Post by sujithw on 2008-11-28
Does this work on 8.10??

I installed it and the GUI tool didn't work. The filter seems to be working even though I was not allowed to visit any sites. I couldn't configure it, so I removed the software.

---

### Post by KIAaze on 2008-11-29
nanomad has stopped following this thread a long time ago I believe.

Anyway, go here for the GUI I'm working on:
[https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)

It should already work (works for me at least).

And here you'll find a list of other projects/solutions in case you're not satisfied with mine:
[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

(I would recommend openDNS for example.)

---

### Post by mikeuhlik on 2008-12-04
Would it be possible to make it a .deb file for easy install. i dont know why know one really uses the .deb there are many .deb creators to use to make great deb installers.

---

### Post by KIAaze on 2008-12-05
> **mikeuhlik said:**
> Would it be possible to make it a .deb file for easy install. i dont know why know one really uses the .deb there are many .deb creators to use to make great deb installers.

[https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)

---

### Post by Jazzmanworks on 2008-12-22
Hi
Can anyone tell me how to access the GUI?
I can't download the uninstaller because Dans is blocking it.

---

### Post by ellipsis21 on 2009-01-02
Hey guys... I am kinda an Ubuntu noob and I need some help with this... I read through the first three pages and didn't see anyone with my problem so don't get mad if this has already been solved hahaha

I got a Dell Netbook (basically a mini-laptop) for Christmas running what I believe to be a sort of watered down version of Ubuntu... My mom wants to get some parental controls on this machine and I've been trying to help her out...

I tried installing the GUI following the instructions but in Konsole I get a few errors regarding Dansguardian (something about parsing or something) and instead of an OK next to it it says [fail]... Also when I install it I lose all access to the internet. (Is this something to do with the proxy settings?) Also, the GUI is no where to be found in my apps...

Any ideas on fixing this?=

All help is VERY appreciated (:

Ellipsis

---

### Post by KIAaze on 2009-01-03
[EDIT]Oops, thought I was on the updated thread.
Please go [here]("http://ubuntuforums.org/showthread.php?t=843510") for a new version of the Parental control GUI. It's based on the one made by nanomad + the one from Ubuntu CE. I'm currently still working on it.[/EDIT]

==================================
_**New release: v1.2.0:**_
[https://launchpad.net/webcontentcontrol/+announcement/1731](https://launchpad.net/webcontentcontrol/+announcement/1731)
==================================

> **Jazzmanworks said:**
> Hi
Can anyone tell me how to access the GUI?
I can't download the uninstaller because Dans is blocking it.

The GUI should be in Applications->System tools->Web Content Control.
Otherwise, you can launch it using:
```
/usr/bin/webcontentcontrol
```

There is no uninstaller to download.
If you installed using the tar.gz, you can uninstall using ```
sudo make uninstall
```

If you installed using the .deb or though synaptic, you can uninstall it using:
```
sudo apt-get remove webcontentcontrol
```

Did you use the packages in the initial post instead of getting the latest from [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol) ?

Let me know if you still have problems removing it. Then I'll post instructions for manual removal.

To gain internet access again, just run the following command:
```
/usr/share/webcontentcontrol/scripts/stop.sh
```
If it doesn't work:
```
sudo /etc/init.d/firehol stop
sudo /etc/init.d/tinyproxy stop
sudo /etc/init.d/dansguardian stop

```

> **ellipsis21 said:**
> Hey guys... I am kinda an Ubuntu noob and I need some help with this... I read through the first three pages and didn't see anyone with my problem so don't get mad if this has already been solved hahaha

I got a Dell Netbook (basically a mini-laptop) for Christmas running what I believe to be a sort of watered down version of Ubuntu... My mom wants to get some parental controls on this machine and I've been trying to help her out...

I tried installing the GUI following the instructions but in Konsole I get a few errors regarding Dansguardian (something about parsing or something) and instead of an OK next to it it says [fail]... Also when I install it I lose all access to the internet. (Is this something to do with the proxy settings?) Also, the GUI is no where to be found in my apps...

Any ideas on fixing this?=

All help is VERY appreciated (:

Ellipsis

Can you post the output of the installation process?

---

### Post by KIAaze on 2009-01-03
Nanomad hasn't been following this thread for a long time.
Please refer to this thread in the future: [http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

For those who installed the GUI using the installer from nanomad's initial post, you can remove it by running the following script:
```

#!/bin/bash
# License GPL, see LICENSE
# Written by KIAaze
# Based on the setup script from Nanomad [condellog_At_gmail_dot_com]

starting_dir=`pwd`
install_dir="/usr/local/apps/parental-control/"
bin_dir="/usr/local/bin/"

function remove_packages {
    zenity --info --title "Ubuntu Parental Control Removal" --text $"Now i will remove dansguardian, firehol, tinyproxy, gambas and the qt libs for the GUI"
    apt-get remove --purge dansguardian firehol tinyproxy gambas libqt3-mt
}

function uninstall_gui {
    zenity --info --title "Ubuntu Parental Control Removal" --text $"Now i will uninstall the GUI"


    if zenity --question --text "rm -rf $install_dir ?"
    then
	    rm -rf $install_dir
    else
	    echo "not OK"
    fi

    if zenity --question --text "rm -rfv $install_dir ?"
    then
	    rm -rfv $install_dir
    else
	    echo "not OK"
    fi

    if zenity --question --text "rm -v $bin_dir/parental-control-config ?"
    then
	    rm -v $bin_dir/parental-control-config
    else
	    echo "not OK"
    fi

    if zenity --question --text "rm -v /usr/share/applications/parental-control-gui.desktop ?"
    then
	    echo $"Uninstalling GUI"
	    rm -v /usr/share/applications/parental-control-gui.desktop
    else
	    echo "not OK"
    fi
}

function update_menu {
    sudo killall -HUP gnome-panel
    update-menus
    echo $"Done!"
}

remove_packages
uninstall_gui
update_menu

zenity --info --title "Ubuntu Parental Control Removal" --text $"All done, enjoy"

```

I attached it for download for you convenience:

---

### Post by Littlejohn on 2009-01-04
Hi,

I'm very new to Ubuntu.

I uninstalled this with synaptic but still cannot connect anywhere.

How can I install the new removal tool from the command line?

Thanks.

---

### Post by Littlejohn on 2009-01-04
I ran the commands from your script manually.

The software seems to be removed, but I still can't connect anywhere.

There must be something else I need to undo.

Any ideas?

Thanks,

---

### Post by opqr175 on 2009-01-04
Plan for some overnight guests, just in case; When the clock strikes midnight; Music; Decorating ideas; Food; Delegate; Get your invites out early;[warcraft gold](http://goleveling.com/)

---

### Post by KIAaze on 2009-01-05
> **Littlejohn said:**
> Hi,

I'm very new to Ubuntu.

I uninstalled this with synaptic but still cannot connect anywhere.


How did you uninstall it with synaptic? Which version did you intall?

> How can I install the new removal tool from the command line?

Thanks.

No need to "install" it. But you must run it with sudo.
Just download it, go to the download directory and run:
```
sudo ./parental_control_removal_tool.sh
```

If you don't want to run the script, just run the following commands:
```
sudo apt-get remove --purge dansguardian firehol tinyproxy gambas libqt3-mt
sudo rm -rfv /usr/local/apps/parental-control/
sudo rm -v /usr/local/bin/parental-control-config
sudo rm -v /usr/share/applications/parental-control-gui.desktop

```

---

### Post by smlsound on 2009-03-25
I can't seem to install it correctly, I followed the link to download the GUI parental control and followed the instructions to install it. I ran the program and had the GUI pop up and seemed like it was working but it wouldn't turn on, and I couldn't access the internet. so I uninstalled, redownloaded, reinstalled and same problem. Any thoughts? BTW I have no idea how to use command lines and that such, if possible let's stay out of the terminal for me!! Thanks, all you guys are very helpful

---

### Post by KIAaze on 2009-03-26
Gah! Why do I always notice that I'm on the old thread too late!(after having written lots of debugging info)
[B]PLEASE GO USE THE UPDATED VERSION! -> [HOWTO: Parental control. Now with GUI too! (updated version)]("http://ubuntuforums.org/showthread.php?t=843510")
[/B]

Note:
When the internet doesn't work:
```
sudo /etc/init.d/firehol stop
```
That should do it. At least for browsers other than firefox if the firefox proxy settings have been locked down.

---

### Post by nanomad on 2009-03-28
Thanks for continuing developing my project. Unfortunately I've lost the sources long ago (and I've got connectivity issues for a long period).
I'm quite busy right now, but tell me if I can help you in any way.

---

