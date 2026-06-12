---
title: "bibtex references not working with newclude and revtex4"
date: 2011-04-02
forum: Programming Talk
---

### Post by simon303 on 2011-04-02
Hi,

I am using the revtex4 style in latex to create my final year report.  I am using separate files for each section, but don't want a new page for each section as space is limited, so I am using the \include* statement form the package newclude.

But now any bibtex \cite command results in the citation being displayed as a letter (possible associated with the author's name), e.g. [D], not a number, e.g. [1]

Does anyone know why this is and how to stop it?

I don't want to use the \input method as I want to refer to figures, etc in previous sections.

Simon

---

### Post by ve4cib on 2011-04-02
What kind of bibliography style are you using?  The \bibliographystyle{plain} command should give you numbered references.

---

### Post by simon303 on 2011-04-02
> **ve4cib said:**
> What kind of bibliography style are you using?

I am using revtex4 with no journal specified, so the bibliography style is either the one set in revtex4 (if it sets one) or the default lates one (probably plain, if one exists).

It works (i.e. uses numbers) if I don't use newclude, but if I use newclude it doesn't work.

---

