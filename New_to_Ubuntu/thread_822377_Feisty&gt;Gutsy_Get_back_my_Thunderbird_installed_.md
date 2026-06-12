---
title: "Feisty&gt;Gutsy Get back my Thunderbird installed with Automatix"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Theresa on 2008-06-08
Hello,
When I first installed Feisty a year ago, I installed Thunderbird through Automatix,one night when a Thunderbird (then installed as part of Ubuntu package) upgrade was very messy.
Now I have updated (a bit painfully) to Gutsy. 
Thunderbird is back through Ubuntu, with only two accounts, an address-book not up to date,etc (that is,files are where Automatix had put them,that is in     .mozilla-thunderbird and not .thunderbird).
How do I get my other mail accounts and attached mails and adress books back ?
Same pb with Firefox: my bookmarks are into the Automatix set up.
I used Automatix then since,as an absolute beginner, it was very easy to use.
A year later,I'm not such a beginner...though my Feisty worked so perfectly I   did not get a chance to learn a thing !!
Thank you much for your help.

---

### Post by ajgreeny on 2008-06-08
I've never used automatix in my three years of ubuntu use, but suggest you uninstall it, having first uninstalled its versions of both FF and ThB.  Then install FF and ThB using synaptic or apt-get as usual.

Make sure you have backups of all your mail folders etc etc and bookmarks and other things you want from FF, and then for safety delete the profiles of both and let new ones be made when you restart the programs.  You can then reinstate the mail and bookmarks, etc and you should have nice clean versions of both available.

---

### Post by Theresa on 2008-06-08
Thank you for your reply.
I am just worried that the fresh install of Thunderbird won't find the right folders since the path to mails and address books set up by Automatix are not the ones set up by an install thru the Ubuntu packages.
What do you think ?

---

### Post by Theresa on 2008-06-08
Sorry,forgot one other question :
how do I remove the Automatix/thunderbird and the Automatix/Firefox ? What is   the path ? (ie, sudo apt-get remove ???)
Thank you again.

---

### Post by alienexplorers on 2008-06-08
sudo apt-get remove thunderbird
sudo apt-get remove firefox

---

### Post by Theresa on 2008-06-08
But this is to remove the "Ubuntu Thunderbird" right ? What about the one installed with Automatix ? (sorry to insist,but I'd rather not mess up everything with half understood "remove" commands !)

---

### Post by Moop on 2008-06-08
You can copy the contents of your old thunderbird profile into your new thunderbird profile and all your settings and mail will be restored. Don't copy the profile folder itself but everything in it and paste it into your new profile folder in .thunderbird. 

Then you can just delete your old .mozilla-thunderbird folder.

---

### Post by Theresa on 2008-06-08
Hi !
Thank you, I got everything back.
I am just not sure yet how to uninstall the softs I had installed with Automatix, and only those. For example, I also have two Skypes now. And can't remember where my amule comes from, same thing for desklets. In short, how do I figure which softs were installed through Automatix ?
Thank you in advance.

---

### Post by ajgreeny on 2008-06-08
As I said, I've never used automatix fior the reason that you are now finding, I think, but I seem to remember that things you installed with automatix, you could also uninstall with it.  So if you still have automatix on the computer, open it and see if you can uninstall from there.  Don't worry too much about your profiles as you can deal with that later, as moop said.

I hope that works, and I'm right about automatix and uninstallation.  Good luck.

---

