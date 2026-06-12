---
title: "Firefox freezes, cannot reinstall"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-02-26
I am at my second haunt and have a computer set up here with a one generation back board (micro ATX with 2GB DDR2 RAM running 12.04 on an SSD). I usually have three different browsers open in three different workspaces, one for each of three different interests. Last night, when I attempted to open FireFox, the computer hung.

I tried everything I could remember, but eventually had to do a power off to get it rebooted. The reboot produced another error which will be the subject of a separate post. Anyway Chrome and Chromium open normally, but when FF started, the computer froze again,

So I uninstalled FF and fired up the Ubuntu Software Center to reinstall, but got this error message:

```
Failed to download package files
Check your Internet connection
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_26.0+build2-0ubuntu0.12.04.2_i386.deb 404  Not Found [IP: 91.189.88.149 80]
```

There is nothing wrong with my internet connection (it is a WiFi) but operating normally with download speeds 5mb or better.

So ran ```
sudo apt-get install firefox
```
and got this text > apt-get install firefox
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
robert@robert-GF7100P-M7S:~$ sudo apt-get install firefox
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  xul-ext-ubufox
Suggested packages:
  ttf-lyx
The following NEW packages will be installed:
  firefox xul-ext-ubufox
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.6 MB/30.7 MB of archives.
After this operation, 64.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main firefox i386 26.0+build2-0ubuntu0.12.04.2
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main firefox i386 26.0+build2-0ubuntu0.12.04.2
  404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_26.0+build2-0ubuntu0.12.04.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_26.0+build2-0ubuntu0.12.04.2_i386.deb)  404  Not Found [IP: 91.189.91.15 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


So tried the recommend update and got this: ```
sudo apt-get update
Get:1 http://us.archive.ubuntu.com precise Release.gpg [198 B]
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]                                           
Get:3 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]                                         
Hit http://us.archive.ubuntu.com precise Release                                                                 
Get:4 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]                                             
Ign http://us.archive.ubuntu.com precise Release                                                                 
Get:5 http://linux.dropbox.com precise Release.gpg [489 B]                                                       
Get:6 http://security.ubuntu.com precise-security Release.gpg [198 B]                                           
Get:7 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:8 http://linux.dropbox.com precise Release [2,603 B]                                  
Get:9 http://linux.dropbox.com precise/main i386 Packages [1,142 B]                                            
Hit http://extras.ubuntu.com precise Release                                                                     
Err http://extras.ubuntu.com precise Release                                                                     
  
Get:10 http://security.ubuntu.com precise-security Release [49.6 kB]                                  
Get:11 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]                                  
Err http://us.archive.ubuntu.com precise-updates Release                                                         
  
Err http://us.archive.ubuntu.com precise-backports Release                                                
  
Ign http://linux.dropbox.com precise/main TranslationIndex                                                
Ign http://us.archive.ubuntu.com precise/main Sources/DiffIndex                 
Ign http://us.archive.ubuntu.com precise/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com precise/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com precise/multiverse Sources/DiffIndex           
Ign http://us.archive.ubuntu.com precise/main i386 Packages/DiffIndex           
Ign http://us.archive.ubuntu.com precise/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise/universe i386 Packages/DiffIndex       
Ign http://us.archive.ubuntu.com precise/multiverse i386 Packages/DiffIndex     
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                  
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex            
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex            
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex              
Hit http://us.archive.ubuntu.com precise/main Sources     
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Sources 
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main i386 Packages                     
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages               
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                 
Err http://security.ubuntu.com precise-security Release                         
  
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages         
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Ign http://linux.dropbox.com precise/main Translation-en_US
Ign http://linux.dropbox.com precise/main Translation-en
Fetched 104 kB in 2s (40.8 kB/s)
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com precise-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com precise-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com precise-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

Ran again with "--fix-missing" but got pretty much the same text.

So I am out of ideas unless the "public key is not available:" messages above hold the answer.

Any ideas/suggestions on how to get FF reinstalled?

---

### Post by Frogs Hair on 2014-02-26
Though the installation command you placed  in code tags is correct I don't see sudo in the command entered in the terminal. This doesn't account for gpg error and there does seem to be an issue with the back-ports repository .

> [COLOR=#000000]*apt-get install firefox*[/COLOR]

> [COLOR=#000000]*Unable to lock the administration directory (/var/lib/dpkg/), are you root?*[/COLOR]

---

### Post by Odyssey1942 on 2014-02-26
It was run as sudo. (see lines 4 and 5).

What can I do about the "gpg error and there does seem to be an issue with the back-ports repository"?

Thanks

---

### Post by Frogs Hair on 2014-02-26
There are methods posted on line and on the forum. 

[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)


Edit I noticed this also . The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1
Use 'apt-get autoremove' to remove them.

```
sudo apt-get autoremove
```

---

### Post by Odyssey1942 on 2014-03-14
Here is what I got:

> robert@robert-GF7100P-M7S:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1 thunderbird-globalmenu
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 427 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 175892 files and directories currently installed.)
Removing gir1.2-ubuntuoneui-3.0 ...
Removing libubuntuoneui-3.0-1 ...
Removing thunderbird-globalmenu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Setting up xul-ext-ubufox (2.7-0ubuntu0.12.04.1) ...
robert@robert-GF7100P-M7S:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ttf-lyx
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.6 MB of archives.
After this operation, 64.1 MB of additional disk space will be used.
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main firefox i386 26.0+build2-0ubuntu0.12.04.2
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main firefox i386 26.0+build2-0ubuntu0.12.04.2
  404  Not Found [IP: 91.189.88.149 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_26.0+build2-0ubuntu0.12.04.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_26.0+build2-0ubuntu0.12.04.2_i386.deb)  404  Not Found [IP: 91.189.88.149 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
robert@robert-GF7100P-M7S:~$

I have run both run apt-get update and with --fix-missing, but still no cigar.

---

### Post by Odyssey1942 on 2014-03-15
Also just noticed that there is a red triangle with an exclamation point in the top right panel. When I click on it, there is a message saying

> The update information is outdated. This may be caused by a network problem or a repository that is no longer available....Check for updates and see if some of the updates fail.

I have run "Check for Updates" and it says the system is up to date.

I feel sure that this "problem notification" and the inability to install FireFox are related somehow.

Any ideas gratefully received. Thanks.

---

### Post by matt_symes on 2014-03-15
Hi

I saw your post in the other thread.

Reading through this thread, there are some things i think we should do to check your system.

I think you should run fsck on your root partition just as a sanity check from your initial post.

Do you have a LiveCD/USB handy ? If so then it should be run from that environment.

But before we do that, open a terminal and copy and paste these two commands into it. 

```
df -i
```

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

Copy and past the output of both commands back into your next post.

Kind regards

---

### Post by JKyleOKC on 2014-03-15
> **Odyssey1942 said:**
> I have run "Check for Updates" and it says the system is up to date.

I feel sure that this "problem notification" and the inability to install FireFox are related somehow.

Any ideas gratefully received. Thanks.I also saw your post in that other thread, and feel quite certain that this is **not** an inodes problem since your "autoremove" would have freed up at least three inodes and maybe more, but your problem persisted after that.

The information that Matt requests will help us get a lead on the actual problem you are having. I **suspect** that some critical file may have been corrupted during that initial power-down, but more data is necessary to make this more than just a suspicion...

---

### Post by thenh813 on 2014-03-15
Your package indexes (basically lists of where to download the .debs from) are corrupt. also you have a outdated or missing GPG keys.

> 
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5


Right now I can easily tell you how to fix the GPG errors.

Enter the following:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192 40976EAF437D05B5

```

This will update/add the missing encryption keys.
Afterwards, run "sudo apt-get clean" and "sudo apt-get update -f". This wil probabally fix the problem with being unable to update the package indexes. If the keys used to verify that the packages are legitimate are out of date or missing, of course apt-get update and apt-get install firefox will fail. There is nothing to verify against, or vaild indexes for locating the packages.

---

### Post by Odyssey1942 on 2014-03-16
Matt, Jim and thenh, Apology for going silent, but had to leave just after my post on the other thread and did not return until late. Thanks to each for your input.

Read all three posts, and since thenh seemed to immediately recognize the symptoms, started with his first and it worked like a charm!

Edit: Actually "like a charm" may be a little misleading. After running the command, I then started FF and the entire system froze up solid. Hard restart got me back to speed and FF started normally.

To hopefully maximize the learning experience on this, I ran the commands that Matt suggested and here is result:

> robert@robert-GF7100P-M7S:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1      1222992 217345 1005647   18% /
udev            209071    502  208569    1% /dev
tmpfs           213200    437  212763    1% /run
none            213200      3  213197    1% /run/lock
none            213200     26  213174    1% /run/shm
/dev/sda6      1220608   8516 1212092    1% /home
robert@robert-GF7100P-M7S:~$ grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:5:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:6:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:10:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:11:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:16:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:17:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:18:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:19:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:26:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:27:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:28:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:29:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:36:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:37:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:39:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:40:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:41:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:42:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:43:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:44:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:55:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:56:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list.d/dropbox.list:1:deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) precise main
robert@robert-GF7100P-M7S:~$ 


and, if your time permits, will be very interested to know what the above would tell you (pretending that we don't already know the problem)?

---

### Post by JKyleOKC on 2014-03-16
> **Odyssey1942 said:**
> will be very interested to know what the above would tell you (pretending that we don't already know the problem)?The first command tells us clearly that it's NOT an inode problem, since no partition is using more than 17% of its inodes. The second simply shows us the exact URLs that your system will use to get updates. In this case, it just shows us that a mis-typed or no-longer-valid URL is NOT the problem, allowing us to look for the real cause -- which *thenh* had already recognized and for which he had given you a suggested remedy, that worked. The reason that FF locked up is probably that its copy in memory was only half-updated and thus ran itself into a tight loop. Re-booting caused a new copy to be read from disk, so it worked.

Doing a hard reset always runs a risk of causing disk corruption; if possible, use the "raising elephants" sequence ([http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)) before resorting to the power switch. That's to press and hold the CTRL, ALT, and SysRq keys, then while holding them (which may be difficult on many keyboards) press in sequence R E I S U B with about a two-second delay between each such keypress (Raising Elephants Is So Utterly Boring). The wikipedia article explains what this does.

Most troubleshooting boils down to following Sherlock Holmes' rule of "eliminate the impossible and what remains must be the solution." Consequently the first step is to run commands designed to eliminate as many possible causes as you can, so that you can concentrate on those which remain.

---

### Post by thenh813 on 2014-03-16
Well, I guess the package indexes are repaired, the installation ran successfully, and I guess it is fixed. Also, if you have anyother missing key someday, you can usually use the MIT public keyserver which keeps copies of all signing keys used by differeno repos and distros. You could have used it instead of the Ubuntu server, but I was sure you needed a Ubuntu key and why not use the official source. It is easy to get any missing keys:

```

apt-key adv --keyserver pgp.mit.edu --recv-keys <INSERT MISSING KEYS>

```

Keys are always hexidecimal, which means it only consisits of 0-9 and A-F.
Hexidecimal is traditionally used in computers because a digit represents a nibble (four bits, ones or zeros).

```

0=0000
1=0001
2=0010
3=0011
4=0100
5=0101
6=0110
7=0111
8=1000
9=1001
A=1010
B=1011
C=1100
D=1101
 E=1110
F=1111
[code]

Only the last eight digits are needed to identify a key,
So the Ubuntu signing keys are actually a binary number:

3E5C1192=00111110010111000001000110010010
437D05B5=01000011011111010000010110110101

Just thought you would find this interesting.
If you are finished, please mark this solved using Thread Tools at the top of the page.
Have a nice day,
                                  -TheNH813



@JKyleOKC
You are right about the REISUB except one thing:
[code]

[LIST=1]
[*]Hold down the Alt and SysRq (Print Screen) keys. 
[*]While holding those down, type the following keys in order, several seconds apart: REISUB 
[*]Computer should reboot. 
[/LIST]

```

According to the linked Wikipedia article, CTRL is not one of the keys you press. I just use ALT+SysRq which works. Maybe the control key has no effect or is no longer required. Obviously you have been working with UNIX/Linux and other systems for quite some time, so maybe something changed or I could be wrong. Just wanted to see why you mentioned CTRL+ALT+SysRq.

You dont know how many times that has come in handy knowing all the shortcuts. I discovered them by accident when taking a screenshot (ALT+PrintScrn is the same as ALT+SysRq) and bumped the "R" key. I was like what just happened, a short search later I found the Wikipedia article and have remembered the codes since.

I found your website searching your name, and had no idea you had done so much or offered database recovery services. No wonder you are so knowledgable on the topics I have seen you discuss. Thanks for sharing some of what you know with me,

                                     -TheNH813

---

### Post by JKyleOKC on 2014-03-16
> **thenh813 said:**
> According to the linked Wikipedia article, CTRL is not one of the keys you press. I just use ALT+SysRq which works. Maybe the control key has no effect or is no longer required. Obviously you have been working with UNIX/Linux and other systems for quite some time, so maybe something changed or I could be wrong. Just wanted to see why you mentioned CTRL+ALT+SysRq.

You dont know how many times that has come in handy knowing all the shortcuts. I discovered them by accident when taking a screenshot (ALT+PrintScrn is the same as ALT+SysRq) and bumped the "R" key. I was like what just happened, a short search later I found the Wikipedia article and have remembered the codes since.

I found your website searching your name, and had no idea you had done so much or offered database recovery services. No wonder you are so knowledgable on the topics I have seen you discuss. Thanks for sharing some of what you know with me.I originally wrote the reply without the CTRL, then re-read the Wikipedia article and saw that some kernels failed to recognize the sequence because, as you noted, ALT-PrtScrn does a screenshot capture, and the PrtScrn and SysReq are the very same key. That's why I went back and added CTRL to the sequence. I also found that it's not really necessary to keep holding SysReq down, apparently, which does free up a hand to do the REISUB keys. I've not yet verified this, though. It IS possible to keep both keys pressed with one hand when CTRL isn't needed, leaving the other hand free.

Yep, it's been quite a ride and I've been very fortunate in having people pay me for doing something I love for most of my life (barring a few months in retail sales very early along the way, and 13 months in a shooting war during 1953 and 54). Tomorrow morning will begin my 84th year of doing this, and I hope to keep it up for at least 20 or 30 years more. Just finished another database recovery, BTW; it was a physician's billing records that had fallen victim to a ransomware attack. I only work on systems based on Pervasive's record manager but there are enough of those to keep me going...

---

