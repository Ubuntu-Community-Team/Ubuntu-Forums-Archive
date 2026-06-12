---
title: "Howto: Configure Pidgin for Google Talk"
date: 2007-05-08
forum: Outdated Tutorials &amp; Tips
---

### Post by FakeOutdoorsman on 2007-05-08
[size=4][color=#FF0000]Note:[/color][/size] This post is very out of date. See the official Google instructions on how to do this: [How do I configure Pidgin for Google Talk?]("http://www.google.com/support/talk/bin/answer.py?hl=en&answer=24073")

[Pidgin]("http://pidgin.im/"), formerly known as GAIM, can be configured to connect to [Google Talk]("http://www.google.com/talk/").

1) The first time you open Pidgin you will see the welcome window.

2) Click **Add**.

3)In the **Add Account** window, add the following:

**Protocol:** XMPP (This used to be "Jabber" in GAIM)
**Screen name:** your Google Talk screen name without @gmail.com
**Server:** gmail.com
**Password:** If you want Pidgin to log in automatically, enter your Google Talk password and check the Remember password box. The password is stored unencrypted on your computer under the **.purple** directory in your home folder, so you may not want Pidgin to remember your password for security reasons.  It should look like the first attached image below.

4) Click the Advanced tab and add the following:

**Connect server:** talk.google.com

It should look like the second attached image below.

5) Click Save and you're done.

---

### Post by chipwhisperer on 2007-05-10
Hi,

Thanks for the tutorial! However, I'm running Edgy and I get the error that 

[FONT="Courier New"]<username>/Home disconnected

Server requires TLS/SSL for login.  No TLS/SSL support found.
[/FONT]

Any idea what I can do? I tried to click the force SSL option but that did not seem to work. 

Thanks for any help!

---

### Post by FakeOutdoorsman on 2007-05-10
My guess is that the necessary ports are being blocked by your firewall, proxy, or router.

*In order to connect to Google Talk and start sending IMs, you'll need to enable TCP connections to talk.google.com on port 5222, or on port 443.* From [What ports does Google Talk require?]("http://www.google.com/support/talk/bin/answer.py?answer=27930")

You can test to see if you can connect to talk.google.com, port 5222 with the following command in a terminal:
```

telnet talk.google.com 5222

```

A successful connection will look like this:
```

telnet talk.google.com 5222
Trying 72.14.253.125...
Connected to talk.l.google.com.
Escape character is '^]'.
^Connection closed by foreign host.

```

---

### Post by Elrohir on 2007-05-11
> **chipwhisperer said:**
> Hi,

Thanks for the tutorial! However, I'm running Edgy and I get the error that 

[FONT=Courier New]<username>/Home disconnected

Server requires TLS/SSL for login.  No TLS/SSL support found.
[/FONT]

Any idea what I can do? I tried to click the force SSL option but that did not seem to work. 

Thanks for any help!
did you built Pidgin from source? in that case you need a SSL Library, I used Mozilla's SSL Library, libnspr-dev, libssl-dev, and libnss-dev... not sure why those three worked together, but they did... maybe just a combination of two of them or not sure... but those are the libs I installed when I compiled and worked... cheers!

PS: If you need help with the source compiling, PM me and I'll help you step by step...

---

### Post by morneHeru on 2007-05-11
Thanks FakeOutdoorsman, works great for me :)

---

### Post by Fylk on 2007-05-11
Hey, thanks. I was wondering why I wasn't seeing Jabber under the add accounts.

---

### Post by chipwhisperer on 2007-05-12
Hey everyone,

thanks for all of your suggestions! It looks like it was a combo of both FakeOutdoorsman's and Elrohir's sugesstions, but now it's working fine. Thanks all! I'm grateful for your help!

---

### Post by dnoble on 2007-05-17
If you're using Google Talk with a Google Apps domain, you'll need to do a couple things differently:

[INDENT][Configure Pidgin for a Google Apps domain]("http://softwaredave.blogspot.com/2007/05/configuring-pidgin-for-google-apps.html")[/INDENT]

---

### Post by macness on 2007-05-22
I upgraded from GAIM and all my user settings ported over from my old .gaim file so all my accounts were added automatically.

However, My Google Talk would continually get SSL Handshake failed. After a few hours the following worked for me.

[LIST=1]
[*]Delete the old Google Talk/Jabber account that gets ported over
[*]Recreate it using [Google's instructions]("http://www.google.com/support/talk/bin/answer.py?answer=24073") WORD FOR WORD
[*]go to the advanced tab (as mentioned before in this tread) and change the server to talk.google.com (not in Google's instructions)
[/LIST]

Happy Trails.  :D

---

### Post by kanna1620 on 2007-05-23
> **macness said:**
> I upgraded from GAIM and all my user settings ported over from my old .gaim file so all my accounts were added automatically.

However, My Google Talk would continually get SSL Handshake failed. After a few hours the following worked for me.

[LIST=1]
[*]Delete the old Google Talk/Jabber account that gets ported over
[*]Recreate it using [Google's instructions]("http://www.google.com/support/talk/bin/answer.py?answer=24073") WORD FOR WORD
[*]go to the advanced tab (as mentioned before in this tread) and change the server to talk.google.com (not in Google's instructions)
[/LIST]

Happy Trails.  :D
I did what you said with no luck. I got the following error.[B]
Read Error[/B]
What to do?

---

### Post by scape on 2007-05-24
Hi,
i'm having the same problem has chipwhisperer, 

Server requires TLS/SSL for login.  No TLS/SSL support found.

i followed Elrohir advice and installed libnspr-dev, libssl-dev, and libnss-dev. I also installed openssl and gnutls-dev, but it still doesn't work.

Any more ideas ?

 Thanks for the help

---

### Post by fornix on 2007-06-02
I get this SSL handshake error too very often. But sometimes gtalk account works. I have the same problem when i connect to gtalk via pidgin on XP too. So i guess it has nothin to do with ubuntu. But the gtalk client works fine on XP.

---

### Post by starlily on 2007-06-27
HOT TO FIX THE TLS ERROR FOR GOOGLE TALK IN PIDGIN!

In a couple of Really Easy Steps:

Since there is no Pidgin Package for Ubuntu yet, I assume you are already building from the source. 

do 'make clean' if you have already built it and you get the error. 

Open Synaptic Package Manager, search for and install 'libgnutls-dev'

When you run ./configure to build Pidgin, do './configure --enable-gnutls=yes', then look for 
SSL Library/Libraries......... : GnuTLS
when it finishes. 

do sudo make install (as normal) to finish. 

You're Welcome. 

Lily

---

### Post by toadtwo on 2007-07-02
Is there a way to send files from pidgin gtalk to people using the official gtalk client? What about the other way?

---

### Post by cooldudeny on 2007-08-15
i did the same setting on pidgin but i m still getting an error message 

and not been able to connect ?

---

### Post by FakeOutdoorsman on 2007-08-15
cooldudeny: What is the error message you get?

---

### Post by ElliottMarlow on 2007-08-17
> **starlily said:**
> HOT TO FIX THE TLS ERROR FOR GOOGLE TALK IN PIDGIN!

In a couple of Really Easy Steps:

Since there is no Pidgin Package for Ubuntu yet, I assume you are already building from the source. 

do 'make clean' if you have already built it and you get the error. 

Open Synaptic Package Manager, search for and install 'libgnutls-dev'

When you run ./configure to build Pidgin, do './configure --enable-gnutls=yes', then look for 
SSL Library/Libraries......... : GnuTLS
when it finishes. 

do sudo make install (as normal) to finish. 

You're Welcome. 

Lily

Worked like a charm! Thanks.

---

### Post by meowsus on 2007-10-18
> **Elrohir said:**
> you need a SSL Library, I used Mozilla's SSL Library, libnspr-dev, libssl-dev, and libnss-dev... 

You are truly a genius sir. Thank you!

---

### Post by Envirnux on 2007-10-26
Great suggestion for how to build the install.  Without that switch it wasn't working for me.  Thanks!

---

### Post by gabizu on 2007-10-30
hy! i have that little problem with the pigin proxy i set my proxy for apt(acquaire::.... in apt.conf) the apt is working, for the synaptic and is working too. but when i select in pidgin use GNOME proxy settings is not working! i tried all the combinations (http proxy ->all the settings) and is not working i don't know what to do! tell me pls if is a file that i must modify or write! tks a lot

---

### Post by brunoscunha on 2007-11-05
I think I have the same problem. I'm running gutsy from a fiesty upgrade. Trying to setup a googletalk account, and the message I get is "Not authorized". I'm runing pidgin 2.2.1 and going to upgrade it to 2.2.2
Some help please.

---

### Post by jspam on 2007-11-30
> **starlily said:**
> HOT TO FIX THE TLS ERROR FOR GOOGLE TALK IN PIDGIN!

In a couple of Really Easy Steps:

Since there is no Pidgin Package for Ubuntu yet, I assume you are already building from the source. 

do 'make clean' if you have already built it and you get the error. 

Open Synaptic Package Manager, search for and install 'libgnutls-dev'

When you run ./configure to build Pidgin, do './configure --enable-gnutls=yes', then look for 
SSL Library/Libraries......... : GnuTLS
when it finishes. 

do sudo make install (as normal) to finish. 

You're Welcome. 

Lily

This helped me a bunch. Thanks!

---

### Post by dunbrokin on 2008-05-23
The above all seems to refer to a previous version of Ubuntu so I am wondering if it is relevant to my problem. I am running 8.04 and cannot get the pidgin to work with Google talk...I have followed the set up instructions for Google Talk but I get

 [email]XXX@gmail.com[/email]/Home disabled
Not Authorised

I have tried re-enable and modify account...but still get the same message.

---

### Post by jrusso2 on 2008-05-23
> **dunbrokin said:**
> The above all seems to refer to a previous version of Ubuntu so I am wondering if it is relevant to my problem. I am running 8.04 and cannot get the pidgin to work with Google talk...I have followed the set up instructions for Google Talk but I get

 [email]XXX@gmail.com[/email]/Home disabled
Not Authorised

I have tried re-enable and modify account...but still get the same message.

Don't add the .gmail.com to your user name it adds it automagically so if you add it it will be [email]username@gmail.com.gmail.com[/email]

---

### Post by dunbrokin on 2008-05-23
> **jrusso2 said:**
> Don't add the .gmail.com to your user name it adds it automagically so if you add it it will be [email]username@gmail.com.gmail.com[/email]

Thanks, I got it to work...no that was not the problem...for some reason it only works with manual input of password and not automatic...

---

### Post by teledyn on 2008-05-23
I had this working just fine for a long time, but as of some recent upgrades, it has stopped connecting -- there were some recent changes to the openssl iirc, and I've also upgraded to Heron although I think this
was broken before then.

is there some sort of certificate that i need to refetch or regenerated?

---

### Post by Wheazel on 2008-06-05
> **dunbrokin said:**
> Thanks, I got it to work...no that was not the problem...for some reason it only works with manual input of password and not automatic...

Same problem here.

---

### Post by K.Mandla on 2008-06-12
Moved to Outdated Tutorials and Tips at the request of the OPer.

---

### Post by sriram.vr on 2008-11-10
Here is a workaround for having voice chat with google talk users.

[http://sriramblox.blogspot.com/2008/08/making-voice-call-to-google-contact.html](http://sriramblox.blogspot.com/2008/08/making-voice-call-to-google-contact.html)

[http://sriramblox.blogspot.com/2008/10/voice-chat-with-google-talk-user-using.html](http://sriramblox.blogspot.com/2008/10/voice-chat-with-google-talk-user-using.html)

I hope this helps.

---

### Post by juanbretti on 2009-01-11
> **dnoble said:**
> If you're using Google Talk with a Google Apps domain, you'll need to do a couple things differently:

[INDENT][Configure Pidgin for a Google Apps domain]("http://softwaredave.blogspot.com/2007/05/configuring-pidgin-for-google-apps.html")[/INDENT]
Thanks!

---

### Post by shantzg001 on 2009-03-22
There can be more issues with gtalk and pidgin, e.g., if you company blocks it. Here is a method to overcome this :P:
[http://tech.shantanugoel.com/2008/09/08/hack-pidgin-gtalk-connection-problems-get-around-the-corporate-firewall.html](http://tech.shantanugoel.com/2008/09/08/hack-pidgin-gtalk-connection-problems-get-around-the-corporate-firewall.html)

---

### Post by asaturn on 2009-07-07
there is a more official way of keeping Pidgin more up to date shown here:

[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

---

### Post by chiques on 2009-09-08
Excellent! Thanks

---

### Post by devilspirit on 2009-10-04
> **Elrohir said:**
> did you built Pidgin from source? in that case you need a SSL Library, I used Mozilla's SSL Library, libnspr-dev, libssl-dev, and libnss-dev... not sure why those three worked together, but they did... maybe just a combination of two of them or not sure... but those are the libs I installed when I compiled and worked... cheers!

PS: If you need help with the source compiling, PM me and I'll help you step by step...


i'm getting messge like

[EMAIL="username@gmail.com"]username@gmail.com[/EMAIL]/host disconnected
ssl connection failed.
i checked force old port(5223)ssl
port 433

even port 5222 doesnt work


i'm behind a proxy sever and the proxy settings work well vth the web browser. 

plz suggest some solution to this problem

---

### Post by devilspirit on 2009-10-05
> **FakeOutdoorsman said:**
> My guess is that the necessary ports are being blocked by your firewall, proxy, or router.

*In order to connect to Google Talk and start sending IMs, you'll need to enable TCP connections to talk.google.com on port 5222, or on port 443.* From [What ports does Google Talk require?]("http://www.google.com/support/talk/bin/answer.py?answer=27930")

You can test to see if you can connect to talk.google.com, port 5222 with the following command in a terminal:
```

telnet talk.google.com 5222

```A successful connection will look like this:
```

telnet talk.google.com 5222
Trying 72.14.253.125...
Connected to talk.l.google.com.
Escape character is '^]'.
^Connection closed by foreign host.

```


hi , i'm using pidgin on xubuntu.
the above settings work well and i got same result as u said. but the problem still persists 
it shows ssl connection failed . i'm behind a proxy network.  can u plz suggest some solution.

---

### Post by dipspesh on 2009-10-18
I had installed an earlier version on pidgin and made it to connect to the servers using the methods told here..but since it didn't support file sharing i upgraded to pidgin 2.6.1 and now i'm not able to connect to any of the servers(i.e yahoo and google )
these error messages are being displayed 
for google->(Unable to find alternative XMPP connection methods after failing to connect directly.)
for yahoo->Unable to connect: Error resolving scsa.msg.yahoo.com:
No address associated with hostname

please help resolving this error!!

---

### Post by kevdog on 2009-10-18
Honestly -- I don't think pidgin works with google talk anymore but I could be wrong.  I thought that capability was halted around Sept/Oct 2009.

---

### Post by stephanecharette on 2009-11-20
> **kevdog said:**
> I don't think pidgin works with google talk anymore but I could be wrong.

Still works for me.  I'm using 2.6.2 in Ubuntu 9.10.  I doubt the Pidgin team would let support lapse very long for one of the biggest networks of users.

Stéphane

---

### Post by skywalker_7421 on 2009-11-25
I ran gtalk on pidgin like this :

Step 1 : Checked which ports were open for me to connect to talk.google.com at console

[IMG]http://i50.tinypic.com/5wlfkh.png[/IMG]

As u see none worked, as i am behind a proxy.

Step 2: Installed latest pidgin available in my local repo (pidgin 2.5.5).

Step 3: Settings in account 

Select the account --> Modify Account 

Basic settings

[IMG]http://i45.tinypic.com/1zc1d2x.png[/IMG]

Advanced settings

[IMG]http://i50.tinypic.com/211j4t4.png[/IMG]

In addition, i played with Tools-->Preferences-->Network too. Well the final setting was following -

[IMG]http://i47.tinypic.com/243n5tk.png[/IMG]

...

---

### Post by Aruz on 2009-11-29
If you use google apps. Must be activated "Google Talk" on Google Apps.

---

### Post by andy_butcher on 2010-02-04
I tried various things mentioned above, including the installing the libssl libraries, and configuring my firewall but in the end I logged into google.com and saw that my username was shown with an @googlemail.com at the end (not gmail.com)

Once I changed that in Pidgin, it worked just fine.

---

### Post by Endolith on 2010-05-04
this has worked fine for me for years, but now one account disconnects and says "not authorized" while the other works fine.  empathy says authentication failed

---

### Post by Sutur on 2010-08-02
Thanks mate, heaps of guides skip the "talk.google.com" section. No WONDER is wasn't connecting before!

---

### Post by sandeepch on 2010-08-16
after configuration how can i make audio call.no tabs for audio and vidio call

---

### Post by sonicleung on 2010-09-02
just google it.a lot of password finder tools support IM.
like:[password recovery bundle]("http://www.********************")

---

### Post by robinpaschal on 2010-09-20
Thanks for help...

---

### Post by Nightcrawlers on 2011-08-10
Thanks for this info!  I switched to Ubuntu 10.10 and was wondering how to configure Pidgin!  Very helpful! May the Gnome Gods bless you lol

---

