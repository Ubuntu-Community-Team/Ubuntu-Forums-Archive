---
title: "Invoice Software"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by rolfUser on 2013-04-23
I really like how Ubuntu is a really stable operating system. I like it so much that I want to install it on this other computer that I have, but I have a bit of a dilemma. This other computer runs on Windows and I need it to so that I can run a program called **My Invoices & Estimates: Deluxe**.

I searched on my desktop in the Software Center under the keyword, "invoice" but all I got were some programs that got bad reviews.   Is there any way of knowing if it is possible to run this invoice program on Ubuntu?    I'm guessing the answer is no  but I am curious to know more about Ubuntu.   More importantly, I want to know if there are any reliable invoice software programs to use that are compatible with Ubuntu. 
 I'm not even sure if this is the section to discuss this, so I'd appreciate it if someone told where to go for the right support.

---

### Post by khelben1979 on 2013-04-23
It is actually possible to install and use Windows software directly on your Ubuntu system. It will depend about how well this Windows software is supported by something which is called Wine. Take a look at [this link]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true").

On the above link you get to the WineHQ homepage where you will be able to click in the exact application that is compatible with the Wine software. The Wine software and the version of Wine decides if the Windows application that you want to use, that decides if it's possible or not. About possible Linux invoice applications, you can always look inside the categories from the Ubuntu Software Center (which I assume that you have already done) and besides that place you also got the sourceforge.net which has a lot of software which is not provided by your Ubuntu Linux distribution. In some cases, it is necessary to compile the source code yourself, but not always.

Hope this helps, for starters. :)

---

### Post by schragge on 2013-04-23
Also have a look at [post=12523641]this post[/post].

---

### Post by Warren Hill on 2013-04-23
Have you looked at [Gnucash]("http://www.gnucash.org/docs.phtml")?

It's handles invoices, cash flow, accounts etc. You can find it in the software centre or from the link above.

It is almost always better to use software suitable for your OS rather than via Wine or Virtualisation software

---

### Post by khelben1979 on 2013-04-23
> **Warren Hill said:**
> It is almost always better to use software suitable for your OS rather than via Wine or Virtualisation software

From a technical standpoint I totally agree with you. But from a more practical standpoint I totally disagree. Because if you're used to using one software application and where it's filled with data records, you will need that very same software to access your data, as you know. Migrating to new software is not always an alternative, as migrating to another operating system should be. 

The choice is free, which I think it's the best thing of all, knowing about alternatives, also knowing the difficulties which comes with it, and I believe that's why we are here too. :)

---

### Post by tgalati4 on 2013-04-23
[http://sugarcrm.com](http://sugarcrm.com) is a Contact Relations Management package that follows the entire pipeline from lead generation to bidding, to contract.  It does not have billing, but it does have a plug-in framework and there are a few invoice plug-ins.  The fact that you have your clients in a database means that you have quite a few of them and you want to keep detailed records on each one.  Sugar runs natively on your Ubuntu server and is accessed via a webpage on your internal network.  You can also get cloud-based services if you have multiple operating locations.

---

### Post by rolfUser on 2013-04-23
The information on GnuCash seems interesting, but I want to know about Wine.

I followed the link to WineHQ. I typed in the software program, **My Invoices & Estimates Deluxe**,  and it brought me here:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6263](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6263)
From there, I clicked the link to see a page with some information. I figured what I was after was at the bottom of the page where it says, "[COLOR=#000000][FONT=bitstream vera sans]**HOWTO get it running**" . ( I'm guessing I will have to install a few programs and then work with a command prompt. )

I'm guessing that what this is telling me is that in theory, I can get it to run. That's great. But what is .... Kubuntu (mentioned under test results)?  The version I currently use is Ubuntu 12.04, I think.  Maybe I could test its compatibility on my PC first before installing Ubuntu on that other computer and try to get it run on there.  
 
Even though it appears that I found what I needed, I don't know what to do with what I have. How to proceed?
[/FONT][/COLOR]

---

### Post by oldfred on 2013-04-24
I do not think Bronze is very good and only one user tried it. That usually means some functions may not fully work. But no harm in experimenting if you are so inclined.
But back to comments above, better to use native software.

I dual booted with XP for 5 years until last year. I had used Quicken since DOS and upgraded just about every year for 20 years. But finally realized I did not need all the features, they were nice & I think if Quicken offered a Linux version I would pay for it. But I have KmyMoney for my checkbook and some other data and that is all I really need.

---

### Post by mastablasta on 2013-04-24
> **rolfUser said:**
> The information on GnuCash seems interesting, but I want to know about Wine.

I followed the link to WineHQ. I typed in the software program, **My Invoices & Estimates Deluxe**, and it brought me here:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6263](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6263)
From there, I clicked the link to see a page with some information. I figured what I was after was at the bottom of the page where it says, "[COLOR=#000000][FONT=bitstream vera sans]**HOWTO get it running**" . ( I'm guessing I will have to install a few programs and then work with a command prompt. )



yup. or you can try Play on linux (a GUI for wine) which has a couple of stuff preset.
bronze means some stuff might not work. however i also see that last test of this software seems to have been done back in 2007. so it might work nicely this time arround. hard to say.

[COLOR=#000000]> [/COLOR]
I'm guessing that what this is telling me is that in theory, I can get it to run. That's great. But what is .... Kubuntu (mentioned under test results)? [/FONT][/COLOR]

Kubuntu is a version of Ubuntu with KDE desktop. KDE looks & feels a bit more like windows.

i would follow oldfried's advice and give alternative porgrammes a try. perhaps they can even import invoices. 

i created small online shop and that one uses it's own invoice system. it doesn't seem that these invoices are anything special. i mean you need some way to track and trace them (archive) and certain data must be on them and that's about it.

if your needs are more complex (bigger company) then your would need an ERP anyway (such as OpenERP for exmaple).

---

### Post by dale52 on 2013-04-24
I have used a website called filetransit and have gotten a few linux programs and haven't had any problems with them. I don't know if anyone else has used them but they have 127 linux programs in the business section under linux if you want to check them out.

---

### Post by Warren Hill on 2013-04-24
One option, which will work but is not free, is to install Virtualbox from the software centre, then install Windows inside Virtualbox and finally the program you want to use.

This is not free because you will need a licence for Windows and install media.  

Running software in a virtual machine is slightly slower than directly on your hardware but I don't think it will be noticeable for the program you want to run.  A high end game on the other hand probably would be too slow.

---

### Post by rolfUser on 2013-05-02
I have an idea. My other computer, which runs on Windows XP Professional, was said (by my computer technician) to be able to run two operating systems. I have seen computers like that. You start it up, and a prompt on a pitch-black screen asks to run either Windows XP or Windows 7.
The technician didn't say I could not also run Ubuntu, so theoretically, I could have both OSs on that computer. But I have a question. If I could do that, what would happen?  Would I still need virus protection for my other computer?

---

### Post by oldfred on 2013-05-02
I dual booted XP and Ubuntu for years and still have XP installed on a drive in my desktop and on my laptop. I actually fired up the XP when my daughter could not get to work due to rain and needed a system to use to do work from home. 
But I hate starting it up as I have to do so many updates and reboots. XP wants its updates, firewall wants its updates, virus software wants its updates, then Jave and some other software which I do not use all pop up insist on updates and each wants a reboot. Why could it not be simple like Ubuntu on only need one set of updates and only if kernel need reboot?

You should not need the virus software for Ubuntu but definitely for XP. The main risk to Linux is phishing or getting you to believe a web site is your Bank or credit card site and get you to type in passwords.  Or similar to install software by convincing you to giving your password. With Linux security of ownership and permissions it is more difficult and about impossible to auto install something in the background unless you specifically authorize it.

How much space do you have on XP system. Windows NTFS partitions need about 30% free space to run well so you should not shrink it more than that.

---

### Post by rolfUser on 2013-05-10
I have lots of space on my Windows computer. 
It's a brand new mother board with the old monitor, keyboard and mouse and printer.  The original motherboard crashed. 
I think it runs on a 500gb hard drive. It also has USB 3.0 ports. I still find it baffling how you could use these ports to exchange 4gb of data in  a few short seconds. 
But this topic is in regards to the invoice software. Let's not digress too much. 

What I am actually looking for is information** to start** on using the invoice software (for Windows) safely and successfully using Ubuntu OS.  
My other idea is that maybe.....     I can run both WIndows XP & Ubuntu on the same computer in the hopes that I wouldn't need anti-virus software anymore.

So look. I now know about WineHQ. I want to learn to take advantage of it and would like to know... which forum in Ubuntu forums deals with support for software like WineHQ? I know I can't just point and click and be done. I kind of have to have some software engineering skills to move forward and would like to develop them from here. Just tell me where to start for instruction.

---

### Post by Derek Karpinski on 2013-05-10
If your computer/processor is anything less than 5 or so years old, and you have a valid windows xp license and install disk, I'd use virtualbox and create a windows xp virtual machine.  Much better than having to restart to run windows applications.

We use it because we use Quicken.

---

### Post by s1baker on 2013-05-10
I agree with Derek Karpinski.

I was runnning Ubuntu 12.04 on my desktop with VirtualBox on my 7 year old computer,
and I had XP as a guest under VirtualBox. Ran just fine.

My old 7 year old computer ( finally went out on me after running
16 hours a day, everyday, last  7 years ) was a 64 bit, and I ran
32 bit XP. If you have the memory, it is a lot easier to run XP programs this way.

---

