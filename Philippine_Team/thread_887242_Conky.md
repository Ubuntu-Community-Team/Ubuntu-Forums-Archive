---
title: "Conky"
date: 2008-08-11
forum: Philippine Team
---

### Post by initial_m on 2008-08-11
Mga bro, tanung lang kung panu ko install ung Conky and uninstall, para my reference lang ako pag ni remove ko.
-di ba sya mag cause ng any prob sa system ko pag nag install ako.. tnx.:)

---

### Post by rjmdomingo2003 on 2008-08-12
Para sa installation: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

Para sa uninstall process:

1. kung via synaptic ka nag-install, go to synaptic, then, mark for removal

2. kung nag-compile ka from source, cd to the conky folder, then, sudo make uninstall

Cheers!

---

### Post by initial_m on 2008-08-12
tnx bro, try ko mag install from synaptic..:)

-bro i try to install conky on synaptic, pero di ko lam san ko sya ma eexecute. wala sa mga programs lists..

---

### Post by rjmdomingo2003 on 2008-08-12
> **initial_m said:**
> tnx bro, try ko mag install from synaptic..:)

-bro i try to install conky on synaptic, pero di ko lam san ko sya ma eexecute. wala sa mga programs lists..
First, make sure na meron kang conkyrc file sa iyong ~/

```
gedit ~/.conkyrc
```

Kung meron, then,

```
conky &
```

Kung wala, zcat mo na lang using yung instructions sa link na pinost ko, or check-out this thread for examples: [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

---

### Post by rjmdomingo2003 on 2008-08-12
Another good thread: [http://ubuntuforums.org/showthread.php?t=867076&highlight=conky](http://ubuntuforums.org/showthread.php?t=867076&highlight=conky)

---

### Post by initial_m on 2008-08-12
ganito kasi gagayahin ko bro...

---

### Post by rjmdomingo2003 on 2008-08-12
May mga katulad yan sa link na binigay ko sa 'yo.

BTW, di mo sya mahahanap sa list of programs pero you can include conky from the startup to display sa desktop.

Personally, mas preferred ko yung minimalistic conky, and not the "info overdrive".

Tyagaan mo lang basahin yung mga post na conkyrc with screenshots.

---

### Post by initial_m on 2008-08-12
tnx bro sa help at links, pero nahihirapan me.. hehehe.. script lang kasi ung mga post nila di ako ganu naiintndhan, hehehehe.. bobo ko sa english.. ahahahha:lolflag:

-btw bro, any ideas kung anung command pwede gamitin sa terminal para ma track ung mga task na ginagawa ng PC, for example network, ung live update ng mga nag rurun, sana na gets mo, hehehe.. gusto ko kasi nakabukas lagi terminal ko na gumagalaw... hehehehe.. parang sa mga movie.. hehehe...

---

### Post by rjmdomingo2003 on 2008-08-12
> **initial_m said:**
> tnx bro sa help at links, pero nahihirapan me.. hehehe.. script lang kasi ung mga post nila di ako ganu naiintndhan, hehehehe.. bobo ko sa english.. ahahahha:lolflag:

-btw bro, any ideas kung anung command pwede gamitin sa terminal para ma track ung mga task na ginagawa ng PC, for example network, ung live update ng mga nag rurun, sana na gets mo, hehehe.. gusto ko kasi nakabukas lagi terminal ko na gumagalaw... hehehehe.. parang sa mga movie.. hehehe...
Install mo through Synaptic ang htop. Then, sa terminal:
```
htop
```
:popcorn:

Yan ba hanap mo?

---

### Post by initial_m on 2008-08-12
ok tnx so much bro. pwede na rin, parang ganyan na rin, hehee, astig..
-sana mahanap mo din ako nung post ko na screen na saktong ganun sa conky nya.. gnun na kasi desktop ko, ginagaya ko un, ganda nung conky nya eh.. sana mahanap mo kung nung exact setup nung conky...tnx ulit:guitar:

---

### Post by rjmdomingo2003 on 2008-08-13
Baka eto yung hinahanap mo...

[http://ubuntuforums.org/showpost.php?p=5581351&postcount=3275](http://ubuntuforums.org/showpost.php?p=5581351&postcount=3275)

---

