---
title: "Ubuntu desktop not much more secure than Windows?"
date: 2013-01-10
forum: Recurring Discussions
---

### Post by Rickubun2 on 2013-01-10
A buddy of mine sent me this YouTube vid as prove that Linux is just as vulnerable to malware as Windows, but wouldn’t you be asked for root access by the system to run this script or at least get a warning message? Is the demo clearly rigged?
  
[http://www.youtube.com/watch?v=9HxFGQ8OpYw](http://www.youtube.com/watch?v=9HxFGQ8OpYw)

---

### Post by haqking on 2013-01-10
it is a demonstration of privelege escalation through exploitation of the .desktop file.

This is well known

you can read more info here [http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

All end user OS are only as secure as their user, no end user OS is "secure" they are all roughtly EAL4 by common criteria making them all usable and functional and secure with reason, anything more and they lose function or usability.

As a whole Linux is not as susceptible to "malware" as Windows but it is not immune.  However malware is often nuisance based and not necessarily exploitation based and one of the many methods of gaining access to a system.

---

### Post by grahammechanical on 2013-01-10
1) Do not let anyone pack your suitcase for you when returning from a trip abroad.
2) Do not carry anybody else's stuff through customs.
3) Do not open email attachments from anyone you do not trust.
4) When someone says it is impossible, don't believe them. Generals who assume that something is impossible usually lose the battle.

Regards.

---

### Post by Jakin on 2013-01-10
Notice how many stars had to align for the Distro used to become infected.

On Windows, surf the wrong url linked Website, and you may be infected.

As mentioned, Linux isn't as susceptible to malware, no-one ever said completely immune.

---

### Post by szymon_g on 2013-01-10
> **grahammechanical said:**
> 1)
3) Do not open email attachments from anyone you do not trust.

unless you encrypt/signature every message (and your friends are doing the same) with pgp-like solutions, you cannot know is that email sent by the person who claims it.

---

### Post by pqwoerituytrueiwoq on 2013-01-10
i don't believe modern version let you execute a .desktop file without making it executable
i am using xubuntu 12.10 and i get this dialog window which would raise a red flag

i would me more concerned about java letting something get command line access than a email attachment
this is why i never install java/icedtea unless it is absolutely necessary

firefox lets you password protect your saved passwords and stuff if you choose

with windows you can get infected from opening regular files like a .doc (ms-word) as long as something does not get command line access on linux it is safe

---

### Post by Rickubun2 on 2013-01-10
> **haqking said:**
> it is a demonstration of privelege escalation through exploitation of the .desktop file.

This is well known

you can read more info here [http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

  

Great read, thanks for the info!

---

### Post by 3rdalbum on 2013-01-12
This video you linked to, from 2009, actually demonstrates how much more secure Ubuntu is than Windows or the Mac OS.

Shortly after the first public announcement of this little scenario, the Gnome developers implemented the warning dialog that pqwoerituytrueiwoq posted about in message #6 above.

If this was Windows, you'd need to wait up to a month.

If this was Mac OS X, you'd probably be waiting between three and six months.

There's also every possibility that Microsoft and Apple wouldn't bother about patching this, as it requires the malicious program to already be running, i.e. the user must double-click on it. The user also needs to be a sudo'er otherwise it won't work. They also must be using one of the affected desktops; not all Linux desktops are affected.

The flaw has long since been fixed in all distros. There's also a movement away from gksudo and toward Policykit (nothing to do with that flaw, just a general tighting of security that began in 2007) which would probably make this all harder to do.

---

### Post by QwUo173Hy on 2013-03-12
I'm curious, since Windows has been using User Access Control since vista, isn't it basically on par with Ubuntu now? Isn't that the same as sudo?

Apologies for digging up an old thread but it seems wrong to clutter the forums with similar threads.

---

