---
title: "evolution-ews packaged for oneiric"
date: 2012-01-21
forum: Packaging and Compiling Programs
---

### Post by NHclimber on 2012-01-21
For those looking for full-scale mail/calendar/contacts/tasks client for Exchange 2007/2010, I packaged a PPA for the native EWS backend project [called evolution-ews] for evolution on oneiric.

Available here: [https://launchpad.net/~phurley/+archive/ppa]("https://launchpad.net/%7Ephurley/+archive/ppa")

The project is not-quite-primetime yet, but getting there.

---

### Post by MacTribe on 2012-01-26
@ NHclimber

What are the limitations of evolution-ews currently? Does everything work i.e contact and calendar sync or are there a few non working things?

---

### Post by NHclimber on 2012-01-26
Firstly, it's still unstable. I was reparenting a folder with drag-n-drop and it wiped it from the server. Gone forever.

What works
   email w/ multiple exchange accounts, calendar* (including notifications), contacts*, tasks
   *although I have an 'extra' empty calender for one of my exchange accounts
    and an 'extra' empty Contacts and 'Suggested Contacts' for all of my exchange accounts
    (probably due to some stale gconf/dconf settings because I had the alpha version of evolution-ews setup earlier)

What doesn't work
   deleting messages does not reliably move them to 'Deleted Items' folder
   'Junk E-mail' folder doesn't have a purge/empty like 'Deleted Items'
   sent emails are stored in local folders 'Sent' rather than 'Sent Items' on the server

---

### Post by MacTribe on 2012-01-26
Ok

Thats not too bad for a completely new project like this. :) 

I'm subscribing to this post, I'd be grateful if you let me know of any changes or improvements. Thanks again for the PPA upload.

---

### Post by boudjere on 2012-01-27
You saved my day!! A working Exchange connection using Evolution was one of the last things I was really missing in Ubuntu!! Thanks a lot!

However, I still have one big and one minor problem :). The big one is: I cannot send email using the ews account. When trying it, I get the error "Das Benutzerkonto, das zum Übermitteln dieser Anforderung verwendet wurde, ist nicht berechtigt, E-Mail im Auftrag des angegebenen sendenden Kontos zu senden" which means in English "The user account that was used to deliver this requirement is not authorized to send e-mail sent on behalf of the specified account" (according to Google Translate). The minor one is, that I am not able to fetch tasks. Here, the error is "No backend factory for 'mapi' of 'VTODO'" which means the same in English ;). If you need more information, just name them!

---

### Post by NHclimber on 2012-01-30
> **boudjere said:**
> The big one is: I cannot send email using the ews account. When trying it, I get the error "Das Benutzerkonto, das zum Übermitteln dieser Anforderung verwendet wurde, ist nicht berechtigt, E-Mail im Auftrag des angegebenen sendenden Kontos zu senden" which means in English "The user account that was used to deliver this requirement is not authorized to send e-mail sent on behalf of the specified account" (according to Google Translate).

I'm guessing that the account requires better authentication than plain password but that's just a guess. You can configure the authentication type in the 'Receiving Email' tab of the 'Account Editor' dialog ( from the main menu:  Edit -> Preferences, select 'Mail Accounts' in the left pane of the 'Evolution Preferences' dialog, select account name, click 'Edit' button brings up the Account Editor, click 'Receiving Email' tab).

If changing that doesn't do anything (or if you can't pick anything other than 'Password'), you should ask on this list => [email]evolution-list@gnome.org[/email]  Make sure to preface the subject line with [evolution-ews] so the right people see it.

 > **boudjere said:**
> The minor one is, that I am not able to fetch tasks. Here, the error is "No backend factory for 'mapi' of 'VTODO'" which means the same in English ;). If you need more information, just name them!

This is probably my packaging error - I might have left out a dependency for the mapi backend factory. I'll look into it and get back to you.

---

### Post by NHclimber on 2012-01-30
> **NHclimber said:**
> Firstly, it's still unstable. I was reparenting a folder with drag-n-drop and it wiped it from the server. Gone forever.

What works
   email w/ multiple exchange accounts, calendar* (including notifications), contacts*, tasks
   *although I have an 'extra' empty calender for one of my exchange accounts
    and an 'extra' empty Contacts and 'Suggested Contacts' for all of my exchange accounts
    (probably due to some stale gconf/dconf settings because I had the alpha version of evolution-ews setup earlier)


Yep - the 'extra' calendars and contacts folders were because of stale gconf settings from my earlier alpha setup. I *very carefully* hand edited (with gconf-editor) the 'sources' key for those accounts => the 'extra' contacts, suggested contacts and calendar have been removed.

> **NHclimber said:**
> 
What doesn't work
   deleting messages does not reliably move them to 'Deleted Items' folder
   'Junk E-mail' folder doesn't have a purge/empty like 'Deleted Items'
   sent emails are stored in local folders 'Sent' rather than 'Sent Items' on the server

I just found out that the 'sent items' issue is configurable (as is a similar issue with 'Drafts'). Which folder evolution-ews uses for 'Sent' and 'Draft' items can be set on the 'Defaults' tab of the 'Account Editor' (see above post for how to navigate to the Account Editor).

---

### Post by boudjere on 2012-01-31
> **NHclimber said:**
> I'm guessing that the account requires better authentication than plain password but that's just a guess. 
 
Thanks a lot for the answer. I had a look at the settings but there are no other choices apart from "password". At OAB URL I have "Public Folderoab.xml", could this be a problem? Public sounds a bit like "not all permissions" to me ;). But I'll see if I find answers at [EMAIL="evolution-list@gnome.org"]evolution-list@gnome.org[/EMAIL]. 

> This is probably my packaging error - I might have left out a dependency for the mapi backend factory. I'll look into it and get back to you.No hurries. I don't like to see my long list of tasks anyway :). Just kidding. 

Thanks again, boudjere

---

