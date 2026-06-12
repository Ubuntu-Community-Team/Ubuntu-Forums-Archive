---
title: "getting arrayList error in Java..."
date: 2009-04-19
forum: Programming Talk
---

### Post by Mia_tech on 2009-04-19
I created a class just for the pingsweep method and I made it runnable, so I can update the progress bar... I'm getting errors on the array.... it seems that the array is empty, how could I pass the arrayList from the IPrange class to the IPscanner class... here are the classes, I'm not using a gui for now as I want to get it working before I import into the gui
IPrange class
[PHP]import java.util.*;
public class IPrange {
    private String from = "";
    private String to = "";
    private int[] ip1 = {0,0,0,0};//holds the numeric ip
    private int[] ip2 = {0,0,0,0};
    private String ipadd = "";
    ArrayList<String> range = new ArrayList<String>();
    //setters
    public void setFromip(String from)
    {
        this.from = from;
    }
    public void setToip(String to)
    {
        this.to = to;
    }

    //convert from String ip to int[] ip
    public void StrToIP()
    {
        //spliting strings
        String[] temp1 = from.split("\\.");
        String[] temp2 = to.split("\\.");
        //parsing and adding ip to ip Array
        for(int i = 0; i < temp1.length; i++)
        {
            ip1[i] = Integer.parseInt(temp1[i]);
            ip2[i] = Integer.parseInt(temp2[i]);
        }
    }
    /**
     * identifying type of network class A, B, C
     */
    public void calcNetwork()
    {
        String addr = "";
        //adding class A network to Array "range"
        if((ip1[1] != ip2[1]) && ( ip1[1] < ip2[1]))
        {
            for(int i = ip1[1]; i <= ip2[1]; i++)
            {
                for(int j = 0; j <= 255; j++)
                {
                    for(int k = 0; k <= 255; k++)
                    {
                        addr = ip1[0]+"."+i+"."+j+"."+k;
                        range.add(addr);
                    }
                }
            }
        }
        //adding class B network to Array "range"
        else if((ip1[2] != ip2[2]) && (ip1[2] < ip2[2]))
        {
            for(int i = ip1[2]; i <= ip2[2]; i++)
            {
                for(int j = 0; j <= 255; j++)
                {
                    addr = ip1[0]+"."+ip1[1]+"."+i+"."+j;
                    range.add(addr);
                }
            }
        }
        //adding class C network to Array "range"
        else if((ip1[3] != ip2[3]) && (ip1[3] < ip2[3]))
        {
            for(int i = ip1[3]; i <= ip2[3]; i++)
            {
                addr = ip1[0]+"."+ip1[1]+"."+ip1[2]+"."+i;
                range.add(addr);
            }
        }
        else System.out.println("Enter correct address range!");
   }
    public ArrayList<String> getRange()
    {
        return range;
    }
}  [/PHP]

IPscanner class
[PHP] import java.util.*;
import java.io.*;
import java.net.*;
public class IPscanner implements Runnable{
    private String ipadd = "";
    IPrange netrange = new IPrange();
    ArrayList<String> block;
    public IPscanner() throws ExceptionInInitializerError
    {
        block = netrange.getRange();
    }
    public void run()
    {
        boolean ping = false;
        System.out.println(block.size());
        ipadd = "Scanning network "+"\""+block.get(0)+"\""+"...."+"\n";

        for(int i = 0; i < block.size(); i++)
        {
            try
            {
                int timeout = 1500;
                InetAddress address = InetAddress.getByName(block.get(i));
                ping = address.isReachable(timeout);
                //progressBar1.setValue(i);//updating progress bar
                if(ping == true)
                {
                     ipadd = block.get(i)+" is alive!"+"\n";
                }
                else
                {
                    ipadd = block.get(i)+"\n";
                }
                System.out.println(ipadd);
            }
            catch(IOException e)
            {
                System.out.println(e);
            }
        }
   }
    public String getIPadd()
    {
        return ipadd;
    }
}  [/PHP]

main method
[PHP]public class Main {
     public static void main(String[] args) {
        IPrange scan = new IPrange();
        Runnable r = new IPscanner();
        IPscanner ipscan = new IPscanner();
        String from = "10.200.50.0";
        String to = "10.200.50.10";
        scan.setFromip(from);
        scan.setToip(to);
        scan.StrToIP();
        scan.calcNetwork();
        Thread t1 = new Thread(r);
        t1.start();
        System.out.println(ipscan.getIPadd()+" I'm here!");
   }
}  [/PHP]

errors:
```
 I'm here!
Exception in thread "Thread-0" java.lang.IndexOutOfBoundsException: Index: 0, Size: 0
0
        at java.util.ArrayList.RangeCheck(ArrayList.java:547)
        at java.util.ArrayList.get(ArrayList.java:322)
        at testscan.IPscanner.run(IPscanner.java:27)
        at java.lang.Thread.run(Thread.java:619)
BUILD SUCCESSFUL (total time: 0 seconds)
```

---

### Post by Mia_tech on 2009-04-19
it seems like when I'm referencing the array the array is reporting an empty array... anyone?

---

### Post by simeon87 on 2009-04-19
> **Mia_tech said:**
> it seems like when I'm referencing the array the array is reporting an empty array... anyone?

Debugging 101

[LIST]
[*]Observation: The ArrayList I'm using is empty.
[*]Question: Where is the ArrayList created?
[*]Answer: Ultimately in IPrange
[*]Question: Where does the ArrayList get populated?
[*]Answer: In calcNetwork()
[*]Question: Where am I using the ArrayList?
[*]Answer: In run() of IPscanner
[*]Question: Is this before or after the ArrayList gets populated?
[*]Answer: Before...
[*]Observation: Cause found.
[*]Solution: To be determined.
[/LIST]

---

### Post by dwhitney67 on 2009-04-19
You allocate 'range', but you never populate it with any Strings... well, at least not within the context of IPscanner's constructor.

IPscanner allocates an IPrange as a data member, never calls calcNetwork(), much less any other method associated with IPrange, to populate 'range'; then a call getRange() is made.

This explains why 'range' has a zero-length.  Your thread, though, doesn't seem to care (it should!) and you call get(0)... then boom... your app crashes.

---

### Post by Mia_tech on 2009-04-19
> **dwhitney67 said:**
> You allocate 'range', but you never populate it with any Strings... well, at least within the context of IPscanner's constructor.
it gets populated during a call to calcNetwork in the main, but the main creates a different reference to IPrange that the one used in IPscanner... I constructed an object type IPrange "netrange" in IPscanner so I can get a reference to ArrayList "range" in IPrange
> 
IPscanner allocates an IPrange as a data member, never calls calcNetwork(), much less any other method associated with IPrange, to populate 'range'; then a call getRange() is made.
should I call calcNetwork from within IPscanner... I thought that in order to use the "range" ArrayList creaed in IPrange, I only needed a reference which is the getRange method in IPrange then I created the reference with the constructor

[PHP]ArrayList<String> block;
    public IPscanner() throws ExceptionInInitializerError
    {
        block = netrange.getRange();
    }[/PHP]
> 
This explains why 'range' has a zero-length.  Your thread, though, doesn't seem to care (it should!) and you call get(0)... then boom... your app crashes.

well, what do I need to implement in the IPscanner class to use the "range" ArrayList... I changed the order in which I call and construct the objects in the main I call calcNetwork before I create any object to the IPscanner class, but still get the same error.. 

[PHP]public static void main(String[] args) {
        IPrange scan = new IPrange();
        String from = "10.200.50.0";
        String to = "10.200.50.10";
        scan.setFromip(from);
        scan.setToip(to);
        scan.StrToIP();
        scan.calcNetwork();//populating range array here
        IPscanner ipscan = new IPscanner();
        Runnable r = new IPscanner();
        Thread t1 = new Thread(r);
        t1.start();
        System.out.println(ipscan.getIPadd()+" I'm here!");
   }[/PHP]


errors
```

 I'm here!
0
Exception in thread "Thread-0" java.lang.IndexOutOfBoundsException: Index: 0, Size: 0
        at java.util.ArrayList.RangeCheck(ArrayList.java:547)
        at java.util.ArrayList.get(ArrayList.java:322)
        at testscan.IPscanner.run(IPscanner.java:27)
        at java.lang.Thread.run(Thread.java:619)
BUILD SUCCESSFUL (total time: 3 seconds)

```

also, notice how the last statement in the main which has a string " I'm here ", gets executed first... why is that?

---

### Post by dwhitney67 on 2009-04-19
You are creating (allocating) too many objects to keep track of which one is initialized and which one is not.

Perhaps consider passing the IPrange object you allocate and setup in main() to the IPscanner constructor.  IPscanner can setup a handle to that IPrange object that can be used when it is run as a thread.

```

class IPscanner
{
  private IPrange netrange;

  public IPscanner(IPrange range)
  {
    this.netrange = range;
  }

  ...
}

```

P.S.  My java skills are rusty; forgive me if there is a syntax error above.

---

### Post by Mia_tech on 2009-04-19
I could just fix this by putting the run() method inside the IPrange class that way I don't have to pass any reference to the range ArrayList, but that defeats the purpose of OOP, besides that method has no business in that class...

---

