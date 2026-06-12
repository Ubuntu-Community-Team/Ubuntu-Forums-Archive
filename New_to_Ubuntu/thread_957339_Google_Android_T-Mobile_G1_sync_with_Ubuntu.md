---
title: "Google Android T-Mobile G1 sync with Ubuntu"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-10-24
Hi, all!

I'm the lucky owner of a G1 now.  Ideas on how to get my contacts and calendar into it?  I use Kontact.  I'd like to get all my stuff into it.  My Gmail already syncs, obviously, but I'd really rather have it remote sync with my Kontact, since I don't like leaving messages on Gmail, and in fact generally choose to keep stuff out of the cloud.

---

### Post by kellemes on 2008-10-24
> **tarahmarie said:**
> Hi, all!

I'm the lucky owner of a G1 now.  Ideas on how to get my contacts and calendar into it?  I use Kontact.  I'd like to get all my stuff into it.  My Gmail already syncs, obviously, but I'd really rather have it remote sync with my Kontact, since I don't like leaving messages on Gmail, and in fact generally choose to keep stuff out of the cloud.

Sorry.. can't answer your question. :(
But man, am I jealous! This G1 I wanna have when it's available in Holland. :guitar:

---

### Post by Crandom on 2008-10-24
Since the G1 has just come out, and you are one of only a few people to own one, you must be a pioneer and work out a solution for yourself! Then post it here so we can spread the word.

Tip: Try looking a the file format for Kontact and for the calendar on your G1. See if there are any similarities. Does one use a MySQL database? Is it text based? Then you can start your quest for world domination!

---

### Post by skillllllz on 2008-10-24
> **tarahmarie said:**
> Hi, all!

I'm the lucky owner of a G1 now.  Ideas on how to get my contacts and calendar into it?  I use Kontact.  I'd like to get all my stuff into it.  My Gmail already syncs, obviously, but I'd really rather have it remote sync with my Kontact, since I don't like leaving messages on Gmail, and in fact generally choose to keep stuff out of the cloud.

Try [Mozilla Sunbird]("http://www.mozilla.org/projects/calendar/sunbird/") with this extention: [Provider for Google Calendar]("https://addons.mozilla.org/en-US/sunbird/addon/4631")

Works like a charm. Enjoy!

---

### Post by kellemes on 2008-10-24
> **skillllllz said:**
> Try [Mozilla Sunbird]("http://www.mozilla.org/projects/calendar/sunbird/") with this extention: [Provider for Google Calendar]("https://addons.mozilla.org/en-US/sunbird/addon/4631")

Works like a charm. Enjoy!

Indeed it does work very well, using this to sync my pc.

This obviously means leaving Kontact, not sure if this is what OP wants.

---

### Post by tarahmarie on 2008-10-24
I'd like to stay with Kontact.  Can I use my Gmail and Kontact as a sort of Microsoft Exchange Server thing?  Where I can get into my home computer as opposed to cloud computing?

---

### Post by skillllllz on 2008-10-24
> **tarahmarie said:**
> I'd like to stay with Kontact.  Can I use my Gmail and Kontact as a sort of Microsoft Exchange Server thing?  Where I can get into my home computer as opposed to cloud computing?

I'm not entirely sure I understand what you mean here. Google Apps (Gmail, Calendar, etc.) are in the cloud.

Currently, Kontact can access and display Google Calendars, but as read only.

It sorta sounds like you want to directly sync the calendar of your T-Mobile G1 with Kontact, i.e. without using Google's servers as a middle-man. If that's the case, then as far I know (someone please correct me if I am wrong), there exists no way to do that (yet).

---

### Post by tarahmarie on 2008-10-24
can Kontact act as a server?

---

### Post by Dougie187 on 2008-10-24
tarahmarie:
The G1 can only sync with gmail right now. All of the contacts that you want have to be entered into your Gmail account in some form, and the calendar can only be synced with your google calendar calendars, I am not sure if you can sync multiple calendars but I wouldn't be surprised. You could always try to export your contacts from kontact and then import them into gmail.

---

### Post by teknotuck on 2008-12-22
You can easily sync your kontact calendar with gmail calendar using GCALDaemon which you can find out about setting up [here/]("http://gcaldaemon.sourceforge.net/"). If you have any questions you cant get resolved hit my up and ill help you out or document it in greater detail and post it back up here.

I myself am still working on a reliable way to sync my contacts, you can try funambol. The biggest issue i have with this is that the fields between all 4 sides (kaddress, gmail, g1, funambol) do not exactly match up as of yet and this causes failures and other issues.

For instance i can get funambol (which is available in the android market) to sync my g1 contacts to their server but any contacts with notes fail. you will only get an error 500 but they do in fact work from i can tell so far.

If anyone else finds a way to resolve the issue of syncing contacts from kaddressbook i would be more most greatful but in the mean time i hope this helps someone else out. I have had gmail calendar syncing with kontacts now for over a year and had it so i could get it to sync with my old treo, now that i have the G1 i'm  twice as happy with it but contacts are still my only unresolved issue.  :KS

---

### Post by teknotuck on 2008-12-22
WOW, just found the solution, contacts now sync'able via gmail too!!

GCALDaemon has a section for contacts that essentially starts up a ldap server which is part of the application itself! just edit the conf file and look for the section 


################################################
# CONFIGURATION OF THE GMAIL CONTACT CONVERTER #
################################################

# Enable LDAP server
ldap.enabled=true

change it to true from false and make sure your firewall allows this then setup a new resource for ldap in kontact and there ya go!

i did have to reboot to get mine to work but probably more so because of all the crazy stuff i have running like psad, snort, bastille and a few others. what would be really nice though is to NOT see every entry doubled up but HEY, i can take it for now. Hopefully and i have not confirmed this yet but hopefully GCALDaemon sanitizes the entries before syncing so you don't have issues. I am wanting to start entering more info in some of my entries like the geo data and since i know the notes section of entries causes issues with funambol (which might no longer be needed now) it would be nice to know there is zero issues going forward. :KS :KS :KS :KS :KS

---

### Post by internalkernel on 2009-02-23
Aye... GCALdaemon does sync contacts through the LDAP feature... The problem I've come across is that some of the fields don't match up. Contacts with multiple emails will only show the first, mobile numbers are displayed as business, etc. etc. I've tried futzing with the LDAP version and editing the attributes in Kontact... but no love. 

I've also had no luck finding any more information online... and it's not like GCAL has a mailing list... oh well... it is the best solution so far. 

Has anyone found a better one? or found a way to fix some of the issues with GCAL? I hate living out of Google...

---

### Post by tarahmarie on 2009-03-13
Hi, all:

I've got two way syncing going on with calendar, one way syncing with contacts, and now, Google has introduced Google Tasks.  This might be the answer to my issues with getting my tasks synced in Kontact--yet still available on my G1 when I'm out.  

Anyone have any ideas how to sync them?

---

### Post by tarahmarie on 2009-04-02
Here's how to get your ebooks onto your Android!

[http://ubuntuforums.org/showthread.php?t=1114484](http://ubuntuforums.org/showthread.php?t=1114484)

---

### Post by free-radical on 2009-04-14
Hi,

I wrote an Android app, which synchronizes the contact list with a LDAP server periodically. It is somewhat limited now, but i’d love to get feedback. See [https://free-radical.ws/pmwiki.php/Software/Ldap2Ab](https://free-radical.ws/pmwiki.php/Software/Ldap2Ab)

Regards

---

### Post by axel206 on 2009-12-01
Is gcaldaemon still working?

---

### Post by Steelbak on 2010-09-27
This thread started two years ago and today the question still remains. Why is there no android sync with native linux PIMs like evolution and kontact? That's all I want in this life.

---

### Post by Paqman on 2010-09-27
> **Steelbak said:**
> Why is there no android sync with native linux PIMs like evolution and kontact? That's all I want in this life.

There is, just sync your PIM with your Google account.

---

### Post by axel206 on 2010-09-27
> **Paqman said:**
> There is, just sync your PIM with your Google account.

That's what I also do. I have synchronized gmail and gcalendar with Kaddressbook and Korganizer and everything is synchronized with my Android now.

[How to synchronize Google contacts and calendar with KAddressbook and KOrganizer](http://www.my-guides.net/en/content/view/178/26/)

---

