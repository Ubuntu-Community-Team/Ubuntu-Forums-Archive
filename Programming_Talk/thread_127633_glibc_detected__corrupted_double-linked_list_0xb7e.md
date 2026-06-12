---
title: "*** glibc detected *** corrupted double-linked list: 0xb7e15938 ***"
date: 2006-02-09
forum: Programming Talk
---

### Post by swong1 on 2006-02-09
Hi all. I have a C++ program that I wrote. The code compiles without any error or warning message. But when I execute it, I get the 

*** glibc detected *** corrupted double-linked list: 0xb7e15938 ***
Aborted

message. This only happens when I chose certain input parameters. It works flawlessly under other conditions. Can someone please help me make sense of this error message? I want to know which part of my program is causing trouble.

---

### Post by rock freak on 2006-02-09
some source code may help out in finding out whats wrong!

look forward to helping you

---

### Post by swong1 on 2006-02-09
Hi rock freak, thanks for your reply. I'll try to make it as plain as possible, I don't want to complicate things unnecessarily.

Okay, here's my main program:
```

#include <iostream>
#include "algo1.h"
#include "algo1p5.h"
#include "algo2a.h"
#include "algo2b.h"
#include "algo3.h"
using namespace std;

int main(int argc, char* argv[]) {

  system("date");  

  if(argc != 4) {
    cout << "Please enter the version of algorithm to use: 1, 1p5, 2a, 2b, 3\n"
	 << "followed by the radius of droplet: 3, 4, 5, 6, 7, 8, 12, 16\n"
	 << "followed by the temperature: e.g. 3.5\n";
    exit(EXIT_FAILURE);
  }

  string algo = argv[1];
  int radius = atoi(argv[2]);
  double temperature = atof(argv[3]);

  if(algo == "1") {
    cout << "Algorithm 1: original Metropolis algorithm.\n";
    algo1 simulation;
    simulation.minimize(argv[1], radius, temperature);
  }
  else if(algo == "2a") {
    cout << "Algorithm 2a: randomly select a neighbour's spin\n"
	 << "with weighted probability.\n"
	 << "4-cases modified Metropolis acceptance ratios.\n";
    algo2a simulation;
    simulation.minimize(argv[1], radius, temperature);
  }
  else if(algo == "1p5") {
    cout << "Algorithm 1.5: randomly select a neighbour's spin\n"
	 << "with equal probability.\n";
    algo1p5 simulation;
    simulation.minimize(argv[1], radius, temperature);
  }
  else if(algo == "2b") {
    cout << "Algorithm 2b: same as 2a but without the modifying\n"
	 << "factor in the acceptance probability.\n";
    algo2b simulation;
    simulation.minimize(argv[1], radius, temperature);
  }
  else if(algo == "3") {
    cout << "Algorithm 3: randomly select a pixel and its neighbour\n"
	 << "with Metropolis acceptance probability.\n";
    algo3 simulation;
    simulation.minimize(argv[1], radius, temperature);
  }
  else {
    cout << "Please enter a valid version of algorithm: 1, 1p5 or 2a\n"
	 << "and the droplet's radius: 3, 4, 5, 6, 7, 8, 12, 16\n";
    exit(EXIT_FAILURE);
  }
** (error message seems to occur at this point)**
  system("date");

}

```
It's pretty standard fare. According to the run time input ('1', '1p5', '2a', '2b', '3'), the program will run slightly different version of the code. The funny thing is, I don't get the error message if I choose '1', but I get the error message if I choose all the other versions. I get the same error message even if I switch the sequence of the "if" statements.

"algo1" is the parent class while all others are derived from "algo1". 

An example code for say, "algo1p5" looks like:
```

#ifndef ALGO1P5_H
#define ALGO1P5_H
#include "algo1.h"


// algo1p5 class is derived from algo1 class
class algo1p5 : public algo1 {

 protected:
  virtual void create_directories();
  virtual void flip_spin_algorithm(const double, const float);

 public:  
  algo1p5(int x = Ddim) : algo1(x) { }
  algo1p5(int x, int y) : algo1(x, y) { }
  ~algo1p5() { for(int i=0; i<=NDROP; i++) delete droplet[i]; }

};

void algo1p5::create_directories() {

  string cd_data = "cd data/algo1p5";
  string cd_movies = "cd movies/algo1p5";
  string mkdir_data = "mkdir data/algo1p5";
  string mkdir_movies = "mkdir movies/algo1p5";

  if(system(cd_data.c_str())) {
    cout << "Creating data directory.\n";
    system(mkdir_data.c_str());
  }
  if(system(cd_movies.c_str())) {
    cout << "Creating movies directory.\n";
    system(mkdir_movies.c_str());
  }
}

void algo1p5::flip_spin_algorithm(const double kT, const float xy) {

  int spin1, t_spin, spin;
  int spin_count[NDROP + 1];
  int coord1, coord2, nn, dET;
  double maxdET = 50*Jij;
  double dEJ, dEA;
  double prob[int(maxdET)];

  // This can only be done if Jij and Ja are integers
  for(dET=0; dET<maxdET; dET++)
    prob[dET] = exp(-dET*Jij/kT);

  for(int attempt=0; attempt<xy; attempt++) {

    dEJ = dEA = 0.0; 
    for(spin=0; spin<=NDROP; spin++)
      spin_count[spin] = 0;
    
    coord1 = MOD(ran3l(&ran_seed1), XY);
    spin1 = lattice[coord1]->get_spin();
  
    // Count the number of neighbours with 0 and non-0 spins
    for(nn=1; nn<=NN4; nn++){
      coord2 = MOD(coord1 + disp[nn], XY);
      spin_count[lattice[coord2]->get_spin()]++;
    }
     
    // All neighbours have the same spin as the candidate spin
    if(spin_count[spin1] == NN4)
      continue;

    else if(ran3f(&ran_seed3) > 0.5) {   // equal probability
      t_spin = abs(spin1 - 1);
      dEJ = (2*spin_count[spin1] - NN4)*Jij;
      dEA = (Ja[spin1]*(-2*(droplet[spin1]->get_area() - 
			    droplet[spin1]->get_target_area()) + 1) +
	     Ja[t_spin]*(2*(droplet[t_spin]->get_area() - 
			    droplet[t_spin]->get_target_area()) + 1));
      
      // This is true only if Jij and Ja are integers
      dET = int(dEJ + dEA);
      if(dET <= 0 || ran3f(&ran_seed3) < prob[dET])
	flip_spin_routine(coord1, spin1, t_spin);
    }
  } 
}

#endif

```
I don't want to include unnecessary code for fear of complicating things. Hope this helps.

---

### Post by swong1 on 2006-02-09
Used valgrind to check for memory allocation. It appears that I have attempted to free memory that has already been freed. I commented out the delete command in the destructor and everything is fine again. This is a novice mistake, the destructor of BOTH derived and parent class are called, so the delete command was executed twice. That is why the error only occurs when I run the derived class and not the parent class.
Thanks!

---

