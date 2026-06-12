---
title: "LaTeX spaces and titles"
date: 2008-12-15
forum: Programming Talk
---

### Post by nitro_n2o on 2008-12-15
Hi all,

I'm not sure where should a general question about latex should go, but I think that since latex could be described by some BNF form then it should go into programming :)

I'm currently writing something in latex with a title using: \maketitle the problem is that latex chooses to  waste so much space above the title. Does anyone know of a solution to this problem. If I can just raise the title by 2/3 lines then I'll be good to go 

Thanks a lot

---

### Post by Zugzwang on 2008-12-15
In fact, there is no "real" LaTeX BNF that also captures the possible commands you can use. The main reason is that these are defined at runtime by the packages you load.

First of all, if you want to raise the title, try using a different document class. There's plenty of them available on the net. If you like to change some detail of an existing style, you will need to re-define commands or define your own \maketitle. The simplest way is possibly copy one of these implementations from a already existing file.

Apart from that, LaTeX customizing not a simple task since there exists no comprehensive documentation that also talks about how the internal commands interact. If you are lucky, you can find some package that does what you want.

BTW, you can also try to make your own titling using the "regular" commands:
```

\begin{center}
{\Huge Your title} \\
\textbf{Your name} \\
\today
\end{center}

```

---

### Post by nitro_n2o on 2008-12-15
Thanks a lot for the reply, i was hoping if latex could such a simple thing on its own. It turns out that this title issue is painful

i'll trust you on the BNF issue :) although in theory BNF does not tell you the command you can use, it is mere definition of acceptable syntax. The unlimited possible latex commands originate from a set of conventions that are describable in some BNF language.. 

never mind my silly BNF intro, I haven't slept for a while and I could be possibly making no sense 

Thanks again

---

### Post by 7raTEYdCql on 2008-12-15
Well i will disagree as far as the simplicity of python goes. Python is useful in almost all cases. And much easier to use than you other "Text Editors" without doubt.

---

### Post by hessiess on 2008-12-15
If you want to make the used part of the page larger, use these commands.
```

\addtolength{\textwidth}{1.5cm} %width of text
\addtolength{\textheight}{4cm} %height of text
\addtolength{\topmargin}{-1.2cm} %topmargen
```

> **i.mehrzad said:**
> Well i will disagree as far as the simplicity of python goes. Python is useful in almost all cases. And much easier to use than you other "Text Editors" without doubt.

What has python got to do with LaTeX?

---

### Post by monkeyking on 2008-12-15
> **hessiess said:**
> ...

What has python got to do with LaTeX?

My thought excatly, I guess the guy likes python :)

---

### Post by kjohansen on 2008-12-16
I use a full page style that can be customized some, it has the effect of moving the title since it expands the text range.  Not exaclty what you were asking for but I hae always found this style useful.

put this in fullpage.sty and call \usepackage{fullpage} at the top of your document.

[php]
% This is FULLPAGE.STY by H.Partl, Version 2 as of 15 Dec 1988.
% Document Style Option to fill the paper just like Plain TeX.
     
\typeout{Style Option FULLPAGE Version 2 as of 15 Dec 1988}
     
\topmargin 0pt
\advance \topmargin by -\headheight
\advance \topmargin by -\headsep
     
\textheight 8.9in
     
\oddsidemargin 0pt
\evensidemargin \oddsidemargin
\marginparwidth 0.5in
     
\textwidth 6.5in
     
     
% For users of A4 paper: The above values are suited for american 8.5x11in
% paper. If your output driver performs a conversion for A4 paper, keep
% those values. If your output driver conforms to the TeX standard (1in/1in),
% then you should add the following commands to center the text on A4 paper:
     
% \advance\hoffset by -3mm  % A4 is narrower.
% \advance\voffset by  8mm  % A4 is taller.
     
\endinput

[/php]

Note: This style file is stolen from the internet and I do not remember the source to credit.

---

