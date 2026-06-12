---
title: "The poor choices of the GNOME team"
date: 2008-03-04
forum: Recurring Discussions
---

### Post by siddartha on 2008-03-04
I was wondering after a system cleanup what's the proportion of bad apps that I have to erase after a system upgrade just because they are included in the GNOME desktop. And I have came to a socking observation: as far as the front-apps the GNOME desktop is a very poor choice for the user. It's like getting Windows 98 and explaining the virtues of the "old and tested".

Linux has been plagues from its start by the touch of coolness. Various projects were drifting away from the BSD standard just because it was a new way of doing it. So far so good. The problems would arise when the implementation made communication impossible between the two apps.

The next problem was that the Linux community is extremely impaired when it comes to memory. The same problems that were major issues with QT and KDE some years ago, now are hailed as a sign of progress when the corporations have taken over every notable project.

So nowadays the GNOME apps are bound to be in one of the two categories - the cool or the corporate. And the smaller projects that managed to get in have to get into one of those categories fast or be removed as soon as something easier to put on one side is going to pop.

CD burning for example. There is a plethora of cool interfaces. They are in almost every case a half-baked project that is barely usable beyond something so basic even a newbie can get in the CLI. And Gnome is changing these apps when something cooler gets the spotlight. These apps split in many ways and redouble their functionality with ease. Like the larger projects for GNOME they are doing their best to mimic some commercial application, but when put side by side they fail. You had GnomeBaker. Now they have Brasero. All cool projects with cool names telling one way or another in a thousand languages that they do "burn" CDs. Pathetic, painfully pathetic. Keep in mind that the backends are the same two or three libs that are here for quite some time. Yet the darn graphical interface can't even follow all the original functions when they should have added something extra.

CD Audio - another app. Why do you need an extra app for just an intermediary step of decoding a compressed file to PCM? Well, they do have an extra app for that. And that is for making the Audio CD. For extracting the Audio there is yet another official app.

And if all this wasn't enough, there is also a plugin for Nautilus. My brothers in the oss pain - why are they bothering to include all these overnight hacks into the desktop? Get the Nautilus plug in, throw an interface with some options and dump fast all the others.

Keep in mind that on the other side of the fence, there is K3B which is both stable and covers this dozen of more or less official GNOME projects which beyond drag and drop they have a hard time communicating. Thank God that the cddb interrogating lib is only one so you can set them all to read from the same directory.

Graphics. Here is easy. There is Eye of the Gnome. A slow loading app that doesn't "see" too many graphic formats, but at least now, in 2008 has reach the point where it can be aware of the color profiles. Guess that would take an extra second to put the image on the screen.

Document viewers. After lots of projects all integrating Ghost View and Xpdf and all bringing next to nothing than some extra dependency and the latency that comes with it... now there is evince. A project that had a lot of marketing going. It was hailed the all encompasing solution to see documents. The result? Just another crappy app that reuses the code from GV and Xpdf. The developers are unable to integrate parts from other open source apps so far. Instead of reading all Office files (both Microsoft and free) and some ebook formats, they are just polishing the same two document formats over and over again. Been reading what's the fall-on-your-*** feature for Gnome 2.20? Well, it can read forms as well. As in PDF forms. What about the whole thousand and one document formats? It's two and a half years since the inclusion in Gnome and there is a light - now you can see the PDF forms. Hmm, even the Adobe guys have made some leaps forward with their Linux support. And the Reader does the PDFs better than all those other libs although I was told that the PDF format is ready available online as well. How come the best PDF generator is pdftex which is free and on the other hand there is no good reader other than the official implementation? Document viewer? Nope. Some PDF reader is more precise.

Archives... file roller. A true pain in the behind some years ago, now I wouldn't dare touch it. But I am checking their page and it says there that is only a wrapper with a cute interface. The app is doing zero, just calling other apps that have to be installed. That's nice. I do hope they have support for the whole list of options and switches for those archiving apps because the list sure is short. 10 formats? It's only a wrapper guys! It should be able to support every known archiving app that does run on Linux or you are missing the whole point! The good part of this is that you have quite a lot of archiving tools on Windows that do run pretty well on Wine. And if you need speed, nothing beats the CLI compared with the overhead resulting from this app.

Nautilus is good. Back in the days when they dumped GMC it was unusable. Now it's usable and has a feature no other file manager has so far - the ability to put some stickers on your files. Else, it doesn't excell at anything. It's just a way to be proud - we have a complete desktop now.

Epiphany, now this is good. And with the move from Geko I think we do have a chance to get rid of Firefox which has more holes than features. But, hey! it's not a hole it's a feature.

Note taking? Tomboy. The poorest of them options to have a cute little yellow post it on your desktop. But that is explanable - it was a way to consolidate the baby project of Icaza - mono. The other way in is fspot which has the same problems as Evince - few formats, slow development, nothing extra than the app it is trying to clone. Worse, it's not even stable or has all the advertised features. Just erasing those two helped me get rid of a dozen mono-related libs that do nothing at all other than giving Icaza the feeling that he is loved and that an app running mono would be welcomed on the Gnome desktop.

Media player. Now this is a heavy one. Totem. Almost no options. Really no value other than this poor and slow interface as it is based on other backends. I wonder how come Kaffeine can do so much and Totem, based on the same back end can do so little? All the brain dead script kiddies in the Gnome team?

Evolution. A mammoth with the stability of the early Outlook which is trying to mimic. After years of pain it got to the point of being at least stable (it is still large and slow) and it was sold. Now it's a corporate app catering for the corporate users. So the Google Calendar might not work but looky here we have integration with the Exchange. Meaning I can offer you the chance to delete the mail sent without checking the delivery address, but that's about it. I remember when Star Office and the newly appeared Open Office were strongly criticised for being a monolith. An app all in one. After all One could have started Word for writting a letter and that doesn't start Excel also. Now all this is forgotten. The open source has corporate backing. Meaning if I click by mistake on a mailto link I have to wait untill the calendar and the to do list and addressbook are loaded to close the new mail.

Now this is one thing I don't understand so please someone enlighten me: if Gnome is moving towards usability, why not get something like Balsa or whatever other GTK app, put the Gnome extensions and link it with the Exchange extension if you need it so much? Because lately I have the feeling that with all this corporate marketing Windows is winning the game. After all this integration and eye candy and whatever... Vista doesn't seem such a bad idea. It's a pain to work with their registration and the fact that they are losing backwards compatibility. But, at least they are sincere.

Not all apps are bad. Ekiga is a very good product and I never had any problems running it. And it can offer all those things that Gaim is promising since 2000 and never delivered like multimedia communication.

What's going on? Who is making the decisions there? Reading the roadmap for 2.22. The guys are amazing. Evince might get a better history menu. Gee. If there's anybody reading from the team - do get to talk with the Adobe guys. You stand a better chance to get them integrate with Gnome in the following year than getting Evince to read .doc files.

From the same roadmap I hail the corporate heads who told the Evolution team that they should integrate other editors. Years ago they were explaining on the mailing list the virtues of their own slow editor and how the rest of the world better get used to it. From the same smart guys (not the developers thank you) comes the possiblity to drop the virtual search folders and get some of your memory back.

Now when the world is moving to XMP and Windows XP (does work with IPTC!) is getting discontinued the eye of the gnome is starting to understand IPTC. Cool! Only that I see this as retarded. It's only making the hooks to get a lib that is years old work with your crappy app. Or are they trying to surprise me and they took so long because they were writing their own implementation? Guess not.

In the same news also the dictionary has heard of wikipedia. The darn thing is so well entrenched that you have to erase a whole pack to get this out of your menus.

Sadly projects that are far more advanced in usability lack the developer power to break free from the shadow of this putrid monster. Window Maker is back with no new stuff. E17 is a promising desktop. It has stability problems but already is more advanced in working with multiple screens. And so on.

Cheers,
Sidd

---

### Post by p_quarles on 2008-03-04
Moved to Recurring Discussions.

---

### Post by awakatanka on 2008-03-04
> **p_quarles said:**
> Moved to Recurring Discussions.

Little trigger happy, because i didn't see this kind of post before our is it because its a gnome complain?

At least post also the similar topics if its recurring discussion.

Don't understand some chooses also but  isn't it up to the distro to put in applications they want?

---

### Post by FuturePilot on 2008-03-04
I'd have to disagree with you on some of those.
I have found EOG to be the best, fastest image view out there. It's been able to open just about every format I've thrown at it. I've tried others and they can't seem to open half the formats EOG can.

Gnome Baker and Brasero can both burn audio CDs. You don't need a separate app for that. And some of your other complaints about that have been taken care of in Hardy. The Nautilus CD burner plugin and Serpentine have both been removed and replaced with Brasero.

---

### Post by Vadi on 2008-03-04
It is a recurring discussion because bashing of desktop enviroments is very common.

---

### Post by tdrusk on 2008-03-04
> **siddartha said:**
> I was wondering after a system cleanup what's the proportion of bad apps that I have to erase after a system upgrade just because they are included in the GNOME desktop. And I have came to a socking observation: as far as the front-apps the GNOME desktop is a very poor choice for the user. It's like getting Windows 98 and explaining the virtues of the "old and tested".

Linux has been plagues from its start by the touch of coolness. Various projects were drifting away from the BSD standard just because it was a new way of doing it. So far so good. The problems would arise when the implementation made communication impossible between the two apps.

The next problem was that the Linux community is extremely impaired when it comes to memory. The same problems that were major issues with QT and KDE some years ago, now are hailed as a sign of progress when the corporations have taken over every notable project.

So nowadays the GNOME apps are bound to be in one of the two categories - the cool or the corporate. And the smaller projects that managed to get in have to get into one of those categories fast or be removed as soon as something easier to put on one side is going to pop.

CD burning for example. There is a plethora of cool interfaces. They are in almost every case a half-baked project that is barely usable beyond something so basic even a newbie can get in the CLI. And Gnome is changing these apps when something cooler gets the spotlight. These apps split in many ways and redouble their functionality with ease. Like the larger projects for GNOME they are doing their best to mimic some commercial application, but when put side by side they fail. You had GnomeBaker. Now they have Brasero. All cool projects with cool names telling one way or another in a thousand languages that they do "burn" CDs. Pathetic, painfully pathetic. Keep in mind that the backends are the same two or three libs that are here for quite some time. Yet the darn graphical interface can't even follow all the original functions when they should have added something extra.

CD Audio - another app. Why do you need an extra app for just an intermediary step of decoding a compressed file to PCM? Well, they do have an extra app for that. And that is for making the Audio CD. For extracting the Audio there is yet another official app.

And if all this wasn't enough, there is also a plugin for Nautilus. My brothers in the oss pain - why are they bothering to include all these overnight hacks into the desktop? Get the Nautilus plug in, throw an interface with some options and dump fast all the others.

Keep in mind that on the other side of the fence, there is K3B which is both stable and covers this dozen of more or less official GNOME projects which beyond drag and drop they have a hard time communicating. Thank God that the cddb interrogating lib is only one so you can set them all to read from the same directory.

Graphics. Here is easy. There is Eye of the Gnome. A slow loading app that doesn't "see" too many graphic formats, but at least now, in 2008 has reach the point where it can be aware of the color profiles. Guess that would take an extra second to put the image on the screen.

Document viewers. After lots of projects all integrating Ghost View and Xpdf and all bringing next to nothing than some extra dependency and the latency that comes with it... now there is evince. A project that had a lot of marketing going. It was hailed the all encompasing solution to see documents. The result? Just another crappy app that reuses the code from GV and Xpdf. The developers are unable to integrate parts from other open source apps so far. Instead of reading all Office files (both Microsoft and free) and some ebook formats, they are just polishing the same two document formats over and over again. Been reading what's the fall-on-your-*** feature for Gnome 2.20? Well, it can read forms as well. As in PDF forms. What about the whole thousand and one document formats? It's two and a half years since the inclusion in Gnome and there is a light - now you can see the PDF forms. Hmm, even the Adobe guys have made some leaps forward with their Linux support. And the Reader does the PDFs better than all those other libs although I was told that the PDF format is ready available online as well. How come the best PDF generator is pdftex which is free and on the other hand there is no good reader other than the official implementation? Document viewer? Nope. Some PDF reader is more precise.

Archives... file roller. A true pain in the behind some years ago, now I wouldn't dare touch it. But I am checking their page and it says there that is only a wrapper with a cute interface. The app is doing zero, just calling other apps that have to be installed. That's nice. I do hope they have support for the whole list of options and switches for those archiving apps because the list sure is short. 10 formats? It's only a wrapper guys! It should be able to support every known archiving app that does run on Linux or you are missing the whole point! The good part of this is that you have quite a lot of archiving tools on Windows that do run pretty well on Wine. And if you need speed, nothing beats the CLI compared with the overhead resulting from this app.

Nautilus is good. Back in the days when they dumped GMC it was unusable. Now it's usable and has a feature no other file manager has so far - the ability to put some stickers on your files. Else, it doesn't excell at anything. It's just a way to be proud - we have a complete desktop now.

Epiphany, now this is good. And with the move from Geko I think we do have a chance to get rid of Firefox which has more holes than features. But, hey! it's not a hole it's a feature.

Note taking? Tomboy. The poorest of them options to have a cute little yellow post it on your desktop. But that is explanable - it was a way to consolidate the baby project of Icaza - mono. The other way in is fspot which has the same problems as Evince - few formats, slow development, nothing extra than the app it is trying to clone. Worse, it's not even stable or has all the advertised features. Just erasing those two helped me get rid of a dozen mono-related libs that do nothing at all other than giving Icaza the feeling that he is loved and that an app running mono would be welcomed on the Gnome desktop.

Media player. Now this is a heavy one. Totem. Almost no options. Really no value other than this poor and slow interface as it is based on other backends. I wonder how come Kaffeine can do so much and Totem, based on the same back end can do so little? All the brain dead script kiddies in the Gnome team?

Evolution. A mammoth with the stability of the early Outlook which is trying to mimic. After years of pain it got to the point of being at least stable (it is still large and slow) and it was sold. Now it's a corporate app catering for the corporate users. So the Google Calendar might not work but looky here we have integration with the Exchange. Meaning I can offer you the chance to delete the mail sent without checking the delivery address, but that's about it. I remember when Star Office and the newly appeared Open Office were strongly criticised for being a monolith. An app all in one. After all One could have started Word for writting a letter and that doesn't start Excel also. Now all this is forgotten. The open source has corporate backing. Meaning if I click by mistake on a mailto link I have to wait untill the calendar and the to do list and addressbook are loaded to close the new mail.

Now this is one thing I don't understand so please someone enlighten me: if Gnome is moving towards usability, why not get something like Balsa or whatever other GTK app, put the Gnome extensions and link it with the Exchange extension if you need it so much? Because lately I have the feeling that with all this corporate marketing Windows is winning the game. After all this integration and eye candy and whatever... Vista doesn't seem such a bad idea. It's a pain to work with their registration and the fact that they are losing backwards compatibility. But, at least they are sincere.

Not all apps are bad. Ekiga is a very good product and I never had any problems running it. And it can offer all those things that Gaim is promising since 2000 and never delivered like multimedia communication.

What's going on? Who is making the decisions there? Reading the roadmap for 2.22. The guys are amazing. Evince might get a better history menu. Gee. If there's anybody reading from the team - do get to talk with the Adobe guys. You stand a better chance to get them integrate with Gnome in the following year than getting Evince to read .doc files.

From the same roadmap I hail the corporate heads who told the Evolution team that they should integrate other editors. Years ago they were explaining on the mailing list the virtues of their own slow editor and how the rest of the world better get used to it. From the same smart guys (not the developers thank you) comes the possiblity to drop the virtual search folders and get some of your memory back.

Now when the world is moving to XMP and Windows XP (does work with IPTC!) is getting discontinued the eye of the gnome is starting to understand IPTC. Cool! Only that I see this as retarded. It's only making the hooks to get a lib that is years old work with your crappy app. Or are they trying to surprise me and they took so long because they were writing their own implementation? Guess not.

In the same news also the dictionary has heard of wikipedia. The darn thing is so well entrenched that you have to erase a whole pack to get this out of your menus.

Sadly projects that are far more advanced in usability lack the developer power to break free from the shadow of this putrid monster. Window Maker is back with no new stuff. E17 is a promising desktop. It has stability problems but already is more advanced in working with multiple screens. And so on.

Cheers,
Sidd

Yet you use Ubuntu 7.10?

---

### Post by bruce89 on 2008-03-04
I don't see you volinteering to add the 1001 new document formats to Evince. It's a lot more difficult that you'd think. It supports PDF, PS, TIFF, DVI, DjVu and comics currently.

You also don't seem to understand the GNOME (and UNIX) philosophy of "do one thing, and do it well". That's why GNOME applications tend to only do one thing.

---

### Post by siddartha on 2008-03-04
> **bruce89 said:**
> I don't see you volinteering to add the 1001 new document formats to Evince. It's a lot more difficult that you'd think. It supports PDF, PS, TIFF, DVI, DjVu and comics currently.

You also don't seem to understand the GNOME (and UNIX) philosophy of "do one thing, and do it well". That's why GNOME applications tend to only do one thing.

PDF forms are also part of the PDF standard, yet they are a new addition. I'm quite sure the support for the formats that you mention is at the same level. So far, on Gnome Abiword is far more of a document viewer that Evince could get in a few years.

And about the philosophy... the say specifies "and do it well". Inkscape is doing well, although it's not a Gnome app. Abiword is doing well and getting better. Gnumeric also. But the others are.. a pain. A 2M applet to show you the darn trash can? Also, getting to one thing is a relative notion. Take for example the burning section. An app for burning audio cds and another one to do all the burning including the audio cd? Weird philosophy. And don't get near Evolution or you'll regret it. KDE Pim is in this spirit... and the darn thing just works. With Evolution you have just one thing: calendar, addressbook, mail, to do list. And if one of them is crashing (it does happen) here go down all of them.

This is my whole issue. The slogans are all forgoten. People like yourself just pop them here and there without so much connection with what's going on. And it's sad to see this going away because people just dump a slogan "eat **** or go code". This attitude is the one stopping the development in the end.

It's even worse, there are so many wrong apps that are pushed forward over the better choices. OpenOffice might be good, but should be optional. It's huge and slow, and requires even extra large dependencies like Java. And this is slowing the acceptance of projects like Abiword or Kword which don't have the huge corporate backing. The push of Firefox over the desktop, although as a holy fight against the Internet Explorer has led people to another bad choice and a slow down in other projects which are less used. MacOSX users get away with Safari tho.

---

### Post by Vadi on 2008-03-04
I didn't find Abiword or Kword to compare to my needs at all. OpenOffice has at least *some* recognition outside the teeeeeny linux world, and that helps new people. Plus, with so many universities and companies adopting OOo, it's hard to argue that it's not a good choice.

---

### Post by p_quarles on 2008-03-04
All other issues aside, I'd like to point out that neither Firefox nor OpenOffice.org have anything to do with the GNOME developers' choices. Those are default applications in Ubuntu, but neither is related to the GNOME project itself. 

Both of those applications are also defaults in Mandriva's KDE distro. Firefox and OpenOffice.org are also, coincidentally, not KDE applications.

---

### Post by mdsmedia on 2008-03-05
I like Abiword and am using Gnumeric more for my own spreadsheets, but compatibility with MS Office documents requires a program that will open Office documents. For that reason alone I think OpenOffice is a good choice.

I've installed OOo on my Windows desktops simply as a tool to create PDFs. Yes OOo is slow to load and not as pretty as Office, but with 90% of the functionality, it's not a bad option.

As far as the choices the Gnome team have made, I'm still using Ubuntu Dapper with some KDE apps, because some KDE apps prvide what I want, but the choice of installing ONE Gnome app to do ONE thing appeals to me.

I installed Kontact because I like it as a PIM, but I removed Kmail because I already have an email client. That appeals to me....being able to choose an app that suits me rather than a suite in which some apps suit me and others don't.

---

### Post by deepclutch on 2008-03-05
the miguel and mono thing u said is reality!WTH :x

---

### Post by siddartha on 2008-03-05
> **Vadi said:**
> I didn't find Abiword or Kword to compare to my needs at all. OpenOffice has at least *some* recognition outside the teeeeeny linux world, and that helps new people. Plus, with so many universities and companies adopting OOo, it's hard to argue that it's not a good choice.

Hehehe
You need to learn some history. Back when Microsoft Office was accepted it was THE worst office pack choice. Your answer would actually prove the contrary of what you actually meant.

---

### Post by siddartha on 2008-03-05
> **p_quarles said:**
> All other issues aside, I'd like to point out that neither Firefox nor OpenOffice.org have anything to do with the GNOME developers' choices. Those are default applications in Ubuntu, but neither is related to the GNOME project itself. 

Both of those applications are also defaults in Mandriva's KDE distro. Firefox and OpenOffice.org are also, coincidentally, not KDE applications.

Yes, and the fact that Gnome has alternative to these two is one of the few good things about it.

---

### Post by siddartha on 2008-03-05
> **mdsmedia said:**
> I like Abiword and am using Gnumeric more for my own spreadsheets, but compatibility with MS Office documents requires a program that will open Office documents. For that reason alone I think OpenOffice is a good choice.

I've installed OOo on my Windows desktops simply as a tool to create PDFs. Yes OOo is slow to load and not as pretty as Office, but with 90% of the functionality, it's not a bad option.

As far as the choices the Gnome team have made, I'm still using Ubuntu Dapper with some KDE apps, because some KDE apps prvide what I want, but the choice of installing ONE Gnome app to do ONE thing appeals to me.

I installed Kontact because I like it as a PIM, but I removed Kmail because I already have an email client. That appeals to me....being able to choose an app that suits me rather than a suite in which some apps suit me and others don't.

If you are not too fussy about it, CUPS gives a nice virtual PDF printer which is good. And there are a couple of apps that can take care of finer work with PDFs like encryption. Bottom line CUPS and one of those apps are better than OO PDF export and CUPS alone is easier and faster. Never had the curiosity to compare the output tho.

As far as working with different apps, we have freedesktop which is a commendable action, otherwise the barbarian developers already drifted away from one another to the point that was barely any communication. Thanks to this initiative Gnome apps are more well behaved at least.

---

### Post by deepclutch on 2008-03-05
developers are community members in a FOSS world.there is NO need of calling someone barbarian :x

---

### Post by dmgExP on 2008-03-06
I must agree with those who reject the Totem movie player.  It is a shame that this is given as default when it performs so badly.

I started out playing my DVDs with totem, having nothing else to compare it to, and was disappointed but not surprised that it didn't show the menu or play special features etc.

But when it refused to fast-forward or backwards when playing a dual-layer DVD I got somewhat peeved.  My patience evaporated entirely when Totem spontaneously jumped over various 20 minute portions of The Wizard of Oz ---  potholes on the Yellow Brick Road?? Glinda censoring the silly bits??

Then I installed VLC and what a difference, [COLOR="Magenta"]everything[/COLOR][COLOR="Red"] now[/COLOR] [COLOR="Teal"]plays[/COLOR] [COLOR="Orange"]perfectly[/COLOR][COLOR="Orange"][COLOR="Blue"]!!![/COLOR][/COLOR]

So my question is: Why is Totem the only movie player installed by default??

---

### Post by deepclutch on 2008-03-06
totem with gstreamer works perfectly fine for me.only thing is acc to Gnome HIG(Human Interface Guidelines) they have disabled extended options and functionalities.that is bad :evil:

---

### Post by justin whitaker on 2008-03-06
I've been running a bit of an experiment as I am using Hardy Alpha 5 (now 6 I guess). 

I hate Gnome. Or at least, I used to. 

I wanted to test the next LTS on it's own merits, not "let's install KDE and forget about Gnome."

The more time I spend in this DE, the more I get it. No, not all of the app choices are perfect, but it's really well done as a complete package. 

I don't really get the Totem hate, since it runs fairly well. WIth all the restricted drivers for Gstreamer, there is little that it cannot handle. I always install VLC and MPLayer, because I want to be sure that I can play everything...but there are valid reasons why these cannot be added to the default desktop in both Ubuntu and Gnome. 

Rhythymbox is growing on me as well. It has a clean interface, and does well with playback and podcast catching. 

Tomboy is good, Brasero is also good, the Text editor gets the job done...even Evolution has improved. 

I even like the twin panel approach...it puts a lot of information right in the corners, where it should be. 

So, I have to revise my Gnome hate. It's growing on me, and I'm hard pressed to change it just because I generally prefer KDE. I'll use PC-BSD for that. :)

I guess I have to say that if the GNOME apps are so bad, then figure out a way to help make them better.

---

### Post by SunnyRabbiera on 2008-03-10
meh for me file roller is much better then ark, the most recent versions of it suck

---

### Post by dmgExP on 2008-03-16
Re Totem Movie Player not playing properly:

Finally installed all the right codecs so that it now plays correctly.  I think installing totem-xine fixed the problem.

It would seem that if the "Play Disk" function on the Movie menu is inoperative then Totem wont play properly.  The function now works and everything works fine without skipping a beat.

The problem is that many things in Linux can be made to almost work by doing it the wrong way.

---

### Post by deepclutch on 2008-03-17
"leafpad" is a small but easy editor in Gnome :)

---

### Post by SunnyRabbiera on 2008-03-17
still for me gnome is the better at least until KDE4.1 is ready, really I think the KDE development team botched it up with the release of KDE4, it just feels so unfinished.

---

