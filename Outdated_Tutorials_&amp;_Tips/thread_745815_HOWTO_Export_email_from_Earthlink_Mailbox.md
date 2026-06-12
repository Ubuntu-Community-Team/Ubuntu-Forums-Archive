---
title: "HOWTO: Export email from Earthlink Mailbox"
date: 2008-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by rockin_goliath on 2008-04-04
I wasn't sure were to post this, but I wanted to post it here so that it would be googlable. My dad and I tore our hair out trying to figure this out, but finally we found this simple and frustratingly obvious solution. Hopefully people in the same situation will find this helpful.

This guide is intended for people who are trying to migrate their email away from the proprietary Earthlink Mailbox client and into an open source format. It is tailored for people wishing to switch to Ubuntu Linux, but it could work for anyone. The guide does not require the purchase of the proprietary migration software ABC Amber Earthlink converter. In fact, this does it better and does not risk you loosing the header information and corrupting you emails as ABC Amber did to us. Yet another reason why open source is better.

What you will need: To be able to access your emails from within Earthlink Mailbox in Windows XP.

For those of you that have tried, Earthlink Mailbox lets you export one message at a time in .eml format, but does not allow you to do this in bulk. If you want to export you messages in bulk using the prescribed Earthlink method, you will get a .csv file, which strips all your message of attachments and date stamps.

Now, time for the juicy part:
[LIST=1]
[*]Within Earthlink Mailbox, separate your email into directories of about 500 messages, so that they can be processed more efficiently.
[*]In each one of the directories you created, select all the messages (ctrl+a) and click the "Forward" button.
[*]You will notice now that all of those emails you selected are now attached as .eml files to this message you just started composing. Save this message as a draft.
[*]Go to your drafts folder. Select the message, then go to File - Save As.
[*]Choose a destination for the file. The message will be saved as a .eml file with all of the attached .eml files within it.
[*]Open the message in an open source email client, such as Thunderbird, and select "Save All" for all those attachments.
[*]Choose a destination directory for that huge pile of emails.
[*]You're messages have now been liberated, and can be imported into just about any open source email client you wish!
[/LIST] 

You may encounter problems with importing these files once you get to Ubuntu because some of them may come with the extension in all caps. A simple solution to this is to download the "Bulk Rename" program from "Add/Remove Programs" and tell it to turn all the suffixes of the files into small caps.  

I believe that you can very easily import these messages into Evolution by just dragging and dropping them into your mailbox, but if you are using Thunderbird, grab the plugin IMPORTEXPORTTOOLS (MboxImport enhanced) from [https://nic-nac-project.de/~kaosmos/index-en.html]("https://nic-nac-project.de/~kaosmos/index-en.html").

For all those disillusioned and liberated Earthlink Mailbox users, welcome to open source!

---

### Post by woconnor on 2009-04-08
Hi -

I'm trying to convert Earthlink mail to Thunderbird, and followed your procedure.  Everything worked well until I opened the saved Earthlink eml file in Thunderbird.  The attachments all appeared as empty files.  They all looked to have valid sizes before I saved them from Earthlink.

Have any ideas on where I went wrong?

Thanks

P.S.  I'm new to forums, so please have patience.

---

### Post by tallship on 2010-07-28
> **rockin_goliath said:**
>  ...we found this simple and frustratingly obvious solution. Hopefully people in the same situation will find this helpful.

Another painless method is to synch w/an IMAP server and then sync the MUA of your choice (I Like Thunderbird) with that IMAP Server. Boom! Done! Easy :)

If you don't have access to an IMAP server (You already have that capability if you're running UNIX) you can get a free one here: [http://www.mailtraq.com/552/?ec=&vc=&Action=edit&replyid=-1](http://www.mailtraq.com/552/?ec=&vc=&Action=edit&replyid=-1)

 > **rockin_goliath said:**
>  ...if you are using Thunderbird, grab the plugin IMPORTEXPORTTOOLS (MboxImport enhanced) from [https://nic-nac-project.de/~kaosmos/index-en.html]("https://nic-nac-project.de/%7Ekaosmos/index-en.html").

Hey thanks for that fantastic plugin!

I hope that helps :)

Kindest regards,

Bradley D. Thornton
Manager Network Services
NorthTech Computer
[http://NorthTech.US](http://NorthTech.US)
[url=skype://tallship?chat]TEL: +1.760.666.2703   (US)
TEL: +44.702.405.1909 (UK)[/url]

[Registered Linux User #190795](http://counter.li.org/cgi-bin/runscript/display-person.cgi?user=190795)

***"This is never going to work. You have to shut it down. Shut it down. Take the whole thing down." - James Allchin.***

.

---

