---
title: "what does this command mean?"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-09-19
I want to install the samsung unified driver. according to their website, adter downloading the file i have t run these commands:

> 1. Download and extract the driver
2. Open ''Root Terminal''
3. Execute installation program.
$ sudo cdroot/autorun
4. After intall, PPD path is set again.
$ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung
5. Execute Configurator, and Add your printer model name by Add Printer 



so I have some questions.


- what does step 4 mean? can someone plz explain it to me.

- and when i try step 3 i get k when i try step 3 i get 
> Command not found

-This is what the autorun file contains:
> #! /bin/sh
BASE=`dirname $0`
exec sh $BASE/Linux/install.sh

---

### Post by iansane on 2008-09-19
well #3 should be "./cdroot/autorun" and you should be in the directory that the extracted folder "cdroot" is in. or cd (change directory) to cdroot and then run 
"./autorun". You have to include the "./" and you have to be in the directory where it is.

---

### Post by iansane on 2008-09-19
my mistake, I was looking at the first five steps for "Unified linux install".
I see what you mean now. It should work the same way as the "./" is just to say "in this directory" basically. Make sure your in the directory where the folder cdroot is or type the complete path like /home/name/Desktop/cdroot/autorun if it's on the desktop.

---

