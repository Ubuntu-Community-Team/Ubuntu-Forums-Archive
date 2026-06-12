---
title: "malformed line 57"
date: 2013-12-16
forum: New to Ubuntu
---

### Post by deaton25 on 2013-12-16
my skype crashed
i tried to uninstall/re-install it through the software center
but then that crashed....
i was told that line 57 is malformed in source.list.The source list could not be read
i am told that there may be unmet dependencies....
i have no idea what this is about!
can  someone tell me precisely what to input at the console
step by step, paint by the numbers
otherwise its off to the repairman $$$$
or a complete re-install of the entire system
i know nothing about computers, ubuntu

---

### Post by Impavidus on 2013-12-16
So, what's in your file named /etc/apt/sources.list, specifically in line 57? It may be easiest if you post the entire file.

---

### Post by deaton25 on 2013-12-16
thanks for responding!
how do i open this file so that i can show it to you?
yes, i am that ignorant about computers
once again, thanks

---

### Post by oldos2er on 2013-12-16
Open a terminal with Ctrl-Alt-t, run ```
cat -n /etc/apt/sources.list
``` and copy and paste all the text output here.

---

### Post by Jonathan Precise on 2013-12-16
You might also try:
```
cat -n /etc/apt/sources.list | less
```
(Yes, it is "**[FONT=Courier New]| less[/FONT]**", not "[FONT=Comic Sans MS]less[/FONT]". [Boring/technical explanation about to come. Skip the rest of this parenthesis if it gets too technical/boring.]This is called a pipeline, where you can pipe functions to others. The less command uses lesspipe.) so you can scroll down (with the up/down keyboard buttons, as the command "**[FONT=Courier New]| less[/FONT]**" does not use scrollbars :( [noparse] )[/noparse].

Also post any output (what text comes up after running the command) with [noparse]```

```[/noparse] tags:

```
This text is in code tags
```

([noparse]```
This text is in code tags
```[/noparse])

Or you could do [FONT=courier new]pastebinit /etc/apt/souces.list[/FONT] and indicate the url.

---

### Post by deaton25 on 2013-12-16
alan@alan-Latitude-D530:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted
     6	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    11	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
    17	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
    18	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe
    19	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
    27	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
    28	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    29	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    37	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    38	
    39	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    40	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    41	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    42	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    43	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    44	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    51	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    57	deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
    58	deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner













SHOULDN'T LINES 57 AND 58 READ 'ubuntu precise partner' not 'partner'. If that is true, how would I make the changes?
thanks, alan

---

### Post by deaton25 on 2013-12-16
```
alan@alan-Latitude-D530:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted
     6	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    11	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
    17	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
    18	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe
    19	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
    27	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
    28	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    29	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    37	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    38	
    39	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    40	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    41	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    42	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    43	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    44	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    51	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    57	deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
    58	deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner
```

I think lines 57 and 58 are supposed to read 'ubuntu precise partner' not 'partner' >But if that's correct, precisely how would i change the code? thanks!

---

### Post by Impavidus on 2013-12-16
That's correct, you have to insert 'ubuntu precise'. Watch the location of the spaces, it should be the same way as in the other lines.

To modify the file you need your root permissions. Type in the terminal```
gksu gedit /etc/apt/sources.list
``` and hit enter. You will be prompted for your password and a text editor will open. Then modify the file and save it.

---

### Post by deaton25 on 2013-12-16
It works!!!!!!!!!!!!!!
God bless you from the bottom of my heart!!!!!!!!!
Many, many thanks
have a blessed day!

---

### Post by Jonathan Precise on 2013-12-17
> **deaton25 said:**
> It works!!!!!!!!!!!!!!
God bless you from the bottom of my heart!!!!!!!!!
Many, many thanks
have a blessed day!

Glad to see it solved! Now can you do us a favor by marking this as solved, so others will know that it is solved? (Go to "thread tools" and select "mark as solved")

---

