---
title: "GSL Shell release 0.6"
date: 2009-10-16
forum: Programming Talk
---

### Post by fr4nko on 2009-10-16
Hi all,

I'm glad to announce to the Ubuntu community the release of GSL Shell 0.6alpha. This new version features, among other things:

[LIST]
[*]a complete interface to perform Fast Fourier Transform of real and complex data with a simple interface
[*]a complete interface to numerical integration routines, including weighted functions and indefinite integrals
[/LIST]

GSL Shell is current usable for many common tasks without any problem. A lot of work is still needed to implement some GSL modules but the GSL modules implemented are fully functional and documented.

With GSL Shell you can very easily use the GSL routines with the full power of Lua scripting language. By using Lua you are free to define even complex functions to perform elaborate computations on structured data and use, at the same time, the GSL routines for performing numerical computations.

The documentation system used by GSL Shell is reStructured Text and Sphinx, both are Python projects. With Sphinx you can produce high quality HTML and Latex documentation by using a **very** simple textual format.

For more information on GSL Shell you can visit the [GSL website]("http://www.nongnu.org/gsl-shell/"), or the GSL shell [project page]("https://savannah.nongnu.org/projects/gsl-shell/") at Savannah.

You can also checkout the Subversion repository:

svn co svn://svn.sv.gnu.org/gsl-shell

I'm also looking for **volunteers** to further develop GSL Shell. A lot of works has to be done to create the interface to many modules like Random numbers, Eigenvalues, Simulated annealing, Special Functions and many others. I need also help to improve and complete the documentation.

Thank you very much in any case for your attention.

Best regards,
Francesco

---

### Post by fr4nko on 2009-10-17
I give just another chance to this announcement ;)

---

