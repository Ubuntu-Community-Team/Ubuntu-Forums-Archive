---
title: "[SOLVED] Script to download attachments from Gmail?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-09-27
I need a script to download an attachment form Gmail and save it on a specific folder. Does someone knows how to do it?

There is a service in my country that provides a xmltv.xml file with TV schedules, so I can use it on the EPG software. The problem is that they don't provide a download link because of copyright issues, so you have to register an e-mail account so they can send the file to you. 

I have already managed to automate the deliver of the xml file to my Gmail account using curl, but I can't retrieve it automatically from Gmail. This is the last step I need to perform in order to make my tv schedules update automatically.

**[COLOR="Red"]Edit: solution on post #6[/COLOR]**

---

### Post by Paqman on 2008-10-01
You could try using one of the terminal-based email clients (eg: Mutt) to fetch your email, then once it's stored locally searching for the file and moving it to the destination directory should be pretty straightforward. The whole script could be automated.

Could be fiddly to set up the email side of it though.

---

### Post by lovinglinux on 2008-10-01
Thanks. I will try this way.

---

### Post by Gannon8 on 2008-10-01
There is an extension for firefox called "iMacros" that may (or may not) help you.

It is built for firefox, so it should do the trick. But I have not tried it so please don't sue me if it does not work :D

---

### Post by lovinglinux on 2008-10-01
> **Gannon8 said:**
> There is an extension for firefox called "iMacros" that may (or may not) help you.

It is built for firefox, so it should do the trick. But I have not tried it so please don't sue me if it does not work :D

Thanks for the tip. I know that extension, but never really used it. Nevertheless, I'm really looking for a script, because all other steps I need to automate the process are performed this way.

---

### Post by lovinglinux on 2008-10-12
After a lot of research I finally figure out a simple way of doing this using IMAP and a shell script. I decided to post a step-by-step description if someone needs this.

1 - Install offlineimap and mpack

```
sudo apt-get install offlineimap mpack
```

2 - Create a folder [COLOR="Black"]**~/mail**[/COLOR] for storing the Gmail messages

3- Create a text file and save it as **~/.offlineimaprc**

This is the configuration file for offlineimap which will sync your Gmail with local maildir files, using IMAP. Add the following code to it:

```

[general]
accounts = GMail

ui = Noninteractive.Basic

[Account GMail]
localrepository = GMailLocalMaildirRepository
remoterepository = GMailServerRepository

[Repository GMailLocalMaildirRepository]
type = Maildir
localfolders = ~/mail/

[Repository GMailServerRepository]
type = IMAP
remotehost = imap.gmail.com
remoteuser = [COLOR="Red"]**yourgmailaccount**[/COLOR]@gmail.com
remotepass = [COLOR="Red"]**yourgmailpassword**[/COLOR]
ssl = yes
```

Then run the following command on a terminal:

```
offlineimap && munpack /home/[COLOR="Red"]**user**[/COLOR]/mail/[COLOR="Red"]**LABEL**[/COLOR]/new/* 
```

The **offlineima**p command will sync Gmail with local files and **munpack** will extract any new messages and attachments in the "**LABEL**" folder, where each folder (label) correspond to Gmail labels.

---

### Post by robsshadow on 2008-11-13
> **lovinglinux said:**
> After a lot of research I finally figure out a simple way of doing this using IMAP and a shell script. I decided to post a step-by-step description if someone needs this.

1 - Install offlineimap and mpack

```
sudo apt-get install offlineimap mpack
```

2 - Create a folder [COLOR="Black"]**~/mail**[/COLOR] for storing the Gmail messages

3- Create a text file and save it as **~/.offlineimaprc**

This is the configuration file for offlineimap which will sync your Gmail with local maildir files, using IMAP. Add the following code to it:

```

[general]
accounts = GMail

ui = Noninteractive.Basic

[Account GMail]
localrepository = GMailLocalMaildirRepository
remoterepository = GMailServerRepository

[Repository GMailLocalMaildirRepository]
type = Maildir
localfolders = ~/mail/

[Repository GMailServerRepository]
type = IMAP
remotehost = imap.gmail.com
remoteuser = [COLOR="Red"]**yourgmailaccount**[/COLOR]@gmail.com
remotepass = [COLOR="Red"]**yourgmailpassword**[/COLOR]
ssl = yes
```

Then run the following command on a terminal:

```
offlineimap && munpack /home/[COLOR="Red"]**user**[/COLOR]/mail/[COLOR="Red"]**LABEL**[/COLOR]/new/* 
```

The **offlineima**p command will sync Gmail with local files and **munpack** will extract any new messages and attachments in the "**LABEL**" folder, where each folder (label) correspond to Gmail labels.

Great guide I was wonder if there was a way to download just one folder from gmail

---

### Post by lovinglinux on 2008-11-13
> **robsshadow said:**
> Great guide I was wonder if there was a way to download just one folder from gmail

Thank you. I don't think is possible to download just a folder using offlineimap, because it would mess with sync.

---

