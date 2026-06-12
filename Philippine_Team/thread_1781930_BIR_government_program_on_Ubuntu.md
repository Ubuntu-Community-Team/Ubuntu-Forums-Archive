---
title: "BIR government program on Ubuntu"
date: 2011-06-14
forum: Philippine Team
---

### Post by arvin555 on 2011-06-14
Hello, would like to request some help.

I have been actively trying to get some office computers converted to Ubuntu, and the recent "victim" is giving me a challenge I need your help with.

She uses the Government's BIR Alphalist program 
[http://www.bir.gov.ph/lumangweb/alphalist_full_setup_v3_4.exe](http://www.bir.gov.ph/lumangweb/alphalist_full_setup_v3_4.exe)

I naturally thought of Wine, and was actually successful in installing the above program and running it on wine.  Which is good news to ubuntu users who are accountants and such.

However during testing, we found just one glitch (for now), there is a button in the program that will create an excel file for archiving and printing.  Of course ubuntu uses OOffice and for sure the program does not recognize it. 

I already emailed BIR but not sure if they are willing to help or if they will even read my email.  I thought I'd post this here and maybe someone can offer ideas and solutions.

Also it is unfortunate that our government or their IT guys actually specifically used excel only and no way to change it to other programs in the market, I mean OOffice is free why didn't they offer that?  

Hope you guys can help.

Using Pentium 4 desktop and Lucid Lynx and latest version of wine (Sorry forgot the version).

TTFN
Arvin

---

### Post by tech-hero on 2011-06-14
The easiest solution i see is to install MS Excel too in wine. :)

---

### Post by arvin555 on 2011-06-15
Thanks for your reply Tech-hero

Have actually considered this and just for confirmation or experiment will try as you suggested.

However as I mentioned it is really bad form for the government to actually make such kinds of programs that makes use of "expensive" and of course not free program, beats the purpose and will not really help in standardization.

What I mean is No "Open source" consideration at the least. :(  

Maybe they can improve on it for their version 3.5 :)

TTFN
Arvin

---

### Post by jsgotangco on 2011-06-15
Excel is probably used to create the form and tied up to some macros. Best shot in the future for this is to export as xml or csv at the very least. It doesn't have to be app specific open source or not (its not a good argument either) - just need to have the data exported to a common format.

---

### Post by arvin555 on 2011-06-15
I understand what you mean, instead of needing to open a specific program, which is not going to be easily standardized, just make it export to a file that can be opened by almost all spreadsheets.    I agree with this direction as well, but unfortunately as of now the program only exports to excel :(

We'll update if or when BIR replies with their suggestion. 

TTFN
Arvin

---

### Post by tech-hero on 2011-06-15
> **arvin555 said:**
> I understand what you mean, instead of needing to open a specific program, which is not going to be easily standardized, just make it export to a file that can be opened by almost all spreadsheets.    I agree with this direction as well, but unfortunately as of now the program only exports to excel :(

We'll update if or when BIR replies with their suggestion. 

TTFN
Arvin
I guess the problem here now lies not on the OS. But on the sofware itself. They have to exert some effort to that "BIR software". Besides, It would benefit them on the long run. It may be costly initially, but considering all the stuffs that you would save in using ubuntu, it's all worth it.

---

### Post by arvin555 on 2011-06-15
Unfortunately a phone call to the BIR call center resulted in more or less the following statement:

The program was written with Excel in mind, so they cannot help us!

How many stars does our government get for this kind of reply? :-k

Still hoping that my email to them might result into something more workable.

TTFN
Arvin

---

### Post by tech-hero on 2011-06-15
Uh oh. Then that's the hard part. "They made everything with excel in mind". That's what microsoft did to most - monopolized almost everything in terms of Office productivity. 
 
Don't worry time will come, as MS lowers down its shares on the market, people will consider cheaper and better alternative options.

---

### Post by arvin555 on 2011-06-15
Yeah, of course in my opinion if they actually just spend maybe even just 30 minutes to write in the program a way to choose what program to use, that would have solved the problem already.  

I understand that there has to be some organization that should lobby against this specially on how government agencies deal with the public. I mean sure this program that they made has streamlined the process for both private and Government, but why make it such that it will only work with one program?

As an update though, I installed excel in wine, and tested, it worked in some parts, but on others it generated errors and still didn't work, now I am not sure it it's wine, wine compatibility with Excel or what not!  More work :(

Last course of action which I hate is Dual boot :(  Sheesh!

TTFN
Arvin

---

### Post by tech-hero on 2011-06-16
30 minutes?  :) I was thinking if they could rewrite the "BIR program" so that it could also run in Linux aside from just changing the Excel thing issue.

You could also use virtual box instead of dual boot.  It will be more convenient that way. But those solutions I think wouldn't solve your main cause.

---

### Post by arvin555 on 2011-06-16
Hehehe, if they chose to just shrug and say sorry that is how we designed it, I am not so optimistic that they will rewrite for linux users!    Which just makes me more motivated in promoting linux for mainstream! :)

I was able to talk to my officemate and at least for now the problem is solved, she has a work around for that other concern that I found.  

Still as I mentioned it is not ideal because it still required me to install excel in wine!  Why should we need to when OO spreadsheet will work nicely.  At least she can just work using wine and not need to dual boot or virtual box.

I am not sure if you guys want to call this closed though. :)

I actually have another issue with another government system, but that is another story, will research first before posting, asking for options.

TTFN
Arvin

---

