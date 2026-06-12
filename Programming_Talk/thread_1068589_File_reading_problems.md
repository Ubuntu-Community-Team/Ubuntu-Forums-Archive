---
title: "File reading problems"
date: 2009-02-13
forum: Programming Talk
---

### Post by tneva82 on 2009-02-13
Ran into rather strange problem when I tried to read bit more complicated 3d model(hand-edited from blender OBJ export). Some relevant code:

```

i=getc(pFile);
//here's vertex and comment handling. Since in my file polygons appear first let's forget them
} else if(i=='p') { 	    
        fscanf(pFile,"%i",&nPolygonV);

         for(a=0; a<nPolygonV; ++a) {
	      fscanf(pFile,"%i",&b);
         } 
         for(int vertice=0;vertice<nPolygonV;vertice++) {
	      float u, v;
	      fscanf(pFile, "%f %f", &u, &v);
         }
}
*
```

What's it's supposed to do is that if first letter from line is p then we are dealing with polygon. It's then supposed to read number of vertexes and store it. Then for each vertex it's supposed to read index number of said vertex. Finally it's supposed to read U and V values.

Now here's clip of my 3d file.

p 3 1 13 4 0.65226352 0.02500000 0.65226352 0.02500000 0.78273284 0.02500000
p 3 13 9 4 0.65226352 0.02500000 0.65226352 0.02500000 0.78273284 0.02500000
p 3 9 14 3 0.65226352 0.02500000 0.65226352 0.02500000 0.78273284 0.02500000

Now the problem. For some reason vertex counts goes all haywire after which rest of the numbers go haywire as well. Printing out to text file each vertex count I got following line of numbers: 1, 13, 9, 14, 6, 16...

As you can see there's not much of a logic. I think what happens is that it skips the first vertex count and then gets royally screwed after that...

Anybody can point me where I have screwed up?

---

### Post by eye208 on 2009-02-13
The code looks OK. I think the problem is in some other part of the program.

---

### Post by tneva82 on 2009-02-13
> **eye208 said:**
> The code looks OK. I think the problem is in some other part of the program.

Where it could be? It doesn't alter polygonCount variable anywhere else(read from file, set to variable, after that it's only read) and as can be seen those are CLEARLY incorrect(correct output would have been 3 3 3 3 3 3...repeat 3 for every polygon.

Even stranger still my original 3d file does work :-/ Similar snippet from that is:

p 3 0 3 1 0.0 0.0 1.0 0.0 0.0 1.0
p 3 3 2 1 1.0 0.0 1.0 1.0 0.0 1.0

As can be seen pretty much only difference is that the UV maps are 1.0 and 0.0 instead of decimals but that's to be expected due to shape of model. I also tried changing them to long list of decimals in case some sort of buffer overrun or something but that doesn't explain it.

Pretty weird :-/

---

### Post by eye208 on 2009-02-13
I added some printf calls:
```
#include <stdio.h>

int main() {
        FILE *pFile;
        char i;
        int nPolygonV, a, b;
        pFile = fopen("data.txt", "r");
        while (!feof(pFile)) {

i=getc(pFile);
if(i=='p') {
        printf("(%d)\n", fscanf(pFile,"%i",&nPolygonV));
printf("%d\n", nPolygonV);

         for(a=0; a<nPolygonV; ++a) {
              printf("(%d)\n", fscanf(pFile,"%i",&b));
printf("%d\n", b);
         }
         for(int vertice=0;vertice<nPolygonV;vertice++) {
              float u, v;
              printf("(%d)\n", fscanf(pFile, "%f %f", &u, &v));
printf("%f %f\n", u, v);
         }
}

        }
        fclose(pFile);
}
```
Input file:
```
p 3 1 13 4 0.65226352 0.02500000 0.65226352 0.02500000 0.78273284 0.02500000
p 3 13 9 4 0.65226352 0.02500000 0.65226352 0.02500000 0.78273284 0.02500000
p 3 9 14 3 0.65226352 0.02500000 0.65226352 0.02500000 0.78273284 0.02500000
p 3 0 3 1 0.0 0.0 1.0 0.0 0.0 1.0
p 3 3 2 1 1.0 0.0 1.0 1.0 0.0 1.0
```
Output:
```
(1)
3
(1)
1
(1)
13
(1)
4
(2)
0.652264 0.025000
(2)
0.652264 0.025000
(2)
0.782733 0.025000
(1)
3
(1)
13
(1)
9
(1)
4
(2)
0.652264 0.025000
(2)
0.652264 0.025000
(2)
0.782733 0.025000
(1)
3
(1)
9
(1)
14
(1)
3
(2)
0.652264 0.025000
(2)
0.652264 0.025000
(2)
0.782733 0.025000
(1)
3
(1)
0
(1)
3
(1)
1
(2)
0.000000 0.000000
(2)
1.000000 0.000000
(2)
0.000000 1.000000
(1)
3
(1)
3
(1)
2
(1)
1
(2)
1.000000 0.000000
(2)
1.000000 1.000000
(2)
0.000000 1.000000
```
Looks OK to me. The problem must be elsewhere.

---

### Post by tneva82 on 2009-02-13
Well I printed the output to file and got the screwed up results I posted.

Also setting nPolygonV to 3 and removing vertex count from file got it working.

---

