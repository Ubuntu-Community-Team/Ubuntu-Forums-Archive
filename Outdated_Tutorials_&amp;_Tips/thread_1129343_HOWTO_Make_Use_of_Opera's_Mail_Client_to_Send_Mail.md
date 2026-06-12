---
title: "HOWTO Make Use of Opera's Mail Client to Send Mails From Within Open Office"
date: 2009-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by ubi-wan on 2009-04-18
[SIZE="5"]Introduction[/SIZE]
This howto is about 3 different tips related to Open Office, Opera, and their combination with view to achieve the goal above:
[LIST=1][*]Using oofromtemplate to start up Open Office directly with the exact functionality you want;[*]Employing Opera or any other unsupported mail client to send documents as mail attachments from within Open Office;[*]Making Opera the default mail client of the user interface (Gnome).
[/LIST]

[SIZE="5"]Your Office Shortcut[/SIZE]
There is an interesting menu item belonging to Open Office which is hidden for some reason in Ubuntu:[INDENT]Applications -> Office -> OpenOffice.org.[/INDENT]
This is the equivalent of Microsoft's office shortcut, offering both the functions of "new office document" and "open an office document" together with a complete template and address book management in one place. In other words, it is the most intuitive way to start up Open Office.
In order to put it within reach, right-click somewhere on your desktop, and create a launcher:
[LIST][*]**Name**:		OpenOffice.org[*]**Command**:	oofromtemplate[*]**Comment**:	Office Suite[*]***Icon***:		/usr/share/icons/hicolor/48x48/applications/ooo-gulls.png
[/LIST]
You can either leave this launcher on the desktop, or better, drag it onto the menu panel on the top. You could also make up such a launcher in Avant Window Navigator (i.e. its manager) or any program or file launcher of your choice.

[SIZE="5"]Send Documents With Any Mail Client You Want[/SIZE]
Being able to send documents directly from within Open Office is not only comfortable, but also increasingly important as Microsoft finally decided to include native support for Open Documents into Office 2007 (see "[Microsoft se sube al carro de OpenDocument]("http://www.imatica.org/bloges/2009/04/160435022009.html")").
All you have to do is to tell Open Office which mail client you happen to use. You do so by naming it in
[INDENT]	Tools -> Options -> Internet -> E-mail -> E-mail program.[/INDENT]
Unfortunately, if you enter "opera" there, you're likely to see the following error message: OpenOffice.org was unable to find a working e-mail configuration...
[INDENT][ATTACH]110219[/ATTACH][/INDENT]
This is also true for any other mail client not supported by Open Office.

Never mind; just let or make that option field empty (this is obligatory!). Download the attached script, open up a terminal, and change to your download directory (let's assume it's called downloads):
```
cd downloads
sudo mkdir --parents /usr/local/bin
sudo cp oofromtemplate.sh /usr/local/bin/oofromtemplate
sudo chmod +x /usr/local/bin/oofromtemplate
```
If you do not want to use oofromtemplate, you could replace it in the commands above by, say, oowriter. In this case though, the send mail function would be available in text documents only.

However, as Opera doesn't handle attachments this way, the name of the file will appear in the "To" field of the message. Hence, you'll have to cut it from here (mark the whole line by triple-clicking on it, then Ctrl+X or right-click) and manually transfer it into the "Attach" window (with Ctrl+V). Then, you can proceed with the mail as usual.

[SIZE="3"]_Note_[/SIZE]: If you use another non-standard mail client, you have to adapt the Opera command line in the script to your needs.

[SIZE="5"]Opera as Default Mail Client[/SIZE]
You should now change the Mail Reader in
[INDENT]System -> Preferences -> Preferred Applications[/INDENT]
to "oofromtemplate %s".

The result of this exercise is being able to start Opera's mail composer by typing mailto:recipient@his_email_server in the Run Application window (called by Alt+F2) or in a terminal. In the latter case, the mailto address must be preceded by "gnome-open ".

The mailto protocol will also work in other applications which can call it like Rubrica, Sunbird, etc. Moreover, it allows to "send to..." any document with Opera from the desktop or a folder by right-clicking on it.

---

### Post by rahuroon on 2010-03-03
it helped. Thanks.

---

### Post by ubi-wan on 2010-03-04
Thanks for your feedback, Rahuroon. Welcome in the very exclusive (see the download counter above) club of

*Hardy, Intrepid (etc.) Linux Users Using Opera Together With Open Office on Ubuntu* :p

---

### Post by ssuuddoo on 2010-08-20
I dunno, what am I doing wrong, but sending documents from OOo as email attachmetns does not work 4 me. It does not do anything by clicking the "Document as email" button. 
The opera is used as the default email app. (in gnome settings I wrote "opera %s" and at least it opens opera whem clicking an email link outside of opera, but doesnt attach the selected file as an attachment)

The "email" field in OOo Internet settings I've left empty and ran the script as U wrote, tried to run ooo with "oofromtemplate" or with the ooo menu items, but didn't help.

any suggestions?

thnx

---

### Post by ubi-wan on 2010-08-24
The trick is to call opera by means of the script provided in order to trigger its mailto function. 

Hence, gnome's own settings for the mail client need to be changed to "ootemplate %s" (see above under "Opera as Default Mail Client").

---

### Post by dsteele on 2010-11-13
The gnome-gmail package includes a shim that automatically configures Open Office to use the default GNOME mail program.

---

### Post by ubi-wan on 2010-11-17
> **dsteele said:**
> The gnome-gmail package includes a shim that automatically configures Open Office to use the default GNOME mail program.

The point here is that opera *isn't* a standard mail program :roll:

---

### Post by ubi-wan on 2011-07-18
Opera has changed its command line, so you'll need a new oofromtemplate.sh. This one works with the following system components:
[LIST]
[*]Ubuntu 10.04 LTS (Lucid Lynx);
[*]Opera 11.50;
[*]OpenOffice.org 3.2.0;
[*]Gnome 2.30.2.
[/LIST]

Here you go :guitar:

---

