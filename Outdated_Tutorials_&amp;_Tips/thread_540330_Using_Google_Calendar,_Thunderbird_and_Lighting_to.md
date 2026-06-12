---
title: "Using Google Calendar, Thunderbird and Lighting to full effect"
date: 2007-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by dmfield on 2007-09-01
One of the best apps available on Windows is MS Outlook, as a complete suite of apps to organize your life, with Mail, to do lists and a calendar application, which allows for scheduling of meetings, and your time, which will communicate happily with your Windows Mobile or Smartphone Device. Allowing you to know what you are doing while both at your PC or away from it. However, being a commercial application, this can be quite a pricey solution, especially, if your are looking for these features to manage yourself, or maybe just a few others.
 However it is possible to archive similar results using Windows, or Linux for free.
 Being the owner of an [Orange M600 Smartphone]("http://www.trustedreviews.com/mobile-devices/review/2006/04/12/Orange-SPV-M600/p1"), and a Linux user, I spent a long time looking over the Internet, as the best way to get the information shared between my Desktop and my PDA phone. and although there are projects out there , [SynCE]("http://www.synce.org/index.php/SynCE-Wiki") springs to mind, they are not easy to setup.
 So I thought i would look at a different way of resolving the issue.. As always, this is not the only way, its just my way.
 **Issue**[LIST]
[*]Cross Platform Calendar Connectivity Windows, Linux, Windows Mobile
[*]Easy to use[/LIST]**How I managed it.**[INDENT]The key to my resolution is [Google Calendar]("http://www.google.com/calendar"), which can be accessed easily enough, especially if you already have a gMail account. If however you don&#8217;t have a gMail account, you can create your self a [Google Account here]("https://www.google.com/accounts/NewAccount?service=cl&passive=true&nui=1&continue=http%3A%2F%2Fwww.google.com%2Fcalendar%2Frender&followup=http%3A%2F%2Fwww.google.com%2Fcalendar%2Frender"), which will give you access to the Calendar functionality. Its pretty self explanatory. Once this is setup, its time to look at your mail client, obviously you could just use google calendar, via the web browser in Windows or Linux, but it doesn&#8217;t display to well on a PDA.. Also the aim here, is to emulate some of the functionality of Outlook, which allows you to have access to multiple mail accounts in one location.
[/INDENT]**The Email Client**[INDENT]The software I use is Thunderbird, Its my preferred Mail client, as i use both POP and IMAP based mail accounts, this mail client doesn&#8217;t however come with any built in calendar function, which is a reason, so many people berate it, and state that &#8220;calendar functionality is required before this app can move forward&#8221;. One of Thunderbirds strengths however, is, like its cousin Firefox, it works on a plugin system. That is, people have written third party modules, which can be used to enhance the functionality of Thunderbird. And I use 2 of these pluginfrom has an old version, Try downloading Lightening from 

 **Lightning Plugin for Thunderbird:**  [http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/)
** Google Calendar Provider:**  [https://addons.mozilla.org/en-US/thunderbird/addon/4631](https://addons.mozilla.org/en-US/thunderbird/addon/4631)

> 
Note: The version of the google provider at this time, requires Lightning version 0.7 or higher, and may not work with the one in the Gutsy repository under add/remove, so use the link above to download the latest version.

Quite simply, Lightning provides a calendar interface for Thunderbird, its part of the [Mozilla Sunbird]("http://www.mozilla.org/projects/calendar/") project, and helps provide the Schedule interface which standalone Thunderbird is missing.
[/INDENT]**Setup The Plugins**[INDENT]The magic here, however is the Provider for Google Calendar plugin, which, unlike just adding the necessary links to Thunderbird, to access Google Calendard, not only provides read access, it provides write access as well..
 Install both plugins, and restart Thunderbird, you will then be shown, a Calendar in the left pane, this calendar has 3 tabs Agenda, Todo and Calendars. To setup Google Calendar, click on the Calendar tab.
 Click on the New Button, in the Calendar Tab, and you will be given a choice, you need to select, On the Network. Click on Next, there is an option for Google Calendar, select this.
 In the Text bar under the Google Calendar you will need to enter the Link URL which allows you to write to your Account, you can find this, buy logging into the Google Calendar account you created earlier.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal1.JPG[/IMG]
 Create a new Calendar, or if you already have a celedar created, click on the down arrow next to the calendar. And click on Share this Calendar.
 You will be taken to a new page, where you will need to click on Calendar Details on the top of this page.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal2.JPG[/IMG]
 Then Select the XML button, next to the Private Address, this will allow you the read/write access to the calendar, if you need read only access, or wish to share calendards with read only access, use the XML button next to the Public Tab.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal3.JPG[/IMG]
 When you click on the XML button a URL will be displayed (i&#8217;ve edited the whole strin below for security reasons) Copy this URL , and paste it into the Thunderbird Text box, then click on Next.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal41.JPG[/IMG]
 Give the Calendar a name which you will use in Thunderbird to identify this calendar, and choose a colour, this is the colour which will identify your Google Calendar, if you are using multiple calendars. Then CLick on Next and then Finish.
 You will then see your calendar listed as available. you should now be able to add an event in either Thunderbird, or the wEb Interface, and both will update to show the events. You can set reminders, repeat events, and all the usual type of Schedule details.
[/INDENT]**Sync the PDA**[INDENT]The next step is to sync the Calendar with the PDA, this is done using the [GMobileSync]("http://rareedge.com/gmobilesync/") app for Windows Mobile or Smartphones. it requires .NET CF 2.0 which is available for download from the site, and provides not only read access to they Google Calendar, it also provides write access. This means as well as having PDA based access to your existing schedule, you can provide updates from your PDA to your calendar too. The application requires your login ID and password for the Google Calendar site. and works as far as i&#8217;m aware over both Wifi and GPRS networks, however i will confess, with UK prices as they are for Data over GPRS i&#8217;ve only tried Wifi. The Sync is a manual operation, and not automatic (yet)
[/INDENT] **Final Thoughts?**[INDENT] So what do we have? quite simply a free, Open source based Mail and personal schedulling system,  which can be accessed, over muliple platforms, Windows Mobile, Windows and Linux (not sure about OSX). Providing access to multiple mail accounts, using POP or IMAP. Read/Write Calendar access on  Desktop, Laptop or PDA.. There is also ToDo list functionality available. and all this can be accessed via a Web Interface. Now thats value for money.. Now if i could get this working with Open Xchange as well&#8230; bye bye M$ Exchange..
 [/INDENT]

---

### Post by be4truth on 2007-09-05
I have some problems with this setup. If I set an reoccurring event in Lighting it a) often doesn't set and b) if it sets, it changes the time by one hour early. 
When I change in Google calender everything will be properly synchronised with Lightning.

---

### Post by xxdesmus on 2007-09-06
Now all we need is for Google to accept the fact that people want a to-do list included with their email (gMail) and their calendar (gCal). It's so painfully easy to implement, but also such a painfully needed feature that the Google suite lacks.

Based on this, we'd then need to find a way to add/update the to-do list offline, and then your Thunderbird solution would be near perfect.

---

### Post by enine on 2007-09-06
Hello all, I'm new to this forum ran across it while working toward the same solution having just purchased a Motorola Q9M smartphone.
I could not get synce working at all and while messing with it my 19 month old grabbed my USB cable and yanked it hard enough to break the USB port on my laptop so until I pull it apart and re solder it I can't mess with synce anymore.
I'm using KDE's Kontact for my e-mail and PIM currently and found the GCALDaemon project and set it up to sync a google calendar with a local .ics file.  I then found an app called oggsync and sync'ed the google calendar down to my phone over wifi.  I tried opensync and it kept creating duplicate entries.  GCALDaemon says it supports the gmail contacts as well so I'm looking for some way to sync those down to the phone, I found an app called emoze but like oggsync its not open source.  Does anyone know of a project for the phone side that will allow that?
I'm also concerned that the gmail and thunderbird (I'd like to switch to TBird for use with portableTbird) don't seem to have many data fields in their contacts list like the kde address book the the thunderbird project doesn't seem interested in missing features.  Anyone have issues there?

WRT Outlook.  I used it from OL97 to OL2002, while its features are nice, its also a very problematic app.   First issue is the 2G .pst limit which I hit shortly after starting with it.  I got to the point in 1998 where I had to archive monthly and would then re-import my calendar.  Of course that was a big pain when the boss asked about that e-mail from customer x and I'd have to ask when it was so I knew which year or month archive to look through.  Then its searches were slooow.  Then sometimes it would still corrupt the pst file and nothing but a little hack tool could back it up while in use.  So you had to spend time with outlook maintenance such as monthly archives, exiting it to make backups, etc so it took a lot of work to keep it going.  Then if you were checking mail from two places and having OL leaving mail on the server for a certain number of days it would often mess up the pointer and re-download all the mail on the server so you had to go through and delete the duplicates.  Those pst files were fun, I'm became convinced that they are only still in use because the company that MS bought OL from originally lost the source and documentation for the format so they worked with what they could reverse engineer because nothing could ever work with those pst files but outlook, any other apps always had to go through outlook.  Then I found out one day that it was limited to 65534 items in a folder when I had an end user that actually hit that limit with 65534 sent items!  Of course there are all the annoyances such as Microsoft's preference for html mail or top posting and that it messes up threading, etc.  IMHO its not even one of the best apps feature wise as the OP stated because of some missing features that are supported in apps like kontact such as sub todo's.

---

### Post by caseywise on 2007-09-07
Great article, this helped me immensely!!  Thank you!!

---

### Post by TheCat on 2007-09-07
Can you post a screenshot or two?

---

### Post by bgreenberg on 2007-09-07
Excellent article, thanks!  This is very close to the "holy grail" of dumping Outlook but still being able to sync with a Windows Smart Phone.  I actually like Outlook, but its horrendous IMAP support kills it for me.

The one piece we're missing: synchronizing contacts.  Does anyone know of any way to either sync up with Thunderbird's Contact List or gMail's?

Syncing task list would be nice, too, but Contacts is much more important.

bg

---

### Post by enine on 2007-09-07
> **bgreenberg said:**
> 


Syncing task list would be nice, too, but Contacts is much more important.

bg

GCALDaemon looks like its close, it lets the gmail contacts act as an LDAP resource so you can then connect to it in thunderbird.  I haven't figured out a way to make them offline yet though.

---

### Post by bgreenberg on 2007-09-07
> **enine said:**
> GCALDaemon looks like its close, it lets the gmail contacts act as an LDAP resource so you can then connect to it in thunderbird.  I haven't figured out a way to make them offline yet though.

Yes but how do you Sync with your phone?

---

### Post by markmathson on 2007-09-08
bgreenberg-

I have heard of options available such as SyncKolab.  I tried it but didn't have a whole lot of success, but others seem to have.  

I second bgreenberg's question on recommendations on how to sync contacts using Thunderbird, specifically using IMAP.

---

### Post by utkjamie on 2007-09-08
Remember The Milk ([http://rememberthemilk.com](http://rememberthemilk.com)) is a very powerful and useful task list manager that can be integrated in Google Calendar.

Some of the great features include:

- SMS reminders of due tasks
- Tagging of tasks for easy retrieval
- Adding tasks via email (even better if you use this with [http://jott.com](http://jott.com))
- Custom task folders
- Custom task searches (e.g. show all tasks that require less than 20 minutes to complete, show all tasks due this week, etc)

---

### Post by mmoalem on 2007-09-08
i use plaxo (plaxo.com) to master sync all my pims and web based accounts

---

### Post by dmfield on 2007-09-08
I have to say i'm shocked.. some very positive reponse

to TheCat.. What screen shots would you like? its just thunderbird, google and a simple smartphone package..

With reference to the other two issues

contacts and todo

I will look into this.. I agree, we would be getting closer to the holy grail

Thanks for the positive responses.

---

### Post by ghostis on 2007-09-09
> **xxdesmus said:**
> Now all we need is for Google to accept the fact that people want a to-do list included with their email (gMail) and their calendar (gCal). It's so painfully easy to implement, but also such a painfully needed feature that the Google suite lacks.

Based on this, we'd then need to find a way to add/update the to-do list offline, and then your Thunderbird solution would be near perfect.

You can implement a todo list manually with tags and filters:

Email with the to address [email]bill+action@gmail.com[/email] automatically tags the email with the "Action" tag.  To mark a task finished, tag the email "finished".  If Thunderbird can handle tagging (have not checked recently), then this technique can be used offline as well.

or you can install the GTDInbox Firefox extension, which automates the above concept.

-Adam

---

### Post by mcdee on 2007-09-23
Has anyone managed to get this working successfully with gutsy?  I had this working fine under feisty but with gutsy the panel after I set the URL the 'next' button doesn't do anything so I can't do anything but cancel...

---

### Post by Blixter on 2007-09-26
Hi!

I had the same problem and found out that if you **install the lightning** from **synaptic package manager** everyting seems to work fine.

-Blixter

---

### Post by StooJ on 2007-10-02
> **ghostis said:**
>  If Thunderbird can handle tagging (have not checked recently)

The most recent version does, yep.

Interesting thread. I'm looking for something similar, but my phone is palm OS based, not Windows Mobile.

Sooner or later I'll have to upgrade it, and it's good to know I don't need to dread it so much if there is a linux-syncing route.

---

### Post by mikemn84 on 2007-10-03
I've been able to set up lightning with reading and writing to my google calendar.  I was also able to subscribe to a public calendar without an issue using the iCal feed.  What I can't get to work is to subscribe calendars that are shared with my google calendar.  These are listed under "Other Calendars" but they aren't fully public.  In calendar settings, it says "Anyone can: see nothing" and "You can: see all event details".

When I go to settings, I do have the choice to use the XML, ICAL, and HTML feeds provided, but when I've tried putting them in as a new calendar in Lightning, none of the events come up.

So I can't subscribe to them the same way I subscribed to my calendar with google provider because I don't have the username/pw for them, but it seems I also can't subscribe via iCal because it isn't fully public.  Is there a way to view these shared calendars with Lightning?

---

### Post by venik212 on 2007-10-03
I tried to implement this under Kubuntu, but the Thunderbird version that is in the repository is 1.5, and this calendar sharing trick requires Thunderbird 2.  Is there a simple way to upgrade?  I downloaded TB2, but have no instructions for its installation.

---

### Post by CaseyR on 2007-10-04
> **mikemn84 said:**
> So I can't subscribe to them the same way I subscribed to my calendar with google provider because I don't have the username/pw for them, but it seems I also can't subscribe via iCal because it isn't fully public.  Is there a way to view these shared calendars with Lightning?

i think i have the same issue as you, but im not quite sure what the cause is.  my original calendar is writable from sunbird but the following calendars i have created in google are read-only.  the link provided by google xml for the first calendar contains "my username%40gmail.com" whereas the others contain "some numbers and letters %40group.calendar.google.com"

has this issue been resolved?  any help would be appreciated.  if needed i can re-explain my situation.


EDIT:  problem solved.  i was entering the wrong login when prompted.

---

### Post by dierde on 2007-10-08
@[utkjamie] ... i use RTM, too and it works fine with google calendar. but how does this work with thunderbird? rtm opens a new calender ("other calendars") at google and i just treid to sync this with the XML, just then i just see the header as shown at google calenders (ToDos for xx day). At google i click on this header and get a fancy RTM popup with the task. Bot how to get this to thnderbird? any idea?

@[venik212] ... use this repository (source and bin):
[http://ubuntu.iuculano.ite](http://ubuntu.iuculano.ite)

worx fine

@[StooJ] ... i am also searching for a way to sync thunderbird with my palm. until now i only got to manage kOrganizer to sync with kpilot (on Kubuntu!!) i would apreciate an solution for that!!

dierde

---

### Post by venik212 on 2007-10-09
I find that when I enter an event into the calendar from TB, it does not appear in the Gmail calendar, which defeats the whole purpose.  I have installed Lighnint and Provider into TB under XP (it only works with version 2 and up of TB, and Ubuntu is still stuck in version 1.5).
ANy idea why the gmail calendar is not being updeated?

---

### Post by jfg69 on 2007-10-09
> **venik212 said:**
> I find that when I enter an event into the calendar from TB, it does not appear in the Gmail calendar, which defeats the whole purpose.  I have installed Lighnint and Provider into TB under XP (it only works with version 2 and up of TB, and Ubuntu is still stuck in version 1.5).
ANy idea why the gmail calendar is not being updeated?

I have version 2 of TB installed on my Ubuntu Ultimate distro.. and I use the calendar w/ lightning. Works very nicely. Do a search, as I dont remember which repository I got it from.

---

### Post by venik212 on 2007-10-10
The problem, I fear, is deeper-- it does not work from WINDOWS XP either, and there I am running TB 2. 
So somehow, what works nicely for others seems to fail for me...;-(

---

### Post by howardf42 on 2007-10-23
Your article is terrific.  Thank you.

After installing the suggested components and going through the setup procedure, I opened my home calendar in TB and went to edit an entry and save it on the new My Google calendar, but the entry just disappears.  I got it back with an undo, but can I transfer my current entries to the new calendar like this or is there another trick I should try?

I, too would like to see a Contacts sync solution in between TB and Google.  Then Bye Bye Outlook and Windows.

Thanks again,
Howard

---

### Post by venik212 on 2007-10-26
No one can pretend that Linux (Kubuntu) is ready for prime time if in order to make a simple thing like that work (a calendar) you have to know that you MUST install the extensions through Adpet (or Synaptic), because they do NOT work in Gutsy if you use TB2 to install them.  This constant need to walk between the drops of the incompatibility rain is frustrating, and is enough to discourage the hordes or MS haters out there.

---

### Post by bean77 on 2007-11-15
Why am I not able to download Provider...it says it is not compatible with Firefox?

---

### Post by jfg69 on 2007-11-15
> **venik212 said:**
> No one can pretend that Linux (Kubuntu) is ready for prime time if in order to make a simple thing like that work (a calendar) you have to know that you MUST install the extensions through Adpet (or Synaptic), because they do NOT work in Gutsy if you use TB2 to install them.  This constant need to walk between the drops of the incompatibility rain is frustrating, and is enough to discourage the hordes or MS haters out there.

Well, they work perfectly in MY version of Gutsy (Ultimate Edition 1.4- which was FF and 1.6 which is GG.) I've not had a single problem with TB or the cal or the extensions...
Thats not to say I havent had OTHER issues, lol..

---

### Post by mikemn84 on 2007-11-15
> Why am I not able to download Provider...it says it is not compatible with Firefox?

By default the download will try to install itself in Firefox, but this extension is for thunderbird so the process is a bit different.  From the site:

> 
How to Install in Thunderbird

   1. Right-click the link below and choose "Save Link As..." to download and save the file to your hard disk.
   2. In Mozilla Thunderbird, open Add-ons from the Tools menu.
   3. Click the Install button, and locate/select the file you downloaded and click "OK".


---

### Post by bean77 on 2007-11-16
Thanks, Mike.  I did just that and it worked great.  Now if I could only enter events in TB...everything else is perfect!

---

### Post by dmfield on 2007-11-30
Interesting that people can't get this working with Gutsy, followed my own instructions, and they seemed to work as i'd written the, Also since writing Lightning and the provider have both had heavy upgrades.

Still wish it was as simple as this to get Evolution working with gnome, because i'm incapbable of getting GcalDaemon working, and it all seems a bit much in order to do something wich does "just work" in Thuhn

---

### Post by stevewabc on 2007-12-09
this is nuts I have used lighting and google now for mo. but in ubuntu after installing the calenders into thunder bird and when I go to add a new calendar I pic (ICS) place the location and can not click on next.. anyone else have this problem?

any pointer would be helpful thanks..

---

### Post by Girindor on 2007-12-27
I have followed the instructions, Provider didn't work (in the TB add-ons menu it said that Provider "requires addictional items". I finally figured out I had to get a "CVS version" (whatever that is...) from [http://gdataprovider.mozdev.org/](http://gdataprovider.mozdev.org/)

So I managed to download a version that actually works (the one released on Oct. 24th 2007). Now, whenever I try to create a calendar in TB following your instructions, after I choose name and colour and click "finish", the window disappears and NO calendar is created.

Very frustrating...

-I'm running Gutsy, TB as well as lightning installed from "Add/Remove Applications".

---

### Post by dmfield on 2007-12-28
I think i know what might be causing the problem here, the version of lightening you use has to be the latest, and maybe the Ubuntu repo you are downloading from has an old version, Try downloading Lightening from 

[http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/)

And Provider from

[https://addons.mozilla.org/en-US/thunderbird/addon/4631](https://addons.mozilla.org/en-US/thunderbird/addon/4631)

---

### Post by Jonathan Métillon on 2008-01-03
Hi,

I want to say to the people who use a mobile phone with a good mobile OS, like my Nokia N95 8GB running S60 and not that crappy Windows Mobile:

You can achieve synchronization between your mobile and Google Calendar using the free service at [GooSync.com]("http://www.goosync.com/"). This will be limited to one calendar and 7 days in the past and 30 days in future. And they can even autoconfigure your phone using SMS!

And if you upgrade your account for only $3.33 USD /month, you will be able to sync all your calendars with no time limit, plus GMail contacts! There's currently an "anniversary" offer with 3 months for free.

Then you will be able to sync GCal and Thunderbird using dmfield method.

Now I'm looking at [RememberTheMilk.com]("http://www.rememberthemilk.com/") and [Jott.com]("http://jott.com/") to sync my todo lists. The bad news is that I will have to migrate from [TadaList.com]("http://www.tadalist.com/")...

---

### Post by jcampos on 2008-02-13
[COLOR="DarkOrange"]**Advantages**[/COLOR]
[LIST]
[*]You can access your PIM data from any '''**web access**''' point (by web interface)
[*]You can manage your PIM data with a '''**local client**''' (it usually has '''**more features**''' and is '''**faster**''')
[*]You can manage your PIM data '''**offline**''' (everything is duplicated locally)
[*]You can '''**backup**''' your PIM data (from the local copy)
[*]You can have more than one local client sharing the same data and work offline (i.e. '''**laptop offline access**''' when there is no connection)
[/LIST]


[COLOR="DarkOrange"]**GMail client: Thunderbird (read/write)**[/COLOR]

**Config**

sudo aptitude install thunderbird

thunderbird

[http://mail.google.com/support/bin/answer.py?answer=77662](http://mail.google.com/support/bin/answer.py?answer=77662)

exit thunderbird, and launch it again

[http://dogmafobia.com/2007/11/02/accede-a-gmail-desde-thunderbird-mediante-el-protocolo-imap/](http://dogmafobia.com/2007/11/02/accede-a-gmail-desde-thunderbird-mediante-el-protocolo-imap/)
* Más configuración de Thunderbird


**Offline**

[LIST]
[*]Menu / Edit / Accounts
[LIST]
[*] from your account, Offline
[*] Choose folders to work offline
[/LIST]
[/LIST]


**Backup**

you messages are in ~/.mozilla-thunderbird/<code>/ImapMail/...

**[COLOR="DarkOrange"]GCalendar from Thunderbird (read/write)[/COLOR]**

**Config**

[http://gcaldaemon.sourceforge.net](http://gcaldaemon.sourceforge.net)

sudo aptitude install lightning-extension lightning-extension-locale-ca

> wget -O /tmp/gcaldaemon-linux-1.0-beta16.zip [http://kent.dl.sourceforge.net/sourceforge/gcaldaemon/gcaldaemon-linux-1.0-beta16.zip](http://kent.dl.sourceforge.net/sourceforge/gcaldaemon/gcaldaemon-linux-1.0-beta16.zip)
cd /usr/local/sbin
sudo unzip /tmp/gcaldaemon-linux-1.0-beta16.zip
sudo addgroup gcaldaemon
sudo vi /etc/group
  gcaldaemon:x:1004:jcampos,...
sudo chgrp -R gcaldaemon /usr/local/sbin/GCALDaemon
sudo chmod -R g+w /usr/local/sbin/GCALDaemon
sudo chmod 755 /usr/local/sbin/GCALDaemon/bin/*.sh
xhost +
su - <your username>     # to ensure you're in the gcaldaemon group
export DISPLAY=:0.0
/usr/local/sbin/GCALDaemon/bin/config-editor.sh
  Calendar reloader script: choose the one that appears
  HTTP Sync
    Google Account
      New account
        Verify
        OK
    Choose account
  Save and Exit

sudo /usr/local/sbin/GCALDaemon/bin/standalone-start.sh

thunderbird

[http://gcaldaemon.sourceforge.net/usage.html#online](http://gcaldaemon.sourceforge.net/usage.html#online)

stop previous standalone-start.sh process, we'll add it to init system

sudo vi /etc/init.d/gcaldaemon 
>  #!/bin/sh
 
 GCAL_PATH=/usr/local/sbin/GCALDaemon/bin/
 GCAL_CMD=standalone-start.sh
 
 case $1 in
 
   start)
 
      $GCAL_PATH/$GCAL_CMD &
   ;;
 
   stop)
 
      GCAL_PID=`ps ax | grep 'org.gcaldaemon.standalone.Main' | grep -v grep | awk '{ print $1; }'`
      kill -9 $GCAL_PID
 
   ;;
 
   restart|reload)
 
      $0 stop
      $0 start
 
   ;;
 
 esac



sudo chmod a+x /etc/init.d/gcaldaemon

sudo update-rc.d gcaldaemon multiuser

sudo invoke-rc.d gcaldaemon restart


sudo vi /usr/local/sbin/GCALDaemon/conf/gcal-daemon.cfg

  http.allowed.addresses=127.0.0.1

sudo invoke-rc.d gcaldaemon restart



**Offline**

Local GCalDaemon provides offline service.


**Backup**

backup files are located in: /usr/local/sbin/GCALDaemon/work/backup

**[COLOR="DarkOrange"]GContacts from Thunderbird (read)[/COLOR]**

**Config**

NOTE: It didn't work with icedtea-java7-jre. It works with sun-java6-jre.

[http://gcaldaemon.sourceforge.net/usage4.html](http://gcaldaemon.sourceforge.net/usage4.html)

sudo /usr/local/sbin/GCALDaemon/bin/password-encoder.sh

add user and password to:

sudo vi /usr/local/sbin/GCALDaemon/conf/gcal-daemon.cfg

  ldap.enabled=true
  ldap.google.username=(gmail)
  ldap.google.password=(use password encoder!)
  ldap.vcard.version=3.0
  ldap.allowed.hostnames=localhost

sudo invoke-rc.d gcaldaemon restart

thunderbird

Menu / Preferences / Compose / Address / Search in directory / GMail

you may need this to import data: [http://labs.brotherli.ch/vcfconvert/](http://labs.brotherli.ch/vcfconvert/)



**Offline**

Local GCalDaemon provides offline service.

However, you can also:

# From the Thunderbird contact manager:
#* import your contacts into the "Local address book" (you can find them in /usr/local/sbin/GCALDaemon/work/vcard/contacts.*)
# in Edit / Preferences / Compose / Address /
#* also mark "Local address book"

**Backup**

you can backup your contacts, which are in: /usr/local/sbin/GCALDaemon/work/vcard/contacts.*

---

### Post by VMan on 2008-02-13
For those that are having problems with Thunderbird versions.  I use the following solution:

Run [Thunderbird Portable]("http://portableapps.com") from a USB stick.  It runs under Windows (XP & Vista) and Linux (using Wine).  

This way, I have the same calendar and contacts on any computer I use (I have to use several different computers at work, plus two different ones at home, and any at school).  The Portable Apps site has a good number of applications that install to and run from a USB stick.  I initially started using it for the OpenOffice.Org installation.  I love the Thunderbird+Lightning functionality.  Now with this guide, I have all I need.  Thanks.  Previous to your guide, I could only get my Google Calendar as read only; now it works perfectly!!:)

---

### Post by skabouter on 2008-02-17
Hi!
Newcomer here, found this thread very usefull. I made the link with Google Calendar from TB but have one itch: how to check my agenda in TB when i'm offline, for example in a meeting with a client or so!? 

Is there a way to locally store the last known calendar in TB for offline viewing? Otherwise... not so usefull for me i'm afraid.

Hope didn't overlook the answer to my question...

Grtz
K

---

### Post by Brian96 on 2008-03-07
Very useful howto, DM.

> **venik212 said:**
> I find that when I enter an event into the calendar from TB, it does not appear in the Gmail calendar, which defeats the whole purpose.  I have installed Lighnint and Provider into TB under XP (it only works with version 2 and up of TB, and Ubuntu is still stuck in version 1.5).
ANy idea why the gmail calendar is not being updeated?

I don't know if you ever got an answer to your question, but Provider puts a "Reload" icon in your Thunderbird toolbar. Clicking on that should sync your online calendars.

> **skabouter said:**
> Hi!
Newcomer here, found this thread very usefull. I made the link with Google Calendar from TB but have one itch: how to check my agenda in TB when i'm offline, for example in a meeting with a client or so!? 

Is there a way to locally store the last known calendar in TB for offline viewing? Otherwise... not so usefull for me i'm afraid.

Hope didn't overlook the answer to my question...

Grtz
K

So, are you saying the Google calendar entries disappear when you load Thunderbird offline? That is a problem.


While I find this an extremely helpful howto, I really dislike the new interface for Lightning 0.7, so I am back to Lightning 0.5 (the one available in the Gutsy repos). Provider, sadly, does not work with the older Lightning.

HOWEVER, you can still VIEW your Google calendar entries in Lightning, you just can't sync them. That is fine for me, as I don't mind switching to the web interface to enter new agenda items.

You can do this by following the instructions in the normal howto for sharing your Google calendar, you just have to use the ICS option (as there will not be a "Google Calendar" option) in Lightning's new calendar dialog.

---

### Post by EddieT on 2008-03-13
I had the same problem with getting lighting to work properly in TB.  Like everyone else I couldn't add new calendars.  I fixed it by getting Lightning v.5 from the repos or add/remove programs. Then I used the previous version of Provider v.2.1 that you can get by clicking on the version history for Provider and finding 0.2.1
[https://addons.mozilla.org/en-US/thunderbird/addons/versions/4631]("https://addons.mozilla.org/en-US/thunderbird/addons/versions/4631")
It's not the newest version but all is working now!

---

### Post by Brian96 on 2008-03-15
> **EddieT said:**
> I had the same problem with getting lighting to work properly in TB.  Like everyone else I couldn't add new calendars.  I fixed it by getting Lightning v.5 from the repos or add/remove programs. Then I used the previous version of Provider v.2.1 that you can get by clicking on the version history for Provider and finding 0.2.1
[https://addons.mozilla.org/en-US/thunderbird/addons/versions/4631]("https://addons.mozilla.org/en-US/thunderbird/addons/versions/4631")
It's not the newest version but all is working now!

Perfect solution for me!

---

### Post by veroloi on 2008-04-05
> **dmfield said:**
> 
 When you click on the XML button a URL will be displayed (i’ve edited the whole strin below for security reasons) Copy this URL , and paste it into the Thunderbird Text box, then click on Next.


Thank you for the howTo, it is exactly what I was looking for, but after entering the URL and then username and password for the calendar I get this error:

[Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsISimpleEnumerator.getNext]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: file:///home/user/.mozilla-thunderbird/xxxxx.default/extensions/xxxxx/js/calGoogleUtils.js :: passwordManagerGet :: line 479"  data: no]

Any idea what the problem could be?
Is it correct to enter my login password to google calendar or is there any other username/password?

I use thunderbird 2.0.0.12 and lightening 0.8 with Gutsy.

---

### Post by Brian96 on 2008-04-06
> **EddieT said:**
> I had the same problem with getting lighting to work properly in TB.  Like everyone else I couldn't add new calendars.  I fixed it by getting Lightning v.5 from the repos or add/remove programs. Then I used the previous version of Provider v.2.1 that you can get by clicking on the version history for Provider and finding 0.2.1
[https://addons.mozilla.org/en-US/thunderbird/addons/versions/4631]("https://addons.mozilla.org/en-US/thunderbird/addons/versions/4631")
It's not the newest version but all is working now!

WARNING!!!!

I installed Lightning 0.8 to see if they made any changes to the interface that I might like. Well, I didn't like it so I uninstalled it. But now when I try to start T-bird I get an error saying that the calendar data in my "profile was updated by a newer version of Lightning, and continuing will probably cause the information to be lost or corrupted" and it won't start.

Don't install 0.8 if you liked the old interface on 0.5!

---

### Post by ctcarton on 2008-04-07
> **Brian96 said:**
> WARNING!!!!

I installed Lightning 0.8 to see if they made any changes to the interface that I might like. Well, I didn't like it so I uninstalled it. But now when I try to start T-bird I get an error saying that the calendar data in my "profile was updated by a newer version of Lightning, and continuing will probably cause the information to be lost or corrupted" and it won't start.

Don't install 0.8 if you liked the old interface on 0.5!

You can wipe your calendar profile by deleting storage.sdb from the profile directory.  As long as you're syncing to google you won't lose anything; it's just a minor inconvenience to re-configure it.

---

### Post by LingLings on 2008-04-07
What an amazing thread!  I'm very grateful for such simple to follow instructions as I'm a total Noob who has experienced varying degrees of success of setting up and using Ubuntu.  I now have Thunderbird 2.0.0.12 running with Lightning 0.8 / Provider for Google Calendar.  Both mail and calendar are now perfectly synchronized.  So a big thank you to original poster!

However I'm having trouble following the instructions to install GCalDaemon so that I can sync the Thunderbird Address book with my Gmail contacts.  No doubt that I'm doing something basic wrong which tends to be the case at the moment.  Can anyone point me in the right direction?

I have downloaded the zip file into my download folder (i.e. it now appears in the panel that pops up in ubuntu with Open / Remove options) and it is also sitting on my desktop.

Here's what happens next...
```

paul@line-city:~$ sudo bash
root@line-city:~# cd /usr/local/sbin
root@line-city:/usr/local/sbin# sudo unzip /downloads/gcaldaemon-linux-1.0-beta16.zip
unzip:  cannot find or open /downloads/gcaldaemon-linux-1.0-beta16.zip, /downloads/gcaldaemon-linux-1.0-beta16.zip.zip or /downloads/gcaldaemon-linux-1.0-beta16.zip.ZIP.
root@line-city:/usr/local/sbin# 
```

I have tried replacing "/downloads" in the path with "/home/paul/Desktop" but this makes no difference

Am I missing an obvious trick? 

Any help will be gratefully received. Please give basic instructions if replying as I'm still finding my feet with the Terminal.

---

### Post by MichaelRST on 2008-04-21
Great thread - thanks!

For contact sync, I'm using a Thunderbird addon:
[zindus thunderbird gmail contact sync]("http://www.zindus.com")

Only been using it a few days but it sems to work well.  I like that it does two-way sync.

---

### Post by Brian96 on 2008-04-21
Has anybody figured out how to get T-bird (and its add-ons) to save synced data for offline access?

---

### Post by tomsa on 2008-04-24
Hi all- this has really been a great thread in general!  My personal problem at the moment is that I can't seem to get lightning to let me add more than one calendar from a single google account.  I have my google calendar set up as four separate calendars so that everything is color coded for different people and to make for easy importing from our work MS computers for the wife and me.  When I try to add a new calendar that is attached to my email account, thunderbird/lightning's password manager doesn't function properly, and I am asked for my password over and over- to the point of crashing the application.  I always check the box to remember the password- is there something else that's really obvious that I'm missing, or is this a bigger problem than I realize?  Many thanks.

---

### Post by venik212 on 2008-04-28
I have installed Kubuntu 8.04 and Thunderbird 2.  The very nice combination of Lightning and Provider for the Google Calendar no longer works.  This is very disappointing, since that combination was truly useful.
I tried old versions of these extensions, but they failed.

Any ideas?

---

### Post by in_rainbow on 2008-04-30
> **venik212 said:**
> I have installed Kubuntu 8.04 and Thunderbird 2.  The very nice combination of Lightning and Provider for the Google Calendar no longer works.  This is very disappointing, since that combination was truly useful.
I tried old versions of these extensions, but they failed.

Any ideas?

Ah damn. I have the same setup and was just about to set this up. Can anyone else confirm? Is there any workaround?

---

### Post by Il Capitano on 2008-04-30
> **venik212 said:**
> I have installed Kubuntu 8.04 and Thunderbird 2.  The very nice combination of Lightning and Provider for the Google Calendar no longer works.  This is very disappointing, since that combination was truly useful.
I tried old versions of these extensions, but they failed.

Any ideas?

I have the same problem.

Things got a bit better when i used Lightning version 0.7, but then provider for google calender doesn't work anymore. :(

---

### Post by michaelphipps on 2008-04-30
Thank you very much for this.

The sync between Sunbird (Lightning) and Google Calendar has had me puzzled for a while.

Now Thunderbird, Lightning and Gmail, Google Calendar work together exactly the way I want.

---

### Post by prosonik on 2008-04-30
Hi All,

I have success with the combination of hardy, thunderbird 2.0.0.12, lighting .8 x64 and provider .4.

I installed thunderbird using apt, then manually installed lighting. Once Lighting was up and working, i added provider.

To top it off, I actually had imported all my settings from my windows parition, and once i had provider set up, all my settings were there and working. 

I have quickly tested it, and everything seems to sync nicely.

Here are the links:

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.7/contrib/linux-x86-64/)

[https://addons.mozilla.org/en-US/thunderbird/addon/4631](https://addons.mozilla.org/en-US/thunderbird/addon/4631)

Hope this helps.

prosonik

---

### Post by in_rainbow on 2008-05-01
It's working for me on a fresh install of Kubuntu Hardy,Thunderbird 2.0.0.12, Lightning 0.8, Provider 0.4. I have read and write access to my GCal.

I followed this guide

[http://bfish.xaedalus.net/?p=239]("http://bfish.xaedalus.net/?p=239")

I do however have these errors repeatedly in my Error Console:

Error: [Exception... "'Component does not have requested interface' when calling method: [nsIInterfaceRequestor::getInterface]"  nsresult: "0x80004002 (NS_NOINTERFACE)"  location: "<unknown>"  data: no]

Warning: nsIInterfaceRequestor requesting invalid interface {a63f70c0-148b-11d3-9333-00104ba0fd40}

But everything seems to be working fine.

---

### Post by alisemail on 2008-05-01
Looks like Kubuntu 8.04 Breaks it for me to. Lighting .7 + Google Cal .4 + Thunderbird (latest version from adept) doesn't work well. THe Provider for Google Calendar states "Requires additional items"

Sad day as this is the first real block I've found in my transition from windows to Ubuntu. Hopefully a fix will be out soon

---

### Post by Raybo on 2008-05-06
I had the problem with lightning .7 and provider .4.  Leave lightning 0.7 in place and downgrade provider to 0.3.1.  It worked for me.

---

### Post by pigphish on 2008-05-06
here is a method that worked for me in 8.04 hardy using thunderbird 2..14 and lightning .8

Uses Plaxo for contacts and Google for calendar 

[http://www.tipsfor.us/2008/04/19/sync-your-windows-mobile-contacts-and-calendar-with-plaxo-thunderbird-and-google-for-free/]("http://www.tipsfor.us/2008/04/19/sync-your-windows-mobile-contacts-and-calendar-with-plaxo-thunderbird-and-google-for-free/")

uses  [http://www.nuevasync.com]("http://www.nuevasync.com")

---

### Post by revchris on 2008-05-14
I can't add a new calendar in 8.04 hardy using thunderbird 2.14, lightning .8, and Provider for Google Calendar .4.  The option is greyed out.  Any ideas?

---

### Post by nlz on 2008-05-19
for me lightning and thunderbird are working nicely, but i have one problem: my (google synchronized) calendar isn't available offline. How can i change this?

---

### Post by cygnis1 on 2008-05-20
I also had trouble syncing Lightning with Google Calendar.  I tried about everything to get my calendar back. Using L.8 and Provider 4 did nothing.  I couldn't even get the option to add google calendars.  Finally I used Lightning 7 and Provider 3, and now I have my calendars back the way I want them.  Whew! What a chore.  I am slowly getting Hardy back to what I want.

---

### Post by terwilligerjones on 2008-05-20
I've had spotty results with 8.04, Thunderbird 2.0.0.14, Lightning and Provider. My home machine works fine. The machines I administer for others, on the other hand, universally refuse to permit me to open a new calendar. The option is grayed out. Not sure what the difference is. All were formerly 7.10 machines. All were upgraded to 8.04 via the net.

stew

---

### Post by revchris on 2008-05-22
> **cygnis1 said:**
> I also had trouble syncing Lightning with Google Calendar.  I tried about everything to get my calendar back. Using L.8 and Provider 4 did nothing.  I couldn't even get the option to add google calendars.  Finally I used Lightning 7 and Provider 3, and now I have my calendars back the way I want them.  Whew! What a chore.  I am slowly getting Hardy back to what I want.

Going back to Lightning 7 and Provider 3 worked for me too.

Thanks

---

### Post by spotteddog on 2008-05-25
I tried Lightning 0.7 (from Synaptic) and Provider 3.1 (from Mozilla), but everything freezes. I start TB and it says "Sending Login Information", then turns all gray. It downloads my "GCal" settings then freezes. I thought it was just taking awhile, so I let it run a (long) while and it never un-freezes. I have to use a "force quit".

Anyone solved this?

Thanks.

---

### Post by reckless2k2 on 2008-06-02
i'm having problems as well. can someone please provide the url to Provider 0.3.1? i can't find it anywhere.

---

### Post by cygnis1 on 2008-06-02
You can find it here:
[URL="You can find it here:  http://addons.mozilla.org/en-US/thunderbird/addons/versions/4631


Cygnis1

---

### Post by reckless2k2 on 2008-06-02
thanks much. for the life of me i couldn't find it. maybe i overlooked it. haha

---

### Post by cygnis1 on 2008-06-03
You are most welcome.  I also have these kind of problems.

---

### Post by zeta on 2008-06-05
I had - and to some extent still have - the same issues with Thunderbirds you guys describe (Ubuntu 8.04). I fixed many of the problems - especially Provider asking for additional addons - when is just uninstallad Provider and Lightning and reinstalled them using the addon-files directly from Mozilla-website. For some reason Provider doesn't like the Lightning version out of repository.
So Provider and Lightning work well, unfortunately Thunderbird is still unstable. It crashes almost every time I start it after a reboot, and I also get 
```
Warning: nsIInterfaceRequestor requesting invalid interface {a63f70c0-148b-11d3-9333-00104ba0fd40}
```
:(

---

### Post by thomsany on 2008-06-26
I tried installing it on my Ubuntu 8.04 machine and for some reason the Lightning plugin is installed and so is the Google Caleandar plugin but when I open Thunderbird, I can't create appointments and the calendar is messed up.
For some reason I can't use it at all.
So I removed the plugins.

Any way to solve this issue?

Thanks much,
Teo

---

### Post by 1jackjack on 2008-08-05
After plenty of faffing, I just got this working in Ubuntu 8.04 and this is how:

1) install thunderbird (mine is version 2.0.0.16 (20080724)) and lightning (mine is 0.7) from start>add/remove
2) install the previous version v0.3.1 of "provider for google calendar" extension by going to the previous versions page for this addon:
[https://addons.mozilla.org/en-US/thunderbird/addons/versions/4631](https://addons.mozilla.org/en-US/thunderbird/addons/versions/4631)
and downloading v0.3.1 to your desktop, then going into thunderbird then tools>addons>install...
3) go into calendar view, and create a new cal (select "on the network" then "google calendar")

hope this helps someone...

---

### Post by venik212 on 2008-08-06
I followed these instructions, but it failed on my 8.04.  The calendar view is all screwed up, and lightning does not respond at all.

---

### Post by giljorak on 2008-08-12
For the screwed up layout and no new calendar option go here:

[http://groups.google.com/group/mozilla.support.calendar/browse_thread/thread/a5a05e45b8235a15](http://groups.google.com/group/mozilla.support.calendar/browse_thread/thread/a5a05e45b8235a15)


That fixed my issues.

---

### Post by beholdforiambob on 2008-08-13
has any one got this to work on the 64 bit version of Ubuntu?

---

### Post by tygern8r on 2008-08-20
> **beholdforiambob said:**
> has any one got this to work on the 64 bit version of Ubuntu?

I run this on my Studio 64 bit:

Thunderbird version 2.0.0.16 (20080724)
Lightning 0.7 (2007120901)
with the SyncSW add-on 1.166

I get my Gmail in Thunderbird and I can sync Lightning with ScheduleWorld, Google Calendar and my windows mobile 6.1 Motorola Q9c (ota sync), contacts and calendar. No special installing of anything. [ScheduleWorld]("http://www.scheduleworld.com/") has good directions and it's free, and they email you the add-on. Thunderbird updated it auto-magically just the other day, too. I love it so far. :)

---

### Post by kevjohns on 2008-08-22
> **dmfield said:**
> One of the best apps available on Windows is MS Outlook, as a complete suite of apps to organize your life, with Mail, to do lists and a calendar application, which allows for scheduling of meetings, and your time, which will communicate happily with your Windows Mobile or Smartphone Device. Allowing you to know what you are doing while both at your PC or away from it. However, being a commercial application, this can be quite a pricey solution, especially, if your are looking for these features to manage yourself, or maybe just a few others.
 However it is possible to archive similar results using Windows, or Linux for free.
 Being the owner of an [Orange M600 Smartphone]("http://www.trustedreviews.com/mobile-devices/review/2006/04/12/Orange-SPV-M600/p1"), and a Linux user, I spent a long time looking over the Internet, as the best way to get the information shared between my Desktop and my PDA phone. and although there are projects out there , [SynCE]("http://www.synce.org/index.php/SynCE-Wiki") springs to mind, they are not easy to setup.
 So I thought i would look at a different way of resolving the issue.. As always, this is not the only way, its just my way.
 **Issue**[LIST]
[*]Cross Platform Calendar Connectivity Windows, Linux, Windows Mobile
[*]Easy to use[/LIST]**How I managed it.**[INDENT]The key to my resolution is [Google Calendar]("http://www.google.com/calendar"), which can be accessed easily enough, especially if you already have a gMail account. If however you don’t have a gMail account, you can create your self a [Google Account here]("https://www.google.com/accounts/NewAccount?service=cl&passive=true&nui=1&continue=http%3A%2F%2Fwww.google.com%2Fcalendar%2Frender&followup=http%3A%2F%2Fwww.google.com%2Fcalendar%2Frender"), which will give you access to the Calendar functionality. Its pretty self explanatory. Once this is setup, its time to look at your mail client, obviously you could just use google calendar, via the web browser in Windows or Linux, but it doesn’t display to well on a PDA.. Also the aim here, is to emulate some of the functionality of Outlook, which allows you to have access to multiple mail accounts in one location.
[/INDENT]**The Email Client**[INDENT]The software I use is Thunderbird, Its my preferred Mail client, as i use both POP and IMAP based mail accounts, this mail client doesn’t however come with any built in calendar function, which is a reason, so many people berate it, and state that “calendar functionality is required before this app can move forward”. One of Thunderbirds strengths however, is, like its cousin Firefox, it works on a plugin system. That is, people have written third party modules, which can be used to enhance the functionality of Thunderbird. And I use 2 of these pluginfrom has an old version, Try downloading Lightening from 

 **Lightning Plugin for Thunderbird:**  [http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/)
** Google Calendar Provider:**  [https://addons.mozilla.org/en-US/thunderbird/addon/4631](https://addons.mozilla.org/en-US/thunderbird/addon/4631)



Quite simply, Lightning provides a calendar interface for Thunderbird, its part of the [Mozilla Sunbird]("http://www.mozilla.org/projects/calendar/") project, and helps provide the Schedule interface which standalone Thunderbird is missing.
[/INDENT]**Setup The Plugins**[INDENT]The magic here, however is the Provider for Google Calendar plugin, which, unlike just adding the necessary links to Thunderbird, to access Google Calendard, not only provides read access, it provides write access as well..
 Install both plugins, and restart Thunderbird, you will then be shown, a Calendar in the left pane, this calendar has 3 tabs Agenda, Todo and Calendars. To setup Google Calendar, click on the Calendar tab.
 Click on the New Button, in the Calendar Tab, and you will be given a choice, you need to select, On the Network. Click on Next, there is an option for Google Calendar, select this.
 In the Text bar under the Google Calendar you will need to enter the Link URL which allows you to write to your Account, you can find this, buy logging into the Google Calendar account you created earlier.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal1.JPG[/IMG]
 Create a new Calendar, or if you already have a celedar created, click on the down arrow next to the calendar. And click on Share this Calendar.
 You will be taken to a new page, where you will need to click on Calendar Details on the top of this page.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal2.JPG[/IMG]
 Then Select the XML button, next to the Private Address, this will allow you the read/write access to the calendar, if you need read only access, or wish to share calendards with read only access, use the XML button next to the Public Tab.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal3.JPG[/IMG]
 When you click on the XML button a URL will be displayed (i’ve edited the whole strin below for security reasons) Copy this URL , and paste it into the Thunderbird Text box, then click on Next.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal41.JPG[/IMG]
 Give the Calendar a name which you will use in Thunderbird to identify this calendar, and choose a colour, this is the colour which will identify your Google Calendar, if you are using multiple calendars. Then CLick on Next and then Finish.
 You will then see your calendar listed as available. you should now be able to add an event in either Thunderbird, or the wEb Interface, and both will update to show the events. You can set reminders, repeat events, and all the usual type of Schedule details.
[/INDENT]**Sync the PDA**[INDENT]The next step is to sync the Calendar with the PDA, this is done using the [GMobileSync]("http://rareedge.com/gmobilesync/") app for Windows Mobile or Smartphones. it requires .NET CF 2.0 which is available for download from the site, and provides not only read access to they Google Calendar, it also provides write access. This means as well as having PDA based access to your existing schedule, you can provide updates from your PDA to your calendar too. The application requires your login ID and password for the Google Calendar site. and works as far as i’m aware over both Wifi and GPRS networks, however i will confess, with UK prices as they are for Data over GPRS i’ve only tried Wifi. The Sync is a manual operation, and not automatic (yet)
[/INDENT] **Final Thoughts?**[INDENT] So what do we have? quite simply a free, Open source based Mail and personal schedulling system,  which can be accessed, over muliple platforms, Windows Mobile, Windows and Linux (not sure about OSX). Providing access to multiple mail accounts, using POP or IMAP. Read/Write Calendar access on  Desktop, Laptop or PDA.. There is also ToDo list functionality available. and all this can be accessed via a Web Interface. Now thats value for money.. Now if i could get this working with Open Xchange as well… bye bye M$ Exchange..
 [/INDENT]

Works with Mac as well. We have thunderbird and the same plugins

regards,
kevjohns

---

### Post by Brian96 on 2008-08-22
Can anyone tell me why T-bird gives me Lightning's mini-calendar in the main mail view in Windows, but not in Ubuntu? All I can get in Ubuntu is the ugly "Today" panel. I get the mini-calendar in Windows even without the "Today" panel.

---

### Post by vikas1234 on 2008-08-23
Thanks for the wonderful article. It helped me in the configuration

---

### Post by 1jackjack on 2008-08-23
Brilliant guide kevjohns, this is almost my exact setup and it works very well! I would just add that if you don't have an MS windows mobile compatible device (probably quite common amongst those who are seeking alternatives to a MS OS and MS Outlook), you can use goosync, which works well with my nokia 6220c (symbian s60 OS).

---

### Post by tjwilli on 2008-08-31
> **giljorak said:**
> For the screwed up layout and no new calendar option go here:

[http://groups.google.com/group/mozilla.support.calendar/browse_thread/thread/a5a05e45b8235a15](http://groups.google.com/group/mozilla.support.calendar/browse_thread/thread/a5a05e45b8235a15)


That fixed my issues.

Thanks so much for this post. I've been struggling with this for days trying to get lightning and google provider working on ubuntu.

The trick is installing libstdc++5

---

### Post by crjackson on 2008-09-26
> **jcampos said:**
> [COLOR="DarkOrange"]**Advantages**[/COLOR]
[LIST]
[*]You can access your PIM data from any '''**web access**''' point (by web interface)
[*]You can manage your PIM data with a '''**local client**''' (it usually has '''**more features**''' and is '''**faster**''')
[*]You can manage your PIM data '''**offline**''' (everything is duplicated locally)
[*]You can '''**backup**''' your PIM data (from the local copy)
[*]You can have more than one local client sharing the same data and work offline (i.e. '''**laptop offline access**''' when there is no connection)
[/LIST]


[COLOR="DarkOrange"]**GMail client: Thunderbird (read/write)**[/COLOR]

**Config**

sudo aptitude install thunderbird

thunderbird

[http://mail.google.com/support/bin/answer.py?answer=77662](http://mail.google.com/support/bin/answer.py?answer=77662)

exit thunderbird, and launch it again

[http://dogmafobia.com/2007/11/02/accede-a-gmail-desde-thunderbird-mediante-el-protocolo-imap/](http://dogmafobia.com/2007/11/02/accede-a-gmail-desde-thunderbird-mediante-el-protocolo-imap/)
* Más configuración de Thunderbird


**Offline**

[LIST]
[*]Menu / Edit / Accounts
[LIST]
[*] from your account, Offline
[*] Choose folders to work offline
[/LIST]
[/LIST]


**Backup**

you messages are in ~/.mozilla-thunderbird/<code>/ImapMail/...

**[COLOR="DarkOrange"]GCalendar from Thunderbird (read/write)[/COLOR]**

**Config**

[http://gcaldaemon.sourceforge.net](http://gcaldaemon.sourceforge.net)

sudo aptitude install lightning-extension lightning-extension-locale-ca



sudo /usr/local/sbin/GCALDaemon/bin/standalone-start.sh

thunderbird

[http://gcaldaemon.sourceforge.net/usage.html#online](http://gcaldaemon.sourceforge.net/usage.html#online)

stop previous standalone-start.sh process, we'll add it to init system

sudo vi /etc/init.d/gcaldaemon 


sudo chmod a+x /etc/init.d/gcaldaemon

sudo update-rc.d gcaldaemon multiuser

sudo invoke-rc.d gcaldaemon restart


sudo vi /usr/local/sbin/GCALDaemon/conf/gcal-daemon.cfg

  http.allowed.addresses=127.0.0.1

sudo invoke-rc.d gcaldaemon restart



**Offline**

Local GCalDaemon provides offline service.


**Backup**

backup files are located in: /usr/local/sbin/GCALDaemon/work/backup

**[COLOR="DarkOrange"]GContacts from Thunderbird (read)[/COLOR]**

**Config**

NOTE: It didn't work with icedtea-java7-jre. It works with sun-java6-jre.

[http://gcaldaemon.sourceforge.net/usage4.html](http://gcaldaemon.sourceforge.net/usage4.html)

sudo /usr/local/sbin/GCALDaemon/bin/password-encoder.sh

add user and password to:

sudo vi /usr/local/sbin/GCALDaemon/conf/gcal-daemon.cfg

  ldap.enabled=true
  ldap.google.username=(gmail)
  ldap.google.password=(use password encoder!)
  ldap.vcard.version=3.0
  ldap.allowed.hostnames=localhost

sudo invoke-rc.d gcaldaemon restart

thunderbird

Menu / Preferences / Compose / Address / Search in directory / GMail

you may need this to import data: [http://labs.brotherli.ch/vcfconvert/](http://labs.brotherli.ch/vcfconvert/)



**Offline**

Local GCalDaemon provides offline service.

However, you can also:

# From the Thunderbird contact manager:
#* import your contacts into the "Local address book" (you can find them in /usr/local/sbin/GCALDaemon/work/vcard/contacts.*)
# in Edit / Preferences / Compose / Address /
#* also mark "Local address book"

**Backup**

you can backup your contacts, which are in: /usr/local/sbin/GCALDaemon/work/vcard/contacts.*

This is quite a nice guide.  I'll give this a try over the weekend.  Part of your script displays as a smily face in the forums.  What should that smily actually be for making the script?

---

### Post by ugm6hr on 2008-09-29
Thanks for the original Tutorial.

It works with Hardy 64-bit, [x64 Lightning 0.9]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.9/contrib/linux-x86_64/lightning-0.9-linux-x86_64.xpi") (save file, and install as addon from within T-bird), and [Google Provider 0.5]("https://addons.mozilla.org/en-US/thunderbird/downloads/file/38052/provider_for_google_calendar-0.5-tb+sb.xpi") (again - save file, install as addon in T-bird).

I did have to initially add the calendar as an ICal calendar (read only), but on restarting T-bird, it automatically detected it and offered to upgrade to read/write.  Unfortunately, adding it directly as a Google calendar didn't seem to work.

Anyway, works great now.

---

### Post by rpost on 2008-10-03
To provide a bit more current info on this issue:

The following order of operations worked well for me with Ubuntu 8.04.1 (amd64)

1. Installed Thunderbird 2.0.0.17 from Ubuntu package

2. Installed Lightning 0.9 from contrib xpi (that is, get download it from Mozilla, don't use the Ubuntu package).  A version is here:

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.9/contrib/linux-x86_64/lightning-0.9-linux-x86_64.xpi](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/0.9/contrib/linux-x86_64/lightning-0.9-linux-x86_64.xpi)

3. Installed Provider for Google 0.5 from Mozilla xpi.  A version is here:

[https://addons.mozilla.org/en-US/thunderbird/downloads/file/38052/provider_for_google_calendar-0.5-tb+sb.xpi](https://addons.mozilla.org/en-US/thunderbird/downloads/file/38052/provider_for_google_calendar-0.5-tb+sb.xpi)

rp

---

### Post by kriss08 on 2008-10-07
I have followed the instructions and installed the 2 components/add-ins.  However, it does not seem to work from the perspective of each respective calendar updating and posting events to the other.

Is there something that I am missing or should be doing?

Thanks,

---

### Post by jakewc2 on 2008-10-07
I have the same problem, I followed the instructions on the first page, when I added the html address to the calender, the dates on the google calender appeared on Lightening, but when I added a task to Lightening, it wont appear on the google calender, and I cant share it with my other pc. Would anybody know why this should be happening?

Thanks.

---

### Post by zerubbabel on 2008-10-07
I have been using Thunderbird/Lightning for awhile very happily, but then decided to reinstall Ubuntu (8.04) to occupy my entire disk, ditching Vista. I backed up my entire home directory, and then restored it after the reinstall. Most of Thunderbird works fine, and all my data is there, including mail and addressbooks, but not my calendars. It will be a great loss if I can't recover them. Has anyone been through this before?

---

### Post by zerubbabel on 2008-10-08
Problem solved. Had to uninstall Lightning, then install libstdc++5, then reinstall Lightning.

---

### Post by cversion7 on 2008-10-13
Great info! It is working perfectly!

---

### Post by anukoolr on 2008-10-20
Gcal does not have the facility of adding tasks. It can accept only events. Thats why you had that problem.

---

### Post by tgyorgyi on 2008-10-30
I have Thunderbird 2.0.0.17 just installed with Add/Remove, and I tried to install Lightning 0.9 from the Mozilla site, but I got an error message that this version of Lightning is not compatible with the version of Thunderbird that I have. :( 

I got a similar message for the Google Provider above as well.

---

### Post by tgyorgyi on 2008-10-30
I have Thunderbird 2.0.0.17 just installed with Add/Remove, and I tried to install Lightning 0.9 from the Mozilla site, but I got an error message that this version of Lightning is not compatible with the version of Thunderbird that I have. :( 

I got a similar message for the Google Provider above as well.

---

### Post by DesertF0x on 2009-01-06
How does it work in 8.10? I've tried to use the Lightning ubuntu package and just the addon.The addon does not work(no calendar availible or addable). And with the lightning package Provider for Google Calendar does not work.

---

### Post by cygnis1 on 2009-01-06
The answer is: It doesn't.  At least I wasn't able to get it working.  I have gone back to 8.04.  I have my system tweaked to the way I want it and am tired of having to retweak everything when I change my system.  Hardy works for me and my laptop.

---

### Post by ender4 on 2009-01-06
I installed lightning .8 with the add/remove program utility and then downloaded and installed provider 0.5.1 but got a message that the i was missing a dependency for google provider. on closer inspection i found out that provider 0.5.1 only works with lightning version 0.9

all i had to do to fix this uninstall lightning 0.8 (this stay may be unnecessary), downloaded lightning 0.9 directly from mozilla ([https://addons.mozilla.org/en-US/thunderbird/addon/2313]("https://addons.mozilla.org/en-US/thunderbird/addon/2313")) and installed it from thunderbird.  now it works fine.

---

### Post by cygnis1 on 2009-01-06
Try installing this library:  libstdc++5  
It worked for me.  It is in the Ubuntu repositories.

---

### Post by wykedengel on 2009-01-11
Okay, I finally got this to work on my system. Here is what I did step by step:

1) Checked to see if libstdc++5 was installed. (It was.)
2) Removed Lightning extension I got from repositories.
3) Downloaded latest Lightning extension from TB extension website.
4) Installed Provider after installing Lightning.
5) Restarted TB and lo and behold, it works.

---

### Post by laakkus on 2009-01-21
If you want to add your phone (I have Nokia N95) to the syncing, follow these instructions. I found them really helpful !!

[http://www.lucagasperini.com/blog/2007-sync-nokia-thunderbird-and-google-calendar/](http://www.lucagasperini.com/blog/2007-sync-nokia-thunderbird-and-google-calendar/)

Now my life is in sync ;)

---

### Post by t0n1 on 2009-02-08
If only it worked for the new Nokia 5800.

---

### Post by Brigrat on 2009-02-09
OK i have read every thread here and think I have most of this worked out.  I have google feeding thunderbird my calendar, but have not proved that it is two way syncing yet.  Thunderbird seems to freeze and grey out sometimes but come back, is this when it is syncing?

I have the calendar working, now how about contacts...  Does this work the same way ie two way sync?????

---

### Post by nowhere@cox.net on 2009-02-25
I second this problem. It is driving me freaking CRAZY! I don't think I have ever gotten this frustrated by anything a computer has done to me. Every so often, like 60 - 90 seconds but sometime longer, TB/Lightning greys out and freezes/hangs for 30-60 seconds while it connects to either a calendar or mail. I can't tell what it's doing and it happens most frequently in the middle of trying to type an email during which time I can't do anything with TB/Lightning.

I have disabled every automatic connection thing in both I can find. This includes:
[LIST]
[*]Fetching mail
[*]Updating Calendars
[*]Checking for TB Updates
[*]Checking for Addon Updates
[/LIST]

ACK! While typing this, there was another TB grey out but since I'm mobile I must have had a momentary connection problem because TB just popped up several errors about not being able to auto save a draft! Maybe that is the last auto save crap I have to disable. 

I sure wish they would just put all the communication in another thread so it wouldn't hang up the entire program...

Anyone know of a real fix for this besides crippling the software?

Thanks!

UPDATE: Can't find any setting to disable autosave of drafts...

---

### Post by stuson on 2009-02-25
Check that you have not got auto compact set with a small limit,  I did and ur right it drives you nuts :)

---

### Post by nowhere@cox.net on 2009-02-26
I found the auto save for drafts and disabled that and increased the compact to 10MB instead of 1MB (for now). I don't think auto compact was the problem because it always asked me if I wanted to do it and I could say no.

We'll see how the auto save disable affects things. Hopefully we'll get an improvement soon...

---

### Post by Brigrat on 2009-02-28
I agree that it was frustrating beyond printable text in this forum.  I did finally get the evolution.gcaldaemon equation solved and now I can happily sync, home desktop, personal laptop and... my Black Jack2 thanks to a couple of other threads.  Isn't google great!!!!  I will try to compose all of my trials errors and solutions back here as soon as I can.  Any questions before I can get it posted feel free to PM me.

---

### Post by tmeier on 2009-03-02
I am running intrepid with Thunderbird 2.0.0.19 Lightning 0.9 and Provider for Google 0.5.1.

I am trying to setup up my remote calendar and get the following error.

[Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [calICalendar.uri]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: file:///home/tmeier/.mozilla-thunderbird/ha5r8yri.default/extensions/%7Be2fda1a4-762b-4020-b5ad-a41df1933103%7D/components/calItemModule.js -> file:///home/tmeier/.mozilla-thunderbird/ha5r8yri.default/extensions/%7Be2fda1a4-762b-4020-b5ad-a41df1933103%7D/js/calCalendarManager.js :: cmgr_createCalendar :: line 536"  data: no]

I have uninstalled Lightning and provider and then redownloaded and installed and still have the issue.  Any ideas.  Thanks.

Thomas

---

### Post by Brigrat on 2009-03-02
I tried everything with Thunderbird and would get errors about writing back to google and the grey outs, could not take the abuse anymore>>>> I went back to Evolution and the Gcaldaemon and walked it through very carefully and it works great.  You need to besure that you perform each step carefully and do not add any extra characters by mistake.  If you do it will just sit there and not update.

---

### Post by WinterHico on 2009-03-09
I have been using Thunderbird and Lightning happily for some time.  I recently purchased a new cell phone - motorola moto Z9.  Not a PDA, but has contacts & calendar etc.  I have been searching and trying different things - including upgrading to Ibex, to find a way to synchronize Sunbird/Lightning with my phone.  After I get that going I will look to get Thunderbird Address book synched too.

My attempts thus far center around opensync/multisync/synche with the various Sunbird and Moto plugins, but to no avail.

If someone has posted a working solution to this that I have missed in my searches, I apologize.

Thanks!

---

### Post by WinterHico on 2009-03-11
Update:
I have now shifted to trying gammu/wammu for syncing and also moto4linux/p2k.  The interface freezes up when trying to ID the phone, after it has sent the first AT commands.  I believe the phone is not responding.  More searching and testing to do...

---

### Post by vlke on 2009-07-16
> **Brigrat said:**
> I tried everything with Thunderbird and would get errors about writing back to google and the grey outs, could not take the abuse anymore>>>> I went back to Evolution and the Gcaldaemon and walked it through very carefully and it works great.  You need to besure that you perform each step carefully and do not add any extra characters by mistake.  If you do it will just sit there and not update.


I have been trying to get GCALDaemon to work with Thuderbird, I followed these instructions [http://gcaldaemon.sourceforge.net/usage.html#offline](http://gcaldaemon.sourceforge.net/usage.html#offline) which are for Sunbird. It partially works, i.e. I get my google calendar to sync once, it imports all the events with locations, descriptions, alarms ...etc. But when I put new event from my laptop, it doesn't show on the google site and vice versa. If I restart it, it brings it up updated on both but then it also turns on 50 alarm beeps for each event that has already passed. Also, should I go through trouble of restarting it everytime, it is not worth it.
I enable visualization for syncying, I can watch "sync" but info doesn't get updated. 

My google calendar syncs fine, the reason I want to use GCALDaemon is that I need to view the calendar when I am offline and be able to modify it.
Anybody has gotten GCALDaemon to work with Thunderbird 2.0???

Thanks in advance,
Marek

---

### Post by master_kernel on 2009-07-16
This helped a ton! Thanks!

---

### Post by vlke on 2009-07-20
> **master_kernel said:**
> This helped a ton! Thanks!
You mean you got it Thunderbird to work with GCAL ?

---

### Post by mukul_s on 2009-09-22
Guys,

Any progress made on this intergration/sync ??

---

### Post by paul sanz on 2009-11-02
Connecting google calendar to Thunderbird-lighting is amazingly easy and I have to say working brilliantly in a single user, but when used with in a enterprise environment where multiple users are actively syncing multiple calendars then serious security issues arise and one starts to ask himself :

Why do I have to make public my gmail account to those who i invite to share my calendars ? wouldn't it be better to offer an option to create a password for each calendar so that when sharing calendars one can keep his gmail account save from nosy/malicious users?

If someone knows of a workaround to solve this problem/bug reply to this post. 
If anyone else have found any other limited functions also add your comments to this post as its a shame this security risk/bug is making gmail calendar still a personal use rather than an enterprise option for small businesses.

Paul

---

### Post by cwhisperer on 2010-01-27
I am running ubuntu 9.10 with Thunderbird 2.0.0.19 Lightning 0.9 and Provider for Google 0.5.1. The menu item New Calendar is grayed out, so I can't click on it and I can't add a new calendar. Any help would be appreciated.

---

### Post by cygnis1 on 2010-01-27
Try installing libstdc++5 .  It helped me.

---

### Post by cwhisperer on 2010-01-28
> **cygnis1 said:**
> Try installing libstdc++5 .  It helped me.

I have libstdc++6 installed... but nothing changed... still not working :(

---

### Post by johnh10000 on 2010-03-01
> **caseywise said:**
> Great article, this helped me immensely!!  Thank you!!

Yeah helped me too.  now, as you seem to know about these things, on the "gadget" for a real website, how do i make show a private calendar?

Any ideas?

---

### Post by confused_user on 2010-06-17
oki', getting an error while trying to add the calender url

[Exception... "[xpconnect wrapped nsIURI]"  nsresult: "0x804b000a (NS_ERROR_MALFORMED_URI)" and then the link i provided which i have not included.

what are arwe you supposed to use as the address of the google calender?

---

### Post by vlke on 2010-06-17
> **confused_user said:**
> oki', getting an error while trying to add the calender url

[Exception... "[xpconnect wrapped nsIURI]"  nsresult: "0x804b000a (NS_ERROR_MALFORMED_URI)" and then the link i provided which i have not included.

what are arwe you supposed to use as the address of the google calender?


I don't know about your error message, but I use "private address" XML.

---

### Post by piggyslasher on 2010-09-19
There's a much more up to date guide here, complete with how to integrate it your desktop like Evolution.

[Replace Evolution with Thunderbird completely in Ubuntu]("http://www.techgarten.com/ubuntu/replace-evolution-thunderbird-completely-ubuntu/")

---

### Post by foxmajik on 2011-01-10
> **dmfield said:**
> 
[/INDENT]**Sync the PDA**[INDENT]The next step is to sync the Calendar with the PDA, this is done using the [GMobileSync]("http://rareedge.com/gmobilesync/") app for Windows Mobile or Smartphones. it requires .NET CF 2.0 which is available for download from the site, and provides not only read access to they Google Calendar, it also provides write access. This means as well as having PDA based access to your existing schedule, you can provide updates from your PDA to your calendar too. The application requires your login ID and password for the Google Calendar site. and works as far as i’m aware over both Wifi and GPRS networks, however i will confess, with UK prices as they are for Data over GPRS i’ve only tried Wifi. The Sync is a manual operation, and not automatic (yet)
[/INDENT] **Final Thoughts?**[INDENT] So what do we have? quite simply a free, Open source based Mail and personal schedulling system,  which can be accessed, over muliple platforms, Windows Mobile, Windows and Linux (not sure about OSX). Providing access to multiple mail accounts, using POP or IMAP. Read/Write Calendar access on  Desktop, Laptop or PDA.. There is also ToDo list functionality available. and all this can be accessed via a Web Interface. Now thats value for money.. Now if i could get this working with Open Xchange as well… bye bye M$ Exchange..
 [/INDENT]

Sorry for the necropost, I just wanted to let you all know that the above link has been hijacked and replaced with a malware page, so don't open the link.

---

### Post by astrobob.tk on 2011-01-22
> **dmfield said:**
> **The Email Client**[INDENT]The software I use is Thunderbird, Its my preferred Mail client, as i use both POP and IMAP based mail accounts, this mail client doesn’t however come with any built in calendar function, which is a reason, so many people berate it, and state that “calendar functionality is required before this app can move forward”. One of Thunderbirds strengths however, is, like its cousin Firefox, it works on a plugin system. That is, people have written third party modules, which can be used to enhance the functionality of Thunderbird. And I use 2 of these pluginfrom has an old version, Try downloading Lightening from 

 **Lightning Plugin for Thunderbird:**  [http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/)
** Google Calendar Provider:**  [https://addons.mozilla.org/en-US/thunderbird/addon/4631](https://addons.mozilla.org/en-US/thunderbird/addon/4631)



Quite simply, Lightning provides a calendar interface for Thunderbird, its part of the [Mozilla Sunbird]("http://www.mozilla.org/projects/calendar/") project, and helps provide the Schedule interface which standalone Thunderbird is missing.
[/INDENT]**Setup The Plugins**[INDENT]The magic here, however is the Provider for Google Calendar plugin, which, unlike just adding the necessary links to Thunderbird, to access Google Calendard, not only provides read access, it provides write access as well..
 Install both plugins, and restart Thunderbird, you will then be shown, a Calendar in the left pane, this calendar has 3 tabs Agenda, Todo and Calendars. To setup Google Calendar, click on the Calendar tab.
 Click on the New Button, in the Calendar Tab, and you will be given a choice, you need to select, On the Network. Click on Next, there is an option for Google Calendar, select this.
 In the Text bar under the Google Calendar you will need to enter the Link URL which allows you to write to your Account, you can find this, buy logging into the Google Calendar account you created earlier.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal1.JPG[/IMG]
 Create a new Calendar, or if you already have a celedar created, click on the down arrow next to the calendar. And click on Share this Calendar.
 You will be taken to a new page, where you will need to click on Calendar Details on the top of this page.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal2.JPG[/IMG]
 Then Select the XML button, next to the Private Address, this will allow you the read/write access to the calendar, if you need read only access, or wish to share calendards with read only access, use the XML button next to the Public Tab.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal3.JPG[/IMG]
 When you click on the XML button a URL will be displayed (i’ve edited the whole strin below for security reasons) Copy this URL , and paste it into the Thunderbird Text box, then click on Next.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal41.JPG[/IMG]
 Give the Calendar a name which you will use in Thunderbird to identify this calendar, and choose a colour, this is the colour which will identify your Google Calendar, if you are using multiple calendars. Then CLick on Next and then Finish.
 You will then see your calendar listed as available. you should now be able to add an event in either Thunderbird, or the wEb Interface, and both will update to show the events. You can set reminders, repeat events, and all the usual type of Schedule details.
[/INDENT] 
Thanks for this helpful thread. I was already using Thunderbird for my gmail account & it is great. I recently installed Lightning & Provider for Google Calendar as described by your thread & it also works great.

I have one little problem though, which I hope to be a solvable little problem.
I have several google calendars some of which are calendars shared from another account. All calendars seem to work but there's one particular one (sometimes others though not all) that doesn't seem to load. It gives a small sign next to the calendar & when the curser hovers over it, it says "The calendar (name) is momentarily not available". Sometimes all calendars don't display anything.

Moreover, the other imp thing I want to ask about is, shouldn't the google calendars be available offline with the Provider addon ? If so, its not the case with me.
I just tried thunderbird in offline mode & only one calendar displays in Lightning while others either don't display anything or state the same sign i mentioned above.

Why exactly is this going on & how can it be solved? 

thanks

---

### Post by crazy ivan on 2011-03-07
> **astrobob.tk said:**
> 
I just tried thunderbird in offline mode & only one calendar displays in Lightning while others either don't display anything or state the same sign i mentioned above.

Why exactly is this going on & how can it be solved? 
thanks

Hi, this feature, which is such a necessity, in fact seems to be missing. Usually in such a situation I use my android, since Gapps fully provides such synchronization functionality. 

A different option is to use the local Calendar and then change the event's "Calendar" property on restored connection.. Unfortunately so far there is no evident way to
* do this automatically (the local events "calendar-data/local.sqlite" are stored in SQlite, any ideas to connect that to google?)
* do this for more than one event at a time (lightning does not allow to change properties for selected events...).

Are there other calendar clients, that offer offline-editing + syncing with Gcalendar?

---

### Post by shrijith1 on 2011-03-11
[SIZE=-1][FONT=Helvetica, Arial, sans-serif]I am not sure if I have missed any post regarding this in this thread.

What I want is to publish my Local calendar to Gcal         automatically. I dont want to manually export/import ics files         everyday to sync my calendar with Gcal. I can see that there is         a publish option and it asks for a weblink - What do I have to         give there?

[/FONT][/SIZE][SIZE=-1][FONT=Helvetica, Arial, sans-serif]I need all these to get the local calendar in my Nokia N900         (Linux phone) - Its bad that Nokia didn't think of a Linux PC         Suite for this phone :([/FONT][/SIZE]

---

