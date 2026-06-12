---
title: "linker error using ubuntu v.10"
date: 2012-04-25
forum: Programming Talk
---

### Post by itba on 2012-04-25
hi,
I have the following function in dm.cpp

    ```
#include <iostream>
    #include <iterator>
    #include <vector>
    #include <cmath>
    #include <Eigen/Dense>
    #include "dm.hpp";//calculateStdDev() is declared in the header

    double calculateStdDev(const Eigen::VectorXf& input, unsigned int count, double& mean, double& variance, double& stddev) {
      double M = input(0);
      double Q = 0.0;
      for (unsigned int k = 1 ; k < count ; k++) {
        double del = input(k) - M;
        unsigned int j = k + 1;
        Q += k * (del * del) / j;
        M += del / j;
      }
      variance = Q / (count - 1);
      stddev = std::sqrt(variance);
      mean = M;
      return stddev;
    }

```
and it is called in my program, test.cpp as below:

    ```
#include <iostream>
    #include <iterator>
    
    #include <Eigen/Dense>
    #include "dm.hpp"
    void regressor:operator()(void) {
 
    unsigned int rows;
        double meanR, varR, stddevR;
      Eigen::MatrixXf A(rows, cols);
      Eigen::VectorXf b(rows),res(rows);

      for (unsigned int k = 0 ; k < rows; k++) {
        for (unsigned int j = 0 ; j < cols ; j++) {
          A(k,j) = Xb[k][j];
        }

      }
      beta = A.jacobiSvd(Eigen::ComputeThinU | Eigen::ComputeThinV).solve(b);
      res = A * beta - b;
      
     calculateStdDev(res,rows,meanR,varR,stddevR);
```


I get the following error:

    ```
In function `regressor:operator()()':
    ../../src/algo/test.cpp:55: undefined reference to `calculateStdDev(Eigen::Matrix<float, -1, 1, 0, -1, 1> const&, unsigned int, double&, double&, double&)'
    collect2: ld returned 1 exit status
```

my OS is ubuntu (v.10) and when the exact same program is run on cygwin, it works. Does that mean this is a GCC issue. If so, can anyone suggest how to fix it because I really want to switch to cygwin.

---

### Post by 11jmb on 2012-04-25
You didn't post the code where it is declared, but is res of type VectorXf?

It is more likely a problem with your code than a problem with gcc

---

### Post by itba on 2012-04-25
yes, that is what res is.
well, ordinarily I would have agreed that it is a problem with the code, but the exact same code run on a cygwin machine is working perfectly fine....that is what I do not understand.

---

