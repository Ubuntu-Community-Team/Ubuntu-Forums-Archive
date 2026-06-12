---
title: "ClamTK: How to use it"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by viriatovigo on 2013-04-01
I was working for more than 10 years with Panda but, unfortunately -so far-, they are not doing a version for Linux.

I did install ClamTK but I have not a clue what to do after it performs the scan. Panda did clear automatically all the threats that where* _real_* threats, and Panda scans** all **the system (thought takes 1 and a half hours to do it), but ClamTK only scans "Home" (so it takes 34 minutes to do it) and in the end does nothing, only tells me that it did find *14 threats*, but there are not threats because, for instance, considers a threat all my bank accounts (????????? never seen before on Trend Micro or Panda). The result is that now I can not be sure if the others are threats or they aren't and I don't dare to tick anything and sent it to quarantine because, as result, I am not confident what ClamTK means by "quarantine". I mean send to quarantine because is the solo option against the wide range of options in Panda.

Right... After the scan, What is supposed to do? If it does nothing when it finds what it calls "threats", It is going to happen the same when it finds a virus?  What to do if that happens?

With thanks in advance for your help,

Tino

---

### Post by Dave M on 2013-04-01
Hi,

Typically if ClamTk finds threats, it will pop open a new window where you can deal with them.   Is this window showing up?  Also, can you tell me what you mean by it does not consider them threats?  Can you tell me what threats it is showing you?

Thanks,
Dave M

---

### Post by monkeybrain2012 on 2013-04-01
Why do you want an antivirus? You don't need one for Ubuntu and other Linux OSes, it is an industry that springs up because of Windows. :)

---

### Post by DuckHook on 2013-04-01
It is highly unlikely that you have any "threats" at all on your box, and your anti-virus is only generating false positives. In general, I am strongly of the opinion that antivirus on Linux is not only a complete waste of time, but a practice that indulges falsehoods and delusions while distracting users from proper practices that provide true security. These forums are continually visited by users who waste enormous amounts of time and effort tracking down non-existent threats because their antivirus cried wolf, which leads them to neglect the practices that would really harden their installations against bad guys. I have dealt with a number of such threads myself, and the poor user is always off chasing invisible bogeymen while true security is ignored or not dealt with.

Please read the following sites/threads for proper security practices in Ubuntu.

For basic security:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

For advanced security:

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
all stickies in:
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)
in particular:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
and anything by gurus bodhi.zazen, Dangertux, Ms Daisy

I do not recommend advanced security until basic security has been read and implemented. However, the one common element in all security recommendations is, ***drop the antivirus***. It is a totally useless appendage and is like adding wings to a submarine.

---

### Post by deadflowr on 2013-04-01
You can scan the whole operating system with clam, not just the home folder.
You need to open the menu entry 'scan' (it's in the global menu; which sits in the left side of the top panel)
and choose a directory, or recursive scan (if you've set recursive scan in the preferences then you can just choose directory).
Then just look for file system in the left hand sidepane highlight and click ok.
If you want any directory you feel you don't want to scan, add it to the whitelist in the preference tab.

---

### Post by viriatovigo on 2013-04-02
Ta Dave M.
 

 Obviously I didn't explain me right. ClaimTK do considers threats that **are not** threats, like my bank accounts, so I can not trust its reports. I can not type here all the threats that it did find just now because they are **74**. I don't know how to attach the screen shots of the report but if you tell me how I have saved them.

 

 monkeybrain2012,
 

 Ubuntu page about anti virus doesn't agree with you.
 

 DuckHook,
 

 Really? &#8220;That&#8221; is not what ClaimTK says. Have a look to the answer to DaveM.  How do you call that? ClamTK is recommended by Ubuntu itself... So, Are you telling me that Ubuntu is cheating me? Last Friday were only 14 threats according to ClaimTK (recommended by Ubuntu) but today it says that there are **74 threats**... What? They were taken a Easter break from Friday to today?
 

 deadflowr,
 

 Thank you for going straight to the point; that is better. Thank you for teaching me how to use ClaimTK, one of my questions.  
 

 But, again, What to do after the scan? Because, as I said earlier, most of the threats are not threats at all (for instance considers threats my bank accounts...) so I am not confident in... in doing I don't know what to eliminate the real threats (if there is any in fact).

---

### Post by neruson on 2013-04-02
> **monkeybrain2012 said:**
> Why do you want an antivirus? You don't need one for Ubuntu and other Linux OSes, it is an industry that springs up because of Windows. :)

I dual boot with Windows and I use it to scan my Windows drive. I thought that was ClamAV's main purpose? There's not really enough linux virus's to warrant one designed for Linux and the few that do exist don't seem to ever get passed the Linux firewall anways. Although the virus's it will find that are designed to attack Windows won't do anything to our Linux machines. It's always good to remove them.

---

### Post by viriatovigo on 2013-04-02
Ta neruson.

Yes... the 90% use Windows, the 2% use Linus and the 6% use Mac and the other 2% is shared by other OSs so no, it si not worth to spend time and resources in something that has not market. Just few minutes ago Panda told me that they have none and they have not plans to make any.

The only thing that I can say is that if someone tries to make me believe that Linux is 100% safe to any hacker attack, he/she can also try to make me believe in Peter Pan and Santa Klaus...

Kind regards.

Tino

---

### Post by neruson on 2013-04-02
> **viriatovigo said:**
> The only thing that I can say is that if someone tries to make me believe that Linux is 100% safe to any hacker attack, he/she can also try to make me believe in Peter Pan and Santa Klaus...

Kind regards.

Tino

I was in no way implying that :) Any system can be hacked, but if your only using Linux and no other operating system all you really need is fine tuned firewall, but again if a good hacker REALLY wants in your system there's not really a whole lot you can do to stop them.

---

### Post by viriatovigo on 2013-04-02
Hi neruson.

Point taken... I am using only Ubuntu in this desktop and AppleMac in the laptop. I did uninstall every thing that smells Microsoft for good.

I am going to do what I told to deadflowr in few minutes.

All the best.

Tino

---

### Post by mastablasta on 2013-04-02
> **viriatovigo said:**
> 
 monkeybrain2012,
 

 Ubuntu page about anti virus doesn't agree with you.
 


what page are you talking about? 

they are communitry contributed pages but let's have a look at the one with the link to it: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
it says
> 2. do not install antivirus, as you *really* don't need it in Linux;unless you share files with Windows 

or perhaps you mean the antivirus page (which by the way lists other free antivirus options): [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
> 7. Linux virus infections are theoretically possible. 

theoretically because there is an idea of how the virus could be made, btu so far no one has made it. and why it is hard is explained here: [http://librenix.com/?inode=21](http://librenix.com/?inode=21)

in ubuntu the virus would need to break through firewall land on your maschine (perhaps this can be done via browser?) then it would need to knwo your user password in order to execute itself. how would it do that? in addition it would also need to hide itself and it owuld need to be contantly pached. like proabbly about every day or so. in short quite difficult. 

it is far more dangerous is if hacker tried to break to your maschine via browser or some programme langauge (like java). same browsers are used in windows and linux. they would then be after you bank account date. but again this can be solved with some steps to protect the browser and not allowing it to run scripts by default.


now assuming you are only scanning the drive because you are a good person and don't want to pass on a windows virus (which shouldn't be your problem but problem of people with microsoft) then why not use another alternative. clamTK is opensource but it's detection rate is not really that good if you check some reviews. avira though far from perfect and avast they both have decent detection rates. so they might give you less false positives.

---

### Post by DuckHook on 2013-04-02
> **viriatovigo said:**
> DuckHook,
 
 Really? &#8220;That&#8221; is not what ClaimTK says. Have a look to the answer to DaveM.  How do you call that? ClamTK is recommended by Ubuntu itself... So, Are you telling me that Ubuntu is cheating me? Last Friday were only 14 threats according to ClaimTK (recommended by Ubuntu) but today it says that there are **74 threats**... What? They were taken a Easter break from Friday to today?

No need to get upset. I was not trying to challenge you.

This is a community-based help forum, frequented by enthusiasts. You came on this forum seeking advice and we give the best advice we know, which, after all, is the whole point of giving advice. But, like all advice, you have the complete liberty and power to accept or reject the advice given. Linux is about doing what you want. It's your box; your choice.

To be fair, I did not just give you my opinion. I went to the trouble to include a list of sites that I thought would be useful and informative. Again, you are at liberty to ignore them.

Good luck and Happy Ubuntuing.

---

### Post by monkeybrain2012 on 2013-04-02
> **neruson said:**
> I dual boot with Windows and I use it to scan my Windows drive. I thought that was ClamAV's main purpose? There's not really enough linux virus's to warrant one designed for Linux and the few that do exist don't seem to ever get passed the Linux firewall anways. Although the virus's it will find that are designed to attack Windows won't do anything to our Linux machines. It's always good to remove them.

Why not just run Av on your Win partition? As far as AV goes Clam is poor anyway (only works for scanning email apparently) and it uses up resources,

---

### Post by monkeybrain2012 on 2013-04-02
> **viriatovigo said:**
> Ta Dave M.
 
 

 Ubuntu page about anti virus doesn't agree with you.
 

 .

How?

BTW, Clam only detects Windows viruses (in case you need to scan email or attachments before sending to Windows users etc) ,so even in the exceedingly  unlikely event where you have a Linux virus in the wild Clam wouldn't do  you any good.

---

### Post by Dave M on 2013-04-02
Hi,

If you have those bank reports in a particular directory, you could consider whitelisting that directory.  And if you can post a screenshot, please do.  Also, feel free to email me further questions - we'll sort it out.

Thanks,
Dave M

---

### Post by Dave M on 2013-04-02
> **monkeybrain2012 said:**
> How?

BTW, Clam only detects Windows viruses (in case you need to scan email or attachments before sending to Windows users etc) ,so even in the exceedingly  unlikely event where you have a Linux virus in the wild Clam wouldn't do  you any good.

That's not necessarily true.  The ClamAV team will write signatures for Linux threats as well.  If they're not, then submit a sample of malware to them so that they can in the future.

Thanks,
Dave M

---

### Post by Dave M on 2013-04-02
> **monkeybrain2012 said:**
> Why not just run Av on your Win partition? As far as AV goes Clam is poor anyway (only works for scanning email apparently) and it uses up resources,

No, ClamAV can scan regular files as well.  Also, ClamAV and ClamTk are "on-demand" scanners unless you do a lot of extra work to make them run ALL THE TIME - so, they're not using your resources unless you run them, like regular applications.

---

### Post by viriatovigo on 2013-04-04
Hi deadflowr.

Sorry about the delay in coming back to you but I was busy resolving another issues. I do apologize.

I did "Scan>Directory>File System" and did scan the full system. Thank you very much indeed for your lesson. It is very much appreciated.

It took about 2 hours and 15 minutes (more or less as Panda used to do) and found not viruses and 80 threats that I don't think that there are threats. Things like "JS.Obfxr-2" (a Java Script), "JS.Xored", "Heuristic.Encrypted.PDF", "PDF.EmbeddedJavaScript" and a lot of "PUA.HTML.Infected.WebPage-1".

I google it and I did find that I am not the only one with the same question and the answer was in the link [http://lurker.clamav.net/message/20100610.135112.6a602b37.en.html](http://lurker.clamav.net/message/20100610.135112.6a602b37.en.html). What it means I have not idea.

What is supposed to do now? ClaimTK only gives two options: Quarantine or Delete (Panda used to give more).

Kind regards.

Tino

---

### Post by viriatovigo on 2013-04-04
Sorry deadflowr.

I did find what means "defaced website" and it seems that I have a lot of hacker attacks. This never did happen with Panda, then -if it is correct- ClamTK is crap.

This is the link: [http://en.wikipedia.org/wiki/Website_defacement](http://en.wikipedia.org/wiki/Website_defacement)

Again, What to do next?

Kind regards.

Tino

---

### Post by deadflowr on 2013-04-04
> **viriatovigo said:**
> Hi deadflowr.

Sorry about the delay in coming back to you but I was busy resolving another issues. I do apologize.

I did "Scan>Directory>File System" and did scan the full system. Thank you very much indeed for your lesson. It is very much appreciated.

It took about 2 hours and 15 minutes (more or less as Panda used to do) and found not viruses and 80 threats that I don't think that there are threats. Things like "JS.Obfxr-2" (a Java Script), "JS.Xored", "Heuristic.Encrypted.PDF", "PDF.EmbeddedJavaScript" and a lot of "PUA.HTML.Infected.WebPage-1".

I google it and I did find that I am not the only one with the same question and the answer was in the link [http://lurker.clamav.net/message/20100610.135112.6a602b37.en.html](http://lurker.clamav.net/message/20100610.135112.6a602b37.en.html). What it means I have not idea.

What is supposed to do now? ClaimTK only gives two options: Quarantine or Delete (Panda used to give more).

Kind regards.

Tino

My advice was simply to help you understand how to scan with clam.
What clam outputs as a result is something you have to investigate, and sometimes take with a grain of salt.
Clam has been known to throw out false-positives for time to time.
But if in doubt about the files in question, quarantine.

---

### Post by viriatovigo on 2013-04-04
Ta deadflowr.

Good enough to me... Quarantine then.

I take the opportunity to apologise to every one for my burst of bad temper. 

Panda is a paid software and is on as soon as you start your PC, uses a cloud system and gets updated every hour so it stops every single threat as soon as it shows up, but ClaimTK is a **free** software, so I should had shut up my mouth.

The saying goes that as we get older we become child again and in my case seems that I am too advanced in that point... From the point of view of a lady I am a typical man, non sense complaining for everything. There is something worse than be a man: Being man, old and foreigner... and I have all the stakes...

All the best to every one and thank you for try to help me..

Tino

---

### Post by mastablasta on 2013-04-04
> **viriatovigo said:**
> 
Panda is a paid software and is on as soon as you start your PC, uses a cloud system and gets updated every hour so it stops every single threat as soon as it shows up, but ClaimTK is a **free** software, so I should had shut up my mouth.



as long as you keep in mind that you are only scanning for windows viruses with Panda or ClamTK.

---

