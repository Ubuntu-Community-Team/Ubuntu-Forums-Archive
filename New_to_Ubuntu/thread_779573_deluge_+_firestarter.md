---
title: "deluge + firestarter"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by myddewji13 on 2008-05-02
ok...deluge seems to be the fastest torrent client i've ever used on linux...but i have a couple problems...it only works when firestarter is disabled...under permissions for firestarter i have all the 'regular' torrent ports available...if i got to event while both deluge and firestarter are running there are like a million hits on a bunch of diff ports....some help guys...how do i configure firestarter to allow deluge to open whatever it needs...and if i cant do this..anyone have a port range etc...that i need to open? .. any help appreciated..thnks guys

---

### Post by Dark Hornet on 2008-05-02
Well, Deluge has two options as far as ports go...1.  you can use the "standard" torrent ports--and it tells you what that is, or 2.  you can set it up to use "random ports"...and you can set a range of ports for it to use.  I think it sets a range in the high 60000's or so by default to use.  Personally I use the random ports, and I just let my firewall know what that range is, and all is well.  Good luck!

Darkhornet

---

### Post by rfurman24 on 2008-05-02
You have to allow Firestarter to allow the port Deluge is using. The port Deluge uses is set in network section of Deluge. In Firestarter you need to right click and add policy under the policy tab and in the allow service area.

---

### Post by myddewji13 on 2008-05-02
it is set to 'standard ports'...but that didn't make a diff...how do i set up a range of ports? ... and can i limit them to deluge use only?

---

### Post by Dark Hornet on 2008-05-03
If you click on "Preferences", and go to the "Network" tab, at the top you will notice a little section regarding your ports.  There is a check box that you can check to use random ports, and you can select a range to use...right now I am using 6881 to 6889 as my "random ports."  Once you have selected the ports, hit ok, exit completely out of Deluge, then restart it...all should be good.  Let me know if you have any issues.

Darkhornet

---

### Post by Kizsde on 2008-05-05
Hi All!

I'm totally green when it comes to Ubuntu, just installed it(HH 8.04) couple of days ago. I'm extremely satisfied with it as almost everything was identified correctly, I could set up the network connection in 5 minutes and had no problems whatsoever with any applications. The only thing that concerns me is in connection with Deluge torrent client and Firestarter. I installed both and could start them without a problem. I started downloading some torrent files and just out of curiosity I checked the active connections section in Firestarter and found that there were services called "Cheeseworm" and "Webadmin". I didn't find much about these after some searching in google, just that it is in connection with trojans, so I got a bit nervous. After this I also added an url to Deluge for IP blocking and since then I didn't see any sign of "Cheeseworm" or "Webadmin". Could someone advise if I should be worried or if there is no threat? Also if someone could explain what the above mentioned 2 'services' are exactly and how do they work that would be great!

Sorry but I'm a total noob when it comes to this kind of stuff :lolflag:

Thanks in advance!

Kizsde

---

### Post by Paqman on 2008-05-05
> **myddewji13 said:**
> ...it only works when firestarter is disabled...

Is that a big problem? Firestarter shouldn't be running normally anyway.

---

### Post by hyper_ch on 2008-05-05
firestarter is nothing but a front-end for iptables and it does not matter whether it runs or not as iptables will always run. So the question should be how to allow iptables this or that...

But I have to say here that you probabaly installed firestarter (and hence added some rules) just for the sake of it. Normally you will not require a firewall... you only require one when you start offering services and want to have control over them. Furthermore there should be a firewall on your router. So if that one is properly configured there's another reason why you don't need altering the default iptables configuration.

---

### Post by myddewji13 on 2008-05-05
agreed...for now when i'm home i just put firestarter on 'stop' mode b/c my router has a firewall...however this is a laptop and i travel quite a bit...i don't really trust all the networks i hook up to.. also the prev. suggestions didn't really work :( ..

PS is there anyway to revery firestarter to default iptables rules?

---

