---
title: "simple shell scripting AWK problem"
date: 2010-01-13
forum: Programming Talk
---

### Post by umshiva on 2010-01-13
Hi Guys ,

I have a file Shi2

Cat shi2 gives me ...

1,2,01/07/2010,shi3


I wrote a prg to display me the local variable inside awk
 
#!/bin/ksh
 effdate="09012010"
 echo $effdate
 export effdate
  awk ' BEGIN { FS=","; OFS="," }
    {
        print $effdate
     }' shi1

it gives me whole record and not the variable 
Dont know whats the problem can u guys please check 
Regards,
Shiva

---

### Post by umshiva on 2010-01-13
Please reply

---

### Post by umshiva on 2010-01-13
Please help

---

### Post by akvino on 2010-01-13
What are you trying to do one more time? What input do you have and output do you want?

---

### Post by umshiva on 2010-01-18
Hi,

I will explain along with the script.

#!/bin/ksh
#effdate=`head -1 $in_dir/BATCHDATE | tail -1 | cut -c 10-18`
effdate="07012010"
      echo "Effective2 date format is $effdate"
      awk ' BEGIN { FS=","; OFS="," }
      {
      print "?????????????/????????????"
           print $effdate
      print "?????????????/????????????"

      gsub( "^..........", '$effdate', $7)
      print $0
      }' F11212.tmp2 > F11212.tmp3
      cat F11212.tmp3 | awk -F"," '{printf "%s,%s,%s,%9d,%s,%s,%8d,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s,%s\n",$1,$2,$3,$4,$5,$6,$7,$8,$9,$10,$11,$12,$13,$14,$15,$16,$17,$18,$19,$20,$21,$22,$23,$24,$25,$26,$27,$28,$29,$30,$31,$32,$33,$34,$35,$36,$37,$38,$39,$40,$41,$42,$43,$44,$45,$46,$47,$48,$49}' | sed 's/ /0/g' | sed 's/-/ /g' > F11212.tmp4
      cp -f F11212.tmp4 F11212.csv

Sample F11212.tmp2 which is been passed as an input to the awk comand is 

MCD,KS01,,68034809,,,07/01/2010,,0.01,,,,,,,,,,,,,,,,,,,I,,,,,,0000066719,,82591324,ICON-SECURITY-GROUP,,,,,31102009,,200023755904,0005,KSS/100040410000000052915934
MCD,KS01,,55981574,,,07/01/2010,,0.12,,,,,,,,,,,,,,,,,,,I,,,,,,0000066719,,20246723,PREBBLE-SEEDS-LIMITE,,,,,31102009,,200023713765,0004,KSS/100040410000000052895758

When i execute the above script i should get an output as shown below

MCD,KS01,,68034809,,,07012010,,0.01,,,,,,,,,,,,,,,,,,,I,,,,,,0000066719,,82591324,ICON-SECURITY-GROUP,,,,,31102009,,200023755904,0005,KSS/100040410000000052915934
MCD,KS01,,55981574,,,07012010,,0.12,,,,,,,,,,,,,,,,,,,I,,,,,,0000066719,,20246723,PREBBLE-SEEDS-LIMITE,,,,,31102009,,200023713765,0004,KSS/100040410000000052895758

But i am getting the below output.01840136

MCD,KS01,,68034809,,,**01840136**,,0.01,,,,,,,,,,,,,,,,,,,I,,,,,,0000066719,,82591324,ICON-SECURITY-GROUP,,,,,31102009,,200023755904,0005,KSS/100040410000000052915934
MCD,KS01,,55981574,,,**01840136**,,0.12,,,,,,,,,,,,,,,,,,,I,,,,,,0000066719,,20246723,PREBBLE-SEEDS-LIMITE,,,,,31102009,,200023713765,0004,KSS/100040410000000052895758

Instead of 07012010 i am getting 01840136 in the 7th field it is happening on for few dates like 07012010,08012010 for rest of the other dates the above script is giving the correct output.
Not sure why this is happning only for 7th and 8th of 2010 jan.

I tried all my luck but not happening..

Please help me out from this.

Kind Regards,
Shiva

---

### Post by saulgoode on 2010-01-18
```
gsub( "^..........", '$effdate', $7)
```
The single quotes around $effdate seems unkosher.

---

### Post by umshiva on 2010-01-19
> **saulgoode said:**
> ```
gsub( "^..........", '$effdate', $7)
```
The single quotes around $effdate seems unkosher.



If single quotes is removed then effdate is coming up as 00000000(zeroes).

sample output

MCD,KS01,,068034809,,,**00000000**,KS01,,068034809,,,17012010,,0.01,,,,,,,,,0000066719,,,,,,,,,,I,,,,,,0000066719,,82591324,ICON SECURITY GROUP,,,,,31102009,
MCD,KS01,,055981574,,,**00000000**,KS01,,055981574,,,17012010,,0.12,,,,,,,,,0000066719,,,,,,,,,,I,,,,,,0000066719,,20246723,PREBBLE SEEDS LIMITE,,,,,31102009,

---

### Post by umshiva on 2010-01-19
If single quotes is removed then effdate is coming up as 00000000(zeroes).

sample output

MCD,KS01,,068034809,,,00000000,KS01,,068034809,,,17012010,,0.01,,,,,,,,,00000667 19,,,,,,,,,,I,,,,,,0000066719,,82591324,ICON SECURITY GROUP,,,,,31102009,
MCD,KS01,,055981574,,,00000000,KS01,,055981574,,,17012010,,0.12,,,,,,,,,00000667 19,,,,,,,,,,I,,,,,,0000066719,,20246723,PREBBLE SEEDS LIMITE,,,,,31102009,

---

### Post by saulgoode on 2010-01-19
Your fprint format is printing out $effdate as an integer (%8d), yet it appears as a string.

---

### Post by umshiva on 2010-01-22
> **saulgoode said:**
> Your fprint format is printing out $effdate as an integer (%8d), yet it appears as a string.


So what can be done in this scenario any idea please.

---

### Post by umshiva on 2010-01-22
Hi,

Please help me,I need to replace only 7th columns in a file with 07012010

Input file is as shown below
MCD,KS01,, 68034809,,,**07/01/2010**,,0.01,,,,,,,,,0000066719,,,,,,,,,,I,,,,,,0000066719,,82591324,ICON-SECURITY-GROUP,,,,,31102009,,,07/01/2010,KSS/100040410000000052915934,,200023755904,0005
MCD,KS01,, 55981574,,,**07/01/2010**,,0.12,,,,,,,,,0000066719,,,,,,,,,,I,,,,,,0000066719,,20246723,PREBBLE-SEEDS-LIMITE,,,,,31102009,,,07/01/2010,KSS/100040410000000052895758,,200023713765,0004
MCD,KS01,, 63990086,,,**07/01/2010**,0.29,,,,,,,,,,0000066719,,,,,,,,,I,,,,,,,0000066719,,56113381,APPRENTICESHIP-TO-IN,,,,,31102009,,,07/01/2010,KSS/100040410000000052907982,,200023738686,0005
MCD,KS01,, 63990086,,,**07/01/2010**,,0.01,,,,,,,,,0000066719,,,,,,,,,,I,,,,,,0000066719,,56113381,APPRENTICESH

expected output file is 
MCD,KS01,, 68034809,,,**07012010**,,0.01,,,,,,,,,0000066719,,,,,,,,,,I,,,,,,0000066719,,82591324,ICON-SECURITY-GROUP,,,,,31102009,,,07/01/2010,KSS/100040410000000052915934,,200023755904,0005
MCD,KS01,, 55981574,,,**07012010**,,0.12,,,,,,,,,0000066719,,,,,,,,,,I,,,,,,0000066719,,20246723,PREBBLE-SEEDS-LIMITE,,,,,31102009,,,07/01/2010,KSS/100040410000000052895758,,200023713765,0004
MCD,KS01,, 63990086,,,**07012010**,0.29,,,,,,,,,,0000066719,,,,,,,,,I,,,,,,,0000066719,,56113381,APPRENTICESHIP-TO-IN,,,,,31102009,,,07/01/2010,KSS/100040410000000052907982,,200023738686,0005
MCD,KS01,, 63990086,,,**07012010**,,0.01,,,,,,,,,0000066719,,,,,,,,,,I,,,,,,0000066719,,56113381,APPRENTICESH

Can you please let me know the exact comand to do this.

---

### Post by umshiva on 2010-01-24
HI,

This is my input record
MCD,KS01,,68034809,,,**01840136**,,0.01,,,,,,,,,,,,,,,,,,,I,,,,,,0000066719,,825913 24,ICON-SECURITY-GROUP,,,,,31102009,,200023755904,0005,KSS/100040410000000052915934
MCD,KS01,,55981574,,,**01840136**,,0.12,,,,,,,,,,,,,,,,,,,I,,,,,,0000066719,,202467 23,PREBBLE-SEEDS-LIMITE,,,,,31102009,,200023713765,0004,KSS/100040410000000052895758

Now i need to replace only the 7th column that is **01840136**
with 11111111

Please help me

---

