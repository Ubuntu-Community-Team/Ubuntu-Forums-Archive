---
title: "Intersection point - double precision error"
date: 2014-10-15
forum: Programming Talk
---

### Post by achuthpnr on 2014-10-15
Hi,

I am trying to figure out the intersection point of a given line segment and a cubic box of edge L. First I check each face of the cube for intersection and if it occurs, calculate the intersection point. I accept and print the point when its on the line segment.  I have the commented sample code below:

My questions are: 

1. Is there any way to optimize this code for speed or altenate method to achieve the same?

2. With the current example code, I am getting an intersection point, which is actually outside the box(-4.440892e-16). I understand that this is due to the error in double precision calcualtion. What should be done to correct/compensate this? eg: reassign to 0. ? and similarly with L<xc..?

3. when I test whether the final point is on the line (its commented out for the moment), shouldn´t the test be dot>0 since the vectors are in same direction? then why am I getting a negative value in this case? where am I going wrong?

```

//finding the intersection point between a line segment and a plane.
//plane is represented by a point in the plane and a normal vector to the plane. Here the unit vectors i,j,k

#include<stdio.h>
#include<stdlib.h>
#include<math.h>

#define dist2(x,xd,y,yd,z,zd) ((x-xd)*(x-xd)+(y-yd)*(y-yd)+(z-zd)*(z-zd))
#define scalar(x,x1,y,y1,z,z1) (x*x1+y*y1+z*z1)

int main()
{
    unsigned long int L;
    double xc,yc,zc;
    double x,y,z,xd,yd,zd;
    double d2,d,dv1,dv2,costheta,dot;

    x=5.; //the initial point of the line segment
    y=5.;
    z=5.;

    xd=-03.; //the final point of the line segment
    yd=02.;
    zd=01.;

    L=15; //Size of the cubic box, assuming the other corner is origin

    d2=dist2(x,xd,y,yd,z,zd);
    d=sqrt(d2);
    dv1=scalar(1.,(x-0.),0.,(y-0.),0.,(z-0.)); //YZ plane left
    dv2=scalar(1.,(xd-0.),0.,(yd-0.),0.,(zd-0.));
    printf("left %le\n",dv1*dv2);
    
    if(dv1*dv2<=0 )
    {
        costheta=scalar(1.,(xd-x)/d,0.,(yd-y)/d,0.,(zd-z)/d);
        xc=xd-(xd-x)/d*dv2/costheta;
        yc=yd-(yd-y)/d*dv2/costheta;
        zc=zd-(zd-z)/d*dv2/costheta;
        dot=scalar(xd-x,xc-x,yd-y,yc-y,zd-z,zc-z);
        //if(dot>0)
            printf("%le\t%le\t%le\t%le\n",xc,yc,zc,dot);
     }
    
    // similarly for the other 5faces
    return(0);
}

```

---

### Post by tgalati4 on 2014-10-15
You could try [quad precision]("http://en.wikipedia.org/wiki/Quadruple-precision_floating-point_format").  

For #2, that is a common way to deal with small precision errors, just set them to values that you think they should be.  It really depends on how the final results are going to be used.

For #3, print out intermediate results.  Since you are taking differences {xd-(xd-x)} there will always be the possibility of negative results, especially with precision errors that you have noted.  Similarly, the [dot produc]("http://en.wikipedia.org/wiki/Dot_product")t should be greater than or equal to 0 (if the vectors are orthogonal).  You would have to track the intermediate results to see how the precision errors get propagated through your calculations.

As far as speed of calculation, you would need to consider the hardware (how many scalers and what bit-width can the floating point unit handle?).

Describe the input and output of this program?  Is it simply displaying the intersection on the screen like a CAD/CAM program?  Or are you assembling molecular chains and need to know how molecules link up?  The end-use application will usually dictate the precision and computation speed required.  Is this a homework assignment?

---

### Post by achuthpnr on 2014-10-15
Thanks for the reply.

Its for a particle in a box kind of problem. When it tries to escape, we stop the motion at contact point. Its not for display, we are after the numbers.

Im getting the correct/expected values until the final scalar function (dot=...) is called. The input parameters are correct, but somehow the scalar function misbehaves and gives wrong answer. Its just not the sign, but the value is also incorrect.

I am rechecking everything for the moment.

---

### Post by tgalati4 on 2014-10-15
Have you looked at any of the open source particle physics tools?

[http://www.dmoz.org/Science/Physics/Particle/Software/](http://www.dmoz.org/Science/Physics/Particle/Software/)

---

### Post by achuthpnr on 2014-10-16
If brackets are used while calculating the value of dot, I am getting the expected answer. Can anybody explain the difference between 
```

dot=scalar((xd-x),(xc-x),(yd-y),(yc-y),(zd-z),(zc-z));

```
and
```

dot=scalar(xd-x,xc-x,yd-y,yc-y,zd-z,zc-z);

```
and the cause of the error? 
:confused:

---

### Post by tgalati4 on 2014-10-16
My C programming is rusty, but both scalar functions appear to be identical.  However, in order to assign a value to a parameter that is then used within a function, it must be evaluated.  Using () is one way to guarantee evaluation of the operands to a value that can then be passed to a parameter for the scalar function evaluation.

You could try defining *scalar* using a more formal method:  [http://www.c4learn.com/c-programming/c-function-definition/](http://www.c4learn.com/c-programming/c-function-definition/)

That might make both calls to *scalar* identical.  There are several assumptions being made as to variable type, and how the value of the operands are being passed to the parameters.

I would include several test scalar computations as a confirmation.  Put them in a comment block as a reminder for future coding.

For example

testdot=scalar(1,1,1,1,1,1);
printf(testdot);
testdot=scalar(2-1,4-3,6-5,6-5, 2-1,2-1);
printf(testdot);
x=2;
y=1;
testdot=scalar(x-y,x-y,x-y,x-y,x-y,x-y);
printf(testdot);
testdot=scalar((x-y),(x-y),(x-y),(x-y),(x-y),(x-y));
printf(testdot);

All of the dot-products should be the same value.  If not, then you know how the parameters are passed.  Comment out the block with a reminder for future programming.

---

### Post by achuthpnr on 2014-10-17
Thanks for the comment. 

> **tgalati4 said:**
>   
There are several assumptions being made as to variable type, and how the value of the operands are being passed to the parameters.

Just being curious, could you point some sources for this and the use of brackets?

---

### Post by tgalati4 on 2014-10-17
Some tutorials:  

[http://fresh2refresh.com/c/c-function/](http://fresh2refresh.com/c/c-function/)

[http://www.cs.utah.edu/~germain/PPS/Topics/C_Language/c_functions.html](http://www.cs.utah.edu/~germain/PPS/Topics/C_Language/c_functions.html)

[http://www.tutorialspoint.com/cprogramming/c_functions.htm](http://www.tutorialspoint.com/cprogramming/c_functions.htm)

It's coming back to me now.  It looks like you need to use & notation that changes the behavior from "Pass by Value" to "Pass by Reference".  "Pass by Value" means that the value must be evaluated before the parameters will accept the value.  "Pass by Reference" allows the variables to change (and hence be evaluated) before they are passed to the parameter.

---

