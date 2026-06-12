---
title: "How to install sylpheed, one of the best desktop email clients for Linux"
date: 2006-09-16
forum: Outdated Tutorials &amp; Tips
---

### Post by rosslaird on 2006-09-16
If, like me, you use IMAP instead of POP for your mail, you may have experienced some difficulty with the popular email clients (kmail, evolution, thunderbird). And you may also have had difficulty with the lack of customization, or poor spam filtering, or lack of features of some of these email clients. You may even have experimented with mutt, which is a wonderful email client but which works from the command line only.

Sylpheed, a lesser-known email client (given its features, I can't figure out how it remains so obscure), is like mutt for the desktop: a gtk application with outstanding functionality and features.

If you want to try it out, here's how you go about getting the most recent version and all the fancy extras:

1. Open a terminal. Download and register the signing key for the sylpheed sources:

```
wget http://colino.net/colin.publickey
sudo apt-key add colin.publickey
```

2. Change your /etc/apt/sources.list to include the sylpheed sources (you can use gedit or any text application for this; I will use nano here, since we're already in the terminal):

```
sudo nano /etc/apt/sources.list
```

Go to the end of the file (page down a few times) and add this:

```
#Sylpheed sources
deb http://www.sylpheed-claws.net/ubuntu/dapper/ ./

```

Save the file (ctl-o), and exit nano (ctl-x).

3. Then update your sources:

```
sudo apt-get update
```

4. Install sylpheed:

```
sudo apt-get install sylpheed-claws-gtk2
```

This will pull down whatever is necessary to install the basic application.

5. Install extras. Sylpheed has very many extensions and plugins. Take a look at them all by doing this:

```
sudo apt-cache search sylpheed-claws-gtk2
```

Take a look at this list (note the spamassassin plugin, the trayicon plugin, the html viewer, etc.). You can get quite a few of the plugins by installing the plugins packages:

```
sudo apt-get install sylpheed-claws-gtk2-plugins sylpheed-claws-gtk2-extra-plugins
```

Or, you can get them individually, by specifying them on the apt-get command line, eg:

```
sudo apt-get install sylpheed-claws-gtk2-spamassassin
```

6. Open sylpheed. You will find it (in gnome) under Applications --> Internet --> Sylpheed Claws gtk2

Spend a few minutes looking around and setting things up. If you like, you can customize the interface (as well as many other things) to use various themes. I use the tango theme (TangoClaws). The complete list is here:

[http://www.sylpheed-claws.net/themes.php]("http://www.sylpheed-claws.net/themes.php")

To use a theme, download it, unpack it, and navigate to the unpacked directory in sylpheed under Configuration --> Preferences --> Themes. Install the theme, then select "Use this".

You may also be interested in various scripts for use with sylpheed (address conversion etc.):

[http://www.sylpheed-claws.net/tools.php]("http://www.sylpheed-claws.net/tools.php")

The feature set of sylpheed is very rich, flexible, and functional. You might find that it becomes a little addictive...

Enjoy.

---

### Post by lagagnon on 2006-09-17
And what Ross failed to point out but alluded to in his reference to mutt is that Sylpheed is blindingly fast and uses a tenth of the resources that Thunderbird, Evolution and other heavyweight email programs use.

Boot it up and you will think you are using a command line program - it is that fast. I love it.

---

### Post by bmt on 2006-11-16
I came across Sylpheed-Claws as a refugee from Evolution (troubles with multiple POP/SMTP accounts and Palm sync).  It's refreshing to get back to a mail client instead of an integrated suite, for speed and efficiency.

---

### Post by rollps on 2006-11-18
Hi,

just discovered sylpheed and loving it so far... so fast :)

BUT it stores mails in a folder "accountname" right in the /home directory...

and I don't want to see this folder all the time ! I mean it's like a config stuff so it should be hidden basically.

and I can't find a way to change this setting, though I'm sure it's possible, isn't it ??

thanks

---

### Post by tturrisi on 2006-11-18
Sylpheed & Sylpheed-Claws are in the Ubuntu repositories already, been using Claws for years cause it has more features than its parent.

---

### Post by rollps on 2006-11-18
ok I found the way to move the default directory where mails are stored :

-edit the file ~/.sylpheed-claws/folderlist.xml using gedit
-change the path to where you want it
-and move your ex folder to the new place if you want to keep your old mails
-that's it !

---

### Post by berserker on 2006-11-18
> **rollps said:**
> ok I found the way to move the default directory where mails are stored :

-edit the file ~/.sylpheed-claws/folderlist.xml using gedit
-change the path to where you want it
-and move your ex folder to the new place if you want to keep your old mails
-that's it !

Thanks!  That was bothering me, too!

Anyone know how to get S/MIME working?  I've installed the plugin but it complains that it can't find the secret key.  I've searched the web trying to find out how to install my digital certificate in sylpheed-claws to no avail.

---

### Post by bmt on 2006-12-02
> **tturrisi said:**
> Sylpheed & Sylpheed-Claws are in the Ubuntu repositories already ...
Well, *very old* versions are in the repositories, with little chance of them being brought up to date for existing Ubuntu releases.

---

### Post by Sebastral on 2006-12-20
Does anyone know how to do thunderbirds 'fetch headers only' option in sylpheed?

---

### Post by Sebastral on 2006-12-22
Sources for edgy;

#Sylpheed sources
deb [http://www.claws-mail.org/ubuntu/edgy/](http://www.claws-mail.org/ubuntu/edgy/) ./

---

### Post by dehru on 2007-02-12
> **berserker said:**
> Anyone know how to get S/MIME working?  I've installed the plugin but it complains that it can't find the secret key.  I've searched the web trying to find out how to install my digital certificate in sylpheed-claws to no avail.
Still having problem with S/MIME?

---

### Post by berserker on 2007-02-12
> **dehru said:**
> Still having problem with S/MIME?

Yes.  I got to the point where I could send signed and encrypted e-mail using S/MIME but S/MIME signed e-mail I received had invalid signatures and encrypted e-mail could not be read.

I finally gave up and went with kmail where I don't have any S/MIME problems.

---

### Post by colinleroy on 2007-02-13
> **berserker said:**
> Yes.  I got to the point where I could send signed and encrypted e-mail using S/MIME but S/MIME signed e-mail I received had invalid signatures and encrypted e-mail could not be read.

I finally gave up and went with kmail where I don't have any S/MIME problems.

Yes, S/MIME had some rough edges. It works now quite well as of version 2.7.2, with some manual configuration of the GpgSM backend. 

A user wrote a quite complete howto at [http://www.claws-mail.org/faq/index.php/S/MIME_howto](http://www.claws-mail.org/faq/index.php/S/MIME_howto)

---

### Post by berserker on 2007-02-13
> **colinleroy said:**
> Yes, S/MIME had some rough edges. It works now quite well as of version 2.7.2, with some manual configuration of the GpgSM backend. 

A user wrote a quite complete howto at [http://www.claws-mail.org/faq/index.php/S/MIME_howto](http://www.claws-mail.org/faq/index.php/S/MIME_howto)

Thank you.  Just tried it again and it works quite well now.

---

### Post by Nikron on 2007-02-13
I love claws, so much faster than thunderbird.  However, do you know how I can start it as the tray icon?

---

### Post by berserker on 2007-02-14
Trying to set up claws-mail to check my system mail (/var/mail/berserker).  

I try to create a new account using "local mbox" but when I point to a folder for the default inbox and click "Apply" or "OK" I receive the following error message:  "The default inbox doesn't exist".

It doesn't matter if I point to an existing folder or create a new one as the default inbox.

Any ideas how I can get claws-mail to check system mail?

TIA

---

### Post by colinleroy on 2007-02-19
> **Nikron said:**
> I love claws, so much faster than thunderbird.  However, do you know how I can start it as the tray icon?

There will be a way to do that in the upcoming 2.8.0 release, planned for next week. :)

---

### Post by Kuoi on 2007-02-23
After doing everything like told at this threat , I'm still have version 2.5 RC3 .

I'm using Edgy 6.10 , after editing the sources list with the edgy command , i have an error > Permanently delete package failed ( as far as I remember ) after the Sylpheed download.

What can I do to fix this ?

Kuoi

---

### Post by Kuoi on 2007-02-23
Tried a second time , and now I don't have the 301 error , but if I do > sudo apt-get install sylpheed-claws-gtk2 it says , it is already the latest version .

I still have version 2.5 though .

Kuoi

---

### Post by colinleroy on 2007-02-24
> **Kuoi said:**
> Tried a second time , and now I don't have the 301 error , but if I do  it says , it is already the latest version .

I still have version 2.5 though .


It's because the packages have been renamed and there are no transition packages yet. You have to remove your sylpheed-claws-gtk2 packages and install claws-mail packages:

claws-mail
claws-mail-i18n
claws-mail-pgpmime
...

---

### Post by Ago12 on 2007-02-24
It looks very interesting, since I don't use a tenth of Evolution's capacties and I've switched to xfce.

But, do you know if there is a way to import Evoltion's settings and mails?

Thanks :)

---

### Post by Kuoi on 2007-02-24
> **colinleroy said:**
> It's because the packages have been renamed and there are no transition packages yet. You have to remove your sylpheed-claws-gtk2 packages and install claws-mail packages:

claws-mail
claws-mail-i18n
claws-mail-pgpmime
...

Thanks !
Works like a charm!

Why can't they make a deb file who knows about the rename , but oh well , we still have this forum !

Thanks very much , Kuoi

---

### Post by colinleroy on 2007-02-24
> **Ago12 said:**
> It looks very interesting, since I don't use a tenth of Evolution's capacties and I've switched to xfce.

But, do you know if there is a way to import Evoltion's settings and mails?

Thanks :)

Mails can be exported to mbox from evolution, and imported by Claws; addressbook should be exportable too, I'm not sure. For settings you'll have to recreate them.

---

### Post by colinleroy on 2007-02-24
> **Kuoi said:**
> Thanks !
Works like a charm!

Why can't they make a deb file who knows about the rename , but oh well , we still have this forum !

Thanks very much , Kuoi

It's me who did these packages :) 
They don't provide meta-packages for migrating from sylpheed-claws-gtk2 to claws-mail, because I don't know how to do these; but our Debian packager has done that, so at the next release my packages will provide an easy migration path :)

---

### Post by Ago12 on 2007-02-24
> **colinleroy said:**
> Mails can be exported to mbox from evolution, and imported by Claws; addressbook should be exportable too, I'm not sure. For settings you'll have to recreate them.

Thanks :)

---

### Post by Kuoi on 2007-02-24
> **colinleroy said:**
> It's me who did these packages :) 
They don't provide meta-packages for migrating from sylpheed-claws-gtk2 to claws-mail, because I don't know how to do these; but our Debian packager has done that, so at the next release my packages will provide an easy migration path :)

You did a great job , and your deb file helped me a lot.

I just didn't know I had to 'uninstall' the gtk2 version in Synaptic  -NOT full uninstall , or you'll loose your settings and maybe mails ( didn't wanted to test this ;-) - , but then I only had to select Claws mail 2.7.2 , and all works well.

The only negative at Claws (imo) is the address book integration.
I can't see all my contacts like in Outlook Express for example under the mailboxes , so I have only to select 1 to mail to that contact .
But for sure Claws is the best and only client one will need on Linux ( Ubuntu ) !!

Thanks , Kuoi

---

### Post by berserker on 2007-02-28
> **berserker said:**
> Trying to set up claws-mail to check my system mail (/var/mail/berserker).  

I try to create a new account using "local mbox" but when I point to a folder for the default inbox and click "Apply" or "OK" I receive the following error message:  "The default inbox doesn't exist".

It doesn't matter if I point to an existing folder or create a new one as the default inbox.

Any ideas how I can get claws-mail to check system mail?

TIA

The latest version of claws-mail (2.8.0) fixes this problem!

---

### Post by dlpfmVfH on 2007-03-05
[FONT=Verdana][SIZE=3]Now the new improved sylpheed claws gtk2 :
Claws-mail for feisty also

[/SIZE][/FONT][FONT=Verdana][SIZE=3] 		  		Unofficial Ubuntu packages			
[www.claws-mail.org]("http://www.claws-mail.org/ubuntu/")Add this to /etc/apt/sources.list:
			      For 6.06 Dapper: 
deb [http://www.claws-mail.org/ubuntu/dapper/](http://www.claws-mail.org/ubuntu/dapper/) ./
			      For 6.10 Edgy: 
deb [http://www.claws-mail.org/ubuntu/edgy/](http://www.claws-mail.org/ubuntu/edgy/) ./
			      For 7.04 Feisty: 
deb [http://www.claws-mail.org/ubuntu/feisty/](http://www.claws-mail.org/ubuntu/feisty/) ./
[/SIZE][/FONT]

---

### Post by shaviro on 2007-03-07
I have been unable to install claws-mail on edgy/gnome. I added the claws-mail repository as instructed, updated apt-get, etc.; but when I try to install claws-mail (either through apt-get, or through Synaptic Package Manager), I get the error message:

claws-mail:
 Depends: libetpan11 (>=0.49-1) but it is not installable

Synaptics tells me that I have libetpan6 (0.45-2) and libetpan8 (0.46.2) already installed, but there is no mention of any version of libetpan that is >=0.49-1. 

Can anyone give me help on this? Since I have discontents with both Evolution and Thunderbird, I would like to give claws-mail a try. 

thanks

---

### Post by colinleroy on 2007-03-07
> **shaviro said:**
> claws-mail:
 Depends: libetpan11 (>=0.49-1) but it is not installable


Sorry, my bad. Fixed!

---

### Post by shaviro on 2007-03-07
Thanks, installs now.

---

### Post by LeeU on 2007-03-29
I have Ubuntu 6.06 and the only thing I was able to download was Sylpheed-Claws 2.1.1. I can't get it to update any further. Any idea?

---

### Post by QwUo173Hy on 2007-04-30
I'm looking at the packages in the Edgy repository. Do I install the claws-mail package or the sylpheed-claws-gtk2 package?

---

### Post by kozimodo on 2007-04-30
Any AMD64 feisty repositories out there?

---

### Post by berserker on 2007-04-30
> **jarlath said:**
> I'm looking at the packages in the Edgy repository. Do I install the claws-mail package or the sylpheed-claws-gtk2 package?

Sylpheed-claws is now Claws-mail so install the claws-mail packages.

---

### Post by QwUo173Hy on 2007-04-30
Thanks berserker. It's up and running!

---

### Post by Lucifiel on 2007-05-08
(modified from threadstarter's instructions)

To everyone who's trying to install this in Feisty, try this:
> 
wget [http://colino.net/colin.publickey](http://colino.net/colin.publickey)
sudo apt-key add colin.publickey

In sources.list, list
> #Sylpheed sources
deb [http://www.claws-mail.org/ubuntu/feisty](http://www.claws-mail.org/ubuntu/feisty) ./ 

Then run
> sudo apt-get update

And run 
> 
sudo apt-get install claws-mail



Then

> sudo apt-get install claws-mail-plugins claws-mail-extra-plugins

And yes, Slypheed claws is incredibly fast. It was able to load around 4000 emails without any problems. No lag, no mouse freezing, nothing! Just pure, hardcore speed!

---

### Post by pinguin on 2007-05-08
**Hi colinleroy  **
can You help me?
I have Feisty amd64 so I can't install your packages
So I'm trying to compile myself claws-mail 2.9.1, but I have errors in compiling and/or installing
I run
./configure --disable-libetpan --disable-clamav-plugin --disable-ldap --disable-ipv6
and it seems work, because I get:
```
......
claws-mail 2.9.1

JPilot        : no
LDAP          : no
OpenSSL       : yes
iconv         : yes
compface      : yes
IPv6          : no
GNU/aspell    : yes
IMAP4         : no
Crash dialog  : no
Libgnomeprint : no
LibSM         : yes
Manual        : yes
Plugins       : dillo-viewer pgpinline pgpmime pgpcore bogofilter spamassassin trayicon 
Maemo  build  : no
Config dir    : .claws-mail

The binary will be installed in /usr/local/bin

Configure finished, type 'make' to build.
```

then I run make and it works without errors

when I run sudo checkinstall, I have these errors:
```
....
Making install in plugins
make[3]: Entering directory `/home/maurizio/claws-mail-2.9.1/src/plugins'
Making install in spamassassin
make[4]: Entering directory `/home/maurizio/claws-mail-2.9.1/src/plugins/spamassassin'
make[5]: Entering directory `/home/maurizio/claws-mail-2.9.1/src/plugins/spamassassin'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/claws-mail/plugins" || /bin/mkdir -p "/usr/local/lib/claws-mail/plugins"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'spamassassin.la' '/usr/local/lib/claws-mail/plugins/spamassassin.la'
/usr/bin/install -c .libs/spamassassin.so /usr/local/lib/claws-mail/plugins/spamassassin.so
/usr/bin/install: setting permissions for `/usr/local/lib/claws-mail/plugins/spamassassin.so': No such file or directory
/usr/bin/install -c .libs/spamassassin.lai /usr/local/lib/claws-mail/plugins/spamassassin.la
/usr/bin/install: setting permissions for `/usr/local/lib/claws-mail/plugins/spamassassin.la': No such file or directory
/usr/bin/install -c .libs/spamassassin.a /usr/local/lib/claws-mail/plugins/spamassassin.a
/usr/bin/install: setting permissions for `/usr/local/lib/claws-mail/plugins/spamassassin.a': No such file or directory
chmod 644 /usr/local/lib/claws-mail/plugins/spamassassin.a
ranlib /usr/local/lib/claws-mail/plugins/spamassassin.a
ranlib: could not create temporary file whilst writing archive: No more archived files
make[5]: *** [install-pluginLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/maurizio/claws-mail-2.9.1/src/plugins/spamassassin'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/maurizio/claws-mail-2.9.1/src/plugins/spamassassin'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/maurizio/claws-mail-2.9.1/src/plugins'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/maurizio/claws-mail-2.9.1/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/maurizio/claws-mail-2.9.1/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```
What's wrong? Can you help me sending step by step what have I to do to compile claws-mail 2.9.1?

I also tryed version 2.6.1 that is in amd64 feisty repos, but when I click on "load images" (gtkhtml2 viewer plugin?) button program crashes and exits
hope you can help me, 
thanks, ciao

---

### Post by Lucifiel on 2007-05-10
After trying Slypeed for about 2 days or so, I find that :

a) yes, Claws mail is blazing fast. It can contain thousands of emails within a folder without any lag. It is also fantastic at loading emails: no lag too. 

b) the default font settings are very small and that might have an effect on the font anti-aliasing too. In comparison with Thunderbird, the fonts looked just dreadful and really hurt my eyes. Because the font hinting settings seem to inherited from the settings in Feisty Fawn(or any other version of Ubuntu), this is an issue better resolved within Ubuntu. 

To resolve the issue of fonts with less than optimal anti-aliasing/hinting, you're advised to increase the font size by launching "Preferences" under "Configuration----> Preferences". 

Then, under Display, select "Font" and increase it. The fonts will look a lot better and will be more easy on your eyes. For me, anything under Font size 11 looked pretty difficult to see while this might vary for your different systems. 

c) The GUI frontend needs more polishing. It just looks pretty dull and the icons are reminiscent of some mid 90s program. The additional themes are pretty boring too, except for a few. 

I just hope more artistically-inclined users will step forward to create more themes for Claws-mail.

d) One needs to load in plugins just to get Sylpheed to recognise spam email and to load html within email. But the email client doesn't always switch into "view html" mode correctly. Nor does it always select the correct "view text"(text/rfc22 or even text/plain) modes correctly. 

e) It is disappointing that to do a more precise search through your emails, one needs to use syntax and not just select certain buttons. I have RSI so I try to type as little as possible. 

Example of syntax would be: "subject matchcase "chickenmomma" | from matchcase "chickenmomma" | body_part matchcase "chickenmomma" | to "matchcase chickenmomma" (Many thanks to the kind fellows at #claws in Freenode who helped me work this out.)

And because the search feature uses filters, you need to click on each folder and every sub-folder in order for the search to start.  

f) In order to auto-complete email addresses, you will need to have already added the email address to your Address Book. Then, type the first letter of the email address and press "Tab" key. My views on this are pretty mixed. While it's excellent to have another way of auto-completing email addresses, what if you don't remember the person's address and can't find the email so you can add it to your Address Book?  

g) I have not tried filters or many of the other features yet but have found that customising the client is usually quite easy. 

I guess I will continue to evaluate this program for a few more days before I decide whether to switch back to Thunderbird or to use another email client. After all, if it doesn't really cater to many of my basic needs, then I see no point in continuing to using it. :)

---

### Post by jaywee on 2007-05-14
I&#8216;ve found a easy-to-use email client so long, even thunderbird can't meet me&#65281; Then I tried this software, precisely what I want!! the only bad thing is I can't visit it's homepage@

---

### Post by hexo1125 on 2007-05-14
> **jaywee said:**
> I‘ve found a easy-to-use email client so long, even thunderbird can't meet me&#65281; Then I tried this software, precisely what I want!! the only bad thing is I can't visit it's homepage@

just google "claws mail" and you should find their site... their site is up, as of this posting moment... not sure about at the time u posted

---

### Post by derekguy on 2007-05-15
Legend, thankyou so much for this how to. I can confirm it works for me Feisty Fawn running on a Compaq laptop. I will look into the great plugins soon I think but setup is really easy and yiu are right. So fast.

---

### Post by Lucifiel on 2007-05-17
Hmmm... Spam Assassin seems to have problems filtering my emails?

It says something about "spamd" and possibly "localhost"? So, I looked at my SpamAssassin plugin settings. And from the Claws-mail Plugins FAQ, it is recommended to use localhost and set at 783. And those are my settings. So, is there something else I need to configure?

Note: I don't have any other spam plugins loaded.

---

### Post by Sebastral on 2007-05-20
I use the deb [http://www.claws-mail.org/ubuntu/feisty/](http://www.claws-mail.org/ubuntu/feisty/) ./ repository but I got the gpg error and found this solution;

[INDENT]>W: GPG error: [http://www.claws-mail.org](http://www.claws-mail.org) ./ Release: Following
> signatures are not konntecheckable because the public key isn't
> available: NO_PUBKEY 4B73A55696D94189

ah, that's it. Get my key:

wget [http://colino.net/colin.publickey](http://colino.net/colin.publickey)

install it:

sudo apt-key add colin.publickey

And run apt-get update again. That should fix it! [/INDENT]
I love claws-mail. Only auto-wrapping isn't perfect. If I'm composing a message and I decide to make a new paragraph of a sentence this happens;

[INDENT]I have
some very interesting books on[/INDENT]
and I have to fix the layout manually. Is there a better way to compose messages?

---

### Post by colinleroy on 2007-05-24
> **Lucifiel said:**
> Hmmm... Spam Assassin seems to have problems filtering my emails?

It says something about "spamd" and possibly "localhost"? So, I looked at my SpamAssassin plugin settings. And from the Claws-mail Plugins FAQ, it is recommended to use localhost and set at 783. And those are my settings. So, is there something else I need to configure?

Note: I don't have any other spam plugins loaded.

You need to install and start the spamd service:

$ sudo apt-get install spamassassin
$ sudo vi /etc/default/spamassassin -- change ENABLED to 1,and add "-i 127.0.0.1" without the quotes in the OPTIONS line
$ sudo /etc/init.d/spamassassin start

Then, Claws Mail's Spamassassin plugin will be able to communicate with the daemon.
Alternatively, you may use the Bogofilter plugin instead. It's purely bayesian so it does less checks than Spamassassin, but it's much faster.

---

### Post by colinleroy on 2007-05-24
> **Sebastral said:**
> Is there a better way to compose messages?

You can setup an external editor.

---

### Post by Peverel on 2007-05-24
Is there a way to have claws as a tray icon? Not in my window list, but in the tray so it notifies me when I get an email?

Is there actually a way to do this in Thunderbird, that's what I'm currently using, but I will try out claws soon...would be perfect if it could stay in the tray...

---

### Post by berserker on 2007-05-24
> **Peverel said:**
> Is there a way to have claws as a tray icon? Not in my window list, but in the tray so it notifies me when I get an email?

```
sudo apt-get install claws-mail-trayicon
```

---

### Post by Lucifiel on 2007-05-24
> **colinleroy said:**
> You need to install and start the spamd service:

$ sudo apt-get install spamassassin
$ sudo vi /etc/default/spamassassin -- change ENABLED to 1,and add "-i 127.0.0.1" without the quotes in the OPTIONS line
$ sudo /etc/init.d/spamassassin start

Then, Claws Mail's Spamassassin plugin will be able to communicate with the daemon.
Alternatively, you may use the Bogofilter plugin instead. It's purely bayesian so it does less checks than Spamassassin, but it's much faster.

Thank you! :) It took me some Googling to learn how to use vi but I seem to have saved and enabled the changes.

And now, we'll wait and see if Spamassassin works. 

Ahhh... thanks for the recommendation. :) Perhaps I'll try that filter next time round.

---

### Post by Peverel on 2007-05-24
Thanks Berserker, I'll try out claws with the tray icon tomorrow and post how it went...

---

### Post by paris3200 on 2007-05-28
I try to get the publickey and it never finishes.  I've tried doing this on 2 different computers over the past 4 days.  Anyone got any idea whats going on?  Heres what happens:

> wget [http://colino.net/colin.publickey](http://colino.net/colin.publickey)
--17:34:12--  [http://colino.net/colin.publickey](http://colino.net/colin.publickey)
           => `colin.publickey'
Resolving colino.net... 213.41.244.236
Connecting to colino.net|213.41.244.236|:80... 

---

### Post by LeeU on 2007-05-29
> **colinleroy said:**
> Alternatively, you may use the Bogofilter plugin instead. It's purely bayesian so it does less checks than Spamassassin, but it's much faster.

I have tried to get this running but no success. How is it set-up? I installed it with the Synaptic Package Manager but it doesn't appear in the plugins folder for Claws (using Sylpheed Claws GTK2)

---

### Post by colinleroy on 2007-05-29
> **paris3200 said:**
> I try to get the publickey and it never finishes.  I've tried doing this on 2 different computers over the past 4 days.  Anyone got any idea whats going on?  Heres what happens:

You've had bad luck, my personal website's been down due to a migration the past 4 days. You should try again, it's back online now!

---

### Post by colinleroy on 2007-05-29
> **LeeU said:**
> I have tried to get this running but no success. How is it set-up? I installed it with the Synaptic Package Manager but it doesn't appear in the plugins folder for Claws (using Sylpheed Claws GTK2)

You need Claws Mail, Sylpheed-Claws Gtk2 is too old.

---

### Post by LeeU on 2007-05-29
> **colinleroy said:**
> You need Claws Mail, Sylpheed-Claws Gtk2 is too old.
Will it upgrade Sylpheed-Claws Gtk2 so I won't lose my current set-up and mail?

Interesting, when I went to install Claws Mail, it said that it would remove Sylpheed-Claws Gtk2. Is this the upgrade or am I going to lose something?

**** UPDATE: I went ahead and tried it and it worked perfectly. I migrated from Sylpheed to the new version and works great (so far). Thanks for the help.

---

### Post by colo505 on 2007-06-18
1. How can I install Claws Mail on Feisty/AMD64?
2. How can I transfer my Thunderbird mail, accounts and address book to Claws Mail?

Thanks

---

### Post by carl.davis on 2007-06-18
I am having the same problems.  Claws mail runs fine on Feisty non 64 bit

---

### Post by herbster on 2007-06-26
WOW, I have installed Sylpheed and Sylpheed-Gtk2, my goodness this program rules! Unbelievably fast, simple and so effective. The preferences you can set alone blow away Evolution-- you can actually *customize* this program! ;)

I actually really love the fact that I have a [email]my@email.com[/email] folder right there in my home directory.

Also, the plugins are awesome, particularly the notification tray icon. I just love the simplicity and that with the bells and whistles possible, you aren't confined to anything, you can really keep it barebones and simple.

I am also wondering how to install Claws-Mail if it is in fact better than Sylpheed-Gtk2??

---

