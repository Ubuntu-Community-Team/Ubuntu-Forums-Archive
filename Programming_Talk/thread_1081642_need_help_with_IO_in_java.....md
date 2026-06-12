---
title: "need help with IO in java...."
date: 2009-02-26
forum: Programming Talk
---

### Post by Mia_tech on 2009-02-26
I need to read a text file, and put it into an arrayList, and display its content:
text file:

cake 10.0
coffee 0.50
pizza 9.99
pie 3.50
ham 5.0

I've created an Items class with a constructor that takes in the name and price, but before that I need to read the file and parse the price from the name... here's the main.

```
import java.util.*;
import java.io.*;
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
//
        ArrayList<Items> menuItems = new ArrayList<Items>();
        try
        {
        //creating file reader
        FileReader file = new FileReader("menu.txt");
        BufferedReader br = new BufferedReader(file);
        String line = "";
        int counter = 0;
        while((line = br.readLine()) != null)
            {
                System.out.println("We have read line: "+counter++);
            }
        String name = "";
        double price = 0.0;
        for(int i = 0; i < line.length(); i++)
        {
            if(!line.substring(i, i+1).equals(" "))
            {
                name+= line.substring(i, i+1);
            }
            else
            {
                price += Double.parseDouble(line.substring(i, line.length()));
                break;
            }
            menuItems.add(new Items(name, price));
        }
        }
        catch(Exception e)
        {
            System.out.println(e);
        }
        for(Items e: menuItems)
        {
            System.out.println(e.getName()+" "+e.getPrice());
        }

    }

}
```

Items Class
```
public class Items {
    String name;
    double price;
//constrcut item that takes in name and price
    public Items(String name, double price)
    {
        this.name = name;
        this.price = price;
    }
    //getters
    public String getName()
    {
        return name;
    }
    public double getPrice()
    {
        return price;
    }

}
```

but for some reason, I'm not able to print out the name and prices....

---

### Post by simeon87 on 2009-02-26
Try the following:

```

import java.io.*;
import java.util.*;

public class Main {

	public static void main(String[] args) {
		ArrayList<Items> menuItems = new ArrayList<Items>();
		
		try
		{
			FileReader file = new FileReader("menu.txt");
			BufferedReader br = new BufferedReader(file);
		        String line = "";
		        int counter = 0;
	        
		        while((line = br.readLine()) != null)
	                {
				counter++;
		                System.out.println("We have read line: "+counter);
		                String name = line.substring(0, line.indexOf(" "));
		                double price = Double.parseDouble(line.substring(line.indexOf(" ")));
		                menuItems.add(new Items(name, price));
	                }
		} catch (Exception e)
		{
			e.printStackTrace();
		}
		
		for(Items e: menuItems)
	        {
	            System.out.println(e.getName()+" "+e.getPrice());
	        }

        
	}
}

```

Also, in this case, it's bad practise to have a class called Items because the class is used to represent a single item (it stores the name and price of a single item).

---

### Post by Mia_tech on 2009-02-26
WOW... talking about simplifying the code!
Thanks...but do you know why my version wasn't working...

---

### Post by Mia_tech on 2009-02-26
ohh, I found out why ... the while loop is not enclosing the other for loop...

> import java.util.*;
import java.io.*;
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        ArrayList<Items> menuItems = new ArrayList<Items>();
        try
        {
        //creating file reader
        FileReader file = new FileReader("menu.txt");
        BufferedReader br = new BufferedReader(file);
        String line = "";
        int counter = 0;
        while((line = br.readLine()) != null)
            {
                System.out.println("We have read line: "+counter++);
        String name = "";
        double price = 0.0;
        for(int i = 0; i < line.length(); i++)
        {
            if(!line.substring(i,i+1).equals(" "))
            {
                name+= line.substring(i,i+1);
            }
            else
            {
                price = Double.parseDouble(line.substring(i,line.length()));
                break;
              }
            }
           menuItems.add(new Items(name, price));
          }
        }
        catch(Exception e)
        {
            System.out.println(e);
        }
        for(Items e: menuItems)
        {
            System.out.println(e.getName()+" "+e.getPrice());
        }

---

### Post by HotCupOfJava on 2009-02-26
I was going to say - at the end of your "while" loop the String "line" would be null because you were overwriting it every time. But it seems you have already figured this out.

---

### Post by txcrackers on 2009-02-27
Y'all need to dig into the API documentation a bit more...

```

String[] s = line.split(" ");
String name = s[0];
double price = Double.parseDouble(s[1]);

```

---

### Post by HotCupOfJava on 2009-02-27
> **txcrackers said:**
> Y'all need to dig into the API documentation a bit more...

```

String[] s = line.split(" ");
String name = s[0];
double price = Double.parseDouble(s[1]);

```

Hmmm... a useful method of the String class....I hadn't noticed that one before. I'll have to put it to work next time I have some String manipulation to do. The documentation on the "limit" parameter is interesting. I wonder why they have the method discard trailing empty Strings when "limit" is 0?

---

