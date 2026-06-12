---
title: "Clam AV nuts and bolts"
date: 2005-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by crazybill on 2005-04-27
To install Clam Antivirus:

**sudo apt-get install clamav**
(Providing that your /etc/apt/sources.list file is up to date, you will get a good recent version of Clam antivirus installed on your machine.)

To update your virus definitions:

**freshclam** 

To check files in your home directory:

**clamscan** 

To check files in the entire home directory:

**clamscan -r /home** 

To check files on the entire drive (displaying everything):

**clamscan -r /** 

To check files on the entire drive but only display infected files and ring a bell when found:

**clamscan -r --bell --mbox -i / ** 

**_Run Clam AV from a terminal window!_ **

Why would you run an antivirus scan on an Ubuntu Linux Hoary computer. At this time, the only reason is if you transfer files back and forth to a Windows machine or transfer/serve email. There are yet no known virus/worm/trojan/root-violation problems with properly set-up Ubuntu computers.  However, if you use a Hoary distribution as a computer to transfer files from one location to another, they originate/end up on Windows machines, or if you want to scan a network.. this can be useful.

Here is a sample readout from:  **clamscan -r --bell --mbox -i /home** 

> 
**clamscan -r --bell --mbox -i /home** 
(infected file would be listed here)

----------- SCAN SUMMARY -----------
Known viruses: 33840
Scanned directories: 145
Scanned files: 226
Infected files: 1
Data scanned: 54.22 MB
I/O buffer size: 131072 bytes
Time: 20.831 sec (0 m 20 s)

Here is a sample readout from **freshclam** :
> root@ubuntu4:/etc/clamav #** freshclam**
ClamAV update process started at Wed Apr 27 00:06:47 2005
main.cvd is up to date (version: 31, sigs: 33079, f-level: 4, builder: tkojm)
daily.cvd is up to date (version: 855, sigs: 714, f-level: 4, builder: ccordes)

To find out what version you have:
> 
root@ubuntu4:/etc/clamav # **clamscan -V**
ClamAV 0.83/855/Tue Apr 26 06:40:32 2005

You can use the --remove flag  (clamscan --remove) too automatically remove virus-infected files,  but it is not recommended it. Sometimes, clam AV will figure a file is a virus when it is not. Thus, I look at the results and make a decision whether a file should be removed.

For learning about more flags for clamscan, try **man clamscan** or **info clamscan**

You can use the **at** command to schedule clamscan and/or freshclam.
For example:
 **at 3:30 tomorrow**
**at>freshclam** 
**at> <CTRL-D>** 
job 3 at 2005-04-28 03:30
(You have scheduled and confirmed that the Clam AV update will occur at 3:30 AM tomorrow.
 

I hope this helps and clears some confusion out there.

---

### Post by lao_V on 2005-04-27
There's a great quote I saw at [The Register]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/"): [i]"To mess up a Linux box, you need to work at it; to mess up your Windows box, you just need to work on it", writes SecurityFocus columnist Scott Granneman.

[/i]I hope this tradition continues

---

### Post by crazybill on 2005-04-27
Iao V, only use the best:

OpenBSD for webserver
Ubuntu Linux for desktop applications
Windows for Solitare

---

### Post by lao_V on 2005-04-27
I wouldn't even use Windows for solitaire :-)

---

### Post by Chayyiel on 2005-04-27
Thanks for the HOWTO!

---

### Post by crazybill on 2005-04-28
No problem

---

### Post by stubby on 2005-05-14
Cheers mate, I appreciate the HOWTO

---

### Post by benplaut on 2005-05-14
<offtopic>i still don't get it! what's the point of antivirus in a "virus free" operating system?!?!  ](*,) </offtopic>

lao_V: great quote!  \\:D/

---

### Post by rum beverage on 2005-05-18
a virus free operating system hasn't been written yet and never will be.

---

### Post by Arthemys on 2005-05-18
[QUOTE=rum beverage]a virus free operating system hasn't been written yet and never will be.[/QUOTE]

That's not wishful thinking now is it? Aspire to be great (linux), and you will be. It gives you something to develop towards, a goal that will prove to be an ever changing target.

---

### Post by Toddy on 2005-05-19
Is there any recommended GUI front end for ClamAV?  I think I've seen something called Gnome-Anti-Virus ([http://developer.berlios.de/projects/gnomeantivirus/](http://developer.berlios.de/projects/gnomeantivirus/)) and I've seen references to ClamTk ([http://freshmeat.net/projects/clamtk/)](http://freshmeat.net/projects/clamtk/)).  I don't think either are available in the repositories.  Or is their a better AV with GUI?

---

### Post by Kyral on 2005-05-19
Very nice. And as to why you would want an AV on a virus free system, well, some of us are just paranoid :) 

I get this msg when I run freshclam

sudo freshclam
ClamAV update process started at Thu May 19 10:26:43 2005
WARNING: Your ClamAV installation is OUTDATED - please update immediately!
WARNING: Local version: 0.83 Recommended version: 0.85.1
Downloading main.cvd [*]
main.cvd updated (version: 31, sigs: 33079, f-level: 4, builder: tkojm)
daily.cvd is up to date (version: 886, sigs: 1438, f-level: 5, builder: trog)
WARNING: Your ClamAV installation is OUTDATED - please update immediately!
WARNING: Current functionality level = 4, required = 5
Database updated (34517 signatures) from db.local.clamav.net (IP: 195.92.99.99)
ERROR: Clamd was NOT notified: Can't connect to clamd through /var/run/clamav/clamd.ctl
connect(): No such file or directory

It seems to be updating, but just wondering what that msg meant

---

### Post by fng on 2005-05-19
im getting the same messages 

the latest clamav in hoary is version 0.83, but the lastest version of clamav is 0.85
we should upgrade
that's why he is complaining :)

---

### Post by littlepr on 2005-05-20
And for those noobies who like GUIs and who would like real time scanning, you can install clamav and setup the deamon for startup on boot. Edit the cron file to enable scheduled scans.  Then search for dazuko ([www.dazuko.org](www.dazuko.org)) for real-time scanning. Here is a good link for setting up clamav
[http://www.flatmtn.com/computer/Linux-Antivirus_Clam.html](http://www.flatmtn.com/computer/Linux-Antivirus_Clam.html)

Then search for Klamav (Front -End GUi). 
[http://klamav.sourceforge.net/](http://klamav.sourceforge.net/)  

When installing Klamav manually, you need dazuko installed for it to work. Just follow the instructions on how to install it manually.
[http://klamav.sourceforge.net/index.php?content=ka_install_instructions](http://klamav.sourceforge.net/index.php?content=ka_install_instructions)

And here are some third party software that works with clamav.
[http://www.clamav.net/3rdparty.html](http://www.clamav.net/3rdparty.html)

You will find essentials for setting up mail servers, Apache virus scanning filter, ProFtp scanning of uploaded files, spam assasin plugins, proxy setup...etc . 

Other Front-end GUI other than Klamav are also available from this link but I recommend Klamav. 

Hope this helps.

---

### Post by rwabel on 2005-06-01
whenever I scan with clamav it uses a lot of cpu ressources. is that normal or due to my system?

---

### Post by Mez on 2005-06-01
backports has the latest version of clamav

---

### Post by petunia_volubilis on 2005-06-01
well I am on amd 64 and the latest clamav in backports is 0.83
I could not get the 0.85.1 version either from the debian sid repository nor from the deb files

is there a way to update viruses definition manually, because freshclam would not run with the 0.83 ?  

thank you

---

### Post by glasscleaner on 2005-06-01
me, im looking for a way to remove claim AV

any tips?

---

### Post by petunia_volubilis on 2005-06-01
@glasscleaner
just do it from synaptic (check for complete removal)

---

### Post by glasscleaner on 2005-06-01
oh thanks

---

### Post by az on 2005-06-01
I copied this to the forum-wiki delta.

[http://test.wiki.ubuntu.com/forum/software/clamav](http://test.wiki.ubuntu.com/forum/software/clamav)

It needs some cleaning up...

---

### Post by petunia_volubilis on 2005-06-03
if I may a little up for my previous post :

latest clamav version in backports for amd-64 is 0.83
it was not possible to get the 0.85.1 version neither from the debian sid repository nor from the deb files

is there a way to update viruses definition manually, because freshclam would not run with the 0.83 ? 

thanx again

---

### Post by Gentist on 2005-06-11
"WARNING: Your ClamAV installation is OUTDATED - please update immediately!
WARNING: Current functionality level = 4, required = 5"

Trying to update the virus-definition base might not be a good idea. I'm not sure how the internals of ClamAV works, but that error message does hint that it might not work well.

It might be partly because I'm a bleeding-edge Gentoo user, but I've found that while it could be ok to be a bit out-of-date at times, as long as security patches are applied, Ubuntu can sometimes be frustratingly out-of-date.

I thought the point of not going bleeding-edge is to assure that things will work. However, with Ubuntu, I've found that it could render things like ClamAV utterly useless, which is most of the time a lot worse than "partly working" or "fixable, but requires some work". If there's anything that Ubuntu needs to fix, it's this. Packages shouldn't be bleeding-edge, but they should at least be current enough for official support (which basically equals functionality).

---

### Post by petunia_volubilis on 2005-06-13
Hi,
I am not sure I did correctly get your point

> 
I thought the point of not going bleeding-edge is to assure that things will work. However, with Ubuntu, I've found that it could render things like ClamAV utterly useless

I am not that uncomfortable with using old clamav version, as long as things work. But  this is not actually the case.
What should I do, then ?

Thank you

---

### Post by billiejoex on 2005-06-21
A little question about ClamAV: does the ClamAV database contains also the Win32 virus signatures or it contains a linux viruses db only? 
Can ClamAV detect a Win32 virus or not?
I ask this becouse I would integrate an AV protection in a linux mail server.

---

### Post by shufla on 2005-06-22
Hi,

[QUOTE=billiejoex]A little question about ClamAV: does the ClamAV database contains also the Win32 virus signatures or it contains a linux viruses db only? 
Can ClamAV detect a Win32 virus or not?
I ask this becouse I would integrate an AV protection in a linux mail server.[/QUOTE]

Yes, clamav _detects_ Win32 viruses. I do not know how many viruses are on Linux/BSD - 5? Less, more.

Best Regards,
Shufla

---

### Post by billiejoex on 2005-06-22
Thanks.

---

### Post by sol77 on 2005-06-29
How about a script for scanning a file for viruses that can be run from Nautilus? 

What I have so far is:
```
#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
	clamscan "$uri"
done
```

But how do I go about getting the results printed out? 
A terminal opening with the results would be fine.

I'm very new to this so I don't have a clue, other than that something should be echoed.

---

### Post by tc101 on 2007-02-07
I tried to install this using the directions from the first post.  In my terminal I entered

sudo apt-get install clamav

I got several pages of messages, but at the end I get the error messages below.  Any idea what my problem is?

Setting up clamav-base (0.88.4-1ubuntu2.1) ...
Adding system user `clamav' with uid 110...
Adding new group `clamav' (115).
Adding new user `clamav' (110) with group `clamav'.
Not creating home directory `/var/lib/clamav'.
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (= 0.88.4-1ubuntu2.1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)
tomcarr@tomcarr-desktop:~$ clamscan -ir $HOME
ERROR: Can't initialize the virus database

---

### Post by caffienda on 2007-02-25
I have the same error as the above poster.  What can I do to fix this?

---

### Post by keeran12345 on 2007-03-10
I get the following errors when i sudo freshclam from terminal :
 ERROR: Please edit the example config file /usr/local/etc/freshclam.conf.
ERROR: Please edit the example config file /usr/local/etc/clamd.conf.
ERROR: Can't parse the config file /usr/local/etc/clamd.conf

when I click update from KlamAV prog, it says config file error.

I recently updated the software from the klamav window which downloaded and compiled the latest version - perhaps the update replaced the configs with defaults that doesnt work with ubuntu.

Does any one know what config files need to be edited, to get it to work with kubuntu & ubuntu?

Thanks

---

### Post by linux_beginner on 2007-11-05
Hi
me too when i tried to update my AV i got the following errors

> root@ubuntuser-desktop:/etc/clamav# freshclam 
ERROR: Please edit the example config file /usr/local/etc/freshclam.conf.
ERROR: Please edit the example config file /usr/local/etc/clamd.conf.
ERROR: Can't parse the config file /usr/local/etc/clamd.conf

waiting for your help !
thnx

---

### Post by strip21 on 2008-01-18
I am using Clamav on my server in Ubuntu 7.10. This is fine, as i can do the samba shares AV. yes you got it i have got infected with Windows PC (ubuntu server).

Im using Webmin to admin the clamav. When i try and open the clamav it keeps asking me to put in the clamd daemon startup file.
[B]
WARNING: Please fill in the location of the ClamAV daemon startup file in the module's configuration (install the ClamAV daemon package if it isn't already done).[/B]

I would love to find this daemon file location

---

### Post by strip21 on 2008-01-24
ok i found out what this is. the Clam Daemon was not install.

---

### Post by ronbrooks on 2008-01-30
I have Clamav 0.92 installed and I want to update Klamav 0.42 but it will not let me.  After I down it and they try to install the package I get this message.  

* configure: error: Can't find X libraries. Please check your installation and add the correct paths!

What are the X libraries and how do I get them or configure them for the system to work.

---

### Post by donniezazen on 2008-09-17
Hi,

Just wondering if ClamAV is just a virus scanner then how to remove viruses if found.

Thanks

---

### Post by JayTom on 2009-05-20
Thanks for the post!
For those who like clamAV but want a GUI for it
 
sudo apt-get install clamtk
 
I like this a little better sence im new with Ubuntu and still alittle scared of Terminal:p

---

### Post by squiddy on 2009-09-09
> **soham_1207 said:**
> Hi,

Just wondering if ClamAV is just a virus scanner then how to remove viruses if found.

Thanks

yep.. so what's the point the antivirus is if it can't remove viruses :o

---

### Post by aaronchall on 2009-09-27
> **crazybill said:**
> To install Clam Antivirus:

**sudo apt-get install clamav**
(Providing that your /etc/apt/sources.list file is up to date, you will get a good recent version of Clam antivirus installed on your machine.)

To update your virus definitions:

**freshclam** 

To check files in your home directory:

**clamscan** 

To check files in the entire home directory:

**clamscan -r /home** 

To check files on the entire drive (displaying everything):

**clamscan -r /** 

To check files on the entire drive but only display infected files and ring a bell when found:

**clamscan -r --bell --mbox -i / ** 
...

Hey, I'm dual booting 9.04 Jaunty with XP, and I wanted to run an antivirus from Ubuntu for complete security's sake (since I run XP with AVGfree, but I love redundancy). It's taken several days searching before I found this thread which seems to indicate what I need to do to scan my C: partition.  Here's my findings:

So I couldn't get the command freshclam to work without sudo in front of it.  

Also, I tried out a couple of frontends for clamav that didn't let me do a full scan of the C: partition.  I used Virus Scanner from "add/remove applications," but it would only scan files in each folder I selected.  Then I used KlamAV, which wouldn't even let me get to the C: part.  

To get a full scan of my C: drive partition to work, I had to enter this on the command line: 
**clamscan -r /media/disk**

This worked, and is scanning right now.  I believe this is scanning my entire C: partition.  

I can't seem to find a full list of commands for clamav anywhere, though (with lay-English explanations).  There's no man or help file/page/whatever.  Maybe one of the other commands would have scanned the C: partition too, but they would have also scanned my Ubuntu partition, and I only want a scan of my C: part. I can let it run a full Linux scan later, but for right now, this is good.

Thank you for this post.  I hope my post adds value.

Aaron

PS To prove my point about lack of resources for command line instructions, just try to figure ClamAV out from the wiki: [http://wiki.clamav.net/Main/WebHome](http://wiki.clamav.net/Main/WebHome)

---

### Post by aaronchall on 2009-09-28
To further add to my frustrations, when the scan was done, it reported 1 virus found.  It didn't indicate which file or virus, nor did it give me an option to deal with it.  I am now rerunning the scan with this command:
[B]
clamscan -r --bell -i /media/disk[/B]

It's ripped off from the original post, subtracting the mbox argument (which a brief web search indicates may relate to "mailbox", which I'm not using...) and adding the media/disk to specify exactly where to scan.  I hope this gives me the results I'm looking for...

Aaron

Post-mortem: was a false positive!  Virus free!  Though a command line entry to display the files found would have been more energy efficient.  I have no way of knowing if such a feature exists or not, because there is no compendium of commands!

Post-Post-Mortem: **clamscan -h** gives a list of command line options!

---

### Post by phamtuanamd on 2009-11-27
With clamav. Remove file infected with viruses? command line ?

---

### Post by emma00 on 2010-07-03
crazybill

when i run this command clamscan -r --bell --mbox -i /  home

it gives this error:

clamscan: unrecognized option `--mbox'
ERROR: Unknown option passed
ERROR: Can't parse command line options

---

### Post by emma00 on 2010-08-03
I have figure out how to scan ur entire disks and files if mentioned commands are not working for u.....

nor they worked for me i only did by hit and trial method so u can also do it....

clamscan -r

---

