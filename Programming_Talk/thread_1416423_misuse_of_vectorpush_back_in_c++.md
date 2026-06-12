---
title: "misuse of vector::push_back in c++"
date: 2010-02-26
forum: Programming Talk
---

### Post by vincentberenz on 2010-02-26
Hi,

I am Java programmer but need to write a small program in c++, and many things are confusing to me. I have been fighting quite a lot on this (simple) bit of code and I do not get what is wrong :

_header file_ :
```

class Cluster {
 public:
  Cluster();
  ~Cluster();
  double distance(Point p1,Point p2);
  double r(double a);
  double getMaxD();
  void addPoint(Point newPoint);
  Point getCenter();
  std::vector<Point> getPoints();
  double distance(Cluster c2);
  void fuse(Cluster c2);
  int getSize();
  void print();
 protected:
  std::vector<Point> points;
  Point center;
  double maxD;
  void compute();
};

```_cpp file_  (note : Point is a structure with only two int, x and y)
```
#include "cluster.h"

Cluster::Cluster(){}
Cluster::~Cluster(){}

double Cluster::r(double a){
  return int(a + 0.5);
}

double Cluster::distance(Point p1,Point p2){
  double dx = p1.x-p2.x;
  dx = dx*dx;
  double dy = p1.y-p2.y;
  dy = dy*dy;
  return sqrt(dx+dy);
}

void Cluster::compute(){
 double x = 0;
  double y = 0;
  maxD = 0;
  for(int i=0;i<points.size();i++){
    x += points[i].x;
    y += points[i].y;
    for(int j=(i+1);j<points.size();j++){
      double d = distance(points[i],points[j]);
      if(d>maxD){
    maxD = d;
      }
    }
  }
  center.x = r(x/points.size());
  center.y = r(y/points.size());
  center.def = true;
}

double Cluster::getMaxD(){
  return maxD;
}

void Cluster::addPoint(Point newPoint){
  printf(" ---- adding %i\t%i\n",newPoint.x,newPoint.y);
  points.push_back(newPoint);
  printf(" ---- \n");
  center.def = false;
  maxD = -1;
}

Point Cluster::getCenter(){
  if(!center.def){
    compute();
    center.def = true;
  }
  return center;
}

std::vector<Point> Cluster::getPoints(){
  return points;
}

double Cluster::distance(Cluster c2){
  return distance(getCenter(),c2.getCenter());
}

void Cluster::fuse(Cluster c2){
  printf("before clustering\n");
  print();
  c2.print();
 std::vector<Point> points2 = c2.getPoints();
  for(int i=0;i<points2.size();i++){
    printf("--- transfering\t%i\t%i\n",points2[i].x,points2[i].y);
    addPoint(points2[i]);
    printf("--\n");
  }
  center.def = false;
  printf("after clustering\n");
  c2.print();
}

int Cluster::getSize(){
  return points.size();
}

void Cluster::print(){
  printf("-- cluster -- \n");
  for(int j=0;j<points.size();j++){
    printf("%i\tx:\t%i\ty:\t %i\n",j,points[j].x,points[j].y);      
  }
  printf("------------- \n");
}

```

Depending on which set it is used the program can run fine or exit with some ugly error message 
```
*** glibc detected *** ./testCluster: double free or corruption (top): 0x0986ab20 ***

```Using the printf function I could find its origine :
-- another program calls the "fuse()"
-- the two clusters and the Points they contained are correctly printed
-- the function addPoint is called a few time without any trouble
-- then at some point the program fails at the line (in the function addPoint) :
 ```
points.push_back(newPoint);
```
Note : in the previous line "newPoint" is correctly printed.

I really do not get what could have get wrong with my vector<Point> points.
I did not copy the code of the other classes and programs, but would be happy to do it if necessary.

thanks a lot !

---

### Post by vincentberenz on 2010-02-26
Actually the problem was coming from somewhere else but showing here.
Some variable was declared but not initiated ....
I had no idea it could have unexpected effect at completely unrelated part of the code !!!

---

