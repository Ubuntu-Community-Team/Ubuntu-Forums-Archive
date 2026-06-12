---
title: "Getting inconsistent results with GCC optimization"
date: 2008-04-13
forum: Programming Talk
---

### Post by Mirrorball on 2008-04-13
I'm compiling the following code with different optimization flags and getting different results.

```
/*  dpole_integrate.hpp
 * 
 *  Solves Wieland's equations of motion for the double pole
 *  balancing problem using Runge-Kutta forth-order method.
 * 
 *  A direct ripoff from Stanley's C++ code (with small changes) written 
 *  by Richard Sutton, Charles Anderson, and Faustino Gomez.
 * 
 *  This code is intended to be used with neat-python:
 *  http://code.google.com/p/neat-python    
*/
   
#include <vector>
#include <cmath>
#include <stdlib.h>

using namespace std;
   
void step(double action, const vector<double> &st, vector<double> &derivs) {
    
    double FORCE_MAG = 10.0;
    double GRAVITY = -9.8;
    double LENGTH_1 = 0.5;
    double LENGTH_2 = 0.05;
    double MASSPOLE_1 = 0.1;
    double MASSPOLE_2 = 0.01;
    double MASSCART = 1.0;
    double MUP = 0.000002;    
    
    double force, costheta_1, costheta_2, sintheta_1, sintheta_2;
    double gsintheta_1, gsintheta_2, temp_1, temp_2;
    double ml_1, ml_2, fi_1, fi_2, mi_1, mi_2;
    
    force =  (action - 0.5) * FORCE_MAG * 2;
    costheta_1 = cos(st[2]);
    sintheta_1 = sin(st[2]);
    gsintheta_1 = GRAVITY * sintheta_1;
    costheta_2 = cos(st[4]);
    sintheta_2 = sin(st[4]);
    gsintheta_2 = GRAVITY * sintheta_2;
    
    ml_1 = LENGTH_1 * MASSPOLE_1;
    ml_2 = LENGTH_2 * MASSPOLE_2;
    temp_1 = MUP * st[3] / ml_1;
    temp_2 = MUP * st[5] / ml_2;
    
    fi_1 = (ml_1 * st[3] * st[3] * sintheta_1) +
           (0.75 * MASSPOLE_1 * costheta_1 * (temp_1 + gsintheta_1));
    fi_2 = (ml_2 * st[5] * st[5] * sintheta_2) +
           (0.75 * MASSPOLE_2 * costheta_2 * (temp_2 + gsintheta_2));
           
    mi_1 = MASSPOLE_1 * (1 - (0.75 * costheta_1 * costheta_1));
    mi_2 = MASSPOLE_2 * (1 - (0.75 * costheta_2 * costheta_2));
    
    derivs[1] = (force + fi_1 + fi_2)
                 / (mi_1 + mi_2 + MASSCART);
    
    derivs[3] = -0.75 * (derivs[1] * costheta_1 + gsintheta_1 + temp_1)
                 / LENGTH_1;
    derivs[5] = -0.75 * (derivs[1] * costheta_2 + gsintheta_2 + temp_2)
                  / LENGTH_2;
}

void rk4(double f, const vector<double> y, const vector<double> &dydx, vector<double> &yout) {

    int i;

    double hh,h6;
    
    vector<double> dym(6), dyt(6), yt(6);

    double TAU = 0.01;
    
    hh=TAU*0.5;
    h6=TAU/6.0;
    for (i=0;i<=5;i++) yt[i]=y[i]+hh*dydx[i];
    step(f,yt,dyt);
    dyt[0] = yt[1];
    dyt[2] = yt[3];
    dyt[4] = yt[5];
    for (i=0;i<=5;i++) yt[i]=y[i]+hh*dyt[i];
    step(f,yt,dym);
    dym[0] = yt[1];
    dym[2] = yt[3];
    dym[4] = yt[5];
    for (i=0;i<=5;i++) {
        yt[i]=y[i]+TAU*dym[i];
        dym[i] += dyt[i];
    }
    step(f,yt,dyt);
    dyt[0] = yt[1];
    dyt[2] = yt[3];
    dyt[4] = yt[5];
    for (i=0;i<=5;i++)
        yout[i]=y[i]+h6*(dydx[i]+dyt[i]+2.0*dym[i]);
}

vector<double> performAction(double output, vector<double> state, int stepnum) { 
  
  vector<double>  dydx(6);
     
  /*--- Apply action to the simulated cart-pole ---*/
  for(int k=0; k<stepnum; k++) {
        for(int i=0; i<2; ++i){
            dydx[0] = state[1];
            dydx[2] = state[3];
            dydx[4] = state[5];
            step(output, state, dydx);
            rk4(output, state, dydx, state);
        }
  }
    
    return state;
  }
  
int main() {
    
    vector<double> state(6);
    
    for(int i=0; i < 6; i++) state[i] = 0.01;
    
    for(int i=0; i < 10; i++)
        state = performAction(0.5, state, 10000);
    
    printf("%.17f   %.17f   %.17f   %.17f   %.17f   %.17f\n",state[0],state[1],state[2],state[3],state[4],state[5]);
    
}

```

```
$ g++ -o dpole dpole_original.cpp && ./dpole
20.87771065470305842   -0.02836753604224248   -4.52406202436528204   -4.71907945048420885   -147.43197456973430803   2.21573688915857003
$ g++ -O1 -o dpole dpole_original.cpp && ./dpole
20.95801285285628168   0.02158455713433968   -0.97341861708115507   -0.46745808743808265   -46.81883270949685993   -1.66276577080065913
$ g++ -O2 -o dpole dpole_original.cpp && ./dpole
20.95567636375585252   0.00072906946319039   -0.89608176628962277   0.36976730358865778   3.53363899202751952   1.63071613861864950
$ g++ -O3 -o dpole dpole_original.cpp && ./dpole
20.95567636375585252   0.00072906946319039   -0.89608176628962277   0.36976730358865778   3.53363899202751952   1.63071613861864950
$ g++ -Os -o dpole dpole_original.cpp && ./dpole
20.87782163586301110   0.04792293044524835   -5.02346123495042995   -2.78857669704863964   -53.15806737976144802   -2.24318043547427104
```

Why? What's wrong with this code? What am I supposed to do?

---

### Post by WW on 2008-04-13
> **Mirrorball said:**
>  What am I supposed to do?
Use a better ODE solver.  RK4 is really only of academic interest.  Take a look at, for example, CVODE (part of the SUNDIALS suite, Ubuntu package libsundials-serial-dev), or the GNU Scientific Library ODE solver functions (Ubuntu package libgsl0-dev).

I don't know exactly why changing the optimization level causes the problem--perhaps it changes the order of several steps of your calculations.  If your equations are sensitive, that could cause big changes in the final output.  A better ODE solver will use error control and adaptive step sizes to maintain a given level of accuracy.  Unless you really understand the expected behavior of your solutions, don't use RK4.

---

### Post by Mirrorball on 2008-04-13
Thanks a lot for your help, I'm going to take a look at these libraries. Meanwhile I found out that the difference disappears if I substitute long double for double. It looks like an accuracy problem. Hopefully one of the other algorithms you suggested will be better at controling the error.

---

