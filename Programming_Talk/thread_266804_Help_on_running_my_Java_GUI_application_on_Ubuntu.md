---
title: "Help on running my Java GUI application on Ubuntu"
date: 2006-09-27
forum: Programming Talk
---

### Post by mimoh_mi on 2006-09-27
**[SIZE="2"]Hi All,[/SIZE]**
[SIZE="4"][I]
Am new to this forum. As a Java Developer, i have been trying
to port my Java application on Ubuntu. I installed the Javs SE
SDK binary version, The initial problem was setting my classpath.
I did it the normal linux conventional way by adding to to
/etc/profile - it didn't work untill i added  to the 
/etc/environment, with this setting, I could only use my Java
Tools as the root user. To use these tool with my personalised
user, i also had to edit /home/mimoh/.bashrc. My question is
why these multiple settings for classpath.

My next question, pls is there anyway to override the default
Java Runtime environment. Because, i believe, if i can do this,
i should be able to run my GUI applications. 
Thanks for anticipated reply.
[/I][/SIZE]

---

### Post by bukwirm on 2006-09-27
Run "sudo update-alternatives --config java" and "sudo update-alternatives --config javac" and select the appropriate item.

---

### Post by mimoh_mi on 2006-09-29
**@bukwirm**
*[SIZE="4"]Thanks for your reply. It was quite informative, but was't able to solve my problem. Some how i was able to get myself started. Since I install my ubuntu, I have been unable to set up my internet connection for some obvious reasons that am still working on, so i had to download the binary version of jdk1.5.0_08 from sun's website. Now, this is what i did to get my sun's jdk and jre running. I created a system link called jdk to my jdk1.5.0_08 directory, all in my /usr/local directory. Next i edited my .bashrc,/etc/profile and /etc/environment files to reflect my new classpath. Now the funny part, I added my jre/bin as the first entry in the /usr/environment path file. Hulala, when i login with my user name, i can actually see my java pointing to the binary version i installed, now i can compile and run any java programme, was also able to install netbean and java studio. Now the problem, as root, my system still point to the ubuntu jvm.[/SIZE]*

---

