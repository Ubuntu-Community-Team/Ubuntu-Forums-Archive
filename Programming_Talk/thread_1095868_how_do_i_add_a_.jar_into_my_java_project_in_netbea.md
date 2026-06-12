---
title: "how do i add a .jar into my java project in netbeans?"
date: 2009-03-14
forum: Programming Talk
---

### Post by picturefreedom on 2009-03-14
hello,

I'm having trouble adding a jar file into my java source through netbeans,

i mean i've added it by right clicking the "libraries" item in the left panel.  but when i ran the code it doesn't seem to find the class.

---

### Post by Voynix on 2009-03-14
> **picturefreedom said:**
> hello,

I'm having trouble adding a jar file into my java source through netbeans,

i mean i've added it by right clicking the "libraries" item in the left panel.  but when i ran the code it doesn't seem to find the class.

In netbeans, you right click on the libraries project and click on "add jar/folder" to add the jar file to your classpath. You then need to import the library through the **import **statement. I guess you are instantiating the class and calling its methods. If you tell us which library you are using we can be more helpful.

---

### Post by picturefreedom on 2009-03-14
i'm trying to follow,

[http://www.jdmp.org/documentation/tutorial/]("http://www.jdmp.org/documentation/tutorial/")

and after googling a while back, i've reach into adding it in 

**tools** --> **Libraries** --> **add new library**.

and basically add a costum library where then i added the jar file which then i added the library to the project, but then running the code in the tutorial, i am met with this error

```

jdmpsample/src/jdmpsample/Main.java:34: unreported exception java.io.IOException; must be caught or declared to be thrown
        Matrix myData = MatrixFactory.importFromFile(FileFormat.CSV, myDataFile);
1 error
BUILD FAILED (total time: 3 seconds)





```



this is the code i'm trying to make sense about, any input is appreciated.

```


package jdmpsample;

import java.io.File;
import java.io.IOException;
import org.ujmp.core.Matrix;
import org.ujmp.core.MatrixFactory;
import org.ujmp.core.enums.FileFormat;


 


public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        
        File myDataFile = new File("formated4.csv");
        Matrix myData = MatrixFactory.importFromFile(FileFormat.CSV, myDataFile);
        
    }

}
```

---

### Post by Voynix on 2009-03-14
You seem to have imported the library correctly. The javac compiler is complaining you have not declared the exception (thrown-catch) This exception means java needs to know what to do if the file is not found, or it cannot be read. Follow the instructions. In netbeans, have a look at the editor pane, click  on the error, and select "surround with try/catch" as follows:

[php]import java.io.File;
import java.io.IOException;
import org.ujmp.core.Matrix;
import org.ujmp.core.MatrixFactory;
import org.ujmp.core.enums.FileFormat;
import org.ujmp.core.exceptions.MatrixException;

public class Main {

    public static void main(String[] args) {
        File myDataFile = new File("path_to_.csv");
        try {
            Matrix myData = MatrixFactory.importFromFile(FileFormat.CSV, myDataFile);
        } catch (MatrixException ex) {
            //
        } catch (IOException ex) {
            //
        }
    }
}[/php]Make sure you have a "csv" file in your classpath or add an absolute path.

---

### Post by picturefreedom on 2009-03-14
oh thank you! :)

it works now! :KS

---

