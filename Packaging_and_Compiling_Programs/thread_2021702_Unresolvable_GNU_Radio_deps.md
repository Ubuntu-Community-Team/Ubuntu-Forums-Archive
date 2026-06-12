---
title: "Unresolvable GNU Radio deps"
date: 2012-07-09
forum: Packaging and Compiling Programs
---

### Post by Jungle-Cat on 2012-07-09
Hi,
I am trying to build GNU Radio from source using their auto build script, for Ubuntu. Sifting through the verbose output it is because there are unresolvable dependencies through apt - namely libgruel (libgruel*, libgruel0*) and I think libgnuradio (-dev as well?)

[https://launchpad.net/ubuntu/precise/i386/libgruel-dev](https://launchpad.net/ubuntu/precise/i386/libgruel-dev)

It was removed for being buggy, and not replaced with a working one?

Any help or guidance would be appreciated (Perhaps how to just build the deps? I'm not very good with nix, already locked myself out twice...)

Thanks

Edit: I am an idiot... didn't read the output correctly. It was trying to remove it since it was being replaced from source. So now I just don't know why the script isn't installing >.> No errors.

---

### Post by mc4man on 2012-07-09
Maybe cd to the folder where the source is, there should be the build script directly in that folder 
If so at the prompt run this to re-run the script
```
./build-gnuradio -v
```
See what it fails on

---

### Post by oldos2er on 2012-07-10
Moved to Packaging and Compiling Programs.

---

