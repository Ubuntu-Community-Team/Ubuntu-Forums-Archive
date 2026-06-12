---
title: "very confused about passing objects in c++"
date: 2011-12-24
forum: Programming Talk
---

### Post by abraxas334 on 2011-12-24
I have the following problem:
I have three classes: a manager class, a "do all the stuff class", and a trajectory class (which holds all the data i want from do all the stuff class and can manipulate that data).
What I want to do is have an instant of trajectory in my manager class pass it to the "do all the stuff" class and then look at the data from my manager class. so basically i just want one instant of trajectory in memory which I can manipulate in both manager and "do all the stuff". 
Firstly is this a bad approach?
Secondly how do I do this properly? Here are my three trial classes.
My main run function in manager:
[PHP]
void manager::run(){
    
    trajectory T ;
    MC newMC;
    bool constant = true;
    
    newMC.setTrajectory(T);
    newMC.evolve(constant);
    //T = newMC.returnTrajectory();
    
    //now look at data:
    cout<<"Container size after const passing "<<T.container1.size()<<endl;
    
    if(T.container1.size()>0){
        for(int i =0; i<T.container1.size(); i++){
            cout<<T.container1[i];
        }
    
    }
    cout<<"printing within manager ......... "<<endl;
    newMC.printTrajectory();
    
    //case not constant reference
    constant = false;
    T.container1.clear();
    T.container2.clear();
    newMC.setTrajectory(T);
    newMC.evolve(constant);
    T = newMC.returnTrajectory();
    
    //now look at data:
    cout<<"Container size after not const passing "<<T.container1.size()<<endl;
    
    if(T.container1.size()>0){
        for(int i =0; i<T.container1.size(); i++){
            cout<<T.container1[i];
        }
    
    }
    
    
}

[/PHP]
My do everything class MC:
[PHP]
#ifndef MC_H
#define	MC_H
#include <iostream>
#include "trajectory.h"


using namespace std;
class MC {
public:
    MC();
    MC(const MC& orig);
    virtual ~MC();
    
    void evolve(bool );
    void setTrajectory(trajectory &);
    trajectory returnTrajectory();
    void printTrajectory();
    
    
private:
    trajectory traj;

};

#endif	/* MC_H */
#include "MC.h"

MC::MC() {
}

MC::MC(const MC& orig) {
}

MC::~MC() {
}

void MC::evolve(bool c) {

    vector<double> temp;
    double var;

    for (int j = 0; j < 10; j++) {
        for (double i = 0; i < 10; i++) {
            temp.push_back(i);
        }
        var = j;
        
        if(!c){
                traj.addData(var,temp);
        }
        else{
            traj.addData_const(var, temp);
        }
        
    }
    cout<<"printing within function.........."<<endl;
    printTrajectory();



}

void MC::setTrajectory(trajectory &T) {
    traj = T;

}

trajectory MC::returnTrajectory() {
    return traj;

}

void MC::printTrajectory(){
    cout<<"Container1 size is: "<<traj.container1.size()<<endl;
    cout<<"Container2 size is: "<<traj.container2.size()<<endl;
}

[/PHP]
and the trajectory class:
[PHP]
#ifndef TRAJECTORY_H
#define	TRAJECTORY_H

#include <vector>


using namespace std;

class trajectory {
public:
    trajectory();
    trajectory(const trajectory& orig);
    virtual ~trajectory();
    void addData_const(double , const vector<double> &);
    void addData(double, vector<double>);
    
    
    vector<double> container1;
    vector<vector <double> > container2;
    
private:

};

#endif	/* TRAJECTORY_H */


trajectory::trajectory() {
}

trajectory::trajectory(const trajectory& orig) {
}

trajectory::~trajectory() {
}

void trajectory::addData_const(double val,const vector<double> &v_val){
    
    container1.push_back(val);
    container2.push_back(v_val);
    
    
}

void trajectory::addData(double val,vector<double> v_val){
    
    container1.push_back(val);
    container2.push_back(v_val);
    
    
}
[/PHP]

---

### Post by ju2wheels on 2011-12-28
I think you are talking about a static object instance (not instant) as a member of your manager class.

See the end of the page here for an example: [http://www.cplusplus.com/doc/tutorial/classes2/](http://www.cplusplus.com/doc/tutorial/classes2/)

1. You must instantiate the static trajectory instance BEFORE compile time if you make it static, however you can change its value later (unless you also make it constant).

2. Your trajectory data is public, so its accessible to the class that contains it (manager in this case) so im not sure what concerns you have there.

3. Is it a bad approach? You would know what you are designing best so since you havent stated what problem you are solving its hard to say. Aside from that, making the trajectory static wont matter since you seem to be using manager as a singleton and not creating more than one instance.

---

