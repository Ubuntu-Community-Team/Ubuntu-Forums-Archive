---
title: "IDE, QT, and other stuff"
date: 2005-08-13
forum: Programming Talk
---

### Post by jsimmons on 2005-08-13
I've been a Windows C++ programmer for about 15 years, and I want to start coding for Linux. I prefer the Gnome desktop, and I want to use QT (because it's similar to MFC), but I don't want to specifically targetting KDE.

Are there any decent IDE's available for Gnome?  Can I use QT for non-desktop-specific apps?

When is QT4 going to be added to the Ubuntu repository?

---

### Post by npaladin2000 on 2005-08-13
Probably never. Who knows?  But anyway, here's some info you need:

1. GNOME is based on the GTK2 toolkit (So is XFCE)  
2. KDE is based on the Qt toolkit (you probably knew that)
3. QT apps will look terrible by default in GNOME
4. GTK2 apps tend to not looks so hot in KDE without any config either. ;)

Basically, even though it might not seem that way, by choosing a toolkit, you're tilting toward a particular DE.  The only way to avoid that is to use a "neutral" toolkit, like Tk, or maybe wxWidgets.

But first read #5

5.  You can NOT legally charge for your Qt applications unless you BUY Qt!!

I was reading their licensing terms.  I don't like them.  Now, mind you, I believe open source is good stuff and has provided us with great stuff.  But it should be up to the programmer whether or not he wants his app to be open-source, or some closed-source binary commercial app.  With Qt, you have to pay for that flexibility. And if you use their open source version, you MUST release your work as open-source.  With GTK2, you get that flexibility for free (Nothing in their licensing terms prevents you from developing a closed-source application for commercial sale if you so choose).  

I believe in open source.  But moreso, I believe in CHOICE.  Choice is good.

---

### Post by jsimmons on 2005-08-13
[QUOTE=npaladin2000]Probably never. Who knows?  But anyway, here's some info you need:

1. GNOME is based on the GTK2 toolkit (So is XFCE)  
2. KDE is based on the Qt toolkit (you probably knew that)
3. QT apps will look terrible by default in GNOME
4. GTK2 apps tend to not looks so hot in KDE without any config either. ;)

Basically, even though it might not seem that way, by choosing a toolkit, you're tilting toward a particular DE.  The only way to avoid that is to use a "neutral" toolkit, like Tk, or maybe wxWidgets.

But first read #5

5.  You can NOT legally charge for your Qt applications unless you BUY Qt!!

I was reading their licensing terms.  I don't like them.  Now, mind you, I believe open source is good stuff and has provided us with great stuff.  But it should be up to the programmer whether or not he wants his app to be open-source, or some closed-source binary commercial app.  With Qt, you have to pay for that flexibility. And if you use their open source version, you MUST release your work as open-source.  With GTK2, you get that flexibility for free (Nothing in their licensing terms prevents you from developing a closed-source application for commercial sale if you so choose).  

I believe in open source.  But moreso, I believe in CHOICE.  Choice is good.[/QUOTE]

The "difference in eye-candy" factor is one of the biggest problems with Linux, as I see it, and you're right, I was already aware of the visual problems when trying to write apps that are independent of a specific DE.  

I knew about the QT license. I work for a government contractor, and our code is open source and is available to anyone that requests it (except for the encryption stuff). However, I'm just converting it to Linux as an exercise (okay, so converting over 500,000 lines of code from Windows to Linux might be considered more than a mere "exercise" - :) ) and as a proof-of-concept.  The specific product I'll be porting is being obsoleted by a newer system, so the Linux version will probably never be seen by "the customer" unless they want to know if we can do Linux code.

---

