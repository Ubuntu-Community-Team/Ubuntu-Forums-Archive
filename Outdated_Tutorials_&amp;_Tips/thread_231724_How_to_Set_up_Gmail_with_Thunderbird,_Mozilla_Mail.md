---
title: "How to: Set up Gmail with Thunderbird, Mozilla Mail, Evolution, and Kmail"
date: 2006-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by flaak_monkey on 2006-08-07
The complete guide to using Gmail with Thunderbird, Mozilla Mail, Evolution, and Kmail

Here is how to set up a gmail account in Thunderbird, Mozilla mail, Evolution and Kmail. This tutorial is meant to help out anyone, especially a noob such as myself, so it's in for dummies language. I wrote this tutorial because of the lack of good resources on how to do this that I could find. By looking at this document you can get a clue on how to set up gmail in any other email program.

Regardless of the email program you want to use, POP must be enabled in gmail

To do this log onto your gmail account (eg: [www.gmail.com](www.gmail.com)) and select “settings” which is located in the top right corner. Then click on “forwarding and pop.” Enable the option “Enable POP for all mail (even mail that's already been downloaded).

Thunderbird and Mozilla Mail

Start Thunderbird or Mozilla Mail

Select “File,” “New,” Account

On the window that pops up select “email account,” and next

Then type in your name in the top box, and your email address in the bottom, and click next

On the next window select “POP” as the type of incoming server, then name the incoming server “pop.gmail.com,” it doesn't matter if “Use Global Inbox is enabled” is checked, it makes all of your email accounts report to the same inbox, check it or uncheck it as you wish, and finally click next.

After that make your user name is the same as your email address and click next

Then type in an account name (eg: inbox, gmail, home) this is what you click on to access this account and can be whatever you want, and click next

Click finish

Next click on “edit,” “Account Settings” in Thunderbird or “Mail and Newsgroup Account Settings” in Mozilla Mail, and from the menu of the new window select “server settings.” Make the port “995” and Check “Use secure connection (ssh)”

Your done! See bottom for notes regarding problems and errors.


Evolution

Start Evolution

Click on “Edit,” then “Preferences”

Click “Add”

Type in your name, email address, reply to address, (what email address you want people to write back to you with) and your organization, if any, and click forward.

Select your server type as “POP,” your host as “pop.gmail.com,” and make sure that your username is the same as your email address. Then under “Use Secure Connection” select always, and your “Authentication Type” as password, and finally click forward.

On the next page adjust settings as you like, they will not interfere with whether gmail will work with evolution or not. Then click forward.

Select server type as “smtp,” type in “smtp.gmail.com” as the host, and check that the “Host requires authentication” box is checked. Next, select, for “Use Secure Connection,” always. Finally, make sure that Authentication type is “Plain” and your user name should be the same as you email address. Click Forward.

On this page name your account whatever you want, it will not interfere with setup and click Forward.

Click apply.

Your done! See bottom for notes regarding problems.

Kmail

Start Kmail

Go to “Settings,” then “Configure Kmail”

Click on accounts
Click “Add”

Select POP3 on the window that pops up and OK

On this window type in whatever you want your account to be called under “Account Name.” Then type your login, which is your entire email address, and your password. Next for the host type in “pop.gmail.com,” and change the port to 950. Change the rest of the settings to your liking.

Then on the top tab, arrow over to “Extras” For encryption select “Use ssl for secure mail download,” and for Authentication Method, select “Clear Text.”

Your done! See below for notes regarding problems.



I'll be happy to help you with any problems you may have, but please, double check that you've followed the instructions, and make sure you post any error messages that you may have. If you know you have messages in your inbox, but they don't show up enable pop again in gmail. To get messages in my inbox that were there before I configured any of the email programs I covered here I had to repeat that step.

Also here a basic chart on the needs of gmail provided by google: [http://gmail.google.com/support/bin/answer.py?answer=12103&query=thunderbird&topic=0&type=f&ctx=search](http://gmail.google.com/support/bin/answer.py?answer=12103&query=thunderbird&topic=0&type=f&ctx=search)

---

### Post by hopstah on 2006-08-08
your link to google at the end doesn't work.  you copied the truncated text instead of the entire link.

do you know if it's possible to re-download all of your messages from gmail if, for example, you accidentally reformatted and lost your thunderbird database?

---

### Post by Frostmourne on 2006-08-08
To redownload your messages, on Gmail's Settings > Forwarding and POP screen I would try setting POP download to disabled, then setting it to the "download all, even if it's already been downloaded" setting. If you had selected the option to delete Gmail's copy when messages are accessed by POP your messages are lost.

---

### Post by flaak_monkey on 2006-08-08
*UPDATE* i fixed the link at the bottom.

---

### Post by dyoung66 on 2006-08-20
kmail won't send a gmail message.

I noticed you didn't include smtp instructions for kmail.

Ive tried the following and some variations of the below settings to get kmail to work.

From google:

Outgoing Mail (SMTP) Server - requires TLS:  	smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587

I tried these and other settings and everytime I get the error " Unrecognized transport protocol - Unable to send message"

POP works fine, I deleted the smtp settings and set it up again but still get the same error.

Does anyone else have this problem??

---

### Post by mindepinde on 2006-09-25
Figured it out by trial-n-error: for Gmail send-mail to work in Evolution, the following should be used under account's configuration "sending mail":

Server type: SMTP
Server: smtp.google.com:465
Server requires authentication: (checked)
Use Secure Connection: SSL
Authentication: Type: Plain
Username: (your.login)@gmail.com
Remember password: (checked, to avoid hassle later, if you want)

As for smtp server, you may use either ports 465 or 587. That all should work.

---

### Post by Tominator on 2006-10-02
Way to go Mindepinde! That definitely worked for me using Evolution on Gnome for Gmail. Thanks a lot and you should spread it around and take the credit. Tom

---

### Post by David Oxland on 2007-03-17
Hello flaak_monkey
 I've been struggling with configuring evolution  using your posted how to pick and send gmail while I'm away on holiday.  Evolution has worked find with my home provider and someattempt at this loation with a HS provider have received gmail  fine through evolution  but kept getting messages that the new setup was "not enabled" inspite of the toogling of enable on and off. Have tried using both  [email]smpt@googlemail.com[/email] and [email]smpt@gmail.com[/email] as well as inserting ports : 465 or 587 and never have been able to send.  At one point it started pointing back to my usual home mail address so I deleted all my Evolution accounts and started again. Now I cannot receive or send.  I'm ready to start again but not sure to begin.  Any suggestions would be appreciated. Evolution ver 2.6.1
Thanks very much David Oxland

additional I did exactly as mindpinde did above and now cannot send or recieve

---

### Post by gentix on 2007-08-15
Thank you muchly for this guide.  I've never used any of these email programs before (allways just the online gmail) so this will be imensely helpful once I get Ubuntu working properly.

---

### Post by gentix on 2007-08-15
I have a couple of questions about pop:

In the past, I've allways used the gmail internets thingy, but I want to try pop, so I'm prety ignorant.  If you use pop forwarding, does email still get sent to my online gmail accound?  I want to archive my messages on my alloted space there, rather than on my local computer, if possible.

---

### Post by AndrewGene on 2007-09-12
> **David Oxland said:**
> 
additional I did exactly as mindpinde did above and now cannot send or recieve

...same here

anyone else with any ideas?

---

### Post by ben2talk on 2008-03-03
This forum is very confusing. Many options mentioned are simply not available! 

In the Gmail help pages, they say 'Tools>Account Settings' which I could not find...  (Edit>Account Settings is correct for Thunderbird 2.0 in ubuntu; perhaps it's in the 

The images are from Windows, but they are very similar indeed, and I managed to send a test email from gmail in thunderbird, received it in Yahoo webmail, and Thunderbird then received the reply from yahoo webmail!!!! It can be done, but you should rely on the advice of Gmail to set up an account.

[http://mail.google.com/support/](http://mail.google.com/support/)

---

### Post by S0VERE1GN on 2008-05-09
i have a small...well big problem here. 

I set my "host" to my router name cuz im a dummy, and i dunno how to change it to the right thing. 

halp! :(

---

### Post by Old Marcus on 2008-05-09
Which mail client?

In evolution it's Edit -> Preferences -> Mail Accounts then choose your mail account and click edit. Click on the recieving email tab and change your server to pop.gmail.com.

---

### Post by S0VERE1GN on 2008-05-09
i've changed my server to about 1000 things people have reccommended, the problem seems to be something else, because when i click on the recieve mail button the same message comes up that says unable to find host "le chapel" (my router name) where can i fix this?
im connected to the internet properly, but apparently the program can't find the internet maybe? i duno.

---

### Post by S0VERE1GN on 2008-05-09
the exact words are here 

Error while performing operation.

Host lookup failed: Le Chapel: Name or service not known

---

### Post by mx727 on 2008-07-30
Hi.

In evolution I had to select under "use secure connection", "SSL Encryption" for incoming mail and "TSL Encryption" for sending email.
Cheers

---

### Post by David Oxland on 2009-05-21
Earlier I had mentioned that I had no success setting up evolution to send via smtp.gmail.com

This winter after giving up on evolution I tried Thunderbird using the instructions found in gmails guide.

It worked well and after an upgrade to Jaunty I thought I would try to set up Evolution again.

Success!

Operated it for  a few weeks and then something got disturbed.
No more smpt.gmail 
I have the feeling that editing or deleting the accounts under preferences does not do the job.
I'm wondering if I should be looking into how to check and delete settings in Terminal?

So as a result I have Evolution working on a desktop but the laptop just won't go with identical settings: both plugged into the router.

---

### Post by jaj23 on 2009-05-29
Can't get evolution mail working nor thunderbird. Followed exact instructions here and been messing with it for hours.

I'm sure it shouldn't make a difference but I am using an @googlemail domain name.

Help! Driving me insane. I need an email client!

---

### Post by tturrisi on 2009-05-29
[http://mail.google.com/support/bin/answer.py?hl=en&answer=13273](http://mail.google.com/support/bin/answer.py?hl=en&answer=13273)
[http://mail.google.com/support/bin/topic.py?hl=en&topic=12805](http://mail.google.com/support/bin/topic.py?hl=en&topic=12805)
[http://mail.google.com/support/bin/answer.py?hl=en&answer=13287](http://mail.google.com/support/bin/answer.py?hl=en&answer=13287)

---

### Post by spike_naples on 2009-06-17
Thank you. 

My error in trying it out (as I read most posts fast) was to NOT enter my email addy as the USERNAME.

Thanks for putting emphasis on this. I happily use Gmail on my Evolution program now.

---

### Post by perceptus on 2009-06-21
For Evolution Mail and Gmail I found this Page to be invaluable.  
[http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)

---

