---
title: "HOWTO: Transfer Emails Between Outlook 2007 (Windows) and Thunderbird (Linux)"
date: 2009-07-01
forum: Outdated Tutorials &amp; Tips
---

### Post by The-Don on 2009-07-01
Howdy,
As I've recently switched from "Windows Vista Business" (legal) to "Ubuntu 9.04" I had to search all over the Internets with multiple tutorials on preserving my emails. Here's my amalgamation of those in an easy way. Simply because, they're all using command lines and confused the hell out of me!

[SIZE=3]**_SPECIAL BONUS NOTE: There are NO command lines to type/memorise_**[/SIZE]

_**[COLOR=#9932cc]Email Transfer[/COLOR]**_
**Source Operating System (O/S):** Microsoft Windows Vista Business
**Source Email Program:** Microsoft Outlook 2007
**Destination Operating System (O/S):** Linux Ubuntu 9.04
**Destination Email Program:** Mozilla Thunderbird 2.0.0.21

**_[COLOR=#9932cc]Outlook Note for Personal Folder File (.pst)[/COLOR]_**
Now. I usually perform a backup of my Outlook 2007 emails every now and again by going to "File > Import and Export > Export to a File > Personal Folder File (.pst)". This is great, everything's backed up. However, this .pst file is a propietary format *(in other words, Microsoft's closed source file system to encode the data within the .pst file)*. So...this will NOT work with Thunderbird as Mozilla cannot 'read' the structure of the data file. I'm not bashing .pst because it's basic security - which is understandable.

**_[COLOR=#9932cc]There Are Two Ways of Doing This[/COLOR]_**
1.) You haven't wiped your Windows system as yet.
2.) You've already got the .pst file from above, wiped your Windows system and have Ubuntu or Linux installed.

_**[COLOR=#4169e1]METHOD ONE: BACKING UP EMAILS[/COLOR]**_
**_On Your Windows Box_**
[LIST]
[*]So, you're on your Windows box with Outlook 2007 installed *(I'm guessing 2003/2010 works this way too)*.
[*]Install Thunderbird on your Windows Box
[*]Inside Thunderbird go to "Tools > Import > Outlook"
[*]This will import all your emails over to Thunderbird (Thunderbird can read Thunderbird regardless of OS).
[*]Inside Thunderbird "Right-Click Inbox > Copy Folder Location"
[*]Press "START+R" aka "Windows Key > Run". Paste the folder location, mine is **"mailbox:/C|/Users/DjmUK/AppData/Roaming/Thunderbird/Profiles/q8btmcj9.default/Mail/Local Folders/Outlook Mail.sbd/Inbox"** * DON'T PRESS ENTER * (well, it won't work anyway lol)
[*]Read that location...manually converted in my head it reads "**C:\Users\DjmUK\AppData\Roaming\Thunderbird\Profiles\q8btmcj9.default\Mail\Local Folders\Outlook Mail.sbd**".
[*]Ideally, just navigate from folder to folder.
[*]There's your emails, inside the 'Inbox.sbd' are your custom folders within the Inbox.
[*]Select all the files and copy them onto a flash disc for example.
[/LIST]
[IMG]http://img.photobucket.com/albums/v335/DjmUK/01.jpg[/IMG]

_**[COLOR=#4169e1]METHOD TWO: BACKING UP EMAILS[/COLOR]**_
**_On Your Linux Box_**
[LIST]
[*]Install VirtualBox (sudo aptitude install virtualbox)
[*]Install Windows into a VirtualBox
[*]Install Outlook 2007 into that Windows VirtualBox
[*]Install Thunderbird on that Windows VirtualBox
[*]Inside Outlook 2007, you will need to import the .pst file. "File > Import and Export > Import from another program or file > Personal Folder File (.pst) > Browse etc."
[*]Inside Thunderbird go to "Tools > Import > Outlook"
[*]Inside Thunderbird "Right-Click Inbox > Copy Folder Location"
[*]Press "START+R" aka "Windows Key > Run". Paste the folder location, mine is **"mailbox:/C|/Users/DjmUK/AppData/Roaming/Thunderbird/Profiles/q8btmcj9.default/Mail/Local Folders/Outlook Mail.sbd/Inbox"** * DON'T PRESS ENTER * (well, it won't work anyway lol)
[*]Read that location...manually converted in my head it reads "**C:\Users\DjmUK\AppData\Roaming\Thunderbird\Profiles\q8btmcj9.default\Mail\Local Folders\Outlook Mail.sbd**".
[*]Ideally, just navigate from folder to folder.
[*]There's your emails, inside the 'Inbox.sbd' are your custom folders within the Inbox.
[*][COLOR=#ff8c00]Alrighty then, if you don't know how to mount flash drives then there's another way. What we're going to do now is to copy the emails from Windows to Linux.[/COLOR]
[*]Inside VirtualBox go to "Devices > Shared Folders > + Button (Add New Shared Folder" In the "Folder Path Box > Select the Dropdown List and Choose 'Other' > Select Desktop or Wherever you Like".
[IMG]http://img.photobucket.com/albums/v335/DjmUK/02.png[/IMG]
[*]Press "OK > OK".
[*]Inside Windows Press "START+R" aka "Windows Key > Run" and type in **net use x: \\vboxsvr\Desktop** *(where Desktop is the name of the new shared folder)*.
[IMG]http://img.photobucket.com/albums/v335/DjmUK/03.jpg[/IMG]
[*]Go to My Computer and there's your new folder.
[IMG]http://img.photobucket.com/albums/v335/DjmUK/04.jpg[/IMG]
[*]Select all the email files and copy them into that folder (X:\).
[/LIST]

_**[COLOR=#ff8c00]NOW TO IMPORT INTO LINUX THUNDERBIRD[/COLOR]**_
**_On Your Linux Box_**
[LIST]
[*]The moment you've been waiting for..!
[*]Open up Thunderbird
[*]"Right-Click the Inbox > Copy File Location". Mine says "**mailbox:/home/djmuk/.mozilla-thunderbird/ihikkq2l.default/Mail/Local Folders/Inbox"**
[*]Read that location...manually converted in my head it reads "**/home/djmuk/.mozilla-thunderbird/ihikkq2l.default/Mail/Local Folders/**"
[*]* Remove the text "mailbox" at the beginning and the text "Inbox" at the end *
[*]Navigate to the above, if you can't see some of the folders (eg, **.mozilla-thunderbird** then go to "View > Show Hidden Files (CTRL+H)").
[*]There we go, copy/paste and you're sorted!
[/LIST]

[IMG]http://img.photobucket.com/albums/v335/DjmUK/05.png[/IMG]

---

### Post by jpeddicord on 2009-07-07
Approved, thank you for your tutorial contribution. :)

---

