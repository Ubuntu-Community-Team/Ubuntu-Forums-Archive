---
title: "Antivirus"
date: 2008-11-27
forum: Recurring Discussions
---

### Post by Jeyaganeshdj on 2008-11-27
Hi Friends,

          I am a Windows user and recently switched to Linux. I need a clarification.. If I insert a pen drive with virus in my Windows the AVG antivirus alerts me... I heard that there is no need for antivirus in Linux but if I do insert the same pen drive in my Linux OS with out antivirus what happens??? May be it sounds a bit dump but am new to Linux...

---

### Post by cmay on 2008-11-27
the virus is most likely for windows so it cant run on linux and thus not harm linux.

---

### Post by halitech on 2008-11-27
there are a few viruses for linux but not in the wild. It would be the same as downloading a windows .exe file and trying to run it - nothing happens. Most people that run antivirus in linux do so to protect their windows using friends.

---

### Post by Skripka on 2008-11-27
> **cmay said:**
> the virus is most likely for windows so it cant run on linux and thus not harm linux.

Even if you have Wine installed, to run Windows .exe files--odds are about 99% that nothing will happen.

---

### Post by Paqman on 2008-11-27
> **Jeyaganeshdj said:**
> with out antivirus what happens???

The vast majority of viruses are designed to infect Windows. Also Ubuntu has a permissions system, which means that things have to ask you for permission to execute.

The virus would only be able to execute if you ran it deliberately. Even then, it would find none of the Windows file system, system files and registry that it is designed to infect. It's likely that it would do very little at all.

So you can have viruses present on an Ubuntu system, but they aren't able to do anything. There are antivirus suites available for Linux, but they are designed to protect Windows boxes.

Instead of installing antivirus software on Ubuntu, all you need to do is keep up to date with security updates.

---

### Post by newbuntuxx on 2008-11-27
nothing will happen. Windows viruses are impotent on Linux. Linux will look at them as text files! 

If you have wine installed though, and you deliberately run the virus using wine, it may destroy your wine installation.

---

### Post by cmay on 2008-11-27
a virus is essential a program. the best are small and written in assembler(so i read) and they take advantage of certain holes in the target OS such as bufferowerflows and so on but there are virus for linux. i think there is nine or so at the most. there was once a worm that went for old red hat severs only but its by far not as comprehensive as on windows. and the thing is that a vira in a usb stick would most likely be hard to even install and run as i figure it on linux. in any case i think its not the thing to worry about. more chance of getting tricked into runnning harmful commands in the terminal or even pay money over something fake internet buisness as also linux users can be tricked. there are not so much to wory about as virus is concerned. 

  WINE cant even run most the programs that are really by design ment for windows X version and nothing else so they (OS specific vira )  are not likely to run in anything else than the OS they are written to attack .

---

### Post by OutOfReach on 2008-11-27
Nothing would happen. Linux is more secure and handles things more securely than Winows does. And anyways you wouldnt be able to run the .exe in that flash drive.

---

### Post by altonbr on 2008-11-27
> **Jeyaganeshdj said:**
> Hi Friends,

          I am a Windows user and recently switched to Linux. I need a clarification.. If I insert a pen drive with virus in my Windows the AVG antivirus alerts me... I heard that there is no need for antivirus in Linux but if I do insert the same pen drive in my Linux OS with out antivirus what happens??? May be it sounds a bit dump but am new to Linux...

Like cmay said, Linux will be completely uninfected by the virus. You CAN install virus scanners such as AVG (from their website) or ClamAV (using 'clamtk') but you really *really* don't need to.

The only way the virus can run is if you have a program called WINE installed (which gives you the ability to execute Windows programs) and you double-click the file. Even then, it is more than likely that the program will not be able to run, run in a low capacity or not effect your files at all.

There is sort of a joke article about running viruses through Wine and seeing how they perform here: [http://www.linux.com/articles/42031](http://www.linux.com/articles/42031).

In the end though, I would not be worried about viruses on Linux, period.

---

### Post by cmay on 2008-11-27
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)
here is a joke about how hard it is to get a virus running under linux. but the joke is in fact not far from the truth. since its a hard  trick a virus to get installed by root in ubuntu since we use sudo and file permissions and have to compile stuff that are not coming from the official reposotieries .

---

### Post by NewJack on 2008-11-27
Bottom line:  

You don't need to worry about viruses in Linux 

AND

If you share files with a Windows box/partition or with friends who are Windows users, you can be proactive and install an AV program to help catch any Windows viruses that may be present in those files.

A/V programs available for Linux:  Clam A/V, Avast, AVG

---

### Post by aysiu on 2008-11-27
> **cmay said:**
> [http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)
here is a joke about how hard it is to get a virus running under linux. but the joke is in fact not far from the truth. since its a hard  trick a virus to get installed by root in ubuntu since we use sudo and file permissions and have to compile stuff that are not coming from the official reposotieries .
Actually, that is quite far from the truth.

If you're talking about malware that requires user intervention (social engineering-based malware) instead of a self-replicating/infecting virus that takes advantage of weakly secured network settings and software vulnerabilities, then it takes only these steps: [list][*]Download malicious .deb file[*]Double-click it to launch GDebi[*]Click *Install Package*[*]Enter your password[/list]

---

### Post by cmay on 2008-11-27
> If you're talking about malware that requires user intervention (social engineering-based malware)i am set to Denmark language per default but what i mean to say is that one should just not ever download random stuff and or enter scripts copy and pasted from the internet per random. one should just stick to synaptic and add remove menu. i said it more clearly in the other post of mine. 
it does not matter if we have too compile stuff and set file permissions for installing out vira from source if we get tricked into it and i think i said the same thing more clear in the other post of mine above. linux users can get tricked also but no need to worry about a vira that jumps out of a usb stick by itself in linux. 

> in any case i think its not the thing to worry about. more chance of getting tricked into runnning harmful commands in the terminal or even pay money over something fake internet buisness as also linux users can be tricked. there are not so much to wory about as virus is concerned.i am tired now. going to bed.  i just wanted to say we agree upon the same thing. :)

---

### Post by sdowney717 on 2008-11-27
still, it would be nice to discover viri on insertable media, just as a way of not further spreading it to windows machines. Do any othe antivirus programs for linux do real time scanning?

---

### Post by bodhi.zazen on 2008-11-27
Security on Linux is not the same

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by Dex73 on 2009-05-09
I have avast. I use it to keep stuff clean for windows.

---

### Post by presence1960 on 2009-05-09
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by gn2 on 2009-05-09
> **aysiu said:**
> If you're talking about malware that requires user intervention (social engineering-based malware) instead of a self-replicating/infecting virus that takes advantage of weakly secured network settings and software vulnerabilities, then it takes only these steps: [list][*]Download malicious .deb file[*]Double-click it to launch GDebi[*]Click *Install Package*[*]Enter your password[/list]

It's even easier than that, just copy and paste dodgy terminal commands e.g: sudo r__________

---

### Post by mrbiggbrain on 2009-05-09
Theres an old story (i dont know if its true) that a company offered $10 to anyone who could write a windows virus in under an hour, and about 100 people won. the same task was given for linux, with a timeframe of 1 month and $1,000,000 offered to crack there version, and noone collected.

Linux has permissions and requires user intervention to do things, unless you are root. even as root, the system does not autorun programs just becuse there there (aka windows).

There are about 50 viruses for linux, theres a few million for windows. otu of the 50 virsues 45 where lab created, and patched into the kernel before ever seeing daylight, that means (to my sources) there are 5 viruses you can get, that most likely require root privlages to run, and most likely have been fixed in the kernel by now

most viruses on windows take advantage of the fact that windows will do near anything just being having anyone say so, and do so whenever you boot.

---

