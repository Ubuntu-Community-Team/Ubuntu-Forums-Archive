---
title: "How to install .cfg file in terminal"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by karthik24 on 2015-06-12
Hi,

When I try to install.cfg file, it is getting errors in the terminal like no such commands. Tried with ./configure [Configuration file name]. Please provide me the commands to be used to execute the .cfg file in Ubuntu 12.04 LTS. *.cfg file can be open in text format and it has some valid data. When I tried to install on terminal, is shows that the command is not valid. So, it seems the commands are wrong. Please guide to use the right command to execute .cfg file. Is there any other ways to execute a .cfg file apart from terminal?

---

### Post by steeldriver on 2015-06-12
AFAIK there are no generic "commands to be used to execute the .cfg file" - you will need to be more specific about

[LIST]
[*]what software this .cfg file is part of 
[*]where you got it, and any installation instructions that you are following 
[*]the exact commands you are typing and the actual error message(s) that result 
[/LIST]

---

### Post by karthik24 on 2015-06-12
I'm trying to install Mcafee. Which I got as .tar.gz file. I downloaded this from internet and there is no instructions to install. When uncompress the tarball file. I got this .cfg file. When I try to open it, I can see just some links and no more. So, I tried to execute this .cfg file through terminal as like ./install. But it is not working.

---

### Post by SeijiSensei on 2015-06-12
I wouldn't give Mr. McAfee a penny given his [rather sordid past]("http://www.bbc.com/news/technology-24441931").

If you must have a commercial antivirus program, try [Kaspersky]("http://www.kaspersky.com/product-updates/linux-endpoint-security").  Download the .deb file and install it by double-clicking it or using "sudo dpkg -i /path/to/file.deb".

Personally I see no purpose in antivirus on Linux at all.  Never have used one, and never had an "infection" either.  If I were to use an antivirus program, I'd just install clamav from the Ubuntu repositories; it's free and open-source.

---

### Post by karthik24 on 2015-06-12
I'm trying to install McAfee on my friend's comupter for a study on the features of the product on vairous platforms and give a presentation. We need McAfee alone and no other AVs for this particular study.

---

### Post by wildmanne39 on 2015-06-12
> **SeijiSensei said:**
> I wouldn't give Mr. McAfee a penny given his [rather sordid past]("http://www.bbc.com/news/technology-24441931").

If you must have a commercial antivirus program, try [Kaspersky]("http://www.kaspersky.com/product-updates/linux-endpoint-security").  Download the .deb file and install it by double-clicking it or using "sudo dpkg -i /path/to/file.deb".

Personally I see no purpose in antivirus on Linux at all.  Never have used one, and never had an "infection" either.  If I were to use an antivirus program, I'd just install clamav from the Ubuntu repositories; it's free and open-source.
+1 I would stay away from McAvfee this is not windows, I personally do not use an antivirus, I have used clamav in the past but it just is not needed.

Antivirus is mainly needed for mail servers for example if you are going to be sending a lot of emails to window machines.

---

### Post by karthik24 on 2015-06-12
Thank you for your suggestion,But I would like to try the software. Any suggestion to execute a .cfg file please.

---

### Post by Lars Noodén on 2015-06-12
AV is not really needed on Ubuntu.  If you feel compelled to have one, ClamAV is better than its competitors according to some comparisons I've read.  That is easy to install because it is in the repository.  

As mentioned above, there are no generic instructions for configuration.  Each package has its own unique situation.  That is one of the reasons people recommend so strongly what's in the software center (repository) such as ClamAV.  Can you provide a link to the instructions you are following?  And a link to where you find the software.   Those two pieces of information are needed to help.

---

