---
title: "[latex] centering a minipage on a page"
date: 2009-12-03
forum: Programming Talk
---

### Post by green0eggs on 2009-12-03
Hello forum!

I really hope it's not annying/too off topic for me to post a LaTeX question here (I'm new to typesetting).

I want to have an introductory quote to a report I'm writing and I want it to have it's own page (which I've managed using the minipage environment) before the abstract (which also has it's own page) but I want to make it centered vertically on the page which I just can't seem to find the command for. Here's my code so far: (hopefully the preamble should be ignoreable and not effect anything)

```
%&latex


% ======= DOCUMENT PREAMBLE =======
\documentclass[a4paper,10pt]{report}

%sorts out page margins
\usepackage[a4paper]{geometry}
\geometry{top=1.0in, bottom=1.0in, left=1.0in, right=1.0in}
\usepackage{setspace}
\usepackage{amstext}
\usepackage{amsmath}
\usepackage{graphicx}

% Removes anoying word: 'Chapter' from each new chapter
%   http://www.latex-community.org/forum/viewtopic.php?f=4&t=638
\makeatletter
\renewcommand{\@makechapterhead}[1]{%
\vspace*{0 pt}%
{\setlength{\parindent}{0pt} \raggedright \normalfont
\bfseries\Huge
\ifnum \value{secnumdepth}>1 
   \if@mainmatter\thechapter \, \fi%
\fi
#1\par\nobreak\vspace{20 pt}}}
\makeatother
\setcounter{secnumdepth}{4}

%chooses nice sans serif font
\renewcommand{\rmdefault}{cmss}

% ======= TITLE PAGE VALUES =======
 \title{\begin{doublespace}\textsf{\textbf{\begin{Huge}Really impressive report title\end{Huge}\end{doublespace}}}}
 \author{\begin{LARGE}\textsf{Mr Greeneggs}\end{LARGE} \\ \begin{large}\textsf{under supervision of Prof. Brainy\end{large}}}
 \\ 
 \date{\textsf{January 2010}\\\begin{normalsize}\textsf{version date: \today}}\end{normalsize}

% ======= PREAMBLE ENDS =======
\usepackage{varioref}
\usepackage{color}

\begin{document}

% ======= TITLE PAGE =======
\maketitle

% ======= OPENING QUOTATION =======
\begin{center}
\begin{minipage}{0.5\textwidth}
  \begin{center} 
  \textbf{Opening Quote}
  \end{center}  
"This is the Dirac equation. It’s completely gorgeous."
  \begin{flushright}-- David Tong \cite{opening quote}\end{flushright}
\end{minipage}
\end{center}

% ======= ABSTRACT =======
\begin{abstract}
\centering
\begin{minipage}{0.75\textwidth}
This paper aims to ... blah
\\\\\linebreak[6]
It is submitted ...blah
\\\linebreak[5]
\begin{center} 
email@email.ac.uk\\Student ID 123456789
\end{center}
\end{minipage}
\end{abstract}

% ======= TABLE OP CONTENTS =======
\setcounter{tocdepth}{4}
\tableofcontents
```

Any suggestions and/or notes on how clunky my formatting commands are is greatly recieved.

---

### Post by Can+~ on 2009-12-03
Are you sure is not a "figure" what you want?

```
\begin{figure}[p]
	\centering
	Hello World
\end{figure}
```

That will put the "Hello World" in a separate page.

Also, your LaTeX has a lot of wrong things, I will probably edit this comment.

[LIST=1]
[*]All [FONT="Courier New"]\usepackage[/FONT] should be done right after the [FONT="Courier New"]\documentclass[/FONT], at the top of the document, for easier adding/removing, just like you do with source code.
[*]All [FONT="Courier New"]\newcommand \def[/FONT] and [FONT="Courier New"]\renewcommand[/FONT] should be done after that, and surely before the \begin{document}, this is because the same reason as above, for easier editing, specially if more people is involved, since they don't have to look for the line where it's defined, just always look on top.
[*][FONT="Courier New"]\begin{Huge}Really impressive report title\end{Huge}[/FONT]. LaTeX titles are already on the correct font size, you shouldn't mess with this. You would probably like to have title and subtitle like:
[FONT="Courier New"]\title{\textbf{Title} \\ Subtitle}[/FONT]
[*][FONT="Courier New"]"This is the Dirac equation. It’s completely gorgeous.". LaTeX quotations are done with: [FONT="Courier New"]``like this''[/FONT][/FONT]
[*][FONT="Courier New"]%Removes annoying "Chapter"[/FONT]. Chapters? Are you writing a book? Stick with article and use [FONT="Courier New"]\section[/FONT], [FONT="Courier New"]\subsection[/FONT] and [FONT="Courier New"]\subsubsection[/FONT]. Or just avoid [FONT="Courier New"]\chapter[/FONT].
[/LIST]

---

### Post by green0eggs on 2009-12-09
> **Can+~ said:**
> Are you sure is not a "figure" what you want?

```
\begin{figure}[p]
	\centering
	Hello World
\end{figure}
```

That will put the "Hello World" in a separate page.


Thanks for the advice. It turns out figure did not work ?!? But I made a separate .tex document with formatting and such to get the quote centered and used the input command with a \pagebreak before and after. This did the trick.

...BUT you definitely where right about
> **Can+~ said:**
> %Removes annoying "Chapter". Chapters? Are you writing a book? Stick with article and use \section, \subsection and \subsubsection. Or just avoid \chapter.

I was using the wrong document type... I changed to article and changed everything to sections and subsections, it now all looks much better.

Your other code-aesthetic points are because I've been using a variety of IDEs some of which are 'smart' and put usepackages that they think you need. But I've tidied it all up.

Thanks for the help!

---

