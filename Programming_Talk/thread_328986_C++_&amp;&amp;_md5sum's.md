---
title: "C++ &amp;&amp; md5sum's"
date: 2006-12-31
forum: Programming Talk
---

### Post by JNowka on 2006-12-31
I am wondering if there are any header files for C++ to deal with md5 sums.  I have not worked with md5 sums before, and am unsure how to go about this.  I just want to convert a password into a md5 sum for security reasons.  I don't want to do this using a file, because I am unsure if this will change the md5sum, so using md5sum that comes with Ubuntu is possibly useless.  Any help will be much appreciated.

Thank you.

---

### Post by duff on 2006-12-31
[ftp://mirror.cs.wisc.edu/pub/mirrors/ghost/packages/md5.tar.gz](ftp://mirror.cs.wisc.edu/pub/mirrors/ghost/packages/md5.tar.gz)

---

### Post by amo-ej1 on 2007-01-02
The easiest would be to steal (did i say steal ? i meant borrow ;-) ) some code from passwd:

```
apt-get source passwd
```

Which contains this function:

```

char *pw_encrypt (const char *clear, const char *salt)
{
	static char cipher[128];
	char *cp;

	cp = crypt (clear, salt);
	if (!cp) {
		/*
		 * Single Unix Spec: crypt() may return a null pointer,
		 * and set errno to indicate an error.  The caller doesn't
		 * expect us to return NULL, so...
		 */
		perror ("crypt");
		exit (1);
	}
	if (strlen (cp) != 13)
		return cp;	/* nonstandard crypt() in libc, better bail out */
	strcpy (cipher, cp);

	return cipher;
}

```

This relies on *man 3 crypt* from the libc6 package (so a basic library readily available, remember to link with -lcrypt).

---

### Post by amo-ej1 on 2007-01-02
Oh yeah, and in the same manpage, all the way down:

```

       The glibc2 version of this function has the following  additional  fea&#8208;
       tures.   If  salt is a character string starting with the three charac&#8208;
       ters "$1$" followed by at most eight characters, and optionally  termi&#8208;
       nated  by  "$",  then instead of using the DES machine, the glibc crypt
       function uses an MD5-based algorithm,  and  outputs  up  to  34  bytes,
       namely  "$1$<string>$", where "<string>" stands for the up to 8 charac&#8208;
       ters following "$1$" in the salt, followed by 22 bytes chosen from  the
       set [a–zA–Z0–9./].  The entire key is significant here (instead of only
       the first 8 bytes).

```

---

### Post by tasos on 2008-01-06
> man 3 crypt does not return the man page..
is there an extra package libc6-doc or something?
thanx

---

### Post by wolfbone on 2008-01-06
Primary documentation for glibc is in texinfo format, not man pages.

---

### Post by geirha on 2008-01-06
Install the manpages-dev package. At least the man-page for crypt is there

---

### Post by tasos on 2008-01-06
Thanx geirha..that did the trick ;)

---

