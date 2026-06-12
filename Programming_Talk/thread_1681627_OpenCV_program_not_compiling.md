---
title: "OpenCV program not compiling"
date: 2011-02-04
forum: Programming Talk
---

### Post by novice_coder on 2011-02-04
I installed opencv1.0 and the OS I use is Jaunty. I am not able to compile even the first program i tried.:confused:
I found the code online and used it to try whether I am able to compile program using OpenCV.
The code is as below.

#include<iostream>
#include<iomanip>
#include<cv.h>

using namespace cv;
usind namespace std;

//Simple function to print out a matrix

void myMatPrint(iomanip::ostream &outStream, std::string stringLabel, Mat &mat)
{
 iomanip::outStream<<stringLabel<<endl;
 for(int iRow=0 ; iRow<mat.rows ; iRow++)
 {
  for(int iCol=0; iCOl<mat.cols; iCol++)
   outStream<<setw(12) <<mat.at<double>(iROw,iCol);
  
  outStream<<endl;
 }
}

//Test code to take the SVD of a matrix and check its correctness
coid testSVD(coid)
{
 //data for the matrix whose SVD we want
 double aDate[] = {     0.078286, 0.152800, 0.483599, 0.132373,
             0.809265, 0.040108, 0.420196, 0.468431,
            0.188109, 0.179386, 0.245392, 0.217179,
            0.345795, 0.915636, 0.618565, 0.786891 };

 //4x4 double-precision matrix initialized from aData[]
 Mat matA(4, 4, CV_64F, aData);

 //Perform the SVD: A=U D V'
 SVD svdA(matA);

 //Check result
 Mat matD = Mat ::eye(matA.rows, matA.rows, CV_64F);
 for (int iDiag = 0; iDiag < matA.rows; iDiag++)
    {
        matD.at<double>(iDiag, iDiag) = svdA.w.at<double>(iDiag, 0);
    }
    Mat matAhat(4, 4, CV_64F);
    matAhat = svdA.u * matD * svdA.vt;
 
    double dError = norm( matA, matAhat );
 
    // Print out results
 
    myMatPrint( cout, "Original matrix A:", matA );
    myMatPrint( cout, "U:", svdA.u );
    myMatPrint( cout, "D:", svdA.w );
    myMatPrint( cout, "V (transposed):", svdA.vt );
    myMatPrint( cout, "U D V':", matAhat );
    cout << "Error (L2 norm): " << dError << endl;
 
    return;
}
// Main
 
int main( void )
{
    cout << "Testing the SVD class..." << endl;
    testSvd();
    return 0;
}

And I get the following error message when i try to compile it.

me@paul-desktop:~/Documents/opencv$ make
g++  -g -Wall -Wno-unused-function 'pkg-config --cflags opencv'   opencv-test.cpp   -o opencv-test
g++: pkg-config --cflags opencv: No such file or directory
opencv-test.cpp:3:15: error: cv.h: No such file or directory
opencv-test.cpp:5: error: ‘cv’ is not a namespace-name
opencv-test.cpp:5: error: expected namespace-name before ‘;’ token
opencv-test.cpp:6: error: expected constructor, destructor, or type conversion before ‘namespace’
opencv-test.cpp:10: error: variable or field ‘myMatPrint’ declared void
opencv-test.cpp:10: error: ‘iomanip’ has not been declared
opencv-test.cpp:10: error: ‘outStream’ was not declared in this scope
opencv-test.cpp:10: error: expected primary-expression before ‘stringLabel’
opencv-test.cpp:10: error: ‘Mat’ was not declared in this scope
opencv-test.cpp:10: error: ‘mat’ was not declared in this scope
make: *** [opencv-test] Error 1

If anyone could help me find out what is wrong, it would be great help.
Thank you in advance.

---

### Post by Some Penguin on 2011-02-04
Use the 'code' tags.  And check whether you've installed the dev package so you actually have the headers.

---

### Post by Vox754 on 2011-02-04
> **novice_coder said:**
> I installed opencv1.0 and the OS I use is Jaunty. I am not able to compile even the first program i tried.:confused:
...

me@paul-desktop:~/Documents/opencv$ make
g++  -g -Wall -Wno-unused-function 'pkg-config --cflags opencv'   opencv-test.cpp   -o opencv-test
g++: **pkg-config --cflags opencv**: No such file or directory
...

If anyone could help me find out what is wrong, it would be great help.
Thank you in advance.

The compilation command is incorrect.

Because you are using single quotes ('), it is interpreting **pkg-config --cflags opencv** as one file, which it is not.

Those are grave accents, also called backquotes, or backticks (`) not single quotes (').
```

g++  -g -Wall -Wno-unused-function **`pkg-config --cflags opencv`**   opencv-test.cpp   -o opencv-test

```

What it does is returning the result of
```

pkg-config --cflags opencv    # run this in your terminal to see

```
and adding it to the compilation command.

It is more clear if you use command substitution this way:
```

g++  -g -Wall -Wno-unused-function **$(pkg-config --cflags opencv)**   opencv-test.cpp   -o opencv-test

```

Since you also need to link the library to produce a working executable:
```

g++  -g -Wall -Wno-unused-function **$(pkg-config --cflags --libs opencv)**   opencv-test.cpp   -o opencv-test

```

---

### Post by novice_coder on 2011-02-05
Thank you for the reply Vox754. I used the code you suggested and this is the result i received.

$ g++  -g -Wall -Wno-unused-function $(pkg-config --cflags opencv)   opencv-test.cpp   -o opencv-test
opencv-test.cpp:6: error: expected constructor, destructor, or type conversion before ‘namespace’
opencv-test.cpp:10: error: variable or field ‘myMatPrint’ declared void
opencv-test.cpp:10: error: ‘iomanip’ has not been declared
opencv-test.cpp:10: error: ‘outStream’ was not declared in this scope
opencv-test.cpp:10: error: expected primary-expression before ‘stringLabel’
opencv-test.cpp:10: error: expected primary-expression before ‘&’ token
opencv-test.cpp:10: error: ‘mat’ was not declared in this scope

$ g++  -g -Wall -Wno-unused-function $(pkg-config --cflags --libs opencv)   opencv-test.cpp   -o opencv-test
opencv-test.cpp:6: error: expected constructor, destructor, or type conversion before ‘namespace’
opencv-test.cpp:10: error: variable or field ‘myMatPrint’ declared void
opencv-test.cpp:10: error: ‘iomanip’ has not been declared
opencv-test.cpp:10: error: ‘outStream’ was not declared in this scope
opencv-test.cpp:10: error: expected primary-expression before ‘stringLabel’
opencv-test.cpp:10: error: expected primary-expression before ‘&’ token
opencv-test.cpp:10: error: ‘mat’ was not declared in this scope

I am assuming that the problem is with the code I have written. Howver, I am not able to rectify it. Looking forward to a reply.

---

### Post by hakermania on 2011-02-05
Ok, 
1. you have mistyped 'usin**d** namepsace' instead of 'using namespace'
2. The line _**coid myMatPrint(iomanip:stream &outStream, std::string stringLabel, Mat &mat)**_ has multiple errors (iomanip has not been declared, and mat hasn't either!

---

### Post by novice_coder on 2011-02-05
Thank you hakermainia. I corrected the spelling of "using" but the rest of the mistakes still exist.

---

### Post by SevenMachines on 2011-02-05
Look at your spelling, remember, these things are case sensitive..

* line 23: You have 2 mispellings of 'void' as 'coid'
* line 10: iomanip:stream ? Sure you dont want an ostream? single ':' dont mean anything here
* line 12: iomanip:utStream, i'm guessing you want the actual outStream reference here
* line 15: iCOl is not the same as iCol
* line 16: Similarly, iROw is not the same as iRow
* line 32: I'm guessing aData is supposed to be aDate
* line 64: testSvd() is not the same as testSVD()

If you look to make some of the changes above...
```
$ g++ -o test test.cpp `pkg-config --cflags --libs opencv`
$ ./test
Testing the SVD class...
Original matrix A:
    0.078286      0.1528    0.483599    0.132373
    0.809265    0.040108    0.420196    0.468431
    0.188109    0.179386    0.245392    0.217179
    0.345795    0.915636    0.618565    0.786891
U:
   -0.253323   0.0542288    0.950949    0.169063
   -0.497937   -0.848586   -0.109392    0.141399
   -0.244213  -0.0311122    0.107958   -0.963191
    -0.79262     0.52535   -0.268466    0.153905
D:
     1.70465
    0.677779
     0.32076
  0.00071192
V (transposed):
   -0.435759    -0.48587    -0.51738     -0.5535
   -0.747551     0.66349  -0.0192079   0.0240654
   -0.270008   -0.266659    0.855282   -0.352819
   -0.422347   -0.502598   0.0210227     0.75404
U D V':
    0.078286      0.1528    0.483599    0.132373
    0.809265    0.040108    0.420196    0.468431
    0.188109    0.179386    0.245392    0.217179
    0.345795    0.915636    0.618565    0.786891
Error (L2 norm): 1.20761e-15
```Mostly your errors are all spelling/case mistakes, you must be typing too quickly :)

---

### Post by realzippy on 2011-02-05
here is a working guide for compiling opencv (latest snapshot) : 
[http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux)
 
...used it days ago,needed opencv for headtrack...

---

### Post by novice_coder on 2011-02-10
Thanks a lot for all the valued replies. I made the necessary corrections and now it works. :o

Posting the code to help anyone who wishes to try it. :)


 #include<iostream>
 #include<iomanip>
 #include<cv.h>

 using namespace cv;
 using namespace std;

 //Simple function to print out a matrix

 void myMatPrint(std::ostream &outStream, std::string stringLabel, Mat &mat)
 {
 outStream<<stringLabel<<endl;
 for(int iRow=0 ; iRow<mat.rows ; iRow++)
 {
 for(int iCol=0; iCol<mat.cols; iCol++)
 outStream<<setw(12) <<mat.at<double>(iRow,iCol);

 outStream<<endl;
 }
 }

 //Test code to take the SVD of a matrix and check its correctness
 void testSVD(void)
 {
 //data for the matrix whose SVD we want
 double aDate[] = { 0.078286, 0.152800, 0.483599, 0.132373,
 0.809265, 0.040108, 0.420196, 0.468431,
 0.188109, 0.179386, 0.245392, 0.217179,
 0.345795, 0.915636, 0.618565, 0.786891 };

 //4x4 double-precision matrix initialized from aData[]
 Mat matA(4, 4, CV_64F, aDate);

 //Perform the SVD: A=U D V'
 SVD svdA(matA);

 //Check result
 Mat matD = Mat ::eye(matA.rows, matA.rows, CV_64F);
 for (int iDiag = 0; iDiag < matA.rows; iDiag++)
 {
 matD.at<double>(iDiag, iDiag) = svdA.w.at<double>(iDiag, 0);
 }
 Mat matAhat(4, 4, CV_64F);
 matAhat = svdA.u * matD * svdA.vt;

 double dError = norm( matA, matAhat );

 // Print out results

 myMatPrint( cout, "Original matrix A:", matA );
 myMatPrint( cout, "U:", svdA.u );
 myMatPrint( cout, "D:", svdA.w );
 myMatPrint( cout, "V (transposed):", svdA.vt );
 myMatPrint( cout, "U D V':", matAhat );
 cout << "Error (L2 norm): " << dError << endl;

 return;
 }
 // Main

 int main( void )
 {
 cout << "Testing the SVD class..." << endl;
 testSVD();
 return 0;
 }

/*

output:

$ g++ opencvtest1.cpp `pkg-config --libs --cflags opencv` -Wall
$ ./opencvtest1
Testing the SVD class...
Original matrix A:
    0.078286      0.1528    0.483599    0.132373
    0.809265    0.040108    0.420196    0.468431
    0.188109    0.179386    0.245392    0.217179
    0.345795    0.915636    0.618565    0.786891
U:
   -0.253323   0.0542288    0.950949    0.169063
   -0.497937   -0.848586   -0.109392    0.141399
   -0.244213  -0.0311122    0.107958   -0.963191
    -0.79262     0.52535   -0.268466    0.153905
D:
     1.70465
    0.677779
     0.32076
  0.00071192
V (transposed):
   -0.435759    -0.48587    -0.51738     -0.5535
   -0.747551     0.66349  -0.0192079   0.0240654
   -0.270008   -0.266659    0.855282   -0.352819
   -0.422347   -0.502598   0.0210227     0.75404
U D V':
    0.078286      0.1528    0.483599    0.132373
    0.809265    0.040108    0.420196    0.468431
    0.188109    0.179386    0.245392    0.217179
    0.345795    0.915636    0.618565    0.786891
Error (L2 norm): 1.08409e-15


*/

---

