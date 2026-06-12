---
title: "How to print from ppd file?"
date: 2011-12-23
forum: Programming Talk
---

### Post by Gurmeet Singh on 2011-12-23
Hi,

I have to develope a driver for 24 pin dot matrix printer on ubuntu.
I have only the ppd file for 24 pin DMP.
**Can i print some test data using this ppd file only?**
Can anyone post good link or step by step guide to develope complete printer driver.
I have read below links
[http://www.cups.org/documentation.php/doc-other/cupsddk.html#INSTALL](http://www.cups.org/documentation.php/doc-other/cupsddk.html#INSTALL)
[http://www.cups.org/](http://www.cups.org/)

These links providing useful information but not complete information like how to develope filters, backend, port monitor etc.
Please help.
Thanks.

---

### Post by Gurmeet Singh on 2011-12-26
Hi Experts,

Please Reply. I am still waiting for your response.

Thanks.

---

### Post by gateway67 on 2011-12-26
> **Gurmeet Singh said:**
> 
I have to develope a driver for 24 pin dot matrix printer on ubuntu.

You *have* to?  Or do you merely *want* to?

> **Gurmeet Singh said:**
> 
These links providing useful information but not complete information like how to develope filters, backend, port monitor etc.
Please help.
Thanks.
Dot-matrix printers "died" out years ago.  Would it not make more economical sense to procure a new printer?  I recently bought an HP Printer-Scanner-Copier for approximately US $25.

---

### Post by Gurmeet Singh on 2011-12-26
Thanks for your reply.

> 
You *have* to?  Or do you merely *want* to?


I am working in an organization and now this task has been assigned to me.

> 
Dot-matrix printers "died" out years ago.  Would it not make more  economical sense to procure a new printer?  I recently bought an HP  Printer-Scanner-Copier for approximately US $25.


As this is the requirement for the client. I don't know why they want to develope driver but this task has been assigned to me so i have to complete it.:confused:
Thanks.

---

### Post by nvteighen on 2011-12-26
I wonder... why did you accept a task you knew you were not capable for...

---

### Post by Gurmeet Singh on 2011-12-26
> 
I wonder... why did you accept a task you knew you were not capable for...

I agree, i am doing this first time but we do all the tasks first time in life and after practicing same kind of task, we become experts.
So, my friend i can't give this excuse to my employer.

> 
Hi,

I have to develope a driver for 24 pin dot matrix printer on ubuntu.
I have only the ppd file for 24 pin DMP.
**Can i print some test data using this ppd file only?**
Can anyone post good link or step by step guide to develope complete printer driver.
I have read below links
[http://www.cups.org/documentation.ph...k.html#INSTALL]("http://www.cups.org/documentation.php/doc-other/cupsddk.html#INSTALL")
[http://www.cups.org/](http://www.cups.org/)

These links providing useful information but not complete information like how to develope filters, backend, port monitor etc.
Please help.


Please help me if anyone can:confused:
Thanks in advance.

---

### Post by Zugzwang on 2011-12-26
Where does the PPD file come from? Is is possibly already a CUPS PPD file? If it is, you are already done - you *have* your printer driver then. Or is it supplied with Windows and a Windows PPD file? See: [http://en.wikipedia.org/wiki/PostScript_Printer_Description](http://en.wikipedia.org/wiki/PostScript_Printer_Description)

---

### Post by nvteighen on 2011-12-26
> **Gurmeet Singh said:**
> I agree, i am doing this first time but we do all the tasks first time in life and after practicing same kind of task, we become experts.


Of course we aren't born as experts and of course there's always a first time in everything.

I don't have a clue on how to write a driver, but I more-or-less know the degree of difficulty it has and what kind of programming it is about. I know I'd have to read and understand the hardware specs of the device... or reverse-engineer the interface if those specs no longer available... I know it will require me to really understand how the OS communicates with hardware in general (e.g. HAL)... I know it will require some ASM and very nasty low-level programming... So, I know I'm not the guy to do that and I know that I wouldn't be able to learn all the required stuff in a reasonable time up to a level that would allow me to write me a reliable driver that's usable in a working environment.

Programmers have to have a more-or-less global picture of the different kinds of programming there are. You get this after several years trying out stuff and learning, and I don't consider myself an expert; I'm not even a decent programmer.

If you accepted such a task and then you come up to a web forum like this one asking such general questions, then all I can think is that you don't know your own skills. It'd be a completely different story if you had come here asking for a precise problem, showing some code or a dump core, etc.

However, if you just don't know or haven't tried the CUPS-way, then it's even worse... then you don't even know your OS.

Sorry for this moralistic rant, but I'm really tired of this kind of threads.

---

### Post by Gurmeet Singh on 2011-12-27
> 
Where does the PPD file come from? Is is possibly already a CUPS PPD file? If it is, you are already done - you *have* your printer driver then. Or is it supplied with Windows and a Windows PPD file? 


Its a CUPS ppd. I am trying to print some data as i have read from [http://www.cups.org/](http://www.cups.org/).
Can you please give me any link or information to print using this ppd.
Thanks for your kind response.

> 
Of course we aren't born as experts and of course there's always a first time in everything.

I don't have a clue on how to write a driver, but I more-or-less know  the degree of difficulty it has and what kind of programming it is  about. I know I'd have to read and understand the hardware specs of the  device... or reverse-engineer the interface if those specs no longer  available... I know it will require me to really understand how the OS  communicates with hardware in general (e.g. HAL)... I know it will  require some ASM and very nasty low-level programming... So, I know I'm  not the guy to do that and I know that I wouldn't be able to learn all  the required stuff in a reasonable time up to a level that would allow  me to write me a reliable driver that's usable in a working environment.

Programmers have to have a more-or-less global picture of the different  kinds of programming there are. You get this after several years trying  out stuff and learning, and I don't consider myself an expert; I'm not  even a decent programmer.

If you accepted such a task and then you come up to a web forum like  this one asking such general questions, then all I can think is that you  don't know your own skills. It'd be a completely different story if you  had come here asking for a precise problem, showing some code or a dump  core, etc.

However, if you just don't know or haven't tried the CUPS-way, then it's even worse... then you don't even know your OS.

Sorry for this moralistic rant, but I'm really tired of this kind of threads.


[]("http://ubuntuforums.org/member.php?u=273037")Hi Nvteighen,
Actually i have 1.5 years of experience in VC++ programming on windows environment. I have worked on OPOS driver and some port communication on windows. This is my first time on Ubuntu. So i was confused how to start with?
Thanks:)

---

### Post by Gurmeet Singh on 2011-12-27
Hi Experts,

Now I am able to print from the ppd file but the speed of printing is slow.
What i need to do to increase the speed of printing?
Thanks:)

---

### Post by Zugzwang on 2011-12-29
> **Gurmeet Singh said:**
> Hi Experts,

Now I am able to print from the ppd file but the speed of printing is slow.
What i need to do to increase the speed of printing?
Thanks:)

I would suggest that you try to consult the CUPS manual on this issue or post the question to a different board in the Ubuntu Forums - It is no longer a programming question.

By the way, if you had a CUPS PPD file for your printer, you already *had* a driver. Why were you asking then for help in developing a driver? You leave us a bit confused here.

---

