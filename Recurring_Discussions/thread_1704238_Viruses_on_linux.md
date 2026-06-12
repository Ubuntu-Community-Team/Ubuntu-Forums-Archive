---
title: "Viruses on linux?"
date: 2011-03-10
forum: Recurring Discussions
---

### Post by Bluehotdog5 on 2011-03-10
how much of a problem are viruses on ubuntu?
how rare are they I mean?

---

### Post by lithopsian on 2011-03-10
Very rare as in I've never actually seen a live one myself.  I've seen rootkits from ssh breakins.  They can do much of the stuff that a virus does, but don't propagate themselves in the same way.  I'd expect most Linux viruses would actually be an infection of a web browser or email client rather than the operating system.

Nothing to stop a Linux virus being written, but lack of machines makes them hard to propagate and lack of a consistent architecture makes them hard to write.

---

### Post by uRock on 2011-03-10
> **Bluehotdog5 said:**
> how much of a problem are viruses on ubuntu?
how rare are they I mean?
0 problem, very rare.

---

### Post by philinux on 2011-03-10
> **Bluehotdog5 said:**
> how much of a problem are viruses on ubuntu?
how rare are they I mean?

Please see here.

[http://ubuntuforums.org/search.php?searchid=79871534](http://ubuntuforums.org/search.php?searchid=79871534)

Moved to recurring.

---

### Post by TeoBigusGeekus on 2011-03-10
[A history of viruses on linux.]("http://www.neowin.net/news/a-history-of-viruses-on-linux")

---

### Post by mmsmc on 2011-03-10
koobecaf was a virus that work don linux, but was made for mac and pc(they did not intend it to work on us) but since this is linux you would have to download it, install it, run as root, then get infected(meaning you have to be really dumb, plus it came in the form of an email)

---

### Post by aysiu on 2011-03-10
Social engineering-based attacks are possible on any platform. These are malware designed to look benign (install this cool program, you need this plugin to view this page, etc.). If you are gullible enough to install trojans (or if the trojan-makers are clever enough to fool people who aren't gullible, though I haven't seen this happen yet), then your system will be compromised.

Malware that takes advantages of flaws in the operating system (and not the user) will not be stopped by so-called antivirus (i.e., placebo).

So just be informed, take precautions, and don't be fooled into thinking antivirus will protect you, and you'll be fine.

More details here:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Rasa1111 on 2011-03-10
Lets just say Ive been using nothing but Ubuntu for a bit over a full year..
with no "virus protection" whatsoever..
and have not had a single issue yet. lol

 Most windows users i know..
Can have a brand new, fresh windows install..(with virus protection)
and be compromised (have viruses) within a week, if not a couple days. lol

Be smart.

---

### Post by kaldor on 2011-03-10
The only thing to worry about is a trojan. 

Trojans disguise themselves as software, etc, and the user needs to run it. Using the Ubuntu Software Centre eliminates this issue completely. I've heard of 3 trojans since I started Linux. One was disguised as a screensaver, and one was in either the Gentoo or Arch repository (forget which).

Just be smart and you are perfectly safe. Downloading random .deb files usually won't be a problem, but if it looks suspicious it probably is.

> **Rasa1111 said:**
> Lets just say Ive been using nothing but Ubuntu for a bit over a full year..
with no "virus protection" whatsoever..
and have not had a single issue yet. lol

 Most windows users i know..
Can have a brand new, fresh windows install..(with virus protection)
and be compromised (have viruses) within a week, if not a couple days. lol

Be smart.

This.

I get into arguments with a friend sometimes because he is overly aggressive about his "amazing virus protection" (Kaspersky) but yet regularly has major issues (trojans, malware, crashes, etc). Then someone has to fix it for him and he gets upset and blames everything *except* Kaspersky. I keep telling him as long as he stops clicking everything he sees, downloading everything that pops up, and stops going on sites he shouldn't then he won't have any issues at all. He still pays lots of money into Kaspersky now and then but still has issues.

But nope, some people are *impossible* to protect. You can have all the antivirus stuff in the world, but if you're stupid and click everything you see and download stuff from all the pr0n sites on the web, you're not going to stay safe. I only remember two issues with malware when I used Windows; and I used it from 95-Vista.

---

### Post by fuduntu on 2011-03-10
> **aysiu said:**
> Malware that takes advantages of flaws in the operating system (and not the user) will not be stopped by so-called antivirus (i.e., placebo).


This is only partially true.  A virus that matches a specific heuristic pattern would be trapped by AntiVirus.  This technology can trap new viruses without definitions as long as they have a certain behavior pattern.  A virus that did not match any known pattern would not be trapped until the virus definition file was updated with the virus signature, this would allow 0day viruses to propagate for a limited amount of time.

There have only been a handful of these types of viruses for Linux, but the number is greater than 0 so there is some risk however slight it may be.

---

### Post by leeshaub on 2011-03-10
> **Rasa1111 said:**
> Lets just say Ive been using nothing but Ubuntu for a bit over a full year..
with no "virus protection" whatsoever..
and have not had a single issue yet. lol

 Most windows users i know..
Can have a brand new, fresh windows install..(with virus protection)
and be compromised (have viruses) within a week, if not a couple days. lol

Be smart.  same thing here but i download more things from 5 sites 
i've not been on ubuntu for a year.

---

### Post by aysiu on 2011-03-10
> **fuduntu said:**
> This is only partially true.  A virus that matches a specific heuristic pattern would be trapped by AntiVirus.  This technology can trap new viruses without definitions as long as they have a certain behavior pattern. But heuristics also lead to false positives, which means a real human being still has to monitor things. I stand by my assertion that antivirus is useless.

---

### Post by Rasa1111 on 2011-03-10
> **aysiu said:**
>  I stand by my assertion that antivirus is useless.

and I stand by your assertion. lol :KS

> leeshaub~ same thing here but i download more things from 5 sites 

"more things from 5 sites"?

I also download a lot of stuff!

---

### Post by fuduntu on 2011-03-10
> **aysiu said:**
> But heuristics also lead to false positives, which means a real human being still has to monitor things. I stand by my assertion that antivirus is useless.

Ok, well I stand by my assertion that your assertion is wrong. ):P

Here is a fine example of why.

[http://www.computerworld.com/s/article/9214023/Symantec_finds_fake_Google_Android_update](http://www.computerworld.com/s/article/9214023/Symantec_finds_fake_Google_Android_update)

---

### Post by leeshaub on 2011-03-10
i agree with fuduntu!

---

### Post by mmsmc on 2011-03-10
i agree with both of them, one needs to be a safe user, but virus protection does help. I have had only two viruses on xp, and the anti-virus did not help, but it did provide a false sense of security and made me feel better about using the Internet, may i add this was 4 years ago when i did not know a thing about computers!(in my view, what anti-virus is designed for :))

---

### Post by leeshaub on 2011-03-10
post #11 is not true my falt i have ubuntu 10.04 on a HP and on the next side is win vista (slow boot) and ubuntu (fast boot)some viruses not more then 2

---

### Post by doas777 on 2011-03-10
> **TeoBigusGeekus said:**
> [A history of viruses on linux.]("http://www.neowin.net/news/a-history-of-viruses-on-linux")

i have to laugh at a few of those. the 2009 reference to a "trojan" on gnome-look was particularly amusing, since this is all it was
[http://ubuntuforums.org/showthread.php?t=1349678](http://ubuntuforums.org/showthread.php?t=1349678)

no backdoor, no outbreak, just some dumb kid playing with scripts for a couple hours before his payload was taken offline. 98% of the people downloading that .deb were us forum posters, and all we were doing was dissecting it.

nice try though.

---

### Post by uRock on 2011-03-10
> **doas777 said:**
> i have to laugh at a few of those. the 2009 reference to a "trojan" on gnome-look was particularly amusing, since this is all it was
[http://ubuntuforums.org/showthread.php?t=1349678](http://ubuntuforums.org/showthread.php?t=1349678)

no backdoor, no outbreak, just some dumb kid playing with scripts for a couple hours before his payload was taken offline. 98% of the people downloading that .deb were us forum posters, and all we were doing was dissecting it.

nice try though.
/me remembers that one!:D

---

### Post by aysiu on 2011-03-10
> **fuduntu said:**
> Ok, well I stand by my assertion that your assertion is wrong. ):P

Here is a fine example of why.

[http://www.computerworld.com/s/article/9214023/Symantec_finds_fake_Google_Android_update](http://www.computerworld.com/s/article/9214023/Symantec_finds_fake_Google_Android_update)
From [a site offering less publicity for Symantec but also reporting the same news story](http://www.techday.co.nz/netguide/news/fake-android-security-update-alert/19570/1/): > This package was found on an unregulated third-party Chinese marketplace So still a great case for using common sense to avoid trojans instead of relying on "antivirus" to do it for you.

---

### Post by Rasa1111 on 2011-03-10
> **aysiu said:**
> From [a site offering less publicity for Symantec but also reporting the same news story](http://www.techday.co.nz/netguide/news/fake-android-security-update-alert/19570/1/):  **So still a great case for using common sense **to avoid trojans instead of relying on "antivirus" to do it for you.

Silly aysiu..
That would be the best thing..     
But..
Common sense is not at all "common"!
Especially among 'the masses' lol ;) :P

---

### Post by Timmer1240 on 2011-03-10
Been on Linux over a year No antivirus nothin not 1 virus or trojan when I was running Windows I was running into stuff all the time until I started using Sandboxie its a great program for Windows.

---

### Post by Hur Dur on 2011-03-10
They exist, but you would have to be an imbecile to get one.

I mean, if you get a virus on Linux, you shouldn't even use a computer.

The only reason I would worry is if you ran as root all the time, and downloaded a file called justin_beeber.deb. 

Anti-Virus is absolutely useless with GNU/Linux. It is already designed to be safe and secure.

---

### Post by uRock on 2011-03-10
Thread has down graded to name calling and insults.

Thread Closed.

---

