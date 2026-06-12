---
title: "Mono in Ubuntu (and Microsoft patents )- A reason to not use GNOME ?"
date: 2008-02-21
forum: Recurring Discussions
---

### Post by vikram on 2008-02-21
Intersting article that makes a case against using mono in GNOME in particular and (against using GNOME in general ?)


[http://boycottnovell.com/2008/02/15/mono-contamination-in-ubuntu/](http://boycottnovell.com/2008/02/15/mono-contamination-in-ubuntu/)


> One thing I noticed this week is that the mono group has been able to encumber a growing number of Ubuntu (not Kubuntu) applications with proprietary Microsoft technology. However, the documentation and program descriptions do not warn of this (of course they want to keep it under the radar).
 “A risk here is that, especially in regards to media (audio, video, pictures, text, etc.) it will provide a ramp for OOXML, WMA, WMV, HDPhoto, and others along with the prerequiste DRM.”A risk here is that, especially in regards to media (audio, video, pictures, text, etc.) it will provide a ramp for OOXML, WMA, WMV, HDPhoto, and others along with the prerequiste DRM. I would expect that if Micrsooft makes further contracts with Novell or other turncoats, that this will soon start to cover DRM.
 In short, mono spreads, becomes integrated into some desktops, then Microsoft formats are rolled out as part of mono.
 […]
 Here is not an example of the dependencies, but of more peripheral incursion:
          [http://www.gnome.org/projects/cheese/](http://www.gnome.org/projects/cheese/)
 Note the recommendation of f-spot. digikam, flphoto, kphotoalbum and others would do the job without infecting the machine with mono.


---

### Post by PmDematagoda on 2008-02-21
This thread has been moved to the Community Cafe as it is not a support request.

---

### Post by laxmanb on 2008-02-21
Not really. MS has opened up (in it's own way) OOXML & HDPhoto. WMA and WMV are really not parts of mono (the Silverlight codec is an optional download btw). I really don't care about the DRM part. I wonder why people just don't use Java, but mono's ok too.

---

### Post by igknighted on 2008-02-21
Please read the other discussions on the topic before posting this FUD again... as has been pointed out numerous times, .NET is a standard, and as such we are free to implement it in our own way.  The standard itself is not patented.  The only reason people have any issue with mono is that microsoft developed it.  They happily have gcj (an open source java implementation, from before java was open sourced) and it is essentially the same thing.  C# is a great language, and having mono allows more developers to develop for linux.  This is not a bad thing.

PS, that site is the linux equivalent of the 911truth site, I would avoid it unless you want a good laugh.

---

### Post by siddartha on 2008-02-21
No need to. You have only tomboy (which has most of the functionality of other sticker apps and applets only with a lot more overhead and memory consumption). And fspot which is broken in more parts they can fix right now. All the other libs in relation with mono on a regular Ubuntu install are just the 'hooks' in case some other app would need the libs. Just examine the packs in Synaptic and remove them. I did that and my system works rather well mono-free. If it wasn't for some OpenOffice functionality and FreeCol my system would be Java free also. And a good reason to do that is not because of patents, but rather because of the fact that most badly written, bloated software is written using those two. Nowadays they have to be a rocket scientist to write C code.

---

### Post by justin whitaker on 2008-02-21
> **PmDematagoda said:**
> This thread has been moved to the Community Cafe as it is not a support request.

Actually, shouldn't it be moved to recurring discussions?

---

### Post by LaRoza on 2008-02-21
> **justin whitaker said:**
> Actually, shouldn't it be moved to recurring discussions?

Moved to Recurring Discussions. It has been discussed before.

---

### Post by original_jamingrit on 2008-02-21
Just out of curiousity, what is supposed to happen when "microsoft formats" are rolled out as a part of the _non-proprietary_ mono?  Will I just have to say: "Oh darn, I have gnome.  Time to give money to Microsoft, they've caught me"?

---

### Post by igknighted on 2008-02-21
> **original_jamingrit said:**
> Just out of curiousity, what is supposed to happen when "microsoft formats" are rolled out as a part of the _non-proprietary_ mono?  Will I just have to say: "Oh darn, I have gnome.  Time to give money to Microsoft, they've caught me"?

What MS formats are part of Mono?  Contrary to what the OP would have you believe, Mono has nothing to do with OOXML, WMA/WMV, etc.  What it does is (possibly) give you connectors (through C#) to these proprietary formats.  So as long as the applications that become part of Gnome don't use those parts, there is no issue.  What you are asking is like asking "why do we use C since you can make proprietary, vendor-lock-in software with it?".

C# is a language that is out there as a standard.  The standard is made for the purpose of being implementable by others.  Mono is simply implementing this standard in a free and open way, they are in no way "adopting" MS's proprietary formats.

---

### Post by vikram on 2008-02-21
here's what I understood after reading wikipedia

[http://en.wikipedia.org/wiki/.NET_Framework#Standardization_and_licensing](http://en.wikipedia.org/wiki/.NET_Framework#Standardization_and_licensing)

.Net implementation is under reasonable and non-discriminatory (RAND) terms and is NOT free. i.e. a company may have to pay 'reasonable' charges for using this. MS and Novell have reached an agreement that only covers Novell and its employees. What prevents MS from suing other developers that use another (incomplete) implementation like Mono?

I am not a lawyer and dont understand software patents well and would like to understand this better.

Can some of the experts here comment on this ?

---

### Post by the_darkside_986 on 2008-02-21
No, the only thing to worry about is the nasty Windows.Forms applications, and anything to do with ASP.NET.  Any open-source application written with Windows.Forms will hopefully never appear in the Ubuntu repositories. 

In fact, MS even knows that the only ammo they would have is WinForms so that is probably why they "released" the source code of WinForms under a restricted developer's reference license in hopes that someone would wrongly unintentionally borrow it for an open source WinForms implementation, thus giving MS a viable chance for patent trolling. But they wouldn't have any real case with just the CLR and C# standards by themselves.

---

### Post by bruce89 on 2008-02-22
> **the_darkside_986 said:**
> No, the only thing to worry about is the nasty Windows.Forms applications, and anything to do with ASP.NET.  Any open-source application written with Windows.Forms will hopefully never appear in the Ubuntu repositories.

```
bruce@Scooby-Dum:~$ apt-cache rdepends libmono-winforms2.0-cil
libmono-winforms2.0-cil
Reverse Depends:
  monodevelop
  libmono-system-messaging2.0-cil
  ironpython
  ikvm
  mono-dbg
  libmono-system2.0-cil
  libmono-system-web2.0-cil
  libmono-microsoft-build2.0-cil
bruce@Scooby-Dum:~$ apt-cache rdepends libmono-winforms1.0-cil
libmono-winforms1.0-cil
Reverse Depends:
  libmono-system-messaging1.0-cil
  nant
  mono-dbg
  libndoc-cil
  libmono-system1.0-cil
```

Oh dear.

---

### Post by igknighted on 2008-02-22
> **bruce89 said:**
> ```
bruce@Scooby-Dum:~$ apt-cache rdepends libmono-winforms2.0-cil
libmono-winforms2.0-cil
Reverse Depends:
  monodevelop
  libmono-system-messaging2.0-cil
  ironpython
  ikvm
  mono-dbg
  libmono-system2.0-cil
  libmono-system-web2.0-cil
  libmono-microsoft-build2.0-cil
bruce@Scooby-Dum:~$ apt-cache rdepends libmono-winforms1.0-cil
libmono-winforms1.0-cil
Reverse Depends:
  libmono-system-messaging1.0-cil
  nant
  mono-dbg
  libndoc-cil
  libmono-system1.0-cil
```

Oh dear.

Those are gone on the next update if the decision is made the Winforms are no good.  As long as the functionality those provide isn't built into applications that are used by default, there's nothing to worry about.

---

### Post by MountainX on 2008-04-02
> **igknighted said:**
> ... there's nothing to worry about.

I'm worried.

---

### Post by smartboyathome on 2008-04-02
> **MountainX said:**
> I'm worried.

Why? Microsoft can't harm you through patents. Do you use ubuntu-restricted-extras? That has the same problem. If you are afraid of mono, you should be afraid of that.

---

### Post by MountainX on 2008-04-02
> **smartboyathome said:**
> Why? Microsoft can't harm you through patents. Do you use ubuntu-restricted-extras? That has the same problem. If you are afraid of mono, you should be afraid of that.

I believe Microsoft can harm (and has already harmed) both the free open source movement as well as the entire computer industry. (I think the later is well known, given the large court cases regarding monopolistic practices.) However, I think we (**not** all of us, certainly) may be acting like lemmings in reagard to .NET, mono, gnome and Microsoft/Novell. That's just my concern. 

The issue goes deeper than an individual installing a restricted extra. When problems get into the gnome code it affects Ubuntu overall.

---

### Post by smartboyathome on 2008-04-02
The only "GNOME" code that uses Mono is Tomboy. Other than that, GNOME is mono-free. So it is like installing restricted extras.

---

### Post by MountainX on 2008-04-02
"I'd like to see Gnome applications written in .NET in version 4.0 ... Gnome 4.0 should be based on .NET," -- Gnome leader Miguel de Icaza

Mono has **already** slayed one of the holy cows of the Gnome project - the insistence that all code be released under the GPL. Gnome now uses MIT X11 license, so the slow infusion has already started.

---

### Post by geoken on 2008-04-02
igknighted, can you please respond to the post at the bottom of the first page? I continually see you posting in Mono related threads, and you always accuse people who are anti-Mono of either blindly hating MS or sheepishly believing people who blindly hate MS yet you never address the posts where people factually disprove the claims you make.

---

### Post by smartboyathome on 2008-04-02
Post from another thread just created:
> **randomstuff said:**
> Since there seems to be a lot of confusion on the issue of mono and .NET I want to make things a bit clearer:

1) Microsoft created a standard called .NET. This standard describes how a .NET implementation should work and is available to anyone. Anyone may use these standards documents to create a piece of software based on this standard. This does not make the software proprietary or controlled by MS.

2) Microsoft created their own implementation of this standard called the .NET framework. This piece of software is proprietary and not open in any way.

3) Novel also created their own implementation of this standard which they call mono. This piece of software is not proprietary but is completely open. There are no patent issues or any other problems because it is developed from scratch and is not based on Microsofts own .NET implementation. 

Because mono is based on the .NET standard it works almost the same as Microsofts own implementation and is very, but not completely, compatible. Since the standard itself (the documents, not the software) can be used by anyone and is open itself, this does not make mono proprietary in any way.

You can compare mono with wine. Wine is free and open source software not tied to Microsoft in any way but it allows you to run windows programs. Mono is similar, only it covers .NET programs instead of windows programs.

I have tried to explain this in terms that non-developers will also understand, so please forgive me if I am using slightly inaccurate terms.




To the moderators: I know that this is a recurring discussion, so feel free to move it to that board. I just want to make sure that there is a topic readily available and properly named so that anyone in doubt can quickly find out the truth about mono. I apologize in advance if this creates additional work for you, but I felt it was necessary because there is so much misinformation going around.


-

---

### Post by MountainX on 2008-04-02
The following is from Icaza regarding Moonlight, but I think the same concerns apply to Mono and Gnome. The discussion shows that Ubuntu *may* not be protected if it distributes code from Gnome/Novell. (I certainly don't have the answers - I'm just supplying this information because it raises questions in my mind.) In particular, I want to know why the founder of gnome suggests that any of us "would have to talk to Microsoft"!

Here is the discussion:

During the discussion, de Icaza explained that while anyone who downloaded Moonlight from Novell was protected by the company's licensing of Silverlight codecs from Microsoft through the company's own cross-licensing agreement. Mike Schroepfer, vice president of engineering from Mozilla, then raised the question that if he downloads and then distributes the code for Moonlight, would he get the patent protection?

**"There is a patent covenant for anyone that downloads [Moonlight] from Novell," answered de Icaza, who then acknowledged that "[COLOR="Red"]as to extending the patents to third parties -- you have to talk to Microsoft[/COLOR]."**

**This answer led Schroepfer to point out the inconsistency between having products that are called open source but are "patent-encumbered."** "There are a lot of complicated IP patent-licensing restrictions," he said. "Even if you have open-source [products], you can't get the end result you're interested in."

See the rest here: [http://www.thestandard.com/news/2008/03/06/mix-novells-de-icaza-criticizes-microsoft-patent-deal](http://www.thestandard.com/news/2008/03/06/mix-novells-de-icaza-criticizes-microsoft-patent-deal)

---

### Post by MountainX on 2008-04-02
> **smartboyathome said:**
> Post from another thread just created:

It is probably worth reading that **whole thread**. Here's one good post in particular:
[http://ubuntuforums.org/showpost.php?p=4345585&postcount=16](http://ubuntuforums.org/showpost.php?p=4345585&postcount=16)

...Mono likely violates hundreds of Microsoft patents. Here is just one example. [http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-bool.html&r=1&f=G&l=50&co1=AND&d=PTXT&s1=%22ASP.NET%22&OS=%22ASP.NET%22&RS=%22ASP.NET%22](http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-bool.html&r=1&f=G&l=50&co1=AND&d=PTXT&s1=%22ASP.NET%22&OS=%22ASP.NET%22&RS=%22ASP.NET%22)

---

### Post by randomstuff on 2008-04-02
here is a [clarification]("http://lists.ximian.com/archives/public/mono-list/2004-March/019042.html") from Miguel de Icaza, the man behind mono.

> [B]There is nothing in Java that makes it any safer than Mono at this
point[/B].  We do not have any guarantees, any written statements, any
guarantees that Java on Linux will not be sued under certain
conditions.

[B]Microsoft has granted RAND+Royalty Free licenses to any patents they
might own that are required to implement the ECMA 334/335 standards. [/B]
So at least our core VM, classes and compilers are safe from any
litigation from *Microsoft*.

AFAIK the patents he is talking about are granted to anyone implementing said ECMA standards, this means that the ECMA compliant parts of mono - which are fully functional on their own - are absolutely free of patent issues (from MS at least).

also, a quote from [wikipedia]("http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.E2.80.99s_patents"):

> The base technologies submitted to the ECMA, and therefore also the Unix/Gnome-specific parts, may be non-problematic. **The concerns primarily relate to technologies developed by Microsoft on top of the .NET Framework**, such as ASP.NET, ADO.NET and Windows Forms, i.e. parts composing Mono&#8217;s Windows compatibility stack. These technologies are today not fully implemented in Mono and **not required for developing Mono-applications**.

Now stop spreading FUD, please!

---

