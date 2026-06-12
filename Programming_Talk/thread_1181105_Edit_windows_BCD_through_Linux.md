---
title: "Edit windows BCD through Linux"
date: 2009-06-07
forum: Programming Talk
---

### Post by saliljain on 2009-06-07
I have a linux application, that i want to use to find and manually read/edit the windows Vista/7 BCD file. I cannot run any existing win32 applications, I need to hard code one in C/C++ 

Please help 

Thank You
~Salil

---

### Post by wmcbrine on 2009-06-07
What's a BCD file? (I see "BCD" and I think "binary coded decimal", but I assume that's not what you're talking about here.)

---

### Post by unknownPoster on 2009-06-07
I'm pretty sure the OP is referring to the MBR.

In this case BCD refers to Boot Configuration Data. It can become corrupted in certain circumstances.

The BCD is fairly new. It has replaced the old boot.ini method, in recent versions of Windows (Vista and 7).

---

### Post by soltanis on 2009-06-07
The files are formatted like registry hives.

I'm trying to find details on the format online. It seems as if this sort of information is hidden from the user.

EDIT.

I keep treating this as I would a Linux issue, whereby I assume that the format is documented somewhere. Obviously not. Microsoft's only method for "third parties" to access their precious bootloader database is through Windows API functions (which are obviously not going to happen in Linux).

---

### Post by Odd_Fellow on 2009-06-10
I had a problem with my bcd and couldn't find any easy way to edit it from Linux (it appears to be more or less impossible to edit it when not in a windows vista environment, though there is hopefully someone that know how). 
 
 My problem was pretty easy - I had accidentally changed the time-out time when switching boot order to let vista boot Ubuntu as default OS - problem there was that each time I tried to start vista, the vista loader pushed me back into Ubuntu.
 
 My solution was (after hours of searching about bcd) was to load the vista recovery GUI (apparently on a live cd if you own a "real" copy of vista, or as a separate load alternative if you (like me) have the OEM version pre installed on a "disc-less" laptop). In the GUI, open a terminal and type
 ```
bcdedit /?
```To find the second load alternative (if you have the same vista set-up as I have): start normally and then choose to see the list of available boot options (press esc during start-up). The bottom two (if you only run ubuntu/vista) should both say "windows longhorn" or "windows vista" or somthing that indicates that it's microsoft - top one of them is the vista loader (that was broken for me) and the bottom one is the recovery gui

From the list of commands, try finding one that will help you with your problem - the one that made my day was ```
bcdedit /timeout 10
```hope this will help you some

---

