---
title: "Basic Programming Question!"
date: 2009-06-24
forum: Programming Talk
---

### Post by Toshibawarrior on 2009-06-24
Hi guys, I was looking at some IDEs today and I found out about Gambas2...It's a very nice and easy to use program, but I was wondering, and I hope someone can help me out.

How do I make widgets (buttons, textboxes, labels...) expand along with the rest of the window/form?

For example: If I resize a window I want all my widgets to expand and not just sit in the middle or left side of the window, I want them to stay proportionate with the whole window. So how do I achieve this?...

I'm a programming-noob, but I really want to learn.

I know that this may be the wrong place to ask, but I had no other choice. Sorry...

Anyway, I hope someone can help me out!

Thanks in advance!

---

### Post by Bachstelze on 2009-06-24
Moved to Programming Talk.

---

### Post by RobOrr on 2009-06-24
In terms of other choices, there's a programming forum in ubuntu forums matey, you're more likely to get useful help in there. It's supposedly similar to Visual Basic, so if you can't find assistance specific to gambas it would be worth having a look at VB so you can get to grips with things.

[www.gambasdoc.org/help/doc/start?en&view]("http://www.gambasdocs.org") seems to have plenty of documentation but I cannot currently access the site, it may be down.

---

### Post by Toshibawarrior on 2009-06-25
Well I used to write up very basic VB programs back in Windoze, but in VB the widgets had a "lock" property that made them stick to a certain part of a windows or panel and expand along with that windows or panel. Here in Gambas I haven't found such a property and I don't know if this can be made with certain code or something.

Thanks for the reply!

---

### Post by kalaharix on 2009-06-25
Hi,

Have a look at the TextEdit example under examples where TextEdit1.expand=true

rgds

---

### Post by Toshibawarrior on 2009-06-25
Hi, I've set the "Expand" property (on the properties window) for each label, button and textbox to True, but still they won't expand, now they just get stuck on middle-left side of the form....and when I expand the window there's just a big empty space on the right side.

I still haven't found the piece of code you mentioned. :(

---

### Post by kalaharix on 2009-06-25
Hi

Have you set FMain(or whatever).arrangement to something other than 'none'. That sets how the container arranges its children.

File, Open example, Controls, TextEdit. It might say it is read-only so just file, save as.. to your directory first.

rgds

---

### Post by Toshibawarrior on 2009-06-25
Hi again,

I made some improvement...I tried the "alignment" property you suggested and set it to "Fill" and I can expand whatever is directly on top the form. In my case I made a practice GUI without any code or functionality and I used a Frame with a button inside of it and a button on the form (outside the frame) and the button literally fills the whole form, so I deleted it and I can see now that the frame is autoexpanding along with the window/form, but everything inside the frame stays the same... What can I do now?

---

### Post by pokerbirch on 2009-06-25
I used Gambas for a while when i first started using Linux about a year ago because i had always used VB6 for Windows programming. Gambas is nice but i found that a lot of the components were very simplified. For instance, i needed to use the Curl component but found that it was lacking most of the features that i needed.

I'm now using Python for all my programming. I found the [Gambas Forum]("http://www.nabble.com/Gambas-f3425.html") useful and the Gambas developer Benoît Minisini can often be found there.

---

### Post by Toshibawarrior on 2009-06-25
Hmmm...I give up...I've spent two days fiddling with Gambas and I still don't know how to do this. Sadly I'm going back to VB (although I believe it's far more complete) but I have a very big question...

Is there any way to program in VB and convert it to Linux?...

I read something about a vb2gb script that converts VB projects to Gambas and then you can supposedly convert your application to run on Linux...but I wonder...is it really true? or, Do I have to learn C or Python to program for Linux OSes?

Thanks for all the help! I'm eagerly waiting for your replies! :popcorn:

---

### Post by Mirge on 2009-06-25
Try using wine to run your apps in Linux.

---

### Post by Toshibawarrior on 2009-06-25
Yeah, I like Wine, but I kinda wished for a Linux-native app...Oh well...I guess I'll keep searching. Thanks!

---

### Post by Mirge on 2009-06-25
You could try learning a cross-platform GUI library like Qt4 or GTK...

---

### Post by Toshibawarrior on 2009-06-25
I was thinking the same thing myself! I don't have lots of time on my hands, but I think I'll start learning GTK...

I love programming, but I don't know basically anything about it...just some really basic VB. Even Python is hard for me. Anyway, thanks again!

---

### Post by Can+~ on 2009-06-25
> **Toshibawarrior said:**
> I was thinking the same thing myself! I don't have lots of time on my hands, but I think I'll start learning GTK...

I love programming, but I don't know basically anything about it...just some really basic VB. Even Python is hard for me. Anyway, thanks again!

Don't expect to build graphical applications with 0 knowledge on a programming language, that's why one of the reasons that students are taught how to do console stuff only and later they can learn how to pair it with a Toolkit.

I get the feeling that you're trying to rush everything, start with python and take your time, don't go through the manual and say "this is hard".

---

### Post by Mirge on 2009-06-25
> **Can+~ said:**
> Don't expect to build graphical applications with 0 knowledge on a programming language, that's why one of the reasons that students are taught how to do console stuff only and later they can learn how to pair it with a Toolkit.

I get the feeling that you're trying to rush everything, start with python and take your time, don't go through the manual and say "this is hard".

Agreed. Walk before you run. You'll be glad you did later (instead of throwing your programming book out the window).

---

### Post by Toshibawarrior on 2009-06-25
> **Can+~ said:**
> Don't expect to build graphical applications with 0 knowledge on a programming language, that's why one of the reasons that students are taught how to do console stuff only and later they can learn how to pair it with a Toolkit.

I get the feeling that you're trying to rush everything, start with python and take your time, don't go through the manual and say "this is hard".

Ummm...kinda...I always rush things...and that's a very bad habit.

So should I start with Python?...

I've read tons of books, manuals, wikis, blogs, aboiut C, VB, Python, C++, HTML...etc, and I draw a blank every time...It confuses me...

---

### Post by Can+~ on 2009-06-25
> **Toshibawarrior said:**
> Ummm...kinda...I always rush things...and that's a very bad habit.

So should I start with Python?...

I've read tons of books, manuals, wikis, blogs, aboiut C, VB, Python, C++, HTML...etc, and I draw a blank every time...It confuses me...

Reading doesn't mean that the knowledge stays in one place. First time programmers learn by doing.

Seriously, grab the tutorial and try to emulate the examples, modify them, play with them. It's all about getting used to your tools.

---

### Post by Toshibawarrior on 2009-06-25
> **Can+~ said:**
> Reading doesn't mean that the knowledge stays in one place. First time programmers learn by doing.

Seriously, grab the tutorial and try to emulate the examples, modify them, play with them. It's all about getting used to your tools.

Hmm...I'll try to take it slow then...I'll learn some Python and read more about VB and Gambas...oh well, I'll let you guys know how it goes!

---

### Post by kalaharix on 2009-06-26
Hi,

'You could try learning a cross-platform GUI library like Qt4 or GTK...'

So what do you think Gambas uses then?

The problems ToshibaWarrior is having are almost certainly due to QT3 or GTK (it is a choice in Gambas) and not Gambas itself.

Container-based programming is tricky. It is exactly the same in Glade.

One step at a time.

rgds

---

### Post by Mirge on 2009-06-26
> **kalaharix said:**
> Hi,

'You could try learning a cross-platform GUI library like Qt4 or GTK...'

So what do you think Gambas uses then?

The problems ToshibaWarrior is having are almost certainly due to QT3 or GTK (it is a choice in Gambas) and not Gambas itself.

Container-based programming is tricky. It is exactly the same in Glade.

One step at a time.

rgds

I guess you didn't realize that I posted that BEFORE he said he knew nothing about programming.

---

### Post by kalaharix on 2009-06-26
Hi

Oops! Grovel Grovel:oops:.

I don't know a lot about container based programming so I thought I would use the opportunity to brush up a bit. 

The problem is not with QT or GTK but with Gambas. From an old post by the creator (Gambas I mean:)) in the Gambas forum: 'The Frame control is the only container that does not arrange its contents at all. Maybe it was not a good idea... '. Messing around I think that applies to the panel and tabstrip containers as well.

There is an easy workaround offered by another user which I have tested. Put a second container (I used an hBox) within the frame and then your controls in that. Position it at the top left of the frame and use an event to control the hBox within the frame like this:

PUBLIC SUB Form_Resize()
  HBox4.width = Frame2.Width - 10
  HBox4.Height = Frame2.Height - 20
END

Hope that helps.

A common argument on this forum is that it is a good thing to seperate the gui design from the program design. That may be right for some but definitely not for me. The logic, for example, in a point-of-sale program is relatively light. The complexity (probably 80% of the code) comes from all the weird things that the end-user will try an do with the program. A programming language that does not tightly integrate the gui with the logic does not help me at all and that is why Gambas is a much better choice FOR ME than other fine languages such as Python.

rgds

---

### Post by Toshibawarrior on 2009-06-26
> **kalaharix said:**
> Hi

Oops! Grovel Grovel:oops:.

I don't know a lot about container based programming so I thought I would use the opportunity to brush up a bit. 

The problem is not with QT or GTK but with Gambas. From an old post by the creator (Gambas I mean:)) in the Gambas forum: 'The Frame control is the only container that does not arrange its contents at all. Maybe it was not a good idea... '. Messing around I think that applies to the panel and tabstrip containers as well.

There is an easy workaround offered by another user which I have tested. Put a second container (I used an hBox) within the frame and then your controls in that. Position it at the top left of the frame and use an event to control the hBox within the frame like this:

PUBLIC SUB Form_Resize()
  HBox4.width = Frame2.Width - 10
  HBox4.Height = Frame2.Height - 20
END

Hope that helps.

A common argument on this forum is that it is a good thing to seperate the gui design from the program design. That may be right for some but definitely not for me. The logic, for example, in a point-of-sale program is relatively light. The complexity (probably 80% of the code) comes from all the weird things that the end-user will try an do with the program. A programming language that does not tightly integrate the gui with the logic does not help me at all and that is why Gambas is a much better choice FOR ME than other fine languages such as Python.

rgds

Well, it gave a good idea about how to do it...but sadly I still don't get it right here on Gambas. last night I fired up Visual Basic and I go a test app running and expanding in 10 minutes (like I used to before when I played around with VB) and in Gambas it's still a mess...So I guess I just have to go back to VB and learn a little more of it. I tried Python again last night and I guess I could give it a shot...once I find a good tutorial about how to get started,

Thanks!

---

