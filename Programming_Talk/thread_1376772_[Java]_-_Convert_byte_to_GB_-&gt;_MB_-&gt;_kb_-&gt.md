---
title: "[Java] - Convert byte to GB -&gt; MB -&gt; kb -&gt; byte"
date: 2010-01-09
forum: Programming Talk
---

### Post by SpinningAround on 2010-01-09
I got a program that print out traffic from time to time, problem is that it only print the largest unit, 2,6 GB become 2 GB. Is it possible to get around it so it print 2 GB 632 MB 20 kB 2 byte

```

	private static String reportTraffic(long trafficPrint){

		if((trafficPrint/1000000000)>0){

			return (trafficPrint/1000000000 + " GB");

		}

		else if((trafficPrint/1000000)>0){

			return (trafficPrint/1000000 + " MB");

		}

		else if((trafficPrint/1000)>0){

			return (trafficPrint/1000 + " kB");

		}

		else{

			return (trafficPrint + " byte");

		}

	}

```

---

### Post by Zugzwang on 2010-01-09
Sure. Create a string buffer (class StringBuffer). compute the number of GBs and put the GB-result into the buffer. Then subtract the bytes corresponding to the number of GBs you printed out. Repeat the process for the MBs, KBs and bytes. Then return the content of the string buffer.

---

### Post by SpinningAround on 2010-01-09
Thanks for the answer, those this look ok or is there something that should be improved? 


[PHP]
	private static StringBuffer print = new StringBuffer();
	private static String reportTraffic(long trafficPrint){

		if( (long)(trafficPrint/1E+9) >0 ){

			print.append((long)(trafficPrint/1E+9)).append("GB ");

			return reportTraffic( (long)(trafficPrint-(long)(trafficPrint/1E+9)*1E+9) );

		}

		else if( (long)(trafficPrint/1E+6) >0 ){

			print.append((long)(trafficPrint/1E+6)).append("MB ");

			return reportTraffic( (long)(trafficPrint-(long)(trafficPrint/1E+6)*1E+6) );

		}

		else if( (long)(trafficPrint/1E+3) >0 ){

			print.append((long)(trafficPrint/1E+3)).append("kB ");

			return reportTraffic( (long)(trafficPrint-(long)(trafficPrint/1E+3)*1E+3) );

		}

		else if (trafficPrint>0){

			print.append(trafficPrint).append("byte");

		}

		send = print.toString();

		print.delete(0, print.length());

		return send;

	}
[/PHP]

---

### Post by pensador82 on 2010-12-08
Careful, the conversion you are using is not quite correct!

1 kilobyte is not equivalent to 1000 bytes, but rather **1024** bytes!

---

### Post by t1497f35 on 2010-12-08
[PHP]
import java.io.*;
import java.text.DecimalFormat;

public class Main {

    private static final double BASE = 1024, KB = BASE, MB = KB*BASE, GB = MB*BASE;
    private static final DecimalFormat df = new DecimalFormat("#.##");

    public static void main(String[] args) {
        try {
            File file = new File("/path/to/file");
            System.out.println(formatSize(file.length()));
        } catch(Exception exc) {
            System.out.println("error: " + exc);
        }
    }

    public static String formatSize(double size) {
        if(size >= GB) {
            return df.format(size/GB) + " GB";
        }
        if(size >= MB) {
            return df.format(size/MB) + " MB";
        }
        if(size >= KB) {
            return df.format(size/KB) + " KB";
        }
        return "" + (int)size + " bytes";
    }
}
[/PHP]

---

### Post by Vaphell on 2010-12-08
> Careful, the conversion you are using is not quite correct!
1 kilobyte is not equivalent to 1000 bytes, but rather 1024 bytes!

it is if you use SI units where kilo=10^3, mega=10^6, giga=10^9

oldschool kilobyte (2^10) is now formally called binary kilobyte or kibibyte (KiB), similarly megabyte (2^20) is now called mebibyte (MiB) and gigabyte (2^30) gibibyte (GiB) to avoid confusion with SI units.

---

