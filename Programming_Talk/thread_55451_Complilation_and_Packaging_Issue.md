---
title: "Complilation and Packaging Issue"
date: 2005-08-09
forum: Programming Talk
---

### Post by Rain on 2005-08-09
Good day everyone,
I am Wilson from Singapore. I have one key question to ask about Programming with a Dual Boot System and on Linux, Please give me your guidances.

If this kind topic has already existed but in different titles/thread, i apologised and please kindly point me to the link to the site/thread. 

I have my first Linux (Ubuntu 5.04) installed and has been VERY pleased with it.
Since then, i have also tried other Linux like Suse9.3, Fedora Core 4, Knoppix 3.7.
I know that there are 2 commonly used bootloaders in Linux, that is, LILO and GRUB. Windows is using NTLRD right?!

The company that I worked for, uses Visual Studio .NET and Java for their clients projects. Therefore I am programming with C#, VB.NET and J2EE.

[COLOR=DarkOliveGreen]Now I wanted to ask, If i were to Dual Boot my system with Windows XP and Linux and have Linux Boot Loader to boot up Windows XP, will I face program Compilation and Packaging problems with .NET?[/COLOR]
[COLOR=DarkSlateBlue]Will my programs be able to run smoothly on my client workstation (installed with Window 2000)?[/COLOR][COLOR=DarkOliveGreen]So what if I program my Java application in Ubuntu(i know that Java is platform-independent) and then used the compiled and packaged application in Windows XP, will it face any error since I programed + compiled + tested my application on a Linux OS and not on a Windows OS??[/COLOR]

Again, I apologise about this noob-ness of mine, since I would like to convince my friends and collegues that Linux is WORTH-IT and that it can be as good and even better than WinXP that they are using now. That is why I went ahead alone and wanted to try to program with a Multiboot system and on Linux. I appreciated anybody who have read my thread and thanked all seniors who will be giving me your advices. Thank you all.

---

### Post by fjleal on 2005-08-09
> **Rain]Good day everyone,[/QUOTE]
Greetings!

[QUOTE=Rain]I have my first Linux (Ubuntu 5.04) installed and has been VERY pleased with it.[/QUOTE]
Way to go!  said:**
> If i were to Dual Boot my system with Windows XP and Linux and have Linux Boot Loader to boot up Windows XP, will I face program Compilation and Packaging problems with .NET?
What makes you think you would? Once you boot into Windows you're in your "normal" Windows environment (considering there's something normal about the way Windows works). It simply ignores whatever other o.s. there may be on any other disk partitions.

[QUOTE=Rain]Will my programs be able to run smoothly on my client workstation (installed with Window 2000)?[/QUOTE]
If they do now, surely they will. Do they? :)

[QUOTE=Rain]So what if I program my Java application in Ubuntu(i know that Java is platform-independent) and then used the compiled and packaged application in Windows XP, will it face any error since I programed + compiled + tested my application on a Linux OS and not on a Windows OS??[/QUOTE]
Your Java app. runs on top of a virtual machine (the JVM). It doesn't matter which o.s. you run underneath it. The java-code is the same.

[QUOTE=Rain]Again, I apologise about this noob-ness of mine, since I would like to convince my friends and collegues that Linux is WORTH-IT and that it can be as good and even better than WinXP that they are using now.[/QUOTE]
And a lot more versatile. And free! ;)

---

