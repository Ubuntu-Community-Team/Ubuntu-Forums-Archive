---
title: "do I need an antivirus?"
date: 2008-11-04
forum: Recurring Discussions
---

### Post by maheshjr2000 on 2008-11-04
Hi sorry for the obvious question but I have only used ubuntu and other linux distros as backup and recovery partitions. For day in day out use do I actually need an antivirus?

---

### Post by aktiwers on 2008-11-04
Not really..
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by crazypenguin2008 on 2008-11-04
your protected by iptables....

---

### Post by hyper_ch on 2008-11-04
Generally, you don't need antivirus. Please seach this forum, especially the security part, for more info.

> **crazypenguin2008 said:**
> your protected by iptables....
How would iptables protect against viruses? Furthermore, by default, iptables filters nothing.

---

### Post by wizard10000 on 2008-11-04
> **maheshjr2000 said:**
> Hi sorry for the obvious question but I have only used ubuntu and other linux distros as backup and recovery partitions. For day in day out use do I actually need an antivirus?

I'm gonna depart from popular opinion and say yes, you should have an antivirus package.

Although you may never catch a virus on your Linux machine there's nothing keeping you from transferring a virus from Linux to Windows.  Let's look at this scenario -

1.  maheshjr2000 receives an email with an infected attachment, which doesn't affect his Linux machine at all, but -

2.  Not knowing the file is infected, maheshjr2000 forwards the email to a friend with a Windows machine.

That said, I run clamav on all my Linux installations just so I don't inadvertently infect someone's Windows box.  I think it's part of responsible computing.

---

### Post by philinux on 2008-11-04
You're protected by the fact that the virus would need your permission/password to even install itself.
It would have to be a linux virus too.

---

### Post by Bios Element on 2008-11-04
> **wizard10000 said:**
> I'm gonna depart from popular opinion and say yes, you should have an antivirus package.

Although you may never catch a virus on your Linux machine there's nothing keeping you from transferring a virus from Linux to Windows.  Let's look at this scenario -

1.  maheshjr2000 receives an email with an infected attachment, which doesn't affect his Linux machine at all, but -

2.  Not knowing the file is infected, maheshjr2000 forwards the email to a friend with a Windows machine.

That said, I run clamav on all my Linux installations just so I don't inadvertently infect someone's Windows box.  I think it's part of responsible computing.

No you do not **_need_** a virus. I'm gonna be mean and evil here and say this. If a Windows user gets infected tough luck! Sucks to be an idiot. No doubt most will disagree but Another win user getting a virus is simply not my problem. No point wasting time and system resources on an antivirus that will do me, myself and I absolutely no good.

Short answer: Do not install an anti-virus unless you want to waste system resources on virus scanning which is #1 pointless and #2 not your problem.

---

### Post by hyper_ch on 2008-11-04
> **wizard10000 said:**
> 1.  maheshjr2000 receives an email with an infected attachment, which doesn't affect his Linux machine at all, but -

2.  Not knowing the file is infected, maheshjr2000 forwards the email to a friend with a Windows machine.
So if that friend is not running antivirus or not up-to-date antivirus on his windows box, what do you think is more likely:

(a) that it is just YOU who send him the virus and he gets infected by it
or
(b) that someone else he knows will send him the virus?

---

### Post by Saint Angeles on 2008-11-04
> **Bios Element said:**
> No you do not **_need_** a virus... [snip]
i don't think anybody here disagrees with that statement

---

### Post by wizard10000 on 2008-11-04
> **hyper_ch said:**
> So if that friend is not running antivirus or not up-to-date antivirus on his windows box, what do you think is more likely:

(a) that it is just YOU who send him the virus and he gets infected by it
or
(b) that someone else he knows will send him the virus?

I'm not worried about what someone else sends, only about what *I* send  ;)

And to address Bios Element's comment on system resources - clamav on my machine only takes up about 500k of memory and no processor resources unless it's actively scanning, which I do as a cron job in the middle of the night.

---

### Post by wizard10000 on 2008-11-04
> **Saint Angeles said:**
> i don't think anybody here disagrees with that statement

:lolflag:

---

### Post by overdrank on 2008-11-04
> **maheshjr2000 said:**
> Hi sorry for the obvious question but I have only used ubuntu and other linux distros as backup and recovery partitions. For day in day out use do I actually need an antivirus?
Hi and welcome, I will add to the others 
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

> **Bios Element said:**
>  Sucks to be an idiot. No doubt most will disagree but Another win user getting a virus is simply not my problem. 


A little Harsh do you think? ;)

---

### Post by Haris-MV on 2008-11-04
err thats so cool :) we do not need a anti virus

---

### Post by Dan_Dranath999 on 2008-11-04
i suppose, in some cases, it would be more efficient, to scan windows partitions from the "outside"

---

### Post by candtalan on 2008-11-04
The link in the previous response is worth reading. (the psychocats link that is)

I trust that you use a router (cabled or wireless)? It gives a useful measure of protection. If you use wireless, there are some security factors which are worth researching and considering carefully.

Even if your installation had a virus installed, it would be quite hard for it to spread to other linux machines. Generally a user-entered password would be needed at each machine. Also most users install only from the central repository, which is administered by people you trust. So - the linux environment is an infertile one for such things as viruses and also malware.

A strong precaution against malware also exists because open source code is available to be examined in detail - by yourself if you like, or by someone else.

Non open source code, as proprietary code usually is, can contain literally anything - what the vendor intended (be afraid) and also what was not intended - all secret.   :-)

hth

---

### Post by maheshjr2000 on 2008-11-04
Thanks for all the help guys! :D As for my wireless security I just increased my wireless password to 18 mixed characters.

Edit: WPA2 not WEP

---

### Post by surelock22 on 2008-11-04
Are you more open for virus' if you use Windows through VirtualBox? My brain can't grasp the concept of what a VM actually is......

---

### Post by wizard10000 on 2008-11-04
> **surelock22 said:**
> Are you more open for virus' if you use Windows through VirtualBox? My brain can't grasp the concept of what a VM actually is......

The VM is about as easy to infect as a standalone Windows machine but a Windows virus won't affect the host Linux system.  There's nothing to stop the Windows VM from sending out nasties over teh intrawebz unless the VM has its own virus scanner.

---

### Post by Coolride on 2008-11-04
Yes, i got a trojan in less than 20 minutes surfing gaming websites, my machine started acting funny by the end of the day. So I downloaded Avast, and sure enough, it's what reminds me of Microsoft all over again. I removed the bug ,and it went back to normal again.If I could remember the site , I'd send all the non believers over there, so they could see for themselves.

---

### Post by DexterLB on 2008-11-04
> **Bios Element said:**
> No you do not **_need_** a virus. I'm gonna be mean and evil here and say this. If a Windows user gets infected tough luck! Sucks to be an idiot. No doubt most will disagree but Another win user getting a virus is simply not my problem. No point wasting time and system resources on an antivirus that will do me, myself and I absolutely no good.

Short answer: Do not install an anti-virus unless you want to waste system resources on virus scanning which is #1 pointless and #2 not your problem.
I totally agree!

---

### Post by Interpreter on 2008-11-04
"watchu talkin 'bout man?"

---

### Post by handydan918 on 2008-11-04
> **wizard10000 said:**
> The VM is about as easy to infect as a standalone Windows machine but a Windows virus won't affect the host Linux system.  There's nothing to stop the Windows VM from sending out nasties over teh intrawebz unless the VM has its own virus scanner.

True enough, but with a VM, you can take a snapshot of the guest system and restore it to it's pre-infection condition anytime. 
It's almost enough to make windows useful again.


Almost.

---

### Post by RequinB4 on 2008-11-04
I think one thing that there are two things that haven't been mentioned.

First, anti-virus is not really anti-virus - it is virus-checking. AV works (for 99.999% of the time, there are exceptions) by comparing files or parts of files to known patterns of virus interaction. Since there have been, what, 10 known viruses that will affect a GNU/linux desktop, and none of them running in the wild, the question "should we be vigilant and not be cocky about our virus protection?" is irrelevent because until someone makes a sucessful virus for GNU/Linux there isn't much to check.

Second, there is the beleif that we should run AV to protect those we contact via the internet getting infected. Assuming we're not talking about a mail or SAMBA server or something, let's think about this for a second - what are the possible outcomes?

1) Linux box doesn't get a virus. No problem.

2) Linux box gets a virus, and doesn't transmit it. No harm done, maybe a few wasted bytes of space.

3) Linux box gets a virus, and transfers it to a Windows box, and the Windows box has equivalent or better anti-virus. They don't get infected, so no harm done.

4) Linux box gets a virus, and transfers it to a Windows box, and the Windows box doesn't have antivirus or it fails to detect. Windows user is very sad.

So, let's examine 4. Since the box doesn't have antivirus, and has an open connection to the internet, and (for the sake of argument) is running unsafe applications such as IE or Outlook, its security is already very low. In fact, it's far, far, far more likely that they get the virus not from you but from normal browsing or from ANOTHER windows box which is ACTIVELY propagating the virus. Add the fact that the probability of 1, 2, and 3 is also MUCH higher than 4, and you begin to see my point.

So you must ask yourself - By running AV on your GNU/Linux desktop, are you protecting against the VERY unlikely, or just delaying the inevitable?

---

### Post by Hyper Tails on 2008-11-04
You can get an anti-virus for linux called clamtk

you can download it in the add-remove invatory

I have it installed

I managed to get a virus on my computer

most ever: 3

it's simple to use

---

### Post by DoubleMcLovin on 2008-11-04
> **wizard10000 said:**
> The VM is about as easy to infect as a standalone Windows machine but a Windows virus won't affect the host Linux system.  There's nothing to stop the Windows VM from sending out nasties over teh intrawebz unless the VM has its own virus scanner.
On a note for this, VM's can be configured to reload the windows install and all files there of to a certain set point. 
EX: I install windows, configure my favorite windows programs and games, and create a restore point. Regardless of virus activity my computer will revert to this save every night and remove all active viruses.

---

### Post by Stan% on 2008-11-04
> **DoubleMcLovin said:**
> On a note for this, VM's can be configured to reload the windows install and all files there of to a certain set point. 
EX: I install windows, configure my favorite windows programs and games, and create a restore point. Regardless of virus activity my computer will revert to this save every night and remove all active viruses.

Unless the virus infects the restore folder. Am I right about that?:confused: I know nothing of VM's.

---

### Post by stalkingwolf on 2008-11-04
This is MY take on this issue.  I have an anti virus installed on my system.
WHY?  Because **I** work on other peoples computers.  The most common for me "repair" I do is Virus removal ( the record to date is 175).  I can stick
their HDD in as a slave/external and scan it several different ways with out threat to MY system.

In todays world most people use some form of standalone email client.  Then there are those that use web based email clients. Then there are those uninitiated/uneducated ones that use outlook.  The ones that use web based and standalone clients have the advantage of their apps usually using some type of "washer" app.  As far as I am concerned anyone that uses outlook
and doesnt have an updated anti virus and some form of email washer is just
"**PLUMB DUMB**" and should be banished to a Texas Insturments word Processor.

---

### Post by surelock22 on 2008-11-04
> **handydan918 said:**
> True enough, but with a VM, you can take a snapshot of the guest system and restore it to it's pre-infection condition anytime. 
It's almost enough to make windows useful again.


Almost.

So THAT'S what a snapshot is!!! :kneeslap:

Ok, let me ask another dumb question then: can i get a virus easier if i use the IE tab on FireFox in VB than using IE by itself, or does it not matter anyways? From what I've just read about that snapshot feature, that seems like my ticket to making sure I don't keep a virus. I'll just snapshot after every install check for infection periodically through trendmicro and snapshot back to pre-infection if there's ever a problem.

---

### Post by cardinals_fan on 2008-11-04
Antivirus has extremely limited value on any OS.

---

### Post by ranch hand on 2008-11-07
YES!!  You need to worry about virus.  You should wash your hands regularly and try to avoid close contact with humanity.

As for passing a virus to Windows users, I would not be to concerned.  Most ISPs have excellent virus screening so not only are you unlikely to receive one, you are even more unlikely to pass one as it passes through your ISP and theirs.

Besides that, I have used windows up until last month (when it just got to be too much) and was infected once in the the last decade through using IE instead of Netscape to deal with a site that we had to access.  Being paranoid, I scanned right after the transaction and cleared it then.  There is no way to protect a computer from the user and that is the source of most problems.

---

### Post by oldsoundguy on 2008-11-07
As a person that repairs a Windows computer now and then for friends, virus files are really the least of the problems now days.  Keyloggers, Trojans, Spyware and Spybots, browser hijackers, Smit Fraud items, root kits are the major items of infection and most Anti Virus programs do not deal with them at all.  If you are going to run a VM that is open to the world, protection from those items is a must to protect others .. AND YOURSELF from the phone home programs that will phone home the moment you go on line with something Windows.  Meanwhile your Linux partition will remain unharmed.

---

### Post by cardinals_fan on 2008-11-07
> **oldsoundguy said:**
> As a person that repairs a Windows computer now and then for friends, virus files are really the least of the problems now days.  Keyloggers, Trojans, Spyware and Spybots, browser hijackers, Smit Fraud items, root kits are the major items of infection and most Anti Virus programs do not deal with them at all.  If you are going to run a VM that is open to the world, protection from those items is a must to protect others .. AND YOURSELF from the phone home programs that will phone home the moment you go on line with something Windows.  Meanwhile your Linux partition will remain unharmed.
...which is why anti* programs are useless.  Intelligent browsing and common sense are all that you need.

---

### Post by aysiu on 2008-11-08
> **cardinals_fan said:**
> ...which is why anti* programs are useless.  Intelligent browsing and common sense are all that you need.
A proper permissions separation wouldn't hurt either.

---

### Post by cardinals_fan on 2008-11-08
> **aysiu said:**
> A proper permissions separation wouldn't hurt either.
Definitely true in order to prevent botnets, but not necessarily useful for preventing malicious damage.  Most people keep their documents in their home directories on any OS, and they can be wiped easily.

---

### Post by Interpreter on 2008-11-08
True that, but then I'd like to throw in that there's been that change from "gotcha viruses" to "secret hidden zombie machine-viruses/trojans/stasispywhatevercamoflage-dangers"that don't even try to touch or delete your home-data.
That being said you're right, doesn't change the fact that we all want our data to be safe.

---

### Post by aysiu on 2008-11-08
> **cardinals_fan said:**
> Definitely true in order to prevent botnets, but not necessarily useful for preventing malicious damage.  Most people keep their documents in their home directories on any OS, and they can be wiped easily.
Yes, all personal files should be backed up, but if the personal and system files are kept separate, it's a lot easier to "clean up" if there's any kind of infiltration (delete the limited user account, create a new one, copy the personal files from back up; instead of reinstall the entire system and all the accompanying programs and then create a new user and copy the personal files from backup).

In Ubuntu, reinstallation isn't that much of a chore, but in Windows it can take 4 to 10 hours of your time.

---

