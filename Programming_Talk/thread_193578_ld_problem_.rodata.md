---
title: "ld problem .rodata"
date: 2006-06-10
forum: Programming Talk
---

### Post by pauljwells on 2006-06-10
I work on a largish c++ project, which ultimately links to form a single executable. On Breezy I had no problems, but trying now to compile on Dapper I get an error at link time

```
`.L206108' referenced in section `.rodata' of ./icecremo/solver/Twister.o: defined in discarded section `.gnu.linkonce.t._ZNK8icecremo4mesh7IceMeshINS_8icefluid8IceFluidEE10getGradVarERKiS6_' of ./icecremo/solver/Twister.o
collect2: ld returned 1 exit status
make[1]: *** [/home/paulwells/Icecremo-2.4.0/Bob/bin/linux/icecremo] Error 1
make[1]: Leaving directory `/tmp/paulwells/Bob/LINUX/GNU/opt'
make: *** [makefile.icecremo] Error 2
2394.6u 40.9s 42:01.19 96.6% 0+0k 0+0io 0pf+0w
```

I read on another forum that force installing an older version of binutils would cure this, but it didn't seem to make any difference.

I have to keep a virtual machine with Breezy just to work on this code and I'd like to be able to do it all in Dapper.

Can anyone help?

---

### Post by toojays on 2006-06-10
Can you show us the code which is causing the error? It will be in the function 'icecremo::mesh::IceMesh<icecremo::icefluid::IceFluid>::getGradVar(int const&, int const&) const'.

If it's a bug in binutils, you may be able to work around it by finding the const or static data which is triggering the bug, and making it non-const/static.

---

### Post by pauljwells on 2006-06-11
Here's the function. Can't see anything too unruly in there...

```
  Stype getGradVar(const int &a, const int &b) const
    {
      Stype val=0.0;
      switch(b)
	{
	case 0:
	  val = ice[a].Get_h();
	  break;
	case 1:
	  val = ice[a].Get_WaveScalar();
	  break;
	case 2:
	  val = ice[a].Get_kappa();
	  break;
	case 3:
	  val = ice[a].Get_DJP();
	  break;
	case 4:
	  val = ice[a].Get_p0();
	  break;
	}
      return val;
    }

```

---

### Post by toojays on 2006-06-11
Sorry, but I don't know. A few things to try:

*) Check that the prototype for this function matches the implementation.

*) Try adding a default case to the switch block.

*) Build your project with the gcc-3.4 toolchain. You can install this from the package manager, then just set g++-3.4 as the compiler in your Makefile.

---

