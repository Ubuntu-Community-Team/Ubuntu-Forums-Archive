---
title: "How Secure is Ubuntu Really?"
date: 2011-11-17
forum: Recurring Discussions
---

### Post by Uchiha_Kori on 2011-11-17
Hello once again all.

First of all, I have never had any problems with Ubuntu. I will always favor Ubuntu over all other Linux distros and Windows 7. However, I am concerned (worried actually) about how secure Ubuntu 10.04 and 11.10 really are. I know that here on the forum, people will post biased comments supporting Ubuntu, but can I get an honest, non-biased opinion on the security features of Ubuntu? 

It concerns me I cannot install McAfee on my system. McAfee has protected all my computers since I got my first HP Windows XP. It concerns me I cannot any longer use it. I felt very safe with it.

Also, I cannot find any antivirus software available for Linux, all the more worry (of course, if I'm wrong, please correct me). So again, can I get an honest, non-biased opinion on the security features of Ubuntu?  

-Kori

---

### Post by haqking on 2011-11-17
> **Uchiha_Kori said:**
> Hello once again all.

First of all, I have never had any problems with Ubuntu. I will always favor Ubuntu over all other Linux distros and Windows 7. However, I am concerned (worried actually) about how secure Ubuntu 10.04 and 11.10 really are. I know that here on the forum, people will post biased comments supporting Ubuntu, but can I get an honest, non-biased opinion on the security features of Ubuntu? 

It concerns me I cannot install McAfee on my system. McAfee has protected all my computers since I got my first HP Windows XP. It concerns me I cannot any longer use it. I felt very safe with it.

Also, I cannot find any antivirus software available for Linux, all the more worry (of course, if I'm wrong, please correct me). So again, can I get an honest, non-biased opinion on the security features of Ubuntu?  

-Kori

this is such a recurring discussion.

read here [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

To be honest there is no difference between the security of a end user OS than any other in its design, the security lies within the end user.  As far as design goes there is a security triangle where securirity would be at the top, the closer you get to that the futher you move away from the other 2 points which are ease of use and functionality.

AV is not needed as much in Linux due to the viruses in the wild or not that exist, but that is due to malicious people not really targeting the Linux desktop market as yet.  But also there are no good end user apps for that purpose, there is ClmaAV if you want something to scan windows files for sharing.

Security is much more than virus related.

---

### Post by CharlesA on 2011-11-17
It has the same security features as Debian.

iptables for the firewall, Apparmor for confining applications, among other things.

Are you asked about security in the sense of a desktop install or server install?

See the link Haqking posted and the monster thread here:
[http://ubuntuforums.org/showthread.php?t=1873643](http://ubuntuforums.org/showthread.php?t=1873643)

---

### Post by ibutho on 2011-11-17
Any operating system is as secure as the system administrator makes it (so how you use your computer, whether you use firewalls, regularly check for rootkits, malware, disable remote root logins etc). Take a look [here]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/") for information about Linux and viruses.

---

### Post by PapaGary on 2011-11-17
> **Uchiha_Kori said:**
> 
It concerns me I cannot install McAfee on my system. McAfee has protected all my computers since I got my first HP Windows XP. It concerns me I cannot any longer use it. I felt very safe with it.
This is not exactly a direct answer to your question but:

Since Windows 95 I have **never** had AV software running on my PC. Every once in awhile, if I'm bored, I will download and run one of the popular AV apps but nothing is ever found. I rely on sensible surfing and a hardware firewall and do not feel vulnerable at all. I'm certainly not worried about running Ubuntu AV free.:cool:

---

### Post by OpSecShellshock on 2011-11-17
The OS is not really as big a deal as the applications, with the biggest risk for most people being the web browser.

For AV software, the thing is that the existing options won't do you any good. They will really only search for Windows malware or old, known Linux malware. If any malware targeting Linux should emerge in the future, there wouldn't be any detection for it anyway as the available engines (including McAfee's, which I think is only available for enterprise systems in the Linux version) don't perform heuristic detection on Linux.

There are changes you can make away from the defaults, but they will make your system and web browser somewhat more difficult to use. See the Basic Security Wiki linked above.

---

### Post by lisati on 2011-11-17
> **Uchiha_Kori said:**
> It concerns me I cannot install McAfee on my system. McAfee has protected all my computers since I got my first HP Windows XP. It concerns me I cannot any longer use it. I felt very safe with it.
The McAfee products that many of us will be aware of just plain won't work on Ubuntu, because programs designed for Windows won't work on Linux-based systems withouth help.

Opinions vary about the need for anti-virus tools on Ubuntu and which, if any, is best. If you *must* install AV software, a search of the software center and other places should help you install something. Personally, I use AVG Free on my Windows installations and clamAV on my Ubuntu-based email server.

I haven't bothered on my "desktop" installation of Ubuntu, because many of the problems introduced by malware can be avoided by other means.

---

### Post by Dangertux on 2011-11-17
Ubuntu like any operating system is as secure as you make it.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) -- Ubuntu Security
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906) -- Apparmor
[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662) -- Host Based Intrusion Detection (read really heavy software that is bypassed easily)
[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696) -- Network based Intrusion Detection ( even heavier software that is equally easy to bypass for an attacker)
[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177) -- Compelling but often ignored argument for why you should build a good firewall. Contains links to resources for creating said firewall.
[http://ubuntuforums.org/showthread.php?t=1873643](http://ubuntuforums.org/showthread.php?t=1873643) -- Gigantic mega thread where 3 infosec professionals and a horde of paranoid end users try to convince people to secure their systems at the same time as educating them how to :-)

Hope this helps :-)

---

### Post by haqking on 2011-11-17
People are always asking this question and having this debate.

The fact is the security of the end user OS will be a balance between Security, Ease of use and functionality, as you increase one the others decrease and so on.

Microsoft operating systems comply with the Common Criteria EAL 4 which is a standard of security required.

Any Linux distro who wants to target a particular audience will seek Common Criteria cetification such as RedHat, CentOS, Suse etc who adhere to EAL3 + or EAL 4 etc depending on their specific configurations.

I dont know if Canonical has sought this certification but i imagine they have and if have or do will adhere to the same, as if you rise above that certification you remove yourself from a given market.

So all are the same at the end of the day though the way they achieve them may be different, either way the security will really come down to the end user and what they do and how they do it.

As soon as you move away from defaults with setting changes, service changes, installtion of apps, installing apps with shrink-wrap code, misconfigurations etc then it is when the bad things are more likely to happen.

Cheers

---

### Post by lisati on 2011-11-17
*Thread moved to **Recurring Discussions**.*

Others more eloquent than myself have summed things up nicely.

---

### Post by Dangertux on 2011-11-17
> **haqking said:**
> People are always asking this question and having this debate.

The fact is the security of the end user OS will be a balance between Security, Ease of use and functionality, as you increase one the others decrease and so on.

Microsoft operating systems comply with the Common Criteria EAL 4 which is a standard of security required.

Any Linux distro who wants to target a particular audience will seek Common Criteria cetification such as RedHat, CentOS, Suse etc who adhere to EAL3 + or EAL 4 etc depending on their specific configurations.

I dont know if Canonical has sought this certification but i imagine they have and if have or do will adhere to the same, as if you rise above that certification you remove yourself from a given market.

So all are the same at the end of the day though the way they achieve them may be different, either way the security will really come down to the end user and what they do and how they do it.

As soon as you move away from defaults with setting changes, service changes, installtion of apps, installing apps with shrink-wrap code, misconfigurations etc then it is when the bad things are more likely to happen.

Cheers

LTS server is CC EAL 4+ I believe.

Long story short this means it's generally safe for production use. And that you have a decent level of assurance against a full spectrum of targets. 1 is the lowest 7 is the highest. If I were to wager (I don't now if they're rated) but I would say desktop LTS'es are probably 3-4 and the intermediate releases are 2-3. Just a hunch.

---

### Post by haqking on 2011-11-17
> **Dangertux said:**
> LTS server is CC EAL 4 I believe.

Long story short this means it's generally safe for production use. And that you have a decent level of assurance against a full spectrum of targets. 1 is the lowest 7 is the highest. If I were to wager (I don't now if they're rated) but I would say desktop LTS'es are probably 3-4 and the intermediate releases are 2-3. Just a hunch.

yeah sounds about right.  I just went to check them actually but the cc site was acting up so i didnt give it any time and left ;-)

end user and mainstream is around 3+ to 4 thereabouts

---

### Post by Dangertux on 2011-11-17
> **haqking said:**
> yeah sounds about right.  I just went to check them actually but the cc site was acting up so i didnt give it any time and left ;-)

end user and mainstream is around 3+ to 4 thereabouts

I corrected it btw LTS server is 4+ since hardy.

---

### Post by haqking on 2011-11-17
> **Dangertux said:**
> I corrected it btw LTS server is 4+ since hardy.

cool, good to know.

cheers

---

### Post by Uchiha_Kori on 2011-11-17
Thanks all. This eases me greatly.

---

### Post by dirtrider1 on 2011-11-18
> **Uchiha_Kori said:**
> Hello once again all.

First of all, I have never had any problems with Ubuntu. I will always favor Ubuntu over all other Linux distros and Windows 7. However, I am concerned (worried actually) about how secure Ubuntu 10.04 and 11.10 really are. I know that here on the forum, people will post biased comments supporting Ubuntu, but can I get an honest, non-biased opinion on the security features of Ubuntu? 

It concerns me I cannot install McAfee on my system. McAfee has protected all my computers since I got my first HP Windows XP. It concerns me I cannot any longer use it. I felt very safe with it.

Also, I cannot find any antivirus software available for Linux, all the more worry (of course, if I'm wrong, please correct me). So again, can I get an honest, non-biased opinion on the security features of Ubuntu?  

-Kori

IMHO Linux/Ubuntu has several security advantages over other OS's including being Free/Open source software, The OS itself is much harder to infect and was designed with a better architecture , and most FOSS applications place a much higher emphasis on security all the way down to the end user documentation and default setups with security as a high priority. As well as Frequent updates,auditing and a low potential for malicious software.

To your second question I suggest you read the security sticky as I'm pretty sure it covers the migrating from Windows and the "Windows Mindset". For the most part Mcafee would be absolutely worthless if installed to protect a Linux machine because it would be scanning for Windows maleware. As of right now there are no known viruses in the wild that will infect an up to date Linux machine.

I feel when a repeated generalizing question like this is asked, many forum members tend to give broad generalizing answers as non biased as they can, which I respect and feel are worthy. But at the same time I truly feel there are some very specific security benefit's especially for new users by using Free software and gaining more knowledge thereof it.

---

