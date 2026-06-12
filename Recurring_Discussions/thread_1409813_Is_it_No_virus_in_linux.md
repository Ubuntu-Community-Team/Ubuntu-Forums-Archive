---
title: "Is it No virus in linux??"
date: 2010-02-18
forum: Recurring Discussions
---

### Post by navaneethan on 2010-02-18
Is it no virus in linux?? why? how? ...what is the reason behind it for your answer??

---

### Post by lisati on 2010-02-18
Have a look here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by switch10 on 2010-02-18
What?  

No there are no viruses in Linux (debate-able).  Linux is run on .6% of PC's in the world.  No one writes Linux viruses because it is pointless.

EDIT although most servers do run some kind of *nix......  We just don't get them..

---

### Post by aviedw on 2010-02-18
None the less, let us not become victims to a false sense of security. I simply compute with the same level of caution as if i were on a windows machine.

---

### Post by sxmaxchine on 2010-02-18
there are viruses for linux just a very very small amount, and it is because there are not many linux users

---

### Post by v1ad on 2010-02-18
yes  viruses can be created for linux but due to open source code they can be handles a lot easier also.

---

### Post by OrangeCrate on 2010-02-18
> **The Truth About Linux and Viruses**

Conventional wisdom says that a virus scanner is one of three protections necessary these days for computers connected to the Internet. (The other two being a spyware scanner or two, and a trainable spam filter.) The same wisdom also says that the only reason Linux and Macintosh computers don't see the same level of virus attacks as Windows PCs is because Windows PCs are so much more prevalent.

While this may be partly true, it's not the whole reason. According to various virus lists, there are less than 100 known viruses for Linux, none of which spread the way a Windows virus does. Meanwhile, there are thousands and thousands of Windows viruses. With the so-called discovery of a Linux/Windows virus, more light is being shined on the subject of Linux security.

But it's easy to protect yourself in Linux, once you know a few things about viruses under the operating system.

1. If you run Linux and only Linux, you do not need antivirus software. In its efforts to make Windows easier to use, Microsoft simplified the process of running executables under its operating system many years ago. Not only can a user launch a program by clicking an e-mail attachment, but it's possible for an executable to launch automatically just by hitting the preview pane of some email packages, including older versions of Outlook and Outlook Express. Scot's Newsletter Forums member Nathan Williams has provided an excellent FAQ for the All Things Linux forum explaining why Linux when used alone does not need antivirus protection.

Under Linux the steps for launching an executable from an e-mail are separate, discrete steps. A user would have to read the email, save the attachment, give the attachment executable permissions, and then run the executable. And to be truly damaging, the latter two would have to be done as root &#8212; not something informed users would allow. (For more information see Ch- Ch- Changing File Permissions.)

2. If you dual boot Linux and Windows and get a virus-infected mail in Linux, it can NOT jump to your Windows partition. Nor can it spread over the local network to other systems. You can even store the attachment in your /home directory and open the zip or click the file, and it will be dead in the water. Windows executables won't run under Linux. Linux files need to be granted permission to become executable. And even then, it can't spread beyond the home folder. (This is also why Linux AV programs do not have a "live guard" module in them &#8212; the virus does not execute or move.) You could even leave a virus executable there as long as you wanted to without risk. Windows will not get infected, unless you deliberately copy the virus to your Windows partition.

3. If you dual boot, however, you better get a good antivirus program for Windows. Microsoft's operating system and its bundled applications, Outlook and Internet Explorer, offer users powerful functionality in their attempts to be easy to use and easy to update. As a result, it's all too easy for virus writers to exploit the same functionality in a malicious way. Don't leave them an opening. Install an antivirus program and keep it updated.

4. The only time you'll need a Linux antivirus program is if you're running a mail server. And that's just good social behavior. It's not to protect your Linux server or client computer so much as to make sure you don't pass a virus on to a Windows system.

Think about it this way: If you have two warehouses, and you use the first one to store cheese, are you going to place mouse-traps in the second one where you only store stainless steel? I mean, be reasonable, mice do not eat stainless steel! So don't let antivirus vendors make you unnecessarily paranoid.

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

---

### Post by bapoumba on 2010-02-18
Moved to Recurring.

---

### Post by juancarlospaco on 2010-02-18
> **navaneethan said:**
> Is it no virus in linux?? why? 

Why not?

---

### Post by navaneethan on 2010-02-18
> **juancarlospaco said:**
> Why not?
we can create virus and we can create antivirus Am i correct?

---

### Post by juancarlospaco on 2010-02-19
> **navaneethan said:**
> we can create virus and we can create antivirus Am i correct?

Both wont work on Linux.

---

### Post by del_diablo on 2010-02-20
> **navaneethan said:**
> we can create virus and we can create antivirus Am i correct?

Why:
*We got a proper infrastructure
*The security is placed close to the kernel, not in userland.(userland = your applications, running stuff outside of the kernel, i think. Then we got your "home" which again is separate from the userland).
*We actually PATCH and FIX the problems(there is big lists of non-patched holes for MS)
*We got more people looking for holes(all paid)
*Did i mention how the system is set up? A reboot would kill anything you manage to get working, in Windows a reboot is what is needed to get a virus kicking into level 2
*The only viruses that exists are lab viruses, which would not have worked in real life
*And most distrobutions got secure software sources(our grand repos, and there is more "updated" distroes such as Archlinux)

So basically it runs down to:
*Design
*Software system
*Windows != OS, but Windows is ANOTHER OS. What troubles one, does not have to destroy the other.

---

### Post by navaneethan on 2010-08-10
Is it wrong??

---

### Post by navaneethan on 2010-08-10
why not ? we can make it work depends what linux supports??

---

### Post by Legendary_Bibo on 2010-08-10
> **navaneethan said:**
> why not ? we can make it work depends what linux supports??

Wait, are you asking how to engineer a virus for Li-nucks?

---

### Post by Autonomous_user on 2010-08-10
> **switch10 said:**
> What?  

No there are no viruses in Linux (debate-able).  Linux is run on .6% of PC's in the world.  No one writes Linux viruses because it is pointless.

EDIT although most servers do run some kind of *nix......  We just don't get them..


That number is highly suspect. The number of linux netbooks alone disproves that number....unless netbooks and tablets are for some reason excluded. We probably have between 1% and 2% in America and a lot more in Europe and Asia. 

That isnt the only reason viruses are not written for Linux though....besides the smaller audience there is better security built in to Linux than windows. Windows7 is a tiny bit more secure when it asks permission now, but its still running with full privileges all the time.....and it seems to be loaded with spyware from the very start. Data mining for the corporations.

---

