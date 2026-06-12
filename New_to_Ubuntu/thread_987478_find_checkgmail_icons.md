---
title: "find checkgmail icons"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by jason6g on 2008-11-19
anyone have a clue where the checkgmail icons are stored?

i have searched and searched and searched and i cannot seem to find these icons

i wish to make a custom set of icons, so that when i run 2 instances of checkgmail i am able to differentiate which icon in the tray correspondes with which email account

just looking for the 3 icons (new mail, no new mail, error) icons so i can copy, edit, and use them for my second instance.

---

### Post by dracayr on 2008-11-19
strang that you searched so long.. for me, one search ("locate checkgmail") was sufficient: /usr/share/app-install/icons. there are a lot of icons there, of course, but the checkgmail icons should be there also

dracayr

---

### Post by jason6g on 2008-11-19
Already loked in there.

That folder has the main icon, that would appear in the applications menu

I am looking for the three (3) icons that represent:
-No new mail
-New mail
-Error

---

### Post by ihendley on 2009-11-25
bump!

I came here with exactly the same problem (I want to make the error icon gray instead of red) and finally figured it out...

If you look at the checkgmail script you find that there are no icon files on disk, rather they are loaded from encoded data. Here is the relevant code:

```
$error_pixbuf = load_pixbuf($error_data);
```

```
$error_data = unpack("u",
'MB5!.1PT*&@H````-24A$4@```!`````0"`8````?\_]A````!F)+1T0`_P#_
M`/^@O:>3````"7!(67,```QU```,=0$M>)1U````!W1)344\'U047"@0$Y9]#
MH0```85)1$%4.,NUTL%*XU`4QO&_-J3,3$-WTC()(Y\'6G;L+@;CH-AN?0\'P%
MWZ#*>0.?YFZSF(!KEPF#E@2]N"L%P9B*"TTF&<O,@\'AV(?E]^6Y.X(.SE0;!
M67TQBB+ZT^G?GJ\>T[0P6L=`,;V\7%OMNT9K)DI!%&W$:%TL6AA@N_WVH>^3
MB8#6&W$F$@]]O\$`30-G/@<1`#(1)E`W:?#HZ,CP].2E03`#7*#7.4(KI,I$
M\'B;0!^XRD?C[^;GY^OP\SD0:W&G0A"A5`05PE8FXP%4;#WW?_;*_WS-OQ^P&
MY\'E5+I>%HU0,&.#7X.3D\4_LS.?4`=L=G"2%\'8;QZO[>&*W[.\?\'&W%[Z@8-
M9K4R+!;CH>\?9"(%<-!@I=[MU@(JX!4/!J9,DK&CU`P8`7O`MQJ7RR5VGH/G
M=0)N@)_KVUNSOKX>VV$XP_-<)XIZB/2;[0!VGE,F"788_OZ5`=(@L\'Z<GKHU
MKE>T<=Y"%A<7KQ\Q#0(+^#\,X\'F=!A:P"QR62?)O_!GS`K6COO-L,Q_/````
)`$E%3D2N0F""');
```

So, with this in mind, does anyone know how I can get this image into some format on disk that I can edit in GIMP for example?

Once I have the edited image I can point to it as a "custom error icon" in checkgmail's prefs.

---

