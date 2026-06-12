---
title: "Scanning text file and inserting contents into array"
date: 2010-03-22
forum: Programming Talk
---

### Post by jmwalloh on 2010-03-22
Hi, am trying to read a text file using scanner in java and inserting the contents into two arrays. One is 1D and the other is 2D.The content of the text file is as follows:

    [B]Nancy    -1.290 36.820
    Mom         -4.040 39.660
    Nelly       -0.280 36.070
    Kim         -0.090 34.750
    Elly         0.52  35.270
    Tom         -1.040 37.090
    Ron         -1.140 36.960
    Kelly        1.030 34.990
    Oscar        0.290 34.730[/B]

    Here is my code sample which isn't working:
     
    ```
import java.io.File;
    import java.io.FileReader;
    import java.util.Scanner;
    
     
    public class Names {
        public static void main(String[] args) throws Exception {
                    
            File file = null;
            FileReader fr = null;
            Scanner sc = null;
            
            int count = 0;
            int count2 = 0;
            String name[] = new String[25];
            float codes[][] = new float[25][2];
     
            try     {
                
                file = new File("namedata.txt");
                fr = new FileReader(file);           
                sc = new Scanner(fr);
                
                while(sc.hasNext()){
                	 
                	 name[count] = sc.next();
                	 codes[count][count2] = sc.nextFloat();
                	 codes[count][(count2+1)] = sc.nextFloat();
                	 count++;
                	 count2 = 0; //reset count2
                	System.out.println("Names = "+name[count]+"\n");
                }
            }catch (Exception ex) {
        	ex.printStackTrace();
        	}finally {
              fr.close();
              sc.close();
          } 
        }
    }
```

Any help or suggestions are highly welcomed.

---

### Post by Some Penguin on 2010-03-22
Presumably it's not printing what you expect it to.  If so, a logical first step is asking yourself what it IS printing.

---

### Post by schauerlich on 2010-03-22
Are you handling newlines correctly?

---

### Post by jmwalloh on 2010-03-22
> **schauerlich said:**
> Are you handling newlines correctly?
The outputs are as follows:

Names = null

Names = null

Names = null

Names = null

Names = null

Names = null

Names = null

Names = null

Names = null

---

### Post by jmwalloh on 2010-03-22
> **Some Penguin said:**
> Presumably it's not printing what you expect it to.  If so, a logical first step is asking yourself what it IS printing.
The outputs are as follows:

Names = null

Names = null

Names = null

Names = null

Names = null

Names = null

Names = null

Names = null

Names = null

---

### Post by Some Penguin on 2010-03-22
Ask yourself why.  For instance, *what value* are you printing?  And why is that value null when you're printing it?

---

