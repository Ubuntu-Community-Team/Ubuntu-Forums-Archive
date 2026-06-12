---
title: "Latex Reference to table in appendix"
date: 2008-09-10
forum: Programming Talk
---

### Post by Sportingfan on 2008-09-10
Dear,

i have got a problem when reffering to tables from the appendix in latex documents.
If i want to refer to the following table in the appendix:

```
\begin{table}[!ht]
\begin{tabular}{|l|}
...
\end{tabular}
\label{exp:mail}
\caption{...}
\end{table}
```

i will use

```
\ref{exp:mail}
```

The LateX output only returns the letter of the appendix, A. 

The appendix chapter is build with:

```
\appendix
\chapter{}
\label{appendix:a}
\input{appendixa}
```

Any ideas?

Ty

---

### Post by WW on 2008-09-10
Put the table label *after* the caption:
```

\begin{table}[!ht]
\begin{tabular}{|l|}
...
\end{tabular}
\caption{...}
\label{exp:mail}
\end{table}

```

---

### Post by Sportingfan on 2008-09-10
> **WW said:**
> Put the table label *after* the caption:
```

\begin{table}[!ht]
\begin{tabular}{|l|}
...
\end{tabular}
\caption{...}
\label{exp:mail}
\end{table}

```

That's it. :) I thaught i already tried it, but ... .

Thx!

---

