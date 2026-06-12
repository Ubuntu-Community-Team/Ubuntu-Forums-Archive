---
title: "visting a hacked website"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by wenbill on 2008-10-25
Hello, I am posting this in the beginner forum because I am a beginner. I did not take notice of the security forum until I visited a hacked website. The site was for Amsynth a  midi synth program. I followed a link from a trusted forum given by a trusted contributer, and the site appeared normal when I got there. It was only when I clicked on the About link and then the Forum link that I discoverd a problem.The about link caused ad windows to open up. The Forum link caused porn site windows to open followed by a big hacked by some name to splash on the screen. When I later shut down the browser, there was still an ad window open.
 So, a word of caution to new people if you do nothing at all, your Firefox 3 browser in Hardy 8.04 is vunerable. It has a pop up blocker but that dosen't work on malicous pop up windows.
  I have since installed Firefox No script. I will probably install rkhunter and or chkroot to try and check if my system was compromised.

 The link title was amsynthe.sourceforge.net

---

### Post by cantormath on 2008-10-25
> **wenbill said:**
>  The Forum link caused porn site windows to open followed by a big hacked by some name to splash on the screen. 


What?

---

### Post by Hexagoon on 2008-10-25
I think he meant that porn sites popped up and after that a " Hacked by .." sign appeared in one of the windows

---

### Post by benny bronx on 2008-10-25
I went to that site and saw the same thing.  I do not think there is anything to worry about.  The site itself was hacked but there was no download that I could see. And even if there was, it would ask for your permission unless you are running as root (terrible idea).  Make sure to clear out your private data in firefox (tools-clear private data)

Also, even though I do not feel your comp was compromised, it is not a good idea to post links to sites that may pose any security risk.

---

### Post by drowner on 2008-10-25
Unless you were running your browser as Root/with Sudo then I would guess it is very unlikely that you did any damage to your computer.

But, if you wish to search for rootkits to ease your mind, then it won't hurt

---

### Post by ethoxyethaan on 2008-10-25
wenbill give us the link where it was posted perhaps.

---

### Post by Dr Small on 2008-10-25
> **ethoxyethaan said:**
> wenbill give us the link where it was posted perhaps.
How about not.

---

### Post by Paqman on 2008-10-25
> **wenbill said:**
>  your Firefox 3 browser in Hardy 8.04 is vunerable.

The server hosting the site you visited had been compromised, not your browser. There's no reason to think that any script(s) the cracker installed would have been able to execute on your machine. If you're concerned, then running one of the rootkit scanners will do no harm.

---

### Post by Lakeside on 2008-10-25
After I read your post, I enabled or installed both things, they were in my synaptec package manager already (bear with me I`m a complete noob) but I can`t find them listed now, when I look for them in `accessories`, they are listed as enabled in the packages list but I`m not sure how to use them.  I think I visited a bad site too, as I got all these pop ups and was surprised, it was the first experience like this since losing my windows addiction (my last bad habit besides coffee lol) and getting Hardy Heron and FF 3. I was surprised, as linux is more secure than windows, I hear. thanks for any help

---

### Post by Ptero-4 on 2008-10-25
rkhunter and chkrootkit are command line tools, they won't appear in the menu.

---

### Post by benny bronx on 2008-10-25
run, in terminal:
sudo chkrootkit
sudo rkhunter --update --checkall

These are not the noob friendliest programs, especially rkhunter, as they will give warnings about hidden or changed files that are normal in ubuntu.

---

### Post by Lakeside on 2008-10-25
So  (being a noob) I googled and got the command line, ran rkhunter in terminal, and was scary to see the loooong list of rootkits out there!  most of which were not found on my system (it was installed two days ago only!) but I did see this: 
 Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Found ]
    Checking if SSH root access is allowed                   [ Warning ]
    Checking if SSH protocol v1 is allowed                   [ Not allowed ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

Should I worry about the `warning`, guess I should do something about the ssh...
Oops, sorry Benny Bronx, just saw your post after I posted....thanks

---

### Post by jure1873 on 2008-10-25
The only strange thig is that you've got ssh root access allowed and afaik this is usually disabled in ubuntu (/etc/ssh/sshd_conf -> PermitRootLogin no).
anyway it is highly unlikely that you've got your computer hacked just by visiting a site. (i'm tempted to make a comment about msie here :))

---

### Post by Lakeside on 2008-10-25
Ya, I`m probably being an annoying noob :)  I read some of a Server installer manual AFTER installing, and noticed that I missed that ssh step probably when installing, so I will have to google and fix the problem now if I can...It`s ok, I will be installing all over again if and when I get the newest  Hardy Heron 8.10 release cd, by then I`ll have read a lot more of that manual.

---

### Post by Malta paul on 2008-10-25
I would try 'sudo chkrootkit'  then, clamscan -r(which is clamav).
also you could install Gufw which is a graphical front end to the firewall installed with Ubuntu. Click the 'install box' and 'Deny incoming traffic'.

Good luck:)

---

### Post by Malta paul on 2008-10-25
> **Malta paul said:**
> I would try 'sudo chkrootkit'  then, clamscan -r(which is clamav).
also you could install Gufw which is a graphical front end to the firewall installed with Ubuntu. Click the 'enable' box and 'Deny incoming traffic'.

Good luck:)

Edit: sorry Read Enable (instead of install!)

---

### Post by Lakeside on 2008-10-25
Ok, dumb question, but I have already run chkroot, so is the clamscan -r thing a seperate thing, like sudo clamscan -r,  or do I run chkroot and after that at some point, enter clamscan -r..not too sure yet how all this works.  Not having luck yet either with the ssh problem, I tried a few googled suggestions at the terminal, but not getting the outcome it showed. One said this:  At your terminal, 'su -' to your root account
- 'pico -w /etc/sshd_config'
- Look for the line containing "PermitRootLogin yes"
- Simply change this line to read "PermitRootLogin no"  the terminal did not show this file,  and I couldl not find it using tracker, don`t know where it is in my files.

---

### Post by Dr Small on 2008-10-25
> **Lakeside said:**
> Ok, dumb question, but I have already run chkroot, so is the clamscan -r thing a seperate thing, like sudo clamscan -r,  or do I run chkroot and after that at some point, enter clamscan -r..not too sure yet how all this works.  Not having luck yet either with the ssh problem, I tried a few googled suggestions at the terminal, but not getting the outcome it showed. One said this:  At your terminal, 'su -' to your root account
- 'pico -w /etc/sshd_config'
- Look for the line containing "PermitRootLogin yes"
- Simply change this line to read "PermitRootLogin no"  the terminal did not show this file,  and I couldl not find it using tracker, don`t know where it is in my files.
To solve the SSH problem, run:
```
sudo nano /etc/ssh/sshd_config
```

Search for "PermitRootLogin yes" and change it to:
```
PermitRootLogin no
```

Save and exit, restart SSH server:
```
sudo /etc/init.d/ssh restart
```

---

### Post by Lakeside on 2008-10-25
You guys are awesome.. this forum is awesome!!  Well, I guess Linux is awesome too, because I actually managed to follow Dr. Small`s  instructions and change the ssh to not allow root login, and learned a bit more about how to do things in the terminal while at it. Malta Paul, I would like to try this Gufw, but it`s not in the repository, so do I download it somewhere, and then somehow install itÉ
(my question mark looks like that, what`s up with thatÉ) thanks everyone.

---

### Post by benny bronx on 2008-10-25
clamscan is a frontend for clamav (an antivirus), both are in the repositories.  My opinion is that an av is usually unnecessary, but if you feel you need one, you may also want to take a look at avast free for linux. As far as a firewall, if you are behind a router/hardware firewall, I also think this would be unnecessary,

---

### Post by Lakeside on 2008-10-25
Ah, got go it (Benny). I have a router, but not totally confident that IT is config`d properly either.  I`ll check out the clam anti virus thing, guess it couldn`t hurt, until I find out more about my router (linksys) *edit* just enabled clamav, and did clamscan,  I`m clean :)

---

### Post by benny bronx on 2008-10-25
You can go to the link and see if you have any ports open, or if they are closed or stealthed.  Be aware that it will be checking your router, not your system.

[https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")

---

### Post by Malta paul on 2008-10-26
The GuFW site link is:
[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

You can also install from the terminal:
~$ sudo apt-get install gufw

:)

---

### Post by alpage2 on 2008-10-26
For command line tools, the man (manual) pages are your friend.

In a terminal window, type:

man chkrootkit

and

man rkhunter

for a description of the command line syntax and the various options available.

Alan

---

### Post by billgoldberg on 2008-10-26
> **wenbill said:**
> 
 So, a word of caution to new people if you do nothing at all, your Firefox 3 browser in Hardy 8.04 is vunerable. 

Someone sure knows how to exaggerate.

---

### Post by Paqman on 2008-10-26
> **Lakeside said:**
> I would like to try this Gufw, but it`s not in the repository

It's in the universe repo, you might want to check you've got that enabled (System > Admin > Software Sources)

---

