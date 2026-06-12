---
title: "namespace, nested-name-specifier"
date: 2008-04-12
forum: Programming Talk
---

### Post by dodu3784 on 2008-04-12
Hello everybody,
I have the following errors when I run my makefile:

```

Systeme.h:7: error: expected nested-name-specifier before ‘namespace’
Systeme.h:7: error: expected unqualified-id before ‘namespace’
Systeme.h:7: error: expected `;' before ‘namespace’
Systeme.h:7: error: expected unqualified-id before ‘namespace’
Systeme.h:12: error: field ‘gen_syst’ has incomplete type
Systeme.h:30: error: ‘std::ostream& Oscillateur_math::operator<<(std::ostream&, const Oscillateur_math::Systeme&)’ must take exactly one argument
Pendule.h:7: error: expected nested-name-specifier before ‘namespace’
Pendule.h:7: error: expected unqualified-id before ‘namespace’
Pendule.h:7: error: expected `;' before ‘namespace’
Pendule.h:7: error: expected unqualified-id before ‘namespace’
Ressort.h:7: error: expected nested-name-specifier before ‘namespace’
Ressort.h:7: error: expected unqualified-id before ‘namespace’
Ressort.h:7: error: expected `;' before ‘namespace’
Ressort.h:7: error: expected unqualified-id before ‘namespace’
exerciceP10.cc:10: error: expected nested-name-specifier before ‘namespace’
exerciceP10.cc:10: error: expected unqualified-id before ‘namespace’
exerciceP10.cc:10: error: expected `;' before ‘namespace’
exerciceP10.cc:10: error: expected unqualified-id before ‘namespace’
exerciceP10.cc:54: error: expected `}' at end of input
Systeme.h: In member function ‘Oscillateur_math::Systeme& Oscillateur_math::Systeme::operator=(const Oscillateur_math::Systeme&)’:
Systeme.h:16: warning: no return statement in function returning non-void
Systeme.h: In constructor ‘Oscillateur_math::Systeme::Systeme()’:
Systeme.h:20: error: ‘gen_syst’ was not declared in this scope
Systeme.h: In member function ‘Oscillateur_math Oscillateur_math::Systeme::get_gen_syst() const’:
Systeme.h:22: error: ‘gen_syst’ was not declared in this scope
exerciceP10.cc: At global scope:
exerciceP10.cc:54: error: expected unqualified-id at end of input
make: *** [exerciceP10.o] Error 1

```
Do you know where is the problem ?
Thank very much for your answers

dodu3784

---

### Post by WW on 2008-04-12
It would help if you included the file Systeme.h, and perhaps the Makefile.

But since you didn't, here is some wild speculation.  Is there a missing semicolon or closing bracket at the end of the statement preceding the namespace that begins on line 7 of Systeme.h?

---

### Post by dodu3784 on 2008-04-12
Here is the Makefile

```

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

Ressort.o: Ressort.cc Ressort.h oscillateur.h vecteur.h

Systeme.o: Systeme.cc Systeme.h Oscillateur_math.h oscillateur.h

Systeme: Systeme.o Oscillateur_math.o oscillateur.o

exerciceP10.o: exerciceP10.cc  Systeme.h oscillateur.h vecteur.h Oscillateur_math.h Pendule.h Ressort.h

exerciceP10: exerciceP10.o Systeme.o oscillateur.o vecteur.o Oscillateur_math.o Pendule.o Ressort.o

testoscillateur.o: testoscillateur.cc oscillateur.h Pendule.h Ressort.h vecteur.h 

testoscillateur: testoscillateur.o oscillateur.o Pendule.o Ressort.o vecteur.o 

```

and here is Systeme.h
```

#ifndef SYSTEME_H
#define SYSTEME_H

#include<iostream>
#include"oscillateur.h"
#include"Oscillateur_math.h"//attention Oscillateur_math.cc
using namespace std;

class Systeme : public Dessinable
{
private:
	Oscillateur_math gen_syst;
	//2
	Systeme(const Systeme& S1){}
	//3
	Systeme& operator=(const Systeme& S1){}//question P7.2, protection des données???
	
public:
	//1
	Systeme(){gen_syst.supprime();}
	
	Oscillateur_math get_gen_syst() const {return gen_syst;}
	
	void ajoute(const Oscillateur&);//c'est ici que deux aspects de gestion de l'interface peuvent apparaître 
	void supprime();
	void dessine(){}
	
};

ostream& operator<<(ostream& out, const Systeme& S1);

#endif

```

And thank you for the help you have given me so far WW

---

### Post by WW on 2008-04-12
OK, now let's see Oscillateur_math.h.

---

### Post by dodu3784 on 2008-04-12
Here it is
```

#ifndef OSCILLATEUR_MATH_H
#define OSCILLATEUR_MATH_H

#include<iostream>
#include<vector>
#include"vecteur.h"
#include"oscillateur.h"
//#include"oscillateur.cc"
using namespace std;

typedef vector< Oscillateur* > os_stack;

//P12

class Oscillateur_math : public Oscillateur
{
private:
	os_stack stack;

public:
	void ajoute(const Oscillateur& Oscillateur1);// pour etre utilisee dans Systeme
	
	void supprime();
	
	Vecteur equation_evolution();
	
	os_stack get_stack(){return stack;}//possibilite de bug ici!!!!!!!!!!!!!!!!
	
	Oscillateur_math(){stack.clear();}// On doit de ce fait implementer un Oscillateur::Oscillateur() dans oscillateur.h ou .cc
	
	Oscillateur* copie() const{{return new Oscillateur_math(*this);}
	
	void to_delete();
};
	
/*
ostream& operator<<(ostream& out, const Oscillateur_math& omath1);
*/
#endif	


```

---

### Post by WW on 2008-04-12
Notice the extra { in this line
[php]
	Oscillateur* copie() const{{return new Oscillateur_math(*this);}
[/php]
near the end of Oscillateur_math.h.

---

### Post by dodu3784 on 2008-04-12
I now get the following:
```

exerciceP10.o: In function `main':
/home/mael/cpp/project/exerciceP10.cc:20: undefined reference to `Vecteur::Vecteur(double*, int)'
/home/mael/cpp/project/exerciceP10.cc:21: undefined reference to `Vecteur::Vecteur(double*, int)'
/home/mael/cpp/project/exerciceP10.cc:23: undefined reference to `Pendule::Pendule(double, double, double, Vecteur, Vecteur, Vecteur, Vecteur)'
/home/mael/cpp/project/exerciceP10.cc:31: undefined reference to `Vecteur::Vecteur(double*, int)'
/home/mael/cpp/project/exerciceP10.cc:32: undefined reference to `Vecteur::Vecteur(double*, int)'
/home/mael/cpp/project/exerciceP10.cc:34: undefined reference to `Ressort::Ressort(double, double, double, double, Vecteur, Vecteur, Vecteur, Vecteur)'
exerciceP10.o: In function `~Ressort':
/home/mael/cpp/project/Ressort.h:12: undefined reference to `vtable for Ressort'
exerciceP10.o: In function `~Pendule':
/home/mael/cpp/project/Pendule.h:12: undefined reference to `vtable for Pendule'
Systeme.o: In function `Oscillateur_math':
/home/mael/cpp/project/Oscillateur_math.h:16: undefined reference to `vtable for Oscillateur_math'
Systeme.o: In function `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Systeme const&)':
/home/mael/cpp/project/Systeme.cc:18: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Oscillateur const&)'
Systeme.o: In function `Oscillateur_math':
/home/mael/cpp/project/Oscillateur_math.h:16: undefined reference to `vtable for Oscillateur_math'
/home/mael/cpp/project/Oscillateur_math.h:16: undefined reference to `vtable for Oscillateur_math'
/home/mael/cpp/project/Oscillateur_math.h:16: undefined reference to `vtable for Oscillateur_math'
Systeme.o: In function `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Systeme const&)':
/home/mael/cpp/project/Systeme.cc:21: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Vecteur const&)'
Systeme.o: In function `Oscillateur_math':
/home/mael/cpp/project/Oscillateur_math.h:16: undefined reference to `vtable for Oscillateur_math'
Systeme.o: In function `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Systeme const&)':
/home/mael/cpp/project/Systeme.cc:22: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, Vecteur const&)'
Systeme.o: In function `Systeme::supprime()':
/home/mael/cpp/project/Systeme.cc:34: undefined reference to `Oscillateur_math::supprime()'
Systeme.o: In function `Systeme::ajoute(Oscillateur const&)':
/home/mael/cpp/project/Systeme.cc:28: undefined reference to `Oscillateur_math::ajoute(Oscillateur const&)'
Systeme.o: In function `~Oscillateur_math':
/home/mael/cpp/project/Oscillateur_math.h:16: undefined reference to `vtable for Oscillateur_math'
collect2: ld returned 1 exit status
make: *** [exerciceP10] Error 1

```
Which I thought I had fixed

---

