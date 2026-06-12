---
title: "C++ undefined reference errors"
date: 2008-04-06
forum: Programming Talk
---

### Post by dodu3784 on 2008-04-06
Hello everybody,
I am seriously stuck on a problem involving a project I am doing using POO stuff. I'm working on ubuntu 7.10 and with the g++ compiler (moreover, i am using xemacs). I have first in my makefile used a vecteur.cc file (definition file) which includes vecteur.h and the testvecteur.cc to test all of this, and this works properly. The problem is now when I use a Pendule, which derives from an abstract base class called Oscillateur located in oscillateur.h and oscillateur.cc, in a test program called testoscillateur. All these classes use the vecteur class somewhere.

i have the following makefile
(

CC  = c++
CXX = c++

 CXXFLAGS  = -ansi -pedantic -Wall   
 CXXFLAGS += -g                      
 CXXFLAGS += -pg                     
 LDFLAGS  += -pg                     
 CXXFLAGS += -O2 
                    
all:: testvecteur testoscillateur #exerciceP10

vecteur.o: vecteur.cc vecteur.h

testvecteur.o: testvecteur.cc vecteur.h

testvecteur: testvecteur.o vecteur.o

oscillateur.o: oscillateur.cc oscillateur.h

Pendule.o: Pendule.cc Pendule.h oscillateur.h vecteur.h

testoscillateur.o: testoscillateur.cc oscillateur.h Pendule.h

testoscillateur: testoscillateur.o oscillateur.o Pendule.o

and I get in the terminal 

mael@alcomitzli:~/cpp/project$ make
c++ -ansi -pedantic -Wall    -g                       -pg                      -O2                        -c -o testoscillateur.o testoscillateur.cc
c++ -ansi -pedantic -Wall    -g                       -pg                      -O2                        -c -o oscillateur.o oscillateur.cc
c++ -ansi -pedantic -Wall    -g                       -pg                      -O2                        -c -o Pendule.o Pendule.cc
c++ -pg                       testoscillateur.o oscillateur.o Pendule.o   -o testoscillateur
oscillateur.o: In function `Oscillateur::modify_Oscillateur(Vecteur, Vecteur)':
/home/mael/cpp/project/oscillateur.cc:26: undefined reference to `Vecteur::operator=(Vecteur const&)'
oscillateur.o: In function `Oscillateur::affiche(std::basic_ostream<char, std::char_traits<char> >&)':
/home/mael/cpp/project/oscillateur.cc:10: undefined reference to `Vecteur::affiche(std::basic_ostream<char, std::char_traits<char> >&)'
oscillateur.o: In function `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Oscillateur const&)':
/home/mael/cpp/project/oscillateur.cc:44: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Vecteur const&)'
/home/mael/cpp/project/oscillateur.cc:45: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Vecteur const&)'
oscillateur.o: In function `Oscillateur::modify_Oscillateur(Vecteur, Vecteur)':
/home/mael/cpp/project/oscillateur.cc:27: undefined reference to `Vecteur::operator=(Vecteur const&)'
oscillateur.o: In function `Oscillateur::affiche(std::basic_ostream<char, std::char_traits<char> >&)':
/home/mael/cpp/project/oscillateur.cc:11: undefined reference to `Vecteur::affiche(std::basic_ostream<char, std::char_traits<char> >&)'
Pendule.o: In function `Pendule':
/home/mael/cpp/project/Pendule.cc:12: undefined reference to `Vecteur::Vecteur(double*, int)'
/home/mael/cpp/project/Pendule.cc:12: undefined reference to `Vecteur::operator=(Vecteur const&)'
/home/mael/cpp/project/Pendule.cc:13: undefined reference to `Vecteur::Vecteur(double*, int)'
/home/mael/cpp/project/Pendule.cc:13: undefined reference to `Vecteur::operator=(Vecteur const&)'
/home/mael/cpp/project/Pendule.cc:12: undefined reference to `Vecteur::Vecteur(double*, int)'
/home/mael/cpp/project/Pendule.cc:12: undefined reference to `Vecteur::operator=(Vecteur const&)'
/home/mael/cpp/project/Pendule.cc:13: undefined reference to `Vecteur::Vecteur(double*, int)'
/home/mael/cpp/project/Pendule.cc:13: undefined reference to `Vecteur::operator=(Vecteur const&)'
Pendule.o: In function `Pendule::equation_evolution()':
/home/mael/cpp/project/Pendule.cc:24: undefined reference to `Vecteur::operator*(Vecteur const&) const'
/home/mael/cpp/project/Pendule.cc:28: undefined reference to `Vecteur::Vecteur(double*, int)'
collect2: ld returned 1 exit status
make: *** [testoscillateur] Error 1

The names are those of functions and overloaded operators.
Thank very much for your help.

dodu3784

---

### Post by WW on 2008-04-06
You haven't told make that testoscillateur depends on vecteur.o.  Change this like
> 
testoscillateur: testoscillateur.o oscillateur.o Pendule.o

to
> 
testoscillateur: testoscillateur.o oscillateur.o Pendule.o vecteur.o


---

### Post by dodu3784 on 2008-04-06
Fantastic, thank you very much WW for your prompt reply and your help.
dodu3784

---

