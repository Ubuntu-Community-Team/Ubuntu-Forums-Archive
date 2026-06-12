---
title: "[Java SWING] Deadkeys and ALT-GR"
date: 2007-11-27
forum: Programming Talk
---

### Post by mzi on 2007-11-27
Hello all,

I recently decided to use Netbeans and installed all the required java packages. However, I cannot use deadkeys and ALT-GR modifier in any Swing application (other apps are fine). I use a Belgian kbd on a dell D620.

My system is:
- Kubuntu 7.10 (fresh),
- java 1.6.0_03-b05,
Relevant xorg.conf section is:
```
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"latitude" # tried "pc105" w/o success
	Option		"XkbLayout"	"be"        # tried "be-oss"
	Option		"XkbOptions"	"ctrl:swapcaps"
```
Environment variables are currently:
```
declare -x GTK_IM_MODULE="simple"
declare -x LANG="fr_BE.UTF-8"  # tried "" w/o success
declare -x LC_ALL="fr_BE.UTF-8" # tried "" w/o success
declare -x QT_IM_MODULE="simple"
declare -x XIM_PROGRAM="scim -d"
declare -x XMODIFIERS="@im=SCIM"
```
I tried tuning SCIM for a while and, as you can see, I finally disabled it.

Using an alternate AWT_TOOLKIT value
```
export AWT_TOOLKIT=MToolkit
```
lets me use ALT-GR, but not the deadkeys. Anyway, I reverted to XToolkit, since MToolkit was slower, provided poor rendering and caused events not to be transmitted correctly after a while.

I am a bit despaired, for all I have found by STFW were "miraculous" recovering from this problem...

Note that I have tried all distros form Dapper and the problem remains.

Any idea?

---

### Post by mzi on 2007-11-28
up

---

### Post by mzi on 2007-12-01
up?

---

### Post by alexroat on 2008-01-06
Hello,
I've a similar problem using netbeans with SCIM activated.
I found a solution :

JVM and AWT catch the input from UIM so is necessary to install a sort of bridge between the SCIM and the UIM.


On gutsy, install the followings packages with the line :
```

sudo apt-get install scim scim-pinyin scim-tables-zh im-switch scim-qtimm scim-bridge scim-bridge-client-gtk scim-bridge-client-qt scim-bridge-agent 

```

Then open your /etc/X11/xinit/xinput.d/scim file and modify it in matter that the result is this

```

XIM=SCIM
XIM_PROGRAM=/usr/bin/scim-bridge
XIM_ARGS="-d"
GTK_IM_MODULE=xim
QT_IM_MODULE=xim
DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangle|scim-prime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-tables-ko|scim-tables-zh"

```

You have simply to change the /usr/bin/scim in /usr/bin/scim-bridge.

In this manner all the combination captured by SCIM will be passed to UIM and then to java/AWT without any modification.

Enjoy :P

---

### Post by mzi on 2008-01-09
Well, thanks, but it does not work...

---

### Post by farseeing_oyster on 2008-11-15
as i read from here [https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/212364/comments/6](https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/212364/comments/6)

```


just start netbeans with XMODIFIERS=''
then it'll work

here's a little script to start it =)

#!/bin/bash
#change /home/samste/netbeans-6.5.rc2 to your netbeans directory
cd /home/samstre/netbeans-6.5rc2/bin/
XMODIFIERS='' ./netbeans

```

hope it's usefull
w ubuntu

---

### Post by mzi on 2008-11-15
WONDERFUL!
At last!

It works

---

### Post by ambra on 2009-02-08
It seems that you get this behavior when LC_CTYPE is set to non-US locale.
Try setting LC_CTYPE="en_US.UTF-8".

You can try starting NetBeans:
LC_CTYPE="en_US.UTF-8" ./netbeans

---

### Post by davidrogerman on 2009-05-28
Before to read this post I was fixed the problem editing /etc/scim/global and changing /SupportedUnicodeLocales = en_US.UTF-8 by /SupportedUnicodeLocales = es_ES.UTF-8. But 
still had a drawback since I press Ctrl + space in Netbeans the problem get back.

The solution of Alexroat help me to correct completely the problem (a lest it seems). Thanks.:)

---

