---
title: "Transfering fonts"
date: 2015-04-19
forum: New to Ubuntu
---

### Post by jake62 on 2015-04-19
I have an insanely stupid question for anyone tech savvy enough to manipulate fonts. I have two computers, one with krubuntu and the other ubuntu 14.04. The Krubuntu has a courier font in which the dash is short and the Em-dash is defined. (This is the downfall of courier new and courier 10 pitch). I cannot find this font for my 14.04 computer. I tried replacing the fonts from the user/share folders and ended up nearly wrecking my OS. I know this seems like a petty issue, but as a writer, I love this font. I'd really just like to transfer the courier on Krubuntu to any computer I'm using. Also, nothing in the user/share/fonts folder on either seems to be designated &#8220;courier.&#8221;

---

### Post by uxbal on 2015-04-19
If I'm not mistaking, courier is part of the microsoft fonts, so basically:

```
sudo apt-get install ttf-mscorefonts-installer
```

...should do the trick. Accept the license, and voila, courier should be available to you.

---

### Post by Impavidus on 2015-04-19
> **uxbal said:**
> If I'm not mistaking, courier is part of the microsoft fonts, so basically:

```
sudo apt-get install ttf-mscorefonts-installer
```

...should do the trick. Accept the license, and voila, courier should be available to you.

Not really. Courier is a free font released in 1955 and one of the original 4 required fonts for Adobe PostScript from 1982 (along with Times, Helvetica and Symbol, and some italic/slanted/bold variants). As with many free things, many variants have been created. The Microsoft font is called Courier New and was introduced in 1992, along with Windows 3.1. That is the one you get from ttf-mscorefonts-installer.

On my 14.04 Xubuntu system (no MS fonts installed, only the default stuff and some additional TeX fonts, one of which home made) I find several Courier-like fonts. One of them is named "Courier" in abiword and has separate dash, n-dash and m-dash, but I can't find the file name(s) of it. Searching for "courier" in the package manager doesn't give anything useful. But it must be available from the repositories.

---

### Post by buzzingrobot on 2015-04-19
Fonts are sometimes mapped to a specific family.  Doing "fc-match courier" in a terminal should display the specific font used when Courier is requested.  Here, it's Nimbus Mono.

---

### Post by Dennis N on 2015-04-19
Have you tried font manager? It will search for and catalog all fonts, provide the file name and location of any font that you can identify through inspection of sample text, or from a search of info in the font files. 

You could also use a custom text with font manager in browsing the fonts, containing the special characteristics you want.

Transferring fonts is just copying the font file(s).

---

### Post by Impavidus on 2015-04-19
@buzzingrobot: Thanks, that helped. I tried a couple of Courier-like fonts in abiword &#8211; see attachment. It seems the OP is after the last example, which has a short dash (shorter than the en-dash) and has a separate em-dash, although Liberation Mono also has them.```
$ fc-match courier
pcrr8a.pfb: "Courier" "Regular"
$ dpkg --search pcrr8a.pfb
texlive-fonts-recommended: /usr/share/texlive/texmf-dist/fonts/type1/adobe/courier/pcrr8a.pfb
texlive-fonts-recommended: /usr/share/fonts/type1/texlive-fonts-recommended/pcrr8a.pfb
$ fc-match "Liberation Mono"
LiberationMono-Regular.ttf: "Liberation Mono" "Regular"
$ dpkg --search LiberationMono-Regular.ttf
fonts-liberation: /usr/share/fonts/truetype/liberation/LiberationMono-Regular.ttf
```So the font "Courier" in my screenshot is provided by the package **texlive-fonts-recommended** and Liberation Mono is provided by **fonts-liberation**. The package texlive-fonts-recommended is not installed by default. It contains fonts recommended for TeX, but also usable in other applications.

OP, you can try the same commands on the system which has your preferred font installed to find the name of the package providing it, and then try and install that package on your system that does not provide the font. I think handling this through the package manager is cleaner than manually installing a font.

---

### Post by jake62 on 2015-04-19
Thanks very much for all the help! You were correct Impavidus, the texlive-fonts-recommended contained the courier I was looking for. I could not find it for the life of me, so thanks again.

---

