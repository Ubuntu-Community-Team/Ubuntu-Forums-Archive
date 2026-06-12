---
title: "LaTeX Computations?"
date: 2007-05-02
forum: Programming Talk
---

### Post by rivera151 on 2007-05-02
If this has already been invented, I've had a hell of a time trying to find it...

Wouldn't it be great to combine the abilities of two software packages, say LaTeX and Octave, to aid in computing stuff?  This would be something analogous to the functionality of MathCad.  So if I typed something like

```

A = [1, 2, 3 ; 2, -1, 1 ; 3, 0, 1 ];
B = [ 9; 8; 3 ];
X = (A^-1)*B

```

then automatically my dvi/ps/pdf file would contain the output corresponding to

```

\begin{math}
   \begin{tabular}{c}
      X=\left( 2 \\ -1 \\ 3 \right)
   \end{tabular}
\end{math}

```

Pardon any syntax errors; point them out if needed; I don't have  a TeX compiler available at this particular moment.

---

### Post by zenkaon on 2007-05-02
If you done have latex installed then do:

sudo apt-get install tetex-dev

That'll put everything you need on your pc. The check out 
[http://www.latex-project.org/guides/](http://www.latex-project.org/guides/)
for documentation

---

### Post by rivera151 on 2007-05-02
I meant I'm on a Win box (no linux) on a corporate machine (no installations allowed).  I have a great tetex installation on my home pc. :lolflag:

---

