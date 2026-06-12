---
title: "quick pre-install question"
date: 2016-04-14
forum: New to Ubuntu
---

### Post by LinuxNewbie1000 on 2016-04-14
Hi,
 New to Ubuntu and have a couple fast questions. 
1) Can I configure Ubuntu so that none of my desktop searches or other keystrokes (this is called Dash I think?) leave my computer, period. Not just doesn't get sent to Amazon, but literally does not produce any kind of http request to Ubuntu or anyone else?
2) Can I use Ubunutu offline, on a computer with no network connection (after I have installed it, possibly from a local ISO or CD)? Will it boot and function? 

THANK YOU COMMUNITY!

---

### Post by sudodus on 2016-04-14
Welcome to the Ubuntu Forums :-)

1. Ubuntu as well as other linux distros checks for updates/upgrades and download of what is needed: security fixes, other bug-fixes and improved features of the installed programs. It would be a bad idea to turn that off (particularly the securiy fixes), if you want to connect to the internet. Of course, it means that you trust Ubuntu and the company Canonical. If you don't trust these organizations, you should not use Ubuntu. Maybe you can trust another linux distro.

2. Yes, you can use Ubuntu offline (without any internet connection).

-o-

If you use the community flavours of Ubuntu, ***Kubuntu, Lubuntu ... Xubuntu***, there will be no connection to Amazon (that you need to turn off). But there will still be checks for updates/upgrades and download of what is needed. These flavours can also run offline.

Please look at the following link, [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity), and also the [sticky threads at the security forum](http://ubuntuforums.org/forumdisplay.php?f=338).

If you want to play very safe, maybe you should consider the linux distro Tails: [https://tails.boum.org](https://tails.boum.org)

---

### Post by LinuxNewbie1000 on 2016-04-14
1. Ubuntu as well as other linux distros checks for updates/upgrades and download of what is needed: security fixes, other bug-fixes and improved features of the installed programs. It would be a bad idea to turn that off (particularly the securiy fixes), if you want to connect to the internet. Of course, it means that you trust Ubuntu and the company Canonical. If you don't trust these organizations, you should not use Ubuntu. Maybe you can trust another linux distro.

Sorry, I think you misread my question. I didn't say anything about trust at all. I think it's obvious I trust Ubuntu and Canonical since I'm considering installing  it. With respect to your first answer, actually, with all due respect, your answer is not what was aasked either.  The first question didn't ask if it was a good idea to disconnect from the internet when I used Ubuntu (although my second question did ask if it would still work). The first question asked if it is possible to prevent my keystrokes from being transmitted to any 2nd party servers including Canonical's / Ubuntu's so that things I intend to be private, which I may type on my local computer, are truly private because they don't result in network connections to known or unknown 2nd parties. That is my question in part 1. 


Thank you sincerely for the direct answer to question 2.

---

### Post by Bucky Ball on 2016-04-14
Welcome to the forums. Along with what sudodus has said, are you talking about the Amazon lens thing? I'm an Xubuntu user so never used that. You can turn that off and I think it has been omitted from the next LTS, 16.04 LTS, due in about a week or so (could be wrong, read it on another thread somewhere). 

So, to add:

1. As above and per sudodus, but with a caveat for the update/upgrading. I don't do any automatic updates/upgrades. I use a terminal on a regular basis to do it, and that is easier than it sounds. 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

That's it. You can also update/upgrade using an application called Synaptic Package Manager which also handles installation/removal of packages (Ubuntu uses Software Centre, changed to Gnome Software (I think) in the next release).

2. Yes. :D

Once you're installed and up to date, if you're not online, really doesn't matter about security updates. You'd want to run those commands above when you do get online, though, particularly if its been awhile.

Be aware that Ubuntu works in a different way as far as installing and removing software. I advise you create install media (a USB or disk), boot from it and choose 'Try Ubuntu' (this will not change your hard drive in any way). Have a look around then ask some questions, if you have some. Have fun exploring. :)

---

### Post by sudodus on 2016-04-14
I help here at the Ubuntu Forums as a volunteer. I trust Ubuntu (and Canonical). It implies that I don't think that my keystrokes are transmitted to Ubuntu/Canonical. It also means that the software is reasonably resistant to attacks from other persons and organizations.

But if someone really wants to break into your computer, they will do it one way or another. And you can be sure that some big companies and security service organizations are supervising your web browsing habits.

---

### Post by LinuxNewbie1000 on 2016-04-14
Thank you for your replies !  I am excited about switching to Ubuntu.  Just to give 2 cents worth of background, I am a long time desktop application  dev, albeit always using Windows. As some of you may have heard, Windows 10 has serious and irremediable priovacy concerns. Specifically the transmission of keystrokes from the desktop to Microsoft servers and other servers is a real concern for us. 

It's up to me to be clearer about what I am asking. Irrespective of the source subsystem (Dash or other), or the destination (Amazon, Canonical or other) will keystrokes be transmitted from my Ubuntru desktop over the internet to anyone else? If so, is there an easy and clear way to prevent 100% of such transmissions from any Ubuntu subsystem? Of course this doesn't  include my deliberately using Dash (or other) as it's designed or searching for remote repos or apt or consciously using the internet as I am now. 

THANK YOU UBUNTU COMMUNITY!!

---

### Post by sudodus on 2016-04-14
I think that there is no keylogger in the Ubuntu operating system. I cannot issue any guarantee, because I don't know all the software in detail. I think nobody knows all details, it is too big. We have to trust the organisations (the linux community, Ubuntu and the company Canonical), or go away and use something else.

But an attacker might be able to install a keylogger, particularly if you visit certain web sites, or if someone breaks into your home and gets direct physical access to your computer.

---

### Post by LinuxNewbie1000 on 2016-04-14
LOL I doubt anyone is going to be interested enough in me to break into my house or target my computer for special attention of any kind. No point in worry about that since there's nothing you can do to stop it anyways.  I also  know keyloggers can be installed and all the rest or the dangers online of course. I am really asking the question you gave an answer to- is there a general keylogger in Ubuntu with (or without) network transmission the way there is in Windows 10? Canonical doesn't have an official pronouncement on this? That would be a great thing to have ! 

For the first time in decades, people I am talking with are actively and seriously planning their flight / defection from Windows. Even people who are adverse to CLIs are telling me they can't live with Windows 10 keyloggers. My company is amongst them. 

In a certain way, this is Linux's Big Chance, but for us, we need as much clarity as we can get on this issue. Any software / hardware may or could be backdoored by the TLAs of course but that is not what this question is about either, it's really about - to the limits of what's possible given the laws which are in fact in place-  can we run Ubuntu free of keyloggers baked into Ubuntu's core (or elsewhere) like we are UNable to do with Windows 10.  

Many thank yous for answering with what you know sudodus.

---

### Post by vasa1 on 2016-04-14
> **LinuxNewbie1000 said:**
> .., but literally does not produce any kind of **http request to Ubuntu** or anyone else? ...
Use some non-Ubuntu distro. All the best.

---

### Post by LinuxNewbie1000 on 2016-04-14
tnx vasa1

---

### Post by LinuxNewbie1000 on 2016-04-14
any suggestions?

---

### Post by grahammechanical on 2016-04-14
You should also read the Ubuntu privacy policy

[http://www.ubuntu.com/legal/terms-and-policies/privacy-policy](http://www.ubuntu.com/legal/terms-and-policies/privacy-policy)

And it is a matter of trust. Sometimes in life we have no choice but to trust someone or something. For example, in registering for this forum we place our trust in Canonical not to misuse the information we provide & to protect it from others who would misuse the information. Our choice is, to trust or not join the forum.

We install Ubuntu but we do not join a cult. Likewise, there is nothing wrong with anyone of us saying, if a person does not like what Ubuntu is, then there are other distributions that may be more to their taste.

Once Ubuntu is installed we can go to System Settings>Security & Privacy>Search tab and turn off Online Search. This means that when we search in the Dash it will only search our hard disk & not onto the internet.

If we can go to the Files & Applications tab we read:

"Files & applications you've used recently can be shown in the Dash & elsewhere. If other people can see or access your user account, you may wish to limit which items are recorded." 

We can turn off this recording. We can clear the usage data. We can deactivate this recording for specific applications. There is a trade off between privacy & convenience.

Regards.

---

### Post by QIII on 2016-04-14
I would say with a fair degree of certainty that no keystrokes are recorded and sent to Canonical except for those you send specifically with that intent (just turn off the Amazon lens if you don't like it.).  One case I can think of where that definitely happens is during updates, when you communicate your update wishes to Canonical's repository servers.  However, given that we are all users and not developers, we cannot make an absolute statement with regard to this.

As for running offline:  yes, of course you can.

---

### Post by jay_bowles2 on 2016-04-14
Seriously, Linux is not Windows. One of the great things with open source is that anyone (including you) can look at the source code for such back doors. Ubuntu uses, open source software, except proprietary stuff that you need to give explicit instructions to install ie Nvidia drivers. Ubuntu cannot check that. As for trusting Canonical (the commercial company behind Ubuntu).... well that would be really up to you to decide. Obviously I trust them, otherwise I wouldn't use Ubuntu. The other flavours of Ubuntu don't connect to Amazon for searches, which some in the Ubuntu world have called spyware..... But this can be deactivated in settings and I believe is there to provide a degree of user experience and obviously an income for the free (of charge) OS.

As an aside I use Kubuntu on my main PC and Ubuntu on my laptop as it runs nicely on it. :) I hope this clarifies things. :)

---

### Post by grahammechanical on 2016-04-14
Open the Dash and open the Applications scope (second icon from the left out of the five icons at the bottom of the Dash) & look for Dash Plugins. Right click on a plugin and we get an option to disable the plugin.

Regards.

---

### Post by LinuxNewbie1000 on 2016-04-14
jay_bowles2b (and everyone else too !)
 
Thank you for your reply!

Yeah I could look at that code but the reality of open source is very unfortunately not equal to the hype for a number of very good reasons. First, the code base for open source is vast and specialized, too much so on both counts for one person but also for a community it appears. For all the ink spilled about systemd, there was precious little that took the form of code alternatives. 

That's just a fact of life; anyone who codes for a living knows code can be inscrutable, as in, totally inscrutable to anyone outside a small group of experts and worse, a million eyes does not (heartbleed) unfortunately amount to the level of assurance we had hoped it would. This is not anyone's fault and more like a fact about the natural world involving time limitations and cognitive limitations. More power to open source ! It is what it is and I am the last to blame its (our) shortcomings on anything but mother nature herself.   

Aside from that, it's become apparent that even billiionaires are forced to live downstream of bigger fish and Ubuntu's acceptance of systemd serves me as proof positive  that even if I were a billionaire -that's spelled with a b- I *still *could not control a code base as big as Linux and even if I, through some heroic means authored something like Linux, I still couldn't control it more effectively than Linus. 

So, well, now we know all that and it's not good news but  it is  always good to know reality so you don't end up acting on false hope.

So yeah, I could look at the code, I could rewrite systemd, I could do a lot of things given a few more lifetimes but it's not going to meaningfully happen. 

I'm just a person looking to keep my private thoughts / business plans / strategies / dreams / etc. private. 

Here's the thing for me. I do depend on providers just like everyone else but the ones I have the most confidence in are the ones I gave money to. 

It's worth 100 bucks a year to me to have an OS that only responds to court orders and otherwise shields me and my data from the outside world.  I have got to think that it's worth that much if not to everyone, to at least a million or two (or more?) people all over the world and 100 -200 million dollars seems like enough of an annual budget to net me that. I am happy to support the people who download for free-as-in-beer and really, I feel nothing but lucky to be able to pay in the first place. 

So if there are a couple million people like me, then why the market failure? Does it truly not know that this is what we really really really really want or is there some other force at play here?

---

### Post by jay_bowles2 on 2016-04-17
Obviously no-one can look at all the code installed in your standard distro, but the fact that it IS free to inspect gives it a major advantage over proprietary OSes, where you are explicitly trusting the whims of the company or share holders behind it. The other thing with Linux in general, is look at the major deployments in server centres of many of the largest online businesses. Why? Well partly the reason is security. Those companies can check the source code.

And yes there have been vulnerabilities (and always will be in code) but as again it is open source they tend to get patched very quickly (once known about). Also how can any government try to influence a operating system that is worldwide??

To be honest you will be barking on your own if you are arguing that proprietary is better than open source here! :D

---

