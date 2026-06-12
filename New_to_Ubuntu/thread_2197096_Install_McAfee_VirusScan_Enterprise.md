---
title: "Install McAfee VirusScan Enterprise"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by basti_schweiger on 2014-01-02
Hello all,

I tried to install McAffe VirusScan on my Ubuntu 12.04 LTS. I download it form here: [http://www.mcafee.com/de/products/virusscan-enterprise-for-linux.aspx](http://www.mcafee.com/de/products/virusscan-enterprise-for-linux.aspx)
After the download I got the file "mcafeevseforlinux-1.9.0.28822-eval-full.noarch.tar.gz". In that file there are some more archives:
- help_vsel_190.zip
- LYNXSHLD1900.zip
- LYNXSHLD1900PARSER.zip
- McAfeeVSEForLinux-1.9.0.28822-eval.tar.gz
- McAfeeVSEForLinux-1.9.0.28822-eval-EPO.zip
- McAfeeVSEForLinux-1.9.0.28822-others.tar.gz

I am an absolute beginner using Ubuntu, and I have no idea how to install that now or what to do with alle these archives. In the installation guide the 1st Task is "Download the MFErt.i686.deb and MFEcma.i686.deb file". How can I download these files?

Thanks for help.

---

### Post by krishna.988 on 2014-01-02
After downloading MFErt.i686.deb,  double click on it to continue installing..then double click on it MFEcma.i686.deb ..

Double clicking on .deb files will open ubuntu software center to install..

---

### Post by basti_schweiger on 2014-01-02
But where can I download these files? I searched for it, but can not find them.

---

### Post by krishna.988 on 2014-01-02
Is it free?? If you have bought it it should be in the DVD..Btw where did you find the instructions?

Also, Ubuntu does'nt need any Antivirus

---

### Post by basti_schweiger on 2014-01-02
As I said, I downloaded the trial version from McAfee homepage: [http://www.mcafee.com/de/products/virusscan-enterprise-for-linux.aspx](http://www.mcafee.com/de/products/virusscan-enterprise-for-linux.aspx)
The installation guide is a PDF and was included in the downloaded file mcafeevseforlinux-1.9.0.28822-eval-full.noarch.tar.gz.
In that instrucion there is an own chapter "Installing on Ubuntu"

---

### Post by andyfied on 2014-01-02
Are you sure the rpms aren't in the tar? I'm reading the manual now and it just says download and install with dpkg.

krishna.988: Some people have Windows users accessing shares on their Ubuntu installs. It's an idea to have an AV to keep them from transmitting stuff to each other.

---

### Post by basti_schweiger on 2014-01-02
Finally found the rpms. I searched in every archive and found them. I was confused by the word "download" in the installation guide. Thank you for your help!

---

### Post by andyfied on 2014-01-02
Yeah, I noticed they used "download" inappropriately which is weird and unhelpful! Did you unpack the tar with -zxvf?

There are some free AV programs that work well on Ubuntu. Is there a particular reason you might be checking out McAfee Enterprise? I'm assuming it's business related.

---

### Post by verymadpip on 2014-01-02
Hi there.
Why would we want rpms for Ubuntu?

---

### Post by andyfied on 2014-01-02
Sorry, I meant the .deb files, I think I'm not so with it today :/

---

### Post by verymadpip on 2014-01-02
> **andyfied said:**
> I think I'm not so with it today :/

Oh yeah; I'm with you on that one :D

---

### Post by newb85 on 2014-01-02
Reasons for using AV in Linux have already been discussed both in this thread and in many others in Absolute Beginners.

---

### Post by monkeybrain20122 on 2014-01-02
> **newb85 said:**
> Reasons for using AV in Linux have already been discussed both in this thread and in many others in Absolute Beginners.

And there was no reason based on those discussions.

(The only sort of legit reason is if you share files with Windows users, but it is not compelling as AV should be installed on Windows' end. If a Windows user relies only on the occasional Linux user whom he/she shares file with to take care of security then his/her system will be screwed sooner or later from somewhere else/by someone else anyway)

---

### Post by whitesmith on 2014-01-02
Lately there has been a lot of sound and fury in the security community about AV software. The consensus is that the lot is "security theater" -- long on claims, short on performance. Today's viruses are so slick that they can pass through AV software as easily as a neutrino can penetrate Swiss cheese. Check out Bruce Schneirer's commentary on the subject. If anyone knows more than Schneirer, they are hiding in the woodwork because the Russian mafia is after them You don't even need an AV program for Windows anymore. On Ubuntu, the whole bunch belongs in the trick-the-unwary category. The firewall built into Ubuntu is more than adequate to keep bad stuff out. Spend your money on something nice for yourself. Cheers.

---

### Post by newb85 on 2014-01-02
I'm certainly not a specialist on AV software, and I'm big enough to admit when I'm out of my league.  But when I read something that doesn't jibe with what I've heard repeatedly in the past, I can't help but look critically (though I try to be open-minded enough to accept that I might be wrong).

When I read a post that says both
> Today's viruses are so slick that they can pass through AV software as easily as a neutrino can penetrate Swiss cheese. 
and
> You don't even need an AV program for Windows anymore. 
it confuses me a little.  Has Windows managed to produce a defense mechanism robust enough to defeat the modern viruses that can't be stopped by modern AV software?  And did they include that defense mechanism in Windows for free?  And did they forget to mention it in their marketing campaign?

I assume this "Bruce Schneirer" is actually Bruce Schneier.  As there was no linked commentary, I did a Google search and read his first commentary on the subject I could find.  [https://www.schneier.com/blog/archives/2009/11/is_antivirus_de.html](https://www.schneier.com/blog/archives/2009/11/is_antivirus_de.html)  (I'll grant that 2009 isn't exactly up-to-date.)  His conclusion was rather interesting:
> Bottom line: antivirus software is neither necessary nor sufficient for security, but it's still a good idea. It's not a panacea that magically makes you safe, nor is it is obsolete in the face of current threats. As countermeasures go, it's cheap, it's easy, and it's effective. I haven't dumped my antivirus program, and I have no intention of doing so anytime soon.

---

### Post by basti_schweiger on 2014-01-03
> **andyfied said:**
> Yeah, I noticed they used "download" inappropriately which is weird and unhelpful! Did you unpack the tar with -zxvf?

There are some free AV programs that work well on Ubuntu. Is there a particular reason you might be checking out McAfee Enterprise? I'm assuming it's business related.

Yes, it is business related. We need a portable tool (on an USB Stick or CD/DVD) to scan Windows computers. So, my idea was to install ubuntu with mcafee on an usb stick, mount the windows drives and scan them. I really do not no if that works, but I will try it. :P

Our company is using McAfee, that is the reason why I wanted to install McAfee on ubuntu.

---

### Post by andyfied on 2014-01-03
> **basti_schweiger said:**
> ... my idea was to install ubuntu with mcafee on an usb stick, mount the windows drives and scan them. I really do not no if that works, but I will try it. :P...
Sounds like a fine plan to me, and if you run into problems come back to the forums :)

---

