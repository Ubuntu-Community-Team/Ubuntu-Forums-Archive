---
title: "Get a shell script to send an email with attachment?"
date: 2009-09-30
forum: Programming Talk
---

### Post by viper474 on 2009-09-30
The reason I'm asking is because I am away from home, and the internet connection is dynamic (at home).  For when I would like to ssh or remote desktop to this computer I need the public ip.  I would rather dismiss the idea of using a no-ip service.  I would also rather not call and have to ask "What's the ip today?"  I have already figured out how to run a program using Evolution mail app on the recipient end.  The program (a shell script) I get to run can get the public ip and store it in a file, but the problem is sending that file to my email.  I have run into the mutt program, but do I really have to set up a mail server?  Would user interaction be required?  Is there any easier solution?  If I'm in the wrong forum, please move me.:confused:

---

### Post by viper474 on 2009-09-30
If you're actually reading this then...it's become a little easier in a sense that I have been able to figure out how to open up a new mail message through evolution with the correct attachment.  Now all I have to do is figure out how to send it automatically.

---

### Post by lavinog on 2009-09-30
What do you mean by automatically?

Do you just need to click the send button automatically?  if so you may be able to use xte to control the mouse.

I am not fully understanding the goal.
Is the process triggered by sending an email to the home computer with a shell script attachment, then the home computer executes the script which is supposed to send another attachment back to you?

Edit:  Are you wanting to have the home computer just email the public ip address? If so, why does it need to be an attachment?

---

### Post by lavinog on 2009-09-30
here is a python script that can be used to send a message.
fill in the appropriate variable information.

send a message like this:
python program.py "the ip address is 123.123.123.123"

```

#!/usr/bin/env python
import smtplib, sys

SERVER = 'smtp.mailserver.com'

smtpuser='user@mailserver.com'
smtppass='password'


FROM = "user@mailserver.com"
TO = ["user@otherserver.com"] # must be a list


SUBJECT = "Subject txt"

TEXT = sys.argv[1]



# Prepare actual message
message = """\
From: %s
To: %s
Subject: %s

%s
""" % (FROM, ", ".join(TO), SUBJECT, TEXT)

# Send the mail
session = smtplib.SMTP(SERVER)
session.starttls
session.login(smtpuser,smtppass)

smtpresult=session.sendmail(FROM, TO, message)
if smtpresult:
  errstr = ""
  for recip in smtpresult.keys():
    errstr = """Could not delivery mail to: %s

Server said: %s
%s

%s""" % (recip, smtpresult[recip][0], smtpresult[recip][1], errstr)
    raise smtplib.SMTPException, errstr


session.quit()


```

---

### Post by viper474 on 2009-09-30
> **lavinog said:**
> What do you mean by automatically?

Do you just need to click the send button automatically?  if so you may be able to use xte to control the mouse.

I am not fully understanding the goal.
Is the process triggered by sending an email to the home computer with a shell script attachment, then the home computer executes the script which is supposed to send another attachment back to you?

Edit:  Are you wanting to have the home computer just email the public ip address? If so, why does it need to be an attachment?

It doesn't have to be an attachment, but I just figured it's easier to pipe the data to a file and worry about it later.

Yes, I will have a file set-up on the home computer.  I will send a email from my mobile computer with a keyword, which will trigger an evolution filter.  Then, it will run the file on the home computer.  That program will give the public ip in a file.  I can open up a new evolution email with the send field and attachment added.  I just can't send it without a mouse click, apparently.  How could I use xte?  I have no idea what it is, sorry.

---

### Post by scorp123 on 2009-09-30
> **viper474 said:**
> The reason I'm asking is because I am away from home, and the internet connection is dynamic (at home). 
[http://www.dyndns.com/](http://www.dyndns.com/)

Your IP address may change ... but with DynDNS your machine at home would always be reachable under the same name, e.g. viper747.homelinux.org

That's how I do it. I have several DynDNS addresses and whenever I travel I can easily access my machines remotely just by remembering their hostnames. My router then does the rest.

> **viper474 said:**
>  The program (a shell script) I get to run can get the public ip and store it in a file, but the problem is sending that file to my email. I salute your ingenuity but you're kinda reinventing the wheel and the fire here.

If you still really want to solve this by sending e-mail to yourself you might want to look at **heirloom-mailx** (you will find it in the repos) ... That's the program I used for a mail-bot of my own :D

I'd also recommend you study this page: It contains some useful examples with the "mailx" program ("heirloom-mailx" is extremely similar and should even understand the same syntax and parameters):

[http://www.commandlinefu.com/commands/using/mailx](http://www.commandlinefu.com/commands/using/mailx)

With "heirloom-mailx" you can also use your ISP's SMTP server so you don't have to setup your own.

But again ... If this is all just about getting your own IP address so you can SSH onto your own machines then DynDNS would definitely be the easier solution. :D

---

### Post by viper474 on 2009-09-30
> **scorp123 said:**
> 
But again ... If this is all just about getting your own IP address so you can SSH onto your own machines then DynDNS would definitely be the easier solution. :D

Yeah, I just didn't want to have to sign up and everything.  Plus, it gave me something to do for a little while =P

---

### Post by scorp123 on 2009-09-30
> **viper474 said:**
>  it gave me something to do for a little while =P Well, if that's the problem ...

You could help me with my project maybe? I am writing a mail-bot. The goal is that it should be some kind of "VPN replacement".

Scenario:

You have to leave a system that 100% belongs to you somewhere where you don't and can't control the firewalls. In my case it happens very often that I have to leave one of my laptops or servers with customers for demo purposes .... But sometimes I'd really really want to remotely access those machines. I can't get through the firewalls from outside. Hamachi doesn't work. But I can send and receive e-mails ...

So my plan would be that a an automated process checks a certain mail account for (encrypted) instructions, downloads those instructions, decrypts the message and then executes whatever the message says, and then delivers the output back to another mail address, e.g. mine.

So what I have in mind is some sort of "SSH-via-mail" or "VPN-via-mail" ...

The cool thing would be that you could remote-control your Linux system with anything that can send e-mails, e.g. your mobile phone even.

And I imagine that such a program could also be useful for retrieving stolen laptops?

Interested? :)

---

### Post by viper474 on 2009-09-30
I finally got it figured out guys.  The tip about xte helped, though it must be called xdotool now...  So now all I got to do is set up another email on my domain, configure evolution on the computer back home, configure the correct mouse position into the shell script, then pretty much wait for the email.

Maybe that didn't make much sense, but thanks guys it finally works now.

:guitar:

---

### Post by viper474 on 2009-09-30
> **scorp123 said:**
> 
So my plan would be that a an automated process checks a certain mail account for (encrypted) instructions, downloads those instructions, decrypts the message and then executes whatever the message says, and then delivers the output back to another mail address, e.g. mine.

So what I have in mind is some sort of "SSH-via-mail" or "VPN-via-mail" ...

The cool thing would be that you could remote-control your Linux system with anything that can send e-mails, e.g. your mobile phone even.

And I imagine that such a program could also be useful for retrieving stolen laptops?

Interested? :)

Other than the encrypted instructions paragraph, it sounds similar to my program.  That and I'm not sure exactly through what medium you want to control your device.

The only thing I use my program for is to get the remote ip and return it, knowing that I will be able to physically port forward my router to the home PC.  If there were no firewalls and you could still get to your computer and port, it would work much like mine.  Unless I missed something important.

---

### Post by scorp123 on 2009-10-01
> **viper474 said:**
>  The only thing I use my program for is to get the remote ip and return it  As I said: DynDNS does all that already :D

But I salute your ingenuity. :D

---

### Post by lavinog on 2009-10-02
> **viper474 said:**
> I finally got it figured out guys.  The tip about xte helped, though it must be called xdotool now...
oh, sorry i forgot it is actually part of the xautomation package.
I haven't tried xdotool, but xautomation has other programs that let you do a screen grab and search for patterns such as button locations.

---

### Post by lavinog on 2009-10-02
You actually don't need to attach a file to the email...the email header should have the originating ip address already.

---

