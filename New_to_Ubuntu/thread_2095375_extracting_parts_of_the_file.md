---
title: "extracting parts of the file"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by jhuuht9 on 2012-12-16
How could I change parts of the file, into separate files in ubuntu? in other words extract things with labels and save them separately?

thanks so much if someone could help!

---

### Post by Cheesemill on 2012-12-16
We need more information.

What sort of files are these?
What exactly are you trying to extract?

---

### Post by jhuuht9 on 2012-12-16
They are .dat files,

they contain x-y data for 11 different graphs, I need to extract two of them.


When I save them using

egrep [label of the graph] directory/file.dat>name of the extracted file

it says the new files are ASCII English text files, im somehow saving them into something else but not files, I think?

---

### Post by steeldriver on 2012-12-16
have you tried actually opening the file(s) in a text editor? it's almost impossible to advise you until we know the format of the data in the files

---

### Post by jhuuht9 on 2012-12-16
I would, but the files are not in computer, they are on the linux server.

Do you have any idea how to save the data to the computer? Using which commands?

It is a .dat file, that is what it says

---

### Post by jhuuht9 on 2012-12-16
[linappserv0]%~> sed -n 'Hist = 1' HWW_4l_lord_cteq66m_170_170_sig_LO.dat > deltasig

Here I was trying to extract certain section of the data into another file, but it says that:

sed: -e expression #1, char 2: extra characters after command

what does it mean?

---

### Post by steeldriver on 2012-12-16
it means you don't know how to speak sed ;)

it thinks H is a command (it appends the pattern space to the **H**old space) and then doesn't know what to do with 'ist = 1'

if you explain exactly the format of the file (or post a segment here) and what you want to extract from it I'm sure someone will be able to help you

EDIT: guessing you want to find the text 'Hist = 1' and extract it plus some number of following lines? if so try something like 

```
sed -n '/Hist = 1/,+20p' yourfile.dat
```

(replace 20 by the number of following lines that you want)

---

### Post by MG&amp;TL on 2012-12-16
> **jhuuht9 said:**
> I would, but the files are not in computer, they are on the linux server.

Do you have any idea how to save the data to the computer? Using which commands?

It is a .dat file, that is what it says

What sort of server? HTTP, FTP, SSH?

.dat is just data. File extensions aren't indicative on Linux anyway.

Anyway, since you seem to have a shell, can you post the output of:

```
cat <file>.dat
```

..replacing <file> with your .dat file?

---

### Post by jhuuht9 on 2012-12-16
this is a part of the file, so it looks like this, but it has many of them,

 cat mdata

( Cross-section is:           296.6021208976 +/-            0.1888307829)
 ( Contribution from parton sub-processes:
 ( Run corresponds to this input file)
 ( [Flags to specify the mode in which MCFM is run] )
 (                   F            [evtgen] )
 (                   F            [creatent] )
 ( [General options to specify the process and execution] )
 (bkg_LO                          [runstring] )
 (             80.3980            [scale] )
 (             80.3980            [facscale] )
 (                   F            [dynamicscale] )
 (                   F            [zerowidth] )
 (                   F            [removebr] )
 ( [Heavy quark masses] )
 ( [Pdf selection] )
 (             cteq66m            [pdlabel ] )
 (cteq6mE.LHgrid                  [LHAPDF group] )
 (                  -1            [LHAPDF set] )
 ( [Jet definition and event cuts] )
 (                   T            [inclusive] )
 (              0.0000            [ptjetmin] )
 (        1000000.0000            [etajetmax] )
 (                   T            [makecuts] )
 (             20.0000            [leptpt] )
 (              2.5000            [leptrap] )
 (             20.0000            [leptpt2] )
 (              2.5000            [leptrap2] )
 (              0.0000            [delyjjmin] )
 (                   F            [jetsopphem] )
 (                   0            [lbjscheme] )
 (              0.7000            [gammcone] )
 ( [Anomalous couplings of the W and Z] )
 (              0.0000            [delg1_z] )
 (              0.0000            [delk_z] )
 (              0.0000            [delk_g] )
 (              0.0000            [lambda_z] )
 (              0.0000            [lambda_g] )
 (              2.0000            [tevscale] )
 ( [How to resume/save a run] )
 (                   F            [readin] )
 (                   F            [writeout] )
 (                                [ingridfile] )
 (                                [outgridfile] )
 DeltaPhi_ee                                                                                         
 AVG = 0.110E+03     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 M_ee                                                                                                
 AVG = 0.903E+02     RMS = 0.000E+00 INTEGRAL = 0.260E+03
 AVG = 0.182E+03     RMS = 0.000E+00 INTEGRAL = 0.293E+03
 AVG = 0.500E+00     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 AVG = 0.500E+00     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 eta3                                                                                                
 AVG = 0.126E-02     RMS = 0.000E+00 INTEGRAL = 0.290E+03
 AVG = 0.126E-02     RMS = 0.000E+00 INTEGRAL = 0.290E+03
 AVG = 0.408E+02     RMS = 0.000E+00 INTEGRAL = 0.293E+03
 eta4                                                                                                
 AVG = 0.108E-03     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 AVG = 0.108E-03     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 AVG = 0.366E+02     RMS = 0.000E+00 INTEGRAL = 0.158E+03
 AVG = 0.478E+02     RMS = 0.000E+00 INTEGRAL = 0.291E+03
 AVG = 0.514E+02     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 eta34                                                                                               
 AVG = 0.645E-03     RMS = 0.000E+00 INTEGRAL = 0.285E+03
 AVG = 0.603E-03     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 AVG = 0.429E+02     RMS = 0.000E+00 INTEGRAL = 0.258E+03
 AVG = 0.817E+02     RMS = 0.000E+00 INTEGRAL = 0.295E+03
 AVG = 0.830E+02     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 misset                                                                                              
 AVG = 0.496E+02     RMS = 0.000E+00 INTEGRAL = 0.291E+03
 eta5                                                                                                
 AVG = 0.113E-02     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 eta5                                                                                                
 AVG = 0.122E-02     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 AVG = 0.513E+02     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 AVG = 0.423E+02     RMS = 0.000E+00 INTEGRAL = 0.295E+03
 eta345                                                                                              
 AVG = 0.272E-02     RMS = 0.000E+00 INTEGRAL = 0.278E+03
 AVG = 0.915E-03     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 AVG = 0.170E+03     RMS = 0.000E+00 INTEGRAL = 0.249E+03
 eta6                                                                                                
 AVG = 0.140E-02     RMS = 0.000E+00 INTEGRAL = 0.295E+03
 AVG = 0.434E+02     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 eta56                                                                                               
 AVG = 0.143E-02     RMS = 0.000E+00 INTEGRAL = 0.290E+03
 AVG = 0.515E+02     RMS = 0.000E+00 INTEGRAL = 0.270E+03
 AVG = 0.245E+01     RMS = 0.000E+00 INTEGRAL = 0.294E+03
 AVG = 0.210E+01     RMS = 0.000E+00 INTEGRAL = 0.296E+03
 AVG = 0.816E+02     RMS = 0.000E+00 INTEGRAL = 0.296E+03
 AVG = 0.771E+02     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 eta5-eta6                                                                                           
 AVG = 0.171E-03     RMS = 0.000E+00 INTEGRAL = 0.297E+03
 eta7                                                                                                
 AVG = 0.110E+01     RMS = 0.000E+00 INTEGRAL = 0.609E+02
 HISTOGRAM  37 IS EMPTY
 HISTOGRAM  38 IS EMPTY
 HISTOGRAM  39 IS EMPTY
 HISTOGRAM  40 IS EMPTY
 HISTOGRAM  41 IS EMPTY
 HISTOGRAM  42 IS EMPTY
 HISTOGRAM  43 IS EMPTY
 HISTOGRAM  44 IS EMPTY
 HISTOGRAM  45 IS EMPTY
 HISTOGRAM  46 IS EMPTY
 HISTOGRAM  47 IS EMPTY
 HISTOGRAM  48 IS EMPTY
 HISTOGRAM  49 IS EMPTY
 HISTOGRAM  50 IS EMPTY
 HISTOGRAM  51 IS EMPTY
 HISTOGRAM  52 IS EMPTY

So I need to extract the data, starting from where it has written: DeltaPhi_ee, and all the data table after that. 

The actual data file is called like this (I hope it helps to see what format of the file it is)

HWW_41_lord_cteq66m_170_170_sig_Lo.dat

or is there any other way than 'file' to find out what format of the file it is?

---

### Post by jhuuht9 on 2012-12-16
> **MG&TL said:**
> What sort of server? HTTP, FTP, SSH?

.dat is just data. File extensions aren't indicative on Linux anyway.

Anyway, since you seem to have a shell, can you post the output of:

```
cat <file>.dat
```..replacing <file> with your .dat file?




It is an ssh server. I have tried that it works. 

What kind of files there could be if the extention doesnt tell it?

---

### Post by jhuuht9 on 2012-12-16
> **steeldriver said:**
> it means you don't know how to speak sed ;)

it thinks H is a command (it appends the pattern space to the **H**old space) and then doesn't know what to do with 'ist = 1'

if you explain exactly the format of the file (or post a segment here) and what you want to extract from it I'm sure someone will be able to help you

EDIT: guessing you want to find the text 'Hist = 1' and extract it plus some number of following lines? if so try something like 

```
sed -n '/Hist = 1/,+20p' yourfile.dat
```(replace 20 by the number of following lines that you want)


Ok, I did that, it worked, but how do I find out what number of lines are the pieces of text I need other thatn counting?

---

### Post by steeldriver on 2012-12-16
You can redirect the standard output stream just like you did before, i.e.

```
 sed -n '/Hist = 1/,+20p' *yourfile*.dat > *newfile*
```

---

### Post by jhuuht9 on 2012-12-16
> **steeldriver said:**
> You can redirect the standard output stream just like you did before, i.e.

```
 sed -n '/Hist = 1/,+20p' *yourfile*.dat > *newfile*
```


Ok, thanks,

Can I use words instead of the line numbers in that command?

---

### Post by jhuuht9 on 2012-12-16
I got the data, but i counted the numbers of lines :D

Thanks for help though!

---

### Post by steeldriver on 2012-12-16
sorry - too late but yes you can use letters (*patterns*) to mark both ends of the range, e.g.

sed -n '/start pattern/,/end pattern/p' *yourfile*.dat > [I]newfile

[/I]It's obviously better to do that if the number of data lines varies from case to case

---

### Post by jhuuht9 on 2012-12-16
> **steeldriver said:**
> sorry - too late but yes you can use letters (*patterns*) to mark both ends of the range, e.g.

sed -n '/start pattern/,/end pattern/p' *yourfile*.dat > [I]newfile

[/I]It's obviously better to do that if the number of data lines varies from case to case

Thanks for that. I also discovered where to see the numbers of lines after a bit!

Do you know how to multiply the whole date filer by a constant ( in my case 5), 
I tried doing this, but it just gives me an empty file:

cat file| grep -v "#"|awk '{print$"constant(mult.factor)"}'>file1

---

### Post by steeldriver on 2012-12-16
you should be able to multiply specific awk fields simply by

```
awk '{print $2*5, $3*5}'
```you could also likely do the line selection directly in awk (removing the need for grep) I think

```
awk '/^[^#]/ {print $2*5, $3*5}'
```(the _regular expression_ ^[^#] says 'records starting with anything except #')

---

### Post by jhuuht9 on 2012-12-16
> **steeldriver said:**
> you should be able to multiply specific awk fields simply by

```
awk '{print $2*5, $3*5}'
```you could also likely do the line selection directly in awk (removing the need for grep) I think

```
awk '/^[^#]/ {print $2*5, $3*5}'
```(the _regular expression_ ^[^#] says 'records starting with anything except #')


Thanks so much, I got it to work :)!

---

