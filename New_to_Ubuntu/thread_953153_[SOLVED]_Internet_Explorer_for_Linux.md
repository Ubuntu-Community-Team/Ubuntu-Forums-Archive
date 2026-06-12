---
title: "[SOLVED] Internet Explorer for Linux"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Georgia boy on 2008-10-19
Hi. Hate to ask this but I'm tired of switching to Windows each time I need to do some classes for work. I have tried to open up in Firefox but for some reason some of the things don't seem to work there. I wind up going to the Windows and using Internet Explorer to do the classes. Is there an Internet Explorer add-on that I can use instead of having to do all of that? 

Wait a minuter, didn't Physcocat have something one time about being able to install Internet Explorer in Ubuntu? How did that go?

By the way it's a company site where I have to do a log in and do the classes or whatever;

 Went to the add-ons in Firefox but probably overlooked what I'm needing.

All advice greatly appreciated.

Thanks
Tom

---

### Post by ItecKid on 2008-10-19
There's an add-on for firefox that lets you emulate IE, give me a sec and I'll see if I can find it...

---

### Post by eternalnewbee on 2008-10-19
> **Georgia boy said:**
> Hi. Hate to ask this but I'm tired of switching to Windows each time I need to do some classes for work. I have tried to open up in Firefox but for some reason some of the things don't seem to work there. I wind up going to the Windows and using Internet Explorer to do the classes. Is there an Internet Explorer add-on that I can use instead of having to do all of that? 

Wait a minuter, didn't Physcocat have something one time about being able to install Internet Explorer in Ubuntu? How did that go?

By the way it's a company site where I have to do a log in and do the classes or whatever;

 Went to the add-ons in Firefox but probably overlooked what I'm needing.

All advice greatly appreciated.

Thanks
Tom

Hi there.
What does work in IE that doesn't in FF?
Btw, I use Swiftweasel...

---

### Post by kostkon on 2008-10-19
[*IEs4Linux*]("http://www.tatanka.com.br/ies4linux/") is the thing you are looking for.

Install *Wine* and *cabextract* before running the *IEs4Linux* script.

---

### Post by Georgia boy on 2008-10-19
It's wanting a GCJ browser plug-in installed now. So, don't know what that is. 

Is wine hard to install and use? I've just started on Ubuntu and have the dual boot with Windows XP. 

I also recall reading something that Pysco cat wrote about installing IE in Ubuntu. Anyone recall reading that besides me? Anything to that?

Thanks
Tom

---

### Post by kostkon on 2008-10-19
> **Georgia boy said:**
> It's wanting a GCJ browser plug-in installed now. So, don't know what that is. 

Is wine hard to install and use? I've just started on Ubuntu and have the dual boot with Windows XP. 

I also recall reading something that Pysco cat wrote about installing IE in Ubuntu. Anyone recall reading that besides me? Anything to that?

Thanks
Tom
Do you mean [this]("http://www.psychocats.net/ubuntu/ies4linux")?

---

### Post by jerrynewt on 2008-10-19
Have you tried the User Agent Switcher add on for firefox. Seems to work great for me so far.

---

### Post by kurtis2772 on 2008-10-20
> **kostkon said:**
> Do you mean [this]("http://www.psychocats.net/ubuntu/ies4linux")?

Kostkon,

Thanks so much for that link. Really easy to follow. Managed to get IE working. Didn't fix my problem, as I require Java version 5 update 16 for Windows........

Seriously though, was a great help. Cheers!!

---

### Post by desperado665 on 2008-10-20
> **jerrynewt said:**
> Have you tried the User Agent Switcher add on for firefox. Seems to work great for me so far.

I agree. I use that same FF plugin and it works flawlessly. For some silly reason, my bank won't let me do online banking without windows and IE. User Agent Switcher saved me from having to resort to a dual boot situation.

---

### Post by Georgia boy on 2008-10-20
Thanks for the link koskon! I booked marked it in case I decide to use it. Also thanks jerrynewt and desperado for the suggestions of the add-on for the User Agent Switcher. Exactly how does that add-on work? The description lacks a lot as to how to use it. 

Any idea what the GCJ plug in is about? Some kind of Java? I use Add Block Plus and NoScript. I tell the NoScript to allow for that site but for some reason I also get that it needs additional plug ins. There are a list of them besides that one. Open JDK is one of them. I'm going to try it again and select that one. Can't figure why it would also want the plug in when I'm using the open java.

Thanks for all of the advice given. Really appreciate each comment.:)

Went back to that site. Seems to want the java even though I am using open JDK. I clicked on installing the GCJ(open JDK) and it installed the icetea. But I notice that each time I get out of it and go back it says to install the plug in. So I click on it and of course I'm told that the Icetea is installed. So I click finish and it works. Guess it has to be fooled or something. Don't know what to think. As long as it works. 

But still would like to know about the User Agent Switcher add-on though as to how it works and how to use it.

Again, thanks for all of the help that you have been giving me. I know, dumb questions but what can I say?

Tom

---

### Post by desperado665 on 2008-10-20
Georgia Boy,

I had a few similar problems with Java that made want to tear my hair out.. Until I found a program called Ubuntu Tweak. I don't think it's available from the repositories, but if you google it, it should be easy enough to find. Once Ubuntu Tweak is installed, choose the ubuntu restricted extras for installation and your java headaches should be over.

As far as using User Agent Switcher, once FF is open you should find the agent listed in your tools menu. It's as easy as choosing Internet Explorer 7 (Windows Vista) and FF will spoof it.

Also, the only dumb question is the one that goes unasked...

---

### Post by fluxlizard on 2008-10-20
One other tip for future reference for you guys.

Some sites use shockwave or some such and don't normally work under linux. If you install the latest firefox under wine, you can use that for those situations. It would be a dirty fix for this case, but it would work- it would grab and install windows version of flash for your wine firefox.

---

### Post by Georgia boy on 2008-10-20
Interesting about the shock wave. So far I'm good. Using the Open JDK for java and also use flash. Will keep this in mind and bookmark for future references. Thanks fluxlizard for that thought. 

Desperado, thanks for the Ubuntu Tweak. Java had been working good for so long, don't know why all of a sudden that one part of the site wanted a plug-in. I have the Open JDK from the repositories. But for some reason it also wanted the plug-in added. When I did you can see from the previous post what happens. Oh well, as long as it works right? I really appreciate all of the help that I have been getting from this forum. A great bunch of people here always willing to help. I know that I ask some dumb questions at times but they are something that I need to know. And so far I have never been slammed. I have seen in some forums where the person asking a question got slammed big time. But I have always been very lucky so far.

Again, thank all of you for you great help and advice. People like you make it an enjoyable experience to come and learn from the forums. Believe me, I always search the forum before asking. I learn a lot from reading what is already here on the different thread topics but also when I ask questions and get great responses.

Thanks
Tom

---

### Post by dlmoak on 2008-10-20
There are some company websites for which none of the above suggestions work.  In that case, you have to install Windows on a virtual machine to use those sites.

---

### Post by Yuki_Nagato on 2008-10-20
Opera, which is in the repositories, has the ability to mask the browser as either Firefox or Internet Explorer.  This works on a site by site preference.

It is a version behind, (9.52, the current is 9.60) but is an awesome browser.

---

### Post by estyles on 2008-10-20
Georgia Boy, you don't have to thank every person that posts in your thread.  Something like, "I think there's a way for Firefox to emulate IE, but I don't have the link," doesn't really need to be thanked.  It kinda defeats the purpose of thanking...  :)

---

### Post by Georgia boy on 2008-10-21
Thanks everyone!! Seems like it might have wanted a plug-in on the Firefox for the java for some reason. So, we'll see what happens from there.

Again, thanks for all the help.
Tom

---

### Post by gandaran on 2008-10-21
> Any idea what the GCJ plug in is about
GCJ plugin is the open-java plugin for firefox and that seems to be your problem, no java installed!
if you running ubuntu 32-bits use sun-java, just install the sun-java6-plugin
for 64-bits you have to use the GCJ plugin, no sun java plugin available

---

