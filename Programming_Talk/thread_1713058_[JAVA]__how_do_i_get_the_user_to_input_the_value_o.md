---
title: "[JAVA]  how do i get the user to input the value of a double? (very new to java)"
date: 2011-03-23
forum: Programming Talk
---

### Post by Zeezj on 2011-03-23
:oops: i'm very new to java, and i can't seem to figure out how to have user input specify the value of a double. i've been trying to use [FONT=Courier New]System.*in*.read();[/FONT],but when i type in the double (e.g. 3) it will use the ASCII value as the value of the variable instead of what i typed. how do i do this? help!!

here is what i am trying to use this for; it's a program designed to rate your self esteem by how awesome you think you are.
```
import java.io.*;

public class AwesomeTest {
    public static void main(String[] args) throws IOException {
 

        System.out.println("on a scale of 1 to 10, how awesome are you?");
        double Awesome = System.in.read();
        
        //this next line is just to see if it uses the correct value
        System.out.println(Awesome);
        
        if ((Awesome < 6) && (Awesome > 1)) {
            System.out.println("stop being so emo and get some self esteem. try for like, 6 or above, cause anything below five is just plain emo.");
        }
    
        if ((Awesome > 6) && (Awesome < 11)) {
            System.out.println("that's pretty damn awesome. seriously, you should, like, go for the world record of awesomeness...");
        }

        if (Awesome > 11) {
            System.out.println("yeah, nice try buddy. nobody is that awesome. i said on a scale of one to TEN!");
        }

        if (Awesome < 1) {
            System.out.println("dude, you need a therapist...");
        }

    }
}

```

---

### Post by wolfgangmcq on 2011-03-23
Perhaps 
```
string AwesomeTxt = system.in.read();
int Awsome = AwsomeTxt.toInt();
```
A quick-&-dirty solution would be to subtract the ASCII value for 1, but that would cause problems if the user answered something completely batty.
However, the ubuntu forums do not seem like a good place to be asking questions about Java. Pehaps you should try your questions about Java on [Java Forums]("http://ubuntuforums.org/www.java-forums.org/") instead.

---

### Post by ve4cib on 2011-03-23
Provided you can read in a string then you can use Double.parseDouble(str) to conver the string to its equivalent double value.  That may be the easiest solution.

---

### Post by GregBrannon on 2011-03-23
Look at the Scanner method nextDouble().

I recommend that you ask your future programming questions in the Programming Talk subforum here on UF.  There are many smart, helpful people who frequent that area.

---

### Post by Zeezj on 2011-03-23
thanks guys!!! the nextDouble(); thing worked. you all get popcorn

:popcorn::popcorn::popcorn::popcorn:

---

