---
title: "bugs in wxGTK compiled program (GENtle)"
date: 2010-03-23
forum: Programming Talk
---

### Post by DzmitryG on 2010-03-23
I am no programmer, so I can only ask for help. There is a really good biological toolkit under GPL - [GENtle]("http://gentle.magnusmanske.de/"). It is available for Unix, Windows and MacOS. For now, the least buggy version is for Windows. The MacOS version is really slow, and the Linux one has a few major bugs. Please, help this project, to my knowledge it is the only acceptable program for Linux of the kind.

There is compiled version on the program site, it is for 32 bit. To compile from source, [read this post]("http://ubuntuforums.org/showthread.php?p=8934742#post8934742") (summary in the last reply).

Bug#1: if you "make install" it does not integrate into menu, and if you run it from the launcher - it does not draw any menus.

Bug#2: same in Windows - if you choose coiled-coils for protein, it just shuts down. To get this bug, press Ctrl-N, put any title, choose "amino acid sequence" in the drop-down menu and paste, for example, following into sequence area: PRTEINSEQWENCE

[IMG]http://img.extra.by/out.php/i44161_new.protein.png[/IMG]

And choose coiled-coil here:

[IMG]http://img.extra.by/out.php/i44162_coil.png[/IMG]

it will be gone.

Bug#3: virtual PCR. It is useful before ordering primers check if everything is fine and no copy/paste mistake. Take any DNA sequence (rename attached emd.gb.txt into emd.gb and in GENtle, press Ctrl-I and select the file), enter forward primer sequence (Ctrl-N, "any title", Primer, GTGACGCGACAACGATTCGG)

[IMG]http://img.extra.by/out.php/i44163_primer.png[/IMG]

and do similar for reverse primer sequence (TTCAGAAGAAGACAAAAGAT) and then select NM_000117 in the tree-like menu to the left and go Tools/PCR. Press green arrow down in the upper tool box and you will see both your primers selected.

[IMG]http://img.extra.by/out.php/i44164_PCR.png[/IMG]

After you press Ok, it will shut down.


Last bug is in _powerpc compiled version only (actually, haven't tested 64 bit)
Bug#4: go to Tools/Aligment - there is only cancel button, but supposed to be more:

[IMG]http://img.extra.by/out.php/i44165_Align.png[/IMG]

---

