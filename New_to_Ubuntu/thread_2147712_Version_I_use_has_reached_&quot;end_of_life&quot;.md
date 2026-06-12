---
title: "Version I use has reached &quot;end of life&quot;"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by gaitedlady on 2013-05-22
and my computer is prompting me to upgrade. The daughter who set up my laptop is now in the military (OTS) and I don't have access to her. I can't call her right now, and I have a few questions.

The current version I use is 11.10, and I've loved it. Here are my questions:

1. I don't know which version I should upgrade to. I'm an author, so I have a great deal of reference bookmarks, professional contacts, and the books that I'm currently working on, saved on this laptop (but my books, and all my music and personal photos, are also backed up on in a cloud and on my external terabyte drive.) I do not do any spreadsheets, charts, or anything like that. I write fiction.

2. If I upgrade will I lose any information on this laptop? All my important information is backed up as of last night. But I seem to remember my daughter doing this once before and other than the user interface looking different, all my information was still on the laptop.

3. I never did learn how to back up all my bookmarks. I really cannot afford to lose my research links. Will my bookmarks folder go empty again? Is there a way to save those links?

If someone can please reply, I would be most appreciative. I have two more months before the darling daughter will come home for a few days before leaving me again for another training facility in another part of the country. Currently Ubuntu is prodding me about two to three times per week, and I expect it will only get more insistent before I have to do something.

Thanks!

Sandy

---

### Post by SuperFreak on 2013-05-22
While someone else will probably help you with these problems I might suggest how to back up bookmarks. If you are using Firefox click on "Bookmarks" (top  menu) followed by "show all bookmarks". Then click on "Import and Backup" followed by "backup" and select a place for your backup(external drive maybe) and a file name. You can also save the file as a HTML file (select export to HTML) which may be more universal if you are importing bookmarks into a different browser. You could always do both.

See [HERE]("http://kb.mozillazine.org/Backing_up_and_restoring_bookmarks_-_Firefox") for the differences between files

---

### Post by Frogs Hair on 2013-05-22
I will address some of these issues and I'm sure others will add their recommendations .  

1.Back up everything important to a removable device before proceeding. 

2. The operating system will upgrade to 12.04 by default . I don't how that will go because the 11.10 repositories are closed and hopefully the system was up to date before that happened.

3. Most browsers and mail clients allow the export of bookmarks/ contacts which can be saved and imported for later use. Firefox, Chrome and Opera all have sync type services that store browser data on line that you can access on other devices and computers by logging in. If you open unsorted bookmarks in Firefox you will see export and backup on top of the  window that  opens. 

4. Upgrades work well for some and not for others and that is why #1 is so important.

[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

### Post by souravc83 on 2013-05-22
I will make another suggestion. Don't upgrade right now. I am living well with 11.10. 
Generally, the default upgrade isn't the best, and a fresh install is a better route to go.
Who wants to do that, when 11.10 works fairly well for what I do. 

Of course, if you need something in particular, go for it. Or if you're excited about the new features in 12.04, go for it. 
You can probably wait for your daughter to come and set it up.

---

### Post by monkeybrain2012 on 2013-05-22
I think it is probably a better idea to back up your important data and  do a clean install instead of an upgrade. Upgrade seems to be problematic for many people.

Here is a detailed tutorial
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Download the 12.04 LTS iso(instead of 13.04)  it has long supported peroid so you don't have to worry about reinstalling for another 4 years. [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) 
The drop down box is defaulted to 32 bit, but you may want 64 bit. To determine which one you are currently running so you can down load the right iso, open a terminal and type
```
uname -m
```

If the output is i686 then it is 32 bit, if it is x86_64 then you would want the 64 bit iso.

---

### Post by uRock on 2013-05-22
If you want a secure system, then upgrade.

The best way to back up Firefox, if that is what you mean by bookmarks, then copy .mozilla to external media. .mozilla is a hidden file within your /home folder. To unhide hidden files open the folder then hit Ctrl+H. This will have your bookmarks, history, addons, and saved passwords.

---

### Post by monkeybrain2012 on 2013-05-22
> **souravc83 said:**
> I will make another suggestion. Don't upgrade right now. I am living well with 11.10. 
Generally, the default upgrade isn't the best, and a fresh install is a better route to go.
Who wants to do that, when 11.10 works fairly well for what I do. 

Of course, if you need something in particular, go for it. Or if you're excited about the new features in 12.04, go for it. 
You can probably wait for your daughter to come and set it up.

Well you are not getting security updates and it may be risky if you go online.

---

### Post by gaitedlady on 2013-05-23
> **monkeybrain2012 said:**
> Well you are not getting security updates and it may be risky if you go online.

I do go online... It's necessary for my business. Which is why I have to do something, and I think the prompts to upgrade are annoying enough now that I am concerned about security.

I've copied .mozilla and my bookmarks over to the external terabyte drive and backed up my active manuscripts and all the research data folders that accompany them. Since I'm not sure how long upgrading will take or how much bandwidth it will use (I'm on satellite internet,) I'll begin my upgrade download at 2 a.m. when I have my free download window.

Now I have a question about Rhythmbox.... Will that still be on the computer, or will it and all my music need to be reloaded?  I don't remember what the darling daughter did when she upgraded me a few years ago, and since I can't just call her to ask, I'm hoping you ladies and gentlemen don't mind me asking.

Thanks a bunch! I really appreciate your help!
Sandy

---

### Post by Dennis N on 2013-05-23
If you are upgrading with the update-manager, your applications and data (including your music) should be retained. Versions of applications will be replaced by newer ones. You must back up your data to be safe with this method.

The prompts to upgrade that are annoying you could have been disabled, but it looks like you are going ahead with your upgrade.

For what it's worth, my preference in upgrading is to keep the existing O.S. until I am sure the newer one is working for me without problems. This can be done by doing a new install of the new version side-by-side with the existing version - called dual boot. Later, you can remove the old one if desired after all your data has been moved over. 

If you think about it, if you kept your system up to date, it is more secure now than any time since you installed it because security bugs have been fixed all along.

---

### Post by monkeybrain2012 on 2013-05-23
> **Dennis N said:**
> 

If you think about it, if you kept your system up to date, it is more secure now than any time since you installed it because security bugs have been fixed all along.

Point is that her system cannot be kept up to date because 11.10 has reached end of life.

---

### Post by gaitedlady on 2013-05-23
> **monkeybrain2012 said:**
> Point is that her system cannot be kept up to date because 11.10 has reached end of life.

This.

I am going to go ahead with the upgrade at 2 a.m., but I do have 11.10 still on a memory stick. And if I have to, I can reload that version. It just doesn't have the support anylonger.

Curious.... Does anyone know how long the download should take? I have more thunderstorms headed in my direction, and with satellite that usually means I will have troubles downloading. Damn....

Sandy

---

### Post by monkeybrain2012 on 2013-05-23
A clean install would just take 20-30 minutes (following the guide from my link) An upgrade may take hours and  may be problematic if you have modified your system, e.g installing third party software, proprietary drivers etc. So if you go ahead with upgrade make sure your system is in a pristine state.

---

### Post by mastablasta on 2013-05-23
> **gaitedlady said:**
> Curious.... Does anyone know how long the download should take? I have more thunderstorms headed in my direction, and with satellite that usually means I will have troubles downloading. Damn....

Sandy


depends on the speed of your internet connection. i have a stable connection but i did it in virtualbox on old mashcine. so the system wasn't fast to begin with. but anyway it took about 2 hours. clean system. i am not doing it anymore on that maschine i think. it just takes too long :-) 
 
but i might do it on the other maschine since it is simpler if it retains the settings and such. 

if you know how to install it it is really faster to back it all up and reinstall.

you can use Linux mint backup tool to backup data from home and your settings (e.g. bookmarks, passwords etc.)
about: [http://community.linuxmint.com/software/view/mintbackup](http://community.linuxmint.com/software/view/mintbackup)
how to on ubuntu: [http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)


the good thing about 12.04 is that it won't be end of life until 2017 ;-)

btw do you write science fiction or fiction?

---

### Post by newb85 on 2013-05-23
As it has been stated, upgrading with the updater is usually more successful if you have all available updates for your current release.  If you had the system up-to-date shortly before it hit EOL, then you have all (or almost all) available updates.

If you don't have all the updates and the default repositories aren't up anymore, you can still get all the updates like this:

```
sudo gedit /etc/apt/sources.list
```

For each line in the file that begins with "deb http:", replace the web address with "http://old-releases.ubuntu.com/ubuntu" (without the quotes).  Make sure to leave the few words after the web address in tact.  Save and close the file.  Then update your system as you would have before it hit EOL.

---

### Post by gaitedlady on 2013-05-24
I *did* have my laptop up to date before it hit end of life.  :-)  And... I did run the update last night and it was successful. I think it works just beautifully. I'll have to get used to a different 'look' but as long as the work, the links, and the contacts are here, I'm a very happy camper! THANK YOU ALL SO MUCH FOR YOUR HELP! It's good to know I have *someone* (actually lots of someones) I can ask these questions to now that my daughter is now less available to me.

Someone asked if I wrote Sci-Fi, and no... I've been writing Historical Romance (Regency and Victorian-set) for over 20 years. Sorry guys. ;-)

Thanks again!

Sandy

---

### Post by landersohn on 2013-05-24
I second one of the earlier posters: don't upgrade! Yes, the system can not be "kept up to date", but if it does what you want and need, who cares? I am aware of the security fixes but realistically, if you go online on a dynamic IP address, don't advertise a domain name, I think you are unlikely to be hacked. Security by obscurity. 

My personal policy has always been to upgrade only if I have to, for example new hardware or I need to do something in software that I can't do with what I have.
An upgrade "should" be OK and not loose any data, but .......

If the nag screen is bugging you, you can go into Upgrade Manager and turn the notifications and checking for upgrades off.

---

