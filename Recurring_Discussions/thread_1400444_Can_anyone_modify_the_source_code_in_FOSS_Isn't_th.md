---
title: "Can anyone modify the source code in FOSS? Isn't that a security risk?"
date: 2010-02-06
forum: Recurring Discussions
---

### Post by Kenny_Strawn on 2010-02-06
Here's the ultimate kill of open source software: Writing malware into the code of otherwise useful software.

Take the Linux Kernel, for instance. It's a very useful operating system kernel to begin with. But what if a hacker made malicious changes to the kernel's code? What can be done?

It makes sense, therefore, to safeguard FOSS from harm. This is why the community needs to constantly search for and disable virus code, and constantly ban such malicious users from the community.

Is anybody with me on preventing this from happening?

---

### Post by Sporkman on 2010-02-06
Let's git 'em!!

---

### Post by jrusso2 on 2010-02-06
Hopefully the code is being audited before going into something as important as the kernel.

---

### Post by chewearn on 2010-02-06
Yes Suh! 

(me taking pitch fork out from the barn)

---

### Post by dragos240 on 2010-02-06
There was a thread all about this a while back.

---

### Post by gsmanners on 2010-02-06
Back doors have been submitted to the kernel team many many times, and they always catch them within minutes.

---

### Post by Sand &amp; Mercury on 2010-02-06
In most projects (especially the Linux kernel) code that goes in does get checked over before it goes into the trunk. If someone snuck bad code in, someone else would notice it.

[http://www.youtube.com/watch?v=4XpnKHJAok8](http://www.youtube.com/watch?v=4XpnKHJAok8) - Have a peek at this video and Linus goes over the general idea of quality control at a few points (about halfway through, iirc)

EDIT: It's about 17 minutes in.

---

### Post by kidux on 2010-02-06
That's kinda the point of FOSS, to open up the inner workings and let everyone see exactly what is in the source code, for the explicit purpose of preventing malicious or outright bad code from getting in.

---

### Post by snowpine on 2010-02-06
Think of the children!!!

---

### Post by Frak on 2010-02-06
Sometimes they find them in minutes. Sometimes, they go unnoticed for years.

---

### Post by NCLI on 2010-02-06
Source? I've only heard of non-intentional security holes so far.

---

### Post by loell on 2010-02-06
> **Kenny_Strawn said:**
> 
Is anybody with me on preventing this from happening?

No.. You're all alone. :p

---

### Post by Twitch6000 on 2010-02-06
I guess you dont releaize that code gets reviewed before submitted into the kernal..

Maybe not as good as the openbsd kernal,but I doubt malware would get into the offical kernal. Maybe a recompiled kernal hosted by a unknown source,but you shouldn't even use it.

---

### Post by Kenny_Strawn on 2010-02-06
Yes, but what about other pieces of FOSS that are more popular (say, if a keylogger was submitted as code for OpenOffice.org)?

---

### Post by blueshiftoverwatch on 2010-02-06
> **Kenny_Strawn said:**
> Here's the ultimate kill of open source software: Writing malware into the code of otherwise useful software...what if a hacker made malicious changes to the kernel's code?
That's not really much of a security hole in reality. Firefox has a very large market share and it's pretty secure in comparison to IE which is closed source.

---

### Post by Kenny_Strawn on 2010-02-06
> **blueshiftoverwatch said:**
> That's not really much of a security hole in reality. Firefox has a very large market share and it's pretty secure in comparison to IE which is closed source.

I know that FOSS is typically more secure than proprietary software, but only the finished product. The source code isn't that secure, because it can easily be manipulated to do a malicious thing.

However, I'm sure the community catches those things. I'm more on the side of The FRAK, because I do believe malicious code gets caught by the open source community.

---

### Post by mamamia88 on 2010-02-06
> **Kenny_Strawn said:**
> I know that FOSS is typically more secure than proprietary software, but only the finished product. The source code isn't that secure, because it can easily be manipulated to do a malicious thing.

However, I'm sure the community catches those things. I'm more on the side of The FRAK, because I do believe malicious code gets caught by the open source community.
i'm not sure i understand you.  in my understanding all open source means is that you are free to view and modify source code as long as you make your changes public.  that does not mean that your changes will be added to the official kernel but you are free to use your changes.  am i right here?

---

### Post by kidux on 2010-02-07
> **Kenny_Strawn said:**
> I know that FOSS is typically more secure than proprietary software, but only the finished product. The source code isn't that secure, because it can easily be manipulated to do a malicious thing.

However, I'm sure the community catches those things. I'm more on the side of The FRAK, because I do believe malicious code gets caught by the open source community.

FOSS by it's very nature of being open is more secure from start to finish because there are thousands of people seeing the code and catching/fixing problems as they pop up. Not only that bu the way it's implemented is safer because it's freely available and if any problems arise it's reported and fixed quick.

---

### Post by Frak on 2010-02-07
> **kidux said:**
> FOSS by it's very nature of being open is more secure from start to finish because there are thousands of people seeing the code and catching/fixing problems as they pop up. Not only that bu the way it's implemented is safer because it's freely available and if any problems arise it's reported and fixed quick.
*Unless the software is maintained by a novice and is not popular enough to attract multiple developers to review the source.

Blanket statements are bust. Plus, very large projects, like the Linux kernel, are much more apt to have malicious code accepted into them. Linux probably doesn't have them, because as he states, if he has too many emails at a time in his mailbox over patches, he just deletes them all. Malware avoided!

---

### Post by Tibuda on 2010-02-07
Not everybody have commit permissions. The code is out there for you, you can send patches to someone with commit rights, but there's no guarantee the guy will read all te code.

---

### Post by Twitch6000 on 2010-02-07
> **Kenny_Strawn said:**
> Yes, but what about other pieces of FOSS that are more popular (say, if a keylogger was submitted as code for OpenOffice.org)?

again most foss software gets reviewed when code is placed.

Atleast foss software with someone behind it.

---

