---
title: "My laptop is possessed by demons (daemons?)"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by harelb on 2013-04-21
I didn't even plan to make that pun - it really has been a headache as
if possessed by demons - only after starting to type that it did I
recall the "daemons" (see below). So I have an old and dying desktop at
home with ubuntu (Disclaimer: though I've used ubuntu for some years,
please assume I know *nothing* other than how to open a terminal..!)

In January I got a shiny new laptop (Samsung, 4GB RAM, 500GB drive,
and AMD "A6" processor). I solved the first "possession" all on my
own. What was that? Getting rid of the windows 8 and installing the
old Ubuntu (I had a CD from 2011 or so from the folks at osdisk). That
alone was like pulling teeth, with a good month putting the laptop
aside but by late Feb I had the laptop working just fine. I used it
probably ten times but again put it aside "until I have time to
upgrade" (my dread must have known something my conscious mind
didn't!)  until realizing it's almost April 2013 when support ends for
that version of Ubuntu..so I got my laptop, and clicked the updater
(that cardboard box icon thing in the command bar, "/usr/bin/updc" is
what it's aliased to on my desktop computer) to upgrade to
12.04...(my notes tell my terrible memory for names that it's "update manager")

What could possibly go wrong? Nearly brand-new laptop, that had the
earlier ubuntu running fine, a laptop I had not downloaded any
software (other than a few updates from that updc and putting
quick-launch icons at top bar) so no malware or clutter etc..like I
said what could go wrong? So when I had a full afternoon I clicked on
that button that "new version 12.04LTS is available!" and let it run..

Three or so  hours later it was done. I was not baby sitting the whole
3 hours of course..but other than item I. below it behaved as if things 
went smoothly.

Note: I hope it is item I. below so I include items II and following
just to give more background in case it helps confirm diagnosis of
what went wrong in I....because in the interest of time (and before my
desktop whose hardware really risks problems..overheat causing loss of
internet access) if you all think it would work to just re-do the
whole install of the entire OS, I'm happy to do that (except I can't
even log in any more, see last item..so I'd need to be reminded how to
boot in safe mode and then which url I can download 12.04LTS from) Ok:

I. During the install there were two times when I came back to peek at
progress and there were messed up dialog boxes. This was not always
the case; there were some normal, readable dialog boxes but two times,
the *entire* dialog boxes was displayed as if it was written in a
font whose entire alphabet consisted of a rectangular box: all the
"sentences" and even the place where I knew it must have meant to say
"ok"  was in those rectangles (I wish I could be 100% sure but I'm
only 90% sure I clicked on the lower-bottom button both times) I have
screenshots; I'll try to attach:

File1:  2013laptopubuntu-install.shutdownerror.jpg
File2:  other-ubuntu-install-error.P170413_18.08.jpg

So that's probably where things went wrong.

II. The first thing I noticed was initially things seemed to be
working ok except for the interface (I eventually got to GNOME
Classic) but really the first problem when when I tried to "Shut Down"
and got an error "A program is still running: GNOME Settings Daemon"
(this error, I'm sure, existed before I switched to GNOME classic
since I did not get the classic until after my first time shutting
down the laptop, and this error happened the very first time I shut
down) See:

File3:  laptop.ubuntu.install.error1.jpg

I eventually tried the strange suggestion of "lock screen" which was
suggested in that dialog box and sure enough it didn't help. Just
"Shut down anyway" or "Restart anyway" were the options I used.

[B] III. Error 1 below immediately, but eventually many  more errors:
[/B]
1. Firefox freezes whenever I right-click
2. Using mouse (rather than keyboard)on Terminal (which I use to ssh,
not just to diagnose) to File then "open tab" Froze the terminal..and
later froze the computer
3. Same for shift-control-t which supposedly does the same, but
initially (the first few times using the laptop; it's been 48 hours
and about 6-8  sessions using it along with about 25+ reboots;
sometimes many reboots to get one functioning session)
4.  Mouse or keyboard to firefox's menus or url box? Firefox
freezes...got it killed with xkill  initially but like errors, next
time it happened got worse and the system would eventually freeze the
system or else kills firefox but won't relaunch
5. Used Flash drive (in case laptop dies again since barely usable)
to type in some notes...mouse to File menu in notepad..no freezing up,
to "save as" no freeze...click "ok" THEN it freezes.. etc

B. Some errors happened some times but not others:

1. Alt-Tab to switch between windows...was working fine for a while
(while lots of other errors were showing up) but more recently, it
froze the laptop (I'm going by my notes but in most cases this means,
mouse will worked to move icon but can't click on anything, not even
"gears" menu to shut down)

well no point typing in a completely exhaustive list from my notes,
right?

IV. As of today (Saturday Apr 20) when I turned on the laptop...[B]can't
even log in! [/B]This is the first time its done that. You get the
vertical bar icon where the password is supposed to go, but keyword
doesn't work...mouse can move icon for mouse but can't click
anywhere...so can't log in.

Well there it is...the complete mess the "upgrading" from the old
ubuntu to 12.04 did on a new laptop :-(

As I said, if there's a 50% or better chance of it working, I'm more
than willing to let the laptop go for a few more hours just
re-installing all of 12.04 (more time for my laptop, but much less
time for me and you, than trying to fix each item in the list above)
If so, ignore II and III, and could someone remind me how to get to
log in (hopefully this won't fail too..) in safe mode and where to
download from...if very unlikely to work before other steps
(*shudder*) then pointers from you experts how to proceed instead of
trying to re-install 12.04, would be most appreciated!
Harel

---

### Post by fantab on 2013-04-21
The gist of your long "demon-possessed" prose is that you have a bad UPGRADE. No surprises there. Between 10.04 and 12.04 Ubuntu has undergone some major changes and personally I do not recommend Upgrade for the exactly the same issues you faced.

Download the latest version of Ubuntu, either 12.04 LTS or 13.04beta2, which is quite stable and due for release shortly. And do a Fresh and Clean install.

---

### Post by harelb on 2013-04-21
fantab - yes, and putting "upgrade" into the keywords for this post is one of the few things I got right it seems ;-)

I'll admit my "prose" is seldom brief, it really it an effort to avoid the "you didn't include enough info!" as much as my style hence my note that sections II and III can be skipped, but in bullet point:
[B]
1. As I mentioned in bold in IV, I can't log into my laptop any more: I get the login screen but keyboard doesn't work to type into the password field (mouse moves cursor but can't slick on anything) There's a keyboard key or several to hold down at once to get me into safe mode, I think? Otherwise I'm stuck at the login screen when I boot the normal way. 

2. Assume this can be done, once I am finally logged in again and hoping it doesn't freeze up for me before I finish following directions, assuming I "don't know how to do anything other than open a terminal" where exactly do I go (and any instructions not dead obvious) to download 12.04LTS? [/B]

Keep in mind even when I log in I **can't** right click in firefox **NOR** as I mentioned could I click in the url box nor use the file etc menus in firefox without the entire laptop freezing.just navigaging with left click to the correct url...which hopefully won't ask me to "right click and save" or right click anything..in order to be able to

Thanks for help from anyone on these two points so I can have my laptop back! :-)

P.S. this is not a separate question so much as curiosity to reduce my ignorance but what exactly is the difference between "downloading 12.04LTS" (so you can skip answering it if it's complicated)  versus what I attempted, "upgrade from [old version] to 12.04LTS" ..and that makes the latter so much less error prone? And should one then sometimes preemprively choose the latter on purpose whenever there are "major changes" we should just say "no thanks!" when "update manager" offers to? 

Thanks for anyone's advice on

---

### Post by fantab on 2013-04-21
Upgrade from 'Update Manager' to the next version works, usually. But since you have an 'older version' and I am assuming it to be 10.04, as you haven't told us what it is, its a big jump. For instance Ubuntu 10.04 used GTK2 while 12.04 uses GTK3, Gnome was at version 2 and it is now 3. These are a few 'major changes'. 'Upgrade' can go wrong, why I don't know. Perhaps because of conflicting replacements and leftovers.

Updates that update manager offers are different from version Upgrade. Updates are essential to keep your system upto date. So you cannot say "No thanks!" to updates. By Upgrade I mean a newer version of Ubuntu which released every six months for regular and two years for LTS versions. 

Most of your problems should get sorted out once you upgrade (doing a Fresh Clean install) to any Latest version of Ubuntu. Since you got a new laptop, are you sure that the "old ubuntu" would support new hardware? There can be issues and which you have...

You can download the latest version from: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) : If don't have another computer assessible then you can use your "older version' Ubuntu CD to boot from, connect to internet, download and create Latest Ubuntu Disk.

By the way, your new machine may have UEFI. It need special care when installing. Search the forums and you will find many threads about ['how to install ubuntu with Uefi]("https://help.ubuntu.com/community/UEFI"). Older versions did not support UEFI.

---

### Post by harelb on 2013-04-21
The new machine definitely did have UEFI...that was the reason it was like pulling teeth (well, a bunch of searching websites before I found the right combination of steps - there were more than one - to get it to work) to replace Windows 8 with the older ubuntu...finally found the CDs and they were 9.10 (gasp! but I'd have thought that update manager would be smart enough to notice my version is old and to either tell me "don't do it" or to take the extra time precautions to prevernt disaster..alas no, ;-)...yet I  <strike>have to assume</strike> would hope that since I turned off uefi berfore (when I got 9.10 installed after a lot of struggle) that it is still off now...even with 9.10 repalced (in some defective way) with 12.04 and with logging in being impossible...

so...hoping that is the case...I'll see if I can boot-from-CD from the 9.10...except, now that another quick google reminded me, the "hold down the shift key to reboot ubuntu in safe mode" is there a reason you don't recommend that and recomment boot-form-cd instead? I see my optoins in safe mode are:

1. ubuntu, with linux 3.2.0-40-generic-pae
2. ubntu.....3.2.0040...(recovery mode)
3. previous linux versions
4 memory test(memtest86+)
5. memory test (memtest86+, serial console 115200)

would item 2 or item 3 work as well or better than boot from cd?

---

### Post by harelb on 2013-04-21
"Updates are essential to keep your system upto date. So you cannot say "No thanks!" to updates. By Upgrade I mean a newer version of Ubuntu which released every six months for regular and two years for LTS versions. "

I understood this part, that is, the difference between the "regular"/routine updates, versus a whole new version of ubuntu (liike 12.04lts) what I meant what that this same program "UpdateManager" has (when there *is* a new version of ubuntu) has an "upgrade to 12.04LTS" button in the very same dialog box that has the button to "check for updates" and the button for "ok" to the usual (routine) upgrades..I just means that based on what you said, I should have said "no thanks" to that button (to using UpdateManager to get 12.04) - and to instead use ubuntu.com as you suggest now - to get 12.04 (and also *not* to say "no thanks" to the routine updates) Well I got in safe mode and if it blows up in my face I'll post here or try boot from cd...let me try the ubuntu.com url you gave..crossing fingers..

---

### Post by texaswriter on 2013-04-21
> **harelb said:**
> "Updates are essential to keep your system upto date. So you cannot say "No thanks!" to updates. By Upgrade I mean a newer version of Ubuntu which released every six months for regular and two years for LTS versions. "

I understood this part, that is, the difference between the "regular"/routine updates, versus a whole new version of ubuntu (liike 12.04lts) what I meant what that this same program "UpdateManager" has (when there *is* a new version of ubuntu) has an "upgrade to 12.04LTS" button in the very same dialog box that has the button to "check for updates" and the button for "ok" to the usual (routine) upgrades..I just means that based on what you said, I should have said "no thanks" to that button (to using UpdateManager to get 12.04) - and to instead use ubuntu.com as you suggest now - to get 12.04 (and also *not* to say "no thanks" to the routine updates) Well I got in safe mode and if it blows up in my face I'll post here or try boot from cd...let me try the ubuntu.com url you gave..crossing fingers..

I have always heard that LTS to LTS dist-upgrade should work.

---

### Post by harelb on 2013-04-21
Gosh, have you "always heard" that Verizon gives perfect service too and that it never rains on wedding days, from same source?

And gee golly thanks for the completely gratuitous insult...I should hope trolls don't stend 1/10 as much time as I have on this..I coudl suspect you're a troll (the claim that *anything* "always" works, as in 100% of the time, is not reality-grounded) or I coudl suspect that the ubuntu.com page is "trolling" me for suggesting I try the install-from-usb, only to be pointed at a page asking me to download a DOS/windows executable when I'm going from ubuntu...but you know what? I don't go making while assumptions about the motivations of people from a post of two..plus I'm "feeding" you but even replying, so never mind ;-) (no the "feeding" joke isn't assuming you're a troll, but pointing out the absurdity of arguing) I'll post update here as to how it goes

and I'm sure this is seen as "trolling" (since no one in the country doesn't have wireless or a router at home, right?) but I don't have wireless or a router so I literally am about to unplug the dsl connection from here and plug back into the laptop so I can download the .iso and see how things go..

will report back..

---

### Post by harelb on 2013-04-21
ok the safe mode seems to have gotten me a  somewhat stable laptop so I don't have to keep switching back to desktop to post here but other than that I don't seem to have any
idea what I'm doing...namely..I thought the url fantab gave, [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) would let me save to disk and double click that but it wants to save to a CD...nothing wrong from that but with everything else gone wrong i didn't want to assume my disk burner would work in this same mode version of ubuntu I'm in now...so I tried save to usb..took me to [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) which turns out is a DOC/windows executibe..but I'm on ubuntu...gave up and decided to let it save raw CD image or some worhds to that effect, and said ok...but it says it's 18 hours to burn and is  indeed super slow with 8MB so far downloaded..I think I know why...by the time I noticed I had already clicked ok but it said something like europe...I think it thinks I'm in europe and thinks that's where the nearest place to download from...so no wonder so slow (I've downloaded much bigger things/much faster) so I tried to kill firefox and see if it asks me again and if I can choose another location...nope, didn't work....so I'm stuk with 18 hours to download a cd image...no good..I'll try to erase browsing hist/cookies, reboot again in safe mode, and try again to download and see if it gives me a choice where to download from...

---

### Post by texaswriter on 2013-04-21
> **harelb said:**
> Gosh, have you "always heard" that Verizon gives perfect service too and that it never rains on wedding days, from same source?

I understand that you may be frustrated, but we are all here to help each other out.  LTS to LTS are supposed to work, but if it didn't than maybe saving your data and reinstalling might work. 

> **harelb said:**
> And gee golly thanks for the completely gratuitous insult...I should hope trolls don't stend 1/10 as much time as I have on this..I coudl suspect you're a troll (the claim that *anything* "always" works, as in 100% of the time, is not reality-grounded) or I coudl suspect that the ubuntu.com page is "trolling" me for suggesting I try the install-from-usb, only to be pointed at a page asking me to download a DOS/windows executable when I'm going from ubuntu...but you know what? I don't go making while assumptions about the motivations of people from a post of two..plus I'm "feeding" you but even replying, so never mind ;-) (no the "feeding" joke isn't assuming you're a troll, but pointing out the absurdity of arguing) I'll post update here as to how it goes

and I'm sure this is seen as "trolling" (since no one in the country doesn't have wireless or a router at home, right?) but I don't have wireless or a router so I literally am about to unplug the dsl connection from here and plug back into the laptop so I can download the .iso and see how things go..

will report back..

It is just my signature. It is not directed at you or anybody else.

---

### Post by harelb on 2013-04-21
> **texaswriter said:**
> I understand that you may be frustrated, but we are all here to help each other out.  LTS to LTS are supposed to work, but if it didn't than maybe saving your data and reinstalling might work. 



It is just my signature. It is not directed at you or anybody else.

Wow..I completely missed that...I saw a two line post where there was a one line post plus a one line signature and I apologize...

I thought you were calling my multi day headaches fake...that's also the only reason I quipped about weddings etc...I thought your "i heard" was the premise from which you drew your "troll" conclusion, again , I'm sorry (that is an unusual signature you had to admit, but I should have read it more carefully to seen that faint line separating message from sig..andprobaly get new glasses too)

and now, still "17h" in the corner of my firefox so it's going to be 17 hours to download the .iso....unless someone can tell me what I'm doing wrong...otherwise I'll have to leave laptopon (it is plugged into electric outlet) overnight and all of tomorrow until evening just to download the 600MB or so iso....ready to bang head in desk again....

just change from 5.1MB to 5.2MB downloaded ....again my connecdtin is normally much faster i'm pretty sure somethign screwy (see previous, europe based server I'm downloading from??) causing this...  and rebotting ater clearning cookies did not help, in facdt, it caused the 12MB or so iso that was there to be gone :-(     :-(

---

### Post by texaswriter on 2013-04-21
> **harelb said:**
> Wow..I completely missed that...I saw a two line post where there was a one line post plus a one line signature and I apologize...I thought you were calling my multi day headaches fake...that's also the only reason I quipped about weddings etc...I thought your "i heard" was the premise from which you drew your "troll" conclusion, again , I'm sorry (that is an unusual signature you had to admit, but I should have read it more carefully to seen that faint line separating message from sig..andprobaly get new glasses too)

and now, still "17h" in the corner of my firefox so it's going to be 17 hours to download the .iso....unless someone can tell me what I'm doing wrong...otherwise I'll have to leave laptopon (it is plugged into electric outlet) overnight and all of tomorrow until evening just to download the 600MB or so iso....ready to bang head in desk again....

just change from 5.1MB to 5.2MB downloaded ....again my connecdtin is normally much faster i'm pretty sure somethign screwy (see previous, europe based server I'm downloading from??) causing this...  and rebotting ater clearning cookies did not help, in facdt, it caused the 12MB or so iso that was there to be gone :-(     :-(

Yeah, sorry about that misunderstanding. 

If you believe your connection is faster than the current download speed, you could try a torrent. 

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Click on the link for your version (12.04, 12.10, etc). Then scroll down until you find the 32-bit/64-bit version (i386/amd64) and desktop version that you need.

---

### Post by harelb on 2013-04-27
The saga continues..I just let the .iso take the 17+ hours to download and burned (slowest speed) onto a CD, but something is not working. 

**1.** Brief recap - I had originally had windows 8 but I replaced it with Ubuntu 9 after some wrestling (this is not dual boot but replacement) after I had (a) turned off quikBoot (b) turned SecureBoot to disabled, (c) set OS mode selection to "UEFI and legacy" instead of "UEFI" and those three steps allowed me to finally install ubuntu 9...then when I later tried to install Ubuntu 12.04 to replace ubuntu 9 the freezing up and the rest of the problems took place described earlier. 
**I'm assuming the (a)-(c) are still in effect** (if not, could someone tell me how to check or how to set these, *from ubuntu* not from windows8 I no longer have (could not find by google..) the link from [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) takes you to [http://ubuntuforums.org/showthread.php?t=2091348&p=12397979#post12397979](http://ubuntuforums.org/showthread.php?t=2091348&p=12397979#post12397979) but as far as I can tell says to, but not how to, disable quickboot (recall, I no longer have windows so need instructions how to do it from ubuntu..and whether it matters if I do so from the current badly installed 12.04 or should shift key while booting to get into previous, and then do it)

Otherwise I'm following the suggestion to use the just-burned CD with ubuntu 12.04 to do the full upgrade again hoping it works this time.

**2. **As I said "assume I don't know anything"...so at [http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin#media](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin#media)  it says
> 
Once you've put the image you downloaded onto a CD, DVD, or USB, you will need to shut down your computer. This may be a good time to print this page, or just read through and make notes.

Turn your computer back on, tapping F12 to select a boot device when your screen shows the name of the manufacturer. You can then use the arrow keys, finally hitting enter, to select either USB or Disc Drive.

Except :

**3.** Most of the time (i.e. I've tried this several times) I am not seeing "Samsung" but see "Ubuntu" as the first thing when (a few times I do see Samsugn and did click f12...like just now..it just said "please wait" in small font in bottom right of screen...after 30? seconds it flashed some white text on blackbackground, just missed grabbing my cellphone for picture, and then immediately gave me login screen...so again won't boot from disk)  keep tryng "f12"...it seems(?) to depent what I'm booting from...if I reboot from the new (and defective) 12.04 that I'm trying to replace (I can confirm I'm in that when I get that "GNOME settings daemon not responding" when I try to restart (then you click on "restart anyway" and then wait 60 seconds or so and it finally does) or whether hold down shift key while rebooting, get into the old 2.6 version of linux (which I assume is the ubuntu 9?) but maybe there are other reasons sometimes I don't see "Samsung" at all, other times a brief flash, and at least once (just now) "Samsung" was on the screen for a long time so I definitely had time to click f12 while it was there as described above (the "please wait" may have been there before I hit f12...ok..but point is I was able to click f12 *while* "Samsung" was displayed...and still no boot-from-cd)

I'll be away from computer tomorrow probably until late afternoon so won't be able to answer qusetions..but if you have several suggestions of things to try, I'll be happy to try them and report back Sat. evening Thanks!

---

### Post by fantab on 2013-04-27
If you are willing to be patient. Then perhaps we can start all over, from nada.

Can you tell us what kind of Graphis do you have? You can check this from Samsung website against your laptop model. (If can give an extact Samsung Model that you have, it will help).

Since you have 'Removed' Windows and perhaps won't be going back to it, you can consider installing Ubuntu 'the old way', without UEFI. As of now there are no great differences between Legacy Boot and UEFI boot. But UEFI is the future. 

We can help you with both methods.

Regarding your concerns in "**1**.": all those features can be accessed from BIOS Menu/Setup. Your laptop will have a dedicated keyboard key to access it. For mine its F2, for other it could be "DEL" or F12 or anything depending on the Mother Board and/or OEM.

While you are at it, also check what kind on SATA mode is enabled. Usually there will be three options: IDE, RAID & AHCI. AHCI is better and Recommended. However we don't want RAID, unless you insist and have a need for it. 

Also tell us how you've 'Removed' Windows. How are your partitions arranged and what partition table you are using, GPT or MBR. Since it had windows8, it is very likely that you have GPT, unless you've changed it. If you don't know what it is then perhaps we should start with re-partitioning your disks.

---

### Post by harelb on 2013-04-27
Hi,
A. My box says "Samsung 365E5C-S05 and bar code is 8-87276-01603-0. If you need more please let me know what, where to find it, or what url on samsung has it. Hopefully the above very specific info is enough :-)

B. > Also tell us how you've 'Removed' Windows. How are your partitions arranged and what partition table you are using, GPT or MBR. 

I have no idea about GPT or MBR etc. What I did was this: what I had was an install disk, a CD disc to install ubuntu from. I got the disc a few years ago from the OSdisc website (because downloading and burning an install disc myself, sometimes worked in past years, other times not, so it was worth a handful of bucks to pay for theirs) It was ubuntu 9 I believe. I struggled to get it to install but eventually did (a), (b), and (c) from Windows 8 and after doing that I was able to install this old ubuntu. It goes out of service as of April 2013, so, even though it seemed to work fine, I realized I have to upgrade to a newer version of ubuntu.

By "removed Windows" I simply mean that I chose NOT the "dual boot" but just to install ubuntu (again, this old version, which worked fine as far as I could tell, for a few months of (infrequent) use).

C. When I tried to install ubuntu 12.04LTS from the website (I should have used osdisc again maybe..!) I did not burn my own CD either. What did I use to upgrade to 12.04 from 9? I used that "carboard box" icon, I think it's called "update manager" or something like that. Usually it is for updates, Not upgrade, but this time it had another button for "New version of Ubuntu is available, get 12.04!" or similar, so I clicked it...took 3 hours or so to install 12.04 but that was and is defective...see original posting...it freezes up a LOT...not usable. So now I have: defective 12.04 OR when I hit the "shfit" key while rebooting I am allowed to choose linux 2.6 which I think(?) is the Ubuntu 9, and use that..and that one works ok...until I reboot again when the defective 12.04 is in place

D.> t, you can consider installing Ubuntu 'the old way', without UEFI. As of now there are no great differences between Legacy Boot and UEFI boot. But UEFI is the future. 

Now I'm confused. All the websites said you MUST turn off uefi (see (a), (b), (c) in previous post, not this post) - or is that ONLY when installing ubunut to replace windows? Because now I'm trying to (do again what I tried earlier) namely trying to replace my ubuntu 9 with 12.04 again..or, to replace the "current, but defectively installed" 12.04 with a properly working 12.04. For the change (from Windows 8) and (to: ubuntu) the websites said to not use uefi...for my upgrade, which is Not "windows to ubuntu" but instead "ubuntu to ubuntu" do I kep the uefi? Please clarify. 

Equally importantly, I have no idea how to access bios from ubuntu. There are websites to remind me (I forgot already) how to change bios/uefi/other acronyms I understand not very well ;-) on windows...info I no longer need...but how to I see what my settings are, or changes them, from ubuntu, I don't know. Do I start somewhere under "system tools"  in the Applications menu? Or "system settings" in the right hand top bar menu?

E. > Regarding your concerns in "1.": all those features can be accessed from BIOS Menu/Setup. Your laptop will have a dedicated keyboard key to access it. For mine its F2, for other it could be "DEL" or F12 or anything depending on the Mother Board and/or OEM.

My F1 to f12 are in white color and in blue color there are other feature..it looks like I'm supposed to use the "Fn" key (similar to "ctrl" and "alt" it appears - my laptop is new and I don't know my laptop that well) and hold it down while clicking on FN where N is a number to get the blue colored feature...like blue font next to "F6" on the same key is "mute" symbol..but that doesn't work, but they are acting strange, instead the bottom-right part of my desktop (that shows all four "desktops" I can jump to, I think that's what it means) just started flashing...it has done other very strange and erratic things so it might be the misinstalled ubuntu...I could try to get into ubuntu 9 ("shift" key while rebooting) but if we can avoid going there entirely, that would be great.

Again, I have burned a CD that one is supposed to be able to boot from...from ubuntu.com/download/desktop....so I'm hoping we can use that burned CD...but maybe you're saying that it's not clear how to fix this, since it should boot-from-CD but is refusing to..? I have no idea what SATA is or what the connection is. As I said earlier, "assume I don't know anything other than how to start a terminal window" (-; (and even that doesn't work in the new ubuntu since half the time it then freezes up the entire desktop and I have to shut down by holding down the on/off button..) 

Oh oh, the strange flashing after I tried Fn+F1 (because in blue color on the F1 key was the icon of a "gear" and "wrench" which is probably where bios is) I cannot even shut down...I selected shut down, and confirmed, and it's just sitting there...I'll have to shut down by holding down the "on/off" button for several seconds....

let me try one more thing before posting...did the bad kind of shut down (holding down on/off key) and held down the "shift" key while it was turning on...selecting "previous linux versions" and then choosing 2.26.31-14-generic (not recovery mode..I can also use recovery more with that, or with 2.6.32-45) instead of the "3.2.0-400generic" which I assume is the old ubuntu 9 that works...now I have the old and correctly installed ubuntu..no, "Fn+F1" , "Fn+F6" etc do not work for me either..not even in this correctly installed, working older linux..so if you need me to go into bios hopefully the model #s etc I gave in A will give the info needed, as to how to access that.

In summary: I used (a)-(c) to install from an OSdiscDotCom CD, the ubuntu 9, replacing (not dual-boot) the Windows 8. It seemd to work 100% fine for several weeks...then I tried "update manager" (since ubuntu 9 "expires in April 2013")  when it told me I should "upgrade to 12.04LTS" so I clicked ok and after 3 hours or so it was done with the install, but this install of 12.04 is defective. In the directions please let me know whether I should use the old ubuntu (holding down shift key when loading)..In fact I probably always should, even if it's more work, since it won't freeze on me...let me know if any instructiosn you have, will *require* me to be logged into the defective 12.04 rather than logging into the 2.6 linux (ubuntu 9?). Thanks :-)

---

### Post by fantab on 2013-04-28
First of all, **you CANNOT enter BIOS setup from any OS**. You have to enter BIOS setup before any OS loads. After booting your computer the first Screen you get with options (like, but not necesarily, F2=BIOS SETUP, F10=BOOT MENU, F12=PXE BOOT etc) should let you enter BIOS with the appropriate key for your laptop.

After entering BIOS navigate yourself to find "**(U)EFI**", "**Secure Boot**", "**Fast Boot**"  and **SATA Mode**. (you should find these in Boot options or Advanced Boot options). UEFI or EFI will have options like UEFI only; Legacy; Auto. Tell us what options do you exactly have.
When you find 'Secure Boot' you will DISABLE it. You will find and DISABLE "Fast Boot" as well, if you have that option. 
Then you wil check for your HARD DRIVE in BIOS to see if its using any *IDE; RAID; AHCI*. If its AHCI, then you do nothing. If its IDE you change to AHCI. If its RAID you Change to AHCI. Tell us what you have? I am particulary interested to know if its "RAID".

Windows 8 pre-installed computers have created certain problems for dual-booters or Linux users. So the above checks are necessary to help you install latest Linux.

Following are some Links which may help you understand what these different things are:

[http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)
[http://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/](http://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/)
[http://www.anchor.com.au/blog/2012/10/the-difference-between-booting-mbr-and-gpt-with-grub/](http://www.anchor.com.au/blog/2012/10/the-difference-between-booting-mbr-and-gpt-with-grub/)
[http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html)
[http://www.petri.co.il/gpt-vs-mbr-based-disks.htm](http://www.petri.co.il/gpt-vs-mbr-based-disks.htm)
[https://www.linux.com/learn/tutorials/588498-uefi-secure-boot-big-hassle-questionable-benefit](https://www.linux.com/learn/tutorials/588498-uefi-secure-boot-big-hassle-questionable-benefit)

The info from above links will help you understand what we are talking about. It pays to know what's inside your computer.

However, All the above features are NOT required if you only intend to boot LINUX/UBUNTU. 

This is why I suggested, "consider installing Ubuntu 'the old way', without UEFI". If you wanted to dual boot Win8 and Ubuntu then we'd have had limited options. Since you want Ubuntu only, we have more options. Install Ubuntu in the "old way'' reduces complications with installing and running Ubuntu. UEFI and GPT are the future of computing but as of now they are optional. Until such time when it will be impossible to go 'old way' or it becomes easier to install Ubuntu with default BIOS setups, I suggest, for now lets stick with what is simple and just works.

My two cents...

---

### Post by harelb on 2013-04-28
> Windows 8 pre-installed computers have created certain problems for dual-booters or Linux users I know it! It wasw a headache to figure out what to do to intstall Ubuntu on my win 8 preinstalled computer...the irony is that even though that was a headache, I succeeded (back in February) and I thought my troubles were over when I finally in Feb, had ubuntu 9 installed and windows8  was (is?) completely gone but, now it's back to square one trying to fix the ubunu 12.04 misinstalled, from my ubuntu (no longer windows) laptop :-( only I could find bios more easily from win8 than I can now on my "ubuntu laptop" :-( See below

>  First of all, you CANNOT enter BIOS setup from any OS. You have to enter BIOS setup before any OS loads.

That's what I initially thought..what confused me was this: when I google's to remind myself how I changed the uefi in *windows* way back in Feb, well, that Windows 8 way of doing it (see 55 second long video  at [http://acer--uk.custhelp.com/app/answers/detail/a_id/27102/~/accessing-the-uefi-%28bios%29-setup-on-a-windows-8-system](http://acer--uk.custhelp.com/app/answers/detail/a_id/27102/~/accessing-the-uefi-%28bios%29-setup-on-a-windows-8-system) ) makes it look like the OS is already there, after all one clicks on "settings" and then proceeds...so it looks like you have your OS there already...so in Windows 8 it fools you into thinking that you already have a desktop/OS type thing already loaded and makes it look like you're going from there into uefi (which that url says is the same thing as bios or same place to go to to change bios) **But I hear you loud and clear: from my laptop I do not want to let my ubuntu Os load first, I need to get to bios/uefi before ubuntu loads**

Now I would **love** to try out your instructions in your second paragraph but apparently I'm missing something very basic when you say [quote. After booting your computer the first Screen you get with options (like, but not necesarily, F2=BIOS SETUP, F10=BOOT MENU, F12=PXE BOOT etc) should let you enter BIOS with the appropriate key for your laptop.[/quote]

because  after I boot the "first Screen you get" that you list,** is not what I see**. I get ubuntu logo almost instnatly. I just did it again in my laptop (I am on my desktop): when I press the "on" button on my laptop I get a completely blank black  screen for a few seconds and immediatley after, the very next thing I get, is I get the word "ubuntu" on my screen while ubuntu loads. *What should I do to get into the options menu that you list?*  The only other way I know is to hold down the "shift" key when I boot and then I do get something a bit different :

> GNU Grub version 1.99-21ubuntu3.9

ubuntu, with linux 3.2.0-40-generic-pae
ubuntu, with linux 3.2.0-40-generic-pae (recovery mode)
Previous Lniux versions
MEmory test (memtest86+)
Memorty test (memtest86+, serial console 115200)


then at the bottom of the screen "use the up-arrow and down-arrow keys to select which entry is highlighted. Press enter to boot the selected OS, 'e' to edit the commands before booting or 'c' for a command-line"

**I do not think this is where you want me to be. **So please, I need basic step by step how to get there where "F2=BIOS SETUP, F10=BOOT MENU, F12=PXE BOOT" is what I will see, because that's not where I am (and as I said if I do *not* hold down the "shift" key to get into grub, then the OS ubuntu starts loading withing a couple of seconds after a completely black, blank screen, after I turn the laptop On). Assume my laptop is off. Assume step #1 is I hit the "on" button. And then tell me what exactly to press to get the menu you describe. 

As I mentioned, if I press nothing, ubuntu loads immediately, the OS loads, and you said you don't want that. The only other way I know is to hold down the shift key immediately after pressing the "on" button, and I get the screen described above (which IS helpful to me since it lets me load the old version of ubuntu, when I want to use my laptop since the default installed ubuntu is the one that is freezign up) but is not helpful to do what you want to me to so, please, simple "for dummies" directions..do I hold down some other key right after hitting the "on" button? Do I do something from grub that I'm not seeing? What you say is the first screen I see is not the first one I see after turning laptop on so I need more basic steps if you can patiently list them...thanks in advance!
P.S. pressing "f2" does not get me into bios setup from this "grub" menu.

---

### Post by d0006 on 2013-04-28
[URL="http://www.samsung.com/us/support/supportOwnersHowToGuidePopupPrint.do?howto_guide_seq=1200&prd_ia_cd=N0000137&map_seq=223"]http://www.samsung.com/us/support/supportOwnersHowToGuidePopupPrint.do?howto_guide_seq=1200&prd_ia_cd=N0000137&map_seq=223

([/URL][http://bit.ly/129pgln](http://bit.ly/129pgln))

---

### Post by harelb on 2013-04-28
> **d0006 said:**
> [URL="http://www.samsung.com/us/support/supportOwnersHowToGuidePopupPrint.do?howto_guide_seq=1200&prd_ia_cd=N0000137&map_seq=223"]http://www.samsung.com/us/support/supportOwnersHowToGuidePopupPrint.do?howto_guide_seq=1200&prd_ia_cd=N0000137&map_seq=223

([/URL][http://bit.ly/129pgln](http://bit.ly/129pgln))

Thanks for the url but it only suggests there is a bigger problems because I am absolutely not getting their step 2

"At the Samsung Logo screen, press the F2 key. "

No Samsung logo screen (yes, out of the 30+reboots..probably 50+ reboots I've done since the botched upgrade from ubuntu9 to 12.04, it has appeared once that I can remember, and flashed for a half or quarter second another time, as I said, not the rest of the times) It is appearing exactly as I described in my last post here it is with even more detail here's what happens:
> 
The laptop is Off.

 Then I click the on button. 

Then maybe 4 seconds before power makes an illuminated but black blank screen

then 2 seconds of a light purple blank screen

then the word ubuntu (in white, with dots unernearth it) on top of that light purple background as ubuntu loads

Then the login screen where it wants my password

(trying to pre-emptirely just hold the F2 key down the whole time within 1-2 seconds after pressing the On button doesn't work either, no bios, no "Samsung" screen, at all, it's exactly as in the above quoted)

This is with a stopwatch next to the screen to be accurate. At no step above is "Samsung" shown to me. Hopefully this very second-by-second detailed desription suggests to someone how I get the @#%#% laptop to not skip the part where a screen with "Samsung" is shown? :-(* It is absolutely not showing me the "Samsung" screen in step 2 of the directions at the samsung.com url, or anything remotely like it..*

 (this is getting more and more bizarre...I wonder if something subtle but ugly happened when I put ubuntu to replace the original windows 8..)

---

### Post by fantab on 2013-04-28
You could try 'un-installing' or 'removing' Ubuntu completely from your HDD. You can do this with Gparted from Ubuntu DVD/USB and delete all partitions, and recreate them. If you have a separate 'recovery' partitions and 'Samsung utilities' and if you want to preserve them, then just delete Ubuntu partition and recreate it. Perhaps then you can get to the Samsung screen. OR you can contact 'Samsung Service' and get their help to enter BIOS, or recover Windows8 as it was before you removed it. So that we can later remove it accordingly. 

Now:
```
GNU Grub version 1.99-21ubuntu3.9

ubuntu, with linux 3.2.0-40-generic-pae
ubuntu, with linux 3.2.0-40-generic-pae (recovery mode)
Previous Lniux versions
MEmory test (memtest86+)
Memorty test (memtest86+, serial console 115200)
```

Have you installed 32bit Ubuntu on 64bit machine? Or is you machine 32bit? I don't like 'pae' at the end of that kernel line. [**PAE**]("https://help.ubuntu.com/community/EnablingPAE").

EDIT:
I suspect that your Ubuntu 'old version' is 32bit and your machine is 64bit, that is why you have a 'pae' kernel. The 12.04 you have downloaded, is it 32bit or 64bit? You must download 64bit Ubuntu. Please confirm this.

---

### Post by -kg- on 2013-04-28
Quite frankly, I've almost *never* had an Upgrade go well.  The one time I did was upgrading to the next version (not LTS), and only because it was on an old computer that I only use for crunching BOINC workunits.  Other than that, I've ended up with anything from a catchy, stuttering, often-malfunctioning mess, to a completely hosed installation.  I *_always_* do a clean installation, and have completely given up on Upgrades from Update Manager.  I would *certainly* never attempt an LTS to LTS upgrade, especially between LTS versions with so many changes.  I've been doing this for quite a while.

That being said, if you want to save it to your hard drive, you'll need to mount one of the partitions.  Once booted into the Live desktop, go to 'Places', click on 'Computer' from the dropdown, then click on the desired partition (preferably /home, if you have one, or '/' root, if you don't).  That will mount the partition.  Though the partitions are obviously there, and ostensibly healthy, Firefox won't be able to "see" them unless they're mounted.

Once you have the partition mounted, *then* go the website and start the download.  I think you'll see more options of where to save the file than to a CD/DVD.  Now, I can't guarantee a quicker download...the download should have been faster than 18 hours, unless you're on dial-up...but at least you won't be saving the file to a CD.

<Edit>  I must apologize...I fired off this post not realizing there was a second page of posts.  The above still stands as good information, but apparently you've resolved the problem.

---

### Post by harelb on 2013-04-30
Proiblem is definitely not resolved...I'm about to try to finish digesting the preceding comment on page 2, but your post slightly "cheer me up" - NOT happy about what happened to you (or to me) but feeling less "alone"...so in *that * sense your comment "Quite frankly, I've almost never had an Upgrade go well." made me "feel better"...but how sad that one can't go LTS to LTS...I would have thought that was the *point* namely that they encourage you to use an LTS and my "so very old" version 9 was still not expiring...if one LTS goes until April 2013 then you'd hope that one can upgrade from it to the "most recent" LTS as of April 2013...but alas apparently not..."Mounting partitions" is beyond my "assume I don't know anything other than opening a Terminal so I'll have to look at the preceding remark but thanks again for sharing..

---

### Post by harelb on 2013-04-30
Fantab,
First, sorry for waiting another 24 hours, had another deadline, I'm back now. I usually like having more options, but right now I feel like I'm drowning in an infinitely recursive spiral never to fix this again, so can you give tell me which is the one (and simplest and easiest) way and then spell out how to do that and I'll try to follow your directions?

As far as your question, by now I'm sorry to say that I can't remember if I downloaded 32 or 64 bit (of 12.04LTS).**..the file is called "ubuntu-12.04.2-desktop-i386.iso" and if I right-click on the icon for this .iso file and use "show properties" it says "727.0 MB (726,970,368 bytes)" does that determine which?** Or is there a command line "sniffer" program I can run on that .iso to tell, if not? I hope  so.. (in the weeks and months of escalating madness I've also lost track of the users manual on this new laptop...I'll find it eventually..but since I purchased it in Jan 2013 I believe, correct me if I'm wrong, that it's almost *certainly* a 64bit laptop) 

Since the pulldown menu says "newer machines" next to 64bit I would "think" that I should have selected the 64 bit for the 12.04LTS...but my exhaustion by that point might have been so I overlooked it..honestly can't remember and I dearly dearly hope the info I gave above about .iso file for 12.04LTS (which still sits on my desktop computer's, um, desktop, is enough info to tell us which .iso I put on the install CD?)

[UPDATE: yay! Not *every* question you ask me is impossible for me to answer, my carboard box of my laptop says, "Features: OS: Windows 8(64b) ; CPU: AMS Dual-Core A6-4400M APC....." etc...which I assume, and believe, means we have **100% confirmation that my Laptop is 64 bit**..can you tell from the info about the .iso file whether the 12.04LTS is 64 bit or 32 bit? The 9.10 I don't know as I say but might be 32 bit...hopefully not lethal? all I can tell you is that my ubuntu 9.10 was working FINE for the (admittedly light) use I was making (but for several weeks) on my new 64bit laptop, so hopefully I don't have to remove both 12.04 AND the ubuntu 9.10 (which would leave me with ZERO operating systems on my laptop)

Question - I'd have to have to spend another 17 to 21 hours downloading another .iso only to find out the 64 bit version isn't any better...or that I already have the 64 bit iso...is that the best path? Or uninstalling ubuntu completely? 

And what does that even mean? removing the 12.04LTS? Or even removing the version 9 (which I guess is more exactly version 9.10)? Dealing with anything other than command lines I can copy/paste is probably way above the complexity I should deal with, partitions anything like that...the simplest simplest way to go forward, please, is what?

[Aside: Overnight I thought, "wait, maybe Samsung is not showing up because what I think is "off" is some SEMIsleep mode!" Because for a 300 dollar laptop without the (I forget its name) type memory, takingly that many seconds as I recorded from OFF to ubuntu loading seems faster than I should be able to expect... but then I realized I have my laptop plugged into a "power strip" which is OFF overnight so there should be no electricity "juice" getting to the laptop, so my "off" should be really off, not semi-sleep right? the battery is entirely removed, so that's not a power source. Let me try to even unplug the cord from the laptop itself and wait 5 minutes and then boot and see if finally I am shown the "Samsung" logo from which I can then try to get into BIOS......added later: nope, even after completely unplugged this 300 dollar cheap laptop still powers in like 6 seconds to get the "purple" background that is when Ubuntu is loading...no "Samsung" logo...]

[Aside #2: I looked for and found my old 2009 email invoice for ubuntu 9.10 from OSdisc.com, but even that does not say 64 versus 32 bit..just says,, "Order #180114 Shipped 2009-12-23 Shipping via Priority Mail
Qty     Description 1       Ubuntu 9.10 - Alternate Install CD (PC) 1       Ubuntu 9.10 - Install/Live CD (PC)]

In summary, I hope the info about my laptop (is 64bit unless I misinterpret what I typed in above for you from carboard box)), and the info about .iso tells you what you need about the version of 12.04LTS I do not wish to not seem grateful for the code you put in but I'm really struggling to follow it (the meaning of the pae reference, and what your "now:" means, whether it means after doing the samsung call or after something else..I'm quite lost about the if/then/mathematical tree of your suggestions...not your fault..my own posts can be hard to follow..it's hard..these things are complex with many subcases.....) and the many suggestions combined in your post leave me really strugling..**.So: Short of calling Samsung,..without "partions" and "mounting" etc....What's the simplest easiest "for linux dummies" next step? Just give me one way to go, that is easy, not several but one way, and copy-paste-for-linux-dummies step-by-step for that, and I'll do my best to follow through..** (I'm even willing to spend another 20 hours doanloading an iso and making sure I am SURE that it's 64bit...and if that still doesn't boot-from-CD then what do I do? (though PLEASE tell me if you can tell from my .iso info, if you can tell my existing one **already is** 64 bit, so avoid downloading the same .iso and spending another 20 hours all over again...) Thanks! :-)


> **fantab said:**
> You could try 'un-installing' or 'removing' Ubuntu completely from your HDD. You can do this with Gparted from Ubuntu DVD/USB and delete all partitions, and recreate them. If you have a separate 'recovery' partitions and 'Samsung utilities' and if you want to preserve them, then just delete Ubuntu partition and recreate it. Perhaps then you can get to the Samsung screen. OR you can contact 'Samsung Service' and get their help to enter BIOS, or recover Windows8 as it was before you removed it. So that we can later remove it accordingly. 

Now:
```
GNU Grub version 1.99-21ubuntu3.9

ubuntu, with linux 3.2.0-40-generic-pae
ubuntu, with linux 3.2.0-40-generic-pae (recovery mode)
Previous Lniux versions
MEmory test (memtest86+)
Memorty test (memtest86+, serial console 115200)
```

Have you installed 32bit Ubuntu on 64bit machine? Or is you machine 32bit? I don't like 'pae' at the end of that kernel line. [**PAE**]("https://help.ubuntu.com/community/EnablingPAE").

EDIT:
I suspect that your Ubuntu 'old version' is 32bit and your machine is 64bit, that is why you have a 'pae' kernel. The 12.04 you have downloaded, is it 32bit or 64bit? You must download 64bit Ubuntu. Please confirm this.

---

### Post by fantab on 2013-04-30
> **harelb said:**
> Proiblem is definitely not resolved...I'm about to try to finish digesting the preceding comment on page 2

Simply put. 32bit CPU (and 32bit OS) can only identify RAM upto 3GiB (its GiB not GB). [COLOR=#454545][FONT=Segoe UI]Physical Address Extension (PAE) is a processor feature that enables x86 or 32bit processors to access more than 3GiB of physical memory, RAM. When you installed 32bit Ubuntu 'old version' it activated PAE in the kernel, when you tried to upgrade with 12.04. We don't want that since your laptop is 64 bit, now do we? Then, first of all reformat that partition on which you have the 'old version'.

EDIT: You posted while I was typing the above.

I am afraid but you have to download the 12.04 64bit Ubuntu. The latest 13.04 is released, so you can also go for 64bit of it. I suggest you go with 13.04 64bit.

It would serve you well if you know whats behind that 'Samsung' screen and enter BIOS setup, otherwise it will be 'trial and error'.  I can only assume what could be and help you.
I still suggest you CONTACT Samsung Service and enter the BIOS setup or restore everything back to its 'Factory State'.

Let us know when you have downloaded 64bit Ubuntu and burned it to disk.

[/FONT][/COLOR]

---

### Post by harelb on 2013-04-30
Update, in sheet desperation I googled for:

"726,970,368" 64 OR 64b OR 64bit OR 32bit OR 32b OR 32 ubuntu

where the sting in quotes is, again, the exact number of bytes of the .is file I had for 12.04...and with that google I found

Index of /ubuntu/12.04/
mirrors.gigenet.com/ubuntu/12.04/&#8206;
Feb 14, 2013 &#8211; ... 20:54 198 ubuntu-12.04.2-alternate-amd64.iso 14-Feb-2013 00:12 ... 726970368 ubuntu-12.04.2-desktop-i386.iso.torrent 14-Feb-2013 ...


does that answer question? (if I click on the link and search-in-browser for "70386" I can't find it...maybe it was in the google cache of this page only but not the current)? Surely my knowing to the EXACT number of bytes what my iso file is, must narrow it down for us on sme page on the world wide web whether my .iso file for 12.04LTS that I had the (mis)install from, is 64bit or 32bit? Hope this extra info might answer if my previous post didn't

---

### Post by harelb on 2013-04-30
If I understand you correctly you're saying
1. you dont' need to know the answer after all, to your earlier question about which version of 12.04 I have installed?
2. that it's very likely that the 9.10 was 32 bit ?

But who cares if I have a "bad" 9.10 if I can successfully install a 12.04 64b correctly? or is that impossible to do until I remove the 9.10? Is that impossible to do, to install a correct 12.04LTS correctly installed and then to delete the (we're assuming) 32bit 9.10?

if answers to all above are "yes" then, are you saying that 

"hen, first of all reformat that partition on which you have the 'old version'."

is the simplest thing (see my post #23 above) since reformatting etc is way beyond what I know how to do without step by step instructions a blind monkey can follow....if there's simpler than "reformat" please can you clarify? if nothing at all is possible simpler then I'm in trouble without something a newbie can follow step 1, step 2, step 3, step 4, etc, for that....

---

### Post by harelb on 2013-04-30
another update - I have 24hour samsung number...if they show me how to get into bios is there *then* a simpler way than "reformat"/erase all ubuntu?

---

### Post by fantab on 2013-05-01
Erasing Ubuntu is not really an issue. Reformatting is 'the' safest and simplest way to remove Ubuntu. Yes, you do have a 32bit Ubuntu 12.04 "i386" means 32bit.

What we need is to enter BIOS set up and find out:

* if you have UEFI (most likely you do)
* if you have 'Secure Boot' (most likely you do)
* if you have SATA in AHCI mode (not a must) but if you have any SSD on your laptop then we have to find out if its using any sort of RAID.

I can help you 'assuming' that you have both UEFI and Secure Boot... But it will be very difficult if you have some sort of RAID. 

Call 24hrs. Samsung Support and tell them you have accidentally deleted your Windows partition and also that your can't enter your BIOS... most likely they will walk you through to troubleshoot.

---

### Post by harelb on 2013-05-01
Okay....waiting for the Samsung logo doesn't work, and clicking f2 before you see anything but after like 2 seconds, nope, you hold it down INSTANTLY after clicking on and you get into BIOS, thanks Samsung 24hour number :-D

Despite very fast turning on he confirmed that I do not have SDD (he said that means I have either "HD" or "HDD" even though the code given in the First menu in bios, "ST500LM012 HN-M500MBB" does not use either acronym, he said that happens) That's from the "SATA Port 1" line. There is a SATA Port 2 line, "TSSTcorp CDDVDW SN-208BB"

I took a photo. Then there is a second menu, Advance, a third one, Security, a fourth, Boot, and a fifth, Exist. I went into the fourth one, took a photo (currently being send from my cell to my gmail..I'll upload later, I'll describe in text for now)

The Boot menu says:

Boot Devide Priority
Touch Pad Mouse [enabled]
Secure Boot [disabled]
OS Mode Selection [UEFI and Legacy OS]

Internal LAN [enabled]
PXE OPROM [Disabled]

Ok, that's looking like it is unchanged from the settings I created (disable secure boot and put OS mode into "UEFI and Legacy OS") back when those settings were needed to allow me to replace Windows 8 with the 9.10 (which worked soooooo well but now I'm told has the 32bit eeeevil in it, ha ha)

And no SDD so we don't have to even ask if there is RAID, and no worries, if I followed that part of your note...
I hope this answers all the questions...in "for dummies" what does this mean 

If "reformatting" is what's next...I have (almost) no idea what that means so need very step by step on how to do that..

...it's some kind of erasing of both the 9.10 and erasing of the 12.04LTS? Should I meanwhile download overnight the 64 bit 12.04 "iso" file?

Meanwhile, I'll try to get that started, it was close to 20 hours to finish last time, but I'll try to** start the 64bit 12.04 iso download**...if you DONT need that let me know so I can stop it halfway throught eh 17-24 hours download...thanks, goodnight for now

[going to bed now will read tomorrow...but just attached two screenshots]

---

### Post by fantab on 2013-05-01
Okay, you've won more than half the battle. :D

Now, after downloading 64bit Ubuntu 12.04 or 13.04, whichever it is, BURN it to a disk.

1. Boot with Ubuntu 64bit and choose "**Try Ubuntu**". Wait until you have working desktop.

2.0. From desktop open and run '**GParted**' , the disk partition management utility.
2.1. Delete ALL partitions by right clicking on a partition and select '**Delete**'. Then you '**Apply**' the changes. See the screenshots.
2.2. Recreate Partition Table. Click on '**Device**' and select '**create new partition table**' and choose **GPT** from **'Advanced Options'**.
2.3. Create FIRST partition of about 250MiB and format it as FAT32 and put a "Boot Flag" on it. 
2.4. Create 20-25GB partition and format it as ext4.
2.5. Create 20-25GB partition and format it as ext4.
2.6. Create 4GB SWAP partition.
2.7 Create RemainingGB partition and format it as ext4.
2.8. Apply changes

[ATTACH=CONFIG]242028[/ATTACH] [ATTACH=CONFIG]242031[/ATTACH]  [ATTACH=CONFIG]242030[/ATTACH]

3.0. Exit GParted and Restart your computer.

4.0. Boot with Ubuntu disk in **UEFI mode**, if there is an option to do so, and choose '**Install Ubuntu**'.

5.0. At the appropriate Screen you will be as how you want to install Ubuntu, choose "**Something Else**".

6.0. In the following screen select your first 20-25GB partition (Not the first 250MiB partition) then hit '**Change**' and choose "**/**" as mountpoint.
6.1. Now select the 'RemainingGB' partition, hit 'change' and choose "**/home**" as mountpoint. If you don't want separate /home and use instead a plain partition to store your DATA then ignore this (6.1) step.
6.2. Below, on the same screen, you will see where is Grub being installed, by default it will be installed on /dev/sda. That is good enough for us. If it doesn't say /dev/sda then change it to /dev/sda.
6.3. "Continue" with installation and "**Install Now**"

7.0. When the installation is complete, as instructed by the installer, REBOOT.

Ubuntu should be able to boot from HDD now. ***In case there is an issue booting Ubuntu***:

1. Boot from Ubuntu install disk and "Try Ubuntu". Once the desktop is ready Connect to Internet, then open Terminal (ctrl+alt+T) and run following commands one after another:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && (sudo boot-repair &)
```

With these commands we are installing [BOOT REPAIR]("https://help.ubuntu.com/community/Boot-Repair") utility on Ubuntu Install Disk to repair our boot. More help with Boot Repair can be found [HERE]("http://ubuntuforums.org/showthread.php?p=10871917#post10871917").

2. 'Boot Repair' will run and search for problems, then it will display "Recommended repair", just click on it. That should fix your boot issues. Reboot to check.

Good Luck...

---

### Post by harelb on 2013-05-01
*[Added in edit later: Just to be clear when I was finally able to go in to BIOS last night, I did NOT change anything; I found the settings to be what they were before...the settings I reported were the ones I found, not new settings (I hope it didn't sound like I was saying I changed them) So the bios is set the way it was earlier...and earlier is when it was not agreeing to boot-from-CD .. ]*

I appreciate the smiley and encouragement..and appreciate the time you took to type in that list but it looks daunting..half the battle or 10% of the battle so far? ...The good news is the is downloaded much faster...So I can and will burn a CD, but, somewhere earlier in this thread I mentioned **not being able to boot-from-CD** the last time I tried (from the  32bit burned cd)

Did you see that? Because if I still can't boot-from-CD then I won't be able to do step 1. Because I couldn't boot from CD earlier, will teh CD being of a 64bit ISO all by itself with no other changes, make my laptop** behave itself and boot from the CD? If so that's great, I just didn't hear you say that this, all by itself, would make it able-to-boot-from-CD...  :confused:

** (the same one that will not even show the Samsung icon (which you'er supposed to click f2 AFTEr you see it, in the official tips) unless I hold down f2 *before* I see "Samsung"

The other concern is can you explain why I would need to do the rest if I am able to do the CD and it is absolutely, positively the very veyr very simplest way to fix my laptop? Because I already don't know how to do your 2.0! I tried on this (on my Desktop computer) and got "**Command not found**" ...**I am willing to go back and forth with questions on 2.1, 2.2, etc (if they come up...but based on 1.0 and 2.0 it suggests they will come up) if you are,** but, if there's a simpler way that will avoid us needing so many steps that will just get me an *operational* laptop - just one that just works , that might be simpler than this 19 steps you have outlined (again with thanks for your details here, honestly thanks! but as ou can see even 2.0 is not working for me on my desktop, and that's just 1 of the 19 steps?)...that might drastically simplify the steps needed, that would be wondeful.....

---

### Post by harelb on 2013-05-01
Just to be clear when I was finally able to go in to BIOS last night, I did NOT change anything; I found the settings to be what they were before...the settings I reported were the ones I found, not new settings (I hope it didn't sound like I was saying I changed them) So the bios is set the way it was earlier...and earlier is when it was not agreeing to boot-from-CD ..

---

### Post by harelb on 2013-05-01
Update did a full "md5sum" check on the iso...and compared and matched properly with hash number...Then did the burning of a new CD this time for this 64bit iso..slowest burning it allowed for more accuracy....CD is done being burned..only thing is like the previous time I burned, got a final dialogue box saying "Please eject the disc from "HL-DT-ST CD-RW GCE-8527B" manually.The disc could not be ejected though it needs to be removed for the current operation to continue" (strangely, the dialog box has a "cancel" but not an "ok" button.. I hit eject..without clicking cancel..then (x)'s out the dialogue box..."image successfully written toCD" it says..hopefully that was not the cause/will not now cause, issues..

This is how I will try to boot from disc **(i)turn laptop on first since I can't open CD drive otherwise (ii)then insert CD (iii)then do a "Restart" and hope it boots from CD (saying cancel/no if it asks me "a volume with software packages has been detected. Would you like to open it with the pacakge manager?" ** I once said yes and it's definitely not for boot-from-cd it thinks it's just a CD with data on it) So using those three steps..is this correct? not correct? 

Well tried it just now and I heard a few sounds on the cd drive, but then *I just get the usual login screen* **does not boot from CD**.Same problem as before..

of course (and this might be, but worth mentioning in case it not, irrelevant)** in step (iii) "Restart" does not work right** in this misinstalled 12.04 [/I](see one of earliest posts - the  "A program is still running: GNOME Settings Daemon" error message and "shut down anyway?" or "restart anyway?" - does this every time from the misinstalled 12.04 and never ever does it from the old (apparently 32 bit but still worked fine) 9.10.... and I say yes) so not sure if it was shut down/restarted properly. So I turn off and then turn laptop on now with shift key down so I can get into ubuntu 9.1 (which does not have that error message when I use Restart or Shut Down) and then, with CD in, hit restart..that will still  restart with 12.04 when I do restart but at least it will have done a proper Restart..

No, it still isn't booting from the cd - I'm not getting that two-choice
[http://leekaelin.co.uk/downloads/TechSpot/Linux_Guides/Ubuntu_11_10/Ubuntu_11_10_Capture1.JPG](http://leekaelin.co.uk/downloads/TechSpot/Linux_Guides/Ubuntu_11_10/Ubuntu_11_10_Capture1.JPG)
"try ubuntu" or "install ubuntu" thing...either my i-iii is missing something (I tried re-reading the how to install they just say "boot form CD" like there is nothing to do but put the cd in) missing something basic or it's something about the laptop state or IDK what...but this is the latest roadblock at just step 1...one that I worried about a couple hours ago in what's post #31..

can anyone help?? :confused:

---

### Post by fantab on 2013-05-01
You have to change in BIOS "BOOT MENU" to boot your CD first, if you don't then the HDD is booted. I think instead of F2 you have to use "Esc" key, you will know the exact key for "BOOT Menu" from the Samsung Screen...

Insert the CD.
Start Laptop. 
Get to Samsung Screen, Enter 'Boot Menu', select CD drive, enter to exit, or sometimes you have to save and exit.

ONE MORE THING: Enter your BIOS setup and navigate to "Advanced" you should be able to see and set SATA MODE" confirm that it is set to 'AHCI', if not change it to 'AHCI'. Post a screenshot if you get confused.

---

### Post by harelb on 2013-05-03
Thank you. I will try that. Need a day or two to catch up with other things. I've also relocated my laptop's owner's manual (hurray) and will read it over. Need a few days. Then I'll be back with partial (I'm sure) progress report and more questions...thx

---

