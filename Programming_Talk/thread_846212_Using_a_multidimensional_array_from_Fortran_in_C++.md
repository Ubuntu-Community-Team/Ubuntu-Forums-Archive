---
title: "Using a multidimensional array from Fortran in C++"
date: 2008-07-01
forum: Programming Talk
---

### Post by Dambrosio on 2008-07-01
I have been trying to call a Fortran Subroutine from my C++ code and I can not figure out how to reference the C++ array correctly so that Fortran can access it.
My FORTRAN subroutine is declared as this:
```
      SUBROUTINE ckengine(iprint, ifuel, ifuelflow, mach, press, temp, eqratio, 
     1     fuelflow, lengthi, lisoi, hinleti, winleti, th_div, th_div2, Xinjsi, Xinjei, 
     2     Lmixi, eta_mix, th_inj, Twalli, combprop, inpoints)
```

I have included the FORTRAN Subroutine in C++ using this declaration: 

```
extern "C"
{
	void ckengine_(double*,double*,double*,double*,double*,double*,double*,double*,
			double*,double*,double*,double*,double*,double*,double*,double*,
			double*,double*,double*,double*,int*,float[][],int*);
}
```

This is how I call it in C++

```
ckengine_(&iprint,&tempfuel,&ifuelflow,&machtemp,&pressuretemp,&temptemp,
		&eqratiotemp,&fuelflowtemp,&lengthtemp,&lisotemp,&hinlettemp,&winlettemp,&th_divtemp,
		&th_div2temp,&xinjstemp,&xinjetemp,&fmltemp,&fmbetemp,&injangletemp,&twalltemp,&itemp,test,
		&inpoints);
```

Here Is my C++ array declaration:```
float output[5][1001];
```
Here Is my FORTRAN array declaration:```
REAL combprop(5,inpoints) //inpoints ==1001
```

Thanks for the help,
Dan

---

