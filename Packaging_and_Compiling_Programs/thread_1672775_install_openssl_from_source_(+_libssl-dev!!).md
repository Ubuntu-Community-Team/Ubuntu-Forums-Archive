---
title: "install openssl from source (+ libssl-dev!!)"
date: 2011-01-21
forum: Packaging and Compiling Programs
---

### Post by piripillo on 2011-01-21
Hello,
i need to install openssl from source (cause i need to patch the source itself, to add support to aes-ccm), and the i need to use it to develop in c.
the problem is that now i installed it successfully, but trying to include the header files into my c program it says 
undefined reference to `EVP_sha1' (or to any openssl function i try to use)

follow what i did:
sudo aptitude remove openssl libssl-dev

unpacked the openssl library (1.0.0-beta2), and the patch
patched the source
./config --prefix=/usr
make
make install

then i run
gcc -I/usr/include `pkg-config --libs openssl` prova_prf.c -o out

and the output is
/tmp/ccLy3YJx.o: In function `PRF':
prova_prf.c:(.text+0x2b8): undefined reference to `EVP_sha1'
prova_prf.c:(.text+0x2ef): undefined reference to `HMAC'
collect2: ld returned 1 exit status
make: *** [prf] Error 1

but i included
#include <openssl/hmac.h>
#include <openssl/evp.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <openssl/pem.h>
#include <openssl/rsa.h>
#include <openssl/bn.h>
#include "/usr/include/openssl/evp.h"
#include </usr/include/openssl/hmac.h>

---

### Post by SevenMachines on 2011-01-21
Did you remember to remove the libssl library package itself?
openssl = binaries and tools
libssl-dev = development files and headers
libssl0.9.8 = Actual openssl libraries

If you forgot then the linker may be running up against mixed up openssl libraries, hence missing definitions

---

### Post by SevenMachines on 2011-01-21
Just to add, didn't removing openssl uninstall a lot of your system? It's a fairly key package. A better way is to install the new openssl libraries in parallel to a non system path and point the compiler to those instead

---

### Post by bogal on 2011-02-24
Hi,

I have just had to install openssl from source for PCI Compliance, I did not remove the previously installed openssl/libssl0.9.8 packages (roughly as SevenMachines has suggested) and everything has gone successfully!

My difference is that I installed the source version after running the following configuration call...

[INDENT][FONT="Courier New"]./config --prefix=/usr/ --openssldir=/etc/ssl shared[/FONT][/INDENT]

Does this potentially leave me open to receiving an automatic update to the openssl/libssl0.9.8 packages some time in the future which could override my source install and break things? Or will my source install remain as required now that it is in place?

Thanks.

(Hope this is ok posting into this thread rather than a new one?! My first post!)

---

### Post by SevenMachines on 2011-02-26
I'm guessing that 'make install' to /usr will install the files in essentially the same places as the deb package. So if you have the package installed, an upgrade will overwrite them. Generally better, if you need to install to /usr and not a local directory, is to create a package. Either a simple 'fake' one with checkinstall, or it should be straight forward enough to download the openssl package source and add any custom options you need to debian/rules. 
In any case, you can 'pin' the package version so it won't automatically update. If i remember correctly, openssl is a key package so its unlikely you can remove it and just use the 'make install' version.

---

### Post by bogal on 2011-02-28
Thanks SevenMachines, I've had a read up on how to 'pin' a package and found this page...

[INDENT][https://help.ubuntu.com/community/PinningHowto]("https://help.ubuntu.com/community/PinningHowto")[/INDENT]

I've now locked (or 'held' I should say) my openssl and libssl0.9.8 packages from being updated though aptitude using...

[INDENT][FONT="Courier New"]echo openssl hold | sudo dpkg --set-selections
echo libssl0.9.8 hold | sudo dpkg --set-selections[/FONT][/INDENT]

I haven't actually got any packages to be upgraded at the moment to test this process but assuming it works as described then those packages will remain at their current version, avoiding any override of my manual install.

I did look at removing the installed openssl package but it prompted me with a scarily big list of other packages that would be removed and asked me to actually type "Yes, do as I say" in order to remove openssl, as a protection against mistaken removal of such a key package!

Thanks!

---

