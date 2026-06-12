---
title: "HowTo: Configure DenyHosts to Send Emails to a Gmail Account"
date: 2011-03-16
forum: Outdated Tutorials &amp; Tips
---

### Post by matt.garriott on 2011-03-16
I noticed that there doesn't seem to be much information about this particular topic, and as I struggled with it myself I thought I would provide a guide to help others that may have had the same problems. I have only tested this on Ubuntu Desktop 10.10.

Firstly you need to install denyhosts
```

sudo apt-get install denyhosts

```

In order to for the email program to generate messages that are formatted correctly we need to modify a line in the denyhosts.conf file.
```

sudo gedit /etc/denyhosts.conf

```

Find this line it should be around line number 221
```

ADMIN_EMAIL = 

```
and add your email address:
```

ADMIN_EMAIL = [email]username@gmail.com[/email]

```
Save changes and close the file.

**Note:** You should go through this file and familiarize yourself with all the other options you can customize in the denyhosts.conf file, but that is beyond the scope of this tutorial.

Now you need to install PostFix
```

sudo apt-get install postfix

```

Mark Sanborn provided an excellent guide for setting up PostFix to work with gmail, and instead of reinvinting the wheel I'll just link to his page for the next several steps. Although this says for Ubuntu server I have tested it and it works great on Ubuntu Desktop as well.

[[COLOR="Blue"]http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/[/COLOR]]("http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/")

I will note that I needed to follow one suggestion from the comments on Mark's site posted by George SHafer before my postfix was completely working.

You need to edit /etc/postfix/main.cf by adding
[smtp.gmail.com]:587 to relayhost and adding this line:
```

transport_maps = hash:/etc/postfix/transport

```
The file should look like this:
```

**transport_maps = hash:/etc/postfix/transport**
myhostname = <your-hostname-here>
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = <destination-names-here> #my entry is simply mydestination = matt.garriott
**relayhost = [smtp.gmail.com]:587**
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
inet_protocols = all
## TLS Settings

```

Now you should be able to send emails using sendmail to your Gmail account!

After postfix has been configured and is working, you need to edit the python script used by denyhosts to send emails.

Thanks to Lars Noodén from this thread [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1288862[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1288862") for pointing out which script had the mail commands.

First lets make a backup of the original script:
```

cd /usr/share/denyhosts/Denyhosts
sudo cp util.py util.py.bak

```

Now we need to edit the script to tell it to use sendmail to send the email instead of the python smtplib. [[COLOR="Blue"]http://docs.python.org/library/smtplib.html[/COLOR]]("http://docs.python.org/library/smtplib.html")

The easiest way to explain the next part is just to provide you with the modified python script. (If you are interested in what I changed just open the old script, and compare it to this new one. Most all the changes are near the bottom of the file.)

Go ahead and stop the denyhost service:
```

sudo service denyhosts stop

```

Download the util.py script (attached to the post), open it up using a text editor, and insert your email address so the line that should be edited looks like this:
```

EMAIL_ADDRESS = "your-user-name@gmail.com"

```
Then move the new python script and replace the old one (you should still be in the /usr/share/denyhosts/Denyhosts directory):
```

sudo mv /downloaded-directory/util.py .

```

Start the denyhost service again:
```

sudo service denyhosts start

```

You should be done! Go ahead and test it.
I tested mine by sshing into my box and purposely mistyping my password several times, until it added the IP to the /etc/hosts.deny file.

You can then re-allow your IP by editing the /etc/hosts.deny file and removing your IP address. Also in order to keep your IP from being re-denied instantly you need to remove the IP address from /var/lib/denyhosts/hosts-restricted as well.

Hope this helps anyone who was struggling with this!

-Matt

---

### Post by masticazzi on 2011-04-11
Far too complicated! Please see my answer:
[http://ubuntuforums.org/showpost.php?p=10615847&postcount=11](http://ubuntuforums.org/showpost.php?p=10615847&postcount=11)

Ciao
Alessandro

---

### Post by matt.garriott on 2011-04-12
I checked your post and you were right masticazzi. I was able to receive denyhosts messages using stunnel4. I did need to comment out the cert line(6) to:
```

;cert = /etc/ssl/certs/stunnel.pem

```
 in the /etc/stunnel/stunnel.conf file in order to get the service to start. After that though everything is up and running, thanks for the tip!

---

### Post by matt.garriott on 2011-04-12
I should also mention that to get the stunnel method working you will need to modify /etc/default/stunnel4 and change the line:
```

ENABLED=0

```
to:
```

ENABLED=1

```

---

