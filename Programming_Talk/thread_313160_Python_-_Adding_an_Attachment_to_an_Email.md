---
title: "Python - Adding an Attachment to an Email"
date: 2006-12-05
forum: Programming Talk
---

### Post by thomasaaron on 2006-12-05
Hey, folks.

Below is a simple python program I wrote to send quick text email messages.
Could someone help me figure out how to add a Word document attachment to the message?

I know it has something to do with the MIME multi-part stuff. But I'm not seeing how to incorporate what I've already got.

Thank you.
Tom

[HTML]#!/usr/bin/env python
#quicknote.py

import os
import sys
import smtplib

while True:
    #Gather Information
    #Get Email Address
    os.system('clear')
    print "To whom would you like to send a quick email?"
    print "Type 'q' to quit."
    print
    sendto = raw_input()
    if sendto == "q":
        loop = False
        os.system('clear')
        sys.exit()

    #Get Subject Line
    os.system('clear')
    print "Please enter the subject of your message."
    print
    subject = raw_input()

    #Get Message
    os.system('clear')
    print "Please enter your message."
    print "Don't hit enter until you're ready to send."
    print
    note = raw_input()

    #Format and Send Message
    msg = "From: copy@tbaaron.com\nSubject: %s\n\n%s" %(subject,note)
    server = smtplib.SMTP("smtp.mail.yahoo.com")
    server.login("MY_LOGIN","MY_PASSWORD")
    server.sendmail("copy@tbaaron.com",sendto,msg)
    server.quit()
        
[/HTML]

---

### Post by ghostdog74 on 2006-12-05
Search google with "Python send attachment". There are links that shows you how. here's an example
[http://www.redcor.ch/intranet_zope_plone/tutorial/faq/SendingMailWithAttachmentsViaPython]("http://www.redcor.ch/intranet_zope_plone/tutorial/faq/SendingMailWithAttachmentsViaPython")

---

### Post by hernan43 on 2006-12-05
Another good one that I have seen/used in teh past is:
[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52243](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52243)

The ASPN Python cookbook is a great place to find python snippets.

---

