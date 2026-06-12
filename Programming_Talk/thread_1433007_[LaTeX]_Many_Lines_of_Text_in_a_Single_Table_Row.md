---
title: "[LaTeX] Many Lines of Text in a Single Table Row"
date: 2010-03-18
forum: Programming Talk
---

### Post by covertcj on 2010-03-18
Hi,

I've been trying to create a resume in LaTeX, and have some prior experience with the language; however, I seem to have run into an issue that I do not know how to resolve.

My resume format looks something like what I have below:

                ```

               Projects
               ________________________________________________________________________
Project        Detail One                                                          Date
Name           Detail Two
               Detail Three
```

I can create te project heading and horizontal line fine, but run into issues once I start making the "tabular" structure to hold the Project name, the details, and the date. I'm trying to make it 3 columns wide, and support the project name/details having line breaks '\\' inside of a single cell. The only way I seem to be able to manage anything of the sort is by using multiple rows of the table (ex. Project & Detail One & Date \\ Name & ...) and doing some really nasty, hard to read work arounds with the text entry.

Is there a way I can make it so that a single cell of the tabular (or use another structure such as arrays or something of that sort) might have multiple lines of text that end at user defined spots?

Thanks,
Chris

---

### Post by eronisko on 2010-03-18
Hi Chris!

It depends on whether the details one, two and three can exceed one line. A universal (although not very elegant) solution might look like this:

```
\begin{tabularx}{\textwidth}{>{\raggedright}p{\1cm} X p{1cm}}

Project Name	&	Detail One \newline
			Detail Two \newline
			Detail Three
						&	Date\\
\end{tabularx}
```
Another way of doing this would be by using the [multirow package]("http://en.wikibooks.org/wiki/LaTeX/Tables#Columns_spanning_multiple_rows"), but that would probably involve arrays...


I've used tabularx instead of tabular because it makes things bit simpler with cell widths. You will obviously have to adjust the table and column sizes so they will match the title line. Again, there is more ways to do that.

More on tabularx [here]("http://www.cs.brown.edu/system/software/latex/doc/tabularx.pdf") and on tables in LaTeX [here]("http://en.wikibooks.org/wiki/LaTeX/Tables")

Hope this helps, if you have any problems, let us know :)

---

### Post by Can+~ on 2010-03-18
A not very scalable solution:

```
\begin{tabular}{| r p{0.65\textwidth} |}
```

Yes, this occupies "0.65" of the text area and the rest for the right-aligned piece.

---

### Post by slavik on 2010-03-19
I tried to do something similar. I suggest finding a different format.

---

