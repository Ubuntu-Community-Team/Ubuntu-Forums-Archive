---
title: "Hardy: Why is it so difficult to change media default?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by peterkeyani on 2008-04-30
Hi,

you would think it should be a simple matter to change media default such as from totem to vlc player or f-spot to picasa, not something you would need a week of fiddling with especially with a brand new operating system but there it is...

any** simple easy** ways to to these everyday things?

thanks

pete

---

### Post by warbread on 2008-04-30
Everyday things?  How often do you do this in other OSes?

A good place to start is in System -> Preferences ->Preferred Applications.    Otherwise, you'll have to go into gconf-editor, which really isn't a big deal.  You could also right click on a file and select 'Open with other application..."

---

### Post by mrgooding on 2008-04-30
I've found it reasonably easy to change the associations, but not the Icons (i.e. i've changed the default media player to VLC, but I don't get that rather fetching traffic cone icon!). It's not a major thing, but it would be nice - is there any easy way to change the associated icons to a given file type?

---

### Post by end-user on 2008-04-30
> **peterkeyani said:**
> Hi,

you would think it should be a simple matter to change media default such as from totem to vlc player or f-spot to picasa, not something you would need a week of fiddling with especially with a brand new operating system but there it is...

any** simple easy** ways to to these everyday things?

thanks

pete

Yeah, I guess preferred applications could offer a few more programs defaults to set. But you can also change preferred programs by type of file while browsing files in Nautilus. For example, say you wanted to use gThumb image viewer (after you downloaded it, of course) to view a .gif instead of Eye of Gnome (which won't show animations) you'd right click it, go to Properties, and go to the Open With tab.

Does that help at all?

---

### Post by warbread on 2008-04-30
> **mrgooding said:**
> I've found it reasonably easy to change the associations, but not the Icons (i.e. i've changed the default media player to VLC, but I don't get that rather fetching traffic cone icon!). It's not a major thing, but it would be nice - is there any easy way to change the associated icons to a given file type?

The easiest way I can think to do this is to go into /etc/usr/share/pixmaps and start renaming icon files to switch and replace the ones you want.  If you know what you want to do, it wouldn't be as hard, but just a pain in the butt.

---

### Post by fhmanas on 2008-04-30
> **peterkeyani said:**
> Hi,

you would think it should be a simple matter to change media default such as from totem to vlc player or f-spot to picasa, not something you would need a week of fiddling with especially with a brand new operating system but there it is...

any** simple easy** ways to to these everyday things?

thanks

pete

I agree, I am still battling with my Ipod to be seen by Banshee.  Also, having an easy and ***obvious*** way would be good.  An average user will never figure out changing these associations in nautilus unless they go to the forums.  Nor would they know how to go to gconf-editor if not for the forums.  Ubuntu transitions would be a lot easier if this things are easily found.

---

### Post by peterkeyani on 2008-04-30
[QUOTE=warbread;4842009]Everyday things?  How often do you do this in other OSes?

You are kidding - right?

In XP - for all its faults - I put a DVD in the tray and a menu springs up asking which application I want to use to open it and if I want that application to do the same every time. Could not be easier!

Further most applications ask you if you want it to be the default.

In ubuntu, you go to "preferred applications" thinking you can change the preferred applications only to find you are give then choice of 1 player - totem - even though I have totem, vlc, and MPlayer installed! Thank goodness I kept my XP partition and I was so looking forward to getting rid of it when Hardy came out!

Thanks for the advice folks but its way to complicated for a new linux user - I cant afford to screw up my system and have to start all over again...

---

### Post by billgoldberg on 2008-04-30
> **peterkeyani said:**
> [QUOTE=warbread;4842009]Everyday things?  How often do you do this in other OSes?

You are kidding - right?

In XP - for all its faults - I put a DVD in the tray and a menu springs up asking which application I want to use to open it and if I want that application to do the same every time. Could not be easier!

Further most applications ask you if you want it to be the default player.

In ubuntu, you go to "preferred applications" thinking you can change the preferred applications only to find you are give then choice of 1 player - totem - even though I have totem, vlc, and MPlayer installed! Thank goodness I kept my XP partition and I was so looking forward to getting rid of it when Hardy came out!

Thanks for the advice folks but its way to complicated for a new linux user - I cant afford to screw up my system and have to start all over again...

So you are giving up ubuntu because you find it hard to change the default programs. 

Good luck with xp.

*ps: It takes me around 1 minute to change them all, and I didn't had to look on the forums.*

---

### Post by hyper_ch on 2008-04-30
> **fhmanas said:**
> An average user will never figure out changing these associations in nautilus unless they go to the forums.  Nor would they know how to go to gconf-editor if not for the forums.  Ubuntu transitions would be a lot easier if this things are easily found.
An average user wouldn't be bothered changing it at all but taking the default media player that comes with the OS.

> **peterkeyani said:**
> [QUOTE=warbread;4842009]In XP - for all its faults - I put a DVD in the tray and a menu springs up asking which application I want to use to open it and if I want that application to do the same every time. Could not be easier!
(1) right-click the file
(2) select "open with"
(3) check that box that says to remember that...
Pretty much the same...

---

### Post by mrgooding on 2008-04-30
I've added an idea to brainstorm for easily changing the Icons and i've added a bit about the program associations sometimes not showing.

[[IMG]http://brainstorm.ubuntu.com/idea/7873/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/7873/)

If you could support this and / or add any ideas (or perhaps even articulate it better than I have) i'd appreciate it.

Cheers!

---

### Post by peterkeyani on 2008-04-30
> **billgoldberg said:**
> [QUOTE=peterkeyani;4842132]

So you are giving up ubuntu because you find it hard to change the default programs. 

It takes me around 1 minute to change them all.

Good luck with xp.

Would it have killed you share this information especially in an "Absolute Beginner" forum? I guess linux users are the arrogant elitists of MicroSoft imagination!

And I have no intention of giving up on ubuntu. It will stay as a dual boot with XP. Both are good operating systems, neither is an excellent one.

---

### Post by hermes0710 on 2008-04-30
Let's not start another Linux vs Windows thread...

---

### Post by SunnyRabbiera on 2008-04-30
well the one to really blame here is the gnome development team, who tend to oversimplify things.

---

### Post by hyper_ch on 2008-04-30
there is no one to be blamed... you have the choice of many different desktops... some allow only basic reconfiguration, others allow extensive one... pick the level you are happy with ;)

---

### Post by SunnyRabbiera on 2008-04-30
Yeh though its hard to tell what is worse, gnome and its oversimplification or KDE4 with its ugly panels and desktop widgets.

---

### Post by warbread on 2008-04-30
> **peterkeyani said:**
> [QUOTE=warbread;4842009]Everyday things?  How often do you do this in other OSes?

You are kidding - right?

In XP - for all its faults - I put a DVD in the tray and a menu springs up asking which application I want to use to open it and if I want that application to do the same every time. Could not be easier!



Yes, it could.  I put a dvd in the tray and the same program that I use for every movie I ever watch comes up.  If it's a data cd, it opens Thunar and I can explore the contents.  If it's a music CD, it opens RubyRipper.  I think this is pretty easy.  Am I missing something?

---

### Post by warbread on 2008-04-30
> **peterkeyani said:**
> 
In ubuntu, you go to "preferred applications" thinking you can change the preferred applications only to find you are give then choice of 1 player - totem - even though I have totem, vlc, and MPlayer installed! Thank goodness I kept my XP partition and I was so looking forward to getting rid of it when Hardy came out!


I believe it also gives you the option of using a custom application.  I can't confirm this, as I'm at work.  If you can find this, try typing in whatever player you want to run.

---

### Post by peterkeyani on 2008-04-30
> **warbread said:**
> [QUOTE=peterkeyani;4842132]

Yes, it could.  I put a dvd in the tray and the same program that I use for every movie I ever watch comes up.  If it's a data cd, it opens Thunar and I can explore the contents.  If it's a music CD, it opens RubyRipper.  I think this is pretty easy.  Am I missing something?

I think some of you misunderstood my reason for asking the question. I had no intention of starting a "flame war" nor looking to be called stupid for not magically understanding how linux works immediately. It was a genuine question looking for a genuine answer. Let me put it this way. if I put a DVD into the drive hardy tries to use totem to play it. I like VLC and I dont like totem. Its easy for me to switch between VLC and Windows Media Player in XP. In a simular fashion its easy for me to decide if I like iTunes of Windows Media best for playing my CD's. These are not critical needs. Hardy gives me a safe and reliable research enviroment - Im finishing up my Phd at the moment - and thats whats most important to me but other things - media and games - would be nice. If however some of you experts would care to share your knowledge on how to do these things without talking down to or sniggering at the beginner that would be great too.

---

### Post by SunnyRabbiera on 2008-04-30
Well as I said the matter really isnt in our hands, more its in the hands of the gnome development team...
It seems like every version of gnome a lot of things improve but a lot of other things seem to go awry.
So far I have not discovered a way to easily make another player default, the previous version of gnome had this feature and its a shame it got left out.

---

### Post by warbread on 2008-04-30
> **peterkeyani said:**
> [QUOTE=warbread;4842227]

I think some of you misunderstood my reason for asking the question. I had no intention of starting a "flame war" nor looking to be called stupid for not magically understanding how linux works immediately. It was a genuine question looking for a genuine answer. Let me put it this way. if I put a DVD into the drive hardy tries to use totem to play it. I like VLC and I dont like totem. Its easy for me to switch between VLC and Windows Media Player in XP. In a simular fashion its easy for me to decide if I like iTunes of Windows Media best for playing my CD's. These are not critical needs. Hardy gives me a safe and reliable research enviroment - Im finishing up my Phd at the moment - and thats whats most important to me but other things - media and games - would be nice. If however some of you experts would care to share your knowledge on how to do these things without talking down to or sniggering at the beginner that would be great too.

I'm not sniggering, I'm pointing out that it can be easier than you think.  I've offered several suggestions at this point, only one of which you've given me any sort of feedback on.  Getting the media player you want to pop up automatically when you put a DVD in the tray is not difficult, but it's going to require doing something new - nothing that would screw up your system, by the way.  If what you want to use is XP, then use XP.  If you want to use Ubuntu, you're going to have to learn to do some things that are different from XP.  

So, are you looking for VLC to open when you insert a DVD, or are you looking for an XP like pop up?  I can help you with the first one and you will have to do minimal work.  Let me know.  I can help better when I get home.

---

### Post by Mattevt on 2008-04-30
> **warbread said:**
> [QUOTE=peterkeyani;4842329]

I'm not sniggering, I'm pointing out that it can be easier than you think.  I've offered several suggestions at this point, only one of which you've given me any sort of feedback on.  Getting the media player you want to pop up automatically when you put a DVD in the tray is not difficult, but it's going to require doing something new - nothing that would screw up your system, by the way.  If what you want to use is XP, then use XP.  If you want to use Ubuntu, you're going to have to learn to do some things that are different from XP.  

So, are you looking for VLC to open when you insert a DVD, or are you looking for an XP like pop up?  I can help you with the first one and you will have to do minimal work.  Let me know.  I can help better when I get home.

Along these same lines, I'd like .avi files to automatically open with VLC.

---

### Post by tyroeternal on 2008-04-30
> An average user will never figure out changing these associations in nautilus unless they go to the forums. Nor would they know how to go to gconf-editor if not for the forums.

Unfortunately you are right, there are some hurdles to get over, but thats why communities like this exist.  It does take a bit of thinking outside the "average user" box to use the documentation, forums, and wiki.  Once you get used to that you find can do a whole lot more with your system, but you also have to learn a whole lot.

---

### Post by wermeulen on 2008-04-30
Okay, so I found this post googleing how to enable default VLC playback for DVDs in Hardy--now somebody please post a solution to the question and stop pointing out us newby's have a lot to learn, *I agree already* :)

Apparently, as per the bug report [URL="https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/216969"]
"Removable Drives and Media" preference tool no longer contains preferences for drives nor media[/URL], the tool you could use on Feisty is no longer usable on Hardy. To make matters worse, the Media tab in the Nautilus Preferences menu doens't allow me to choose another application either. It does allow me to ask what to do when a DVD is inserted--at which point you again can not select another application.

gconf-editor was no help either. It might be possible from there, but I can't find it. Just as useful as regedit...

---

### Post by wermeulen on 2008-05-01
There is a good [post]("http://ubuntuforums.org/archive/index.php/t-333714.html") on how to use gconf-editor to change the default DVD playback application. Very easy to follow!

**Update:** Okay, so it's easy to follow -- but it doesn't actually do anything on Hardy because of course the volume manager bug is in effect here :)

HALP! Who can point out how to do it now...

---

### Post by mivo on 2008-05-01
> **hyper_ch said:**
> An average user wouldn't be bothered changing it at all but taking the default media player that comes with the OS.

Which doesn't play encrypted DVDs out of the box. ;)

---

### Post by kenny1948 on 2008-05-01
[QUOTE=billgoldberg;4842144][QUOTE=peterkeyani;4842132]

So you are giving up ubuntu because you find it hard to change the default programs. 

Good luck with xp.

just forget what I think!

---

### Post by warbread on 2008-05-01
Ok, granted, I haven't used Hardy yet, but in Gutsy I can right click on a file, go to "Open with Other Program" and select VLC, then check the "use as default for this type of file".  That works.  Also, I can go into gconf-editor and select the key Apps -> Gnome -> Desktop -> Volume manager and select what I want to autostart.  

I can understand not wanting to spend a day or two just figuring out how to change the default media player for any given file, but I know that in Gutsy, it's really easy.  I won't be using Hardy at least until FF3 final is released, so I won't be able to help until then.  Right now, you have the choice of going back to Gutsy.  If you're not liking Hardy, then I think this choice is a good one.

---

### Post by kenny1948 on 2008-05-01
> **warbread said:**
> Ok, granted, I haven't used Hardy yet, but in Gutsy I can right click on a file, go to "Open with Other Program" and select VLC, then check the "use as default for this type of file".  That works.  Also, I can go into gconf-editor and select the key Apps -> Gnome -> Desktop -> Volume manager and select what I want to autostart.  

I can understand not wanting to spend a day or two just figuring out how to change the default media player for any given file, but I know that in Gutsy, it's really easy.  I won't be using Hardy at least until FF3 final is released, so I won't be able to help until then.  Right now, you have the choice of going back to Gutsy.  If you're not liking Hardy, then I think this choice is a good one.

OK, maybe that's what this person is trying to tell you. In Gutsy, you could do that. Here you cannot. I too am very frustrated with this. I like to use my computer for making video DVD's and digital photo editing.
I finally had things working pretty well on Gutsy. I was even able to listen to my favorite web-radio station while I read my mail. Now I can't. 
It took weeks of searching the forums to find what I needed, and then I managed to get the programs that worked best for me up and running. Now I am given the choice of Totem and Brasero, which I don't like at all. It cannot burn videos that play in a normal player. Tonight I tried burning a DVD for the first time since I "upgraded" and it won't play in my player. Nor does it play very well with Totem which is the only program I can open a DVD with on this damned thing.
Not all of us are computer geeks! I use my computer to communicate, and explore some of my hobbies. I don't know what the rest of you use a computer for. Other than multimedia and mail I have no use for the other programs. 
Sorry, but I had to rant. This is like someone else said, supposedly for absolute beginners. So have a little compassion for the rest of us simpletons.
Thank You:(

I might just add, had I realized that Hardy would not work as well as Gutsy, I would not have "upgraded". Gutsy solved the problems I had back with Feisty. I assumed that Hardy would be even better.  So far I am very disappointed.

---

### Post by mc4man on 2008-05-02
In Hardy if you want to add vlc as a choice for default (autorun) movie player see here - do it only once - [http://ubuntuforums.org/showpost.php?p=4580595&postcount=8](http://ubuntuforums.org/showpost.php?p=4580595&postcount=8)
If you want to change icon of any app - r.click on applications-> edit menus->choose app from right side and r.click->properties-> double click on icon->wait for icons to load and choose another. You can also browse from after icons load to where others are stored

note on default - if the exec for vlc is something other than %U, change it to %m anyway

edit slightly less involved method
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by xjgnsdof on 2008-05-30
Try doing the following:

1) Pop in your DVD and look for the DVD in Nautilus under "Computer"
2) Right click the DVD, then click the "Open with" tab"
3) Select the application that you want to automatically play the DVD

Adapt the steps above for AVIs and other media formats.

---

### Post by philinux on 2008-05-30
Thats not selecting the default player which was wanted. 

Interesting if I do as suggested and pick VLC it crashes.

If I open VLC and select play disk it works fine.

---

### Post by spiderbatdad on 2008-05-30
With respect to inserted media, how about open the file browser: Places>>Home folder>> Edit>>preferences>>Media

---

### Post by philinux on 2008-05-31
> **spiderbatdad said:**
> With respect to inserted media, how about open the file browser: Places>>Home folder>> Edit>>preferences>>Media

Have you ckecked the options for DVD? It's not good really. Only Totem.

---

### Post by tom56 on 2008-05-31
Instead of arguing with each everyone else did anyone actually try to answer this guy's question? The solution is in a sticky post in (surprise!) Multimedia and Video.

> VLC AS DEFAULT DVD PLAYER IN UBUNTU 8.04 HARDY HERON SYSTEMS ONLY


To change the default DVD player in Hardy Heron to VLC (I strongly advise you do), open the terminal and copy and paste this command into it:

gksudo gedit /etc/gnome/defaults.list

Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to Places > Computer > Edit > Preferences > Media > DVD Video, select VLC

I agree that this is a pretty awful way of doing it and I believe it's being worked on.

---

### Post by rainwalker on 2008-06-01
I can attest to the difficulty of selecting default applications in Hardy as well. On Gutsy, everything was either in System > Preferences > Removable Drives and Media or System > Preferences > Preferred Applications. On hardy, neither of those give the same options that were available on Gutsy. Instead, it's now under System > Preferences > File Management or Edit > Preferences in Nautilus. 
Not only is this WAY less obvious, but it's also less configurable. Besides having to look on the forums to figure out how to change the default applications, but I had to edit text files to do it. This was not the case on Gutsy. On Hardy there's no simple button to add a new application to open things with, which is incredibly confusing. 
Yes, I'm aware you can right-click on things and in the Properties window choose what to open them with, but when you have to do that on a file-by-file basis rather than choosing one default for all of them, it's just a step backwards.

I've heard that the reason for this change is that Nautilus handles mounting in Hardy rather than gnome-mount, but that's no reason to make things harder to find/understand/change.

---

### Post by timcredible on 2008-06-04
yeah, hardy absolutely stinks in this regard - there's no way possible to change the default app for playing a dvd via a menu - all the ways that used to work don't anymore, and the ways suggested in this thread do not work - there is a no 'open with' in nautilus, there is no option to choose anything else that you've installed on your system either by menus or asking what to do when the dvd is inserted.  also, it's sad the number of people that replied to this thread with derogatory (sp?) remarks.  i guess i'll have to do it the way the one person said about the multi-step process with editing the default.list file manually.

---

### Post by Ekeluo on 2008-06-29
Okay this is just weird, talking about the above posts. 

Anyway why don't other programs (AWN, deskbar, tracker, etc..) respect the apps I chose to open my media in nautilus? I have chosen totem for most of them (avi,rmvb,wmv,flv,mpg,) but they all (tracker, etc) decide that other programs are more competent. Or something. [SIZE="5"]I DON'T CARE WHAT YOU THINK. OPEN IN THE MEDIA PLAYER I ASKED FOR![/SIZE]

[SIZE="1"]Or is there another way to set preferences for all programs? I've tried editing mime types, doesn't work.[/SIZE]

---

### Post by chrismja on 2008-11-15
I don't know if anyone is still having problems with this or not, but I was also having a difficult time selecting which program that i wanted to start when i plugged in my ipod. I'm using Intrepid, but I just went System->Preferences->File Management->then Media tab. Worked for me, maybe it'll help someone else too.

---

### Post by chrismja on 2008-11-20
Oh BTW, if you don't see File Management under System->Preferences then you will need to enable file management in your menu. To do this go to System->Preferences->Main Menu....at the bottom left hand side you will see the tab for the menu System->Prefernces. Click on Preferences then check to enable File Management in the right hand pane.

---

