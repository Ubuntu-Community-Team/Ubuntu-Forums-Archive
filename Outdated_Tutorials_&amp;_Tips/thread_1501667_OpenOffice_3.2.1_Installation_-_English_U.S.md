---
title: "OpenOffice 3.2.1 Installation - English U.S"
date: 2010-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by scouser73 on 2010-06-04
Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the Linux .deb file to your desktop

Once you have done that, extract the .deb file, 

OOo_3.2.1_LinuxIntel_install_en-US_deb.tar.gz

Then you'll see a file called OOO320_m18_native_packed-1_en-US.9502

You can remove the existing version of OpenOffice if you wish with this command: 

**> sudo apt-get remove openoffice*.***
 
Then **> sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/*.deb**

Then paste this command: 

**> sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9502_all.deb**

Once you've done that you'll find OpenOffice 3.2.1 in Office.

---

### Post by Aiolos on 2010-10-05
> **scouser73 said:**
> Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the Linux .deb file to your desktop

Once you have done that, extract the .deb file, 

OOo_3.2.1_LinuxIntel_install_en-US_deb.tar.gz

Then you'll see a file called OOO320_m18_native_packed-1_en-US.9502

You can remove the existing version of OpenOffice if you wish with this command: 

****
 
Then ****

Then paste this command: 

****

Once you've done that you'll find OpenOffice 3.2.1 in Office.


This worked like a charm, thank you very much. Erasure of 3.2 left 3.2 user preferences intact, which 3.2.1 assumed.

---

### Post by Aiolos on 2011-01-28
Scouser73

Successfully transposed 3.3 descriptors into your install command.  Substituting 330 for 320, 20 for 18, 9567 for 9502 and 3.3 for 3.2 in your command to integrate 3.3 components into the Ubuntu Debian menu structure failed.  Would you consider posting an updated menu-integrating command for this newbie?

Aiolos

---

### Post by Hagar Delest on 2011-01-28
No need to type the whole commands! Just open a terminal in the DEBS folder once it has been uncompressed and then run the sudo dpkg -i *.deb command line. Then cd to the desktop-integration folder and run again that same command line (use your arrow key to navigate the shell history).

---

### Post by Aiolos on 2011-01-31
Hagar,

Many things I do not understand, beginning with the inoperability of the Quick Reply button at foot of your message. Thanks for your note: I am astonished that anyone else was trolling in this pool.

I cannot find any folder in my file structure named "DEBS", except a folder in the break-out of the OOo tar.gz that I performed in my Desktop.  Suspect you mean system folder that contains deb apps.  Do not find a desktop-integration folder either, hidden or exposed.  Humor me: what might be the default path?

I foresee I will regret raising my hand after I have received the answer.

Aiolos

---

### Post by Hagar Delest on 2011-01-31
To use the quick reply feature of the forum, you've to click the little arrow bottom right of the last post.

In fact, once you've downloaded the archive (tar.gz), you right click it and uncompress it in the current folder. It will create a folder. Open that folder, you'll find a subfolder called DEBS. Right click it and select Open a terminal here (or something like that). Then run the dpkg command and so on. See also [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by canundrum69 on 2011-02-01
Can I assume that this method is good to put in OOo 3.3 as well?

---

### Post by Hagar Delest on 2011-02-01
Yes, of course, just adapt the names. But the TAB auto-completion trick should take care of that.

---

### Post by majoda on 2011-02-05
I have downloaded 3.3.0 and followed steps, extracted file. Don't have option to open this extracted file in terminal when I right click on the deb file. I can open file and open desktop intergration with GDebi, but all the other files wont open with GDebi.
Have Ubuntu 10.10.
Help appreciated, my abilities are copy and past.
Thanks
Ross

---

### Post by Hagar Delest on 2011-02-05
Don't right click a .deb file. Right click the /DEBS folder to have a terminal inside that folder. Then type the command line with dpkg.

---

### Post by majoda on 2011-02-05
How do I get the option to open with terminal?
If I right click folder I don't have an option to open with terminal or GDebi.

---

### Post by Hagar Delest on 2011-02-05
I've that option in my context menu in Nautilus. Perhaps it came with TweakUbuntu.

But it may be quicker to open a terminal and cd to the /DEBS folder with cd then type the first letters of the OOo installation folder and hit the TAB key.

---

### Post by majoda on 2011-02-05
If I open terminal through applications what do I type.
I do not know commands so copy and paste is my abilities.
Thanks 
Ross

---

### Post by Hagar Delest on 2011-02-05
Then copy/paste what is in the first post. Or follow the tutorial I've linked.

Everything has been said already. Chose the method that suits you the best.

---

### Post by majoda on 2011-02-05
In first post I had copied in terminal the text as is written and also with cd in front of text, did not work, not a directory.
Your link to open office step 4 I copied and past text in box did not work.
Ross

---

### Post by Hagar Delest on 2011-02-05
Indeed, I just checked and the first post is about 3.2.1. No topic on 3.3 yet it seems so you've to adapt the command lines or learn how to navigate the system with the 'cd' command...

---

### Post by majoda on 2011-02-05
I'll just resort to what is in ubuntu software centre.
Thanks for your help.
Ross

---

### Post by canundrum69 on 2011-02-05
I still haven't tried yet ... as soon as I have the free time at work though I do appreciate the feedback:popcorn:

---

### Post by canundrum69 on 2011-02-07
> **majoda said:**
> I have downloaded 3.3.0 and followed steps, extracted file. Don't have option to open this extracted file in terminal when I right click on the deb file. I can open file and open desktop intergration with GDebi, but all the other files wont open with GDebi.
Have Ubuntu 10.10.
Help appreciated, my abilities are copy and past.
Thanks
Ross


I had no problems with this except for one minor snafu which just takes a few seconds to correct
[I][SIZE=2][B]sudo dpkg -i ~/Desktop/OOO330_m20_native_packed-1_en-US.9567/DEBS/*.deb 			 		 	 	 
[/B][/SIZE][/I][B]Then:
	 		 			 				[SIZE=3]sudo dpkg -i  ~/Desktop/OOO330_m20_native_packed-1_en-US.9567/DEBS/desktop-integration/openoffice.org3.3-debian-menus_3.3-9556_all.deb  			 		[/SIZE]
[/B]
Thanks all for the info

---

