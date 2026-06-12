---
title: "How to remove file?"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by Buenadriver on 2014-02-22
How to insert a screenshot in a new post? Thank you.[ATTACH=CONFIG]250566[/ATTACH]

---

### Post by sudodus on 2014-02-22
Click on the big red button 'Go Advanced'

and far down (below the editing window) see 'Additional Options' and a grey button 'Manage Attachments'. Click on it and follow the instructions to attach your screenshot picture file.

---

### Post by Buenadriver on 2014-02-22
Will try, thanks.

Sorry, but where is the big red button? What page do I need to be on? Thanks.

---

### Post by Iowan on 2014-02-22
The big red button is orange... ;)
Lower right of the edit window are three buttons "Post Quick Reply", "Go Advanced", "Cancel".
If it's a LARGE image, please use a thumbnail - it'll be removed or reduced anyway...

---

### Post by Buenadriver on 2014-02-22
Ok, thank you. Some how my brain was stuck in neutral.

Ok, now how to remove the file shown in the screenshot? Thanks again.

---

### Post by sudodus on 2014-02-22
Please put new things (like the screenshot) in a reply (alias new post). It is easy to overlook edits in old posts.

-o-

I would not like to remove xserver-common. Try instead to install vlc via the command line like this

```
sudo  apt-get update
```
```
sudo  apt-get upgrade
```
```
sudo apt-get install vlc
```

and let us know what happens (what output there is from the commands). Put the output within code tags (Go Advanced, mark the text and click on the **#** icon at the top of the editing window).

By the way, which version of Ubuntu are you running? (If it is Trusty Tahr, the problem might be that there is not yet a vlc version ready for it. Trusty is not released yet.)

---

### Post by Buenadriver on 2014-02-22
```
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease   
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg [933 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates InRelease                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release [49.6 kB]
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [72 B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports InRelease                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release.gpg 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources [30.0 kB] 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release.gpg [933 B]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports Release.gpg                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources [14 B]      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release                        
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources [8,397 B]     
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources [689 B]     
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release [49.6 kB]             
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages [84.6 kB] 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports Release                       
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages [32.6 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Sources                            
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages [1,388 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Sources [71.8 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_US
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Sources [14 B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Sources [66.8 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Sources [1,358 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main i386 Packages [201 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe i386 Packages [154 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse i386 Packages [1,763 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/universe Translation-en_US
Fetched 756 kB in 21s (35.5 kB/s)
Reading package lists... Done
dale@dale-System-Product-Name:~$
```

```
[sudo] password for dale: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xserver-common-lts-raring
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,646 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 200496 files and directories currently installed.)
Removing xserver-common-lts-raring ...
Removing 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring'
dpkg-divert: error: rename involves overwriting `/usr/lib/xorg/protocol.txt' with
  different file `/usr/lib/xorg/protocol-precise.txt', not allowed
dpkg: error processing xserver-common-lts-raring (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 xserver-common-lts-raring
E: Sub-process /usr/bin/dpkg returned an error code (1)
dale@dale-System-Product-Name:~$
```

```
dale@dale-System-Product-Name:~$ 
dale@dale-System-Product-Name:~$ sudo apt-get install vl
[sudo] password for dale: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vl
dale@dale-System-Product-Name:~$ 

Running 13.10
``` Sorry forgot to results in code.

---

### Post by sudodus on 2014-02-22
There seems to be something wrong with **xserver-common-lts-raring**

Try ```
sudo apt-get dist-upgrade
```

- What file is it? Do you use some ppa, that might create this problem?

Edit: OK, after Iowan's editing I saw that you use 13.10. But what about some ppa or other special program package, that you have installed?

---

### Post by sudodus on 2014-02-22
Also you dropped the c in vlc, it should be

```
sudo apt-get install vlc
```

But it won't work until you have fixed the problem with the package** xserver-common-lts-raring**

---

### Post by sudodus on 2014-02-22
OK, after Iowan's editing I saw that you use 13.10. But what about some  ppa or other special program package, that you have installed?

Or have you activated some special repository?

---

### Post by Buenadriver on 2014-02-22
```
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  xserver-common-lts-raring
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,646 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 200496 files and directories currently installed.)
Removing xserver-common-lts-raring ...
Removing 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring'
dpkg-divert: error: rename involves overwriting `/usr/lib/xorg/protocol.txt' with
  different file `/usr/lib/xorg/protocol-precise.txt', not allowed
dpkg: error processing xserver-common-lts-raring (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 xserver-common-lts-raring
E: Sub-process /usr/bin/dpkg returned an error code (1)
dale@dale-System-Product-Name:~$ 

```

Tried to install vlc again but got same error msg. Outside of a 357mag how to remove the file? Thanks again.

---

### Post by deadflowr on 2014-02-22
> **Buenadriver said:**
> Tried to install vlc again but got same error msg. Outside of a 357mag how to remove the file? Thanks again.


I would have to ask, what method of upgrading from precise to saucy
(12.04 to 13.10)
did you use?

It would seem that the broken package should have been removed upon the releases upgrade.

---

### Post by sudodus on 2014-02-22
Did you try dist-upgrade this time, and it did not work either? (By the way, vlc works for me in Lubuntu 13.10)

Please describe your system (and reply to the questions in posts #9 and #11), otherwise it is difficult to help!

---

### Post by Buenadriver on 2014-02-22
How should I go about removing   xserver-common-lts-raring. It is well hidden and does't want to be removed. All help appreciated. Thanks.














I

---

### Post by Bashing-om on 2014-02-22
Buenadriver; Hi !

Before we even go there, why do you want to remove a critical system file ?
What problem are you experiencing ?

[INDENT]an once of prevention is
[INDENT][INDENT]worth a pound of cure !
[/INDENT][/INDENT][/INDENT]

---

### Post by Vladlenin5000 on 2014-02-22
Bashing-om, Hi again!

He already posted here [http://ubuntuforums.org/showthread.php?t=2207171](http://ubuntuforums.org/showthread.php?t=2207171)
Lots of replies... Well, most of them were about teaching how to properly use the forum's tool but there were also some important troubleshooting and the ppl there trying to help is actually waiting for some answers.
IMO, opening a new thread ISN'T the way to go...

---

### Post by Bashing-om on 2014-02-22
@ Vladlenin5000; Appreciate the heads up !

No further action in this thread, will report it as a duplicate !

Yeah, double posting is a no no !

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by Buenadriver on 2014-02-22
Don't know what a ppa is, and did try the dist-upgrade. What info is needed about system? Also what is the difference between Lubuntu and Ubuntu? Thanks again.

---

### Post by deadflowr on 2014-02-22
> **Buenadriver said:**
> Don't know what a ppa is, and did try the dist-upgrade. What info is needed about system?


Well, that package, though build from the xserver package used in Ubuntu 13.04(raring ringtail) is only available for 12.04(precise pangolin).
So, what would be helpful would be any info on how you got from 12.04 to 13.10.

---

### Post by Buenadriver on 2014-02-22
If I remember correctly I just installed 13.10 over 12.04 from a CD.

Someone said that keeping up with an old post could get ignored, so did another post. Sorry for the double post. Still don't have answer to original post on removing file. Trying to install VLC but said I had to remove a file first. All help appreciated.

Did you see the original screenshot? Before I could install VLC I had to remove this file. Just learning this system and it's tough navigating. I do appreciate all help.

---

### Post by sudodus on 2014-02-22
> **Buenadriver said:**
> If I remember correctly I just installed 13.10 over 12.04 from a CD.

It is recommended to upgrade step-wise from version via next version(s) except between LTS versions. So from 12.04 LTS you will be able to upgrade to 14.04 LTS in the end of April (or better beginning of May, when the worst bug are squashed). Otherwise upgrade in a chain

***12.04 LTS - 12.10 - 13.04 -13.10***

which is a long chain prone to breakage. But skipping 12.10 a dn 13.04 might have caused your problem, and other problems might be lurking.

Maybe the best thing would be to copy your home directory to an own partition and let it be a home partition, and reinstall 13.10 (with separate root and home partitions).

---

### Post by Buenadriver on 2014-02-22
Did you see the original screenshot? Before I could install VLC I had to remove this file. Just learning this system and it's tough navigating. I do appreciate all help.

Don't quite understand the partition method but willing to give a try. Probably was an error to do it the way I did but thats my dilemma. Best solution??

---

### Post by Bashing-om on 2014-02-22
Buenadriver; Hi !

Learning a new operating system is always tough, and there is a steep learning curve. We are trying our best to help.
Please bear in mind that the file " xserver-common-lts-raring" is a critical system file and can not just be removed, rather, it must be replaced with the proper version.
Now, before it can be replaced we must determine why that old version is resident on your system. Most likely is an old PPA.

PPA is Personal Package Archive = a third party addition of software that is not standard to ubuntu. So we need to know what PPAs you have added to the system (maybe like a PPA from a prior install is not supported in the current install of saucy ??).

EDIT: Failed to notice sudodus' advise, (re-)install is always a sure fire fix, and please bear in mind that it is possibly the best solution.
Else we can continue to work to fix this present installation.

So to continue:
Post back to us the output of terminal codes:
```

ls -la /etc/apt/sources.list.d
apt-cache policy xserver-common-lts-raring
dpkg -l | grep "xserver-common*"

```

for our inspection ->
[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by Buenadriver on 2014-02-22
```
dale@dale-System-Product-Name:~$ ls -la /etc/apt/sources.list.d
total 8
drwxr-xr-x 2 root root 4096 Apr 20  2012 .
drwxr-xr-x 6 root root 4096 Feb 14 19:46 ..
dale@dale-System-Product-Name:~$ 

```

```
dale@dale-System-Product-Name:~$ apt-cache policy xserver-common-lts-raring
xserver-common-lts-raring:
  Installed: 2:1.13.3-0ubuntu6~precise3
  Candidate: 2:1.13.3-0ubuntu6~precise3
  Version table:
 *** 2:1.13.3-0ubuntu6~precise3 0
        100 /var/lib/dpkg/status
dale@dale-System-Product-Name:~$ 

```

```
dale@dale-System-Product-Name:~$ dpkg -l | grep "xserver-common*"
ii  xserver-common                            2:1.14.5-1ubuntu2~saucy1                all          common files used by various X servers
rH  xserver-common-lts-raring                 2:1.13.3-0ubuntu6~precise3              all          common files used by various X servers
dale@dale-System-Product-Name:~$ 


```

---

### Post by Bashing-om on 2014-02-22
Buenadriver; Well !

A surprise, It is not due to a PPA, unless the source is in the main control file.
show us the out put of:
```

cat -n /etc/apt/sources.list

```
and still of interest is // dpkg -l | grep "xserver-common*" //.

Then will see what course of action is best.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Buenadriver on 2014-02-22
```
dale@dale-System-Product-Name:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://us.archive.ubuntu.com/ubuntu/ saucy main restricted
     6	deb-src http://us.archive.ubuntu.com/ubuntu/ saucy main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    11	deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://us.archive.ubuntu.com/ubuntu/ saucy universe
    17	deb-src http://us.archive.ubuntu.com/ubuntu/ saucy universe
    18	deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe
    19	deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://us.archive.ubuntu.com/ubuntu/ saucy multiverse
    27	deb-src http://us.archive.ubuntu.com/ubuntu/ saucy multiverse
    28	deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    29	deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb http://us.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    37	deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    38	
    39	deb http://security.ubuntu.com/ubuntu saucy-security main restricted
    40	deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
    41	deb http://security.ubuntu.com/ubuntu saucy-security universe
    42	deb-src http://security.ubuntu.com/ubuntu saucy-security universe
    43	deb http://security.ubuntu.com/ubuntu saucy-security multiverse
    44	deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb http://archive.canonical.com/ubuntu precise partner
    51	# deb-src http://archive.canonical.com/ubuntu precise partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb http://extras.ubuntu.com/ubuntu saucy main
    56	deb-src http://extras.ubuntu.com/ubuntu saucy main
dale@dale-System-Product-Name:~$ 

```

---

### Post by Bashing-om on 2014-02-22
Buenadriver;
Well, nothing I see out of the ordinary in /etc/apt/sources.list either.
Back to the why !
show us:
```

dpkg -l | grep "xserver-common*"

```
and will consider a way to replace it with the correct version.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Buenadriver on 2014-02-22
```
dale@dale-System-Product-Name:~$ dpkg -l | grep "xserver-common*"
ii  xserver-common                            2:1.14.5-1ubuntu2~saucy1                all          common files used by various X servers
rH  xserver-common-lts-raring                 2:1.13.3-0ubuntu6~precise3              all          common files used by various X servers
dale@dale-System-Product-Name:~$ 


```

---

### Post by Bashing-om on 2014-02-22
Buenadriver. OK !

The version is installed and can not co-exist with that older version.
Let's try an easier method to rid ourselves of that old version. I propose that you use the tool "synaptic" to effect that removal:
"synaptic" is no longer installed by default, so let's see if we can install it .
```

sudo apt-get install synaptic

```

else. we will do it from terminal.

[INDENT][INDENT]many paths to one end
[/INDENT][/INDENT]

---

### Post by deadflowr on 2014-02-22
Now it's understandable as to what happened.
Somehow that package wasn't correctly identified and removed during the upgrade.
But that upgrade technique isn't one of the more normal ways to do an upgrade, so problems like that are probably more common, but less reported.

That said, I wonder if bodhi.zazen's method of [fixing very broken packages]("http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/") would work in this case.
A quick breakdown would be this
```
cd /var/lib/dpkg/info
sudo rm xserver-common-lts-raring.*
sudo dpkg --remove --force-remove-reinstreq xserver-common-lts-raring
```

---

### Post by Buenadriver on 2014-02-22
```

``````

``````
dale@dale-System-Product-Name:~$ 
dale@dale-System-Product-Name:~$ ls -l /usr/lib/xorg
total 68
drwxr-xr-x 6 root root  4096 Feb 14 19:04 modules
-rw-r--r-- 1 root root 31246 Dec 17 03:06 protocol-precise.txt
-rw-r--r-- 1 root root 31246 Oct 16 10:47 protocol.txt
dale@dale-System-Product-Name:~$ 


``````

``````
dale@dale-System-Product-Name:~$ 
dale@dale@dale-System-Product-Name:~$ dpkg-divert --list | grep xorg
diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring
dale@dale-System-Product-Name:~$ 

dale-System-Product-Name:~$ 
dale@dale-System-Product-Name:~$ ls -la /var/cache/apt/archives/xserver-common*
-rw-r--r-- 1 root root 31794 Oct 17 11:14 /var/cache/apt/archives/xserver-common_2%3a1.11.4-0ubuntu10.14_all.deb
-rw-r--r-- 1 root root 31768 Nov  5 08:38 /var/cache/apt/archives/xserver-common_2%3a1.13.0-0ubuntu6.5_all.deb
-rw-r--r-- 1 root root 31836 Dec 17 03:18 /var/cache/apt/archives/xserver-common_2%3a1.14.5-1ubuntu2~saucy1_all.deb
-rw-r--r-- 1 root root 23036 Oct 17 11:14 /var/cache/apt/archives/xserver-common-lts-raring_2%3a1.13.3-0ubuntu6~precise3_all.deb
dale@dale-System-Product-Name:~$ 


``````
dale@dale-System-Product-Name:~$ sudo apt-get install synaptic
[sudo] password for dale: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  printer-driver-hpijs
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  docbook-xml libept1.4.12 librarian0 rarian-compat sgml-data
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide perlsgml w3-recs opensp
  libxml2-utils dwww menu deborphan tasksel
The following packages will be REMOVED:
  xserver-common-lts-raring
The following NEW packages will be installed:
  docbook-xml libept1.4.12 librarian0 rarian-compat sgml-data synaptic
0 upgraded, 6 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 3,360 kB of archives.
After this operation, 10.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ saucy/main sgml-data all 2.0.9-1 [277 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ saucy/main docbook-xml all 4.5-7.2 [336 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ saucy/main libept1.4.12 i386 1.0.9 [136 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ saucy/main librarian0 i386 0.8.1-5build1 [58.4 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ saucy/main rarian-compat i386 0.8.1-5build1 [100 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ saucy/universe synaptic i386 0.80.2 [2,452 kB]
Fetched 3,360 kB in 38s (87.4 kB/s)                                            
(Reading database ... 200496 files and directories currently installed.)
Removing xserver-common-lts-raring ...
Removing 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring'
dpkg-divert: error: rename involves overwriting `/usr/lib/xorg/protocol.txt' with
  different file `/usr/lib/xorg/protocol-precise.txt', not allowed
dpkg: error processing xserver-common-lts-raring (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 xserver-common-lts-raring
E: Sub-process /usr/bin/dpkg returned an error code (1)
dale@dale-System-Product-Name:~$ 

```

```
dale@dale-System-Product-Name:~$ cd /var/lib/dpkg/info
dale@dale-System-Product-Name:/var/lib/dpkg/info$ 


```

```
dale@dale-System-Product-Name:~$ sudo rm xserver-common-lts-raring.*
[sudo] password for dale: 
rm: cannot remove ‘xserver-common-lts-raring.*’: No such file or directory
dale@dale-System-Product-Name:~$ 


```

```
dale@dale-System-Product-Name:~$ sudo dpkg --remove --force-remove-reinstreq xserver-common-lts-raring
[sudo] password for dale: 
(Reading database ... 200496 files and directories currently installed.)
Removing xserver-common-lts-raring ...
Removing 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring'
dpkg-divert: error: rename involves overwriting `/usr/lib/xorg/protocol.txt' with
  different file `/usr/lib/xorg/protocol-precise.txt', not allowed
dpkg: error processing xserver-common-lts-raring (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 xserver-common-lts-raring
dale@dale-System-Product-Name:~$ 


```dale@dale-System-Product-Name:~$ dpkg-divert --list | grep xorg
diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring
dale@dale-System-Product-Name:~$dale@dale-System-Product-Name:~$ 
dale@dale-System-Product-Name:~$ ls -l /usr/lib/xorg
total 68
drwxr-xr-x 6 root root  4096 Feb 14 19:04 modules
-rw-r--r-- 1 root root 31246 Dec 17 03:06 protocol-precise.txt
-rw-r--r-- 1 root root 31246 Oct 16 10:47 protocol.txt
dale@dale-System-Product-Name:~$ code
dale@dale-System-Product-Name:~$ ls -la /var/cache/apt/archives/xserver-common*
-rw-r--r-- 1 root root 31794 Oct 17 11:14 /var/cache/apt/archives/xserver-common_2%3a1.11.4-0ubuntu10.14_all.deb
-rw-r--r-- 1 root root 31768 Nov  5 08:38 /var/cache/apt/archives/xserver-common_2%3a1.13.0-0ubuntu6.5_all.deb
-rw-r--r-- 1 root root 31836 Dec 17 03:18 /var/cache/apt/archives/xserver-common_2%3a1.14.5-1ubuntu2~saucy1_all.deb
-rw-r--r-- 1 root root 23036 Oct 17 11:14 /var/cache/apt/archives/xserver-common-lts-raring_2%3a1.13.3-0ubuntu6~precise3_all.deb
dale@dale-System-Product-Name:~$

---

### Post by Bashing-om on 2014-02-22
Buenadriver; Ummphh,

Not real surprised as
> 
rH  xserver-common-lts-raring
 the 'rh' denotes -Removed- but only -Halfway-.
What now have we got to work with on the system (??): 
show us:
```

ls -la /var/cache/apt/archives/xserver-common*

```
One way or another
[INDENT][INDENT]we will work through this
[/INDENT][/INDENT]

---

### Post by steeldriver on 2014-02-22
Can we also see

```

dpkg-divert --list | grep xorg

ls -l /usr/lib/xorg

```

---

### Post by Bashing-om on 2014-02-22
Hey steeldriver !

Welcome to the party ! This has indeed turned interesting !

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by sudodus on 2014-02-23
> **Bashing-om said:**
> Hey steeldriver !

Welcome to the party ! This has indeed turned interesting !
[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


+1

I have nothing to contribute at this level, so I'm reading and learning :-P

---

### Post by steeldriver on 2014-02-23
Well iirc someone had the same diversion error a couple of weeks ago, and the solution was to edit the post-install script directly - I don't really know anything about dpkg file diversions but it would be nice if we could figure out a more elegant way (or at least figure out if editing the post-rm is safe)

---

