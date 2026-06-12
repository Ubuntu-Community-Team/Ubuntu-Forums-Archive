---
title: "reading a byte from a File that is not ascii in c++"
date: 2008-02-16
forum: Programming Talk
---

### Post by g3k0 on 2008-02-16
Hey, I just want to read a byte from a file.  Not as ascii. How do I do this in c++.  I tried using fscanf but for some reason the variable becomes a gigantic number.  I *know* there is a hex value of 32 right where I am reading.  I fread() it and get a 2 because 32 is ascii.  But I want to get the decimal equivalent of 32 hex instead.

```

	string MyStr;
	int YAY;

	char theC[6];
		FILE * cdRm = fopen ( "/dev/hdb", "r" );

		fseek(cdRm, 16*sectorSize+dateVolCreateOff,SEEK_SET);
		int n = fscanf ( cdRm, "%d", &YAY );

		sprintf(theC,"%d",YAY);
		fclose(cdRm);
	MyStr = theC;

```

---

### Post by Compyx on 2008-02-17
You're using a string to store the data (and presumably also to print it), use an array of unsigned char to store the data, or the C++ equivalent (Vector?) and print  the data by using the %u printf specifier (or %x for hex) and iterating the array/vector.

---

### Post by cb951303 on 2008-02-17
use fread() with a "unsigned char" ;)

---

