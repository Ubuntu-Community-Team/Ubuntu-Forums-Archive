---
title: "WINE apps not showing up in 'Uninstall Wine Software' box"
date: 2015-03-01
forum: New to Ubuntu
---

### Post by penny3 on 2015-03-01
I installed ADE and KOBO from Wine to try and get things set up to download ebooks. ADE is on my desktop but doesn't recognize my device (have done the required 'persistant path' thing and all but this is another frustrating story altogether). Decided I would uninstall both programs and try again but when I to to the Dash and open up the Uninstall Wine Software icon, all that is showing is "Wine Gecko 32-bit' - no sign of ADE of Kobo. Where the heck are they so that I can uninstall them properly?

---

### Post by penny3 on 2015-03-01
After installing Wine and Winetricks, I downloaded ADE and Kobo (at least I thought I did!). As I am having problems getting ADE to setup properly, I thought I would do an uninstall and start over. However, when I go into the Wine 'Uninstall Wine Software' screen, all that is showing is 'Wine Gecko (32 bit)' - the apps I thought I downloaded don't show up there at all. I have the ADE icon showing on the desktop and, if I do a search from Dash, Kobo shows up as an application but it hasn't been launched yet. As there is nothing showing up under the Uninstall Wine Software screen, does that mean I can just send the ADE desktop icon to the trash bin and try installing it again? Also ... I run a 64 bit system and I see that Wine Gecko is 32 bit. Is this a problem/conflict? 

Thanks for any help here! If I can just get my system set up to download and transfer ebooks to my reader and download and transfer photos from my camera, I will be the world's happiest Ubuntu camper! These are the only two things that I need to work on my new Ubuntu desktop.

---

### Post by Mike_Walsh on 2015-03-01
Hallo, penny3.

You don't actually look in the 'Uninstall' section at all.....strange as it may sound. You need to go into your 'Home' folder, and, top left, click on 'View'. Then, check the entry that says 'Show hidden files'. You'll then see a whole load of extra directories (folders) and files, which have a '.' before them; this is how Ubuntu denotes hidden files.

If you look through them, you will find a directory named '.wine'. If you open this, then click on 'C:drive', I believe..... (it's been a while since I've needed to do this!) you'll THEN see a folder called 'Program Files', or something very similar. Open this, and you should find your programs & apps that you've installed. If you click on each one in turn, you'll find the '.exe' file, along with, somewhere round there, an 'Uninstall' option. Just click on this, and follow your program's uninstall procedure.

This is because, although Wine runs Windows programs, it's still a piece of Linux software.....and Linux stores various parts of the program files all over the place, in different folders, according to their function. And every single setting related to your personal apps & preferences, is always stored in your 'Home' folder; this is all to do with the multi-user nature of Linux.

Hope that helps. BTW, for enquiries about Wine-related stuff, you'll possibly get on better by posting in the 'Wine' sub-forum, in the 'Specialised Help' section. And always bear in mind that, although Wine works what amounts to a minor miracle, it's not the 'be-all & end-all' as far as Windows programs are concerned. Some stuff works better than others; some stuff won't work at all, or very poorly. Much depends on the version of Wine used, and the support given to each Windows program by that version. 

If you want to find out whether a Windows program will work in Wine, look at the Wine App Database. I warn you, there's a LOT of stuff to work your way through! You'll need the 'Browse Apps' section when you get there:-

[https://appdb.winehq.org/](https://appdb.winehq.org/)


Regards,

Mike. :)

---

### Post by Bucky Ball on 2015-03-01
*Thread moved to **Wine**.*

Here tis. ;)

---

### Post by penny3 on 2015-03-01
Thank you, Mike. I am a total noob to Linux - it's a miracle I was even able to install Ubuntu as a duel boot OS on my laptop. 

Have a couple of puzzling things happening though. First - when I did what you suggested, I see that there are program files in .wine - Program Files and Program Files(x86). Not sure why but, when I looked for the apps I wanted to uninstall, neither of them are showing up there. Also tried uninstalling through the Terminal and it says that they weren't installed so it can't uninstall them. Boy, am I confused now! 

I even tried totally uninstalling Wine and Winetricks using the following command:
sudo apt-get remove wine1.6.2 winetricks (system said it couldn't find it) so them tried
sudo apt-get remove wine winetricks (said it wasn't installed ...)

I am still learning commands mostly by searching for them in the forum or on the internet so I could easily have typed in the wrong format? 

I am totally confused now. If I can access Wine through the Dash, why can't the system find it to uninstall it?

---

### Post by penny3 on 2015-03-02
As I appear to be having some weird issues re installing/uninstalling apps, could someone please take a peek at this bootinfo summary and let me know if something looks weird with my Ubuntu install? This was installed as a duel boot system on my laptop. Thank you!

[http://paste.ubuntu.com/10497935/](http://paste.ubuntu.com/10497935/)

---

### Post by mastablasta on 2015-03-02
what would be the weird issue you describe? if they appear in Linux only, then boot info script won't help.

---

### Post by penny3 on 2015-03-02
I installed ADE and Kobo through Wine Tricks. When I couldn't get ADE to work properly, I thought I would uninstall and reinstall but couldn't find them anywhere even though I had an ADE icon on the desktop. Even the sudo apt-get command line couldn't find the app and said it wasn't installed but there is a folder in my Home folder called 'My Digital Editions'. Looked in .wine folder and neither ADE or Kobo were there either. Thought maybe something went wrong with the Wine install so decided to uninstall *that *and Wine Tricks and reinstall. The sudo apt-get remove command said Wine wasn't installed but it is certainly there when I open up the Dash and look for it. So I am wondering if I missed something when I installed Ubuntu in the settings or something that is causing these programs to be installed 'somewhere' other than where they are supposed to be.  It probably sounds preposterous but, with my level of 'non-expertise' in all things computer, it is quite possible that I have made some error in the install of Ubuntu somewhere along the line. This is a duel boot install. 

If I at least knew that the Ubuntu was installed correctly, that removes one element of 'what the ... is going on' in my mind. I have no problems doing the normal stuff like browsing or email - it is just these apps that are getting screwed up.

---

### Post by Bucky Ball on 2015-03-02
***Threads merged.***

Boils down to the same issue: Can't find apps downloaded in Wine. Bootinfo script won't help here. If everything's working ok at boot and you can boot all your installed OSs, then that's not it, and nothing to do with your lost apps/Wine issue (even if you could).

Open a terminal, type in 'ade' or 'kobo', then hit tab two or three times in succession. Might give a clue as to where they are. You could also do a search on the computer (I use Catfish to look for files, there is probably something else in Ubuntu).

---

### Post by Fincer on 2015-03-02
To get rid of an unlisted application, you might consider removing the whole wineprefix where you have your applications installed. This is not an option unless ADE/KOBO is the only stuff you have there. If you have any other installed Wine applications, do not delete your wineprefix.

As an alternative to the first option: Have you checked any native Windows tools such as regcleaner or something equal?

_**About the application**_

The application itself seems to work pretty well, according to [Wine Application Database]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=30928"). 

However, your device relies to USB connection, right?

Wine doesn't handle USB connections to be used between applications and external USB devices. There is a way to get your ebooks into the device but it's bit tricky. What's said on AppDB is as follows:

> The app does not recognize my ebook reader (a B&N nook), so I had to play around to get the book onto my reader.

The USB support for Wine is on its way, but there is hardly anything officially out there for external USB devices yet. I've not heard any news about the development of USB support for Wine for some time but you might take a look on the following link for details if you care:

[http://wiki.winehq.org/USB](http://wiki.winehq.org/USB)

Regards,
Fincer

---

### Post by Mike_Walsh on 2015-03-02
Hallo again, penny3.

Hmmmm. Unfortunately, Wine is a PITA at the best of times. AFAICT, it's an absolute nightmare to uninstall, too. Not something I've ever needed to do; as it turned out, the one, solitary Windows app for which I installed Wine has the coveted 'Platinum' rating, which generally means that it'll run without issues (it does, too..!) Before I actually installed Wine, I did a LOT of research, asked even more questions on here, and in other Linux-related forums, and generally made a real nuisance of myself in order to find out what I needed to know. You need an 'inquiring mind' to progress with Linux to any degree; you mustn't be afraid to ask questions (lots of them!).....but the end results are well worth it.

By the time you've finished, you'll have a system you can make sit up and dance...to YOUR tune. I hate to say this, but with Wine being the 'can of worms' that it is, you might be better off simply to re-install from scratch, and start afresh. I lost track of the number of times that I 'broke' my system, and had to re-install, in the early days.....but it's definitely the only way to learn. And you tend to remember your mistakes more clearly that way!

If you do that, before attempting to use Wine again, do your homework. Browse the Wine App Database; see what it says about the app you want to use, and what kind of ratings & reviews it's got. It'll also tell you what versions of Wine have been tested out with that application, and also on what distros the attempt was made. You may find you need to use one of the newer 'beta' versions of Wine, rather than simply using the version in the Software Centre. It'll involve installing the PPA for that version of Wine, so as to receive what support & updates may be available, but most of the blogs & tutorials on the web for this kind of thing (and there are HUNDREDS) will tell you how to add the requisite PPAs.

I can't really add any more than that, I'm afraid. Good luck with whatever you decide to do, and don't forget; we're one big happy family on here.....there's always someone who'll help you out of a muddle. And you'll need plenty of patience, too, if you're not that technically-minded.....but just persevere. It's worth it in the end.


Regards,

Mike. :)

---

### Post by penny3 on 2015-03-02
Thanks for the info, Bucky. Will try that 'tab,tab,tab' thing you suggested. 

And thank you, Mike, for the info on Wine. I actually did read a bit about it and knew that there have been issues with it sometime but, as I really wanted to get my ereader (Kobo) up and running on the system so that I could download books from the library, this seemed like the only way to get the ADE and Kobo apps that I needed. However this has now become a real hair-pulling issue. Am thinking of using the Kobo as a door stop these days and just going back to the old fashioned hard copy kind of books, 

I am seriously tempted to just drop the whole thing as everything else is working great. I hate having 'loose ends' out there but, if I never use Wine to install any more apps (highly unlikely at this point!), it truly is tempting to just forget it is even in there (or not). 

For now (unless you think that I really DO need to get this Wine thing rectified) I would really like to just leave sleeping dogs lie. Maybe just run an 'autoclean' command and see what happens. 

And, yes, I agree ... the Ubuntu community is really fantastic! Between this forum, online searches, YouTube and the 14.04 User Manual I downloaded, I couldn't have gotten this far. I really do not want to ever go back to Windows so will continue to plug away

---

### Post by Bucky Ball on 2015-03-02
Keep on pluggin'! Yes, once Wine is installed it is virtually impossible to completely eradicate all trace of it. You can, though, as you mention, just pretend it is not there. 

There are some ebook readers in Ubuntu. Calibre among a few others. Have a search in Software Centre for 'ebook'. Good luck.

---

### Post by penny3 on 2015-03-03
Hi Bucky - I've been eyeballing that Cailbre. Thanks for everyone's help here. Greatly appreciated. I know you haven't heard the last of me, though! LOL.

---

### Post by Mike_Walsh on 2015-03-03
Hi again.

Actually, I'd forgotten all about Calibre. I have it installed on a Puppy Linux laptop I've been working in for the last 2-3 months.....just haven't got around to setting it up, yet. So, unfortunately, I can't give you any feedback on how it works. Anyway, never having used an 'e-book' reader before, I wouldn't have a clue whether it's any better or worse than any other one.

All I know is, I've had my nose buried in one book or another, ever since I learnt to read at the very young age of 4...! And THAT was over 50 years ago, now...


Regards,

Mike.

---

### Post by penny3 on 2015-03-06
Thank you for your reply, Fincer. Sounds like you have hit the problem on the head re Wine and USB's. Even though I am not computer literate enough to even consider any work-arounds, it is good to know what the likely culprit is.

---

### Post by Bucky Ball on 2015-03-06
***Threads merged.***

... for the second time. That is three threads you've posted about the same issue. Please do not do this. One issue, one thread and pursue a fix there. If it is getting no attention DON'T post a new thread about it. BUMP the thread instead (but give it a reasonable amount of time as we are an international forum operating in many time-zones). Thanks.

---

