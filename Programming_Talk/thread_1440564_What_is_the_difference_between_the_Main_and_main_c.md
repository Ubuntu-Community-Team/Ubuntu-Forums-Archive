---
title: "What is the difference between the Main and main classes?"
date: 2010-03-27
forum: Programming Talk
---

### Post by s3a on 2010-03-27
I'm new to netbeans and I did Java-->Java Application and changed "Project Name" to MagicSquare but I did nothing else except clicking "Finish."

Here is the default code it made:
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package magicsquare;

/**
 *
 * @author
 */
**public class Main** {

    /**
     * @param args the command line arguments
     */
**    public static void main(String[] args)** {
        // TODO code application logic here
    }

}

```

I would just like to know what the difference between the two bolded lines is.

Any input would be appreciated!
Thanks in advance!

---

### Post by whoop on 2010-03-27
Main is a class, main is not a class (it's a function, the main function).
The main function is required, if you don't have it, the program you write would not know where to start (it could be viewed as the beginning of the program). main can be viewed as being a part of Main.

---

### Post by s3a on 2010-03-27
I know the main method is needed but I just wanted to confirm what the Main class was. So you're saying it's just any regular class but netbeans chose to just call it "Main," right? (because of the .main on that new package screen)

Edit: I just tested it out and that seems to be the case.

---

### Post by whoop on 2010-03-27
> **s3a said:**
> I know the main method is needed but I just wanted to confirm what the Main class was. So you're saying it's just any regular class but netbeans chose to just call it "Main?" (because of the .main on that new package screen)

We'll this is valid in java:
```


public class Testing {

    public static void main(String[] args) {
        System.out.println("testing...");
    }

}

```

---

### Post by CptPicard on 2010-03-27
> **s3a said:**
> So you're saying it's just any regular class but netbeans chose to just call it "Main," right?

In a Java application, the main method must go somewhere (everything is in a class in Java anyway), so it is common practice just to stick it onto a class called Main. That way, you can also quickly locate the "entry point" to code...

---

