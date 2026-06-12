---
title: "[SOLVED] /.profiles trouble"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Qtips on 2008-10-09
Hi everyone,

I'm installing a numerical library called Diffpack on my Ubuntu-8.04 computer box. I followed the installation instructions and all went well until this: 

```
EDITING START-UP FILES
----------------------

Edit your private start-up file(s) (~/.cshrc for (t)csh users and
~/.profile or ~/.bashrc for (ba)sh users). In this file set the
environment variable MACHINE_TYPE to the appropriate value according
to the binaries you have installed, e.g. linux-gcc-4.0.2.  
If you have Diffpack installed for several platforms, you may want to
test on the host type of host IDs in order to choose a suitable
setting of MACHINE_TYPE. After setting this variable, source the
relevant Diffpack start-up file.

  Example 1 (csh) for MACHINE_TYPE = linux-gcc-4.0.2:

    In ~/.cshrc

    setenv MACHINE_TYPE linux-gcc-4.0.2
    source /usr/local/NO/etc/setup/dpcshrc


  Example 2 (bash) for MACHINE_TYPE = linux-gcc-4.0.2:

    In ~/.profile

    export MACHINE_TYPE=linux-gcc-4.0.2
    . /usr/local/NO/etc/setup/dpshrc


(Edit the example path /usr/local/NO to reflect the path of your Diffpack
installation.) After these changes, log out and in again to activate
the changes. Test the setup by

    cd $NOR

which should lead you to the root directory of your diffpack
installation, e.g., /usr/local/NO.
```

I'm a new to Ubuntu and i don't know what i need to do in order to properly finish the installation.

Help is needed ;)

Thank you !

---

### Post by jemate18 on 2008-10-10
> **Qtips said:**
> Hi everyone,

I'm installing a numerical library called Diffpack on my Ubuntu-8.04 computer box. I followed the installation instructions and all went well until this: 

```
EDITING START-UP FILES
----------------------

Edit your private start-up file(s) (~/.cshrc for (t)csh users and
~/.profile or ~/.bashrc for (ba)sh users). In this file set the
environment variable MACHINE_TYPE to the appropriate value according
to the binaries you have installed, e.g. linux-gcc-4.0.2.  
If you have Diffpack installed for several platforms, you may want to
test on the host type of host IDs in order to choose a suitable
setting of MACHINE_TYPE. After setting this variable, source the
relevant Diffpack start-up file.

  Example 1 (csh) for MACHINE_TYPE = linux-gcc-4.0.2:

    In ~/.cshrc

    setenv MACHINE_TYPE linux-gcc-4.0.2
    source /usr/local/NO/etc/setup/dpcshrc


  Example 2 (bash) for MACHINE_TYPE = linux-gcc-4.0.2:

    In ~/.profile

    export MACHINE_TYPE=linux-gcc-4.0.2
    . /usr/local/NO/etc/setup/dpshrc


(Edit the example path /usr/local/NO to reflect the path of your Diffpack
installation.) After these changes, log out and in again to activate
the changes. Test the setup by

    cd $NOR

which should lead you to the root directory of your diffpack
installation, e.g., /usr/local/NO.
```

I'm a new to Ubuntu and i don't know what i need to do in order to properly finish the installation.


Help is needed ;)

Thank you !

can you give the complete details on how you installed this?

---

### Post by Qtips on 2008-10-10
Thanks for the reply, but i managed to find my way...i
ve contacted the compagny inuTech and he help me to properly install the numerical library.

Thanks !

---

