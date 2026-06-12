---
title: "Root powers and rescue mode"
date: 2010-02-07
forum: Recurring Discussions
---

### Post by Gorgonkernel on 2010-02-07
I just don't understand this. Why when booting into rescue mode, anyone has acces to the root account without having to type a password. What security is this and why there isn't required any password in order to access root from the rescue mode?

---

### Post by Gorgonkernel on 2010-02-07
No one can help me?Please!

---

### Post by falconindy on 2010-02-07
Physical access is root access. Even without rescue mode, root access is only a liveCD away. Filesystem level encryption can circumvent this to some degree, but adds a level of complexity some users aren't interested in.

If you're concerned about this, you need to secure the area that your computer is in with lock and key.

---

### Post by Gorgonkernel on 2010-02-07
Thanks for the reply but for example if I leave my laptop on my work desk and leave to get some food. Everyone can access all my files regarding if they are encrypted or not because root can also go in the /private folder....or simply could compromise my machine. I love your irony but unfortunately I can't get a key and a lock for my machine...is there a way to PREVENT LOGGING DIRECTLY TO ROOT WHILE RESCUE MODE?

---

### Post by overdrank on 2010-02-07
Moved to Recurring Discussions

---

### Post by theozzlives on 2010-02-07
Just take your laptop with you. Talking about security, I can bust into any Windows machine and obtain all usernames and passwords.

---

### Post by houseworkshy on 2010-02-07
A good point.  If one chooses to encrypt ones home folder, an option available during installation and later if wished, then files will be unreadable.  However I suppose someone could copy the lot and try to decrypt them, they could also make a right mess of the system if they wished.  This is also true of windows, a feature I've actually been glad of when backing up documents prior to attempting to mend an xp installation.  The above poster is right though and I *think* this applies to all operating systems though I don't know about macs.  Several distos which aim at security do it by running only as a live cd which saves work to a memory stick and overwrites ram before shuting down.  Another approach is to have decryption keys so huge they live on the equivalent of a memory stick.  It still boils down to an object which must be kept out of the hands of vandals and villans.  Just one of those things.  Personally I never bank online.

As an aside to that one thing I don't understand is why postal orders and po boxes are not booming in this era of identity theft.  Seems obvious, research online, buy a postal order and get proof of payment, the vendor gets the cash, makes the delivery, both paries get proof, and no personal details are disclosed.  One could always install xray machines and sniffers for drugs and explosives at where ever the po box depot is.  I suppose companies like to collect information and this ancient method would spoil things.

---

### Post by Gorgonkernel on 2010-02-07
Thanks overdrank for moving this topic. Listen theozzlives, with all the respect, Windows is not LINUX. So giving me an example like that is 0, NOT RELEVANT. When I go to get some fast food I don't want to get my laptop with me. Isn't this a little awkward that anyone can boot into rescue mode and be root with no password? So is there a way to stop that? I AM REALLY concerned about security...and see this as a negative aspect to Ubuntu.

---

### Post by Gorgonkernel on 2010-02-07
No one can answer my question?

---

### Post by houseworkshy on 2010-02-07
Actually a live cd can read windows just as easily as it can linux.  Perhaps your best method would be to use a flash stick with a huge encryption/decryption key on it.  When you go to lunch take it with you.  Yes they could still get at your desktop but without the key would have little chance of doing anything with stolen data.  As an additional security, against villains installing malware, you could also use some of the checksum programs to make sure that your system has not been tampered with.

---

### Post by houseworkshy on 2010-02-07
As an attempt to answer your question, how about this.  Any method which blocked root access to a stranger at the keyboard would also have to apply to the legitimate user sitting at the keyboard.  Unless one used retina scans or finger prints, which are available technologies now I that think about it.....  Hummm ever see that sci fi film, can't remember what it was called now, where a guards head was cut off in order to fool such a system?  I think that I'd rather hand the flash stick over to the baddie actually.  Short of that the small portable object which is crucial in making the big object, and the data in it, useable is probably the best bet.

---

### Post by houseworkshy on 2010-02-07
deleted

---

### Post by yester64 on 2010-02-07
> **Gorgonkernel said:**
> I just don't understand this. Why when booting into rescue mode, anyone has acces to the root account without having to type a password. What security is this and why there isn't required any password in order to access root from the rescue mode?

Can't confirm that. If i boot and drop to root you need a password.
As far as the boot process goes for the bios, you should disable booting from any other source then the harddrive.

---

### Post by rajcan on 2010-02-07
What do you need rescue mode for? If you're REALLY concerned about this why don't you just go into grub's menu.lst file and remove the entry for rescue mode? And again, like everyone here has said, root access to your machine is just a liveCD/USB away.

---

### Post by Hetor on 2010-02-08
> **rajcan said:**
> What do you need rescue mode for? If you're REALLY concerned about this why don't you just go into grub's menu.lst file and remove the entry for rescue mode? And again, like everyone here has said, root access to your machine is just a liveCD/USB away.

You can still get into rescue mode even if there's no grub entry for it (well, at least with GRUB 1). Just press E on the boot menu and it'll let you edit the boot options.

---

### Post by Barrucadu on 2010-02-08
To prevent entering rescue mode, remove it from the GRUB menu.

&#8230;and, to stop someone from editing the GRUB options: GRUB password!

&#8230;and, to stop someone booting from a CD: BIOS password!

&#8230;and, to stop someone simply stealing and reading the HDD: filesystem encryption!

&#8230;and, to stop someone stealing the computer: locks and bolts!

&#8230;and, to stop someone removing the locks and bolts&#8230;

Physical access *is* root access.

---

### Post by doas777 on 2010-02-08
> **Gorgonkernel said:**
> No one can answer my question?
I didn't think you were asking a question, you expected us to answer. sounded retorical.

simply put, physical access is root access. this is true of ALL computers regardless of os.


now if you want to make it harder for an attacker, set a grub password and a bios password. then set your system to boot off the hdd as #1. 

that of course will only hold up if you can prevent the attacker from clearing your cmos (using a nothing but a screwdriver), clear the password and boot from live cd.

disk encryption is one way to try to secure your system, but if they have it in their posession, they can just hibernate it, scrape teh ram, and retreive your ency keys. or if they are familliar with your disk encryption system, there is usually an enterprise feature that allows admins to get in, which can be subverted. there is one industry leading disk encryption system (which shall remain nameless) that has really strong ency, but has an enterprise recovery system that can be cut through in seconds.

---

### Post by yester64 on 2010-02-08
I am myself would like to secure my system as much as i can. Simply to avoid losses due burglary or else.
One thing that helps is to 
a) limit booting to just the harddrive
b) password the bios (strong password helps)
c) encrypt the harddrive like with truecrypt

(i think these things were already mentioned)

But there is also a downside to this.

In case someone wants to get really bad onto your things and can't, he may simply force you by pointing something (fill in) at you.

There are certain way's to protect data's but it only goes so far.
I still think it is more secure than windows. I also would argue that if you encrypt a harddrive that a rescue disk will not recover data's. You would need the key to decrypt them. That is the whole point of encrypting.

So for physical loss, encrypting is a good (or best) solution. That, i think, even applies to web theft in that someone can not grab data's if they encrypted.

---

### Post by MarcusW on 2010-02-09
Isn't it as easy as setting a root password?

---

### Post by houseworkshy on 2010-02-09
I posted and then deleted, the hd only boot and bios password thing, because I think it is such a bad idea.  It's been posted anyway now so.....The danger is that one makes the computer so secure that, should it go wrong, corrupted passwords or key mapping for example, one is in real trouble.  As pointed out before even bios can be reset with jumpers switches or just taking the battery out for a while so why bother.  All Internet activity is recorded down to every mouse click and keystroke so if any of the secrets involve on line activity even throwing your machine into a furnace won't kill the data.  I have also read of technology which can read data from monitor emissions or your power supply.  

As an aside, but still on topic, the latter will probably lead to an integrated power and data grid.  As this would utilize existing power grids it would be the cheapest optition.  Because it will be so difficult for alternatives to compete against economically when the technology is ready for large scale global implementation it's near certain. 
 [http://www.faqs.org/patents/app/20080238204](http://www.faqs.org/patents/app/20080238204)
   [http://www.physorg.com/news110480330.html](http://www.physorg.com/news110480330.html)  

At the moment the technology is already there for small networking and surveillance purposes.  If you search for it you will find many companies which are offering the stuff for sale, it is actually so developed it's become cheap, therefore, if paranoid, don't even plug the machine in to the mains.  

If one looks at quantum physics the relationship between entangled particles irrespective of physical separation may even lead to data transmission which is not limited by the speed of light, instant.  Particle entanglement has implications for both spying and cryptography   [http://whyfiles.org/shorties/133quantum_leap/](http://whyfiles.org/shorties/133quantum_leap/)

It's on the way

[http://physicsworld.com/cws/article/news/40067](http://physicsworld.com/cws/article/news/40067). 
 
There was also an experiment which worked between Europe and America but I don't have time to dig it out at the moment.  Searching for "+computers +"particle entanglement" +experiment +successful" will pull a lot if you feel like reading up on it.   Wikipedia has a good article too with links.  One implication of this is that even denying physical access, including connections, won't do any good.

So how can you secure your data?  You can't.  Might as well ask how can I fly to the moon using nothing but a paperclip.  Mac, Linux and Windows simply aren't capable of perfect data security though the first two are less bad at it.  Incidentally the British stock exchange have just opted for a Linux based system, I assume that is after taking expensive advice.  If ever someone did find a way of making data uncrackable, should anything ever go wrong the machine would become an expensive pile of junk.  You wouldn't be able to get in to mend it either.  In short if one can get at it, even the user, so can another.

What you *can* do is make it easy and, more importantly, quick for the user to use the data whilst making it difficult and time consuming for someone unauthorized.  The idea is that by the time a criminal has got at the data it is irrelevant, sort of   &#8220;At last! I've got Shakespeare's identity...the royalties for &#8220;Hamlet&#8221; are mine, all mine!  ...er ...what does public domain mean?&#8221;  All 'keeping data safe advice boils down to this, buying time.  So if it is something like secret company strategy or an invention use a time buying method.  Recent editions of Ubuntu make this easy, during the install one is asked to encrypt the home folder.  This means that though someone could access it with a live cd  they'd need to decrypt it, or get your password, before they could make any sense of what they'd found.  Which could eventully be done but hopefully you'd have had the good sense to alert authorities to behaviour patters and risks likely to arise from knowlage of the stolen data, cancel bank cards etc by then.  The user however, after putting the password in can use it normally.  Obviously this only works if you shut the machine down when leaving it unattended. Few will care or be able to do damage with what Gorgonkernal Ltd planned to wow the market with several years ago.
 
Against identity theft I just trust banks to do this for me, they have the vast amounts of money needed to maintain such things.  Judging by recent news. even google and other un-named  big companies don't seem to have the resources to succeed all the time.  Never bank on line unless absolutely necessary and when insured against identity theft.  And yes I know everyone wants you to, not only because it is easier and cheaper for them, frankly they want to pull as much personal data as they can along with the transaction too.  You will have no alternative a lot of the time.  For times like that various on line banking schemes do insure against loss due to their systems being compromised, so go with one of them.  Research on line yes, but avoid online financial action when ever you can.  The final answer to &#8220;how do I make my data secure?&#8221; is the sound of one hand clapping.

---

### Post by rottentree on 2010-02-09
I simply don't get this.
You leave your laptop somewhere and your problem is that someone might boot into rescue mode to steal your precious data?
They could just as well pick up your laptop and take it home.

---

### Post by yester64 on 2010-02-09
Well, there are some pro and contra's on that issue.
But the main reason you want to secure a system is to limit access to people who are allowed to use it and everyone else not.

There is of course the fact, that there is no 100% security.

But should you not try to make it harder for others? This is for everyone to decide but personal information should be made secure.

Of course once you establish a connection to the internet, you are visible and could be exploided. Now you do not have to be paranoid really but use some common sense and can be securer.

I favour 

a) good browser
b) firewall (only open ports you really need)
c) only visit sites you know are secure or safe
d) limit information you share

Of course you can limit even the use of banks to be offline only. But i think this is a little paranoid already.

Secondly, some people use 2 computers. One for web and one (not hooked up to the internet) for the serious work.
I only have one computer.

I still think that protecting your computer is a good thing. Encrypting is one thing someone can do. Also use a good password.
With good i mean long and make heavy use of lower/capital letters, numbers, symbols.
Also, if someone wants to get it, they will gather information about you. social hacking is the first step to make the actual hack.

To a previous post, yes i heard about that and actually read about it years ago. Monitors can be read out from afar to collect datas.
Even sound can be filtered. Every keystroke emits a different sound or frequency. So once someone records the keystroke, someone can know what you typed.

Again, no 100% security. Altough in normal life i do not think that someone uses that. That would only apply to something bigger.

How do you all secure your computer? I don't think i have anything special running as what came with ubuntu.

---

### Post by doas777 on 2010-02-10
> **MarcusW said:**
> Isn't it as easy as setting a root password?
no, not really.
first, your system is more secure with the root account disabled for many usecases (especially if you run ssh or other webservices).

additionally, how to you reset the root password if you are locked out and can't remember what you set it to? single user mode is exactly for this usecase, and assumes that the only user that can get on has physical access to the host. it makes more sense in the old server/mainframe world where the box is behind a locked door though.

---

