---
title: "Please help!! Compiling errors......."
date: 2008-11-29
forum: Packaging and Compiling Programs
---

### Post by mcweaver1 on 2008-11-29
Hi,

When I compile my code I get the following errors:

Note: Cwk2Problem1.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
Note: Cwk2Problem1.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.

I think it's something to do with the fact I ought to be creating an arraylist of arraylists.... 

When I run the code it doesn't work either and I have a feeling that once this is sorted out it will be much happier!

Please help!!! I'm a bit of a beginner....

Here is the code:

import java.io.*;
import java.util.ArrayList;

class Cwk2Problem1
{
    public static void main(String[] args)
    {
        Cwk2Problem1 program = new Cwk2Problem1();
        int result = program.createlists(args);
        System.out.println("result = %d" + result);
    }
    int createlists(String[] args)
    {
       //calculates the length of the input string given
        int len = args[0].length();
        //takes the substring of the given string
        //takes the last 3 chars of the string
        String ext = args[0].substring(len-3, len);
        if ((args.length == 1) & (ext.equals(".gr")))
        {        
            int nodes = 0;
            int edges = 0;
            DataInputStream dis = null;
            try
            {
                String record;
                File f = new File(args[0]);
                FileInputStream fis = new FileInputStream(f);
                BufferedInputStream bis = new BufferedInputStream(fis);
                dis = new DataInputStream(bis);
                while ((record = dis.readLine()) != null)
                {
                    String[] data = record.split(" ");
                    if ( data[0].equals("p"))
                    {
                        nodes = Integer.parseInt(data[2])+1;
                        edges = Integer.parseInt(data[3]);
                        break;
                    }
                }
                ArrayList[] gertrude = new ArrayList[nodes];  
                dis.close();
                f = new File(args[0]);
                fis = new FileInputStream(f);
                bis = new BufferedInputStream(fis);
                dis = new DataInputStream(bis);
                while ((record = dis.readLine()) != null)
                {
                    String[] data = record.split(" ");
                    if (data[0].equals("a"))
                    {
                        int position = Integer.parseInt(data[1]);
                        int a = Integer.parseInt(data[2]);
                        int b = Integer.parseInt(data[3]);
                        Apples pineapple = new Apples(a, b);
                        gertrude[position].add(pineapple);
                    }     
                }
             }
             catch (IOException e)
             {
                System.out.println("IOException error!");
             }
             return (int)(nodes/edges);
        }
        else
        {
            System.err.println("Wrong file");
            return 0;
        }
    }
}

class Apples
{
    int a, b;
    Apples(int c, int d)
    {
        a = c;
        b = d;
    }
    int geta()
    {
        return a;
    }
    int getb()
    {
        return b;
    }
    void seta(int orange)
    {
        a=orange;
    }
    void setb(int banana)
    {
        b=banana;
    }
}

---

### Post by meatpan on 2008-12-05
The compiler messages look like warnings, and not errors. Can you attach the full compiler output?

Also, try to strip your program to the smallest amount of code necessary to display the error.  This is difficult, but useful, especially when asking others to help you.  Another benefit is the potential elimination of other errors in your program.

---

