---
title: "LaTeX/XeTeX Question regarding fonts"
date: 2008-06-30
forum: Programming Talk
---

### Post by johnation33 on 2008-06-30
Hi everyone,

I've picked up latex and xetex recently and I love it. I'm making a resume using xetex, and I want to use the small caps Times New Roman font. Unfortunately, I only have the opentype times new roman font installed, and I don't know if it includes small caps. I've tried to use small caps code such as \textsc{inserttexthere} and what not but it just won't work. Tried following this posts instructions (although I didn't understand it all) [http://newsgroups.derkeiler.com/Archive/Comp/comp.text.tex/2008-06/msg00470.html](http://newsgroups.derkeiler.com/Archive/Comp/comp.text.tex/2008-06/msg00470.html) and small caps just refuse to work. Can anyone help me how to make small caps work for LateX/Xetex? Is my font .otf file the problem or am I coding it wrong? Here my my code:

```
{\fontspec{TimesNewRomanMTStd}
{\normalsize E{\fontspec[SmallCapsFeatures={Letters=SmallCaps}]{TimesNewRomanMTStd}\textsc{DUCATION}}}}\vspace{0.025in}\hline

```

Thanks for your help in advance :)

---

### Post by johnation33 on 2008-06-30
Just to clarify, I'm trying to make the word EDUCATION all caps with E big caps and DUCATION small caps all in TimesNewRoman.

---

### Post by shifty2 on 2008-06-30
Bit of advice, if you didn't already know, there is a "resume" documentclass that you can install - works very nicely. 

Additionally, I always thought the mantra with latex was along the lines of if its getting messy to do it, you shouldn't be doing it (from a typographical point of view). 

Sorry to not  help with the actual question :)

---

### Post by johnation33 on 2008-06-30
haha no problem although what you say is true, I'm not using Latex. I'm using XeTeX which I believe is based off of Latex but is different because it allows me to use Unicode fonts (asian fonts) as well as use a different font besides arial or computer modern/4 other supplied in Latex. That's the biggest problem I found with Latex, using an opentype already installed on your computer is a 25step conversion to TYpe1 font process which I find too time-consuming. XeTeX has all the benefits of LaTeX and I get to use my own fonts. Anyways, you are philosophically right although i believe LateX does have its own small caps function for its computer modern font.

---

### Post by johnation33 on 2008-06-30
and just wondering, what is this resume document class you speak of? Is it some kind of template?

---

### Post by Zugzwang on 2008-06-30
This is not a clean solution but try including the graphicx package. Then you can use the scalebox command:
```

E\scalebox{0.7}{DUCATION}

```

---

### Post by shifty2 on 2008-06-30
You use it like /documentclass{article} but its /documentclass{res}. Here are some examples of it + the file itself: [http://www.rpi.edu/dept/arc/training/latex/resumes/](http://www.rpi.edu/dept/arc/training/latex/resumes/)

---

### Post by hugmenot on 2008-07-04
You have to inspect your font file to see if it includes real small caps at all.

e.g.:

```
otfinfo --features .fonts/MinionPro-Regular.otf

aalt	Access All Alternates
c2sc	Small Capitals From Capitals
case	Case-Sensitive Forms
cpsp	Capital Spacing
dlig	Discretionary Ligatures
dnom	Denominators
fina	Terminal Forms
frac	Fractions
hist	Historical Forms
kern	Kerning
liga	Standard Ligatures
lnum	Lining Figures
numr	Numerators
onum	Oldstyle Figures
ordn	Ordinals
ornm	Ornaments
pnum	Proportional Figures
salt	Stylistic Alternates
sinf	Scientific Inferiors
size	Optical Size
smcp	Small Capitals
ss01	Stylistic Set 1
ss02	Stylistic Set 2
sups	Superscript
tnum	Tabular Figures
zero	Slashed Zero

```

The feature you need is "smcp". otfinfo is in lcdf-typetools. I hope this comes not too late.
Besides, why don&#8217;t you use Minion instead. It&#8217;s a nice default Serif for your typing.
You can fish the font out of the package of commercial Adobe Reader 8. Most people assume that it should be alright to use the font to make PDF files from reading the EULA of Adobe Reader.

---

### Post by Zugzwang on 2008-07-04
> **hugmenot said:**
> You have to inspect your font file to see if it includes real small caps at all.


...except for the scalebox solution. :)

---

### Post by hugmenot on 2008-07-04
Yeah, but he uses XeTeX, and I can hence assume that he has an eye for typographic quality. Fake small caps [are a poor hack]("http://nitens.org/taraborelli/latex#smallcaps") that have no place in a professional resume.

---

### Post by nitro_n2o on 2008-07-04
> **johnation33 said:**
> Just to clarify, I'm trying to make the word EDUCATION all caps with E big caps and DUCATION small caps all in TimesNewRoman.
use the small caps command \sc{Education}

---

