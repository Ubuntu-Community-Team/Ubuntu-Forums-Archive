---
title: "DecimalFormat not working in Java"
date: 2015-10-17
forum: Programming Talk
---

### Post by polaris90 on 2015-10-17
I'm writing this program to read data from yahoo finances and read the stock market values. The problem is that the values have 6 decimal places so I decided to use DecimalFormat to get a double with only 2 decimal places but it keeps displaying 6 decimal places. 

```
//import java.io.BufferedReader;import java.io.IOException;
import java.net.URL;
import java.text.DecimalFormat;
import java.util.Scanner;


public class DataRead {


    public static void main(String[] args) {


        Scanner sc;// to read the raw data from the site
        String str;// used to read a single line from the scanner
        URL url;//url to read the data from the site
        // get historical data first
        try {


            // Create a URL for the desired page
             url = new URL("http://real-chart.finance.yahoo.com/table.csv?s=GOOG&d=9&e=16&f=2015&g=d&a=9&b=15&c=2014&ignore=.csv");


            // Read all the text returned by the server/site
            // BufferedReader in = new BufferedReader(new
            // InputStreamReader(url.openStream()));
            sc = new Scanner(url.openStream());
            
            System.out.println("historical data");
            //read first line for column titles 
            str = sc.nextLine();
            String[] singleValues = str.split(",");
            for(int i = 0; i<singleValues.length; i++){
                System.out.print("      " + singleValues[i]);
            }
            
            System.out.println();    
            
            while (sc.hasNextLine()){
                str = sc.nextLine();
                singleValues = str.split(",");
                for(int i = 0; i < singleValues.length; i++){
                    
                    String s = singleValues[i];
                    
                    if(i>0){
                        
                        //change values to 2 decimal places
                        double x = Double.parseDouble(s);
                        DecimalFormat df = new DecimalFormat("#.##");
                        
                        //s = String.format("%.02f", x);
                        //x = Double.parseDouble(s);
                        df.format(x);
                        
                        System.out.print(x+"   ");//Double.parseDouble(s) + "  ");
                    }
                    else
                        System.out.printf("%-15s", s);
                }
                System.out.println();
                
            }
            sc.close();
        } catch (IOException e){
            e.printStackTrace();
        }
        
        System.out.println("\ncurrent data");
        
        
    }
}
```

sample run

historical data
      Date      Open      High      Low      Close      Volume      Adj Close
2015-10-16     664.109985     664.969971     657.200012     662.200012     1606100.0     662.200012     
2015-10-15     654.659973     663.130005     654.460022     661.73999     1830500.0     661.73999     
2015-10-14     653.210022     659.390015     648.849976     651.159973     1412000.0     651.159973     
2015-10-13     643.150024     657.812012     643.150024     652.299988     1790700.0     652.299988     
2015-10-12     642.090027     648.5     639.01001     646.669983     1275200.0     646.669983     
2015-10-09     640.0     645.98999     635.317993     643.609985     1648700.0     643.609985    



it works if I do it like this, but it seems unnecessary given the API already being written
double x = Double.parseDouble(s);
s = String.format("%.02f", x);x = Double.parseDouble(s);
                    
I could simply format the string and print it using format above but I want the double value so I can pass it to another object. Can anybody point at what I'm doing wrong when formatting the values?

---

### Post by PaulM1985 on 2015-10-19
In your line System.out.print(x+ "  ") x here is a double, so you are printing a double to double precision, which is why you are getting the output you are seeing.  You should be printing the output of the decimal format function:
System.out.print(df.format(x) + "  ")

Paul

---

### Post by polaris90 on 2015-10-19
Thanks PaulM1985, I see what you mean. I thought the number would get formatted and then I would be able to print it with the decimal format. Thanks for your comment

---

