---
title: "Compiler issue with Ubuntu 16.04"
date: 2016-11-29
forum: Packaging and Compiling Programs
---

### Post by miriam66 on 2016-11-29
My code compiles fine with Ubuntu 10.04 but I get 'undefined reference' errors when I compile the code with Ubuntu 16.04. When I run the Makefile I get the following output


bds-admin@BDS-PRECISION:~/Miriam/MyCODE$ make
g++ -g   -c -o GEListGenome.o GEListGenome.cpp
g++ -g   -c -o initfunc.o initfunc.cpp
g++ -g   -c -o main.o main.cpp
g++ -g   -c -o MySelector.o MySelector.cpp
g++ -g   -c -o MyGA.o MyGA.cpp
g++ -g   -c -o Validation.o Validation.cpp
g++ -g   -c -o Function_Codon_List.o Function_Codon_List.cpp
g++ -g   -c -o Retrieve_CodonList.o Retrieve_CodonList.cpp
g++ -g   -c -o Test_Code.o Test_Code.cpp
g++ -g   -c -o Miriam_6.o Miriam_6.cpp
Miriam_6.cpp: In function ‘long int Print_to_File(std::__cxx11::string)’:
Miriam_6.cpp:7840:28: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long int’ [-Wformat=]
    fprintf(file,"%d\n",rnum);
                            ^
g++ -g   -c -o Pareto_Fitness_Eval_Two.o Pareto_Fitness_Eval_Two.cpp
Pareto_Fitness_Eval_Two.cpp: In function ‘void print_NonDominated_Population_2_File(const GAPopulation&)’:
Pareto_Fitness_Eval_Two.cpp:5237:32: warning: format ‘%f’ expects argument of type ‘double’, but argument 3 has type ‘const char*’ [-Wformat=]
    fprintf(bfile,"%.2f\n","0.0");
                                ^
Pareto_Fitness_Eval_Two.cpp:5239:32: warning: format ‘%f’ expects argument of type ‘double’, but argument 3 has type ‘const char*’ [-Wformat=]
    fprintf(cfile,"%.2f\n","0.0");
                                ^
Pareto_Fitness_Eval_Two.cpp:5241:32: warning: format ‘%f’ expects argument of type ‘double’, but argument 3 has type ‘const char*’ [-Wformat=]
    fprintf(dfile,"%.2f\n","0.0");
                                ^
g++ -g -I/usr/local/include -I../include -o testPareto GEListGenome.o initfunc.o main.o MySelector.o MyGA.o Validation.o Function_Codon_List.o Retrieve_CodonList.o Test_Code.o Miriam_6.o Pareto_Fitness_Eval_Two.o   -L/usr/local/lib -L../lib -lga -lGE
initfunc.o: In function `My_SI_Initializer(GAPopulation&)':
/home/bds-admin/Miriam/MyCODE/initfunc.cpp:335: undefined reference to `Genotype::Genotype(int const*, unsigned int, bool, long double)'
main.o: In function `main':
/home/bds-admin/Miriam/MyCODE/main.cpp:523: undefined reference to `GEListGenome::MyOnePointCrossover(GAGenome const&, GAGenome const&, GAGenome*, GAGenome*)'
/home/bds-admin/Miriam/MyCODE/main.cpp:587: undefined reference to `Mapper::setGenotypeMaxCodonValue(int)'
/home/bds-admin/Miriam/MyCODE/main.cpp:589: undefined reference to `Initialiser::setPopSize(unsigned int)'
main.o: In function `__static_initialization_and_destruction_0(int, int)':
/home/bds-admin/Miriam/MyCODE/main.cpp:255: undefined reference to `Genotype::Genotype(int const*, unsigned int, bool, long double)'
Miriam_6.o: In function `Miriam::Miriam()':
/home/bds-admin/Miriam/MyCODE/Miriam_6.cpp:97: undefined reference to `Initialiser::Initialiser(unsigned int)'
Miriam_6.o: In function `Miriam::~Miriam()':
/home/bds-admin/Miriam/MyCODE/Miriam_6.cpp:100: undefined reference to `Initialiser::~Initialiser()'
/home/bds-admin/Miriam/MyCODE/Miriam_6.cpp:100: undefined reference to `Initialiser::~Initialiser()'
Miriam_6.o:(.rodata._ZTI6Miriam[_ZTI6Miriam]+0x28): undefined reference to `typeinfo for Initialiser'
Pareto_Fitness_Eval_Two.o: In function `print_individual(GAGenome const&)':
/home/bds-admin/Miriam/MyCODE/Pareto_Fitness_Eval_Two.cpp:1967: undefined reference to `Genotype::getWraps() const'
collect2: error: ld returned 1 exit status
Makefile:34: recipe for target 'testPareto' failed
make: *** [testPareto] Error 1


Any help/advice would be greatly appreciated.
Thanks,
Miriam66

---

### Post by steeldriver on 2016-11-29
Hello and welcome to the forums

Link order matters - see for example [Why does the order of '-l' option in gcc matter?]("http://stackoverflow.com/questions/11893996/why-does-the-order-of-l-option-in-gcc-matter")[URL="http://stackoverflow.com/questions/11893996/why-does-the-order-of-l-option-in-gcc-matter"]
[/URL]
Where (for example) is Genotype::Genotype defined? My guess is it's in GEListGenome.o and if so, the link order needs to be modified to place GEListGenome.o to the right of initfunc.o on the link line

Likewise for the relationship between initfunc.o and main.o

You should also fix the compiler warnings IMHO e.g.

```

fprintf(cfile,"%.2f\n","0.0");

```

to

```

fprintf(cfile,"%.2f\n",0.0);

```
[URL="http://stackoverflow.com/questions/11893996/why-does-the-order-of-l-option-in-gcc-matter"]
[/URL]

---

### Post by miriam66 on 2016-11-30
Hi, 
I took your advice and fixed the compiler warnings. Thanks for that.
Regarding the other issue, when you say linker I'm assuming that in my makefile this is referring to 'lGE' and 'lga' . I read the link that you included above and I'm assuming that by having 'lGE' and 'lga' at the end is correct. I'm not clear on what you mean by putting GEListGenome.o to the right of initfunc.o in the link line.

Regards,
Miriam

---

