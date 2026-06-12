---
title: "Viruses on Ubuntu"
date: 2010-03-05
forum: Recurring Discussions
---

### Post by El-Linux on 2010-03-05
Just started using Ubuntu recently and I've been told that Linux (Ubuntu) can't get viruses as viruses are pretty much designed to effect Windows and specific files on that, which naturally Linux doesn't have or use.

Whilst this sounds logical to some extent, it still seems too good to be true.

Are Linux viruses common? Is it worth installing a program? I have a Norton's CD, but does the Norton database of viruses include Linux ones? Can anyone recommend any decent Linux-based ones if Norton's doesn't do the trick.

Thanks all!

---

### Post by theozzlives on 2010-03-05
You can't run Norton on Linux. October 2007, and no viruses as of yet, matter of fact no Malware whatsoever. Kinda miss it in a sick way.

---

### Post by spiky001 on 2010-03-05
Hi I think you will find that viruses on linux are not comman at this moment but there is still malware,if you share with windows it is possible that you could pass on something, there are a few antivirus programs Clamav is 1 i,m sure other ppl will point others out or you can google for them in all I think yo will find not many ppl here use AV for there linux boxes

---

### Post by kaldor on 2010-03-05
The reason Ubuntu (and of course, Linux/UNIX in general) do not get viruses are related to a few things...

1) You're not the administrator(root). Even if you do get a virus attacking you, it will only affect your /home/username directory.

2) Not enough market share in the desktop area for people to want to focus on it.

3) Linux is open source; security fixes can come out very quickly.



Do *not* install an antivirus program. It really, really is not worth it. You'll see what I mean when you have run this for a few months without protection :)

You're still used to the Windows way of doing things; try to look at Ubuntu as something totally new instead of comparing. 

Good luck, welcome to the club!

Edit: I'd also like to make a comment related to the Mac OS. Mac users are famous for claiming that you can never get a virus on a Mac. That is nothing but a lie; Apple based their OS on BSD (the most secure OS) but, of course, in the name of business made some changes and therefore opened up a few security problems. Unlike Mac OS, Ubuntu/Linux is community driven. Because of this, security fixes can be applied quickly. The "No Linux Viruses" statement is very largely true.

---

### Post by J V on 2010-03-05
**Viruses**
Linux has no viruses, not that it's not a popular target, google, yahoo, and several other multi-million dollar targets run on linux.

If there ever was a serious Linux virus out there, to get it to actually work, you would need to:


[LIST]
[*]Log onto your email
[*]Open your email
[*] Download the attachment
[*]Find the attachment
[*]Right-click and go to properties
[*]Go to the permissions tab
[*]Check the box marked execution
[*]Run the application (It can now infect the files in the same directory as it is in)
[*]Input your password (It can now infect files over the entire system)
[/LIST]

 On windows, all you have to do is to log onto your email, windows does the rest automatically, which leaves you open to viruses.

If you are still worried you will actually do this whole list without wondering if its a virus, the Ubuntu wiki has a nice list of [currently known Linux viruses]("https://help.ubuntu.com/community/Linuxvirus"), and their trivial (sometimes whimsical) natures.

You might still however, want to scan for windows viruses, so you don't infect your friends/colleagues with files from your computer (Which is equally unlikely as you would have to deliberately copy it over to them)

For this purpose you should install "[ClamTK]("apt://clamtk")" (Click to install) which is an interface for "ClamAV", which can scan incoming and outgoing email, or in your case, specific files.

---

### Post by QIII on 2010-03-05
Eh.

No EFFECTIVE Linux viruses, at this point.  Kaspersky has cataloged a number of them, but they have really not been able to make any exploits, primarily because it is a little difficult (OK, a lot difficult) for them to gain root access, replicate and then move on.

Malware (like key loggers) does exist, but again, no root access = "Sorry, pal".  But that doesn't mean that "social engineering" can't get you to naively install malicious code.

We shouldn't get over-confident and arrogant.

There could be some PFY in Des Moines who is at this very minute uploading something that will catch us all off guard.

As above, the current threat is passing Windows viruses on in emails, so I check for viruses in emails I intend to forward to Windows users.

---

### Post by Nicolas.Perrault on 2010-03-05
Viruses on Linux? Hahahah! There are about as many of those as George Bush's IQ...

---

### Post by theozzlives on 2010-03-05
I keep ClamAV on my Flash Drive for scanning Windows systems. If your bound determined go:
```
sudo apt-get install clamav
```

to scan a system go:
```
sudo mkdir /tmp/virus
clamscan -ri --move=/tmp/virus /home
```

The /home is most likely where a virus (if any) would reside. That command I gave you won't display anything unless it finds something. At the end it will display a summery.You won't need it though. When I went to Linux I was all paranoid about defraging, running scandisk, anti malware. It turns out that kinda maintenance is un-needed.

---

### Post by QIII on 2010-03-05
> **nicolas.perrault said:**
> viruses on linux? Hahahah! There are about as many of those as george bush's iq...

9?

---

### Post by pricetech on 2010-03-05
I have ClamAV installed just to be safe, but I've never had a problem running any version of Linux.  Interestingly I never had a problem on my computer running winders either, though I've had a couple of times that I could have had a problem had I not been protected.

Go ahead and install ClamAV.  It won't hurt a thing and you'll probably be helping protect others who don't run Linux.

---

### Post by xpod on 2010-03-05
Read Bodhi-zazens excellent [Security Sticky](http://ubuntuforums.org/showthread.php?t=510812) in the Security Section and mabey have a look in the recent [Ever find Malware?](http://ubuntuforums.org/showthread.php?t=1421071) thread to see how many computer nasties some of our members have encountered along the way.

Pay particular note in both threads to the parts about services/servers such as VNC  & SSH and of course the Social Engineering stuff.

---

### Post by theozzlives on 2010-03-05
> **pricetech said:**
> I have ClamAV installed just to be safe, but I've never had a problem running any version of Linux.  Interestingly I never had a problem on my computer running winders either, though I've had a couple of times that I could have had a problem had I not been protected.

Go ahead and install ClamAV.  It won't hurt a thing and you'll probably be helping protect others who don't run Linux.

I've had some nasty ones, the two that come to mind are Michaelangelo with DOS 5.0, and one that infected my system32.dll (without witch nothing works).

That goes to show Microsoft has been a target since the DOS days.

---

### Post by theozzlives on 2010-03-05
Anyhow, I just want to leave on the note that you don't AV. It's useful if you have a Windows partition or WINE. The directions for installation and use are above. I wish you well and welcome you to the Ubuntu community.

---

### Post by cariboo on 2010-03-05
This has come up so many times before, that it is a recurring discussion. Moved.

---

