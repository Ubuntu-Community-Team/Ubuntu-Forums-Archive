---
title: "Java tuning help to beat a C program"
date: 2010-10-19
forum: Programming Talk
---

### Post by Gunnlaugur on 2010-10-19
Hi you guys and girls.

I have written a small java program I need tuning help with so I can match or even better, beat a simular C program.

Both programs are very straigh forward. They take input from standard in and write what ever that is cated as input to an outfile.

I have tried what I can to tune but I'm out of ideas.
Any help would be greatly appreciated

Here is my Java code.
```

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
import java.io.InputStreamReader;

public class AMS {
    private static String outFile = "ams.log";

    public static void main(String args[]) {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String line = "";
        BufferedWriter out = null;
        try {
            FileWriter fileWriter = new FileWriter(outFile);
            out = new BufferedWriter(fileWriter);
            while ((line = br.readLine()) != null) {
                out.write(line);
            }
        } catch (IOException e) {
            System.err.println(e);
        } finally {
            try {
                out.close();
            } catch (IOException e) {
                System.err.println(e);
            }
        }
    }
}

```And this is the C program in question.
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <signal.h>
#define INPUT_LINE_SIZE        4096
FILE *prg_log = NULL;

int main(int argc, char **argv)
{
  char pim_line[INPUT_LINE_SIZE];
  prg_log = fopen("/home/tomasj/src/alarm_test/alarm11.log", "at");
  while(!feof(stdin)) {
    /* read up to the newline, up to INPUT_LINE_SIZE-1 characters;
       fgets will null terminate the string for us */
    fgets(pim_line, INPUT_LINE_SIZE, stdin);
    fprintf(prg_log,"%s",pim_line);
  }
 
  /* close logfile and exit */
  fclose(prg_log);
  return 0;
}

```Here is the running time of my java program
> 
[gunnl@ishka java]$ time cat alarm.log | java -jar ams7.jar

real    0m0.392s
user    0m0.291s
sys    0m0.075s
And then the time of the C program.
> 
[root@ishka ~]# time cat /home/gunnl/java/alarm.log | /home/tomasj/src/alarm_test/rugl  

real    0m0.131s
user    0m0.097s
sys     0m0.035s
JRE version used server
> 
java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) Client VM (build 17.1-b03, mixed mode, sharing)
And the linux version running on server where both programs are executed.
> 
# uname -a gives me
Linux ishka.foo.bar 2.6.9-78.0.1.EL #1 Tue Jul 22 17:50:01 EDT 2008 i686 athlon i386
GNU/Linux

# cat /etc/issue gives
Red Hat Enterprise Linux ES release 4 (Nahant Update 7)
Kernel \r on an \m

# cat /proc/meminfo gives
MemTotal:      1035556 kB
MemFree:         50356 kB
Buffers:        105428 kB
Cached:         707976 kB
SwapCached:          0 kB
Active:         392544 kB
Inactive:       428976 kB
HighTotal:      131008 kB
HighFree:          256 kB
LowTotal:       904548 kB
LowFree:         50100 kB
SwapTotal:     2031608 kB
SwapFree:      2031400 kB
Dirty:             132 kB
Writeback:           0 kB
Mapped:          13776 kB
Slab:           151776 kB
CommitLimit:   2549384 kB
Committed_AS:    53496 kB
PageTables:        744 kB
VmallocTotal:   106488 kB
VmallocUsed:      3936 kB
VmallocChunk:   102392 kB
HugePages_Total:     0
HugePages_Free:      0
Hugepagesize:     4096 kB

# more /proc/cpuinfo gives
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 33
model name    : Quad-Core AMD Opteron(tm) Processor 2356
stepping    : 0
cpu MHz        : 2294.827
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 pni syscall nx mmxex
t fxsr_opt lm 3dnowext 3dnow constant_tsc pni
bogomips    : 4605.00
I hope the information provided are enough.

Thanks in advance
Regards
Gunnlaugur

---

### Post by spjackson on 2010-10-19
> **Gunnlaugur said:**
> 
I have written a small java program I need tuning help with so I can match or even better, beat a simular C program.

Both programs are very straight forward. They take input from standard in  and write what ever that is cated as input to an outfile.
```

[gunnl@ishka java]$ time cat alarm.log | java -jar ams7.jar

real 0m0.392s
user 0m0.291s
sys 0m0.075s 

[root@ishka ~]# time cat /home/gunnl/java/alarm.log | /home/tomasj/src/alarm_test/rugl

real 0m0.131s
user 0m0.097s
sys 0m0.035s 

```When it comes to short running programs like this, java is on a hiding to nothing because of the overhead in bringing up the virtual machine. For example, take a minimal C program and equivalent java
```

/* C */
int main() {}

/* java */
public class AMS {
    public static void main(String args[]) {
    }
}

```and compare the runtimes. You will very likely find the same sort of difference as you get from your IO program, i.e. the IO part is probably almost equally fast in both java and C.

If you process huge input files that take several seconds, the absolute difference between the two versions should stay about the same, whereas the relative difference would be much smaller.

If you need to run lots of java programs each of which is of short duration, then something like Nailgun [http://martiansoftware.com/nailgun/](http://martiansoftware.com/nailgun/) will reduce your overall execution time by eliminating the overhead needed to start the JVM.

---

### Post by Gunnlaugur on 2010-10-19
Thank you spjackson.
I'll take a look at Nailgun.

---

### Post by Some Penguin on 2010-10-19
I wouldn't bother using a BufferedReader if you're just copying files; I'd use InputStream but reading maybe 8K + bytes at a time, and ditto for FileOutputStream.  This way you don't have any unnecessary overhead associated with converting bytes to characters (i.e. charset encoding conversion) or scanning for newlines.

---

### Post by Zymus on 2010-10-20
Something like this?
```

import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStream;
import java.io.OutputStream;

public class Main {
    public static void main(String[] args) {
        try {
            InputStream input = new FileInputStream(args[0]);
            OutputStream output = new FileOutputStream(args[1]);
            byte[] buffer = new byte[128];
            int read = 0;
            while((read = input.read(buffer)) != -1) {
                output.write(buffer, 0, read);
                output.flush();
            }
            output.close();
        } catch(Exception e) {
            e.printStackTrace();
        }
    }
}

```output:
> 
zymus@zymus-laptop:~/NetBeansProjects/377_Client/RS_Client$ time java Main /var/log/messages log.txt

real    0m0.124s
user    0m0.064s
sys    0m0.036s


---

### Post by spjackson on 2010-10-20
> **Zymus said:**
> 
output:
```

zymus@zymus-laptop:~/NetBeansProjects/377_Client/RS_Client$ time java Main /var/log/messages log.txt

real    0m0.124s
user    0m0.064s
sys    0m0.036s                      

```
Those figures on their own don't show anything. On my system a Java program that does nothing at all takes significantly longer than that.  How do those figures compare to the C equivalent on the same platform?

---

### Post by wmcbrine on 2010-10-20
> **Gunnlaugur said:**
> I have written a small java program I need tuning help with so I can match or even better, beat a simular C program.What makes you think this is possible?

---

### Post by Finalfantasykid on 2010-10-20
I've had some pretty good success with a program which did something fairly similar.  Instead of reading one line, and outputting it, and repeating until the file is done, what I did was read in one line at a time, and append it to a StringBuilder (don't use regular Strings as they are immutable and will crawl with larger Strings).  Just append the line with a \n to the StringBuilder, and then just output the entire StringBuilder using it's toString() method.  It was super fast with what I did it with, and if the File you are reading is large enough, you should see a decent speed improvement I would imagine.  For smaller Files it might not make a difference though.

---

