---
title: "GPL-compatible license confusion, can someone help"
date: 2010-05-14
forum: Programming Talk
---

### Post by ulao on 2010-05-14
I give up looking for a GPL specific forum, but I figured someone here has to know..

I have developed some code that uses a few GPL projects. I want to sell my device but I dont want to publish my source code or use the GPL license. The GPL source code's are libraries and not part of my code.

I included this note:

> This project makes use of other projects using the GNU GPL. The usb Interface is part of the V-USB project. For a copy of their GPL please reference the V-USB site. In addition, the following Code to interface with these devices is made available on Ralphs page: [ then I list the devices. ]. I have not modified the code responsible in reading the devices in any way. In addition to these wonderful projects I have developed the means to communicate with a wide range of other devices. The complete workings of my code are not available at the moment and contained outside of the GPL projects, it merely interacts with it.


I created hyper links to each project. 


Now I'm told that is not good enough by some random user. I must host these copies on my server? Does anyone have a moment to talk about this, I'm not finding my answers.

---

### Post by Some Penguin on 2010-05-14
Not good enough, if your device contains your code, which is a derivative work using GPL'd code.  There's a difference between the LGPL and the GPL.

---

### Post by StephenF on 2010-05-14
It seems you want to be paid for your code and not share the source while violating the license of code obtained from others at no price and profit from theirs.

Without checking (IANAL etc):

The GPL2 states that if you use other peoples GPL2 code as part of the workings of your program then your program is a derivative work of the other and must be distributed under the same license.

To not do so is to reject a term of the others license. The GPL2 states that to reject part of the license is to reject the license entirely which means you have no license to distribute GPL2 works for which you do not own the copyright.

I suspect you already knew that and you were just looking for a loophole. Commercial interests have been looking for loopholes in the GPL2 for almost twenty years. They have not found any and the GPL2 has always been upheld in court on the few occasions that people and organizations have tried their luck.

Linking to an external library is using other code as part of the workings of your program. The code does not live in the same executable file but when loaded into memory at execution time the two merge into one program. This is different to putting two independent programs, one a GPL and the other a non GPL program into an archive (tar.gz for example). Note that in that case both works live in the same file on the hard drive but are not part of the same work. They do not interact with one another.

To comply with the GPL you will have to make the source code of your program available for download. Making the source available does not mean you can't charge money for the device you are making though it doesn't help if all you want to do is shut out competitors. Remember, the value of a thing is in the value added by labour. Add value by writing your own libraries instead and you won't have to keep the source open. You will have created a thing of value at greater expense. Nothing comes from nothing so little should come from little, don't you think?

---

### Post by splicerr on 2010-05-14
> **ulao said:**
> I give up looking for a GPL specific forum, but I figured someone here has to know..

I have developed some code that uses a few GPL projects. I want to sell my device but I dont want to publish my source code or use the GPL license. The GPL source code's are libraries and not part of my code.
.

Doesn't matter if it's not part of your code. You're still using these libraries in a manner that the license explicitly prohibits. This is **copyright infringement**.  Besides releasing the source code of your program which you already stated don't want to do you have two other choices.


[LIST=1]
[*]Stop using GPL libraries from your non-GPL code
[*]Ask the copyright holders of the libraries you are using to license the libraries to you under a different license.
[/LIST]
It appears that the  V-USB project which you are using libraries from offers just that:

> 
**[SIZE=2]Commercial Licenses for V-USB[/SIZE]**

 If the terms and conditions of the GPL are unsuitable for  you, e.g. because you don't want to publish the source code of your  firmware, you can simply pay money for a commercial V-USB license.

[http://www.obdev.at/products/vusb/license.html](http://www.obdev.at/products/vusb/license.html)


So either pay them for a commercial license or stop using their libraries. Failing to do so is a **violation of their copyright.**

---

### Post by soltanis on 2010-05-14
Welcome to the GPL. If you link to a GPL library, then you must also license your code under the GPL. Either do that, or use a differently licensed library.

---

### Post by ulao on 2010-05-14
thx guys, not looking for loopholes, just asking. I have never released any code period. Si I dont know a thing about license and i think I made that part clear ;)

---

### Post by nvteighen on 2010-05-15
Ugh...

I am not a lawyer, even though I have some little legal training... 

Actually, **nobody** knows how to deal with dynamically linked libraries because there's no court ruling about this yet. Copying code or statically linking a library are both totally clear cases of derivative work. But dynamic linking... on one hand, it's clear that without the specific version of the library your program isn't guarranteed to work, so one could say that library and program are part of the same "thing" and therefore, it is a derivative work... on the other hand, it's perfectly possible, given a 100% compatible library, to have your program being loaded at startup with a totally different implementation of that library...

The FSF's, MS's and other software companies' official position is that dynamic linking does constitute a derivative work; but there's the obvious fact that they want it to be that way so each respective licenses has a broader range of application. The best attitude, IMO, is that as long as this isn't cleared you act like it was that way.

---

### Post by ulao on 2010-05-15
Ok, say I have no choice but to show my source code. Being that I have to do so since I use other GPL code. Must I then void myself of all license and copyright other then GPL? Granted my code is exposed so I cant do much about it but do I have any say of what people do with my code?

---

### Post by ibuclaw on 2010-05-15
> **ulao said:**
> Ok, say I have no choice but to show my source code. Being that I have to do so since I use other GPL code. Must I then void myself of all license and copyright other then GPL? Granted my code is exposed so I cant do much about it but do I have any say of what people do with my code?

No, you don't if it is GPL'd. But at the same time you give no warranty on the code or for any personal changes they may make to it. So someone else's buggy derivative is not the fault of yours.

If you read the License.txt file of the project you are using, you'll find the following:

> 
Adhere to minimum publication standards. Please include AT LEAST:
- a circuit diagram in PDF, PNG or GIF format
- full source code for the host software
- a Readme.txt file in ASCII format which describes the purpose of the
  project and what can be found in which directories and which files
- a reference to [http://www.obdev.at/vusb/](http://www.obdev.at/vusb/)


Regards
Iain

---

### Post by ulao on 2010-05-15
thx ibuclaw, See this is what is confusing me to death. According to this topic I must include my source ( or at least that is how I read it ) but according that lic file I only need to include the host source?


- a circuit diagram in PDF, PNG or GIF format **[done]**
- full source code for the host software **[ I'm not the host so done]**

- a reference to [http://www.obdev.at/vusb/](http://www.obdev.at/vusb/)**[done]**

- a Readme.txt file in ASCII format which describes the purpose of the project **[mine or theirs?]** and what can be found in which directories and which files**[again this implies I need my source available?]**

I know I have a bad habit of picking works apart but why use the word the? - "of your project" or "of the host project" would be much more clear to me. It sounds to me like this is stating I must include source code. If that is the case does anyone know where to find a preamble that I can use at the top of my code that say not for re-use or would la-mans terms be acceptable. 

I do thank you all for your help, I will not take any of it as legal advice. I'm just really in the clouds here.

---

### Post by splicerr on 2010-05-15
Well it's all very clear to me.

> 
The firmware-only USB driver for AVR microcontrollers is published under  the terms of the **GNU General Public License Version 2** (GPL). See the  file "License.txt" in the "usbdrv" subdirectory of any  reference project for details. In addition to the terms and conditions  of the GPL, we strongly  recommend..
And the terms of the GPL are very clear about this. You have to release **your source code** that is using the GPL licensed library. You may not like it but that's the way it is. And no you can not add such preambles to the GPL, that would make it a different license,  not compatible with the GPL. And your code would be in violation with the GPL license.

---

### Post by ulao on 2010-05-15
ok thx,

---

