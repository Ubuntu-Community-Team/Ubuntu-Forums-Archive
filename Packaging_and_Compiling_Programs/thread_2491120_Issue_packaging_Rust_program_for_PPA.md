---
title: "Issue packaging Rust program for PPA"
date: 2023-09-26
forum: Packaging and Compiling Programs
---

### Post by tabulate on 2023-09-26
Hey! I'm having issues packaging my Rust program for a PPA, and I'm not sure what I'm supposed to be doing. I've read through the packaging guide and can't find anything about this. My program requires a newer version of Rust for building than is in the Ubuntu repositories, and I can't install it with curl via rustup during the build process, because the container doesn't allow for internet access it seems. I also need a newer verison of cmake, which I was trying to install via pip, however this also fails. What is the correct way to go about this? Thank you for any help, my current relevant debian/ files are below, let me know if you need something else.

```

Source: squiid
Section: math
Priority: optional
Maintainer: Connor Sample <tabulatejarl8@gmail.com>
Build-Depends: debhelper-compat (= 11), python3-pip, curl
Standards-Version: 4.6.0
Homepage: https://gitlab.com/ImaginaryInfinity/squiid-calculator/squiid
#Vcs-Browser: https://salsa.debian.org/debian/squiid
#Vcs-Git: https://salsa.debian.org/debian/squiid.git
Rules-Requires-Root: no

Package: squiid
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: Do advanced algebraic and RPN calculations.
 Advanced calculator written in Rust, featuring a terminal user interface supporting both RPN and algebraic input.

```

```

#!/usr/bin/make -f
# See debhelper(7) (uncomment to enable)
# output every command that modifies files on the build system.
export DH_VERBOSE = 1

%:
    dh $@

override_dh_auto_build:
    # install rust through rustup 
    # this fails
    @cargo --version >/dev/null 2>&1 || curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y

    cat $$HOME/.cargo/env

    python3 -m pip install scikit-build
    PIP_ONLY_BINARY=cmake python3 -m pip install cmake

    PATH="$$PATH:$$HOME/.cargo/bin" make build

override_dh_auto_test:
    PATH="$$PATH:$$HOME/.cargo/bin" dh_auto_test

override_dh_auto_install:
    PATH="$$PATH:$$HOME/.cargo/bin" dh_auto_install -- BINARY_PATH=target/release/squiid ELEVATE='' EXECUTABLE_PERMISSION='' NORMAL_PERMISSION=''

```

---

### Post by TheFu on 2023-09-27
I've never created a .deb package, so you know more about this than I do, but 
a) pip is for python, right?  cmake is "C", so it makes sense that pip can't install it.  On Debian-based systems, like Ubuntu, we use 'apt' to install things.
b) Maybe if there are so many dependencies for a simple calculator, it should be packaged as an AppImpage/Flatpak/SnapPackage, not in a PPA?

Why would a calculator package need cmake to be installed? I can see the need for the binary program and the manpage for it, but nothing else, especially since it is a terminal program, not a GUI.  Am I missing something?

---

### Post by readableauthor on 2023-09-27
I believe the correct way is to publish updated rust and cmake in your  PPA as packages (you can search launchpad to see if someone has packaged  it already). Then you'd be able to use them as dev dependencies. This  seems like a lot of work. I recommend providing a Snap package instead, which gives more freedom regarding internet access.

---

