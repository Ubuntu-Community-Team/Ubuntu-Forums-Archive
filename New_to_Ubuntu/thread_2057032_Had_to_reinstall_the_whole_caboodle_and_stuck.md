---
title: "Had to reinstall the whole caboodle and stuck"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-09-12
Came home tonight to do do some stuff on the laptop and the whole thing was mad. There was no way I could get Ubuntu 12.4 to work at all- not even in restore mode.  No use trying to copy it all because there was so much which seemed to be numbered 1-44  and it was at 44 it stopped.....I have no idea if that means anything to anyone.

In despair I reinstalled and lost everything-very annoying in terms of downloads and redoing libre office but I tend to email myself important files.

But why would it suddenly get the hump and go mad like that? 

Various things I need help with so will do a thread for each.

J

---

### Post by anewguy on 2012-09-12
Too late for your old data, but something to keep in mind for future problems:

besides a system (mounted as "/") partition and a swap partition, set up a separate partition and select it to mount as "/home".  If you lose Ubuntu you can reinstall and all your data will remain that you kept in your home folder - including downloads, etc..  You might still need to reinstall packages, but at least your data would be preserved.

Then there's the old proverbial "you do backups, right?".  Don't feel bad there - a lot of us sort of skip that along the way - and as one user has in their signature for the forum: if you don't back up your important data then it isn't important data.  ;)

---

### Post by Jackalyn on 2012-09-12
> **anewguy said:**
> Too late for your old data, but something to keep in mind for future problems:

besides a system (mounted as "/") partition and a swap partition, set up a separate partition and select it to mount as "/home".  If you lose Ubuntu you can reinstall and all your data will remain that you kept in your home folder - including downloads, etc..  You might still need to reinstall packages, but at least your data would be preserved.

Then there's the old proverbial "you do backups, right?".  Don't feel bad there - a lot of us sort of skip that along the way - and as one user has in their signature for the forum: if you don't back up your important data then it isn't important data.  ;)

Thanks - because the stupid network manager played up I couldn't get here to get that info earlier...but my emails to myself with the files are a back up so it is not as bad as when my ex husband met me in a bookstore and told me he had managed to (in trying to put something right, delete my entire thesis........(not why we divorced lol), I don't remember how I got that back -but that way in the days of the imac.

I will copy and paste and email myself your info just in case!

J

---

### Post by newb85 on 2012-09-12
> **anewguy said:**
> Too late for your old data, but something to keep in mind for future problems:

besides a system (mounted as "/") partition and a swap partition, set up a separate partition and select it to mount as "/home".  If you lose Ubuntu you can reinstall and all your data will remain that you kept in your home folder - including downloads, etc..  You might still need to reinstall packages, but at least your data would be preserved.

Then there's the old proverbial "you do backups, right?".  Don't feel bad there - a lot of us sort of skip that along the way - and as one user has in their signature for the forum: if you don't back up your important data then it isn't important data.  ;)

Even if your /home isn't on a separate partition, when your system becomes unbootable, it's usually possible to boot from a LiveCD, mount your / partition, and browse to your home folder.

---

### Post by anewguy on 2012-09-12
> **newb85 said:**
> Even if your /home isn't on a separate partition, when your system becomes unbootable, it's usually possible to boot from a LiveCD, mount your / partition, and browse to your home folder.

Very true.  I'm just thinking about the reinstalling issue, or for that matter, installing a new release and having problems.  Your data is still safe - it's just the OS itself you'd be messing with.

Dave ;)

---

### Post by anewguy on 2012-09-12
> **Jackalyn said:**
> Thanks - because the stupid network manager played up I couldn't get here to get that info earlier...but my emails to myself with the files are a back up so it is not as bad as when my ex husband met me in a bookstore and told me he had managed to (in trying to put something right, delete my entire thesis........(not why we divorced lol), I don't remember how I got that back -but that way in the days of the imac.

I will copy and paste and email myself your info just in case!

J

oooooooooo, so if the wasn't why you got divorced, it must have been bad! ;)

---

### Post by opensshd on 2012-09-12
If you do get something running again, try using something like this:

sudo apt-get install scalpel

if you'd like to scan that disk for recoverable items. that data is not necessarily lost.

Re: [https://www.google.ca/search?q=restore+formatted+data+ubuntu&sugexp=chrome,mod=8&sourceid=chrome&ie=UTF-8](https://www.google.ca/search?q=restore+formatted+data+ubuntu&sugexp=chrome,mod=8&sourceid=chrome&ie=UTF-8)

---

### Post by anewguy on 2012-09-13
> **opensshd said:**
> If you do get something running again, try using something like this:

sudo apt-get install scalpel

if you'd like to scan that disk for recoverable items. that data is not necessarily lost.

Re: [https://www.google.ca/search?q=restore+formatted+data+ubuntu&sugexp=chrome,mod=8&sourceid=chrome&ie=UTF-8](https://www.google.ca/search?q=restore+formatted+data+ubuntu&sugexp=chrome,mod=8&sourceid=chrome&ie=UTF-8)

I'll remember that myself!

Thanks!
Dave ;)

---

### Post by newb85 on 2012-09-13
> **opensshd said:**
> If you do get something running again, try using something like this:

sudo apt-get install scalpel

if you'd like to scan that disk for recoverable items. that data is not necessarily lost.

Re: [https://www.google.ca/search?q=restore+formatted+data+ubuntu&sugexp=chrome,mod=8&sourceid=chrome&ie=UTF-8](https://www.google.ca/search?q=restore+formatted+data+ubuntu&sugexp=chrome,mod=8&sourceid=chrome&ie=UTF-8)

Thanks for the scalpel tip.  It says it's filesystem-independent, but does it also scan through a borked Windows system?  That could have come in handy when my brother's Windows partition became unbootable.

By the way, did you really mean to link to a Google search page?

---

### Post by opensshd on 2012-09-13
Yah I did, I noticed my search turned up several good looking results, so I figured I'd post it.

I've only used recovery programs like that a few times, and quite some time ago. I do remember I was rather surprised and impressed with the results though.

I suppose anything you can retrieve from an accidental data loss is good news eh?

Interesting, I'm not exactly sure if it will scan a windows filesystem, worth a shot for sure.

---

### Post by jmore9 on 2012-09-13
I use a seperate partition and / or hard drive to store my data that i want to keep.  On the desktop I use a seperate drive and on the laptop i made a seperate partition from the os partition to keep my data on.

That way when i mess up the is by my tinkering i can reinstall and not lose anything.

---

### Post by opensshd on 2012-09-13
Yup, pretty much same as my setup. Four partitions - three operating systems, one common data.

It's still not enough to consider it safe however. I burn a lot of DVD's and try to copy the important stuff to another entirely different medium to eliminate the possibility of a single point of data failure.

All hard drives will eventually die, better backup first ;)

---

### Post by Jackalyn on 2012-09-13
> **anewguy said:**
> Very true.  I'm just thinking about the reinstalling issue, or for that matter, installing a new release and having problems.  Your data is still safe - it's just the OS itself you'd be messing with.

Dave ;)

Which I would of done if I had known, I could not of course, log in to find out, Can someone give me the idiots guide to making this partition thingy please. In laymans English. Thanks.

Actually I am pleased I have done fairly well with the new install and got a lot of it back. Just one file that I was editing is a nuisance-but as I said I had emailed most stuff to myself.

---

### Post by Jackalyn on 2012-09-13
> **opensshd said:**
> If you do get something running again, try using something like this:

sudo apt-get install scalpel

if you'd like to scan that disk for recoverable items. that data is not necessarily lost.

Re: [https://www.google.ca/search?q=restore+formatted+data+ubuntu&sugexp=chrome,mod=8&sourceid=chrome&ie=UTF-8](https://www.google.ca/search?q=restore+formatted+data+ubuntu&sugexp=chrome,mod=8&sourceid=chrome&ie=UTF-8)

Tried it and get this?

jacky@jacky-Aspire-6930G:~$ sudo apt-get install scalpel
[sudo] password for jacky: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jacky@jacky-Aspire-6930G:~$ ^C
jacky@jacky-Aspire-6930G:~$ ^C
jacky@jacky-Aspire-6930G:~$ 

I have no clue what is running to close down as as as far as I know nothing is....

---

### Post by Jackalyn on 2012-09-13
> **Jackalyn said:**
> Tried it and get this?

jacky@jacky-Aspire-6930G:~$ sudo apt-get install scalpel
[sudo] password for jacky: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jacky@jacky-Aspire-6930G:~$ ^C
jacky@jacky-Aspire-6930G:~$ ^C
jacky@jacky-Aspire-6930G:~$ 

I have no clue what is running to close down as as as far as I know nothing is....

and then it worked BUT..are microft trying to make it so nobody can use anything but them as I yet again have the screen frozen at:

 Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
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
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by oldos2er on 2012-09-13
Use the Tab key to highlight 'Ok' then press Enter.

---

### Post by newb85 on 2012-09-13
> **Jackalyn said:**
> and then it worked BUT..are microft trying to make it so nobody can use anything but them as I yet again have the screen frozen at:

 Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
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
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

if you say no, it simply won't install Microsoft's fonts.  This is the same EULA you'd have to agree to to manually download the fonts from their website.

---

### Post by Jackalyn on 2012-09-14
> **newb85 said:**
> if you say no, it simply won't install Microsoft's fonts.  This is the same EULA you'd have to agree to to manually download the fonts from their website.

Yes, I know what it is. My problem is that whatever I try to do to accept the terms, to say 'OK' it will not let me do it. I was using the keyboard etc.  Quite simply, I cannot get any further because no matter what I do I cannot say OK!

---

### Post by newb85 on 2012-09-14
Did you try oldos2er's last suggestion?

---

### Post by Jackalyn on 2012-09-14
> **newb85 said:**
> Did you try oldos2er's last suggestion?

No because the fonts miraculously appeared when I installed the JRE that libre was telling me I already had. I did that from the Ubuntu software thing. Might be useful to note it was JRE7 and not 6.

---

### Post by newb85 on 2012-09-14
You shouldn't use this thread as your catch-all.  If new problems or questions arise, first search for them in existing threads, and if you don't find any, start a new thread.

---

