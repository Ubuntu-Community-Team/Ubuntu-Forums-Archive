---
title: "Is there a workaround for having the wrong version of Ubuntu?"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-11-06
Hi,

I have an online meeting scheduled to meet a tutor from my university tonight (in about 6 hrs). The software they use is Elluminate.

[http://www.dsu.edu/academics/tutoring/faq.aspx](http://www.dsu.edu/academics/tutoring/faq.aspx)

and ???

[http://www.elluminate.com/Services/Training/Elluminate_Live!/?id=418](http://www.elluminate.com/Services/Training/Elluminate_Live!/?id=418)


I'm unable to connect on my computer to that session (a specific url was given to me that goes to the right 'room' and it is possible to connect outside of the time for the session --I did it before on a different computer).

I went to Elluminate's live chat and spoke with someone. The content of the chat is pasted below. The jist of what I got from that chat is that I don't have the right version of Ubuntu. I use Ubuntu 10.04 LTS but they say 9.10 is supported.

What I am wondering is if there's a way to put the things that make 9.10 work with Elluminate in my version here and get this one to work.

I'm at a friend's house now and will be able to use their computer to do tonight's session but that won't always be available to me. These sessions are set up on sunday evenings and I won't have access to another computer on sundays in the future. I will need to get this working somehow before next week, but if I could get it working before tonight's session that would be better.

Can anyone help?

> 
You are number '1' in the Queue. Please wait while we connect you to a Blackboard Collaborate Support Representative. Your wait time will be approximately '0' minute(s) and '30' seconds.

Hello, my name is 'Sharayah'. I am currently reviewing the information that you have provided, please give me a minute to complete this.

Jake: I'm sorry, I didn't know what to choose in the thing to get into chat. It's not an error message, it's what I described below that.

Sharayah: I would be happy to look into this for you. One moment please. 

Sharayah: Are you prompted to open or save a file?


Jake: ok

Jake: yes

Sharayah: Which option are you selecting?

Jake: in the drop down feild entitled "Open With" is "OpenJDK Java 6 Web Start" then I click "OK"

Sharayah: What version of Java do you have installed, specifically?

Jake: how do I find that out?

Jake: how do I find that out?

Sharayah: If you could go to the following link, it will tell you if your version of Java is supported or not: [http://support.blackboardcollaborate.com/ics/support/default.asp?deptID=8336&task=knowledge&questionID=1473](http://support.blackboardcollaborate.com/ics/support/default.asp?deptID=8336&task=knowledge&questionID=1473) 

Sharayah: This link will also check to see if your version of Linux is supported with Blackboard Collaborate.

Jake: [http://support.blackboardcollaborate.com/ics/support/default.asp?deptID=8336&task=knowledge&questionID=1473](http://support.blackboardcollaborate.com/ics/support/default.asp?deptID=8336&task=knowledge&questionID=1473)

Jake: it says my o/s is not supoorted but version of java is. Is that right?
Sharayah: That could be right. Only certain versions of Linux are supported. Do you know what version you have?

Jake: Ubuntu 10.04 LTS

Sharayah: At this time, only Linux Ubuntu 9.10 is fully supported. This could be causing the launching problem. If you don't have access to another computer, I would recommend uninstalling your version of Java and reinstalling the latest version from Java just to ensure that you do not have a corrupted version installed. 

Sharayah: For assistance with uninstalling and reinstalling Java on Linux, please visit [http://www.java.com/en/download/help/linux_uninstall.xml](http://www.java.com/en/download/help/linux_uninstall.xml) 

Sharayah: Can I be of assistance with anything else?

Jake: ok

Jake: no prob

Jake: thank you

Sharayah: You are welcome. Have a wonderful day.

Jake: is there a way to keep a copy of this chat?


---

### Post by Paqman on 2011-11-06
Try switching from OpenJDK to Sun Java:

[Elluminate on 10.04]("http://ubuntuforums.org/showthread.php?t=1479615")

---

### Post by beew on 2011-11-06
That is stupid. Ubuntu 9.04 has reached end of life last October. These people are not serious about supporting Linux. Sorry can't be of much help, maybe you can try virtual box or something?

Edited: Just saw Pagman's post. Hope that works for you. I am on 11.04 and have enabled Sun Java as default, it still says my OS is not supported. Hope you have better luck with 10.04.

---

### Post by squenson on 2011-11-06
A workaround: Install VirtualBox on your machine and then create a virtual machine with Ubuntu 9.10.

---

### Post by llamabr on 2011-11-06
It's not a linux or ubuntu issue, it's a java issue.  I use elluminate just fine on the LTR.

Try installing, reinstalling, or downgrading your java, though that should not matter either.

Instead, try just shutting everything down and opening a new browser and try again.  Be sure to allow popups in firefox.  Also, try opening it in chrome.  Could be java is already running something else, and is getting hung.

---

### Post by ClientAlive on 2011-11-06
> **Paqman said:**
> Try switching from OpenJDK to Sun Java:

[Elluminate on 10.04]("http://ubuntuforums.org/showthread.php?t=1479615")


Hi,

At the post you linked to there is also a link in it that lead you to how to install sun java. When I try adding the repo using the command they tell you there I get the output

```

Error: need a repository as argument

```

I tried it without the quotes after that but get the same response from the terminal. What could be happening here?

---

### Post by Paqman on 2011-11-06
You can use Software Sources to enable the Partner repo.

---

### Post by beew on 2011-11-06
Just open up Synaptic and go to Settings > Repository > Other software and check the box for Canonical's Partners, then close the dialogue box, reload Synaptic and install the sun-java packages with it (search for java on the search box).

---

### Post by ClientAlive on 2011-11-06
Well apparently that repo was already installed bc I decided to see what would happen if I ran the command to just install sun java and it did. Now I'm at that Elluminate link to see if this works (I know the guy in that other thread suggested you uninstall open jdk but I wanted to see if it works w/o uninstalling the other one first). So when you click, "log in" (at the Elluminate page) you get the pop up window asking what you want to do with the file. In that window there is a drop down menu to select which application to open the file with. Even though I know I installed sun java successfuly, OpenJDK is the only item in the list. Or I can click "other" in that list but it basically brings up my entire file system and I don't know what or where to look to find the sun java one and tell it to use that.

---

### Post by Paqman on 2011-11-06
Having more than one type of Java on your system will confuse it, either uninstall OpenJDK or run the following command to set the default Java:
```
sudo update-alternatives --config java
```

---

### Post by ClientAlive on 2011-11-06
> **Paqman said:**
> Having more than one type of Java on your system will confuse it, either uninstall OpenJDK or run the following command to set the default Java:
```
sudo update-alternatives --config java
```


Ok, I ran that command and selected the number corresponding to sun java. Now it is the item which is starred. Tried to do the log in at Elluminate and found I had the same situation (able to select "OpenJDK" or "other" to open the file with). Figured maybe I needed to do reboot before the new default took effect. Did that. Went back to try log in at Elluminate and same situation. If I need to uninstall OpenJDK that's fine but not sure what, specifically, to uninstall or not. In synaptic there are a few entries to do with OpenJDK.

-----------------

Edit:

Ok, so I found the item in synaptic where the description said it was the web start thing, right clicked and clicked "mark for complete removal" and clicked "apply". Synaptic finished and said it had uninstalled it. I went back to that log in page. Still, only OpenJDK avail to open the file. This didn't make sense to me since, supposedly, it had been uninstalled. Rebooted again thinking that might make a difference. Then, after booting back up, I ran:

```

sudo update-alternatives --config java

```

Here is what I saw:

```

shine@BashBox ~ > sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice[*], or type selection number: 

```


Not sure what's going on. I would be happy, for right now anyhow, just surfing to the sun java thing and clicking it to get it to open the file but I don't know where to find it. Also though, the output from "sudo update-alternatives --config java" doesn't make sense. If OpenJDK was uninstalled why would it still show up there?

---

### Post by Paqman on 2011-11-06
You probably didn't remove the right OpenJDK package. I believe the correct one to remove should be openjdk-6-jre, if you've still got that one installed, remove it. To be sure you might as well go ahead and remove anything related to OpenJDK.

---

### Post by beew on 2011-11-06
I think the uninstalling takes place when you reboot.

---

### Post by ClientAlive on 2011-11-06
I got it guys. It connected. Thank you for your help everybody.

:popcorn:

---

