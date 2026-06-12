---
title: "How To: Command-Line Email as Simply as Possible"
date: 2008-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by klenwell on 2008-05-03
**Update:** I'm adding additional instructions for installing nail on newer versions of Ubuntu.  You can use mailx as others have suggested later in the thread, but I like nail's -A option, which the instructions below depend on and for which I could not find an equivalent in mailx.  I've reposted a [complete 6-step guide]("http://www.klenwell.com/press/2009/03/ubuntu-email-with-nail/") on my blog.

I'm copying this from my blog where the markup may be a little neater.  I only wish it could be a little simpler.  Link at bottom.

[SIZE="4"]problem[/SIZE]
I want to send email using the command line on my laptop Ubuntu system. Mainly for cron jobs and automated backups. I want to be able to do so without having to set up a full-fledged MTA like sendmail or exim. And I want to be able to use either my ISP email account or a Gmail account.

Seemed simple enough and it probably is for people who do this type of thing for a living. Took me all night. So hopefully this will save someone else (perhaps me again) hours of unnecessary frustration in the future.

[SIZE="4"]solution[/SIZE]
First, look at this diagram from Wikipedia: [http://en.wikipedia.org/wiki/Email#Workings](http://en.wikipedia.org/wiki/Email#Workings). Without being able to find a simple step-by-step tutorial to guide me, the biggest problem I was having was sorting out what was my MUA, what was my MTA, and what if anything I needed to connect the two. Long story short, they are as follows:

MUA (the client): nail (you can also use mailx or mutt or what you will)
MTA (the mail server): your isp or gmail
MSA (smtp middle man): msmtp (a simple MTA that gets mail from your local MTA to your real MTA or mailhub)

[SIZE="4"]step-by-step[/SIZE]
For newer versions of Ubuntu (post-Gutsy), add Breezy archive to your repository
```
$ sudo gedit /etc/apt/sources.list
```

Add the following lines at the bottom of the file:
```
# breezy repositories (added to install nail)
# see http://old-releases.ubuntu.com/releases/ for more info
deb http://old-releases.ubuntu.com/ubuntu/ breezy universe
```

Update:
```
$ sudo apt-get update
```


Install the needed programs
```
$ sudo apt-get install msmtp
$ sudo apt-get install nail
```


Install Thawte certificate for Gmail
This is necessary (I think) for Gmail. Probably the most complicated step, though not too bad thanks to instructions [here]("http://laurentbois.com/2007/10/20/activemailer-using-msmtp-and-gmail/"):
```
$ mkdir -p ~/etc/.certs
$ chmod 0700 ~/etc/.certs
$ cd ~/etc/.certs
$ wget https://www.verisign.com/support/thawte-roots.zip --no-check-certificate
$ unzip thawte-roots.zip
$ cp Thawte\ Server\ Roots/ThawtePremiumServerCA_b64.txt ThawtePremiumServerCA.crt
```


Configure msmtp
Replace UPPERCASE text with your personal settings
```
$ gedit ~/.msmtprc
```

This will open up an msmtp configuration file where you'll want to copy the following lines, with your correct settings, of course:
```
# config options: http://msmtp.sourceforge.net/doc/msmtp.html#A-user-configuration-file
defaults
logfile /tmp/msmtp.log


# isp account
account isp
auth login
host SMTP.YOURISP.COM
port 25
user YOURNAME@ISP.COM
from YOURNAME@ISP.COM
password *****


# gmail account
account gmail
auth on
host smtp.gmail.com
port 587
user YOURNAME@gmail.com
password *****
from YOURNAME@gmail.com
tls on
tls_trust_file /home/USER/etc/.certs/ThawtePremiumServerCA.crt


# set default account to use (from above)
account default : isp

```

Change permission on this file or msmtp will complain:
```
$ chmod 600 ~/.msmtprc
```

Configure nail
```
$ gedit ~/.mailrc
```

```
# set smtp for nail
# ref: [http://ubuntuforums.org/showpost.php?p=4531994&postcount=6](http://ubuntuforums.org/showpost.php?p=4531994&postcount=6)
# docs: [http://msmtp.sourceforge.net/doc/msmtp.html#Configuration-files](http://msmtp.sourceforge.net/doc/msmtp.html#Configuration-files)

# isp account (default)
# $ nail -s "subject line" -a /path/file [email]recipient@email.com[/email] < /path/body.txt
set from="YOURNAME@ISP.COM"
set sendmail="/usr/bin/msmtp"
set message-sendmail-extra-arguments="-a isp"

# gmail account
# $ nail -A gmail -s "subject line" -a /path/file [email]recipient@email.com[/email] < /path/body.txt
account gmail {
set from="YOURNAME@gmail.com (YOURNAME)"
set sendmail="/usr/bin/msmtp"
set message-sendmail-extra-arguments="-a gmail"
}
```


Send test messages for both accounts
```
$ echo -e "testing email from the command line" > /tmp/test_email
$ nail -s "isp test" YOURNAME@gmail.com < /tmp/test_email
$ nail -A gmail -s "gmail test" YOURNAME@gmail.com < /tmp/test_email
```


Check your gmail account and you should have two new messages -- one from that account and one from your ISP account. To check your log:
```
$ gedit /tmp/msmtp.log
```

Hope this helps someone.  I know I could have used it!
Original source: [http://phosphorusandlime.blogspot.com/2008/05/ubuntu-command-line-email.html](http://phosphorusandlime.blogspot.com/2008/05/ubuntu-command-line-email.html)

---

### Post by andrew.46 on 2008-05-03
Hi,

Great guide!!

Have you considered in your own setup using mutt rather than nail? There are many guides to using this more fully featured program but in blatant self-promotion I post my own here:

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)
[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

The second link uses msmtp as you have in your guide, a great program for sure. Anyway thanks for making the effort to put this together, nail has always been a bit of a mystery to me and it is good to see a working config.

            Andrew

---

### Post by klenwell on 2008-05-04
> **andrew.46 said:**
> Great guide!!

Have you considered in your own setup using mutt rather than nail? There are many guides to using this more fully featured program but in blatant self-promotion I post my own here:

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)
[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)


Thanks, Andrew.  At one point in my many false starts, I installed mutt and even came across your guide (which is very well done).  Mutt is just a little more than I needed in this case.

> I have formerly been an advocate for the simple MTA ssmtp, which some would call a Mail Sending Agent (MSA).

Ha!  Just the term I was looking for!  I knew it must have its own TLA.

Tom

---

### Post by hazica on 2008-05-04
Thanks for this simple and straightforward tutorial mate. I have been looking for something like this for a long time. 

There is, however, one addendum I'd like to make for all the Hardy users out there. It appears that nail is now known as heirloom-mailx in Hardy. Don't fret, though, because it can still be found in the Hardy repositories; just install heirloom-mailx instead of nail:
Replace 
```
sudo apt-get install nail
```
with
```
sudo apt-get install heirloom-mailx
```

Also, when you test the mail sending function, you have to replace 
```
nail -A gmail -s "gmail test" USERNAME@gmail.com < /tmp/test_email 
```
with
```
mailx -A gmail -s "gmail test" USERNAME@gmail.com < /tmp/test_email 
```

Keep up the good work mate, even if it means you have to sacrifice other Friday nights. I know that puking your guts out in some dark alley can be quite entertaining, but the community comes first, right? :D

---

### Post by HJB on 2008-05-05
Tnx, but I cant find a way to use mailx to send files as attachments to gmail?
If tried piping through uuencode and mpack but no go.
Any help please
Im using kubuntu 8.04 kde 4

---

### Post by klenwell on 2008-05-06
> **HJB said:**
> Tnx, but I cant find a way to use mailx to send files as attachments to gmail?
If tried piping through uuencode and mpack but no go.
Any help please
Im using kubuntu 8.04 kde 4

As a proof of concept, the following worked in nail:

```
nail -s "isp test" -a /tmp/test_email klenwell@gmail.com < /tmp/test_email
```

Google puts some restrictions on the type of files it will deliver so try with a simple case first.  Also note that this guide is for nail (mailx-heirloom), so you may need to adjust your config file for mailx.  

I'm not much help on the subject beyond this, but I imagine more details would help anyone who wished to assist.

---

### Post by mwgrient on 2008-05-19
Thank you klenwell for sharing this info with us. And thanks all for commenting it.
Saves me a lot of time and having fun with my commandline...

---

### Post by John Little on 2008-07-17
> **hazica said:**
> 
There is, however, one addendum I'd like to make for all the Hardy users out there. It appears that nail is now known as heirloom-mailx in Hardy. Don't fret, though, because it can still be found in the Hardy repositories; just install heirloom-mailx instead of nail:
Replace 
```
sudo apt-get install nail
```
with
```
sudo apt-get install heirloom-mailx
```


Thanks, hazica, but my Hardy doesn't see heirloom-mailx, and my mailx doesn't have a -A option, and doesn't understand the mutiple account stuff in the given .mailrc.  I wonder if I'm missing a repository that you've used?

---

### Post by stinger30au on 2008-07-17
> **klenwell said:**
> I'm copying this from my blog where the markup may be a little neater.  I only wish it could be a little simpler.  Link at bottom.
Hope this helps someone.  I know I could have used it!




thanks for the info!!!!

---

### Post by r.stiltskin on 2008-07-25
I can't find heirloom-mailx either.   Anybody know where to find it?

---

### Post by andrew.46 on 2008-07-31
Hi,

Can you confirm that gmail has changed to the Equifax Secure CA now after the problem of the expired cert?

         Andrew

---

### Post by DFord425 on 2008-10-22
> **r.stiltskin said:**
> I can't find heirloom-mailx either.   Anybody know where to find it?

I recently found this and i am trying to do the same thing. I cannot find heirloom-mailx or nail. I tried to use the apt-get install command for both. Also i am trying to modify the msmtrpc file but i cant find it. Does anyone know where i find it.

---

### Post by r.stiltskin on 2008-10-22
> **DFord425 said:**
>  I cannot find heirloom-mailx or nail. I tried to use the apt-get install command for both. Also i am trying to modify the msmtrpc file but i cant find it. Does anyone know where i find it.

You don't need heirloom-mailx or nail.  It turned out that mailx (included in the Ubuntu distro) works fine.  As for msmtprc -- you create it.   

If you need more info:

-------------------------------------------------------------------------
USING MAIL + MSMTP TO SEND EMAILS FROM A TERMINAL PROMPT OR FROM A SCRIPT:
-------------------------------------------------------------------------
mail (/usr/bin/mail) is provided by mailx or smail (smail requires mailx and uucp), and msmtp provides the interface to the isp that forwards the mail. So:
~$ sudo apt-get install msmtp smail uucp
(mailx will be installed as a dependency)

In your home directory, create a ~/.mailrc file containing just:
```
set sendmail=/usr/bin/msmtp

```

Create a config file for msmtp; mine is ~/.msmtprc but I think a systemwide /etc/msmtprc file would work as well.  For my Verizon account this file consists of:
```
# .msmtprc    ##configuration file for msmtp

#account    verizon
host        outgoing.verizon.net
from        [from address to appear on the email]
auth        login
tls         off
user        [username]@verizon.net
password    [************]

#account default : verizon

```
notes:
- The lines "account   verizon" and "account default : verizon" are commented out -- they seem to be unnecessary if only 1 account is listed in the file.
- The [from address ...] can be whatever you want to appear on the email; it does not have to be your isp account address.
- The line "auth    login" is to be copied exactly.  This "login" is NOT your username.
- You'll have to determine the appropriate entries for the host, auth, and tls lines, depending on your isp.


To send an email manually from a terminal prompt, type a first line consisting of the command, the subject and one or more recipient addresses (no commas):```
~$ mail -s "the subject line" [first recipient] [second recipient] [...]
```followed by <enter>.
Then type the body of the message.  This can be on multiple lines (<enter> will not terminate the message).
Finally, to terminate the message, type <enter> at the end of the last message line, and then type ctrl-D at the beginning of the next line.

To send an email from, say, a perl script, include a line similar to this in the script:
```
system("echo \"Body of the message\" | mail -s \"Subject line\" recipient1@address1 recipient2@address2");
```

---

### Post by mhourahine on 2008-11-16
Thanks for this info and for the helpful comments afterwards.  This saved me alot of time.

heirloom-mailx seems to be just called mailx now

```
sudo apt-get install mailx
```

should do the trick

---

### Post by mitchhb on 2009-04-03
Thank you for the detailed directions. I think I have followed them carefully and have installed mailx and mstmp. 

But when I try to send mail, I get the error message "msmtp: no recipients given". Any suggestions about what mistake I might have made? Thanks for any help.

---

### Post by r.stiltskin on 2009-04-04
I don't know -- I can't find any way to produce that error message.

---

### Post by mitchhb on 2009-04-04
Update: I was able to send mail using msmtp directly but see the error message when trying to send using mailx. So there is some issue between mails and msmtp.

---

### Post by mitchhb on 2009-04-04
Resolved: I had been using mailx from the mailutils package. After I installed it from mailx, everything works.

---

### Post by djmm on 2009-05-12
Fantastic.  Just what I've been looking for.  Thanks for documenting this. This is something that should definitely be incorporated into the distro too - simple out of the box smtp at least.

While these instructions work great for $USER, is anyone using a modified set for a system-wide solution or is that not possible given that, say, using gmail requires specific user settings? 

I'm asking because I only have 3 users on the machine and then root.  I could set this up for the other 3 users and root as well, but wondering if there's any configuration that can be shared and what the system-level file equivalents are.

---

### Post by r.stiltskin on 2009-05-12
I haven't tried it but I believe you can replace the ~/.mailrc with /etc/mail.rc and replace ~/.msmtprc with /etc/msmtprc and that should work system-wide if all users share the same isp settings.

---

### Post by boris464 on 2009-05-31
Great stuff! 

At least for the gmail account the fumbling with the certificates can be avoided with

```
sudo apt-get install ca-certificates
```

and changing the trust file in the .mstmp file to:

```
tls_trust_file /etc/ssl/certs/Thawte_Premium_Server_CA.pem
```

---

### Post by JohnJBBrown on 2009-05-31
Hi 

I have a small file server at home running Ubuntu 8.04 and I set up SMART hard disk monitoring following the instructions at:
[http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/](http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/)

I followed this how-to to set up mail using mailx and msmtp so that the server can send me automatically SMART warnings to an address at an ISP, however I cannot resolve the following problem:

If I own the /home/USER/.msmtprc file, I can send email from the command line, but the smartd daemon cannot and in /var/log/daemon there is the following message: /etc/smartmontools/run.d/10mail: send-mail: /home/USER/.msmtprc: must be owned by you Can't send mail: sendmail process failed  

And the other way round: if I chown the /home/USER/.msmtprc to root, the daemon can send the mail, but I can't. 

Any idea what I do wrong?

Thanks.

---

### Post by dcstar on 2009-06-03
> **JohnJBBrown said:**
> Hi 

I have a small file server at home running Ubuntu 8.04 and I set up SMART hard disk monitoring following the instructions at:
[http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/](http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/)

I followed this how-to to set up mail using mailx and msmtp so that the server can send me automatically SMART warnings to an address at an ISP, however I cannot resolve the following problem:
.........

I do not know why people just don't install the **postfix** package, it requires virtually no configuration for immediately sending outgoing mail and it just works (just select "Internet" on install or run this later):

```
dpkg-reconfigure postfix
```

The only manual thing I have to do is set the mail forwarder to my ISP (a trivial task) because I get allocated dynamic IP addresses that are on Spam lists so some mail is blocked if sent directly from my connection.

---

### Post by zouhair on 2009-09-04
Can't seem to find ThawtePremiumServerCA_b64.txt in the downloaded zip file, you can find it [here]("http://www.cs.utexas.edu/~suriya/UT-wireless/ThawtePremiumServerCA_b64.txt").

Thanks for this tutorial, very much appreciated.

zouhair

---

### Post by jdmonroe on 2010-06-03
Looks like the Thwart certs are no longer working.

Made the following changes:

renamed all mail servers to googlemail.com

Also downloaded the following cert file
[https://www.geotrust.com/resources/root_certificates/certificates/Equifax_Secure_Certificate_Authority.cer](https://www.geotrust.com/resources/root_certificates/certificates/Equifax_Secure_Certificate_Authority.cer)


Renamed it to
EquifaxSecureCertificateAuthority.crt

Command line to send the mail has changed also.  "mailx" instead of "nail"

Success!

---

### Post by charliehubuntu on 2011-09-01
send-mail: account default not found: no configuration file available

---

