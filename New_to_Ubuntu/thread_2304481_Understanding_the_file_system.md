---
title: "Understanding the file system"
date: 2015-11-27
forum: New to Ubuntu
---

### Post by Jan_Erik on 2015-11-27
I am a new starter and I just installed Ubuntustudio (wily werewolf) because I want to use the the application PureData(PD). However I need to upgrade the PD vanilla to PD extended. I have a few questions connected to this: 

1)In the process I looked in the file system and found the following:
[FONT=arial]**/usr/bin/pd** is a link to **/etc/alternatives/pd** which again is a link to the executable **/usr/bin/puredata**
[/FONT]
[FONT=arial]Why this structure with so many links?

2)Also I could not find a installation file for **Wily **on this site [http://apt.puredata.info/releases/dists/](http://apt.puredata.info/releases/dists/)
However can I use the **trusty **version?

3) If the trusty version is ok can I then use similar intructions as this to install? [http://ubuntuportal.com/2014/04/how-to-install-google-chrome-web-browser-in-ubuntu-14-04-lts-trusty-tahr.html](http://ubuntuportal.com/2014/04/how-to-install-google-chrome-web-browser-in-ubuntu-14-04-lts-trusty-tahr.html)[/FONT]

---

### Post by mastablasta on 2015-11-27
first check if the application is available in repositories. it should be there: [https://launchpad.net/ubuntu/+source/puredata](https://launchpad.net/ubuntu/+source/puredata)

if not add the ppa : [https://puredata.info/docs/faq/debian](https://puredata.info/docs/faq/debian)
update the sources and should be in software center for you to install

otherwise yes you can try to install trusty package and see what happens.

as for the Linux file structure it has to do with system programs, user programs and such.: [http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

---

### Post by grahammechanical on 2015-11-27
Be careful when using installation instructions for one program to install another program. You might get more than you bargained for.

When I do a web search for information I prefix the search terms with Wiki Ubuntu and then I get either official Ubuntu documentation or community written documentation. such as this

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

When switching to Linux from some other operating system it is important to keep in mind that Linux is not Microsoft Windows. Things are done differently. The reasons why Linux is the way it is go back into the dim mists of time. Symbolic links are a way of avoiding the duplications of libraries in different locations. One application may look for a library in one location and another application may look for the same library in a different location.

---

### Post by Jan_Erik on 2015-11-27
Thanks for the great link and the replies for explaining the file system:) Very useful for a new starter..  Can I just ask what is a PPA?


With regards the installation I could not find it in the repositories. It seems like it is only the vanilla version there and not the puredata extended version(?).


I then tried to install the "Trusty" package by downloading the .deb and running a sudo dpkg -i .... but this did not work. There were dependencies not in place. (Is it possible to back out from doing a dpkg -i  ??)


I wish there were a standard routine for installing applications on linux but I guess that is how it is.... well well


Since this is a fresh machine I am considering doing a fresh install of Ubuntu studio since Trusty Tahr since this seems to be a more supported version..

---

### Post by bab1 on 2015-11-27
> **Jan_Erik said:**
> ... I am considering doing a fresh install of Ubuntu studio since Trusty Tahr since this seems to be a more supported version..
Trusty is a Long Term Support (LTS) version.  It is supported for 5 years.  The next LTS is 16.04 (Xerus).  In between are regular support versions.  Regular releases are supported for only 9 months.

---

### Post by Jan_Erik on 2015-11-27
Ok thanks. I did a fresh install of Trusty Tahr. I then followed the instructions on the site [https://puredata.info/docs/faq/debian](https://puredata.info/docs/faq/debian)
and the packages did install fine. (I still do not quite understand what the commands do but I guess I will in time..)

Restarting the machine and opening application search PD extended was there. When starting the application it started ok and it seems to be working OK but I get some error messages at startup in the application. But I will take this issue over to the PureData forum.  (However I will list it here if anyone is familiar with this *:tried but couldn't sync A/D/A ALSA output error (restart failed): Broken pipe)*

Anyhow thank you so much for input and for giving me more understanding about how Linux works.

---

### Post by bab1 on 2015-11-27
> **Jan_Erik said:**
> Ok thanks. I did a fresh install of Trusty Tahr. I then followed the instructions on the site [https://puredata.info/docs/faq/debian](https://puredata.info/docs/faq/debian)
and the packages did install fine. (I still do not quite understand what the commands do but I guess I will in time..)

Restarting the machine and opening application search PD extended was there. When starting the application it started ok and it seems to be working OK but I get some error messages at startup in the application. But I will take this issue over to the PureData forum.  (However I will list it here if anyone is familiar with this *:tried but couldn't sync A/D/A ALSA output error (restart failed): Broken pipe)*

Anyhow thank you so much for input and for giving me more understanding about how Linux works.
The instructions you are following are almost 10 years old.  Many things have changed.  Sometimes Linux distros are radically different from each other.  Whe did you not want to install the packaged version of Pd that was created specifically for your version of Ubuntu?  The version I see is 0.45.  Isn't that pretty current?

ALSA stands for Advanced Linux Sound Architecture.  Pretty important for multimedia I would think.  My guess is this is all worked out in the Ubuntu package of PD.

FYI:   I searched on " tried but couldn't sync A/D/A ALSA output error (restart failed): Broken pipe" and it brought me to **[this]("https://www.google.com/search?client=ubuntu&channel=fs&q=alsa+linux&ie=utf-8&oe=utf-8#channel=fs&q=tried+but+couldn%27t+sync+A%2FD%2FA+ALSA+output+error+%28restart+failed%29:+Broken+pipe")**.   Search first and learn more by fixing the problems.  We will help if you really need it.  :-)

Either way this is a new topic and you should post on that in the section that is appropriate.

---

### Post by Jan_Erik on 2015-11-28
> **bab1 said:**
> The instructions you are following are almost 10 years old.  Many things have changed.  Sometimes Linux distros are radically different from each other.  Whe did you not want to install the packaged version of Pd that was created specifically for your version of Ubuntu?  The version I see is 0.45.  Isn't that pretty current?

ALSA stands for Advanced Linux Sound Architecture.  Pretty important for multimedia I would think.  My guess is this is all worked out in the Ubuntu package of PD.

FYI:   I searched on " tried but couldn't sync A/D/A ALSA output error (restart failed): Broken pipe" and it brought me to **[this]("https://www.google.com/search?client=ubuntu&channel=fs&q=alsa+linux&ie=utf-8&oe=utf-8#channel=fs&q=tried+but+couldn%27t+sync+A%2FD%2FA+ALSA+output+error+%28restart+failed%29:+Broken+pipe")**.   Search first and learn more by fixing the problems.  We will help if you really need it.  :-)

Either way this is a new topic and you should post on that in the section that is appropriate.

Hi, thanks for the reply.

With regards to error I did actually search the web. I found a possible solution on the url below. He mentioned that he started PD extend as root and that fixed it. However I do not know how to start a program as root. I found a suggestion on YouTube but that was only for Gnome.. i am using Xfce

[http://forum.pdpatchrepo.info/topic/1540/tried-but-couldn-t-sync-a-d-a](http://forum.pdpatchrepo.info/topic/1540/tried-but-couldn-t-sync-a-d-a)

As mentioned before I am fairly new to linux. When you mention that the instructions are 10 years old how on earth can I know that it is? You mention you have seen a version 0.45? where did you find this?? And if I get the packaged version how do I install it? 

Please bear in mind that I am coming from Win and Mac and I think meeting with the penguin has been quite overwhelming with issue after issue and I am very close to giving in and crawl back to win/mac.. My main interest is to make music and not spend my days configuring and solving software issues. But I suspect Linux is not ready for this yet. I did actually do some work with red hat linux for about 10 years ago and I recall having the same impression of too many issues then, so in that regards not too much have changed.

Maybe if the community could work together and create one solid version of Linux instead of X number of distributions etc then Linux could maybe one day be a real alternative to win/mac....Until this happens I am afraid Linux will only be an OS for software technical interested persons and not users interested in using linux as a plaform for creative work etc.. But maybe I am wrong?? Anyhow I will stick with it for a few more days. I got Supercollider running today and that is a good thing. But then again Quarks in Supercollider did not work so here we go...a new issue... And by the way the preconfigured Jack server also failed to start... It looks like one of us is not ready, the penguin or me;)

---

### Post by bab1 on 2015-11-28
> **Jan_Erik said:**
> Hi, thanks for the reply.

With regards to error I did actually search the web. I found a possible solution on the url below. He mentioned that he started PD extend as root and that fixed it. However I do not know how to start a program as root. I found a suggestion on YouTube but that was only for Gnome.. i am using Xfce

[http://forum.pdpatchrepo.info/topic/1540/tried-but-couldn-t-sync-a-d-a](http://forum.pdpatchrepo.info/topic/1540/tried-but-couldn-t-sync-a-d-a)

As mentioned before I am fairly new to linux. When you mention that the instructions are 10 years old how on earth can I know that it is? 

It's easy to tell when Ubuntu versions are released.  The major number (to the left of the dot (.)) is the year of release.  The minor number (to the right of the dot (.)) is the month.  When I see this ```
 # Ubuntu/dapper 06.04 LTS
```...I see April of 2006.
> 
You mention you have seen a version 0.45? where did you find this?? And if I get the packaged version how do I install it? 

It is in the Ubuntu 14.04 LTS package repositories that can be accessed by the Ubuntu Software Center.  Unlike Windows or OSX, you do not need to search the web for applications or visit the application download site.  In fact using anything but the Ubuntu packaged application means you may have to make the changes that are already in the package for the application to work with the version of Ubuntu you are using.  Ubuntu package maintainers do all of this for each version of Ubuntu.  Bottom line for you is: only use Ubuntu packaged applications that are for your version of Ubuntu.  The access to the repos are: apt (command line), Synaptic (GUI app that you need to install) or Ubuntu Software Center, Ubuntu's current GUI method of accessing the APT packages.  
> 
Please bear in mind that I am coming from Win and Mac and I think meeting with the penguin has been quite overwhelming with issue after issue and I am very close to giving in and crawl back to win/mac.. My main interest is to make music and not spend my days configuring and solving software issues. 

As in life, it's always time or money.  Linux is free, but you need to devote time to getting everything working.  Windows and Apple will provide easy access for the right amount of money.
> 
But I suspect Linux is not ready for this yet. I did actually do some work with red hat linux for about 10 years ago and I recall having the same impression of too many issues then, so in that regards not too much have changed.

Nor will it ever really change.  Ubuntu is one of the easiest Linux Desktops to use, but you still need to configure things and should understand how it all works.  The forum is full of people willing to help.  A positive attitude helps.
> 
Maybe if the community could work together and create one solid version of Linux instead of X number of distributions etc then Linux could maybe one day be a real alternative to win/mac....Until this happens I am afraid Linux will only be an OS for software technical interested persons and not users interested in using linux as a plaform for creative work etc.. 

Creative is in the eyes of the beholder.  Your kind of creative may not be what my idea of creative is.  IMO most folks that use Linux and create software on the Linux platform aren't really all that interested in whether Linux is a commercial alternative to Windows or Mac.  It will always be a place of experimentation and strong enterprise "back end" support.
> 
But maybe I am wrong?? Anyhow I will stick with it for a few more days. I got Supercollider running today and that is a good thing. But then again Quarks in Supercollider did not work so here we go...a new issue... And by the way the preconfigured Jack server also failed to start... It looks like one of us is not ready, the penguin or me;)
Look inward.

I would start over and use the Ubuntu Software center to install PD .45.4-1

If you have a specific problem search on the term with keywords (<keyword> + Ubuntu +14.04).  

PD specific problems should have a a separate thread.

---

### Post by Jan_Erik on 2015-11-28
Ok thanks again for the reply. I may have jumped the gun but I have been pulling my hear for a few days here and felt the growing frustration for all the issues. But as you say it is all a matter of time and money, but I also like the idea of using opensource software (PD and Supercollider) on a free OS to make music and sound installations.

However with regards to the PD application one of the issues here is that there is two versions of PD. It is the PD (vanilla) which is a stripped down version and is available in the repositories indeed. It even comes preinstalled with Ubuntu studio. However the version I need is PD (extend) and this is not in the repositories as far as I can see. The only way to install it as far as I am aware is by using the instructions found here [https://puredata.info/docs/faq/debian](https://puredata.info/docs/faq/debian)  (Or I might still be missing something?)

---

### Post by bab1 on 2015-11-28
> **Jan_Erik said:**
> Ok thanks again for the reply. I may have jumped the gun but I have been pulling my hear for a few days here and felt the growing frustration for all the issues. But as you say it is all a matter of time and money, but I also like the idea of using opensource software (PD and Supercollider) on a free OS to make music and sound installations.

However with regards to the PD application one of the issues here is that there is two versions of PD. It is the PD (vanilla) which is a stripped down version and is available in the repositories indeed. It even comes preinstalled with Ubuntu studio. However the version I need is PD (extend) and this is not in the repositories as far as I can see. The only way to install it as far as I am aware is by using the instructions found here [https://puredata.info/docs/faq/debian](https://puredata.info/docs/faq/debian)  (Or I might still be missing something?)
The instructions you show are only really current to Ubuntu 13.0.  See```
 # Ubuntu/raring 13.04
 deb http://apt.puredata.info/releases raring main
```
This means that you will be adding a repository that not tested against the current Ubuntu versions.  This is a Personal Package Archive (PPA) that is maintained by PD. that they don't seem to have any interest in updating.

[**Here**]("https://www.google.com/search?client=ubuntu&channel=fs&q=purdata+site%3Ahttp%3A%2F%2Fwww.webupd8.org%2F&ie=utf-8&oe=utf-8#channel=fs&q=pd-extended+ubuntu+14.04") is the search I did on installing the PPA with Ubuntu 14.04.

Once again this really should have a new thread started in the appropriate sub-forum or at PD itself.

---

### Post by Jan_Erik on 2015-11-30
Thanks again for the advise. Can I ask one final question where/how you found the statement:

>  # Ubuntu/raring 13.04
 deb [http://apt.puredata.info/releases](http://apt.puredata.info/releases) raring main

I will take this issue / question to the PD forum and try to find out why a 14.04 version has not been provided.

---

### Post by bab1 on 2015-11-30
> **Jan_Erik said:**
> Thanks again for the advise. Can I ask one final question where/how you found the statement:```
# Ubuntu/raring 13.04
deb http://apt.puredata.info/releases raring main 
```



I will take this issue / question to the PD forum and try to find out why a 14.04 version has not been provided.

At the site you referenced:  [https://puredata.info/docs/faq/debian]("https://puredata.info/docs/faq/debian"): 

Look at the bottom of the section listing Ubuntu PPA's.

---

### Post by Jan_Erik on 2015-11-30
Thanks again for all help and support in the process I am now in. Enjoying Linux more and more and I guess with a bit more patience, experience and understanding Ubuntu studio will be a good plaform for my projects.

---

### Post by bab1 on 2015-11-30
I think you can mark this thread solved then.  I there are other questions on Ubuntu, post them at this forum.  If you have PD questions I would post them in the Multimedia section of the forum.

---

### Post by Geoffrey_Arndt on 2015-11-30
Also Jan, as a media person . . . take advantage of youtube channels about Ubuntu and Linux in general.   Will make the 30 to 90 day learning curve (for non-tech users) a lot smoother.

Lastly, recognize in the future that running Ubuntu can be a trivial matter to setup and use if getting hardware with Linux "pre-installed" (just like you did with Windows or Mac).

Of these vendors, I use System76 high end PC's  . . . for photo, dvd and audio customizations:     [http://linuxpreloaded.com](http://linuxpreloaded.com)

---

