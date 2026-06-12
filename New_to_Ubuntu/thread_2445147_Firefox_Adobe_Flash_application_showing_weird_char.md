---
title: "Firefox Adobe Flash application showing weird character"
date: 2020-06-09
forum: New to Ubuntu
---

### Post by geovani25 on 2020-06-09
Hi there,

When I access a specific page in Firefox (Lubuntu OS) which loads a Flash Player application I get the characters of the image below.

[ATTACH=CONFIG]286176[/ATTACH]

The page is [http://ce.imbil.com.br/ce/catalogoeletronico/catalogoeletronico.cfm?idioma=P](http://ce.imbil.com.br/ce/catalogoeletronico/catalogoeletronico.cfm?idioma=P) .

I've tried font settings (changing fonts and turning on/off the "Allow pages to choose their own fonts, instead of my selections above"), page encoding (which I can't change, firefox doesn't let me) and even some settings in the about:config page.

Thanks in advance.

---

### Post by monkeybrain20122 on 2020-06-09
Who is still using flash in 2020?  Moreover the page said flash 11.1.0 or greater, 11.1.0 is an ancient version so it looks like they haven't updated the webpage for a while.

---

### Post by jpf2 on 2020-06-12
will you tell me what is the best alternative to adobe flash for Firefox?
sorry kinda new at this.
jpf2

---

### Post by Holger_Gehrke on 2020-06-12
**@jpf2:** There is no alternative to Adobe Flash on the client side if a server offers content only in Flash format. If you need Flash you can install the package flashplugin-installer ('sudo apt install flashplugin-installer'). This downloads and installs the latest flash and gets regularly updated to get the latest bugfixes. The alternative on the server is obviously HTML 5 and possibly SVG for the vector elements Flash offers with lots and lots of JavaScript.  

**@geovani25:** The page works fine on my machine. Since Flash is not bound by any settings you make in the browser and can and will use whatever font the designer of the page decided on, I think the core of the problem is a font being needed that I have installed and you probably don't. Since a lot of designers don't know or care about Linux, I think they are using some font that's available on Windows. Try installing the 'Microsoft Core Fonts for the Web'. They can be installed through the package 'ttf-mscorefonts-installer' from the repositories.

Thankfully, Flash is going to go away [soon]("https://www.adobe.com/products/flashplayer/end-of-life.html").

Holger

---

### Post by guiverc on 2020-06-12
I don't know your issue, and you haven't provided your release details (a modern LXQt based Lubuntu, or legacy LXDE based, let alone the age of your software stack in use)

Looking at your image, my suspicion is you are missing a font file, thus a backup unreadable character is used maybe.  I could be wrong (flash? technically not EOL, but very close).

---

