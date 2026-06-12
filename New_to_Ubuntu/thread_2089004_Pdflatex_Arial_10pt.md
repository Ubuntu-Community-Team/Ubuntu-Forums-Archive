---
title: "Pdflatex: Arial 10pt?"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by honeybear on 2012-11-28
Hello,

My goal is to format the document with arial 11pt font.

I am wondering if it is normal that I still get times with 11pt.

I have this file into the folder to compile wiht pdflatex
[http://mirrors.ctan.org/macros/latex/contrib/pclnfss/tex/latex/pclnfss/arial.sty](http://mirrors.ctan.org/macros/latex/contrib/pclnfss/tex/latex/pclnfss/arial.sty)


```

%
\documentclass[11pt,a4paper,fleqn]{article}
\usepackage{arial}

\pagestyle{empty}
\mathindent 7.5mm
 \begin{document}

   hello world! \\

 \end{document}


```

But still I get Times and not Arial.

Same results with pdflatex and miktex. Any ideas? 

thanks in advance

---

### Post by bryncoles on 2012-11-28
Hi honeybear.  

Try installing the texlive-xetex package ```
sudo apt-get install texlive-xetex
```

Then you can include ```
\usepackage{fontspec}
\setmainfont{Arial}
```

In your preamble before \begin{document}, and you should be good to go!

---

### Post by honeybear on 2012-11-30
I made it with familyfonts

however I cannot change into a doc the font size. It is defined in doc class at beginning for all doc.

---

