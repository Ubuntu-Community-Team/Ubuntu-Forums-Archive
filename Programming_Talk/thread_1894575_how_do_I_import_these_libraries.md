---
title: "how do I import these libraries?"
date: 2011-12-12
forum: Programming Talk
---

### Post by ntesla123 on 2011-12-12
I am trying to use a java application in ubuntu, but I am getting errors when I try to compile it. The app is trying to import from these libraries in the beginning:

```

import java.util.regex.Pattern;
import java.util.concurrent.TimeUnit;
import org.junit.*;
import static org.junit.Assert.*;
import static org.hamcrest.CoreMatchers.*;
import org.openqa.selenium.*;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.support.ui.Select;

```

Java doesn't recognize this. How do I install?

---

### Post by HotCupOfJava on 2011-12-13
1. Make sure these libraries are installed. Most Java libraries are packaged into .jar files.

2. When you compile, make sure the libraries are in your class path. If you are compiling from the command line, it would look something like:

```
javac -classpath "/path/to/my/library/library.jar:/path/to/another/library/another.jar:." MyApp.java
```

---

