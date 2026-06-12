---
title: "any osmo users? help please"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Knacker on 2008-11-06
Hi,
This is a question about Osmo ([http://clay.ll.pl/osm/](http://clay.ll.pl/osm/)). If someone knows the application and could help out, I'm sure it will be useful for other new users. If you think this question belongs somewhere, can you recommend where I put it? I can't find a package specific forum for this and I'm not confident it's a bug, so I don't know where else to ask. I've checked other threads and looked for answers on other forums. I'm running version 0.2.4 of osmo on Hardy/Mint 5. I installed from .deb grabbed from website (osmo_0.2.4-1_i386.deb).   

So, I've just started using Osmo and I've got the new 0.2.4 version installed from .deb. But I can't figure out whether i'm doing something wrong or certain functions just don't work. I have two questions.  

1) I can't get the recurrent task scheduling function to work properly. Honestly, I don't understand how this is supposed to work. What do these different categories (time period, date period) refer to and what do I need to change in order for a event to repeat (for example) on the same date/time for a few weeks? I've tried everyhting I can think of and the task does not repeat (i.e. appear on the appropriate, subsequent calendar days as I'd expect it should). In the task tab, it is clearly marked as a recurrent task, but it doesn't populate to the calendar. I hope that's clear. Basically: does the recurrent task function work for you and, if so, what am I missing?  

2) how do I set up alarm commands? (say launch a reminder window and/or sound)? 

This application would be perfect for me and a lot of others...and that's a rare thing. I just wish I could get it to work.
Please help!!

---

### Post by Jonas813 on 2011-07-26
For the recurrent tasks, you can see this link :
[http://www.murga-linux.com/puppy/viewtopic.php?t=53162&sid=9e7df00293eee591750e2645a5b927a5](http://www.murga-linux.com/puppy/viewtopic.php?t=53162&sid=9e7df00293eee591750e2645a5b927a5)

The following text was quoted from here :

> **Recurrent task:** 
 
This is broken down into two subsections: **Time period** and **Date period**.  You should probably use only one or the other of these sets of fields.  I've not had good results when trying to mix them. 
 
**Time Period** 
 
This is for tasks that repeat during the day. 
 
"Start" and "End" define the period during the day when the task recurs. 
 
"Interval" defines the frequency that it recurs. 
 
For instance, if you spend the hours from 9:00 AM to 5:00 PM trying to fathom the mysteries of how to use undocumented software, and you need to take a pain reliever every four hours to deal with the resulting headaches, you could set the fields like this: 
 
------------------------------------ 
**Start**   Hour: 9   Minute: 0 
**End**  Hour: 17  Minute: 0 
**Interval**  Hour: 4   Minute: 0 
------------------------------------ 
 
**Date period** 
 
This is for tasks that repeat once a day or less frequently, and always at the same time of day. 
 
"Days" and "Months" define the frequency that it recurs (like "Interval" fields in Time Period, but confusingly not so labeled here). 
 
"Repeat" defines the number of times the task will be repeated.  If left at zero, it will be repeated forever. 
 
"Repeat in the following days" allows you to tell Osmo that you have no intention whatsoever of dealing with this task on your days off, if any. Simply un-check the appropriate days. 

I am trying to do a recurrent task every month, so I will see if it works. For your case, I think you need to edit only the date period and (for example) set the day field to 14 for a 2 week recurring task.

> In the task tab, it is clearly marked as a recurrent task, but it doesn't populate to the calendar.

This question is also answered on the link I showed :

> First it should be noted that Osmo does not fill your calendar with every iteration of your recurrent tasks. That is to say, if you set a task to be done every Monday, you won't see a mark on all the Mondays on your calendar, just the next Monday.


Jonas

---

