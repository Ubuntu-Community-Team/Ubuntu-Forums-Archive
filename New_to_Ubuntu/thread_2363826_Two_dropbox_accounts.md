---
title: "Two dropbox accounts?"
date: 2017-06-14
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2017-06-14
Somehow I seem to have set up two different Dropbox accounts. In my office I use a browser in my Win10 computer to go to dropbox.com and sign in. At home, I have a Dropbox folder on my Ubuntu desktop so no sign in required.

The contents are different, therefore I am assuming that there must be two accounts.

Problem is that I cannot figure out what my signin is for the linux dropbox. It is just a folder and there are no settings, as there is in the browser based one, that I can access to determine how I sign in to this version. I feel really stupid about this, but it must have been set up some time ago as I have no idea when.

Is there a place within the Ubuntu files that I can see this info? 

If not, I can try to consolidate the two by downloading the contents of my linux desktop version, then upload these files into my browser based version.

Or am I being a bit dense about this and what do I need to do to get all the files into the one I can sign in to in a browser?

---

### Post by vasa1 on 2017-06-14
What does```
ps -o pid,command -u $USER | grep -i dropbox
```show? Maybe you have a fully functional Dropbox but its icon isn't showing up for whatever reason?

What does ```
apt-cache policy dropbox
``` show?

And are you using Ubuntu or Lubuntu?

---

### Post by Odyssey1942 on 2017-06-15
Thanks

> 25964 grep --color=auto -i dropbox

and
> dropbox:
  Installed: (none)
  Candidate: (none)
  Version table:
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
 Using Ubuntu Mate 16.04.02 64 bit

BTW, I can access the DropBox folder on my desktop, upload and download files etc, so it is working well. I just don't know how to go to a different computer and sign into the account that shows up on my my desktop.

On the Windows computer, I sign in using a browser (there is  no folder on my desktop) so I know the login and password., but
on the linux computer, I don't remember the login and password.

Dropbox uses an email addy as the login, so I guess I could open a browser on this linux computer and start trying to sign in using my various email addresses (not the one that is in use on the Win 10 machine) and try to reset my pw?

BTW, does U Mate automatically set up a DropBox for you? I just don't remember at all having set it up.

---

### Post by AWB70UK on 2017-06-15
Dropbox won't install on ubuntu unless you ask it to by either going into the software centre or downloading the deb file from the dropbox website. You can access both your Dropbox accounts via the browser if you have two accounts by signing out and back in. Dropbox has file syncing software for both linux and windows but you would have to download them and install to each pc but that would be pointless I reckon if you want dropbox to sync over all computers which I assume is the selling point of dropbox.
If you do have two accounts I would downlaod DB to all your computers and set up which DB account you use the most to sync right across them all. If you do have another account and can't remember the password go to DB web site and try an email you think it is and ask to reset your password which will be emailed to you. 
Obviously don't use these details to sign in with DB software just using the web version in the browser. If you want to join these two accounts together I would use the web to download all the files from it to your computer and then throw them all into your DB folder on the computer if you have enough storage space.

Sorry, seen you were using mate so maybe DB is pre-installed. When running do you have the DB icon on your screen? If so click on it>preferances>accounts and see which account you're logged in to.

---

### Post by Odyssey1942 on 2017-06-15
No icon, just a folder.

So if I use a browser in Mate and sign into the account I know the login for, I can then install a new folder on my desktop from the browser? Will it also be named "Dropbox"?

Then I assume that I can drag anything from the mystery folder to the known folder (assuming space available)

Many thanks.

Edit: Googling shows "caja Dropbox". Unsure what that means?

And on dropbox.com it offers "Dowload the app". Man, am I confused!

In checking for pw reset info, I see that I have "linked" other computers to my Win 10 DropBox, but also don't remember how to do it (but can find out). Is this another alternative (given that I already have a DB account on this computer)?

---

### Post by Quarkrad on 2017-06-18
I too use Dropbox and Ubuntu Mate 16.04 - caja is the file manager used in Ubuntu Mate, Dropbox is not pre-installed when using Mate (16.04).  If you look in Applications/Internet you should see an entry for something called Dropbox - on my system there is an entry called Applications/Internet/Caja Dropbox (this is because I installed caja dropbox - which is th e same as installing just Dropbox). If your version of Mate is using, say Nautilus as the file manager, you may have something called Applications/Internet/Dropbox.  If you have something called Dropbox left click on it and launch it - you should now have an icon appear on the right hand side of your top panel.  Right click on this icon and choose Preferences.  In the window that pops up click on the Account tab and there is an entry under **Account Linking** at the bottom.  Here you will see the owner of the Dropbox account and the email it is fixed to.

---

### Post by Odyssey1942 on 2017-07-02
In response to Quarkrod's very optimism-inducing post:

I cannot find any reference to Dropbox anywhere in Applications (with or without Caja, etc)

I do not have a Dropbox icon in the top panel, but I do have an icon on my desktop

However while left clicking on the icon does show me the contents of my Dropbox account, I cannot find any reference to Account Linking (either in the window that opens, right clicking the icon, or anywhere else I have looked (including Applications, Places, System)

I was very optimistic, but my install seems to be something of a mystery.

Quarkrod, or anyone else, have any suggestions?

---

### Post by #&amp;thj^% on 2017-07-02
What dose this show from the terminal:
```
apt policy caja-dropbox
```
Paste back here.

---

### Post by Odyssey1942 on 2017-07-02
> caja-dropbox:
  Installed: (none)
  Candidate: 1.12.0-3
  Version table:
     1.12.0-3 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/multiverse amd64 Packages
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension


Hope this is informative

---

### Post by #&amp;thj^% on 2017-07-03
> **Odyssey1942 said:**
> Hope this is informative

It was thanks....Here is some information to help fix  the preferences (Editing) problems. [https://websetnet.com/fix-dropbox-indicator-icon-menu-working-xubuntu-lubuntu-ubuntu-mate/](https://websetnet.com/fix-dropbox-indicator-icon-menu-working-xubuntu-lubuntu-ubuntu-mate/)
You will need to install the "caja-dropbox" package to have this option.
You will need to sort out which account credentials you are using first though.

---

### Post by Odyssey1942 on 2017-07-03
Thanks for yours and I may get to the preference issue later, but "You will need to sort out which account credentials you are using first though." is what I am trying to do in this thread.

Have you or anyone have additional thoughts on that?

---

### Post by #&amp;thj^% on 2017-07-03
> **Odyssey1942 said:**
> Thanks for yours and I may get to the preference issue later, but "You will need to sort out which account credentials you are using first though." is what I am trying to do in this thread.

Have you or anyone have additional thoughts on that?

It will make more sense to you when this **on your end** is first fixed...
> BTW, I can access the DropBox folder on my desktop, upload and download files etc, so it is working well. I just don't know how to go to a different computer and sign into the account that shows up on my my desktop.

On the Windows computer, I sign in using a browser (there is no folder on my desktop) so I know the login and password., but
on the linux computer,**_ I don't remember the login and password._**
That's something we here can not help with. (I'm sure that makes sense now right?)
You may have to get a hold of the Dropbox Folks...with "Forgot Login and Password" ;)
EDIT: This is good place to start: [https://www.dropbox.com/help/sign-in/password-reset](https://www.dropbox.com/help/sign-in/password-reset)

---

### Post by migueandz on 2017-07-27
You can clic on Dropbox icon located on top of the screen, and select open Dropbox web site. In the web site you can check your registered email and change your password.

---

