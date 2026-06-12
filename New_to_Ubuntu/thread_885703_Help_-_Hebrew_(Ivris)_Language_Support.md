---
title: "Help - Hebrew (Ivris) Language Support"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by iaskedalice09 on 2008-08-10
First, to those fasting for Tishah B'Av, have an easy fast.

Second, I can't get Hebrew language support on here. I install the language support pack by going to System > Language Support and checking Hebrew and put the Keyboard indicator button on my task bar. Now it is USA, but when I click (hoping to change to Hebrew, or perhaps show the &#1506; letter), it doesn't. I really need Hebrew language support for email and shul projects. Right now I use Firefox extension AnyKey but it doesn't work with Thunderbird or OpenOffice. I tried the tips on [HebrewLocalizationHowto - Community Ubuntu Documentation](https://help.ubuntu.com/community/HebrewLocalizationHowto) and all went fine till Oo support. Here's what I got:

```

sudo apt-get install openoffice.org-l10n-he
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openoffice.org-l10n-he is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

But I cannot type b'Ivris in Oo.o so I must have done something wrong.

THANK YOU IN ADVANCE!!!

---

### Post by mikewhatever on 2008-08-10
Hi there, if I understand you correctly, all you want is to type in Hebrew. Language support you installed applies to interface: menus, titles, etc. It's safe to remove it if you don't use Hebrew interface. To get the Hebrew keyboard, go to System>Preferences>Keyboard Layout, Layouts (second tab) and add Israel (not sure why, but some languages there are designated by state names).

&#1489;&#1492;&#1510;&#1500;&#1495;&#1492;!

---

### Post by iaskedalice09 on 2008-08-10
> **mikewhatever said:**
> Hi there, if I understand you correctly, all you want is to type in Hebrew. Language support you installed applies to interface: menus, titles, etc. It's safe to remove it if you don't use Hebrew interface. To get the Hebrew keyboard, go to System>Preferences>Keyboard Layout, Layouts (second tab) and add Israel (not sure why, but some languages there are designated by state names).

&#1489;&#1492;&#1510;&#1500;&#1495;&#1492;!

&#1514;&#1493;&#1491;&#1492;. It worked! The ones I saw are only country names. I don't get why they have Biblical Hebrew. I wonder if it works with Spell-check.

---

### Post by iaskedalice09 on 2008-08-10
Oh, how do you switch keyboards via a keyboard shortcut (hope you understand my meaning)? It's a little hard to spot the keyboard button at the top. I saw a forum thread a long time ago but forgot where it was. Do you know how to?

---

### Post by mikewhatever on 2008-08-10
> **iaskedalice09 said:**
> Oh, how do you switch keyboards via a keyboard shortcut (hope you understand my meaning)? It's a little hard to spot the keyboard button at the top. I saw a forum thread a long time ago but forgot where it was. Do you know how to?

I think the default combination is Alt+Alt, but you can change it to something different, such as left Alt+Shift, by clicking on Layout Options while in Layout tab and opening Layout Switching (7-th from top). Just make sure to unselect the default one if you change it.

You are right, almost all languages are named after their countries there. One exception is Arabic, there is also Latin American, whatever that means.

---

### Post by iaskedalice09 on 2008-08-10
Changed it but it doesn't work. The default didn't work. What do I do?

---

### Post by mikewhatever on 2008-08-10
> **iaskedalice09 said:**
> Changed it but it doesn't work. The default didn't work. What do I do?

Not sure. Try logging out and then back in.

This is kind of odd, but Alt+Alt doesn't work for me too, but Alt+Shift does.

---

### Post by iaskedalice09 on 2008-08-10
Still doesn't work. That's OK, I just made the font for the USA/GBr/Isr bigger. No biggie.

---

