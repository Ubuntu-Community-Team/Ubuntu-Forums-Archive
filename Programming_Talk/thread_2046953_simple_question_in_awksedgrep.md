---
title: "simple? question in awk/sed/grep"
date: 2012-08-23
forum: Programming Talk
---

### Post by stevieP on 2012-08-23
I have a simple question in awk, or sed or grep
suppose I want to read a file and print out every line up to and including a given expression. 
Here is an example file:

[PHP]
HEADER    IMMUNE SYSTEM                           24-JUL-01   1JNJ              
TITLE     NMR SOLUTION STRUCTURE                
COMPND    MOL_ID: 1;                                                            
COMPND   2 MOLECULE: BETA2-MICROGLOBULIN;                                       
ATOM     23  O   ILE A   1      -2.899 -19.630  -3.642  1.00  0.00           O  
ATOM     24  CB  ILE A   1      -2.389 -22.441  -3.644  1.00  0.00           C  
ATOM     32 HG13 ILE A   1      -1.569 -24.333  -4.276  1.00  0.00           H  
ATOM     33 HG21 ILE A   1      -1.068 -22.119  -1.948  1.00  0.00           H  
ATOM     34 HG22 ILE A   1      -0.236 -22.584  -3.448  1.00  0.00           H  
ATOM    767  HB3 GLU A  47       5.674   7.664 -11.282  1.00  0.00           H  
ATOM    768  HG2 GLU A  47       3.235   7.139 -11.700  1.00  0.00           H  
ATOM    769  HG3 GLU A  47       2.852   8.831 -11.352  1.00  0.00           H  
ATOM    770  N   LYS A  48       6.056   8.485  -7.649  1.00  0.00           N  
ATOM    771  CA  LYS A  48       7.226   8.556  -6.785  1.00  0.00           C  
ATOM    772  C   LYS A  48       7.039   7.597  -5.606  1.00  0.00           C  
ATOM   1630  CE  MET A  99      -1.201  15.052  12.834  1.00  0.00           C  
ATOM   1631  OXT MET A  99      -4.601  14.678  11.618  1.00  0.00           O  
ATOM   1638  HE1 MET A  99      -2.192  15.464  12.648  1.00  0.00           H  
ATOM   1639  HE2 MET A  99      -0.880  15.310  13.843  1.00  0.00           H  
ATOM   1640  HE3 MET A  99      -0.497  15.471  12.117  1.00  0.00           H  
TER    1641      MET A  99                                                      
ENDMDL                                                                          
MODEL        2                                                                  
ATOM      1  N   MET A   0      -7.328 -24.381  -4.310  1.00  0.00           N  
ATOM      2  CA  MET A   0      -7.133 -23.021  -3.778  1.00  0.00           C  
ATOM      3  C   MET A   0      -6.133 -23.032  -2.619  1.00  0.00           C  
ATOM     33 HG21 ILE A   1      -4.192 -25.045  -2.176  1.00  0.00           H  
ATOM     34 HG22 ILE A   1      -2.597 -25.388  -1.496  1.00  0.00           H  
ATOM     35 HG23 ILE A   1      -3.830 -24.623  -0.484  1.00  0.00           H  
ATOM     36 HD11 ILE A   1      -2.653 -21.428  -4.153  1.00  0.00           H  
[/PHP]

suppose I want to print out everything either before "ENDMDL", or up to and including "ENDMDL"

Here is an answer: 
awk 'BEGIN {flag=0;}  {if (flag==0 && $1 !="ENDMDL") {print $0;} else {flag=1;}}'  FILENAME

This doesn't print out the last line containing ENDMDL. It suffices for my purposes, but I also think there must be an easier awk or sed one-liner  to do this, either printing out the line containing ENDMDL or not. 

Thanks,

StevieP

---

### Post by papibe on 2012-08-23
Hi stevieP.

If you use the 'exit' statement, it gets a little simpler.

Without the ending line:
```
awk  '/ENDMDL/{exit} {print}'  FILENAME
```
or with it:
```
awk  '/ENDMDL/{print; exit} {print}'  FILENAME
```
Regards.

---

### Post by stevieP on 2012-08-24
Nice, thanks papibe.

---

