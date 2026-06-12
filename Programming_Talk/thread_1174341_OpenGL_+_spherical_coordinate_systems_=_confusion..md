---
title: "OpenGL + spherical coordinate systems = confusion."
date: 2009-05-30
forum: Programming Talk
---

### Post by Bulletbeast on 2009-05-30
[http://en.wikipedia.org/wiki/Equatorial_coordinate_system](http://en.wikipedia.org/wiki/Equatorial_coordinate_system)
[http://en.wikipedia.org/wiki/Galactic_coordinate_system](http://en.wikipedia.org/wiki/Galactic_coordinate_system)
[http://en.wikipedia.org/wiki/Supergalactic_coordinate_system](http://en.wikipedia.org/wiki/Supergalactic_coordinate_system)

I've been trying to do this for a while. The program that I am writing is a deep sky astronomy model, and I want it to make use of those three coordinate systems. By "make use" I mean having one of their equatorial planes drawn at any given time, as shown in the screenshot, smoothly switching between them, and the lines starting from the galaxies always falling perpendicularly to the active plane.

[[IMG]http://img195.imageshack.us/img195/5117/screenshotc.th.png[/IMG]](http://img195.imageshack.us/my.php?image=screenshotc.png)
(sorry for windows taskbar, that's all I've got at the moment)

I might be able to do the lines thing with surface normals, but I just can't seem to make the planes work like they should. I've calculated a rotation matrix for the Galactic coordinate system, but I'm still not getting anywhere. Please, help me, and don't send me to high school or to a matrix tutorial. I just need some specific advice on mapping one coordinate system to another...

---

### Post by Victor Liu on 2009-05-31
If you have the normal vector for each plane then by continuously varying the normal vector from one to another you will sweep the plane from one to another (if the normal vectors differ in angle by more than Pi/4, negate one of them). For each intermediate plane, you can then project each star/planet onto the plane (obtain the point's 2D coordinates in the plane), then draw the new vertical line. Assuming you have normal vectors v0 and v1 for the old equatorial plane and the new equatorial plane, then you will want to some kind of spherical interpolation from one to another:

[http://en.wikipedia.org/wiki/Slerp](http://en.wikipedia.org/wiki/Slerp)

Thus obtaining a vector v such that v0 <= v <= v1 (where inequality is in the slerp sense). Assuming you're rotating the plane about the origin, then the new "in-plane projections" of each star (located at position r) is (r - v.r/v.v) where a period is the dot product. Given these points, you can connect them to the star locations to draw the vertical lines. Just do this at each intermediate sweep plane.

---

### Post by Bulletbeast on 2009-05-31
Thanks, that will prove useful. However, it doesn't answer my main problem. The equatorial coordinate system is my base system, with north pole at (ra=0,dec=90) and zero point at (ra=0,dec=0). I have the north poles and zero points of two other coordinate systems given as such ra/dec pairs (see wikipedia articles), but since consequential rotations in OpenGL rotate the coordinate axes, I'm not sure whether I'll get the expected outcome. And that's where I need most help. When the user picks another coordinate system, a very same plane (only of a different colour) fades in as the galaxies turn around.

To put it as simple as it gets, when the selected coordinate system is equatorial, I want a (hypothetical) object with ra=0,dec=90,distance=1 to be at (0,1,0), and an object with ra=0,dec=0,distance=1 to be at (0,0,1). When the coordinate system is galactic, I want an object with ra=192,8595083 deg, dec=27,1283361 deg to be at (0,1,0), and one with ra=266,4051,dec=-28,9361749 at (0,0,1). And when the coordinate system is supergalactic, I want the objects with ra=283.5 dec=15.7 and ra=42,3 dec=59,5 at those same two positions. It's easiest to understand putting it that way, I guess, but I'm currently out of thought power.

I've obtained a rotation matrix for one system (I made OpenGL follow the instructions in [one article](http://seds.org/~spider/spider/ScholarX/coords.html#galactic), which said that, to convert to galactic coordinates, one rotates 282.25 degrees around the axis, then 62.9 degrees around the node, then 33 degrees around the new axis, then I glGot the modelview matrix) but I'm not quite sure what to do with it.

---

### Post by Victor Liu on 2009-05-31
Ugh, this brings back bad memories of intro astronomy, with your silly right ascension/declination nonsense :).

Ok, it seems I misunderstood you initially; it seems you want the equatorial plane to always sit at the same place when you change coordinate systems, but you want the galaxies to move around. Is that correct?

If that is the case, then you need to generate the rotation matrix for each transformation between the ECS and whichever final coordinate system you want to transition to. Once you have this matrix, you should just do a glMatrixMult to apply the matrix to the current modelview matrix (you don't need to use glGet, since you don't need to know the current absolute modelview matrix).

Since you have the rotation matrices from ECS to the other two, you already in principle have all the information necessary to map from any one coordinate system to any other. Whether you have them correct is another matter. I suggest to begin with that you start with rendering everything in the ECS, then use Slerp to generate a rotation matrix that is very slightly rotated towards one of the other coordinate systems. The matrix you generated should be nearly the identity matrix (check this). If this seems okay, then apply it to your rendering (so do a glMatrixMult right before you render the galaxies, etc.) and allow yourself keyboard control to toggle between applying the matrix and not applying it to visually inspect if the results "make sense". If all is still well, then implement the full blown rotations. If at any point you messed up the matrices, you will in all likelihood see nothing on screen :).

Now, to answer your question of how to draw those vertical lines. Using the transformation matrices you can easily find the vector directions corresponding to (ra=0, d=90). You then have the 'v' vector I described below. It just transforms in the same way as all the galaxies so whatever rotation/transformation you applied to smoothly transition coordinate systems can be applied to the north-pole-vector as well.

---

### Post by Bulletbeast on 2009-05-31
That's cool. I'm getting your point, but generating the matrices is what's stopping me. I could try calculating the coordinates of zero points/north poles from ra/dec at a distance of 1, and putting those in a matrix...

---

### Post by Victor Liu on 2009-05-31
Generating the matrices should be pretty simple since (ra,dec) values correspond roughly to spherical coordinates, so you can get the Cartesian coordinates of the basis vectors directly. With the basis vectors in hand, all you have to do is arrange them into the matrix to obtain the transformation matrix. I will attempt to describe the process here.

For this I will assume that you are in the ECS, trying to transform into the GCS and currently ECS(ra=0,d=90) corresponds to OpenGl-space (0,0,1). Exactly what the starting point is does not matter since these rotation matrices are relative to the starting configuration.

Here are some notes for myself while I work this out:
```

In ECS:
\hat{z} = (ra=0,d=0)
\hat{y} = (ra=0,d=90)
\hat{x} = (ra=90,d=0)
z = cos(ra)cos(d)
y = cos(ra)sin(d)
x = sin(ra)cos(d)

ECS -> GCS matrix:
[ Cx  sin(ra_y)cos(d_y)  sin(ra_z)cos(d_z)   0  ]
[ Cy  cos(ra_y)sin(d_y)  cos(ra_z)sin(d_z)   0  ]
[ Cz  cos(ra_y)cos(d_y)  cos(ra_y)cos(d_y)   0  ]
[  0         0                0              1  ]
where (Cx,Cy,Cz) is the second crossed with the third column),
and ra_*,d_* are the current interpolated (ra,d) of the basis vector in the * direction.

```

Initially in ECS, (ra_y_0=0,d_y_0=90) and (ra_z_0=0,d_z_0=0). We need to interpolate them into (ra_y_1=193,d_y_1=27) and (ra_z_1=266,d_z_1=-29) to be in GCS. We can just use linear interpolation during the transition to generate the angles:

Suppose during the transition we maintain a parameter t, such that t = 0 initially, and t = 1 at the end of the transition, then we generate
```

ra_y = (1-t)*ra_y_0 + t*ra_y_1

```
and similarly for d_y, ra_z, and d_z.
We then plug these numbers into the matrix formula above (generate the second and third columns first, then cross them to fill in the first column).

To render, set up everything as if you were going to render in the ECS. Right before submitting geometry information to OpenGL, do a glMatrixMult() with the matrix just calculated.

The procedure for going from ECS to SCS is generated similarly. To go between GCS and SCS you could compute both transformations from ECS and invert one, or you could work out all the numbers separately (the formulas in the matrix will be much uglier).

I have absolutely no idea if any of that was correct or makes any sense. When I try these things I usually mess up and get the inverse rotation instead. ALso, OpenGL might need a matrix transpose depending on how you set things up; I can never remember. Hope this helps, and good luck with the geometry.

---

### Post by Bulletbeast on 2009-06-01
Well, I generated my axes in the same way that I calculate Cartesian positions for my objects:

x=cos(ra)*cos(d);
y=sin(d)
z=sin(ra)*cos(d);

And the matrix that this generated for the GCS was close to the result from the rotations in one of the articles above, so I guess I've gotten it correct. However, is there a way to decompose a matrix into three discreet rotations, one in X, one in Y, and one in Z? If that was possible, I could just do it with the source that I already have and not have to implement anything new at all.

---

### Post by Victor Liu on 2009-06-01
Oh yeah, I messed up the equation for the y-component...

You can always separate out a matrix into 3 discrete rotations, but then the order in which you apply them matters (in particular, the order of application determines what the decomposition is). If all you're looking for is to convert the rotation matrix into an angle about an axis, then the Wikipedia page on rotation matrices describes how you might go about it.

If you really do want to get 3 separate rotations, you can get Euler angles out of the matrix, and then figure out how to apply them. There are plenty of pages online about converting matrices to Euler angles and using them.

---

### Post by Bulletbeast on 2009-06-01
[http:/www.j3d.org/matrix_faq/matrfaq_latest.html#Q37](http:/www.j3d.org/matrix_faq/matrfaq_latest.html#Q37)
[http:/www.j3d.org/matrix_faq/matrfaq_latest.html#Q36](http:/www.j3d.org/matrix_faq/matrfaq_latest.html#Q36)

Yeah, now I think I've finally gotten some insight on how to solve my and you have been most helpful. Thank you (:
What I'm going to do is pre-calculate Euler angles for the coordinate systems from the two matrices that I've calculated, store those in the structs that hold the info for the coordinate systems, then generate a matrix from the gradually changing angles for every frame (if plane_turned<1.0f) and apply it with glMultMatrix.

And the Euler angles have arrived!
Galactic: 167.223 297.267 275.561
Supergalactic: 69.953 12.9874 343.877
Let's just hope that they are correct...

---

### Post by NielsBhor on 2009-06-01
I am learning OpenGL. After reading up on the matrix transformation, I'd love to you see what you've done in action when you get it working. Quite interesting BulletBeast. If you wish not to let anyone see the source, then compile it and post it if possible. That is if you don't mind posting it. I learned alot about ECS, GCS, and SCS.

---

### Post by Bulletbeast on 2009-06-01
I'd be glad if you learned anything from my source; however, that's quite an uncertain affair, as my code would probably seem too messy to you. It all started as a 6 hour project based on one of NeHe's tutorials, the one with a spiral of stars (that's why I'm coding it for Windows; until recently, however, I worked on it exclusively through on Wine -- much better support than a virtual machine!). And once I start out something sloppily, it remains like this until it's finished. If you still want me to, though, I'll whip up a package in the near future.

Anyway, I've been quite excited about the whole Euler angle thing, forgetting that the original idea was not to implement anything new but instead spend time on something more productive (such as writing lengthy posts in forums). So, before getting down to matrix multiplication and inverse matrices stuff (things that I've tried to avoid to this point -- which would probably greatly reduce my source code's educational value :D)... how would I decompose the matrix into three angles, if I always apply the transformations in the order x,y,z, and, when needed, -z,-y,-x?

EDIT: Here's something that I'll try: [http://www.robertblum.com/articles/2005/02/14/decomposing-matrices](http://www.robertblum.com/articles/2005/02/14/decomposing-matrices)

And the result's apparently the same as what I got from the Euler angle calculations, only the values don't get above 180 deg, and some are negative. I'm confused. And an object with ra,dec as in the Galactic North Pole doesn't even get close to the position that it should take. I guess I'll go for Euler angles. After dinner.

---

### Post by Bulletbeast on 2009-06-03
Update.

I just found out that I weren't turning degrees to radians in the function that computed my Cartesian coordinates.
And, I was applying rotations in z,y,x<->-x,-y,-z order.

More to follow.

---

### Post by Bulletbeast on 2009-06-10
I can't, I can't, I can't bloody do it. Please help me, please. I have coordinates for the north pole (direction of Z axis), and coordinates for the point where both spherical coordinates are 0 (direction of Y axis) but I can't make the axes point that way... I tried this code:

```
void Vcross_3f(float *p, float* v, float *u)
{
  p[0]=v[1]*u[2]-v[2]*u[1];
  p[1]=-(v[0]*u[2]-v[2]*u[0]);
  p[2]=(v[0]*u[1]-v[1]*u[0]);
  return;
}

void RaDectoM_3f(float* m, float A, float nR, float nD, float zR, float zD)
{
  static float vecz[3], vecy[3], vecx[3];
  
  float ra=nR*A;
  float dec=90-(90-nD)*A;
  
  vecy[0]=cos(ra*PI/180)*sin(dec*PI/180);
  vecy[1]=sin(ra*PI/180)*sin(dec*PI/180);
  vecy[2]=cos(dec*PI/180);
  
  ra=90-zR*A;
  dec=90-(90-zD)*A;
  
  vecz[1]=cos(ra*PI/180)*sin(dec*PI/180);
  vecz[1]=sin(ra*PI/180)*sin(dec*PI/180);
  vecz[2]=cos(dec*PI/180);
  
  Vcross_3f(vecx,vecy,vecz);
  
  m[0]=vecx[0]; m[1]=vecx[1]; m[2]=vecx[2];
  m[3]=vecy[0]; m[4]=vecy[1]; m[5]=vecy[2];
  m[6]=vecz[0]; m[7]=vecz[1]; m[8]=vecz[2];
  
  return;
}
```

I turned m into an OpenGL matrix, and multiplied it in, but it only resulted in distorting my projection and it even messed up blending. Please, help me...

---

### Post by Victor Liu on 2009-06-10
Could you perhaps post the entire set of source code somewhere so that we can compile it and see what's going on? It's fine if you can't, but it makes this a lot harder.

---

### Post by Bulletbeast on 2009-06-11
Well, I just need a function to create a matrix out of the spherical coordinates of two points... Or, a way to decompose those matrices that I generated back then to a set of rotations in an arbitrary order, that would work...

```
#include <iostream>
#include <iomanip>
#include <cstdio>
#include <cmath>

#define PI M_PI

using namespace std;

void Vcross_3f(float *p, float *v, float *u)
{
  p[0]=v[1]*u[2]-v[2]*u[1];
  p[1]=-(v[0]*u[2]-v[2]*u[0]);
  p[2]=(v[0]*u[1]-v[1]*u[0]);
  return;
}

int main()
{
  float gnp_ra, gzp_ra, snp_ra, szp_ra;
  float gnp_dec, gzp_dec, snp_dec, szp_dec;
  
  float vecz[3], vecy[3], vecx[3]; // z is up and y is out
  
  gnp_ra=15*(12+51/60+26.2/3600);
  gnp_dec=27+7/60+42/3600;
  
  gzp_ra=15*(17+45/60+37.2/3600);
  gzp_dec=-(28+56/60+10.2/3600);
  
  cout << cos(0) << endl;
  
  for (float a=0.0f; a<=1.1f; a+=0.05f)
  {
    float ra=gnp_ra*a;
    float dec=90-(90-gnp_dec)*a;
    
    vecz[0]=cos(ra*PI/180)*sin(dec*PI/180);
    vecz[1]=sin(ra*PI/180)*sin(dec*PI/180);
    vecz[2]=cos(dec*PI/180);
    
    ra=90-gzp_ra*a;
    dec=90-(90-gzp_dec)*a;
    
    vecy[0]=cos(ra*PI/180)*sin(dec*PI/180);
    vecy[1]=sin(ra*PI/180)*sin(dec*PI/180);
    vecy[2]=cos(dec*PI/180);
    
    Vcross_3f(vecx,vecy,vecz);
    
    cout << fixed << a << ": " << endl <<
         vecx[0] << " " << vecx[1] << " " << vecx[2] << endl <<
         vecy[0] << " " << vecy[1] << " " << vecy[2] << endl <<
         vecz[0] << " " << vecz[1] << " " << vecz[2] << endl << endl;
  }

  system("pause");
  return 0;
}
```

This is calculate_radec_to_matrix.cpp, a test program which outputs:

```
1
0.000000:
0.000000 0.000000 -1.000000
0.000000 1.000000 0.000000
1.000000 0.000000 0.000000

0.050000:
0.037244 0.089304 -0.922408
0.219660 0.970146 0.102795
0.986181 0.156292 0.054950

0.100000:
0.034089 0.147036 -0.705448
0.421652 0.883396 0.204501
0.945255 0.307331 0.109734

0.150000:
-0.013439 0.170302 -0.392837
0.590089 0.747900 0.304040
0.878787 0.448081 0.164187

0.200000:
-0.104062 0.160591 -0.045980
0.712456 0.576298 0.400358
0.789315 0.573930 0.218143

0.250000:
-0.230944 0.123016 0.270175
0.780853 0.384418 0.492434
0.680234 0.680883 0.271440

0.300000:
-0.382146 0.065103 0.501647
0.792752 0.189642 0.579293
0.555657 0.765717 0.323917

0.350000:
-0.541824 -0.004651 0.616742
0.751197 0.009122 0.660015
0.420233 0.826116 0.375416

0.400000:
-0.692025 -0.078221 0.611513
0.664426 -0.141980 0.733743
0.278951 0.860754 0.425779

0.450000:
-0.814891 -0.149270 0.508255
0.544945 -0.252028 0.799698
0.136927 0.869346 0.474856

0.500000:
-0.894970 -0.213962 0.347763
0.408166 -0.314075 0.857180
-0.000812 0.852640 0.522499

0.550000:
-0.921323 -0.271247 0.177651
0.270748 -0.326527 0.905580
-0.129541 0.812377 0.568562

0.600000:
-0.889154 -0.322612 0.039937
0.148814 -0.293239 0.944386
-0.245030 0.751202 0.612907

0.650000:
-0.800683 -0.371359 -0.038849
0.056228 -0.223040 0.973186
-0.343724 0.672536 0.655400

0.700000:
-0.665161 -0.421534 -0.052619
0.003127 -0.128723 0.991676
-0.422879 0.580413 0.695913

0.750000:
-0.497953 -0.476723 -0.014787
-0.005152 -0.025627 0.999658
-0.480670 0.479298 0.734323

0.800000:
-0.318800 -0.538907 0.047896
0.031372 0.070055 0.997050
-0.516257 0.373882 0.770513

0.850000:
-0.149464 -0.607599 0.104649
0.107336 0.143053 0.983877
-0.529802 0.268867 0.804376

0.900000:
-0.011027 -0.679400 0.130288
0.212620 0.180701 0.960281
-0.522442 0.168762 0.835807

0.950000:
0.078788 -0.748088 0.112411
0.333442 0.174339 0.926511
-0.496223 0.077673 0.864714

1.000000:
0.107945 -0.805217 0.054219
0.453844 0.120292 0.882924
-0.453990 -0.000865 0.891007

1.050000:
0.071743 -0.841180 -0.027593
0.557418 0.020315 0.829983
-0.399238 -0.064052 0.914607

1.100000:
-0.026422 -0.846560 -0.108977
0.629082 -0.118531 0.768249
-0.335945 -0.109934 0.935444
```

The question is, why can't I use those values for a matrix.

Or, let's start slowly, if I have a point with arbitrary X, Y, Z coordinates, how do I rotate it so that it falls on the Z axis? Then I could just rotate around that...

---

### Post by Victor Liu on 2009-06-11
Here is a rough outline of a function to do what you want. You need to supply a matrix inversion routine and some other bits. I have not tried it, obviously, but the general idea is there. Keep in mind that OpenGL might need the transpose of the matrix that you compute, since the row/column-major-ness of your matrices depends on how you use them.

```

// Given (x,y,z) coordinates
// Output: (0,0,z1) such that z1 = sign(z) * sqrt(x^2 + y^2 + z^2)
void RotateToZ(float xyz[3], float *m){ // m is the rotation matrix
	float axis[3];
	if(xyz[2] == 0){ // degenerate projection
		// axis is (x,y,z) cross (0,0,1)
		axis[0] = xyz[1];
		axis[1] = -xyz[0];
		axis[2] = 0;
	}else{
		// (0,0,z) is the projection onto z axis
		// axis of rotation is: (x,y,z) cross (0,0,z)
		axis[0] =  xyz[1]*xyz[2];
		axis[1] = -xyz[0]*xyz[2];
		axis[2] = 0;
	}
	// normalize the rotation axis
	float axis_inv_norm = 1.f/sqrt(axis[0]*axis[0] + axis[1] * axis[1]);
	axis[0] *= axis_inv_norm;
	axis[1] *= axis_inv_norm;

	// make the last orthogonal basis vector
	float b[3]; // b = (x,y,z) cross axis
	b[0] = xyz[0]*axis[2] - xyz[2]*axis[0];
	b[1] = ...
	b[2] = ...
	// normalize both xyz and b
	float xyz_normalized[3] = // copy xyz
	// normalize xyz_normalized
	// normalize b
	
	// The inverse of the rotation matrix is:
	// [axis   b   xyz_normalized]
	m[0] = axis[0]; m[1] = b[0]; m[2] = xyz_normalized[0];
	m[3] = axis[1]; m[4] = b[1]; m[5] = xyz_normalized[1];
	m[6] = axis[2]; m[7] = b[2]; m[8] = xyz_normalized[2];
	
	// the rotation matrix is the inverse of this
	invert_matrix(m);
}

```

---

### Post by Victor Liu on 2009-06-11
In regards to the code you posted above, what exactly is it supposed to do? If it's supposed to print out the set of transformation matrices for a smooth transition, then the first matrix is obviously wrong, since it's not the identity matrix. It seems the first and last columns/rows are flipped. Maybe swapping them might producing something intelligible.

Some more comments about what the variables like gzp_* are would be helpful, but ultimately, I can't visualize the problem without the entire app's code, working or not.

---

### Post by Bulletbeast on 2009-06-26
Thought I should share this.

With Z pointing upwards, and Y into the screen (or maybe out of it):
**Rotation 1: ***alphaN* (north pole right ascension) or alpha-360 degrees around Z.
**Rotation 2:** *90-deltaN* (north pole declination) around Y.
Those get the pole in place. And then, for the zero meridian:
**Rotation 3:** *gamma* degrees around Z again.

Where *gamma* is obtained by solving the spherical triangle formed by the north pole, the zero point after rotations 1&2, and the final desired zero point. Here's the resulting equation:
***gamma*** := arccos( cos(180-deltaN)*cos(90-deltaZ) + sin(180-deltaN)*sin(90-deltaZ)*cos(alphaN-alphaZ));

Of course, to do what I need to do, the rotations are performed in reverse order, with inverted values.

Next: making the lines reach out to the plane (and no further).

---

