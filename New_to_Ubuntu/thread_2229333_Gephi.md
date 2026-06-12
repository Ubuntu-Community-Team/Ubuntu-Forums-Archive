---
title: "Gephi"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by Glkanter on 2014-06-12
Hi,

Gephi is a free charting software package. I couldn't find it in the Ubuntu Software Center.

These are the instructions for installing, and I couldn't accomplish it.

[https://gephi.org/users/install/](https://gephi.org/users/install/)

I'd appreciate any friendly help.

Thanks, as always!

Garry

---

### Post by QIII on 2014-06-12
Hello!

What part couldn't you do?

(I have a pretty good idea if you followed those instructions, but I won't make an assumption.)

---

### Post by Glkanter on 2014-06-12
Step 1 is: "Install Sun Java via [Synaptic]("https://help.ubuntu.com/community/SynapticHowto"), do a Quick Search Search for &#8220;sun java&#8221; and install the jre and jdk. Do not forget to run *update-alternatives &#8211;config java* and  *update-alternatives &#8211;config javac*."

I endeavored to do "Install Sun Java via [Synaptic]("https://help.ubuntu.com/community/SynapticHowto"), do a Quick Search Search for &#8220;sun java&#8221; and install the jre and jdk." 

I went to the Synaptic link, did the search, and I was lost.

Instead, I installed Synaptic via the Ubuntu Software Center.

Then I tried to run: update-alternatives &#8211;config java in a terminal, 
and got this error message: "unknown argument `&#8211;config' ".

Then I asked for help on this forum.

Thanks.

---

### Post by QIII on 2014-06-12
Thought that was it.

Java is no longer in the Ubuntu repo, nor anyone else's because Oracle (which now owns Java - there is no longer any such thing as Sun Java) took its ball back home.

Please have a look at the wiki in my signature for how to install it using webupd8.org's PPA.

---

### Post by Glkanter on 2014-06-12
Thanks, QIII.

I'm afraid that advice is a little too cryptic for me.

I have no foundation upon which to solve my own problem.

Thanks, again.

---

### Post by QIII on 2014-06-12
Just go to the wiki and look under the command line installation section.  I think the text of the link I put there is "Using webupd8.org's strikingly simple method."

Cut and paste three commands as instructed at that website in the terminal and Oracle Java will be installed for you.

---

### Post by Glkanter on 2014-06-12
So far so good! Now to install Gephi...

For the benefit of any future persons referencing this thread, these are the three commands required, from this link [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html):

sudo add-apt-repository ppa:webupd8team/java

sudo apt-get update

sudo apt-get install oracle-java7-installer

---

### Post by QIII on 2014-06-12
I wish you well from here.  That application and its instruction page seem very old, so there is no guarantee it will work.

Keeping my fingers crossed.

---

### Post by Glkanter on 2014-06-12
After I extracted the download, all I had to do was run Gephi from the bin folder.

Thanks!!

---

