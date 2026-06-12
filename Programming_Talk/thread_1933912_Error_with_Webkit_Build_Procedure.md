---
title: "Error with Webkit Build Procedure"
date: 2012-03-01
forum: Programming Talk
---

### Post by yugandharbabu on 2012-03-01
Hi everybody,

I am new to Linux. I downloaded the WebKit source code from [here]("http://nightly.webkit.org/"). I am building the source code with help of [this]("https://help.ubuntu.com/community/WebKit").

After executing below command, i got errors related to glib-2.31.2.
./autogen.sh --prefix=/usr
I solved those errors and again issued above command. I got below errors.

[FONT=Courier New]checking for ZLIB... configure: error: Package requirements (zlib) were not met:

No package 'zlib' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ZLIB_CFLAGS
and ZLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/FONT]

I searched in many forums for this problem, but no use. Please help me regarding this. Thanks

---

### Post by Zugzwang on 2012-03-02
You might need to install the "zlib1g-dev" package: [http://packages.ubuntu.com/oneiric/zlib1g-dev](http://packages.ubuntu.com/oneiric/zlib1g-dev)

Note that [http://packages.ubuntu.com](http://packages.ubuntu.com) is a nice page to search for which packages might be missing.

---

