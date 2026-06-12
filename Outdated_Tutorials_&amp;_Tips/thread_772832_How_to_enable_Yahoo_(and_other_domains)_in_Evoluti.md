---
title: "How to enable Yahoo (and other domains) in Evolution Mail"
date: 2008-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by jeffimperial on 2008-04-28
A MUCH MORE DETAILED VERSION OF THIS POST IS AVAILABLE IN A THREE-PART HOWTO ON [MY BLOG]("http://openjeff.wordpress.com/2008/05/08/installing-yahoo-evolution-1/").

I've been looking around the forum, and on some Websites for a HOWTO enable pop3 access to my Free Yahoo! Email account. I remember being able to do this in Outlook on my Windows machine using [FreePops]("http://www.freepops.org/"), a general-usage program for the POP3 protocol.

For this tutorial, however, we're going to do the same thing using Evolution Mail through [YPops]("http://www.ypopsemail.com/"), another OSS that allows access to mail services through POP3 and SMTP.

Before anything else, let's be clear about some things.
[LIST]
[*]You are using Evolution Mail, the default Mail Client installed with Gutsy and Hardy. If you're on Thunderbird and are looking for config information, this might still help you. But I'm detailing this HOWTO for Evolution Mail people.
[*]You have Internet connection while doing the stuff that we're about to do. This is critical, as there are downloads to be done aside from testing your newfound Emailing glory when all is said and done.
[*]You have an existing Yahoo! Mail account, with its Username and Password ready at hand or in mind.
[*]Your firewall is not blocking any of the default POP and SMTP ports.
[*]Finally, you are aware that this may mean theft of service, and are using it for educational purposes ;)
[/LIST]

Now, on to business shall we...

First, we edit sources.list file (/etc/apt/sources.list). In a terminal, do ```
$sudo gedit /etc/apt/sources.list
```

Then, add the following line to your list (the bottomest line)
```
deb [http://tskariah.000webhost.com/ubuntu](http://tskariah.000webhost.com/ubuntu) ubuntu main
```

Now, save and exit the file.

We now add the Public PGP key for the repository we just put in.
```
$ wget [http://tskariah.000webhost.com/t_skariah.asc.gpg](http://tskariah.000webhost.com/t_skariah.asc.gpg)
```

```
$ sudo apt-key add t_skariah.asc.gpg
```

Now that we have access to the repo, we need to update the source list.
```
$ sudo apt-get update
```

Then we can install YPops.
```
$ sudo aptitude install ypops
```

Hopefully, you're still with me. You'd probably want to configure YPops now, and here's how:
```
$ sudo dpkg-reconfigure -fgnome ypops
```

A setup assistant or wizard should come up by now.
[IMG]http://www.testserver6.site88.net/howtoypops/1.png[/IMG]
Don't tick "Add a new account". Press Forward.

Now, you get Receiving Email options.

The default values should do for now. If you're using 3-degree domains, edit the last field as should (e.g. yahoo.com.uk, yahoo.com.hk, etc). Press Forward.

The Download Folders part is a feature of YPops that I really like. If, like me, you have filters working for you so that Emails that contain a certain keyword is delivered to a particular folder, than this one's a big help. Just type in the folders you want checked, with each folder separated by commas. After making the change/es you want, press Forward.


Now, the sending part. You are asked if you want to save Emails in the Sent Items folder. Leave this checked. Then Forward.
[IMG]http://www.testserver6.site88.net/howtoypops/5.png[/IMG]

The Session timeout setting defines how long Evolution is to wait before telling you that the request has timed out. If you're on dial-up, the default 1200 should do, but if you're not leave it as is.

Press Forward.

Proxies part. If you're connecting to the Internet via an HTTP proxy, tick the box. check the box. If not, leave it unchecked. Press Forward.


Define your proxy server settings by filling out the fields. Press Forward.
[IMG]http://www.testserver6.site88.net/howtoypops/8.png[/IMG]
If you don't know what to put in, ask the person who maintains your network.

Leave the Enable Proxy Authentication box unchecked. Press Forward.


Leave the present values unchanged. Again, check that your firewall/s is/are not blocking port 5110. Also, make sure that Enable SMTP is checked.

Then press Forward.

The SMTP port is what Evolution will be using when you send mails with your Yahoo! account. Leave 5025 as it is.

Once again, check your firewall/s allow/s this port. Press Forward.

Activity Log. Leave it checked, so that you may have something to go back to just in case.

Now press Forward


Leave these values as they are. But if you want more detailed logs, click the dropdown arrow and choose Advanced. Press Forward.

Finally, make sure that UIDL is enabled. And of course, you might want to automatically start YPOPs at startup. Press Forward.
[IMG]http://www.testserver6.site88.net/howtoypops/14.png[/IMG]


We now configure Evolution Mail.

First off, go to Edit > Preferences. Click Add to add your Yahoo! account.

Put in your name and Email address.
[IMG]http://www.testserver6.site88.net/howtoypops/16.png[/IMG]

Click the Receiving Email Tab. Key in the following:
[IMG]http://www.testserver6.site88.net/howtoypops/17.png[/IMG]
[LIST=1]
[*]Server Type = POP
[*]Server = localhost:5110 (If you remember, this is the default port that YPops set)
[*]Username = [email]user@yahoo.com[/email] (make sure you put in the @yahoo.com or @yahoo.com.uk part)
[*]Use Secure Connection = No encryption
[*]Authentication Type = Password (Tick on Remember password if you don't want to get a prompt for your password eveytime you try to get an Email)
[/LIST]

Click the Sending Email Tab. Key in the following:
[IMG]http://www.testserver6.site88.net/howtoypops/18.png[/IMG]
[LIST=1]
[*]Server Type = SMTP
[*]Server = 127.0.0.1:5025 (If you remember, these are the server and port we set up in YPops)
[*]Uncheck Server requires authentication
[*]Use secure encryption = No encryption
[/LIST]
Click on OK.

And you're done.

If you need to reconfigure YPops settings, or add another Email Yahoo! account, simply ```
$ sudo dpkg-reconfigure -fgnome ypops
``` to bring up the setup assistant/wizard again.

---

### Post by puifais on 2008-05-01
I have a really silly question.  After the step:

$ sudo aptitude install ypops

There's pop-up disclaimer window from ypops and I need to click ok at the bottom.  How do I click ok in terminal?  I tried clicking on the word <ok> in the disclaimer window, highlighting the whole thing and press enter, closing the window instead it'll just install the program, but nothing worked.  And this is just stupid cuz I know if this was in Windows, you just need to move the mouse over the OK button :(

---

### Post by jeffimperial on 2008-05-01
> There's pop-up disclaimer window from ypops and I need to click ok at the bottom.

It's not exactly a click that would execute the <Ok>.. Try using your down arrow button or the Page Down key until the <Ok> highlights red.

> a really silly questionNot Really. Others have had the same "problem".

---

### Post by Gripp on 2008-05-01
on apt-get update i get the following error

> W: Failed to fetch [http://tskariah.000webhost.com/ubuntu/dists/ubuntu/Release](http://tskariah.000webhost.com/ubuntu/dists/ubuntu/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

---

### Post by jeffimperial on 2008-05-01
I'm really not sure, but maybe that's because you're on a 64-bit machine. I'm trying to look around.

If I were you, I'd make sure everything in the HOWTO I posted were followed. Just to make sure there was no typo or anything. :)

---

### Post by Gripp on 2008-05-01
yeah, no typo.  i did some research and found that they just haven't compiled a 64bit version.  
i have no idea how to work from source so i guess i can continue to live without my yahoo account for the time being.  thanks though!  good tute :)

---

### Post by puifais on 2008-05-01
> **jeffimperial said:**
> It's not exactly a click that would execute the <Ok>.. Try using your down arrow button or the Page Down key until the <Ok> highlights red.

Not Really. Others have had the same "problem".
lol, that window has been on my screen for the last 2 days.  Everything works now.  Thank you.

---

### Post by jeffimperial on 2008-05-02
> **Gripp said:**
> yeah, no typo.  i did some research and found that they just haven't compiled a 64bit version.  
i have no idea how to work from source so i guess i can continue to live without my yahoo account for the time being.  thanks though!  good tute :)

Yeah, just figured that out myself too. Learning to compile would be one big plus for everyone of us here. As for myself I'm trying to learn it so that when I wanna try somethin' that's still in development, or just doesn't have a compiled version yet (debian package or whatever they call it lol) I'd be able to.

---

### Post by HossJF on 2008-05-04
Just to say Thank You for the instructions. Up and running in few minutes.

---

### Post by csat on 2008-05-04
Hi Jef

Thanks for this nice tutorial.  Here I am using Hardy Heron.  Evolution worked only the first time to send mail and refused after booting my system.  I've deleted all stuff and restarted again but no way to send any mail using 127.0.0.1:5025.  It just stops and keeps held at output queue.  I've checked if ypops was loaded and confirmed with ps -al.  So, I am puzzled so far.  Any ideas will be welcomed.
Csat

---

### Post by jeffimperial on 2008-05-05
> **csat said:**
> Hi Jef

Thanks for this nice tutorial.  Here I am using Hardy Heron.  Evolution worked only the first time to send mail and refused after booting my system.  I've deleted all stuff and restarted again but no way to send any mail using 127.0.0.1:5025.  It just stops and keeps held at output queue.  I've checked if ypops was loaded and confirmed with ps -al.  So, I am puzzled so far.  Any ideas will be welcomed.
Csat
Hi, csat!

I tried to duplicate the situation you're having, and found this out:

Under the Sending Email tab, in Security when "Use Secure Connection" option has "SSL Encryption" or "TLS Encryption" in it, sending hangs at the queue as you have described, and ultimately fails. Now, make sure that this option has "No encryption" in it.

If this doesn't solve it, just go ask again and I'll be happy to help out. :)

---

### Post by csat on 2008-05-05
> **jeffimperial said:**
> Hi, csat!

I tried to duplicate the situation you're having, and found this out:

Under the Sending Email tab, in Security when "Use Secure Connection" option has "SSL Encryption" or "TLS Encryption" in it, sending hangs at the queue as you have described, and ultimately fails. Now, make sure that this option has "No encryption" in it.

If this doesn't solve it, just go ask again and I'll be happy to help out. :)

Thank you Jeff!

Everything is up and running now.  Yesterday, right after posting my message, I examined /var/log/ypops and found csat.checkerror.html.  There was an warning saying Yahoo couldn't deliver my mail at that time (maybe a busy time) so I figured out that it was not my mail configurations.  Anyway, this morning, I've double checked SMTP setup and it was found accordingly with your recommendations.  I could get mail and reply, both using localhost and Ypops.

So, thank you again for your time and support.

Csat

---

### Post by S0VERE1GN on 2008-05-09
My recieve email action gets mad and tells me the host isnt any good, where do i  change that to make it work?

---

### Post by s_spiff on 2008-05-09
this doesn't seem to work for me. the apt-get update itself results in an error stating :
> 
W: Failed to fetch [http://tskariah.000webhost.com/ubuntu/dists/ubuntu/Release](http://tskariah.000webhost.com/ubuntu/dists/ubuntu/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

Am I the only one?
I'm on hardy amd64 bit.

---

### Post by jeffimperial on 2008-05-10
> **S0VERE1GN said:**
> My recieve email action gets mad and tells me the host isnt any good, where do i  change that to make it work?

Hello, SOVEREIGN

Make sure you have **127.0.0.1:5025** as your server under Server Configuration. It seems that one has to explicitly tell Evolution which port to use. Also, if this is already set as such, or the above does not work, you may have port 5025 closed by a firewall. Setting your firewall to allow this port open should make it work.

Similarly, Yahoo! cannot accept secure connections via Ypops, so make sure the Server Requires Authentication checkbox is **unchecked**, and that Use Secure Cinnection dropdown menu is set to **No Encryption**.

Please tell me if this doesn't work out for you. And as final note, there are particular moments when *Yahoo! seems to be very busy*. As CSAT (the user who posted another reply previous to yours) ***retrying at another hour*** worked out for her.

Jeff

---

### Post by jeffimperial on 2008-05-10
> **s_spiff said:**
> this doesn't seem to work for me. the apt-get update itself results in an error stating :

Am I the only one?
I'm on hardy amd64 bit.

>  Originally Posted by **Gripp**
yeah, no typo. i did some research and found that they just haven't compiled a 64bit version.
i have no idea how to work from source so i guess i can continue to live without my yahoo account for the time being. thanks though! good tute 

Sorry, spiff

It seems YPops hasn't made the package 64-bit ready yet. I'm looking into it if I could help you 64-bit guys with something to work it out with. For now, perhaps you could do a little research about compiling YPops yourself since the current package is for i386, 32 bit architectures only. YPops *is* Open Source Software, so their Website should have the tarballs and source code there.

Im really sorry if this has to be a little more difficult for you. And good luck!

Jeff

---

### Post by s_spiff on 2008-05-10
Nah, no issues. Will compile. Will try to make a deb and post it too in my next update.

---

### Post by jeffimperial on 2008-05-10
Well, that would be great! A 64-bit debian package of this would certainly please many.

---

### Post by Anthony0857 on 2008-05-18
I followed the directions exactly, but whenever I try to check my mail, it says Error while Fetching Mail. Could not connect to localhost: connection refused 

Any idea how to fix this?

---

### Post by jeffimperial on 2008-05-19
I also often get this error prompt. Usually, it's because the Yahoo! mail servers are too busy. Premium Account users have been complaining about this for quite some time now. What I do is just restart Evolution.

Anyways, please post again if a restart of Evolution, and a restart of your system, does not work. :)

---

### Post by fasoulas on 2008-05-27
> **jeffimperial said:**
> A MUCH MORE DETAILED VERSION OF THIS POST IS AVAILABLE IN A THREE-PART HOWTO ON [MY BLOG]("http://openjeff.wordpress.com/2008/05/08/installing-yahoo-evolution-1/").

I've been looking around the forum, and on some Websites for a HOWTO enable pop3 access to my Free Yahoo! Email account. I remember being able to do this in Outlook on my Windows machine using [FreePops]("http://www.freepops.org/"), a general-usage program for the POP3 protocol.

For this tutorial, however, we're going to do the same thing using Evolution Mail through [YPops]("http://www.ypopsemail.com/"), another OSS that allows access to mail services through POP3 and SMTP.

Before anything else, let's be clear about some things.
[LIST]
[*]You are using Evolution Mail, the default Mail Client installed with Gutsy and Hardy. If you're on Thunderbird and are looking for config information, this might still help you. But I'm detailing this HOWTO for Evolution Mail people.
[*]You have Internet connection while doing the stuff that we're about to do. This is critical, as there are downloads to be done aside from testing your newfound Emailing glory when all is said and done.
[*]You have an existing Yahoo! Mail account, with its Username and Password ready at hand or in mind.
[*]Your firewall is not blocking any of the default POP and SMTP ports.
[*]Finally, you are aware that this may mean theft of service, and are using it for educational purposes ;)
[/LIST]

Now, on to business shall we...

First, we edit sources.list file (/etc/apt/sources.list). In a terminal, do ```
$sudo gedit /etc/apt/sources.list
```

Then, add the following line to your list (the bottomest line)
```
deb [http://tskariah.000webhost.com/ubuntu](http://tskariah.000webhost.com/ubuntu) ubuntu main
```

Now, save and exit the file.

We now add the Public PGP key for the repository we just put in.
```
$ wget [http://tskariah.000webhost.com/t_skariah.asc.gpg](http://tskariah.000webhost.com/t_skariah.asc.gpg)
```

```
$ sudo apt-key add t_skariah.asc.gpg
```

Now that we have access to the repo, we need to update the source list.
```
$ sudo apt-get update
```

Then we can install YPops.
```
$ sudo aptitude install ypops
```

Hopefully, you're still with me. You'd probably want to configure YPops now, and here's how:
```
$ sudo dpkg-reconfigure -fgnome ypops
```

A setup assistant or wizard should come up by now.
[IMG]http://www.testserver6.site88.net/howtoypops/1.png[/IMG]
Don't tick "Add a new account". Press Forward.

Now, you get Receiving Email options.

The default values should do for now. If you're using 3-degree domains, edit the last field as should (e.g. yahoo.com.uk, yahoo.com.hk, etc). Press Forward.

The Download Folders part is a feature of YPops that I really like. If, like me, you have filters working for you so that Emails that contain a certain keyword is delivered to a particular folder, than this one's a big help. Just type in the folders you want checked, with each folder separated by commas. After making the change/es you want, press Forward.


Now, the sending part. You are asked if you want to save Emails in the Sent Items folder. Leave this checked. Then Forward.
[IMG]http://www.testserver6.site88.net/howtoypops/5.png[/IMG]

The Session timeout setting defines how long Evolution is to wait before telling you that the request has timed out. If you're on dial-up, the default 1200 should do, but if you're not leave it as is.

Press Forward.

Proxies part. If you're connecting to the Internet via an HTTP proxy, tick the box. check the box. If not, leave it unchecked. Press Forward.


Define your proxy server settings by filling out the fields. Press Forward.
[IMG]http://www.testserver6.site88.net/howtoypops/8.png[/IMG]
If you don't know what to put in, ask the person who maintains your network.

Leave the Enable Proxy Authentication box unchecked. Press Forward.


Leave the present values unchanged. Again, check that your firewall/s is/are not blocking port 5110. Also, make sure that Enable SMTP is checked.

Then press Forward.

The SMTP port is what Evolution will be using when you send mails with your Yahoo! account. Leave 5025 as it is.

Once again, check your firewall/s allow/s this port. Press Forward.

Activity Log. Leave it checked, so that you may have something to go back to just in case.

Now press Forward


Leave these values as they are. But if you want more detailed logs, click the dropdown arrow and choose Advanced. Press Forward.

Finally, make sure that UIDL is enabled. And of course, you might want to automatically start YPOPs at startup. Press Forward.
[IMG]http://www.testserver6.site88.net/howtoypops/14.png[/IMG]


We now configure Evolution Mail.

First off, go to Edit > Preferences. Click Add to add your Yahoo! account.

Put in your name and Email address.
[IMG]http://www.testserver6.site88.net/howtoypops/16.png[/IMG]

Click the Receiving Email Tab. Key in the following:
[IMG]http://www.testserver6.site88.net/howtoypops/17.png[/IMG]
[LIST=1]
[*]Server Type = POP
[*]Server = localhost:5110 (If you remember, this is the default port that YPops set)
[*]Username = [email]user@yahoo.com[/email] (make sure you put in the @yahoo.com or @yahoo.com.uk part)
[*]Use Secure Connection = No encryption
[*]Authentication Type = Password (Tick on Remember password if you don't want to get a prompt for your password eveytime you try to get an Email)
[/LIST]

Click the Sending Email Tab. Key in the following:
[IMG]http://www.testserver6.site88.net/howtoypops/18.png[/IMG]
[LIST=1]
[*]Server Type = SMTP
[*]Server = 127.0.0.1:5025 (If you remember, these are the server and port we set up in YPops)
[*]Uncheck Server requires authentication
[*]Use secure encryption = No encryption
[/LIST]
Click on OK.

And you're done.

If you need to reconfigure YPops settings, or add another Email Yahoo! account, simply ```
$ sudo dpkg-reconfigure -fgnome ypops
``` to bring up the setup assistant/wizard again.

Can i do that but using thunderbird???

---

### Post by jeffimperial on 2008-05-29
> **fasoulas said:**
> Can i do that but using thunderbird???
You definitely can. The config attributes are pretty much named similarly or resemble one another.

---

### Post by theedudenator on 2008-06-11
There seems to be an error in the website for the key.

pete@Ubuntu-Basement:~$ wget [http://tskariah.000webhost.com/t_skariah.asc.gpg](http://tskariah.000webhost.com/t_skariah.asc.gpg)
--17:47:54--  [http://tskariah.000webhost.com/t_skariah.asc.gpg](http://tskariah.000webhost.com/t_skariah.asc.gpg)
           => `t_skariah.asc.gpg'
Resolving tskariah.000webhost.com... 75.127.68.66
Connecting to tskariah.000webhost.com|75.127.68.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://error.000webhost.com/not_found.html](http://error.000webhost.com/not_found.html) [following]
--17:47:54--  [http://error.000webhost.com/not_found.html](http://error.000webhost.com/not_found.html)
           => `not_found.html'
Resolving error.000webhost.com... 64.22.110.162
Connecting to error.000webhost.com|64.22.110.162|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6,022 (5.9K) [text/html]

100%[====================================>] 6,022         --.--K/s

---

### Post by jeffimperial on 2008-06-12
> **theedudenator said:**
> There seems to be an error in the website for the key....
It seems that the Web source for the GPG key is down. Let me try to contact the developer/s of this project and ask for the new location, or perhaps I could put it up myself for you, as soon as I have time.

---

### Post by birdmun on 2008-07-18
[http://tskariah.net78.net/ubuntu](http://tskariah.net78.net/ubuntu)
The above is the new server address I found it in my searches. The old address had to be taken down because of a phishing scheme that someone ran on an address they set up on the 000webhost servers so all of the sites on that domain got blocked.
Now if I can just get passed the localhost: connection refused I will be cooking with gas. :)

---

### Post by tskariah on 2008-07-22
hi all,

I have also added ypops for the 64bit ubuntu in my repository. you could follow the same steps as for the 32bit version. (for more details: [http://www.geocities.com/t_skariah/ypops/]("http://www.geocities.com/t_skariah/ypops/"))

And thanks jeffimperial, for "promoting" my work.

---

### Post by mirhciulica on 2008-09-04
Cool tutorial! Thanks jeffimperial for this and tskariah for his work!

But, I hate when i have to say but :(, i can't get Evolution connected to yahoo.

Firstly, I found that if you have other name as host, for example ubuntu instead of localhost, it won't work even if you set the server: ubuntu:5110, and will give you this error: Host lookup failed: ubuntu: Name or service not known.

I changed my host name to localhost, I set it in the server address and i have this error: Could not connect to localhost: Connection refused.
I checked the firewall, the ports aren't blocked. Restarted the computer, waited several hours and the same error I have.

What I observed is that ypops is not running. Here is my terminal:
```
mirhciulica@localhost:~$ sudo /etc/init.d/ypops  force-reload
 * Restarting ypops daemon: ypops                                                not running                                                             [ OK ]
mirhciulica@localhost:~$ sudo /etc/init.d/ypops  start
 * Starting ypops daemon: ypops                                          [ OK ] 
mirhciulica@localhost:~$ sudo /etc/init.d/ypops  start
 * Starting ypops daemon: ypops                                          [ OK ] 
mirhciulica@localhost:~$ sudo /etc/init.d/ypops  restart
 * Restarting ypops daemon: ypops                                                not running                             
```

Do you know how to resolve it?
Thanks.

---

### Post by vinber on 2008-09-22
Same problems...

Up!:)

---

### Post by Infinite Indefinite on 2008-09-27
I have exactly the same problem as mirhciulica; any help would be greatly appreciated.

---

### Post by karnak on 2008-09-27
I`d preffer "get to the point" tutorials, lot of tutorials are full of blah blah`s and 1 line of what you need

---

### Post by mgangav on 2008-11-07
Does this tutorial still work? I heard recently yahoo change something that broke YPops functionality. Is this true. The most annoying thing is that you have to pay to have your email forwarded as well. Gosh darn it...

---

### Post by sir4taye on 2009-02-02
I can't get the sending on yahoo servers up and running. I think the 5025 server is no good? Here's a picture of the problem screen. Having the same issue with 32bit and 64bit after following the same instructions.

---

### Post by Infinite Indefinite on 2009-05-02
> **mirhciulica said:**
> 

What I observed is that ypops is not running. Here is my terminal:

```
mirhciulica@localhost:~$ sudo /etc/init.d/ypops  force-reload
 * Restarting ypops daemon: ypops                                                not running                                                             [ OK ]
mirhciulica@localhost:~$ sudo /etc/init.d/ypops  start
 * Starting ypops daemon: ypops                                          [ OK ] 
mirhciulica@localhost:~$ sudo /etc/init.d/ypops  start
 * Starting ypops daemon: ypops                                          [ OK ] 
mirhciulica@localhost:~$ sudo /etc/init.d/ypops  restart
 * Restarting ypops daemon: ypops                                                not running                             
```

Do you know how to resolve it?
Thanks.

I removed YPOPS

```
sudo apt-get purge ypops
```

Then I reinstalled it, using the instructions at [YPOPS! for Ubuntu]("http://www.geocities.com/t_skariah/ypops/")

It seems that YPOPS is operational now - but I haven't yet got Evolution to work fully with Yahoo.  After updating from Mail Classic to their new mail, I've managed to send an e-mail, but not to receive my Inbox.  So half the job is done.

---

### Post by Infinite Indefinite on 2009-05-20
After logging in via the browser, and then logging out, and then starting Evolution, I've been able to get two e-mails in my Inbox before Evolution provides me with an error message regarding the third and stops there.

Update:

I went to Edit > Preferences > Mail Preferences, and unchecked 'Do not format text contents in messages if the text size exceeds...' - and I find that I download more e-mails now.

Maybe that will help.

---

### Post by yuli_capone on 2009-05-21
I get this after I edit sources.list file :

yuli@yuli-laptop:~$ wget [http://tskariah.000webhost.com/t_skariah.asc.gpg](http://tskariah.000webhost.com/t_skariah.asc.gpg)
--2009-05-21 12:20:28--  [http://tskariah.000webhost.com/t_skariah.asc.gpg](http://tskariah.000webhost.com/t_skariah.asc.gpg)
Resolving tskariah.000webhost.com... 64.191.78.229
Connecting to tskariah.000webhost.com|64.191.78.229|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://error.000webhost.com/not_found.html](http://error.000webhost.com/not_found.html) [following]
--2009-05-21 12:20:32--  [http://error.000webhost.com/not_found.html](http://error.000webhost.com/not_found.html)
Resolving error.000webhost.com... 64.235.48.196
Connecting to error.000webhost.com|64.235.48.196|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 303 [text/html]
Saving to: `not_found.html'

100%[======================================>] 303         --.-K/s   in 0s      

2009-05-21 12:20:33 (14.2 MB/s) - `not_found.html' saved [303/303]

yuli@yuli-laptop:~$ sudo apt-key add t_skariah.asc.gpg
gpg: can't open `t_skariah.asc.gpg': No such file or directory

---

### Post by Infinite Indefinite on 2009-05-23
I've attached a text version of the file you're seeking.  (Just remove the .txt after downloading the file and it should be identical to the original.)

---

### Post by yuli_capone on 2009-05-23
Thanks,I will try in a few hours:D

What should i do with t_skariah.asc.gpg?
can you explain me step by step please?

---

### Post by tacantara on 2009-05-23
There appears to be a problem with the download source.  I keep getting this error when I attempt to get the program:
[I][B][COLOR=Red]
W: Failed to fetch [http://tskariah.net78.net/ubuntu/dists/ubuntu/main/binary-i386/Packages.bz2](http://tskariah.net78.net/ubuntu/dists/ubuntu/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)[/COLOR][/B][/I]

I rechecked my steps, and I can't seem to locate any input on my part that could be part of the problem.  Any ideas?

BTW, yuli_capone, I put the  t_skariah.asc.gpg file in my home folder.  That seemed to do the trick, as the terminal returned an OK when I ran the step to install it.  I hope that helps you.

---

### Post by yuli_capone on 2009-05-24
Thanks,but i get this in terminal:
yuli@yuli-laptop:~$ sudo apt-key add t_skariah.asc.gpg
OK
yuli@yuli-laptop:~$ sudo apt-get update
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty Release.gpg
Ign [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Ign [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty/universe Translation-en_US             
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Ign [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty Release                                
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates Release                        
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [197B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [11.7kB]                     
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]                         
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty/restricted Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                   
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates/main Packages                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) jaunty-updates/universe Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources                          
Get:5 [http://tskariah.000webhost.com](http://tskariah.000webhost.com) ubuntu Release.gpg [303B]                 
Get:6 [http://tskariah.000webhost.com](http://tskariah.000webhost.com) ubuntu/main Translation-en_US [303B]      
99% [6 Translation-en_US bzip2 0] [3 Release 11329/11.7kB 96%] [Connecting to tbzip2: (stdin) is not a bzip2 file.
Ign [http://tskariah.000webhost.com](http://tskariah.000webhost.com) ubuntu/main Translation-en_US               
Get:7 [http://tskariah.000webhost.com](http://tskariah.000webhost.com) ubuntu Release [303B]                     
Ign [http://tskariah.000webhost.com](http://tskariah.000webhost.com) ubuntu Release                              
Get:8 [http://tskariah.000webhost.com](http://tskariah.000webhost.com) ubuntu/main Packages [303B]               
98% [3 Release 11329/11.7kB 96%]                                    10.7kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://tskariah.000webhost.com](http://tskariah.000webhost.com) ubuntu/main Packages                        
  Sub-process bzip2 returned an error code (2)
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages [8677B]                
Get:10 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages [3731B]           
Fetched 25.2kB in 20s (1226B/s)                                                
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1281ADAE04F71C22
W: GPG error: [http://tskariah.000webhost.com](http://tskariah.000webhost.com) ubuntu Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://tskariah.000webhost.com/ubuntu/dists/ubuntu/main/binary-i386/Packages.bz2](http://tskariah.000webhost.com/ubuntu/dists/ubuntu/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
yuli@yuli-laptop:~$ sudo aptitude install ypops
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "ypops"
Couldn't find any package whose name or description matched "ypops"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

yuli@yuli-laptop:~$ sudo dpkg-reconfigure -fgnome ypops
Package `ypops' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: ypops is not installed
yuli@yuli-laptop:~$

---

### Post by cor2y on 2009-06-02
the repo/server seems to be gone.
Looks like ypops will have to be compiled from scratch

---

### Post by jeffimperial on 2009-06-26
@All

I've been gone for quite a while so I wasn't able to give this thread attention. [YPOPS! for Ubuntu]("http://www.geocities.com/t_skariah/ypops/") seems to be the most convenient resource at the moment.

Make sure you have the owner's [PGP public key]("http://tskariah.net78.net/t_skariah.asc.gpg") before downloading. But then again, the broken deb file link that was fixed on 21.10.2008 may have gone down more recently.

---

### Post by biloyp on 2009-11-28
I am using Thunderbird but this tutorial helped. When I try and retrieve emails, the Tbird status bar shows Downloading 1 of 25 messages (it can connect) but then I get an error msg saying the RETR command did not succeed. Mail server 127.0.0.1 responded: Message 1 cannot be downloaded. Hmmm not sure what to do.

---

### Post by jeffimperial on 2009-11-30
> **biloyp said:**
> I am using Thunderbird but this tutorial helped. When I try and retrieve emails, the Tbird status bar shows Downloading 1 of 25 messages (it can connect) but then I get an error msg saying the RETR command did not succeed. Mail server 127.0.0.1 responded: Message 1 cannot be downloaded. Hmmm not sure what to do.
I usually just try again. Y! servers sometimes takes too long to respond. You could either set RTO (request timeout) to a higher value - trial and error here - or keep trying until you get them messages.

---

### Post by gabak on 2009-12-08
it does nt work any more this site

deb [http://tskariah.000webhost.com/ubuntu](http://tskariah.000webhost.com/ubuntu) ubuntu main

---

### Post by gabak on 2009-12-08
does anyone know what is the right url?? deb [http://tskariah.000webhost.com/ubuntu](http://tskariah.000webhost.com/ubuntu) ubuntu main that one does nt work

---

