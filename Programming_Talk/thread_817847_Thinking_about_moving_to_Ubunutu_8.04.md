---
title: "Thinking about moving to Ubunutu 8.04"
date: 2008-06-04
forum: Programming Talk
---

### Post by RaleTheBlade on 2008-06-04
I recently installed Ubuntu 8.04 on my secondary hard drive and I have to say its a very impressive piece of work :) Im a .NET developer (mixed with a little Win32 C++) so I was looking for a way to develop for the .NET framework on Ubuntu.

After searching, I discovered MonoDevelop, which did work to a degree. I had a few problems with it however. When I moved my solutions over from Windows XP and opened them in MonoDevelop, I had to re-add all of my project references (not a huge deal) and add an interop library. However, more to the point, the main problem I had with it was developing the forms. The way they were displayed when the build was run was pretty misaligned and jumbled. Is this normal? I cant professionally develop for Windows if I cannot develop the user interface properly.

I guess Ill sum up my questions and make it a bit easier :)

Is MonoDevelop used for professional development by anyone?
How is the support for .NET 3.0 and the Windows API?
If MonoDevelop isnt the best solution for this, what is?

Really what Im looking for is a good solid reason to kick Windows (I will buy a Mac before moving to Vista!) and make the permanent move to Ubuntu, but unfortunately Windows XP is the only environment Ive found so far that I can develop for Windows properly :( I thoroughly enjoy Ubuntu's rich features and "it just works" attitude, but if I cant develop professionally on it, I sadly cant use it *sniffle*

Any advice is much appreciated :D

---

### Post by Rocket2DMn on 2008-06-04
Welcome to Ubuntu, this is certainly not a question for the Absolute Beginners forum.  I will ask a mod to move this thread to the Programming Talk forum, but in the meantime - the best place to develop for windows is in windows, especially professionally.  You might want to consider keeping your dual boot setup.  As far as I know, .NET support in linux is limited.
An alternate option is to setup Windows XP in a Virtual Machine using VirtualBox - [http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

---

### Post by EXCiD3 on 2008-06-04
Not sure about how much MonoDevelop is used anymore. There are a few applications such as Banshee that use it.

One of the issues you are facing is the newness of MonoDevelop...Its only just now hit version 1.0 and look at .Net...they are in their 3rd framework already! I'm not sure if the "jumbled forms" that you are describing has anything to do with the way it "packs" the forms, unlike Visual Studio's designer that has a set placement. Widgets are expanded to fill all space (unless set otherwise) in GTK.

Saw you are from Illinois! Me too! I've been enjoying all the storms down around springfield for the last week! ;)

---

### Post by LaRoza on 2008-06-04
You see, .NET is for Windows. It is like using the POSIX headers on Windows, not what according to their design.

If you want to do Windows development the best place for that is on Windows.

Mono will allow you to use C# and perhaps a few other languages on Linux, but that would be limiting yourself. Linux has much more to offer than rehashes of what Windows uses.

---

### Post by LaRoza on 2008-06-04
> **EXCiD3 said:**
> Not sure about how much MonoDevelop is used anymore. There are a few applications such as Banshee that use it.

Monodevelop is an IDE, applications don't "use it".

mono: [http://en.wikipedia.org/wiki/Mono_(software](http://en.wikipedia.org/wiki/Mono_(software))

---

### Post by LaRoza on 2008-06-04
> **RaleTheBlade said:**
> 
Is MonoDevelop used for professional development by anyone?
How is the support for .NET 3.0 and the Windows API?
If MonoDevelop isnt the best solution for this, what is?

Really what Im looking for is a good solid reason to kick Windows (I will buy a Mac before moving to Vista!) and make the permanent move to Ubuntu, but unfortunately Windows XP is the only environment Ive found so far that I can develop for Windows properly :( I thoroughly enjoy Ubuntu's rich features and "it just works" attitude, but if I cant develop professionally on it, I sadly cant use it *sniffle*


Now that I carefully read you post...

What is "professional"? For serious work, yes it is. For corporate work? Perhaps not I would think. There would be little reason to have a developer use Linux if they were to restrict themselves like that.

Zilch. Windows API is for Windows. Read the wikipedia article.

Windows is the best solution for Windows development.

You will also perhaps be surprised to learn the Linux is the only platform that can really be used for Linux development.

---

### Post by Vadi on 2008-06-04
There certainly are lots of C# apps in Ubuntu now, as Windows programmers are moving over. While more native things are certainly preferred, you're certainly welcome to use mono tools for development. I don't know if there's a ubuntu group or no, but beside some of the default apps in ubuntu that use mono, there are several useful projects on launchpad.net also.

Just like there are tons of mingw-compiled programs for Windows. Not everyone cares to do the work twice.

PS. Ignore the mono haters; they are small in numbers, are loud, and don't make up for the troubles they're causing. Users don't care if it's C, Python, or C#, as long as it works better.

---

### Post by RaleTheBlade on 2008-06-04
Thanks for all the replies :) This forum is certainly more active and friendly than some of the other ".net, Windows, Microsoft" forums Ive visited.

One of the real reasons I want to move over to Linux is because Im tired of Micro$ofts "we rule the world, just deal with it" attitude. But unfortunately, I am a .NET developer, thats what I was hired to do. But just because I develop apps for Windows doesn't mean I should have to use Windows. I dont hate Windows... its just not my preferred OS when compared with Linux or even Mac OS X.

I suppose I will continue developing on Windows XP. But I would like to develop for Linux using C++ preferably. This is probably a redundant question I'm sure, but since I'm here Ill ask: How is g++ for development in Linux? Anyone used it? Does it have good features? :) I personally am partial to C++ and C, granted some may deem them as "outdated" languages, but any language that allows you both low level control and high level ease of use is not outdated, its just or put aside for form over function.

Vadi, I don't hate the haters, everyone is entitled to their opinion :) And if i had my way (which I'm moving over to Win32) I wont even use C# much anymore. Its just that thats what a lot of employers want these days. They want the RAD because they often want the best software and they want it done yesterday, lol. But time and time again Ive found myself saying "What the &%@#& is C# compiling, what is it doing?!" because Ive run into many problems that just don't make sense unless you know what the compiler is doing under the hood.

Anyway, I'm a long winded talker... Ill use Windows for .NET development. But I would also like to start development for Linux and contribute to such an awesome environment and community. The more software we make and the more powerful we make Linux distro's, the larger chunk we (hopefully) take out of Microsoft's market share and put free PC's and free use back on the map :guitar:

---

### Post by LaRoza on 2008-06-04
> **RaleTheBlade said:**
> 
I suppose I will continue developing on Windows XP. But I would like to develop for Linux using C++ preferably. This is probably a redundant question I'm sure, but since I'm here Ill ask: How is g++ for development in Linux? Anyone used it? Does it have good features? :) I personally am partial to C++ and C, granted some may deem them as "outdated" languages, but any language that allows you both low level control and high level ease of use is not outdated, its just or put aside for form over function.

And if i had my way (which I'm moving over to Win32) I wont even use C# much anymore. Its just that thats what a lot of employers want these days. They want the RAD because they often want the best software and they want it done yesterday, lol. But time and time again Ive found myself saying "What the &%@#& is C# compiling, what is it doing?!" because Ive run into many problems that just don't make sense unless you know what the compiler is doing under the hood.

You can run Windows in a virtual machine, if you have the RAM and want to do that. 

gcc (of which g++ is a part) is the most important piece of software ever written. Without it, free software wouldn't exist. Everyone who uses C++ here used g++. You can check out the sticky for basic usage of them. You can get IDE's (see sticky for list) also, you have a lot to chose from :-)

You can use C# (at least, what is in the ECMA standard) on Linux with little trouble. C# isn't really all that RAD, you could get yourself Glade/QT Designer/wxGlade and your language of choice for that (also, see sticky on "GUI toolkits")

---

### Post by altonbr on 2008-06-04
I've created a script for helping you install VMware on Ubuntu: [http://ubuntuforums.org/showthread.php?t=788169](http://ubuntuforums.org/showthread.php?t=788169) (if you don't want to go through the 20+ steps to install it).

As for C or C++ programming in Linux, it is CERTAINLY NOT DEAD. Yes, a lot of programmers are now using scripting languages, such as python, to do their dirty work, but just make a couple posts stating you skills or find some Linux job postings and you will see that it is highly beneficial to know C and/or C++.

Anyway, since you're more of a .NET developer, you'll probably want to pick up some good books on the subject. For Linux, O'Reilly is almost always the best choice.

C/C++: [http://oreilly.com/pub/topic/cprog?page=bestselling](http://oreilly.com/pub/topic/cprog?page=bestselling)
Linux: [http://oreilly.com/pub/topic/linux?page=bestselling](http://oreilly.com/pub/topic/linux?page=bestselling)
Linux and C++ @ Chapters/Indigo (Canadian): [http://www.chapters.indigo.ca/books/search?keywords=linux%20c%2B%2B&pageSize=10](http://www.chapters.indigo.ca/books/search?keywords=linux%20c%2B%2B&pageSize=10)

Hope that helps!

---

### Post by Vadi on 2008-06-04
I'd recommend getting VirtualBox, installing Windows in it, and doing development like that. That's what I do too - can't be bothered to reboot each time I want to compile for windows, while Virtualbox starts up in 3-5 seconds tops.

---

### Post by altonbr on 2008-06-04
> **Vadi said:**
> I'd recommend getting VirtualBox, installing Windows in it, and doing development like that. That's what I do too - can't be bothered to reboot each time I want to compile for windows, while Virtualbox starts up in 3-5 seconds tops.

You can also a method - possibly using VirtualBox, but I know in VMware - to make Windows start up as soon as the VMware service is running, so when you need to switch to it, its there! Of course, there is some performance degradation if you have Windows auto-loading lots of apps.

---

### Post by Can+~ on 2008-06-04
Unix pretty much defined the standards on C and C++, you can assume that gcc (and g++) are top-notch.

Anyway, I KNOW you'll miss Visual Studio, almost everyone who moves from windows and C# seeks for an alternative. Sometimes Eclipse with the cdt plugin does fine (for C++ and C), mono for C#, my brother has windows running on a virtual box, me too (although I rarely use it), I can run photoshop from inside the virtual box with just 1 gb of memory, and VS is big, but not photoshop-big.

At least, in this forums, we encourage users to move to python (I know pmasiar is hiding, somewhere), perl, or ruby, or sometimes LISP for the extra knowledge, just so they get the "high level language" experience. But since you're getting paid for it, it won't be an alternative, but more like a hobby.

---

### Post by pmasiar on 2008-06-06
Did someone mentioned my name? :-)

> **RaleTheBlade said:**
> I am a .NET developer, .... employers want these days... the RAD because they often want the best software and they want it done yesterday

Did you considered dynamically typed language instead of statically typed like C# or C++? Speed comes from flexibility (you pay with 20% slower performance for 500% gain in productivity - a bargain I would take any day). MSFT released IronPython, Python implemented for .NET, under open-source license. It is not GPL of course, but close. And when you learn Python, you can hack for FOSS too - language is same, just some libraries differ.

With IronPython, you would be able to do stuff you did not think is even possible in C#.

See wiki in my sig for links

---

### Post by RaleTheBlade on 2008-06-08
Well Ive officially moved this machine to a full Ubuntu 8.04 machine now :) I got sick of Windows after it crashed on me big time the other day and I lost my network connections and it was blue screening regularly. Then when I tried to reinstall XP on this machine, it kept having file copy issues and the like... so after a few hours of testing to make sure my hardware was solid, I got my girlfriends computer, downloaded the ISO to burn to a CD, and installed a full 64 bit desktop version of Ubuntu.

It worked perfectly, without a hitch, started right up and ran great! To h3!! with Microsoft, lol.

IronPython, huh? Ill have to look into that. I was also looking into the NetBeans IDE for Java development too (anyone have any ideas on it?), and it looks pretty good. I messed around with it earlier today. But what I will probably do is set up a dev-only box and use it strictly for my Windows and .NET development, and use this one for games and personal use since it actually... you know... runs correctly now, haha. Thanks to Ubuntu =D

Ill definitely have to check out some of the C++ options, but as far as dev goes, Im kind of interested in doing some Java too.

Thanks for all the replies! Its great =D I'm happy to be a part of the open source community now.

---

### Post by LaRoza on 2008-06-08
> **RaleTheBlade said:**
> 
Ill definitely have to check out some of the C++ options, but as far as dev goes, Im kind of interested in doing some Java too.


You might want to check out the 64 bit users forum (on main page) if you have any problems. You shouldn't have any though.

Java works the same on Linux, so you can do that kind of development. The sticky has information on using Java, although it has no information on IDE's that are commonly used with Java. Netbeans and Eclipse are common it seems.

---

### Post by Rocket2DMn on 2008-06-08
I use Eclipse and haven't found any pressing need to switch.  Overall, it's a good functional IDE for Java.

---

### Post by Vadi on 2008-06-08
I'd also recommend Geany as an IDE because of it's amazing flexibility. If you've ever used Notepad++ on windows, this uses the same scintilla, but is better.

---

### Post by Jimmay on 2008-06-08
I use java a lot as a hobby. I've always used netbeans and I think it's great (though I haven't tried eclipse, but I've heard it's good). One thing: if you're using 64-bit, you may have a * of a time with trying to get applets and stuff to work, because sun hasn't put support for them into the 64-bit java runtime. It's great for the vast majority of the time though, and someone posted a script to help with installing 32-bit firefox so that you can use applets ([http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435))

---

### Post by altonbr on 2008-06-08
Yeah, Eclipse or an Eclipse derivative is probably your best bet for an IDE. Geany is also quite handsome but is lacking (some) features that Eclipse has.

Both are freely available in Ubuntu

To try it out, run:
```
sudo aptitude install geany
```
```
sudo aptitude install eclipse
```
If you don't like it, run:
```
sudo aptitude purge geany
```
```
sudo aptitude purge eclipse
```

Or install/uninstall through Applications > Add/Remove if you prefer the GUI.

---

### Post by Vadi on 2008-06-08
Or simply click here ([click]("apt:geany")) for geany and here ([click]("apt:eclipse")) for eclipse if you're lazy.

---

### Post by LaRoza on 2008-06-08
> **Vadi said:**
> Or simply click here ([click]("apt:geany")) for geany and here ([click]("apt:eclipse")) for eclipse if you're lazy.

..and happen to be using Firefox.

For those with the best browser, that won't work.

---

### Post by Vadi on 2008-06-08
I *think* it works with Konqueror too.

And hey, if you got the 'best' browser, surely everything must work best in it.

---

### Post by bruce89 on 2008-06-08
> **Vadi said:**
> And hey, if you got the 'best' browser, surely everything must work best in it.

If it doesn't work in Epiphany, I'm not interested.

---

### Post by Vadi on 2008-06-08
Don't worry about it.

---

### Post by RaleTheBlade on 2008-06-08
> **Vadi said:**
> Or simply click here ([click]("apt:geany")) for geany and here ([click]("apt:eclipse")) for eclipse if you're lazy.

I guess this makes me super lazy, but I used the Synaptics Package Manager and downloaded Eclipse and NetBeans and had them automatically installed for me, hahaha. So far NetBeans seems to be working correctly. I actually haven't had much trouble at all with software and the 64 bit version of Ubuntu. Even Wine runs some basic Windows games without much issue.

---

### Post by RaleTheBlade on 2008-06-08
> **Vadi said:**
> 

And hey, if you got the 'best' browser, surely everything must work best in it.

Whats the "best" browser? Ive always used Firefox, but are you mocking IE? haha. You should check out the definition of IE on UrbanDictionary

[http://www.urbandictionary.com/define.php?term=Internet+Explorer](http://www.urbandictionary.com/define.php?term=Internet+Explorer)

---

### Post by Vadi on 2008-06-08
No, I believe LaRoza was referring to Opera as being in her view the 'best' browser. You get people here and there in the Linux community that can sometimes feel *very* strongly about their personal preferences o.O

---

### Post by Can+~ on 2008-06-08
I agree with LaRoza, Opera is (or at least was) the best browser, it introduced tabs before than anyone, themes, plugins, W3 standards compliance, and much more.

I still prefer firefox though. :KS

---

### Post by bruce89 on 2008-06-08
Don't hijack this thread with browser rubbish.

---

### Post by kevdog on 2008-06-08
LR just likes to throw in under-the-table jabs, hoping no one will notice :)

---

### Post by RaleTheBlade on 2008-06-08
I love Firefox, I even have a Firefox t-shirt, lol. But yeah, lets not hijack the thread. I think I have all I need to get started with dev in Ubuntu, and Ive completely moved to Ubuntu (installed from a CD, no sign of Microsoft's junk on this PC) so if the moderator wants, they can close this thread :)

---

