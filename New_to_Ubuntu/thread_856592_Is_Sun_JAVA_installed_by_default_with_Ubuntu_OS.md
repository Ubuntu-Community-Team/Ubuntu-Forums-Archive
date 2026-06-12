---
title: "Is Sun JAVA installed by default with Ubuntu O/S ?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by wpshooter on 2008-07-11
Is any version of Sun JAVA automatically installed during the installation of the Ubuntu operating system versions ?

Here is the reason I ask.

I am trying to get the Linux shutdown software installed for a Tripplite UPS that I just purchased.

On Tripplite's website the instructions for installing the PowerAlert shutdown software that is "**SUPPOSED**" to work with a Ubuntu O/S (or at least that is what Tripplite has told me) they say that **PRIOR** to installing the PowerAlert software that you need to go to the JAVA website and download and install JAVA.  They even give you a link that takes you to the JAVA site.

BUT when I go to the JAVA site and after I download and install the Linux compatible version of JAVA which is apparently supposed to be something like either version 3.6 or maybe it is 6.6, there is also a verification function link on the JAVA website to verify that the correct version of JAVA is installed on your computer.  

Well when I run the verification function it comes back reporting that the version of JAVA on my machine is the 3.3 version but that I need to have version 3.6 installed instead.  

How can this be ???  I just downloaded and installed it from the very site that is performing the version verification function ???

And indeed, if I attempt to go ahead and install the Tripplite PowerAlert shutdown software, it comes back and tells me that there is NO JRE JAVA installed on my computer.  Again, how can this be unless one of two things are happening.  

1) The JAVA website is setup to download and install the incorrect version of JAVA for Linux or

2) The installer on the JAVA website is installing the JAVA software incorrectly (perhaps in the wrong place) on the Ubuntu machine ?

Any advice on how to proceed is appreciated.  Other than contact, Tripplite, which I have attempted to do, but have yet to get any response from them.

Thanks.

---

### Post by LowSky on 2008-07-11
Java isn't install by default

got to the Menu and clcik on add/remove
make sure you select all avaible softeware fromt eh top menu then
type in JAVA, and check off and install

---

### Post by youthforlinux on 2008-07-11
[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")
Install the Sun Java Package that is explained....you need to make sure that Universe is enable in your repository list.

---

### Post by Inxsible on 2008-07-11
instead of installing from the website..you can install from the repos itself. The version in the repos is jdk6 update 6

```
aptitude install sun-java6-jre sun-java6-bin sun-java6-plugin
```

---

### Post by Kedster on 2008-07-11
one thing that u may want to do is unistall ICEDTEA

Go to system > administration > synaptic package manager 
it will ask for ur password ans then it will open just go up to the top were it says search and  type "icedtea" then when its done searching go and uninstall all the things that are installed

---

### Post by wpshooter on 2008-07-11
> **Inxsible said:**
> instead of installing from the website..you can install from the repos itself. The version in the repos is jdk6 update 6

```
aptitude install sun-java6-jre sun-java6-bin sun-java6-plugin
```

It would seem to me that this would be the same thing that is supposed to be installed directly from the JAVA site.  Is there something different about the way/where this method would install the program as opposed to the way/where it is being installed from the JAVA site ?

Does this mean that the Ubuntu O/S is NOT necessarily compatible with the JAVA installation for "LINUX" ?

Thanks.

---

### Post by wpshooter on 2008-07-11
> **Kedster said:**
> one thing that u may want to do is unistall ICEDTEA

Go to system > administration > synaptic package manager 
it will ask for ur password ans then it will open just go up to the top were it says search and  type "icedtea" then when its done searching go and uninstall all the things that are installed

What would this do ?

There were no such instructions for doing this on the Tripplite download and installation instructions page.

Thanks.

---

### Post by tjwoosta on 2008-07-11
> Is there something different about the way/where this method would install the program as opposed to the way/where it is being installed from the JAVA site ?

its just easier  (everything is automatic when installing from apt-get)

> What would this do ?

There were no such instructions for doing this on the Tripplite download and installation instructions page.

Thanks. 

im not 100% but i think there is some type of bug with iced tea, because i also had to uninstall it in order to make java applets work properly

---

### Post by Inxsible on 2008-07-11
> **wpshooter said:**
> It would seem to me that this would be the same thing that is supposed to be installed directly from the JAVA site.  Is there something different about the way/where this method would install the program as opposed to the way/where it is being installed from the JAVA site ?

Does this mean that the Ubuntu O/S is NOT necessarily compatible with the JAVA installation for "LINUX" ?

Thanks.
What this method also does is set some environment variables for you. Even if you have java installed, but you don't set the environment variables, other programs have no way of knowing what version of java you have on your computer.

---

### Post by wpshooter on 2008-07-11
> **Inxsible said:**
> What this method also does is set some environment variables for you. Even if you have java installed, but you don't set the environment variables, other programs have no way of knowing what version of java you have on your computer.

Are you saying the the JAVA website/people do not know how to properly install their program to a Ubuntu O/S computer ?

Thanks.

---

### Post by Inxsible on 2008-07-11
> **wpshooter said:**
> Are you saying the the JAVA website/people do not know how to properly install their program to a Ubuntu O/S computer ?

Thanks.Not at all. All I am saying is they may not have access to the environment variables on your machine. Or they might have noted somewhere that you would have to do this manually.


Question is : are you sure you downloaded and installed the correct version? can you provide us with a link where you downloaded and installed from?

---

### Post by SunnyRabbiera on 2008-07-11
always user repositories.
Ubuntu does come with a version of java though its not the main official version, its the experimental open source version.
use this guide on installing packages in Ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by wpshooter on 2008-07-11
> **Inxsible said:**
> Not at all. All I am saying is they may not have access to the environment variables on your machine. Or they might have noted somewhere that you would have to do this manually.


Question is : are you sure you downloaded and installed the correct version? can you provide us with a link where you downloaded and installed from?

Second one on the listing.

Please notice verification function just to the right of the listings.  See my comments about this in the original posting of this thread.

Thanks.

[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)

---

### Post by wpshooter on 2008-07-11
> **SunnyRabbiera said:**
> always user repositories.
Ubuntu does come with a version of java though its not the main official version, its the experimental open source version.
use this guide on installing packages in Ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Thanks.  I know those programs are in Synaptic.

But that was not the instruction that was given on the Tripplite website.

---

### Post by Inxsible on 2008-07-11
> **wpshooter said:**
> Second one on the listing.

Please notice verification function just to the right of the listings.  See my comments about this in the original posting of this thread.

Thanks.

[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)Did you follow the instructions that they have for installing the self extracting file at this page

[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

I am sure you already know this - but you need to change the version number while giving chmod permissions on it. Also did you perform these instructions as root or your user?

---

### Post by wpshooter on 2008-07-11
> **Inxsible said:**
> Did you follow the instructions that they have for installing the self extracting file at this page

[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

I am sure you already know this - but you need to change the version number while giving chmod permissions on it. Also did you perform these instructions as root or your user?

I followed the instructions are they are laid out on the site.  I gave the change mode command as show in the instructions and to the best of my recall the listing/name of the downloaded file was 6u6.

But what I don't understand is that I just went back and installed the JAVA 6 from Synaptic and then I went back to the JAVA site and did the verification test and this is what I got.

[http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_03&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.22-14-generic](http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_03&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.22-14-generic)

It almost appears to me from all of this that Synaptic is installing update   #3, the JAVA site is installing update #6 and the JAVA site is testing/verifying for update #7.

Am I missing something here ?  I am about to go ahead and try the install of the Tripplite PowerAlert software again with the JAVA that I have installed from Synaptic and see if it let me go ahead with the install as things stand now.  I am not very confident that it is going to work.

Thanks.

---

### Post by Inxsible on 2008-07-11
> **wpshooter said:**
> I followed the instructions are they are laid out on the site.  I gave the change mode command as show in the instructions and to the best of my recall the listing/name of the downloaded file was 6u6.

But what I don't understand is that I just went back and installed the JAVA 6 from Synaptic and then I went back to the JAVA site and did the verification test and this is what I got.

[http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_03&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.22-14-generic](http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_03&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.22-14-generic)

It almost appears to me from all of this that Synaptic is installing update   #3, the JAVA site is installing update #6 and the JAVA site is testing/verifying for update #7.

Am I missing something here ?  I am about to go ahead and try the install of the Tripplite PowerAlert software again with the JAVA that I have installed from Synaptic and see if it let me go ahead with the install as things stand now.  I am not very confident that it is going to work.

Thanks.A new version of the JRE came out...I got an update notification for version 7 just today.

So I guess thats why the site checks for the latest. If you install update 7...it WILL work for earlier versions as well. Java is always backward compatible.

But synaptic should install update 6...hell i have installed update 6 from the standard repos...so I am a bit surprised.

Maybe the mirrors that you are using havent been updated :(

---

### Post by wpshooter on 2008-07-11
I just try the Tripplite PowerAlert install again and I got exactly the same thing.

NO JRE was found on the system.

Boy, am I confused.  I may not be the best in the world in following instructions but then I don't think I am the worst either.  I sure believe it helps when the instructions themselves are correct.  I don't believe that any of the instructions that I am seeing on these site know exactly what they are talking about.  

$#($**@$($(#92.

I think I am going to tell my sister that she just needs to buy herself a copy of XP and to forget about this stuff.

---

### Post by wpshooter on 2008-07-11
[QUOTE=
Maybe the mirrors that you are using havent been updated :([/QUOTE]

Software sources says Server for the United States.

Is there one that should be more up-to-date than that one ?

Thanks.

---

