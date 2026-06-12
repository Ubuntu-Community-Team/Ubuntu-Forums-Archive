---
title: "openGL, vertex arrays, graphic cards memory and crashes"
date: 2009-04-09
forum: Programming Talk
---

### Post by tneva82 on 2009-04-09
In process of optimising graphic engine I have began 3-stage process. 1) turn drawing use vertex arrays instead of glBegin/glEnd pairs 2) put arrays into memory of graphic card if possible(ie there's room for it) and 3) limit area drawn.

Stage 1 is working allright. Stage 2 is on the way. I have got it to memory and can use it(I think. Atleast it's drawing it correctly! I could be wrong and it still sends arrays into graphic cards memory every frame...). Problem comes when I try to simulate graphic cards memory running out. Basicly what I do is that after I have created the arrays I put boolean buffered to true. Then I try to create and fill graphic cards memory with glGenBuffer/glBindBuffer/glBufferData calls. If these fails boolean is set to false.

In drawing if boolean is true then I use(or atleast try to. Depends did I figure that one correctly) data in memory. If not I send data old fashioned way.

The PROBLEM is that if I, after allocating buffers, set bool to false(as if it had ran out of memory and returned GL_OUT_OF_MEMORY error message) program crashes when trying to draw it old fashioned way. Specifically it crashes here:

```

    glDrawElements(GL_TRIANGLES, polygonCount*3, GL_UNSIGNED_BYTE, indexArray);

```

However if I simply comment the buffer creation calls old-fashioned method works fine.

Question: Does the glGenBuffer/glBindBuffer/glBufferData calls alter the original data so that after call the array is NULL or something? Here's how I allocate the vertex buffer for example:

```

   glGenBuffers(1, &vertexBuffer);
   glBindBuffer(GL_ARRAY_BUFFER, vertexBuffer);
   glBufferData(GL_ARRAY_BUFFER, sizeof(float)*polygonCount*3*3, vertexArray, GL_STREAM_DRAW);
   if(glGetError()==GL_OUT_OF_MEMORY) {
    buffered=false;
   }

```

Could be doing something wrong anyway. Only started to study this thing ~1.5h ago so haven't had time to study it yet that much.

---

### Post by tneva82 on 2009-04-09
Crash issue has gone away but now that I'm trying to get objects(which unlike terrain has animation and therefore I need separate data for each frame) doesn't work which is pretty weird since terrain works just fine.

```

#ifndef OBJECT3D
#define OBJECT3D
#include <vector>
#include "ownmath.h"
#include "characterstatus.h"

using namespace std;

struct polygon3d {
  int uvIndex[3];
  int vertexes[3];
};

struct frame {
  vertex *vertexTable; // x, y, z
  normalVector *normalTable; // x, y, z
  int *normalIndexes;
  int normalCount;

  vertexComplete *vertexes; // x, y, z, nx, ny, nz, u, v
  float *vertexArray;
  float *normalArray;
  float *uvArray;
};

class object3d {
private:
  char *name;
  int polygonCount, vertexCount, uvCount, frameCount;
  frame *myFrames;
  polygon3d *myPolygons;
  float *uMapTable;
  float *vMapTable; 
  bool loop[STATUS_COUNT];
  int minFrame[STATUS_COUNT];
  int maxFrame[STATUS_COUNT];

  GLushort *indexArray;
  GLuint vertexBuffer;
  GLuint uvBuffer;
  GLuint normalBuffer;
  bool buffered;
public:
  object3d(const char *fileName);
  object3d(const object3d &orig);
  object3d() { }
  ~object3d();
  float draw(float frame, int status, float FPSModifier);
  int statusChange(int newStatus);
};

#endif
```

Note that all *Table's, normalIndexes and polygons are now essentially placeholders before I convert data from them to those Array arrays. I'll change it to create those straight up from file once I get this thing working but for now those remain.

Here's how I fill those arrays.

```

    indexArray=new GLushort[polygonCount*3];
    for(int i=0;i<frameCount;i++) {
      myFrames[i].uvArray=new float[polygonCount*3*2];
      myFrames[i].vertexArray=new float[polygonCount*3*3];
      myFrames[i].normalArray=new float[polygonCount*3*3];
      myFrames[i].vertexes=new vertexComplete[polygonCount*3];
    }  

    
    for(int f=0;f<frameCount; f++) {
      for(int i=0;i<polygonCount;i++) {
	for(int j=0;j<3;j++) {
	  myFrames[f].vertexes[i*3+j].x=myFrames[f].vertexTable[myPolygons[i].vertexes[j]].x;
	  myFrames[f].vertexes[i*3+j].y=myFrames[f].vertexTable[myPolygons[i].vertexes[j]].y;
	  myFrames[f].vertexes[i*3+j].z=myFrames[f].vertexTable[myPolygons[i].vertexes[j]].z;

	  myFrames[f].vertexes[i*3+j].nx=myFrames[f].normalTable[myFrames[f].normalIndexes[i]].x;
	  myFrames[f].vertexes[i*3+j].ny=myFrames[f].normalTable[myFrames[f].normalIndexes[i]].y;
	  myFrames[f].vertexes[i*3+j].nz=myFrames[f].normalTable[myFrames[f].normalIndexes[i]].z;

	  myFrames[f].vertexes[i*3+j].u=uMapTable[myPolygons[i].uvIndex[j]];
	  myFrames[f].vertexes[i*3+j].v=vMapTable[myPolygons[i].uvIndex[j]];
	}
      }


    }

    for(int f=0;f<frameCount;f++) {
      for(int i=0;i<polygonCount;i++) {
	for(int j=0;j<3;j++) {
	  myFrames[f].vertexArray[i*9+j*3+0]=myFrames[f].vertexes[i*3+j].x;
	  myFrames[f].vertexArray[i*9+j*3+1]=myFrames[f].vertexes[i*3+j].y;
	  myFrames[f].vertexArray[i*9+j*3+2]=myFrames[f].vertexes[i*3+j].z;
	  myFrames[f].uvArray[i*6+j*2+0]=myFrames[f].vertexes[i*3+j].u;
	  myFrames[f].uvArray[i*6+j*2+1]=myFrames[f].vertexes[i*3+j].v;
	  myFrames[f].normalArray[i*9+j*3+0]=myFrames[f].vertexes[i*3+j].nx;
	  myFrames[f].normalArray[i*9+j*3+1]=myFrames[f].vertexes[i*3+j].ny;
	  myFrames[f].normalArray[i*9+j*3+2]=myFrames[f].vertexes[i*3+j].nz;
	}
      }
  
    }
    for(int i=0;i<polygonCount;i++) {
      for(int j=0;j<3;j++) {
	indexArray[i*3+j]=i*3+j;  
	
      }
    }

```

Note that the data before turning to arrays gives quite working model so it's pretty safe to say loading from file works fine. Problems start when I try to draw it with arrays like this:

```

float object3d::draw(float frame, int status, float FPSModifier) {
  int a,b;
  int drawnFrame=ceil(frame);

  glEnableClientState(GL_VERTEX_ARRAY);
  glEnableClientState(GL_TEXTURE_COORD_ARRAY);
  //glEnableClientState(GL_NORMAL_ARRAY);

  glVertexPointer(3, GL_FLOAT, 0, myFrames[drawnFrame].vertexArray);
  glTexCoordPointer(2, GL_FLOAT, 0, myFrames[drawnFrame].uvArray);
  //glNormalPointer(GL_FLOAT, 0, myFrames[drawnFrame].normalArray);

  glDrawElements(GL_TRIANGLES, polygonCount*3, GL_UNSIGNED_SHORT, indexArray);

  glDisableClientState(GL_VERTEX_ARRAY);
  glDisableClientState(GL_TEXTURE_COORD_ARRAY);

```

However apart from glXXXPointer pointing to array inside struct nothing changes here so I don't think the problem lies here.

Now for comparison how I create arrays for terrain which does work:

```


   indexArray=new GLushort[polygonCount*3];
   uvArray=new float[polygonCount*3*2];
   vertexArray=new float[polygonCount*3*3];
   normalArray=new float[polygonCount*3*3];

   vertexes=new vertexComplete[polygonCount*3];

   for(int i=0;i<polygonCount;i++) {
    for(int j=0;j<3;j++) {
      vertexes[i*3+j].x=vertexTable[polygons[i].vertexes[j]].x;
      vertexes[i*3+j].y=vertexTable[polygons[i].vertexes[j]].y;
      vertexes[i*3+j].z=vertexTable[polygons[i].vertexes[j]].z;
      vertexes[i*3+j].nx=normalTable[polygons[i].normalIndex].x;
      vertexes[i*3+j].ny=normalTable[polygons[i].normalIndex].y;
      vertexes[i*3+j].nz=normalTable[polygons[i].normalIndex].z;
      vertexes[i*3+j].u=uMapTable[polygons[i].uvIndex[j]];
      vertexes[i*3+j].v=vMapTable[polygons[i].uvIndex[j]];
    }
   }
   delete[] polygons;
   delete[] vertexTable;
   delete[] normalTable;
   delete[] uMapTable;
   delete[] vMapTable; 

   for(int i=0;i<polygonCount;i++) {
    for(int j=0;j<3;j++) {

      vertexArray[i*9+j*3+0]=vertexes[i*3+j].x;
      vertexArray[i*9+j*3+1]=vertexes[i*3+j].y;
      vertexArray[i*9+j*3+2]=vertexes[i*3+j].z;
      uvArray[i*6+j*2+0]=vertexes[i*3+j].u;
      uvArray[i*6+j*2+1]=vertexes[i*3+j].v;
      normalArray[i*9+j*3+0]=vertexes[i*3+j].nx;
      normalArray[i*9+j*3+1]=vertexes[i*3+j].ny;
      normalArray[i*9+j*3+2]=vertexes[i*3+j].nz;
    }
   }

   delete[] vertexes;

   for(int i=0;i<polygonCount;i++) {
    for(int j=0;j<3;j++) {
      indexArray[i*3+j]=i*3+j;  
    }
   }


```

Another oddity is that if I don't delete object3d's spare template data in constructor but instead in destructor program crashes while trying to delete one of these arrays. Very odd. Maybe somehow connected?

And picture of error in action:

[www.tneva.net/wtf.png](www.tneva.net/wtf.png)

You can't see it from picture but it flickers a lot(atleast when you move forward or turn. Move backward doesn't flicker though) and you can see glimpses of terrain there. Most of the time it moves as expected though once eventhough I didn't move things the terrain rotated. However player's position/angle didn't alter(which could have explained).

Pretty darned odd and can't figure where I have gone wrong. Apart from modifying terrain code to deal with frames no real changes have been done yet doesn't work :( Or is there change I have missed and which screws this up?

Edit: Some valgrind errors:

```

==7826== Invalid write of size 2                                                             
==7826==    at 0x805BBB6: object3d::object3d(char const*) (object3d.cpp:142)                 
==7826==    by 0x8062F96: world::setPartList(char const*) (world.cpp:315)                    
==7826==    by 0x806438C: world::world(char const*) (world.cpp:71)                           
==7826==    by 0x804F3E0: client::init() (clientBasic.cpp:101)                               
==7826==    by 0x805963D: main (mainclient.cpp:10)                                           
==7826==  Address 0x618ce98 is 0 bytes after a block of size 72 alloc'd
==7826==    at 0x402505E: operator new[](unsigned) (vg_replace_malloc.c:268)
==7826==    by 0x805B364: object3d::object3d(char const*) (object3d.cpp:83)
==7826==    by 0x8062F96: world::setPartList(char const*) (world.cpp:315)
==7826==    by 0x806438C: world::world(char const*) (world.cpp:71)
==7826==    by 0x804F3E0: client::init() (clientBasic.cpp:101)
==7826==    by 0x805963D: main (mainclient.cpp:10)
```

object3d.cpp: 83 reads:    indexArray=new GLushort[polygonCount*3];
object3d:cpp: 142 reads: indexArray[i*3+j]=i*3+j;

What bloody invalid write? Can't be out of bounds since I check that. And what does it mean some address is 0 bytes? Why? 

And why do these lines cause invalid read size 4 error messages in valgrind?

```

	    myFrames[f].vertexes[i*3+j].nx=myFrames[f].normalTable[myFrames[f].normalIndexes[i]].x;
	    myFrames[f].vertexes[i*3+j].ny=myFrames[f].normalTable[myFrames[f].normalIndexes[i]].y;
	    myFrames[f].vertexes[i*3+j].nz=myFrames[f].normalTable[myFrames[f].normalIndexes[i]].z;
```

again boundaries are checked so i*3+j won't take past array size(if it would those wouldn't be executed and instead I would see message telling it happened).

Are these any significance and if so how could I fix these?

Starting to get really frustrating. Project doesn't progress at all and I have zero idea where the problem might be :(

Edit2: Crash issue fixed. Small typo caused that one. Oops! So now to figure out why on earth object still appears in odd mess.

---

### Post by tneva82 on 2009-04-12
Turns out there was very simple fix for this afterall. This line:

  glBindBuffer(GL_ARRAY_BUFFER, 0);

At the start of drawing routine and it works.

Still not quite sure why terrain worked fine without this. Ah well. Mysteries of the programming.

Maybe somebody finds this bit useful.

---

