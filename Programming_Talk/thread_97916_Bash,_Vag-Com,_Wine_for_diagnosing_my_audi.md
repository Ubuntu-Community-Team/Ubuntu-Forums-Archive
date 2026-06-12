---
title: "Bash, Vag-Com, Wine for diagnosing my audi"
date: 2005-12-01
forum: Programming Talk
---

### Post by tay on 2005-12-01
I am not sure how to do this with ubuntu, i found a how-to for linux and vag-com diagnostic cables and ross-tech software.

Here it is:
[http://autos.groups.yahoo.com/group/VAG-COM/message/4441]("http://autos.groups.yahoo.com/group/VAG-COM/message/4441")

I made through the first couple steps with
sudo mkdir ~/w_c
and the other one
mv ~/Desktop/Release3112n.exe ~/w_c/vagcom/
and then had some problems with this part

5. Create these files (touch):
~/w_c/windows/win.ini
~/w_c/windows/system/shell.dll
~/w_c/windows/system/shell32.dll
~/w_c/windows/system/winsock.dll
~/w_c/windows/system/wsock32.dll

how do you do that?

steps 7,9,10 i don't really understand either.

---

### Post by ltmon on 2005-12-02
The program "touch" will create an empty file if it didn't previously exist.  If it did exist, the file modification date will be updated to the current date.

Just type into a terminal:

> touch <filename>

for each of those files.

Step 7 and 8 is asking you to install wine.  Don't do it this way, instead go to [http://winehq.org](http://winehq.org) and find the ubuntu instructions there (much easier this way).

I wouldn't do step 10 either.  Just type "winecfg" into a terminal and adjust your configuration there.  You may have to play around a bit at this stage.... but using wine is never straightforward and easy (yet).

L.

EDIT:

I just read the full instruction set, and although I'm sure they'll work they are a bit non-standard and may lead to more pain than necessary.  I would try the following sequence first:

1. Install wine from winehq.org
2. Run "winecfg".  The most import setting is your "drives" (use "autodetect" here).
3. type "wine yourapp.exe" at a command prompt.

L.

---

### Post by tay on 2005-12-02
i ran into a problem ,  here are the screenshots:

um. i don't know how to put pictures in.  anyways..

I had a problem with a active x plugin that is going to be required to install to make it work.  I installed it fine, and then it asked me for mozilla/bin files, because they could'nt find it.. i also could not find any bin files.

---

### Post by tay on 2005-12-03
*bump,, is active x controls possible under linux?  i had plenty problems using these on windows.

---

