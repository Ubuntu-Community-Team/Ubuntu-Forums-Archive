---
title: "Installing a new Engine"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Elycian on 2008-07-01
I really don't enjoy the default themes ubuntu comes with. So I've been looking at other themes and noticed a lot that I really like but all of them involve installing a new engine such as Murrina or Rezlooks and it looks like all of them are installed by using this code in the terminal

Do the normal dance to install:

	(./autogen.sh ; ) ./configure (generally --prefix=/usr, try --enable-animation); make ; make install

but whenever I do that I keep getting this for whatever engine I try
bash: syntax error near unexpected token `./configure'

Sooo... how can I install one of these engines? thanks :]

---

### Post by albeano2004 on 2008-07-01
If I'm right in thinking all you're trying to do is install a new theme, then all you need to do is:
- Download the tar.gz containing the new GTK 2.x theme
- Go to System->Preferences->Appearance
- Drag the tar.gz into the 'Appearance Preferences' window
- Click 'Apply New Theme'

Edit: I make this assumption because those two 'engines' you mention are theme names

---

### Post by nowshining on 2008-07-01
sh ./autogen.sh

that's all that's needed or ./configure - choose one, then make and sudo checkinstall -D make install to make a deb package.

or try doing what albeano said.

if u get errors on ./configure and autogen.sh more than likely u'll need to install the -dev  version of any libs it asks for.

by doing this ur compiling from source.

---

### Post by spupy on 2008-07-01
I just installed Murrina yesterday. Here how it is done:
($ before command means normal user, # is root)
go to the folder that contains the stuff
```
$ ./configure --enable-animation
$ make
# make install
```

Open the theme settings and see if a Murrine theme loads correctly.

Tip: Download this:
[http://www.cimitan.com/murrine/configurator](http://www.cimitan.com/murrine/configurator)
It is the official Murrine graphical theme editor. You can tweak Murrine themes with it.

---

### Post by nowshining on 2008-07-01
checkinstall creates a deb file for easier removal later and easier install if you do decide to re-install it.

---

### Post by mcduck on 2008-07-02
Murrine is already installed by default in Hardy Heron.

..and both Murrine and Rezlooks are in the repositories. No need to compile anything. :)

---

