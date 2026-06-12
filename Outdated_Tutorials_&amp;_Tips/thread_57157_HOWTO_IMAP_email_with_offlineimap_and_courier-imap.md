---
title: "HOWTO: IMAP email with offlineimap and courier-imap"
date: 2005-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by tony_st on 2005-08-15
IMAP is a convenient way to do email which allows you to use more than one client to access the mail account on an external server.  For example, you could use Eudora at work, Thunderbird at home, and access you email by webmail while on vacation.  Email is maintained on the server, unlike a typical POP3 situation where you download your email from the server and maintain it locally.

By default, with IMAP your email is usually left on the server and your client downloads each message every time you look at it.  But, many people like to download their email to their client programs as well, for performance or connection reasons.  Most IMAP client email programs have ways to do this.  In that case, the clients needs to synchronize with the server.  When any of these clients start up again, they check with the server to see the state of your email account on the server and download/upload the differences according to what they have saved locally.  For example, a message you sent from work will also show up in the Sent folder when you synchronize from home.  A message you delete at home will show up in the Trash folder later at work.

For laptop users, it is often important to have a complete copy of your email account locally, as you may be disconnected from the Internet while traveling, but still want to work on your email.

Unfortunately, most IMAP client programs are not efficient or consistent with synchronizing downloaded messages with a server.  Here is a way around that.

You first create a "server style" copy (known as Maildir format) of your external server email on your local machine.  This is synchronized using the offlineimap program.  Depending on your email client, this may be enough.  Some email clients (like Mutt), can read the /Maildir directly.

Other email client programs can't read this kind of directory, so you have to trick them in to thinking they are getting their information from an external server.  You do this by serving this local copy of your server style email to yourself, with the courier-imap program. Your client email program sends IMAP requests to a courier-imap process on your own machine, which serves up the data from your local copy of the Maildir files.  Every now and then you re-synchronize with offlineimap so your changes locally make it back to the external server.  This how-to assumes you will install courier-imap as well.


How-to

*Note: *try this first with a dummy email account!  If you make a mistake, you could accidentally delete all your email on the server.  For example, a typo in a configuration file could cause something to crash and all your email could be lost.

*Note: *some of the files for setting options are Python files.  This means that leading spaces at the beginning of a line could affect how they work.  So, be sure when you uncomment a line, that you remove not only the leading hash symbol but also the leading spaces.

Make sure your email provider supports IMAP.  It's common.

You need to install these Ubuntu (Debian) packages:

[INDENT]offlineimap
courier-imap[/INDENT]

You do not need to install the courier-webadmin package, and can ignore any options to configure for webadmin.

After install, courier-imap will already be running on your machine (localhost) and you can accept all the defaults it comes with.  There is one I changed in /etc/courier/imapd:
```
IMAP_EMPTYTRASH="Trash:1000"
```
This will keep courier-imap from periodically emptying the trash can on your external email server.  I prefer to have manual control over that.  (If you do change this, be sure to restart the the daemon with "sudo /etc/init.d/courier-imap restart".)

For the rest of the set-up you need to be logged in as yourself, if you are not already.  Your local Ubuntu account will also be your local email account, for the sake of the courier-imap server.

Maildir directories have a special layout and setup, so you can't just use any unix directory.  Create one in your home with:
```
  cd
  maildirmake.courier Maildir
```

For the offlineimap program you will also need a local control file called .offlineimaprc .  You can create that based on a default delivered with the offlineimap package like this:
```
  gzip --stdout --decompress /usr/share/doc/offlineimap/examples/offlineimap.conf.gz > .offlineimaprc
```

Many of the defaults in the file will work out of the box for you.  There are few you need to change.

Uncomment this line in .offlineimaprc in order to turn on folder name translations that are compatible with the folder naming convention used by courier-imap.  Be sure NO SPACES indent the line.
```
nametrans = lambda foldername: re.sub('^INBOX\.*', '.', foldername)
```

You need to enter the host of you external email server.  Find and update this line:
```
remotehost = mailmachine.youremailhost.net
```

And enter your remote user name on that host.  Find and update this line:
```
remoteuser = your_email_name_here
```

You may optionally want to uncomment this line in .offlineimaprc so that offlineimap keeps running and synchronizing every 5 minutes, in case you want to use email in almost real time.  Be sure NO SPACES indent the line
```
autorefresh = 5
```

Next you will need to setup your email client program (Evolution, Thunderbird, whatever).  You will need to set the account options, keeping in mind the following.  Remember, in this case, now "server" no longer means the external server but your local machine, which will be doing the serving instead:
servername: localhost
server username: your_Ubuntu_username
server password: your_Ubuntu_password
smtp: use the same info you have always used here

When you run your client email program, it will ask you for a password.  You enter your Ubuntu account password here, because you are accessing your machine, not the external one.  Your email account should be "empty" because you haven't synchronized yet, and the Maildir in your home directory has no messages yet.  You synchronize with the shell command:
```
offlineimap
```
Depending on where you run this from, a little GUI window might pop up in your Xwindows.  Enter your password for the external email server when prompted.  The first time you run offlineimap it may take several minutes if you have a lot of email on the server to download initially.  Then use the get-new-mail button in your client email program, and it should now fill up with your email, by way of your courier-imap local mail server accessing your local /Maildir.

(Note: I use Thunderbird, and in that case, you must go to the account in the left pane, right click, and choose the Subscribe option in order to see all of the folders.  The offline section in Account Settings did not work for me.)

---

### Post by AgenT on 2005-08-19
Good guide, but this does not seem to work very well with multiple maildir folders. How does one setup the local imap server with multiple maildir folders?

---

### Post by tony_st on 2005-08-20
I'm not sure that's possible.  The local courier-IMAP server associates an email account with an Ubuntu user account, and always looks in the /Maildir folder (or whatever folder name you set in the courier-imap preferences) in that user's home directory.  How would you indicate which Maildir folder you wanted, if all you are logging in to courier-imap with is your local username/password?  I don't see how.  Alternatively, you could create some new local Ubuntu users, and put one of the Maildir accounts in each of those.  Or, let offlineimap bring in your various accounts, forget about courier-imap, and use an email client that can read Maildir directories directly, such as mutt.

---

### Post by AgenT on 2005-08-20
That is exactly what I need however. I do not need to sync right now (to use offlineimap) but just the local imap. Reason for this is a lot of email clients, for whatever annoying and shameful reason, do not support the maildir format. Thunderbird being an example. So by using local imap one could use more or less any email client since most are able to use imap.

Any ideas on how to go about this?


Some notes:

For whatever reason courier-imap refused to accept a different directory from the default Maildir. Even if the configuration was changed and courier restarted, it kept insisting to look in Maildir. 

Another strange incident was that Thunderbird refused to communicate to the imap but other email clients worked. This may be because by default courier uses the newer imap standard and maybe Thunderbird was not setup properly to use it.

---

### Post by tony_st on 2005-08-21
I'm afraid your issue then, is not covered by what I was trying to accomplish for myself when I set these things up, and I can not be of much help.

As far as I can guess, for courier-imap to serve up different /Maildir directories, you would need to setup a different unix account for each one.

Though I saw the setting in the configuration file, I did not try to change the /Maildir default, so I can't help you much there.  Maybe try rebooting?  The courier family of products seems to start a number of processes and maybe some of them are not being reset?

I am successfully using Thunderbird and courier-imap with all the latest packages off of Ubuntu, so perhaps there is something in your setup.  Can you use other IMAP email accounts on other machines, i.e. without courier-imap?  Be certain you initially set up the Thunderbird "account" to be of type IMAP.  You can't switch it later, I don't think.

---

### Post by AgenT on 2005-08-21
Yes, I figured that something like this would not be feasable using courier-imap. And having multiple accounts setup just for email is not acceptable because the folders require being owned by a single user.

Don't worry about not being able to help, you have done enough with the howto already for those that need it. There are a few other imap programs but they lack in documentation (bincimap is a good example of this).

The funny tidbit is that not much has changed since 1995 in email clients except for fancy graphics. "All mail clients suck. This one [mutt] just sucks less." Seriously, to not have maildir support is just shameful.

---

