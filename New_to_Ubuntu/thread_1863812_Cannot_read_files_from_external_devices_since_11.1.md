---
title: "Cannot read files from external devices since 11.10 upgrade"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by Filthy Stockings on 2011-10-18
Since taking up the auto alerted UPGRADE TO 11.10 from 11.04, the latter which have run with great ease and satisfaction for 4 months, am finding SO MANY PROBLEMS.

This is major problem 1

Plugging in my camera memory card provides an icon on the vertical left of screen pop-out ['desktop'?] but whereas in 11.04 I could just right click and open it to reveal the various folders which I could then copy to folders on my PC, the card is being grabbed by MOVIEPLAYER and then it starts to play all and any AVI files on the card.

I cannot even SEE the folders of still photographs. I get a list of sub directories on the card but nothing can be opened without the MOVIEPLAYER starting to play the AVI files.

EVEN WORSE is plugging in my 1TB external hard drive, prompts the usual icon on the vertical toolbar BUT nothing can be read, just like with the camera memory card.

Furthermore I now get this message;

  	 	 	 	 	 	   *[COLOR=#000000][SIZE=3]No suitable decoder module:[/SIZE][/COLOR]*
 *[COLOR=#000000][SIZE=3]VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.[/SIZE][/COLOR]*
 *[COLOR=#000000][SIZE=3]No suitable decoder module:[/SIZE][/COLOR]*
 *[COLOR=#000000][SIZE=3]VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.[/SIZE][/COLOR]*
 *[COLOR=#000000][SIZE=3]No suitable decoder module:[/SIZE][/COLOR]*
 *[COLOR=#000000][SIZE=3]VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.[/SIZE][/COLOR]*
 *[COLOR=#000000][SIZE=3]No suitable decoder module:[/SIZE][/COLOR]*
* [COLOR=#000000][SIZE=3]VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.[/SIZE][/COLOR]*


[SIZE=1][COLOR=#000000]More alarming was that when I tried to then right click SAFELY REMOVE the whole PC froze, which has never happened with UBUNTU, and I had to force shut down and then reboot. I have not had chance to check if the valuable data on the external has been adversely affected.[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]
[/COLOR][/SIZE]
[SIZE=1][COLOR=#000000]Can anyone please help me sort this out.[/COLOR][/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1][COLOR=#000000]I am a novice so please excuse my lack of correct naming of elements etc.[/COLOR][/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1][COLOR=#000000]Would there be a way just to go back to 11.04? It worked so right for me and for the few general computing needs I have I cannot see ANY ADVANTAGE in 11.10, only major headaches and problems and a waste of a whole day trying to do what took me a few minutes of relaxed computing.[/COLOR][/SIZE]
[SIZE=2]
[/SIZE]
[COLOR=#000000][SIZE=3][SIZE=2]Sorry to be so negative but this is the reality for this previously UBUNTU impressed.[/SIZE]
[/SIZE][/COLOR]

---

### Post by Mark Phelps on 2011-10-18
I feel for you, really -- to the point that I have complained NUMEROUS times about Ubuntu NOT having a version rollback option -- which would help LOTS of folks who, like you, upgraded expecting the best, but in reality, got the worst.

Unfortunately, unlike with MS Windows, Ubuntu does not have the option to roll-back to a previous OS version.  The best you can do at this point, if you can't fix it, is to back off the files you want to save and reinstall 11.04.

---

### Post by fantab on 2011-10-18
You know, how much Ubuntu (or for that matter any other distro) supports and recommends Upgrade to a newer version, I, for one never support the view. Especially to major release version like 11.10, which uses Gnome 3.

I would suggest you reinstall 11.10 after backing up all your data. I too share partitions with Windows and all my External Hdd are NTFS and are working fine on with my 11.10. 

So your issue seems more like an upgrade issue. Just clean install now and everytime.

---

### Post by Filthy Stockings on 2011-10-25
Belated thanks for replies and advice....been so cheesed off with 11.10 upgrade disaster am loathe to even use the PC!

After many hours reading around the forum i can now appreciate that CLEAN INSTALL is the safest method for new OS but how was I to know that being only a novice?

Having 4 months of trouble free UBUNTU 11.04 use and within that accepting all offered UPDATES I just presumed that the same box offering UPGRADE would produce no problems.

BUT I am STILL STUCK!!

I have a 11.04 ISO ready to clean install, as many aspects of 11.10 UPGRADE are just of no use or help to me 

* hate the pop out launcher 
* BANSHEE freezes so cannot play my mp3s 
* VLC STILL grabs TRASH so cannot operate that BASIC function
* VLC STILL grabs anything externally installed [when I R CLICK to open their icon, as did without any problem in 11.04, VLC player starts to run any AVI file in the external HDD and I STILL cannot see a list of folders that I can add to/delete etc.]

So I CANNOT BACK UP whilst VLC prevents me from locating the EXTERNAL HDD locations onscreen, as my original request for help title stated.

Any ideas what I can do?

I am currently stuck with an OS with lots of bugs and have not been able to BACKUP for a week!!

Can I not just delete VLC [HOW?] and that would surely stop it interfering with my operations...that player is inferior to MOVIEPLAYER when I try to play a DVD and as never spotted it in my 11.04 version I resent its invasion into my UBUNTU life.

What has VLC ever done for me?

Thanks in advance

SA

---

### Post by Darren01 on 2011-10-25
Nothing constructive to say other than, (i) sympathies, and (ii), I'm in a similar position.

---

### Post by JayKay3OOO on 2011-10-25
Using unity right? You get the unity launcher on the left? (popout laucher?) 

Ok, to see your files click the ubuntu Icon at the top of this launcher.

A window opens, at the bottom of this window there are 4 icons, one of them being a house. Click the one that looks like a piece of paper. You should see a bunch of folders. Click one to open the file manager.

You can easily delete vlc. If you don't know where the terminal app or software center is then press ctrl+alt+F1 log in using your user name and pass.

type:

sudo apt-get remove vlc

Almost forgot. To get back to the graphical interface if you pressed ctrl+alt+F1 press Ctrl+alt+F6 or F7

---

### Post by Filthy Stockings on 2011-10-26
Apologies for belated reply and MANY THANKS for advice.

I have realised the DASH aspect of LAUNCHER but even following your advice re clicking on one of the folders via the PAPER icon, all it gets me is what appears to be yet another VLC associated page...even when I chose DOCUMENTS folder to click on...which have NO video/music/photo files within.

Surely VLC PLAYER is not the default FILE MANAGER?

Do you think that VLC has been corrupted or similar during the 11.10 UPGRADE?

So should I just delete it?

Also as BANSHEE, my preferred mp3 player on the PC, seems to have stopped functioning correctly [since UPGRADE it allows playlist to start playing but then screen dims and cannot pause or stop or move to a different track in playlist so only choice to just RED BUTTON quit] can one just find that programme and then re-install it OR do I have to delete the current non-working version first?

Thanks again for your time and assistance.

SA

---

### Post by coffeecat on 2011-10-26
> **Shia Asininity said:**
> 
Surely VLC PLAYER is not the default FILE MANAGER?

Do you think that VLC has been corrupted or similar during the 11.10 UPGRADE?

So should I just delete it?

VLC has been associated with opening a folder. Try this:

Right-click on the desktop -> Create new folder. Leave it as "Untitled Folder" - you will be deleting it shortly. Right click on the new folder -> Open with Other Application. Under Recommended Applications, does VLC show? If so, untick or delete it. Close the context menu. Delete the untitled folder.

---

### Post by Filthy Stockings on 2011-10-26
Thanks for reply. Sorry if appear stupid but where do I find the CREATE FOLDER option?

I went to HOME right clicked on DESKTOP icon and get options such as OPEN/COPY/PASTE etc but NO CREATE NEW FOLDER.

Am I looking in the wrong place?

---

### Post by Filthy Stockings on 2011-10-26
Sorry for being slow.....realised that if I opted for OPEN on DESKTOP that it then gave option to R/CLICK CREATE FOLDER so did as you advised.

Found that UNTITLED folder, thus created, was associated with VLC/BANSHEE/FILES so got rid of the VLC and then deleted the UNTITLED folder.

Then tried to open TRASH which since 11.10 UPGRADE had been prevented opening due to association with VLC. .......now it seems associated with BANSHEE!!

Any idea what might be happening? Should I remove BANSHEE from another CREATED UNTITLED FOLDER and just leave the FILES assocation?

What IS FILES?

Thanks for your advice.

UPDATE

Have just tried my CANON_DC camera memory card, which kept being associated with VLC and now when I try to OPEN it just launches BANSHEE!!

WHERE can I find the file directory for this, as was so easy in 11.04?

Hope someone can help on this 8 day old problem.

Thanks in advance.

UPDATE 2 1210

Followed your advice and removed BANSHEE association and now can see EXTERNAL DEVICE folders.................AT LAST!!! 8 DAYS of trying to get this sorted and who would think it was this simple.

THANKS TO ALL WHO HAVE READ AND HELPED.....SO APPRECIATED!!!

PS....How do I mark this problem SOLVED?

---

