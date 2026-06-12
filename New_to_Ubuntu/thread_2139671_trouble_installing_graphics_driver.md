---
title: "trouble installing graphics driver"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by abhich on 2013-04-27
[FONT=arial]i have tried to install graphics driver but failed repeatedly. i am following [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450) this post step by step ... 

but whan i type [/FONT][FONT=Arial][SIZE=2]
[FONT=arial]sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
[SIZE=2]it shows some error and cant pro[SIZE=2]cede furth[SIZE=2]er in the pro[SIZE=2]cess 


please help 

newbie here !![/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/FONT]

---

### Post by zero2xiii on 2013-04-27
Hay,

We are going to need the error to assist you.

Please post the output of the stated command including the error so we can assist you.

Please post this between [Code ] tags (the # sign above the post).

Cheers

---

### Post by abhich on 2013-04-28
i have done every step properly but then i type
```

sudo aticonfig --initial -f
```

it shows - 
```
aticonfig: No supported adapters detected
```


please help

---

### Post by 0N3 on 2013-04-28
[http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html](http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html)


Try that tutorial i had same problem. after that it worked! After following first part of installation you have to run 


```
sudo ubuntu-amd-catalyst-install
```

---

### Post by 0N3 on 2013-04-28
After the tutorial not the first part sorry

---

### Post by abhich on 2013-04-29
let me try it !!

---

### Post by abhich on 2013-04-29
looks like it didnt work for me . when i try opening the amd catalyst . it shows this message

i have attached a screenshot
[ATTACH=CONFIG]241957[/ATTACH]

thanks in advance

---

### Post by gordintoronto on 2013-04-29
Are you sure you have hybrid graphics? If you run the command: lspci
one or two lines should include "VGA." They identify your graphics adapter or adapters. Copy those lines and paste them into a message.

What is the brand and model of your laptop?

---

### Post by abhich on 2013-04-29
its done . graphics driver now works perfectly. i had forgotten to write

```

sudo ubuntu-amd-catalyst-install
```

after this . everything is perfect !!!
 
Thanks everyone

---

### Post by 0N3 on 2013-04-29
Well done I did quote to run it [COLOR=#000000][FONT=Ubuntu Mono]sudo ubuntu-amd-catalyst-install[/FONT][/COLOR]

---

### Post by abhich on 2013-04-29
ya .. that code solved the problem . thanks

---

