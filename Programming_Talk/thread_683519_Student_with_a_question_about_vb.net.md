---
title: "Student with a question about vb.net"
date: 2008-01-31
forum: Programming Talk
---

### Post by doctorbighands on 2008-01-31
I've posted the following in its entirety on the Absolute Beginner forums. At the suggestion of a user there, I am reposting here in the hope that someone can help clear things up for me.

The original post:

----------------------

Hey all,

I'm looking to take some CIS classes. Just to be sure, I sent an email to the department at the college to ask if I could make it with just a Linux OS installed on my machine. Here is the relevant portion of the response I received:

"If he installs or has installed a Microsoft operating system on his Linux machine and then buys Microsoft Office for $60 (deal is only good for students) and installs that, he could then dual-boot and go through the program without a problem.

With just Linux he could take the UNIX classes and maybe some others, but he definitely couldn't take VB.Net classes. He might be able to take C++ and Java classes. He couldn't take my version of [a particular class] because it requires having VBA."

I don't know specifically what he's talking about, but I want so badly for him to be wrong! Do I really have to buy a copy of MS Office?! Being the ignoramus that I am, I installed Mono and MonoDevelop on my system. Will that give me what I need?

What I want, ultimately, is to be able to succeed in these classes entirely outside of a Windows environment; also, I want to be able to tell this prof exactly how I intend to do that. That's where I need your help: Someone please tell me I can make this happen without M$!

Thank you!

EDIT: Just for the record, I know I'm covered in almost all languages if I use any of the multitude of IDEs out there (personally, I like Geany). I'm really concerned about this .NET stuff (VB.NET, VBA, etc) - something with which I'm entirely unfamiliar.

---

### Post by d0nny2600 on 2008-01-31
I am a VB .Net developer and I'm a long time Linux user. However, If you want to learn VB.NET you are stuck with windows...yeah you could try use monodevelop etc. but the reality is you do need to do it on Windows if you want to become an accomplished programmer.

On another note...you never need to buy MS Office unless you are going to be programming in VBA. You use OpenOffice for your everyday needs but for VBA you need Access and Excel etc.

---

### Post by lnostdal on 2008-01-31
So .. you're learning, like, Java, C# and VB - at the same time in one course?

Java is not a problem of course.

C# should neither be a problem, because of Mono.

VB is a no go. And, well, it sucks anyways, even on Windows. If you want to target .NET use C#, or maybe something else -- but not VB.

VBA is, well, it's Microsoft Office -- but why do you care? Use, support and develop for Openoffice instead.

---

### Post by Lord Illidan on 2008-01-31
I found a link here : [http://www.mono-project.com/VisualBasic.NET_support](http://www.mono-project.com/VisualBasic.NET_support)

However, when it comes to .NET, I would recommend a Windows platform. Mono can be a bit patchy at times, and it has some catching up to do. It's still "newish".

So I would say..dualboot for the time being.

---

### Post by NovaAesa on 2008-01-31
Instead of duel booting you could just run Windows in Virtual Box (If you have enough system resources i.e. at least 1GiB RAM)

---

### Post by pedro_orange on 2008-01-31
> **lnostdal said:**
> VB is a no go. And, well, it sucks anyways, even on Windows. If you want to target .NET use C#, or maybe something else -- but not VB.

I think you'll find the majority of non-IT businesses use applications developed in VB.NET because it is just so quick to make an application. They don't care what it's written in, they want bang for buck.

Alot of industry (power, gas, water etc) rely on reporting tools based solely on SQL, Sharepoint, Office and Visual Basic to drive it. 
I actually work in this industry, and by trade I'm a C++ developer that spends nearly everyday writing Visual Basic / VBA / VBScript / Some variatation of VB within industry applications - because its what the customers want. 
I can talk people through code changes on the phone that they can compile their end cause it's so damn easy.

To the OP - I run Ubuntu at home and I cannot compile VB on it using any of the applications mentioned. Plus it's too much of a headache. 
I have a second hard drive with Windows on for when I need to take my work home, and thats not very often! :)
Students generally get a free copy of Windows, Office & Visual Studio under the MSDN AA (Academic Alliance). I got these at uni and I still run them on my spare HDD.
If you have to write Visual Basic, do it in Windows.

---

### Post by pmasiar on 2008-01-31
When in Rome, do as Romans do.
When programming using MSFT proprietary tools, do it on MSFT proprietary platform.

After you get your degree, you can either have a day job using MSFT platfor and double boot, like many of us, or with some luck find a more interesting job in a company which has a clue, and use Linux.

---

### Post by LaRoza on 2008-01-31
> **pmasiar said:**
> When in Rome, do as Romans do.
When programming using MSFT proprietary tools, do it on MSFT proprietary platform.

After you get your degree, you can either have a day job using MSFT platfor and double boot, like many of us, or with some luck find a more interesting job in a company which has a clue, and use Linux.

Exactly. I don't like seeing IT or CS majors trying to use a single platform. Granted, most of the time I am yelling at them for just knowing Windows, but occasionally I see someone (usually on this forum) trying to do everything in Linux.

(Even I dual boot for my web development. I do nothing else in Windows and haven't booted into it in a while)

---

### Post by cwaldbieser on 2008-02-02
Doesn't the college provide computer labs for that kind of thing?  When I went to college, I didn't have my own PC, so I ended up spending a lot of time in the lab.

---

### Post by Lord Illidan on 2008-02-02
> **LaRoza said:**
> Exactly. I don't like seeing IT or CS majors trying to use a single platform. Granted, most of the time I am yelling at them for just knowing Windows, but occasionally I see someone (usually on this forum) trying to do everything in Linux.

(Even I dual boot for my web development. I do nothing else in Windows and haven't booted into it in a while)

Um. I do everything in Linux :D
But then, we only do Java, Prolog and Haskell so far. Still, I am not going to install XP/Vista just to install a funky IDE if I can do the same in Linux. The exception would be if we had to do plenty of C#..in that case I might consider it, but so far we're only covering Java, and the teacher recommends Eclipse or netbeans.

---

### Post by Lord Illidan on 2008-02-02
> **cwaldbieser said:**
> Doesn't the college provide computer labs for that kind of thing?  When I went to college, I didn't have my own PC, so I ended up spending a lot of time in the lab.

That's true, but I like to develop from the comfort of my own home.

---

