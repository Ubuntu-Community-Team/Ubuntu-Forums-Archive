---
title: "X server doesn't start"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by mikk2 on 2014-02-22
Hello I am new in linux world and it was my first experience with linux.

I've problem with startx. If my computer boots then my computer shows me only black screen. I can choose an recovery mode from the beginning and from the recovery mode I can choose "Resume" I press enter and I have there a command line. If I login as a root and type startx then my screnn goes grey and after a while it turns to black. How can I fix this problem? I've installed ubuntu-desktop, X server and even reinstalled fglrx driver. I'm using asus p4r8l2 motherboard. You can download the manual from here: [http://www.manualslib.com/manual/370561/Asus-Pundit-R350.html#manual](http://www.manualslib.com/manual/370561/Asus-Pundit-R350.html#manual). Please help me!


Sorry for my bad English I'm from Estonia.

Mikk Kruusalu

---

### Post by mörgæs on 2014-02-22
Hi, welcome to the fora.

It's an old motherboard, and I doubt that Ubuntu is the best choice. How does it work in a live boot of Lubuntu 13.10?

---

### Post by mikk2 on 2014-02-22
I tryied to install Lubuntu but I choosed install Lubuntu and then the screen turned grey and then to black.

---

### Post by mörgæs on 2014-02-22
Ok. From a live boot please run
```
lspci | grep -i vga
```
and post the results.

---

### Post by mikk2 on 2014-02-22
I'm so new that I don't know what means live boot. Please explain to me what it means. Sorry for this question I'm very beginner.
I think that code needs to be: lspci | grep -i dvi. Because my screen is connected with DVI not VGA.

---

### Post by mörgæs on 2014-02-22
A live boot is 'try without installing'.

You could enter both commands and see the difference :-)

---

### Post by mikk2 on 2014-02-22
Sorry that i'm so stupid but what do you mean "without installing". I need to install ubuntu to enter somthing onto command line. :)

---

### Post by SeijiSensei on 2014-02-22
You can boot from installation disk and click "Try Ubuntu".  That will run Ubuntu from the installation media and leave the computer unchanged.  Once you've done that, open a Terminal and type "lspci | grep -i vga".  This reports the identity of the graphics adapter regardless of how it connects to the display.

---

### Post by mikk2 on 2014-02-22
But I haven't "Try Ubuntu" option there. I'm running on ubuntu 12.04

---

### Post by Bashing-om on 2014-02-22
mikk2; Hi !

Not to know is not a sin ! None of us were born knowing what we know.

Try ubuntu: -> 
Set in bios to boot the external device that you are using - as for example a DVD, as the 1st boot priority;
As soon as the bios screen clears depress and hold the right shift key -> language screen, escape key to accept the default ->
Boot options screen, of which one of the options is "try ubuntu without installing". -> Desk top !

When you can access "try ubuntu" additional advise will be provided.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by mikk2 on 2014-02-22
Hello I thank you for your [COLOR=#000000][FONT=arial]forbearance!

I tryied both commands "lspci | grep -i avg" and "lspci | grep -i dvi". On both options it gives me an error like this: Could not find kernel image: lspci.[/FONT][/COLOR]

---

### Post by Bashing-om on 2014-02-22
mikk2; Hey !
Per your statement, not a valid command.
Try it as:
> 
sysop@1310mini:~$ lspci | grep -i vga
06:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550]
sysop@1310mini:~$ 

where 'avg' should be 'vga'.

Try again, and post the exact output. Please use "code tags" for posting the command's outputs:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]together
[INDENT][INDENT]we will get there
[/INDENT][/INDENT][/INDENT]

---

