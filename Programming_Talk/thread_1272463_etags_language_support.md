---
title: "etags language support"
date: 2009-09-22
forum: Programming Talk
---

### Post by fieldri1 on 2009-09-22
Hi Ubuntu Gurus,
I'm not sure if this is the correct forum, but my query regards etags, so I *think* I'm in the right place!

I'm currently between jobs, so I'm using the time that I have when I'm not writing CVs and application letters to deepen my knowledge of all things Linux related. This has included brushing up my programming skills as well as LaTeX.  Reading up on etags for use within Emacs I thought that sounded like a way cool thing to use and I've been using it successfully with C, C++ and a little bit of Java.

Reading around the subject I see repeated mentions that etags should also support LaTeX, but when I run:

etags --list-languages

the resultant list is:

Asm
Asp
Awk
Basic
BETA
C
C++
C#
Cobol
Eiffel
Erlang
Fortran
HTML
Java
JavaScript
Lisp
Lua
Make
Pascal
Perl
PHP
Python
REXX
Ruby
Scheme
Sh
SLang
SML
SQL
Tcl
Vera
Verilog
Vim
YACC

with no mention of LaTeX.  Is support for LaTeX no longer provided (it wouldn't be too much of a problem really, AUCTeX and RefTeX provide a similar cross referencing functionality for LaTeX docs)?  If there is something I need to do to enable the LaTeX functionality in etags (re-instal etags after installing LaTeX possibly?) then I'd appreciate guidance on what is required.

Thanks in anticipation

Richard

---

### Post by soelvraeven on 2009-09-28
Hi,

etags has some support for LaTeX, but I had to add the following to my ~/.ctags file for complete support with Vim, i.e. jumping around labels, bibrefs etc.

Good luck with your skill brushing and job hunt :)

```

--langdef=latex
--langmap=latex:.tex .latex
--regex-latex=/^\\part[[:space:]]*(\[[^]]*\])?[[:space:]]*\{([^}]+)\}/PART \2/s,part/
--regex-latex=/^\\part[[:space:]]*\*[[:space:]]*\{([^}]+)\}/PART \1/s,part/
--regex-latex=/^\\chapter[[:space:]]*(\[[^]]*\])?[[:space:]]*\{([^}]+)\}/CHAP \2/s,chapter/
--regex-latex=/^\\chapter[[:space:]]*\*[[:space:]]*\{([^}]+)\}/CHAP \1/s,chapter/
--regex-latex=/^\\section[[:space:]]*(\[[^]]*\])?[[:space:]]*\{([^}]+)\}/\2/s,section/
--regex-latex=/^\\section[[:space:]]*\*[[:space:]]*\{([^}]+)\}/\1/s,section/
--regex-latex=/^\\subsection[[:space:]]*(\[[^]]*\])?[[:space:]]*\{([^}]+)\}/-\2/s,subsection/
--regex-latex=/^\\subsection[[:space:]]*\*[[:space:]]*\{([^}]+)\}/-\1/s,subsection/
--regex-latex=/^\\subsubsection[[:space:]]*(\[[^]]*\])?[[:space:]]*\{([^}]+)\}/--\2/s,subsubsection/
--regex-latex=/^\\subsubsection[[:space:]]*\*[[:space:]]*\{([^}]+)\}/--\1/s,subsubsection/
--regex-latex=/^\\includegraphics[[:space:]]*(\[[^]]*\])?[[:space:]]*(\[[^]]*\])?[[:space:]]*\{([^}]+)\}/\3/g,graphic/
--regex-latex=/^\\lstinputlisting[[:space:]]*(\[[^]]*\])?[[:space:]]*(\[[^]]*\])?[[:space:]]*\{([^}]+)\}/\3/i,listing/
--regex-latex=/\\label[[:space:]]*\{([^}]+)\}/\1/l,label/
--regex-latex=/\\bibitem[[:space:]]*\[([^]]*)\]\{([^}]+)\}/\1 \2/b,bibitem/

--langdef=bibtex
--langmap=bibtex:.bib
--regex-bibtex=/@string\{([^ "#%')(,=}{]+)/\1/s,BibTeX-Strings/i
--regex-bibtex=/@(article|book|booklet|inbook|incollection|inproceedings|manual|masterthesis|misc|phdthesis|proceedings|techreport|unpublished)\{([^,]+),/\2/e,BibTeX-Entries/i
--regex-bibtex=/[[:space:]]*author[[:space:]]*=[[:space:]]*("([^"]+)"|\{([^\}]+)\})[[:space:]]*,?[[:space:]]*$/\2\3/a,BibTeX-Authors/i
--regex-bibtex=/[[:space:]]*title[[:space:]]*=[[:space:]]*["\{](\{[:word:]+\}.+|.+)(["}][[:space:]]*,[[:space:]]*$|$)/\1/t,BibTeX-Titles/i

```

---

