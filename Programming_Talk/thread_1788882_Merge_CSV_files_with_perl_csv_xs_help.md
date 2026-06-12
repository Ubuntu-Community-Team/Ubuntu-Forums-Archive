---
title: "Merge CSV files with perl csv_xs help"
date: 2011-06-23
forum: Programming Talk
---

### Post by franestepona on 2011-06-23
Hello,

I have a bunch of CSV files that I would like to merge into one. These files are rather complicated to work with (they contain all sorts of special characters, commas and newlines inside fields). What I need is to merge them into one and append the filename at each row (so I know the file they came from). I tried using CSVfix, but due to special characters some rows are messed up. awk won't help either.

I have a Perl script that works just fine but it appends the filename on new lines inside the fields. Here is the code:

```
#!/usr/bin/perl
my $result_file=shift;
my $pattern=shift;
my (@file_list) = glob $pattern;

open( OUT, ">$result_file") or die "Can't open '$result_file':$!";
foreach my $in_file (@file_list) { 
   open(IN, "$in_file"); 
   while (<IN>) {
      chomp;
      print OUT $_ . ',' . $in_file . "\n" ;
      }
   close (IN);
   }

close (OUT);
```

I think perl can solve the problem since csv_xs can handle new lines inside fields, but I can't find any good example on how to do this.

Any help is greatly appreciated.

Fran

---

### Post by shawnhcorey on 2011-06-23
What "special characters"?  Do you know the encoding of the text?

If it's UTF-8, try:
```

my $result_file = shift @ARGV;

my $pattern = shift @ARGV;
my @file_list = glob $pattern;

open( my $out_fh, '>:encoding(utf8)', $result_file ) or die "Could not open '$result_file': $!\n";

foreach my $in_file (@file_list) { 
   open( my $in_fh, '<:encoding(utf8)', $in_file ) or die "Could not open '$in_file': $!\n"; 
   while (<$in_fh>) {
      chomp;
      print $out_fh $_ . ',' . $in_file . "\n" ;
      }
   close ($in_fh);
   }

close ($out_fh);

```

You should use the three-argument open since it allows you to specify the encoding in the open.

You should use lexical file handles so they won't interfere with others.

---

### Post by dethorpe on 2011-06-23
Hi,
 
Havn't used Text:CVS_XS myself, but looking at its CPAN doc i think something like this is what you may need:
 
```
 
#!/usr/bin/perl
use Text::CSV_XS;
 
my $result_file=shift;
my $pattern=shift;
my (@file_list) = glob $pattern;
 
open( OUT, ">$result_file") or die "Can't open '$result_file':$!";
foreach my $in_file (@file_list) {
   my $csv = Text::CSV_XS->new ({ binary => 1, eol => $/ });
   open(my $fh, '<',"$in_file");
   while (my $row = $csv->getline($fh)) {
      chomp $row;
      print OUT $row . ',' . $in_file . "\n" ;
      }
   close ($fh);
   }
close (OUT);
 

```
 
This is just minimal mods to your script to use Text::CVS_XS in binary mode to handle the embeded newlines. Note i havn't been able to run this as can't install the module at the moment on work PC so may not work and I think this may only work if fields with newlines are quoted in your data.
 
If fields with newlines are not quoted you may need to have a know unique start or end of row/record tag/delimiter, can then detect that and only add filename on line that is actual end or record.
 
If you post sample of your data I may be able to have a look and suggest/try something else.

---

### Post by franestepona on 2011-06-24
Hi!

Thank you very much for both answers.

@shawnhcorey: Yes I think the encoding is UTF-8. The script I have does just fine, however, it only opens the first file in the directory and ignore the rest. All files are named "number_surname_name.csv".

@dethorpe: I tried your script and it produced

```
ARRAY(0x891b818),/home/fran/Desktop/chalmers/100_LARSSON_KRISTIAN.csv
ARRAY(0x891b818),/home/fran/Desktop/chalmers/100_LARSSON_KRISTIAN.csv
ARRAY(0x891b818),/home/fran/Desktop/chalmers/100_LARSSON_KRISTIAN.csv
ARRAY(0x891b818),/home/fran/Desktop/chalmers/100_LARSSON_KRISTIAN.csv
```

again it only took the first file :(

Here is a sample of my data:

```
"Innography URL",Assignee,"Publication Number","Publication Country","Publication Date",Source,Title,Abstract,"Application Number",Citations,"Est. Expiration Date","Family ID","File Date","First Claim","All Claims",Inventors,"First IP Classification","All IPC Classifications","Kind Code","Priority Date","Normalized Assignee","Number of Claims","Number of Backward References","Number of Forward References","Original Assignee",Strength,"Ultimate Parent","US Classification"
"=Hyperlink(""https://app.innography.com/patents/92619518"",""Innography Link"")","St. Jude Medical Ab",US20100099994,US,2010-04-22,"US Applications","Implantable heart analyzing device, system and method","An implantable heart analyzing device has a housing and a control circuit located within said housing. The control circuit generates an output signal adapted to actuate an activator which is able to make a wall of the heart deflect or vibrate. The control circuit also communicates with a sensor which can be identical with the activator with which the movement of the heart wall can be sensed. The control circuit executes a procedure that involves the generation of an output signal and sensing a corresponding sensor signal and to be able to derive information concerning the tension of the heart wall. An implantable heart analyzing includes the aforementioned heart analyzing device as well as the activator and the sensor. The heart analyzing device and the system implement a method that results in generation of the aforementioned information concerning the tension of the heart wall.",US11/528160,,2027-02-28,39721469,2007-02-28,1.-,"1. 1.-

2. (canceled)

3. An implantable heart analyzing device comprising:
a housing configured for in vivo implantation in a patient;
a control circuit contained within said housing;
said control circuit comprising output circuitry configured to electrically communicate with an activator positioned in contact with a heart wall, selected from the group consisting of an inner wall and an outer wall, of the heart of the subject, said output circuitry being configured to generate an output signal that causes said activator to deflect or vibrate said heart wall;
said control circuit comprising input circuitry configured to electrically communicate with a sensor that supplies a sensor signal to said input circuitry representing movement of said heart wall; and
said control circuit being configured to implement a session comprising generating at least one output signal with said output circuitry and supplying said output signal from said output circuitry to said activator, and detecting said sensor signal representing movement of the heart wall caused by said activator within a predetermined time interval, said sensor signal having a sensor signal morphology, and to automatically evaluate said sensor signal morphology to identify information representing tension of said heart wall.

4. An implantable heart analyzing device as claimed in claim 31 comprising a memory in said implantable device connected to said control circuit, said memory having information electronically stored therein representing a stored sensor signal morphology, and wherein said control circuit determines said information representing tension of said heart wall by comparing the sensor signal morphology represented by the detected sensor signal with the stored sensor signal morphology in said memory.

5. An implantable heart analyzing device as claimed in claim 31 wherein said control circuit is configured to implement said session in time cycles corresponding to heart cycles of the heart of the subject.

6. An implantable heart analyzing device as claimed in claim 33 wherein said control circuit is configured to implement said session during a portion of said time cycle corresponding to a late portion of the diastolic phase of the heart cycle of the heart of the subject.

7. An implantable heart analyzing device as claimed in claim 31 comprising a memory connected to said control circuit in said housing, and wherein said control circuit is configured to implement said session a plurality of times respectively in different heart cycles of the heart of the subject, and to obtain said information describing tension of the heart wall in each session as a session result, and to store the respective session results in said memory, and to evaluate the respective session results in said memory to determine a change in said tension of the heart wall between different sessions.

8. An implantable heart analyzing device as claimed in claim 35 wherein said control circuit is configured to implement said session in a same part of each of said different heart cycles.

9. An implantable heart analyzing device as claimed in claim 35 wherein said control circuit is configured to implement said session multiple times within a single heart cycle of the heart of the subject.

10. An implantable heart analyzing device as claimed in claim 37 wherein said control circuit is configured to identify a relationship between at least two of the sensor signals for respective sessions within said single heart cycle, and to store said relationship in said memory.

11. An implantable heart analyzing device as claimed in claim 38 wherein said control circuit is configured to implement said session multiple times in each of a plurality of different heart cycles of the heart of the subject, and to determine said relationship of at least two of said sensor signals respectively obtained in different ones of said plurality of heart cycles, and to determine a change in said relationship between said different ones of said heart cycles.

12. An implantable heart analyzing device as claimed in claim 31 wherein said output circuitry is configured to generate said output signal in a form selected from the group consisting of pulses and voltage steps.

13. An implantable heart analyzing device as claimed in claim 31 wherein said activator is a piezoelectric device.

14. An implantable heart analyzing device as claimed in claim 31 wherein said control circuit is configured to begin said time interval within 30 ms after generating said output signal with said output circuitry.

15. An implantable heart analyzing device as claimed in claim 31 wherein said control circuit is configured to set said time interval as being less than 200 ms in duration.

16. An implantable heart analyzing device as claimed in claim 31 wherein said control circuit is configured to evaluate the morphology of the sensor signal by identifying an attenuation of the sensor signal within said time interval as a measure of said tension of the heart wall.

17. An implantable heart analyzing system comprising:
an activator configured for in vivo placement on a heart wall, selected from the group consisting of an inner heart wall and an outer heart wall, of the heart of a subject, said activator being operable to cause said heart wall to deflect or vibrate;
a sensor configured for in vivo placement at said heart wall to detect movement of said heart wall;
a housing configured for in vivo implantation in the subject;
a control circuit contained in said housing, said control circuit comprising output circuitry electrically connected to said activator and input circuitry electrically connected to said sensor;
said output circuitry being configured to generate an output signal that causes said activator to deflect or vibrate said heart wall;
said input circuitry being configured to detect, within a predetermined time interval, a sensor signal from said sensor representing movement of said heart wall in response to operation of said activator, said sensor signal having a sensor signal morphology; and
said control circuit being configured to implement a session, comprising generating said output signal and detecting said sensor signal in said time interval, and to evaluate said sensor signal morphology to derive information representing tension of said heart wall.

18. An implantable heart analyzing system as claimed in claim 45 wherein said activator is the same component as said sensor.

19. A method for monitoring a heart comprising the steps of:
implanting an activator in vivo in contact with a heart wall, selected from the group consisting of an inner wall and an outer wall, of the heart of the subject; said
placing said activator in communication with a control circuit and, from output circuitry of said control circuit, generating an output signal that causes said activator to deflect or vibrate said heart wall;
implanting a sensor in vivo at a location to sense movement of said heart wall and placing said sensor in communication with said control circuit and supplying a sensor signal to input circuitry of said control circuit representing said movement of said heart wall; and
in said control circuit, implementing a session comprising generating at least one output signal with said output circuitry and supplying said output signal from said output circuitry to said activator, and detecting said sensor signal representing movement of the heart wall caused by said activator within a predetermined time interval, said sensor signal having a sensor signal morphology, and automatically evaluating said sensor signal morphology to identify information representing tension of said heart wall.

20. A method as claimed in claim 47 comprising, in a memory in communication with said control circuit, storing information representing a stored sensor signal morphology and, in said control circuit, determining said information representing tension of said heart wall by comparing the sensor signal morphology represented by the detected sensor signal with the stored sensor signal morphology in said memory.

21. A method as claimed in claim 47 comprising, in said control circuit, implementing said session in time cycles corresponding to heart cycles of the heart of the subject.

22. A method as claimed in claim 49 comprising, in said control circuit, implementing said session during a portion of said time cycle corresponding to a late portion of the diastolic phase of the heart cycle of the heart of the subject.

23. A method as claimed in claim 47 comprising placing said control circuit in communication with a memory and, in said control circuit, implementing said session a plurality of times respectively in different heart cycles of the heart of the subject, and obtaining said information describing tension of the heart wall in each session as a session result, and storing the respective session results in said memory, and evaluating the respective session results in said memory to determine a change in said tension of the heart wall between different sessions.

24. A method as claimed in claim 50 comprising, in said control circuit, implementing said session in a same part of each of said different heart cycles.

25. A method as claimed in claim 50 comprising, in said control circuit, implementing said session multiple times within a single heart cycle of the heart of the subject.

26. A method as claimed in claim 53 comprising, in said control circuit, identifying a relationship between at least two of the sensor signals for respective sessions within said single heart cycle, and to storing said relationship in said memory.

27. A method as claimed in claim 54 comprising, in said control circuit, implementing said session multiple times in each of a plurality of different heart cycles of the heart of the subject, and determining said relationship of at least two of said sensor signals respectively obtained in different ones of said plurality of heart cycles, and determining a change in said relationship between said different ones of said heart cycles.

28. A method as claimed in claim 47 comprising, from said output circuitry, generating said output signal in a form selected from the group consisting of pulses and voltage steps.

29. A method as claimed in claim 47 comprising employing a piezoelectric device as said activator.

30. A method as claimed in claim 47 comprising, in said control circuit, beginning said time interval within 30 ms after generating said output signal with said output circuitry.

31. A method as claimed in claim 47 comprising, in said control circuit, setting said time interval as being less than 200 ms in duration.

32. A method as claimed in claim 47 comprising, in said control circuit, evaluating the morphology of the sensor signal by identifying an attenuation of the sensor signal within said time interval as a measure of said tension of the heart wall.

33. A method as claimed in claim 47 comprising employing the same component as said analyzer and said sensor.

34. A method as claimed in claim 47 comprising placing said activator in the pericardium of the heart of the subject.

35. A method as claimed in claim 47 comprising placing said activator in the septum between chambers in the heart of the subject.

36. A computer-readable medium encoded with programming instructions that operate a control circuit of an implantable heart analyzing system comprising an activator configured for in vivo placement on a heart wall, selected from the group consisting of an inner heart wall and an outer heart wall, of the heart of a subject, said activator being operable to cause said heart wall to deflect or vibrate, a sensor configured for in vivo placement at said heart wall to detect movement of said heart wall, and said control circuit comprising output circuitry electrically connected to said activator and input circuitry electrically connected to said sensor, said programming instructions causing said control circuit to:
from said output circuitry, generate an output signal that causes said activator to deflect or vibrate said heart wall;
with said input circuitry, detect, within a predetermined time interval, a sensor signal from said sensor representing movement of said heart wall in response to operation of said activator, said sensor signal having a sensor signal morphology; and
implement a session, comprising generating said output signal and detecting said sensor signal in said time interval, and evaluate said sensor signal morphology to derive information representing tension of said heart wall.

","Nils  HolmstrÃ¶m Andreas  Blomqvist Berit  Larsson Karin  JÃ¤rverud Sven-erik  Hedberg ",A61B00500200,"A61B 005/020",A1,2007-02-28,"St. Jude Medical Ab",0,0,0,,"0th-10th Percentile","St. Jude Medical, Inc.",600508000
```

Thank you again for your help!

---

### Post by dethorpe on 2011-06-27
Ah, didn't fully understand the Text::CVS_XS usage, getline() returns array ref of columns, not just the record as a string.

Try this instead:

```
use Text::CSV_XS;

my $result_file=shift;
my $pattern=shift;
my (@file_list) = glob $pattern;

open( OUT, ">$result_file") or die "Can't open '$result_file':$!";
foreach my $in_file (@file_list) {
   my $csv = Text::CSV_XS->new ({ binary => 1, eol => $/ });
   open(my $fh, '<',"$in_file");
   while (my $columns = $csv->getline($fh)) {
        $csv->combine(@{$columns});
        my $record = $csv->string();
        chomp $record;
        print OUT $record . ',' . $in_file . "\n" ;
      }
   close ($fh);
   }
close (OUT);

```Your probably not quoting the pattern on the command line which is why only the 1st file is processed. Need to call it like this:

```
$ script.pl output.txt "*.csv"
```If you don't have the quotes on the file pattern the shell will expend it first and pass the actual list of files so the second shift statement will just get the first file name as the pattern and the glob will then justs return that one name.

Hope that helps.

---

