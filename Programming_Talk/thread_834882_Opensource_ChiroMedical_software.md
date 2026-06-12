---
title: "Opensource Chiro/Medical software?"
date: 2008-06-19
forum: Programming Talk
---

### Post by jtsmith on 2008-06-19
Hello,
This is Jedidiah Smith in Alaska, and I have just installed Ubuntu on a box here, trying to get back into Linux.  I used to use Linux about 8 years ago at work, but have not used it for many years - boy things change!

I have a funny question, but can anyone point me to projects that may have been started in the open source community for either chiropractic or medical software?

I always thought I'd go into computer science, but life takes us down interesting paths, and now I am a 27 year old upper cervical chiropractor.  After a dissapointing time with Windows Vista 64bit, I am very interested in running Linux on all my office computers. (I used to work at an ISP in my high school and early college days, and remember how stable Linux was.)
However, the only drawback is that I can't seem to find the kind of application I need for Linux.

At the office, we currently Run EZBIS software - [www.ezbis.com](www.ezbis.com) - and it takes care of all billing, patient database, services rendered, etc.  Does anyone know if there is a similar program for Linux?  If not, I would be willing to donate time and/or money (and I'm sure other doctors would be as well) to programmers willing to help make an open source chiropractic type billing / database / service software.  I am envisioning something that we could eventually offer free of charge to any doctors or health care centers, and especially the colleges.  I think we could help keep health care costs down by doing something like this.

Sorry for the ramble, but my first post here, and I am excited to be back using Linux again.
Thanks for any help or leads on this project, or tips on where I should channel my energy next with this idea.
Sincerely,
Jedidiah T. Smith, D.C.
Anchorage, Alaska

---

### Post by LaRoza on 2008-06-19
That software might work in [wine]("http://www.winehq.org/")

To test it out run this command:

```

sudo apt-get update && sudo aptitude install wine && sudo apt-get clean

```

(Highlight it, and middle click in a terminal. Middle click can be pressing both mouse buttons at once, or pressing the wheel)

Then, use the install disk/program for that software and run it with wine (right click it, and select to run it with wine, or the custom command "wine").

---

### Post by Can+~ on 2008-06-19
Could you say what is specifically needed from that application? I tried reading the webpage, but the web design threw me back into the 90s, and I ran.

---

### Post by marialice on 2008-06-20
Take a look at [gnumed](http://www.gnumed.org). 

> The GNUmed project builds an open source Electronic Medical Record. It is developed by a handful of medical doctors and programmers from all over the world. It can be useful to anyone documenting the health of patients, including but not limited to doctors, physical therapists, occupational therapists, ... 

I'm not sure if it does what you need, but it's a start :)

Edit: there's also [care2x](www.care2x.org), targeted at hospitals (very impressive). They also have a practice managment module, which can be installed separately.

And even more:
see [http://linuxforclinics.sourceforge.net/mainsite/resources.php](http://linuxforclinics.sourceforge.net/mainsite/resources.php) for links to

* FreeMED and Remitt
* ClearHealth
* OpenEMR
* FreeB
* Res Medicinae
* CYBOP

---

### Post by jtsmith on 2008-06-20
Wow, that was fast.  Thanks for the responses.  :-)

I will check out all those links tomorrow when I have some time; perhaps they are what I am looking for, or at least a good start.  No reason to reinvent the wheel if it's already there!

Basically the software needs to be able to print out a HICFA form, which is the standard form used by insurance companies as well as medicare.  It has the patient's name and other data, along with the ICD9 codes for diagnosis, CMPT codes for service rendered along with fee charged for each, and the physical location of the service.  It is all pretty much straight forward, and has to be in the specified order because optical machines read (scan) the HICFA forms at the insurance company.

Hope that helps to see what I'm looking for - thanks again for the links, and I will see what I can come up with.
Sincerely,
Jed

---

### Post by duuchung on 2008-06-21
I read in the paper that the Hong Kong Medical Association has contracted out a project using open source software. I thought that might be a e-project for communication between members or for handling of records in clinics. I am not a doctor. I do not know the details. Anyway on completion, the system can only be used by members of the Association.

It is good that a public body of learned people has endorsed open source software.

regards,
duuchung

---

### Post by shilbert on 2008-09-12
Take a look at [gnumed](http://www.gnumed.org). 


Hi, I am from GNUmed. If you try GNUmed on Hardy make sure you use the version 0.2.8.10 from the repository hardy-proposed.

This version has many bugfixes and sits there until it will be moved to hardy-updates.

You can install through synaptic (just enable the hardy-proposed repository there).

Sebastian

---

### Post by yinhsi on 2008-12-10
Hi Dr. Smith,

I too am a chiropractor/Acupuncturist practicing in Maine and using ez-bis.  I just switched to linux and am trying to get ez-bis to run on it with wine.  I think I'm getting close to making it work.  Perhaps if there are enough of us into this, ezbis will help?  
Nice to know I'm not the only one wanting to do this!

All the best,

MJ

---

### Post by Docaltmed on 2009-01-27
What is it with all of us chiropractor/acupuncturists jumping onto Ubuntu?

Anyway, I got SOAPware to run successfully under VirtualBox with little difficulty.

I'm now looking at gnumed as my next EMR.

---

### Post by shilbert on 2009-05-07
GNUmed currently does not provide billing. there are however a number of US-centric EMR that do that. GNUmed can however interact with other EMR so it is possible to use seperate applications for billing and tracking patient's health.

---

### Post by locutus42 on 2010-11-16
bump

---

