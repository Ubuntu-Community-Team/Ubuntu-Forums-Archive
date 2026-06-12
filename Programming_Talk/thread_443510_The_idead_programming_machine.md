---
title: "The idead programming machine"
date: 2007-05-14
forum: Programming Talk
---

### Post by Eagleon on 2007-05-14
Hello everyone,

Not so long ago, I use to program on the windows platform. After switching to ubuntu several months ago, I don't think I will ever go back. It's amazing how inferior windows is in comparison. Although I am good at getting my stuff done in windows, and just a beginner in linux, I am willing to invest my time in learning how to get things done just as well on ubuntu. So this is what I need advice on. 

My main question is... what are some of the best combinations of software I can set up for everything to run smoothly. I do a lot of php, css, ajax, and mysql based coding. In addition, I also need to do some C++ and C# for college assignments as well (Visual C++ 6.0 is the required compiler to use for C++, and Microsoft again for the C#). I have installed Visual studio in the past using wine, but it's a little problematic sometimes and does not always function the same as in windows. For php, I have used Geany so far and love it... but are there any other programs that might be better? I have used geany for C++ as well, but isn't fully sufficient. As for CVS, I am thinking of dropping it and moving to subversion or even something else. What would you recommend? Also, what would be the best way to have my servers installed? That is, my php, apache, and mysql stuff. I tried installing a virtual machine, and it "almost" works. I used VirtualBox, but when the drive-size is larger than 2 GB, it hangs during the OS install. Is there any way that I could install windows on a partition and use it as a virtual machine using VirtualBox? Sorry, I know it is a lot of questions, but any advice will be greatly appreciated. 

Thank you so much....

---

### Post by Eagleon on 2007-05-14
p.s. sorry about the title, I meant to write: "The Ideal Programming Machine" ... oops!

---

### Post by kragen on 2007-05-14
> **Eagleon said:**
> p.s. sorry about the title, I meant to write: "The Ideal Programming Machine" ... oops!

If you go back to the category view and kind of double click on your thread name (not on the text, on the space to the right I think), then it lets you edit it.

I just found this out earlier today :P

---

### Post by JT673 on 2007-05-14
If I was in that situation, I would download ReactOS (a free, open-source Windows alternative), dual-boot (make a new partition for it), and install VC++/# on it.  I don't know, I haven't tried ReactOS yet, but from what I heard, it's pretty good.

---

### Post by Eagleon on 2007-05-15
> **kragen said:**
> If you go back to the category view and kind of double click on your thread name (not on the text, on the space to the right I think), then it lets you edit it.

I just found this out earlier today :P

Thanks... this is great to know! :) ill fix it right away

[QUOTE=JT673]If I was in that situation, I would download ReactOS (a free, open-source Windows alternative), dual-boot (make a new partition for it), and install VC++/# on it. I don't know, I haven't tried ReactOS yet, but from what I heard, it's pretty good.[/QUOTE]

ReactOS seems great! wow.. I never knew about this! Seems like a much better alternative than M$ ... since it's open source, it will soon surpass the caliber of XP itself! 

Thanks again both for the help, I really appreciate it!

---

### Post by Eagleon on 2007-05-15
> **kragen said:**
> If you go back to the category view and kind of double click on your thread name (not on the text, on the space to the right I think), then it lets you edit it.

I just found this out earlier today :P

it didn't work :( ... there was no such link.

---

### Post by pmasiar on 2007-05-15
> **Eagleon said:**
> I also need to do some C++ and C# for college assignments as well (Visual C++ 6.0 is the required compiler to use for C++, and Microsoft again for the C#). I have installed Visual studio in the past using wine, but it's a little problematic sometimes and does not always function the same as in windows. 

It depends where you see your core expertise. Do you prefer to be expert developer, dealing with platform only as needed, or do you see yourself diving deep into platform issues if something does not work as supposed to?

If platform is a "black box" for you, IMHO you are better off double-booting and running your MSFT-related apps on Windows. Don't waste your time on wine etc, if you do not want to dive in and figure why something does not work the same. When done, reboot to Linux and play with your next language on free platform.

But if you want and enjoy to dive in when encountering problems, please do use free software, and fix anything you found so next guy has it easier than you did.

Just my $0.02

---

### Post by Eagleon on 2007-05-15
thanks for the advice pmasiar. As for my C++ and C# related programming, it is only for school assignments... so as long as I am able to at least develop the code in Linux, I don't mind dual booting to compile and add final touches later in windows. The thing is.. I don't like windows anymore, and I want to avoid it as much as possible. Basically, what I am seeking to accomplish is write the codes on ubuntu and then move it to windows later and fix anything that doesn't work. What would be ideal though is to be able to test the source and see that everything is OK every now and then: during the coding process (on linux). I know it sounds silly lol but most of the code I write for C++ is console based anyway, and very simple. The C# stuff is also very simple stuff. I am only taking the classes because they are required by my major...

---

### Post by kknd on 2007-05-15
My programming environment:

O.S: Ubuntu 7.04 Feisty Fawn
Compilers: gcc 4.1, g++ 4.1, javac (JDK 6.0)
IDE's: Eclipse (for C++, Python and Haskell), NetBeans (for Java).
Frameworks and etc.: gtkmm, boost and the JDK itself.
  
I used to program in Windows until last years, and I prefer GNU / Linux over Windows for both development and general use.

In GNU / Linux, its easy (comparing to Windows) to make portable software, so you still can develop targeting Windows and other O.S's with little effort)

---

### Post by pmasiar on 2007-05-15
> **Eagleon said:**
>  As for my C++ and C# related programming, it is only for school assignments... so as long as I am able to at least develop the code in Linux, I don't mind dual booting to compile and add final touches later in windows. The thing is.. I don't like windows anymore, and I want to avoid it as much as possible.... I write for C++ is console based anyway, and very simple. The C# stuff is also very simple stuff. .

If I understand you correctly, you prefer to develop under Linux. Which makes sense, because all knowledge and editor "finger memory" you gain, is directly transferable to other projects on Linux.

So you might try the compromise: develop all code on Linux, then transfer it to Windows and double-check & finish there. Mono (C#) should be OK for most of basic  functionality.

---

### Post by Eagleon on 2007-05-16
thank you kknd and pmasiar! I appreciate the help. You were absolutely right about me liking Linux over windows. Apart from the benefits you mentioned, windows is a pain to use. I probably spend over 40% of my time trying to maintain the damn thing in top running condition. With linux, thats not even a problem. I would literally have to deliberately do something wrong to mess it up. wouldn't you agree? :)

---

