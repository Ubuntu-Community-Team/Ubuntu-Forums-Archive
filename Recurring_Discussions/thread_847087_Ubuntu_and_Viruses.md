---
title: "Ubuntu and Viruses"
date: 2008-07-02
forum: Recurring Discussions
---

### Post by Uchiha_madara on 2008-07-02
Which Kind of viruses can harm ubuntu ???

---

### Post by lisati on 2008-07-02
Only the ones you give permission to do so. Have a look[ here]("http://ubuntuforums.org/showthread.php?t=765421")

---

### Post by kdcoetzee on 2008-07-02
I have never seen or heard of any Linux viruses in my life time. (I am young but that is not the point :p)

If there is any. please correct me that I can learn something new.

Now to quickly read this thing lisati sent... Which I should have done before posting this.

---

### Post by smartboyathome on 2008-07-02
You shouldn't have done anything; as of this moment, viruses are almost non-existant in Ubuntu (the most recent one rendered harmless years ago). Why do you think it is used on 66% of servers? ;)

---

### Post by sdlynx on 2009-06-18
> **lisati said:**
> Only the ones you give permission to do so. Have a look[ here]("http://ubuntuforums.org/showthread.php?t=765421")

he's right
due to the root account it is hard to not notice anything you don't want being installed (ie a virus)

also considering that almost all the applications you install will be from a package manager there is no danger for a virus at all

---

### Post by doas777 on 2009-06-18
the stuff that can affect ubuntu is completely unknown. I'm sure the nsa and cyber espionage agencies around the world have the capability, but I am pretty sure we'd never see it coming. but then again, they'd need a reason, wouldn't they.

also be careful about terminology. Viruses (parasitic malware, that uses system software to act badly, and are contagious) are virtually non-existant in linux, and ubuntu is structured such that it would be hard to get it to run, or do much if you could. 

but viruses are only one kind of malware. as lisati said, ubuntu is vulnerable to linux trojans (pretty rare, mainly used in targted spear-phishing) if you are tricked into executing them.  *nix does have a history of problems with some worms (also very rare; like viruses, but self-contained; they do not need to use system software to act bad or spread), and spyware/adware written to run in firefox, will likely run exactly as it would on windows, as long as it did not rely on any system/environment calls.

my biggest worry, is that someday someone will compromise the repos.

---

### Post by rookcifer on 2009-06-19
> **doas777 said:**
> 
my biggest worry, is that someday someone will compromise the repos.

It's already happened to several distros, with Fedora being the most [recent example]("http://www.thetechherald.com/article.php/200835/1847/Fedora-Project-and-Red-Hat-hit-by-intruders-%E2%80%93-why-the-delay-in-disclosure").

And even without repo compromises, one must still ask, "who watches the watchers?"  It was demonstrated over 20 years ago by Ken Thompson (one of the creators of Unix) that one can hide backdoors in compilers and make them undetectable -- literally impossible to find even if one checks the compiler *source*.  Thompson himself [created]("http://scienceblogs.com/goodmath/2007/04/strange_loops_dennis_ritchie_a.php") a Unix backdoor that gave him full access to any Unix system compiled with a specific compiler and only told the world about it during his 1983 [Turing award acceptance speech]("http://cm.bell-labs.com/who/ken/trust.html"), some 15 years after he did it.

I suppose the lesson to be learned is you can only have a limited amount of trust in any sophisticated software project like an OS, whether it be closed-source or open-source (though open-source would be less susceptible by nature but still not bullet proof).  Unless one can go through every line of the ~9 million lines of code in the kernel oneself to check for every possible security hole, one can never be sure.  Even seasoned security experts cannot spot all the errors.  And then you have to take into account not only a distro's package repostory but also the CVS, subversion, and git repositories from where the code is originally stored.  It's possible for an intruder to crack those repos and insert malicious code even without the developer's knowledge.  Of course such code probably wouldn't last all that long before it was discovered, but it would still be feasible for it to "get into the wild."

And this is all not even taking into account compromised hardware.  It's perfectly feasible that CPU manufacturers, for instance, could allow compromised microcode to be released.  This would allow total system compromise no matter the OS being used.  This is a concern due to the fact that some chips are manufactured in countries that aren't really that friendly to the west.

The only thing the end user can do is take the basic security steps (firewall, don't run as root, only install from distro repos, etc) and hope that the "watchers" are trustworthy.  That's why "viruses" and the like should be the least of a Linux/BSD user's worries.  They aren't really a threat at all.  The biggest threat is from compromised or incompetent source code.

---

### Post by starcannon on 2009-06-19
Don't leave your remote desktop turned on when not in use.
Keep your updates current.
Don't run commands you do not understand, or are not prepared to research first.
Don't install software/*.deb from anyone you don't trust.
No problems.

P.S.
If your really paranoid about security, there is always [Tin Foil Hat Linux]("http://tinfoilhat.shmoo.com/") or [Linux From Scratch (LFS)]("http://www.linuxfromscratch.org/")

---

### Post by juancarlospaco on 2009-06-19
**[SIZE="3"]Mono[/SIZE]**
it can bloat your system with .EXEs and .DLLs on Linux
*.EXEs and .DDLs can be infected, so you are running infected programs*

---

### Post by directhex on 2009-06-20
> **juancarlospaco said:**
> **[SIZE="3"]Mono[/SIZE]**
it can bloat your system with .EXEs and .DLLs on Linux
*.EXEs and .DDLs can be infected, so you are running infected programs*

You'll only embarrass yourself if you don't know what you're talking about.

File extensions don't mean anything. If I rename "/bin/bash" to "/bin/bash.exe" that doesn't suddenly make it infectable

And if we're talking purely about file contents, what makes CLI assemblies infectable? As opposed to Windows PE executables, which Mono doesn't know how to deal with (those are Wine's job)

---

### Post by juancarlospaco on 2009-06-20
You'll only embarrass yourself if you don't know what you're talking about.

File extensions don't mean anything. 
For example if i make **file /usr/bin/nemo.exe**   *
it says its a :
**Program for Microsoft Windows - WIN32 Executable**

So why are needed a Program for Microsoft Windows on my Linux box???


******[SIZE="1"][Nemo its a random example]("http://www.iola.dk/nemo/"), its a File browser developed using M$ Mono, the same for other programs.[/SIZE]*

As the same to Windows executables, which Mono uses everytime, checked by the *"file"* command.

---

### Post by shadylookin on 2009-06-20
> **juancarlospaco said:**
> You'll only embarrass yourself if you don't know what you're talking about.

File extensions don't mean anything. 
For example if i make **file /usr/bin/nemo.exe**   *
it says its a :
**Program for Microsoft Windows - WIN32 Executable**

So why are needed a Program for Microsoft Windows on my Linux box???


******[SIZE="1"][Nemo its a random example]("http://www.iola.dk/nemo/"), its a File browser developed using M$ Mono, the same for other programs.[/SIZE]*

As the same to Windows executables, which Mono uses everytime, checked by the *"file"* command.

.exe are typically only used on windows. On linux file extensions are only to let the users know what they can expect(you can make the file extension whatever you please for all linux cares). You can name a linux binary .exe and it will still work, but you cannot run that binary on windows.

---

### Post by directhex on 2009-06-20
> **juancarlospaco said:**
> it says its a :
**Program for Microsoft Windows - WIN32 Executable**

So why are needed a Program for Microsoft Windows on my Linux box???

Nice paraphrasing.

What it ACTUALLY says is:
"PE32 executable for MS Windows (console) Intel 80386 32-bit Mono/.Net assembly"

CLI assemblies use PE file headers, as per the ECMA335 specification. It's the binary equivalent to sticking #!/bin/bash at the top of a script.

A PE header does not a Windows app make. Other than the oh-so-offensive collection of bits and bytes at the top of the file, a CLI assembly is no less "native" than a Python script. It's certainly not a "Program for Microsoft Windows"

As for Windows apps, you're mistaken - they do NOT produce the same output from file.

```
jms@osc-franzibald:~$ file /usr/lib/gnome-do/Do.exe
/usr/lib/gnome-do/Do.exe: PE32 executable for MS Windows (console) Intel 80386 32-bit Mono/.Net assembly
jms@osc-franzibald:~$ file /media/WindowsXP/WINDOWS/system32/sol.exe 
/media/WindowsXP/WINDOWS/system32/sol.exe: PE32 executable for MS Windows (GUI) Intel 80386 32-bit
```

And Mono has nothing to do with Windows apps

```
jms@osc-franzibald:~$ mono /media/WindowsXP/WINDOWS/system32/sol.exe
Cannot open assembly '/media/WindowsXP/WINDOWS/system32/sol.exe': File does not contain a valid CIL image.
```

File extensions don't mean anything.

---

### Post by juancarlospaco on 2009-06-20
...Then we discover a Bug on " file " *(?)*
by the way i sucessfully created .deb containing infected mono .exe's,
installed, and run it, this feeling don't like me.

---

### Post by directhex on 2009-06-21
> **juancarlospaco said:**
> ...Then we discover a Bug on " file " *(?)*
by the way i sucessfully created .deb containing infected mono .exe's,
installed, and run it, this feeling don't like me.

Define "infected". You've found a security hole in Mono's JITter? Or are you just talking crap?

---

### Post by sydbat on 2009-06-22
Maybe juancarlospaco is a victim of this - [http://boycottnovell.com/wiki/index.php/Main_Page](http://boycottnovell.com/wiki/index.php/Main_Page) (discussed in this thread - [http://ubuntuforums.org/showthread.php?t=1189210](http://ubuntuforums.org/showthread.php?t=1189210))...

---

### Post by monsterstack on 2009-06-22
> **rookcifer said:**
> It's already happened to several distros, with Fedora being the most [recent example]("http://www.thetechherald.com/article.php/200835/1847/Fedora-Project-and-Red-Hat-hit-by-intruders-%E2%80%93-why-the-delay-in-disclosure").

And even without repo compromises, one must still ask, "who watches the watchers?"  It was demonstrated over 20 years ago by Ken Thompson (one of the creators of Unix) that one can hide backdoors in compilers and make them undetectable -- literally impossible to find even if one checks the compiler *source*.  Thompson himself [created]("http://scienceblogs.com/goodmath/2007/04/strange_loops_dennis_ritchie_a.php") a Unix backdoor that gave him full access to any Unix system compiled with a specific compiler and only told the world about it during his 1983 [Turing award acceptance speech]("http://cm.bell-labs.com/who/ken/trust.html"), some 15 years after he did it.

I suppose the lesson to be learned is you can only have a limited amount of trust in any sophisticated software project like an OS, whether it be closed-source or open-source (though open-source would be less susceptible by nature but still not bullet proof).  Unless one can go through every line of the ~9 million lines of code in the kernel oneself to check for every possible security hole, one can never be sure.  Even seasoned security experts cannot spot all the errors.  And then you have to take into account not only a distro's package repostory but also the CVS, subversion, and git repositories from where the code is originally stored.  It's possible for an intruder to crack those repos and insert malicious code even without the developer's knowledge.  Of course such code probably wouldn't last all that long before it was discovered, but it would still be feasible for it to "get into the wild."

And this is all not even taking into account compromised hardware.  It's perfectly feasible that CPU manufacturers, for instance, could allow compromised microcode to be released.  This would allow total system compromise no matter the OS being used.  This is a concern due to the fact that some chips are manufactured in countries that aren't really that friendly to the west.

The only thing the end user can do is take the basic security steps (firewall, don't run as root, only install from distro repos, etc) and hope that the "watchers" are trustworthy.  That's why "viruses" and the like should be the least of a Linux/BSD user's worries.  They aren't really a threat at all.  The biggest threat is from compromised or incompetent source code.

I hadn't heard of this before. Thanks a lot, it was really interesting to read up about all that stuff.

---

### Post by nanderv on 2009-11-26
> **smartboyathome said:**
> You shouldn't have done anything; as of this moment, viruses are almost non-existant in Ubuntu (the most recent one rendered harmless years ago). Why do you think it is used on 66% of servers? ;)
There are virusses.. But they can only harm your wine directory..
I think WineHQ should also add a list of virusses that work under wine...

---

### Post by HeadHunter00 on 2009-11-30
> **smartboyathome said:**
> You shouldn't have done anything; as of this moment, viruses are almost non-existant in Ubuntu (the most recent one rendered harmless years ago). Why do you think it is used on 66% of servers? ;)
Interesting. :-k

---

### Post by HeadHunter00 on 2009-11-30
> **nanderv said:**
> There are virusses.. But they can only harm your wine directory..
I think WineHQ should also add a list of virusses that work under wine...
Even more interesting:-k

---

### Post by doas777 on 2009-11-30
> **HeadHunter00 said:**
> Even more interesting:-k

just be careful of terminology. ubuntu is reasonably secure agains viruses specifically, but what most people mean when they say "viruses" is actually "malware", and no ubuntu is not immune to all forms of malware.

---

### Post by buubonic on 2009-12-02
Bottom line is *nix is not immune to all forms of malware and furthermore is not immune to invasive tacticts i.e. hijacked servers. does not happen often but it has happened before [as pointed out here]("http://www.thetechherald.com/article.php/200835/1847/Fedora-Project-and-Red-Hat-hit-by-intruders-%E2%80%93-why-the-delay-in-disclosure") and i would have to support the idea of terminology being of utmost importance. computer science is a science afterall and any science is highly dependent on the understanding and correct use of terminology.

---

### Post by iamgeniusrnti on 2009-12-02
Well as a newb, it has always intriged me Ubuntu is tauted as a fairly bullet proof system against malware.  And just for the record, I define malware as simply a malicious program and a virus as a malicious program designed to infect/propagate.
 
After installing Ubuntu on another partition, I disabled my Dansguardian on Smoothie and spent the last couple evenings going to every bad site, running videos from FB I knew to be infected, downloading and installing fake spyware scanners, going to warez sites and basically doing every dumb thing I could possibly think a dumb person could do.  I even gave the malware a chance and installed Wine.  I answered yes if a website wanted to scan my computer and surprisingly, I couldn't even get the website to lie to me.  I went to finallyfast.com and said my computer was too slow.
 
No matter what I did, I could not get Ubuntu to crash, self destruct or otherwise take over the world.  As a matter of fact even Wine didn't get pissed off.
 
I am sure there are Linux viruses and some bad codes I could run to wipe out my system but as far as typical internet websites injecting malware into machines via video trojans, I don't see Ubuntu being vulnerable to that... at a minimum, I would have to know exactly what I'm doing and somehow recompile the virus to make it work.

---

### Post by geezbeez on 2009-12-04
Linux is pretty much strong against viruses, but KDE and GNome are not as resistant.
Thery are still pretty good but not as strong as the underlying linux.
I'm a little uncomfortable with the way in ubuntu KDE ot Gnome is more integrated to linux.
You cant just boot to a lower run level. or easily remove gnome or kde and reinstall it without a full OS reinstall like you can say with slackware or gentoo. 
Its possible to pick up malware which will exploit KDE or Gnome , but gnnome or KDE should only be running under the account you log on as so it will only spoil the one account unless you do something stupid. To fix things if you do ever get malware on your ubuntu machine its best when you install to create a two spare accounts which you never use for webbrowsing or anything, just there incase stuff gets broken, one for fixing things and one to log on to use when you upgrade and do sudo operations. You should also set the root password to something secret just incase you need to use it 
If you suspect you do have malware you can log on under spare account, sudo to root , delete your main account home dir saving only your personal files you need to keep and recreate the account , put files back.
Also worth noting if you suspect something is a miss you should be able to do ctl,shift,f2 to get a new terminal to log on and check behind scenes whats going on. ctl,shift f1 or is it f6 to go back to original term

---

### Post by geezbeez on 2009-12-04
File extensions dont mean anything to linux true.
FIle associations are however crucial to way KDE,gnome work??? Do a web search. 
Its not just wine thats the problem.
P.S 
Im not slagging gnome, KDE. think about it theres no way around what they do except keeping the distinction between underlying os and the desktop environment be it KDE, gnome xfce whatever which has never been there in Windows.

---

### Post by dmengo on 2009-12-04
[COLOR=black][FONT=Verdana]Wikipedia has a write-up on different types of Linux malware.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][[COLOR=blue]http://en.wikipedia.org/wiki/Linux_malware[/COLOR]]("http://en.wikipedia.org/wiki/Linux_malware")[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I feel as if many people have a false sense of security when it comes to the Linux and Mac operating systems. Even though the vast majority of computer viruses are written specifically to target Windows systems, the Mac and Linux computers will still have the usual OS security vulnerabilities (buffer overflows, kernel exploits, etc.) that frequently need patched.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Take for instance the example of running an Apache web server on Linux. You would always want to make sure the Apache web service and the Linux OS are patched and up-to-date.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Keep in mind that almost all the malware written today is done by organized crime.[/FONT][/COLOR]

---

### Post by foldingstock on 2009-12-04
> **juancarlospaco said:**
> **[SIZE="3"]Mono[/SIZE]**
it can bloat your system with .EXEs and .DLLs on Linux
*.EXEs and .DDLs can be infected, so you are running infected programs*

This is nonsense. If someone could gain access to your system, they could rather easily configure "/bin/ls" and "/usr/bin/top" to use an alias file that would prevent them from displaying certain information. For example, a custom bot program could be installed to "/home/$USER/secretbot" and, by creating an alias in "ls" and "top," it would be completely invisible on disk and running in the background. The same could be done with other programs, such as netstat, to hide outgoing/incoming connections.

Linux in general is not wide open, but do not be fooled into believe Linux=secure. Also, even though "viruses" are not a major threat to Linux, malware does exist. Do some research on rootkits sometime.

Security is a process, not a product.

---

### Post by yahia999 on 2010-06-13
yeah i got you rpoint, so i can just simply download ANY UBUNTU app without worrying, or have you anything that denies that??? :confused: :confused:
i'm still new, it's my first day so i very much appreciate help... :p :p :p

---

