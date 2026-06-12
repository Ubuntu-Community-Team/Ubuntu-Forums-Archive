---
title: "Help downloading Clam TK updates"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Nodestar on 2008-06-30
I just downloaded Clam TK Virus Scanner from the Ubuntu Hardy Heron Add/Remove Programs. 
When I first started it up it said something was 140 days old.
I looked for a way to update. But I only found "Update Signatures" under "Help". 

When I tried to update it says I must be root to install updates.
I don't want to enable a root account. As in. Give root a password and log into root. 

Can someone give me a workaround or a terminal command to download updates for Clam TK.

Thanks

---

### Post by iaculallad on 2008-06-30
Drop to your terminal:

```
sudo apt-get install freshclam
sudo freshclam 
```

---

### Post by Nodestar on 2008-06-30
sudo apt-get install freshclam

Gives an error
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package freshclam

```

sudo freshclam

Gives 
```

ClamAV update process started at Mon Jun 30 00:52:38 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.92.1 Recommended version: 0.93.1
DON'T PANIC! Read http://www.clamav.net/support/faq
main.inc is up to date (version: 47, sigs: 312304, f-level: 31, builder: sven)
daily.cvd is up to date (version: 7586, sigs: 19725, f-level: 31, builder: guitar)

```

---

### Post by iaculallad on 2008-06-30
> **Nodestar said:**
> sudo apt-get install freshclam

Gives an error
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package freshclam

```

sudo freshclam

Gives 
```

ClamAV update process started at Mon Jun 30 00:52:38 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.92.1 Recommended version: 0.93.1
DON'T PANIC! Read http://www.clamav.net/support/faq
main.inc is up to date (version: 47, sigs: 312304, f-level: 31, builder: sven)
daily.cvd is up to date (version: 7586, sigs: 19725, f-level: 31, builder: guitar)

```

Using sudo in **sudo freshclam** had already given you the authorization to update your clamAV definition files w/o being the root user.

Disregard **sudo apt-get install freshclam**, application already installed in your system.

---

### Post by Nodestar on 2008-06-30
Well I uninstalled Clam. The freshclam still would'nt work. Gave the error that it could not be found. But "sudo apt-get install clamav" worked. It installed version 0.92.1 which it is saying is out of date. And I need version 0.93.1.
```

ClamAV update process started at Mon Jun 30 01:02:55 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.92.1 Recommended version: 0.93.1
DON'T PANIC! Read http://www.clamav.net/support/faq
main.inc is up to date (version: 47, sigs: 312304, f-level: 31, builder: sven)
daily.cvd is up to date (version: 7586, sigs: 19725, f-level: 31, builder: guitar)

```
I went to the main site. They have a precompiled version for Debian but I don't know if I'm ready to venture that yet.

Anything else I could try?

---

### Post by iaculallad on 2008-06-30
Try to update the CVD files manually using wget:

```
wget http://db.local.clamav.net/main.cvd
```

and

```
wget http://db.local.clamav.net/daily.cvd
```

Then:

```
sudo mv daily.cvd main.cvd /var/lib/clamav
```

To move the files to your clamav definition directory

---

### Post by Nodestar on 2008-06-30
Alright. I did that. when I type "sudo freshclam" I still get the "my installation is outdated". With recommendations to upgrade to 0.93.1.
Not sure if it worked or not.

EDIT

Alright. Up to date. Thanks for the help.

---

### Post by iaculallad on 2008-06-30
> **Nodestar said:**
> Alright. I did that. when I type "sudo freshclam" I still get the "my installation is outdated". With recommendations to upgrade to 0.93.1.
Not sure if it worked or not.

EDIT

Alright. Up to date. Thanks for the help.

Uuuhhh... what about doing a logout then log back in then re-check your clamAV definition version by sudo freshclam.

---

### Post by RomeReactor on 2008-06-30
> **Nodestar said:**
> I just downloaded Clam TK Virus Scanner from the Ubuntu Hardy Heron Add/Remove Programs. 
When I first started it up it said something was 140 days old.
I looked for a way to update. But I only found "Update Signatures" under "Help". 

When I tried to update it says I must be root to install updates.
I don't want to enable a root account. As in. Give root a password and log into root.
Hi. This means that you must start the application with administrator rights using gksudo:
```
gksudo clamtk
```
Then you'll be able to update the virus definition database in 'Help->Update Signatures'. **gksudo** is used for graphical applications, while **sudo** is used for command line programs; more on sudo [here]("https://help.ubuntu.com/community/RootSudo").
> Can someone give me a workaround or a terminal command to download updates for Clam TK.
As iaculallad said, **sudo freshclam** does that. It's provided by the **clamav-freshclam** package, which in turn is part of the packages Clam AV installs.

> daily.cvd is up to date (version: 7586, sigs: 19725, f-level: 31, builder: guitar)
Your virus definitions are up to date.

> when I type "sudo freshclam" I still get the "my installation is outdated". With recommendations to upgrade to 0.93.1.
That refers to the package itself and not the virus database. Did you uninstall Clam AV first? You installed Clam AV from the terminal, four posts above:
> Well I uninstalled Clam. The freshclam still would'nt work. Gave the error that it could not be found. But "sudo apt-get install clamav" worked.
The [frequently asked questions]("http://www.clamav.net/support/faq") section of the Clam AV site offers more information on that (read the third and fourth points).

Is there a particular reason you need the absolute newest version? Note that if your computer only has Ubuntu, you don't really need an antivirus.

EDIT: Too slow to post...

---

### Post by edcouch on 2008-12-21
Rome reactor is absolutely right!
I had the same problem, and when I entered gksudo clamtk  in a teminal , it asked for my password, then brough up the clamtk GUI and when you click on help you will see a green check mark beside update signatures and if you click on up date it will tell you that the signatures are up to date, and if not it will then update them.

Thank you very much Rome Reactor this helps a lot.  I'm getting there with Ubuntu, but this forum really helps.

---

### Post by laxminarayanag on 2010-11-11
good morning..
i have also same updating problum witn clamtk engine
how can i solve?

---

