---
title: "Has ubuntu changed its mind about Banshee/Mono?"
date: 2010-11-23
forum: Recurring Discussions
---

### Post by oscalation on 2010-11-23
I would like to know if Ubuntu has began to change its mind about the inclusion of banshee in ubuntu 11.04. By Ubuntu, i mean the developers, Canonical Staff members, and the community. I would love to hear some remarks from the CTO Matt Zimmerman who (by posts and interviews from the past) acknowledges the risks of the mono project. 

I would also like to hear from Jono Bacon. 

The FSF and Richard Stallman have both made official statements about mono and its risk. 

"**Q1**: I'm interested in       hearing your opinion on the relationship between Mono and GNOME.                  **Richard Stallman**: Mono       is a free implementation of Microsoft's language C#.  Microsoft       has declared itself our enemy and we know that Microsoft is       getting patents on some features of C#.  So I think it's       dangerous to use C#, and it may be dangerous to use Mono.       There's nothing wrong with Mono.  Mono is a free implementation       of a language that users use.  It's good to provide free       implementations.  We should have free implementations of every       language.  But, depending on it is dangerous, and we better not       do that."




The MCP .. Community Promise only says that Microsoft will not sue you over  claims in patents that it owns or controls. If Microsoft sells one of  those patents, there&#8217;s nothing stopping the buyer from suing everyone  who uses the software. Theres the open discussion of how much water the "Promise" would hold in court, if its revocable...Also, there are standards in mono that are not covered by the ECMA 334 335, this become a big issue when the standards not covered are common functions that are used often. 



With the recent acquisition of Novell, im interested to see if this has any effect on ... well yeah.

---

### Post by Elfy on 2010-11-23
Moved to recurring - another mono thread.

---

### Post by zekopeko on 2010-11-23
> **bigthinker said:**
> I would like to know if Ubuntu has began to change its mind about the inclusion of banshee in ubuntu 11.04. By Ubuntu, i mean the developers, Canonical Staff members, and the community. I would love to hear some remarks from the CTO Matt Zimmerman who (by posts and interviews from the past) acknowledges the risks of the mono project. 

I would also like to hear from Jono Bacon.


Banshee has been waiting to get into Ubuntu since 9.10. So no, people have no problem with Mono and Banshee.

Mono has been FUD-ed for the majority of it's existence by people who have little to no understanding of what Mono is, how patents work 


> 
The FSF and Richard Stallman have both made official statements about mono and its risk. 

"**Q1**: I'm interested in       hearing your opinion on the relationship between Mono and GNOME.                  **Richard Stallman**: Mono       is a free implementation of Microsoft's language C#.  Microsoft       has declared itself our enemy and we know that Microsoft is       getting patents on some features of C#.  So I think it's       dangerous to use C#, and it may be dangerous to use Mono.       There's nothing wrong with Mono.  Mono is a free implementation       of a language that users use.  It's good to provide free       implementations.  We should have free implementations of every       language.  But, depending on it is dangerous, and we better not       do that."

Richard Stallman has supported Mono when it was first announced. He even called it GNU Mono. The problem was that he did against the wishes of the Mono creators so only he could forcefully co-opt the project into GNU. 

Today GNU even has a project called dotGNU which is basically copying .NET.

Here is an [interesting email]("http://mail.gnome.org/archives/foundation-list/2010-March/msg00091.html") about those "potential dangers of Mono". Apparently other FOSS projects copied .NET extensively so those "potential dangers" would equally apply to them.

This brings us to the Community Promise:

> The MCP .. Community Promise only says that Microsoft will not sue you over  claims in patents that it owns or controls. If Microsoft sells one of  those patents, there’s nothing stopping the buyer from suing everyone  who uses the software. Theres the open discussion of how much water the "Promise" would hold in court, if its revocable...Also, there are standards in mono that are not covered by the ECMA 334 335, this become a big issue when the standards not covered are common functions that are used often.

Projects that implement ideas from .NET aren't protected by the Community Promise so Mono is in effect safer then those projects.

> With the recent acquisition of Novell, im interested to see if this has any effect on ... well yeah.

Novell is planned to be acquired by a company that has no connections to Microsoft (AFAICT). Patents are being sold to a holding company that is lead by Microsoft (do note there are other companies with a share in the holding company). 

Of course this has nothing to do with Mono but probably has to do with other essentials technologies such as XML since Novell had patents on that. This deal, if anything, put other projects at more risk.

Now a question for you. Could you give me some links to sites from which you got the information about Mono (excluding those mentioned here)? I would like to know what exactly shaped your current opinion of the situation.

---

### Post by Ric_NYC on 2010-11-23
I believe the Mono integration in Ubuntu has to be discussed.

Nobody knows what is included in the patent deals that Microsoft has gotten in the last years (Novell, Amazon, HTC, LG etc)... and until someone can tell what's involved in those deals **_NO ONE_** can prove that having Mono installed is safe.


BTW I found this "bug" last year... It seems like someone is trying to force Mono stuff in Ubuntu:



Go to **Ubuntu Software Center** and search for "gThumb"... The first result is F-Spot. It needs Mono to work.
[IMG]http://img201.imageshack.us/img201/7739/screenshot1gl.png[/IMG]

My question is... Why is F-Spot shown when I didn't search for it?... besides that "gThumb" appears in second place.


I ask someone to fix that.

---

### Post by zekopeko on 2010-11-23
> **Ric_NYC said:**
> I believe the Mono integration in Ubuntu has to be discussed.

Nobody knows what is included in the patent deals that Microsoft has gotten in the last years (Novell, Amazon, HTC, LG etc)... and until someone can tell what's involved in those deals **_NONE_** can prove that having Mono installed is safe.

Dear Ric_NYC you can't prove a negative.

If you think that your statement is something else then a logical fallacy then I present you with a modified version so you can see how wrong you are (I doubt you will concede that but it might prove valuable to others to start understanding how little you actually know):

> Nobody knows what is included in the patent deals that Microsoft has gotten in the last years (Novell, Amazon, HTC, LG etc)... and until someone can tell what's involved in those deals **_NONE_** can prove that having the **Linux kernel** or GNU userland**** or **GNOME** or **Firefox** or **OpenOffice.org** or **Java** or **Gnote** or **Shotwell** or **Kupfer** installed is safe.

So by your own faulty logic you should immediately remove all traces of any Linux distribution on your computer since you don't know if it's safe. Now I'm sure you are going to start saying how those apps couldn't possibly be unsafe since you believe them to be (disregarding the fact that Java and the kernel were/are attacked by patents). So in the end it is all down to your own personal belief. So why should anyone care about your opinion since it's obviously not based on even remotely sound logic or facts?

> BTW I found this "bug" last year... It seems like someone is trying to force Mono stuff in Ubuntu:

Go to **Ubuntu Software Center** and search for "gThumb"... The first result is F-Spot. It needs Mono to work.
[IMG]http://img201.imageshack.us/img201/7739/screenshot1gl.png[/IMG]

My question is... Why is F-Spot shown when I didn't search for it?... besides that "gThumb" appears in second place.

I ask someone to fix that.

Thank you for providing even more proof that you have no idea what you are talking about. 

That bug you found "last year" was actually from this year. 

It originated from [this thread]("http://ubuntuforums.org/showthread.php?t=1202591&highlight=monolith&page=27") in which you found this "evil conspiracy". You also didn't "ask someone to fix that" since [I was the one that reported that bug]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/569099") since you were to lazy to do it yourself. 

That bug was marked as a duplicate of a wider bug which returns the searched application but further down the list. If you search for Gnome Do (another Mono applications; OMG! it's a conspiracy) you will see that it is further down the list then it should be, mixed with applications that have nothing to do with it. What an amazing conspiracy it is. They push one app (which isn't on the liveCD anymore) and shun the other.

---

### Post by Ric_NYC on 2010-11-23
> **zekopeko said:**
> 
That bug you found "last year" was actually from this year. 

It originated from [this thread]("http://ubuntuforums.org/showthread.php?t=1202591&highlight=monolith&page=27") in which you found this "evil conspiracy". You also didn't "ask someone to fix that" since [I was the one that reported that bug]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/569099") since you were to lazy to do it yourself. 




You are right about the date. I found the "bug" in April. 


It seems like I'm not the only "lazy" person here... since the "bug" is still there.



When I can take a screenshot and post it here I don't think that can be called a "conspiracy". It's there for anyone to see.

---

### Post by Ric_NYC on 2010-11-23
> **zekopeko said:**
> 



So by your own faulty logic you should immediately remove all traces of any Linux distribution on your computer since you don't know if it's safe. Now I'm sure you are going to start saying how those apps couldn't possibly be unsafe since you believe them to be (disregarding the fact that Java and the kernel were/are attacked by patents). So in the end it is all down to your own personal belief. So why should anyone care about your opinion since it's obviously not based on even remotely sound logic or facts?



Thank you for providing even more proof that you have no idea what you are talking about. 

That bug you found "last year" was actually from this year. 




I"ll never put the Linux Kernel, Java, Firefox and Mono at the same level.

Openoffice has been removed from my computer.

---

### Post by zekopeko on 2010-11-23
> **Ric_NYC said:**
> You are right about the date. I found the "bug" in April. 

It seems like I'm not the only "lazy" person here... since the "bug" is still there.

When I can take a screenshot and post it here I don't think that can be called a "conspiracy". It's there for anyone to see.

This is the conspiracy part:

> BTW I found this "bug" last year... It seems like someone is trying to force Mono stuff in Ubuntu:

Your usage of quotation marks is very telling. You're saying that **someone** (who exactly) is pushing Mono stuff in Ubuntu when it's obvious that it's a bug. Occam's razor, Hanlon's razor and all that.

---

### Post by zekopeko on 2010-11-23
> **Ric_NYC said:**
> I"ll never put the Linux Kernel, Java, Firefox and Mono at the same level.

Openoffice has been removed from my computer.

Thank you for proving my point. Your entire FUD is based on your faulty beliefs. Facts and logic are, for you, simply nuisances to be ignored ;) .

---

### Post by cariboo on 2010-11-23
Please keep this thread on topic, and keep personalities out of it.

---

### Post by czr114 on 2010-11-23
Ditching Mono because of what a Microsoft successor hypothetically might do with software patents of dubious strength would be like having ditched Linux entirely when SCO reared its ugly head.

Patent FUD is sorely in need of some sanity.

Yes, these patents are an issue, and Microsoft could make good on its words by granting the public a perpetual, royalty-free, unencumbered license to use them.

Mono is still a free, non-commercial implementation, built cleanly, with a strong interoperability argument behind it. In many countries, end users have a right to interoperability rendered through pure speech (source code).

About the worst that could happen to Mono, even if Microsoft came out swinging, would be that users would have to opt-in to a package which builds the source on the fly.

Unless something changes, I'll be considering this FUD on par with SCO's outlandish claims, the LZW debacle, or issues with MP3.

If you're going to purge your system of Mono, go ahead and stay consistent by also bouncing anything that touches MP3 or libdvdcss.

Mono is a great framework for a great language, which is going to help us by encouraging cross-platform development and a pull of talent from all the devs learning skills for the Microsoft ecosystem.

---

### Post by oscalation on 2010-11-24
> **czr114 said:**
> Ditching Mono because of what a Microsoft successor hypothetically might do with software patents of dubious strength would be like having ditched Linux entirely when SCO reared its ugly head.

Patent FUD is sorely in need of some sanity.

Yes, these patents are an issue, and Microsoft could make good on its words by granting the public a perpetual, royalty-free, unencumbered license to use them.

Mono is still a free, non-commercial implementation, built cleanly, with a strong interoperability argument behind it. In many countries, end users have a right to interoperability rendered through pure speech (source code).

About the worst that could happen to Mono, even if Microsoft came out swinging, would be that users would have to opt-in to a package which builds the source on the fly.

Unless something changes, I'll be considering this FUD on par with SCO's outlandish claims, the LZW debacle, or issues with MP3.

If you're going to purge your system of Mono, go ahead and stay consistent by also bouncing anything that touches MP3 or libdvdcss.

Mono is a great framework for a great language, which is going to help us by encouraging cross-platform development and a pull of talent from all the devs learning skills for the Microsoft ecosystem.

My system is clean of MP3's and most restricted drivers. Thank goodness for .FLAC 

The deal that was struck between Novell and M$ is between M$ and Novell, every other distribution is subject to litigation from M$ regarding their prior claims of .. 235 known Patent infringements from Open Source Software, and the 42 claimed patent infringements from the linux kernel itself. Yes these are claims, claims made publicly multiple times with various trust worthy sources. M$ hasn't shared what patents are infringed apon not because they don't exist, but because this is a common business practice and smart legal tactics. The r ecent suite against TomTom is a good example

[http://www.microsoft.com/presspass/press/2009/feb09/02-25statement.mspx](http://www.microsoft.com/presspass/press/2009/feb09/02-25statement.mspx)
[http://www.microsoft.com/Presspass/press/2009/mar09/03-30MSTomTomPR.mspx](http://www.microsoft.com/Presspass/press/2009/mar09/03-30MSTomTomPR.mspx)

thanks Gutierrez, there are tons of links around the net regarding this.. no need to post. 



[http://www.gnu.org/licenses/rms-why-gplv3.html](http://www.gnu.org/licenses/rms-why-gplv3.html)

""Another threat that GPLv3 resists is that of patent deals like the Novell-Microsoft pact.  Microsoft wants to use its thousands of patents to make users pay Microsoft for the privilege of running GNU/Linux, and made this pact to try to achieve that.  The deal offers rather limited protection from Microsoft patents to Novell's customers.
  Microsoft made a few mistakes in the Novell-Microsoft deal, and GPLv3 is designed to turn them against Microsoft, extending that limited patent protection to the whole community.  In order to take advantage of this protection, programs need to use GPLv3.
  Microsoft's lawyers are not stupid, and next time they may manage to avoid those mistakes.  GPLv3 therefore says they don't get a &#8220;next time&#8221;.  Releasing a program under GPL version 3 protects it from Microsoft's future attempts to make redistributors collect Microsoft royalties from the program's users.""

[http://www.microsoft.com/presspass/misc/07-05statement.mspx](http://www.microsoft.com/presspass/misc/07-05statement.mspx)  

[http://www.fsf.org/news/dont-depend-on-mono](http://www.fsf.org/news/dont-depend-on-mono)

I could continue to post links all day, but why. Microsoft stance on open source software has been obvious for years. They have even said publicly that they will protect their shareholders and litigate for any patent infringement strategically.. which IMO is a smart business move and is the right thing to do for M$ shareholders. Not good for FOSS. Oh, and im not a M$ shareholder so.. 

interoperability between linux and windows to me and many others is a waste of resources. If linux could effectively (which we have made great strides) provide an import method for users changing from closed source proprietary applications/file formats/etc to linux than interoperability would be less important. An open source implementation of a proprietary M$ framework (.net) is supposed to benefit who? M$ or FOSS? 

I dont see Patent trolling, or Patent FUD, i see concerned FOSS users that want to preserve the freedoms we have all come to enjoy. The same freedoms that other competitors want control over.

---

### Post by czr114 on 2010-11-24
Interoperability and ease of porting is critical for a minority-share OS.

Most of the development talent and development focus is on the Windows platform. Helping it to easily migrate to GNU/Linux via something like Mono offers increased choice and software availability for Linux users. The goal is to help things which were being built for Windows anyway be easily built for Linux desktops.

Plus, C# run through Mono is a productive and powerful setup.

While I don't trust Microsoft, and would hope they'd proactively defuse the issue by properly granting a perpetual and unrestricted community license, Mono is not going to be sunk by Microsoft any more than VLC wasn't sunk by a whole host of companies who might take issue with it on similar grounds.

---

### Post by Mr. Picklesworth on 2010-11-24
> **bigthinker said:**
> My system is clean of MP3's and most restricted drivers. Thank goodness for .FLAC 

The deal that was struck between Novell and M$ is between M$ and Novell, every other distribution is subject to litigation from M$ regarding their prior claims of .. 235 known Patent infringements from Open Source Software, and the 42 claimed patent infringements from the linux kernel itself. Yes these are claims, claims made publicly multiple times with various trust worthy sources. M$ hasn't shared what patents are infringed apon not because they don't exist, but because this is a common business practice and smart legal tactics. The r ecent suite against TomTom is a good example


Actually, [what they are doing]("http://news.slashdot.org/story/10/02/23/1231255/Microsoft-Amazon-Ink-Kindle-and-Linux-Patent-Deal") is called [racketeering]("http://en.wikipedia.org/wiki/Racket_(crime)"). It is illegal, and you are feeding them. Congratulations, you are saving Microsoft legal fees and handing them the reward for a case they could never win in the open.

---

### Post by czr114 on 2010-11-24
I do find it hard to believe that, in this day and age, any system would be completely free of MP3 support.

---

### Post by _khAttAm_ on 2010-11-25
> **bigthinker said:**
> I would like to know if Ubuntu has began to change its mind about the inclusion of banshee in ubuntu 11.04. By Ubuntu, i mean the developers, Canonical Staff members, and **the community.** 

I would like to know if Ubuntu has begun to change its mind about the community. Does it consider the community at all?

---

### Post by zekopeko on 2010-11-26
> **_khAttAm_ said:**
> I would like to know if Ubuntu has begun to change its mind about the community. Does it consider the community at all?

About what exactly?

---

### Post by Tibuda on 2010-11-28
> **Ric_NYC said:**
> I"ll never put the Linux Kernel, Java, Firefox and Mono at the same level.

The kernel has much more patent-risky implementations than Mono.

---

### Post by Spice Weasel on 2010-11-28
> **Tibuda said:**
> The kernel has much more patent-risky implementations than Mono.

Every program has patent-risky implementations.

Which is why software patents are BS.

What happens if someone starts suing everyone that uses scrollbars in a program?

---

### Post by Tibuda on 2010-11-28
> **Spice Weasel said:**
> Every program has patent-risky implementations.

Which is why software patents are BS.

What happens if someone starts suing everyone that uses scrollbars in a program?

Exactly.

---

### Post by radioboy on 2010-12-08
> **Tibuda said:**
> The kernel has much more patent-risky implementations than Mono.
The difference here is that Mono is a non-critical part.

---

### Post by zekopeko on 2010-12-08
> **radioboy said:**
> The difference here is that Mono is a non-critical part.

Is Java a non-critical part? How about Python? GTK+? Qt? X? Who are you to say what is critical or not?

---

### Post by directhex on 2010-12-08
> **radioboy said:**
> The difference here is that Mono is a non-critical part.

Surely it should be even more important to replace it, then, if your fear is patent litigation? Stuff on the margins is easy to remove. If the kernel suddenly vanishes due to teh patents, the way Mono supposedly will, then what are we left with?

---

### Post by radioboy on 2011-01-10
> **zekopeko said:**
> Is Java a non-critical part? How about Python? GTK+? Qt? X? Who are you to say what is critical or not?

You can have a clean install of Ubuntu without Mono and still have  a functional desktop and good applications. Instead of Tomboy, Gnote or Zim; gbrainy can perfectly stay out. Nothing else happens.
On the other hand, if one takes out Python, GTK+, X or Qt (in Kubuntu), the system/desktop breaks **heavily**. That's the difference and you know it.

Sad that now they will be including Banshee by default in Natty.

---

### Post by zekopeko on 2011-01-10
> **radioboy said:**
> You can have a clean install of Ubuntu without Mono and still have  a functional desktop and good applications. Instead of Tomboy, Gnote or Zim; gbrainy can perfectly stay out. Nothing else happens.
On the other hand, if one takes out Python, GTK+, X or Qt (in Kubuntu), the system/desktop breaks **heavily**. That's the difference and you know it.

Sad that now they will be including Banshee by default in Natty.

Software you deem "essential" for a Linux desktop implements stuff that exists in parts of Mono. So if Mono can be sued so can the rest of them.

I'm glad that Banshee is being included simply because it's a better music player with a very active and friendly upstream. 

If people listened to people like you the Linux desktop wouldn't be able to compete with either Windows or Mac. I'm glad that saner heads prevailed.

---

