---
title: "Virus protection software"
date: 2013-12-15
forum: New to Ubuntu
---

### Post by msekkappan on 2013-12-15
Please recommend a virus protection software for Ubuntu.

---

### Post by Mark de J on 2013-12-15
You don't need a virus protection on Ubuntu. :)

---

### Post by mörgæs on 2013-12-15
Mark, if you want to help please provide not only your conclusion but also the reasoning behind.

---

### Post by BlinkinCat on 2013-12-15
This may be of interest to you -

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Also this - [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

Cheers - :P

---

### Post by 1clue on 2013-12-15
+1 on BlinkinCat's recommendations.

You don't need virus protection on Linux because the specific type of malware called a "virus" doesn't really apply to Linux.  However there are lots of other kinds of malware, and Linux is susceptible to enough of it.

One big problem with this sort of discussion is you started out using the word "virus".  You'll get all sorts of people yacking about "don't need virus protection" and "Linux can't get viruses" with no substance behind it.  You'll also get a good idea of the people who have never had malware ***that they knew of*** on their systems, and who did.  I've had more than one of my systems broken into, so you'll not get any of that from me.

My biggest recommendation is to view that BasicSecurity page though, so I guess that makes it a shorter discussion for me.

---

### Post by sammiev on 2013-12-15
Hi, If you share files and attachments between a Linux OS and Window computers I would suggest something like [Bitdefender]("http://linuxg.net/how-to-install-bitdefender-on-ubuntu-13-04-raring-ringtail-and-linux-mint-15-olivia/"). It's free. Few viruses affect Linux OS but will affect Windows. I would hate to think I could be affecting other computers like family and friends. There are other programs that work as well.

---

### Post by ben-magee on 2013-12-15
While it is true you generally don't need virus protection on Ubuntu, or other linux distributions, if you are sharing files (eg: on the internet, by flash drive) with a windows computer, you may want to consider installing an antivirus software such as ClamAV (available from the software centre, I think) - this allows you to scan for infected files: then even you can't "pass on" viruses either!

---

### Post by 1clue on 2013-12-15
The most common intrusion comes from the user not being careful and actually clicking somwhere to cause a problem.  It really has nothing to do with Linux and everything to do with social engineering.  You essentially are tricked into giving up valuable information, or tricked into thinking something is a legitimate app, or tricked because one of the "features" of an app you downloaded involves some sort of malware.

For example, you get an email which appears to be from your bank.  You click the link and log in, and suddenly the bad guys have your banking password.

Or you open an Excel spreadsheet, and the malware is embedded as a script inside the spreadsheet.  If your spreadsheet app understands Excel macros, then your linux box just executed that malware.  Susceptibility to the malware is inherent to compatibility with the Windows app.

Really, there's nothing you can do to combat this type of thing without significant education of the user.  You could avoid apps that can open documents from Windows-based apps, but that's not practical in the real world.  The same thing can be said for the types of malware Linux is actually susceptible to, you need to be an informed user and be careful.  It certainly doesn't hurt to install some intrusion detection software, configure it properly and then pay attention to the daily updates.  It also helps to go through security how-to's from whatever Linux vendor you're using.

---

### Post by SCBrisbane on 2014-01-08
"Virus" checkers generally check for a range of malware.

Most people in my organisation use Sophos.

ClamAV + common sense is the free option

---

### Post by monkeybrain20122 on 2014-01-08
> **1clue said:**
> 

Or you open an Excel spreadsheet, and the malware is embedded as a script inside the spreadsheet.  If your spreadsheet app understands Excel macros, then your linux box just executed that malware.  Susceptibility to the malware is inherent to compatibility with the Windows app.
.

By default Libreoffice doesn't execute embedded macros, you can configure it to execute macros only with explicit permission.

---

### Post by monkeybrain20122 on 2014-01-08
> **sammiev said:**
> Hi, If you share files and attachments between a Linux OS and Window computers I would suggest something like [Bitdefender]("http://linuxg.net/how-to-install-bitdefender-on-ubuntu-13-04-raring-ringtail-and-linux-mint-15-olivia/"). It's free. Few viruses affect Linux OS but will affect Windows. I would hate to think I could be affecting other computers like family and friends. There are other programs that work as well.

I would think that it would make more sense to have an AV on Windows' end if it is the OS the viruses target. 1) It is not my job to babysit Windows users 2) people who use Windows would need to have AV running anyway and cannot rely on people with whom they exchange files with occasionally to take care of security for them.

---

### Post by 1clue on 2014-01-08
> **monkeybrain20122 said:**
> By default Libreoffice doesn't execute embedded macros, you can configure it to execute macros only with explicit permission.

Yes, but that's one of many examples of software written for Linux which is designed to be "compatible" with Windows software.  As you said, the level of "compatibility" is configurable.  Everything about ... let's not call them viruses, but how about malware? ... is education and caution.  Even with the default setting you can tell Libre to execute the macro without looking at it, and you're owned.

Generally speaking, Linux isn't susceptible to too many attacks. But nothing can protect you from an ignorant user who takes the bait.  Especially when that user can execute with root authority.

---

### Post by sammiev on 2014-01-08
> **monkeybrain20122 said:**
> I would think that it would make more sense to have an AV on Windows' end if it is the OS the viruses target. 1) It is not my job to babysit Windows users 2) people who use Windows would need to have AV running anyway and cannot rely on people with whom they exchange files with occasionally to take care of security for them.

With the up most respect to friends and family members I will keep on using a virus checker.

---

