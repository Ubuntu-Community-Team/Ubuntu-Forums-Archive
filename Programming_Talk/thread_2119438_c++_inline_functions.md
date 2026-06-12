---
title: "c++ inline functions"
date: 2013-02-23
forum: Programming Talk
---

### Post by Dirich on 2013-02-23
I had a perfectly working program, but I wanted to divide one of my source file in 3 because it was too messy. So I divided my OLD.cpp in:
saReadConfigure.cpp
saReadInput.cpp
saReadUtility.cpp
Of course every file has its header.
In the first two files I put only the functions dealing with Configure and Input respectively.
In the third, saReadUtility, I put all the functions that were used by functions from BOTH the other files.
They are small utility functions, all defined as INLINE.
Obviously, I included saReadUtility.h in all three .cpp files.

Now the crux of the problem: the program does not compile anymore.
If I put all the code from saReadUtility.cpp in BOTH the other files, then it compiles again. Thus it's just a matter concerning the function and their being inline but declared and defined in a source different from the one using them (since I know this mess does not happen when I do stuff like I did here but the functions are not inline).

An example of what my compiler throws at me when I compile:
```
g++ -g -Wall -o SystemAnalysis SystemAnalysis.cpp saException.cpp saGenerateConfigure.cpp saGenerateInput.cpp saGenerateREADME.cpp saReadConfigure.cpp saReadInput.cpp saReadUtility.cpp -lm -lmpfr -lgmp -lstdc++
saReadUtility.h:46:13: warning: inline function &#8216;void Skip_Spaces(std::ifstream&, char&, bool&)&#8217; used but never defined [enabled by default]
saReadUtility.h:12:13: warning: inline function &#8216;void GOTO_Next_Input_Data(std::ifstream&, char*, char)&#8217; used but never defined [enabled by default]
saReadUtility.h:24:13: warning: inline function &#8216;bool Skip_Lines(std::ifstream&, char*)&#8217; used but never defined [enabled by default]
saReadUtility.h:12:13: warning: inline function &#8216;void GOTO_Next_Input_Data(std::ifstream&, char*, char)&#8217; used but never defined [enabled by default]
saReadUtility.h:24:13: warning: inline function &#8216;bool Skip_Lines(std::ifstream&, char*)&#8217; used but never defined [enabled by default]
saReadUtility.h:37:13: warning: inline function &#8216;void Skip_Lines(std::ifstream&, char*, char, char, int)&#8217; used but never defined [enabled by default]
/tmp/ccptM4D7.o: In function `Read_Configure_Software(SoftwareData&)':
PATH/saReadConfigure.cpp:100: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadConfigure.cpp:123: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadConfigure.cpp:135: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadConfigure.cpp:147: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadConfigure.cpp:159: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
/tmp/ccptM4D7.o:PATH/saReadConfigure.cpp:171: more undefined references to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)' follow
/tmp/ccptM4D7.o: In function `Read_Configure_Simulation(SimulationData&, short const&, short const&)':
PATH/saReadConfigure.cpp:373: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadConfigure.cpp:388: undefined reference to `Skip_Spaces(std::basic_ifstream<char, std::char_traits<char> >&, char&, bool&)'
PATH/saReadConfigure.cpp:407: undefined reference to `Skip_Spaces(std::basic_ifstream<char, std::char_traits<char> >&, char&, bool&)'
PATH/saReadConfigure.cpp:436: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadConfigure.cpp:463: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadConfigure.cpp:464: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadConfigure.cpp:526: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
/tmp/ccptM4D7.o: In function `Read_Branches(short*, std::basic_ifstream<char, std::char_traits<char> >&, char&, bool&)':
PATH/saReadConfigure.cpp:29: undefined reference to `Skip_Spaces(std::basic_ifstream<char, std::char_traits<char> >&, char&, bool&)'
PATH/saReadConfigure.cpp:34: undefined reference to `Skip_Spaces(std::basic_ifstream<char, std::char_traits<char> >&, char&, bool&)'
PATH/saReadConfigure.cpp:39: undefined reference to `Skip_Spaces(std::basic_ifstream<char, std::char_traits<char> >&, char&, bool&)'
PATH/saReadConfigure.cpp:44: undefined reference to `Skip_Spaces(std::basic_ifstream<char, std::char_traits<char> >&, char&, bool&)'
/tmp/ccdiPnmB.o: In function `Read_Input(short&)':
PATH/saReadInput.cpp:269: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
/tmp/ccdiPnmB.o: In function `Read_Input_Hamiltonian(HamiltonianData&)':
PATH/saReadInput.cpp:294: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadInput.cpp:306: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadInput.cpp:325: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadInput.cpp:337: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
/tmp/ccdiPnmB.o:PATH/saReadInput.cpp:354: more undefined references to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)' follow
/tmp/ccdiPnmB.o: In function `Read_Input_Hamiltonian(HamiltonianData&)':
PATH/saReadInput.cpp:403: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:440: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*, char, char, int)'
PATH/saReadInput.cpp:444: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadInput.cpp:445: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:476: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*, char, char, int)'
/tmp/ccdiPnmB.o: In function `int Input_List_Acquisition<CellPassivation>(CellPassivation*, std::basic_ifstream<char, std::char_traits<char> >&, char, HamiltonianData&)':
PATH/saReadInput.cpp:130: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadInput.cpp:131: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:155: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:174: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:189: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*, char, char, int)'
/tmp/ccdiPnmB.o: In function `int Input_List_Acquisition<DevicePassivation>(DevicePassivation*, std::basic_ifstream<char, std::char_traits<char> >&, char, HamiltonianData&)':
PATH/saReadInput.cpp:130: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadInput.cpp:131: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:155: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:174: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:189: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*, char, char, int)'
/tmp/ccdiPnmB.o: In function `int Input_List_Acquisition<CellAdatom>(CellAdatom*, std::basic_ifstream<char, std::char_traits<char> >&, char, HamiltonianData&)':
PATH/saReadInput.cpp:130: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadInput.cpp:131: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:155: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:174: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:189: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*, char, char, int)'
/tmp/ccdiPnmB.o: In function `int Input_List_Acquisition<DeviceAdatom>(DeviceAdatom*, std::basic_ifstream<char, std::char_traits<char> >&, char, HamiltonianData&)':
PATH/saReadInput.cpp:130: undefined reference to `GOTO_Next_Input_Data(std::basic_ifstream<char, std::char_traits<char> >&, char*, char)'
PATH/saReadInput.cpp:131: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:155: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:174: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*)'
PATH/saReadInput.cpp:189: undefined reference to `Skip_Lines(std::basic_ifstream<char, std::char_traits<char> >&, char*, char, char, int)'
collect2: ld returned 1 exit status
make: *** [SystemAnalysis] Error 1

```So... what's happening? What is wrong with using inline functions defined and declared in another source+header file?

---

### Post by fdrake on 2013-02-23
cahnge the filenames of the 2 file (containing the functions) from function.cpp to function.hpp.

make sure that in the main programe the header is: "#include<function.hpp>"

---

### Post by gnusci on 2013-02-23
Headers should aware that something was already included!

#ifndef _SA_READ_CONFIGURE_H_
#define _SA_READ_CONFIGURE_H_

// You code here

#endif

---

### Post by Dirich on 2013-02-23
> **fdrake said:**
> cahnge the filenames of the 2 file (containing the functions) from function.cpp to function.hpp.

make sure that in the main programe the header is: "#include<function.hpp>"
To delete the old .h and rename the .cpp to .hpp works. Thank you.

EDIT:
Ok, I got it. Due to how the inline functions work, it has to be defined in a header or in every .cpp that uses it. For everybody with the same problem and interested in the reason why.

---

### Post by Dirich on 2013-02-23
> **gnusci said:**
> Headers should aware that something was already included!

#ifndef _SA_READ_CONFIGURE_H_
#define _SA_READ_CONFIGURE_H_

// You code here

#endif

Yep, I do that in every .h
Thanks anyway

---

### Post by fdrake on 2013-02-24
> **Dirich said:**
> To delete the old .h and rename the .cpp to .hpp works. Thank you.

EDIT:
Ok, I got it. Due to how the inline functions work, it has to be defined in a header or in every .cpp that uses it. For everybody with the same problem and interested in the reason why.

glad it worked.

---

