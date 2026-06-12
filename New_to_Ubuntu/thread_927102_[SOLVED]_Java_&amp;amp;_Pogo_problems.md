---
title: "[SOLVED] Java &amp;amp; Pogo problems"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by PT.Linn.A on 2008-09-22
I am ready to toss in the towel!

I cannot get Java to load Pogo games.

I understand that this is not a huge issue for a lot of people. However, I cannot get my wife to agree to a full Linux change until I can get her Pogo games to work.

I have read the other posts regarding Java and Pogo. But, have not been able to get it to work for me.  :(

Will someone walk me through, step-by-step, please?

---

### Post by zephyrcat on 2008-09-22
The problem here is that the Pogo Games site tries to deal with the issues itself instead of letting the browser deal with it. This can be better for Windows or Mac users, but often gets in the way on less used platforms.

Anyway, here is what made it work for me:

1. Go to this URL:
[http://www.java.com/en/download/help/testvm.xml?ff3](http://www.java.com/en/download/help/testvm.xml?ff3)

2. Look for a dancing thing. If you see, it, post that. If not, continue to follow this.

3. Find another site that uses Java and look for a bar at the top of the Firefox window about additional plugins. Click the buttons.

4. Follow the instructions and choose Java 6.0.

5. When all that is done, restart your browser, and try again.

Hope that works for you!

---

### Post by alzie on 2008-09-22
This is how I got Pogo.com to play

I checked in synaptic package manager to see which java is currently installed by searching for java.

If its icedtea-java mark them for removal and apply
Then search for sun-java.
Mark sun-java5-plugin for install and apply. It should automatically pick up sun-java5-jre and sun-java5-bin.

Please note is sun-java5,  I couldn't get sun java6 to work.

The only problem is if you click to see someone's profile it closes your game.  I haven't found a fix for that.  I'm hoping the next flash will correct it.

I hope this helps

---

### Post by PT.Linn.A on 2008-09-23
Thanks for the help.

I completely removed all Sun-Java with Synaptic, except:

Sun-Java5-Plugin, Sun-Java5-JRE, and Sun-Java5-Bin

Alzie was correct! Can't get Java6 to work with what I was needed/wanted to do.

Any ideas if there will be a fix for Ubuntu 8.10 regarding Java?

---

### Post by zephyrcat on 2008-09-23
Hmm... I have the Java 6 packages installed and it works for me, so I suspect there is something else different/wrong. I have no idea what, though.

---

### Post by PT.Linn.A on 2008-09-24
Java 6 was working with most of what I wanted to do. However, when it came time to load up a game on POGO ... forget about it!

With Java 5 I can still do everything I could do with Java 6 ... PLUS I can get the games to work. And, that is significant to me since without the games ability I have NO chance of convincing my Wife to abandon Win.

---

### Post by Sisyphus48 on 2008-10-26
> **PT.Linn.A said:**
> I am ready to toss in the towel!

I cannot get Java to load Pogo games.

I understand that this is not a huge issue for a lot of people. However, I cannot get my wife to agree to a full Linux change until I can get her Pogo games to work.

I have read the other posts regarding Java and Pogo. But, have not been able to get it to work for me.  :(

Will someone walk me through, step-by-step, please?

Man, I'm right there with you.  I have tried everything thats been posted on Ubuntu forums and nothing helps.  What is maddening is that the pogo tests tell me my pop-up blocker is fine and that I have the right version of Java installed and that it is working fine.  Then when I try to play, pogo :confused:tells me that Java isn't installed.  I've emailed the "support" for pogo and all I got back was an email asking for information that I included in the original email.  Pogo support  is as useless as tits on a boar!

---

### Post by alzie on 2008-10-26
I probably can't tell you anything you haven't already tried but Pogo works with me ( not 100% see above)
For Flash I have flashplugin-nonfree and ubuntu-restricted-extras from the repositories. 
For Java I have removed the iced-tea java and replaced it with sun-java5-plugin which pulled the java5 bin and jre files.

I am hoping that when Flash10 hits the repos that more of our issues will be solved, but as I said this works ok for me now.

Maybe something here will help you.

---

### Post by jyanek on 2008-11-25
where do I find sun-java5-plugin?  It is not in Synaptic.  I can find sun-java5-bin and sun-java5-jre.  I am using Intrepid (8.10), 64 bit.  Thanks.

---

### Post by himuraken on 2009-03-11
Bump Bump on that last one.

---

### Post by Miljet on 2009-03-11
I had the same problem when I upgraded from 7.10 (Gutsy) to 8.04 (Hardy). I fought with it for several months. Pogo games would run with Gutsy, but not with Hardy. I wound up making a new partition and re-loading Gutsy just so that I could run Pogo games. When I installed 8.10 (Intrepid), the problem disappeared. Pogo runs fine right out of the box and I am using the Sun-java6 plugin. I am running all 32 bit versions so don't know about 64 bit.
If you want to compare configuration files or anything, just post what you need.

---

### Post by hobo on 2009-03-13
I too have had problems running POGO games in 8.04 after upgrading from 6.06. What I found was TWO JAVA plugins resident in a Firefox subdirectory. Anyways, what I did was remove all JAVA from the system and downloaded the newest JAVA from SUN and installed. Then I deleted the OLD plugin and now POGO works just fine in 8.04 for me.

---

