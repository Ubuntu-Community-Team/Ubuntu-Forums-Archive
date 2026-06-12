---
title: "Firefox Problems"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by richie42 on 2008-09-15
When registering for the SAT, I need to open a javascript window to print out my admissions ticket, but when I click on it, it always (and this works for doing UCAS too), firefox turns grey. How do I fix that?

---

### Post by phidia on 2008-09-15
Do you have java installed/enabled? From a terminal enter "java -version"

Maybe there are special requirements for accessing those forms-does the school have a system/software requirements page?

When ff greys out it's trying to load or open something.

---

### Post by richie42 on 2008-09-15
Hmmm... I get this, and when I go into my UCAS account and click on something, it is still broken.

As for terminal, it says this:

```
richard@theSelbys:~$ java -version
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * j2re1.4
 * kaffe
 * cacao
 * gij-4.1
 * jamvm
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
richard@theSelbys:~$ 


```

---

### Post by richie42 on 2008-09-15
I still cannot use ANY javascript at all on Firefox....

---

### Post by richie42 on 2008-09-15
can someone please help me?

---

### Post by frank002 on 2008-09-15
type    about:plugins and scroll to see if you have java. If not, open Synaptic and search for... sun-java.  Install sun-java 6-bin, sun-java 6-jre and sun-java 6-plugin. There is probably an easier way but this worked for me. Good luck.

---

### Post by richie42 on 2008-09-15
> **frank002 said:**
> type    about:plugins and scroll to see if you have java. If not, open Synaptic and search for... sun-java.  Install sun-java 6-bin, sun-java 6-jre and sun-java 6-plugin. There is probably an easier way but this worked for me. Good luck.

Type about:plugins in what?

---

### Post by shoot2kill on 2008-09-15
firefox address bar

and just for clarity it is "about: plugins" without the space.. forum code creates the  :p

---

### Post by richie42 on 2008-09-15
Well, now I have java, but whatever I do in the UCAS form, it isn't working. I cannot click on essential links.

Help me troubleshoot this please.

I need to go to sleep.

---

### Post by lswb on 2008-09-15
java and javascript are different. The java plugin has nothing to do with javascript. 

Make sure javascript is enabled. From the firefox menu, select Edit/Preferences/Content and make sure the "Enable Javascript" box is checked. 

If that doesn't work check any sercurity or privacy related plugins you may have installed. Some of these will inhibit javascript or stop it altogether

---

### Post by richie42 on 2008-09-16
What plugins will inhibit this?

---

### Post by richie42 on 2008-09-16
???????

---

### Post by kansasnoob on 2008-09-16
> **richie42 said:**
> Well, now I have java, but whatever I do in the UCAS form, it isn't working. I cannot click on essential links.

Help me troubleshoot this please.

I need to go to sleep.

I could be mistaken, but it sounds like you may also need Adobe, called acroread in linux. I have four packages installed from synaptic:

[ATTACH]85462[/ATTACH]

Notice the description for escript: 

> The Adobe EScript (ECMA Script) Plug-In allows PDF documents to take
advantage of JavaScript.

But you'll want all four packages. First you'll need the Medibuntu repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Don't forget the GPG key!

If you need more specific help installing either the repo or the packages be sure to say what version of Ubuntu you're using.

---

### Post by richie42 on 2008-09-16
How do I install medibuntu?

---

### Post by richie42 on 2008-09-16
???????????

---

### Post by kansasnoob on 2008-09-16
> **richie42 said:**
> How do I install medibuntu?

What version of Ubuntu are you running? Hardy Heron?

---

### Post by frank002 on 2008-09-16
To add the medibuntu repository do the following:

 Open  the terminal and type

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

      Then add the key

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by kansasnoob on 2008-09-17
> **frank002 said:**
> To add the medibuntu repository do the following:

 Open  the terminal and type

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

      Then add the key

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

And what if it's not Hardy?

---

### Post by m_duck on 2008-09-17
You can just change hardy in the first terminal command for a different version, ie gutsy.

More information is [here]("https://help.ubuntu.com/community/Medibuntu") under the section 'Adding the Repositories' with examples for different versions of Ubuntu.

---

