---
title: "Anti-Virus"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by dimension123 on 2012-10-26
What are some good free anti-virus for Ubuntu? Or does Ubuntu not need an anti-virus?

---

### Post by Old_Grey_Wolf on 2012-10-26
If you share files with Microsoft Windows users, it is reasonable that you would want to remove malware from the files that you share with them. 

There are very few Linux malware threats at this time. That could change in the future. You may want to protect the Microsoft Windows users sharing files passing through your computer. Linux users can detect Microsoft Windows malware in files that we are sharing between Microsoft Windows users and remove the malware.

There are some malware/anti-virus vendors that support Linux; Avast, BitDefender, ClamAV, and AVG. There may be more of them that I am not familiar with.

---

### Post by kherring7383 on 2012-10-26
While there are plenty of free apps such as AVG and Avast on the web, I recommend that before you download and install one of these that check into it first since some require you to obtain a license from them before you can actually active it and on occasion you may have to update the licence from time to time. 

As an alternative, you could give clamav a try which is in the Ubuntu repository and can be installed with the following commands: 

sudo apt-get install clamav clamtk

Clamav is the actual antivirus app and clamtk is the GUI you can use to monitor it.

---

### Post by kaldor on 2012-10-26
> **dimension123 said:**
> What are some good free anti-virus for Ubuntu? Or does Ubuntu not need an anti-virus?

I've not used an anti-virus program since switching to Linux during Ubuntu 7.10. There's absolutely no reason to use it, and you'd only be doing it for the "peace of mind" aspect. However, you *do* need to be aware of trojans- don't install stuff from unknown sources or from those you do not trust. 

The case where it would be wise to use antivirus software would be when sharing files with Windows users. You would scan the files before sharing, but it'd be for their protection as opposed to your own.


Nutshell: Just be aware of what you're doing online and you've nothing to worry about :)

---

### Post by dimension123 on 2012-10-26
Thank you all for the great responses!

---

### Post by oldos2er on 2012-10-26
> **dimension123 said:**
> What are some good free anti-virus for Ubuntu? Or does Ubuntu not need an anti-virus?

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by offgridguy on 2012-10-26
I personally  don't use an anti-virus,  there are a couple of firewall options in the
software centre though that you might be interested in if you thought you needed it.

---

### Post by monkeybrain2012 on 2012-10-26
I don't use antivirus in Linux. If I share files with Windows users I assume they  have enough sense to install av on their ends so I don't really worry about that either.

---

### Post by jroa on 2012-10-27
I don't use antivirus with Ubuntu.  If I were downloading files or something that I intended to share with Windows computers, I might consider it.  But I have been safely surfing the internet for years without any problems.

Also, antivirus just does not feel the same as unprotected surfing.

---

### Post by lisati on 2012-10-27
I have clamav scan incoming and outgoing emails on my server, partly because I interact with Windows users, and partly because it helps make my ISP happier about me running an email server at home. Other than that, I'm not overly worried: I'm not obliged to open files from strangers.

---

### Post by vibaviattigala on 2012-10-27
its much rare to see a virus infected by a linux desktop so i think its useless to get a AV becasue most of ubuntu AV searches for windows viruses which wont work in ubuntu desktop nad AV uses much of ur ram for no reason which is hard to detect virus

---

### Post by offgridguy on 2012-10-27
You might take a look at this.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

