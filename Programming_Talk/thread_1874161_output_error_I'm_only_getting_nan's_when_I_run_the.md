---
title: "output error: I'm only getting nan's when I run the program"
date: 2011-11-02
forum: Programming Talk
---

### Post by Jumper11550 on 2011-11-02
I'm writing a program to compute the the summ of a bessel series but the output I'm getting is all nan or inf.  I'm not sure what could be causing this beyond a precision limitation.   Large section so of the code are commented out, but that's unrelated to the summation.  Currently it is set to output the sum to the command line on each iteration (so I could watch its output)

```

#include <iostream>
#include <fstream>
#include <cstdlib>
#include <cmath>
#include <math.h>
#include <stdio.h>
#include <string.h>
using namespace std;
int factorial (int);
int minusone (int);
int main()
{
  double r, rinc, rini, rmax, n;
    double xlow, xupp, xstep, sum, gamma, mu;
    std::string filename;
    std::string configfile;
    char again;
    again='y';
    while(again=='y')
    {
    
        cout << "What is the domain:" << endl;
        cout << "Lower limit?" << endl;
        cin >> xlow;
        cout << "Upper limit?" << endl;
        cin >> xupp;
        cout << "What size is delta x?" << endl;
        cin >> xstep;
        cout << "What is the initial r?" <<endl;
        cin >> rini;
        cout << "r increment?" << endl;
        cin >> rinc;
        cout << "What is r maximum?" << endl;
        cin >> rmax;
        cout << "What is mu?" << endl;
        cin >> mu;
        cout << "What is n?" << endl;
        cin >> n;

        /*for(double mu=0.5; mu <=1; mu += 0.5)
          {
            for(int n= 0; n<=2; n++)
              {
            if(mu == 0.5)
              {
                string number;
                number = n;
                cout << number;
                filename = "besselsumhalf" + number + ".dat";
                configfile = "besselsumhalf" + number;
                cout << filename;
              }
            else
              {
                string number;
                number = n;
                filename = "besselsumone" + number + ".dat";
                configfile = "besselsumone" + number;
                cout << filename;
                }*/
            ofstream myfile;
            myfile.open ("test.dat");
            if (myfile.is_open())
              {
                myfile << "#x" << "    " << "J(x)" << endl;
              }
            else
              {
                cout << "could not open file" << endl;
              }
            myfile.close();
    
            for(double x=xlow; x <= xupp; x += xstep)
              {
                
                r=rini;
                sum=0;
                while(r <= rmax)
                  {
                gamma = factorial(n+r);
                sum+=((minusone(r)*pow(((mu*x)/2),(n+(2*r))))/(factorial(r)*gamma));
                r+=rinc;
                cout << sum;
                  }
                
                myfile.open ("test.dat", ios::app);
                if (myfile.is_open())
                  {
                myfile << x << "    " << sum << endl;
                  }
                else
                  {
                cout << "could not open file" << endl;
                  }
                myfile.close();
              }
            /*myfile.open((configfile + ".cfg").c_str());
            if(myfile.is_open())
              {
                myfile << "set xlabel 'x'" << endl;
                myfile << "set ylabel 'J(n)'" << endl;
                myfile << "set label '" << configfile << "'" << endl;
                myfile << "plot [0:" << xupp << "] '" << filename << "' w lines" << endl;
                myfile << "set term png" << endl;
                myfile << "set output '" << configfile << ".png'" << endl;
                myfile << "replot" << endl;
              }
            else
              {
                cout << "could not open file" << endl;
              }
            myfile.close();
            string command;
            command = "gnuplot -persist " + configfile + ".cfg";
            FILE *pipe = popen(command.c_str(), "w");*/
            cout << "Would you like to run again(y/n)?" << endl;
            cin >> again;
            //    }
            // }
    }
    return 0;
}

int factorial (int m)
{
   int fact = 1;
   if (m <= 1)
     {
       return 1;
     }
   else
     {
       fact  = m * factorial (m - 1);
     }
   return fact;
}

int minusone (int l)
{
  if(l%2 == 0)
    {
      return 1;
    }
  else if(l%2 == 1)
    {
      return -1;
    }
}


```

Thanks in advance for all your help.

P.S. if it is a precision issue I already have the gmp library but I'm not really sure how to use it so if you could point me to a good tutorial that's easy to understand and starts at the basics I'd appreciate it

---

### Post by Jumper11550 on 2011-11-02
Okay, so I guess it would help if I provided bounds for x and r in this summations, however I've decided to go with a minimum precision limit and just use a while loop with a stop condition.  So thread is no longer needed.

Please lock

---

### Post by karlson on 2011-11-02
> **Jumper11550 said:**
> I'm writing a program to compute the the summ of a bessel series but the output I'm getting is all nan or inf.  I'm not sure what could be causing this beyond a precision limitation.   Large section so of the code are commented out, but that's unrelated to the summation.  Currently it is set to output the sum to the command line on each iteration (so I could watch its output)

```

#include <iostream>
#include <fstream>
#include <cstdlib>
#include <cmath>
#include <math.h>
#include <stdio.h>
#include <string.h>
using namespace std;
int factorial (int);
int minusone (int);
int main()
{
  double r, rinc, rini, rmax, n;
    double xlow, xupp, xstep, sum, gamma, mu;
    std::string filename;
    std::string configfile;
    char again;
    again='y';
    while(again=='y')
    {
    
        cout << "What is the domain:" << endl;
        cout << "Lower limit?" << endl;
        cin >> xlow;
        cout << "Upper limit?" << endl;
        cin >> xupp;
        cout << "What size is delta x?" << endl;
        cin >> xstep;
        cout << "What is the initial r?" <<endl;
        cin >> rini;
        cout << "r increment?" << endl;
        cin >> rinc;
        cout << "What is r maximum?" << endl;
        cin >> rmax;
        cout << "What is mu?" << endl;
        cin >> mu;
        cout << "What is n?" << endl;
        cin >> n;

        /*for(double mu=0.5; mu <=1; mu += 0.5)
          {
            for(int n= 0; n<=2; n++)
              {
            if(mu == 0.5)
              {
                string number;
                number = n;
                cout << number;
                filename = "besselsumhalf" + number + ".dat";
                configfile = "besselsumhalf" + number;
                cout << filename;
              }
            else
              {
                string number;
                number = n;
                filename = "besselsumone" + number + ".dat";
                configfile = "besselsumone" + number;
                cout << filename;
                }*/
            ofstream myfile;
            myfile.open ("test.dat");
            if (myfile.is_open())
              {
                myfile << "#x" << "    " << "J(x)" << endl;
              }
            else
              {
                cout << "could not open file" << endl;
              }
            myfile.close();
    
            for(double x=xlow; x <= xupp; x += xstep)
              {
                
                r=rini;
                sum=0;
                while(r <= rmax)
                  {
                gamma = factorial(n+r);
                sum+=((minusone(r)*pow(((mu*x)/2),(n+(2*r))))/(factorial(r)*gamma));
                r+=rinc;
                cout << sum;
                  }
                
                myfile.open ("test.dat", ios::app);
                if (myfile.is_open())
                  {
                myfile << x << "    " << sum << endl;
                  }
                else
                  {
                cout << "could not open file" << endl;
                  }
                myfile.close();
              }
            /*myfile.open((configfile + ".cfg").c_str());
            if(myfile.is_open())
              {
                myfile << "set xlabel 'x'" << endl;
                myfile << "set ylabel 'J(n)'" << endl;
                myfile << "set label '" << configfile << "'" << endl;
                myfile << "plot [0:" << xupp << "] '" << filename << "' w lines" << endl;
                myfile << "set term png" << endl;
                myfile << "set output '" << configfile << ".png'" << endl;
                myfile << "replot" << endl;
              }
            else
              {
                cout << "could not open file" << endl;
              }
            myfile.close();
            string command;
            command = "gnuplot -persist " + configfile + ".cfg";
            FILE *pipe = popen(command.c_str(), "w");*/
            cout << "Would you like to run again(y/n)?" << endl;
            cin >> again;
            //    }
            // }
    }
    return 0;
}

int factorial (int m)
{
   int fact = 1;
   if (m <= 1)
     {
       return 1;
     }
   else
     {
       fact  = m * factorial (m - 1);
     }
   return fact;
}

int minusone (int l)
{
  if(l%2 == 0)
    {
      return 1;
    }
  else if(l%2 == 1)
    {
      return -1;
    }
}


```

Thanks in advance for all your help.

P.S. if it is a precision issue I already have the gmp library but I'm not really sure how to use it so if you could point me to a good tutorial that's easy to understand and starts at the basics I'd appreciate it

Looking at this line:
> 
sum+=( (minusone(r) * pow( ((mu*x)/2) ,(n+2*r) ) ) ) / ( factorial(r) * gamma ) );


I would suggest separating the terms and looking at there values as well as the result of the operations individually.  You are casting things all over the place which may not give you the result you are expecting.

NaN is most commonly received of number/0 or 0/0, Inf is number /0 or number very close to 0.

---

### Post by 11jmb on 2011-11-02
It could be that you are dividing by a number that is very small, possibly being rounded down to zero.

Try throwing in some debug statements and seeing if you are ever dividing by a number that gets that small.

---

