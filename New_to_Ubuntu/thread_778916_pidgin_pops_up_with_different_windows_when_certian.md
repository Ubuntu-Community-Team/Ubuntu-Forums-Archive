---
title: "pidgin pops up with different windows when certian keys are pressed"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by steelmole on 2008-05-02
For instance when I press o instead of typing an o I get buddy information.  When I type u I get a search box.  How can I change this so I can go back to typing to people?

---

### Post by billgoldberg on 2008-05-02
I use emesene for IM, but I'm pretty sure you will be able to change short-cuts in some preferences menu (inside pidgin).

---

### Post by steelmole on 2008-05-02
Well having looked at the menu it seems the shortcut for info is ctrl-o , so it looks like I have a ctrl key coming out of no where.  

Here's my keyboard layout, I think it might be relevant:
```
partial alphanumeric_keys
xkb_symbols "dvorak-l" {

       name[Group1]= "U.S. English - Dvorak/Qwerty";

    // Alphanumeric section

    key <TLDE> { [       grave, asciitilde ]  };

    key <AE01> { [          1,  exclam   ] };
    key <AE02> { [          2,  at     ] };
    key <AE03> { [          3,  numbersign ] };
    key <AE04> { [          4,  dollar  ] };
    key <AE05> { [          5,  percent  ] };
    key <AE06> { [          6,  asciicircum  ]  };
    key <AE07> { [          7,  ampersand ] };
    key <AE08> { [          8,  asterisk ] };
    key <AE09> { [          9,  parenleft ] };
    key <AE10> { [          0,  parenright ] };
    key <AE11> { [ bracketleft, braceleft ] };
    key <AE12> { [ bracketright, braceright ]   };

    key <AD01> {
        type = "CONTROL_Q",
        symbols[Group1] = [  apostrophe, quotedbl, q ]
    };
    key <AD02> {
        type = "CONTROL_Q",
    symbols[Group1] = [ comma,  less,  w ]
    };
    key <AD03> {
        type = "CONTROL_Q",
        symbols[Group1] = [      period, greater,e ]
    };
    key <AD04> {
        type = "CONTROL_Q",
        symbols[Group1] = [         p, P,  r ]
    };
    key <AD05> {
        type = "CONTROL_Q",
        symbols[Group1] = [         y, Y, t ]
    };
    key <AD06> {
        type = "CONTROL_Q",
        symbols[Group1] = [         f, F, y ]
    };
    key <AD07> {
        type = "CONTROL_Q",
        symbols[Group1] = [         g, G, u ]
    };
    key <AD08> {
        type = "CONTROL_Q",
        symbols[Group1] = [         c, C, j ]
    };
    key <AD09> {
        type = "CONTROL_Q",
        symbols[Group1] = [         r, R, o ]
    };
    key <AD10> {
        type = "CONTROL_Q",
        symbols[Group1] = [         l, L, p ]
    };
    key <AD11> { [      slash,  question ] };
    key <AD12> { [      equal,  plus    ] };

    key <AC01> {
    type = "CONTROL_Q",
    symbols[Group1] = [     a,  A,  a  ]
    };
    key <AC02> {
    type = "CONTROL_Q",
    symbols[Group1] = [     o,  O,  s  ]
    };
    key <AC03> {
        type = "CONTROL_Q",
        symbols[Group1] = [         e, E, d ]
    };
    key <AC04> {
        type = "CONTROL_Q",
        symbols[Group1] = [         u, U, f ]
    };
    key <AC05> {
        type = "CONTROL_Q",
        symbols[Group1] = [         i, I, g ]
    };
    key <AC06> {
        type = "CONTROL_Q",
        symbols[Group1] = [         d, D, h ]
    };
    key <AC07> {
        type = "CONTROL_Q",
        symbols[Group1] = [         h, H, j ]
    };
    key <AC08> {
        type = "CONTROL_Q",
        symbols[Group1] = [         t, T, k ]
    };
    key <AC09> {
        type = "CONTROL_Q",
        symbols[Group1] = [         n, N, l ]
    };
    key <AC10> { [          s,  S      ] };
    key <AC11> { [      minus,  underscore ] };

    key <AB01> {
        type = "CONTROL_Q",
        symbols[Group1] = [   semicolon, colon, z ]
    };
    key <AB02> {
        type = "CONTROL_Q",
        symbols[Group1] = [         q, Q, x ]
    };
    key <AB03> {
        type = "CONTROL_Q",
        symbols[Group1] = [         j, J, c ]
    };
    key <AB04> {
        type = "CONTROL_Q",
        symbols[Group1] = [         k, K, v ]
    };
    key <AB05> {
        type = "CONTROL_Q",
        symbols[Group1] = [         x, X, b ]
    };
    key <AB06> {
        type = "CONTROL_Q",
        symbols[Group1] = [         b, B, n ]
    };
    key <AB07> {
        type = "CONTROL_Q",
        symbols[Group1] = [         m, M, m ]
    };
    key <AB08> { [          w,  W      ] };
    key <AB09> { [          v,  V      ] };
    key <AB10> { [          z,  Z      ] };
};
```

---

