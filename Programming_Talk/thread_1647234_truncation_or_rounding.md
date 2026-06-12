---
title: "truncation or rounding?"
date: 2010-12-17
forum: Programming Talk
---

### Post by worksofcraft on 2010-12-17
All the scientists seem to like numerical exponents that are multiples of 3... that way they can talk about milli volts and Mega watts, Terra bytes and nano Farads... without having to think about it...

So I made this little conversion class:
[php]
#include <math.h>

const double c2Log1000 = 9.9657842846620869892;

struct unfloat {
	double iMantissa;
	short iExponent;
	unfloat(double iD);
};

unfloat::unfloat(double iD) {
	iExponent = short( floor(log2(iD)/c2Log1000) );
	iMantissa = iD / pow(1000.0, iExponent);
	iExponent *= 3;
};

#include <cstdio>

int main(int argc, char *argv[], char *envp[]) {
	double iD;
	while (--argc) {
		sscanf(*++argv, "%lf", &iD);
		unfloat sU(iD);
		printf("%e=%lfe%d\n", iD, sU.iMantissa, sU.iExponent);
	}
	return !printf("exits normally\n");
}
[/php]

... however I just can't work out how it be affected by rounding errors... like say it is really close to moving to the next power of 3 and somehow the exponent and the mantissa fall opposite sides of the boundary ?

please if can anyone offer insights in how to make sure that never happens... my maths just ain't up to it :(

---

### Post by worksofcraft on 2010-12-17
like here you see it fail already:
```


$> ./a.out 0.0009999999999
1.000000e-03=1000.000000e-6
exits normally

```

See I want it to say 1...e-3
and not 1000....e-6 :(

---

### Post by talonmies on 2010-12-17
There are several places in that example where implicit casting to float is happening. If the original input value or the intermediate representation of it are not exactly representable as a floating point value, then your code will fail, as you have noticed.

You should change the code so that the data is preserved as double all the way through the calculation, and read the man pages for the logb and scalb functions. If you have trouble understanding them, then I would recommend reading [this]("http://docs.sun.com/source/806-3568/ncg_goldberg.html") paper first.

---

### Post by worksofcraft on 2010-12-17
> **talonmies said:**
> There are several places in that example where implicit casting to float is happening. If the original input value or the intermediate representation of it are not exactly representable as a floating point value, then your code will fail, as you have noticed.

You should change the code so that the data is preserved as double all the way through the calculation, and read the man pages for the logb and scalb functions. If you have trouble understanding them, then I would recommend reading [this]("http://docs.sun.com/source/806-3568/ncg_goldberg.html") paper first.

Thanks for that URL :)
I see it really is quite complicated and also I discovered that the standard functions dealing with this kind of thing have diverging standards between C++ and C99 :(

What I am ultimately aiming for is to break a double precision number into a rounded long integer, a "precision" that says where the decimal point should go and a decimal exponent.

Sounds really easy but it's doing my head in atm :confused:

p.s. The purpose of all this is to be able to format these numbers for different locales... so like I heard that French people use a comma instead of a decimal point and they use points as separators instead of commas and I also gather that some countries like to put separators every 4 digits and some even use different Unicode digits...

I have solved all that for long integers and now I am restructuring my experimental prototype software library into production version for general release

---

### Post by worksofcraft on 2010-12-17
Oh well so as not to get bogged down I'm going to encapsulate it in a module with the following interface (alternative suggestions welcome).
[php]
// Input:
//     iD = double precision float value to convert
//     iP = desired precision
//		i.e. (place to put the decimal point counting from ls digit)
// Output:
//     returned long representing the significant digits and sign
//     iP = actual precision adjusted if necessary
//     iX = the decimal exponent
// catering for 3 formats:

// accountants: fixed point (typically iP = 2 to give cents and dollars)
long unfloat_account(double iD, short &iP, short &iX);
// scientific: iP is a multiple of 3 to match SI units
long unfloat_science(double iD, short &iP, short &iX);
// mathematical: Always one significant digit infront of decimal point
long unfloat_math(double iD, short &iP, short &iX);
[/php]

p.s. source code module with test program included for people with floating point wizard hats.

---

