---
title: "Need a scriptable way to get font information"
date: 2008-11-04
forum: Packaging and Compiling Programs
---

### Post by cdean on 2008-11-04
I had been using ftinfo, a program provided by the package fttools, which relied on the library libft-perl. fttools and libft-perl come from the perlftlib source package.

All was good in Hardy, but in Intrepid (and Debian Lenny), these packages were removed.

Its seems that there is no plan upstream to replace fttools ([http://webui.sourcelabs.com/debian/issues/279824](http://webui.sourcelabs.com/debian/issues/279824)). The launchpad page obviously lists it as removed/deleted ([https://launchpad.net/ubuntu/+source/perlftlib/](https://launchpad.net/ubuntu/+source/perlftlib/)).

My first instinct was to try the Hardy packages. Apparently, these packages haven't been updated since Edgy. Anyway, they were uninstallable because of a broken dependency on perlapi-5.8.8 (no installation candidate). perlapi-5.10.0 redirects to perl-core, which is obviously already installed.

A forced installation errors when I attempt to use ftinfo: ```
/usr/bin/perl: symbol lookup error: /usr/lib/perl5/auto/FreeType/FreeType.so: undefined symbol: Perl_Tstack_sp_ptr
```

I tried building from source (from [http://debian.cs.binghamton.edu/debian/pool/main/p/perlftlib/](http://debian.cs.binghamton.edu/debian/pool/main/p/perlftlib/)) but I'm tens of errors that look like this: ```
FreeType.c: In function ‘XS_FreeType_TT_Get_Glyph_Bitmap’:
FreeType.c:1271: error: static declaration of ‘XS_FreeType_TT_Get_Glyph_Pixmap’ follows non-static declaration
FreeType.c:1270: error: previous declaration of ‘XS_FreeType_TT_Get_Glyph_Pixmap’ was here
```

I could probably putz around with the C and try to fix it, but I don't have that kind of time on my hands. I could if that's the only solution, but there's got to be something else out there.

I'm not married to ftinfo at all. I simply need a program or a PHP, Python, or Java library which can give me the embedded TrueType name and style (Font Family name and Font Subfamily name, specifically) given a ttf.

Ideas? 

Is it worth my time to attempt to fix perlftlib's C errors since its functionality is somehow no longer needed in future versions of Debian/Ubuntu? 

Or is there something else out there waiting to be exploited?

---

