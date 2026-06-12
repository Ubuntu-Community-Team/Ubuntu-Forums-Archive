---
title: "HOWTO: Send and Receive Hotmail through Evolution"
date: 2006-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Indras on 2006-06-20
Okay everyone, after digging around in these forums and googling like I've never googled before, I figured out how to send and receive e-mail through hotmail using Evolution.  I'm throwing together a rough HOWTO for others.  If things need more clarification, let me know and I'll update it.

**First, make sure your system is up to date.  Open up a terminal and type:**

```
sudo apt-get update
```

**Now, install the inet daemon**

```
sudo apt-get install inetutils-inetd
```

**This takes care of all of our dependencies.  Now on to the good stuff...**

```
sudo apt-get install hotway hotsmtp
```

**This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP.  By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.**

```
sudo gedit /etc/inetd.conf
```

**Look for a line like this:**

```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd
```

**By default, hotway leaves a copy of each message it downloads on the server.  I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:**

```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r
```

**And we also need to add a line to get hotsmtpd working, just paste this at the bottom:**

```
2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd
```

**This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon.  Now, save your file, exit gedit, and restart your inetd server:**

```
sudo /etc/init.d/inetutils-inetd restart
```

**If everything is working properly, you'll see this pop up on your screen:**

```
* Restarting internet superserver inetd                            [ ok ]
```

**Now, close out of your terminal and start up Evolution.  It may pop up the first-time use wizard, you can use that if you like.  Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left.  However you choose to do it, here's your information:**

**Email Address:** *xxx*@hotmail.com  (fill in your normal e-mail address that you use to login to hotmail)

**Receive Server type:** POP
**Server:** 127.0.0.1
**Username:** *xxx*@hotmail.com (same as above)
**Security:** No encryption
**Authentication type:** Password
(Remember password checkbox is up to you)

**Send Server type:** SMTP
**Server:** 127.0.0.1:2500
**[X] Server requires authentication** (check this box)
**Use Secure Connection:** No encryption
**Authentication Type:** PLAIN
**Username:** *xxx*@hotmail.com (same as above)
(Optional Remember password checkbox)

---

### Post by avtolle on 2006-06-20
Thanks. However, should be hotsmtp, not hotsmtpd as set out in the third code step in your original post.:KS

---

### Post by 146lily on 2006-06-20
> Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Hotmail said you must pay money to have WebDAV access

Please enter the POP password for [email]bigron.msn@hotmail.com[/email] on host 127.0.0.1

I get this error message after entering password and trying to download mail?

---

### Post by Flojomojo on 2006-06-20
[QUOTE=146lily]I get this error message after entering password and trying to download mail?[/QUOTE]
Doesn't M$ require you to pay a free for POP and IMAP access to Hotmail now? 

That, along with the MSIE-centric focus of [www.live.com](www.live.com), is one of the things that pushed me into moving to Linux.

---

### Post by avtolle on 2006-06-20
Yeah, I got the same message. Thus, away from Hotmail, onto Gmail.

---

### Post by Thund3rstruck on 2006-06-20
Great guide, thanks! Worked perfect and now I have my hotmail inside Linux!! Amazing

---

### Post by Indras on 2006-06-20
[QUOTE=avtolle]Thanks. However, should be hotsmtp, not hotsmtpd as set out in the third code step in your original post.:KS[/QUOTE]

Thanks, all corrected.

[Quote=146lily]I get this error message after entering password and trying to download mail?[/quote]

I've heard of people getting this before, I'm going to look into it.

By the way, how old is your account?  I find a lot of articles in google saying that Hotmail was ending WebDAV access to new accounts in order to crack down on spam, but all the articles are around September 27, 2004.  I know for a fact that I've had my hotmail account for at least six years, and I've always had the capability to open it in Outlook Express (which uses WebDAV).  I'm thinking if it's a really new account, it might need to be active for a certain number of months before they give you WebDAV.  Otherwise, it might be that all new accounts are not getting WebDAV at all, in which case you're SOL.

My only other suggestion is to try logging directly in via [www.hotmail.com](www.hotmail.com) to confirm that the e-mail address and password are 100% correct, and that the account is active.

EDIT: Here's a website that confirms my suspicions:
[http://www.neilturner.me.uk/2006/Apr/11/using_windows_live_mail_i.html](http://www.neilturner.me.uk/2006/Apr/11/using_windows_live_mail_i.html)
> You can experience with the WebDAV option, which may work with your account if you have been using Hotmail for a few years.

---

### Post by unique on 2006-06-20
Or better yet just use...
```
pop3hot.com
```
as your pop3 server and your set. :-\"

---

### Post by shof2k on 2006-06-30
Cool, worked for me without any problems.

Are there any security implications of using email this way.  I noticed authentication is in the clear, but am I right in assuming this doesn't matter because the hotmail server is really localost?

Basically I want to know if any passwords or data is sent in the open.

Thanks for the howto :)

---

### Post by Indras on 2006-06-30
[QUOTE=shof2k]Cool, worked for me without any problems.

Are there any security implications of using email this way.  I noticed authentication is in the clear, but am I right in assuming this doesn't matter because the hotmail server is really localost?

Basically I want to know if any passwords or data is sent in the open.

Thanks for the howto :)[/QUOTE]

You're welcome!

I did a bit of research, but it seems the project page for hotwayd is missing or corrupted ([http://hotwayd.sourceforge.net](http://hotwayd.sourceforge.net)).  The only "real" information I can find is this: [http://www.freshports.org/mail/hotwayd/](http://www.freshports.org/mail/hotwayd/)

[quote=http://www.freshports.org/mail/hotwayd/]Hotwayd uses HTTPMail (the same protocol that Outlook Express uses) to access
servers such as Hotmail.  The software acts as a proxy mail server, allowing
you to access e-mail on Hotmail and similar servers using standard POP3 mail
clients.[/quote]

So, either Hotwayd and Outlook Express both send your username and password in plaintext to the server, or they both do not.

After a bit of digging, I found this site, which is currently missing (so I'm linking to the google cache page):

[http://72.14.203.104/search?q=cache:kPlGzQLluWwJ:docs.safehaus.org/display/TRIPLESEC/HTTPMail%2BProtocol%2BNotes+httpmail+hotwayd+ssl&hl=en&gl=us&ct=clnk&cd=2](http://72.14.203.104/search?q=cache:kPlGzQLluWwJ:docs.safehaus.org/display/TRIPLESEC/HTTPMail%2BProtocol%2BNotes+httpmail+hotwayd+ssl&hl=en&gl=us&ct=clnk&cd=2)

This gives an idea of the login process that Hotwayd uses to connect to the Hotmail server.

If you're feeling really frisky, feel free to read the specifications for the WebDAV protocol for very specific information: [http://webdav.org](http://webdav.org).

Personally, I find it all a bit over my head :D

---

### Post by richbarna on 2006-06-30
When I tried to retreive my mail I got this error :-
> Error while Fetching Mail.

Unable to connect to POP server 127.0.0.1: No support for requested authentication mechanism.

EDIT: All sorted, authentication was login instead of password ;)

Worked lovely, excellent !!!

---

### Post by cptnapalm on 2006-06-30
I used to use this forever and a half ago, but I had forgotten all about it.  Thanks.

---

### Post by reid on 2006-07-05
This is a great tutorial, very helpful, thanks.

My install was however using xinetd instead of inetd.  Is this installed autimatically with Ubuntu?  Xinetd is considered more secure than inetd, so I decided to keep it instead of installing inetd.  Anyway, to get xinetd to read your inetd.conf, and incorporate those rules into it's functionality you can do this:

Edit the startup script that calls xinetd.
```
sudo gedit /etc/init.d/xinetd
```
Change this under the 'start' case:
```
start-stop-daemon --start --quiet --background --exec /usr/sbin/xinetd -- -pidfile /var/run/xinetd.pid $XINETD_OPTS
```
By adding the '-inetd_compat' argument:
```
start-stop-daemon --start --quiet --background --exec /usr/sbin/xinetd -- [COLOR="Red"]-inetd_compat[/COLOR] -pidfile /var/run/xinetd.pid XINETD_OPTS
```
Then, restart xinetd:
```
sudo /etc/init.d/xinetd restart
```

I got that nugget from /usr/share/doc/xinetd/README.Debian

Thanks again for the great tutorial - I had no idea this was even an option.

---

### Post by Browser_ice on 2006-07-06
The link about :

EDIT: Here's a website that confirms my suspicions:
[http://www.neilturner.me.uk/2006/Apr...ve_mail_i.html](http://www.neilturner.me.uk/2006/Apr...ve_mail_i.html)

says to open the extension dialog. I don't know where this is.

---

### Post by PPower on 2006-07-19
Brill guide. It worked great.

If you have a newer account like me the way to get it going is to get into the Windows Live Mail Desktop beta as that enables WebDAV to get Delta Sync working.

---

### Post by klytu on 2006-07-19
Excellent posts, Indras! Works great for me and your step-by-step instructions are really clear. 

My Hotmail account uses multiple folders to sort incoming mail. Has anyone figured out how to synchronize folders other than the Inbox? While I am waiting for a response, I'll see if can figure out how ....

---

### Post by klytu on 2006-07-19
> **klytu said:**
> Excellent posts, Indras! Works great for me and your step-by-step instructions are really clear. 

My Hotmail account uses multiple folders to sort incoming mail. Has anyone figured out how to synchronize folders other than the Inbox? While I am waiting for a response, I'll see if can figure out how ....

Found an answer in the hotwayd man pages (quoted verbatim): 

> It  is now also possible to get any folder you like instead of just the inbox. Just put the name of the folder you want  after  the  domain  in
your email address with a forward slash. For example, to get the folder named "hello" you would issue the command "user [email]dave@hotmail.com[/email]/hello" at  the  prompt. So this means in your mail reader you should enter the user name as "dave@hotmail.com/hello". You will need to  create  a  new mailbox  in your mail reader for each folder. Work continues on an IMAP implementation of hotwayd which will circumvent this folder hack due to the native folder support in IMAP.

To set up the additional Hotmail folders, you add a new hotmail account for each one. For example, I have a folder called "Programming" in my Hotmail account. To set it up in Evolution, I created a new Hotmail account using the steps in the howto, but for the username I used [email]my_username@hotmail.com[/email]/Programming and named the new account Hotmail-Programming. Next in Evolution I created a mail folder called Programming. Then I set my message filters to send all mail from that new account to the Programming folder: Edit>Message Filters; Add; for search name I typed programming (I don't think it matters what you put there); Under "find items that meet the following criteria" changed "sender" "is" to "source account" "is" using the selection arrows and chose the new account created; under "then" "move to folder" selected the Programming folder I had created in Evolution. Now when I click "Send/Receive" mail from my Hotmail Programming folder is sent to the mail folder Programming in Evolution.

Something I noticed which might not be obvious is that if you want messages you download in Evolution to stay on the Hotmail server so that you can read them later from another location (on the web, for example), you should tick the "Leave messages on server option" when setting up your Hotmail account(s) (Edit>Preferences>Accounts, select an account and click Edit, choose "Receiving Options" tab and tick or clear "Leave messages on server option" as desired). I missed this step when I first set-up Hotmail under Evolution, and when Evolution downloaded my messages it emptied my Hotmail inbox - which is not what I wanted. I had to forward all those messages back to myself in order to access them from the web again.

---

### Post by Josh_b on 2006-07-24
> If you have a newer account like me the way to get it going is to get into the Windows Live Mail Desktop beta as that enables WebDAV to get Delta Sync working.

Yeah, I fall into that category. So how do I do that?

---

### Post by PPower on 2006-07-24
Wait for a public beta

---

### Post by EdwinH on 2006-07-24
This works great with the in Opera integrated email client too.

---

### Post by Josh_b on 2006-07-25
bugger.:(

---

### Post by kutuluu on 2006-09-04
This worked 99 % correctly for me. 

One flaw happend to me while applying original instructions from indras,,,,

(Evolution was running on backround)

I executed all as described, then activated evolution , but evolution has crashed.Did not accept any commands, had to kill it.
-> then i tried to open it again, but nothing happened
--> then i restarted ubuntu.
---> all worked ! 

As you might see / feel, i am windows user :) restart makes magic.

But, most importantly, this is the way to make instructions !

BIG thx !!!

---

### Post by BLTicklemonster on 2006-09-05
Wow, I'm recieving email from my hotmail account in evolution for the first time ever. Sweet! But I sent myself 2 emails and haven't gotten either one yet. Hmmmm. Just checked it on the web browser, and they are there, probably just takes a bit to make it from there to here. Excellent! Thanks!

---

### Post by cvmostert on 2006-09-12
great guide, worked for me! takes long to log onto the server though..

cheers

---

### Post by MrLeN on 2006-09-12
I tried both setws of instructions, but when i type:

sudo gedit /etc/init.d/xinetd

I get a document, but there's nothing in it -- so I can't change it.

MrLeN

---

### Post by MrLeN on 2006-09-12
sudo apt-get install inetutils-inetd

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package inetutils-inetd

Is this bad?

---

### Post by srf21c on 2006-09-25
> **146lily said:**
> 
Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Hotmail said you must pay money to have WebDAV access

Please enter the POP password for [email]<username>@hotmail.com[/email] on host 127.0.0.1

>I get this error message after entering password and trying to download mail?

Just tried setting up hotway+evolution for a friends account, and getting the same error.  Hotmail account is 3 years old.  Going to have him sign up for the Windows Live desktop beta, see if that helps.

---

### Post by Jeremiah478 on 2006-09-25
Thanks for the HowTo, just thought that I would let you know that I used this to setup Hotmail inside of Thunderbird and it works great, so once again, Thanks.

---

### Post by darundal on 2006-09-27
Was able to get it "almost" running in Thunderbird. Pretty sure this is a cross platform then, but when I try to use it, it says I must pay for WebDAV Access...

---

### Post by srf21c on 2006-09-28
an update.  Hotmail access via Thunderbird and the Webmail extension(s) works fine with the friends hotmail account in question.  

Next step is to try configuring Evolution+Hotway on another system to see if I can replicate the problem.

---

### Post by adambullock on 2006-10-03
absolutely beautiful. I've been simply logging in thru firefox, but this is great, and worked perfect for me. I too would switch to gmail, but as I've had my hotmail account since about the time it came out, I'm a little attached to it. I'm one of the few people left that've had the same personal email account for a DECADE! So thanks again for this workaround.

---

### Post by tetherblood on 2006-10-26
Ive tried this and i am returning the "pay to use webdav" error. Am i right in thinking there is no workaround for this?
Does anyone know of any other options if someone finds themselves in this situation?

or is it simply to use firefox and log in or pay MS ](*,) 

thanks


Matt

---

### Post by vagayan on 2006-10-29
Thank you so much for this guide, it worked for me. My hotmail account is probably 6 years old if not more. If someone finds a definitive answer about security (whether passwords are passed in clear), please post it here.

---

### Post by theicyj on 2006-10-31
Thanks a lot this this guide.  Worked flawlessly! :)

---

### Post by dpm on 2006-11-04
> **reid said:**
> This is a great tutorial, very helpful, thanks.

My install was however using xinetd instead of inetd.  Is this installed autimatically with Ubuntu?  Xinetd is considered more secure than inetd, so I decided to keep it instead of installing inetd.  Anyway, to get xinetd to read your inetd.conf, and incorporate those rules into it's functionality you can do this:


Rather than running in **inetd** compatibility mode, why not create a **xinetd** server configuration file for **hotwayd** as described here?:

[http://www.ubuntuforums.org/showpost.php?p=619554&postcount=3](http://www.ubuntuforums.org/showpost.php?p=619554&postcount=3)

The only additional step I had to perform was to edit the **/etc/hosts.allow** file and add the following line (otherwise I could not connect to 127.0.0.1):

```
hotwayd: 127.0.0.1
```Cheers.

---

### Post by dpm on 2006-11-04
Also I think it would be sensible to add the **hotwayd** tag to this thread. A standard search on "hotwayd" on the forums does not list this thread.

---

### Post by dpm on 2006-11-04
> **vagayan said:**
> If someone finds a definitive answer about security (whether passwords are passed in clear), please post it here.

Here is some documentation on the so-called HTTPMail protocol (apparently an undocumented implementation of a subset of the WebDAV protocol) which hotmail uses for communication with clients such as outlook express or in this case a gateway like hotwayd:

[http://web.archive.org/web/20050327063733/http://jhttpmail.sourceforge.net/httpmail.html](http://web.archive.org/web/20050327063733/http://jhttpmail.sourceforge.net/httpmail.html)

As far as I gather from my limited understanding, yes, the information is sent in the clear. I hope someone more knowledgeable on the subject can confirm or deny this. 

In any case, would it be possible to encrypt the communication between hotwayd and the HTTPMail server within an SSH tunnel, for example?

---

### Post by dpm on 2006-11-04
> **tetherblood said:**
> Ive tried this and i am returning the "pay to use webdav" error. Am i right in thinking there is no workaround for this?
Does anyone know of any other options if someone finds themselves in this situation?

or is it simply to use firefox and log in or pay MS ](*,) 

thanks


Matt

IIRC there is a **gotmail** project which allows you to receive (and send?) hotmail messages for accounts which do not implement the HTTMail protocol.

---

### Post by reid on 2006-11-09
> **desp said:**
> Rather than running in **inetd** compatibility mode, why not create a **xinetd** server configuration file for **hotwayd** as described here?:

[http://www.ubuntuforums.org/showpost.php?p=619554&postcount=3](http://www.ubuntuforums.org/showpost.php?p=619554&postcount=3)

The only additional step I had to perform was to edit the **/etc/hosts.allow** file and add the following line (otherwise I could not connect to 127.0.0.1):

```
hotwayd: 127.0.0.1
```Cheers.

Thanks desp, that is a much more elegant solution.

---

### Post by cwynnes on 2006-11-11
Hey ppls,

Just new to linux and ubuntu and found the OP great but when i went to test it by sending a mail i was given the following error

Host lookup failed: @hotmail.com: Name or service not known

I followed the original post word for word and i cant figure out what went wrong,

Any help would be greatly appreciated,

Regards

---

### Post by dpm on 2006-11-12
> **cwynnes said:**
> Host lookup failed: @hotmail.com: Name or service not known
My guess would be that you did not fill in the smtp server correctly in Evolution, but I cannot tell you much, since I only use hotwayd to receive e-mail, not to send.

Does receiving e-mail work for you?

---

### Post by Lucas2005 on 2006-11-17
the first method worked for me, i even have a @msn.com address and not @hotmail.com

---

### Post by SirShaggy on 2006-11-17
I had never done this before, I don't use my msn account much at all. I decided to give it a try, only I wanted to use Thunderbird. I used the setup direct from the howto with my account information, it immediately downloaded the 87 messages I had on the server. Cool!

SirShaggy

---

### Post by gammyhand on 2006-11-20
> **PPower said:**
> 
If you have a newer account like me the way to get it going is to get into the Windows Live Mail Desktop beta as that enables WebDAV to get Delta Sync working.

Brilliant guide and the tip above fixed it for me.

---

### Post by klokwyze on 2006-11-25
I get the WebDAV pay error as well.

"Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Hotmail said you must pay money to have WebDAV access

Please enter the POP password for *****@hotmail.com on host 127.0.0.1"

ill look for this "gotmail" project now... anyone else have any obvious/easy solutions to this problem besides a new different email service or program?

---

### Post by klokwyze on 2006-11-25
Nevermind... got going through a pop3server thing called "izymail.com" to receive my inbox messages.

I can't seem to send messages though... Evolution just hangs on the "send/receive mail" screen. It completes receiving inbound messages, but just stays @ 0% on outbound messages.

For "server" under server configuration I've tried

127.0.0.1:2500
127.0.0.7:2500
hotmail.com:2500
out.izymail.com:2500

all of them with server type "smtp", "server requires authentication" checked, no security, plain authentication, with my full email as the username.

anyone have any suggestions?

---

### Post by matchstich on 2006-12-15
> **richbarna said:**
> When I tried to retreive my mail I got this error :-


EDIT: All sorted, authentication was login instead of password ;)

Worked lovely, excellent !!!

can 

you explain what you mean by this, i am getting the same error
thanks

---

### Post by cibara on 2006-12-17
> **desp said:**
> As far as I gather from my limited understanding, yes, the information is sent in the clear. I hope someone more knowledgeable on the subject can confirm or deny this.

I was also curious, so i sniffed the traffic while connecting, and found some enlightening data in the TCP stream.

Connection: Keep-Alive
Authorization: Digest username="xxxxxxxx@msn.com", realm="Microsoft Passport", qop="auth", ***algorithm="MD5"***

Although the user name is sent in the clear, the password authentication is encrypted. Albeit lightly. So, as long as you have a respectable password, you are in good shape.

Thanks to the original poster for an excellent how-to.

---

### Post by linderback on 2006-12-25
Thank you for this guide.

Downloading my messages in Evolution works fine. However, when I try to send messages I get the following message "Error while performing operation. Welcome response error. Operation now in progress". Outbound messages are stuck in the outbox.

I've used Hotmail for about 8 years or so but I recently "upgraded" it to Windows Live Mail. I've had my account for a long time and I'm not very keen on switching to a new one.

I guess I can't be the only one with this problem?

Rich

---

### Post by kashms on 2006-12-26
I was getting an error about needing to pay for webdav access but then I signed up for the Desktop Mail Live beta and I think it is ok for webdav access now. But now I'm getting another error in Evolution:
"Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Unable to find folder inbox on remote server"

Anyone know what this one is about?

---

### Post by ksamvel on 2007-01-16
> **desp said:**
> Rather than running in **inetd** compatibility mode, why not create a **xinetd** server configuration file for **hotwayd** as described here?:

[http://www.ubuntuforums.org/showpost.php?p=619554&postcount=3](http://www.ubuntuforums.org/showpost.php?p=619554&postcount=3)

The only additional step I had to perform was to edit the **/etc/hosts.allow** file and add the following line (otherwise I could not connect to 127.0.0.1):

```
hotwayd: 127.0.0.1
```Cheers.

That is Saint step!!! I have spent lots of my time to figure this out. Thanks.

---

### Post by dothedorky on 2007-01-18
```
Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Hotmail said you must pay money to have WebDAV access

Please enter the POP password for *****@hotmail.com on host 127.0.0.1
```

Now what?](*,)

---

### Post by nicktrik on 2007-01-29
Great work. Works a charm.

---

### Post by avisual on 2007-01-31
Thats works great :-)

---

### Post by geminifire on 2007-02-01
it works for me, thx!:D

---

### Post by nsleiman on 2007-02-03
I just give it a try, the 127.0.0.1 as pop did not work but the pop3hot.com worked out after adding login and password on IzyMail. is this in any way secure ? what if i change the hotmail password will it work after that like its working now?

I work with Kmail (KDE).

---

### Post by hito1 on 2007-02-14
I would like to try this, but first I'd like to know if running this inet daemon will make a sensible hit in the computer performance?

Thanks.

---

### Post by forgeuk on 2007-02-21
OK, mine's working fine, thanks to the original poster!

This is more of an evolution question, I'd like my hotmails to go into a seperate folder that I've just made, but I can't seem to see a way to do a message rule for it. Is there a way to set up a rule to filter by account rather than by subject or sender?


[COLOR="Red"]Ignore that...found it, its Add then choose source account from the drop down...nice[/COLOR]

---

### Post by nicktrik on 2007-02-21
I had problems with sending mail and I usually had to sudo /etc/init.d/inetutils-inetd restart in order just to receive mail. Then I came across izymail, and all problems solved. [http://v3.izymail.com/support.aspx#setup](http://v3.izymail.com/support.aspx#setup) is the way to go.

---

### Post by joinf on 2007-02-22
Very cool  I am new to linux and i needed a good explaination to make hotwayd work. thank you

---

### Post by xodeus on 2007-02-28
> **nicktrik said:**
> I had problems with sending mail and I usually had to sudo /etc/init.d/inetutils-inetd restart in order just to receive mail. Then I came across izymail, and all problems solved. [http://v3.izymail.com/support.aspx#setup](http://v3.izymail.com/support.aspx#setup) is the way to go.

But this costs money to use...

---

### Post by RicTN on 2007-03-04
Hey!  Worked like a charm!  For a newbie!  Thanks!

---

### Post by Rizado on 2007-03-05
I joined windows live mail beta but I still got the you have to pay for webdav error. Anything else I have to do?

---

### Post by finferflu on 2007-03-05
Yay! It works! I didn't even know I could check Hotmail without Outlook! I don't use Hotmail a lot, that's why I prefer not even visiting hotmail.com... Gmail is the best for me, by the way. 

Thanks a lot for this howto, you liberated me from having to go on the Hotmail website!!!

---

### Post by Rizado on 2007-03-05
Turns out I registered to windows live mail and not windows live mail **desktop**.

However now I get a new error. Server Answer: "Unable to find folder inbox on remote server"

I think this might be because I have a swedish account. inbox is actually called inkorg. I had the exact same problem with gotmail but there you can choose what folder to download. Can I do that here to?

EDIT: Crap, not the problem. I changed it to inkorg and recompiled. Still the same error. Except it's "Unable to find folder inkorg on remote server" now.

---

### Post by Bruegger on 2007-03-11
Fantastic HowTo.
Worked like a charm for me.Finally i can send and receive mail without going to firefox.

Now if only someone could tell me how to import and sync all my personal folders from hotmail, my day would be made!

---

### Post by Lajiao on 2007-03-16
Thank you very much.
I got the same error message :

Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Hotmail said you must pay money to have WebDAV access

My account is old, at least from 2003.

Thanks again.

---

### Post by Floppyjoe on 2007-03-18
Worked great in Thunderbird for me! Can send and receive using Thunderbird and this Hotmail account.

Edit: I had to redo this guide when I upgraded to Feisty.

---

### Post by Inkubas on 2007-03-30
THANK YOU FOR THIS WONDERFUL THREAD!

I just set up my hotmail account to evolution! It looks great and it's neat and well made. I'm so happy. This thread really helped me and it was easy enough to follow. I didn't have any problems (thankfully) installing it, but I do have two questions. My first question is the following:

Is there a specific setting that must be fine tuned for receiving emails? I can send with no problem, however, whenever I try to receive emails they don't go through. Instead, I've got to log into hotmail to retrieve them. Any ideas? It can be something simple that I've missed out. Please help.

The second question:

Are there themes/mods/plugings that you can download to make it even better or more stylish? Style is a very important thing next to features

---

### Post by Inkubas on 2007-03-30
I've no clue how but the messages are actually going through. It just takes awhile, I'm going to see if there's anyway to configure it so that a) I don't have to enter a password to do everything & b) don't have to wait as long to be notified about a new message. Again, an amazing thread.

---

### Post by catch007 on 2007-03-30
kind of complex...

---

### Post by Buttonboy on 2007-04-08
i couldent get it to work at first but when i used pop3hot.com i got a link to izymail and when i set that up it all worked fine. thanks for the help. 
[http://v3.izymail.com/](http://v3.izymail.com/)

---

### Post by Shoine on 2007-04-12
Hi,
Thanks for the HowTo, unfortunatly, i'm unable to download the package from the terminal.
This is the message i got :

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package inetutils-inetd

And same error for hotway.

Could you help me ?

I started to use Ubuntu a little while ago (actually 2 hours ago), but I already enjoy it. However, i can't figure out what's the problem here. Thanks for your help !

---

### Post by malimal on 2007-04-26
> **klytu said:**
> Found an answer in the hotwayd man pages (quoted verbatim): 



To set up the additional Hotmail folders, you add a new hotmail account for each one. For example, I have a folder called "Programming" in my Hotmail account. To set it up in Evolution, I created a new Hotmail account using the steps in the howto, but for the username I used [email]my_username@hotmail.com[/email]/Programming and named the new account Hotmail-Programming. Next in Evolution I created a mail folder called Programming. Then I set my message filters to send all mail from that new account to the Programming folder: Edit>Message Filters; Add; for search name I typed programming (I don't think it matters what you put there); Under "find items that meet the following criteria" changed "sender" "is" to "source account" "is" using the selection arrows and chose the new account created; under "then" "move to folder" selected the Programming folder I had created in Evolution. Now when I click "Send/Receive" mail from my Hotmail Programming folder is sent to the mail folder Programming in Evolution.

Something I noticed which might not be obvious is that if you want messages you download in Evolution to stay on the Hotmail server so that you can read them later from another location (on the web, for example), you should tick the "Leave messages on server option" when setting up your Hotmail account(s) (Edit>Preferences>Accounts, select an account and click Edit, choose "Receiving Options" tab and tick or clear "Leave messages on server option" as desired). I missed this step when I first set-up Hotmail under Evolution, and when Evolution downloaded my messages it emptied my Hotmail inbox - which is not what I wanted. I had to forward all those messages back to myself in order to access them from the web again.

Is their any update for hotmail subfolder support or imap support?

---

### Post by shutrbug on 2007-04-28
Thanks, OP, for writing this HOWTO.  Everything works fine for me.  Is it possible to delete messages from the server through Evolution or will my inbox just keep growing larger and larger if I don't manage it through the web interface or Outlook Express on the Windows side?

---

### Post by Dimension7 on 2007-04-30
Thank you for this HOWTO.  I am now able to check my Hotmail without having to go through their website.

---

### Post by eXSiR on 2007-05-13
Thanks for the HOWTO. Now i can check my account Thunderbird instead of Evolution. It works perfectly, thnx again.

---

### Post by DMLane on 2007-05-17
I tried thistwice I get message f ailed to read a valid greeting from POP server 127.0.0.1.
I need to get my hot mail on this Ubuntu system. I just downloaded Ubuntu last weekend. I'll nece use windows on my home system again.

---

### Post by DMLane on 2007-05-17
sorry cat on keyboard . I ment to say I'll never use windows on my home system again.

---

### Post by voodew on 2007-05-18
I've been using Hotmail through Evolution for months now and today I'm getting a connection refused through 127.0.0.1 message. Did M$uck change something?

---

### Post by Freaky_Llama on 2007-05-23
UPDATE and a FIX:

For those of you who have issues SENDING using this method, the following is for you.

I am running 7.04 on my Tosh laptop, and had the exact same error with sending : "Operation In Progress" in Evolution using hotwayd and hotsmtpd.

I felt the issue was in hosts.allow and I was right. Please add the following line to /etc/hosts.allow :

```

hotsmtpd: 127.0.0.1 2500

```

This was the end-all-be all of my issues, and now sending works fine. I hope it helps with anyone else who is having the issue.

Also, to mention, I have configured xinetd with option "--inetd_compat" as suggested in a post somewhere in this thread. After editing hosts.allow, I did the following:
```

sudo /etc/init.d/inetutils-inetd restart
sudo /etc/init.d/xinetd restart

```

---

### Post by mominnawaz1 on 2007-05-23
You're a genius man, i have been trying this for ages, and it works perfect with my ubuntu as im a geek too , but man ure amazing.

Thanks,

Cheers,

M

---

### Post by mamadou on 2007-05-23
Great how to!!!
It worked for me from the first time.
No worries,
Good Job.
Thank you very much!

---

### Post by voodew on 2007-05-24
I figured out that I was running xinetd and the package was installed as a dependency of vmware. I tried adding the -inetd_compat parameter to the xinetd file and was only able to receive mail. Editing the hosts.allow didn't help either. I figured out the configuration for xinetd without use of the -inetd_compat parameter. It goes as follows:

sudo gedit /etc/xinetd.conf and copy and paste this:
```

defaults
{
        instances               = 60
        log_type                = SYSLOG authpriv
        log_on_success          = HOST PID
        log_on_failure          = HOST
        cps                     = 25 30
}
includedir /etc/xinetd.d
```

Next sudo gedit and create these two files:
/etc/xinetd.d/hotsmtpd
```

service hotsmtpd
{
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = nobody
groups = yes
server = /usr/bin/hotsmtpd
port = 2500
}
```

/etc/xinetd.d/hotwayd
```

service hotwayd
{
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = nobody
groups = yes
server = /usr/bin/hotwayd
log_on_failure += USERID
log_on_success += PID HOST EXIT
port = 110
}
```

Restart the xinetd server
```
sudo /etc/init.d/xinetd restart
```

I'm sure there is a more streamlined way of configuring these files and the log files that are being created are probably unnecessary. I'm not sure if editing of hosts.allow is required if you use this method, my file is blank. I also don't know how secure this method is. Anyone have any additional input?

---

### Post by sehe on 2007-05-26
> **unique said:**
> Or better yet just use...
```
pop3hot.com
```
as your pop3 server and your set. :-\"

JUST SAY NO =;

Aw please... ](*,) That is one blunt way to invite people into massively dumping their hotmail passwords onto some guy's nifty 'free server'   #-o

I would *not* advise anyone to do this as long as it is trivial to set up hotway locally. I know, passwords will probably still get sent in cleartext, but purposely sending them through a specific server that *knows* what to listen for is just a little bit naive in my book [-X.

Trouble is, people don't know how much privacy-sensitive information can be gained from their lowly hotmail boxes... Please do not advise unsuspecting computer users of bad ideas like this. Thank you thank you thank you

---

### Post by chrno2004 on 2007-05-27
I've already got courier-pop installed on my server. Is there anyway to configure hotway to listen on alternative port? Also, configure hotway to download the mail to one of my mailbox in courier? 

Thanks!

chrno :D

---

### Post by voodew on 2007-05-27
> **chrno2004 said:**
> I've already got courier-pop installed on my server. Is there anyway to configure hotway to listen on alternative port? Also, configure hotway to download the mail to one of my mailbox in courier? 

Thanks!

chrno :D

Just to promote my last post, if you use xinetd instead of inetd (xinetd is the update to inetd), then follow the instructions in my last post and just change the port numbers as so:

```

service hotwayd
{
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = nobody
groups = yes
server = /usr/bin/hotwayd
port = **1100**
}

```
If you're using the inetd method just change this line in inetd.conf:
```

pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r

```

to something like

```

1100		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r
```

---

### Post by utopial on 2007-05-30
I've set up evolution with my hotmail account according to the following instructions:
[http://onlyubuntu.blogspot.com/2007/03/send-and-receive-your-hotmail-messages.html](http://onlyubuntu.blogspot.com/2007/03/send-and-receive-your-hotmail-messages.html)

I have 2 major problems, which are related:
- after evolution downloads my mail, it is automatically put in my hotmail trash when i check it out via webmail
- how do i sync the two together so that if i make a folder or move emails between folders in evolution or web-based hotmail, the other one recognises it and automatically does the same?

I consider this to be a massive problem with evolution. outlook does it perfectly.

---

### Post by voodew on 2007-05-30
> **utopial said:**
> I've set up evolution with my hotmail account according to the following instructions:
[http://onlyubuntu.blogspot.com/2007/03/send-and-receive-your-hotmail-messages.html](http://onlyubuntu.blogspot.com/2007/03/send-and-receive-your-hotmail-messages.html)

I have 2 major problems, which are related:
- after evolution downloads my mail, it is automatically put in my hotmail trash when i check it out via webmail
- how do i sync the two together so that if i make a folder or move emails between folders in evolution or web-based hotmail, the other one recognises it and automatically does the same?

I consider this to be a massive problem with evolution. outlook does it perfectly.

I'm not sure about syncing, but the hotmail trash problem should be an easy fix.
If you have a line that looks like
```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r
```
in your inetd.conf file, remove the -r option.
In the account preferences in evolution, go to the Receiving Options tab and make sure "Leave Messages on Server" is checked.

---

### Post by jnewm on 2007-05-30
Thanks so much, this worked perfectly for me the first time also!  

But, to echo some previous posts, if anyone does know or figures out how to make it so when you delete downloaded hotmail emails in evolution, they also get deleted from your online hotmail account, please clue me in. 

Thanks again!

---

### Post by voodew on 2007-05-31
> **jnewm said:**
> Thanks so much, this worked perfectly for me the first time also!  

But, to echo some previous posts, if anyone does know or figures out how to make it so when you delete downloaded hotmail emails in evolution, they also get deleted from your online hotmail account, please clue me in. 

Thanks again!

I think the suggestions in the previous post are the fix. Remove the -r option and make sure "Leave messages on server" option is enabled on whatever client you're using.

---

### Post by utopial on 2007-05-31
> **voodew said:**
> I'm not sure about syncing, but the hotmail trash problem should be an easy fix.
If you have a line that looks like
```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r
```
in your inetd.conf file, remove the -r option.
In the account preferences in evolution, go to the Receiving Options tab and make sure "Leave Messages on Server" is checked.

thanks
i forgot to say that i dont have that '-r' on the end of the code but i didnt have the "Leave Messages on Server" ticked

anyone have any idea how to properly sync up the folder & email creation/movements between evolution and web-hotmail??
im kinda shocked and disappointed that evolution didnt try incorporate this into their design. such an important feature that outlook thoroughly caters to. hopefully im just ignorant of an existing solution

---

### Post by puterboy on 2007-06-03
great howto. greatly appreciated!!!

---

### Post by utopial on 2007-06-21
has anyone worked out how to properly sync up the folder & email creation/movements between evolution and web-hotmail??

---

### Post by karlseith on 2007-06-22
Thank You Thank You Thank You!!!

---

### Post by Floppyjoe on 2007-07-04
I also had the Vmware issue and just did the following to get it to work:
> **voodew said:**
> sudo gedit and create these two files:
/etc/xinetd.d/hotsmtpd
```

service hotsmtpd
{
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = nobody
groups = yes
server = /usr/bin/hotsmtpd
port = 2500
}
```

/etc/xinetd.d/hotwayd
```

service hotwayd
{
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = nobody
groups = yes
server = /usr/bin/hotwayd
log_on_failure += USERID
log_on_success += PID HOST EXIT
port = 110
}
```

Restart the xinetd server
```
sudo /etc/init.d/xinetd restart
```


---

### Post by Ped666 on 2007-07-13
I've only been using Ubuntu for a few days and I'm loving it.

My Hotmail account is working fine through Evolution.

A massive thank you to the original poster.

---

### Post by Setebos on 2007-07-13
I honestly deeply appreciate the effort gone into setting this up for all us inexperienced new guys. Unfortunately, it doesn't work for me as yet. The sending of mail works fine, but on clicking Send/Receive, I get the message -ERR Could not find folder inbox on remote server. A few other people have had it, I believe.

Sorry if this has already been answered; I have looked through the thread.

---

### Post by whiteshore on 2007-07-20
I'm getting the same error as above :(

---

### Post by j.miller565 on 2007-07-24
soz to revive this thread but has anyone been able to fix the: 

Error sending password: -ERR Hotmail said you must pay money to have WebDAV access

problem yet? can it be fixed?

---

### Post by beterraba on 2007-07-24
> **Freaky_Llama said:**
> UPDATE and a FIX:

For those of you who have issues SENDING using this method, the following is for you.

I am running 7.04 on my Tosh laptop, and had the exact same error with sending : "Operation In Progress" in Evolution using hotwayd and hotsmtpd.

I felt the issue was in hosts.allow and I was right. Please add the following line to /etc/hosts.allow :

```

hotsmtpd: 127.0.0.1 2500

```

This was the end-all-be all of my issues, and now sending works fine. I hope it helps with anyone else who is having the issue.

Also, to mention, I have configured xinetd with option "--inetd_compat" as suggested in a post somewhere in this thread. After editing hosts.allow, I did the following:
```

sudo /etc/init.d/inetutils-inetd restart
sudo /etc/init.d/xinetd restart

```

What to do when this appear:

```
sudo: /etc/init.d/xinetd: command not found
```

?

---

### Post by voodew on 2007-07-24
> **beterraba said:**
> What to do when this appear:

```
sudo: /etc/init.d/xinetd: command not found
```

?

If you
```
cd /etc/init.d/
ls xinetd
```
And have nothing, then you don't have xinetd installed.

---

### Post by beterraba on 2007-07-24
So I tried 

```
 sudo apt-get intall xinetd
```

and I just installed it, but this folder remains empty.

Sugestions? :(

---

### Post by voodew on 2007-07-24
> **beterraba said:**
> So..

If you don't have xinetd installed, you should be able to follow the instructions of the original post. There's something weird going on with my ability to send a password now, but I'm able to receive messages. Try the page 1 post and tell me your results.
If you really want xinetd, then the code is:
```
sudo apt-get install xinetd
```
I hope the original poster updates and posts a how-to for xinetd.

---

### Post by voodew on 2007-07-24
> **beterraba said:**
> So I tried 

```
 sudo apt-get intall xinetd
```

and I just installed it, but this folder remains empty.

Sugestions? :(

OK, I'm stumped, I don't understand how xinetd would be installed and the command xinetd not be present in /etc/init.d/ . That's part of the installation. Do you have a weird source installing the program?

---

### Post by voodew on 2007-07-24
> **beterraba said:**
> So I tried 

```
 sudo apt-get intall xinetd
```

and I just installed it, but this folder remains empty.

Sugestions? :(

I assume that you followed the instructions at the beginning of the thread. What wasn't working that required you to install xinetd?

---

### Post by beterraba on 2007-07-24
> **voodew said:**
> I assume that you followed the instructions at the beginning of the thread. What wasn't working that required you to install xinetd?

The problem which I must to pay money to have acess. =\

---

### Post by voodew on 2007-07-25
> **beterraba said:**
> The problem which I must to pay money to have acess. =\

How old is your account? Microsoft doesn't give WebDAV access to new accounts and you'll normally get a message saying that you need to pay for access. I suspect that new accounts are given WebDAV after they mature. You might want to look into POP3Hot, that should work.

---

### Post by juanbretti on 2007-07-31
> **unique said:**
> Or better yet just use...
```
pop3hot.com
```
as your pop3 server and your set. :-\"
Does anyone has tried this [http://v3.izymail.com/how.aspx]("http://v3.izymail.com/how.aspx")?

---

### Post by gordonh on 2007-08-01
I have hotsmtp installed but there are occasions when I get the "broken pipe" error.

When I do, evolution just sits there waiting for the OK button to be pressed and so when I do, there's a long wait while all the spam is downloaded.

BTW I tried pop3hot.com as server at got a message to the effect "domain name not found"

---

### Post by juanbretti on 2007-08-01
> **gordonh said:**
> BTW I tried pop3hot.com as server at got a message to the effect "domain name not found"

I read in Google ([http://javedmandary.blogspot.com/2007/03/reading-your-hotmail-email-directly.html](http://javedmandary.blogspot.com/2007/03/reading-your-hotmail-email-directly.html)) that [http://www.izymail.com]("http://www.izymail.com") and [http://www.pop3hot.com]("http://www.pop3hot.com") are the same service, the same company.

What we need is a free solution for *Izymail.com*

---

### Post by gordonh on 2007-08-03
> **pepemosca said:**
> I read in Google ([http://javedmandary.blogspot.com/2007/03/reading-your-hotmail-email-directly.html](http://javedmandary.blogspot.com/2007/03/reading-your-hotmail-email-directly.html)) that [http://www.izymail.com]("http://www.izymail.com") and [http://www.pop3hot.com]("http://www.pop3hot.com") are the same service, the same company.

What we need is a free solution for *Izymail.com*

I've just registered with izymail (it says on their site that pop3hot is replaced by izymail)

There's some sort of limitation on the free registration after thirty mails, so I'll see what happens then.

If Izymail isn't a success for any reason I'd like to hack the dialogs so that they default to OK and go away after 10 seconds (I'm a professional mainframe developer), but I need someone to tell me where to look for the code to change.

It would be a good way for me to start to use non dinosaur languages

---

### Post by RavanH on 2007-08-03
Thanks, Indras, for this excellent How-To!

No external services (like IzyMail or whatever) needed... that :guitar:s

So this one goes in my signature :)

--ravan

---

### Post by 2scoops on 2007-08-04
Hi,
Just wanted to say fantastic "how-to" - Really enjoying Ubuntu/Linux & working out all the little tips & tricks everybody takes for granted in Windose..

But after my searching - trial & error I am unbale to send an email through evoultion.. I can recieve all my emails, no problem but when I try to send I get an error about contacting 127.0.0.1

I have tried the :-

hotsmtpd: 127.0.0.1 2500
&
sudo /etc/init.d/inetutils-inetd restart
sudo /etc/init.d/xinetd restart

When I type "sudo /etc/init.d/xinetd restart" I get an error about it not being found..

Can anybody point in the right direction..

Thanks
2scoops

---

### Post by jw5801 on 2007-08-05
At above:
xinetd shouldn't be installed on your system unless you've used it for anything else, so the second command you have above is redundant, hence the "command not found" error. As for the sending error, your sending service is definately SMTP using the server 127.0.0.1:2500 (a colon not a space like you've written above), and your entry into inetd.conf (the line relevant to sending that is) definately starts with 2500?

On another note, has there been any resolution to the "inbox not found on server" issue? I believe that it may have something to do with the difference between hotmail, and windows live mail. If anyone has this working who uses live mail rather than old school hotmail then that would prove me wrong, but are the people getting this error using windows live mail? Hopefully they're still checking this thread...

---

### Post by Setebos on 2007-08-05
The problem persisted after I switched back to hotmail, sadly.

---

### Post by gordonh on 2007-08-06
> **gordonh said:**
> 
There's some sort of limitation on the free registration after thirty mails, so I'll see what happens then.


As promised;

after the 30 mails they only give text only mails, and they won't allow updating (deleting) of mails from your Email client.

might be OK for some users but not me.

---

### Post by juanbretti on 2007-08-09
> **gordonh said:**
> As promised;

after the 30 mails they only give text only mails, and they won't allow updating (deleting) of mails from your Email client.

might be OK for some users but not me.

What do you mean with "updating (deleting)"?
Thanks for the "review" about the service!

---

### Post by gordonh on 2007-08-11
> **pepemosca said:**
> What do you mean with "updating (deleting)"?
Thanks for the "review" about the service!

Synchronization of the account.  

When you've deleted mails from the client (evolution in my case), they should also be deleted from the server

---

### Post by sehe on 2007-08-11
why does nobody *ever* worry about privacy/security issues 

(cf. pop3hot.com, izymail and other scammers)

---

### Post by juanbretti on 2007-08-11
> **gordonh said:**
> Synchronization of the account.  

When you've deleted mails from the client (evolution in my case), they should also be deleted from the server

Thanks!

---

### Post by d4x2hhhy on 2007-09-06
Worked almost perfectly.  Im getting mail no worries and after ticking the no delete box im also leaving a copy on hotmail, my inbox is somewhat emptier than before tho!

But...it wont send mails, ive set it up as I believe is correct but get an error.

---

### Post by juanbretti on 2007-09-06
> **d4x2hhhy said:**
> Worked almost perfectly.  Im getting mail no worries and after ticking the no delete box im also leaving a copy on hotmail, my inbox is somewhat emptier than before tho!

But...it wont send mails, ive set it up as I believe is correct but get an error.


But you can only download (or lets say "get") 20 mails? and then... bum! no more service?

Could you tell me more about this?

Thanks!

---

### Post by d4x2hhhy on 2007-09-06
no ive got 500.  it did stall every so often but got them all now.  wouldnt say it only gets 20 tho.

---

### Post by juanbretti on 2007-09-06
> **d4x2hhhy said:**
> no ive got 500.  it did stall every so often but got them all now.  wouldnt say it only gets 20 tho.

Thanks for the info!

---

### Post by RonP on 2007-09-09
works great thankyou

---

### Post by charlieab1 on 2007-09-14
Thanx for this thread been searching the internet to find out how to do it. Thanx charlie

---

### Post by maryjanua on 2007-09-21
damn after all that it says i have to pay ( which i aint about to do)
how do i get rid of it now?:(

---

### Post by Kedster on 2007-09-22
i get this
Error while performing operation.

Host lookup failed: drytel.mail: Name or service not known

and this
Error while Fetching Mail.

Could not connect to 127.0.0.1: Connection refused

---

### Post by ShuaM75 on 2007-09-23
Hi, this looks like a great tut, but I'm having trouble with step three where you enter:

sudo gedit /etc/inetd.conf

When I do the Terminal does nothing, just sits there with the cursor blinking on a new line.
Am I entering this correctly or is there more I need to learn about using the Terminal?

Any thaughts would be apreciated and as always I love the Linux comunity.

Oh and by the way I'm running:
    Ubuntu 7.04 Feisty Fawn
    All current up dates on a fresh install, ie: no other addons

System:
    HP pavilion ze4500 (also called ze4560us)

Thanks Shua

---

### Post by pkfz on 2007-10-01
Wonderful. Thank you very much. Total newbee, it worked just following the explanation.

---

### Post by Anthony M on 2007-10-07
I just followed the OP's instructions for setting up my hotmail through evolution, and evolution took all my inbox messages and left my hotmail server inbox empty. 

I know he said add '-r' at the end of the pop3 script if you want this to be done, so I excluded the '-r'. Why did this happen?

Is there any way I can reassociate evolution and hotmail server so I can have my inbox with my old messages online?

---

### Post by Stienus on 2007-10-08
super thanx dude !!!

---

### Post by fuzzylogic on 2007-10-08
I have Ubuntu 7.04 but seem to have a problem entering necessary information to access email account. When ask to enter server I use comcast.net but my email is yahoo.com, how can I make it work? I know  
I'm asking a silly question to those who's understand of computers way beyond my level.

Fuzzy

---

### Post by mlapaglia on 2007-10-10
Worked flawlessly. Thanks for the great tut!

---

### Post by Doomguy0505 on 2007-10-18
I get an error saying "you have to PAY to have WebDAV access"

---

### Post by Quartieri on 2007-10-19
i have my hotmail account for at least 8 years but i still got the message that i have to pay for the WebDAV access.. is there any way to change this situation? or i just have to wait for more 6 years and try it again?

btw, the tut was perfect, only this anoying problem bugs me..

---

### Post by jw5801 on 2007-10-20
No there's no way to change it. And I don't think waiting any length of times will mean Microsoft making access free again. If you upgraded to the Windows Live Mail thing rather than sticking with traditional hotmail, then that would explain why you're required to pay now. I use GMail now, since they have a free pop server.

---

### Post by jjfourtwenty on 2007-10-23
Worked first time! one of the biggest things I missed about windows is now in ubuntu! awsome.

---

### Post by chocoboyz on 2007-10-23
Worked like a charm. Thank you!

---

### Post by corney91 on 2007-10-24
Brilliant! Thank you so much!

---

### Post by FdWalkerGT on 2007-10-26
Receiving this when I try send and receive.

Unable to connect to POP server 127.0.0.1.
Error sending username: -ERR Please log in with USER first

Please enter the POP password for [email]XXXXXXX@homail.com[/email] on host 127.0.0.1



Any Ideas?


Thanks

---

### Post by adolfofoliaco on 2007-10-31
I just update from 7.04 to 7.10 and it does not work it used to work on 7.04 any help

---

### Post by doppis on 2007-11-01
Is there still no fix for this?

Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Unable to find folder inbox on remote server

---

### Post by aeg1s on 2007-11-04
Thanks Indras!  Worked perfectly...

---

### Post by yellowpaseo on 2007-11-04
When I try to get my email via hotmail I get this error when I start up evolution:
Unable to connect to POP server 127.0.0.1.
Error sending username: -ERR Command not implemented

Please enter the POP password for [email]yellowpaseo@hotmail.com[/email] on host 127.0.0.1

Any ideas guy?
Thanks in advance

---

### Post by scituatejohn on 2007-11-16
Be warned, this thing can seriously mess things up on your Hotmail inbox.  I followed the instructions on the first page.  This thing really didn't work out for me because it deleted everything in my inbox.  That was the last thing I wanted it to do.  Now I cannot check my email on another computer.  This is a bummer for me.  Does anyone know how I can get the emails back into my inbox?

---

### Post by praveenpious on 2007-11-17
Thanks for the info

---

### Post by lotacus on 2007-11-18
I'm wanting to try this, however, I think it's quite out dated, and probably risky. I could be wrong though.  The new windows live mail application seems to work just fine to access hotmail, because that is what it's for. I am sure if someone took a deeper look into that application, there may be a better way for evolution to access hotmail.

---

### Post by treesurf on 2007-11-25
This used to work just fine for me.  However, now that I upgraded to Gutsy it no longer works.  I went through the whole process in the first post again just to make sure, but no luck.

Any suggestions would be greatly appreciated.

---

### Post by treesurf on 2007-11-25
Never mind, problem solved, I feel really silly.  I just noticed now noticed that for some reason the upgrade to gutsy commented out the first line in my /etc/inetd.conf.  I fixed that and now I have hotmail again.

---

### Post by voodew on 2007-12-11
> **Quartieri said:**
> i have my hotmail account for at least 8 years but i still got the message that i have to pay for the WebDAV access.. is there any way to change this situation? or i just have to wait for more 6 years and try it again?

btw, the tut was perfect, only this anoying problem bugs me..

I can't find any info regarding up-to-date webdav policies. I sent hotmail support an email requesting information on WebDAV access, I'll post the response once I get it. I've had my account since 2002 and I have webdav access. The newest article I've seen is from 2004. Hopefully, I get a response, but if it's an arbitrary process, I doubt I will.

If you don't have webdav access, I suspect that you wouldn't be able to access your account from Outlook Express or Outlook. Can anyone verify this?

---

### Post by voodew on 2007-12-12
> **treesurf said:**
> This used to work just fine for me.  However, now that I upgraded to Gutsy it no longer works.  I went through the whole process in the first post again just to make sure, but no luck.

Any suggestions would be greatly appreciated.

I'm using Gutsy and it works for me. However, I make it a common practice to set it up using xinetd instead of inetd. Around page 10 or 11 is the configuration that I used for 7.04 and 7.10.

I use xinetd because most new applications (like vmware) require it which disables inetd. I think inetd will eventually be phased out. If the original poster doesn't include xinetd, I'll probably make my own how-to and link it to this topic for inetd info. My only problem is that I'm looking for refinement of my xinetd settings because I know a lot of what I have in their is unnecessary.

---

### Post by audiofreq on 2007-12-13
> **reid said:**
> This is a great tutorial, very helpful, thanks.

My install was however using xinetd instead of inetd.  Is this installed autimatically with Ubuntu?  Xinetd is considered more secure than inetd, so I decided to keep it instead of installing inetd.  Anyway, to get xinetd to read your inetd.conf, and incorporate those rules into it's functionality you can do this:

Edit the startup script that calls xinetd.
```
sudo gedit /etc/init.d/xinetd
```
Change this under the 'start' case:
```
start-stop-daemon --start --quiet --background --exec /usr/sbin/xinetd -- -pidfile /var/run/xinetd.pid $XINETD_OPTS
```
By adding the '-inetd_compat' argument:
```
start-stop-daemon --start --quiet --background --exec /usr/sbin/xinetd -- [COLOR="Red"]-inetd_compat[/COLOR] -pidfile /var/run/xinetd.pid XINETD_OPTS
```
Then, restart xinetd:
```
sudo /etc/init.d/xinetd restart
```

I got that nugget from /usr/share/doc/xinetd/README.Debian

Thanks again for the great tutorial - I had no idea this was even an option.


This one did it for me.

No luck using inetd

Was just getting a connection refused error.

---

### Post by gammyhand on 2007-12-17
I find it is taking ages to download my messages. Is this an accepted limitation of this method of bolting hotmail onto evolution?

---

### Post by gleble on 2007-12-18
Got Evolution to handle my hotmail. One problem though, it is not showing any junk mail. Any ideas?

---

### Post by voodew on 2007-12-19
> **gleble said:**
> Got Evolution to handle my hotmail. One problem though, it is not showing any junk mail. Any ideas?

I couldn't find an obvious way to download the junk mail folder in evolution. However, if you really want the junk, then set your hotmail account preferences to accept most (there isn't one for all) emails. Also delete your "Safe" and "Unsafe" lists.
After that, you can use filtering in evolution to separate the emails into junk and good emails if you wish.
Sorry, that's the best I can come up with. If anyone knows how to download from all folders, I'd like to know the trick:)

---

### Post by gleble on 2007-12-19
I don't really want junk, it's just that receipts and other important matters end up there. You don't know how to transfer address books do you?

---

### Post by nikoPSK on 2007-12-19
it says it can't find the folder "inbox"...

---

### Post by bluebrew on 2007-12-26
-Ok I tried to set mine up with the tutorial and didn't make it past the first command
I'm running Gutsy...I'll post all the error message that I get When I type in "sudo apt-get update" from the Terminal I get :

"joey@joey-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Translation-en_CA                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Translation-en_CA
-gutsy-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Fetched 3B in 0s (4B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
joey@joey-desktop:~$ "

=And assuming my system was already up to date cause it downloaded alot of updates after I installed gutsy I decided to skip the install command and put "sudo apt-get install inetutils-inetd" and still got the same error :

joey@joey-desktop:~$ sudo apt-get install inetutils-inetd
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
joey@joey-desktop:~$ 

-So it seems as if I gotta run that dpkg --configure -a' to correct the problem...I have no idea what that is or how to fix it

needless to say I'm still very new with Ubuntu

Thanx in Advance.

---

### Post by bluebrew on 2007-12-26
Dis-regard my last post....I found a easy work around
I set up a forwarding rule from hotmail to my gmail and added my gmail to evolution which was much much easier

unless some1 knows what this error message is "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"

Thnx,comming from a new ubuntu user =)

---

### Post by RavUn on 2007-12-28
Still no word on the "-ERR Hotmail said you must pay money to have WebDAV access", eh?  I saw on some site that you have to sign up for MSN premium or Hotmail Plus to get WebDAV access now...

Would anyone care to post how to go through gmail or gotmail using evolution to get hotmail email?  if that's possible...

---

### Post by bluebrew on 2007-12-29
Hi this is what I done to get my hotmail to Evolution and worked great for me
I signed into my hotmail acct,went to options and selected forward my messages,set it to forward to my gmail acct
signed into gmail,went to settings to make it pop3 enabled
then I followed this [https://help.ubuntu.com/community/UsingGmailWithEvolution](https://help.ubuntu.com/community/UsingGmailWithEvolution) to get gmail into Evolution
hope that helps,worked flawlessly for me




> **RavUn said:**
> Still no word on the "-ERR Hotmail said you must pay money to have WebDAV access", eh?  I saw on some site that you have to sign up for MSN premium or Hotmail Plus to get WebDAV access now...

Would anyone care to post how to go through gmail or gotmail using evolution to get hotmail email?  if that's possible...

---

### Post by mandrill on 2007-12-29
am I missing something here? install freepops from the site, update the lua files (with the updater supplied) enter server as localhost;2000 (for evolution) or localhost port 2000 with other clients, and all the other normal stuff, and you can get your hotmail - as well as just about any other web-based email you want. simple.

---

### Post by alphapenguin on 2008-01-01
> **treesurf said:**
> Never mind, problem solved, I feel really silly.  I just noticed now noticed that for some reason the upgrade to gutsy commented out the first line in my /etc/inetd.conf.  I fixed that and now I have hotmail again.

I've been having troubles as well since I have upgraded to Gutsy. used to work in 7.04, but now I get this message:


Error while Fetching Mail.

Could not connect to 127.0.0.1: Connection refused


Cant figure out what is up with this one.


My hotmail accounts are old, and have no problem accessing them with MS Outlook either. I might just have to abandon these addresses if I cant get them working.

---

### Post by mandrill on 2008-01-01
I believe the freepops autoscript is for the newer hotmail, but all you have to do is "upgrade" it, not trash it.....the error you are getting is also what happens when the freepops daemon is not running. from terminal 'freepopsd' will get it running but you can/should have it start  as a service when you fire up your pc......

---

### Post by switlikbob on 2008-01-02
> **forgeuk said:**
> OK, mine's working fine, thanks to the original poster!

This is more of an evolution question, I'd like my hotmails to go into a seperate folder that I've just made, but I can't seem to see a way to do a message rule for it. Is there a way to set up a rule to filter by account rather than by subject or sender?


[COLOR="Red"]Ignore that...found it, its Add then choose source account from the drop down...nice[/COLOR]

Could you please explain this in more detail?  I have 3 hotmail accounts setup in Evolution.  The problem is, all of the contents of all 3 hotmail inboxes ends up in one inbox in evolution (On this Computer).  I need to keep them seperated, as each hotmail account serves its own purpose.  I couldn't find the "choose source account" from any drop down box.  TIA!

---

### Post by MDaugaard on 2008-01-05
Excellent guide. Works like a charm.

Thanks a million

---

### Post by Kevbert on 2008-01-09
Thanks for an excellent post.  It works like a charm - I can now use Gmail, Skymail and Hotmail in Evolution.:)

---

### Post by ladybumavere on 2008-01-20
Totally worked, and very very easily!


Thank you very much!


:guitar:

---

### Post by nikoPSK on 2008-01-21
It says can't find the folder "inbox". :confused:

---

### Post by gocharlie on 2008-01-22
When I type code: sudo gedit /etc/inetd.conf all I get is an empty file. Why is that?

When I did the preceding installation I was asked if I wanted it to automatically configure hotway (I think that was the question) but I chose to do it manually. Can it have anything to do with that? In that case how can I reset the changes to start all over?

Thx

---

### Post by mandrill on 2008-01-22
> **mandrill said:**
> am I missing something here? install freepops from the site, update the lua files (with the updater supplied) enter server as localhost;2000 (for evolution) or localhost port 2000 with other clients, and all the other normal stuff, and you can get your hotmail - as well as just about any other web-based email you want. simple.

Also, my next post explains the command for terminal.

Good Luck and may the Force be with you!

---

### Post by mandrill on 2008-01-22
> **mandrill said:**
> I believe the freepops autoscript is for the newer hotmail, but all you have to do is "upgrade" it, not trash it.....the error you are getting is also what happens when the freepops daemon is not running. from terminal 'freepopsd' will get it running but you can/should have it start  as a service when you fire up your pc......

here it is, so you do not have to backtrack.....

---

### Post by wizzer on 2008-01-23
Thanks so much!!  Works perfectly!:popcorn:

---

### Post by Vivica_Gsy on 2008-01-24
This is a brilliant put together walk through.
I've never really been into Evolution before, largely because i never knew how to get Hotmail supported.

Whoever worked all this out is obviously in another league of intelligence to me :-D

---

### Post by msktje on 2008-01-26
> **yellowpaseo said:**
> When I try to get my email via hotmail I get this error when I start up evolution:
Unable to connect to POP server 127.0.0.1.
Error sending username: -ERR Command not implemented

Please enter the POP password for [email]yellowpaseo@hotmail.com[/email] on host 127.0.0.1

Any ideas guy?
Thanks in advance

take a look at the workaround here:
[https://bugs.launchpad.net/evolution/+bug/140460](https://bugs.launchpad.net/evolution/+bug/140460)

I think i had the same problem it worked for me.

---

### Post by mandrill on 2008-01-26
" Originally Posted by yellowpaseo  View Post
When I try to get my email via hotmail I get this error when I start up evolution:
Unable to connect to POP server 127.0.0.1.
Error sending username: -ERR Command not implemented

Please enter the POP password for [email]yellowpaseo@hotmail.com[/email] on host 127.0.0.1

Any ideas guy?
Thanks in advance"

Hotmail is not a POP - freepops runs an autoscript essentially signing you in to Hotmail as "you"....as if you were actually signing in from the website. The freepops daemon runs as a service, and is configured thusly -  localhost:2000 - in Evolution, and the error you are getting more than likely means that you have not invoked the command freepopsd, and the daemon is not running. ( POP server 127.0.0.1 *is* your own pc/freepops). Obviously invoking from the terminal every time you want to check your mail is inconvenient, so set it as a service that starts when your pc does. In most cases if installed from the website it works right off the bat. 

Also, update to the new livemail, because I think the autoscript is set for that, and make sure you update the freepops lua files with the updater provided from the website.

Provided with no guarantees! Good Luck!

---

### Post by alphapenguin on 2008-02-02
amazing, I had this working at one point with Fiesty, upgraded to gutsy, things went to poo. I couldnt get hotmail to work anymore.  Came back and tried again like 2 months later. Followed steps on the first post <again> exactly <again> and voila. PERFECT! 

To the original poster: Thank you! and thanks to everyone else who is willing to help out!

---

### Post by Setebos on 2008-02-03
Must say that the fact I've never got this working has temporarily infuriated me every time I've thought about it. Less to do with Ubuntu, more to do with the spectacularly non-wonderful Hotmail. I was one of the poor saps getting "could not find folder inbox on remote server" which apparently can't be resolved.

Experimentally tried out the xinetd stuff, and now I get "connection refused." What's more annoying is that I can't even forward my emails to my gmail account, since MS disallow that too. Wunderbar.

Edit: Well, resolved the connection refused stuff with the handy -inetd-compat stuff; back to ye olde "could not find folder inbox on remote server" :(

---

### Post by ebozzz on 2008-02-04
After reading this it appears that if a MSN Premium or Live account is in use, no workaround has been found short of the *forward mail* solution that was posted a couple of pages back, right?

---

### Post by mandrill on 2008-02-05
Not So. When I use msn for mail I use Livemail. works fine. Update the  autoscripts with the freepops updater, no problems. Premium I can't vouch for...

---

### Post by ebozzz on 2008-02-05
> **mandrill said:**
> Not So. When I use msn for mail I use Livemail. works fine. Update the  autoscripts with the freepops updater, no problems. Premium I can't vouch for...

Thanks Mandrill. Believe it or not, I've got it working without any of the other configuration steps. This is what I configured.....

INCOMING
User name = [email]xxx@q.com[/email]
Server name: pop3.live.com
Use secure connection: SSL Encryption

OUTGOING
Server name: smtp.live.com
User name = [email]xxx@q.com[/email]
Use "Server Requires Authentication": TLS Encryption 

The outgoing server would not work with SSL encryption. I selected TLS and "Server Requires Authentication" for SMTP ( smtp.live.com) and POP with SSL for the incoming server (pop3.live.com). :)

By the way, what do you know about *Fencewalk* and *Peck Ya Neck*? :guitar:

---

### Post by msharmony2001 on 2008-02-05
I am very new to Lenux. I just installed this weekend.
Where does the pop3hot.com get entered? I tried it in a couple places and it only made it worse. I have it where it received the mail but does not send.I get a message like this,

Error while performing operation.

Could not connect to 127.0.0.1: Connection refused

---

### Post by ebozzz on 2008-02-05
> **msharmony2001 said:**
> I am very new to Lenux. I just installed this weekend.
Where does the pop3hot.com get entered? I tried it in a couple places and it only made it worse. I have it where it received the mail but does not send.I get a message like this,

Error while performing operation.

Could not connect to 127.0.0.1: Connection refused

Did you try the settings that I just posted? Forget about all of the other stuff for a few minutes and give them a try......

---

### Post by mandrill on 2008-02-05
Ebozzz - I can tell from the settings you showed me that msn premium must be a paid service - in which case you would not need freepops (for that account). However, you would need it for most other web-based email services. The only folks I know of that give you free
POP access to mail are (usually) your ISP provider, Gmail, or your employer.....something like that.....

Peace.

---

### Post by ebozzz on 2008-02-05
> **mandrill said:**
> Ebozzz - I can tell from the settings you showed me that msn premium must be a paid service - in which case you would not need freepops (for that account). However, you would need it for most other web-based email services. The only folks I know of that give you free
POP access to mail are (usually) your ISP provider, Gmail, or your employer.....something like that.....

Peace.

You're probably right as my ISP, Qwest, provides The Premium/Live Mail accounts through a business arrangement with MSN. What the heck, it works! Thanks for the insight.....

---

### Post by Person_1873 on 2008-02-05
Windows Live Hotmail is now using HTTP, so can anyone tell me how to use that in evolution, btw i know this because i downloaded windows live mail on my win install and it told me so XD the new server is [http://mail.services.live.com/DeltaSync_v1.0.0/sync.aspx](http://mail.services.live.com/DeltaSync_v1.0.0/sync.aspx)
so yea, http support for evolution???

---

### Post by mandrill on 2008-02-06
> **Person_1873 said:**
> Windows Live Hotmail is now using HTTP, so can anyone tell me how to use that in evolution, btw i know this because i downloaded windows live mail on my win install and it told me so XD the new server is [http://mail.services.live.com/DeltaSync_v1.0.0/sync.aspx](http://mail.services.live.com/DeltaSync_v1.0.0/sync.aspx)
so yea, http support for evolution???

I guess you have to decide if you want all the crap that comes with downloading microsoft's version of how THEY want you to do things on a windows box ( hey, Vista's a huge hit, huh?) - or whether you just want to get your Livemail on your Ubuntu box. Don't get me wrong, I use XP pro on my production machine - but with *my* rules, as far as I can. I have the complete Office for small business suite installed, nice graphics, printers, scanners, external hard drives, media server, large sound system, etc...but I do not, and refuse to have, bloated, resource absorbing, driver conflicting, unnecessary, pseudo-spyware BS crowding up my pc, forced upon me by the manufacturer. I own it, I didn't RENT it from microsoft.

So, rant over. The guide I have presented will (and does) work very well on Evolution, and most every other mail client I know of, and it even works on Windows. (Without downloading anything - except freepops & a decent mail client, no outlook express!)

So, again, rant over, have fun. Good Luck. Peace.

---

### Post by msharmony2001 on 2008-02-07
Thank you very much. It works very well now.

---

### Post by mandrill on 2008-02-07
> **msharmony2001 said:**
> Thank you very much. It works very well now.

You are quite welcome. Welcome to Ubuntu.

---

### Post by hgurol on 2008-02-15
Hi,

Does the instructions on the first page still valid?

The writing is not only too old but I have also noticed some alterations to that instructions through out the other pages.

Im a bit confused for which one to follow.

Thanks,
Halil


<< what a bad, poor and weak first post is this :) >>

---

### Post by mandrill on 2008-02-15
> **mandrill said:**
> am I missing something here? install freepops from the site, update the lua files (with the updater supplied) enter server as localhost;2000 (for evolution) or localhost port 2000 with other clients, and all the other normal stuff, and you can get your hotmail - as well as just about any other web-based email you want. simple.

This is the easiest, most expedient way to accomplish what you are trying to do. Good Luck!

---

### Post by NEUR0M4NCER on 2008-02-16
Heh... okay. Y'reckon it'd be possible to get Hotmail notification in Conky a-la Gmail? Not too well versed in these things, but i'm loving Conky's versatility.

Regards!

(edit) Yeah, I know I could forward the Hotmail to Gmail, but it just seems a bit messy - i'd like to have a seperate Hotmail notifier...

---

### Post by Fred_E _krugar on 2008-02-17
I have tried forwarding my hotmail to gmail but hotmail will not allow me to do that or am I missing something??

---

### Post by mandrill on 2008-02-17
> **Fred_E _krugar said:**
> I have tried forwarding my hotmail to gmail but hotmail will not allow me to do that or am I missing something??

You do not have to forward anything anywhere. Go here:

[http://www.freepops.org/en/](http://www.freepops.org/en/) 

  and download the program and its updater, They are self installing: make sure your email accts are set up 1st or you will get error messages. See my prior posts in this thread. Good Luck!

---

### Post by Fred_E _krugar on 2008-02-17
Could you possibly do a tut on the correct ways to use freepops and setup??

---

### Post by ebozzz on 2008-02-17
I don't know if you missed this but there is a FreePops user's manual [here]("http://www.freepops.org/en/doc.shtml")....

A tutorial is [here]("http://www.freepops.org/en/tutorial/index.shtml")......

---

### Post by ebozzz on 2008-02-17
This may also prove to be helpful. It's a thread from the FreePops forum....

[ Hotmail & Evolution]("http://freepops.diludovico.it/showthread.php?t=4529&highlight=Evolution")

---

### Post by Fred_E _krugar on 2008-02-17
when I put in terminal freepopsd it says unable to bind on 0.0.0.0:2000

---

### Post by Fred_E _krugar on 2008-02-17
ok got it figured out. Do I have to start Freepops every time I want to check my mail ??

---

### Post by mandrill on 2008-02-17
> **Fred_E _krugar said:**
> ok got it figured out. Do I have to start Freepops every time I want to check my mail ??

Nope. The daemon will start when you start the pc. If you have sudden
dysfunction on an account, run the updater - it will (should) have the new, current autoscript for signing into almost any web-based mail.

In case you have to start freepops manually run "freepopsd" in terminal. It will only run as long as the terminal is open, though.

---

### Post by r3v3ng3 on 2008-02-18
This is so frustrating! :@:@:@

I've spent almost 3 hours trying to get this to work with hotmail and the only thing I can do is read messages!
I've just decided to screw it and use gmail as the smtp server.
If anyone has a solution please email/pm me

---

### Post by brummie on 2008-02-18
Works great, thx :)

---

### Post by mandrill on 2008-02-18
> **r3v3ng3 said:**
> This is so frustrating! :@:@:@

I've spent almost 3 hours trying to get this to work with hotmail and the only thing I can do is read messages!
I've just decided to screw it and use gmail as the smtp server.
If anyone has a solution please email/pm me

If your local ISP smtp doesn't work or is not available, then I believe your hotmail/livemail would have to be a paid version. I know that it works just fine if you use the freepops updater, and "upgrade" or use livemail....I use it, as do many others - works fine.

---

### Post by Truedream on 2008-02-21
is there a solution for this error?
 
```
Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Unable to find folder inbox on remote server
```

I looked around alot and cannot find the solution :( will really appreciate it if you can point me to the right thread.

---

### Post by mandrill on 2008-02-21
> **Truedream said:**
> is there a solution for this error?
 
```
Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Unable to find folder inbox on remote server
```

I looked around alot and cannot find the solution :( will really appreciate it if you can point me to the right thread.

I really need more info, but....if it is hotmail (the free kind) it could be a combination of things. Is your pop server set as "localhost:2000" (without the quotes) Unable to connect to POP server 127.0.0.1 is freepops/your machine. And the unable to find inbox thing looks like an imap, not pop issue. (you cannot imap hotmail, that I know of) Have you re-checked that you have .com instead of .net, etc....? Also make sure you have updated freepops with the supplied (but separate) updater? Re-check the details, and post back, or, post your current settings here....If your hotmail is provided through your ISP go back a few pages, there are posts about pop3 settings....

(sometimes just uninstalling and re-installing an email account will fix bugs)

---

### Post by nuytnie on 2008-02-22
Worked perfect! Thanks for this great thread!

---

### Post by Inicholson on 2008-02-29
> **klytu said:**
> 
To set up the additional Hotmail folders, you add a new hotmail account for each one. For example, I have a folder called "Programming" in my Hotmail account. To set it up in Evolution, I created a new Hotmail account using the steps in the howto, but for the username I used [email]my_username@hotmail.com[/email]/Programming and named the new account Hotmail-Programming. Next in Evolution I created a mail folder called Programming. Then I set my message filters to send all mail from that new account to the Programming folder: Edit>Message Filters; Add; for search name I typed programming (I don't think it matters what you put there); Under "find items that meet the following criteria" changed "sender" "is" to "source account" "is" using the selection arrows and chose the new account created; under "then" "move to folder" selected the Programming folder I had created in Evolution. Now when I click "Send/Receive" mail from my Hotmail Programming folder is sent to the mail folder Programming in Evolution.

I tried this for my Junk folder but it tells me my password is wrong!  I've put my Hotmail password in and it's working fine for my Inbox but won'y accept it for the Junk folder - have i missed something?


PS;   This is day 2 of my Ubuntu PC -I decided to give it a try on my desktop after my daughter downloaded a trojan which fried my Windows XP installation.  It seems great for email and the web so far.  If I didn't need MS Office for work I'd probably put Ubuntu on my laptop too.

---

### Post by Inicholson on 2008-02-29
> **voodew said:**
> I can't find any info regarding up-to-date webdav policies. I sent hotmail support an email requesting information on WebDAV access, I'll post the response once I get it. I've had my account since 2002 and I have webdav access. The newest article I've seen is from 2004. Hopefully, I get a response, but if it's an arbitrary process, I doubt I will.

If you don't have webdav access, I suspect that you wouldn't be able to access your account from Outlook Express or Outlook. Can anyone verify this?

I remember reading on the MSN site some time ago that new Hotmail accounts won't work with Outlook Express but older accounts which have already been used with Outlook Epress will continue to operate that way.  I've always used my Hotmail via Outlook Express (until recently, it won't run on Vista so i have to use Windows Live Mail now).  Presumably old accounts which have never been used with Outlook Express don't have webdav activated and now that Microsoft have changed their policy (to prevent Hotmail being used to send automated spam) webdav can't be activated unless you're willing to pay for it.

I'd like to be able to continue using Outlook Express or something as similar as possible with my Hotmail - it appears that Evolution will work but isn't able to download my Junk folder. (I use it to separate mail form mailing lists - such as this one - from personal and business emails which go to my inbox).  

Would I have any more success with Thunderbird or another program?

thanks

---

### Post by mandrill on 2008-02-29
Wouldn't it be better to have a "dedicated" account for that kind of thing? That's what I do, rather than having to reconfigure hotmail's rules and evolutions ability to decipher things. 
I mean, it can be done, (new folder not called junk, for one thing), but how about setting up a "Junk" email account where all that stuff goes.....much easier! Also, you might consider using a different mail provider. (Fastmail, Mail.com, etc...) all the configs would be the same for them as hotmail without the headaches.

---

### Post by mrobinson_sr on 2008-03-01
I feel kind of left out, everyone post that this works great.  I was following the directions and it was working fine until I entered:

sudo gedit /etc/inetd.conf

Thats when it crashed and told me:

michael@michael-desktop:~$ sudo gedit /etc/inetd.conf
sudo: gedit: command not found

I tried moving on any way and get:

michael@michael-desktop:~$ pop3 stream tcp nowait nobody /us                                                                                      r/sbin/tcpd /usr/bin/hotwayd
bash: pop3: command not found


Any thoughts on what's up?:confused:

---

### Post by mandrill on 2008-03-01
Here is absolutely the easiest way to get hotmail, or almost any webmail,  through Evolution, or any other mail client:

 Originally Posted by mandrill  View Post

Install freepops & updater from the site,[http://cybertech.altervista.org/freepops.php](http://cybertech.altervista.org/freepops.php), Update the freepops  database. For Evolution enter pop server as localhost;2000, or localhost port 2000 with other mail clients, and all the other normal stuff, and you can get your hotmail - as well as just about any other web-based email you want. Simple.If you get error message "cannot bind" - make sure you have your email account set up first.There are versions for both I386 & amd64.

This will not work on paid versions of hot/livemail, You will have to use the alternative - also somewhere in this thread....

---

### Post by angry_johnnie on 2008-03-04
> gedit: command not found

Most likely means gedit is not installed.  Gedit is gnome's default text editor.  If you use KDE (kubuntu) type kate instead of gedit.   If you use XFCE (xubuntu)  type mousepad instead of gedit.

---

### Post by mandrill on 2008-03-04
> **angry_johnnie said:**
> Most likely means gedit is not installed.  Gedit is gnome's default text editor.  If you use KDE (kubuntu) type kate instead of gedit.   If you use XFCE (xubuntu)  type mousepad instead of gedit.

Good catch. Didn't see it first time. That would mean it somehow got uninstalled first, would it not?

---

### Post by mi_were on 2008-03-05
I have just installed freepops and it works like a charm. I can now access/archive my hotmail email from evolution. Thanks everyone.

---

### Post by Furiattl on 2008-03-16
Yeah, so easy.
Hotmail only works with outlook in windows.

---

### Post by Merovius on 2008-03-22
I just installed FreePops with evolution a few days ago and it was working. Now it seems like it checks Hotmail but nothing happens. I have had Hotmail for ever and still get the free POP access. Works well under Thunderbird with Webmail but was hoping to get Evolution up and running. Any ideas?

---

### Post by mandrill on 2008-03-22
[QUOTE=Merovius;4564456]I just installed FreePops with evolution a few days ago and it was working. Now it seems like it checks Hotmail but nothing happens. I have had Hotmail for ever and still get the free POP access. Works well under Thunderbird with Webmail but was hoping to get Evolution up and running. Any ideas?[/QUOTE


With no error messages, just no mail I would suggest that you run the updater. Can you log on to hotmail directly? Also, make sure the daemon is running, the
command to start it is freepopsd, but when done that way it will only run as long as the terminal is open. A good thing to do is mount your system monitor somewhere convenient, like one of your panels, then all you have to do is open it, check running processes, and you'll know whats going on.....also make sure you have updated to the newer version hotmail (livemail) or the script will not work.

---

### Post by taurusx5 on 2008-03-25
I had followed instructions according to this guide:[http://ubuntuforums.org/archive/index.php/t-200408.html](http://ubuntuforums.org/archive/index.php/t-200408.html) to send and receive hotmail from Opera. I am able to receive hotmail but I'm not able to send email. Before my ubuntu 7.10 crashed, I was able to send email. After I re-installed ubuntu, I forgot what I did to configure the settings via smtp to send email through Opera. I know it uses port 25. Does anyone know what are the proper smtp settings to send hotmail email in Opera? Thanks!

---

### Post by mandrill on 2008-03-26
> **taurusx5 said:**
> I had followed instructions according to this guide:[http://ubuntuforums.org/archive/index.php/t-200408.html](http://ubuntuforums.org/archive/index.php/t-200408.html) to send and receive hotmail from Opera. I am able to receive hotmail but I'm not able to send email. Before my ubuntu 7.10 crashed, I was able to send email. After I re-installed ubuntu, I forgot what I did to configure the settings via smtp to send email through Opera. I know it uses port 25. Does anyone know what are the proper smtp settings to send hotmail email in Opera? Thanks!

According to your post, the instructions given in the provided link configure smtp as localhost:2500.........or 127.0.0.1:2500 (2500 is the port #) **Why not use your ISP's smtp settings?**

OR, you could set it up as in my how-to with freepops. Should work in Opera as well, and as a pop account. Much easier. Best of luck!

---

### Post by arella71 on 2008-03-26
I am having trouble getting my email set up with evolution. I have done everything in this forum on a yahoo and windows live account, and nothing works. I would like to bind to a differnet port, but the terminal says the command is not valid (freepops -p port#). I had freepops set up nicely on my windows partion which is on a vm, but I don't want to boot into that just to get mail. I have also tried doing this through opera, again with no responce. Any suggestions would be greatly appreciated.

I am very new to linux, so please don't assume I no what you might be suggesting.:confused:

---

### Post by mandrill on 2008-03-26
> **arella71 said:**
> I am having trouble getting my email set up with evolution. I have done everything in this forum on a yahoo and windows live account, and nothing works. I would like to bind to a differnet port, but the terminal says the command is not valid (freepops -p port#). I had freepops set up nicely on my windows partion which is on a vm, but I don't want to boot into that just to get mail. I have also tried doing this through opera, again with no responce. Any suggestions would be greatly appreciated.

I am very new to linux, so please don't assume I no what you might be suggesting.:confused:

Not sure why you want to bind to different port, unless another client is already listening there. But here is what you can do if you feel brave - ```
sudo gedit /etc/init.d/freepops
```

There's a variable in there named $DEFAULT_DAEMON_OPTS. Drop your switches in there..for example: ```
-p 110 -b MY_COMPUTER (or whatever you want)
```

This is posted as is, no guarantees.

---

### Post by arella71 on 2008-03-26
Thanks, I don't really want to bind to a different port. I just know one that I have already opened for bittorrent- I thought I could use that. Also my ISP blocks port 25 but i can use 587 for sending. Anyways I have not been able to get this work still.:(

---

### Post by mandrill on 2008-03-26
Anybody unable to get your Hotmail through Freepops (like me) as of yesterday or today, they usually have a fix out within 48 hours.

Microsoft puts some effort into stopping the use of automated scripts to access their POP mail - they want you to sign on to the website and get all the ads......

For those of you that are interested, here is a very good article about Freepops and how it works. [http://www.linux.com/feature/119379]("http://www.linux.com/feature/119379")

---

### Post by mandrill on 2008-03-29
> **mandrill said:**
> Anybody unable to get your Hotmail through Freepops (like me) as of yesterday or today, they usually have a fix out within 48 hours.

Microsoft puts some effort into stopping the use of automated scripts to access their POP mail - they want you to sign on to the website and get all the ads......

For those of you that are interested, here is a very good article about Freepops and how it works. [http://www.linux.com/feature/119379]("http://www.linux.com/feature/119379")

Hotmail is working again in Freepops

---

### Post by ph1sh on 2008-04-03
> **Indras said:**
> Okay everyone, after digging around in these forums and googling like I've never googled before, I figured out how to send and receive e-mail through hotmail using Evolution.  I'm throwing together a rough HOWTO for others.  If things need more clarification, let me know and I'll update it.

**First, make sure your system is up to date.  Open up a terminal and type:**

```
sudo apt-get update
```

**Now, install the inet daemon**

```
sudo apt-get install inetutils-inetd
```

**This takes care of all of our dependencies.  Now on to the good stuff...**

```
sudo apt-get install hotway hotsmtp
```

**This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP.  By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.**

```
sudo gedit /etc/inetd.conf
```

**Look for a line like this:**

```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd
```

**By default, hotway leaves a copy of each message it downloads on the server.  I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:**

```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r
```

**And we also need to add a line to get hotsmtpd working, just paste this at the bottom:**

```
2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd
```

**This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon.  Now, save your file, exit gedit, and restart your inetd server:**

```
sudo /etc/init.d/inetutils-inetd restart
```

**If everything is working properly, you'll see this pop up on your screen:**

```
* Restarting internet superserver inetd                            [ ok ]
```

**Now, close out of your terminal and start up Evolution.  It may pop up the first-time use wizard, you can use that if you like.  Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left.  However you choose to do it, here's your information:**

**Email Address:** *xxx*@hotmail.com  (fill in your normal e-mail address that you use to login to hotmail)

**Receive Server type:** POP
**Server:** 127.0.0.1
**Username:** *xxx*@hotmail.com (same as above)
**Security:** No encryption
**Authentication type:** Password
(Remember password checkbox is up to you)

**Send Server type:** SMTP
**Server:** 127.0.0.1:2500
**[X] Server requires authentication** (check this box)
**Use Secure Connection:** No encryption
**Authentication Type:** PLAIN
**Username:** *xxx*@hotmail.com (same as above)
(Optional Remember password checkbox)
Hi, I would love this to work for me.
I followed your instructions, but got an error:
Error sending password: -ERR Unable to find folder inbox on remote server
Is this because it only works with hotmail.com addresses (I've got a hotmail.co.uk address)?
Thank for any help

---

### Post by mandrill on 2008-04-04
---Quote (By P1SH)---Hi, I would love this to work for me.
I followed your instructions, but got an error:
Error sending password: -ERR Unable to find folder inbox on remote server
Is this because it only works with hotmail.com addresses (I've got a hotmail.co.uk address)?
Thank for any help[/QUOTE] 

NO. UK addresses will work only from the actual webpage.(Usually, but with some help,maybe...(eg Thunderbird)

As far as the "how-to" just posted above.....why make new people spend 1/2 hour doing something that can be done in 5 minutes, not to mention all the added steps that increase the likelihood of error? Right now, these folks just wanna get their mail - no need to make it look like they've got to climb Everest first.

Follow my how-to earlier in this thread and you'll see what I'm talking about........

---

### Post by ph1sh on 2008-04-05
Hi mandrill
Thank you very much for your reply. Very helpful. Will read throught the posts of this thread.

---

### Post by A_B on 2008-04-06
Having same problem as ph1sh, only I have a normal msn.com email address. Could it be I'm using the wrong server IP (or whatever it is, the 127.0.0.1 thing) ?

Thanks
Alex

---

### Post by mandrill on 2008-04-06
> **A_B said:**
> Having same problem as ph1sh, only I have a normal msn.com email address. Could it be I'm using the wrong server IP (or whatever it is, the 127.0.0.1 thing) ?

Thanks
Alex

A_B.....get everything **set** in your email first. One step at a time.OK.go to the page of evolution's setup that says Receiving Email.(i've assumed you already filled out the name/email address on the prior page.)
 Under server type choose POP (because that's what freepops is doing for you with scripts)
 Configuration = localhost:2000 No security settings.(except password)
 Fill in name and password, all good so far.Remember the 127.0.0.1 error? Thats freepops telling you "hey! there's nothing on port 2000!
Well, now there is -as long as you downloaded the correct distro version of freepops FROM THEIR WEBSITE, (I believe the one in the distros had some issues) Download the updater, it will run once as user then will ask for root permissions.Run the updater every so often, the freepops daemon is automatic - as your mail should be now.....post back your results, so others can learn as well. 

Peace, Out.

---

### Post by A_B on 2008-04-06
I get this error:

Error while Fetching Mail
Could not connect to localhost: Connection refused

when i change to 'localhost:2500 I get this error:

Error while Fetching Mail
Failed to read a valid greeting from POP server localhost.

Whenever I try to add a spce between 'localhost' and ':', The space changes in '20%'.

Thanks
Alex

---

### Post by A_B on 2008-04-06
oh.. I downloaded the newest freepops. Now it sais "retrieving POP summary" for a while and the just stops.

Thanks

---

### Post by A_B on 2008-04-06
I can send mail from evolution though.

---

### Post by mandrill on 2008-04-06
> **A_B said:**
> I can send mail from evolution though.

Its got to be something simple.Like where it says "username" right
below where you put in localhost:2000 did you put the @msn.com part in? Did you run the updater? Microsoft is notorious for changing little things here and there so you have to logon, But the guys at freepops  are really on top of it- happened last week, back up again in 48 hrs.
Sometimes, just deleting the account and adding it again later will make it work.... are  you using a proxy? Did you put a check mark in the box to remember your password?  Re-check your typing/spelling - its something that simple. Try this - in a terminal type ```
freepopsd
``` leave the terminal open and try getting some mail.....post back success or failure, please,

{ edit - NO spaces between localhost, the colon, and 2000}

---

### Post by A_B on 2008-04-07
When I type "freepopsd" in terminal I get the following error:

Unable to bind on 0.0.0.0:2000

Is it something with a .conf file I have to edit?

Thanks
Alex

---

### Post by mandrill on 2008-04-07
That means freepops can't see any mail account that is sending out on port 2000. Delete your mail account from Evolution. Reboot. On Evolution Identity page put your name and the **whole** email address. Move to next screen called Receiving Mail. At the top there is a drop down menu, choose server type POP. Move to next screen, you should see server type at the top already filled in with POP. In the section below that you see 2 empty boxes under Configuration - server, and username.

For server, use localhost:2000
For username fill in the rest of your email address, so that the whole email address is in that box

Go to authentication type, choose password/remember password.. 

Go to Sending mail page - fill in your smtp info, and under username, put your **complete** email address there. My server doesn't require any
authentication, so I uncheck that box. Next page put account name and you're done.If it doesn't work immediately, reboot, it should clear some cobwebs out and work fine. You are using English, right? Let me know how it goes.

---

### Post by arella71 on 2008-04-07
Ok, I got my mail coming in, but sending is now the issue. I know using windows live mail before that I had to send out of port 587, because my isp blocks port 25. Anyone have any suggestions how I can now push my mail out?

---

### Post by msmarti58 on 2008-04-07
Suddenly this is not working for me since I upgraded to 7.1.0. It did say something like changing hotway or something about port 110 but I disregarded it since I had no clue what it was talking about. When I edited the file it looked different than before but I changed it back to how it was, but it still doesn't work. 

Sorry, I am a Windows user and don't really know much about Linux.

---

### Post by msmarti58 on 2008-04-07
Never mind, spoke too soon. Now I need to work on figuring out how to download my Saved folder and Junk folders. If I can find that post that tells me how...

---

### Post by A_B on 2008-04-07
Error while performing operation.

Welcome response error: Operation now in progress

Welcome response error: Operation now in progress


cant even send mail anymore :(

thanks
Alex

---

### Post by msmarti58 on 2008-04-07
> **klytu said:**
> Found an answer in the hotwayd man pages (quoted verbatim): 



To set up the additional Hotmail folders, you add a new hotmail account for each one. For example, I have a folder called "Programming" in my Hotmail account. To set it up in Evolution, I created a new Hotmail account using the steps in the howto, but for the username I used [email]my_username@hotmail.com[/email]/Programming and named the new account Hotmail-Programming. Next in Evolution I created a mail folder called Programming. Then I set my message filters to send all mail from that new account to the Programming folder: Edit>Message Filters; Add; for search name I typed programming (I don't think it matters what you put there); Under "find items that meet the following criteria" changed "sender" "is" to "source account" "is" using the selection arrows and chose the new account created; under "then" "move to folder" selected the Programming folder I had created in Evolution. Now when I click "Send/Receive" mail from my Hotmail Programming folder is sent to the mail folder Programming in Evolution.

Something I noticed which might not be obvious is that if you want messages you download in Evolution to stay on the Hotmail server so that you can read them later from another location (on the web, for example), you should tick the "Leave messages on server option" when setting up your Hotmail account(s) (Edit>Preferences>Accounts, select an account and click Edit, choose "Receiving Options" tab and tick or clear "Leave messages on server option" as desired). I missed this step when I first set-up Hotmail under Evolution, and when Evolution downloaded my messages it emptied my Hotmail inbox - which is not what I wanted. I had to forward all those messages back to myself in order to access them from the web again.
Tried this and not working, maybe I'm missing something. I need step by step in Evolution using Pop. 

Thanks,

---

### Post by aquinashub on 2008-04-15
Great! Worked parfecto-mondo for me - there doesn't seem to be a "thanks" button on my browser right now.. hmmn. As soon as I find it, I'll give you one Indras!

---

### Post by mandrill on 2008-04-16
> **aquinashub said:**
> Great! Worked parfecto-mondo for me - there doesn't seem to be a "thanks" button on my browser right now.. hmmn. As soon as I find it, I'll give you one Indras!

Have to admit, I'm curious, aquinashub. Which method did you follow?

---

### Post by ubestim on 2008-04-23
Unable to connect to POP server 127.0.0.1.
Error sending username: -ERR Please log in with USER first

could anyone give me a favour?

---

### Post by popodoc on 2008-04-23
I just set the mine up and it work great. thanks

---

### Post by Tnhl1989 on 2008-04-29
I get a error  

E:Malformed line 57 in source list /etc/apt/sources.list (dist parse)

when i enter sudo apt-get update

---

### Post by Ganescha on 2008-05-01
Iget, when trying to send in evolution that "cant send - broken pipe" what does that mean.

---

### Post by gsiliceo on 2008-05-02
GUys microsoft will be closing the access to hotmail, you'll need windows live mail, and something tells me they wont release that tool for linux.
[http://blog.fastmail.fm/2008/04/22/microsoft-closing-external-hotmail-access-by-end-of-june-2008/](http://blog.fastmail.fm/2008/04/22/microsoft-closing-external-hotmail-access-by-end-of-june-2008/)

---

### Post by bisnaguete on 2008-05-04
Veeeery thanks, worked perfectly.

Can i use this in other e-mail managers like Thunderbird?

---

### Post by mandrill on 2008-05-05
> **gsiliceo said:**
> GUys microsoft will be closing the access to hotmail, you'll need windows live mail, and something tells me they wont release that tool for linux.
[http://blog.fastmail.fm/2008/04/22/microsoft-closing-external-hotmail-access-by-end-of-june-2008/](http://blog.fastmail.fm/2008/04/22/microsoft-closing-external-hotmail-access-by-end-of-june-2008/)

I currently use Hotmail. Zero problems. Just have to keep the sign-in scripts up-to-date....(updater)

---

### Post by mandrill on 2008-05-05
> **ubestim said:**
> Unable to connect to POP server 127.0.0.1.
Error sending username: -ERR Please log in with USER first

could anyone give me a favour?

Means the Freepops daemon is not running, and/or port settings incorrect

---

### Post by mandrill on 2008-05-05
> **bisnaguete said:**
> Veeeery thanks, worked perfectly.

Can i use this in other e-mail managers like Thunderbird?

I have been using Freepops with Thunderbird for several years. Thunderbird does have it's own version, called webmail, but it is awkward to use, and is only designed for around 1/2 dozen webmails, compared with Freepops, which takes very little skill or know-how, and will get you virtually any webmail you desire.

---

### Post by ihatejoefitz on 2008-05-05
Worked perfectly. Thank you!

---

### Post by gsiliceo on 2008-05-06
does wine run Livemail?

---

### Post by mandrill on 2008-05-06
> **gsiliceo said:**
> does wine run Livemail?

You can run Outlook through Wine, and a whole lot of other stuff, but I 
wouldn't say that was a good reason to install Wine.....

---

### Post by hugh_h_chen on 2008-05-12
> **mandrill said:**
> Here is absolutely the easiest way to get hotmail, or almost any webmail,  through Evolution, or any other mail client:

 Originally Posted by mandrill  View Post

Install freepops & updater from the site,[http://cybertech.altervista.org/freepops.php](http://cybertech.altervista.org/freepops.php), Update the freepops  database. For Evolution enter pop server as localhost;2000, or localhost port 2000 with other mail clients, and all the other normal stuff, and you can get your hotmail - as well as just about any other web-based email you want. Simple.If you get error message "cannot bind" - make sure you have your email account set up first.There are versions for both I386 & amd64.

This will not work on paid versions of hot/livemail, You will have to use the alternative - also somewhere in this thread....

i really have to say that i absolutely thank Indras for his tuturial and kind thread for this subjuct, many didn't experienced  any problem. But too sad, i tried for about 2 hours with the problem of "Hotmail wants me to pay" thing....

in despair, i uninstalled hotway and Xinetd and tried mandrill's freepops. it turned out to be really easy, for some one like with only some it experience both windows and ubuntu. only hicup was that i used 'localhost' in stead of what should be 'localhost:2000' which i found out somewhere else. as the freepops manual's tutorial only illustrates outlook express which has a tab for proxy/socket. and evolution doesn't have this tab. you have to use  localhost:2000 to specify the socket 2000 that freepops needs.

in non-conclusive conclusion, for a newbie like me, freepops is better.

grateful thanks again for both Indras and mandrill's help.....

---

### Post by hugh_h_chen on 2008-05-12
> **gsiliceo said:**
> does wine run Livemail?

U don't have to use wine for windows anymore.....

if u use freepops, it works in  utuntu, why wine? if some one have problem with live, update and get the freepops hotmail latest plugin which will resolve live mail. as least the freepops faq says so  :-)

each popular webmail domain has its own plugin, just take the plugin for your mail address. if your address if not supported by freepops, well you will have to develop a plugin for my own address, or request someone to help ya...

---

### Post by gsiliceo on 2008-05-12
But is important, because i don't want to run outlook just to get my email im quite comfortable with evolution, i don't need the adv. features and lets just hope the freepops guys manage to reverse ingineer the new protocole microsoft will be rolling out at the end of june.
Otherwise, its [www.hotmail.com](www.hotmail.com) back again. I'm trying to minmize my use of that account but is hard since i have it since 1998.

---

### Post by ooolongT on 2008-05-25
> **mandrill said:**
> Wouldn't it be better to have a "dedicated" account for that kind of thing? That's what I do, rather than having to reconfigure hotmail's rules and evolutions ability to decipher things. 
I mean, it can be done, (new folder not called junk, for one thing), but how about setting up a "Junk" email account where all that stuff goes.....much easier! Also, you might consider using a different mail provider. (Fastmail, Mail.com, etc...) all the configs would be the same for them as hotmail without the headaches.


Bitchin'!  It worked!! :shock: Thanks Mandrill

---

### Post by Gourgi on 2008-06-03
[[IMG]http://img207.imageshack.us/img207/9806/errorag7.th.jpg[/IMG]](http://img207.imageshack.us/my.php?image=errorag7.jpg)
i'm getting the above message
i'm damn sure i 'm typing the correct password for my hotmail account

any ideas ?

[COLOR="Red"]edit[/COLOR] : 
i also tried telnetting and here is the output
```

 telnet localhost 110
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
+OK POP3 hotwayd v0.8.4 -> The POP3-HTTPMail Gateway. Server on gourgi active.
USER XXXxxxXXXXXXxxx@hotmail.com
+OK Username validated, Password required
PASS XXXxxxXXXXXXxxx
-ERR Hotmail said you must pay money to have WebDAV access
```

> -ERR Hotmail said you must pay money to have WebDAV accessthis means i have to pay ?? :confused:

---

### Post by wariskampar on 2008-06-17
Thanks Mandrill, it works!

---

### Post by mandrill on 2008-06-17
> **wariskampar said:**
> Thanks Mandrill, it works!

No problem - glad to be of some help. This community has certainly helped me
enough.....

---

### Post by brianflanery on 2008-06-22
I know this is kind of two years after this was last edited, but I'm trying to do the same thing as mentioned and I get the following error:

> Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Unable to find folder inbox
on remote server

Please enter the POP password for
**xxxx@hotmail.com** on host **127.0.0.1**.

Any ideas?

---

### Post by mandrill on 2008-06-23
> **brianflanery said:**
> I know this is kind of two years after this was last edited, but I'm trying to do the same thing as mentioned and I get the following error:

Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Unable to find folder inbox
on remote server

Please enter the POP password for
[email]xxxx@hotmail.com[/email] on host 127.0.0.1. 



Any ideas?

Depends on which "same thing" you're referring to. There are 2 different methods (with their tutorials) in this thread (yeah, its a tad long) but it looks like you are trying to use mine. So, either your freepops daemon is not running, you have not updated the freepops program, or you have not configured your ports correctly. This is one program you DO NOT want to install from the repos; it is buggy and difficult to update if you are new. Download from website, use the installer provided for whichever architecture you run, including the updater, (there's one just for GDM) install it, update it, and configure evolution mail client pop server as localhost:2000. Everything else is easy. (noticed this - -ERR Unable to find folder inbox) are you trying to run as IMAP?

---

### Post by Paresh on 2008-06-27
This worked first time, great :popcorn:

Only one issue though, it only picks up the inbox, sometimes I get emails that hotmail filters to junk.  Is there anyway of picking that up also?

---

### Post by mandrill on 2008-06-27
> **Paresh said:**
> This worked first time, great :popcorn:

Only one issue though, it only picks up the inbox, sometimes I get emails that hotmail filters to junk.  Is there anyway of picking that up also?

Not sure I understand your question....or more precisely, what you are trying to accomplish?

---

### Post by Paresh on 2008-06-29
If you get an email from someone in your hotmail address book, it's put in the hotmail inbox.

However, if the email is from someone not in your hotmail address book, that email is put in the junk folder.

Is there any way of to access this 'junk' folder through hotway, or do I have to access them the traditional hotmail way?

---

### Post by mandrill on 2008-06-30
> **Paresh said:**
> If you get an email from someone in your hotmail address book, it's put in the hotmail inbox.

However, if the email is from someone not in your hotmail address book, that email is put in the junk folder.

Is there any way of to access this 'junk' folder through hotway, or do I have to access them the traditional hotmail way?

I would think you can change your junk mail settings in hotmail. However, my tutorial was not concerning hotway.

---

### Post by Chillihead on 2008-07-01
Worked a treat. Cheers man.

---

### Post by forbzie22 on 2008-07-11
> **Indras said:**
> Thanks, all corrected.



I've heard of people getting this before, I'm going to look into it.

By the way, how old is your account?  I find a lot of articles in google saying that Hotmail was ending WebDAV access to new accounts in order to crack down on spam, but all the articles are around September 27, 2004.  I know for a fact that I've had my hotmail account for at least six years, and I've always had the capability to open it in Outlook Express (which uses WebDAV).  I'm thinking if it's a really new account, it might need to be active for a certain number of months before they give you WebDAV.  Otherwise, it might be that all new accounts are not getting WebDAV at all, in which case you're SOL.

My only other suggestion is to try logging directly in via [www.hotmail.com](www.hotmail.com) to confirm that the e-mail address and password are 100% correct, and that the account is active.

EDIT: Here's a website that confirms my suspicions:
[http://www.neilturner.me.uk/2006/Apr/11/using_windows_live_mail_i.html](http://www.neilturner.me.uk/2006/Apr/11/using_windows_live_mail_i.html)

FYI - Your setup instructions worked fine for one of my hotmail accounts which is about 7 years old, my other hotmail account ive had for 3 years, this one doesnt work, complains about ERR to POP 3 server.

---

### Post by Truedream on 2008-07-12
I keep getting unable to bind error :(

---

### Post by Sealbhach on 2008-07-12
[QUOTE=Sealbhach]
Hi,

Anyone know if something similar could be done for Yahoo Mail?[/QUOTE]

Never mind, I've done it. Took ages until I realised I had to go into my yahoo account and enable POP3 to be used!

It's just dumped 1,287 messages into my Evolution client, hee hee!



.

---

### Post by Melindrea on 2008-07-17
I just got this to work, yay!

And Sealbhach? It did the same to me... It was taking ages to work, so I imagined something was wrong, right? I close Evolution, and then notice that there were new mails. It had gotten to may of this year. So, I opened it again, to let it run thoroughly. =)

---

### Post by Mylton on 2008-07-24
i am a new to Ubuntu and have read the forum and found the below information. i followed the instruction listed below to setup my hotmail email using evolution mail. However i received a error message say error in performing operation.

What else can i try





> **Indras said:**
> Okay everyone, after digging around in these forums and googling like I've never googled before, I figured out how to send and receive e-mail through hotmail using Evolution.  I'm throwing together a rough HOWTO for others.  If things need more clarification, let me know and I'll update it.

**First, make sure your system is up to date.  Open up a terminal and type:**

```
sudo apt-get update
```

**Now, install the inet daemon**

```
sudo apt-get install inetutils-inetd
```

**This takes care of all of our dependencies.  Now on to the good stuff...**

```
sudo apt-get install hotway hotsmtp
```

**This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP.  By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.**

```
sudo gedit /etc/inetd.conf
```

**Look for a line like this:**

```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd
```

**By default, hotway leaves a copy of each message it downloads on the server.  I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:**

```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r
```

**And we also need to add a line to get hotsmtpd working, just paste this at the bottom:**

```
2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd
```

**This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon.  Now, save your file, exit gedit, and restart your inetd server:**

```
sudo /etc/init.d/inetutils-inetd restart
```

**If everything is working properly, you'll see this pop up on your screen:**

```
* Restarting internet superserver inetd                            [ ok ]
```

**Now, close out of your terminal and start up Evolution.  It may pop up the first-time use wizard, you can use that if you like.  Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left.  However you choose to do it, here's your information:**

**Email Address:** *xxx*@hotmail.com  (fill in your normal e-mail address that you use to login to hotmail)

**Receive Server type:** POP
**Server:** 127.0.0.1
**Username:** *xxx*@hotmail.com (same as above)
**Security:** No encryption
**Authentication type:** Password
(Remember password checkbox is up to you)

**Send Server type:** SMTP
**Server:** 127.0.0.1:2500
**[X] Server requires authentication** (check this box)
**Use Secure Connection:** No encryption
**Authentication Type:** PLAIN
**Username:** *xxx*@hotmail.com (same as above)
(Optional Remember password checkbox)

---

### Post by mandrill on 2008-07-24
> **Mylton said:**
> i am a new to Ubuntu and have read the forum and found the below information. i followed the instruction listed below to setup my hotmail email using evolution mail. However i received a error message say error in performing operation.

What else can i try

That sure looks like a lot of unnecessary work. No love, either. Why don't you look at my how-to (in this thread - I forget what pages) and start getting your mail?

I have also answered various error questions associated with same  throughout this thread.

Peace, Love, Out!

---

### Post by mandrill on 2008-07-24
> **gsiliceo said:**
> GUys microsoft will be closing the access to hotmail, you'll need windows live mail, and something tells me they wont release that tool for linux.
[http://blog.fastmail.fm/2008/04/22/microsoft-closing-external-hotmail-access-by-end-of-june-2008/](http://blog.fastmail.fm/2008/04/22/microsoft-closing-external-hotmail-access-by-end-of-june-2008/)

My hotmail account is still quite accessible.

---

### Post by gsiliceo on 2008-07-24
Yeah, they pushed the date until further notice, we can enjoy accesing hotmail a few months (hopefully).

[http://blogs.zdnet.com/microsoft/?p=1379](http://blogs.zdnet.com/microsoft/?p=1379)

---

### Post by titimoi on 2008-08-04
that's great thank's a lot

---

### Post by ab636 on 2008-08-06
hi! I followed the instructions on the first page. downloaded emails, but can't sent using hotmail. I get this msg

"Error while performing operation.
Welcome response error: Operation now in progress"

anybody solved this issue?

---

### Post by mandrill on 2008-08-08
> **ab636 said:**
> hi! I followed the instructions on the first page. downloaded emails, but can't sent using hotmail. I get this msg

"Error while performing operation.
Welcome response error: Operation now in progress"

anybody solved this issue?

This all comes down to one issue - easy or hard. Not wrong or right. For beginners, use my how-to (all through this thread). You will be using your ISP's smtp to send, but will not have to log in to get your hotmail.

Good Luck!

---

### Post by phantomjoker on 2008-08-13
does anyone know - will the instructions given stop your online hotmail viewer work?

That set of instructions didn't work for me... but I don't seem to get all my emails anymore!?

---

### Post by mandrill on 2008-08-13
> **phantomjoker said:**
> does anyone know - will the instructions given stop your online hotmail viewer work?

That set of instructions didn't work for me... but I don't seem to get all my emails anymore!?

Help us with a little further clarification. Which method are you using to try to get your hotmail? (I believe there are 2 methods described in this thread); and what is it you mean by "stop your online hotmail viewer work"? Also, what emails aren't you getting?

The more specific you are about the problem, the more likely it will be that you will get an effective reply....

---

### Post by Kevbert on 2008-08-16
> **Mylton said:**
> i am a new to Ubuntu and have read the forum and found the below information. i followed the instruction listed below to setup my hotmail email using evolution mail. However i received a error message say error in performing operation.

What else can i try

There is an error in one line of your post:
```
2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/[COLOR="Red"]hotsmtpd [/COLOR]
```
Should actually be 
```
2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/[COLOR="Red"]hotsmtp[/COLOR]
```
without the 'd' on the end.

---

### Post by ukjimbow on 2008-09-01
> **Indras said:**
> Okay everyone, after digging around in these forums and googling like I've never googled before, I figured out how to send and receive e-mail through hotmail using Evolution.  I'm throwing together a rough HOWTO for others.  If things need more clarification, let me know and I'll update it.

**First, make sure your system is up to date.  Open up a terminal and type:**

```
sudo apt-get update
```

**Now, install the inet daemon**

```
sudo apt-get install inetutils-inetd
```

**This takes care of all of our dependencies.  Now on to the good stuff...**

```
sudo apt-get install hotway hotsmtp
```

**This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP.  By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.**

```
sudo gedit /etc/inetd.conf
```

**Look for a line like this:**

```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd
```

**By default, hotway leaves a copy of each message it downloads on the server.  I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:**

```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r
```

**And we also need to add a line to get hotsmtpd working, just paste this at the bottom:**

```
2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd
```

**This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon.  Now, save your file, exit gedit, and restart your inetd server:**

```
sudo /etc/init.d/inetutils-inetd restart
```

**If everything is working properly, you'll see this pop up on your screen:**

```
* Restarting internet superserver inetd                            [ ok ]
```

**Now, close out of your terminal and start up Evolution.  It may pop up the first-time use wizard, you can use that if you like.  Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left.  However you choose to do it, here's your information:**

**Email Address:** *xxx*@hotmail.com  (fill in your normal e-mail address that you use to login to hotmail)

**Receive Server type:** POP
**Server:** 127.0.0.1
**Username:** *xxx*@hotmail.com (same as above)
**Security:** No encryption
**Authentication type:** Password
(Remember password checkbox is up to you)

**Send Server type:** SMTP
**Server:** 127.0.0.1:2500
**[X] Server requires authentication** (check this box)
**Use Secure Connection:** No encryption
**Authentication Type:** PLAIN
**Username:** *xxx*@hotmail.com (same as above)
(Optional Remember password checkbox)
Any chance of adding encryption?

---

### Post by mandrill on 2008-09-03
Not without 3rd party application, I believe, & I am unaware (take that for what its worth) of any such application for Linux. ( I mean, its Hotmail, fer crying out loud!) I seem to remember something from a while back about MSN having "built-in" encryption, but that may have just been something I thought I remembered reading on a Saturday morning after a long Friday night............

---

### Post by SenojLuap on 2008-09-04
Just wanted to say that I used the method above and it worked perfectly! Thanks alot!

---

### Post by zolts on 2008-09-06
I have followed the instructions in the first post but when i send/receive messages the following happens

[IMG]http://i265.photobucket.com/albums/ii219/zolts/BYO/Screenshot.png[/IMG]

Can anyone help with this????

---

### Post by lernatix on 2008-09-15
Hi peeps,

So far the OP works for outgoing e-mails on my *@hotmail.com account.

However, I cannot seem to get any e-mails recieved and have to use 
the hotmail website to see incomming mail on that account.

Any ideas?  Something about the 2500?

> Unable to connect to POP server 127.0.0.1: No support for requested authentication mechanism.

---

### Post by swelmer on 2008-09-17
> **Flojomojo said:**
> Doesn't M$ require you to pay a free for POP and IMAP access to Hotmail now? 

That, along with the MSIE-centric focus of [www.live.com](www.live.com), is one of the things that pushed me into moving to Linux.


 has anyone seen this message, this is what i get after following the directions in this post.

ERR- unable to find folder on remote server.

---

### Post by mandrill on 2008-09-18
> **swelmer said:**
> has anyone seen this message, this is what i get after following the directions in this post.

ERR- unable to find folder on remote server.

You must have set your incoming server as IMAP. For really easy hotmail access, download *freepops* @ [http://cybertech.altervista.org/en/freepops.php](http://cybertech.altervista.org/en/freepops.php), making sure you download proper architecture for your machine, (both freepops and its updater), install via gdebi, set incoming server as localhost:2000, set server as POP, use your isp smtp for outgoing, update the freepops program with the separate updater,(applications>internet) and you're good to go.

I don't use hotmail very often, if at all, but I just now checked mine, and it is working perfectly.

ps - restart your machine the daemon will run automatically. 

Good Luck!

---

### Post by readinglady on 2008-09-20
Many thanks, followed your initial instructions and five minutes later was reading my email. 

readinglady

---

### Post by huntantr on 2008-09-28
Is it possible for someone to repost the steps on how to do this. I have tried the steps from the very beginning, But there seem to be other ways of setting this up, I can't quite seem to figure out all of the steps from the many pages and posts.
Any help here would be greatly appreciated. I'm a new user trying to switch from windows to ubuntu.


Thanks,
Anthony

---

### Post by mandrill on 2008-09-29
For really easy hotmail access, download *freepops* @ [http://cybertech.altervista.org/en/freepops.php](http://cybertech.altervista.org/en/freepops.php), making sure you download proper architecture for your machine, (both freepops and its updater), install via gdebi, set incoming server as localhost:2000, set server as POP, use your isp smtp for outgoing, update the freepops program with the separate updater,(applications>internet) and you're good to go.

I don't use hotmail very often, if at all, but I just now checked mine, and it is working perfectly.

ps - restart your machine the daemon will run automatically. 

Good Luck!

---

### Post by rinishak on 2008-09-29
> **zolts said:**
> I have followed the instructions in the first post but when i send/receive messages the following happens

[IMG]http://i265.photobucket.com/albums/ii219/zolts/BYO/Screenshot.png[/IMG]

Can anyone help with this????

Same thing happened to me as described by zolts in the above quote. The message shows up after clicking Send/Receive and entering the pass. I noticed that quite a few people have mentioned this error since the beginning of this thread, but I'm unclear of the solution. Would you kindly help us resolve this issue?

Thanks in advance.

Rin

---

### Post by mandrill on 2008-09-29
> **rinishak said:**
> Same thing happened to me as described by zolts in the above quote. The message shows up after clicking Send/Receive and entering the pass. I noticed that quite a few people have mentioned this error since the beginning of this thread, but I'm unclear of the solution. Would you kindly help us resolve this issue?

Thanks in advance.

Rin

See the post 2 posts directly above. Got a picture on it just like the one to your left......

---

### Post by huntantr on 2008-09-30
> **mandrill said:**
> For really easy hotmail access, download *freepops* @ [http://cybertech.altervista.org/en/freepops.php](http://cybertech.altervista.org/en/freepops.php), making sure you download proper architecture for your machine, (both freepops and its updater), install via gdebi, set incoming server as localhost:2000, set server as POP, use your isp smtp for outgoing, update the freepops program with the separate updater,(applications>internet) and you're good to go.

I don't use hotmail very often, if at all, but I just now checked mine, and it is working perfectly.

ps - restart your machine the daemon will run automatically. 

Good Luck!


Thanks for the help, this did the trick.This is much simpler then what is described in the original post.

---

### Post by Zarafet on 2008-10-01
I just installed Ubuntu today and I was so confused as to terminals, but I found the terminal, and followed all of your instructions and my hotmail is working through evolution so I wanted to say great work and thank you!

---

### Post by pmrb on 2008-10-01
Thank you for the tutorial. I get it to work, but my problem is that a wanna left the messages on the server, and when i remove them in evolution the message is not removed within the server. Anyone can help me with this?

---

### Post by gjasuwan on 2008-10-02
Dude:

I don't know how you learn to do all this stuff with Linux but if it wasn't for the Forums tonight with the howto posts I wouldn't be able to watch movies on my Ubuntu OS and access my Gmail & MS Accounts and I'm still trying to think of some other things that I am going to have to get this OS system to do but so far most of the codes that I have entered are way above my knowledgeable windows mind set - this is the first time I have started to use Linux and the Howto posts are making my life a lot easier then having to figure all this stuff out myself with not knowing a lick a spit about Linux.

Thank you to all the Howto Contributors :D

---

### Post by mandrill on 2008-10-02
> **pmrb said:**
> Thank you for the tutorial. I get it to work, but my problem is that a wanna left the messages on the server, and when i remove them in evolution the message is not removed within the server. Anyone can help me with this?

Not being sarcastic, but, what? You want to leave your messages on the hotmail server or you don't?  If you want to leave your messages on the server for later, in Evolution click "Edit > preferences > hotmail acct > edit > receiving options > and check the box that says "Leave Messages on Server"

Ciao!

---

### Post by pmrb on 2008-10-02
Yes I want to leave messages on the server, and they are.
But the problem is that when i delete messages in evolution, they are not removed in the server.
I've used thunderbird before and he was able to do this, even leaving messages on the server when I erased in the thunderbird they also were removed from the server.

---

### Post by rinishak on 2008-10-02
> **mandrill said:**
> See the post 2 posts directly above. Got a picture on it just like the one to your left......

Is Freepops another separate program from Evolution? Because I prefer if I could use Evolution to check my Hotmail, since I use it to check my other e-mail accounts (Gmail, etc.). I just prefer if they shared the same mail program for convenience. :)

---

### Post by mandrill on 2008-10-02
> **rinishak said:**
> Is Freepops another separate program from Evolution? Because I prefer if I could use Evolution to check my Hotmail, since I use it to check my other e-mail accounts (Gmail, etc.). I just prefer if they shared the same mail program for convenience. :)

Yes, Freepops is separate, although it comes standard in some distros - its even in the repositories, but that version is usually out of date, and you have to remember the command line (freepops-updater-fltk) to update the sign-in scripts, or make a launcher,  whereas doing it this way makes it easier for noobs, as there is a graphical interface to the updater.

And the whole point of this discussion is that you can get ANY (well, almost any) webmail, or email, or rss feed you want through whatever email client you wish. Bada-Bing.

---

### Post by mandrill on 2008-10-02
> **pmrb said:**
> Yes I want to leave messages on the server, and they are.
But the problem is that when i delete messages in evolution, they are not removed in the server.
I've used thunderbird before and he was able to do this, even leaving messages on the server when I erased in the thunderbird they also were removed from the server.

As for you, you say "Yes I want to leave messages on the server" and then you say "the problem is that when i delete messages in evolution, they are not removed in the server."

Strange, but just to test it out, I unchecked the box "Leave messages on server" , sent myself an email, got it on evolution, deleted it, then signed into hotmail website directly, and, POOF! No emails. (As a matter of fact, I did it twice, just to make sure). So, you have to decide if you want the little box checked or unchecked. (Lets move along, nothing to see here....)

---

### Post by klytu on 2008-10-03
> **mandrill said:**
> As for you, you say "Yes I want to leave messages on the server" and then you say "the problem is that when i delete messages in evolution, they are not removed in the server."

Strange, but just to test it out, I unchecked the box "Leave messages on server" , sent myself an email, got it on evolution, deleted it, then signed into hotmail website directly, and, POOF! No emails. (As a matter of fact, I did it twice, just to make sure). So, you have to decide if you want the little box checked or unchecked. (Lets move along, nothing to see here....)

In your test, the message wasn't deleted in Hotmail because you deleted it in Evolution. Rather, it was deleted because you unchecked the box "Leave messages on server". Without that box checked, messages are deleted from Hotmail whenever Evolution downloads them. 

I think what the original poster might be looking for was a way for Evolution mail to be in sync with Hotmail so that whatever appears in Hotmail appears in Evolution or vice-versa. I don't know how to accomplish this with Hotmail and Evolution.

---

### Post by mandrill on 2008-10-03
> **klytu said:**
> In your test, the message wasn't deleted in Hotmail because you deleted it in Evolution. Rather, it was deleted because you unchecked the box "Leave messages on server". Without that box checked, messages are deleted from Hotmail whenever Evolution downloads them. 

I think what the original poster might be looking for was a way for Evolution mail to be in sync with Hotmail so that whatever appears in Hotmail appears in Evolution or vice-versa. I don't know how to accomplish this with Hotmail and Evolution.

If Evolution is set to download the entire message, thereby leaving no messages on the server, they are, by definition, in sync. You *can* download just the headers, to see if you want the whole message or not, but the whole point of this exercise is to save steps, not create more. Then again, he could just put a link to hotmail on his desktop, thereby making it ***really*** (expletive deleted) simple.

---

### Post by pmrb on 2008-10-03
klytu,you got it. That is what i want to do...
I think i'll have to use thunderbird again.

---

### Post by filibertov on 2008-10-03
Guys.  Why can't this be just simply understood?  If M$ does it (and has done it for a long time), then Ubuntu should do it.  Here's a pic of what we want.

A simple check box that says "Remove from server when deleted from 'Deleted' items".

---

### Post by mandrill on 2008-10-03
> **filibertov said:**
> Guys.  Why can't this be just simply understood?  If M$ does it (and has done it for a long time), then Ubuntu should do it.  Here's a pic of what we want.

A simple check box that says "Remove from server when deleted from 'Deleted' items".

How about edit > preferences > mail preferences > delete mail? Notice the expunge box.

And this isn't M$....what we have here is very common - folks thinking in one language (windows) and having to communicate in another language (linux) and it doesn't work. You have to learn to think in linux. I've been doing it every day for 15 months, and I'm still a noob. 

To answer your question "Why can't this be just simply understood?" I have 2 answers for you. 1) As far as I can tell, the original question has been answered well and effectively, and 2) You must have had some kind of learning curve on windows, right? Easier when you are younger for sure, but doesn't it follow then that there is a learning curve here as well? Relax. It's just another (self-inflicted) challenge!

---

### Post by pmrb on 2008-10-04
Don't you think we've tried that?
We are not here to get you working for us. If we are asking, we have done at least a little research on the subject. If you don't know the answer, do not try to find it in excuses concerning about not to understand the problem and say that I do not speak the same language than you!
Either way thank you for trying to find a solution to the problem, and sorry for the bad English.

Greetings

---

### Post by mandrill on 2008-10-04
> **pmrb said:**
> Don't you think we've tried that?
We are not here to get you working for us. If we are asking, we have done at least a little research on the subject. If you don't know the answer, do not try to find it in excuses concerning about not to understand the problem and say that I do not speak the same language than you!
Either way thank you for trying to find a solution to the problem, and sorry for the bad English.

Greetings

I think its nap time for somebody.

---

### Post by trailortrash on 2008-10-04
Thank You, followed the first post step by step and it works perfect :thumbsup:

---

### Post by jens83 on 2008-10-13
thanks for ur howto's mandrill!
i had to download the freepops program and now it works, -that is the incoming mails work. when trying to send an email, it asks for my smtp password. according to my isp, thats the same as my password for the adsl login. anyway i tried that but it wont authenticate.
any thoughts?
thanks

---

### Post by matey3 on 2008-10-15
> **Indras said:**
> Okay everyone, after digging around in these forums and googling like I've never googled before, I figured out how to send and receive e-mail through hotmail using Evolution.  I'm throwing together a rough HOWTO for others.  If things need more clarification, let me know and I'll update it.

[b]First, .........


(I donno how long ago this was posted (I googled it)and I dont care...)but
You are all right man, great job...

You know I trashed my system and re-built it last week. I had somehow found a page with a whole lot of screen shots of setting up Evolution for hotmail. This guy had spent a lot of time for his instructions and I give him credit for all his hard work but still some ppl had troubles with getting it to work (mainly my problem was I had to tweak the port number)..
Any way that was the 1st time, took me a long time to set it all up and of course every thing was destroyed after re-doing my machine...
But this instructions you gave us is most excellent and least time-consuming.I got it going in few minutes...

Just wanted to thank you for a great job well done!
Regards;

---

### Post by mandrill on 2008-10-17
> **jens83 said:**
> thanks for ur howto's mandrill!
i had to download the freepops program and now it works, -that is the incoming mails work. when trying to send an email, it asks for my smtp password. according to my isp, thats the same as my password for the adsl login. anyway i tried that but it wont authenticate.
any thoughts?
thanks

Your smtp password could be 2 things. "Password" usually means your code to access the ISP's server for your mail, but in this case, I think you want something in this format - smtp.xxx.xxxx.net/com. For instance "smtp.east.comcast.net" or somesuch in that format. Port 25. 

Good Luck!

---

### Post by jens83 on 2008-10-18
that would be: smtp.mail.dravanet.hu and it didnt work.. also not sure where to check if im using "port 25"

trying to attach an image here

---

### Post by mandrill on 2008-10-19
> **jens83 said:**
> that would be: smtp.mail.dravanet.hu and it didnt work.. also not sure where to check if im using "port 25"

trying to attach an image here

I'm gonna take a guess here, but since Evolution is set to port 25 by default (here, anyway), your ISP either blocks port 25, or doesn't allow outgoing (smtp) mail that is not encrypted/secured, (an easy fix.) Best bet, call them and ask. (Port settings default at 25 out and 110 in for pop mail) Gmail uses 995 for smtp (I think) and IMAP servers use 143 instead of 110. Anyway, I don't remember whether or not you were restricted on your other OS or not; some ISP's don't offer smtp, you have to use a separate server (or make one.) 

Either way, its not a big deal, you're real close.

---

### Post by sirdouglas on 2008-10-20
I'm starting to think Linux hates me.  This tutorial worked for almost everybody, but of course after following the instruction word-for-word and double-checking every step along the way, I get an error message while trying to receive my mail. "Error while Fetching Mail.

Unable to connect to POP server 127.0.0.1: No support for requested authentication mechanism."

Why?  I did try searching through the forums and these 32 pages of posting without solving my problem.  I appreciate any help with this.

Thanks,

Doug

---

### Post by mandrill on 2008-10-21
> **sirdouglas said:**
> I'm starting to think Linux hates me.  This tutorial worked for almost everybody, but of course after following the instruction word-for-word and double-checking every step along the way, I get an error message while trying to receive my mail. "Error while Fetching Mail.

Unable to connect to POP server 127.0.0.1: No support for requested authentication mechanism."

Why?  I did try searching through the forums and these 32 pages of posting without solving my problem.  I appreciate any help with this.

Thanks,

Doug


Linux doesn't hate you any more than it hated me for a year. The problem you are having is that the freepops daemon is not starting for you automatically, and therefore is not connecting to your POP server 127.0.1.1 (which is your machine). You could start it manually in a terminal every time you wanted to check mail by typing "freepopsd" in a terminal and leaving it open during your mail session. When you close the terminal,you close freepops.

Therefore, I recommend the much more satisfying route of going to System > Preferences > Sessions (in Gnome) and manually adding it to the list of start-up services. Again, the command is "freepopsd" Strangely, you only have to do that if you get freepops from the Ubuntu repos (and its a version or two behind the current release). If you download the deb package from the site it configures automatically, (except when the download link shows nothing but javascript like it did the other day). If that doesn't fix it, post back. Make sure your pop server is localhost:2000.

Good Luck!

---

### Post by sirdouglas on 2008-10-26
Alright, so first I tried to get the .deb package as that sounded like the best way to go, but I couldn't get the package installed.  Anyways, so after typing "freepopsd" in the terminal I found that I do not have the program.  So I typed the command to get it, finished download, typed in "freepopsd" once again in the terminal window, opened evolution... and it still didn't work.  "Error fetching mail."  Ugh.  Any ideas? 

Thanks for the help. appreciate it,

Doug

---

### Post by mandrill on 2008-10-26
> **sirdouglas said:**
> Alright, so first I tried to get the .deb package as that sounded like the best way to go, but I couldn't get the package installed.  Anyways, so after typing "freepopsd" in the terminal I found that I do not have the program.  So I typed the command to get it, finished download, typed in "freepopsd" once again in the terminal window, opened evolution... and it still didn't work.  "Error fetching mail."  Ugh.  Any ideas? 

Thanks for the help. appreciate it,

Doug

The website debpackage *was* mangled and uninstallable. Thats why I suggested the version from the repos (older) and if you run the updater (in terminal), freepops-updater-fltk, you'll be fine. Your problem sounds like you did not set your incoming server to localhost:2000 with no encryption and password validation only. Also, recheck the little stuff,like I didn't do once and spent an hour swearing until I found the missing dot in .com. Post back results!

---

### Post by sirdouglas on 2008-10-26
So, here's where I'm at... first, I think you're underestimating my lack of knowledge with Linux.  I can't figure out how to get the freepops downloaded using repos.  Would this be where you click "Add/Remove" applications and then install after finding it in the list?  Well, I tried that but couldn't even find freepops in the list.  Well I thought it would be installed after using the terminal, but it doesn't seem to appear anywhere.

Second, I thought the incoming server was supposed to be set to 127.0.0.1, and now you're saying it's localhost:2000.  Well, I tried both (localhost:2000 asks for my password upon trying to connect, whereas the 127.0.0.1 does not), but neither brought success.  

Thanks for bearing with me and my impressive skills in Linux:)

Doug

---

### Post by mandrill on 2008-10-27
> **sirdouglas said:**
> So, here's where I'm at... first, I think you're underestimating my lack of knowledge with Linux.  I can't figure out how to get the freepops downloaded using repos.  Would this be where you click "Add/Remove" applications and then install after finding it in the list?  Well, I tried that but couldn't even find freepops in the list.  Well I thought it would be installed after using the terminal, but it doesn't seem to appear anywhere.

Second, I thought the incoming server was supposed to be set to 127.0.0.1, and now you're saying it's localhost:2000.  Well, I tried both (localhost:2000 asks for my password upon trying to connect, whereas the 127.0.0.1 does not), but neither brought success.  

Thanks for bearing with me and my impressive skills in Linux:)

Doug

Dude, I just spent an hour writing a foolproof tutorial, but because I did it before I logged in, I lost it!

OK, short version. Enter all email info as normal,use pop server, name is entire email address, normal smtp info , finish & exit and immediately click account and then edit, hit receiving mail tab, this is where you enter server localhost:2000 and name is entire email address. Go to System > Admin > Synaptic, Hit search, enter freepops, and updater, let synaptic install. No gui here but command is "freepopsd" which I would then enter as a startup service thru System > Preferences> Sessions. There is a GUI for updater, must be invoked with "freepops-updater-fltk" in terminal,  follow 10 second directions. **Restart.** Evolution will ask for email password 1st time you use. Your mail will now work. Give me the good word, PM
is ok.

Good Luck!

---

### Post by sirdouglas on 2008-10-27
Well, I'd love to give you good news that I got it working... but I didn't:(  I did just what you said.  I have all the information filled in correctly and got freepopsd installed properly.  The update was running smoothly until it came to an error: "Error downloading fastmail: Unable to update the module: /var/lib/freepops/lua_updates//fastmail.lua: Permission denied."  Along with this little message came a whole line of messages in the command box:

sirdouglas@sirdouglas-laptop:~$ freepops-updater-fltk
Mon Oct 27 09:11:17 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 41) : Unable to find psock
Mon Oct 27 09:11:17 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 42) : Assuming it was a toplevel module
Mon Oct 27 09:12:31 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 121) : Unable to update the module: fastmail.  The module will not be updated, Error: /var/lib/freepops/lua_updates//fastmail.lua: Permission denied

LUAY: lua error message:
LUAY:    invalid key to 'next'

LUAY: lua stack traceback:
LUAY:    [C]: run: -1 (C field)
LUAY:    /usr/share/freepops/lua/updater.lua: fun: 396 (Lua local)
LUAY:    /usr/share/freepops/lua/updater.lua: (null): 508 (Lua )

The main function raised an error
LUAY: lua stack image:
LUAY: stack( 2) : function:  ??
LUAY: stack( 1) : function:  ??
LUAY: stack( 0) : --bottom--

sirdouglas@sirdouglas-laptop:~$ freepops-updater-fltk
Mon Oct 27 09:13:53 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 41) : Unable to find psock
Mon Oct 27 09:13:53 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 42) : Assuming it was a toplevel module
Mon Oct 27 09:14:41 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 121) : Unable to update the module: fastmail.  The module will not be updated, Error: /var/lib/freepops/lua_updates//fastmail.lua: Permission denied

LUAY: lua error message:
LUAY:    invalid key to 'next'

LUAY: lua stack traceback:
LUAY:    [C]: run: -1 (C field)
LUAY:    /usr/share/freepops/lua/updater.lua: fun: 396 (Lua local)
LUAY:    /usr/share/freepops/lua/updater.lua: (null): 508 (Lua )

The main function raised an error
LUAY: lua stack image:
LUAY: stack( 2) : function:  ??
LUAY: stack( 1) : function:  ??
LUAY: stack( 0) : --bottom--

sirdouglas@sirdouglas-laptop:~$ freepopsd
Unable to bind on 0.0.0.0:2000
sirdouglas@sirdouglas-laptop:~$ freepopsd
Unable to bind on 0.0.0.0:2000
sirdouglas@sirdouglas-laptop:~$ freepopsd
Unable to bind on 0.0.0.0:2000
sirdouglas@sirdouglas-laptop:~$ freepops-updater-fltk
Mon Oct 27 09:24:01 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 41) : Unable to find psock
Mon Oct 27 09:24:01 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 42) : Assuming it was a toplevel module
Mon Oct 27 09:25:24 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 121) : Unable to update the module: fastmail.  The module will not be updated, Error: /var/lib/freepops/lua_updates//fastmail.lua: Permission denied

LUAY: lua error message:
LUAY:    invalid key to 'next'

LUAY: lua stack traceback:
LUAY:    [C]: run: -1 (C field)
LUAY:    /usr/share/freepops/lua/updater.lua: fun: 396 (Lua local)
LUAY:    /usr/share/freepops/lua/updater.lua: (null): 508 (Lua )

The main function raised an error
LUAY: lua stack image:
LUAY: stack( 2) : function:  ??
LUAY: stack( 1) : function:  ??
LUAY: stack( 0) : --bottom--

sirdouglas@sirdouglas-laptop:~$ freepops-updater-fltk
Mon Oct 27 09:29:19 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 41) : Unable to find psock
Mon Oct 27 09:29:19 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 42) : Assuming it was a toplevel module
Mon Oct 27 09:29:32 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 121) : Unable to update the module: fastmail.  The module will not be updated, Error: /var/lib/freepops/lua_updates//fastmail.lua: Permission denied

I still added freepopsd to the startup list with the slight hope of it working upon restart.  

Wasn't this very original thread supposed to be a fool proof guide?... seemed to work for most.  And why does the original post say to enter "127.0.0.1" while you tell me "localhost:2000"?  Thanks for the help though so far.  We'll get it!

Doug

Btw, *sending* mail from Evolution works

---

### Post by mandrill on 2008-10-27
I think you are bad luck for me. I just ran the updater and was gifted with this: 
     jim@raven:~/Desktop$ freepops-updater-fltk
Mon Oct 27 17:53:30 2008 freepopsd: ERROR(log_lua.c,  70): (@/var/lib/freepops/lua_updates/updater_common.lua, 41) : Unable to find psock
Mon Oct 27 17:53:30 2008 freepopsd: ERROR(log_lua.c,  70): (@/var/lib/freepops/lua_updates/updater_common.lua, 42) : Assuming it was a toplevel module

OK, now its personal! The Ubuntu maintainer's debpackages are fubar, the repos are 2 versions behind. By the way, localhost and 127.0.0.1 are the same thing - your machine. This is interesting - Unable to bind on 0.0.0.0:2000....(from your post), as was this - Unable to find psock.

In essence,freepops keeps up with the sign-in scripts for about a hundred different email services, it will even work on your local ISP service. Since I have never had this happen before, I tried to run from command line, and this is what I got:

jim@raven:~/Desktop$ freepopsd
Unable to bind on 0.0.0.0:2000
jim@raven:~/Desktop$ sudo freepopsd
sudo: unable to resolve host raven
Unable to bind on 0.0.0.0:2000

I assume that the kernel update has something to do with this, as I just now updated mine and BAM, no more freepops. That's pretty common. Sourceforge has a tar file, we could build it from source - that would be really jumping into the fire! Let me know if you can hardwire your laptop, if it is x86 or x64, etc....or, you could go back to the very beginning of this thread and try to follow indras' tutorial - I wasn't able to......

---

### Post by mandrill on 2008-10-28
OK. I found the new packages for Intrepid in Launchpad. Up-to-date version,graphical installers (debpackage), daemon starts when you launch email client, and the updater has GUI that shows up under Applications > System Tools......no muss, no fuss, download, install, update, & enjoy! 

(I better hear back from you that everything works perfectly or I'll throw some serious mojo chee-chee your way!)

You may download your new toys here: (Just install them straight from the debpackage installer that will magically appear on your desktop.....)

1) Freepops 0.2.7.1

[http://launchpadlibrarian.net/15235843/freepops_0.2.7-1_i386.deb](http://launchpadlibrarian.net/15235843/freepops_0.2.7-1_i386.deb)


 
2) Freepops Updater 0.2.7.1

[http://launchpadlibrarian.net/15235844/freepops-updater-fltk_0.2.7-1_i386.deb](http://launchpadlibrarian.net/15235844/freepops-updater-fltk_0.2.7-1_i386.deb)



just in case,you might need this: [http://launchpadlibrarian.net/15235844/freepops-updater-fltk_0.2.7-1_i386.deb](http://launchpadlibrarian.net/15235844/freepops-updater-fltk_0.2.7-1_i386.deb)

---

### Post by altkon on 2008-10-28
Hi!!! Everybody..I am a newbee...
I have activated my POP3 e-mail client services on evolution and all works fine..
But I cannot setup my hotmail services e-mail account which I get it for free on http access basis.
I am an old account member with hotmail since 2003, therefore I am still able to work with OE6 e-mail client which offer http built in support for Hotmail accounts.
Can you explain to me what commands I should use to work around this problem?? with Ubuntu 8.4.1.:confused:
altkon

---

### Post by sirdouglas on 2008-10-28
Okay, first let me say.. I'm quite sorry as it stillll didn't work:(  I think we got closer though because it at least tried to connect this time with the box opening saying:
----------------------------------------------- 
"send and receive mail,
[email]sirdouglas@hotmail.com[/email] (pop) localhost
Waiting... (which eventually changes to "Retrieving POP Summary")
Smtp: 127.0.0.1
Complete"
-----------------------------------------------

Then the box disappears and a message at the bottom left corner says "Error Fetching Mail."  After clicking on the error, it says "Error while Fetching Mail.

Cannot get POP summary: Operation now in progress"

Ugh, don't worry, it it's too much we may give up at this point.  You've done a lot so far to try help me!  

Doug

---

### Post by mandrill on 2008-10-28
> **sirdouglas said:**
> Okay, first let me say.. I'm quite sorry as it stillll didn't work:(  I think we got closer though because it at least tried to connect this time with the box opening saying:
----------------------------------------------- 
"send and receive mail,
[email]sirdouglas@hotmail.com[/email] (pop) localhost
Waiting... (which eventually changes to "Retrieving POP Summary")
Smtp: 127.0.0.1
Complete"
-----------------------------------------------

Then the box disappears and a message at the bottom left corner says "Error Fetching Mail."  After clicking on the error, it says "Error while Fetching Mail.

Cannot get POP summary: Operation now in progress"


Ugh, don't worry, it i[/I]t's too much we may give up at this point.  You've done a lot so far to try help me!  

Doug

The daemon did not start. Type freepopsd in terminal -leave it open. You will get mail, if you are updated. I had to stick mine in System > Preferences > Sessions again to assure the daemon started automatically , and had to switch to the fltk updater instead of the one with a GUI, but I am up and running.....I don't know what version you're running or anything, but if its 8.04 it *will* work. You are less than 1 minute away from having this done!

---

### Post by mandrill on 2008-10-28
> **altkon said:**
> Hi!!! Everybody..I am a newbee...
I have activated my POP3 e-mail client services on evolution and all works fine..
But I cannot setup my hotmail services e-mail account which I get it for free on http access basis.
I am an old account member with hotmail since 2003, therefore I am still able to work with OE6 e-mail client which offer http built in support for Hotmail accounts.
Can you explain to me what commands I should use to work around this problem?? with Ubuntu 8.4.1.:confused:
altkon

How can all be fine if you cannot get your hotmail? Above and below your post is an ongoing thread between myself & sirdouglas; if your questions are not answered by reading those dialogues, please post back.

---

### Post by Merovius on 2008-10-28
Tried creating an account for the Junk mail download with [email]XXX@hotmail.com[/email]/junk. Won't except the password. Inbox works OK. What am I doing wrong?

TIA

---

### Post by Merovius on 2008-10-28
Forgot to mention ERR cannot find folder junk on server is displayed when it fails to connect.

Thanks again.

---

### Post by sirdouglas on 2008-10-28
Mandrill, thanks for all the help you've given so far.  I'm starting to feel bad!  (I still didn't accomplish:()

Here's what I tried in the terminal:

sirdouglas@sirdouglas-laptop:~$ freepopsd
Unable to bind on 0.0.0.0:2000
sirdouglas@sirdouglas-laptop:~$ freepops-updater-fltk
Tue Oct 28 21:31:08 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 121) : Unable to update the module: mimer.  The module will not be updated, Error: /var/lib/freepops/lua_updates//mimer.lua: Permission denied

LUAY: lua error message:
LUAY:    invalid key to 'next'

LUAY: lua stack traceback:
LUAY:    [C]: run: -1 (C field)
LUAY:    /usr/share/freepops/lua/updater.lua: fun: 396 (Lua local)
LUAY:    /usr/share/freepops/lua/updater.lua: (null): 517 (Lua )

The main function raised an error
LUAY: lua stack image:
LUAY: stack( 2) : function:  ??
LUAY: stack( 1) : function:  ??
LUAY: stack( 0) : --bottom--
---------------------------------------------------
Consequently I still haven't gotten my mail.  How has no one else ran into these problems?  I'm using version 8.04 now, but I'm in the process of updating to 8.10.  I'll let you know when success comes, we're on our way there!

Doug

---

### Post by mandrill on 2008-10-28
> **sirdouglas said:**
> Mandrill, thanks for all the help you've given so far.  I'm starting to feel bad!  (I still didn't accomplish:()

Here's what I tried in the terminal:

sirdouglas@sirdouglas-laptop:~$ freepopsd
Unable to bind on 0.0.0.0:2000
sirdouglas@sirdouglas-laptop:~$ freepops-updater-fltk
Tue Oct 28 21:31:08 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 121) : Unable to update the module: mimer.  The module will not be updated, Error: /var/lib/freepops/lua_updates//mimer.lua: Permission denied

LUAY: lua error message:
LUAY:    invalid key to 'next'

LUAY: lua stack traceback:
LUAY:    [C]: run: -1 (C field)
LUAY:    /usr/share/freepops/lua/updater.lua: fun: 396 (Lua local)
LUAY:    /usr/share/freepops/lua/updater.lua: (null): 517 (Lua )

The main function raised an error
LUAY: lua stack image:
LUAY: stack( 2) : function:  ??
LUAY: stack( 1) : function:  ??
LUAY: stack( 0) : --bottom--
---------------------------------------------------
Consequently I still haven't gotten my mail.  How has no one else ran into these problems?  I'm using version 8.04 now, but I'm in the process of updating to 8.10.  I'll let you know when success comes, we're on our way there!

Doug

Gotta be something really simple.Delete your account from Evolution, and remove all vestiges of freepops currently installed. Just for the heck of it open terminal and run "sudo apt-get autoremove". Then start over, run the updater and add freepopsd to Sessions manager.Re-enter your email info, (localhost:2000) and reboot. When you hit send/receive you should be prompted for your password. Now I've gotta tear down a triple-boot xp, vista,ubuntu and go back to a single- too much maintainance.Good Luck! ps - save the deb packages for freepops future use.

---

### Post by mandrill on 2008-10-28
> **Merovius said:**
> Tried creating an account for the Junk mail download with [email]XXX@hotmail.com[/email]/junk. Won't except the password. Inbox works OK. What am I doing wrong?

TIA

The freepops lua scripts are designed to open the front door, not take out the trash. In other words, you are using an automated script to duplicate the process of signing into your inbox, nothing else. What you are describing is something available with IMAP, but not, as far as I know, with POP. 

I guess I'm also wondering why you would want to download spam? If I'm missing the point here, set me straight....'cause I definitely don't know what (no sarcasm) you are trying to do.

---

### Post by Merovius on 2008-10-29
The idea was that I wouldn't have to go to hotmail to see if a piece of mail went to "junk" by accident. 

After a bit of thinking, (sometimes comes to me a bit slow these days...) I thought maybe I should turn off the hotmail filtering and do it with evolution. If the mail is filtered locally then there's no need to go to Hotmail looking for missing e-mails.

Does this sound resonable?

TIA

---

### Post by mandrill on 2008-10-29
> **Merovius said:**
> The idea was that I wouldn't have to go to hotmail to see if a piece of mail went to "junk" by accident. 

After a bit of thinking, (sometimes comes to me a bit slow these days...) I thought maybe I should turn off the hotmail filtering and do it with evolution. If the mail is filtered locally then there's no need to go to Hotmail looking for missing e-mails.

Does this sound resonable?

TIA

Not only reasonable, but expeditious, because Evolution is quite capable of spam filtering. Moreover, I believe that is the *only* way to do it.

---

### Post by Merovius on 2008-10-29
Beautious!  :guitar:

Thanks

---

### Post by sirdouglas on 2008-10-30
I deleted everything (except I don't even know how to remove freepops), but I reinstalled the other package, my account, and reinstalled all my information again.  One question, why do I even need freepops if it's not in the original instructions?  Do I need freepops on top of the original poster's instructions, or just one or the other?

Well, after all that it still doesn't work.  I used 127.0.0.1 along with everything else from the original post and it continually asked for my password, without actually signing in.  Sooo, I donno at this point:(

Thanks so far though:)

Doug

---

### Post by Kimbo66 on 2008-10-31
> **sirdouglas said:**
> Mandrill, thanks for all the help you've given so far.  I'm starting to feel bad!  (I still didn't accomplish:()

Here's what I tried in the terminal:

sirdouglas@sirdouglas-laptop:~$ freepopsd
Unable to bind on 0.0.0.0:2000
sirdouglas@sirdouglas-laptop:~$ freepops-updater-fltk
Tue Oct 28 21:31:08 2008 freepopsd: ERROR(log_lua.c,  70): (@/usr/share/freepops/lua/updater_common.lua, 121) : Unable to update the module: mimer.  The module will not be updated, Error: /var/lib/freepops/lua_updates//mimer.lua: Permission denied



try "sudo freepops-updater-fltk" in the terminal, worked for me

---

### Post by sirdouglas on 2008-10-31
Yes yes yes!!!  I'm not sure if I even believe it myself, BUT it works!  I think that update just needed to be completed which wasn't working before for some reason.  After updating to Ubuntu 8.10 and trying again though, perfecto I say.  Actually a lot of error in trying to check the junk mail folder show up, but that doesn't worry me too much, the inbox is there.  Thanks everyone and especially Mandrill for your efforts in helping me:)  

Doug

---

### Post by mandrill on 2008-11-02
FreePops version 0.2.8 came out yesterday. As of this moment the Ubuntu Debian packages maintained by Blackmoon are not updated.

However, you can download the tar.gz file here:

[http://downloads.sourceforge.net/freepops/freepops-0.2.8.tar.gz?modtime=1225551274&big_mirror=0]("http://downloads.sourceforge.net/freepops/freepops-0.2.8.tar.gz?modtime=1225551274&big_mirror=0")

Extract to your desktop, build instructions inside.

---

### Post by Erinn on 2008-11-03
Okay I'm having the same problem which has just been discussed. Using freepops,  from the links Mandrill provided, on 8.04. (really do not want to upgrade to 8.10) 

When I type freepopsd into the terminal, I get the same unable to bind error as before. 

I can send, but not receive, and the error in Evolution is that it timed out, after about 15 minutes. 

I've removed and deleted everything so many times over now, and I still can't make it work.. and I've followed everything here. 

Also, it works using in.izymail.com as the receive mail server, but it takes too long for it to receive emails. I'd rather use freepops..

Stuck :(

---

### Post by mandrill on 2008-11-03
> **Erinn said:**
> Okay I'm having the same problem which has just been discussed. Using freepops,  from the links Mandrill provided, on 8.04. (really do not want to upgrade to 8.10) 

When I type freepopsd into the terminal, I get the same unable to bind error as before. 

I can send, but not receive, and the error in Evolution is that it timed out, after about 15 minutes. 

I've removed and deleted everything so many times over now, and I still can't make it work.. and I've followed everything here. 

Also, it works using in.izymail.com as the receive mail server, but it takes too long for it to receive emails. I'd rather use freepops..

Stuck :(

Run: ```
sudo freepops-updater-fltk
```
That should fix it, and you can still use the version in the repos. In fact, unless you really know what you're doing, standard 'nix doctrine is use *only* those packages. I just like to push the envelope.

---

### Post by Erinn on 2008-11-03
Nope...

And I'd already tried this so wasn't too hopeful. 

"Could not connect to localhost: connection refused."

I might try a reboot but, again, this hasn't helped before now.

---

### Post by mandrill on 2008-11-03
> **Erinn said:**
> Nope...

And I'd already tried this so wasn't too hopeful. 

"Could not connect to localhost: connection refused."

I might try a reboot but, again, this hasn't helped before now.

Please see my signature...

Its unbelievably easy, yet when I installed Intrepid last night, I tried to get my emails and couldn't.
I had forgotten to type in my whole email address as "user name".

The devil is in the details. The only reasons for "connection refused" are: not updating freepops, forgetting to make it autostart, or entering incorrect/insufficient info. Period.

So, we'll go over it all again just for the heck of it.

In Terminal:

01) Install freepops from repos: ```
sudo apt-get install freepops freepops-updater-fltk
```

02) Update by running: ```
freepops-updater-fltk
```

In Evolution:

03) Server type = POP

04) Server address = localhost:2000 (no variations)

05) User Name = whole email address.

06) No encrypted/secured/authenticated anything.

07) Remember password.

08) smtp server = smtp.xxxx.xxx.com/net/whatever (your ISP).

Then:

09) Make it start at boot by adding it to start-ups thusly: System > Preferences > Sessions > click "Add" then fill in Name/FreePops, Command/freepopsd, Comment/Webmail Interface, & make sure the little box next to your entry is checked.

10) Reboot. Get your mail. Get some sleep.

---

### Post by tarvtarv on 2008-11-04
First of all Thank you for getting back so fast; Much appreciaation here

> **mandrill said:**
> 

08) smtp server = smtp.xxxx.xxx.com/net/whatever (your ISP).





OK I dont know what my ISP is;I am staying in a hotel for the time being so in a couple of days my ISP will be different again what tool do i use to find out what my ISP

{xxxx.xxx.com}/?

---

### Post by sirdouglas on 2008-11-04
Okay, here's where I'm at... few problems by now.

1) The whole send/receive mail box starts out working fine, but finishes with an error:

[I]"Error while performing operation.

DATA command failed: Operation now in progress"[/I]

2) After I try closing Evolution altogether a warning box comes saying:

[I]"You have unsent messages, do you wish to quit anyway?

If you quit, these messages will not be sent until Evolution is started again."[/I]

What unsent message?  I didn't even try sending a message throughout my session.

3) When I check my mail through hotmail.com it shows that I have no messages in my inbox, not even old messages.  I usually get around 15 emails a day and it just feels like I've only been getting 3 or 4 since Evolution started.

Sorry for throwing more problems at you guys, but help is quite appreciated!

Doug

---

### Post by mandrill on 2008-11-04
Delete your account. Reboot. Follow guide above. That really *should* fix it, but Evolution isn't real good about details of the error. System logs will tell you, but its really easier and probably better to start over. One of the things about the way email works is its almost always something really f-ing simple to fix, once you know what's wrong. Just getting familiar with Linux requires some tenacity and a whole bunch of patience. Not in Kansas anymore....

---

### Post by hydraulicjj on 2008-11-05
> **swelmer said:**
> has anyone seen this message, this is what i get after following the directions in this post.

ERR- unable to find folder on remote server.
i get that but mine is @hotmail.co.uk. Could it mean that it only works with hotmail.com  adresses?

---

### Post by williebear on 2008-11-06
I too would like to know if it works with hotmail.co.uk. My personal email is hotmail.com and i set it up as per instructions here and it worked a treat. I then tried to add another account for my wife who has a .co.uk but it wont work. 
keep getting error sending password  err: not finding folder on remote server..this is doing my head in...she cant even send mail via live mail as this for some reason will not allow text to be added to the text field of the email which looks as if  ascript is blocked  but in mozzila js is enabled. 

Please help ...my new experience with Ubuntu has been great and I think i have a steep learning curve but this baffles me.

---

### Post by simtaalo on 2008-11-06
i set my hotmail to come through evolution using the inetutils method. its receiving messages fine but i get this error message when trying to send

```
Error while performing operation.

Welcome response error: Operation now in progress
```

> **williebear said:**
> .she cant even send mail via live mail as this for some reason will not allow text to be added to the text field of the email which looks as if  ascript is blocked  but in mozzila js is enabled. 


i've had this problem too and not been able to work out what it is yet.

EDIT: i found a solution for this on the mint forum
[http://www.linuxmint.com/forum/viewtopic.php?f=90&t=18548](http://www.linuxmint.com/forum/viewtopic.php?f=90&t=18548)

---

### Post by raedbenz on 2008-11-07
i am getting this error
[ATTACH]91623[/ATTACH]

hints??
thanx in advance

---

### Post by tuathan on 2008-11-07
thanks, this worked perfectly for me.

is there a way to only download new, unread emails from the hotmail server?

i have approx 2000 emails in my inbox i don't want them all : ) just unread ones from now on.

---

### Post by PrimaryMaster on 2008-11-08
Thanks a lot. Worked like a charm. :)

---

### Post by TyTiger on 2008-11-08
Cheers dude! worked great. :popcorn:

---

### Post by double_d on 2008-11-09
I'm too lazy to read all the pages.
Anybody know if it deletes the messages you delete from the server even if you have it set to leave them on the server?
Thanks

---

### Post by ykewea on 2008-11-10
do the steps described in page 1 (back in 2006) still apply today in 2008 due to possible changes in the hotmail site?????

---

### Post by kubug on 2008-11-10
> **raedbenz said:**
> i am getting this error
[ATTACH]91623[/ATTACH]

hints??
thanx in advance

It's because Microsoft wants your money! 

This is only available for free if you have signed up for your hotmail account many many moons ago. I signed up back in '94 and I get it for free, but most people after me didn't get it anymore.

Sorry. Maybe try another webmail service, like gmail for example.

---

### Post by kubug on 2008-11-10
Thank you. Worked great!

---

### Post by raedbenz on 2008-11-10
> **kubug said:**
> It's because Microsoft wants your money! 

This is only available for free if you have signed up for your hotmail account many many moons ago. I signed up back in '94 and I get it for free, but most people after me didn't get it anymore.

Sorry. Maybe try another webmail service, like gmail for example.

really thanx for ur clarification.

---

### Post by Michael12uk on 2008-11-10
I just recently joint and have not much clue about it. I hope someone knows a bit more then me.

unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Please login with user first

what should i do? I entered the right password. Please post me back

---

### Post by lyminhtriet on 2008-11-11
Now, @hotmail (@msn or @live) support IMAP. When I use OutlookConnector to synchronize my MS Oulook with [email]xxx@msn.com[/email]. The wonderful things is Connector also can synchronize my contact and Calendar. 

Now I decide using Ubuntu and must take Evolution mail. 

I wonder, how can I combine Evolution mail with IMAP live mail?

Can you help me?

Tks

---

### Post by crosswound on 2008-11-12
> **raedbenz said:**
> i am getting this error
[ATTACH]91623[/ATTACH]

hints??
thanx in advance

i'm getting that same error too bad i didn't sign up back in 94 like some other user suggested. i signed up in 2001 -__-.

---

### Post by sirdouglas on 2008-11-12
I'm back... I know, I know you're thinking "What did he screw up now?"...

Well, a few simple things.  I'm still getting my mail (I think all of it at least) and I *love* using Evolution for email instead of opening firefox everytime.  But is it supposed to erase my entire online inbox?  When I check my hotmail using firefox, I have absolutely no messages in my inbox when there should be a few hundred.  And I'm assuming that other hotmail folders don't naturally work with evolution (specific folders I made to save messages)?

Next, my mom just sent me an email asking why I keep sending the same email over and over again.  She's received it a few dozen times now.  I have noticed that every time I open Evolution a box opens saying "Fetching mail" and it also says "Sending message 1 of 2."  Sending what message?.. probably the same 2 over and over again.  And when I close Evolution a message pops up saying "You have unsent messages, do you wish to quit anyway?  If you quit, these messages will not be sent until Evolution is started again."

And lastly, I randomly get this error which I unfortunately can't remember at the moment... some about "DAT"?... nevermind if you have no idea what I'm talking about:)

Thanks guys once again for your help!

Doug

EDIT: Now I just accessed my hotmail account from firefox and found there to be 67 unread messages from the past few days in my "DELETED MESSAGES" folder... alright so now my emails are automatically getting deleted.  I think it's about time to say that I tried my best, but it just wasn't meant to be.  I've tried deleting the account and starting over, but for some reason Evolution doesn't like me.

---

### Post by kubug on 2008-11-12
> **sirdouglas said:**
> I'm back... I know, I know you're thinking "What did he screw up now?"...

Well, a few simple things.  I'm still getting my mail (I think all of it at least) and I *love* using Evolution for email instead of opening firefox everytime.  But is it supposed to erase my entire online inbox?  When I check my hotmail using firefox, I have absolutely no messages in my inbox when there should be a few hundred.  And I'm assuming that other hotmail folders don't naturally work with evolution (specific folders I made to save messages)?

Next, my mom just sent me an email asking why I keep sending the same email over and over again.  She's received it a few dozen times now.  I have noticed that every time I open Evolution a box opens saying "Fetching mail" and it also says "Sending message 1 of 2."  Sending what message?.. probably the same 2 over and over again.  And when I close Evolution a message pops up saying "You have unsent messages, do you wish to quit anyway?  If you quit, these messages will not be sent until Evolution is started again."

And lastly, I randomly get this error which I unfortunately can't remember at the moment... some about "DAT"?... nevermind if you have no idea what I'm talking about:)

Thanks guys once again for your help!

Doug

EDIT: Now I just accessed my hotmail account from firefox and found there to be 67 unread messages from the past few days in my "DELETED MESSAGES" folder... alright so now my emails are automatically getting deleted.  I think it's about time to say that I tried my best, but it just wasn't meant to be.  I've tried deleting the account and starting over, but for some reason Evolution doesn't like me.

As to why your messages are getting deleted, the first post mentioned this:
> By default, hotway leaves a copy of each message it downloads on the server. I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:


pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r



Notice the "-r" at the end there? If you added that in your /etc/inetd.conf file then what you described is going to happen. Check that, and if it is there, remove the "-r"! 

As to your issue with the same emails sending over and over, I would check that you have no unsend messages on the hotmail account via firefox and send them or erase them there. It should work fine after that. Dunno.

Hope that helped.

---

### Post by Antioch on 2008-11-14
> **lyminhtriet said:**
> Now, @hotmail (@msn or @live) support IMAP. When I use OutlookConnector to synchronize my MS Oulook with [email]xxx@msn.com[/email]. The wonderful things is Connector also can synchronize my contact and Calendar. 

Now I decide using Ubuntu and must take Evolution mail. 

I wonder, how can I combine Evolution mail with IMAP live mail?

Can you help me?

Tks

What IMAP are you talking about?

---

### Post by Lotrean on 2008-11-15
I get an error:

Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Unable to find folder inbox on remote server

i'm pretty sure that I typed the right pass, i logged to hotmail from firefox... Any help, please? Pretty please? :)

---

### Post by 666porcondissaum on 2008-11-15
Lot... after the post after a few comments there are a little correction... in the line that is:

2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd

... should be

2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtp

Got it?

No 'd' in the endline...

Well... and after this there are another corrective cause... use the pop3hot.com for the POP server...

Well... everything is done... got a success message and... there's no e-mail but my box in hotmail has... where is it?

---

### Post by 666porcondissaum on 2008-11-15
> **forgeuk said:**
> OK, mine's working fine, thanks to the original poster!

This is more of an evolution question, I'd like my hotmails to go into a seperate folder that I've just made, but I can't seem to see a way to do a message rule for it. Is there a way to set up a rule to filter by account rather than by subject or sender?


[COLOR="Red"]Ignore that...found it, its Add then choose source account from the drop down...nice[/COLOR]
It is now also possible to get any folder you like instead of just the inbox. Just put the name of the folder you want after the domain in
your email address with a forward slash. For example, to get the folder named "hello" you would issue the command "user [email]dave@hotmail.com[/email]/hello" at the prompt. So this means in your mail reader you should enter the user name as "dave@hotmail.com/hello". You will need to create a new mailbox in your mail reader for each folder. Work continues on an IMAP implementation of hotwayd which will circumvent this folder hack due to the native folder support in IMAP.

---

### Post by Michael12uk on 2008-11-25
Can't be my friend uses Mac and he is able to use an email client called  entourage. He hasen't signt up. He uses the regular account!!

---

### Post by ludder on 2008-11-26
I get this:

-ERR Unable to find folder inbox on remote server
-ERR That command is not available right now.

Regular hotmail.com account.

Can anyone explain why it doesnt work for me? Seems to work for everybody else.

---

### Post by zzztownsend on 2008-12-05
Hi folks -- A SOLUTION!

I fought for ages with Getlive ([www.sourceforge.net/projects/getlive](www.sourceforge.net/projects/getlive)) which worked of a fashion but a proper fiddle to get going. After a clean install of intrepid I decided to have a look around to find alternatives. This thread looks like HOTWAY only works if you have the right vintage of hotmail account.

So heres an alternative:

to get hotmail - using freepops ([www.freepops.org](www.freepops.org))
go to website
download .deb package
download updated hotmail.lua
install .deb package (from nautilus)
copy the updated hotmail.lua to /usr/share/freepops/lua
restart daemon: sudo /etc/init.d/freepops restart

then configure evolution:
Add mail account
Name:  <your name>
Email address <your full hotmail email address>
-->Forward
server type: POP
Server: 127.0.0.1:2000   (NOTE PORT 2000 !! IMPORTANT !!)
Username: <your full hotmail email address, incl domain>
No encryption
Authentication: password
Tick remember password
-->Forward
Checking for new mail - probably best to leave this un-ticked and get messages manually when you want to, by clicking Send/Receive. Avoid repeat slow logon and tipping MS off that you are using a scraper (against MS terms of use I believe)
Message storage
accept defaults
-->forward
Sending email. You can't!! but evolution demands info so I suggest server type SMTP, server <insert junk>, untick 'server requires authentication.
-->forward
Account info
Whatever you want to call it, I use 'hotmail via freepops'
-->forward
-->apply

Click 'send / receive' button on evolution toolbar
When prompted for a password enter your usual *HOTMAIL* password
****************************

BONZA worked first time no aggro. Recommended

Good luck if you decide to give it a go

Cheers

Matt

---

### Post by Rubicon421 on 2008-12-08
I'm trying to get all my old emails from hotmail to gmail. I went into hotmail and marked them all as unread, then added the hotmail accout to gmail using a free POP access website. It only got some of the mail though. I don't need constant POP access because I'm just trying to get rid of hotmail alltogether but I want to keep my old emails and there are too many to forward one at a time. 

How else can I just transfer all of them to gmail?

---

### Post by pwhitted on 2008-12-13
[SOLVED] I tried the FreePops steps zzztownsend provided, but I received the following error message in Evolution:

Error while Fetching Mail.
Unable to connect to POP server 127.0.0.1.
Error sending password: Operation now in progress

I've tried exiting Evolution and restarting the FreePops service, but still no workee. Clues?

[EDIT]: I found a link that described changing the FireFox configuration value for general.useragent.vendor from "Ubuntu" to "Firefox" - and it worked! After rebooting I was able to receive all my Hotmail mail.

[UPDATE]: As noted by zzztownsend, FreePops only works for receiving your Hotmail. I found that if I also installed HotSMTP, I could also send from my Hotmail account to other email accounts through Evolution. Just search forums for details on how to install hotsmtp and configure with Evolution. Most instructions include installing hotway to receive Hotmail mail, but just skip those steps and execute the hotsmtp steps and you're good to go!

---

### Post by handyi on 2008-12-18
it works perfectly the reception but don't work the sending

---

### Post by gfxfreak on 2008-12-20
Thank you so much! hotmail on evolution! wooow! you are my hero! I won't leave linux again...ever! :D

---

### Post by deepee_oz on 2008-12-21
This had been working great using the details of ZZTOWNSEND's post for about 3 weeks but for no apparent reason I can't check hotmail anymore.
Started getting the following error: 
Unable to connect to POP server 127.0.0.1
Error sending password: -ERR NETWORK ERROR
Please enter the POP password for (my email account) on host 127.0.0.1

Checked the password in a firefox hotmail session and it is correct.
Shutdown and restarted the freepops server ok but still no joy.
Uninstalled the freepops packages and re-installed - no change.
Tried changing the POP server value in the Evolution mail account from 127.0.0.1 to "localhost" - both return the same error.
Tried changing the FireFox configuration value for general.useragent.vendor from "Ubuntu" to "Firefox" - still nothing.

Anyone else having issues?

---

### Post by lukeyduke on 2008-12-22
Hello,
Just letting you know that I have recently upgraded to a fantastic webmail client, Atmail. They are a commercial email server appliance and webmail provider, however they have recently released a free version of their software, called atmail open. The biggest advantage is that I can now access my emails from anywhere in the world from the same fantastic interface every time. I find it is a much faster, simpler, better looking interface than any other, such as hotmail and gmail.

You can find an tutorial for installing it on there website here --> [http://atmail.com/kb/2008/installing-atmail-open-webmail-client-on-ubuntu/]("http://atmail.com/kb/2008/installing-atmail-open-webmail-client-on-ubuntu/")

---

### Post by kingcharles1666 on 2008-12-23
The freepops method works great, also for windows live mail.

just use this format for your username:

[email]xxxxxxx@hotmail.com?domain=live.xxx[/email]

---

### Post by dragos240 on 2008-12-30
Is there any way to make the first method work? IF so that would be great

---

### Post by Michael12uk on 2009-01-11
thx worked for me us well

---

### Post by linfidel on 2009-01-18
> **deepee_oz said:**
> This had been working great using the details of ZZTOWNSEND's post for about 3 weeks but for no apparent reason I can't check hotmail anymore.
Started getting the following error: 
Unable to connect to POP server 127.0.0.1
Error sending password: -ERR NETWORK ERROR
Please enter the POP password for (my email account) on host 127.0.0.1
. . .Anyone else having issues?
I get a similar type of error (I'm using Thunderbird).  I ran the server from a terminal using the command "freepopsd -w", which prints out lots of debug commands.  The error wasn't due to a wrong password, but that's just what the pop client thinks because it's the last error.

I used the output along with the script (hotmail.lua) and it seems that hotmail has changed their protocol so it no longer matches what the script is looking for.  I remember recently accepting some Hotmail upgrade to a newer and greater UI, so I suspect that's the problem.  Perhaps the people who say it works great did not make this change.

I tried hacking a little with the script, and made it get one step further, but it got another similar failure (string did not match).  It's not really important enough to me to spend more time trying to figure it out and fix it, as I rarely use Hotmail (which is partly why I wanted some notification to tell me if I got mail).  Gmail is so much nicer - it can forward to another account, or you can use pop.  I don't know why Hotmail can't be a little more user friendly.

If I had been using it a long time, I'd switch to gmail, then set up a vacation response in Hotmail telling everyone my new address, and check Hotmail every once in a while to see if anything important was there, and try to change the address for those that didn't switch over to the new address.  Or send feedback complaining about how bad it is.

---

### Post by brimurray on 2009-01-19
Done all this, but I cannot send or receive as constantly asking for password for 127.0.0.1 despite inputting correct one!

---

### Post by jrz on 2009-01-19
Thanks, this worked very nicely.

---

### Post by RavanH on 2009-01-27
After 2.5 years and two completely new Ubuntu versions, still very valid how-to. Thanks Indras ! :)

---

### Post by Baby Boy on 2009-01-28
> **brimurray said:**
> Done all this, but I cannot send or receive as constantly asking for password for 127.0.0.1 despite inputting correct one!

Same here. :(

Trying to make it work for live.com BTW. So what linfidel said is true, there is some change in the protocol so this doesn't work now?

---

### Post by manoka on 2009-02-03
> **zzztownsend said:**
> Hi folks -- A SOLUTION!

I fought for ages with Getlive ([www.sourceforge.net/projects/getlive](www.sourceforge.net/projects/getlive)) which worked of a fashion but a proper fiddle to get going. After a clean install of intrepid I decided to have a look around to find alternatives. This thread looks like HOTWAY only works if you have the right vintage of hotmail account.

So heres an alternative:

to get hotmail - using freepops ([www.freepops.org](www.freepops.org))
go to website
download .deb package


I can follow only as far as this. It sounds promicing, but as a newbie I don't know how to do all the steps.

From where do you download the "updated hotmail.lua"?

How does one "install .deb package (from nautilus)"?

And how exactly do you "copy the updated hotmail.lua to /usr/share/freepops/lua"?

> restart daemon: sudo /etc/init.d/freepops restart
I guess "sudo /etc/init.d/freepops restart" would be entered in the terminal.

> Username: <your full hotmail email address, incl domain>
What might be the "domain"?

> Message storage
accept defaults
I can't see this option.

> Sending email. You can't!!
Sorry, but with this solution it's only possible to receive e-mails?

I have my hotmail account at least for five years and never changed anything. At some time it was automatically changed to Windows Live.

Many thanks in advance!

---

### Post by linfidel on 2009-02-03
> **manoka said:**
> I can follow only as far as this. It sounds promicing, but as a newbie I don't know how to do all the steps.

From where do you download the "updated hotmail.lua"? 
I assume this is on the freepops website; lua is a free scripting language that must be used to parse the html and get the mail.

> How does one "install .deb package (from nautilus)"?
Simply double-click on it.  .deb files are associated with the package manager.

And how exactly do you "copy the updated hotmail.lua to /usr/share/freepops/lua"?
That's not as easy as it seems, because you need su ("admin") authority to write to that directory.  At the terminal, you would find the lua file, then```
 "sudo cp hotmail.lua /usr/share/freepops/lua"
```> I guess "sudo /etc/init.d/freepops restart" would be entered in the terminal.That would be the most satisfying place to enter it.

> What might be the "domain"?
hotmail.com - the domain for a URL is always the part after the @ sign.

> I can't see this option.  It's not an option.  It means don't change any of the existing settings, which are normally set to reasonable default values.

> Sorry, but with this solution it's only possible to receive e-mails?You should be able to use your ISP's SMTP server for sending mail.  In the old days, you needed a POP server to get mail, and an SMTP server to send mail; they don't need to be the same.  In the really old days, you could use any SMTP server to relay mail, because there was no authentication, but now they either require login, or you need to be withing the range of IP addresses for the provider.

I have my hotmail account at least for five years and never changed anything. At some time it was automatically changed to Windows Live.

I hope this helps.  I've never actually used this service, so I don't know details, but I thought I might be able to help you somewhat.

By the way, I just read that Microsoft has started allowing POP/SMTP for regular hotmail.  It's available in several countries already, and the rest will follow later this year.
[http://windowslivewire.spaces.live.com/blog/cns!2F7EB29B42641D59!32413.entry]("http://windowslivewire.spaces.live.com/blog/cns%212F7EB29B42641D59%2132413.entry")

---

### Post by manoka on 2009-02-04
Many thanks linfidel!

I think I was able to follow your instructions, as well as the ones from [http://windowslivewire.spaces.live.com/blog/](http://windowslivewire.spaces.live.com/blog/)...

But even though it reads there that: "...now that Hotmail has POP3,...", now I'm getting the following error message:
> Unable to connect to POP server pop3.live.com.
Error sending password: -ERR user does not have POP3 access
Please enter the POP password for ...@hotmail.com on host pop3.live.com.

I tried a couple of times unsuccessfully to use my regular hotmail login password, as well as another one I was required to create for a keyring(?) or whatever.

Any suggestions highly appreciated!

P.S. At [http://windowslivewire.spaces.live.com/blog/](http://windowslivewire.spaces.live.com/blog/)... it also reads:
> To be able to use POP3, you need to have a Windows Live Hotmail Plus subscription. However, free users can access their emails offline either through Microsoft Outlook Connector or Windows Live Mail Client.
Thus it seems like there's no way to Evolution for those with a free Hotmail account.

On the other hand it reads at [http://windowslivehelp.com/solutions/settings/archive/2009/01/13/pop3-availability-in-windows-live-hotmail.aspx](http://windowslivehelp.com/solutions/settings/archive/2009/01/13/pop3-availability-in-windows-live-hotmail.aspx)
> As part of Phase 1, we have rolled  this feature out to all free users in the following countries: 
UK, Canada, Australia, France, Japan, Spain, Germany, Italy, and the Netherlands. 
Next Phases are still in planning and US will be included in Phase 2 which is targeted sometime in the month of February. We will be updating this solution article with more specific dates as we get closer to the migration.
Users registered in the countries mentioned above will be able to use the POP services for free and will not require a subscription to do so.
I suppose we might try again later this month.

---

### Post by Deadwhisper on 2009-02-05
I'm a newbie at this so please help me with this problem. I have a live.com account. 

I ran through the OP's steps and everything went well up to the point where I hit the "Send/Recieve" button. After asking for my password an error message came up. It reads the following:

> Unable to connect to POP server 127.0.0.1
Error sending username: -ERR Please log in with USER first

Please enter the POP password for <myemail>@live.com on host 127.0.0.1

The password I entered is correct because I checked it by going to home.live.com and entering my username and password there. I logged in just fine there.

I've tried changing the username to <myemail>@hotmail.com?domain-live.com because I read somewhere that this would work. No luck though. I also switched "Authentification Type" from "Password" to "Login" in both "Receiving Email" and "Sending Email" with no success. I tried combinations of the above with no luck either.

Right now I have the following setup.

Running on Ubuntu 8.10 (Gnome)
Account properties/editor shows the following information for my mail account
Receiving Server Type = POP
Receiving Server = 127.0.0.1
Receiving Username = <myemail>@live.com
Receiving Security = No encryption
Receiving Authentification Type = Password
Sending Server Type = SMTP
Sending Server = 127.0.0.1:2500
Sending Security = No encryption
Sending Authentification = Plain
Sending Username = <mymail>@live.com

Please help. Will my live.com email account work with Evolution? if so, do you see any errors in the information above that can be corrected? Do you know of any solutions to the issue above?

Any and all help will be appreciated. And again, I'm a newbie when it comes to linux so please, only assume I know nothing and can only follow detailed instructions.

Thx

---

### Post by MellonCollie on 2009-02-06
If you want to use pop3 but you don't live in UK, Canada, Australia, France, Japan, Spain, Germany, Italy, or Netherlands, [try this](http://www.mydigitallife.info/2009/01/22/hack-to-enable-hotmail-pop3-and-smtp-support-instantly-for-all-countries/).

Create a standard pop3 account. Your settings in Evolution should look like this...


[ATTACH]102458[/ATTACH]

[ATTACH]102459[/ATTACH]

---

### Post by kill5witch on 2009-02-07
Just wanted to say thanks for you efforts. This worked well for me too :)

---

### Post by Jyncka on 2009-02-08
Thanks for this how-to, it was incredibly helpful!:KS

---

### Post by Milk Rulz on 2009-02-15
I did everything exactly as you said for hotmail and I got this:


Unable to connect to POP server 127.0.0.1.
Error sending password: -ERR Unable to find folder inbox on remote server

Please enter the POP password for
[email]xxx@hotmail.com[/email] on host 127.0.0.1. (yes I replaced [email]xxx@hotmail.com[/email] with my email)

---

### Post by Coinneach on 2009-02-16
Awesome! Works great :)
Thanks

---

### Post by Kerel on 2009-03-02
Everything worked fine, but I had to manually check the box 


Receiving Options -> Message Storage -> "Leave messages on server"

That sucked, anyone knows how to put the messages back on the server?

---

### Post by tcavazos on 2009-03-11
Thanks mate, it worked perfect for me.

---

### Post by fibrewire on 2009-03-12
1) Disregard everything that you have read previously in this post because this is information directly from Microsoft Windows Live - it works!

2) Please don't post after this, as it will just confuse others that need this information - as I did 6 months ago with completely useless forum answers.

Configuration Settings:

    * Incoming Server = pop3.live.com
      -Port 995
      -Encryption/Authentication = SSL is required
      -Full Username = [email]username@xxxx.com[/email] (same as full email address, where xxxx.com = live.com, msn.com or hotmail.com )
      -Password is required
      -SPA(secure password authorization) = Off(uncheck this option)
    * Outgoing Server = smtp.live.com
      -Port 25 or 587 [Note: Preferred Outgoing is Port 587 instead of Port 25 since many ISP&#8217;s blocks Port 25 use. Similar blocking can occur when using Port 25 in hotels or accessing via a WiFi network]
      -Outgoing Server Authentication = On(check the option)

      -Encryption/Authentication = SSL or TLS
      * Choose SSL for Windows Live Mail, Outlook 2003, iPhone, iPod Touch, Outlook Express and Vista's Windows Mail * Choose TLS for Outlook 2007 (required)
      -Full Username = [email]username@xxxx.com[/email] (same as full email address)
        - unless outgoing server is configured to use same incoming server option
      -Password is required
        - unless outgoing server is configured to use same incoming server option

* To specify a port in Evolution - "pop3.live.com:995" and "smtp.live.com:587"

* To prevent Evolution from emptying your webmail Inbox - "Receiving Options -> Message Storage -> Leave messages on server"

---

### Post by andymac69 on 2009-03-13
I've had Hotmail in my Outlook Express for years. Now it works great in Evolution, thanks.

---

### Post by linfidel on 2009-03-13
As has been stated here and in the news, Microsoft has recently been enabling POP for free customers, starting last month.  This information is not even on the Hotmail web site yet.

It's not that the information in this thread has been incorrect; it's that the changes with Hotmail just happened.  Anyone that didn't pick up on that didn't read this thread very carefully, and probably still won't be able to connect due to lack of reading comprehension. :lol:

---

### Post by kevh on 2009-03-15
Thanks fibrewire. The previous advice hadn't worked for me. This did the trick.
Kev

---

### Post by Ome Knomee on 2009-03-19
Hey guys just a heads up. I tried this method today (19/03/2009) and it does not work. I get an error message after I enter my password saying "You need to pay money to get this service" so what I gather from the error is that to have your Hotmail emails coming into Evolution you need to pay Microsoft. Just another reason to choose Linux :P




-- Gone off Microsoft . . . Never Going Back --

---

### Post by joserpena on 2009-03-22
Hi Fibrewire,

Thanks for advice. Would you give us specific instructions on implementing Hotmail settings in Evolution?

I'm asking because POP3 is working fine for me, but SMTP isn't working. I'd like to know exact configurations for following options:
[LIST]
[*]Secure connection
[*]Authentication type
[*]username (full or just login)
[/LIST]
I'm using server smtp.live.com:587. Tried port 25 too.

Thanks again.

José

---

### Post by guv999 on 2009-03-29
Many thanks fibrewire - all working well for me now

---

### Post by sightl3ss on 2009-03-29
EDIT:

lol, sry for compulsive posting eheh >.<

It all works PERFECTLY! Many many thanks fibrewire, what I did was change from encryption SSL to TSL in the  and it all worked perfectly.

Again, sorry for posting so fast without attempting to fix it first :P many thanks fibrewire.

---

### Post by gsiliceo on 2009-04-04
[http://arstechnica.com/microsoft/news/2009/03/rollout-for-hotmail-pop3-worldwide-support-complete.ars?utm_source=microblogging&utm_medium=pingfm&utm_term=Main%20Account&utm_campaign=microblogging](http://arstechnica.com/microsoft/news/2009/03/rollout-for-hotmail-pop3-worldwide-support-complete.ars?utm_source=microblogging&utm_medium=pingfm&utm_term=Main%20Account&utm_campaign=microblogging)

---

### Post by naveensn on 2009-04-05
Thanks Fibrewire. Its working for me.

---

### Post by ruibrito on 2009-04-09
hi, i use the tutorial that's in page 1 (the first one), and I got only this error when i try to download my mail from **hotmail**:

"-ERR unable to find folder inbox on remote server"

i belive it's because of POP and i yet cannt find a way to put hotmail to work in EVOLUTION.

i try to find pop3.com and fail.

please help and sorry if this inst the first something like this happens

best regards

---

### Post by lisati on 2009-04-12
> **ruibrito said:**
> hi, i use the tutorial that's in page 1 (the first one), and I got only this error when i try to download my mail from **hotmail**:

"-ERR unable to find folder inbox on remote server"

i belive it's because of POP and i yet cannt find a way to put hotmail to work in EVOLUTION.

i try to find pop3.com and fail.

please help and sorry if this inst the first something like this happens

best regards

Ditto.....setup according to first post, but got the same error.....

---

### Post by RavanH on 2009-04-13
Installation of hotwayd as described in the first post is no longer needed. It is mentioned earlier in this thread, but that info gets snowed under because every time new posts are added...

Since some time now, you can use the following settings just like any regular POP account:

```
Incoming server: pop3.live.com
Username: your_username @hotmail.com
Use secure connection: SSL
Authentication type: password

Outgoing server: smtp.live.com
Server requires authentication: yes
Security: SSL
Authentication type: plain
```

With these settings, you should be able to get is working without going through the hotway deamon (on 127.0.0.1) ...

---

### Post by Nevon on 2009-04-15
I tried using the settings described in the last two pages, and it still doesn't work. I get prompted for my password, and when I enter it I get: "Unable to connect to POP server pop3.live.com. Error sending password: resource temporarily unavailable."

---

### Post by dphirschler on 2009-04-16
> **Nevon said:**
> I tried using the settings described in the last two pages, and it still doesn't work. I get prompted for my password, and when I enter it I get: "Unable to connect to POP server pop3.live.com. Error sending password: resource temporarily unavailable."

I had the above error until I corrected my username to [email]xxxxxxxxxxx@hotmail.com[/email] (note, I had to add the '@hotmail.com' part).  Hell yeah!  Hotmail in Linux, baby!


Darryl

---

### Post by Nevon on 2009-04-16
> **dphirschler said:**
> I had the above error until I corrected my username to [email]xxxxxxxxxxx@hotmail.com[/email] (note, I had to add the '@hotmail.com' part).

I already had the @hotmail.com part in there. So that's not my problem, unfortunately.

EDIT: Oh man, I am such an idiot! My C key is kind of busted, so I had accidentally written xxxxxxxxx@hotmail.**om**. Now it's working as it's supposed to.

---

### Post by dphirschler on 2009-04-19
Well it appears to work fine, but at closer inspection I can only receive hotmail.  I still cannot send.  I've checked and rechecked my settings and I can't think of what I might have missed.  I am using the new pop3 settings posted above... which are also spelled out in Microsoft's press release.

```
Incoming server: pop3.live.com
Username: your_username @hotmail.com
Use secure connection: SSL
Authentication type: password

Outgoing server: smtp.live.com
Server requires authentication: yes
Security: SSL
Authentication type: plain
```


Darryl

---

### Post by willj on 2009-04-19
Hello, i to am having issues with the sending emails part.  Getting error saying "Could not connect to smtp.live.com; Connection timed out"

---

### Post by willj on 2009-04-19
> **avtolle said:**
> Thanks. However, should be hotsmtp, not hotsmtpd as set out in the third code step in your original post.:KS

ok i got it working using the original tut.  however the first time i did it, i didn't add the d like stated in the quote above.  Went back added the d and everything works like it should.  Again original tutorial works great, thanks.

---

### Post by dphirschler on 2009-04-23
OK, I think I have some answers.  It turns out my ISP, Bellsouth.net (which is now att.net) is blocking port 25 which is what Hotmail wants to use.  They have a fix on their website which basically has you using their smtp server for sending emails.  I found the fix by searching their website for "smtp port 25".

For me, I had to go into Evolution's Hotmail settings and change the sending server to mail.bellsouth.net.  Then I had to say "no encryption" and change the Authentication Type to "Login" and then put in my bellsouth email address in the username field.  Finally check "remember password".

So now I can send and receive Hotmail using Evolution.  However I have noticed that deleting emails here in Evolution and then checking my hotmail through the web interface, the emails are still there.  So it behaves differently than Outlook did in my Windows PC.  In Outlook, when I deleted an email, it would delete it locally as well as on the Hotmail web werver.  Maybe there is still some setting I need to check.  

At least we are one step closer.  Why can't it "just work" like gmail?


Darryl

---

### Post by dphirschler on 2009-04-23
OK, I think I have some answers.  It turns out my ISP, Bellsouth.net (which is now att.net) is blocking port 25 which is what Hotmail wants to use.  They have a fix on their website which basically has you using their smtp server for sending emails.  I found the fix by searching their website for "smtp port 25".

For me, I had to go into Evolution's Hotmail settings and change the sending server to mail.bellsouth.net.  Then I had to say "no encryption" and change the Authentication Type to "Login" and then put in my bellsouth email address in the username field.  Finally check "remember password".

So now I can send and receive Hotmail using Evolution.  However I have noticed that deleting emails here in Evolution and then checking my hotmail through the web interface, the emails are still there.  So it behaves differently than Outlook did in my Windows PC.  In Outlook, when I deleted an email, it would delete it locally as well as on the Hotmail web werver.  Maybe there is still some setting I need to check.  

At least we are one step closer.  Why can't it "just work" like gmail?


Darryl

---

### Post by ubuntu01 on 2009-04-24
These settings work with no other configuration needed /required:

Incoming server: pop3.live.com
Username: your_username @hotmail.com
Use secure connection: SSL
Authentication type: password

Server: smtp.live.com
Use Secure Connection: TLS Encryption
Authentication Type: Login

---

### Post by brownybrowny on 2009-04-24
This is a wonderful opinion. The things mentioned are unanimous and needs to be appreciated by everyone.


vichi.......
[http://www.hotmail247.com]("http://www.hotmail247.com/")

---

### Post by tentaro on 2009-04-27
Let me just say this is my first time using Ubuntu but I have worked on Unix in the past. I am having 1 small problem with this set up when I try to install hotway it tells me :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway


and even if I try anything else it just laughs at me :)  I downloaded the install and extracted to me /usr folder but it still won't install.....Is there some strange thing I need to do to get this to work. It just took me like 1.5 days to fix the Nvidia SLI problem I was having and this doesn't seem like it will be any easier. I am really looking for an alternative to M$ but this is starting to make me wonder if this is the one. Please any help would be appreciated. New: I found the other post about hotmail and used those hotmail is now working.

---

### Post by tentaro on 2009-04-27
> **ubuntu01 said:**
> These settings work with no other configuration needed /required:

Incoming server: pop3.live.com
Username: your_username @hotmail.com
Use secure connection: SSL
Authentication type: password

Server: smtp.live.com
Use Secure Connection: TLS Encryption
Authentication Type: Login


This worked great but unfortunatley it doesn't download my Junk mail, not sure y but if anyone knows, please let me know. Sometimes important things come in my junk folder before I can add the to acceptable mail. Thanks

---

### Post by Immortaly007 on 2009-04-28
Yay, my first post here :D anyway, on to business/questions:
I also get the connection timeout error on the smtp.live.com server. I tried the hotway/hotsmtp as well, but that didn't work either. pop3.live.com however seems to work flawlessly.

---

### Post by mcrene on 2009-04-29
seems there are some common problems as of late

this is the message I am receiving

Error while performing operation.
Could not connect to 127.0.0.1: Connection refused
Could not connect to 127.0.0.1: Connection refused
Could not connect to 127.0.0.1: Connection refused
Could not connect to 127.0.0.1: Connection refused

I am not able to send or receive my normal Hotmail emails, not through evolution atleast, which is all I use.
Its back to logging onto MSN all the time, dang it, here and I thought I was rid of the MSN monster.

Hope the powers that be can figure this out.
Thanks

---

### Post by stevefrisby on 2009-05-01
Have just set up evolution with hotmail using information on this web site
[http://www.liveside.net/main/archive/2009/03/13/pop3-technology-has-now-rolled-out-to-hotmail-customers-worldwide.aspx](http://www.liveside.net/main/archive/2009/03/13/pop3-technology-has-now-rolled-out-to-hotmail-customers-worldwide.aspx)

---

### Post by caco on 2009-05-09
Hello folks, [http://ubuntuforums.org/showthread.php?t=1143295](http://ubuntuforums.org/showthread.php?t=1143295) might be interesting to read.

---

### Post by redmistpete on 2009-05-20
Cant' get it to work :( It keeps rejecting my SMTP password authentication

---

### Post by bkbilly on 2009-05-22
forget about izymail.com!!!
I found a way to enable hotmail pop3 from [here]("http://www.mydigitallife.info/2009/01/22/hack-to-enable-hotmail-pop3-and-smtp-support-instantly-for-all-countries/")

Here are the instructions and in this forum:
   1. Login to Hotmail.
   2. Mouse over Options, and then click on More Options.
   3. Click on View and edit your personal information link under “Manger your account” section.
   4. Click on Registered Information link.
   5. For both Home Location and Work Location, change the following details to specified values:
> 
      Postal Code: WC1B 3DG
      Constituent Country: England
      Time zone: London, United Kingdom - GMT
   6. Click on Save when done.
   7. Go back to Hotmail, and ensure that the display language of Hotmail is set to English by mouse over the Options.
   8. Configure your email client or other webmail service (Gmail configuration to access Hotmail via POP3) to access and download Hotmail Inbox via POP3 protocol, using the Hotmail POP3 and SMTP configuration settings.
   9. The email client or another mail service provider should be able to access, login and download or send through Hotmail server without error.
  10. Once Hotmail POP3 and SMTP support is enable on the account, it’s possible to change and revert back to your original web interface language, home and work location.

Hotmail POP3 and SMTP configuration settings.> 
Incoming Server (POP3 Server): pop3.live.com
Incoming Server POP Port: 995
Incoming Server POP SSL Encryption: Yes (On or Required)

Outgoing Server (SMTP Server): smtp.live.com
Outgoing Server SMTP Port: 25
Outgoing Server Authentication: Yes (On - Use POP username and password or Hotmail credentials)
Outgoing Server TLS or SSL Secure Encrypted Connection: Yes (On or Required)

User Name: Windows Live ID (e.g. [email]yourname@hotmail.com[/email])
Password: password used to sign in to Hotmail or Windows Live service

Note: “Log on using Secure Password Authentication (SPA)” check box in Outlook, Outlook Express or Windows Live Mail should not be selected.

---

### Post by feriender on 2009-06-08
The configuration was described above did not work in Ubuntu 9.04, but the following configuration helped:

#0. install and set up hotwayd

#1. add the following lines to /etc/hosts AND to /etc/hosts.allow
```

hotwayd:127.0.0.1
hotsmtpd:127.0.0.1

```

#2. to /etc/inetd.conf
```

pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd
2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd

```

#3. to /etc/xinetd.d/hotsmtpd
```

service hotsmtpd
{
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = nobody
groups = yes
server = /usr/bin/hotsmtpd
#server_args = -r
port = 25
}

```

#4. to /etc/xinetd.d/hotwayd
```

service hotwayd
{
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = nobody
groups = yes
server = /usr/bin/hotwayd
server_args = -r
port = 110
}

```


#7. use the settings in Evolution:
Receiving: POP, server: 127.0.0.1, No Encryption, Password
Sending (!): server:127.0.0.1, reques authentication, No encryption, PLAIN

#6. restart xinetd

---

### Post by bkbilly on 2009-06-08
> **feriender said:**
> The configuration was described above did not work in Ubuntu 9.04, but the following configuration helped:
.
.
.


The configuration I wrote works on ubuntu 8.10...
I haven't tried it on 9.04.

---

### Post by MrLeN on 2009-06-12
> **Indras said:**
> Okay everyone, after digging around in these forums and googling like I've never googled before, I figured out how to send and receive e-mail through hotmail using Evolution.  I'm throwing together a rough HOWTO for others.  If things need more clarification, let me know and I'll update it.

**First, make sure your system is up to date.  Open up a terminal and type:**

```
sudo apt-get update
```

**Now, install the inet daemon**

```
sudo apt-get install inetutils-inetd
```

**This takes care of all of our dependencies.  Now on to the good stuff...**

```
sudo apt-get install hotway hotsmtp
```

**This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP.  By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.**

```
sudo gedit /etc/inetd.conf
```

**Look for a line like this:**

```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd
```

**By default, hotway leaves a copy of each message it downloads on the server.  I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:**

```
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r
```

**And we also need to add a line to get hotsmtpd working, just paste this at the bottom:**

```
2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd
```

**This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon.  Now, save your file, exit gedit, and restart your inetd server:**

```
sudo /etc/init.d/inetutils-inetd restart
```

**If everything is working properly, you'll see this pop up on your screen:**

```
* Restarting internet superserver inetd                            [ ok ]
```

**Now, close out of your terminal and start up Evolution.  It may pop up the first-time use wizard, you can use that if you like.  Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left.  However you choose to do it, here's your information:**

**Email Address:** *xxx*@hotmail.com  (fill in your normal e-mail address that you use to login to hotmail)

**Receive Server type:** POP
**Server:** 127.0.0.1
**Username:** *xxx*@hotmail.com (same as above)
**Security:** No encryption
**Authentication type:** Password
(Remember password checkbox is up to you)

**Send Server type:** SMTP
**Server:** 127.0.0.1:2500
**[X] Server requires authentication** (check this box)
**Use Secure Connection:** No encryption
**Authentication Type:** PLAIN
**Username:** *xxx*@hotmail.com (same as above)
(Optional Remember password checkbox)
wow thanks.. this worked perfectly.

Is there any way in future that Hotmail will realise how this is done and then put a stop to it?

If it is likely -- how likely?

---

### Post by WouterKvG on 2009-06-22
from [http://ubuntuforums.org/showthread.php?t=1124293](http://ubuntuforums.org/showthread.php?t=1124293)

> **Paresh said:**
> Now that pop3 is available FOC from Hotmail, you can amend your evolution account:-

Receiving email
Server Type = POP
Server = pop3.live.com
Secure Connection = SSL encryption

Sending email
Server Type = SMTP
Server = smtp.live.com
Secure Connection = TLS encryption

All other settings stay the same.

Not sure why TLS works for sending and SSL for receiving, but this is what worked for me.

The only thing is that it does seem to download all messages on the server, _***even if they were downloaded previously***_.

More info [here]("http://windowslivehelp.com/solutions/settings/archive/2009/01/06/send-and-receive-windows-live-hotmail-emails-from-a-mail-client.aspx")

Now I use Thunderbird with the Webmail extension, this seems to work just fine. I'm trying to fix it in evolution too.

---

### Post by darkeale on 2009-08-04
hi,

when i try and do this line:-

sudo apt-get install hotway hotsmtp

i get the error "couldn't find package hotway"

any way around this?

thanks,
Alex

---

### Post by Elisavan on 2009-08-06
> **darkeale said:**
> hi,

when i try and do this line:-

sudo apt-get install hotway hotsmtp

i get the error "couldn't find package hotway"

any way around this?

thanks,
Alex

Hey guys, I was having this error msg as well.
I'm running Ubuntu 9.04 on a relatively new machine. Everything went smoothly until the third (3) command.
This is what prints in Terminal following the command in question.
[quote=Terminal]--------@----------laptop:~$ sudo apt-get install hotway hotsmtp
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package hotway
[/quote]This might seem like too simple a solution, but is there an online source code/file that could be accessed to come up with a workaround? I'm relatively new to Linux, so I don't know what all is possible/impossible with the language it runs in, but I think it might be possible to acquire a smooth-working version of the hotway package.

I'm thinking either 
[LIST]
[*]do it the long way and re-write it word for word (which seems rather daunting)
[*]**or**
[*]copy the package to the tmp directory and them move it into place once it is in the system
[/LIST]
 Of course, not knowing much about the computing power of the language is a little of a setback. I'd love to hear what anyone thinks of my ideas for workarounds.

---

### Post by RavanH on 2009-08-10
> **darkeale said:**
> hi,

when i try and do this line:-

sudo apt-get install hotway hotsmtp

i get the error "couldn't find package hotway"

any way around this?

thanks,
Alex

Did you know you do no longer need hotway for accessing hotmail? You can now use regular POP/SMTP access like normal mail accounts. Check out [http://en.wikipedia.org/wiki/Hotmail#POP3](http://en.wikipedia.org/wiki/Hotmail#POP3) for the settings.

---

### Post by prufrockthe3rd on 2009-08-12
> **RavanH said:**
> Did you know you do no longer need hotway for accessing hotmail? You can now use regular POP/SMTP access like normal mail accounts. Check out [http://en.wikipedia.org/wiki/Hotmail#POP3](http://en.wikipedia.org/wiki/Hotmail#POP3) for the settings.


Thanks for the info, incredibly useful.

---

### Post by jtpoole99 on 2009-08-21
Thanks, this worked perfectly for me.  I followed everything to the letter and I'm downloading my Hotmail messages...  Thanks again...

---

### Post by freddalind on 2009-09-04
Am i the only one having problem with hotmail in evo, thundebird kmail and so on??
I wont connect to the pop3 server i anyone!

Anyone have a clue?

thx Fred

---

### Post by ebozzz on 2009-09-04
> **freddalind said:**
> Am i the only one having problem with hotmail in evo, thundebird kmail and so on??
I wont connect to the pop3 server i anyone!

Anyone have a clue?

thx Fred

Can you provide more info about your settings? I have no problems with either client. Here's what I use....

**Receive Mail:** 
pop3.live.com (server)
Port 995
Select SSL under user secure connection. Do **NOT** check use secure authentication.
The user ID will be your entire email address.

**Send Mail:** 
smtp.live.com (server)
Port 25
Select TLS under user secure connection. Secure authentication **WILL** be selected for the outgoing server.
The user ID will be your entire email address.

Try those and if you are still having problems post more about exactlly what is happening. Good luck....

---

### Post by jgamio on 2009-09-04
Hi, It works for reciving but not to send, where do you change the port ?

---

### Post by ebozzz on 2009-09-04
> **jgamio said:**
> Hi, It works for reciving but not to send, where do you change the port ?

Please post more information. Which email client are you attempting to configure? What are the current settings? What error message are you getting?

---

### Post by jgamio on 2009-09-05
Sorry I use evolution I used the configuration you put  before but i didnt set the port , i recive email but i cant send

---

### Post by ebozzz on 2009-09-05
> **jgamio said:**
> Sorry I use evolution I used the configuration you put  before but i didnt set the port , i recive email but i cant send

I do not think that it is possible to change the port setting in Evolution. It works fine in mine. Here's a screen shot of how it should look....

---

### Post by ebozzz on 2009-09-05
> **jgamio said:**
> Sorry I use evolution I used the configuration you put  before but i didnt set the port , i recive email but i cant send

I do not think that it is possible to change the port setting in Evolution. It works fine in mine. Here's a screen shot of how it should look. Your settings should match the image but of course, you email address should be entered into the User Name field. If that does not work, it would help to know what the error message is that you are receiving....

---

### Post by jgamio on 2009-09-05
thank you for your time but I have the same like the picture, the pop works fine but when i send a mesagge i get a error of time out

---

### Post by fatjonny on 2009-09-06
Never thought i would find and be able to post the answer to a problem.

Seems you have to apply the same settings as suggested by ebozzz but also when the outbox folder is highlighted.

Does anyone have any idea why evolution failed to send and receive via hotmail. this problem became evident about a week ago

---

### Post by joe2580 on 2009-09-07
So I spend 20 mins trying to get it to work and when it finally does work I am greeted with "Downloading message 1 of 1072" :-?

But hey, thats not the point, it works\\:D/

---

### Post by jgamio on 2009-09-09
I solved my problem to send the email I was using smtp.live.com instead smtp.live.com:587

---

### Post by philinux on 2009-09-11
> **tentaro said:**
> This worked great but unfortunatley it doesn't download my Junk mail, not sure y but if anyone knows, please let me know. Sometimes important things come in my junk folder before I can add the to acceptable mail. Thanks

Just got the junk mail sorted as sometimes important stuff gets missed and I've got the junk filters going in Evo.

From here. [https://windowslivehelp.com/community/t/5739.aspx](https://windowslivehelp.com/community/t/5739.aspx)
> I'm sorry to inform you that there is no feature yet in Hotmail that'll allow you to turn off your Junk folder from receiving any messages, however, there's a work-around for this. I suggest that you set up a helpful custom filter by following these steps:

1.  Sign in to the Windows Live Hotmail website with your Windows Live ID.
2.  In the upper-right corner of the page, click Options, and then click More options.
3.  Under Customize your mail, click Automatically sort e-mail into folders.
4.  Click New filter.
5.  Under step 1, Select "From address" on the 1st drop-down, "contains" on the 2nd and then place "@" sign (without the "") on the blank field.
6.  Under Step 2, put a tick mark beside Inbox.
7.  Click on "Save.”

By having this custom filter, you'll receive all of your incoming messages in your Inbox due to the condition your custom filter applies, since all e-mail addresses have an "@" sign.

---

### Post by Kullervo on 2009-10-01
Hi! I used this to configure my hotmail account yesterday, and it worked great. But, for some reason, it does not work today. The problem is, that I can't press the send/recieve button! I have checked my hotmail account, and I've received several mails (there), and no one in Evolution. I have very little PC-knowledge, and I am new to both Ubuntu and Evolution, so I hope someone can help me. :)

---

### Post by kevinguillorytraining on 2009-10-10
Thanks for a nice tutorial

---

### Post by gamelord12 on 2009-10-19
So how do I make sure my junk folder in Hotmail transfers directly to my junk folder in Evolution?  In other words, I want my inbox and junk folders on the Hotmail server and on my computer (via Evolution) to be identical.

---

### Post by Rud91 on 2009-10-28
hi @ all

i tried to follow this tut and is written really good.
But i din't get the connection to 127.0.0.1

so i tested my own way:

- download hotwayd-0.8.4.tar.gz from sourceforge
- unpack and ./configure (at the end: hotwayd yes and hotsmtpd yes)
- make and make install with root
- hotsmtpd -> /usr/local/sbin/hotsmtpd
- hotwayd -> /usr/local/sbin/hotwayd
- then edit /etc/inetd.conf and add following lines:
> 
1100    stream    tcp    nowait    nobody    /usr/sbin/tcpd    /usr/local/sbin/hotwayd
2800    stream    tcp    nowait    nobody    /usr/sbin/tcpd    /usr/local/sbin/hotsmtpd

- after this i edit /etc/hosts.allow by adding this:
> 
hotsmtpd:127.0.0.1 2800
hotwayd:127.0.0.1 1100


at least i restarted inetdutilities like in the first post, with the message [OK]

now the problem is. why does evolution-mail doesn't find the daemons?
Error: connection refused.

what went wrong. please help me. i'm a noob and i want to delete windows on my Lifebook T1010.

additional info: i work with ubuntu 9.04


dirk

---

### Post by Merk42 on 2009-10-29
Anything different with these instructions in Evolution 2.28.1 that came with Karmic today?

---

### Post by Rud91 on 2009-10-30
I'don't think so.

i had much problems setting up hotwayd and hotsmtpd. after hours oft testing an viewing logfiles i change the xinetd settings so that it work on 9.04. but recieving emails allsow doesn't work well. i don't know why. 

the server returns allways -ERR send user first (or so ^^).

so i will say. this tut doesn't work for hotmail.de email. not with pop3.live.com and also not with hotwayd.

if their is some one how work with hotmail.de an hotwayd/pop3.live.com with ubuntu 9.04. plaese. say what should i do???

... when it doesn't work with 9.04 ... how should it work with 9.10?


dirk

---

### Post by Marrkk on 2009-10-31
hotmail pop3 works well in any mail client..

[http://www.ghacks.net/2009/03/14/hotmail-pop3-configuration/](http://www.ghacks.net/2009/03/14/hotmail-pop3-configuration/)

kmail is lovely
:)

---

### Post by Rud91 on 2009-10-31
ok.

my problem was the password. using only the first codepoint of Unicode, or only ASCII works.


Dirk

---

### Post by ~Niebr~ on 2009-11-04
hey guys, im having a problem with this, i was following the instructions, and got stopped here. 
```

niebr@niebr-desktop:~$ sudo apt-get install hotway hotsmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway

```

---

### Post by prawler on 2009-11-05
Hey - firstly I'd like to say big thanks for finding a way past the hotmail problem.

Secondly I'd get to my problem.

When entering the "code" to terminal

```
sudo apt-get install hotway hotsmtp
```


I get this error message

```
prawler@prawler-desktop:~$ sudo apt-get install hotway hotsmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway

```

Anything I'm doing wrong?

---

### Post by Hagen99 on 2009-11-14
Is this working in 2009 ?

---

### Post by jgamio on 2009-11-15
Why do you use hotway hotsmtp?

Now you can access your account without these files

---

### Post by dealcorn on 2009-11-20
It would be most helpful if this thread could be preceded by a highlighted comment saying:

This thread is obsolete and completely dysfunctional.  The thread is obsolete because Evolution now provides native support for Hotmail.  See [https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution) for what works today.  The reason the thread is completely dysfunctional is that it was a workaround and the superceded workaround package, hotway, has been removed from the repositories and a reader will fail if they try to follow the thread.  Due to the length of the thread it is possible to waste large amounts of time prior to the realization that you are in the wrong place so read on forewarned.

---

### Post by nush on 2009-11-27
> **dealcorn said:**
> It would be most helpful if this thread could be preceded by a highlighted comment saying:

This thread is obsolete and completely dysfunctional.  The thread is obsolete because Evolution now provides native support for Hotmail.  See [https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution) for what works today.  The reason the thread is completely dysfunctional is that it was a workaround and the superceded workaround package, hotway, has been removed from the repositories and a reader will fail if they try to follow the thread.  Due to the length of the thread it is possible to waste large amounts of time prior to the realization that you are in the wrong place so read on forewarned.

you are not wrong:mad:

---

### Post by ebozzz on 2009-11-27
> **dealcorn said:**
> It would be most helpful if this thread could be preceded by a highlighted comment saying:

This thread is obsolete and completely dysfunctional.  The thread is obsolete because Evolution now provides native support for Hotmail.  See [https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution) for what works today.  The reason the thread is completely dysfunctional is that it was a workaround and the superceded workaround package, hotway, has been removed from the repositories and a reader will fail if they try to follow the thread.  Due to the length of the thread it is possible to waste large amounts of time prior to the realization that you are in the wrong place so read on forewarned.


It may very well be obsolete at this time but I don't know if it was when this thread was created. As for me, I have always been able to use the settings that are supplied in the URL that you posted ([https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution)) with success....

---

### Post by bapoumba on 2009-11-27
Thread moved to the Outdated Tutorials.

---

### Post by gakon77 on 2009-12-02
> **dealcorn said:**
> It would be most helpful if this thread could be preceded by a highlighted comment saying:

This thread is obsolete and completely dysfunctional.  The thread is obsolete because Evolution now provides native support for Hotmail.  See [https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution) for what works today.  The reason the thread is completely dysfunctional is that it was a workaround and the superceded workaround package, hotway, has been removed from the repositories and a reader will fail if they try to follow the thread.  Due to the length of the thread it is possible to waste large amounts of time prior to the realization that you are in the wrong place so read on forewarned.


It works nice¡¡¡¡

---

### Post by greendodge50 on 2010-01-17
I got only as far as the third step, installing hotway.

here is the result of Step 3:

*STEP 3 - "This will install hotway...":*
root@greendodge50-laptop:/home/greendodge50# sudo apt-get install hotway hotsmtpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway

*STEP 4: Get this when i entered sudi gedit /etc/inetd.conf :*
#<off># sane-port	stream	tcp	nowait	saned:saned	/usr/sbin/saned saned

Any idea where I'm going wrong? I'm pretty new to all this. Thanks for taking time to read this.

---

### Post by t4thfavor on 2010-01-28
Or just use Gmail...

The method posted here works for me, I have had my account since 99-00 though.

[https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution)

---

### Post by BobLloyd on 2010-02-12
With Ubuntu 9.04 and Evolution 2.26.1 I found the following settings work with live.com emails.

Go to Edit/Preferences and edit your email account.

Identity tab
Full name - enter your email address [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]
Email address, ditto.

Receiving Email tab
Server Type: POP
Server: pop3.live.com
Security: SSL Encryption
Authentication type: Password and remember password.

Sending Email tab
Server Type: SMTP
Server: smtp.live.com
Tick the box Server requires authentication
Security: TLS encryption
Authentication: PLAIN
Username: [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]
Tick the box remember password.

Everything then seems to work fine.

---

### Post by perezomail on 2010-02-13
Not starting internet superserver: no services enabled.

E: Directory '/var/log/apt/' missing

is the message i get after trying the second step this /var/log/apt/ missing as been common as of late - running on easypeaze 1.5 

no other distro has given me this message other than this messege the netbook works out of the box fantastic

any ideas on how to correct this or should i just mkdir /var/log/apt 
and try again

---

### Post by Will.V.King on 2010-03-09
> **BobLloyd said:**
> With Ubuntu 9.04 and Evolution 2.26.1 I found the following settings work with live.com emails.

Go to Edit/Preferences and edit your email account.

Identity tab
Full name - enter your email address [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]
Email address, ditto.

Receiving Email tab
Server Type: POP
Server: pop3.live.com
Security: SSL Encryption
Authentication type: Password and remember password.

Sending Email tab
Server Type: SMTP
Server: smtp.live.com
Tick the box Server requires authentication
Security: TLS encryption
Authentication: PLAIN
Username: [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]
Tick the box remember password.

Everything then seems to work fine.

under Ubuntu 9.10 :popcorn: success-ed too~

---

### Post by barna10 on 2010-03-09
> **BobLloyd said:**
> With Ubuntu 9.04 and Evolution 2.26.1 I found the following settings work with live.com emails.
 
Go to Edit/Preferences and edit your email account.
 
Identity tab
Full name - enter your email address [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]
Email address, ditto.
 
Receiving Email tab
Server Type: POP
Server: pop3.live.com
Security: SSL Encryption
Authentication type: Password and remember password.
 
Sending Email tab
Server Type: SMTP
Server: smtp.live.com
Tick the box Server requires authentication
Security: TLS encryption
Authentication: PLAIN
Username: [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]
Tick the box remember password.
 
Everything then seems to work fine.
 
Worked great for me as well! Thanks

---

### Post by GhostyGu on 2010-03-20
> **BobLloyd said:**
> With Ubuntu 9.04 and Evolution 2.26.1 I found the following settings work with live.com emails.

Go to Edit/Preferences and edit your email account.

Identity tab
Full name - enter your email address [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]
Email address, ditto.

Receiving Email tab
Server Type: POP
Server: pop3.live.com
Security: SSL Encryption
Authentication type: Password and remember password.

Sending Email tab
Server Type: SMTP
Server: smtp.live.com
Tick the box Server requires authentication
Security: TLS encryption
Authentication: PLAIN
Username: [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]
Tick the box remember password.

Everything then seems to work fine.

Absolutely marvelous work! Thank-you most kindly!

---

### Post by WannabeFantasma on 2010-04-03
> **BobLloyd said:**
>  How to.

Thank you! it works :)

My sister was asking for it so now I can fix it for her!
Thanks alot!

But if i got to hotmail.com every mail is in the Deleted box? :D

---

### Post by daedalas1981 on 2010-04-11
Go to Edit/Preferences and edit your email account or (Shift + Ctrl + S)

Identity tab
Full name - enter your Full Name
Email address - enter your email address [email]xxxxxxx@live.com[/email]

Receiving Email tab
Server Type: POP
Server: pop3.live.com
Security: SSL Encryption
Authentication type: Password and remember password.

Sending Email tab
Server Type: SMTP
**Server: smtp.live.com:587**
Tick the box Server requires authentication
**Security: TLS encryption**
Authentication: PLAIN
Username: [email]xxxxxxx@live.com[/email]
Tick the box remember password.

Notice the port 587, it makes the difference with the TLS encryption.
Hope this helps everyone! :)

:guitar:

---

### Post by VRsuper6 on 2010-04-26
damn! this has pissed me off for the last time haha! 

every now and then when fetching mail it start fetching like 50 some-odd messages. All of which are already in my inbox. so then i have 'new/unread' messages, filed by date with everything else, all over my inbox. it just happened like 6 times these past two days!

anyone have a fix for that?

---

### Post by akand074 on 2010-05-01
> **daedalas1981 said:**
> Go to Edit/Preferences and edit your email account or (Shift + Ctrl + S)

Identity tab
Full name - enter your Full Name
Email address - enter your email address [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]

Receiving Email tab
Server Type: POP
Server: pop3.live.com
Security: SSL Encryption
Authentication type: Password and remember password.

Sending Email tab
Server Type: SMTP
**Server: smtp.live.com:587**
Tick the box Server requires authentication
**Security: TLS encryption**
Authentication: PLAIN
Username: [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]
Tick the box remember password.

Notice the port 587, it makes the difference with the TLS encryption.
Hope this helps everyone! :)

:guitar:

wow perfect, I've been playing around for an hour trying to find out how to input my password, putting the TLS/SSL encryption and port 587 and pressed Send/Receive and it prompted me for a password. Your the man!

---

### Post by hihihi100 on 2010-05-18
> **akand074 said:**
> wow perfect, I've been playing around for an hour trying to find out how to input my password, putting the TLS/SSL encryption and port 587 and pressed Send/Receive and it prompted me for a password. Your the man!

Hiya:

I have followed all the amentioned steps, including the port 587 step, but every time I try to send mail, I get:

```
Error while Sending message.

Could not connect to smtp.live.com: Connection timed out
```

Is this related to Evolution? Or is it a connection-net problem? I also have a memory leak problem, could that have triggered this window?

---

### Post by pricetech on 2010-05-20
> **WannabeFantasma said:**
> Thank you! it works :)

My sister was asking for it so now I can fix it for her!
Thanks alot!

But if i got to hotmail.com every mail is in the Deleted box? :D

I haven't confirmed this yet, but check the box on the Receiving Options tab to Leave Messages on Server.

---

### Post by pricetech on 2010-05-20
> **VRsuper6 said:**
> damn! this has pissed me off for the last time haha! 

every now and then when fetching mail it start fetching like 50 some-odd messages. All of which are already in my inbox. so then i have 'new/unread' messages, filed by date with everything else, all over my inbox. it just happened like 6 times these past two days!

anyone have a fix for that?

Do you check your hotmail with a browser as well ??  I had the same thing happen after I undeleted some messages that were deleted, though they shouldn't have been.

Try checking the box on the Receiving Options tab that says Leave Messages on Server.  See if that helps.

---

### Post by Matrix828 on 2010-05-28
didnt work for me, came up with an error message saying "Could not connect with 127.0.0.1: connection refused"
i followed all of the steps and it didnt work, why?
thanks
~Matrix828

---

### Post by Hunterounet on 2010-07-11
HI!

I have been trying to follow the tutorial written on the first page of this topic, but i have encounter this problem :
after entering the command "sudo apt-get install hotway hotsmtp" 
I get the following response : "E: Impossible de trouver le paquet hotway" (meaning "impossible to find the hotway package (i am french ^^))
What should I do ????? 

thanks for your help

---

### Post by leogibson on 2010-07-13
> **Hunterounet said:**
> (meaning "impossible to find the hotway package (i am french ^^))
What should I do ????? 

thanks for your help

I think this package, for whatever reason, is gone from the repository.  Perhaps Microsoft didn't appreciate it's existence.  It's sad, because I wanted to do this, too.

---

### Post by Jonypoo on 2010-08-30
umm when i typed the 
sudo apt-get install hotway hotsmtp
it says 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway

also, when i enter
sudo gedit/etc/inetd.conf, and the windows pops up, i cant find the "pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd"
pls help :)
oh wait i just saw the person above me post it... any solutions?

---

### Post by Toke on 2010-09-03
> **daedalas1981 said:**
> Go to Edit/Preferences and edit your email account or (Shift + Ctrl + S)

Identity tab
Full name - enter your Full Name
Email address - enter your email address [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]

Receiving Email tab
Server Type: POP
Server: pop3.live.com
Security: SSL Encryption
Authentication type: Password and remember password.

Sending Email tab
Server Type: SMTP
**Server: smtp.live.com:587**
Tick the box Server requires authentication
**Security: TLS encryption**
Authentication: PLAIN
Username: [EMAIL="xxxxxxx@live.com"]xxxxxxx@live.com[/EMAIL]
Tick the box remember password.

Notice the port 587, it makes the difference with the TLS encryption.
Hope this helps everyone! :)

:guitar:

Cool, this one worked for me.
Thanks.

---

### Post by Hal9002 on 2010-09-21
On the third one it says: nill@ubuntu:~$ sudo apt-get install hotway hotsmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway

Can you help me with this?

---

### Post by fouda on 2010-09-28
Hi, i was trying to follow your instructions but i can't get it to work, can you please help me out, i'm totally new to ubuntu

but when i entered the second line into the terminal: 
sudo apt-get install inetutils-inetd
i get the following: 

Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  inetutils-inetd
0 upgraded, 1 newly installed, 0 to remove and 68 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

notice the last two lines.
can you please help me out here, how can i fix this ?

---

### Post by Hal9002 on 2010-10-01
how do you get evolution to work with bell mail? it uses the same interface as hotmail. does anyone know how to do this?:confused:

---

### Post by geeky_chris on 2010-11-26
> **ubuntu01 said:**
> These settings work with no other configuration needed /required:

Incoming server: pop3.live.com
Username: your_username @hotmail.com
Use secure connection: SSL
Authentication type: password

Server: smtp.live.com
Use Secure Connection: TLS Encryption
Authentication Type: Login

This worked for me too!  :D:D:D:D

---

### Post by Dan.K on 2010-12-21
> **daedalas1981 said:**
> Go to Edit/Preferences and edit your email account or (Shift + Ctrl + S)

Identity tab
Full name - enter your Full Name
Email address - enter your email address [email]xxxxxxx@live.com[/email]

Receiving Email tab
Server Type: POP
Server: pop3.live.com
Security: SSL Encryption
Authentication type: Password and remember password.

Sending Email tab
Server Type: SMTP
**Server: smtp.live.com:587**
Tick the box Server requires authentication
**Security: TLS encryption**
Authentication: PLAIN
Username: [email]xxxxxxx@live.com[/email]
Tick the box remember password.

Notice the port 587, it makes the difference with the TLS encryption.
Hope this helps everyone! :)

:guitar:

Excellent.. adding port 587 to the server solved my sending problems.

Thanks

---

### Post by yax51 on 2011-01-13
ok, when I try to install hotway and hotsmtp I get an error saying packing not found.....and ideas?

---

### Post by H-Cim on 2011-02-04
> **daedalas1981 said:**
> Go to Edit/Preferences and edit your email account or (Shift + Ctrl + S)

Identity tab
Full name - enter your Full Name
Email address - enter your email address [email]xxxxxxx@live.com[/email]

Receiving Email tab
Server Type: POP
Server: pop3.live.com
Security: SSL Encryption
Authentication type: Password and remember password.

Sending Email tab
Server Type: SMTP
**Server: smtp.live.com:587**
Tick the box Server requires authentication
**Security: TLS encryption**
Authentication: PLAIN
Username: [email]xxxxxxx@live.com[/email]
Tick the box remember password.

Notice the port 587, it makes the difference with the TLS encryption.
Hope this helps everyone! :)

:guitar:


Works like a charm (For those who can't find "Plain", just use "Login" on SMTP). "Plain" was no longer an option to select with the lastest version of Evolution

---

### Post by sirozzy on 2011-02-05
Hi there guys,

I have stupid problem. ;) My evolution is downloading like 7 times the same messages. So i have normally 2000 email on my mailbox but now in evolution shows 10000 just because it downloaded it few times. Is it possible to fix this somehow? Thanks a lot anyway.

---

### Post by jezzyjez on 2011-02-18
Hi I've just started using 10.10 and i'm completely new to UNIX I'm having some problems with this HowTo. When I put the first step:

```
sudo apt-get update
```

into the terminal in runs through fine to 96%

then I get the message:

```
Media Change: Please insert the disc labelled
 'Lubuntu 10.10 _Maverick Meerkat_ - i386 (20101010)'
in the drive ‘/cdrom/’ and press enter
```

This is confusing to me as I have never used Lubuntu shouldn't the update work automatically?

Any help or explanation would be appreciated.

Jez

---

### Post by satrapes on 2011-10-10
Thanks excellent post even though i didn't read it all i found all necessary information and then some. I must say that in my case the only useful was that instead of plain username you need to insert [email]username@hotmail.com[/email] and it worked.

---

### Post by skag on 2011-10-19
I just did this: [http://pricklytech.wordpress.com/2010/05/01/ubuntu-10-4-lucid-configuring-evolution-to-connect-to-hotmail-windows-live-mail/](http://pricklytech.wordpress.com/2010/05/01/ubuntu-10-4-lucid-configuring-evolution-to-connect-to-hotmail-windows-live-mail/) and it worked...

---

