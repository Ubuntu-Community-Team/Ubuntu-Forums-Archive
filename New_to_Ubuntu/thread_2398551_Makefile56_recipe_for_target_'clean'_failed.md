---
title: "Makefile:56: recipe for target 'clean' failed"
date: 2018-08-14
forum: New to Ubuntu
---

### Post by prateekarora2 on 2018-08-14
I'm very new to UBUNTU and I'm trying to install a .sh simulation software for my physics thesis project.
As per the general instructions, I changed the directory and gave the install command with sudo ,it wasn't working otherwise.

In the middle of installation, all of it stopped with:---

```
prateek@prateek:~/Downloads$ sudo ./candle-Install.sh

###CANDLE--------CANDLE++++++++CANDLE////////CANDLE********CANDLE###
Checking for xmkmf                                         [PASSED]

Entering WORK-DIR                                          [PASSED]
Uncompressing 'candle'                                     [PASSED]

Entering TMP-DIR                                           [PASSED]
make clean                                                 [FAILED]
Look at the files
          '/tmp/candle-root-log1' and '/tmp/candle-root-log2'
          to understand the reason for failure.
 Press <ENTER> to proceed ... 

prateek@prateek:~/Downloads$
``` 


After this, I opened the log files to check for the error and found :---

FROM File log1- (last 2 lines)--

```
tmp/candle.mY7LEW/CANDLE /tmp/candle.mY7LEW ~/Downloads
Makefile:56: recipe for target 'clean' failed
```

FROM File log2-
 
```
/bin/sh: 1: xmkmf: not found
make: *** [clean] Error 127
```

----------------------

I've tried somethings from various threads but nothing works. Please suggest a way out.
----------

P.S.-- The bash file has following commands when opened with viewer---

```
action "pushd ${NAME}" "Entering TMP-DIR"
action "make clean" "make clean"
action "make candle" "Compiling candle ..."
action "make install" "Installing candle ..."
action "popd" "Leaving TMP-DIR"

printMsg ""
action "popd" "Leaving WORK-DIR"
action "rm -rf $WRKDIR" "Cleaning up temporary files"
printMsg ""
printMsg "Happy computing ..."
printWarning "###CANDLE--------CANDLE++++++++CANDLE////////CANDLE********CANDLE###"
printMsg ""

exit 0
```

---

### Post by spjackson on 2018-08-15
> **prateekarora2 said:**
> 
 
```
/bin/sh: 1: xmkmf: not found
make: *** [clean] Error 127
```


xmkmf is in the xutils-dev package. Hence:
```

sudo apt-get install xutils-dev

```

---

### Post by prateekarora2 on 2018-08-16
it did the job. thanks a ton.

---

