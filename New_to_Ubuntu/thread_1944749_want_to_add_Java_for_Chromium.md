---
title: "want to add Java for Chromium"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by mzimmers on 2012-03-21
I searched the forum (and the web) for information on this...it appeared that the favored package is OpenJDK Java 7 Runtime. I tried to download it through USC with the browser plugin, and it failed, telling me to check my internet connection (which is fine). It also gave me an error message about trying to download from an untrusted site. 

I think the untrusted site warning applies to the browser plugin, but if I don't include this, then Java won't work with Chromium, will it? Suggestions?

Thanks.

---

### Post by wojox on 2012-03-21
Did you try:
```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mzimmers on 2012-03-21
Well...I did now!

It looked like everything was going OK, but now I have a Package Configuration screen on my terminal. It says "Configuring ttf-mscorefonts-installer" and contains a warning about agreeing to the license terms. But...there doesn't seem to be any way to respond to it. There's an "<Ok>" at the bottom, but it's not live.

What am I supposed to do here?

---

### Post by wojox on 2012-03-21
<Tab> into it and then on the next screen use the arrow key.

---

### Post by mzimmers on 2012-03-21
Oh, duh...that was sure tough.

The terminal was moving pretty fast, but now seems stuck on a section:

Saving to: './trebuc32.exe'

It blitzed through the first 2 1/2 lines, and is now hung. Should I wait on it, or it this likely a problem?

EDIT: of course, as soon as I hit "save" it moves on and finishes. Announces no errors.

I see an IcedTea entry in my plug-ins...is that a sign that this took? The speed test on megapath still doesn't execute, but that could be do to something else.

---

### Post by QIII on 2012-03-21
[LEFT]That indicates that it "took".

Your continued problem may have something to do with the fact that OpenJDK , even though it is soon to be the reference implementation for Java 7 (if it is not already), and and the IcedTea plugin are not universally recognized by the rest of the world as "Java".  Thus, some Java content on some sites will not execute.

Hopefully this misunderstanding (dare I say "ignorance" or "arrogance"?) among some web developers will be resolved soon.
[/LEFT]

---

### Post by mzimmers on 2012-03-21
Hmm...OK, well, that sucks for megatest, I guess. Just so I can be sure that the installation is good, can you refer me to a site that will do some Java stuff for me?

---

### Post by QIII on 2012-03-21
[www.java.com/en/download/installed.jsp?detect=jre&try=1](www.java.com/en/download/installed.jsp?detect=jre&try=1)

should detect that you have either the Java plugin or the IcedTea plugin installed.

As to what sites will work or not with the IcedTea plugin, that's a crap shoot.

---

### Post by mzimmers on 2012-03-21
Very nice. It says that I have version 6.23, and that 6.31 is available. Should I go ahead and download it through the browser?

Thanks.

---

### Post by QIII on 2012-03-21
If you installed from the repos, I'm not sure which version you would have gotten.  I think that it is likely that you got OpenJDK 6 Update 23(?)

I see in Precise (12.04) that IcedTea 7 is available in the repos, but I'm not sure about prior releases.

Check Synaptic or the Software Center to see if IcedTea 7 is available.  Otherwise you likely have the most recent update in the repos.

You can't update "through the browser" exactly in Linux.  You would have to download the .bin and install it from the console.

---

### Post by mzimmers on 2012-03-21
What exactly are the "repos?" And what is Synaptic?

According to the USC, I already have IcedTea Java 6 Web Start, OpenJDK Java 6 Runtime and OpenJDK Java7 Runtime. Can I remove Java 6?

---

### Post by mzimmers on 2012-03-22
Do these instructions look valid for installing the 6.31 package?

[http://www.java.com/en/download/help/linux_x64_install.xml]("http://www.java.com/en/download/help/linux_x64_install.xml")

Thanks.

---

### Post by QIII on 2012-03-22
Yes, but there are no instructions for creating a symbolic link to the Java plugin so that your browser can find it.

The following is a very clear process with great instructions and explanations for what you are doing.  Up to the point where the symbolic link is created for Firefox, the process will work for you just fine.  It'll give you Java 6 Update 31 and allow you to select you JRE alternative. 

As for Firefox, I don't like where they put the symbolic link, but it works.

You will have to find another place for it for Chromium.  I don't use Chromium, so I can't tell you where.  Perhaps someone else will come along and help out with that.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

If you read the whole thing, the maintainer talks about duinsoft.nl.  It is entirely legit.  But if you don't want to have a scripted installation that is not transparent, you don't have to use it.  I'm not sure where it puts the symlink either.

Although you have to uninstall the IcedTea plugin, you do NOT have to uninstall OpenJDK -- so you can update your alternatives any time you want to to switch back and forth.  You can have Java 6, Java 7, OpenJDK 7, etc, all installed at the same time.  You just have to pick the alternative to use.

---

### Post by mzimmers on 2012-03-23
Those are indeed excellent directions for installing Java. May I ask what it is about the link location that you don't care for? I ask because I will probably have to do something similar for Chromium.

---

### Post by katsugawa on 2012-03-23
just install jdk 7 from ubuntu program manager in desktop, there will be add plugin that you can use easily. Cheers

---

### Post by mzimmers on 2012-03-23
Forgive my ignorance, but where do I find ubuntu program manager? This isn't the same as the USC, is it?

---

