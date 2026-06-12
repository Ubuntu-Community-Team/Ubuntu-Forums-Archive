---
title: "need help printing output to textArea"
date: 2009-04-14
forum: Programming Talk
---

### Post by Mia_tech on 2009-04-14
I'm working on a app that prints out to a txtArea the results of an IP scan on the network.... the output prints just fine the problem is that I have to wait until it finishes scanning the range of ip's to print, meanwhile the user wonders what is it doing.... my question is: is there anyway to outupt one ping responce at a time... meaning as soon I get a response from an ip print it to the txtArea....
Attached is what the ip scanner looks like.
here's the code I'm using
the "Start" button action:

[PHP]IPrange netRange = new IPrange();
    IPscanner netScan = new IPscanner();
    @Action //get network range & start scanning
    public void StartNetworkScan()
    {
        String clear = " ";
        txtAreaIPscan.setText(clear);
        String ipFrom = "", ipTo = "";
        ipFrom = txtfieldAddressFrom.getText();
        ipTo = txtfieldAddressTo.getText();
        //setting from: ip and to: ip
        netRange.setFromip(ipFrom);
        netRange.setToip(ipTo);
        //converting str ip to int ip & calc net class
        netRange.StrToIP();
        netRange.calcNetwork();
        txtAreaIPscan.setText(netScan.pingSweep());
     }[/PHP]

IPscanner class

[PHP]import java.util.*;
public class IPrange {
    private String from = "";
    private String to = "";
    private int[] ip1 = {0,0,0,0};//holds the numeric ip
    private int[] ip2 = {0,0,0,0};
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

    //identify and display the network: A, B, C
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
  }
[/PHP]

[PHP]import java.net.*;
import java.io.*;
import java.util.*;
public class IPscanner {
    IPrange scan;
    ArrayList<String> block = scan.getRange();
    //construc for the complete block to scan
    public IPscanner()
    {
        scan = new IPrange();
    }
    //ping sweep the network
    public String pingSweep()
    {
        boolean ping = false;
        String ipadd = "";
        ipadd = "Scanning network "+"\""+block.get(0)+"\""+"...."+"\n";
        for(int i = 0; i < block.size(); i++)
        {
            try
            {
                
                    int timeout = 3000;
                    InetAddress address = InetAddress.getByName(block.get(i));
                    ping = address.isReachable(timeout);
                    if(ping == true)
                    {
                         ipadd += block.get(i)+" is alive!"+"\n";
                    }
               
                
            }
            catch(IOException e)
            {
                System.out.println(e);
            }
        }
      return ipadd;
    }
}
[/PHP]

---

### Post by myrtle1908 on 2009-04-15
Have your IPScanner class request that the textArea be updated as and when it needs to.  For example, your GUI/main class could have a static method named "log" which your IPScanner class can call eg.

[PHP]public static void log(String s) {
  textArea.append(s);
  textArea.setCaretPosition(textArea.getText().length());
}[/PHP]

---

### Post by Mia_tech on 2009-04-15
> **myrtle1908 said:**
> Have your IPScanner class request that the textArea be updated as and when it needs to.  For example, your GUI/main class could have a static method named "log" which your IPScanner class can call eg.

[PHP]public static void log(String s) {
  textArea.append(s);
  textArea.setCaretPosition(textArea.getText().length());
}[/PHP]

well, I did create a static method, but I can't call it from within the IPscanner class

[PHP]public static void updateIPscan(String ipadd)
    {
        txtareaIPscan.append(ipadd);
    }[/PHP]

---

### Post by myrtle1908 on 2009-04-15
Ok.  That was just off the top of my head...I'm not exactly sure how your program is put together.

Looking at your code again, I would assume that with the following line:-

[PHP]txtAreaIPscan.setText(netScan.pingSweep());[/PHP]

*setText()* wont do anything until *netScan.pingSweep()* has returned.  That would explain why you are not seeing anything in the textarea until it has finished.

I'm not that great with Java and Swing but I have done this exact thing before.  From memory I had threads that would communicate with the GUI notifying it when to update things like textareas etc.

A quick and dirty solution would be to pass a reference of your GUI class to your IPScanner class and have it call your *updateIPscan()* method.

Hope that helps a little.

---

