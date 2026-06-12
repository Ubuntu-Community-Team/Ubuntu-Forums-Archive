---
title: "I'm lost straight away."
date: 2014-05-02
forum: New to Ubuntu
---

### Post by Robert_de_Kock on 2014-05-02
I'm already disheartened since I notice that few newbies actually get an effective answer to their questions here.
But let's try.

I'm trying Lubuntu as alternative to XP.
Made bootable thumb drive, no problem.
Dell Netbook will boot from thumb drive.
Machine will log on to wireless network. Can browse the Web.

Can't say I understand how to browse the local machine though. Where are my disks?

Anyway, first thing I want is join my own home XP workgroup so I can see the other files on my network. I find
[http://www.techrepublic.com/blog/linux-and-open-source/how-to-join-ubuntu-to-a-windows-workgroup/](http://www.techrepublic.com/blog/linux-and-open-source/how-to-join-ubuntu-to-a-windows-workgroup/)
"how to join Ubuntu to a Windows workgroup"

This tells me to
sudo apt-get install samba smbfs

This doesn't work, and after another hour or so of browsing I find that I shouldn't have put smbfs
but something else, I forget which. Whatever it means. However, machine appears to install samba.

Next I read

"Now it's time to open up the */etc/samba/smb.conf*file and look for the line:
workgroup = WORKGROUP

I finally succeed in getting an editing window and putting in the actual workgroup name.
But now there's no way I can get the file to save, and my evening is gone.

Sorry, this is taking too much out of me.

Listen, I was a mainframe programmer in 1970. I got my first PC in 1982. I went from DOS 1.0 to DOS 3.1 to 
Win95 to Win 98 to Win XP. I'm not afraid of a command line. Why can't I understand this thing?[/FONT] [FONT=tahoma]
Why does anything Linux appear so, well, inconsistent and whacky?

Cheers mates

---

### Post by Impavidus on 2014-05-02
> **Robert_de_Kock said:**
> I'm already disheartened since I notice that few newbies actually get an effective answer to their questions here.
But let's try.I think most get an effective answer, but not necessarily to their question. Peop[FONT=arial]le sometimes ask the wrong question.> 
Can't say I understand how to browse the local machine though. Where are my disks?Open your file manager. All partitions available to be mounted should be listed (on the left, if it's the same as Nautilus and Thunar, the file managers on other Ubuntu flavours). Click them to mount. They will be mounted at /media/something.> (...)
But now there's no way I can get the file to save, and my evening is gone.To edit files from /etc you need root permission. This means you have to run your text editor as root, not as your normal user. I don't know anything about samba, but plenty of people here do.> (...)
Why does anything Linux appear so, well, inconsistent and whacky?I always thought that Windows was inconsistent and whacky. But that may just be me. Linux is different from Windows and that's why I use it.> Cheers matesAnd welcome to the Ubuntu forums.[/FONT]

---

### Post by pfeiffep on 2014-05-02
Welcome to the forum @[**[COLOR=#000000]Robert_de_Kock[/COLOR]**]("http://ubuntuforums.org/member.php?u=1921215")

Unix and Linux are different for certain. 
Two caveats 
[INDENT]1) I have no direct experience with samba or connecting Linux to Windows work group 
2) below reference thread is old
[/INDENT]
[INDENT=3]try this [thread]("http://ubuntuforums.org/showthread.php?t=1169149")
[/INDENT]
 
Another thought - if the Windows work group is the machine that you booted Lubuntu try executing pcmanfm which I believe is Lubuntu's native file manager (I have minimal knowledge of Lubuntu)

---

### Post by claracc on 2014-05-02
I think your problem is you don't have permission to write the smb.conf file ( for this reason, you cannot save the file), you have to edit the smb.conf file begining with sudo in order to write the file, in a xterm will be:

```
sudo leafpad /etc/samba/smb.conf
```, you will be asked for your password, enter it and change the file in the way you have to. ( I am assuming you are using leafpad software to edit the file)

Always it is better to go to oficial documentation, because of this, I recommend you these two guides to install and configure samba to share network as you want:

[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

[https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)

No desperate, conversion from win xp user to lubuntu one will take you certain time, there is a learning curve which has to be passed becuase the two os are very different. Of course, much better ubuntu. Also, ubuntu fora are the better way to get advice, try to search in them.

---

### Post by buzzingrobot on 2014-05-02
> **Robert_de_Kock said:**
> I'm already disheartened since I notice that few newbies actually get an effective answer to their questions here.

I think most answerable questions are answered.  

If someone is insistent on trying to use Linux as if it is a Windows clone, some dissatisfaction is inevitable. 

> I'm trying Lubuntu as alternative to XP.
Made bootable thumb drive, no problem.
Dell Netbook will boot from thumb drive.
Machine will log on to wireless network. Can browse the Web.

Can't say I understand how to browse the local machine though. Where are my disks?


If this is "Live Mode" (you haven't said if you installed Lubuntu) then the local drives are, in my experience, identified in the file manager rather generically, usually by their capacity. 

That said, the Linux filesystem does not use the "C:", "D:", etc., nomenclature Windows inherited from DOS.  Unix/Linux file systems can extend across multiple physical drives.

> 
Anyway, first thing I want is join my own home XP workgroup so I can see the other files on my network. I find
[http://www.techrepublic.com/blog/linux-and-open-source/how-to-join-ubuntu-to-a-windows-workgroup/](http://www.techrepublic.com/blog/linux-and-open-source/how-to-join-ubuntu-to-a-windows-workgroup/)
"how to join Ubuntu to a Windows workgroup"



Probably best to look first at Ubuntu resources that address your version of Ubuntu, rather than turn to random and possibly outdated/wrong resources via Google.  

> 
Why does anything Linux appear so, well, inconsistent and whacky?


Because your frame of reference is something entirely different?

I hadn't used Windows for more than 10 years when I bought a new laptop last year.  I played with Windows for a few days before I replaced it. I couldn't find anything or figure out how to get anything done, either.

Linux is a Unix.  Windows is Windows.  They're pretty different.  Nothing wrong with staying with what we know and like. (I do.)  If you like Windows and want a migration path away from XP,  Win 7/8 are there.

---

### Post by 3rdalbum on 2014-05-02
Part of your problem is that you are following a guide from 2010, on a Linux distribution from 2014. Unlike in the Windows world where one version of the operating system can be "the latest" for seven years, Ubuntu changes rapidly. Following a Linux guide from 2010 is like following a Windows guide from 1998.

Another part of your problem is that the guide describes setting up your computer as a Samba server. From my understanding, that's not what you are trying to do. You already have a server, you just want to view the files on it.

The last part of the problem is that the guide assumes the kind of knowledge that a Linux user would have already if they wanted to set up a server, and you simply don't have that knowledge. I'm not saying that you need the command-line to use Samba (you actually don't) but this guide seems to think that you do. Perhaps as a former DOS user and a current Windows XP user you are not familiar with the concept that your user account should be unprivileged, but with the ability to escalate to 'root' or 'admin' on-demand. That's the way Ubuntu, Mac OS X and Windows Vista and above work. It's central to why Linux is so much more secure than Windows XP, and if you want to manually poke around system files you'll need to understand it. You might find that you don't need to poke around system files manually.

I'm unfortunately not a Lubuntu user so I can't tell you exactly how to connect or how to troubleshoot if things aren't going right. On Ubuntu I just open up my file browser and click "Browse Network" on the left-hand side of the window, and the available workgroups pop up and I can just double-click and navigate like that. Lubuntu doesn't have anything like that?

---

### Post by bapoumba on 2014-05-02
> **3rdalbum said:**
> 
I'm unfortunately not a Lubuntu user so I can't tell you exactly how to connect or how to troubleshoot if things aren't going right. On Ubuntu I just open up my file browser and click "Browse Network" on the left-hand side of the window, and the available workgroups pop up and I can just double-click and navigate like that. Lubuntu doesn't have anything like that?
PCManFM > Edit > Preferences.

---

### Post by Sir_Ismicoo on 2014-05-02
I can't really help with your Samba issues as I don't use it. I don't use Windows so I prefer NFS. However generally speaking, anything outside of /home/Your_User_Name/ will require root privileges to change. This is to prevent just anyone from messing about with your computer. To gain root access on the command line you use the sudo command. When you do so, it will ask for your password but when you enter it, it will look like nothing is happening. 

The Linux file system is different to DOS / Windows. [Here]("http://tuxradar.com/content/take-linux-filesystem-tour/") is a somewhat light-hearted introduction to it as published in Linux Format magazine a couple of years ago. 

As to why things seem wacky and inconsistent, that would be because you are not used to the Linux way of doing things. I feel the same when I have to use a Windows based computer these days,  but still remember how odd Linux seemed when I first made the switch. Take a deep breath, and accept that Linux *is* different which *will* entail a learning curve and also remember that you were not born with DOS / Windows expertise; that you gained it over many years.

I haven't been a member here long, but it seems to be a friendly place so don't worry about asking questions.

---

### Post by grahammechanical on 2014-05-02
You tell us we are not helpful and then you ask for our help. That is wacky!

---

### Post by Robert_de_Kock on 2014-05-02
Another thing I shall need to get used to is how people feel a sense of ownership. My apologies, Grahammechanical.

---

### Post by Robert_de_Kock on 2014-05-02
Thank you Sir_Ismicoo. I see I need to work on getting used to things, as they're far more different than I thought. I'm taking the light-hearted tour right now.
Kind Sir, just to drift away from the original query, one of several reasons why I want to familiarise myself with Unix is that I maintain and fix the computers of a few mostly elderly XP-using friends. So far I have told them not to worry about the cessation of automatic updates from Microsoft as I have never noticed those to do any good anyway. However in due course they will need to change over to *something*. These people have simple computing needs, and I doubt whether any of them care about the file system, but it is very important for them that *nothing* changes that they can see. For instance I made them switch from Outlook Express to Thunderbird and most of them ended up in therapy. Can this be done using Linux?

---

### Post by SeijiSensei on 2014-05-02
One convenient trick that some file managers like Dolphin and Nautilus support is the ability to access SMB shares by writing a URL like this into the address bar:
```
smb://server/share
```
You'll be prompted for a Windows username and password if required.

I don't know whether this works with PCManFM.  I usually run KDE ("Kubuntu").  On other flavors like Lubuntu I install the KDE file manager Dolphin from the Ubuntu repositories.

As for the general problem of transition from one set of computing metaphors to another, I find a lot of older users rely on rote to accomplish tasks:  "click this, then press that, then ...."  That makes it very hard for them to move to another system.  If they had been taught the reasons to click, press, whatever, the transition would be much smoother.   I bet the problems with moving from Outlook to Thunderbird had something to do with this rote approach to computing.

Perhaps it's too late for your friends to start thinking in terms of tasks rather than mouse-clicks, but I'd encourage you to give it a try.  What do you need to do in an email program?  Well, reading your mail is pretty obvious in Thunderbird; the inbox is open by default.  Folders have the same meaning and are located in the left pane; I think Outlook looks the same.  What else do you need to do?  Write a message?  Press the "write" button.  Open the address book?  Click the "address book" button.  People can navigate a computer much more effectively if they start with thinking about what they want to do, then looking for a mechanism that enables them to do it.

 I'm almost 65, by the way, and know some people like the ones you describe.

Oh, one other thing.  Despite your disdain for security updates, I *strongly* recommend that everyone you know update today to [fix the Internet Explorer bug]("https://technet.microsoft.com/library/security/ms14-012").    This bug is so severe that Microsoft has [even released a fix for XP machines]("http://www.pcworld.com/article/2150248/microsoft-backs-down-will-fix-internet-explorer-vulnerability-even-on-windows-xp.html") despite its support having ended.  But "just this once," though.

Even better, they should fix the bug then switch to Firefox.

---

### Post by buzzingrobot on 2014-05-02
> **Robert_de_Kock said:**
> ...I made them switch from Outlook Express to Thunderbird and most of them ended up in therapy. Can this be done using Linux?

Well, there's no Outlook in Linux. Microsoft wants you to buy Windows to use it.  Their online webmail offering, whatever it's called this month, should work fine. 

The Zorin distribution offers an interface that purports to be very Windows-like, if that's a sticking point for the folks you help out. The individual applications, of course,will still look and work as they do elsewhere in Linux.

---

### Post by QIII on 2014-05-02
Frankly, I am a bit offended that you say that few newcomers get good answers here.  Most of us spend many hours a day doing just that -- for free.

If you were a mainframe programmer in the 70s you should find Linux very consistent, as I did from a Unix background in the 70s.

Smart remarks like "had to go to therapy" aren't conducive to getting help.

I would suggest that if you want help, it is best not to prod the *volunteers *who spend time here helping people.

Please take care to modify your attitude appropriately.

---

### Post by pfeiffep on 2014-05-02
> **Robert_de_Kock said:**
> Thank you Sir_Ismicoo. I see I need to work on getting used to things, as they're far more different than I thought. I'm taking the light-hearted tour right now.
Kind Sir, just to drift away from the original query, one of several reasons why I want to familiarise myself with Unix is that I maintain and fix the computers of a few mostly elderly XP-using friends. So far I have told them not to worry about the cessation of automatic updates from Microsoft as I have never noticed those to do any good anyway. However in due course they will need to change over to *something*. These people have simple computing needs, and I doubt whether any of them care about the file system, but it is very important for them that *nothing* changes that they can see. For instance I made them switch from Outlook Express to Thunderbird and most of them ended up in therapy. Can this be done using Linux?
Therapy has nothing to do with OS selection :) . 

Thunderbird is available in Linux as are automatic updates if configured correctly. The software updater prompts when updates are available and provides a selection to upgrade now or later. Most Linux upgrades do NOT require restarting the machine.  
User's bookmarks from IE can be easily imported into either Chromium or Fire Fox. I've found that with a bit of patience Libre Office is a more than adequate Office Suite. For those of your support folks who might need financial software I've found the online Mint version by Quicken very adequate. For tax preparation Tax Act has an online version.

Just a bit of friendly advice - try focusing on what can be done and how to do it rather than looking for differences. I suggest that since I, too, came from CPM, DOS, and mainframes - looking for similarities and helped me quite a bit.

Good luck with your venture into Linux support!

---

### Post by Atitudes on 2014-05-02
> **Robert_de_Kock said:**
> I'm already disheartened since I notice that few newbies actually get an effective answer to their questions here.
But let's try.

I am going to be completely honest, the rest of the post I don't understand much. That is because I am such a NOOB in these kind of matter and I am still asking myself why I went to chemistry instead of computing... Anyway, I also grew with first versions of DOS and if I recall, another operating system with something about, lets say, 40 "amazing" diskettes to transfer the required data... Something almost unthinkable to an ordinary child nowadays, believe me, I tried (I still have the diskettes :))

As a newbie, I can confirm I was never left unanswered. It sometimes require a lot of patience and reading but I always got there, following the kind (and more helpful than I) members of this forum helping each other. In fact, I think I only started a post once and of course, because I had screwed up. After some helpful answers, someone helped me more in detail to finally find out AlsaMixer was "tricking" me... This is kind of my personal testimony since 2009, I only register the forums around 2012 mostly to search easier :p ). Followed Ubuntu since 2009, completely switched in 2011 and happy ever after!! I take the opportunity to leave a huge thank you to everyone in this very helpful forum.

I really had fun reading some threads in this post, I really laughed pretty hard!! Specially because of the Outlook/Thunderbird issue. It is amazing how certain people really are unreceptive to change, I see that every day. In fact, I am myself also in chains, like them!! I am very receptive to others, but since everyone likes MS the best, well...MS it is all the way. Personally, I daily use some awesome features from Ms Office (One Note is something new to me and helpful in my case for example) combined with other more specialized software and it works pretty smoothly . Among these "specialized software", although I am sure a great percentage were developed under some Linux software, I am really proud of finding about 75% of it is executable under any Linux running machine. Some of them are really hard to install but I keep music for my "Home" and sadly MS for my "Work". 
That said, I am sorry if you got bored reading this but I certainly enjoyed reading everything (even the parts I didn't get :cool:) On the other hand, try "forcing" a bit and suggest a better therapist ;) 

Cheers!

---

### Post by ian-weisser on 2014-05-02
> **Robert_de_Kock said:**
>  These people have simple computing needs, and I doubt whether any of them care about the file system, but it is very important for them that *nothing* changes that they can see. For instance I made them switch from Outlook Express to Thunderbird and most of them ended up in therapy. Can this be done using Linux?

Can user interface changes be eliminated? No...unless they want to use a command-line interface. From your description, that seems unlikely.

Can user interface changes be minimized? Yes, reduced to major changes every five years using LTS releases of Ubuntu. However, the change then may be quite abrupt and briefly annoying. Some changes, like browser interfaces, will continue to change frequently.

Can user interface changes be reduced to minor changes at regular intervals to prevent the LTS chasm? Yes, generally by using the semiannual releases of Ubuntu instead of the LTS.

I think you have discovered that a *software strategy* should guide distro and software selection. How much change do you want, and when? How much control? And how much administrative headache do you want to accept in exchange for that control?
Example: Do you want to be in control of the mail application's user interface, or will you cede that to, say, a webmail provider in exchange for the storage and portability benefits?

The wide range of Ubuntu applications available (and the even wider range of Linux applications available) make those choices available to you.

---

### Post by whitesmith on 2014-05-02
> **Robert_de_Kock said:**
> Why can't I understand this thing? Why does anything Linux appear so, well, inconsistent and whacky?It **seems** inconsistent and wacky only because you come from a different background. Windows would have you list the files in a directory by CD-ing to it, then doing a **dir**ectory. In Linux you do the same by doing a **l**i**s**t. This is not an inconsistency but a difference. To appreciate Linux you must discard preconceptions and approach variances with an open mind. (See, above all, the first link in my sig line.) Linux people, a subset of *nix users, understand that Linux can never be understood by comparing it to Windows. Ours is an OS designed by two immensely talented fellows from Bell Telephone Laboratories in 1968-9. Windows, many of us think, is the wailing of mercenary children from the late 1980s. Yes, Windows is more popular, just as today's twerking "artists" are more popular than, say, Bach, Beethoven or Brahms. But gyrations make no contribution to immortality. You are clearly a thoughtful, intelligent person. I urge you to learn Linux by, first, reading and absorbing the first link in my sig line. Each step along your journey will carry you tso a higher level of understanding and appreciation.  I promise that, given a few months (possibly weeks) or less, you will never return to that OS from the Pacific Northwest. Cheers from one who admits to bias.

---

### Post by mastablasta on 2014-05-03
outlook? there is evolution mail (with a very similar look)
if they were using calendar it can be added to Thunderbird with plugin (e.g. lighning plugin)
there is alo Kmail (for KDE). 

anyway most email clients and webmail interfaces are rather similar if not the same in design. menu on the left, send, address button, email on the right...

Samba is used to access windows drives in network not internal drives. internal drives are porbably mounted using their volume label. they can also be recognised by size.
linux drivers:
/sda1 - first disk, partition 1
/sda2 - first disk, partition 2
/sdb1 - second disk, partition 1

hard disks are marked with sd and letter, parittions are with numbers.
cd/dvd drives and floppies are marked differently

---

### Post by Robert_de_Kock on 2014-05-04
Thank you all for your valuable comments. For now my problem is **[solved]**  though I don't yet quite understand how. What I did was to boot a live  Xubuntu rather than Lubuntu, no extra installs or other adaptations. It  turns out that the File Manager of that distro shows "network" exactly like  XP has "my network places." You then just click through to all the  other machines on the Windows network. This is very good as I can now  start experimenting with Linux applications on known data. Expect me  back here though.

---

### Post by Robert_de_Kock on 2014-05-04
My apologies. One does get frustrated.

I had no previous exposure to X systems. My 1971 etc. experience was punch card in, punch card out, carry the output stack to an offline printer to get readable output for your client. There was one CRT terminal for the operator, with whom you went to sit through the night hoping to insert program deck as gaps between production runs appeared. There was nothing interactive, nor anything remotely like Unix. We were involved in installing a roomful of interactive Teletype terminals, that was a brand new development, but those ran Basic only. Got back into programming from 1982 onwards and all was PCs, DOS etc. Then became a user. Now I'm semi-retired and can't afford expensive MS stuff and unnecessary hardware upgrades anymore.

I need to tell you - my bad - that I don't know what **code** and **/code** mean. Another question is why my replies sometimes end up at the top of the topic, and sometimes at the bottom. But never mind, the immediate issue has been solved.

---

### Post by JeQhdMD on 2014-05-04
On a netbook, you probably need to stick to a lighter desktop environment such as provided by Lubuntu or Xubuntu.   Between the two, I find Xubuntu more intuitive although not quite as fast as Lubuntu .  

Also, there are many good Youtube tutorials on Linux via a couple dozen channels.   Even "NixiePixel" has a video explaining the basic Linux (similar to Unix) file system.  Just take your time and peruse those.   It took me a couple months (even with some Unix admin background) to get fully up to speed with Linux.   Now, I find Windows both confusing and especially "annoying."

---

### Post by claracc on 2014-05-04
> **Robert_de_Kock said:**
> Thank you all for your valuable comments. For now my problem is **[solved]**  though I don't yet quite understand how. What I did was to boot a live  Xubuntu rather than Lubuntu, no extra installs or other adaptations. It  turns out that the File Manager of that distro shows "network" exactly like  XP has "my network places." You then just click through to all the  other machines on the Windows network. This is very good as I can now  start experimenting with Linux applications on known data. Expect me  back here though.

Please mark the thread solved with thread tools button in the top right of the page, to help other people.

About the Code or /code you ask in following comment, it means the commands or instructions writen in ubuntu console ( xterm, which you can run with keys ctrl+alt+t, as ms-dos console) to perform tasks in linux instead of using the graphic interface software (GUI). See: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by buzzingrobot on 2014-05-04
Samba is the standard Linux suite for dealing with Windows networks.  I run neither Xubuntu or Lubuntu, but, since it is intended to be lightweight system targeting older or less capable hardware, perhaps Lubuntu just doesn't use Samba by default.

File managers won't see network devices unless something provides that interface.  In Linux, it's Samba. I assume XP launches something by default, enabling its "network places" gizmo.

---

### Post by bapoumba on 2014-05-04
> **buzzingrobot said:**
> Samba is the standard Linux suite for dealing with Windows networks.  I run neither Xubuntu or Lubuntu, but, since it is intended to be lightweight system targeting older or less capable hardware, perhaps Lubuntu just doesn't use Samba by default.

File managers won't see network devices unless something provides that interface.  In Linux, it's Samba. I assume XP launches something by default, enabling its "network places" gizmo.

```
apt-cache policy samba
samba:
  Installed: (none)
  Candidate: 2:4.1.6+dfsg-1ubuntu2

```
Not installed on lubuntu by default indeed..

---

### Post by SeijiSensei on 2014-05-04
Not having Samba installed doesn't mean you can't browse SMB shares on other machines.  As I wrote above, you can use smb://server/share URLs in a file manager like Dolphin.  I removed both samba and smbclient from this client machine and could still open shares on my server running samba.

I particularly like Dolphin's support of fish:// URLs that make a connection over SSH.  It makes copying files to and from my remote web server trivially easy.

---

### Post by bab1 on 2014-05-04
> **SeijiSensei said:**
> Not having Samba installed doesn't mean you can't browse SMB shares on other machines.  As I wrote above, you can use smb://server/share URLs in a file manager like Dolphin.  I removed both samba and smbclient from this client machine and could still open shares on my server running samba.

I believe that the rest of the samba client routines are still on the host.  See the contents of the [samba-common-bin]("http://packages.ubuntu.com/trusty/samba-common-bin") package.  The package is install by default on all recent Ubuntu distros.

---

