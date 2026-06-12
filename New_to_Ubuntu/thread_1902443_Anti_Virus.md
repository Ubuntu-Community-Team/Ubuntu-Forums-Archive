---
title: "Anti Virus"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by JeremySchubert on 2011-12-30
I realize that most malicious programs are created to attack windows.  However, I assume that hackers might troll computers with any operating systems to see what they can find.  With that in mind, is there a need for an anti virus on Ubuntu.  
Thanks,
Jeremy

---

### Post by howefield on 2011-12-30
Here's a link which might help you make up your mind.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by guyver_dio on 2011-12-30
I don't see the need, it would also defeat one reason I switched to ubuntu, I was sick of the OS being weighed down with antiviral and firewall software that used alot of resources in the background. 

I guess if I had to think about what I'm most fearful of viruses doing is obtaining personal information like my bank details. They mainly do this by exploiting open ports. So if I was to do anything I'd probably go with a firewall and not worry about a antiviral scanner. But honesty I think you'll be quite safe without any of it.

---

### Post by sammiev on 2011-12-30
If you move items over different OS like Windows, I would suggest a scanner.

---

### Post by lolpenguin on 2011-12-31
You really only need AV to not get your Windows computer infected, but do take caution when installing software from third-party sources. Remember when kernel.org got some malware?

---

### Post by chipbuster on 2011-12-31
I run periodic scans of ClamAV just as a service to some of my Windows-running friends (basically, all of them). I haven't gotten anything yet, but I've heard stories where people on Macs ran antiviral scans and found 10 or 20 pieces of Windows malware squatting on their systems, which could be accidentally passed on.

---

### Post by Paqman on 2011-12-31
> **chipbuster said:**
> I run periodic scans of ClamAV just as a service to some of my Windows-running friends (basically, all of them).

You might want to think about switching to a better AV product if that's important to you. ClamAV is very poor quality.

---

### Post by chipbuster on 2011-12-31
Anything you'd recommend in particular? I haven't seen any benchmarks for Linux antivirus programs (unless the windows ones apply, in which case I have)

---

### Post by neostar123 on 2011-12-31
I don't see any need but if you want to scan your windows drive with AV from linux you can use Avast Home Edition..Its easy to use..

---

### Post by Paqman on 2011-12-31
> **chipbuster said:**
> Anything you'd recommend in particular? I haven't seen any benchmarks for Linux antivirus programs (unless the windows ones apply, in which case I have)

Avast? AVG? There's probably others, but I don't use AV on Linux.

---

### Post by Ms. Daisy on 2011-12-31
[QUOTE=guyver_dio]I don't see the need, it would also defeat one reason I switched to  ubuntu, I was sick of the OS being weighed down with antiviral and  firewall software that used alot of resources in the background. 

I guess if I had to think about what I'm most fearful of viruses doing  is obtaining personal information like my bank details. They mainly do  this by exploiting open ports. So if I was to do anything I'd probably  go with a firewall and not worry about a antiviral scanner. But honesty I  think you'll be quite safe without any of it.     [/QUOTE]

To guyver_dio, if you're concerned about personal information like bank details, you also need to harden  your browser. Use NoScript, Adblock. Use a new browser session for banking, then close the browser when done.  Yes, I'd recommend a firewall for sure.  [Apparmor]("http://ubuntuforums.org/showthread.php?t=1008906") would limit the damage any nasty stuff you encounter could do, but it's got a bit of a learning curve.

To guyver_dio & chipbuster & JeremySchubert: I would recommend that you read the [Basic Security Wiki]("https://wiki.ubuntu.com/BasicSecurity"). Security on Ubuntu is different than how security is usually approached on Windows.

As far as anti-virus, see [this thread]("http://ubuntuforums.org/showthread.php?t=1890989") for a few suggestions on Linux products.  Basically the crux is that the  free AV software available  will probably throw out mostly false  positives if anything, and will just be scanning for Windows malware  anyway.

[QUOTE=lolpenguin]but do take caution when installing software from third-party sources. [/QUOTE] +1

---

### Post by lisati on 2011-12-31
As others have hinted at, your best defence begins with being smart with what you allow on your computer. No matter how good the AV tool you install, it's only as good as its database. There's no guarantee that it will be able to detect a brand new piece of malware - it probably won't.

Some of the AV products I've looked at have a rescue CD available, including [AVG]("http://www.avg.com/us-en/avg-rescue-cd"). The last time I checked it out, AVG's was a Linux based live CD.

---

### Post by Lalaith on 2011-12-31
In case of third-party software I would like to try (as lisati said, "being smart with what you allow in your computer"), Is it an option to try it inside a Virtual Machine?

---

### Post by howefield on 2011-12-31
> **chipbuster said:**
> Anything you'd recommend in particular?

Bitdefender is pretty decent.

Avast and AVG are also good, however in the case of AVG, be aware that is is command line only, there is no GUI for it.

---

### Post by donkyhotay on 2011-12-31
I'm amazed this thread hasn't gone to recurring discussions already. Anyways here is my regular 'antivirus on linux post'. Suffice it to say, you really only need antivirus on linux if you're trying to prevent forwarding viruses back to a windows machine.


Master Foo and the Nervous Novice
There was a novice who learned much at the Master's feet, but felt something to be missing. After meditating on his doubts for some time, he found the courage to approach Master Foo about his problem.

Master Foo,he asked why do Unix users not employ antivirus programs? And defragmentors? And malware cleaners?

Master Foo smiled, and said When your house is well constructed, there is no need to add pillars to keep the roof in place.

The novice replied Would it not be better to use these things anyway, just to be certain?

Master Foo reached for a nearby ball of string, and began wrapping it around the novice's feet.

What are you doing? the novice asked in surprise.

Master Foo replied simply: Tying your shoes.

Upon hearing this, the novice was enlightened.

---

### Post by Dangertux on 2011-12-31
Master foo never heard of compliance audits? AV is a requirement for most production audits. 

Also +1 to bitdefender its pretty good.

---

### Post by jockyburns on 2011-12-31
Probably the biggest danger for Linux users is passing on Win viruses to Win users via email. A Win virus won't infect Linux so you can usually open attachments you receive. But should you forward the email on to your friends and they are using Windoze , then they could pick up the virus embedded in the attachment. I never forward emails anyway so probably doesn't matter to me.

---

### Post by sammiev on 2011-12-31
+1 to [BitDefender]("https://help.ubuntu.com/community/BitDefender") as well. Seems to update the fastest and runs quick. Avast and AVG are great as well. :)

---

