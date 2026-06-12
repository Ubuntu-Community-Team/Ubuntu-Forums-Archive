---
title: "How to handle references/cross-ref with Miktex/LATEX?"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by honeybear on 2012-10-31
Hi,

I would like to import the RIS, Ref. files from Elsevier or Sciencesdirect. 

How to do that with Latex, with which program?

And how to handle references in a Latex/miktex document? 

Thanks

---

### Post by Impavidus on 2012-10-31
I'm not sure what you want, but maybe you should have a look at bibtex. You can find instructions on ctan.org

---

### Post by honeybear on 2012-10-31
> **Impavidus said:**
> I'm not sure what you want, but maybe you should have a look at bibtex. You can find instructions on ctan.org

thanks 

how you you into the plain text link a ref to a fix end reference 


```
bla bla [1,3,5,7]



References:
[1] me, you, ... : book of nothing, 2050, Chicago, -4 pages.

```

---

### Post by Impavidus on 2012-10-31
For example I have here a execise.tex file containing:
```

\usepackage{cite}
(...)
See for example \cite{1995Natur.373..127M}.
(...)
\bibliography{exercise}{}
\bibliographystyle{plain}
\end{document}

```with exercise.bib containing
```

@ARTICLE{1995Natur.373..127M,
   author = {{Miyoshi}, M. and {Moran}, J. and {Herrnstein}, J. and {Greenhill}, L. and 
    {Nakai}, N. and {Diamond}, P. and {Inoue}, M.},
    title = "{Evidence for a black hole from high rotation velocities in a sub-parsec region of NGC4258}",
  journal = {\nat},
     year = 1995,
    month = jan, 
   volume = 373,
    pages = {127-129},
      doi = {10.1038/373127a0},
   adsurl = {http://adsabs.harvard.edu/abs/1995Natur.373..127M},
  adsnote = {Provided by the SAO/NASA Astrophysics Data System}
}

```taken from the abstract service of some website.

Run latex, run bibtex, run latex again (although if you're using an IDE it should go automatically) and the result looks like
```

See for example [1].

References
[1] M. Miyoshi, ...

```

---

