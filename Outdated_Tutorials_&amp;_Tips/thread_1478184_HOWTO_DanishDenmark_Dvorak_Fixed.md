---
title: "HOWTO: Danish/Denmark Dvorak Fixed"
date: 2010-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Excizted on 2010-05-09
Hello,

If you are from Denmark and use the Dvorak keyboard layout, you may be happy that Ubuntu has Dvorak right from the Ubuntu installation screen.

But, unless you don't use signs very much, unlike a programmer, you will have noticed that what should appear when you hit your keyboard, won't.

Most significant in PHP is fx the $-sign, that with the Ubuntu Danish Dvorak layout is triggered with SHIFT+4 rather than the regular Alt Gr+4.

There is a lot other bad things that I actually have forgotten, I've had it fixed for quite some time now - and now I will share it with you :)


I've got two options for you - either use my script to install it, or do it manually.

**[SIZE=5]Script[/SIZE]**

Script location: [http://excizted.lexkorbs.dk/files/danish-dvorak-fixed.tar.gz](http://excizted.lexkorbs.dk/files/danish-dvorak-fixed.tar.gz)
It takes backup before messing up your stuff - open it with gedit if you want to be sure I'm not bugging your PC ;)


[B][SIZE=5]DIY

[/SIZE][/B]Firstly, backup your existing danish keymap:
```
sudo cp /usr/share/X11/xkb/symbols/dk /usr/share/X11/xkb/symbols/dk_backup
```Now, you have to echo the new keymap into the original keymap...

Open the keymap file
```
gksudo gedit /usr/share/X11/xkb/symbols/dk
```Now paste the following into the file and save

```

// based on a keyboard map from an 'xkb/symbols/dk' file
//
// $XKeyboardConfig$
// $XFree86: xc/programs/xkbcomp/symbols/dk,v 1.3 2002/12/19 01:07:56 dawes Exp $

partial default alphanumeric_keys
xkb_symbols "basic" {

    include "latin(type2)"

    name[Group1]="Denmark";

    key <AE11>    { [      plus,   question,    plusminus, questiondown ]    };
    key <AE12>    { [dead_acute, dead_grave,          bar,    brokenbar ]    };


    key <AC10>    { [        ae,        AE,   dead_acute, dead_doubleacute ] };
    key <AC11>    { [    oslash,  Ooblique, dead_circumflex, dead_caron ]    };
    key <TLDE>    { [   onehalf,   section, threequarters,    paragraph ]    };

    key <BKSL>    { [apostrophe,   asterisk, dead_doubleacute, multiply ]    };

    key <LSGT>    { [      less,    greater,    backslash,      notsign ]    };

    include "kpdl(comma)"

    include "level3(ralt_switch)"
};

partial alphanumeric_keys
xkb_symbols "nodeadkeys" {

    include "dk(basic)"

    name[Group1]="Denmark - Eliminate dead keys";

    key <AE12>    { [     acute,      grave,          bar,       ogonek ]    };
    key <AD11>    { [     aring,      Aring,    diaeresis,       degree ]    };
    key <AD12>    { [ diaeresis, asciicircum,  asciitilde,       macron ]    };
    key <AC10>    { [        ae,         AE,        acute,  doubleacute ]    };
    key <AC11>    { [    oslash,   Ooblique,  asciicircum,        caron ]    };
    key <BKSL>    { [apostrophe,   asterisk,  doubleacute,     multiply ]    };
    key <AB08>    { [     comma,  semicolon,      cedilla,       ogonek ]    };
    key <AB09>    { [    period,      colon, periodcentered,   abovedot ]    };

};

// Copied from macintosh_vndr/dk
partial alphanumeric_keys 
xkb_symbols "mac" {

    include "dk"
    name[Group1]= "Denmark - Macintosh";

    key <SPCE>    { [    space,       space, nobreakspace, nobreakspace ]    };
    key <AB10>    { [    minus,  underscore,       hyphen,       macron ]    };
    include "kpdl(dot)"
};


partial alphanumeric_keys 
xkb_symbols "mac_nodeadkeys" {
    include "dk(mac)"
    name[Group1]= "Denmark - Macintosh, eliminate dead keys";

    key <AE12>    { [    acute,       grave,          bar,       ogonek ]    };
    key <AD12>    { [diaeresis, asciicircum,   asciitilde,  dead_macron ]    };
};

partial alphanumeric_keys 
xkb_symbols "dvorak" {
    include "us(dvorak)"

    name[Group1]= "Denmark - Dvorak";

    key <TLDE> { [      onehalf,    section,  paragraph    ] };

    key <AE01> { [        1,    exclam, exclamdown, onesuperior    ] };
    key <AE02> { [        2,    quotedbl,   at,     twosuperior    ] };
    key <AE03> { [        3,    numbersign, sterling, threesuperior ] };
    key <AE04> { [        4,    currency, dollar, onequarter    ] };
    key <AE05> { [        5,    percent,    onehalf,    onehalf    ] };
    key <AE06> { [        6,    ampersand,  threequarters, threequarters ] };
    key <AE07> { [        7,    slash,      braceleft, division    ] };
    key <AE08> { [        8,    parenleft,  bracketleft        ] };
    key <AE09> { [        9,    parenright, bracketright    ] };
    key <AE10> { [        0,    equal,        braceright        ] };
    key <AE11> { [     plus,    question,   plusminus, questiondown ] };
    key <AE12> { [       dead_acute,    dead_grave, bar, brokenbar  ] };

    key <AD01> { [       aring,    Aring,  braceright, bracketright ] };
    key <AD02> { [    comma,    semicolon, dead_cedilla, cedilla ] };
    key <AD03> { [      period,    colon,  periodcentered         ] };
    key <AD04> { [        p,    P,      thorn,    THORN         ] };
    key <AD05> { [        y,    Y,      yen             ] };
    key <AD06> { [        f,    F,      ordfeminine         ] };
    key <AD08> { [        c,    C,      copyright     ] };
    key <AD09> { [        r,    R,      registered         ] };
    key <AD11> { [  apostrophe,    asterisk ] };
    key <AD12> { [  dead_diaeresis, dead_circumflex, dead_tilde, asciitilde] };

    key <AC03> { [        e,    E,      EuroSign,    cent     ] };
    key <AC05> { [        i,    I,      idotless,       Iabovedot] };
    key <AC06> { [        d,    D,      eth,        ETH     ] };
    key <AC10> { [        s,    S,      ssharp             ] };
    key <AC11> { [    minus,    underscore, hyphen,    diaeresis] };

    key <AB01> { [       ae,    AE     ] };
    key <AB05> { [        x,    X,      multiply         ] };
    key <AB07> { [        m,    M,    mu             ] };
    key <BKSL> { [     less,    greater, backslash    ] };

    key <SPCE> { [     space,    space, nobreakspace, nobreakspace] };

    key <LSGT> { [    oslash,    Ooblique     ] };

    // fixed https://bugs.freedesktop.org/show_bug.cgi?id=4397
    include "level3(ralt_switch)"
};
```Now you just have to log out and it will be functional.
I recommend relogging asap after changing the keymap.

I hope someone will have use of this.

---

