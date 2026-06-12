---
title: "smpt error"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by Tahinimoon on 2012-07-19
Hi, 
I'm using evolution mail. It was working fine until a few days ago. 
1. It then started giving an SMTP  error message: message sending failed, you are not authorized to do this (cant recall exact words)
2. Then error message changed to simply nothing - when I try sending anything, including a test to myself - it just hangs. 

I am on Ubuntu 12.04 LTS. 

1.Things to note: For my internet access i use MWeb - I have called them and they have checked and reset my settings. 

2. My email is with a place called smarter mail - on a different server. MWeb suggested I check my 'enable verify message sending' - all seems fine there. 

I'm not sure what I should do next. 

So I thought to post this message to see if the error is in someway related to my ubuntu settings ?? I can receive my messages - but to send messages i have to login to the online mail server to send any messages. It is a bit tedious. Any suggestions as to what the problem could be?

---

### Post by searchfgold6789 on 2012-07-19
Your email client (Thunderbird I'm assuming?) must have SMTP Authentication enabled. You can enable this by going to the Outgoing mail server, or SMTP, settings, and enabling it; there should be fields for the username and password for the email account.

---

### Post by Tahinimoon on 2012-07-19
> **searchfgold6789 said:**
> Your email client (Thunderbird I'm assuming?) must have SMTP Authentication enabled. You can enable this by going to the Outgoing mail server, or SMTP, settings, and enabling it; there should be fields for the username and password for the email account.
I'm using evolution mail not thunderbird

---

### Post by Tahinimoon on 2012-07-19
> **Tahinimoon said:**
> I'm using evolution mail not thunderbird
Authentication:
type - login 
username: b....... 
remember password is ticked

port is 25
server requires authentication is ticked

server type SMTP

---

### Post by steeldriver on 2012-07-19
whose SMTP server are you using (i.e. smartermail or your isp?) are you sure they accept port 25 connections?

---

### Post by donkyhotay on 2012-07-19
You might want to correct the name of this thread. I was very curious as to what in the world a SMPT error was, reading this it's obvious you mean SMTP error. Getting back to your issue though, have you tried using a different Email client like thunderbird? Even if you prefer evolution if you have problems with multiple clients then it might be something with your SMTP server rather then your client configuration.

---

### Post by Tahinimoon on 2012-07-20
Sorry about incorrect heading - :{ and i cant seem to alter it only the message text. 

At the moment my settings are set to use smarter mail settings. I have also tried my isp providers settings - neither work for sending mail using evolution mail. 

How do i know if i have correct port or not?

Is it easy to change to Thunderbird? I'm willing to try anything - as it is annoying receiving mail in evolution then having to login online to send mail at smarter mail.

---

### Post by Tahinimoon on 2012-07-20
Last week I changed my email password on smarter mail, I also changed my user login password for Ubuntu. I'm wondering if this is causing a problem with not being able to send mail? 

My oem password has not been changed on ubuntu - the one i use to log in on the terminal. Should I change this one as well? If so, how do i do that?

---

### Post by Wim Sturkenboom on 2012-07-20
Post #8 makes life confusing. You only have one password in Ubuntu (unless you did set up multiple users). Your password to login into the graphical environment is the same as the one to login into a terminal (assuming you're refering to the consoles that you access with <ctrl><alt><F1> etc).

So I'm not sure what you mean by oem password.

---

### Post by Tahinimoon on 2012-07-20
> **Wim Sturkenboom said:**
> Post #8 makes life confusing. You only have one password in Ubuntu (unless you did set up multiple users). Your password to login into the graphical environment is the same as the one to login into a terminal (assuming you're refering to the consoles that you access with <ctrl><alt><F1> etc).

So I'm not sure what you mean by oem password.

Sorry, I'm really trying to convey the correct terms. :{ I'm really not very pc adept at this. 
I'll try be clearer.

1. I changed my password at smartermail. Then I changed my password in my evolution email settings. 
2. My terminal password and user login password is still the same as it's always been. 

This is the exact error message i receive. 

Unable to authenticate to SMTP server
Bad Authentication response from server
Please enter the SMTP password for (my email address) on host smtp(address)

Hope that makes sense. :(

---

### Post by searchfgold6789 on 2012-07-21
First, check with this Smartermail service that what you entered in your account's SMTP and SSL settings is correct. I googled and found no clear information on this, so you'll probably have to contact them directly. Try playing around with the SMTP authentication settings in the SSL tab in your account preferences, perhaps?

Or, you could try using Thunderbird. This is the default email client that comes installed with Ubuntu. When you open the Unity menu, simply click "Check email", which is on the bottom row of logos and is accompanied by a picture of a blue bird encompassing an envelope. When you first run the program, you will be guided through the process of setting up an account. In Thunderbird, more of the settings are discovered automatically for you.

---

### Post by Tahinimoon on 2012-08-09
I have changed my SMTP service and checked my settings. Sometimes I can send emails and sometimes I can't. Most times I can't. I just can't figure out what the problem is with sending emails. 

If I switch from Evolution to Thunderbird how do I ensure that my emails I have aren't lost? I have created many sub-folders with important emails.

---

