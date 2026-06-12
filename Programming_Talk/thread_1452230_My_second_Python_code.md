---
title: "My second Python code"
date: 2010-04-11
forum: Programming Talk
---

### Post by eckeroo on 2010-04-11
Hello all,

Been a while since my last program, but now check out my second ever Python program..

I've created a program that calculates the force reactions at the redundancies of a multiple span beam. The supports are assumed pin-jointed.

The instructions for the 'beam input.txt' are as follows:

N [Node]
P [Force]
R [Redundancy]

The beam

N0------N1(P)------N2------N3(R3)------N4(R2)------N5(R1)
  

Enter the node number the force (P) is applied at and the magnitude of the force (negative is down)

Enter the properties of each span

make sure 'beam_unitload.py' and 'beam input.txt' are in the same directory and run 'python beam_unitload.py'

The program uses the unit load method to solve the reactions for an indeterminate beam. This program hasn't been fully tested so don't use it for an actual engineering application as it may be incorrect.

Please give me advice on the programming and in particular my use of Numpy. There are parts in the code I'm sure can be made simpler and more effective.

Any feedback will be much appreciated!

Cheers

input file 'beam input.txt':

[PHP]#Input file for Beam

#beam lengths (mm)				
16.8, 26.9, 43.1, 40.0, 36.0

#Beam stiffnesses (MPa)				
66240, 66240, 66240, 66240, 66240

#Beam 2nd moment of areas(mm^4)			
69666, 116952, 103020, 70946, 22150

#position and magnitude of applied load '0=1st node, load(N)'
1,-10000[/PHP]

main program 'beam_unitload.py':

[PHP]# Program to calculate the reaction forces for a multiple span beam with a pin-jointed supports

# reads input data into a list of strings

from scipy import array,append,sum,multiply,zeros,mat
from scipy.linalg import solve

rawinput=open('beam input.txt')
data=[]
for lines in rawinput:
    line = lines[:lines.find('#')]
    parsed = line.split(',')
    if bool(parsed[0])==True:
        flt = [float(entry) for entry in parsed]
        data.append(flt)
rawinput.close()

Lengths=data[0]
Evalues=data[1]
Ivalues=data[2]
Pnode=int(data[3][0])
Pload=data[3][1]

num_spans=len(Lengths)

# The statically determinate reactions, F(P)1 and F(P)2, need to be calculated first so
# bending moment combinations can be calculated depending on the position of the applied load.  

Redundancy = len(Lengths)-2

if Pnode ==1:
    P_moment_arm = sum(Lengths[:Pnode])
    FP2_moment_arm = sum(Lengths[:2])
    FP2 =-Pload*P_moment_arm/FP2_moment_arm
    FP1 = -Pload - FP2

    static_loads=[0,FP2*Lengths[1],FP2*sum(Lengths[:2])+Pload*Lengths[0]]
    static_loads=Redundancy*[0]+static_loads

elif Pnode >1:
    P_moment_arm = sum(Lengths[:Pnode])
    FP2_moment_arm = Lengths[0]
    FP2 =-Pload*P_moment_arm/FP2_moment_arm
    FP1 = -Pload - FP2      

    static_loads=[0,Pload*Lengths[1],Pload*sum(Lengths[:2])+FP2*Lengths[0]]
    static_loads=Redundancy*[0]+static_loads

elif Pnode <1:
    P_moment_arm = -sum(Lengths[:2])
    FP1_moment_arm = Lengths[1]
    FP1 =-Pload*P_moment_arm/FP1_moment_arm 
    FP2 = -Pload - FP1 

    static_loads=[0,FP2*Lengths[1],FP2*sum(Lengths[:2])+FP1*Lengths[0]]
    static_loads=Redundancy*[0]+static_loads

# Each section can only be assigned one value for a bending moment,
# as the bending moment varies linearly across each section, an average bending moment can therefore be assigned
# to each section.

static_loads=[(static_loads[x]+static_loads[x+1])/2 for x in range(num_spans)]
static_loads.reverse()

# A unit load is now applied at each of the redunancies in turn and the subsequent bending moments at the beginning
# and end of each section are calculated. 

unit_loads=range(Redundancy)

# As Python doesn't index 'Lengths[:-0]',  I had to reverse the whole list to do the summation I needed and reverse it back again.

LR = Lengths[:]
LR.reverse()

for u in unit_loads:

    unit_loads[u]=[sum(LR[u:x+1]) for x in range(num_spans)]
    unit_loads[u].insert(0,0)

    unit_loads[u].reverse()

# Each section can only be assigned one value for a bending moment,
# as the bending moment varies linearly across each section, an average bending moment can therefore be assigned
# to each section.

    unit_loads[u]=[(unit_loads[u][x]+unit_loads[u][x+1])/2 for x in range(num_spans)]


A=array(unit_loads)

B=array(unit_loads)

# Creating all the products of unit loads to form the coefficients of the Virtual Work Equations

VWeqns=zeros((Redundancy**2,num_spans))

x=0

for coef1 in range(Redundancy):
    for coef2 in range(Redundancy):
        VWeqns[x]=A[coef1]*B[coef2]
        x+=1

VWeqns=VWeqns*Lengths/Evalues/Ivalues

# Sum up all the members

VWeqns=sum(VWeqns,1)

# Fold the VWeqns array into a square matrix

VWeqns.shape=(Redundancy,Redundancy)

C=mat(VWeqns)

# Creating all the constants of the Virtual Work Equations

D = A*array(static_loads)*Lengths/Evalues/Ivalues
D = sum(D,1)


# Forces at the redundancies R1, R2,..

print solve(C,D)

# The remaining forces can be statically determined
[/PHP]

---

### Post by eckeroo on 2010-05-02
I've now corrected quite a lot of errors. The moments from the unit loads were not correct [the resultant of the external forces now equals zero]. I've now done some runs and checked it against hand calculations on a spreadsheet and it now returns sensible looking answers for all loading conditions and number of spans. For example, if you apply a load directly in the middle of a symmetrical beam, the resultants forces become symmetrical which is what you would expect. Also, mirrored loading conditions return the same resultant forces but in the opposite order.

Looking good. For my next trick I will use Pygame to graphically plot the beam deflections. 

[PHP]# Program to calculate the reaction forces for a multiple span beam with a pin-jointed supports

# reads input data into a list of strings

from scipy import array,append,sum,multiply,zeros,mat
from scipy.linalg import solve

rawinput=open('beam input.txt')
data=[]
for lines in rawinput:
    line = lines[:lines.find('#')]
    parsed = line.split(',')
    if bool(parsed[0])==True:
        flt = [float(entry) for entry in parsed]
        data.append(flt)
rawinput.close()

Lengths=data[0]
Evalues=data[1]
Ivalues=data[2]
Pnode=int(data[3][0])
Pload=data[3][1]


num_spans=len(Lengths)

# The statically determinate reactions, F(P)1 and F(P)2, need to be calculated first so
# bending moment combinations can be calculated depending on the position of the applied load.  

Redundancy = len(Lengths)-2

if Pnode ==1:
    P_moment_arm = sum(Lengths[:Pnode])
    FP2_moment_arm = sum(Lengths[:2])
    FP2 =-Pload*P_moment_arm/FP2_moment_arm
    FP1 = -Pload - FP2

    static_loads=[0,FP2*Lengths[1],0]
    static_loads=static_loads+Redundancy*[0]

elif Pnode >1:
    P_moment_arm = sum(Lengths[:Pnode])
    FP2_moment_arm = Lengths[0]
    FP2 =-Pload*P_moment_arm/FP2_moment_arm
    FP1 = -Pload - FP2      

    n=Pnode-1
    static_loads=[0]*n
    t=Redundancy-n+2
    P_static=[static_loads[x]+Pload*sum(Lengths[x+1:Pnode]) for x in range(n)]
    static_loads=[0]+P_static+t*[0]

elif Pnode <1:
    P_moment_arm = Lengths[0]
    FP2_moment_arm = Lengths[1]
    FP2 = Pload*P_moment_arm/FP2_moment_arm 
    FP1 = -Pload - FP2 

    static_loads=[0,FP2*FP2_moment_arm,0]
    static_loads=static_loads+Redundancy*[0]

# Each section can only be assigned one value for a bending moment,
# as the bending moment varies linearly across each section, an average bending moment can therefore be assigned
# to each section.

static_loads=[(static_loads[x]+static_loads[x+1])/2 for x in range(num_spans)]


# A unit load is now applied at each of the redunancies in turn and the subsequent bending moments at the beginning
# and end of each section are calculated. [Resultant of external forces equals zero]

unit_loads=range(Redundancy+1)

# As Python doesn't index 'Lengths[:-0]',  I had to reverse the whole list to do the summation I needed and reverse it back again.

LR = Lengths[:]
LR.reverse()

nodes=range(num_spans+1)
if Pnode>1:
    for u in unit_loads:
        unit_loads[u]=[sum(LR[u:x]) for x in nodes]
        unit_loads[u][-1]=0
        unit_loads[u].reverse()
        unit_loads[u]=[(unit_loads[u][x]+unit_loads[u][x+1])/2 for x in range(num_spans)]

    unit_loads.pop(num_spans-Pnode)


elif Pnode==1:
    for u in unit_loads:
        unit_loads[u]=[sum(LR[u:x]) for x in nodes]
        unit_loads[u][-2]=unit_loads[u][-2]-unit_loads[u][-1]/sum(Lengths[:2])*Lengths[1]
        unit_loads[u][-1]=0
        unit_loads[u].reverse()
        unit_loads[u]=[(unit_loads[u][x]+unit_loads[u][x+1])/2 for x in range(num_spans)]

    unit_loads.pop()


if Pnode<1:
    for u in unit_loads:
        unit_loads[u]=[sum(LR[u:x]) for x in nodes]
        unit_loads[u][-1]=0
        unit_loads[u][-2]=0
        unit_loads[u].reverse()
        unit_loads[u]=[(unit_loads[u][x]+unit_loads[u][x+1])/2 for x in range(num_spans)]

    unit_loads.pop()



A=array(unit_loads)

B=array(unit_loads)

# Creating all the products of unit loads to form the coefficients of the Virtual Work Equations

VWeqns=zeros((Redundancy**2,num_spans))

x=0

for coef1 in range(Redundancy):
    for coef2 in range(Redundancy):
        VWeqns[x]=A[coef1]*B[coef2]
        x+=1

VWeqns=VWeqns*Lengths/Evalues/Ivalues

# Sum up all the members

VWeqns=sum(VWeqns,1)

# Fold the VWeqns array into a square matrix

VWeqns.shape=(Redundancy,Redundancy)

C=mat(VWeqns)

# Creating all the constants of the Virtual Work Equations

D = -A*array(static_loads)*Lengths/Evalues/Ivalues
D = sum(D,1)


# Forces at the redundancies R1, R2,..

Reactions=solve(C,D).tolist()

# The remaining forces can be statically determined

Redundancy_arms=[sum(Lengths[:x]) for x in nodes]
Redundancy_arms.reverse()

moments=0
 
if Pnode>1:
    for m in range(Redundancy+1):
        if m == num_spans-Pnode:
            moments+=Pload*Redundancy_arms[m]
            Reactions.insert(m,Pload)
        else:
            moments+=Reactions[m]*Redundancy_arms[m]
    
    FP2 =-moments/FP2_moment_arm
    FP1 = - FP2 - sum(Reactions)

    Forces=Reactions
    Forces.append(FP2), Forces.append(FP1)
    
    Forces.reverse()

    print Forces
    print sum(Forces)

if Pnode==1:

    for m in range(Redundancy):
        moments+=Reactions[m]*Redundancy_arms[m]   

    moments+=Pload*P_moment_arm

    print moments
    
    FP2 =-moments/FP2_moment_arm
    FP1 = - FP2 - sum(Reactions)-Pload

    Forces=Reactions
    Forces.append(FP2),Forces.append(Pload), Forces.append(FP1)
    
    Forces.reverse()

    print Forces
    print sum(Forces)

elif Pnode <1:
    print Redundancy_arms
    for m in range(Redundancy):
        moments+=Reactions[m]*(Redundancy_arms[m]-Lengths[0])

    moments+=-Pload*P_moment_arm
    FP2 = -moments/FP2_moment_arm
    FP1 = -Pload - FP2 - sum(Reactions)

    Forces=Reactions
    Forces.append(FP2), Forces.append(FP1), Forces.append(Pload)
    Forces.reverse()

    print Forces
    print sum(Forces)

[/PHP]

---

