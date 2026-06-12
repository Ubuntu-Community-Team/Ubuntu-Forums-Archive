---
title: "[ANNOUNCE] new GSL Shell release / new contour plot function"
date: 2010-06-26
forum: Programming Talk
---

### Post by fr4nko on 2010-06-26
Hi all,

I'm glad to announce the release 0.10.0 of GSL Shell. This new release does improve GSL Shell in several ways to make it more reliable and simple to use.

Here a short list of the more important changes with this release of GSL Shell:

[LIST]
[*]A contour plot algorithm is implemented. It is written entirely in Lua and it is quite fast and robust. The module name is contour".
[*]An “high precision” experimental contour plot is also available. It is much more computational expensive but it draws accurate smooths curve and it does require the derivatives of the function. The module name is "hpcontour".
[*]To print an expression now you don’t need to write an ‘=’ sign  before.
[*]Some serious bugs related to the graphical window system have been fixed. Now the plotting system appears to be reliable in all situations both on Windows and on X Window.
[*]More GSL modules implemented:
  [LIST]
  [*]Basis splines
  [*]Linear Regression
  [*]Multi variables minimization
  [*]Eigensystems resolution
  [/LIST]
[/LIST]

The project documentation website address is:

[http://www.nongnu.org/gsl-shell/](http://www.nongnu.org/gsl-shell/)

In the download page you will find the source code, the windows
binaries and the documentation in HTML format.

You can test the modules by using the examples in the "examples"
directory. For example, to test the ODE module you can type:

> dofile('examples/ode.lua')
> demo1()
> demo2()

You can give a look to the examples directory to understand better how the different modules works. Some examples you may wish to try are: 'plot', 'graphics', 'fractals', 'minimize', 'contour', 'hpcontour'.

All the modules are documented in the online documentation page and the documentation can also be downloaded in HTML format from the download page.

The author has made a lot of efforts to ensure the quality of the
software and of the documentation but some bugs can be still present and the documentation can incomplete or not entirely accurate in some cases. You can help us by reporting any problem to the author.

We are also looking for volunteers so if you want to help don't hesitate to contact the author.

Enjoy,
Francesco

---

