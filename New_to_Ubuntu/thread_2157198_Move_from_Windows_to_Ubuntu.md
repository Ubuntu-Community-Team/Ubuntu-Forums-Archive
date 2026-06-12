---
title: "Move from Windows to Ubuntu"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by mtfar on 2013-06-24
Hullo All. I have a medium size Construction company running on a Work Group system at our offices in Zambia. We have 15 users. Our business runs on programs I have written in MS Access. As there is no relative security with a Work Group I would like to move to Ubuntu. Before doing this there are obviously some questions that need to be considered. 1. Will QuickBooks 2012 run on Ubuntu? 2. Pastel Payroll run on Ubuntu? 3. How will I be able to run my Access programs on Ubuntu? 4. Do I need to purchase a proper server & if so where would I be able to get advice regarding this and the subsequent set up of the server. 5. Forseeable problems? 6. I live in Johannesburg SA.

---

### Post by zero2xiii on 2013-06-24
Hay,

Then I suggest you ask them? Otherwise we can not try and support you.

Thanks

---

### Post by mtfar on 2013-06-24
I assume your comment relates to QuickBooks & Pastel. I have investigated this but am hoping there would be usefull responses from the forum users that use the aforementioned programs. Furthermore I would also appreciate responses to the balance of my thread

---

### Post by ajgreeny on 2013-06-24
It doesn't look as if you will have much luck with recent versions of Quickbooks nor with any version of Pastel Payroll software running in wine, though some versions of MS Office will do so quite well.

You can search any windows applications running in wine using the [Wine Application DB]("http://appdb.winehq.org/") web-page.

---

### Post by JKyleOKC on 2013-06-24
For your questions 1, 2, and 3, keep in mind that NO Windows programs will run natively on Ubuntu or any other Linux system. Several ways to run them do exist, but none are fully satisfactory for non-technical-oriented users of the machines, and most of them reduce the security inherent in the architecture of Linux to that present in Windows.

Some, but not all, Windows programs can be run using "WINE" which attempts to duplicate the Windows environment within Linux. However the duplication is less than complete. Since Microsoft has been known to make extensive use of undocumented features in the past, I seriously doubt that your Access programs would all work properly under Wine -- but the only real way to find out would be to try it.

You can also use virtualization programs, such as VMWare Player or VirtualBox, create "virtual machines" with them, install Windows in those virtual machines, and then run your Windows programs -- but in your situation, this would seem to be going the long way around to gain absolutely no advantages. It does happen to be the way that I support my customers, who use Windows almost exclusively, but in my case each virtual machine is dedicated to a single purpose and is extremely limited in its capabilities. I would not consider trying to run my entire business within a single VM. For instance, I have one VM that simply runs QuickBooks for me and prints invoices that I can mail out. Another handles my software develoment needs, while a third has all the data recovery tools on which my business is based. Day to day operation, Email, and other such activity is handled by Xubuntu using native Linux programs rather than Windows versions.

I would recommend, in your case, simply hardening your Windows installation and staying with it (much as I dislike sending more money to Redmond). Any other approach is likely to result in disappointment, or worse...

---

### Post by Halpm on 2013-06-24
Wine HQ doesn't seem to think quickbooks will work. Found this thread with a guy who tried to get it to work. It's not encouraging: [http://forum.winehq.org/viewtopic.php?t=15596](http://forum.winehq.org/viewtopic.php?t=15596)
Pastel's products don't seem to fare much better.
You might want to see if there are any open source alternatives that can import/export the files? I have never used accounting software myself, so I can't point you anywhere specific, but I've used opensource office programs and music notation software alongside my windows and mac colleagues for a while now without any problems.

---

### Post by oldfred on 2013-06-24
I think Quickbooks is one of those that will mean you have to keep a Windows computer. But how many users are actually using Quickbooks? And how much per day?
In Linux there are some small accounting apps and very large complicated MRP/ERP type apps but either is a huge change and normally the accounting system you want is whatever your accountant uses. In USA the CPA comes in perhaps at end of month & end of year to review and use the reports. And in USA it almost always is Quickbooks for smaller systems.

I used MS Access a lot when working. I retired about 6 years ago and started using Linux. There is no real equivalent to Access in Linux. There are better sql tools and are better at multi-user access, but you have to then use a separate programming language and then another separate gui. Reporting writing is usually another add in to the programming language. Or it is not integrated and a huge learning curve. 
I have attempted just for my own knowledge to use python, qt4, and SQLite to appropriate Access and it does work, but took a lot to learn. Plus the tools to create the programs are another application which takes a bit to learn about.

---

### Post by snowpine on 2013-06-24
Welcome to the forums! Can you please clarify what you mean by the following statement?

> **mtfar said:**
> As there is no relative security with a Work Group I would like to move to Ubuntu.

Both Ubuntu and Windows can be secure (or insecure) depending on the skils of the person administering them. Do you have the expertise within your organization to set up and maintain a Linux deploy? (Or, for that matter, a Windows deploy?) If not, do you have access to consultants with this expertise? (and the money to pay them?) Or are you thinking this is something you can do yourself, and if so, what is your Linux experience?

You will have to weigh these important factors vs. other variables, such as the disruption of your company's work flow to migrate from Access/Quickbooks/Pastel to open-source alternatives.

---

