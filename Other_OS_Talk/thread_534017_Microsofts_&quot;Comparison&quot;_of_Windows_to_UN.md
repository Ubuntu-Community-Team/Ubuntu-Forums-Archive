---
title: "Microsofts &quot;Comparison&quot; of Windows to UNIX"
date: 2007-08-24
forum: Other OS Talk
---

### Post by toupeiro on 2007-08-24
Ok, I'm gonna rant a little bit here, but hopefully these rantings end up making people think twice about reading crap like this. :-D

I read a [full page]("http://www.microsoft.com/windowsserver/compare/compare_linux.mspx") of microsoft jargon trying to convince companies and admins in the position of choice for their server platform to use windows.  This was of the following excerpts were my favorites:

> Over the first 650 days of product life for Windows Server 2003, Red Hat Enterprise Linux 3, and Red Hat Enterprise Linux 4, Windows Server 2003 had 75 percent fewer published vulnerabilities.

&#8220;Although it&#8217;s still often used as an argument, it seems quite clear to me that the &#8220;many eyes&#8221; argument, when applied to security, is not true.&#8221;

 
Ok, I call foul.  Microsoft, show me ONE CASE of a worldwide virus epidemic that catastrophically brought down Redhat servers and Oracle Databases in the way they have with MSSQL and Server 2003.  Show me  one incident where a patch from redhat or any other vendor FORCED A REBOOT ON ALL PRODUCTION BOXES, costing the company millions.  Microsoft has little room to talk about vulnerabilities.  THe key thing here that they said is PUBLISHED vulnerabilities.  "many eyes" means better patching, and in some cases more frequent patching, but overall a more secure environment.  Windows, however, is subject to what their lab rats find out in an unreal world environment, or what their customers report to them AFTER it already cost them productivity and money in addition to what they've already paid.

Lets also not forget, up until very recently, Windows Server was not in the 64-bit game.  It couldn't hold a candle to linux on a technical computing level.  It taps out at 4GB of RAM, and swaps to disk WELL before that.  It's bloated code takes up valuable memory that could be used for computing, but has to be used instead to support itself idling.  and as far as subscription costs in redhat, let us not forget one more thing, Microsoft licenses its OS by CAL, and typically server 2003 gives you 3-5 CAL's..  Linux, however, is not licensed by such nonsense.  They are actually comparing Server 2003 to RHEL3 and RHEl4 AS which is absurd, windows cannot even scale to the level of RHEL3 and RHEL4 ES which is SIGNIFICANTLY cheaper than AS.  If you want to talk about license costs, why don't you analyze their terminal services costs or the concurrent client connection costs of windows to those of Linux?  Then, figure in microsofts server licensing costs for small and medium sized businesses compared to the appropriate RedHat server version that small and medium sized business would deploy. (ES).   Unless you plan on having more than 2 physical processors in your server, RHEL4 AS is not the choice for you, and neither is Server 2003 standard.  You have to buy ENTERPRISE for that, so if you want a fair apples to apples comparison, compare 2k3 Enterprise to rhel4 AS and see if Micro$oft is still a cheaper option.

Windows is outscaled, overpriced, and overblown.    There are some things tailored for windows still because of the longivity of their dominance, but to say they are a better choice today is a hard thing for me to swallow.

*gets off podium* :-D

---

### Post by Sp4cedOut on 2007-08-24
They didn't say less viruses, they said less vulnerabilities.

---

### Post by dulbirakan on 2007-08-24
See this : [http://blogs.zdnet.com/microsoft/?p=670]("http://blogs.zdnet.com/microsoft/?p=670")


Quoting from that: Recently, it came to light that Microsoft tried to influence some of the analysts it hired to perform studies in 2002 comparing Windows and Linux to portray Microsoft offerings in a more favorable light. Microsoft&#8217;s whole policy of sponsoring analysts to conduct studies comparing its products to open-source ones &#8212; which many company observers believed would naturally show Microsoft products and strategies to be superior &#8212; had been a bone of contention since the site launched at the start of this decade.

There has also been some debate on Slashdot on this topic a few months back. The methodology employed by Microshaft in their research is scientificaly flawed. All M$ ever does is double speaking and stating half truths...

---

### Post by aussiedini on 2007-08-24
My thoughts...if you were about to ship a new version of server, as MS is, why would you bother fixing vulnerablities anyway. As we all know MS support drops off dramatically over time.....got to sell the new product. Also they are quite lax at releasing what they see as minor vulnerabilities anyway. If its a major flaw, that makes them look stupid, yes they will, but otherwise they wait for a patchday.

---

### Post by juxtaposed on 2007-08-24
Heh. Windows exists to make money. Linux exists to make a great OS. Microsoft will twist the truth until it isn't the truth anymore, everyone knows it. Anyone who would trust microsoft deserves their server to be running windows.

---

### Post by toupeiro on 2007-08-24
> **Sp4cedOut said:**
> They didn't say less viruses, they said less vulnerabilities.

lol, you're right!  Damn, my bad.  I'm one of those crazy people who think those two things are synonymous. hehe

---

### Post by jacob01 on 2007-08-24
im not recommending it since Microsoft wont give any thing to the open source community but what Microsoft should do is make a linux Microsoft hybrid operating system  ms can learn a lot from the open source developers and the thing is is that Microsoft is making so much money of their operating systems that are not secure as  the open source operating systems that cost not even half as much 

and don't say you get better support through a phone tech that a community run irc forum or what ever 

i have had better support through the community than through a big company that that offers support 


ms better get patching to catch up

---

### Post by jacob01 on 2007-08-24
> **juxtaposed said:**
> Heh. Windows exists to make money. Linux exists to make a great OS. Microsoft will twist the truth until it isn't the truth anymore, everyone knows it. Anyone who would trust microsoft deserves their server to be running windows.

yea

---

### Post by Dark Star on 2007-08-26
Get the Facts was one of Microsoft’s advertising campaigns, launched in 2004 as a website and its main role was to encourage users to switch from Linux to Windows Server System. The site provided case studies and other related materials; they’ve initially compared the TCO of Linux to Windows, but later the company has also featured comparisons regarding reliability, security and interoperability.

At that
time, Microsoft claimed its products had a lower overall TCO than open source programs, due to its ease of use. Also known as an "anti-Linux campaign", the Get the facts website stirred lots of controversies so far. There were lots of people who claimed Microsoft has actually bribed some analysts to compare Windows software with Linux software and to put Microsoft’s products in a better light.

However, for unknown reasons, the Redmond company decided to close the Get the factswebsite. Some claim this might be at the suggestion of MS’s partners from the open source world, such as Novell, Xandros, Linspire, SugarCRM, XenSource. Actually, MS didn’t close the website, that is it didn’t put an end to the charade, they rather replaced it with something else. The brand new Windows Server Compare website resumes to relate the Micro$oft software only to Red Hat’s. Is this because Red Hat Linux is one of the distributors that keeps on refusing a patent-protection agreement with Microsoft? Who knows … (hint: Microsoft).

As Mary Jo Foley writes in her Microsoft kills its ‘Get the Facts’ anti-Linux site, Ryan Gavin, director of Platform Strategy with MS, claimed they’ve come to the decision to close the website due to the following reasons:

> "Customers have increasingly asked for not only credible 3rd party information from other customers and industry experts, but also for Microsoft’s perspective on platform decisions as a key technology partner. Customers want to consume this information in a variety of formats - from short Q&A to more in-depth business cases - from videos and podcasts to research reports. Compare was designed with these requirements in mind - to provide in-depth information about how Windows, Linux, UNIX and Mainframe stack up along key attributes. Given that the /compare site will provide 3rd party information, Get the Facts will be retired as a destination." 

Links :[ Server Compare Site]("http://www.microsoft.com/windowsserver/compare/compare_linux.mspx")
Source :[ Zdnet]("http://blogs.zdnet.com/microsoft/?p=670")

---

