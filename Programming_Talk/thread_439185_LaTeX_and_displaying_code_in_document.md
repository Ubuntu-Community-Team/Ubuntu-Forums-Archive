---
title: "LaTeX and displaying code in document"
date: 2007-05-10
forum: Programming Talk
---

### Post by Laterix on 2007-05-10
Hi, 

I need to display code in my LaTeX document and I have problems with long code snippets. I use LaTeX-code like this:

```

\begin{figure}[htb]
	\begin{center}
		\small
		\verbatiminput{source_code.java}
		\normalsize
		\caption{This is the caption text for the code.}
		\label{fig:code_example}
	\end{center}
\end{figure}

```

This works ok with short codes, but longer codes are moved to the end of the document for some reason. Even though code and caption fits to one page. Does anyone have any good suggestions how to display code at LaTeX?

---

### Post by Laterix on 2007-05-10
I found a some kind of solutions to this problem. Now I use

```

\begin{figure}[htbp]
	\makebox[\textwidth]{\hrulefill}{
	\small
	\verbatiminput{source_file.java}
	\normalsize}
	\caption{Caption for the code.}
	\label{fig:code}
\end{figure}

```

---

### Post by tkjacobsen on 2007-05-10
I always use the 'listings' package.

You can find the manual here
[ftp://tug.ctan.org/pub/tex-archive/macros/latex/contrib/listings/listings.pdf](ftp://tug.ctan.org/pub/tex-archive/macros/latex/contrib/listings/listings.pdf)

You can tell it which language to display. It can input from source code files or you can insert code directly/manually.It also break lines nicely.

---

### Post by Laterix on 2007-05-10
> **tkjacobsen said:**
> I always use the 'listings' package.
Thanks for the tip. This sounds interesting although it won't recognize my code syntax, because this is completely new language that I discuss in my masters thesis. But I will take a look. Thanks

---

### Post by tkjacobsen on 2007-05-11
You can define your own language with \lstdefinelanguage in the .tex or \lst@definelanguage in a .sty file. You can see how it is done in existing lstlangN.sty, where N is 1,2 or 3 on my installation (using texlive). lstlang files are located in  /usr/share/texmf-texlive/tex/latex/listings (again in my installation).

---

