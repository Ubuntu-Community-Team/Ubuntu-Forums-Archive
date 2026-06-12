---
title: "Compiling Windows Apps in Ubuntu"
date: 2008-11-17
forum: Programming Talk
---

### Post by Palu on 2008-11-17
Alright... my suspicion is that there is no way to compile C++ code in Ubuntu which can run under Windows. However, I'd really like to get into writing Windows programs (perhaps through Wine??) inside Ubuntu so that I can instantly test them through Wine. I don't, after all, have a Java background (which would probably be a better-cross-platform way to start tinkering), and this might be my easiest way to first dabble in Linux app development while not needing to boot into Windows. :)

I HAVE seen people get things like Dev-C++ to run under Wine, but I couldn't for the life of me figure out if the resultant work was an app that would run natively on Linux or if it compiled Windows apps. (Dev-C++ was my IDE of choice ever since originally learning with Visual Studio; I've tried to use Anjuta but embarrassingly have not been able to get anything to compile in the unfamiliar IDE.)

---

### Post by SeanHodges on 2008-11-17
If you want to use an IDE for C++ development you might want to try either Geany or Code::Blocks:

Geany: [http://www.geany.org/Main/HomePage](http://www.geany.org/Main/HomePage) (to install: [apt://geany]("apt://geany"))

Code::Blocks: [http://www.codeblocks.org/downloads/binaries](http://www.codeblocks.org/downloads/binaries)

Geany is a simple light-weight IDE, whilst Code::Blocks is more complex and is closer-matched to VS for features. You can also open Visual Studio projects in Code::Blocks.

As far as developing for Windows/Wine, you may want to check this out: [http://www.winehq.org/site/docs/winelib-guide/index](http://www.winehq.org/site/docs/winelib-guide/index)

There was a Linux version of Dev-C++ started years ago, but I don't think even the Windows version of Dev-C++ has been maintained since 2005.

---

### Post by Kilon on 2008-11-17
> **Palu said:**
> Alright... my suspicion is that there is no way to compile C++ code in Ubuntu which can run under Windows. However, I'd really like to get into writing Windows programs (perhaps through Wine??) inside Ubuntu so that I can instantly test them through Wine. I don't, after all, have a Java background (which would probably be a better-cross-platform way to start tinkering), and this might be my easiest way to first dabble in Linux app development while not needing to boot into Windows. :)

I HAVE seen people get things like Dev-C++ to run under Wine, but I couldn't for the life of me figure out if the resultant work was an app that would run natively on Linux or if it compiled Windows apps. (Dev-C++ was my IDE of choice ever since originally learning with Visual Studio; I've tried to use Anjuta but embarrassingly have not been able to get anything to compile in the unfamiliar IDE.)

Actually if you do not like to mess with JAva and start from zero you best bet besided WINE is actually the .NET framework.

The good thing about the .Net frameworks is that they keep alot of things the same, so if you have done C++ you will find alot of similarities in the libraries. Of course on the other hand is the diffirences, take GUI for example it is a completely different thing.  But do not forget that in Windows .NET application are exe files so it is highly likely a windows apps you already using ,that is a .NET app. On the other hand it is as much likely that it will be not a .NET app. 

If it is not then WINE comes for help. WINE builds a virtual Windows environment which allows you to run windows application. That is the theory , in practice alot of things can go wrong. At home I have a mac and I use Crossover Games for playing Guild Wars. Suffice to say that Guild Wars and WINE do not mix well. 

Crossover is a commercial application is actually an expansion to the free WINE. Crossover Games targets games only . For example I can play windows-only game GUILD WARS with no problem at all. There is also Crossover which can run windows apps like Microsoft office. But even CROSSOVER has alot of limitation so do not think of it as a final solution at all. There are many apps and games which simply wont even run. 

So my advice will be. First try WINE with no guarantees. Then crossover 

[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)

And those two only if .NET does not interest you. If it does then you will be fine with MONO (mono permits you to port .NET apps to any other paltform like Linux and Mac). 

Lastly if you want true cross platform , Java is the only choice. Python and mono have problems with the MAC platform. If you do not care about MACs then you will be fine with both MONO and Python. Python is much easier but you will be more familiar with C#. 

You can try all those things and see for yourself what fits you best. I tried them and found that JAVA was the only true candidate for what I needed.

---

### Post by Palu on 2008-11-17
> **SeanHodges said:**
> There was a Linux version of Dev-C++ started years ago, but I don't think even the Windows version of Dev-C++ has been maintained since 2005.

:( Oh, that would sadden my heart. I must have not been paying much attention to updates, because I hadn't realized that it wasn't active.

I think I will move to Java.

I guess I will reword my question to be simpler:

If I install a Windows IDE (any I can get to work inside wine) on my Ubuntu box and write a simple non-GUI (console input/output) application, can I compile it and run the binary both on a Windows machine, as well as the Linux box (using Wine)? I'm just not entirely sure what an IDE tries to do when it thinks it's a Windows app but running in Wine.

---

### Post by directhex on 2008-11-17
> **Kilon said:**
> Python and mono have problems with the MAC platform.

Still not sure what your source is for this.

Try [http://download.banshee-project.org/banshee/banshee-1-1.4.1.macosx.intel.dmg](http://download.banshee-project.org/banshee/banshee-1-1.4.1.macosx.intel.dmg) for size, having previously installed a recent Mono ([http://ftp.novell.com/pub/mono/archive/2.0.1/macos-10-universal/1/MonoFramework-2.0.1_1.macos10.novell.universal.dmg](http://ftp.novell.com/pub/mono/archive/2.0.1/macos-10-universal/1/MonoFramework-2.0.1_1.macos10.novell.universal.dmg)), as a headline Mono (GTK#) app running on Mac

---

### Post by Kilon on 2008-11-17
> **directhex said:**
> Still not sure what your source is for this.

Try [http://download.banshee-project.org/banshee/banshee-1-1.4.1.macosx.intel.dmg](http://download.banshee-project.org/banshee/banshee-1-1.4.1.macosx.intel.dmg) for size, having previously installed a recent Mono ([http://ftp.novell.com/pub/mono/archive/2.0.1/macos-10-universal/1/MonoFramework-2.0.1_1.macos10.novell.universal.dmg](http://ftp.novell.com/pub/mono/archive/2.0.1/macos-10-universal/1/MonoFramework-2.0.1_1.macos10.novell.universal.dmg)), as a headline Mono (GTK#) app running on Mac


Well my source is two BIG things

1) Python 2.6 wont even run on a mac both IDLE and Interpretter

2) GTK# ,  tested the examples included and some of them crashed a difficult to crash OS and some of them open windows in enormous sizes a feature which I think it was not intended by the GTK# team. Not counting of course the fact that GTK# mailing list supports the claim that the library is far from finished for the MAC platform. Why should I even bother ?

Those two big issues forced me into choosing Java. Java does not need any external libraries not only to work efficiently and reliably but natively as well. As far as I know (and tested) is the only language that has achieved this on the MAC platform (of course with the help of Apple). The GUI for instance looks exactly the same with any other MAC application just by issuing a command to use the native GUI look. 

Of course I wont even go into the matters of documentation between JAVA , MONO and PYTHON again on the MAC platform. GTK# and WXpython documentation is far from finished. 

Of course on the UBUNTU MONO and Python are excellent choices but personally I wont call a language cross platform if it cannot run the same code without any problems to all three big platforms WINDOWS,MACOS and LINUX.

> 
If I install a Windows IDE (any I can get to work inside wine) on my Ubuntu box and write a simple non-GUI (console input/output) application, can I compile it and run the binary both on a Windows machine, as well as the Linux box (using Wine)? I'm just not entirely sure what an IDE tries to do when it thinks it's a Windows app but running in Wine

Well it is most likely that it would work if you use regular windows libraries and nothing fancy . But does it worth it living constantly with the fear that your application might fail under WINE? You have to bare in mind that if you compile it UNDER WINE that equals to compiling UNDER WINDOWS , which means that your apps will need WINE to run and will never be a true UBUNTU app.

---

### Post by Palu on 2008-11-17
That's fine. I'm not looking to do this for much beyond academic reasons. My job doesn't require real programming--just minor ASP tweaks, CSS or html scripting, and some JavaScript. My question's inspiration is founded in wanting to stay within Ubuntu while coding in C++ (which is what I like for personal recreation--making small academic exercises for myself while not at work). Of course, this means I wouldn't need to do anything with Wine... except for the fact that it's nice to send things I make to friends (who are mostly stubborn Windows users).

If I go back to school or study a lot on my own, I'm pretty convinced that I will go the route of learning Java. :) But at the moment, my livelihood doesn't require me to know Java.

---

### Post by Kilon on 2008-11-17
> **Palu said:**
> That's fine. I'm not looking to do this for much beyond academic reasons. My job doesn't require real programming--just minor ASP tweaks, CSS or html scripting, and some JavaScript. My question's inspiration is founded in wanting to stay within Ubuntu while coding in C++ (which is what I like for personal recreation--making small academic exercises for myself while not at work). Of course, this means I wouldn't need to do anything with Wine... except for the fact that it's nice to send things I make to friends (who are mostly stubborn Windows users).

If I go back to school or study a lot on my own, I'm pretty convinced that I will go the route of learning Java. :) But at the moment, my livelihood doesn't require me to know Java.


My advice is to pursue you interests , I am a hobist programmer myself , I am doing it for the fun , now I am buried in a very big JAVA book and I enjoy it 100%. Pursue what makes you happy .If you really like C++ you could always try MONO. You wont find so many  diffirence.Or you could try Java or python. Learning a language is not that difficult , it is easy and highly rewarding. I think it will make you very happy to start making new programs that will impress your Windows friends. You never know , you might convert them into UBUNTU users. 


What I love about UBUNTU is that there are alot of people interesting on programming and eager to help, you can find plenty of source code and any help you will need. Remember even the smallest contribution counts.

---

### Post by Luggy on 2008-11-17
You can cross-compile code using GCC. A quick bit of googling pointed me towards this howto that maybe useful:
[http://www.kegel.com/crosstool/current/doc/crosstool-howto.html]("http://www.kegel.com/crosstool/current/doc/crosstool-howto.html")

I got a sneaking suspicion that this will require you to dive deep into the land of Makefiles, which can be difficult to grasp.

---

