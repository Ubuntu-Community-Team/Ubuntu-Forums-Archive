---
title: "[SOLVED] Does build-essential package include Fortran 90 compiler?"
date: 2008-03-11
forum: Programming Talk
---

### Post by Ryozanpaku Tiger on 2008-03-11
Dear all,

I would like to port my old codes, thus, I need a compiler for Fortran 90. I have *build-essential* package installed, but I don't see any Fortran compiler there. Which compiler do I need to install?

Thank you!

---

### Post by Jimmey on 2008-03-11
The only thing I can suggest at the moment  is to open up synaptic and search for "FORTRAN". 

I think one is included with build-essential, but cannot be sure (I'm not at my computer at the moment).

---

### Post by Ryozanpaku Tiger on 2008-03-11
Thank you, I've checked that already, and I don't see any reference to a Fortran compiler in the *build-essential* list.

---

### Post by LaRoza on 2008-03-11
No, you will need gfortran or g77.

---

### Post by Ryozanpaku Tiger on 2008-03-11
Thank you! I would like to have gfortran. Could you please tell which packages do I need to install in Synaptic Package Manager? I see gfortran and gfortran-4.2 are available. Is libgfortran2 also necessary?

---

### Post by mssever on 2008-03-11
Generally, when there's a package with a version in its name and one without, the versionless package always points to the latest version. Also, you don't need to explicitly install libs unless you need the lib for your programming work (in which case you ned the -dev version). So, gfortran is probably the package you want.

---

### Post by LaRoza on 2008-03-11
> **Ryozanpaku Tiger said:**
> Thank you! I would like to have gfortran. Could you please tell which packages do I need to install in Synaptic Package Manager? I see gfortran and gfortran-4.2 are available. Is libgfortran2 also necessary?

```

sudo aptitude install gfortran

```

That will give you everything you need. It is used like gcc, and has a man page for more information.

---

### Post by Ryozanpaku Tiger on 2008-03-12
Thank you, very much, LaRoza!

---

