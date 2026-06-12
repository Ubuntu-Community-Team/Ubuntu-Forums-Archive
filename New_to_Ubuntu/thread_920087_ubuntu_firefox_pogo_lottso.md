---
title: "ubuntu firefox pogo lottso"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by hickorynutz on 2008-09-14
Hi. Computer is compaq c500 laptop.  I just removed vista and installed Ubuntu, upgraded to hardy.  Got the wireless finally working, everything seems to work great except for playing Lottso at pogo.com.

When I go to join a room, the applet opens to the point of showing the chat area but the rest of the applet doesn't open, gives the message of loading, please wait.

I've read numerous tips online, here at this forum and elsewheres.

I updated every package.  I have java package installed,   I have the .so file in the firefox plugin folder.  I have flash installed.  

I was wondering if someone had a simple guide of what exactly needs to be done and what version of packages is needed to make this work.

I have even tried Opera browser and Seamonkey, same problem.  I deleted guarddog thinking it might be blocking it.   

Also I tried logging in via chatzilla to the ubuntu irc site but that didn't work but it ain't my main goal.....which is to get pogo working.

thank you in advance.

---

### Post by pavel989 on 2008-09-14
just cuz u have the java packages, doesnt really mean their totally isntalled or in use. i unfortunetly forgot the commands for it. check in the IRC's

---

### Post by the.phantom on 2008-09-14
might try going here (java test)

and see if your java works and what version


[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

it takes a bit for it to load ! ( say 30 sec max)

---

### Post by alzie on 2008-09-15
I'd check in synaptic package manager to see which java is currently installed by searching for java.

If its icedtea-java mark them for removal and apply
Then search for sun-java.
Mark sun-java6-plugin for install and apply. It should automatically pick up sun-java6-jre and sun-java6-bin.

Also make sure " ubuntu-restricted-extras " is enabled.

This is what I had to do to get pogo working for me.  There still is an issue if you want to check someone's profile,  it will crash the popup window.

I hope this helps

---

### Post by hickorynutz on 2008-09-15
> **the.phantom said:**
> might try going here (java test)

and see if your java works and what version


[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

it takes a bit for it to load ! ( say 30 sec max)

It only took a few seconds, I do have the latest version of JRE installed,
version 6 update 7.  thanks all for replies.

---

### Post by hickorynutz on 2008-09-15
> **alzie said:**
> I'd check in synaptic package manager to see which java is currently installed by searching for java.

If its icedtea-java mark them for removal and apply
Then search for sun-java.
Mark sun-java6-plugin for install and apply. It should automatically pick up sun-java6-jre and sun-java6-bin.

Also make sure " ubuntu-restricted-extras " is enabled.

This is what I had to do to get pogo working for me.  There still is an issue if you want to check someone's profile,  it will crash the popup window.

I hope this helps

Thanks Alzie, I have already removed icedtea, installed java6 plugin and the restricted extras.  Still no pogo, I could do without the profile bit.
Does yours work in lottso?

---

### Post by Denestria on 2008-09-15
I think you'll find that Pogo works badly with sun-java6.  When I had it installed right clicking on someone in the chat window would kick me out of the game, most games wouldn't even load with an applet bail error.  If you have problems try using sun-java5 it worked much better.

---

### Post by hickorynutz on 2008-09-15
> **Denestria said:**
> I think you'll find that Pogo works badly with sun-java6.  When I had it installed right clicking on someone in the chat window would kick me out of the game, most games wouldn't even load with an applet bail error.  If you have problems try using sun-java5 it worked much better.

Okay, finally got it working.  Profiles working also.

I searched for "icedtea" in 'places' and used terminal to go to all the hits and deleted them.  sometimes I had to use sudo -s.
Did the same thing with "openjdk".

reboot

then i disabled firewall guarddog.
then in terminal i deleted rc.firewall and rc.firewall~

rebooted and pogo lottso is working.  i tried a couple other programs and everything seems ok.

not sure which thing or combination of things did the trick, i had guarddog setup to allow everything that i thought pogo would need, maybe not.  anyway I see a lot of people having problems with pogo and ubuntu, don't give up! thanks to all.   

p.s. loving my ubuntu

---

### Post by Chinchy on 2008-10-14
The fix may be easier for you then uninstalling and reinstalling java. I could not play pogo games for months. What I found out was wrong was the java security settings. If you go under system then to preferences and down to java 6 control panel it will open the control panel. Next, go to advance and click on security. What I did was enabled the use SSL 2.0 compatible ClientHello format and enable online certificate validation, and pogo worked after that. I don't know if both in combination got it to work or if I only needed one checked but it works now. Also, the only things that are NOT checked under security is:

                  show site certificate from server even if it's valid
             and  check publisher certificate for revocation.
If you want to make sure all the things are checked that I have. Hopefully everyone gets it working as pogo's online help isn't the greatest. I dealt with them first before coming here.

---

### Post by bsyapril88 on 2010-05-06
Changing the settings of sun java worked for me.

Took me forever to get it going.  Seems like a silly thing.

---

