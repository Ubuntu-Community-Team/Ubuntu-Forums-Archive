---
title: "HowTo: Set language locales from UTF-8 to ISO-8859_1"
date: 2006-02-06
forum: Outdated Tutorials &amp; Tips
---

### Post by lptr on 2006-02-06
Maybe there are persons out there who got into more or less trouble while using UTF-8 and want to fall back into old 'bad' behaviours ;-) like mine.

Because of historical things I still got stuck with ISO-8859_1 under Hoary. One of the disadvantages while connecting from hoary box via xterm/ssh into the 'new' headless Dapper machine had been quite ugly signs when working for example with mc. This results comming from UTF-8 locales settings on dapper box.

Under Hoary I did switch away from UTF-8 back to ISO-8859_1 simply using

```
# dpkg-reconfigure locales
```

And disabled in following dialogs UTF-8 reenabling ISO.

I tried this with my headless dapper installation, too. But it did not work. None of the dialogs appeared. So I needed a workaround.


Within Dapper do edit **environment** to:
```
# nano /etc/environment
LANGUAGE="de_DE:de"
LANG=de_DE

```
((please take your language locales instead of mine))

and copied over additionally /etc/locale.alias and locale.gen
from my old Hoary box:

```
/etc/locale.alias ((content without header))
bokmal		no_NO.ISO-8859-1
bokmål		no_NO.ISO-8859-1
catalan		ca_ES.ISO-8859-1
croatian	hr_HR.ISO-8859-2
czech		cs_CZ.ISO-8859-2
danish          da_DK.ISO-8859-1
dansk		da_DK.ISO-8859-1
deutsch		de_DE.ISO-8859-1
dutch		nl_NL.ISO-8859-1
eesti		et_EE.ISO-8859-1
estonian	et_EE.ISO-8859-1
finnish         fi_FI.ISO-8859-1
français	fr_FR.ISO-8859-1
french		fr_FR.ISO-8859-1
galego		gl_ES.ISO-8859-1
galician	gl_ES.ISO-8859-1
german		de_DE.ISO-8859-1
greek           el_GR.ISO-8859-7
hebrew          he_IL.ISO-8859-8
hrvatski	hr_HR.ISO-8859-2
hungarian       hu_HU.ISO-8859-2
icelandic       is_IS.ISO-8859-1
italian         it_IT.ISO-8859-1
japanese	ja_JP.eucJP
japanese.euc	ja_JP.eucJP
ja_JP		ja_JP.eucJP
ja_JP.ujis	ja_JP.eucJP
japanese.sjis	ja_JP.SJIS
korean		ko_KR.eucKR
korean.euc 	ko_KR.eucKR
ko_KR		ko_KR.eucKR
lithuanian      lt_LT.ISO-8859-13
norwegian       no_NO.ISO-8859-1
nynorsk		nn_NO.ISO-8859-1
polish          pl_PL.ISO-8859-2
portuguese      pt_PT.ISO-8859-1
romanian        ro_RO.ISO-8859-2
russian         ru_RU.KOI8-R
slovak          sk_SK.ISO-8859-2
slovene         sl_SI.ISO-8859-2
slovenian       sl_SI.ISO-8859-2
spanish         es_ES.ISO-8859-1
swedish         sv_SE.ISO-8859-1
thai		th_TH.TIS-620
turkish         tr_TR.ISO-8859-9

```

```
/etc/locale.gen
de_DE.UTF-8 UTF-8
en_US.UTF-8 UTF-8
de_AT.UTF-8 UTF-8
de_BE.UTF-8 UTF-8
de_CH.UTF-8 UTF-8
de_LU.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_BW.UTF-8 UTF-8
en_CA.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_HK.UTF-8 UTF-8
en_IE.UTF-8 UTF-8
en_IN UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_SG.UTF-8 UTF-8
en_ZA.UTF-8 UTF-8
en_ZW.UTF-8 UTF-8

de_DE ISO-8859-1

```
((same like above: Please alter /etc/locale.gen settings to your needs))


Important note: [COLOR="Red"]You need to do[/COLOR] upper steps [COLOR="Red"]FIRST!![/COLOR]

If you are finished, do **install** missing **locales**:

```
# apt-get install locales
```

During installation there will come up a message, that package contributor found having different locales settings. Skript suggests to overwrite modified/current settings. But: Do NOT overwrite settings. Instead: Keep things as shown.

After finishing reboot and all should be as expected.


Hope this helps some folks until reconfigure works with dapper in CLI mode :)

rob*/

---

### Post by jannol on 2006-02-20
Thx, it worked great.

---

### Post by beetlish on 2006-03-03
For some reason this didn't work for me. I had to edit /var/lib/locales/supported.d/en like this:

```

en_HK.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_IN UTF-8
en_ZW.UTF-8 UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_SG.UTF-8 UTF-8
en_BW.UTF-8 UTF-8
en_ZA.UTF-8 UTF-8
en_CA.UTF-8 UTF-8
en_IE.UTF-8 UTF-8

en_US.ISO-8859-1 ISO-8859-1

```

Replace the last line (or add another) with your choice and run: sudo dpkg-reconfigure locales

---

### Post by lptr on 2006-03-03
Recently I did install a newer Dapper (01/31/2006) and recognized that my own method does not work any longer with it. 

Did your change lead to success?

Anyways: dpkg-reconfigure locales still seems to be broken :confused: .

rob*/

---

### Post by StarQuake on 2006-09-12
It seems when you install the package localeconf, you do get the config dialogs with:

dpkg-reconfigure locales

Still couldn't get any ISO-8859-1 locales. Are those not included anymore in dapper?

---

### Post by isoaglib on 2007-01-02
Hi,

locale setting to ISO-8859-xy got more and more complicated from Breezy to Dapper and finally to Edgy.
While it was totally enough in **Dapper**, to copy from */usr/share/i18n/SUPPORTED* the required ISO-8859 strings over to */var/lib/locales/supported.d/local* and call ```
sudo dpkg-reconfigure locales
```, and to select the appropriate default locale with ```
sudo dpkg-reconfigure localeconfig
```, this is no more enough for **edgy**. The worst thing is, that there is no warning in the *dpkg-reconfigure localeconfig* procedure, that the user should do his changes somewhere else. The settings are simply ignored - overwritten by something else.

Even setting by hand LANG and LANGUAGE in*/etc/environment* is not enough, as some programs are sourcing the locale setting from somewhere else.

I found finally, that */etc/default/locale* has to be changed by hand, to contain the appropriate LANG and LANGUAGE settings. This file seems to be the state-of-the art version to set locales in debian and ubuntu. */etc/environment* seems to be replaced in the long run.

So my personal solution in step-by-step approach:
[LIST=1]
[*]grep your wanted locale settings from */usr/share/i18n/SUPPORTED* and paste them to */var/lib/locales/supported.d/local*
[*]call ```
sudo dpkg-reconfigure locales
``` to produce the new locales
[*]edit both */etc/environment* and */etc/default/locale* to contain settings like **LANG="de_DE@euro"** and **LANGUAGE="de_DE:de:en_GB:en"**.
[*]**reboot your system**
[/LIST]

Now some more problem tracing description with keywords to help people, that suffered the same problems as me, and are now googling for solutions:
The original installation with German utf8 didn't let my favorite **nedit** work any more. It had been kicked always with a error message that contained *Major opcode of failed request: 70 X_PolyFillRectangle*.

My first try with */etc/environment* and */etc/default/locale* used a wrong LANG setting of **de_DE@euro ISO-8859-15** - which is totally wrong at this place, and is resulting in many many error messages that contain *Locales not supported on X server*. The correct setting is solely **de_DE@euro**.

Do **not use language-selector** or one of its frontends from QT or GTK, as they overwrite your handmade settings with utf8 settings.

I hope this helps,
isoaglib

---

### Post by ydur on 2010-09-22
Thank you very much isoaglib!
It works also with Karmic.

Rudy

---

