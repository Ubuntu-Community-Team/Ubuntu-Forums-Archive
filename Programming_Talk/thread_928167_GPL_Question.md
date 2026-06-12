---
title: "GPL Question"
date: 2008-09-23
forum: Programming Talk
---

### Post by dark joev on 2008-09-23
I have read the GPL but I don't understand it and I am interested in using it in my commercial games but I have some questions.

Would using the GPL allow competiters to steal my game?

What protections does the GPL offer?

I want to make sure that I am using the right license so that I know what it allows and doesn't.

---

### Post by OutOfReach on 2008-09-23
> **dark joev said:**
> I have read the GPL but I don't understand it and I am interested in using it in my commercial games but I have some questions.

Would using the GPL allow competiters to steal my game?

What protections does the GPL offer?

I want to make sure that I am using the right license so that I know what it allows and doesn't.

Depends on your definition of 'steal' if you mean other people using your code in theirs, as far as I know the GPL allows other people to fork your code and use it in their own projects (While keeping it open source).

---

### Post by LaRoza on 2008-09-23
> **dark joev said:**
> I have read the GPL but I don't understand it and I am interested in using it in my commercial games but I have some questions.

Would using the GPL allow competiters to steal my game?

What protections does the GPL offer?

I want to make sure that I am using the right license so that I know what it allows and doesn't.

I am not a lawyer.

The GPL allows people to get the source code to the application and modify it and release it under the same license. So, I made sysres under the GPL. Anyone can use and modify and release that code; hey can even sell it, but they have to use the same license (basically, they have to grant the same rights they were given.)

As for stealing, stealing is usually illegal and that hasn't stopped everyone. So yes, a company could steal it. If you are asking if it is legal to steal it, no, otherwise, it wouldn't be stealing.

The GPL is enforcable. You could sue (as I believe this would be handled in civil courts for most things) for violations of it.

I am not a lawyer, and going by US law, in Pennsylvania specifically.

---

### Post by dark joev on 2008-09-23
By steal I meand like taking my whole game and then just changing its namd and putting it back out on the market or do I still own the copyright to the actual product.

---

### Post by Kadrus on 2008-09-23
I believe there are some licenses where the people who receive your code and would like to use it have to give you credit for your work if that's what you're looking for.

---

### Post by dark joev on 2008-09-23
Yeah, I am just wondering if I could use the GPL I have a way of making money without having to charge the person wanting my product. My file host will pay me.

---

### Post by Kadrus on 2008-09-23
Take a look at different licences and the comparaison,and you can choose the one that fits you best.
[http://en.wikipedia.org/wiki/Comparison_of_free_software_licences](http://en.wikipedia.org/wiki/Comparison_of_free_software_licences)

---

### Post by LaRoza on 2008-09-23
> **dark joev said:**
> By steal I meand like taking my whole game and then just changing its namd and putting it back out on the market or do I still own the copyright to the actual product.

Like I said, one can sell GPL applications. Their version would have to have the GPL also and you'd be creditted. You wouldn't expect any money from it.

You can write your own license, or use a more restrictive license if you want.

---

### Post by Kadrus on 2008-09-23
Xandros is a commerical OS,and I believe it uses GPL.

---

### Post by Tomosaur on 2008-09-23
The GPL applies to the source code only.

Data files - sound files, images, 3D models, story scripts / dialog stuff (provided the script isn't hard-coded into the code itself - many small games still do this, which is fine most of the time but makes translation and modification difficult) can all be covered under a different license which forbids copying, modifying or rebranding etc.

Doing this means people are still able to modify your code and create their own version, but to create a working version of the game they would need to create their own sound files, images, models and dialog stuff. This is likely to discourage anybody but the most determined from altering and selling your game.

The GPL is a philosophical license as well as a legally binding one. If you don't want people to copy your game, then you should use a different license.

Basically, using the GPL allows people to copy, modify and sell (if they wish) your program's **code**. Unless you explicitly state, most people will assume the software is a normal GPLd program (ie: the creator doesn't really mind what you do with it so long as you don't try to restrict the software's usage if you make it available elsewhere). If you want the code GPLd but the data files under a restrictive licence, then you should make people aware of this yourself - do not just assume people will check out whether the license covers everything or just the code. If you don't make a full attempt to do this, then any violation of your license(s) you choose to sue over may well be thrown out of court. It's the same general idea as trademark infringement - if the company has made no obvious effort to protect their trademark, then the court won't attempt to uphold the company's claims.

---

### Post by Bios Element on 2008-09-23
Tomosaur is right. To simplify that a little, It's basically this simple. *I'm Not a lawyer*

1. GPL applies to source code
2. Graphics, Sound, Story ETC of a GPL game can be copyright
3. Name of a product for a GPL Program can also be copyright

So basically, The engine could be used by someone else but they'd have to remake all the actual 'content'.

---

### Post by slavik on 2008-09-23
> **Tomosaur said:**
> The GPL applies to the source code only.

Data files - sound files, images, 3D models, story scripts / dialog stuff (provided the script isn't hard-coded into the code itself - many small games still do this, which is fine most of the time but makes translation and modification difficult) can all be covered under a different license which forbids copying, modifying or rebranding etc.

Doing this means people are still able to modify your code and create their own version, but to create a working version of the game they would need to create their own sound files, images, models and dialog stuff. This is likely to discourage anybody but the most determined from altering and selling your game.


A very good example of this is OpenArena. They took Quake3Arena code (which was released under GPL), created their own maps, models, sounds, etc. and released OpenArena. Q3A models and such are not free as in speech (or beer).

---

### Post by pmasiar on 2008-09-23
GPL allows you to incorporate any cede released under GPL into yours, and requires you do the same - or anyone who wants to use your code. Company can 'steal' your code and use/change it without releasing it (ie to prevent you to include their changes in your code), but if you find out, you ca sue them, and win (releasing the code and maybe some penalties). But anyone can use/copy/modify your code, with only one condition: any changes has to be made public.

To protect your 'brand' you can use other legal protection, separate from copyrigh: trademark. Like Firefox places restrictions on Linux distros who want to use Firefox name and graphic: so debian swithed from FF to 'IceWeasel' :-)

---

### Post by sloggerkhan on 2008-09-23
One way to do this is to keep game engine and such code under a differente license than artistic content.

---

### Post by dark joev on 2008-09-25
Ok thank you all I will look into other licenses.

---

### Post by Tomosaur on 2008-09-25
> **dark joev said:**
> Ok thank you all I will look into other licenses.

What is it you want to accomplish? If you don't want to allow people to copy your game, but want people to contribute to its development - then you're going to get people copying it anyway. Developers need to be able to compile a working version of the game in order to test, so they will all have copies of the code.

I'm kind of struggling to understand why you want to use the GPL for a game you don't want people to copy. Seems like a conflict of interest.

---

### Post by nvteighen on 2008-09-25
Also not a lawyer, but having a little bit of laws background.

GPL gives permission to redistribute copies, with or without modifications if and only if attribution is preserved, the resulting product also is released under GPL and you make all efforts to let people be able to exercise their rights (this has been improved a lot in GPLv3).

If you want the name be protected, the Mozilla-case is the way to go. But be aware that in Free Software, that's usually not done. For example, the OpenOffice.org you get from Ubuntu is not the "official build" (I don't know what the changes are, but look at the "About" box), but retains its name and those guys have no problem with that, because the "OpenOffice.org" product, as Tomosaur correctly stated, is not the application but the code. I may build some random program using code from OpenOffice.org and retain the name and they won't complain, because they haven't trademarked it... (but that's not copyright law, therefore GPL is not appliable). Mozilla, instead, could complain and they indeed have complained in the past to Debian... and Ubuntu saved itself using the "Ubufox" extension as a way to pass changes to the distro's Firefox without having to rebrand it.

---

### Post by dark joev on 2008-09-25
Ok... So does that mean I could release the game engine as open source and keep the game in a closed source form and use a more restrictive license.

---

### Post by Tomosaur on 2008-09-26
> **dark joev said:**
> Ok... So does that mean I could release the game engine as open source and keep the game in a closed source form and use a more restrictive license.

If you develop a program which is a derivative of a GPL program, then you would need to release your program under the GPL too. I'm not entirely sure whether games which use GPLd game engines are considered derivatives. I have a hunch that provided it is done 'properly' - ie: you don't confuse your game code (story, levels and such) with the code for the game engine, then you would be able to release your game under a different licence. However, I'm not an expert on GPL issues - you would be much better reading through the info here: [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) and checking whether you'd be ok. The GPL is notorious for being misunderstood and misinterpreted so there are a LOT of FAQs and info out there for your kind of question.

---

### Post by nvteighen on 2008-09-26
> **Tomosaur said:**
> If you develop a program which is a derivative of a GPL program, then you would need to release your program under the GPL too.

Except if you create a derivative from code that's yours, because you're the copyright holder and therefore, you can relicence your code however you like. (You can't violate your own copyright).

> I'm not entirely sure whether games which use GPLd game engines are considered derivatives.

That's a hard nut. What constitutes a "derivative work" is usually defined by national laws, so there might very subtle differences between countries. Check with a lawyer.

What it's sure is that if your code in a country happens to be considered "derivative work" of a GPL'ed program, then it has to be GPL'ed. IIRC, in USA and Europe, linking to libraries is considered to form derivative works... that's why some standard libraries usually use LGPL, so they can be linked to by proprietary software. So, if your game engine is GPL'ed, any program written to work with that engine will have to be GPL'ed, except if it's yours.

---

### Post by Tomosaur on 2008-09-26
> **nvteighen said:**
> Except if you create a derivative from code that's yours, because you're the copyright holder and therefore, you can relicence your code however you like. (You can't violate your own copyright).


Yeah, I was thinking more in general terms - you can use your own code however you like. UNLESS of course, your game engine relies on other GPL libraries, in which case you're back to square one :P

---

### Post by elbarto_87 on 2008-09-27
This is an interesting topic. I have been wondering a similar thing with a program I have been working on. If I develop a program in python using a GPL IDE and useing the python libraries like scipy etc then does this mean that I have no option but to release my program under a GPL if I wanted to sell my work?

I do not know what constitutes something "deriving" from a GPL program as apposed to something being created by implementing GPL programs.

---

### Post by nvteighen on 2008-09-27
> **elbarto_87 said:**
> This is an interesting topic. I have been wondering a similar thing with a program I have been working on. If I develop a program in python using a GPL IDE and useing the python libraries like scipy etc then does this mean that I have no option but to release my program under a GPL if I wanted to sell my work?

I do not know what constitutes something "deriving" from a GPL program as apposed to something being created by implementing GPL programs.
Again, what's "derived" is defined by national laws.

The general idea seems to be the following: anything "derived" has to include parts of the original work; e.g. in C and C++, using dynamic libraries is considered to form "derivative works" because you're including code that's not yours through the header files. In Python, a "library" is a module you import, so the resulting work also includes stuff that's not yours into the compiled file (the pyc, which is what's actually executed)... So, if that module is GPL, you'll have to use GPL too (Are you sure SciPy isn't LGPL?).

So, executing something in a GPL'ed shell (e.g. a bash script) or writing some code in Gedit (also GPL) doesn't affect your program, as it isn't including any code that's not yours into yours.

But again, these are some loose criteria based on my observations that may guide you. The best is to talk with a lawyer, I think.

---

### Post by Tomosaur on 2008-09-27
> **elbarto_87 said:**
> This is an interesting topic. I have been wondering a similar thing with a program I have been working on. If I develop a program in python using a GPL IDE and useing the python libraries like scipy etc then does this mean that I have no option but to release my program under a GPL if I wanted to sell my work?

I do not know what constitutes something "deriving" from a GPL program as apposed to something being created by implementing GPL programs.

The only 'real way' to use GPL stuff with a non-GPL program (by non-GPL I mean 'proprietary', not some other GPL-compatible licence) is if the GPL stuff and the non-GPL stuff are obviously seperate. This means that - say your software depended on GPL libraries - maybe the easiest way to avoid any GPL violations - you would write your own GPL program which **used** those libraries, and then wrote your non-GPL program to use this GPL program for its normal operations.

Of course, this is a ridiculously round-about way of writing proprietary software which uses GPLd stuff - not to mention performance issues and other problems it would throw up.

It is for this reason that the LGPL was created - allowing you to use LGPLd libraries in a proprietary program - but the onus is on you to find out whether the libraries you are using do use the LGPL. 

Scipy is actually distributed under the BSD licence terms, which means you do not need to release your own source code just because your project relies on scipy. However, you would need to go through the libraries your project uses to make sure there are no other conficts.

Python itself is NOT GPL software. It uses a BSD-style, GPL-compatible licence. The core modules (those distributed as part of python itself) should be ok to include in proprietary software. Third party libraries, you would need to find out for yourself what licence they fall under.

However the whole area is generally a mine-field of 'potential violations'. There is a lot of debate over whether the GPL is a help or hindrance to open-source development. On the one hand, it ensures open-source code remains unrestricted and available for others to use. It removes the need to purchase licences for libraries and all of the other crud that goes on in the proprietary world. On the other hand, the GPL is considered 'viral' by many proprietary (and also many FOSS) developers, due to its 'if you use GPLd code, your project has to be GPL' terms.

BSD-style licences are probably better given the current climate, a lot of money is made from proprietary software, and companies are unlikely to want to shift any time soon. By using BSD-style licences, you have the greatest opportunity for the greatest number of users in both commercial and non-commercial environments. GPL licensed software presents problems for the commercial sector, and lawyers hate it. The LGPL was designed to allow commercial use under a GPL-style licence, but even GNU itself is trying to shift people away from using the LGPL. The goal of the GPL is to give FOSS an advantage - by developing innovative software under the terms of the GPL, the FOSS world can gain an advantage - and probably more importantly - leverage over the proprietary world (the reasons people want this are many and various, it's too big a discussion to get into here).

Either way - it's your duty to make sure you don't violate any licences.

---

### Post by pmasiar on 2008-09-27
> **Tomosaur said:**
> However the whole area is generally a mine-field of 'potential violations'. There is a lot of debate over whether the GPL is a help or hindrance to open-source development.

The main difference is ideological difference between 'open source' (which focuses on flrxibility nad convenience of developer via BSD-style licenses) and 'free software' (GPL places most importance on freedoms of the user, even if it restricts some flexibility of developer compared to BSD).

So obviously GPL is hindrance for OSS, because it was designed for Free Software :-)

> GPL is considered 'viral' by many proprietary (and also many FOSS) developers, due to its 'if you use GPLd code, your project has to be GPL' terms.

It is exactly like any other license: you can use it when you pay: money for proprietary license, pay in kind (code and time) for GPL, and pay by taking a risk that someone will take your own code private when using BSD.

> By using BSD-style licences, you have the greatest opportunity for the greatest number of users in both commercial and non-commercial environments. 

But you are taking a risk that if your code will be great success, someone else will take your code private and out-innovate you.

> GPL licensed software presents problems for the commercial sector, and lawyers hate it. 

It depends if those companies sell software or not. If they don't sell software, everybody (including lawyers) just love it. Free software is focused on users.

---

### Post by nvteighen on 2008-09-27
> **pmasiar said:**
> 
It is exactly like any other license: you can use it when you pay: money for proprietary license, pay in kind (code and time) for GPL, and pay by taking a risk that someone will take your own code private when using BSD.


Perfect description.

---

### Post by techmarks on 2008-09-27
Trying to create a proprietary application using GPL'd code is extremely problematic in many ways.

It goes against everything the users and creators of that license believe in, and if you're not extremely careful you'll be violating the license.

In many ways it is an odd and problematic license.

While it is focused on users rights, it addresses concerns of minor interest to the great number of users.

Most software users are not much interested in source code at all, not even in compiling software.

The problem is not proprietary software, the real problem is software patents.  Software patents should not exist at all.

---

### Post by dark joev on 2008-09-29
I think I will be using some other license besides GPL, BSD seems cool

---

### Post by howlingmadhowie on 2008-09-29
the easiest way to ensure that you are in compliance with the gpl is to act according to the spirit of the license.

---

### Post by bruce89 on 2008-09-29
I'm surpised no-one's mentioned the LGPL. It's essentially the GPL, but allows non GPL (or compatible) code to link to it.

Correct me if I'm wrong.

---

### Post by pmasiar on 2008-09-29
Yes, you **are** wrong: see post #20. Also, more info than you provided 8-)

---

