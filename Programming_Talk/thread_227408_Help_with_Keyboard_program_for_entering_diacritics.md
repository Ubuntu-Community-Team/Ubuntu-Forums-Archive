---
title: "Help with Keyboard program for entering diacritics"
date: 2006-08-01
forum: Programming Talk
---

### Post by urukrama on 2006-08-01
I've recently started testing Ubuntu to see whether I want to make the switch from Windows. So far, I'm pretty convinced and hooked. Unfortunately, I cannot really make the switch as I cannot run several programs I need for my work in Ubuntu 

In Windows I use a small program called Keysans to type Sanskrit transliteration, ie. roman fonts with diacritics. The program, which can be found [here](http://www.granthamandira.com/utilities/keysan.zip), is quite simple. You leave it running in the background, and whenever you press the 'input key' (any key you set, most ppl I know use control) followed by a letter you get a letter with a diacritic mark (provided you use the proper font of course). Thus "ctrl a" (not pressed simultaneously) becomes a long a (a with a line over it), etc. Keysan gives you the option to use several encodings. The one I am mostly interested in is the "America Character Map (Tamal)".

I have tried and tried running it in Wine, trying all different settings: the program loads, but doesn't really do anything. It doesn't affect the keyboard output in my text processor (OpenOffice).

Some Ubuntu user suggested I post something here, to see if someone might be able to help out. I am not a programmer, but was hoping someone could help transferring/creating such a program for Ubuntu.

---

### Post by amerikkanu on 2007-10-21
Hi,

I imagine you solved your problem long ago, but since there's no update here, and since others might find your thread trying to solve the same problem, I thought I'd mention that there's an easy way to write transliterated Sanskrit now.  I just posted about it [here]("http://ubuntuforums.org/showthread.php?t=585466").

---

### Post by Arjunanda on 2007-12-22
There are several methods - .Xmodmap, SCIM,  XKB and KXKB. Though for now none of the work for me. Some years ago I created a IAST keyboard layout for KXKB, where it was working well. Now I have modified it a bit and have tried to get it enabledt in XKB, but for some reason it just does not work. It does not display among the keyboard variants in gnome keyboard selector applet, neither can I see it in gnome keyboard preferences add layout dialog.

Here is the layout:
/etc/X11/xkb/symbols/sa
```

// based on a keyboard map from an 'xkb/symbols/fi' file
//
// $XFree86: xc/programs/xkbcomp/symbols/pc/fi,v 1.9 2003/01/29 17:17:31 dawes Exp $


partial default alphanumeric_keys
xkb_symbols "basic" {
    include "pc/latin(type2)"
    include "pc/sa(sa)"
};

partial alphanumeric_keys
xkb_symbols "sa" {

    // Based on a Finnish keyboard with dead key support and all of
    // ISO-8859-1 and ISO-8859-15 characters available.

    name[Group1]="Sanskrit";

    key <TLDE> { [ section,    onehalf,     onequarter,   threequarters	] };
    key <LSGT> { [    less,    greater,            bar,       brokenbar	] };
    // AltGr+<SPCE> is pressed accidentally too often after AltGr+<LSGT>,
    // hence AltGr+<SPCE> produces now space, not nobreakspace.
    key <SPCE> { [   space,      space,          space,    nobreakspace	] };
    key <AE01> { [       1,     exclam,     exclamdown,     onesuperior	] };
    key <AE02> { [       2,   quotedbl,             at,     twosuperior	] };
    key <AE03> { [     	 3, numbersign,       sterling,   threesuperior	] };
    key <AE04> { [       4,   currency,         dollar,	           cent	] };
    key <AE05> { [       5,    percent,       EuroSign,	      masculine	] };
    key <AE06> { [       6,  ampersand,            yen,     ordfeminine	] };
    key <AE07> { [       7,      slash,      braceleft,       plusminus	] };
    key <AE08> { [       8,  parenleft,    bracketleft,   guillemotleft	] };
    key <AE09> { [       9, parenright,   bracketright,  guillemotright	] };
    key <AE10> { [       0,      equal,     braceright,           U0325	] };
    key <AE11> { [    plus,      question,   backslash,    questiondown	] };
    key <AE12> { [ dead_acute, dead_grave, 	 U015B, 	  U015A ] };
    key <AB01> { [       z,          Z,         zcaron,	         Zcaron	] };
    key <AB02> { [       x,          X,		 U0950, 	  U0310	] };
    key <AB03> { [       c,          C,      copyright,	           cent	] };
    key <AB05> { [       b,          B,         ssharp,        NoSymbol	] };
    key <AB06> { [       n,          N,          U1E47,	          U1E46	] };
    key <AB07> { [       m,          M,          U1E40,	          U1E41	] };
    key	<AB08> { [   comma,  semicolon,		 U0325,		  U0325 ] };
    key <AB09> { [  period,      colon, 	 U0323,           U0307	] };
    key <AB10> { [   minus, underscore,         hyphen,           U0304	] };
    key <AC01> { [       a,          A,          U0101,	          U0100	] };
    key <AC02> { [       s,          S,          U1E63,           U1E62	] };
    key <AC03> { [       d,          D,          U1E0D,           U1E0C	] };
    key <AC04> { [	 f,	     F ] };
    key <AC05> { [	 g,	     G,		 U1E45,		  U1E44	] };
    key <AC06> { [       h,          H,          U1E25,           U1E24	] };
    key <AC07> { [	 j,	     J ] };
    key <AC08> { [	 k,	     K ] };
    key <AC09> { [       l,          L,          U1E39,           U1E38	] };
    key <AC10> { [ odiaeresis, Odiaeresis,      oslash,        Ooblique	] };
    key	<AC11> { [ adiaeresis, Adiaeresis,         ae,	             AE	] };
    key <AD03> { [       e,          E,       EuroSign,            cent	] };
    key <AD04> { [       r,          R,          U1E5B,           U1E5A	] };
    key <AD05> { [       t,          T,          U1E6D,           U1E6C	] };
    key <AD07> { [       u,          U,          U016B,           U016A	] };
    key <AD08> { [       i,          I,          U012B,           U012A	] };
    key <AD10> { [       p,          P,      paragraph,        NoSymbol	] };
    key <AD11> { [   aring,         Aring,         oe,		     OE	] };
    key <AD12> { [ dead_diaeresis, dead_circumflex, dead_tilde, dead_caron ] };
    key <BKSL> { [ apostrophe,   asterisk ] };

    // End alphanumeric section, begin "Keypad"
    key <KPDL> {	[  KP_Delete,	KP_Separator	]	};
    // End "Keypad" section

    key <RALT>  { type[Group1]="TWO_LEVEL",
                  [ ISO_Level3_Shift, Multi_key ]   };
    modifier_map Mod5   { <RALT> };
};

partial alphanumeric_keys
xkb_symbols "nodeadkeys" {
    include "pc/latin(type2)"
    include "pc/latin(type2_nodeadkeys)"
    include "pc/sa(sa)"

    key <AE12> { [ acute, grave ] };
    key <AD12> { [ diaeresis, asciicircum, asciitilde, caron ] };
};


```

---

