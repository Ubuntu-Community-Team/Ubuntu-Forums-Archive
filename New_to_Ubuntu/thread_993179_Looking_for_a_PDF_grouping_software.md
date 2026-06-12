---
title: "Looking for a PDF grouping software"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by LowSky on 2008-11-25
My company has a billing system that creates all invoices as PDFs. Our customers have expressed that they would like to receive their bills in one envelope. Due to applicable laws each invoice has to be billed separately, but the law states nothing about mailing the invoices together (nice little loophole) and will save us considerable envelopes.

So what I need is a software the will group the invoices based on the actual address listed and not the PDF file name. Is this possible in Linux. I am asking because Pitney Bowes sells a software solution but it is heavily based on MS Access 2003 but is extremely expensive, and fails to work with our PDF creator, as they state "it is out of date," which is BS -- IMHO!

I would love an open-source solution if anyone has one.

thanks guys

---

### Post by Olivier2371 on 2008-11-25
I don't know that can help but I heard of a function in Microsoft office call mail merge.

I don't know if openoffice would have the same function.

---

### Post by opscure on 2008-11-25
Post script is readable!  Open one or two of the invoices in a text editor (like vi, emacs, nano, etc) (not a pdf viewer) and search for the date.  When you find it look at the tags right before it.  If it's the same across each of the documents then you can spider each file using a  bash script to grep and cut out the dates.  From there just create a kdialog or terminal user input to specify what you're looking for.  While this may be more advanced then you would like to jump into, I'm sure if you jumped on rentacoder you could find someone to make you a little program that does this.

---

### Post by picturefreedom on 2008-11-25
hi, new to the forum, i was looking for something like this a month ago, but couldn't find a solution, would be nice if there's an existing one.

but snooping around, i'm  almost certain now, that someone has to code this in, my IT friends told me that this is doable in python? with some pdf component?

---

### Post by LowSky on 2008-11-25
> **opscure said:**
> Post script is readable!  Open one or two of the invoices in a text editor (like vi, emacs, nano, etc) (not a pdf viewer) and search for the date.  When you find it look at the tags right before it.  If it's the same across each of the documents then you can spider each file using a  bash script to grep and cut out the dates.  From there just create a kdialog or terminal user input to specify what you're looking for.  While this may be more advanced then you would like to jump into, I'm sure if you jumped on rentacoder you could find someone to make you a little program that does this.

this might work... seems simple enough, I'll try it tonight. I'm going crazy trying to write scripts for so many other things, I'm going nuts... off to the next project

never even heard of Rentacoder before, very cool website.

---

### Post by opscure on 2008-11-26
> **picturefreedom said:**
> hi, new to the forum, i was looking for something like this a month ago, but couldn't find a solution, would be nice if there's an existing one.

but snooping around, i'm  almost certain now, that someone has to code this in, my IT friends told me that this is doable in python? with some pdf component?

Yeah, python will work.  so will perl, java, c, php, etc almost every language has a post script library and if you don't want to use a formal language you can use grep in a bash script to make needed changes or awk for even more control with less code.  It's really not a hard process once you get the hang of it.  

Just a bit time consuming and a little annoying the first time around.

---

