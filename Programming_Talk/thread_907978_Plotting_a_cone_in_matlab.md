---
title: "Plotting a cone in matlab"
date: 2008-09-02
forum: Programming Talk
---

### Post by nitro_n2o on 2008-09-02
Hi all,

I'm trying to plot a cone in matlab given the parameters h, r, theta, where h is the height of the cone, r is the radius and theta is the angle inside! 

The, the intent is to have the cone move on some line in 3d, so if the line is curved it'll also curve with the line

is there a way to do this in matlab? 

Thx

---

### Post by WW on 2008-09-02
If you give r and h, you have completely determined the shape of the cone, so you can't also give "the angle inside", theta. 

Here's a matlab script that plots a cone around the z-axis, and then rotates the data to plot two more cones.  This might give you some ideas for your application.
```

clf

r = 1.0;
h = 2.0;
m = h/r;
[R,A] = meshgrid(linspace(0,r,11),linspace(0,2*pi,41));
X = R .* cos(A);
Y = R .* sin(A);
Z = m*R;
% Cone around the z-axis, point at the origin
mesh(X,Y,Z)

hold on
axis equal
axis([-3 3 -3 3 0 3])

phi = -pi/3;
X1 = X*cos(phi) - Z*sin(phi);
Y1 = Y;
Z1 = X*sin(phi) + Z*cos(phi);
% Previous cone, rotated by angle phi about the y-axis
mesh(X1,Y1,Z1)

theta = pi/4;
X2 = X1*cos(theta) - Y1*sin(theta);
Y2 = X1*sin(theta) + Y1*cos(theta);
Z2 = Z1;
% Second cone rotated by angle theta about the z-axis
mesh(X2,Y2,Z2)

xlabel('x')
ylabel('y')
zlabel('z')

```

---

### Post by cszikszoy on 2008-09-02
> **nitro_n2o said:**
> I'm trying to plot a cone in matlab

What's Matlab?  I've heard of Octave, but never Matlab?


:)

---

### Post by nitro_n2o on 2008-09-02
This is really great, thanks so much :) 
and yeah what to do.. Matlab!!

---

