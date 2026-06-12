---
title: "Dev cpp"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by powerof2 on 2008-08-22
OK, I somehow managed to get Bloodshed C++ and Wine installed with the former working just fine. I wrote Hello World, and it compiled.

Two questions them immediately came up.
1. What is the command to get the output display to stick around.

2. Once compiled, where can I see the output?

Remember, with Wine, the program and compiler seem to be in a pseudo-Windows environment and the location can't be found, or at least I can't find it, in the Ubuntu terminal.

Thanks,

j
--
Jay Reidy
[email]jay.reidy@gmail.com[/email]

---

### Post by Majorix on 2008-08-22
You can usually check where DevC++ saves its files. In wine, usually Z:\ is your Linux /, while there might or might not be special "Documents", "Desktop" shortcuts Wine uses to point to specific locations on your HDD.

Best is to look in "winecfg" under "Drives".

---

### Post by iansane on 2008-08-22
Do you mean the output of the c or c++ application? If so, in windows command line just put a "system(pause)" before "return" in the program.

In linux for terminal it would be "getchar()" to wait for the user to press a key.

Installing dev in wine seems strange to me cause I haven't been able to get anything to work exactly right as far as command line commands because it's still on a linux system. I guess as long as you use the cmd.exe in wine to run them it works? I don't know. hope that is helpful

---

