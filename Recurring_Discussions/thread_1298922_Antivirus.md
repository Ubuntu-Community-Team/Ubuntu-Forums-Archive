---
title: "Antivirus?"
date: 2009-10-23
forum: Recurring Discussions
---

### Post by shadowayex on 2009-10-23
I'm sure there's been many discussions on this topic, but it still remains a high concern for me.

I'm running Ubuntu 9.04, and I have a friend who is now running it as well (his Vista in his Dell crashed and destroyed a hard drive, imagine that xD). We both enjoy using questionable software (Limewire, Frostwire, the like) and go to questionable site (sites of all kinds, not just dirty).

That being said, I'm aware there are viruses for Linux, and I know how things work for a Linux virus (privileges and the like), but my friend isn't familiar with how to protect himself from getting viruses.

I know of many different Linux Antiviruses, but I can never tell what's good and what isn't. I tried AVG 8.5, but it doesn't clean viruses (only finds them) so it's a waste. I've heard Avast and Bit Defender, thought about them. I've heard ClamAV, not sure what to think about it.

I would like some opinions. GUI and cleaning capabilities are a must. Also, he's on a laptop so something that won't make it burn up from a scan while he's working on something else. He's a multi-tasker through and through.

What does everyone got?

---

### Post by QLee on 2009-10-23
[QUOTE=shadowayex]I'm sure there's been many discussions on this topic, but it still remains a high concern for me.[/QUOTE]

Yes, there have been many posts regarding the issue, if you have read through them you should be less concerned in my opinion.

[QUOTE=shadowayex]I'm running Ubuntu 9.04, and I have a friend who is now running it as well (his Vista in his Dell crashed and destroyed a hard drive, imagine that xD). We both enjoy using questionable software (Limewire, Frostwire, the like) and go to questionable site (sites of all kinds, not just dirty).

That being said, I'm aware there are viruses for Linux, and I know how things work for a Linux virus (privileges and the like), but my friend isn't familiar with how to protect himself from getting viruses.[/QUOTE]

The "Linux" virus exist as proof-of-concept, they are not in the wild. There is not a propagation method for virus in GNU/Linux as has existed in another OS.

[QUOTE=shadowayex]I know of many different Linux Antiviruses, but I can never tell what's good and what isn't. I tried AVG 8.5, but it doesn't clean viruses (only finds them) so it's a waste. I've heard Avast and Bit Defender, thought about them. I've heard ClamAV, not sure what to think about it.

I would like some opinions. GUI and cleaning capabilities are a must. Also, he's on a laptop so something that won't make it burn up from a scan while he's working on something else. He's a multi-tasker through and through.[/QUOTE]

My opinion is that GNU/Linux AV apps are useful for protecting Windows systems on a network from Windows virus (i.e. if one is running a mailserver for the LAN). My opinion is that you don't need to use an AV for Ubuntu.

You might want to do some reading about rootkits (that's a good keyword to use in a search), a bigger threat than Linux virus but still not a huge one unless you do something to make your system less secure, like leave open ports or use easy to crack passwords or allow remote root access, etc.

---

### Post by sarsbretta on 2009-10-23
I would maybe add a USER for looking at "questionable sites" with limited rights and maybe another for "questionable programs/files."

Also, maybe this will help
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by lovinglinux on 2009-10-23
If you really want an anti-virus, then try BitDefender. It works like a charm, has a nice GUI and is capable of cleaning infected files.

---

### Post by shadowayex on 2009-10-23
Good answer guys. I'm getting some good information.

I'm concerned not only for my computer and my friends' computer, but at the fact that we both run on a network with 7 or 8 Windows machines.

I'm also running a Linux web/mail/database server for testing purposes. Security on the machines is pretty much default (except for an account on each that has sudo rights) so I'm not sure how big of a deal security is on them.

I would like to keep them virus-free no matter what kind of virus they may get.

I've heard good things about both BitDefender and Avast. I'm going to give BitDefender a go.

One last question: do these search for Windows viruses too?

---

### Post by lovinglinux on 2009-10-23
> **shadowayex said:**
> One last question: do these search for Windows viruses too?

Actually they only search for Windows viruses.

---

### Post by CharlesA on 2009-10-23
I'm running ClamAV on my linux box since it serves files to Windows machines. Unfortunately I have been unable to set it to "clean" any infected files, only detect them.

---

### Post by shadowayex on 2009-10-23
> **lovinglinux said:**
> Actually they only search for Windows viruses.

Sweet. That'll do =D. Thanks.

---

### Post by shadowayex on 2009-10-23
After a half an hour of trying to get BitDefender, I've gotten nowhere.

I'm becoming frustrated as all walkthroughs I found failed, and the site wants be to buy the product.

How do I get this elusive program?

---

### Post by boof1988 on 2009-10-23
> **lovinglinux said:**
> Actually they only search for Windows viruses.

Can you show the evidence or source of this information?

Thank You...

---

### Post by lovinglinux on 2009-10-23
> **shadowayex said:**
> After a half an hour of trying to get BitDefender, I've gotten nowhere.

I'm becoming frustrated as all walkthroughs I found failed, and the site wants be to buy the product.

How do I get this elusive program?

Go to [http://www.bitdefender.com/site/Products/ScannerLicense/](http://www.bitdefender.com/site/Products/ScannerLicense/)

Fill the form. You will receive a free license by e-mail.

Then go to [http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html) and click the download button.

Fill the form. You will receive the download link by e-mail. Go to the download page and click the last option "BitDefender Antivirus Scanner for Unices (Linux, FreeBSD)". The download link will show up. Click it. A new page with some folders will appear. Click the Linux folder, then select the version appropriate to your system. Download, install, put your free license.

> **boof1988 said:**
> Can you show the evidence or source of this information?

Thank You...

No.

---

### Post by Norm24 on 2009-10-24
> **shadowayex said:**
> After a half an hour of trying to get BitDefender, I've gotten nowhere.

I'm becoming frustrated as all walkthroughs I found failed, and the site wants be to buy the product.

How do I get this elusive program?

Go here:
[https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

---

### Post by jimmers on 2009-10-25
Shadowayex,
Greetings, try the following:-
  	 	 	 	 	 	  

  	 	 		 			
[SIZE=1]1. Ubuntu guide to installing Bitdefender 			
[https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

2. To request a license key (a bit like on a Win box) from 			Bitdefender 			
[http://www.bitdefender.com/site/Products/ScannerLicense/](http://www.bitdefender.com/site/Products/ScannerLicense/)[/SIZE] 			
 		 	  [SIZE=1][Back to top]("http://www.linuxformat.com/forums/viewtopic.php?t=10956#top")[/SIZE]  
 

Hope it Helps


jimmers

---

### Post by jimmers on 2009-10-26
Hi, Try the following links, they worked for me, and it will not cost you.
  	 	 	 	 	 	  

  	 	 		 			[SIZE=2]
1. Ubuntu guide to installing Bifdefender 			
[https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

2. To request a license key (a bit like on a Win box) from 			Bitdefender 			
[http://www.bitdefender.com/site/Products/ScannerLicense/](http://www.bitdefender.com/site/Products/ScannerLicense/)[/SIZE] 			
 		 	  [Back to top]("http://www.linuxformat.com/forums/viewtopic.php?t=10956#top")  
  	 	 		 			[[IMG]http://www.linuxformat.com/forums/templates/subSilver/images/lang_english/icon_profile.gif[/IMG]]("http://www.linuxformat.com/forums/profile.php?mode=viewprofile&u=16434")
 		 	  



Jimmers

---

### Post by shadowayex on 2009-10-26
I've got it installed now. I was installing a non GUI package or something. Anyway, I know how to launch it command line, but I have a launcher for it in my menus. My question is can I make the launcher load it with sudo permissions? There are some directories it can't scan (3441 to be exact) and I would like it to scan those as well.

---

