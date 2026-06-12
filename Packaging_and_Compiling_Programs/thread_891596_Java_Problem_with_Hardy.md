---
title: "Java Problem with Hardy"
date: 2008-08-16
forum: Packaging and Compiling Programs
---

### Post by myrightangle on 2008-08-16
The following snippet does not compile under Hardy with Java version 1.6.0_07. It compiles fine on my pre-release Hardy using Java version 1.6.0_03. It also compiles on Gutsy with no problems. I found no release notes from Sun stating that they changed the way the Formatter class works. I also tried changing it to use StringBuffer but get the same error message. Any suggestions?

<--- CODE --->
import java.io.*;
import java.util.*;

public class FormatTest {
    public static void main(String[] args)
    {
        Formatter fmt = new Formatter();

        fmt.format(" %02d %02d %02d %02d %02d %02d \n",
                        1, 2, 3, 4, 5, 6 );
        System.out.println(fmt);
    }
}
<--- END CODE --->

 javac FormatTest.java 
----------
1. ERROR in FormatTest.java (at line 9)
	fmt.format(" %02d %02d %02d %02d %02d %02d \n",
	    ^^^^^^
The method format(String, Object[]) in the type Formatter is not applicable for the arguments (String, int, int, int, int, int, int)

---

### Post by myrightangle on 2008-08-19
Checking the javac version I find this:

javac -help
Eclipse Java Compiler v_774_R33x, 3.3.1

Oops! To fix I ran this:

sudo update-alternatives --config javac

Select the Sun Version.

Thanks,

---

