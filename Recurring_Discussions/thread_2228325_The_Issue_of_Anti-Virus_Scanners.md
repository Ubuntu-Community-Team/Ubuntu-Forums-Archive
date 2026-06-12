---
title: "The Issue of Anti-Virus Scanners"
date: 2014-06-06
forum: Recurring Discussions
---

### Post by Jonny87 on 2014-06-06
I will start by stating that I am not a novice user to Linux and so this not a direct question of naivety from someone that doesn't understand Linux. I have never really run my linux systems with a virus scanner as I have always been of the belief that Linux doesn't need it, unless it's to scan file that could potentially infect a windows computer.

Though I'm wondering what other users think of this claim from Comodo regarding their Anti-Virus for Linux;
> **Does Linux require an anti-virus?**
Definitely. It used to be the case that Linux was  not heavily targeted by malware writers for two main reasons. Firstly,  the general popularity of Linux amongst home users wasn't very high.  This meant hackers had a low number of potential victims and hence a low  'return on investment' for their efforts.                      It was always far more lucrative to attack Windows because of its  large user base. Secondly, the fact that there are many variations  (distributions) of the Linux OS meant virus programmers would have to  create and test separate attack code for each of them.                       Compare this to Windows where a single virus code is capable of  infecting everybody that uses the operating system.                       In the past few years, however, both these points have been  eroded. Firstly, there is a general increase in the popularity of the OS  with more and more home users adopting Linux.                      The fact that major computer distributors like Dell are shipping  desktops and laptops with Linux per-installed is testament to this  shift. Secondly, the run-away popularity of easy-to-use distributions  like Ubuntu has consolidated the fragmented Linux user base.                       Unfortunately, this makes it easier for hackers to create a  single piece of virus code that will hit millions of users.

[http://www.comodo.com/home/internet-security/antivirus-for-linux.php?tc=1&key5sk1=eb9534ba8c68a61b991c4a86a37e4b97a73ddf84&key5sk2=2128&key5sk3=1402097789000&key5sk26=&key5sk27=1402097078000&key5sk28=2720&key5sk29=1402097800000&key5sk30=2720&key5sk31=1402097819000&key6sk1=&key6sk2=FF290&key6sk3=8&key6sk4=en-us&key6sk5=AU&key6sk6=1&key6sk7=http%3A%2F%2Fwww.comodo.com%2F&key6sk8=112202&key6sk9=1366768&key6sk10=false&key6sk11=d9a88c1960c3acc1eeb3ce201f925824e696d953&key6sk12=2035&key7sk1=2&key7sk2=19&key1sk1=dt&key1sk2=http%3A%2F%2Fwww.comodo.com%2F](http://www.comodo.com/home/internet-security/antivirus-for-linux.php?tc=1&key5sk1=eb9534ba8c68a61b991c4a86a37e4b97a73ddf84&key5sk2=2128&key5sk3=1402097789000&key5sk26=&key5sk27=1402097078000&key5sk28=2720&key5sk29=1402097800000&key5sk30=2720&key5sk31=1402097819000&key6sk1=&key6sk2=FF290&key6sk3=8&key6sk4=en-us&key6sk5=AU&key6sk6=1&key6sk7=http%3A%2F%2Fwww.comodo.com%2F&key6sk8=112202&key6sk9=1366768&key6sk10=false&key6sk11=d9a88c1960c3acc1eeb3ce201f925824e696d953&key6sk12=2035&key7sk1=2&key7sk2=19&key1sk1=dt&key1sk2=http%3A%2F%2Fwww.comodo.com%2F)
Under "Frequent Questions"

I'm interested to know what are the opinions of other seasoned Linux Admins and Users out there? Is there any truth in it perhaps? Has the world of Linux taken a turn toward viruses? Or is Comodo just trying to scaremonger people in the Linux market into using their product?

For the record, just out of curiosity, I have downloaded and am trying it just to see if it any good any way.

---

### Post by craig10x on 2014-06-06
Well i have been running linux since 2008 (started with ubuntu 8.04) and also ran other linux distros as well over the years...no virus scanner and never got one virus/malware/trojan etc etc....i think you will find that is the case for most people on here...:)

That's why you don't really see any virus scanners in the software center except which is really more designed to protect windows users when you send an e-mail to them...though i'd assume they would be running a scanner on their side...linux does not get windows viruses and as far as comodo it sounds like they are just scaremonger...

Others here can probably give you a better explanation or links to articles that explain why linux is so much more secure then windows by DESIGN...

---

### Post by Jonny87 on 2014-06-06
Agreed [**[COLOR=#000000]craig10x[/COLOR]**]("http://ubuntuforums.org/member.php?u=869825"), as I said I have been running linux for years and never had a virus scanner and never had issue. And if I was to run one it would be to make sure I don't pass on an infected file to someone else. But as you said, one would assume that if someone is going to use such a weak os such as Windows they would have an AV Scanner installed on their own system.

I'm just curious in seeing the response of the community, and what their opinions are.

---

### Post by maglin2 on 2014-06-07
One indication of the need/uptake is that the comodo linux av hasn't been updaed for well over a year, and the redirect driver is not compatible with linux kernels beyond 3.5 - ie it doesn't work in real time with any current release of any major distro as far as I am aware.

---

### Post by LastDino on 2014-06-07
Its classic marketing; create need of their product and convert possible customer base into actual customer base. Do not forget that; most people coming from Windows, install AV as soon as they install drivers as a general practice, so all of sudden not being in need of one can  put certain level of doubt in their mind. Most will install it anyway.


Though, it is wrong to believe that there are no Linux Viruses, they are just super duper unlikely to ever reach you as you're probably being outnumber by Windows users few thousand to one, and that is not a very ripe fruit to reap. Not to mention, difficulty level is like 100x minimum.

---

### Post by bashiergui on 2014-06-07
It's FUD. There are numerous ways your Linux system can be compromised. Viruses are near the bottom of the list.

You're far more likely to get compromised by
- malicious javascript in your browser
- having weak passwords for internet-facing services like vnc, ssh, ftp
- torrenting backdoored software

AV on linux diverts attention from actually useful security measures.

---

### Post by unspawn on 2014-06-08
> **bashiergui said:**
> - torrenting backdoored software With all due respect but that's not true. Bittorrent clients don't *execute* torrent contents you download or upload. *If you meant actually trying to use what you download then that's absolutely not confined to Bittorrent: that's a *Layer 8 problem*.

---

### Post by kurt18947 on 2014-06-08
Unmentioned (because it makes linux users sound eliteist?) is a more savvy user base.  It's been the case that people who know what linux is and are able to install it and get it working are able to recognize and ignore social engineering attempts. My biggest concerns are cross platform vulnerabilities, particularly flash & javascript.  If the flash or javascript malware uses a windows-only function to perform its mischief there's still no issue.  Plus it'd need to be capable of silent privilege escalation to install in the system rather than just the user's folder.  I wonder if the proliferation of Android malware is going to affect desktop linux users?  I don't know anything about Android or how easy it would be to modify Android malware to run on desktop linux systems.

---

### Post by bashiergui on 2014-06-08
> **unspawn said:**
> With all due respect but that's not true. Bittorrent clients don't *execute* torrent contents you download or upload. *If you meant actually trying to use what you download then that's absolutely not confined to Bittorrent: that's a *Layer 8 problem*.
Yes I was imprecise in my description. The assumption was that if you get ahold of compromised software you would eventually execute it, and that's when problems ensue.

---

### Post by Chayak on 2014-06-08
I use to analyze malware for a living before being promoted to solutions engineering so I have a decent perspective on the question.

The truth about all Anti-Virus programs is they don't detect new threats. I'll lump them all into the term AV for brevity.
I have a few hundred out of 4TB of malware samples that are not detected by any vendor's AV. It's a fact of life. AV software signatures only detect samples that have been in circulation for a bit or are widespread enough to become a priority. The most dangerous malware is the ones you never know you have and it can be months if ever before a signature is produced.

As to not being an idiot on the web you can get malware from anywhere. A script inserted into an ad can exploit your browser and inject a malicious payload. Many people assume only porn and shady sites are a risk but your more likely to get malware from religious based sites. It's easy to get malware. There's a reason why malware analysts tend to work in virtual machines. There's a huge number of computers running AV software infected with malware and there's zero signs operationally until you forensically examine the system for it. The malware isn't detected because it doesn't draw attention to itself, hence no analysts have spared time to look at it and make signatures.

There's a reason most malware analysts become rather paranoid and end up using Linux, or Macs. Yes, I know malware isn't unknown on the platforms but compared to Windows the number of malware threats combined are far less than .01%

But as for Linux as long as you're not running an SSH server on a system with weak passwords so a bruteforce bot doesn't infect your system you're quite safe. There's a reason most malware labs run on Linux and just use windows virtual machines for analysis. The system I use to archive all the samples is running Ubuntu Server.

The AV available for Linux is crap anyway.  If you're concerned with windows malware then run a good windows AV like Kaspersky on a windows machine.

And no, Android malware is no threat to mainstream linux because it's all Dalvik based so unless you go installing a Dalvik VM on your machine by some means and I'm not even sure that would work properly.

---

### Post by kurt18947 on 2014-06-08
> **Chayak said:**
> 
...................................
And no, Android malware is no threat to mainstream linux because it's all Dalvik based so unless you go installing a Dalvik VM on your machine by some means and I'm not even sure that would work properly.

Thank you.  I'm quite ignorant about this sort of thing.

---

### Post by Jonny87 on 2014-06-08
> **Chayak said:**
> I use to analyze malware for a living before being promoted to solutions engineering so I have a decent perspective on the question.

The truth about all Anti-Virus programs is they don't detect new threats. I'll lump them all into the term AV for brevity.
I have a few hundred out of 4TB of malware samples that are not detected by any vendor's AV. It's a fact of life. AV software signatures only detect samples that have been in circulation for a bit or are widespread enough to become a priority. The most dangerous malware is the ones you never know you have and it can be months if ever before a signature is produced.

As to not being an idiot on the web you can get malware from anywhere. A script inserted into an ad can exploit your browser and inject a malicious payload. Many people assume only porn and shady sites are a risk but your more likely to get malware from religious based sites. It's easy to get malware. There's a reason why malware analysts tend to work in virtual machines. There's a huge number of computers running AV software infected with malware and there's zero signs operationally until you forensically examine the system for it. The malware isn't detected because it doesn't draw attention to itself, hence no analysts have spared time to look at it and make signatures.

There's a reason most malware analysts become rather paranoid and end up using Linux, or Macs. Yes, I know malware isn't unknown on the platforms but compared to Windows the number of malware threats combined are far less than .01%

But as for Linux as long as you're not running an SSH server on a system with weak passwords so a bruteforce bot doesn't infect your system you're quite safe. There's a reason most malware labs run on Linux and just use windows virtual machines for analysis. The system I use to archive all the samples is running Ubuntu Server.

The AV available for Linux is crap anyway.  If you're concerned with windows malware then run a good windows AV like Kaspersky on a windows machine.

And no, Android malware is no threat to mainstream linux because it's all Dalvik based so unless you go installing a Dalvik VM on your machine by some means and I'm not even sure that would work properly.

Thanks for your input Chayak, your knowledge and experience is appreciated in this discussion. I do have a couple of questions for you though if your still following this thread.

If there a lot of virus/malware are unknown and go un detected form the scanners, does that mean that they can't be cleaned until the AV companies have picked up on them?

What is the point of the silent malware that show no sign of harm to the computer? Are they spyware or are just slowly breaking the system down behind the scene?

I ask as I'm a computer tech and a lot of the work I get is removing virus/malware from infected systems.

For those that mentioned web browsing as being part of the cause, that's why I recommend for people to use browser addons such as AdBlockPlus and WOT. These won't completely stop an infection but they are just another line of defence for novice users.

---

### Post by bashiergui on 2014-06-09
> If there a lot of virus/malware are unknown and go un detected form the scanners, does that mean that they can't be cleaned until the AV companies have picked up on them?I'm sure Chayak can and will answer your questions. I can offer you this: All AV does is look at the hashes of the files on your system. It compares your hashes with all the bad hashes it knows about. The reason that's so limited is because you can very easily change the hash of a file by changing a few lines in the code. For instance an executable malware might hard code a call out to evildomain.com. That gets hashed by an AV vendor. Then the malware author changes the domain to superevil.com. Totally different hashes. That's over-simplistic but you get the idea. It's fairly easy for the bad guy to use the same malware by modifying it to create dozens/hundreds of new hashes. It takes AV vendors a lot of work to analyze and hash every single variant of that malware.

Personally I'm not a fan of "cleaning" malware. Because AV is so bad at detecting all malware, it's quite hard to be certain that you've removed every single malicious thing without an intensive and time consuming forensic investigation. Ain't nobody got time for that. I find it hard to justify anything other than reimaging.

---

### Post by unspawn on 2014-06-09
> **kurt18947 said:**
> Unmentioned (..) is a more savvy user base. One portion of Linux users aren't aware they're using Linux. More importantly, if you look at the amount of spam, malware hosting and scanning that comes from compromised machines at resellers and large hosting providers like Rackspace, 1AND1, OVH, Hertzner you'll find a large portion of Linux users is drawn to Linux by its (perceived) cost. They aren't savvy at all. Worse, they're not even remotely interested.    And unless you want to focus purely on the part of the on-line Community that are seasoned Netizens you'll find social engineering attacks have to do with *gullibility* and greed. So that can happen to anyone susceptible enough. The OS really plays no role in that.

---

### Post by Chayak on 2014-06-09
> **Jonny87 said:**
> Thanks for your input Chayak, your knowledge and experience is appreciated in this discussion. I do have a couple of questions for you though if your still following this thread.

If there a lot of virus/malware are unknown and go un detected form the scanners, does that mean that they can't be cleaned until the AV companies have picked up on them?

What is the point of the silent malware that show no sign of harm to the computer? Are they spyware or are just slowly breaking the system down behind the scene?

I ask as I'm a computer tech and a lot of the work I get is removing virus/malware from infected systems.

For those that mentioned web browsing as being part of the cause, that's why I recommend for people to use browser addons such as AdBlockPlus and WOT. These won't completely stop an infection but they are just another line of defence for novice users.

AV can't delete malware it doesn't detect.

Some of the worst kinds of malware are the ones that sit quietly and collect information.  Most modern malware is about money, so they want credit card numbers, industrial secrets, or anything that might be of value.  The more aggressive malware such as cryptolocker holds your files for ransom and punishes you if you fail to pay.

There's all kinds of malware.  You can have the amateur hour script driven brute force bots, or you can have examples that implement their own network stack to be invisible to any network tool on the infected system.  I've seen stuff that will also write itself out to firmware and hide then as it was built modularly it can quietly pull in extra functionality when needed.

If a piece of malware is detected it's trivial to rearrange the code so the signatures will no longer detect it as well.  Polymorphic malware will do this itself, sometimes actively while running, to keep itself hidden.

Malware is getting so difficult to remove that it's best even for the experts to wipe the system and reinstall.  That is of course if you haven't gotten a really sophisticated one that writes itself out to hardware firmware and then pulls stuff back in as soon as the operating system will support it.  That's pretty rare and normally smells of state sponsored items, but it does exist.

---

### Post by unspawn on 2014-06-09
> **Chayak said:**
> But as for Linux as long as you're not running an SSH server on a system with weak passwords so a bruteforce bot doesn't infect your system you're quite safe. That may be the case for amateur machines safely tucked away behind non-port-forwarding CPE (also saying "weak passwords" suggests somebody here isn't adhering to SSH best practices like using only pubkey auth...) but it definitely is not wnough for the rest of the 'net. There's more precautions to take. If you don't get that see recent major compromises involving Linux. Definitely not SSH alone.

---

### Post by Chayak on 2014-06-10
> **unspawn said:**
> That may be the case for amateur machines safely tucked away behind non-port-forwarding CPE (also saying "weak passwords" suggests somebody here isn't adhering to SSH best practices like using only pubkey auth...) but it definitely is not wnough for the rest of the 'net. There's more precautions to take. If you don't get that see recent major compromises involving Linux. Definitely not SSH alone.

Yes, but not everyone is technically savvy with linux to configure things.  The number one reason linux systems are compromised is weak passwords on SSH and FTP.  The easiest thing that any user can do, other than not running SSH/FTP, to improve their security is to use strong passwords.  Security isn't absolutes, it's just about raising the bar.  I guarantee most users on this forum aren't using strong passwords in general, not just on their systems.  Once they get past step one they can read the stickies and raise the bar higher as they learn.  Number two, which is a no-brainer, is updates.

It's constantly the top remediation item when I submit reports on network assessments.  When they get past keeping computers updated and using strong passwords then I'll start preaching best practices for SSH and exploits.  Internet facing servers are a whole different animal as you know and a very deep subject.

---

### Post by sam-c on 2014-06-14
> **Jonny87 said:**
> I will start by stating that I am not a novice user to Linux and so this not a direct question of naivety from someone that doesn't understand Linux. I have never really run my linux systems with a virus scanner as I have always been of the belief that Linux doesn't need it, unless it's to scan file that could potentially infect a windows computer.

Though I'm wondering what other users think of this claim from Comodo regarding their Anti-Virus for Linux;

[http://www.comodo.com/home/internet-security/antivirus-for-linux.php?tc=1&key5sk1=eb9534ba8c68a61b991c4a86a37e4b97a73ddf84&key5sk2=2128&key5sk3=1402097789000&key5sk26=&key5sk27=1402097078000&key5sk28=2720&key5sk29=1402097800000&key5sk30=2720&key5sk31=1402097819000&key6sk1=&key6sk2=FF290&key6sk3=8&key6sk4=en-us&key6sk5=AU&key6sk6=1&key6sk7=http%3A%2F%2Fwww.comodo.com%2F&key6sk8=112202&key6sk9=1366768&key6sk10=false&key6sk11=d9a88c1960c3acc1eeb3ce201f925824e696d953&key6sk12=2035&key7sk1=2&key7sk2=19&key1sk1=dt&key1sk2=http%3A%2F%2Fwww.comodo.com%2F](http://www.comodo.com/home/internet-security/antivirus-for-linux.php?tc=1&key5sk1=eb9534ba8c68a61b991c4a86a37e4b97a73ddf84&key5sk2=2128&key5sk3=1402097789000&key5sk26=&key5sk27=1402097078000&key5sk28=2720&key5sk29=1402097800000&key5sk30=2720&key5sk31=1402097819000&key6sk1=&key6sk2=FF290&key6sk3=8&key6sk4=en-us&key6sk5=AU&key6sk6=1&key6sk7=http%3A%2F%2Fwww.comodo.com%2F&key6sk8=112202&key6sk9=1366768&key6sk10=false&key6sk11=d9a88c1960c3acc1eeb3ce201f925824e696d953&key6sk12=2035&key7sk1=2&key7sk2=19&key1sk1=dt&key1sk2=http%3A%2F%2Fwww.comodo.com%2F)
Under "Frequent Questions"

I'm interested to know what are the opinions of other seasoned Linux Admins and Users out there? Is there any truth in it perhaps? Has the world of Linux taken a turn toward viruses? Or is Comodo just trying to scaremonger people in the Linux market into using their product?

For the record, just out of curiosity, I have downloaded and am trying it just to see if it any good any way.

[SIZE=3][B]These days Anti-Virus is needed.
For simple Solution in Ubuntu I use Clamav with clamtk interface[/B][/SIZE]
try them
Uncle Sam:)

---

### Post by jimmy-frydkaer on 2014-06-14
> **sam-c said:**
> [SIZE=3][B]These days Anti-Virus is needed.
For simple Solution in Ubuntu I use Clamav with clamtk interface[/B][/SIZE]
try them
Uncle Sam:)

I have been running Linux since Ubuntu 6.10 back in 2006. Not *once* have I had an AV installed on my systems.

At the end of the day, when the talk is about security, it all comes down to the users being to lazy to develop their own skills and knowledge to keep themselves safe on the Internet. Pure bad habit from their days on Windows.

It is no art just to sit back after installing an AV scanner, then blame the scanner when the fool finds out that the scanner can't keep him/her safe from malicious software. Nor is it fruitful cry out on the forums in claim of bad advice. 

Many a user will, sadly, experience malware on their system simply because they didn't read the subject seriously when experienced users tell them to use strong passwords, strong encryption on their system and so on. Being an "expert" on the Windows platform is worth nothing on the Linux platform, one will still be a novice on numerous areas of the OS. Having used Linux for eight years does not make me an expert, far from.

Your best friend on Linux and the use thereof is your lust to learn more. No matter what OS you use it *will be*** a never ending learning process**. No one will ever know everything there is to know about his/her OS. Admitting that will make you a bit safer in your use of it.

---

### Post by Frogs Hair on 2014-06-15
Moved to ***Recurring Discussions***

---

### Post by steve26 on 2014-06-28
What is FUD is the fact that people think that Linux is some how.. "immune" to Viruses or Malware. the fact people think that its all about bad habits carried over from Windows is *most often *wrong. 

Linux may have a different file system, but it runs on the same hardware as Windows. With a few exceptions to the kernel, windows is fairly monolithic, just like Linux. apart from the API, code is easily ported between systems. there is not "magic" that makes linux any more secure. strong passwords and encryption will do **nothing** to stop exploits and vulnerabilties in software. not a damn thing.

and COMODO is right! To be honest, I really do not like COMODO, and I  do agree that this is a marketing tact...** but it doesn't mean they are *wrong***. 

if you think you have never been infected while running Linux... **it's likely you just havent realized it yet!**

as somebody who has managed a plethora of machines, for both local area personal networks, local and wide area corporate networks, personal ventures, web hosting businesses, and client and server computing systems in factories (which operate million dollar manufacturing and die cast machinery).. I can tell you that there is _certainly_ a need for antivirus. espeically on Linux.. and it's a ***shame*** that there isn't a realistic solution available to users these days. this is just an unforunate consequence of the fragmented market and the way open source works.

the assumption that anti-virus just compares hashes? sorry! this is just ***not*** true. **this is what the clamscan backend does**, and thats because its a* scanning backend*, **not an anti-virus and security suite.** and it was never intended to be used as one. check out any antivirus suite today... they do **FAR **more than scan files: and there is a reason!

that reason is because the attack landscape has dramatically changed over the years. you do NOT need to install, or run a file, to be infected.

[QUOTE="jimmy-frydkaer"]At the end of the day, when the talk is about security, it all comes  down to the users being to lazy to develop their own skills and  knowledge to keep themselves safe on the Internet. Pure bad habit from  their days on Windows.[/QUOTE]

Sorry, this is not entirely true, and is another false asumption that only Ubuntu users seem to carry. Virus and Malware writers can be ***very*** savvy. while *sometimes*, they gain access to systems because the users bad habits..  this is only a very small part of the puzzle, and most often it's much more complicated that how you have put it.

 **Why do you think that apt-get uses keyrings and compares packages against hashes?** because its a very real threat that the upstream repository can become infected with a trojan or malware. PPAs can have even more risk, and this gets ever Riskier when installing from source! 

and this is **Not** because we cannot trust the publisher. of course installing source from an untrusted mirror is a bad idea, but the bigger problem is rather, because there are often **Vulnerabilities** and **Zero Day Exploits** in many ubuntu or linux services, and application code. some of which go unnoticed for **long **periods of time *(Heartbleed?)*. these can potentially allow an attacker to gain access to a server, and insert his trojan in to the repository. 

and if this can happen to a *server*, or a *repository.. *you can be **certain** that it can happen to any *desktop machine*. plus the chance is actually exponentially greater! this is due to the fact that there is many more pieces of software installed, some of which are much more complex and technically diverse. in the end, they depend on exponentially more binaries and shared libaries... all of which end up increasing your chance to get exploited! 

and what about securing small to medium sized businesses?** there is a legitimate need for a real antivirus solution on Linux**..

lets say you start a business, you have 15 computers, a file server, and some terminals. are you going to spend valuable time and money securing every single system the old fashioned way, using highley fragmented tools from the open source repository?... are you gonna hire a few different IT guys, full time, to constantly manage these machines? train every user how to respect the highly fragmented security policy you had to implement? or would this be another excuse to install windows on all these machines... ? wait.. how much will THAT cost? 

_**Most people I talk with are clear on the fact that the attack landscape is constantly evolving. the Stigma surrounding security and Linux... it needs to Vanish. or it will be a long road ahead for great operating systems like Debian and Ubuntu Linux.**_

---

### Post by steve26 on 2014-06-28
_**What antivirus on Linux *currently* looks like:**_

 with alot of time and effort, a serious security professional will  build his own anti-virus and security solution... typically out of many* existing* open source solutions and projects.

 like I said, antivirus these days does **not** just scan  files and compare hashes! using host based, and network based intrusion  detection systems, kernel level security solutions like SELinux or  AppArmor, packet filtering applictions or scripts, kernel patches (like  GRSecurity), rebuilding out of date or PPA/Source software (using  hardened compiler security parameters), checking for security updates,  performing log file analysis, etc... an adept security analyst will  cobble together the different cogs that which make up an antivirus  solution by 2014's standards.  piece of peice.

 they will also sometimes need to build elements from scratch using  custom code (targeted at the desired platform and his or her particular  environment). using "inotify" or inotifytools, for example, you can call  the virus scanner whenever there are changes to volatile aspects of the  filesystem.

until we get a realistic open source solution like this, comparable to any modern antivirus solution.. we **do** have some options (in the meantime). if you have money to spend: **Symantec, ESET, Kapersky and Avast have released paid solutions**,  which are becoming nearly as useful as their windows counterparts, day  by day. however, from the open source perspective, beyond everything i  talked about above.. there are many third party databases that can be  used with clamscan  to help find common threats for linux. it may even  be useful along side a Paid Solution.

**Linux Malware Detection by RFXN** provides a nice set of linux malware databases. if you do not want to install **LMD**, just download their database files, and use them with ClamScan. do the same with **Sansecurity**. there is an ubuntu package called **clamav-unofficial-sigs**  which provides a number of third party signature databases to help  within this regard... and besides things like this, you should be wary  of rootkits too. **rkhunter** has a database of known rootkits. and there is also **chkrootkit**. or **ossec**. note: there is a plugin you can use to scan all files which are downloaded by firefox as well (**Fireclam**?)

**AppArmor** is fairly important in most any scenario...  especially with FireFox or Chromium on Ubuntu... not to mention most  other main stream applications on Ubuntu today! perfrom a general  security audit on your system, find out what is most potentially  vulnerable, and make sure you set AppArmor to Enforce rules for these  applications. if you are more comfortable with **SELinux**, maybe you should start here.

you can use **"unhide"** to detect hidden processes. this is also available for windows, so this just goes to show that it does not matter **what** system you are running. likewise, **"unhide-tcp"** can find hidden network services. you can use **"ninja"** to whitelist setuid applications. you can use **"checksecurity"** to detect some other critical changes. security audits can be performed with applications like **"Lynis"** (or **"Tiger"** which is more in depth). Check apps against the **CVE Reports** (see "debsecan"). and so on, and so forth.

_**What linux needs from an antivirus, just like any other Operating System:**_|

anti-virus needs to keep a realistic and corrugated mapping of what a   typical attack pattern looks like. it needs to be able to identify   potentially new forms of emerging illicit code. it needs to use   heuristics. it needs to be able to hook the kernel and monitor access to   the file system in realtime. it needs to monitor direct memory access.   protect devices, and drivers. it needs to understand high risk sectors   of the operating system, and be able to detect new or llicit changes.  it  needs to be able to analyze the system for vulnerabilities on the  fly.  monitor installed packages and compare them against the ubuntu   vulnerability database.

most importantly, it needs to be able to do these things without constant user intervention.

the malware writers ARE targetting mainstream linux distributions more  and more, and the problem is that there is nothing for the typical  desktop user to even detect the intrusion! they are driving blind!  companies like Symantec, ESET, Kapersky and Avast have released  solutions for Linux environment, and they cover a majority of the things  I have touched on in this post. and If you think they wasted all the  venture capital by dumping resources into something that isn't needed,  you are dreaming..

if you think that somebody who got infected with a a trojan or malware  on Ubuntu is lazy.... you are just making an excuse. why? because **WE**  are the ones who are responsible for what you see in Ubuntu. if there  is no open source all-in-one security solution, it's because the  community hasn't the resources to complete such a task, or because  people have idea that it simply isn't required. and this is wrong. this  idea is stifling the growth of our operating system.

 in the coming years, there will be another breakthrough when it comes  to Operating Systems. and my bet is on the team that can realize the  future, its potential, and brace for impact if need be. Operating  Systems in the linux world have died off before, and if people are going  to be in denial about the usefulness of security, especially in the age  of the credit card and online transaction... they are digging Ubuntu's  grave.

**the fact of the matter is that just because you are running  Linux, does not mean that your system is secure. just because you get a  virus, does not mean you are a noob. and there are plenty of trojans  floating around that people on linux might not even know they have. **

---

### Post by craig10x on 2014-06-29
Been running linux since ubuntu 8.04 (that's 2008) right to the present...never got a single one of any of those things...comodo is wrong...you are just paranoid about these things...what can i say...
A jealous windows troll, perhaps... ;)

---

### Post by Mike_Walsh on 2014-08-02
I would agree with chayak.

I migrated from Windows XP back in March. I haven't bothered trying to locate or install AV software, due to having friends who've been using Linux for some years, and who have all, without exception, told me that you simply do not need AV software in Linux because of the way it is structured, and the way that root permissions are assigned.

For sure, toward the end in XP (the last 2 years or so anyway), as I became more 'tech-savvy', I'd quit running in Admin mode all the time, having set up a limited user account. That, together with running Comodo's Firewall (not having much faith in the built-in offering), and Malwarebytes, kept me cleaner than I had been for many years previously.

I agree that the AV vendors are trying to scare people into believing that they NEED AV software on Linux.....because with the growing popularity of distros like Ubuntu and Mint, etc., it is now being perceived as a growing market. And since the vast majority of migrants ARE coming from Windows, it's automatic for such people to straight away look for an AV solution (having become so used to the need for it running Microsoft products.)

There again, I feel it's probably true that folk who have taken the time to research, find, download & install a Linux distro, of whichever flavour, ARE going to be a cut above the average intelligence when it comes to using Linux, and understanding why it works in the way that it does!

Regards, 

Mike.

---

