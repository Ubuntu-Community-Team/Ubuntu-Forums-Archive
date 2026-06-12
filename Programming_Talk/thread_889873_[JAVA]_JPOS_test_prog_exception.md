---
title: "[JAVA] JPOS test prog exception"
date: 2008-08-14
forum: Programming Talk
---

### Post by mike_g on 2008-08-14
I'm trying to run a JPOS test program. Its compiled but when I run it I get this:
```
Exception in thread "main" java.lang.UnsatisfiedLinkError: /root/.commandemulator/libCommandEmulatorJ.so: Can't load IA 32-bit .so on a IA 32-bit platform
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
        at java.lang.Runtime.load0(Runtime.java:769)
        at java.lang.Runtime.load(Runtime.java:757)
        at com.starmicronics.commandemulator.CommandEmulator.<clinit>(CommandEmulator.java:246)
        at com.starmicronics.starjavapos.CashDrawerService.open(Unknown Source)
        at jpos.BaseJposControl.open(Unknown Source)
        at StarCashDrawerTest.main(StarCashDrawerTest.java:42)

``` 
Anyone know what this would mean?

Cheers.

---

### Post by KingTermite on 2008-08-14
Not sure....but what's at line 42 in StarCashDrawerTest.java?

---

### Post by mike_g on 2008-08-14
Not much, but since you mentioned it the program name was kind of weird; I'm running StarReceiptTest, but the comments were telling me to compile it as StarCashDrawerTest. I changed the name; it still get the same errors, but for some reason the error has jumped to line 50 even tho I havent altered the code. Anyway, this is where it tries to open the printer.

The function parameter needs to be given the name set in the CUPS manager, which I did. Heres the code:
```
// StarReceiptTest.java

// This file contains sample code illustrating how to use the POSPrinter class to

// control your Star printer.  The basic printing and status querying mechanisms

// are used here.  For more advanced usage of the POSPrinter class, see the 

// JavaPOS specification.



// usage instructions - Windows

// 1. add current directory to the CLASSPATH = set CLASSPATH=%CLASSPATH%;.

// 2. compile from command line - javac StarReceiptTest.java

// 3. execute from command line - java StarReceiptTest

// usage instructions - Linux
// 1. compile from command line - javac -classpath jpos191-controls.jar:jcl.jar StarReceiptTest.java
// 2. execute from command line - java -classpath jpos191-controls.jar:jcl.jar:xercesimpl.jar:xml-apis.jar:commandemulator.jar:stario.jar:starjavapos.jar:. StarReceiptTest



// NOTE: CHANGE THE PRINTER NAME IN THE printer.open STATEMENT BELOW TO MATCH YOUR CONFIGURED DEVICE NAME



import jpos.JposConst;

import jpos.JposException;

import jpos.POSPrinter;

import jpos.POSPrinterConst;



import jpos.util.JposPropertiesConst;



public class StarReceiptTest

{

    public static void main(String[] args)

    {   

        /*

         	If you want to place the jpos.xml file elsewhere on your local file system then uncomment the

            following line and specify the full path to jpos.xml.

         

            If you want to place the jpos.xml file on a webserver for access over the internet then uncomment

            the second System.setProperty line below and specify the full URL to jpos.xml.

        */

        System.setProperty(JposPropertiesConst.JPOS_POPULATOR_FILE_PROP_NAME, "jpos.xml");

        //System.setProperty(JposPropertiesConst.JPOS_POPULATOR_FILE_URL_PROP_NAME, "http://some-where-remote.com/jpos.xml");

        

        // constants defined for convience sake (could be inlined)

        String ESC    = ((char) 0x1b) + "";

        String LF     = ((char) 0x0a) + "";

        String SPACES = "                                                                      ";

        

        // instantiate a new jpos.POSPrinter object

        POSPrinter printer = new POSPrinter();

        

        try

        {

            // open the printer object according to the entry names defined in jpos.xml

            printer.open("startsp");



            // claim exclsive usage of the printer object

            printer.claim(1);

            

            // enable the device for input and output

            printer.setDeviceEnabled(true);

            

            // set map mode to metric - all dimensions specified in 1/100mm units

            printer.setMapMode(POSPrinterConst.PTR_MM_METRIC);  // unit = 1/100 mm - i.e. 1 cm = 10 mm = 10 * 100 units

            

            do

            {

                // poll for printer status

                //   a javax.swing based application would be best to both poll for status

                //   AND register for asynchronous StatusUpdateEvent notification

                //   see the JavaPOS specification for details on this

                

                // check if the cover is open

                if (printer.getCoverOpen() == true)

                {

                    System.out.println("printer.getCoverOpen() == true");

                    

                    // cover open so do not attempt printing

                    break;

                }

                

                // check if the printer is out of paper

                if (printer.getRecEmpty() == true)

                {

                    System.out.println("printer.getRecEmpty() == true");

                    

                    // the printer is out of paper so do not attempt printing

                    break;

                }

                

                // being a transaction

                //   transaction mode causes all output to be buffered

                //   once transaction mode is terminated, the buffered data is

                //   outputted to the printer in one shot - increased reliability

                printer.transactionPrint(POSPrinterConst.PTR_S_RECEIPT, POSPrinterConst.PTR_TP_TRANSACTION);

                

                if (printer.getCapRecBitmap() == true)

                {

                    // print an image file

                    try

                    {

                        printer.printBitmap(POSPrinterConst.PTR_S_RECEIPT, "star.gif", POSPrinterConst.PTR_BM_ASIS, POSPrinterConst.PTR_BM_CENTER);

                    }

                    catch (JposException e)

                    {

                        if (e.getErrorCode () != JposConst.JPOS_E_NOEXIST)

                        {

                            // error other than file not exist - propogate it

                            throw e;

                        }

                        

                        // image file not found - ignore this error & proceed

                    }

                }

                

                // call printNormal repeatedly to generate out receipt

                //   the following JavaPOS-POSPrinter control code sequences are used here

                //   ESC + "|cA"          -> center alignment

                //   ESC + "|4C"          -> double high double wide character printing

                //   ESC + "|bC"          -> bold character printing

                //   ESC + "|uC"          -> underline character printing

                //   ESC + "|rA"          -> right alignment

                

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT, ESC + "|cA" + ESC + "|4C" + ESC + "|bC" + "Star Grocer"     + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT, ESC + "|cA" + ESC + "|bC" +               "Shizuoka, Japan" + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT, ESC + "|cA" + ESC + "|bC" +               "054-555-5555"    + LF);



                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT, ESC + "|uC" + "Qnty Unit Tx Description" + SPACES.substring(0, printer.getRecLineChars() - "Qnty Unit Tx Description".length()) + LF);

                

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT,               "   1  830    Soba Noodles"        + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT,               "   1  180    Daikon Radish"       + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT,               "   1  350    Shouyu Soy Sauce"    + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT,               "   1   80    Negi Green Onions"   + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT,               "   1  100    Wasabi Horse Radish" + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT,               "   2  200 Tx Hashi Chop Sticks"   + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT, LF);

                

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT,               ESC + "|rA" +               "Subtotal:  2160" + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT,               ESC + "|rA" +               "Tax:         24" + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT,               ESC + "|rA" + ESC + "|bC" + "Total:     2184" + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT,               ESC + "|rA" +               "Tender:    2200" + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT,               ESC + "|rA" + ESC + "|bC" + "Change:      16" + LF);

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT, LF);

                                

                if (printer.getCapRecBarCode() == true)

                {

                    // print a Code 3 of 9 barcode with the data "123456789012" encoded

                    //   the 10 * 100, 60 * 100 parameters below specify the barcode's height and width

                    //   in the metric map mode (1cm tall, 6cm wide)

                    printer.printBarCode(POSPrinterConst.PTR_S_RECEIPT, "123456789012", POSPrinterConst.PTR_BCS_Code39, 10 * 100, 60 * 100, POSPrinterConst.PTR_BC_CENTER, POSPrinterConst.PTR_BC_TEXT_BELOW);

                }

                

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT, ESC + "|cA" + ESC + "|4C" + ESC + "|bC" + "Thank you" + LF);



                // the ESC + "|100fP" control code causes the printer to execute a paper cut

                //   after feeding to the cutter position

                printer.printNormal(POSPrinterConst.PTR_S_RECEIPT, ESC + "|100fP");



                // terminate the transaction causing all of the above buffered data to be sent to the printer

                printer.transactionPrint(POSPrinterConst.PTR_S_RECEIPT, POSPrinterConst.PTR_TP_NORMAL);

                

                // exit our printing loop

            } while (false);

        }

        catch(JposException e)

        {

            // display any errors that come up

            e.printStackTrace();

        }

        finally

        {

            // close the printer object

            try

            {

                printer.close();

            }

            catch (Exception e) {}

        }

        

        System.out.println("StarReceiptTest finished.");

        System.exit(0);

    }

}

```
Any ideas?

---

### Post by mike_g on 2008-08-15
bump :)

---

### Post by txcrackers on 2008-08-15
Does this file
```
/root/.commandemulator/libCommandEmulatorJ.so
```
exist? Is the file readable by whichever user you're running as? (Considering the path above, I doubt the file exists or is readable by you.)

An UnsatisfiedLinkError usually indicates that it's trying to locate a native library (.so on Linux, .dll on Windows) that is used by the program. So the indicated .so file must be placed in the appropriate JVM directory (/usr/lib/jvm/java-6-sun/jre/lib/i386) or you need to "tell" the JVM where it is (-Djava.library.path=/path/to/directory).

I'd strongly recommend checking the JPOS documentation again regarding the native library...

---

### Post by mike_g on 2008-08-15
> Does this file exist? 
Err.. No. It dosent.  

> So the indicated .so file must be placed in the appropriate JVM directory (/usr/lib/jvm/java-6-sun/jre/lib/i386) or you need to "tell" the JVM where it is (-Djava.library.path=/path/to/directory). 
Thanks; I'll try that tomorrow. I think you got it ;)

> I'd strongly recommend checking the JPOS documentation again regarding the native library..
Yeah, the only JPOS docs I have atm is the stuff in the sample code header. Your right tho it would be a good idea to look for the docs tho. Tbh I have been pretty lazy with this issue; kinda just sat on my *** and waited for someone to tell me what to do, lol.

---

### Post by sureshkumarece on 2009-07-27
Hi we are also got the error SetDeviecEnabled(unknown source).
How to solve the issue.CUPS printing is working fine.we are using Star TSP 100 Printer

---

