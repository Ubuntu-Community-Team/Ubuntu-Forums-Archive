---
title: "Internet Security Suite"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by wharvey51 on 2008-07-17
Are there any internet Security Suites available for Ubuntu Linux 8.05?

---

### Post by mcduck on 2008-07-17
You don't need any.

Ubuntu has no running services that would respond to incoming connections, so a firewall isn't needed. But if you want one, the LInux kernel already includes a firewall, all you need is soem tool to configure itäs settings. Firestarter is a popular one, and the new UFW is great as well.

There isn't any Linux viruses in the wild, so a virus scanner is not needed. There are some, but only thing they do is scan for Windows viruses.

Also there isn't any spyware/Adware for Linux.

Edit: BTW, it's 8.06. The version numbers come from the release year and month. So, for example, 8.06 was released in June 2008.. Previous version was 7.10, releasen in October 2007.

---

### Post by tuxxy on 2008-07-17
```
sudo apt-get install firestarter
```

---

### Post by hyper_ch on 2008-07-17
no need to install antivirus or "firewalls". Mostly they cause more problems than they help.

so ignore what the poster above me has posted.

You might want to have a read here:

[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Canis familiaris on 2008-07-17
You dont need any antivirus, firewall or anti-spyware for Linux.
Just use your mind and do not copy paste commands blindly and you'll be safe.

---

### Post by DJ_Peng on 2008-07-17
> **mcduck said:**
> Edit: BTW, it's 8.06. The version numbers come from the release year and month. So, for example, 8.06 was released in June 2008.. Previous version was 7.10, releasen in October 2007.
At the risk of picking a nit, it's actually version 8.04. There was a point update that came out last month, but the version numbers are according to the month it was originally released, which in the case of Ubuntu Hardy was April.


Other than that mcduck's spot on about the lack of need for a 'net security suite in Linux. It's one of those great Windows habits that we can unlearn when we switch to Linux. I did the same thing 20 months ago.

---

### Post by hyper_ch on 2008-07-17
actually it's 8.04.1 ;)

---

### Post by DJ_Peng on 2008-07-18
True. I was thinking about the original release, and the fact that the OP may not have taken the update to .1 due to possible some holdover distrust of updates after using Windows for a while. Tux knows that when we see updates from Microsoft many of us first check to see if there are any reasons not to apply updates, especially with the latest MS update breaking ZoneAlarm.

Thank the Penguin Linux updates are vetted (and tested) better before being released.

---

### Post by tuxxy on 2008-07-18
> no need to install antivirus or "firewalls". Mostly they cause more problems than they help.

so ignore what the poster above me has posted.


That comment for me assumes to much, even if the firewall will cause more problems in your opinion does that mean he shouldn't know about it or try it?  

It could just be me but I thought his post said are there any...not should I use...

I was under the impression he would obviously be able to make up his own mind based on his running services and needs from his Ubuntu machine.

---

### Post by hyper_ch on 2008-07-18
> **tuxxy said:**
> That comment for me assumes to much, even if the firewall will cause more problems in your opinion does that mean he shouldn't know about it or try it?
They shouldn't try it just to have a firewall as on windows ;)

---

### Post by jimv on 2008-07-18
> **mcduck said:**
> btw, It's 8.06

8.04.1

---

### Post by tuxxy on 2008-07-18
> They shouldn't try it just to have a firewall as on windows 

I agree but again for me this comment assumes a lot, what makes you think this is the case, how do you know for example he isnt running a few services or planning too? and then when he asked if there is a firewall you gave him that original answer of there is no need....maybe you should of rephrased as **I** have no need....

To go on to state that he should ignore what me and mcduck suggested is just ridiculous

---

### Post by hyper_ch on 2008-07-18
> **tuxxy said:**
> I agree but again for me this comment assumes a lot, what makes you think this is the case, how do you know for example he isnt running a few services or planning too?
Experience with new linux users asking about it ;)

> **tuxxy said:**
> and then when he asked if there is a firewall you gave him that original answer of there is no need....maybe you should of rephrased as **I** have no need....
Why? You just seem to ignore half of my post - especially the two links with more details on that issue ;)

> **tuxxy said:**
> To go on to state that he should ignore what me and mcduck suggested is just ridiculous
Actually just to ignore what you told him to do - which is installing firestarter without actually knowing what he's going to do ;) never said he should ignore mcduck ;)

---

### Post by hovzio on 2008-07-18
So if I for example have an openssh-server installed I should not be running a firewall??

---

### Post by hyper_ch on 2008-07-18
> **hovzio said:**
> So if I for example have an openssh-server installed I should not be running a firewall??

not quite... you should make yourself concious what that services does that you run and then what you try to achieve and then you decide what the according measures are to secure that services - if any are needed at all...

by running a ssh server people will try to brute-force a username and password... so IMHO it is sufficient to (1) have a strong password and (2) to run a services like denyhosts or fail2ban which will auto-blacklist an ip with too many unsuccessfull login attempts in a too short time period. Some people also like to move ssh to another port but I prefer using standard port.

---

### Post by tuxxy on 2008-07-18
> Why? You just seem to ignore half of my post - especially the two links with more details on that issue 

Yes I viewed them, just some texts regarding virii and IPtables.

> Actually just to ignore what you told him to do - which is installing firestarter without actually knowing what he's going to do  never said he should ignore mcduck 

mcduck advised firestarter for configuring his IP tables, I too advised it and included the command he would use to install if he so wished now or in the future, how can you ignore me and not him if its the same advice...it seems your splitting hairs, trawling for arguments or atleast attempting to start them.

He thanked mine and mcducks original post so it seems he didnt ignore it as you had wished and it must of been of some use to him...I think this is maybe your problem...

---

### Post by jerome1232 on 2008-07-18
It's funny how these threads always start debates.

---

### Post by hyper_ch on 2008-07-18
> **tuxxy said:**
> Yes I viewed them, just some texts regarding virii and IPtables.
Have a read through them again ;)

> **tuxxy said:**
> mcduck advised firestarter for configuring his IP tables, I too advised it and included the command he would use to install if he so wished now or in the future, how can you ignore me and not him if its the same advice...
It is not the same... he said to install and configure it ;) you just gave a command to install it - and by doing the default rules on iptables will be changed ;) hence it's not the same

> **tuxxy said:**
> He thanked mine and mcducks original post so it seems he didnt ignore it as you had wished and it must of been of some use to him...I think this is maybe your problem...
I have no problem ;) and he just thanked about everyone - so I wouldn't give that too much meaning. But it seems to me you have a problem because I contradict you.

---

### Post by t0p on 2008-07-18
> **mcduck said:**
> 
BTW, it's 8.06. The version numbers come from the release year and month. So, for example, 8.06 was released in June 2008.. Previous version was 7.10, releasen in October 2007.

Hi mcduck, I was just wondering why you say it's 8.06?  Hardy is 8.04.  I've got a CD that shipit sent me, and it's got **Ubuntu 8.04 LTS Desktop Edition** printed on the front.  You're right about the version numbers coming from the year and month of release, but Hardy came out April 2008.

**EDIT:** Even though the CD I got has 8.04 printed on it, there's been an incremental update which makes up-to-date installations 8.04.1 - as a few previous posters have already pointed out.  Still, it certainly ain't 8.06!!

---

### Post by hyper_ch on 2008-07-18
he thought because the updated release would now be numbered 8.06 and not 8.04.1 ;)

---

### Post by t0p on 2008-07-18
> **jerome1232 said:**
> It's funny how these threads always start debates.

Some people think that, if a poster asks about the existence of antivirus and the like for Ubuntu, we ought to just tell them what software is available.  But others (me included) believe that someone posting such a question obviously thinks Linux is like Windoze, and that such a poster will be better served if he's enlightened as to the Linux security situation.  Debate is healthy.  But it's a shame if mini flame wars erupt as a result.

---

### Post by tuxxy on 2008-07-18
> 
It is not the same... he said to install and configure it  you just gave a command to install it - and by doing the default rules on iptables will be changed  hence it's not the same

At no point did mcduck tell him or explain to him anything about configuring his IPtables, he simply advised that firestarter would do the trick.  I expanded on this by including the command to install it,  we cannot tell him how to configure it simply because we dont know what services he is running, his needs etc so to just lie about what duck said to validate a fictious point of yours in a pointless argument you started is ridiculous.

Seriously save youself any embarrasment and just forget about it, what you are doing is immature and a dissapointment to these forums.

---

### Post by tuxxy on 2008-07-18
please delete

---

### Post by tuxxy on 2008-07-18
please delete

---

### Post by hyper_ch on 2008-07-18
> **tuxxy said:**
> Seriously save youself any embarrasment and just forget about it, what you are doing is immature and a dissapointment to these forums.

ditto

---

### Post by bodhi.zazen on 2008-07-18
If you are interested in learning security, start here :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

In terms of a firewall, the default firewall is iptables.

As of Ubuntu 8.04 there is no need for firestarter. 8.04 comes with ufw. Sure, it is a command line tool, but it is more secure, stable and more powerful then firestarter.

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

I think the question is not if you need a firewall or not, but rather what do you expect a firewall to do for you ? Once you answer that question it is much easier to know if you should install a firewall. It depends on a number of variables such as the users level of paranoia, the sensitivity of any data one is protecting, what servers are running, public or private ?, do you have a router ?

IMO most people who say you do not need a firewall mean, you do not need a firewall with a default installation of Ubuntu, are running no servers you wish to keep private, and you are behind a router.

IMO most people who say you need a firewall do not understand what it means that Ubuntu is running no servers, are inherently a little more security conscious, or are protecting a private server or sensitive data.

When the specific goals of a firewall are brought into the discussion there will often be a consensus opinion and not this endless, vague debate. The debate only starts with a general question in the absence of specific details of hardware/server configuration and/or specific goals of a firewall.

The main point here is, unlike Windows, a default installation of Ubuntu has no servers listening for connections so there is minimal or no need for a firewall.

I think this thread has otherwise run it's course and if you feel the need to debate firewalls please use the recurring discussions section :).

---

