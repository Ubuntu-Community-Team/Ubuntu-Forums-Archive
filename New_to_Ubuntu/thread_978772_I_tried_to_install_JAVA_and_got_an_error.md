---
title: "I tried to install JAVA and got an error"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-11
hey, I tried installing Java to my ubuntu 8.10, and after ```
chmod a+x
``` and then ```
./jre_____most_up_to_date_java-rpm.bin
``` It spits out the EULA, which I accepted...and it gave me this:

```
Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-6u10-linux-i586.rpm  
error: Failed dependencies:
	/bin/basename is needed by jre-1.6.0_10-fcs.i586
	/bin/cat is needed by jre-1.6.0_10-fcs.i586
	/bin/cp is needed by jre-1.6.0_10-fcs.i586
	/bin/gawk is needed by jre-1.6.0_10-fcs.i586
	/bin/grep is needed by jre-1.6.0_10-fcs.i586
	/bin/ln is needed by jre-1.6.0_10-fcs.i586
	/bin/ls is needed by jre-1.6.0_10-fcs.i586
	/bin/mkdir is needed by jre-1.6.0_10-fcs.i586
	/bin/mv is needed by jre-1.6.0_10-fcs.i586
	/bin/pwd is needed by jre-1.6.0_10-fcs.i586
	/bin/rm is needed by jre-1.6.0_10-fcs.i586
	/bin/sed is needed by jre-1.6.0_10-fcs.i586
	/bin/sort is needed by jre-1.6.0_10-fcs.i586
	/bin/touch is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/cut is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/dirname is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/expr is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/find is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/tail is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/tr is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/wc is needed by jre-1.6.0_10-fcs.i586
	/bin/sh is needed by jre-1.6.0_10-fcs.i586
 
Done.

```

I realize its a dependency error, but do I seriously have to go through and apt-get ALL of those o.O

---

### Post by bawilson2 on 2008-11-11
Easiest way to install java is to go to the Applications->Add/Remove program and then make sure you're searching under "All available applications".  Look for "icedtea".  There should be three things that come up.  Install all three and you should be good to go.

---

### Post by taurus on 2008-11-11
Install it from the repos.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by oldos2er on 2008-11-11
Ubuntu doesn't handle RPM files well. They're meant for Red Hat and its derivatives. Ubuntu comes from Debian, which use *.deb packages instead.

 In this case, it's best to stick with the package manager.

---

### Post by SunnyRabbiera on 2008-11-11
Indeed, the RPM installer will not work.
Though the binary on Sun's website kind of stinks too thats why we have the repositories.

---

