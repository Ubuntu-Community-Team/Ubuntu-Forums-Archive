---
title: "Internet Filter"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by arendell on 2011-12-03
I'm looking for an internet filter that I can install with Ubuntu, where I can set parental controls to limit where my kid goes (what she sees) on the internet.

I also know next to nothing about command line commands.  So gotta be easy for a dummy like me to install.  :)

Thanks.

---

### Post by Gone fishing on 2011-12-03
Squid and Squidguard will do this well - too well. This is what I use for filtering.

However it isn't so easy and more than you need try Googling dansguardian I think it's what you want.

---

### Post by SirWeazel on 2011-12-03
I'm not sure what your end goal is, but depending on how old your kids are you might want to check out "kidzui."  You can use the firefox plugin, I've installed it before for family. But it's been awhile since I've checked up on it.  

It does have some cool features and can even email you reports. Plus it's simple for the kids with content they might want. But this all depends on age group and what you really are trying to do.

---

### Post by Frogs Hair on 2011-12-03
Nanny is the only option in the software center and the reviews are very poor . Follow Gone fishing's or other suggestions .

---

### Post by BBQdave on 2011-12-03
Good info :)

I too have little ones that will soon be on the web... I need to explore filters as well.

My Wife says when the time comes for the kids to use the web (for school), that we will have a centralized computer (maybe in the family room) that they will use.  The idea is that they do their computing while we are around.  It is a good idea, but with the advent of smart phones and more schools going to tablets, not to mention the existing netbook per kid in schools...

I am not sure how to protect kids, other than educate and *talk* with them about appropriate web behavior (social forums).

It is funny how the *Talk* with kids has changed to include web use and appropriateness :)

---

### Post by oldos2er on 2011-12-03
Try OpenDNS, [http://www.opendns.com/](http://www.opendns.com/)

---

### Post by arendell on 2011-12-03
Thank you for the suggestions, folks. Much appreciated!

---

### Post by Gone fishing on 2011-12-04
If you have an old box that you could use then ipcop with urlfilter would probably make a fantastic setup - headless controlled with a web interface and all the features you could want - you can get the actual blacklists from here: [http://urlblacklist.com](http://urlblacklist.com)

You could also do the same with ipcop or pfsense (which I use as a firewall) and [www.opendns.com](www.opendns.com). This would cost a little money for the opendns service.

---

### Post by arendell on 2011-12-20
Okay,so I'm feeling pretty foolish right now.  As I noted in the OP, I'm not too savvy with Ubuntu (read:  I ain't got a clue).  I was hoping that Dan's Guardian would just be as easy as downloading and then clicking "Install", and VOILA.  But, apparently, I have to know some code to install it.  

The download instructions don't help me.  They're written for someone who's got a little knowledge already.

Any chance some fine soul could walk me through the installation of DansGuardian?  It's not my laptop (it's my daughter's), and I don't have much time to invest in learning.

Thanks,
Randy

---

### Post by arendell on 2011-12-20
Frustrated with my level of ignorance, I decided to go the OpenDNS route instead.  Nothing to install;  just redirecting DNS.  Seems strong so far.  I wish there was a way to block objectionable content on YouTube, as well.  

Still digging, though.  And just thinking out loud.  :)

---

