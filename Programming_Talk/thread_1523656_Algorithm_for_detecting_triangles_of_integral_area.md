---
title: "Algorithm for detecting triangles of integral area"
date: 2010-07-04
forum: Programming Talk
---

### Post by Dara Javaherian on 2010-07-04
Hello. I'm wondering if anyone would have any ideas for a method that returns whether or not a triangle has integral area. This is the code I have(Java):

```
  
public static boolean hasIntegralArea(int a, int b, int c){
  long cosCh = ((a*a)+(b*b)-(c*c));
  long cosCl = (2*a*b);
  double cosC = (double)cosCh/(double)cosCl;
  double C = Math.acos(cosC);
  double result = (a*b*Math.sin(C))/2;
  return result%1 == 0;
}

```

However, this seems to work only on low values (I think due to a loss in precision). Can anyone push me towards a better algorithm?

---

### Post by Dara Javaherian on 2010-07-04
> **Dara Javaherian said:**
> Hello. I'm wondering if anyone would have any ideas for a method that returns whether or not a triangle has integral area. This is the code I have(Java):

```
  
public static boolean hasIntegralArea(int a, int b, int c){
  long cosCh = ((a*a)+(b*b)-(c*c));
  long cosCl = (2*a*b);
  double cosC = (double)cosCh/(double)cosCl;
  double C = Math.acos(cosC);
  double result = (a*b*Math.sin(C))/2;
  return result%1 == 0;
}

```However, this seems to work only on low values (I think due to a loss in precision). Can anyone push me towards a better algorithm?

Okay, I think I have a better solution:
```
[color=#BC7A00]#include <math.h> 
#include <stdio.h>
[/color]
[color=#408080][i]// Calculate the area of an isoceles trangle given the length of the sides.
// 'side' is the length of the two equal sides, 'difference' is the difference between the unique side and the other two sides
[/i][/color][color=#B00040]double[/color] [color=#0000FF]area[/color]([color=#B00040]int[/color] side, [color=#B00040]int[/color] difference) {
  [color=#B00040]double[/color] PI [color=#666666]=[/color] [color=#666666]3.141592653589793238462643[/color];

	[color=#408080][i]// Triangle for reference.
[/i][/color]	[color=#408080][i]//          ^
[/i][/color]	[color=#408080][i]//         /|\
	//        /B| \
	//      a/  |  \
	//      /   |c  \
	//     /    |    \
	//    /C___A|_____\
	//       b 
[/i][/color]	
	[color=#408080][i]// Figure out all the angles.
[/i][/color]  [color=#B00040]double[/color] a [color=#666666]=[/color] side, 
	  b [color=#666666]=[/color] (side[color=#666666]+[/color]difference)[color=#666666]/[/color][color=#666666]2[/color],
	  c, 
	  A [color=#666666]=[/color] PI[color=#666666]/[/color][color=#666666]2[/color],
	  B, C, 
	  sinA [color=#666666]=[/color] sin(A), 
	  sinB, sinC;

	  sinB [color=#666666]=[/color] b[color=#666666]/[/color](a[color=#666666]/[/color]sinA);
	  B [color=#666666]=[/color] sinh(sinB);
	  C [color=#666666]=[/color] PI[color=#666666]-[/color]B[color=#666666]-[/color]A;
	  sinC [color=#666666]=[/color] sin(C);
	  c [color=#666666]=[/color] sinC[color=#666666]*[/color](b[color=#666666]/[/color]sinB);
	
	[color=#008000]**return**[/color] b[color=#666666]*[/color]c;
}
[color=#B00040]int[/color] main(){
	 printf([color=#BA2121]"%f"[/color],area([color=#666666]5[/color],[color=#666666]1[/color]));
}

```
However, this gives slight inaccuracies. Can anyone help?

---

### Post by pbrane on 2010-07-04
Maybe this will work better. I'm not sure what you mean about *slight inaccuracies*. I promoted the variables to doubles. The **isIntegral** function is using the law of cosines to calculate the area of the triangle. I'm not sure if that will work on all triangles. Your second post's code is for isosceles triangles only. 

```

#include <math.h> 
#include <stdio.h>

#define SQR(a) ((a) == 0.0 ? (0.0) : ((a) * (a)))

int isIntegral(double a, double b, double c)
{
  double cosCh = SQR(a) + SQR(b) - SQR(c);
  double cosCl = (2*a*b);
  double cosC = (double)cosCh/(double)cosCl;
  double angle = acos(cosC);
  double result = (a * b * sin(angle)) / 2.0;
  return (fmod(result, 1.0) == 0.0);
}

int main(void)
{
  double sideA = 21.05;
  double sideB = 18.53;
  double sideC = 21.05;
  printf("This triangle %s integral area\n", isIntegral(sideA, sideB, sideC) ? "has" : "does not have");
	 
  return 0;
}

```

---

### Post by gmargo on 2010-07-04
You can avoid the trigonometry by using Heron's Formula.
[http://mathworld.wolfram.com/HeronsFormula.html](http://mathworld.wolfram.com/HeronsFormula.html)

---

