---
title: "Deluge, encrypted connections, safe in UK?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by adwatkin19 on 2008-08-19
I live in the uk, and at the moment the 6 main largest ISP's have grouped together to crack down on people sharing games, music and movies over the internet via file sharing.

They have sent thousands of letters out to warn people that they are aware of that they may face prosecution if they continue.

My question is, if in deluge you encrypt the outgoing and incoming connections, will that cover what peope alre doing thus allowing them at least a little protection, or will it all be recognised and followed as file sharing traffic.

Thanks for any help or advice people can shed on this. 

Adwatkin19

---

### Post by Pro-reason on 2008-08-19
They will probably just throttle the speed of any torrent-style data they see.  It doesn't matter if the data is not in infringement, or encrypted.

---

### Post by Archmage on 2008-08-19
Encryping your connection will only disquise that you are P2P so that your ISP won't throttle you down.

But someone that takes part on P2P can still see that you are downloading from him.

---

### Post by insane_alien on 2008-08-19
they are going through the torrents and checking ip addresses. not looking for p2p traffic.

use a good blocklist and you should be fine.

---

### Post by hyper_ch on 2008-08-19
don't torrent anything illegal according to UK law and you should be fine.

---

### Post by solitaire on 2008-08-19
Also change ISP from the "Big 6" to a better ISP :D

if torrents connections are encrypted their is not a lot the ISP's can do without reinvesting in "Deep Packet Inspection" machines. Also they are sending those "P2P are illegal stop it" letters to all their customers that have a high bandwidth usage regardless, even if the user is using it for Legal means, i.e. Streaming BBC, 4OD, Five & SKY Anytime feature or even just D/O every Linux ISO around :D

Since more any more Legal P2P options are poping up ISP's are going to have to invest in more £££ in bandwidth rather than restricting users...

---

### Post by nynoah on 2008-08-19
In seriousness, will encrypting keep them from figuring out what files I have coming down?

---

### Post by forger on 2008-08-19
> **nynoah said:**
> In seriousness, will encrypting keep them from figuring out what files I have coming down?

[http://en.wikipedia.org/wiki/BitTorrent_protocol_encryption](http://en.wikipedia.org/wiki/BitTorrent_protocol_encryption)
> Some ISPs are now using more sophisticated measures (e.g. pattern/timing analysis or categorizing ports based on side-channel data) to detect BitTorrent traffic. This means that even encrypted BitTorrent traffic can be throttled. However, with ISPs that continue to use simpler, less costly methods to identify and throttle BitTorrent, the current solution remains extremely effective.

---

### Post by tuxxy on 2008-08-19
Has anyone received a letter yet, im interested to know how many torrents it would take before receiving one aswell.

---

### Post by adwatkin19 on 2008-08-19
I haven't had a letter yet, I sort of expected one by now to be honest. 

Although from news bits i have been seeing on the internet the main ones getting letters and in trouble are the uploaders. or quote "Prolific uploaders".

---

### Post by nicedude on 2008-08-20
In seriousness, will encrypting keep them from figuring out what files I have coming down? 

YES it will stop them from seeing what files unless they are participating in the torrent swarm ( like all the little spying companies do ) but it won't stop them from figuring out that you are downloading stuff in general, nothing really will since the data has to move across their lines to get to you and they will pretty much know that 5GB a day of incoming data from 1000 locations means downloading. I would suggest at least using moblocker or ipblock in conjunction with some of the bluetack lists ( at least level 1 & 2 list as well as the government list ). I recommend ipblock which is part of the iplist software package. Just install iplist and then go to Applications -> Internet -> ipblock to run it. 

You can get iplist ( which contains ipblock ) here in the form of a Deb package for Hardy
[http://sourceforge.net/project/showfiles.php?group_id=198679](http://sourceforge.net/project/showfiles.php?group_id=198679)

Hope that keeps the government out of your hair :-)

---

### Post by Nepherte on 2008-08-20
I guess they don't make a difference between downloading a legal ubuntu distribution and some illegal movie, both with torrents?

---

### Post by Rolcol on 2008-08-20
The newer versions (much new than the one in the repositories) of Transmission has a blocklist that you can update that will keep you from downloading from certain peers.  The blocklist blocks 222,683 IPs.  If you want it, you have to either compile or find a .deb file floating around.

---

### Post by t0p on 2008-08-20
> **nynoah said:**
> In seriousness, will encrypting keep them from figuring out what files I have coming down?

Yes!  As Forger points out above, the ISP will still be able to figure out you are downloading torrents.  But they won't know *what* you are downloading.  Which means you can't be successfully prosecuted for copyright infringement. (Unless you do something dumb like confess!)

---

### Post by t0p on 2008-08-20
> **hyper_ch said:**
> don't torrent anything illegal according to UK law and you should be fine.

I realize you're just parroting forum policy, but it isn't relevant tothe OP's question.  He wanted to know if encrypting the p2p traffic would stop his isp from knowing what content he is downloading.  Reminding him not to break the law is hardly helpful!

When someone asks a question about encryption, I think it's bad form to start going on about the legality or otherwise of what he wants to encrypt.  He wants to keep the stuff secret - that's what encryption software is for - so let's not accuse people of being crooks eh!

---

### Post by hyper_ch on 2008-08-20
> **t0p said:**
> I realize you're just parroting forum policy
You realize wrong ;)

> **t0p said:**
> When someone asks a question about encryption, I think it's bad form to start going on about the legality or otherwise of what he wants to encrypt.
He did not ask for encryption in general but specifically to the UK... and whether he's "safe". IMHO it's evident what he's trying to accomplish. He's not worried about data he transfers in general but whether he might get caught.

And then not to forget:
> **adwatkin19 said:**
> I live in the uk, and at the moment the 6 main largest ISP's have grouped together to crack down on people sharing games, music and movies over the internet via file sharing.

---

### Post by t0p on 2008-08-20
**hyper_ch**: everything you say above is true, and is irrelevant.  It really doesn't matter what the OP wants to encrypt and why he wants to encrypt it.  This is a *technical* forum, the OP has a *technical* question, we should endeavor to give him a *technical* answer.  He wasn't asking a legal question, so why give him your legal opinion?  As I already said, it's bad form.

---

### Post by hyper_ch on 2008-08-20
> **t0p said:**
> It really doesn't matter what the OP wants to encrypt and why he wants to encrypt it.

Yet it does as it's against the Ubuntuforums CoC. You forget that postings in here will be reflected on Canoncial.

If he generally asks about encryption --> then it does not matter.

If he asks about encryption and says he wants to circumvent legal provisions in his country --> then it does matter.

As far as you want to seperate technical and legal issues, you just can't do that on a public forum.

---

### Post by t0p on 2008-08-20
> **hyper_ch said:**
> Yet it does as it's against the Ubuntuforums CoC. 

Earlier...

> **t0p said:**
> I realize you're just parroting forum policy

> **hyper_ch said:**
> You realize wrong ;)

Seems I realized right in the first place, huh?

---

### Post by hyper_ch on 2008-08-20
Not really... I'm not parroting but I do keep in my as to why this policy is there.

[http://wordnet.princeton.edu/perl/webwn?s=parrot](http://wordnet.princeton.edu/perl/webwn?s=parrot)

And besides, there are many ways to solve a problem. You only have the techincal focus in mind. I think not in such a narrow way. As the TO wants to fileshare stuff that's considered illegal in his country another option is to not do that anymore. ;)

---

### Post by nothingspecial on 2008-08-20
Knock it off please. This discussion should be somewhere else.

---

### Post by nynoah on 2008-08-20
Thanks I found MoBlock here 
[https://help.ubuntu.com/community/MoBlock]("https://help.ubuntu.com/community/MoBlock")

---

