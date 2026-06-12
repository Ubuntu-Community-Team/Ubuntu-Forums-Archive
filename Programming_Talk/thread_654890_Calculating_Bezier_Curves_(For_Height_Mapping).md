---
title: "Calculating Bezier Curves (For Height Mapping)"
date: 2007-12-31
forum: Programming Talk
---

### Post by Lster on 2007-12-31
Hi again (sorry to be asking so much recently :()

I terrain mapping working very well. However it can, apparently, be improved by using Bezier curves when interpolating between points. I searched for this but couldn't really find anything I understood.

Can anyone explain how to calculate them and then how to apply this to the subject of a height map?

Thank you,
Lster

---

### Post by YourSurrogateGod on 2007-12-31
Height mapping? What do you mean?

Here is a wiki link that I found that could help (has formulas and such.)

[http://en.wikipedia.org/wiki/B%C3%A9zier_curve](http://en.wikipedia.org/wiki/B%C3%A9zier_curve)

---

### Post by Wybiral on 2007-12-31
You probably don't want to google for just a curve, you probably need a patch or surface. Look for NURB surfaces and patches.

For most applications, unless your height map has terrible resolution or something, you probably won't need this. The linearly interpolated height is the real height, so it will usually work when thats what you want. Using a curve could cause issues with inaccuracy (unless you curve your rendered terrain the collision will be wrong because you'll be cutting corners that actually exist).

---

### Post by DavidBell on 2007-12-31
Sorry I haven't got time to do a code example, but this is the method to calculate a bezier.

Linear Interpolation. Given two points on you terrain A, B and a point P somewhere in between you just interpolate the value based on how close it is to the two points - so if P is X fraction along line segemnt AB

```
Value(P) = Value(A) + X * (Value(B) - Value(A))
```

Bezier between two points is the same as linear, so think about three points A, C, E in your terrain that form a bit of a bump. You do linear interpolation to calculate b & d so they are half way between the segments

```
Point b = A + 0.5 (C - A)
Point d = C + 0.5 (E - C)
```

so now it is A b C d E. Take a point Q that is Y fraction along the segment bCd, then what you do is three linear interpolations

(Running out of letters)
```
Point R = b + Y * (C - b)
Point S = C + Y * (d - C)
Bezier Value(Q) = Value(R) + Y * (Value(S) - Value(R))
```

It's important to calculate the midpoints then do you bezier between the made up segments (bCd, dEf ...) or the curves don't join up properly, but in the case of a terrain model they can be calculated once at the start

Hope that makes sense. I've only used them in 2D, but 3D is just the same, you just make appropriate ACE linear and work from there.

DB

---

### Post by Lster on 2008-01-01
Thanks for all your replies. I tried Googling "NURB surfaces" but I'm quite sure what I'm looking for.

[QUOTE=DavidBell]Take a point Q that is Y fraction along the segment bCd, then what you do is three linear interpolations[/QUOTE]

Thanks for your reply. I understand everything up to this bit at which point I'm not sure what Q or Y are or represent.

---

### Post by Lster on 2008-01-01
*Bump*

---

### Post by DavidBell on 2008-01-01
It's a bit hard without doing a lot of drawings, but I'll try with fixed width font

In the linear interpolation, P is the point of interest and X is the fraction it is along the line segment AB

```

    A----P--------B
    < X > <  1-X  >

```

For bezier Q is point of interest, and Y is the fraction along segment bCd

```

    b----Q---C----d
    < Y > <  1-Y  >

```

In a terrain map segments bC and Bd would be equal distant, and in two dimensions. Q would be somewhere in the 2D plane.

```

    A    b    C    d    E



    F    g    H    i    J

    T    U Q  V

    K    l    M    n    O

```

In case above you could use linear interp of (FK, gl, HM) or bezier of (AFK, bgl, CHM) to find values of points (T, U, V). Then bezier TUV to find value at Q. 

Not sure but a NURB might be the same as bezier x bezier route. There also other goodies like Splines and higher order beziers that are better left to another day.

It all sounds complicated, but when you do it it's not so bad, it's really only two simple functions - LinearInterp() and BezierInterp() which in turn calls LinearInterp five times. When I did this to smooth GPS paths I kept putting it off for ages because it looked painful, but in the end it only took 20 mins and I was kicking myself for delaying something easy.

HTH DB

---

### Post by Wybiral on 2008-01-01
I bet it would work great for paths (such as a camera "fly-by" effect) but for entity-to-terrain collision, using a curve is going to cause issues. Primarily because you are cutting corners on the collision that aren't being cut in the rendering, so when your model is at the top of a sharp peak, her feet will most likely be underground when you curve that peak off. Unless, of course, you curved your terrain render as well, but if that's the case you could just use those height points (and you would lose the sharp "rocky" look that most terrains go for).

---

### Post by YourSurrogateGod on 2008-01-01
[http://www.robthebloke.org/opengl_programming.html](http://www.robthebloke.org/opengl_programming.html)

That has a link to an executable which has C++ code to calculate Bezier Curves (just do a search on the web-page for the word "bezier".) You can wade through the code and tease out the specific parts for the Bezier Curves.

I hope that helps.

---

### Post by DavidBell on 2008-01-01
> **Wybiral said:**
> .... but for entity-to-terrain collision, using a curve is going to cause issues....
.... you would lose the sharp "rocky" look that most terrains go for).

I don't do OpenGL so just guessing most graphics cards have surface smoothing built in. I guess what you would really need to do is find out what methods they use for that and emulate it in your own terrain functions ... or maybe there is an OpenGL function that does it for you,

I think the 'rocky look' is an artifact from the days before we all had graphics cards to smooth them for us :-)

DB

---

### Post by Wybiral on 2008-01-01
> **DavidBell said:**
> I think the 'rocky look' is an artifact from the days before we all had graphics cards to smooth them for us :-)

You don't want them to be too smooth or they become hills, not mountains/rocky martian landscapes. For some things you need the sharp edges, for everything else smooth lighting and higher sample resolutions usually do the trick.

---

### Post by Lster on 2008-01-02
**@DavidBell**:

Thank you. That clears up that bit. I still have a question, though!

[QUOTE=DavidBell]In case above you could use linear interp of (FK, gl, HM) or bezier of (AFK, bgl, CHM) to find values of points (T, U, V). Then bezier TUV to find value at Q. [/QUOTE]

In the Bezier interpolation you don't take into account E, J and O does it? Probably I could learn this quickest if you show me the formula using the function LinearInterpolation (which I already know fine) in relation to the letters below. That would be brilliant if you could, but don't worry if it's too much!

```
    A    b    C    d    E



    F    g    H    i    J

    T    U Q  V

    K    l    M    n    O
```

[QUOTE=Wybiral]I bet it would work great for paths (such as a camera "fly-by" effect) but for entity-to-terrain collision, using a curve is going to cause issues. Primarily because you are cutting corners on the collision that aren't being cut in the rendering, so when your model is at the top of a sharp peak, her feet will most likely be underground when you curve that peak off. Unless, of course, you curved your terrain render as well, but if that's the case you could just use those height points (and you would lose the sharp "rocky" look that most terrains go for). [/QUOTE]

Well my plan is to implement the choice as a global variable and then allow it to be altered my maps depending on what the developer of the map thinks best.

[QUOTE=YourSurrogateGod]That has a link to an executable which has C++ code to calculate Bezier Curves (just do a search on the web-page for the word "bezier".) You can wade through the code and tease out the specific parts for the Bezier Curves.[/QUOTE]

I'll have a look at this, thanks.

---

### Post by Lster on 2008-01-02
*Bump*

---

### Post by DavidBell on 2008-01-03
I'll try and do some example code over the weekend, can't at the moment becasue I'm doing somthing I want to be working on Monday. 

No it doesn't use EJO. 

I have to think it through, but off the top of my head two way bezier in one cell will need data from the eight surrounding cells - ie it has to be the central cell in 3 x 3 cells, or 4 x 4 vertices. So I'll try to put together  a function that takes 4 x 4 vertex array and does 2D bezier. I might find it handy one day anyway.

DB

---

### Post by Lster on 2008-01-03
That would be awesome - thank you very much! :)

---

### Post by DavidBell on 2008-01-07
Here you go. Code not tested but should be close. DB

(BTW method is not exactly the same as higher up, I made an error there)

[PHP]// General notes ================================

/*  * These compile OK, but I haven't actaully run them. Should be OK with a 
 	  bit of luck
 	 	
    * All these functions assume a nicely aligned line segment/grid of 
	  terrain points, though a little bit of misalignment wouldn't really
	  matter.
	
	* If you follow them through, these functions are not efficient, a lot of
	  points get calculated more than once etc. I wrote them just to 
	  demonstrate the methods clearly, not to break speed records, so I'll let
	  someone else optimise them (it's not hard).
	
	* Also there is only rudimentary error handling, for the same reason and
	  again I'll leave it to someone else.
	
	* To call, just call Bezier functions with your normal terrain points and
	  UseMidpoints = true

	* General Function Arguments & Varibles
		* POI = Point of Interest, POIxy must be inside STP grid in all cases
		* STP# = Surrounding Terain Point
		* MV#, BV# = Intermediate Linear & Bezier vertices
		* UseMidpoints = If set to true in Bezier functions, it calculates 
						 midpoints in the STP grid and then does the 
						 interpolation with UseMidpoints = false from there.
						 This makes the beziers join up correctly. (Beziers 
						 are bumpier than linear if you don't do this)
						 *** Note if set to true it requires POI be within 0.5 
						 'units' of centre STP point ***
	
	
	* 

*/

#define whole_lot_of_checking_fails false

struct sVertex {double x, y, z;};

double GetDistance (sVertex &V0, sVertex &V1)
	{return sqrt(pow(V1.x - V0.x, 2.0) + pow(V1.y - V0.y, 2.0));
	}
	
bool GetFraction (double &tFraction, sVertex &POI, sVertex &STP0, sVertex &STP1)
	{// Calculate fraction along STP0->STP1 line segment
	 double tDist = GetDistance(STP1, STP0);
	 if (tDist == 0.0 || whole_lot_of_checking_fails)
	 	{tFraction = 0.0;
	 	 return false;
	 	}
	 else
		{tFraction = GetDistance(POI, STP0) / tDist;
		 return (tFraction >= 0 && tFraction <= 1.0)? true: false;
		} 
	}

void GetMidVertex (sVertex &POI, sVertex &STP0, sVertex &STP1, double tFraction)
	{// Calc a vertex tFraction along STP0->STP1 line segment
	 POI.x = STP0.x + tFraction * (STP1.x - STP0.x);
	 POI.y = STP0.y + tFraction * (STP1.y - STP0.y);
	 POI.z = STP0.z + tFraction * (STP1.z - STP0.z);
	}

bool LinearInterp_1D (sVertex &POI, sVertex &STP0, sVertex &STP1)
	{// Calculate one direction Linear Interpolation
	 if (whole_lot_of_checking_fails) 
	 	return false;
	 else
	 	{// POI must be aligned and inside STP0->STP1
	 	 double fraction;
	 	 if (!GetFraction(fraction, POI, STP0, STP1)) return false;
	 	 GetMidVertex(POI, STP0, STP1, fraction);
	 	 return true;
	 	}
	}
	
bool BezierInterp_1D (sVertex &POI, sVertex &STP0, sVertex &STP1, sVertex &STP2, bool UseMidpoints)
	{// Calculate one direction Bezier Interpolation
	 if (whole_lot_of_checking_fails) 
	 	return false;
	 else if (UseMidpoints)
	 	{// POI must be aligned with STP0->STP2 and within 0.5 units of STP1
	 	 sVertex MV01, MV12;
	 	 GetMidVertex(MV01, STP0, STP1, 0.5);
	 	 GetMidVertex(MV12, STP1, STP2, 0.5);
	 	 return BezierInterp_1D(POI, MV01, STP1, MV12, false);
	 	}
	 else
	 	{// POI must be aligned and inside STP0->STP2
	 	 double fraction;
	 	 if (!GetFraction(fraction, POI, STP0, STP2)) return false;
	 	 sVertex BV01, BV12;
		 GetMidVertex(BV01, STP0, STP1, fraction);
		 GetMidVertex(BV12, STP1, STP2, fraction);
		 GetMidVertex(POI, BV01, BV12, fraction);
		 return true;
	 	}
	}

	 
bool LinearInterp_2D (sVertex &POI, sVertex &STP00, sVertex &STP10,
									sVertex &STP01, sVertex &STP11)
	{// Calculate two direction Linear Interpolation
	 if (whole_lot_of_checking_fails) 
	 	return false;
	 else
	 	{// POI must be inside STP00->STP11 grid, STP grid should be aligned
	 	 sVertex MV0010 = POI; 
	 	 MV0010.y = STP00.y;
	 	 if (!LinearInterp_1D(MV0010, STP00, STP10)) return false;
	 	 
	 	 sVertex MV0111 = POI; 
	 	 MV0111.y = STP11.y;
	 	 if (!LinearInterp_1D(MV0111, STP01, STP11)) return false;
	 	 
	 	 return LinearInterp_1D(POI, MV0010, MV0111);
	 	}
 	 return true;
 	}

bool BezierInterp_2D (sVertex &POI, sVertex &STP00, sVertex &STP10, sVertex &STP20,
									sVertex &STP01, sVertex &STP11, sVertex &STP21,
									sVertex &STP02, sVertex &STP12, sVertex &STP22,
									bool UseMidpoints)
	{// Calculate two direction Bezier Interpolation
	 if (whole_lot_of_checking_fails) 
	 	return false;
	 else if (UseMidpoints)
	 	{// POI must be within 0.5 unit from STP11, STP grid should be aligned
	 	 sVertex MV00, MV10, MV20, 
	 			 MV01, MV11, MV21,
	 			 MV02, MV12, MV22;
	 			 
	 	 GetMidVertex(MV00, STP00, STP11, 0.5);
	 	 GetMidVertex(MV10, STP10, STP11, 0.5);
	 	 GetMidVertex(MV20, STP20, STP11, 0.5);
	 	 
	 	 GetMidVertex(MV01, STP01, STP11, 0.5);
	 	 GetMidVertex(MV11, STP11, STP11, 0.5); // = STP11
	 	 GetMidVertex(MV21, STP21, STP11, 0.5);

	 	 GetMidVertex(MV02, STP02, STP11, 0.5);
	 	 GetMidVertex(MV12, STP12, STP11, 0.5);
	 	 GetMidVertex(MV22, STP22, STP11, 0.5);

	 	 return BezierInterp_2D(POI, MV00, MV10, MV20,
	 	 							 MV01, MV11, MV21,
	 	 							 MV02, MV12, MV22, false);
		}	 	
	 else
	 	{// POI must be within STP00->STP22 grid, STP grid should be aligned
	 	 sVertex MV001020 = POI; 
	 	 MV001020.y = STP10.y;
 		 if (!BezierInterp_1D(MV001020, STP00, STP10, STP20, false)) return false;
 		 
	 	 sVertex MV011121 = POI; 
	 	 MV011121.y = STP11.y;
	 	 if (!BezierInterp_1D(MV011121, STP01, STP11, STP21, false)) return false;
	 	 
	 	 sVertex MV021222 = POI; 
	 	 MV021222.y = STP12.y;
	 	 if (!BezierInterp_1D(MV021222, STP02, STP12, STP22, false)) return false;
	 	 
	 	 return BezierInterp_1D(POI, MV001020, MV011121, MV021222, false);
	 	}
	}
[/PHP]

---

### Post by Lster on 2008-01-07
Thank you very very much indeed, DavidBell. You rock. :-D I must go to sleep now but I will be sure to post how everything goes tomorrow.

---

