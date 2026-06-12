---
title: "Ubuntu in the Enterprise Environment"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Ice Dragon on 2008-07-15
Hello everyone, first of all I would like to say that I appreciate the Ubuntu effort, free quality OS for everyone is really something.

That being said, I am having a hard time convincing myself that Ubuntu (or any linux distro for that matter) is really the equal (let alone  better) of modern Windows operating systems. Before you quit reading due to that statement, please hear my reasoning.

I work in a professional IT environment that uses many Enterprise tools such as Deep Freeze, Symantec Ghost, Domains, Papercut, exchange servers for email and mobile devices, image deployments with sysprep, etc.. etc..

I know that Ubuntu can do some of this, but its really a hack to get these things to work and most of it cant even be done. With Symantec Ghost Solution Suite 2.0, I can control a Lab of 40+ computers remotely from our IT office. I can power them all on, send out AI packages to install updates and new programs remotely to all 40+ at once, and then shut them down again. I can even install images (copies of the OS) remotely on all 40 at a time, and thats just one lab of many.

I just cant see using Ubuntu in an environment where everything works so beautifully together and is setup to really make IT work efficient like described above. Ubuntu just seems to lack the tools available to the Windows OS for Enterprise use.

Now, I understand that maybe the target is home users and that is fine. For home users that do not play video games on their desktops, Ubuntu may be a good choice for them over Windows. Then again, if they do play games, why wouldn't you use windows? Even more to the point, if you want your grandma to use a home user computer, why not get her a mac? it can play a lot of games now days and is arguably the easiest computer on the market to use for average people who don't know computers well.

I then question, If windows is superior for Enterprise and business use (no simply accounting for Ubuntu right?), and Mac is superior for ease of use and hassle free computing at home, where does the Ubuntu desktop fit in? Is its only placement for countries where people are poor beyond belief and very under-privileged?

Anyway this is an honest inquiry, I hope you dont view this as bashing, as I like very much the idea behind the Ubuntu movement, but for businesses $100 per machine or less to buy windows is NOT an issue at all, its "basically free" to them. Id like some good reasoning on how Ubuntu fits in.

---

### Post by Het Irv on 2008-07-15
I have to agree with you, in your situation Ubuntu is not a good fit.  Ubuntu in the buisiness world seems to work better in a small business environment.  A small business can used Ubuntu to reduce costs, but without generating many problems, as long as they use software that work under Linux.  Personally I don't think that Ubuntu or any Linux distro is quite ready for mass use (but there are a few that are very close).  

If you want to use Linux, you might find a better fit on single user PC's.

---

### Post by hyper_ch on 2008-07-15
> **Ice Dragon said:**
> I work in a professional IT environment that uses many Enterprise tools such as Deep Freeze, Symantec Ghost, Domains, Papercut, exchange servers for email and mobile devices, image deployments with sysprep, etc.. etc..
Deep Freeze --> no clue what that is
Ghost --> there are tools for it
Domains --> you're kidding? Linux offers generally way better networking services
Papercut --> no cue what that is
Exchange Server --> there are quite a few tools for it
Image deployments --> there are also tools for it
.... --> there are also tools for it

> **Ice Dragon said:**
> but its really a hack to get these things to work and most of it cant even be done.
All of it can be done and it's not really a hack to get these things working, you just don't know how because you have X years of Windows experience and roughly 0 years linux experience...

> **Ice Dragon said:**
> With Symantec Ghost Solution Suite 2.0, I can control a Lab of 40+ computers remotely from our IT office.
There are linux admins that manage several hundred machines all through the CLI ;)

> **Ice Dragon said:**
> I can power them all on, send out AI packages to install updates and new programs remotely to all 40+ at once, and then shut them down again.
Can be simply done with linux

> **Ice Dragon said:**
> I can even install images (copies of the OS) remotely on all 40 at a time, and thats just one lab of many.
PXE - no problem

As said, networking wise linux is way superior ;)

> **Ice Dragon said:**
> Now, I understand that maybe the target is home users and that is fine.
Not really... well the target for ubuntu might be... but turn off all linux servers and then try to surf the net ;) so much for targeting the "home user".

> **Ice Dragon said:**
> For home users that do not play video games on their desktops, Ubuntu may be a good choice for them over Windows. Then again, if they do play games, why wouldn't you use windows?
A lot of windows games run fine on linux... some stuff even better ;)

> **Ice Dragon said:**
> is arguably the easiest computer on the market to use for average people who don't know computers well.
A perfectly setup linux system suits everyone... how many did install OS X themselves? XP? Vista? ....

---

### Post by Het Irv on 2008-07-15
Deep Freeze is a big one... It allows an IT staff member to setup a profile and lock down the computer so that no changes can be done to it.  Without Deep Freeze, you have many more problems

---

### Post by Ice Dragon on 2008-07-15
> **hyper_ch said:**
> Deep Freeze --> no clue what that is
Ghost --> there are tools for it
Domains --> you're kidding? Linux offers generally way better networking services
Papercut --> no cue what that is
Exchange Server --> there are quite a few tools for it
Image deployments --> there are also tools for it
.... --> there are also tools for it

Hello and thanks for your reply, I do have to question some of the things you say however, because as you point out, I do not have as much linux experience as I do windows.

You claim that ghost "there are tools for it". I am not talking about cloning a drive which you can easily do with clonzilla or any other linux cloning software. Im talking about a full power console that can control any number of windows computers on a network. One that allows me to install and uninstall programs that have been previously packaged to X number of computers at a time by clicking a simple "deploy" button from my single office PC. What is the name of this tool? I would like to see if it does what im talking about.

With regard to domains, I should have specified more Active Directory, which is a great tool for managing user rights on an entire network without ever having to touch individual PCs, it can all be maintained through one server. I know linux can join active directory, but whereas in windows I just type the domain and its auto in active directory, i know linux requires pages of documentation command line commands to link up properly. Is there a tool that makes this as easy as on windows, what is the name if so, as id like to get it?

Papercut is a program that allows and disallows use of network printers to individual accounts (regardless of what computer they are logged into) based upon how much remaining credits they have. This allows people to buy printer top up cards from the front desk, and use the card on any computer to print at a cost per page.

Deep Freeze is a program that "freezes" the current state of the computer. It allows any changes you make but as soon as you reboot the computer it comes back as the original frozen state. Deep freeze essentially makes windows machines immune to viruses and spyware as a simple reboot wipes anything newly added to the machine since the last freeze out. Now it also lets you declare portions of the HD as thawed locations where data will not be lost upon reboot, this is handy for protecting the OS entirely while still allowing locations for documents and other such things.

Again if these things can be done, jsut as easily, please let me know the names of the programs for linux that can do it so I can make a case myself to those who know nothing about Ubuntu.

---

### Post by silverglade00 on 2008-07-15
> **Ice Dragon said:**
> 

With regard to domains, I should have specified more Active Directory, which is a great tool for managing user rights on an entire network without ever having to touch individual PCs, it can all be maintained through one server. I know linux can join active directory, but whereas in windows I just type the domain and its auto in active directory, i know linux requires pages of documentation command line commands to link up properly. Is there a tool that makes this as easy as on windows, what is the name if so, as id like to get it?



Likewise. [www.likewisesoftware.com](www.likewisesoftware.com)
Papercut has Mac and Linux versions. [http://www.papercut.com/products/ng/download/](http://www.papercut.com/products/ng/download/)

As does Deep Freeze... [http://www.faronics.com/html/choose.asp](http://www.faronics.com/html/choose.asp)

---

### Post by Ice Dragon on 2008-07-15
> **silverglade00 said:**
> Likewise. [www.likewisesoftware.com](www.likewisesoftware.com)
Papercut has Mac and Linux versions. [http://www.papercut.com/products/ng/download/](http://www.papercut.com/products/ng/download/)

As does Deep Freeze... [http://www.faronics.com/html/choose.asp](http://www.faronics.com/html/choose.asp)

Excellent! Thank you for that information, I swear it was not there last time I looked ><

Now how about the most important one of all, the  Symantec Ghost Solution Suite that gives my little Office all its power? If something equivalent exists for linux that will probably be all we need, assuming this likewise works as easy as it says, im reading about it now.

---

### Post by lazyart on 2008-07-15
Check Acronis TrueImage and related products for your imaging needs.

Here's a [linky]("http://www.acronis.com/enterprise/") to it's enterprise line.  Not only does it work in Linux, it's recovery disks are built on it.

Cool.  Post #1000.

---

### Post by dca on 2008-07-15
> **Ice Dragon said:**
> 

I work in a professional IT environment that uses many Enterprise tools such as Deep Freeze, Symantec Ghost, Domains, Papercut, exchange servers for email and mobile devices, image deployments with sysprep, etc.. etc..



Don't takes this the wrong way but nothing you've mentioned reminds me of a professional IT environment.
 
That's more like a high-tech environment for someone who is A+ certified, not somone who is an IBM certified infrastructure specialist or CISCO certified, or HP-UX/AIX admin, or RHCT certified, etc, etc.

---

### Post by Ice Dragon on 2008-07-15
> **dca said:**
> Don't takes this the wrong way but nothing you've mentioned reminds me of a professional IT environment.
 
That's more like a high-tech environment for someone who is A+ certified, not somone who is an IBM certified infrastructure specialist or CISCO certified, or HP-UX/AIX admin, or RHCT certified, etc, etc.

Kind of hard to not take that the "wrong way" isn't it though? I mean what other point could you be making?

I simply listed some tools in use by our IT department. No matter what tools you use, someone out there uses better ones or uses the ones you have in a better way. No matter how qualified you are, someone out there is more qualified yet. No matter how Professional of an IT environment you work in, there is an environment even greater then that.

So if you are trying to belittle my statement that I work in a professional IT environment, simply because you may be the someone I mentioned in the above paragraph, then I'm sorry but I didn't make this post with the intention of playing the "My IT Environment is more professional/bigger/better than yours" game.

With how many genius computer people there is out there, one would have to be fool hardy indeed to think they are top dog, so why bother measuring?

---

### Post by dca on 2008-07-15
No, I mean the tools you're using (outside of Exchange) are the same tools you can use when you go to a friends house and fix his XP box...  Imaging a drive, using sysprep for deploying Windows XP, etc.
 
Ubuntu in the Enterprise Environment is how you labeled the thread.  Well, in an enterprise, Ubuntu can run your MTA(s), it can serve files, it can host websites, it can do a lot of things.  It can even provide a neat replacement for Exchange in the form of Open-Xchange. Now, that's generalizing because most GNU/Linux distributions can provide the same functionality.

---

### Post by hyper_ch on 2008-07-16
> **Ice Dragon said:**
> I do not have as much linux experience as I do windows.
Over time this will change - if you want it ;)

> **Ice Dragon said:**
> Im talking about a full power console that can control any number of windows computers on a network. One that allows me to install and uninstall programs that have been previously packaged to X number of computers at a time by clicking a simple "deploy" button from my single office PC. What is the name of this tool? I would like to see if it does what im talking about.
There are different ways to achieve that... although I don't know for sure if a tool, like you describe, exists. With ssh connections into the boxes you can install anything from there. Another approach would be to setup the boxes with a cron job that regurarly runs and checks a "main" computer if it shall install anything - that way you could install various software on different computers individually... another approach would be thin-clients... tools exist, I just don't know all of them ;) I stumble accross some stuff, keep it in mind but mostly never use it... so I just know it exists ;)

> **Ice Dragon said:**
> With regard to domains, I should have specified more Active Directory, which is a great tool for managing user rights on an entire network without ever having to touch individual PCs, it can all be maintained through one server. I know linux can join active directory, but whereas in windows I just type the domain and its auto in active directory, i know linux requires pages of documentation command line commands to link up properly. Is there a tool that makes this as easy as on windows, what is the name if so, as id like to get it?
I haven't done user management on linux - especially not over a network. But if you need to type something in the command line, you can just combine those commands and make it a script... you can even make "easy" user interfaces with Zenity
( [http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/) ; [http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/) ) and I'm pretty sure there are more advanced tools also...

---

### Post by t0p on 2008-07-16
> **Ice Dragon said:**
> 
I then question, If windows is superior for Enterprise and business use (no simply accounting for Ubuntu right?), and Mac is superior for ease of use and hassle free computing at home, where does the Ubuntu desktop fit in? Is its only placement for countries where people are poor beyond belief and very under-privileged?


The Ubuntu desktop is an ideal fit for the user who believes in the ethics of Free software and disagrees with the Microsoft "ethic" of exploitation.

---

