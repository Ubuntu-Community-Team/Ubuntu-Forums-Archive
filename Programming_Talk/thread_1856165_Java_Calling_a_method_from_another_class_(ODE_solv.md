---
title: "Java: Calling a method from another class (ODE solver)"
date: 2011-10-07
forum: Programming Talk
---

### Post by jr226 on 2011-10-07
Hi, I'm trying to program an ODE solver (similar to ODE45 in MATLAB).  I want this solver to be "stand alone", ie I can pass it the name of the ODE I want it to solve, and it runs the code for that specific Differential equation.

So far I have my main class (where the bulk of the program is) and a class called ODEsolver (where the ODE solver is located).  I want to be able to make a call from my main class to ODEsolver, and have ODE look at a method which is referenced by a String arguement (the name of the ODE I want to solve)

The way I envision it is:

public class Main {
[INDENT]double y[];
double x0,xf,y0;
x0 = 0;
xf = 10;
y0 = 1;

ODEsolver ode1 = new ODEsolver("name_of_ode_to_be_solved");

y = ode1.ODE45(x0,xf,y0);

[/INDENT]


}

where ODE45 is the ODE solver in the ODEsolver class.

However I do not know how I would use the "name_of_ode_to_be_solved" to create a call to that method (the method is not in ODEsolver, it's either in main or some other class)

Thanks!

---

### Post by Lux Perpetua on 2011-10-07
I'd suggest something more object-oriented: have an "ODE" interface that abstracts the features of the ODE that the solver needs to know about. For example, the solver needs to be able to evaluate the function defining the ODE; it needs the initial value, etc. Since this is Java, you can literally use an interface for that. Then for each ODE (or family of such) you want to solve, you can implement that interface with a class. To instantiate an ODEsolver, you pass an instance of such a class (anything that implements the ODE interface), not a string. If at the end of the day you want a string mapped to an ODE, you could just put a bunch of ODE objects in a HashMap or something. 

Hope that makes sense...

---

### Post by ofnuts on 2011-10-08
> **Lux Perpetua said:**
> I'd suggest something more object-oriented: have an "ODE" interface that abstracts the features of the ODE that the solver needs to know about. For example, the solver needs to be able to evaluate the function defining the ODE; it needs the initial value, etc. Since this is Java, you can literally use an interface for that. Then for each ODE (or family of such) you want to solve, you can implement that interface with a class. To instantiate an ODEsolver, you pass an instance of such a class (anything that implements the ODE interface), not a string. If at the end of the day you want a string mapped to an ODE, you could just put a bunch of ODE objects in a HashMap or something. 

Hope that makes sense...
+1 for most of the above. Creating an instance of the ODE interface from a name is a typical job for a "factory".

---

