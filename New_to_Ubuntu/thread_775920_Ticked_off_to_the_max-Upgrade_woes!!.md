---
title: "Ticked off to the max-Upgrade woes!!"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Romin-1 on 2008-04-30
When I was ofered the upgrade to Hardy Heron I thought it was time to move ahead and sat through the 2+ hours it took.

Much to my consternation all of my customizations were lost including the ability to have full function of my Logitech Mouse buttons.

Then I fired-up the new Firefox, ver 3.b5, and things were even worse. 15 out of 22 add-ons don't work, half of the tool bar buttons are missing and when I right click on the tool bar and then customize the box with the buttons doesn't open. Basically speaking, FF is unusable as it is now.

I only have 3 questions;

1-Why, everytime I upgrade, I have to spend hours customizing my setup?

2-Is there an easy way to to recover my settings or do I have to do it one at a time?

3-How can I install an earlier version of FF, 2.0.0.13 preferably, and at least be able surf the way I want?

To say I'm very  upset would be an understatement...

Thanks for any soothing advice,

Jon

---

### Post by vexorian on 2008-04-30
1. Because it is a whole OS upgrade :) Compare it to a windows to vista upgrade or as a OS/X upgrade (in which you basically need to buy a new computer) It is always painful, I do wish it wasn't since I'll upgrade today as well, but that's how it works. This is also the reason I try not to upgrade unless it is necessary, the live CD seems to work in my comp and I have the time to set it up, I kept feisty for a year now and the problem is that repos no longer give me updates :( so I'll have to upgrade. The good thing about hardy is that it is a LTS so I might be allowed to stay with it for a longer time.

2. I have no idea, first of all most of your settings must have stayed... sudo apt-get dist-upgrade or the one in the update-manager don't touch /home I have no idea what method you used to upgrade, did you use the CD to install or did you use the update-manager? The later is supposed to keep your settings.

It depends on your settings,  I have no idea whatsoever as to what a logitech mouse is, so no help there .

3. There is one in the repositories.

IMHO, get used to firefox 3, it is hard in the first place but later it really shows how much of an improvement it is . I don't know about what half of the toolbar buttons you are talking about, I didn't have this issue, I am sure you can add them back though? Plugins are a problem, but you can wait, now that heron is forcing firefox 3 on everybody the plugin makers should get more updates, even though most of the plugins I loved didn't have this issue.

Well after typing that last paragraph I read more in your post, and it sounds as if you got to a bad firefox bug, tips:
- go to synaptic and force a firefox 3 reinstall.
- backup /home/username/.mozilla then delete that folder (this will force firefox 3 to give you a brand new account)

Anyways, you can recover firefox 2 from the repos if that's what you want.

---

### Post by Romin-1 on 2008-04-30
Thanks for the reply, vexorian.

What I meant was Firefox _will not_ allow me to customize the toolbars. No Back/Forward, Bookmark/Bookmark Manager buttons among others. Stylish is gone, Custom Buttons are gone. Even my home page is gone. Cannot install/uninstall addons...ad nasium. At this point FF is a total waste.

Tried your suggestion and uninstalled ver 3 and installed ver2 with no joy whatsoever.

Not many problems with Hardy Heron though. Sad thing is I'm having to reply on my Vista machine.

The upgrade was done online which I feel now was a BIG mistake. Gonna wait a couple days till I cool off and burn an iso and try again,,,maybe.

Right now I got a 20 pound paperweight.

Thanks again,

Jon

---

### Post by aheckler on 2008-04-30
Did you try deleting your profile and letting FF3 make a new one?

---

### Post by cubeist on 2008-04-30
> **Romin-1 said:**
> Thanks for the reply, vexorian.

What I meant was Firefox _will not_ allow me to customize the toolbars. No Back/Forward, Bookmark/Bookmark Manager buttons among others. Stylish is gone, Custom Buttons are gone. Even my home page is gone. Cannot install/uninstall addons...ad nasium. At this point FF is a total waste.

Tried your suggestion and uninstalled ver 3 and installed ver2 with no joy whatsoever.

Not many problems with Hardy Heron though. Sad thing is I'm having to reply on my Vista machine.

The upgrade was done online which I feel now was a BIG mistake. Gonna wait a couple days till I cool off and burn an iso and try again,,,maybe.

Right now I got a 20 pound paperweight.

Thanks again,

Jon

In FF does view/toolbars/customize work?

As far as your settings, if you look in you home .mozilla/firefox folder, how many settings folders are there?  For me, I had to move the new default settings out and replace it with a recent backup I had to get my bookmarks back.  This may work assuming you have a backup?!

As for 2.0.x addons not working in ffb3, well this cannot really be blamed on ubuntu.  I would imagine it may take some time for individual add-on developers to test their addons for ff3 compatibility.

As for your logitech settings, did you backup before upgrading? if so you can probably copy/paste your old settings back into your new xorg.conf file.  If you didn't backup (its ok... not many people do!) there are quite a few good tutorials for mouse settings in xorg.

Edit - 
Just to clarify... I did not replace the entire default folder in home/.mozilla/firefox, just the parts that were not working... for me this was the bookmarks file...

---

### Post by Romin-1 on 2008-04-30
Here's where we are, so far;

xorg was a snap. The Heron is a happy bird now.

Bunny-too says all my folders are root and since I'm not the OWNER I can't do a darn thing with the files...Was going to delete the Localstore.rdf file which usually works in FF on my other machines. Uh yeah, this is a dedicated machine. Ubuntu only.

I do know we have to wait for the developers to catch up with the addons but I cannot get rid of the bad ones or even disable them. They may be the cause of some of the problems.

How can I get this thing to recognize me as the owner so I can do some work on the files?

Many thanks, guys

Jon

---

### Post by cubeist on 2008-04-30
> **Romin-1 said:**
> Here's where we are, so far;

xorg was a snap. The Heron is a happy bird now.

Bunny-too says all my folders are root and since I'm not the OWNER I can't do a darn thing with the files...Was going to delete the Localstore.rdf file which usually works in FF on my other machines. Uh yeah, this is a dedicated machine. Ubuntu only.

I do know we have to wait for the developers to catch up with the addons but I cannot get rid of the bad ones or even disable them. They may be the cause of some of the problems.

How can I get this thing to recognize me as the owner so I can do some work on the files?

Many thanks, guys

Jon

Do you mean that your files and folders in your home directory are all root:root?
Or is it a permission issue?  Can you post a sample of ls -al from your home directory?

edit -
I have no idea what you mean by "bunny-too" What is that?

---

### Post by Romin-1 on 2008-04-30
Bunny-too was just a play on the word 'Ubuntu'.

When I open a file in home,firefox is when I see the statement that I can't change anything 'cause I'm not the owner. All files are listed undr permissions as 'Root'. Delete is greyed out as well as a couple other things. Cannot get a screen shot 'cause I don't have anything setup to do so thus far.

Thanks again,

Jon

As for Customizing the toolbar, nothing works. In View or right click.

---

### Post by cubeist on 2008-04-30
> **Romin-1 said:**
> Bunny-too was just a play on the word 'Ubuntu'.

When I open a file in home,firefox is when I see the statement that I can't change anything 'cause I'm not the owner. All files are listed undr permissions as 'Root'. Delete is greyed out as well as a couple other things. Cannot get a screen shot 'cause I don't have anything setup to do so thus far.

Thanks again,

Jon

As for Customizing the toolbar, nothing works. In View or right click.

buny-too duh! should have got that!

you don't have to post a screen shot... just copy and paste a few lines so we can see if there is a permissions problem (fixable with chmod) or a ownership problem (fixable with chown)

for example if I type ls -al in terminal at my home folder the first line I get is
drwxr-xr-x   5 john john   4096 2008-04-19 14:53 Adds

---

### Post by Romin-1 on 2008-04-30
I wasn't going through terminal to get to the folders. Was going via Home-File Sets-Inc-Firefox.

Duh! What's next?

Many kudos for your patience,

Jon

---

### Post by cubeist on 2008-04-30
> **Romin-1 said:**
> I wasn't going through terminal to get to the folders. Was going via Home-File Sets-Inc-Firefox.

Duh! What's next?

Many kudos for your patience,

Jon

ok...
open a terminal
type
```
cd .mozilla/firefox
```
then
```
ls -al
```
and copy and paste the results here.  If the permissions are incorrect I will give you steps to fix.

---

### Post by Romin-1 on 2008-04-30
Is this what we're looking for?

jon@MMI:~$ cd .mozilla/firefox
[email]jon@MMI:~/.mozi[/email]lla/firefox$ ls -al
total 20
drwx------ 3 jon jon 4096 2007-12-31 17:15 .
drwx------ 4 jon jon 4096 2008-04-30 05:28 ..
-rw------- 1 jon jon 2066 2008-04-30 14:12 pluginreg.dat
-rw-r--r-- 1 jon jon   94 2007-12-31 17:14 profiles.ini
drwx------ 9 jon jon 4096 2008-04-30 19:44 skju9axg.default
[email]jon@MMI:~/.mozi[/email]lla/firefox$

---

### Post by MaindotC on 2008-04-30
Foxmarks doesn't work - how could they not see that as being important - and even though I have my preferences correctly set, sometimes when I close Firefox and restart it, my previously opened tabs don't appear.  Very frustrating.

---

### Post by cubeist on 2008-04-30
> **Romin-1 said:**
> Is this what we're looking for?

jon@MMI:~$ cd .mozilla/firefox
[email]jon@MMI:~/.mozi[/email]lla/firefox$ ls -al
total 20
drwx------ 3 jon jon 4096 2007-12-31 17:15 .
drwx------ 4 jon jon 4096 2008-04-30 05:28 ..
-rw------- 1 jon jon 2066 2008-04-30 14:12 pluginreg.dat
-rw-r--r-- 1 jon jon   94 2007-12-31 17:14 profiles.ini
drwx------ 9 jon jon 4096 2008-04-30 19:44 skju9axg.default
[email]jon@MMI:~/.mozi[/email]lla/firefox$

Aha! yes, 

while you are in that directory (.mozilla/firefox) type
```
chmod 755 skju9axg.default
```

if you type that and then ls -al you will see the first digits will change from drwx------ to drwxrw-rw-
In unix permissions are set in three stages read (r) write (w) and execute(x)... making the change will allow you to read and write which should let you customize firefox...

also while you are in that folder I would highly recommend to make a backup copy of that folder (skju9axg.default) because if you are like me you probably have hundreds or thousands of bookmarks in that folder!

---

### Post by Romin-1 on 2008-04-30
Sorry to say, that did not change a thing.

How the dickens do I tell this thing that I am the owner and have root permission? I remember back in Drake, or perhaps before that, I put something in terminal that gave me full permission to everything.

Think I'll call it a night and start again early in the morn. It's 11 pm here and I'm about burned out for one day.

BTW-I use the Bookmark Backup Extension which saves a copy everyday in a folder in HOME. Therefore if something happens to FF you can retrieve them from there. You can specify where to save them.

Thanks for everything,

Jon

---

### Post by cubeist on 2008-05-01
> **Romin-1 said:**
> Sorry to say, that did not change a thing.

How the dickens do I tell this thing that I am the owner and have root permission? I remember back in Drake, or perhaps before that, I put something in terminal that gave me full permission to everything.

Think I'll call it a night and start again early in the morn. It's 11 pm here and I'm about burned out for one day.

BTW-I use the Bookmark Backup Extension which saves a copy everyday in a folder in HOME. Therefore if something happens to FF you can retrieve them from there. You can specify where to save them.

Thanks for everything,

Jon
Do you mean that command did not change the permissions? Or it did change the permissions but you still cannot make changes in firefox?

you could try this in your .mozilla/firefox folder
```
sudo chmod 777 skju9axg.default
```
Note this will give you full access to your profile and should allow you to make changes...

misc note: to ensure you are typing things correctly in a terminal command you can use tab completion.  For example, for the above command instead of typing out the full skju... folder just type the first few letters and hit tab and it will fill out the rest for you.

---

### Post by Bubba64 on 2008-05-01
Nightly tester tools in add ons will get your add ons from FF2 working. Toolbar buttons in add ons will give you access to a bunch of controls. Hope this is some help

---

### Post by Romin-1 on 2008-05-01
I really hate to tell you guys but all this effort was for naught. The problem did not involve The Bird or FF. After I burned the ISO and reinstalled the whole bit the danged thang was in worse shape than before.

Started up in diagnostic mode and after check Bios and other things realized the Mobo was on its way south.

Hopefuly by the time I re-build the PC the final version of Hardy and FF will be out.

Thanks for all your efforts, even though in vain, they are appreciated.

Jon

---

### Post by cubeist on 2008-05-01
> **Romin-1 said:**
> I really hate to tell you guys but all this effort was for naught. The problem did not involve The Bird or FF. After I burned the ISO and reinstalled the whole bit the danged thang was in worse shape than before.

Started up in diagnostic mode and after check Bios and other things realized the Mobo was on its way south.

Hopefuly by the time I re-build the PC the final version of Hardy and FF will be out.

Thanks for all your efforts, even though in vain, they are appreciated.

Jon

well, at least now you know how to change those pesky permissions!

also, if you are looking for a new mobo. I just setup a new system with the new gigabyte GA-MA78GM-S2H great price for a decent board and everything works in linux (haven't tested the hdmi but I am sure it will work too)... the onboard radeon hd3200 gives me about 3100fps in glxgears...

---

### Post by Romin-1 on 2008-05-01
Thanks for the heads-up on the mobo. I'll give it a look-see,,,

Jon

---

### Post by nowshining on 2008-05-02
for FF3 the problems are not FF3 it's the add-ons, mainly you gotta wait until the FF add-on authors update their add-ons for the new FF3 which is still in BETA by the way and I read that once FF3 beta becomes FF3 final, it will be incl. for updating in the Ubuntu HH repos. If you plan on updating the max version urself, well you may have comp. problems. However I think a program/add-on called nightly tester will help quickly make all programs tmp compatible with the FF versions.

---

