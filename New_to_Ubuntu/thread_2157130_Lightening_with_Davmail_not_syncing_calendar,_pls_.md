---
title: "Lightening with Davmail not syncing calendar, pls help"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by silverbullet007 on 2013-06-24
So using Davmail with Thunderbird/Lightening to work with my Exchange 2010 server here at work.  The mail side of things works fairly well, teh calendaring not so much.  I have set it up following the normal instructions, then created a new calendar pointing to localhost:1080.users/user@domain/calendar and I'm getting reminders which is weird.. but cannot see the events.. their not being displayed at all.

Any clues on how I can fix this?

---

### Post by GrouchyGaijin on 2013-06-24
I wonder if there is something with Exchange 2010 that doesn't work well with Davmail.
I had used it for a few years in conjunction with Kaivalgai's Conky email script.
[http://ubuntuforums.org/showthread.php?t=869771](http://ubuntuforums.org/showthread.php?t=869771)

Right about the time my employer upgraded to Exchange 2010 I started having trouble with Davmail.
The mail in Thunderbird worked OK, most of the time, but the notification via the Conky email script stopped working all together.
I fiddled with the script a bit (I don't remember what exactly I did.) and was then able to get notification of one new message at a time.
Any other messages aside from the first one were not displayed.

I went to the Davmail site and made sure I added the snippet of code for Exchange 2010, but that didn't help.

There are a couple of solutions: 

1. There is an add-on for Thunderbird that will let you access Exchange (including the calendar).  I can't remember the name, but I have used it and it worked pretty well.
2. This worked for me, but probably isn't what you are looking for, I installed Popper and it picks up new mail messages from the Exchange server.  I then use OWA to read the mail.  I did this because I use Mutt for email and just didn't want to setup a separate client for work email on my personal machine.  I use Google calendar for all of my appointments, so the Exchange calendar isn't a big deal to me.

---

