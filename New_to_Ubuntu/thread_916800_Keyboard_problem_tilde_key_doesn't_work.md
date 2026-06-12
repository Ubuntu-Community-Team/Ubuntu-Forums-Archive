---
title: "Keyboard problem: tilde key doesn't work"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by crowhill on 2008-09-11
Hi there

I just installed Ubuntu Hardy Heron on my Dell Inspiron 6000 laptop. Everything seems fine so far except for the keyboard. During installation, I set it to the Swiss (German, dead Sun keys) layout. However, now, when I try to hit the tilde key (only works in combination with the AltGr key), nothing happens. In fact, it seems like Ubuntu doesn't know about any of the symbols on the key. It's like a dead key. I know that this key works since I have a dual boot and on the WinXP system everything is fine. Furthermore, I once had an installation of Ubuntu on this machine and the key worked fine.

I tried to set the manufacturer option (or something like this) in system, preferences, keyboard to Dell/Inspiron, but it didn't help.

Most likely, I'm going to try a re-installation of the system anyway. However, if somebody out there has an idea of how to fix this, I might reconsider ... :)

Thanks a lot in advance,
best regards,
crowhill.

---

### Post by gvartser on 2008-09-11
System -> Preferences -> Keyboard -> Layout -> Add

Layout: Switzerland
Variant: Test the different models.

/g

---

### Post by crowhill on 2008-09-11
> **gvartser said:**
> System -> Preferences -> Keyboard -> Layout -> Add

Layout: Switzerland
Variant: Test the different models.

/g

i did that but it isn't working in any of the layouts ...

weired, right!?

---

### Post by gvartser on 2008-09-11
Yes.
U sure you are using a Switzerland layout on your keyboard?

Many US residents often mix up Sweden and Switzerland.. ;)


/g

---

### Post by meborc on 2008-09-11
well... i use estonian layout... and i get the tilde key in the terminal by pressing page dn key... it works only in terminal, not anywhere else... try to see if you have the same behavior

---

### Post by Idefix82 on 2008-09-11
Have you tried pressing tilde and then space? Ubuntu doesn't display the tilde straight away, it waits whether you might want to put the tilde on top of the next letter.

---

### Post by crowhill on 2008-09-11
> **gvartser said:**
> Yes.
U sure you are using a Switzerland layout on your keyboard?

Many US residents often mix up Sweden and Switzerland.. ;)


/g
I know what you mean, I'm Swiss :)

---

### Post by crowhill on 2008-09-11
> **meborc said:**
> well... i use estonian layout... and i get the tilde key in the terminal by pressing page dn key... it works only in terminal, not anywhere else... try to see if you have the same behavior
I will try the tilde in combination with the page dn and space key as soon as I'm back home from work :)

---

### Post by simosx on 2008-09-11
> **crowhill said:**
> Hi there

I just installed Ubuntu Hardy Heron on my Dell Inspiron 6000 laptop. Everything seems fine so far except for the keyboard. During installation, I set it to the Swiss (German, dead Sun keys) layout. However, now, when I try to hit the tilde key (only works in combination with the AltGr key), nothing happens. In fact, it seems like Ubuntu doesn't know about any of the symbols on the key. It's like a dead key. I know that this key works since I have a dual boot and on the WinXP system everything is fine. Furthermore, I once had an installation of Ubuntu on this machine and the key worked fine.

I tried to set the manufacturer option (or something like this) in system, preferences, keyboard to Dell/Inspiron, but it didn't help.

Most likely, I'm going to try a re-installation of the system anyway. However, if somebody out there has an idea of how to fix this, I might reconsider ... :)

Thanks a lot in advance,
best regards,
crowhill.

Why did you choose the "Sun deadkeys" variant?
"Sun" refers to the company that makes special hardware, and is not suitable for PCs.

The source of the problem is that the layout for Sun deadkeys is missing some important information, making several keys not work at all.
Specifically,

partial alphanumeric_keys
xkb_symbols "de_Sundeadkeys" {
    // modify the basic Swiss German layout to use Sun dead keys
    include "ch(basic)"
    key <AE11> { [      apostrophe,    question,  SunFA_Acute   ] };
    key <AE12> { [    SunFA_Circum, SunFA_Grave,  SunFA_Tilde   ] };
    key <AD12> { [ SunFA_Diaeresis,      exclam, bracketright   ] };
};

There is no "SunFA_Tilde" in the sources, which makes those keys not work.

What you need is use the default CH (or FR, or DE) layouts, which have all sort of dead keys and special characters.

---

### Post by crowhill on 2008-09-11
thanks a lot for that reply, simosx. i tried all the layouts, except for the default one :) with it, everything is perfect!

have a wonderful day,
cheers,
crowhill.

---

