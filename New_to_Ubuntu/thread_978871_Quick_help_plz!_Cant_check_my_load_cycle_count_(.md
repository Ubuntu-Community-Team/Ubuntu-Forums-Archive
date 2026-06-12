---
title: "Quick help plz! Cant check my load cycle count :("
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Kestol on 2008-11-11
Hello people,

Hope i can get a quick answer... Since i suffered from the load cycle bug in 8.04... But now i'm testing 8.10...

But when i run the command:

> $ sudo aptitude install smartmontools

I get this:
> kevin@kevin-laptop:~$ sudo aptitude install smartmontools
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
Reading extended state information      
Initializing package states... Færdig
[B]Couldn't find any package whose name or description matched "smartmontools"
Couldn't find any package whose name or description matched "smartmontools"[/B]
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
Reading extended state information      
Initializing package states... Færdig


Whyyy?!

I cant run this command because it isnt installed ;(

> $ sudo smartctl -a /dev/sda | grep Load_Cycle_Count

Can anybody tell me why I cant install :(

---

### Post by cariboo on 2008-11-11
Have you got all the repositories enabled in System-->Administration-->Software Sources?

Jim

---

### Post by Kestol on 2008-11-12
ty slot:KS

Switching source fixed my problem:D

---

