---
title: "undefined reference error, makefiles"
date: 2008-04-07
forum: Programming Talk
---

### Post by dodu3784 on 2008-04-07
Hello everybody,
I am seriously stuck another time on a problem involving a project I am doing using POO stuff. I'm working on ubuntu 7.10 and with the g++ compiler (moreover, i am using xemacs). I have first in my makefile used a vecteur.cc file (definition file) which includes vecteur.h and the testvecteur.cc and testoscillateur.cc to test all of this, and this works properly. The problem is now when I use in a third test program called exerciceP10 a Systeme class which contains an  Oscillateur_math that derives from an Oscillateur which is an abstract base-class, All these classes use the vecteur class somewhere.

Here is the output in the terminal:

mael@alcomitzli:~/cpp/project$ make
c++ -ansi -pedantic -Wall    -g                       -pg                      -O2                        -c -o exerciceP10.o exerciceP10.cc
Oscillateur_math.cc: In member function ‘virtual Vecteur Oscillateur_math::equation_evolution()’:
Oscillateur_math.cc:18: warning: comparison between signed and unsigned integer expressions
Systeme.h: In member function ‘Systeme& Systeme::operator=(const Systeme&)’:
Systeme.h:16: warning: no return statement in function returning non-void
Oscillateur_math.cc: In member function ‘virtual Oscillateur* Oscillateur_math::copie() const’:
Oscillateur_math.cc:58: warning: control reaches end of non-void function
c++ -pg                       exerciceP10.o   -o exerciceP10
exerciceP10.o: In function `main':
/home/mael/cpp/project/exerciceP10.cc:16: undefined reference to `Pendule::Pendule(double, double, double, double, double, double*, double*)'
/home/mael/cpp/project/exerciceP10.cc:18: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Oscillateur const&)'
/home/mael/cpp/project/exerciceP10.cc:20: undefined reference to `Systeme::Systeme()'
/home/mael/cpp/project/exerciceP10.cc:21: undefined reference to `Systeme::ajoute(Oscillateur const&)'
/home/mael/cpp/project/exerciceP10.cc:22: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Systeme const&)'
exerciceP10.o: In function `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Oscillateur_math const&)':
/home/mael/cpp/project/Oscillateur_math.cc:10: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Vecteur const&)'
/home/mael/cpp/project/Oscillateur_math.cc:11: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Vecteur const&)'
collect2: ld returned 1 exit status
make: *** [exerciceP10] Error 1

Thank very much for your help and your time.

dodu3784

---

### Post by dodu3784 on 2008-04-07
Sorry, I just have forgotten to post the makefile code, here it is:

CC  = c++
CXX = c++

# Partie commentée : choisissez les options que vous voulez avoir
#                    en décommentant la/les lignes correspondantes
#
 CXXFLAGS  = -ansi -pedantic -Wall   # pour les purs et durs
 CXXFLAGS += -g                      # pour debugger
 CXXFLAGS += -pg                     # pour profiler
 LDFLAGS  += -pg                     # pour profiler
 CXXFLAGS += -O2                     # pour optimiser la vitesse

all:: testvecteur testoscillateur exerciceP10

vecteur.o: vecteur.cc vecteur.h

testvecteur.o: testvecteur.cc vecteur.h

testvecteur: testvecteur.o vecteur.o

oscillateur.o: oscillateur.cc oscillateur.h

Oscillateur_math.o: Oscillateur_math.cc Oscillateur_math.h oscillateur.h vecteur.h

Pendule.o: Pendule.cc Pendule.h oscillateur.h vecteur.h

Systeme.o: Systeme.cc Systeme.h Oscillateur_math.h 

Systeme: Systeme.o Oscillateur_math.o

exerciceP10.o: exerciceP10.cc Pendule.h Systeme.h oscillateur.h vecteur.h Oscillateur_math.h

exercieP10: exercieP10.o Pendule.o Systeme.o oscillateur.o vecteur.o Oscillateur_math.o

testoscillateur.o: testoscillateur.cc oscillateur.h Pendule.h vecteur.h 

testoscillateur: testoscillateur.o oscillateur.o Pendule.o vecteur.o 

Thank you.

---

### Post by dodu3784 on 2008-04-08
Hello everybody,
I am seriously stuck another time on a problem involving a project I am doing using POO stuff. I'm working on ubuntu 7.10 and with the g++ compiler (moreover, i am using xemacs). I have first in my makefile used a vecteur.cc file (definition file) which includes vecteur.h and the testvecteur.cc and testoscillateur.cc to test all of this, and this works properly. The problem is now when I use in a third test program called exerciceP10 a Systeme class which contains an Oscillateur_math that derives from an Oscillateur which is an abstract base-class, All these classes use the vecteur class somewhere.

Here is the output in the terminal:

mael@alcomitzli:~/cpp/project$ make
c++ -ansi -pedantic -Wall -g -pg -O2 -c -o exerciceP10.o exerciceP10.cc
Oscillateur_math.cc: In member function ‘virtual Vecteur Oscillateur_math::equation_evolution()’:
Oscillateur_math.cc:18: warning: comparison between signed and unsigned integer expressions
Systeme.h: In member function ‘Systeme& Systeme:perator=(const Systeme&)’:
Systeme.h:16: warning: no return statement in function returning non-void
Oscillateur_math.cc: In member function ‘virtual Oscillateur* Oscillateur_math::copie() const’:
Oscillateur_math.cc:58: warning: control reaches end of non-void function
c++ -pg exerciceP10.o -o exerciceP10
exerciceP10.o: In function `main':
/home/mael/cpp/project/exerciceP10.cc:16: undefined reference to `Pendule::Pendule(double, double, double, double, double, double*, double*)'
/home/mael/cpp/project/exerciceP10.cc:18: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Oscillateur const&)'
/home/mael/cpp/project/exerciceP10.cc:20: undefined reference to `Systeme::Systeme()'
/home/mael/cpp/project/exerciceP10.cc:21: undefined reference to `Systeme::ajoute(Oscillateur const&)'
/home/mael/cpp/project/exerciceP10.cc:22: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Systeme const&)'
exerciceP10.o: In function `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Oscillateur_math const&)':
/home/mael/cpp/project/Oscillateur_math.cc:10: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Vecteur const&)'
/home/mael/cpp/project/Oscillateur_math.cc:11: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Vecteur const&)'
collect2: ld returned 1 exit status
make: *** [exerciceP10] Error 1

and the code of my Makefile:
CC = c++
CXX = c++

CXXFLAGS = -ansi -pedantic -Wall 
CXXFLAGS += -g 
CXXFLAGS += -pg 
LDFLAGS += -pg
CXXFLAGS += -O2 

all:: testvecteur testoscillateur exerciceP10

vecteur.o: vecteur.cc vecteur.h

testvecteur.o: testvecteur.cc vecteur.h

testvecteur: testvecteur.o vecteur.o

oscillateur.o: oscillateur.cc oscillateur.h

Oscillateur_math.o: Oscillateur_math.cc Oscillateur_math.h oscillateur.h vecteur.h

Pendule.o: Pendule.cc Pendule.h oscillateur.h vecteur.h

Systeme.o: Systeme.cc Systeme.h Oscillateur_math.h

Systeme: Systeme.o Oscillateur_math.o

exerciceP10.o: exerciceP10.cc Pendule.h Systeme.h oscillateur.h vecteur.h Oscillateur_math.h

exercieP10: exercieP10.o Pendule.o Systeme.o oscillateur.o vecteur.o Oscillateur_math.o

testoscillateur.o: testoscillateur.cc oscillateur.h Pendule.h vecteur.h

testoscillateur: testoscillateur.o oscillateur.o Pendule.o vecteur.o

Thank you very much to all.

---

### Post by bapoumba on 2008-04-08
Threads merged. Please use [code] tags around your terminal outputs, thanks.

---

### Post by WW on 2008-04-08
> **dodu3784 said:**
> Hello everybody,
I am seriously stuck another time on a problem involving a project I am doing using POO stuff. I'm working on ubuntu 7.10 and with the g++ compiler (moreover, i am using xemacs). I have first in my makefile used a vecteur.cc file (definition file) which includes vecteur.h and the testvecteur.cc and testoscillateur.cc to test all of this, and this works properly. The problem is now when I use in a third test program called exerciceP10 a Systeme class which contains an Oscillateur_math that derives from an Oscillateur which is an abstract base-class, All these classes use the vecteur class somewhere.

Here is the output in the terminal:

mael@alcomitzli:~/cpp/project$ make
c++ -ansi -pedantic -Wall -g -pg -O2 -c -o [color=red]exerciceP10.o[/color] exerciceP10.cc
Oscillateur_math.cc: In member function &#8216;virtual Vecteur Oscillateur_math::equation_evolution()&#8217;:
Oscillateur_math.cc:18: warning: comparison between signed and unsigned integer expressions
Systeme.h: In member function &#8216;Systeme& Systeme:perator=(const Systeme&)&#8217;:
Systeme.h:16: warning: no return statement in function returning non-void
Oscillateur_math.cc: In member function &#8216;virtual Oscillateur* Oscillateur_math::copie() const&#8217;:
Oscillateur_math.cc:58: warning: control reaches end of non-void function
c++ -pg [color=red]exerciceP10.o[/color] -o [color=red]exerciceP10[/color]
exerciceP10.o: In function `main':
/home/mael/cpp/project/exerciceP10.cc:16: undefined reference to `Pendule::Pendule(double, double, double, double, double, double*, double*)'
/home/mael/cpp/project/exerciceP10.cc:18: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Oscillateur const&)'
/home/mael/cpp/project/exerciceP10.cc:20: undefined reference to `Systeme::Systeme()'
/home/mael/cpp/project/exerciceP10.cc:21: undefined reference to `Systeme::ajoute(Oscillateur const&)'
/home/mael/cpp/project/exerciceP10.cc:22: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Systeme const&)'
exerciceP10.o: In function `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Oscillateur_math const&)':
/home/mael/cpp/project/Oscillateur_math.cc:10: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Vecteur const&)'
/home/mael/cpp/project/Oscillateur_math.cc:11: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Vecteur const&)'
collect2: ld returned 1 exit status
make: *** [exerciceP10] Error 1

and the code of my Makefile:
CC = c++
CXX = c++

CXXFLAGS = -ansi -pedantic -Wall 
CXXFLAGS += -g 
CXXFLAGS += -pg 
LDFLAGS += -pg
CXXFLAGS += -O2 

all:: testvecteur testoscillateur exerciceP10

vecteur.o: vecteur.cc vecteur.h

testvecteur.o: testvecteur.cc vecteur.h

testvecteur: testvecteur.o vecteur.o

oscillateur.o: oscillateur.cc oscillateur.h

Oscillateur_math.o: Oscillateur_math.cc Oscillateur_math.h oscillateur.h vecteur.h

Pendule.o: Pendule.cc Pendule.h oscillateur.h vecteur.h

Systeme.o: Systeme.cc Systeme.h Oscillateur_math.h

Systeme: Systeme.o Oscillateur_math.o

[color=red]exerciceP10.o[/color]: exerciceP10.cc Pendule.h Systeme.h oscillateur.h vecteur.h Oscillateur_math.h

[color=red]exercieP10[/color]: [color=red]exercieP10.o[/color] Pendule.o Systeme.o oscillateur.o vecteur.o Oscillateur_math.o

testoscillateur.o: testoscillateur.cc oscillateur.h Pendule.h vecteur.h

testoscillateur: testoscillateur.o oscillateur.o Pendule.o vecteur.o

Thank you very much to all.

Look carefully at the words marked in red above.  In the future, be sure to look at the commands that **make** runs.  You can see in the output above that **make** is running **c++ -pg exerciceP10.o -o exerciceP10**; notice that the command does not have all the object (*.o) files that you expected.  This should tell you that you have a mistake in your Makefile.

---

