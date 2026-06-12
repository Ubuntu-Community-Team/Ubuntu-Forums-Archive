---
title: "Antivirus checking needed for Hardy"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by swarup on 2008-05-08
I have a dual boot with Hardy and Vista. I often download software while in the Hardy partition, which will be used in Vista. So I need to be able to check it for viruses before I install it in Vista. I do not go online with the Vista partition, nor do I have any antivirus software installed in it. I have gone into Synaptic Package Manager and there are various utilities listed: ClamAV, OpenAntiVirus, Trophie, AVG, f-prot, Sophos AVs. Has anyone used them? 

1. Will these utilities be able to effectively check what I download for viruses? If so, which of them is best? Are they burdensome to the OS in the same way that Norton and Macaffy slow down a Windows OS?

2. Would it be better to install such an antivirus application in Hardy, or to use one of the free online utilites? (I tried one of these, and it seemed to take an awfully long time to upload software into the online engine for checking. --But if such a thing were to work well, it might be preferable to having a utility permanently on the HD??)

---

### Post by garyedwardjohnston on 2008-05-08
The beauty of Linux is no viruses.  I havent thought about them for a while.

Of course virus checkers use up your system resources.  If you are really worried about passing a virus to a Windoze user, you should install one.  Can't provide advice except

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

As far as which OS to install virus protection on.  I would install it on the OS that you use the least.

---

### Post by Sef on 2008-05-08
> 1. Will these utilities be able to effectively check what I download for viruses? If so, which of them is best? Are they burdensome to the OS in the same way that Norton and Macaffy slow down a Windows OS?

Applications > Add/Remove > Set top box to 'All Available Applications' > Search: type in Clam > check box > apply changes > apply > close

[quote[2. Would it be better to install such an antivirus application in Hardy, or to use one of the free online utilites? (I tried one of these, and it seemed to take an awfully long time to upload software into the online engine for checking. --But if such a thing were to work well, it might be preferable to having a utility permanently on the HD??)[/QUOTE]

Clam does not use a lot of resources.

---

### Post by bodhi.zazen on 2008-05-08
Actually I advise you install antivirus / Norton / etc on windows. You should not run windows without these protections and there is no way to protect windows from your linux partition.

---

### Post by anewguy on 2008-05-09
This brings a question to mind that I have had for a long time about this same subject:

do the Linux anti-virus programs check for Windows-based viruses as well, or only threats to Linux? 

I ask this because I've thought of doing the same thing (but with a MUCH older version of Windows for which it's hard to find a checker now).  I would prefer to download via Ubuntu, have it check for Windows viruses, then I can copy the file over.

I've just never been able to figure out an answer to that question, which seems to me to be at the root of the question for this post as well.

Thanks! :)

---

### Post by hyper_ch on 2008-05-09
> **bodhi.zazen said:**
> Actually I advise you install antivirus / Norton / etc on windows. You should not run windows without these protections and there is no way to protect windows from your linux partition.
But wouldn't that imply that this malware has to run somehow on linux first in order to spread over to the windows partition?

---

### Post by Sirron on 2008-05-09
Be careful if you use Wine, [http://winehq.org/?issue=343#Viruses%20in%20Wine?](http://winehq.org/?issue=343#Viruses%20in%20Wine?)

Apparently windows viruses can work via wine, so surely they could be able to at least infect files on the windows partition, as long as it's mounted?

---

### Post by swarup on 2008-05-09
There seem to be three as yet unanswered/unconfirmed questions that have emerged in this discussion:

1. Does an Ubuntu-based antivirus application such as Clam check for  viruses that are threats to Linux and Windows, or does it check only for threats to Linux? 

(For example, if you do a download in Ubuntu, when the antivirus program checks it, does it check it for viruses that could infect either Linux or Windows?)

2. Will the Ubuntu-based antivirus application run a scan of the entire HD for viruses? i.e. if you are running a dual partition (Linux and Win), will it check both partitions? Or will it only check the Linux partition?

3. If you have a dual partition Vista/Hardy with no antivirus software on either partition: Is it in fact the case that if you only go online with Hardy, then a virus can actually jump partitions and infect Vista-- even if that virus is unable to run in Linux? 

(And if so, then does the Vista partition have to be mounted in Linux for the virus to jump partitions?)

---

### Post by mlentink on 2008-05-09
> **swarup said:**
> 1. Does an Ubuntu-based antivirus application such as Clam check for  viruses that are threats to Linux and Windows, or does it check only for threats to Linux? 
It checks for malware in its database, 99.99999% of which is for Windows)
> **swarup said:**
> 2. Will the Ubuntu-based antivirus application run a scan of the entire HD for viruses? i.e. if you are running a dual partition (Linux and Win), will it check both partitions? Or will it only check the Linux partition? I guess that depends on the type of AV shoftware you are using. I sort of gathered you wanted on-the-fly checking of downloads. That would imply checkin only stuf that comes over the line. If you want a on-demand-checking an intelligent checker would check the filesystem, which woul include any mounted (windows)-partitions. But maybe I wrong. I use that stuf only on windows.

> **swarup said:**
> 3. If you have a dual partition Vista/Hardy with no antivirus software on either partition: Is it in fact the case that if you only go online with Hardy, then a virus can actually jump partitions and infect Vista-- even if that virus is unable to run in Linux? 

(And if so, then does the Vista partition have to be mounted in Linux for the virus to jump partitions?)

The partition would have to be mounted.

---

### Post by bodhi.zazen on 2008-05-09
> **hyper_ch said:**
> But wouldn't that imply that this malware has to run somehow on linux first in order to spread over to the windows partition?

No. The OP stated :

> I have a dual boot with Hardy and Vista. **I often download software while in the Hardy partition, which will be used in Vista.**

Emphasis added my me. This type of activity is the fastest way to infect Windows. IMO the Linux tools are not as sophisticated as the windows tools. IMO you should scan all files with windows tools (from windows) before you transfer a file to windows.

If you transfer a file , either by mounting the partition, network protocols, removable devices (CD/DVD or USB) you need to be very careful.

---

### Post by swarup on 2008-05-09
> **mlentink said:**
> It [Clam] checks for malware in its database, 99.99999% of which is for Windows)

[one para here deleted as per correction in next post]

I see bodhi.zazen has just written in, expressing that Linux AV software is not as sophisticated as Win AV software. Is there general consensus then, that given the common scenario of a dual partition Hardy/Vista where the Vista partition is occasionally mounted and software is occasionally downloaded via Hardy for use in Vista, that in this scenario the only safe approach is to install AV software directly in Vista?

If the answer is yes, then I guess I am disappointed. I thought I was keeping my Vista partition safe by keeping it off-line. And if I really do need to install AV software in Vista, then that means that to keep the AV software current, Vista will need to go online and it will have to do so frequently at that, to download virus definitions. And then all the garbage will be downloaded into Windows which slows it down and ultimately ruins the partition. ...Which destroys my entire plan of keeping the Vista partition clean, Virus-free and AV software-free.

It just kind of puts a gloomy forecast on dual partitions. At least the kind I have kept for the past year, and what I envisioned for the future.

> **mlentink said:**
>  I guess that depends on the type of AV shoftware you are using. I sort of gathered you wanted on-the-fly checking of downloads. That would imply checking only stuff that comes over the line. If you want a on-demand-checking an intelligent checker would check the filesystem, which would include any mounted (windows)-partitions. But maybe I wrong. I use that stuf only on windows.

Going forward, I would indeed only need to check stuff on the fly as it is being downloaded. But the problem I face now is, that I've already downloaded something via Hardy and installed it in Vista. And afterward I uploaded the download onto an on-line AV engine (via Hardy), and found that the software has a virus in it. So I deleted the software from Vista, but now need to scan the Vista partition to make sure it is virus-free. Once that is done, then going forward in the future yes I would only need to check things on the fly as they download. 

> **mlentink said:**
> The partition would have to be mounted [for a virus to spread from Linux to Vista].

ok. So the virus **can** spread to Vista even if it doesn't run in Linux. And here I refer to the virus spreading on its own, spontaneously. Not where one purposely installs a piece of software which one has downloaded via Hardy. That is a critical piece of information that until now I was unaware of.

But so long as the Vista partition is not mounted, it will not be able to spread to it. And if it is mounted, then it can spread spontaneously. Have I understood correctly.

---

### Post by hyper_ch on 2008-05-09
actually, virus is just one part of malware... not vice-versa

---

### Post by swarup on 2008-05-09
> **hyper_ch said:**
> actually, virus is just one part of malware... not vice-versa

Thank you very much for that info-- it makes my understanding of the matter much clearer.

If you could reply on the point of dual boot in general which I raised in the post just above yours, I'd be grateful. Do you think any proper management of a Win/Linux dual boot should include AV software for the Win partition even if that partition is otherwise not ever going online? (Of course, once AV software is installed on Win, then the presence of AV software itself makes it necessary for the Win partition to go online to get virus definition updates.) Very much like to hear your thoughts regarding this, as expressed in my post just above. Thanks.

---

### Post by kamitsukai on 2008-05-09
well if you want a sligtly better avtivrus you can install avg on ubuntu

---

