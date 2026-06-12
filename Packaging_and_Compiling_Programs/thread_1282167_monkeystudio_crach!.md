---
title: "monkeystudio crach!"
date: 2009-10-04
forum: Packaging and Compiling Programs
---

### Post by Face_Man on 2009-10-04
hello all, 

monkeystudio  keep crashing and wouldn't start 

```


monkeystudio
Found plugin: AStyle, type: 1
Found plugin: ClassBrowser, type: 1
Found plugin: Ctags2Api, type: 1
Found plugin: FileBrowser, type: 1
Found plugin: MessageBox, type: 1
Found plugin: MkSShell, type: 1
Found plugin: PostIt, type: 1
Found plugin: ProjectHeaders, type: 1
Found plugin: RegExpEditor, type: 1
Found plugin: SearchEndReplace, type: 1
Found plugin: GNUMake, type: 8
Found plugin: MSVCMake, type: 8
Found plugin: QtAssistant, type: 2
Found plugin: QtDesigner, type: 2
Found plugin: G++, type: 16
Found plugin: Gcc, type: 16
Found plugin: GccParser, type: 1
Found plugin: MSVC, type: 16
Found plugin: PHP, type: 64
Found plugin: Python, type: 64
Found plugin: Irc, type: 1
Found plugin: PHP-Qt, type: 128
Found plugin: PyQt, type: 128
Found plugin: QMake, type: 128
User wantn't to intall plugin: AStyle
QSqlDatabase: QSQLITE driver not loaded
QSqlDatabase: available drivers: QMYSQL3 QMYSQL
"Driver not loaded Driver not loaded" 
qCtagsSense instance not initialized 
Successfully enabled plugin: ClassBrowser
User wantn't to intall plugin: Ctags2Api
Successfully enabled plugin: FileBrowser
Successfully enabled plugin: MessageBox
User wantn't to intall plugin: MkSShell
User wantn't to intall plugin: PostIt
User wantn't to intall plugin: ProjectHeaders
User wantn't to intall plugin: RegExpEditor
Successfully enabled plugin: SearchEndReplace
User wantn't to intall plugin: GNUMake
User wantn't to intall plugin: MSVCMake
QSqlDatabase: QSQLITE driver not loaded
QSqlDatabase: available drivers: QMYSQL3 QMYSQL
QSqlDatabase: QSQLITE driver not loaded
QSqlDatabase: available drivers: QMYSQL3 QMYSQL
QSqlDatabase: QSQLITE driver not loaded
QSqlDatabase: available drivers: QMYSQL3 QMYSQL
Successfully enabled plugin: QtAssistant
Successfully enabled plugin: QtDesigner
User wantn't to intall plugin: G++
User wantn't to intall plugin: Gcc
User wantn't to intall plugin: GccParser
User wantn't to intall plugin: MSVC
Successfully enabled plugin: PHP
Successfully enabled plugin: Python
User wantn't to intall plugin: Irc
Successfully enabled plugin: PHP-Qt
Successfully enabled plugin: PyQt
Successfully enabled plugin: QMake
*** glibc detected *** monkeystudio: malloc(): memory corruption: 0x0000000002248720 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fea36465dd6]
/lib/libc.so.6[0x7fea36468c0e]
/lib/libc.so.6(__libc_malloc+0x6e)[0x7fea3646a7ee]
/usr/lib/libstdc++.so.6(_Znwm+0x1d)[0x7fea36cc564d]
/usr/lib/libQtGui.so.4(_ZN5QFontC1ERK7QStringiib+0x3a)[0x7fea376b391a]
/usr/lib/libqscintilla2.so.5(_ZN9QsciLexerC2EP7QObject+0xab)[0x7fea38b4b9bb]
/usr/lib/libqscintilla2.so.5(_ZN14QsciLexerBatchC1EP7QObject+0x9)[0x7fea38b4f839]
monkeystudio(_ZN13pMonkeyStudio16lexerForLanguageERK7QString+0x25f)[0x502e6f]
monkeystudio(_ZN10UISettingsC1EP7QWidget+0xfb8)[0x485948]
monkeystudio(_ZN10QSingletonI10UISettingsE8instanceEv+0x10f)[0x5499bf]
monkeystudio(_ZN10MonkeyCore4initEv+0x91a)[0x54906a]
monkeystudio(main+0xb96)[0x53c936]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7fea3640eabd]
monkeystudio[0x4737a9]
======= Memory map: ========
00400000-006ec000 r-xp 00000000 08:01 336516                             /usr/bin/monkeystudio
008ec000-008f4000 r--p 002ec000 08:01 336516                             /usr/bin/monkeystudio
008f4000-008f9000 rw-p 002f4000 08:01 336516                             /usr/bin/monkeystudio
008f9000-008fb000 rw-p 00000000 00:00 0 
010cd000-02258000 rw-p 00000000 00:00 0                                  [heap]
7fea1a950000-7fea1a99a000 r--p 00000000 08:01 276563                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Bold.ttf
7fea1a99a000-7fea1a9e7000 r--p 00000000 08:01 276494                     /usr/share/fonts/truetype/freefont/FreeMono.ttf
7fea1a9e7000-7fea1aa36000 r--p 00000000 08:01 276564                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
7fea1aa36000-7fea1adb9000 r--p 00000000 08:01 276595                     /usr/share/fonts/truetype/unfonts/UnBatang.ttf
7fea1adb9000-7fea1add7000 r--p 00000000 08:01 276568                     /usr/share/fonts/truetype/ttf-indic-fonts-core/Malige-n.ttf
7fea1add7000-7fea1adf6000 r--p 00000000 08:01 276593                     /usr/share/fonts/truetype/ttf-kacst/mry_KacstQurn.ttf
7fea1adf6000-7fea1ae0b000 r--p 00000000 08:01 276534                     /usr/share/fonts/truetype/thai/Sawasdee.ttf
7fea1ae0b000-7fea1ae3c000 r--p 00000000 08:01 276572                     /usr/share/fonts/truetype/ttf-indic-fonts-core/Vemana.ttf
7fea1ae3c000-7fea1ae58000 r--p 00000000 08:01 311674                     /usr/share/fonts/truetype/openoffice/opens___.ttf
7fea1ae58000-7fea1af91000 r--p 00000000 08:01 276502                     /usr/share/fonts/truetype/freefont/FreeSerif.ttf
7fea1af91000-7fea1b35d000 r--p 00000000 08:01 276600                     /usr/share/fonts/truetype/vlgothic/VL-PGothic-Regular.ttf
7fea1b35d000-7fea1c000000 r--p 00000000 08:01 276601                     /usr/share/fonts/truetype/wqy/wqy-zenhei.ttc
7fea1c000000-7fea1c028000 rw-p 00000000 00:00 0 
7fea1c028000-7fea20000000 ---p 00000000 00:00 0 
7fea20045000-7fea2006a000 r--p 00000000 08:01 276530                     /usr/share/fonts/truetype/thai/Purisa.ttf
7fea2006a000-7fea200bb000 r--p 00000000 08:01 276566                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
7fea200bb000-7fea20119000 r--p 00000000 08:01 276571                     /usr/share/fonts/truetype/ttf-indic-fonts-core/Rachana_04.ttf
7fea20119000-7fea20140000 r--p 00000000 08:01 276577                     /usr/share/fonts/truetype/ttf-indic-fonts-core/utkal.ttf
7fea20140000-7fea2015a000 r--p 00000000 08:01 276578                     /usr/share/fonts/truetype/ttf-kacst/KacstArt.ttf
7fea2015a000-7fea201ca000 r--p 00000000 08:01 276498                     /usr/share/fonts/truetype/freefont/FreeSans.ttf
7fea201ca000-7fea201da000 r--p 00000000 08:01 276576                     /usr/share/fonts/truetype/ttf-indic-fonts-core/lohit_ta.ttf
7fea201da000-7fea201e0000 r--p 00000000 08:01 276575                     /usr/share/fonts/truetype/ttf-indic-fonts-core/lohit_pa.ttf
7fea201e0000-7fea201f3000 r--p 00000000 08:01 276574                     /usr/share/fonts/truetype/ttf-indic-fonts-core/lohit_hi.ttf
7fea201f3000-7fea20207000 r--p 00000000 08:01 276573                     /usr/share/fonts/truetype/ttf-indic-fonts-core/lohit_gu.ttf
7fea20207000-7fea205b0000 r--p 00000000 08:01 276599                     /usr/share/fonts/truetype/vlgothic/VL-Gothic-Regular.ttf
7fea205b0000-7fea205de000 r--p 00000000 08:01 276569                     /usr/share/fonts/truetype/ttf-indic-fonts-core/MuktiNarrow.ttf
7fea205de000-7fea205f8000 r--p 00000000 08:01 276526                     /usr/share/fonts/truetype/thai/Norasi.ttf
7fea205f8000-7fea2060d000 r--p 00000000 08:01 276560                     /usr/share/fonts/truetype/thai/Waree.ttf
7fea2060d000-7fea20621000 r--p 00000000 08:01 276643                     /usr/share/fonts/type1/gsfonts/n019003l.pfb
7fea20621000-7fea212c4000 r--p 00000000 08:01 276601                     /usr/share/fonts/truetype/wqy/wqy-zenhei.ttc
7fea212c4000-7fea212c9000 r-xp 00000000 08:01 395939                     /usr/lib/qt4/plugins/designer/libqwebview.so
7fea212c9000-7fea214c8000 ---p 00005000 08:01 395939                     /usr/lib/qt4/plugins/designer/libqwebview.so
7fea214c8000-7fea214c9000 r--p 00004000 08:01 395939                     /usr/lib/qt4/plugins/designer/libqwebview.so
7fea214c9000-7fea214ca000 rw-p 00005000 08:01 395939                     /usr/lib/qt4/plugins/designer/libqwebview.so
7fea214ca000-7fea214cc000 r-xp 00000000 08:01 909                        /lib/libutil-2.10.1.so
7fea214cc000-7fea216cb000 ---p 00002000 08:01 909                        /lib/libutil-2.10.1.so
7fea216cb000-7fea216cc000 r--p 00001000 08:01 909                        /lib/libutil-2.10.1.so
7fea216cc000-7fea216cd000 rw-p 00002000 08:01 909                        /lib/libutil-2.10.1.so
7fea216cd000-7fea21900000 r-xp 00000000 08:01 282322                     /usr/lib/libpython2.6.so.1.0
7fea21900000-7fea21aff000 ---p 00233000 08:01 282322                     /usr/lib/libpython2.6.so.1.0
7fea21aff000-7fea21b01000 r--p 00232000 08:01 282322                     /usr/lib/libpython2.6.so.1.0
7fea21b01000-7fea21b62000 rw-p 00234000 08:01 282322                     /usr/lib/libpython2.6.so.1.0
7fea21b62000-7fea21b71000 rw-p 00000000 00:00 0 
7fea21b71000-7fea21b79000 r-xp 00000000 08:01 409280                     /usr/lib/qt4/plugins/designer/libpythonplugin.so
7fea21b79000-7fea21d78000 ---p 00008000 08:01 409280                     /usr/lib/qt4/plugins/designer/libpythonplugin.so
7fea21d78000-7fea21d79000 r--p 00007000 08:01 409280                     /usr/lib/qt4/plugins/designer/libpythonplugin.so
7fea21d79000-7fea21d7a000 rw-p 00008000 08:01 409280                     /usr/lib/qt4/plugins/designer/libpythonplugin.so
7fea21d7a000-7fea21d7b000 ---p 00000000 00:00 0 Aborted (core dumped)



```

---

### Post by dinxter on 2009-10-04
is this a version you've built from source? if its the packaged version from the karmic repository then bugs should be filed [here]("https://launchpad.net/ubuntu/+source/monkeystudio").

---

### Post by dinxter on 2009-10-04
This exists in the karmic package, i've added the bug, confirm if you are using the repository package.
[https://bugs.launchpad.net/ubuntu/+source/monkeystudio/+bug/442151](https://bugs.launchpad.net/ubuntu/+source/monkeystudio/+bug/442151)

This thread should probably be in the [karmic forum]("http://ubuntuforums.org/forumdisplay.php?f=359")

[EDIT] Sorry, the karmic bug is a different one to yours by the looks of it
[ ]("http://ubuntuforums.org/forumdisplay.php?f=359")

---

### Post by dinxter on 2009-10-04
if compiled from source, did you compile it against the same version of glibc that you're running it on?

---

### Post by Face_Man on 2009-10-04
well, thx for the reply. I try fallowing the links but i didn't go anywhere.  i will move the thread to the [karmic forum]("http://ubuntuforums.org/forumdisplay.php?f=359")

---

