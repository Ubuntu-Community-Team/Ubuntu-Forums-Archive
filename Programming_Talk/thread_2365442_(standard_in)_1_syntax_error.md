---
title: "(standard_in) 1: syntax error"
date: 2017-07-06
forum: Programming Talk
---

### Post by drli0822 on 2017-07-06
This is my code.

```
rm EvsA EvsV evfit.4 SUMMARY

sT="$(date +%s)"

# Set the range and number of points generated
low=`echo 0.8\*$2 | bc`         # Sets the lower bound to 80% of guess
high=`echo 1.2\*$2 | bc`        # Sets the upper bound to 120% of guess
step=`echo "($high-$low)/2" | bc -l`    # Sets stepsize such that 20 points are created
for a in `seq -w $low $step $high`
do
#a=4.8
echo "a= $a" 
a_au=`echo "$a/0.529" | bc -l`

# Lattice vectors with fewest atoms
if [ "$1" == fcc ] || [ "$1" == bcc ]
then 
natom=1

elif [ "$1" == hcp ]
then
natom=2

fi

input=$1.ev.in
 
# sed the lattice parameter
curr=`grep "celldm(1)" $input | awk '{print $4}'`
sed -i "s/celldm(1) $curr/celldm(1) =$a_au,/g" $input

# Run Quantum Espresso with the correct input deck
# Must provide path to executable
pw.x < $input > pw_ev.out

# Gather energy and volume data from the output file
# Store the data in "EvsA" and "EvsV" text files
V=`grep volume pw_ev.out | awk '{print $4}'`
E=`grep "! *[ ] total energy" pw_ev.out | awk '{print $5}'`
# Convert volume to Ang^3 and energy to eV
V=`echo "$V*0.1481847" | bc -l`
E=`echo "$E/$natom*13.605685" | bc -l`
echo $a $E >> EvsA
echo $V $E >> EvsV

# Restart
done
```

When I run it, I get the below error. Can someone help me fix it? 

```
a= 3.79999999999999999996
(standard_in) 1: syntax error
(standard_in) 1: syntax error
a= 4.75000000000000000000
(standard_in) 1: syntax error
(standard_in) 1: syntax error
a= 5.69999999999999999983
(standard_in) 1: syntax error
(standard_in) 1: syntax error
```

---

### Post by steeldriver on 2017-07-06
Well, those are typical errors when piping into bc

I suspect one or more of your variable assignments is failing e.g.

```

$ echo "$V*0.1481847" | bc -l
.4445541

```
but
```

$ V=
$ echo "$V*0.1481847" | bc -l
(standard_in) 1: syntax error

```

Maybe check your `greps`?

---

### Post by drli0822 on 2017-07-07
I've tested a few things, and I can confirm that the error is in this part:

```

# Gather energy and volume data from the output file
# Store the data in "EvsA" and "EvsV" text files
V=`grep volume pw_ev.out | awk '{print $4}'`
E=`grep "! *[ ] total energy" pw_ev.out | awk '{print $5}'`
# Convert volume to Ang^3 and energy to eV
V=`echo "$V*0.1481847" | bc -l`
E=`echo "$E/$natom*13.605685" | bc -l`
echo $a $E >> EvsA
echo $V $E >> EvsV

```

I still get this error:

```

(standard_in) 1: syntax error
(standard_in) 1: syntax error

```

How do I fix this?

---

### Post by drli0822 on 2017-07-07
I think that the syntax error comes from these lines:
```

# sed the lattice parameter
curr=`grep "celldm(1)" $input | awk '{print $4}'`
sed -i "s/celldm(1) $curr/celldm(1) =$a_au,/g" $input

# Run Quantum Espresso with the correct input deck
# Must provide path to executable
pw.x < $input > pw_ev.out

# Gather energy and volume data from the output file
# Store the data in "EvsA" and "EvsV" text files
V=`grep volume pw_ev.out | awk '{print $4}'`
E=`grep "! *[ ] total energy" pw_ev.out | awk '{print $5}'`
# Convert volume to Ang^3 and energy to eV
V=`echo "$V*0.1481847" | bc -l`
E=`echo "$E/$natom*13.605685" | bc -l`
echo $a $E >> EvsA
echo $V $E >> EvsV


```

When I open pw_ev.out, it says that I have the error 
```

     Error in routine  read_namelists (5010):
      reading namelist system

```

This is the system part of my input file.
```
 &system
    ibrav =  4, 
    celldm(1) =18.90359168241965973534,=17.01323251417769376181,=15.12287334593572778827,=13.23251417769376181474,=11.34215500945179584120,=9.45179584120982986767,=7.56143667296786389413,=5.67107750472589792060,=3.78071833648393194706,=1.89035916824196597353, 
celldm(3) = 1.588,   
    nat =  2, 
    ntyp = 1,
    ecutwfc = 35,
occupations='smearing', smearing='marzari-vanderbilt',degauss=0.05
 /

```
So, I think that the problem is with celldm(1) because everything else is standard. 
Is anything wrong with celldm(1)? Is there anything else wrong with the system part or with grep?

Thank you for any help!

---

### Post by steeldriver on 2017-07-07
You really need to be systematic and go LINE BY LINE checking that the assigned variables make sense

It looks to me like the line from your input file that matches "celldm(1)" does not have 4 (whitespace delimited) fields - hence the awk command will print nothing and '$curr' will be empty

Then the sed command will screw up your input file

Then pw.x (whatever that is) will barf and fail to produce the expected pw_ev.out file

Then your greps for V and E will return empty

Then your bc commands will be malformed

---

### Post by sisco311 on 2017-07-07
The format of your input file is the main problem here I think. bash, sed and awk aren't designed to parse such files.

But there must be more than one way to skin Schrödinger's cat. :)

Can you tell us more about what are you trying to accomplish? What are the tools you are using to generate  the input file? Do you have some control of its format?

---

