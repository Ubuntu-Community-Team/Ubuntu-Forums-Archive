---
title: "Rotation Matrix"
date: 2008-11-20
forum: Programming Talk
---

### Post by elbarto_87 on 2008-11-20
Hopefully someone here has some experience with rotational matrices. I have tried to write a program to create a rotational matrix based on 2 points and the angle gamma, which is rotation about the local x axis.

My script works ok, but when I specify a vector with 2 points where the change in Z and X are zero, I do not get the result I need. I can see the problem is the formula I have (which I got from my text book) divides by zero in this case hence the problom.


The problem is very obvious as you can see by looking at where the local y and z matrices are not plotted in my figure.

The result should be a 3x3 orthogonal matrix. I used this matrix to plot the local axis of members in my structure, also shown. If any one knows of a better way to calculate a rotational matrix please let me know.



Regards Elbarto

```
function Ro = L(ri,rj,gamma)

gamma = deg2rad(gamma);
lx = rj(1)-ri(1);
ly = rj(2)-ri(2);
lz = rj(3)-ri(3);
l = sqrt(lx^2+ly^2+lz^2);
Ro = [lx/l ly/l lz/l; ...
    (-lx*ly*cos(gamma)-l*lz*sin(gamma))/(l*sqrt(lx^2+lz^2))  sqrt(lx^2+lz^2)*cos(gamma)/l (-ly*lz*cos(gamma) +l*lx*sin(gamma))/(l*sqrt(lx^2+lz^2)); ...
    (lx*ly*sin(gamma)-l*lz*cos(gamma))/(l*sqrt(lx^2+lz^2)) -sqrt(lx^2+lz^2)*sin(gamma)/l (ly*lz*sin(gamma)+l*lx*cos(gamma))/(l*sqrt(lx^2+lz^2))];
```

---

### Post by Kazade on 2008-11-20
Hmm, I'm not entirely sure I understand the question (and I'm at work so I shouldn't really even be here!) but, you can take a look at the rotation matrix code in my math library, specifically the 4x4 matrix stuff:

[http://github.com/Kazade/kazmath/tree/master/src%2Fmat4.c](http://github.com/Kazade/kazmath/tree/master/src%2Fmat4.c)

Just focus on the top left 3x3 elements for the rotation matrix you are after. The matrix indices are laid out as:

0 3 7  11
1 4 8  12
2 5 9  13
3 6 10 14

So you may need to transpose depending on what your application expects.

---

### Post by elbarto_87 on 2008-11-20
Basically what I want to be able to do is this:

1)Draw a line based on a start point(x,y,z) and a end point (x,y,z)

2)The vector between these two points represents a structural element ie. a beam or such

3) The member has its own set of axis, with the local x-axis running along the length of the member.

4) I need a rotational matrix to find what the other local axis are. More specifically, I need this matrix so I can later transform any force acting in a local system (this is trivial for 1 member, but if I have 100 members obviously I want to have them defined in one set of axis) into my global co ordinates.

Does this make sense or am I being even more confusing. [http://en.wikipedia.org/wiki/Rotation_matrix](http://en.wikipedia.org/wiki/Rotation_matrix) has an explanation, but I am having trouble trying to make sense of their numbers.

---

### Post by Npl on 2008-11-20
a rotation matrix rotates around the origin (0,0,0). To rotate an arbitrary vector A->B (from point A to point B) around A you must:
*) transpose (=move) A to the origin
*) rotate
*) transpose back to A

In short, if you for example want to transform point X, do:
X_Transformed = ( rotate(X-A) ) + A

your rotation is very simple and you dont need cos/sin for that (cos(90°)=0, sin(90°) = 1). its enough to swap component in that case.

now if you want a generic approach to that you can look into affine transformation matrixes (4-dimensional) which can deal with transformations aswell. You can then calculate a a single matrix for your composite transformation.

---

### Post by hod139 on 2008-11-20
> **elbarto_87 said:**
> Basically what I want to be able to do is this:

1)Draw a line based on a start point(x,y,z) and a end point (x,y,z)

2)The vector between these two points represents a structural element ie. a beam or such

3) The member has its own set of axis, with the local x-axis running along the length of the member.

4) I need a rotational matrix to find what the other local axis are. More specifically, I need this matrix so I can later transform any force acting in a local system (this is trivial for 1 member, but if I have 100 members obviously I want to have them defined in one set of axis) into my global co ordinates.
.

Step 4 is not correct..  A rotation matrix can be thought of two ways, 1) for rotating coordinate frames or 2) transforming a vector between frames.  It will not, however, allow you to construct a local frame.

For step 4, you have to realize that given one of the basis vectors of a reference frame, you have an infinite amount of possibilities for assigning the other 2 basis directions.  To see this, consider the local x-axis as you defined it as the normal to a plane.  You now need to find two vectors that lie in that plane and are orthogonal to each other.  This is an ill-posed question, since there are an infinite number of possibilities.

In robotics we use conventions for assigning frames, a popular one being the Devanit-Hartenberg convention. Looking back at your problem and using this convention:
Let p1 and p2 be the respective start and end points of a vector defined in the fixed coordinate frame <X,Y,Z>.  We want to attach a local frame, <U,V,W>, to this vector:
 U = normalize(p2-p1)
 V = U cross X
 W = U cross V

Note, if U is parallel with the X-axis, this method will fail, since the cross product of two parallel vectors will be (0,0,0).  For this corner case you will have to pick a different axis to cross U with.

Now, given the local coordinate frame <U,V,W>, the rotation matrix describing the rotation of this local frame in the fixed frame <X,Y,Z> is:
[U_x V_x W_x]
[U_y V_y W_y]
[U_z V_z W_z]

Hope I understood your problem and this helps

---

