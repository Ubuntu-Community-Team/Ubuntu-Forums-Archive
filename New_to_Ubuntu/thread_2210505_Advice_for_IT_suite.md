---
title: "Advice for IT suite"
date: 2014-03-11
forum: New to Ubuntu
---

### Post by caeras on 2014-03-11
Hi all,

Hoping some kind soul can help me out.  I work for a small UK charity, based in Chester and we have an IT suite for users to come and use the internet and word processing free of charge.  It is part of the UK Online initiative, which I suppose is similar to how a library works with internet access but we don't restrict someone to an hour or charge for use.  Users are quite varied from job seekers, older people, homeless people etc all with varying IT skills, some just come and use and others need a bit of support which we offer when needed.

I have some knowledge of Ubuntu and Xubuntu from installing and using them at home but not in a work environment where certain things need to be locked down.  I enjoy using my linux systems at home but I have no restrictions there and can fiddle with them as much as I like!

Due to the XP switch off, we are having a rethink and one of the solutions we have come up with is to install a linux based system on to 4 machines (currently on XP) and use them in the suite.  All they need to do is have internet access (Chrome/firefox would be best as people tend to be comfortable with these) and word processing (thinking open office or something else) so people can prepare CV's etc.  Ideally they would be able to save documents to the computer but they would be made aware that anyone can see them, so would be encouraged to use a memory stick.  

As we have a lot of people using the computers I don't want to create accounts for each person.  I was also thinking of a kiosk mode of some sort but the word processing and saving of documents is likely to be an issue with this?

All are Dell computers and running XP at moment, specs vary but roughly:
[LIST]
[*]2GB RAM
[*]Pentium 2.5ghz
[/LIST]

Therefore, the system needs to be:
[LIST]
[*]User friendly
[*]Internet ready (with flash etc)
[*]Word processing available
[*]Saving of documents to shared, open space
[*]Without need to update every few months
[/LIST]

I was thinking of Ubuntu 12.04 LTS as I think it will do all I need but wondering whether people think I would be better with lighter weight, maybe Xubuntu or something else (Mint for example?)

The next issue is the locking down, I was thinking of using the guest account but enabling saving of documents (found a link online for this), but I may not be on the right track here, as I said earlier this is not something I have experience of.  What I want to achieve is someone not being able to modify system settings or install anything, I know how to achieve this on MS using Group Policy but Linux I have no idea!

As an extra to this, we will be carrying out this move sometime in April and will be posting a volunteer opportunity for someone to help if possible.  If you are based in the Chester area, want some real life work experience and may be interested please drop me a private message. :KS

Thanks in advance, happy to provide further information.

---

### Post by Lars Noodén on 2014-03-11
Trusty Tahr will be released April 17th.  If that fits your schedule, you could start your experiment with Trusty beta now and then roll out Trusty.  The advantage there is that it is a LTS release and will have 5 years of support.

---

### Post by caeras on 2014-03-11
Thanks for the reply, appreciate it.

Had thought of that but think we need it done before then, although schedule hasn't been decided yet.  If we have to stick to 12.04 I'm not overly disappointed as it still gives us till 2017 I think?  However, if we can hold on then we definitely will.

Any thoughts on the other issues in my post?

---

### Post by Impavidus on 2014-03-11
As this is for occasional Linux users who are probably somewhat familiar to the Windows interface, it may be better to use Xubuntu. The xfce interface can be configuered to look similar to the Windows interface, whereas Unity (the default Ubuntu interface) definitely takes time to get used to. Not good for the occasional user.

I don't know whether people can save files to the hard disk when using kiosk mode or something like that. When you allow people to use a normal login they can change any user settings, but if you make a backup of the preferred user settings somewhere where they can't get to them, you can restore all settings with a single command using your own root permission.

---

### Post by ajgreeny on 2014-03-11
If you have one admin user (the first that is set up at install) and make a second user called whatever your charity is named but with normal, ie non-admin permissions, you could set the machines to autologin to this second user, and that user will then be unable to install any applications or change system settings but will be able to use all applications and save files.

One problem would perhaps be that all the computer users would be saving files to the same /home folders, so everyone would be able to see everyone else's files, but you mention shared space so I presume that is not a big problem for your users..

I would also suggest that with the specs of those machines you look at Lubuntu or Xubuntu rather than Ubuntu; they will have lower resource requirements and also look more like Win XP.

---

### Post by caeras on 2014-03-11
Thanks for the advice so far.

I agree with the idea of xubuntu so likely to go down that route, although concerned about the LTS for it as it appears to only have another 12 months on it?

Does anyone have a link to show me how to theme it similar to Windows?  It doesn't need to be exactly like it, just something that would be familiar.

Also does anyone have any details on what a non-admin person can and can't do?  And is there an easy way to restrict them more if needed?

---

### Post by The Cog on 2014-03-11
> **ajgreeny said:**
> If you have one admin user (the first that is set up at install) and make a second user called whatever your charity is named but with normal, ie non-admin permissions, you could set the machines to autologin to this second user, and that user will then be unable to install any applications or change system settings but will be able to use all applications and save files.
I would be against this. My reason is that as people use the browser, it will accumulate cookies, form entries and perhaps usernames/passwords that could inadvertantly cause leakage of private information, account details, erroneous logins etc. to later users.

I think that because of this, a kiosk mode is essential.

---

### Post by caeras on 2014-03-11
> **The Cog said:**
> I would be against this. My reason is that as people use the browser, it will accumulate cookies, form entries and perhaps usernames/passwords that could inadvertantly cause leakage of private information, account details, erroneous logins etc. to later users.

I think that because of this, a kiosk mode is essential.

Thanks for your help, appreciate your response and hadn't thought of that.

Would a kiosk mode allow people to use word processing though, and save documents to a shared space?  If so how would I implement this?

Thinking the guest account may be a better solution?  As I understood this would delete data every time?  However, I need some sort of shared file system so people can save documents if needed (although they will be persuaded to use their own memory stick)

---

### Post by ajgreeny on 2014-03-11
Xubuntu 12.04 has only one more year but I believe 14.04 will have the full 5 year support, so if you can wait for that it may be worthwhile doing so.  It already looks good at the moment, so if you are fairly computer literate you might try using the trusty daily image now, however, it sounds as if that is probably not a wise move as you do not yet really know Linux.

To theme Xubuntu to look like windows all you really need to do is move the top panel to the bottom, after removing the autohidden bottom panel, or better moving the bottom one to one side for an easy launchbar, as I have, see screenshot.  I moved the bottom panel to the left side, as you can see and for this shot the top panel is at the bottom, much like WinXP or Win7, but you could leave it at the top if you wanted.

---

### Post by caeras on 2014-03-11
> **ajgreeny said:**
> Xubuntu 12.04 has only one more year but I believe 14.04 will have the full 5 year support, so if you can wait for that it may be worthwhile doing so.  It already looks good at the moment, so if you are fairly computer literate you might try using the trusty daily image now, however, it sounds as if that is probably not a wise move as you do not yet really know Linux.

To theme Xubuntu to look like windows all you really need to do is move the top panel to the bottom, after removing the autohidden bottom panel, or better moving the bottom one to one side for an easy launchbar, as I have, see screenshot.  I moved the bottom panel to the left side, as you can see and for this shot the top panel is at the bottom, much like WinXP or Win7, but you could leave it at the top if you wanted.

Great information, thanks.

Would it be a massive risk going down the 14.04 route early?  Considering machines are only for web and word processing?

Also, if I did go down the early route, when the full version is released would I just update like I normally would using xubuntu?  May be a daft question that but just want to check beta-full upgrade is the same as full (old)-full (new) upgrade if that makes sense?

---

### Post by The Cog on 2014-03-11
> **caeras said:**
> Thanks for your help, appreciate your response and hadn't thought of that.

Would a kiosk mode allow people to use word processing though, and save documents to a shared space?  If so how would I implement this?

Thinking the guest account may be a better solution?  As I understood this would delete data every time?  However, I need some sort of shared file system so people can save documents if needed (although they will be persuaded to use their own memory stick)

I don't know anything about kiosk mode, I've just heard about it. I have used a guest account once, and discovered that I was unable to save a downloaded file anywhere outside of the guest home folder (which gets vapourised upon logout). So I don't know how to overcome this problem. Maybe arranging an account with a login script that removes all the browser's folders (or replaces them with a clean set to replace the settings) might be an option. 

I think that installing a recent 14.4 build would be a fairly safe bet now. It's in feature freeze so the mad rush to get the last few changes in is over and there should be relatively few updates between now and release. I have been using 14.04 for a couple of months, and it has been pretty stable anyway. An install of 14.04 now will get updated to the proper release version as you install updates.

---

### Post by caeras on 2014-03-11
Thanks for that, I found [https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession) and at the bottom it says "Save files on disk".  Would that work on xubuntu or just ubuntu or does it make no difference, I get confused with things like that sometimes!

---

### Post by ajgreeny on 2014-03-11
> **caeras said:**
> Thanks for that, I found [https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession) and at the bottom it says "Save files on disk".  Would that work on xubuntu or just ubuntu or does it make no difference, I get confused with things like that sometimes!
It looks as if it would work for all the *ubuntu family, but I'm not certain about that as I have never needed the guest session on my machines and therefore have little experience of how to use it.

I also think that The Cog is right in saying that the risk associated with installing 14.04 now is very small.  I have been running it in a virtual machine for a while with no real problems related to the OS itself,more to do with the virtualisation software which I was not so experienced in using.

I had not really thought about the problems that The Cog mentions of cookies etc etc, but he is correct.  It is possible to set the browser preferences to delete all such session info when closed, but the risk is still there.  However, my knowledge of kiosk mode is zero, so I will have to leave that to others to help you with.

---

### Post by PondPuppy on 2014-03-11
A brief note on The Cog's observation about browser history and cookies - might tentatively suggest setting Firefox to destroy all cookies, history, and cache on exit.

---

### Post by whitesmith on 2014-03-11
The easiest way is to use Gnome 3 as your DE, since that gives a reasonable emulation of Windows' Start Menu. Keep in mind that XP users are familiar with a text mode Start menu. That rules out Canonical's Unity Interface because it is confusingly graphical (yes, and I'm prepared to argue the point!) and requires a rigid mind set to appreciate. Others have recommended 14.04; I would go with that and gain full five years' worth of support.

Questions of browser security can be dispatched by using FF in Private Browsing mode. Locking down a *nix box is far easier than attempting the same under Windows.

---

### Post by caeras on 2014-03-14
Thanks for all the help, think we are delaying till start of May so can implement Xubuntu LTS.  

Think we will go for standard accounts, lock them down where we need to and enable firefox in private mode.

Thanks again everyone, I'm sure I will be back!

---

