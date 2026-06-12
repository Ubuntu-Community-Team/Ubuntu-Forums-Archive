---
title: "HOW TO: Export mail from Evolution to Thunderbird"
date: 2006-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by GuitarFingers on 2006-11-29
This is my first HOW TO on here so please be gentle with me :)
[SIZE="3"][B]
Exporting Mail from Evolution to Thunderbird.[/B][/SIZE]

[SIZE="2"]**PREPARATION**[/SIZE]

Create a new mail account in Thunderbird (this is so that if everything goes pear shaped nothing else will be affected). 

In Thunderbird choose *Edit -> Account Settings -> Add Account*

Select Email Account and click Next
Leave identity settings as they are and click next
Set the Incoming Server to "localhost" and REMOVE the tick from "Use Global Inbox" Click next
Leave the Incoming user name as it is. Click Next
Change the Account Name to something relevant such as "Evolution Mail"

Once the settings are created return to Edit -> Account Settings and select the "Server Settings" option under the "Evolution Mail" account.  Take note of the "Local Directory" Setting. It will be a string like "/home/yourloginname/.mozilla-thunderbird/a2ti6rsz.default/Mail/localhost". This is where all mail is stored for this account.

Now that the account is created and you know where to find it (you wrote down the path didn't you?) you can transfer the emails from Evolution.
[SIZE="2"][B]
TRANSFERRING MAIL[/B][/SIZE]

Open up two windows to your Home Directory. Navigate in one of the windows to the path that Thunderbird has assigned for your email storage above. *HINT: CTRL+h in your home folder will show all hidden files and folders so you will be able to see the ".mozilla-thunderbird" folder.*  Once you are in this folder you will see some files in there with names such as Inbox, Inbox.msf, Junk.msf and so on.

In the other window from your home folder navigate to ".evolution/mail/local" This is where any locally stored mail from Evolution is placed. There are a similar set of files to what you see in the Thunderbird folder, Inbox, Drafts and so on.

Copy the files named Inbox, Sent, Outbox and Drafts from the evolution folder to the mozilla-thunderbird folder (dragging and dropping while holding down your ctrl key will copy rather than move the files). When it asks if its ok to overwrite them just say yes. Its ok, nothing bad will happen. Its just a copy. You can trust me. Honest.

If you have your mail folders organised in evolution under your Inbox there will be a sub directory called "Inbox.sbd" under the .evolution/mail/local/ directory. In that directory you will find files named the same as your folders such as Humour, Humour.cmeta, Humour.ev-summary, Humour.ibex.index and so on. Of course, this depends on what you've called your folders.

For any of the folders you want to move to Thunderbird chose the file WITHOUT any extension and copy it to the localhost folder where you previously placed the Inbox and other files.

Thats all there is to it! Open Thunderbird and you should see all your mail and the relevant folders under the "Evolution Mail" account. You can keep the mail there or move it around in Thunderbird. The choices are yours.

Hope this HOW TO helps! :D

---

### Post by afon on 2006-12-14
Very useful and simple. Thanks

---

### Post by merlyn on 2006-12-28
Straightforward and easy to follow, worked like a charm. :)

Thankyou.

---

### Post by DSn0wMan on 2006-12-29
Very cool. Easy as pie. Thanks for the how to!

---

### Post by shakma on 2007-01-23
Excellent!  Thank you SO much.  Now I can honestly tell my boss, "I've switched your email program, but all of your old messages are there."

Peace.

---

### Post by mcwtlg on 2007-01-23
I wish I would have seen this last month...I figured it out, but it was not easy.  Evolution is not the mail client/PIM for me.

Thanx for posting this.

:guitar: 

No Fascination with death, It's fascinated with me....

---

### Post by dolny on 2007-01-23
Btw -  is there a way to export Sylpheed mail to Thunderbird?

---

### Post by wantime on 2007-02-15
Excellent how to ... thanks.

---

### Post by PartisanEntity on 2007-02-16
Anyone have a good tutorial for exporting mail the other way round? i.e. from Thunderbird to Evolution? Thanks :)

---

### Post by yemu on 2007-02-26
try this: [http://ubuntuforums.org/showthread.php?t=313305](http://ubuntuforums.org/showthread.php?t=313305)

---

### Post by shane2peru on 2007-04-27
Thanks for the tutorial, worked great!  May want to have them close Thunderbird after noting where to find the mail boxes.  Not that important though since mine worked even with it open.

Shane

---

### Post by Miger on 2007-11-06
Thank you very much! With your how-to everything was simple and quick.

---

### Post by Hilko on 2008-07-21
I've created a page on the wiki [https://help.ubuntu.com/community/MigrateEvolutionToThunderbird]("https://help.ubuntu.com/community/MigrateEvolutionToThunderbird").

It also explains how to migrate your addressbooks.

Thanks for the tutorial !

---

