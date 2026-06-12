---
title: "[SOLVED] Which Java to install?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Kenza on 2008-06-22
there are a few Java RTE's to install, but i don't know what the 3 letters at the end mean

Java runtime environment using GIJ <---those 3 letters
Java runtime environment with GCJ
Java runtime environment using GIJ (headless version)

---

### Post by rockerphil on 2008-06-22
here's what i'd do, i prefer java6, so run this in terminal, it should do the job

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin


it's the closed source version of Java from Sun, but it does well for me on my Gutsy insall. hope this helps

---

### Post by Kenza on 2008-06-22
Thanx, it does, because that's what version i was trying to install, but couldn't figure out how to do it manually after i downloaded =)

---

### Post by Kenza on 2008-06-23
Well, i thought it did, but that command goes to an old or "obsolete" file, it did a rebuild on my lists, but then said that program was no longer available.

---

### Post by Nepherte on 2008-06-23
Is the multiverse repository enabled?

---

### Post by Kenza on 2008-06-23
I'm a real n00b here, i'm not sure =S Went to package manager to check (figured it must be an option), but nope, don't see it

---

### Post by Nepherte on 2008-06-23
To see if it's enabled, navigate to system > administration > software resources (or something that looks like it, so not synaptic!). On the first tab "Ubuntu Software" multiverse should be checked.

---

### Post by Kenza on 2008-06-24
Yep, it was checked, i guess by default =) thanx

Still don't know how to get the basic Java since that command that was given to me earlier didn't work:

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin

(Is that an old version? when i tried that command it said it might be "obsolete")

---

### Post by tinny on 2008-06-24
What version of Ubuntu are you using?

Do you know how to use synaptic package manger?

Search for "sun-java6" and post a screen shot of the results.

Also try to just install the jre on its own.

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6-jre

```

If there are problems post the results back here.

---

### Post by Kenza on 2008-06-24
Yes, i have used the package manager for a few installs, have Ubuntu 8.04, i just got confused as i had earlier posted about what the Acronyms at the end of the files meant and didn't wanna' mess anything up :confused: <---i have already messed up a few times pretty bad :( But it seems those were the wrong files anyway (They were listed on the package manager when i did a search for Java)

Edit: BTW, i am getting ready to try the commands u gave me, will let u know and ty


> **Kenza said:**
> there are a few Java RTE's to install, but i don't know what the 3 letters at the end mean

Java runtime environment using GIJ <---those 3 letters
Java runtime environment with GCJ
Java runtime environment using GIJ (headless version)

---

### Post by Kenza on 2008-06-24
Well, no SS's to post, i did it through the terminal and everything worked GREAT, thanx for the help! Maybe this will help another n00b like myself too :)

---

### Post by tinny on 2008-06-24
A couple of checks you can do to make sure its all working.

```

java -version

```

Should give you some output like this:

```

java version "1.6.0_05"
Java(TM) SE Runtime Environment (build 1.6.0_05-b13)
Java HotSpot(TM) Client VM (build 10.0-b19, mixed mode, sharing)

```

It would probably be a good idea for you to check if java is working within firefox.

[http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")

Browse to this site and if all is well you should see the Java duke doing a dance for you. If these two things are working you can be quite confident that java is working on your system.

---

