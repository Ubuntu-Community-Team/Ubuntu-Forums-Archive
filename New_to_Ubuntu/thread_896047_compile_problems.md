---
title: "compile problems"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by HighHat on 2008-08-20
I can't seem to compile anything from source! At first I got this error "no c+ compiler" so I installed every gcc package I could get so now I get this error  "checking for C compiler default output... configure: error: C compiler cannot create executables"

What the h_ll gives???  Please somebody HELP!

Lost in cyberspace
HighHat

---

### Post by Rolcol on 2008-08-20
Did you install the [build-essential](apt://build-essential) package?

---

### Post by Riffer on 2008-08-20
Why are you compiling?  With so many programs to choose from in the repos and so many .debs it is so rare that you need to compile.

---

### Post by Joeb454 on 2008-08-20
You need to install [build-essential]("apt://build-essential")

Clicking that link should install it for you

---

### Post by HighHat on 2008-08-20
Wow that was fast! thanks guys I'll give that a try.

Not everything is prepackaged for Ubuntu!

---

### Post by Sef on 2008-08-20
To install build-essential:

Applications > Accessories > Terminal

then copy and paste or type in this code:

```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by motang on 2008-08-20
> **HighHat said:**
> Wow that was fast! thanks guys I'll give that a try.

Not everything is prepackaged for Ubuntu!

Well if not everything is prepackaged for Ubuntu, have you tried [GetDeb.net]("http://www.getdeb.net/")?  They might have what you looking for.

---

### Post by HighHat on 2008-08-20
Ok I installed build-essential and now I get this error

*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Test for GTK failed. See the file 'INSTALL' for help
 

And when I said not everything is prepackaged I was referring to riffer's comment.

thanks for everyones help

lost
HighHat

---

### Post by HighHat on 2008-08-20
Anyone??????????????????????

---

### Post by bodhi.zazen on 2008-08-20
It would help if you told us what you are trying to compile exactly ...

---

### Post by HighHat on 2008-08-20
sag cad for one i'm trying out diff cad programs or at least trying to.

---

### Post by HighHat on 2008-08-20
anybody  please..........

---

### Post by ramjet_1953 on 2008-08-20
Sagcad IS in the repositories!

Type these commands in a terminal:

```
sudo apt-get install sagcad

sudo apt-get install sagcad-doc
```

Regards,
Roger :cool:

---

### Post by HighHat on 2008-08-21
got this message

E: Couldn't find package sagcad

besides i still want to know why i can't compile  who freakin cares if it's in the repository i want to be able to compile!

sorry for the rant
HighHat

---

### Post by oldos2er on 2008-08-21
> **HighHat said:**
> got this message

E: Couldn't find package sagcad

besides i still want to know why i can't compile  who freakin cares if it's in the repository i want to be able to compile!

sorry for the rant
HighHat

 Check your Software Sources and make sure you have the universe repository enabled; that's where sagcad is.

---

### Post by Keith Hedger on 2008-08-21
try```
apt-get build-dep sagcad
```
this will pull in the dependencies for sagcad u are just missing some development files ( the packages ending in "-dev" )

---

### Post by Keith Hedger on 2008-08-21
u may also need to enable the universe/multiverse and source repos (not sure about the source)

from the looks of it u probably also need these dev packages:
libatk1.0-dev
libc6-dev
libcairo2-dev
libgtk2.0-dev
libpango1.0-dev
ruby1.8 (ruby1.8-dev ?)

hope this helps and keep on compiling!!

---

### Post by HighHat on 2008-08-24
still won't compile and still can't find it with apt get

i give up i'll try a different CAD porog if I can get one besides graphiteone 
to install, which following the howto was quite simple(worked first try).

---

