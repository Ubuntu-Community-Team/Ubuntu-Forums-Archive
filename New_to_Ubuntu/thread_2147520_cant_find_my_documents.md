---
title: "cant find my documents"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by arranskye on 2013-05-22
Hi  I typed a few test documents just to get used to LO.   and although I named and saved them, I  couldnt find them.  eventually one of them appeared above the icons on the desktop.   tried various methods of saving them but  nothing appeared to be consistent and the only place the**y NEVER **appeared was in documents.

I must be doing something very wrong or perhaps LO writer is not working properly.  can you help please.   Is it ok to install ABI Word. thanks

---

### Post by newb85 on 2013-05-22
Sounds very odd...

Just checking, you're not beginning your file names with a period, are you?

---

### Post by Bucky Ball on 2013-05-22
Might sound too simple but:

Save As;
Choose 'Documents' in the left hand pane (if you haven't got one then go to View>Side Pane; might be different on your file manager);
Name the document;
Save.

This is what you're doing? If it's still not going to the right place you could open a terminal and type:

locate nameofyourfile.odt

That should at least tell you where it's going and you might be able to put two and two together. If it is a problem with LO I've never seen anything like it. You might like to check your paths in LO: Tools>Options>Libreoffice>Paths. See if that gives any clues as to where the files are perhaps getting saved to by default.  

Yes, it's fine to install Abiword but if you're doing it because you can't find your files in Libreoffice I would focus on working out where your files are ending up in preference to installing Abiword. Good luck. ;)

---

### Post by Feathers McGraw on 2013-05-22
Hi arranskye,



You mentioned in another thread that you are running Ubuntu using the CD - I think this is the problem.

When you do this, Ubuntu is loaded into your RAM temporarily, and any files you have saved are lost when you turn the machine off and the RAM no longer has power.

If you install Ubuntu alongside Windows 7 then Ubuntu will have a portion of your hard drive where it can save files, and they will be there when you return! If you'd like help doing this then let us know - you can still remove Ubuntu afterwards if you decide you don't like it.



The live CD is mostly used to give people a chance to try Ubuntu without actually making any changes to their computer, but it also has other uses, some of which are covered [here]("https://help.ubuntu.com/community/LiveCD"), and are actually really useful.


Feathers

---

### Post by arranskye on 2013-05-22
Hi guys, Thanks very much.  I am now using Ubuntu 13.04 and I am able to save my files ok, but I will still take on board your suggestions as the only way to learn Linux is trial & error. I will also make a persistent image USB just for the xperience of using linux  "code/script" and it will help me to move forward.   You may have noticed my other posts where I allowed the Ubuntu Cd to wipe out windows 7 on my PC.  I now intend to install linux on my HDD before I re-install Windows 7. First I want to install it on an older PC to dual boot with windows xp so yes please I would really like some help.  What a bin head!!!! Should have realised that documents would be lost after shutting down.
A lot of really useful advice on the link you gave me and its reasonably easy to understand which is a big bonus.

Thanks again  & best  regards

---

### Post by Feathers McGraw on 2013-05-22
You're welcome! There's a load of info on that site, and it's all pretty good I've found!

I only started using Linux myself a few months ago, and have learned a lot through troubleshooting and tweaking to get things "just so".

**In my experience it's a lot easier to install windows first** (only windows) and then install Ubuntu. Installing Windows 7 afterwards will break the GRUB bootloader and you'll have to use the Ubuntu CD to repair it...Windows has the arrogance to assume that it is the only OS on the machine, whereas to my knowledge every other OS checks for other systems when they install!

Incidentally, have you tried using [Kubuntu]("http://www.kubuntu.org")? It's worth making a live CD and testing it out before you make the final change, it's set up more like a "normal" desktop so you may prefer it! You could even have more than one Linux distribution, whatever takes your fancy.

The advantage of all the *buntus (there are at least two more, Lubuntu and Xubuntu that use less RAM so are good for old hardware and netbooks) is that the different distributions are all the same under the bonnet, they just come with different applications and have different desktop appearances. This means that if you ever learn any terminal commands, almost all of them will work on any other *buntu :)

Anyway...the mods will probably get frustrated if we carry on here because the initial problem has been solved and it's a bit off topic. If you have any additional questions about other issues, please start a new thread and someone will answer there.

Also, you can mark the thread as "solved" by clicking edit on your original post, then "go advanced", and then change the prefix.

Feathers

---

### Post by Bucky Ball on 2013-05-23
Please mark thread as solved when you think it is by following the link in my signature. Post a new thread for any further (new) problems. Thanks.

---

### Post by arranskye on 2013-05-24
Sorry could not end the thread without thanking feathers properly for all her help  THANK YOU.  i changed from Ubuntu 12.10 to 13.4. Like 12.10 better but no problems saving docs. on 13.4.
Thanks for your advice.  I have 2 pc desktops & 2 laptops. Running puppy 5.28 and ubuntu and up for trying more. Much as I like playing with them I really want to get down to the nuts & bols 
especially terminal commands etc.
i will be needing a lot more help but these forums are brilliant. The members respond so quickly and offer so much help and Ubuntu has more members than win 7 forums.  Amazing!!!!
thanks again.

---

### Post by Feathers McGraw on 2013-05-24
> **arranskye said:**
> Sorry could not end the thread without thanking feathers properly for all her help  THANK YOU.  i changed from Ubuntu 12.10 to 13.4. Like 12.10 better but no problems saving docs. on 13.4.
Thanks for your advice.  I have 2 pc desktops & 2 laptops. Running puppy 5.28 and ubuntu and up for trying more. Much as I like playing with them I really want to get down to the nuts & bols 
especially terminal commands etc.
i will be needing a lot more help but these forums are brilliant. The members respond so quickly and offer so much help and Ubuntu has more members than win 7 forums.  Amazing!!!!
thanks again.

Feathers is a guy, but thanks all the same ;). Refreshing that you don't automatically assume I'm male!

[Try This]("http://linuxcommand.org/lc3_learning_the_shell.php") for learning how to use terminal!

I agree about the forums being brilliant, it's amazing that other people give so much time to help others... keep an eye on the "Absolute beginners section" and give something back :)

Feathers

---

### Post by Bucky Ball on 2013-05-24
> **Feathers McGraw said:**
>  Refreshing that you don't automatically assume I'm male!



+1. A common problem round here! The fallback stereotype is if you're into technology you must be a male. We have lots of women on the forums, including on staff. 

To help others, please mark thread as solved by following the link in my thread. Cheers and good luck. ;)

---

### Post by arranskye on 2013-05-26
[Try This]("http://linuxcommand.org/lc3_learning_the_shell.php") for learning how to use terminal!

. 
Feathers[/QUOTE]

[I]keep an eye on the "Absolute beginners section" and give something back :) 
[/I]
 Whoops!!!!!!!!!! that might take a while, right now it would be the blind leading the blind, but look forward to the day that i might be able to. For the record Im a very silver surfer of the female variety.  Arran & Skye are 2 beautiful Scottish islands. and the names of my dogs.

Started doing an excellent tutorial which i found in this "absolute beginners section",  and now I cant locate it to continue.   Scream!!!!!!!!!             
In this tutorial there was a link to a scientific page, that was then saved in a newly created unixstuff folder as part of the exercise. perhaps someone could help me relocate 

I copied a page from a different tutorial and saved it in the unixstuff folder as tutorial.odt, then just to try,  opened the terminal and input      locate tutorial.odt  but no response in terminal.
I know the document is located in    home/ubuntu/unixstuff/tutorial so what did I copy incorrectly that the terminal could not find the tutorial document.  Should I have prefixed the command with  cd or ~ or  /  or  added folder or something else??  thanks

---

### Post by steeldriver on 2013-05-26
The 'locate' command (in fact pretty much everything in Linux/Unix) is case sensitive, so if it's possible that you saved it with upper-case or mixed-case characters you could try making it case-insensitive with

```
locate -i tutorial.odt
```

If there's a possibility you saved it as something other than an odt file, you can make the search even less specific by omitting the .extension altogether

```
locate -i tutorial
```

OTOH it may just be that the database that the 'locate' command uses has not been updated since you saved the file - in which case try

```

sudo updatedb
locate -i tutorial

```

Alternatively, you can try the 'find' command

```
find ~ -iname 'tutorial.*'
```

Hope this helps

---

