---
title: "[SOLVED] Help here please :)"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by ALex! on 2008-07-12
Hi everybody! I have a laptop and want to install Ubuntu in it... It has an Intel Centrino Duo processor, but my Vista install is a 32 bit one. I was wondering which Ubuntu version should I use, wether the 32 bit one or the 64 bit one...

Thanks in advance!!!

---

### Post by hyper_ch on 2008-07-12
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by meindian523 on 2008-07-12
Well,32 bit is always safe,because atleast I couldn't find any documentation which showed whether the Centrino Duo supports Intel EM64T which supports both 32 and 64-bit.

---

### Post by ibizatunes on 2008-07-12
Go with the x64 bit, its faster (not by much but still quicker) x32 used to be a more stable system (in 7.04 and 7.10), due to problems with flash in Firefox, but with Firefox 3 that isnt a problem any more! 8.04 x64 is really good!!

x64 is going to become more and more common over the coming years!
 
U cant chop and change from x64 to x32 without a rebuilt of your OS, so go with x64, its the future! 
And you want maximum performance from your PC dont you?

---

### Post by ALex! on 2008-07-12
> **hyper_ch said:**
> it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

ok ok sorry... this won't happen any more.... but now I can't edit my topic title!

> **hyper_ch said:**
> and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved
I only have ONE problem!:???: which version?! :confused:

---

### Post by ALex! on 2008-07-12
> **ibizatunes said:**
> Go with the x64 bit, its faster (not by much but still quicker) x32 used to be a more stable system (in 7.04 and 7.10), due to problems with flash in Firefox, but with Firefox 3 that isnt a problem any more! 8.04 x64 is really good!!

x64 is going to become more and more common over the coming years!
 
U cant chop and change from x64 to x32 without a rebuilt of your OS, so go with x64, its the future! 
And you want maximum performance from your PC dont you?

that means the x64 bit version makes use of both cores?!

---

### Post by ALex! on 2008-07-12
I've read that 64 bit OS's have some hardware and/or software compatibility problems... Is this true in any way???

---

### Post by meindian523 on 2008-07-12
> **ALex! said:**
> that means the x64 bit version makes use of both cores?!
64 bit doesn't have anything to with the number of cores.

> **ALex! said:**
> I've read that 64 bit OS's have some hardware and/or software compatibility problems... Is this true in any way???

Yes,hardware,if your hardware doesn't support 64 bit.As I mentioned earlier,I've found no mention that Intel Centrino Duo supports EM64T.I'm still looking for people who know more about this processor,and don't blindly recommend 64 bit to give their inputs here,though.

Software side,pretty much everything has been ironed out.The problems you have heard about were primarily Flash,etc.Nothing you can't live without.

---

### Post by ALex! on 2008-07-12
> **meindian523 said:**
> 64 bit doesn't have anything to with the number of cores.



Yes,hardware,if your hardware doesn't support 64 bit.As I mentioned earlier,I've found no mention that Intel Centrino Duo supports EM64T.I'm still looking for people who know more about this processor,and don't blindly recommend 64 bit to give their inputs here,though.

Software side,pretty much everything has been ironed out.The problems you have heard about were primarily Flash,etc.Nothing you can't live without.

oh! so you think sticking to x86 is my best bet?!

---

### Post by meindian523 on 2008-07-12
It's safer.I'm erring on the side of caution.And in case you find out later that your box supports 64 bit,you can overwrite your / partition with the 64 bit CD install,assuming you create a separate partition for /home.But,you won't be able to install any packages you installed on your 32 bit box before you realized it could support 64 bit on your new 64 bit system.That will also include all the updates you installed.

Look [here]("http://en.wikipedia.org/wiki/Intel_Centrino_Duo#Centrino_Brand_Names_Updated") and tell me whether your sticker is from the Napa or Snata Rosa family.

---

### Post by ALex! on 2008-07-12
> **meindian523 said:**
> It's safer.I'm erring on the side of caution.And in case you find out later that your box supports 64 bit,you can overwrite your / partition with the 64 bit CD install,assuming you create a separate partition for /home.But,you won't be able to install any packages you installed on your 32 bit box before you realized it could support 64 bit on your new 64 bit system.That will also include all the updates you installed.

Look [here]("http://en.wikipedia.org/wiki/Intel_Centrino_Duo#Centrino_Brand_Names_Updated") and tell me whether your sticker is from the Napa or Snata Rosa family.

it's a napa intel centrino duo

---

### Post by meindian523 on 2008-07-12
Probably not 64-bit.Look here:
5th comment on [http://softwareblogs.intel.com/2006/09/20/64-bit-and-intel/](http://softwareblogs.intel.com/2006/09/20/64-bit-and-intel/)
The FIRST Core Duo,which is the Napa,I believe, was pure 32 bit according to the research conducted by the guy who wrote that comment.

---

### Post by tone33 on 2008-07-12
you might want to check out this little program to tell you more about your cpu.  [http://www.grc.com/securable.htm](http://www.grc.com/securable.htm).

---

### Post by meindian523 on 2008-07-13
The code was wrong.

---

### Post by meindian523 on 2008-07-15
I found the code!
```
sudo lshw -C cpu|grep width
``` if it is 64 bits,you can use a 64 bit OS.BTW,why did you mark the thread solved?What did you install?It's good Netiquette to come back and tell people who advised you as how your problem was solved.Comes in use for other people searching the web for similar questions.

---

