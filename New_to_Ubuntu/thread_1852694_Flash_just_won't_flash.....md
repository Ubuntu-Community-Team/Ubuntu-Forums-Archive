---
title: "Flash just won't flash...."
date: 2011-09-30
forum: New to Ubuntu
---

### Post by verucasalt on 2011-09-30
hey everyone, i'm losing me mind here....
for some reason flash refuses to download.. anyone experiencing the same? i'm about to throw my pc out the window....
it keeps telling me to check my net connection when i'm obviouslly connected..... then it says it would imply downloading from an untrusted source... wtf?!:confused:

i'm using ubuntu 11, and i used to the software program to try to download that crap  ( flash ).....

Any other options for watching youtube on ubuntu? nevermind minitube, it's horrible....


pls help, thanks :)

---

### Post by seawolf167 on 2011-09-30
Assuming you are using a 32bit (x86) machine, enter the following lines in a terminal and hit enter after each one. Report back with any errors you encounter.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by verucasalt on 2011-09-30
ok....

i did that, it seemed to go fine, but now there's a license agreement on the terminal... how do i "tell" it ok?

"Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; TrueType core fonts for the Web EULA                                        
 &#9474;                                                                             
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                           
 &#9474;                                                                             
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement         
 &#9474; ("EULA") is a legal agreement between you (either an individual or a        
 &#9474; single entity) and Microsoft Corporation for the Microsoft software         
 &#9474; accompanying this EULA, which includes computer software and may include    
 &#9474; associated media, printed materials, and "on-line" or electronic            
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your        
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be      
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of        
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                            
 &#9474;                                                                             
 &#9474;                                                                             
 &#9474;                                  <Ok>

---

### Post by verucasalt on 2011-09-30
hey nevermind, i apreciatte ur help, i'm cruising back to good old windows XP....):P

i apreciate ur help, though...


( linux, u guys need to simplify, like really... )

---

### Post by Stray Wolf on 2011-09-30
> **verucasalt said:**
> ok....

i did that, it seemed to go fine, but now there's a license agreement on the terminal... how do i "tell" it ok?

"Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; TrueType core fonts for the Web EULA                                        
 &#9474;                                                                             
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                           
 &#9474;                                                                             
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement         
 &#9474; ("EULA") is a legal agreement between you (either an individual or a        
 &#9474; single entity) and Microsoft Corporation for the Microsoft software         
 &#9474; accompanying this EULA, which includes computer software and may include    
 &#9474; associated media, printed materials, and "on-line" or electronic            
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your        
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be      
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of        
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                            
 &#9474;                                                                             
 &#9474;                                                                             
 &#9474;                                  <Ok>

Arrow keys should highlight  "yes" or "no", then enter or space bar should select it.  While you're at it you should check out the "natty guide" here:[http://ubuntuguide.org/wiki/Ubuntu:Natty](http://ubuntuguide.org/wiki/Ubuntu:Natty) - mainly for future reference.  Sometimes flash may act funny and you have to purge gnash and swf.  Hopefully, yours works fine out-of-the-box.  But the guide should help you find other proprietary plugins like java and how to install them if the need should arise.

---

### Post by Stray Wolf on 2011-09-30
> **verucasalt said:**
> hey nevermind, i apreciatte ur help, i'm cruising back to good old windows XP....):P

i apreciate ur help, though...


( linux, u guys need to simplify, like really... )

Windows prolly wouldn't seem that simple if you were new to it.  There's always a learning curve with something new.

---

### Post by verucasalt on 2011-09-30
my point was why doesn't linux come with flash in the first place?


anyways, after reboot seems that flash is working :)
apreciate u guys's help  ;), thanks

---

### Post by wildmanne39 on 2011-09-30
Hi, there are packages and drivers that are not installed by default for legal reasons.
Thank you

---

### Post by bodhi.zazen on 2011-09-30
> **verucasalt said:**
> my point was why doesn't linux come with flash in the first place?

For the exact same reason windows does not come with flash either, lol

If you took the time to read the license issues that are displayed when you agree to use windows, flash, etc, rather then just blindly click "yes" or "ok" you would understand.

---

### Post by dwasifar on 2011-10-01
> **verucasalt said:**
> my point was why doesn't linux come with flash in the first place?

Some distros do.  There are legalities surrounding proprietary formats like Flash, audio/video codecs, hardware drivers, and other stuff.  Some distros play it safe with those things and ask the users to install them for themselves; other distros are okay with it.

If you want a distro with more of those things preinstalled, I suggest you try Linux Mint or Pinguy OS.  They're both Ubuntu derivatives, so most of what you've already learned about Ubuntu will still be useful to you.

---

