---
title: "Programming with C# in Ubuntu?"
date: 2005-08-05
forum: Programming Talk
---

### Post by L150 on 2005-08-05
Hello,
I program using C# , and was wondering wether it is possible to install the .net framework on to ubuntu HH? If not can you reccommend a programming language that Linux developers use for around the same purposes.
regards L150

---

### Post by NoTiG on 2005-08-05
Google Mono

---

### Post by tom-ubuntu on 2005-08-06
I am a c# developer aswell. Just installed monodevelop yesterday, to check the progress on this IDE. What I reckognized immediately, is, how unstable it still is. Just moved around some windows within the IDE and hat 3 crashes within 5 minutes. Do not move around anything. More I can't tell you know  ;)

I will try to port an applicatin from .Net to mono and see how good it will work.

---

### Post by L150 on 2005-08-06
Hello,
Thank you for your help greatley appreciated.
I have heard a lot of people also say that mono is unstable after i found out what it was called from you, they seemed to insist I wait on a more stable release of the application what would you reccomend?  Regards L150

---

### Post by Gnobody on 2005-08-06
In the meantime Python is a GREAT easy to learn powerful alternative.  [www.python.org](http://www.python.org)

---

### Post by varunus on 2005-08-06
What you guys should do is enable the hoary backports repositories as described here:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Then, install mono. This will get you the much newer 1.1.7 version instead of the 1.0.X version in Hoary.  The new mono is MUCH stabler; I was able to get some programs written using monodevelop (though I prefer not having an IDE in some cases, so I just use gedit with C# highlighting and mcs in a terminal to compile).

---

### Post by tom-ubuntu on 2005-08-07
[QUOTE=L150]Hello,
Thank you for your help greatley appreciated.
I have heard a lot of people also say that mono is unstable after i found out what it was called from you, they seemed to insist I wait on a more stable release of the application what would you reccomend?  Regards L150[/QUOTE]
No, I did NOT say that Mono is unstable. Mono is rock solid, excellent work. But **monodevelop is unstable currently**. That's a different thing. But keeping in mind, that monodevelop is still at its beginning, it is ok for me. I will continue to test with it, I really think this is an IDE linux really need.

---

### Post by mostwanted on 2005-08-07
[QUOTE=joeuser]No, I did NOT say that Mono is unstable. Mono is rock solid, excellent work. But **monodevelop is unstable currently**. That's a different thing. But keeping in mind, that monodevelop is still at its beginning, it is ok for me. I will continue to test with it, I really think this is an IDE linux really need.[/QUOTE]

Agreed. Monodevelop is horrible, at least the version included with Ubuntu (and/or backports) is.

---

### Post by tom-ubuntu on 2005-08-08
It is just at a early stage. If you have a look at SharpDevelop, Monodevelop is a port of this, I am really looking forward for a stable version. It has a lot of nice features. Hope they will have time to implement most of the stuff.

---

### Post by L150 on 2005-08-09
[QUOTE=Gnobody]In the meantime Python is a GREAT easy to learn powerful alternative.  [www.python.org](http://www.python.org)[/QUOTE]

Thanks but i'll pass  :)  IMO python sucks ...

---

### Post by L150 on 2005-08-09
[QUOTE=joeuser]It is just at a early stage. If you have a look at SharpDevelop, Monodevelop is a port of this, I am really looking forward for a stable version. It has a lot of nice features. Hope they will have time to implement most of the stuff.[/QUOTE]

Yes i think it will be great when there is a stable version of mono, as sharp develop is also competing against VS.net if mono can pull this off for linux i think a lot more pepole with convert to linux imo. regards L150

---

### Post by tom-ubuntu on 2005-08-12
[QUOTE=L150]Yes i think it will be great when there is a stable version of mono, as sharp develop is also competing against VS.net if mono can pull this off for linux i think a lot more pepole with convert to linux imo. regards L150[/QUOTE]
But they really need to hurry up; Visual Studio 2005 is around the corner. MS improved a lot, everything looks much more nice, more integrated. 

SharpDevelop has many nice features implemented in the standart installation, but most of these plugins are also available for VS.net. And, I am wrong, or is there no integrated debugger in SharpDevelop? Just tried to set a breakpoint, like in VS.net, but didn't work.....

---

### Post by David Marrs on 2005-08-13
[QUOTE=joeuser]But they really need to hurry up; Visual Studio 2005 is around the corner. MS improved a lot, everything looks much more nice, more integrated. 

SharpDevelop has many nice features implemented in the standart installation, but most of these plugins are also available for VS.net. And, I am wrong, or is there no integrated debugger in SharpDevelop? Just tried to set a breakpoint, like in VS.net, but didn't work.....[/QUOTE]
 You know MonoDevelop is written in C#, and you're a C# programmer, so... ;)

---

### Post by tom-ubuntu on 2005-08-13
[QUOTE=David Marrs]You know MonoDevelop is written in C#, and you're a C# programmer, so... ;)[/QUOTE]
You got me ;) Honestly, if I would have the time, it would be very interesting in helping out there, it is a very interesting project. But: I am working on other projects already, sport a little bit more intensive then most people, and there is also my family. So my day is more or less booked. Excuse enough? ;)  But trying to help out the Ubuntu community as much as possible here in this forum. Puuhhh, it is getting personal here  :grin:

---

### Post by David Marrs on 2005-08-14
sorry, I couldn't resist :)

---

