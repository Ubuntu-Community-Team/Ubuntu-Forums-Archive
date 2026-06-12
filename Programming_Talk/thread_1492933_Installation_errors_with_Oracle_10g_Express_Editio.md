---
title: "Installation errors with Oracle 10g Express Edition client."
date: 2010-05-25
forum: Programming Talk
---

### Post by ProgramErgoSum on 2010-05-25
Hi,
I want to use the Oracle 10g XE client. I am following the installation instructions as mentioned at [Installing Database Oracle XE Client]("http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm#BABFEDEI"). When I run the .sh file for my bash shell, I keep getting this error message:
```
root@machine:/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin# . ./oracle_env.sh
/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/nls_lang.sh: 112: [[: not found
/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/nls_lang.sh: 112: [[: not found

```
And, when I look up nls_lang.sh at around line 112, I see this:
```
# Detertmine the LANGUAGE_TERRITORY part of NLS_LANG
# we derive it from the current locale by inspecting the LC_ALL and
# the LANG environment variable. Other LC_* environment variables
# are not inspected.
#
if [[ -n "$LC_ALL" ]]; then
  locale=$LC_ALL
elif [[ -n "$LANG" ]]; then
  locale=$LANG
else
  locale=
fi
```

Notice the else of elif ? Is that correct ? How do I get the client working ?

---

### Post by ProgramErgoSum on 2010-05-25
Changed !/bin/sh to #!/bin/bash and the script runs fine.

---

### Post by spreeker on 2011-02-21
Thanx that was usefull ;)

---

### Post by Praveen30 on 2011-02-21
> **ProgramErgoSum said:**
> Hi,
I want to use the Oracle 10g XE client. I am following the installation instructions as mentioned at [Installing Database Oracle XE Client]("http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm#BABFEDEI"). When I run the .sh file for my bash shell, I keep getting this error message:
```
root@machine:/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin# . ./oracle_env.sh
/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/nls_lang.sh: 112: [[: not found
/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/nls_lang.sh: 112: [[: not found

```And, when I look up nls_lang.sh at around line 112, I see this:
```
# Detertmine the LANGUAGE_TERRITORY part of NLS_LANG
# we derive it from the current locale by inspecting the LC_ALL and
# the LANG environment variable. Other LC_* environment variables
# are not inspected.
#
if [[ -n "$LC_ALL" ]]; then
  locale=$LC_ALL
elif [[ -n "$LANG" ]]; then
  locale=$LANG
else
  locale=
fi
```Notice the else of elif ? Is that correct ? How do I get the client working ?

there is a very simple way here--

[http://tricksfind.blogspot.com/2011/02/how-to-install-oracle-10g-in-ubuntu.html](http://tricksfind.blogspot.com/2011/02/how-to-install-oracle-10g-in-ubuntu.html)

---

