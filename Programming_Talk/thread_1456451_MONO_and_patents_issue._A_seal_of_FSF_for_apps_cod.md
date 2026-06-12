---
title: "MONO and patents issue. A seal of FSF for apps coded in Gtk# declaring free of patent"
date: 2010-04-17
forum: Programming Talk
---

### Post by michaelmartin007 on 2010-04-17
Mono Gtk# is a good language to program in Gnome. Probably the best. There is much opposition against Mono, I think Gnome is divided half against the other half in favor and against.

Many developers are working hard in C sharp with applications like Banshee, F-spot, Tomboy ... These people is working hard but there is a strong opposition to their programs to be included in the default distributions of Gnome.

THERE IS A SOLUTION FOR ALL GNOME DEVELOPERS AND USERS.

THERE IS A PART OF MONO (winforms, asp ...) with potential licensing problems. OTHER PARTS ARE FREE OF PROBLEMS (GTK #)

I propose that any program written with GTK# BE FREE TO BE INCLUDED IN GNOME. For example a day in future could Banshee replace Rhymthbox.

I propose a SEAL from THE FSF to declare that a mono apps (tomboy, banshee...) is free of patents problems. I think this is
good for all gnome users and developers. The FSF could guarantee with a kind of seal that a mono app is free of patents and what part of Mono is free for develop in Gnome.

This is half way. No letting all code from mono and no forbid all code.

---

### Post by Quikee on 2010-04-17
What are you talking about? Tomboy is already part of standard Gnome - because of this Mono is a required dependency.

---

### Post by jkxx on 2010-04-17
Good point but it's not just winforms that is patented. There is a core definition of C# that can be reused without issues (ECMA standard) but which covers very little functionality. Beyond that, things go in a grey area where you can't be sure if it's ok to use something or not. Microsoft's history of threatening to sue just makes it look that much worse.

I'm a fan of C# but I'm not sure any of it can be safely used outside of Windows. Perhaps someone more familiar with the legal side of things can elaborate.

---

### Post by phrostbyte on 2010-04-17
Arguably even WinForms and ASP.NET are free of patent issues as well. At least no one has been able to point to a single patent Microsoft owns on the technology. :)

---

### Post by michaelmartin007 on 2010-04-18
> **jkxx said:**
> Good point but it's not just winforms that is patented. There is a core definition of C# that can be reused without issues (ECMA standard) but which covers very little functionality. Beyond that, things go in a grey area where you can't be sure if it's ok to use something or not. Microsoft's history of threatening to sue just makes it look that much worse.

I'm a fan of C# but I'm not sure any of it can be safely used outside of Windows. Perhaps someone more familiar with the legal side of things can elaborate.

I didn't know that the possible problem should be in the C# functionality. I thought it should be in the Microsoft libraries and the implementation on that libraries for Mono. So, I thought Gtk# should be free at all of any kind of patent and problem with Microsoft.
In any case the fear of patents is doing great harm to Mono apps.
I think Gnome should address the problem on C# development. Novell already reached an agreement with Microsoft but it is a bilateral agreement which leaves out the rest of the distributions. 
I don't like the idea that development in C# is living in dire straits. This is, waiting the day Microsoft decide to get Gnome to a tribunal por patent misuse. 
There are many important applications written in C# and each year more.

---

### Post by danbh on 2010-04-18
fsf has a compelling statement on this issue here: [http://www.fsf.org/news/2009-07-mscp-mono](http://www.fsf.org/news/2009-07-mscp-mono)

I like the part where Microsoft could sell the patents.  The only promise that MS has given so far is that they won't sue you over their patents.  That doesn't stop them from selling/giving the patent to someone else to do the suing.  Real protection would involved MS giving an actual license, which would persist even if the patent was sold.

---

### Post by jkxx on 2010-04-18
> In any case the fear of patents is doing great harm to Mono apps.

That's really the biggest problem right there.

Also if you look at [http://linux.slashdot.org/story/07/10/09/1221223/Ballmer-Suggests-Linux-Distros-Will-Soon-Have-to-Pay-Up]("http://linux.slashdot.org/story/07/10/09/1221223/Ballmer-Suggests-Linux-Distros-Will-Soon-Have-to-Pay-Up") or [http://linux.slashdot.org/story/07/08/07/1842205/Microsoft-Fracturing-the-Open-Source-Community]("http://linux.slashdot.org/story/07/08/07/1842205/Microsoft-Fracturing-the-Open-Source-Community") you can see examples of what they've done in the past. The best was the blanket threat with the 235 patents they refused to reveal. It did enough harm to make a lot of people think twice about including anything Microsoft-related in their projects.

In the end they might not do anything but the threat is still very real.

---

### Post by michaelmartin007 on 2010-04-18
> **danbh said:**
> fsf has a compelling statement on this issue here: [http://www.fsf.org/news/2009-07-mscp-mono](http://www.fsf.org/news/2009-07-mscp-mono)

I like the part where Microsoft could sell the patents.  The only promise that MS has given so far is that they won't sue you over their patents.  That doesn't stop them from selling/giving the patent to someone else to do the suing.  Real protection would involved MS giving an actual license, which would persist even if the patent was sold.

Thanks for the link. After reading what the FSF says about C# I have no doubt that it is not a good idea to have Mono apps in Gnome. It's sad because I'm a fan of C#, but Microsoft has the potential to stop the development of these applications when they want.

I would like to quote this text from the FSF about developing in C#.  
"Until that happens, free software developers still should not write software that depends on Mono. C# implementations can still be attacked by Microsoft's patents: the Community Promise is designed to give the company several outs if it wants them. We don't want to see developers' hard work lost to the community if we lose the ability to use Mono, and until we eliminate software patents altogether, using another language is the best way to prevent that from happening."

[http://www.fsf.org/news/2009-07-mscp-mono](http://www.fsf.org/news/2009-07-mscp-mono)

I think the heart speaks of applications that we like and are part of the applications that are installed by default (tomboy, F-spot, gbrainy). The head tells us that the patent owner may terminate our use of them when he wants and that's an unnecessary risk. I think that gnome should, perhaps, reconsider the default inclusion of these applications.

---

### Post by bruce89 on 2010-04-18
> **michaelmartin007 said:**
> I think the heart speaks of applications that we like and are part of the applications that are installed by default (tomboy, F-spot, gbrainy). The head tells us that the patent owner may terminate our use of them when he wants and that's an unnecessary risk. I think that gnome should, perhaps, reconsider the default inclusion of these applications.

GNOME doesn't "include" these programs, only Tomboy does. Ubuntu != GNOME.

---

### Post by phrostbyte on 2010-04-18
AFIAK, no one has ever conclusively pointed to a patent that Mono might violate. Even so, Microsoft has made itself aware of Mono for quite some time and the longer they wait to sue Mono, the more and more the doctrine of latches will make it more difficult to do so in the future.

---

