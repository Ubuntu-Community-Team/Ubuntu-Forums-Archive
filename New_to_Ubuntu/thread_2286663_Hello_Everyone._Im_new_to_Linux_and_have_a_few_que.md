---
title: "Hello Everyone. Im new to Linux and have a few questions"
date: 2015-07-13
forum: New to Ubuntu
---

### Post by gillie.john78 on 2015-07-13
Alright I'm sorry if this is in the wrong area but the mods here seem to be nice and move them around from what I've seen :razz:

So i am new to the whole Linux/Ubuntu Distro Operating Systems but i  have tried Ubuntu a few times before. I decided to clear out my PC from  all my games and junk to do something more productive with my time and  wish to try something more technical which Ubuntu seems to be. I am  trying to get into programming more so Web Development and maybe some  Android Development but anyways i have some questions (Already tried C++  , C# , Java , CSS , HTML  [COLOR=#a9a9a9][SIZE=1]*PS. Never Got into them as much as i should on Windows*[/SIZE][/COLOR]


1. How do i get on the same level of all you professionals here? I keep  hearing about servers and all the inner-workings of Linux but i have no  idea what any of it means. I haven't made a server or anything before  and the closest thing to command line i have achieved was the Sudo - Get  Apt commands. So how do i learn everything about Ubuntu? *[SIZE=1][COLOR=#a9a9a9]Im saying im stupid but. You guessed that right? Okay Then.[/COLOR][/SIZE]*

2. Is it good for Development? More So Web Development etc and can it do anything for Android development  

Look im going to lay gravy on the table and :tldr = (How do i learn everything?) [COLOR=#a9a9a9][SIZE=1]*You can tell i have no idea what i am talking about.. *[/SIZE][/COLOR]

---

### Post by QIII on 2015-07-13
Just so you know, only a small fraction of us are computer professionals.  Most are not.  We are all just regular Joes and Janes who volunteer our time here.

---

### Post by gillie.john78 on 2015-07-13
> **QIII said:**
> Just so you know, only a small fraction of us are computer professionals.  Most are not.  We are all just regular Joes and Janes who volunteer our time here.

Oh. I thought everyone here were experts.. Still. Is there anyway to know the things i asked?

---

### Post by sandyd on 2015-07-13
> **gillie.john78 said:**
> <shnip>
1. How do i get on the same level of all you professionals here? I keep  hearing about servers and all the inner-workings of Linux but i have no  idea what any of it means. I haven't made a server or anything before  and the closest thing to command line i have achieved was the Sudo - Get  Apt commands. So how do i learn everything about Ubuntu? *[SIZE=1][COLOR=#a9a9a9]Im saying im stupid but. You guessed that right? Okay Then.[/COLOR][/SIZE]*

2. Is it good for Development? More So Web Development etc and can it do anything for Android development  

Look im going to lay gravy on the table and :tldr = (How do i learn everything?) [COLOR=#a9a9a9][SIZE=1]*You can tell i have no idea what i am talking about.. *[/SIZE][/COLOR]

> **gillie.john78 said:**
> Oh. I thought everyone here were experts.. Still. Is there anyway to know the things i asked?

The best way is to poke around Linux and discover how it works. Don't be afraid to break something; breaking something creates a chance for you to learn how to reverse what you have done to it/

2. There is no "best os" for web development, most of what you need is a text editor or IDE (I reccomend Komodo, sublime, or PHPStorm if you are a serious developer) and a web server. Both of those things are mostly the same on all OSes. There are some things that may be harder to get working in one OS (I'm sure that Microsoft SQL Server doesn't work in Linux by default). Most people, however find that Linux is a better server OS due to package management. Packages can all (mostly) be found in the repositories, and that makes updating easy. OSes like Ubuntu also provide security updates without updating the application version itself, which makes more sense to people running servers. Generally, for major applications, applications to not get updated to major versions in the middle of a release.

---

### Post by Irihapeti on 2015-07-13
The general answer would be to try things. And to try them on a machine where it doesn't matter if you make a huge mess. That is, don't use the same one where you store your precious photos, videos and other documents. If you're playing with a server, best to start out with it not connected to the internet, so that you don't get hacked before you even start.

You could start with reading [https://help.ubuntu.com/lts/serverguide/index.html](https://help.ubuntu.com/lts/serverguide/index.html) Other people may have other suggestions.

For the record, I'm not a pro. I run a few servers at home, all but one not publicly accessible. I've lost count of the number of times I've broken things, including some really stupid mistakes. :( The nice thing about Ubuntu is that it's easy to restore and start again.

---

### Post by gillie.john78 on 2015-07-13
> **Irihapeti said:**
> The general answer would be to try things. And to try them on a machine where it doesn't matter if you make a huge mess. That is, don't use the same one where you store your precious photos, videos and other documents. If you're playing with a server, best to start out with it not connected to the internet, so that you don't get hacked before you even start.

You could start with reading [https://help.ubuntu.com/lts/serverguide/index.html](https://help.ubuntu.com/lts/serverguide/index.html) Other people may have other suggestions.

For the record, I'm not a pro. I run a few servers at home, all but one not publicly accessible. I've lost count of the number of times I've broken things, including some really stupid mistakes. :( The nice thing about Ubuntu is that it's easy to restore and start again.

Thanks. Why do you run servers? I always hear linux users running them but i cant think why myself. This is a rookie question im sure.

---

### Post by nerdtron on 2015-07-13
I'm working with Linux administration. I started from scratch and read lots of books/articles. Plus I'm lucky that my company allowed me to fiddle with test servers and do pretty much everything with those. There's no easy path so you'll need passion and willingness to understand and learn how Linux works.

I'm not a developer/programmer (although I know lots of web devs running linux). We use Linux for web servers, database servers, file servers, emails, DNS etc.

---

### Post by Bucky Ball on 2015-07-13
> **gillie.john78 said:**
> Thanks. Why do you run servers? I always hear linux users running them but i cant think why myself. This is a rookie question im sure.

Welcome. If you're asking why people run servers and can't think of a reason why, I'd say you probably don't need to run one. :)

Ubuntu is fine for development of the things you mention. 

Download a desktop .iso, create boot media (disk or USB), boot from it and 'Try Ubuntu'. If it is all good, install Ubuntu. Any questions, ask. Your other option, if you do want to go the server route, is download the server .iso and as above. You need a cable ethernet connection to install server. That will be a steep learning curve as the server has no desktop environment. Easily overcome by installing one. 

Just one other point, the Ubuntu desktop environment, Unity, is not very Windows like. You might be more comfortable with Xubuntu or Ubuntu-Mate as an entry point. Still, its all a learning curve, however you go about it. Enjoy the curve! As above, best way to learn is dive in and start asking questions. :)

Good luck.

---

### Post by Irihapeti on 2015-07-13
> **gillie.john78 said:**
> Thanks. Why do you run servers? I always hear linux users running them but i cant think why myself. This is a rookie question im sure.

Why do I run servers at home? Two reasons, really.

One, so that I can do things on my home network, such as access files on my desktop machine using my netbook or my cellphone

Two, so that I can learn things. One day, I may set up a VPS, but I want to be reasonably confident that I know what I'm doing first - or at least enough to avoid getting into too much trouble.

Plus, I love tinkering with things. :)

---

### Post by lisati on 2015-07-13
> **gillie.john78 said:**
> Thanks. Why do you run servers? I always hear linux users running them but i cant think why myself. This is a rookie question im sure.

I used to run my own email server, partly because I didn't like the spam filtering options available via my email provider, and partly because I could. It took a fair bit of work (and learning) to get it to the point where I was reasonably happy with the results, but, unfortunately, the computer I was using for that task died, and my budget isn't up to replacing it (yet). 

> **Bucky Ball said:**
> Welcome. If you're asking why people run servers and can't think of a reason why, I'd say you probably don't need to run one. :)
Agreed. 

These days I use Ubuntu mainly for my day-to-day stuff,  such as surfing the net, checking email, and visiting a handful of online forums such as this one.

There is immense satisfaction that can be found in trying a new operating system and getting comfortable with its way of doing things. Enjoy!

---

### Post by QIII on 2015-07-13
And remember, you don't have to divorce Windows.  Linux doesn't care if you have a mistress or sugar daddy.

You don't have to give up speaking English to learn to speak German, right?

---

### Post by Geoffrey_Arndt on 2015-07-13
How you learn Linux mainly depends on what you want to achieve.   The "path" for different objectives is VERY wide.   If you just want to be a Linux "enthusiast" (similar to Windows "Power User") . . . then, the advice already given is OK (e.g., do your first download, do install & customize your setup.   Then use your system daily for at least 6 months (a year is even better).   Read up at sites like this daily (or at least 2-3 times per week).

However . . . if you want to go down other routes (career IT person), the path is quite different . . . serious developer (including web), engineer, security cons., systems analyst, project mgr, etc., etc., etc.  End result - - to qualify for top jobs is a Masters or higher in the relevant field.   Some starting jobs at smaller companies require at least an AAS or BS in Comp. Sci.   There are still some exceptions (but not many).

---

### Post by huff2 on 2015-07-14
I'm by no means an expert. I'm a beginner just like you. I've found that I'm learning new things everyday just by reading these forums and trying new things. If I get stuck, I ask around on the forums and usually get great advice. For example, I recently created a virtual machine and ran a different version of linux on it just to play around. I've installed several programs and am now getting better at using ppa's and compiling from the source. If you like programming, then try and install PyCharm for python. That's it. Just play around and if you have a question just post it. Hope this helps.

---

### Post by jason_gibson2 on 2015-07-14
My only suggestion along with everything everyone else has said. Before you dump Windows and put yourself in a corner, get Virtualbox and run linux inside a vm, and live in that vm for awhile. That way you can always jump between windows and linux at will without having to deal with rebooting. After you've done that and are sure of what you want to do or whatever, then boot the live image to see if it will work with all of your hardware. Only at that point if you are sure go for a full installation.

*EDIT* Not an expert. Only been using Linux as daily driver for a couple years. Recently went back to Windows, regretting it, currently debating my choice for permanent distro.

---

