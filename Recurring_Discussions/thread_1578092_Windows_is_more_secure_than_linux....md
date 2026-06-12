---
title: "Windows is more secure than linux...?"
date: 2010-09-19
forum: Recurring Discussions
---

### Post by raafaell on 2010-09-19
Executive Summary

Much ado has been made about whether or not Linux is truly more secure than Windows. We compared Windows vs. Linux by examining the following metrics in the 40 most recent patches/vulnerabilities listed for Microsoft Windows Server 2003 vs. Red Hat Enterprise Linux AS v.3:

   1. The severity of security vulnerabilities, derived from the following metrics:
         1. damage potential (how much damage is possible?)
         2. exploitation potential (how easy is it to exploit?)
         3. exposure potential (what kind of access is necessary to exploit the vulnerability?)
   2. The number of critically severe vulnerabilities

The results were not unexpected. Even by Microsoft&#8217;s subjective and flawed standards, fully 38% of the most recent patches address flaws that Microsoft ranks as Critical. Only 10% of Red Hat&#8217;s patches and alerts address flaws of Critical severity. These results are easily demonstrated to be generous to Microsoft and arguably harsh with Red Hat, since the above results are based on Microsoft&#8217;s ratings rather than our more stringent application of the security metrics. If we were to apply our own metrics, it would increase the number of Critical flaws in Windows Server 2003 to 50%.

We queried the United States Computer Emergency Readiness Team (CERT) database, and the CERT data confirms our conclusions by a more dramatic margin. When we queried the database to present results in order of severity from most critical to least critical, 39 of the first 40 entries in the CERT database for Windows are rated above the CERT threshold for a severe alert. Only three of the first 40 entries were above the threshold when we queried the database about Red Hat. When we queried the CERT database about Linux, only 6 of the first 40 entries were above the threshold.

Consider also that both the Red Hat and Linux lists include flaws in software that runs on Windows, which means these flaws apply to both Linux and Windows. None of the alerts associated with Windows affect software that runs on Linux.

So why have there been so many credible-sounding claims to the contrary, that Linux is actually less secure than Windows? There are glaring logical holes in the reasoning behind the conclusion that Linux is less secure. It takes only a little scrutiny to debunk the myths and logical errors behind the following oft-repeated axioms:

   1. Windows only suffers so many attacks because there are more Windows installations than Linux, therefore Linux would be just as vulnerable if it had as many installations
   2. Open source is inherently less secure because malicious hackers can find flaws more easily
   3. There are more security alerts for Linux than for Windows, **therefore Linux is less secure than Windows**
   4. There is a longer time between the discovery of a flaw and a patch for the flaw with Linux than with Windows...

Full Article: [here]("http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/")

I was reading this and stopped to see what you guys think about it,
Is windows really more secure than Linux? :confused:

What do you think?


Thanks

---

### Post by Rasa1111 on 2010-09-19
I think..
 not a chance. 

> **So why have there been so many credible-sounding claims to the contrary, that Linux is actually less secure than Windows?** There are glaring logical holes in the reasoning behind the conclusion that Linux is less secure. It takes only a little scrutiny to debunk the myths and logical errors behind the following oft-repeated axioms:

 One , simple answer... Money. 
MS are known to be shady as hell, in any way they possibly can. 

No surprise here.

 thanks for the post..
 interesting..

---

### Post by raafaell on 2010-09-19
> **Rasa1111 said:**
> 
 One , simple answer... Money. 


I agree with you, but the article made sense after saying that open-source is easier to the bad guys to find cracks, I use Linux as my only and great OS, and hopefully we can and will prove that this article is wrong!

---

### Post by inameiname on 2010-09-19
The thing about Linux being easier to crack because it's open-source, negating the far less number of people using it, is why would most hackers bother? Linux is free, and it's code is open-source, and there isn't much need to 'crack' anything. Of course, there are always some folks who do, but in general, the fact that it's easier to crack doesn't really mean much. On the other hand, Windows stuff is closed-source, and is certainly not free, so of course there is far more of a desire to 'crack' things with it, regardless of whether it's more secure or less secure.

---

### Post by Sef on 2010-09-19
Nothing new about this discussion.

> 1.Windows only suffers so many attacks because there are more Windows installations than Linux, therefore Linux would be just as vulnerable if it had as many installations
2. Open source is inherently less secure because malicious hackers can find flaws more easily
3. There are more security alerts for Linux than for Windows, therefore Linux is less secure than Windows
4. There is a longer time between the discovery of a flaw and a patch for the flaw with Linux than with Windows...

Locked for FUD. 

1) So why are 2/3 of the web servers open source, but the majority of attacks still against Windows web servers?

2) Says who?  Hackers have no trouble finding flaws in closed source.

3)Not necessarily true.  If Windows problems are unreported that do not mean that they do not exist.

4) Source?

---

### Post by inameiname on 2010-09-19
Indeed. ;)

---

### Post by srs5694 on 2010-09-19
> **raafaell said:**
> I agree with you, but the article made sense after saying that open-source is easier to the bad guys to find cracks, I use Linux as my only and great OS, and hopefully we can and will prove that this article is wrong!

I've only skimmed parts of the article, and read the part you quoted, but I think you're misinterpreting it. The article was written to *refute* the claim that Windows is more secure than Linux. It repeats claims that Windows is more secure, but clearly labels them as "myths" and then describes why they're untrue (in the author's opinion).

Furthermore, the article is extremely old by the standards of computer security: It was written in 2004. At that time, Windows XP was current, and Ubuntu was brand-new (released the same month as the article, in fact). IMHO, there's no point in discussing the specifics in the article unless you're interested in computer history.

---

