---
title: "[SOLVED] need your opinion: how to make a program run faster"
date: 2008-01-15
forum: Programming Talk
---

### Post by nephritiri on 2008-01-15
hey everyone. i need your opinion regarding optimization of a code.
FYI, i use a standard desktop PC. single-processor. 512mb ram.

i am experimenting on rotating a single 2D image from 0 to 360 degrees.
without any parallelism/concurrency whatsoever, this kind of program which has a loop structure of:

[HTML]
    for(degree=0,degree<=360;degree++){
           for(x=0,x<=width;x++){
                for(y=0,y<=height;y++){

                     .....rotate here and print frame here

                }//for y
           }//for x
    }//for degree
[/HTML]

...runs fine (and fast).  Now, i extended this code to rotate a volume-a 3D object which has a loop structure of:

[HTML]
    for(degree=0,degree<=360;degree++){
           for(x=0,x<=width;x++){
                for(y=0,y<=height;y++){
                     for(z=0,z<=depth;z++){

                            .....rotate here and print frame here

                     }//for z
                }//for y
           }//for x
    }//for degree
[/HTML]
...and because of this structure, this code has a running time of O(n^4). printing each frame takes as much as 5 to 6 minutes! imagine the total of 361 -> [0,360] frames*6 minutes!

so, i seeked some suggestions and tried them (people from this forum have been helping me with this):

1.) pthreads
     pthread_create,pthread_join/pthread_detach
     for this suggestion, i experimented with 2D rotation first.
     for each degree, i create a thread (total of 361 threads, a massive amount!)
     program ran just fine but at the end, i hit segmentation fault. (with just 3 loops)

2.) fork() 
     i experimented with 2D rotation first and it worked fine. i was able to print all     361 images.
     i extended it to 3D rotation. it worked fine and was able to print the first frame but it took 5-6 minutes also.so, i terminated it later on.
     i experimented to simplify my 3d code by just printing a number so that i could see if it will be able to create all the 361 threads. and then, i hit segmentation fault.

     i've expected this result from fork() cause it's more expensive than threads. but with this massive amount of threads with these available resources, i still can't meet my goal of making my code run faster. ive written my code as simple as it can be, but it is really slow.

some said that it is not really recommended for me to use pthreads in this case, and that fork() is more expensive. your opinions and suggestions will be of a very BIG help.

---

### Post by CptPicard on 2008-01-15
> **nephritiri said:**
> 
i am experimenting on rotating a single 2D image from 0 to 360 degrees.
without any parallelism/concurrency whatsoever

Glad you hear you got rid of the parallelism... don't let it creep back into your design here, as it strangely seems like at the end of your post. Forget about it unless you get more cores, ok? :) Neither pthreads nor fork belong to the solution.

Now, without knowing much about your situation... how big are the dimensions of your 3D object? If you absolutely must rotate each voxel, I really don't see how something that simple could be made faster in the big-Oh sense... however, you can always try making the innermost loop faster. 

One of the most immediate tricks you can try is precomputing the values of the trig functions you need for the rotation. Calling sin and cos from the math library is slow, and as you're using integer degree values, you can just create a 360-slot array for both of them...

---

### Post by nephritiri on 2008-01-15
hehehe. okay. i hope to upgrade my pc to more than one core someday. =>

anyway, someone has suggested that to me before but i took it for granted and forgot. because i was "tangled" with threads then. hehe 

the dimensions of my volume are
height = 480
width = 640
depth = 640

depends on the 2D image size im converting to 3D. originally, it was 1024? x 760.. i forgot the width but the point is, i thought it was too big so i scaled my image to 640x480.

thank you for helping me all along... i'l not take suggestions for granted again. il try precomputing the trigs() and see what happens. =>

---

### Post by CptPicard on 2008-01-15
Yeah, do that. It's going to give you a big boost -- precomputation of trigs was one of the first things you did back in the 90s when writing demos -- this was the time when you had to do all of your 3D operations yourself...

Mind you, moving to a 4-core machine would just push your computation time down to a quarter, but precomputing trigs is going to... well...  check it out...

---

### Post by dwhitney67 on 2008-01-15
You might be able to shave off one iteration in your outermost loop.  Shouldn't you be indexing from 0 to less than 360 (not less than or equal)?

Perhaps something similar could be said for the other loops.

---

### Post by public_void on 2008-01-15
Before optimising anything use a profiler to find the CPU intensive portions of your code. Surprisingly you may find sections of code other than the loop that are slow. Therefore optimising the loop may result in little to no performance gain. 

A couple of suggestions:
- Order of nesting. Remember the outer loop executes more often than the inner loop.
- Remove unnecessary work. For example dereferencing many pointers or performing the same evaluations. Put reused values into variables before the loop.
- Precision. Floating pointer operators are costly, if you can use integers.
- Move some operators between loops.

These are just a few, you can optimise expressions, or write some assembly. There are lots of technique, find the most appropriate for your situation.

---

### Post by Lster on 2008-01-15
Hi

You could explore whether your compiler can optimize your code a little. I'm not sure how much it will help, but *I* noticed a significant improvement with optimizations in GCC.

[http://gcc.gnu.org/onlinedocs/gcc-4.2.2/gcc/Optimize-Options.html#Optimize-Options](http://gcc.gnu.org/onlinedocs/gcc-4.2.2/gcc/Optimize-Options.html#Optimize-Options)

Hope it helps,
Lster

---

### Post by stroyan on 2008-01-15
It is very important to avoid computing the trig functions repeatedly for the same value. But you can go beyond that and keep just the delta values for each step in the x direction and each step in the y direction.  You could use double precision nx and ny variables that are incremented by a precomputed amount for each increment of y.  Then by keeping your nx and ny values in double precision you can make each step of x or y require just a few floating point additions to compute new values of nx and ny.

When you get into really large data the CPU implementation becomes very important.  There is a huge difference between the speed of instructions vs. the speed of main memory.  To compensate for that the CPU has one or more layers of relatively small cache which holds copies of recently used memory locations.  The cache can be much, much faster than normal RAM.  But the cache is small.  It is arranged in groups of nearby addresses.  You get much better performance when accessing memory locations in a series of adjacent addresses than when bouncing around in memory.

Another similiar structure occurs around the page table.  i386 CPUs have a 4096 byte page size.  A first access to a page is much more expensive than additional accesses because the CPU must fault in a page table entry for the first access to a page.  There are few page table entries in the CPU's TLB.

The bottom line that results from this CPU implementation is that you get better performance by accessing groups of nearby addresses.  The measure of what is nearby differs for different CPUs.  In your case the two most interesting distances are probably 64 bytes and 4096 bytes.

In the case of your pixel or voxel arrays the stride from one index value to another can be very large for some directions.  The common cure for that is to break up a big pixel array into tiles.  Instead of having a voxel saved in an address like A[x*1+y*width+z*(width*height)] the bits from the x, y, and z offsets are mixed together so that a small motion in any direction is likely to produce a small change in address.  If the binary digits of an offset in x, y, and z were represented as 8 bit values like this-
xxxxxxxx
yyyyyyyy
zzzzzzzz
Then an untiled offset address might look like this-
zzzzzzzzyyyyyyyyxxxxxxxx
But a tiled address would have bits shifted and or'd together like this-
zzzzyyyyxxxxzzzzyyyyxxxx
The size of cache and TLB structures in your CPU will affect how finely you should mix the bits from the three directions.  Experimentation would be interesting.

---

### Post by stroyan on 2008-01-15
> **public_void said:**
> 
- Precision. Floating pointer operators are costly, if you can use integers.

That is obsolete advice.  Floating points adds and multiplies can be as fast as integer adds and multiplies in modern CPUs.

---

### Post by popch on 2008-01-15
How do you 'print' a 3D image? With a solid 3D representation?

Depending on the contents of your 3D image, you might want to rotate just a section or a projection of your image. Are there any hidden (invisible) parts you can easily identify, such as the insides or the back side of an opaque solid?

---

### Post by nephritiri on 2008-01-15
wow... im overflowing with suggestions.. im getting the picture little by little..

CptPicard, iv tried precomputing the trigs outside the 4d loop, and just put it in another loop so that i can put them each in an array. it took so much time... i patiently waited for almost 2 hrs.the first frame hasnt been printed because i think its still computing the trigs.i terminated it.i wonder, in 2D rotation, computing these trigs ran just fine, it was fast inside the 3Dloop, but inside just 1loop,well...iv said it. hmmm. i must be stupid.maybe i shud try precomputing them inside the degree loop but outside x.. adding another loop outside the 4Dloop just adds more time to  my program..

hi dwhitney67. the range of my array is [0,360]. i included 0 so that i can print the volume in its unrotated state.hey, my lightbulb just lit. u think that if i add a condition like:
[HTML]
    if degree=0
         do not rotate
   else rotate
[/HTML]
it could save time computing for 0 degree? am i right?

Lster,thanks for the link.il go look at it.
stroyan,thanks, i get a better picture in the aspect of memory mgt. yeah, maybe i shud experiment more.

hey popch, i print the volume, well, not really the volume... i traverse the 3d space and along the z axis, when i encounter the first voxel, i save the value of z(the distance) and compute the gray value (with the percentage of gradient) and that gray value is what will be printed on the 2D image. the gray value is what makes this image look 3D-ish. ahm ur suggestion re rotating just a section?well, i cant see how will that work for my case...coz as iv mentioned, i have to get the z-distance after rotating the whole volume... maybe i dont get it, can u tell me how rotating just a section can help?

---

### Post by CptPicard on 2008-01-15
> **nephritiri said:**
> 
CptPicard, iv tried precomputing the trigs outside the 4d loop, and just put it in another loop so that i can put them each in an array. it took so much time... 

Are you sure you're precomputing the trigs outside of *all* of your loops?

What I want you to do is (pseudocode):

```

float cos_array[360] 
float sin_array[360]

for (int deg = 0; deg < 360; deg++) {
  cos_array[deg] = cos(deg);
  sin_array[deg] = sin(deg);
}

for (int deg = 0; deg < 360; deg++)
  for (int x ...)
    for (int y...)
      for (int z ...) {
         // use the precomputed arrays here instead of sin() and cos()
     }

```

EDIT: it also seems like what you're doing doesn't require you to rotate the interior points, right? It's just your normal cube rotation and projection, with something like shading added? Everything you need to rotate are the corner vertices, and then you just shade the side squares... no?

---

### Post by nephritiri on 2008-01-15
yeah, thats what i did. except that i converted the degree to radians first, then compute the trigs, and put them in their respective arrays.

no... the main goal of my code is to render a volume from a sequence of 2d images.for simplicity, let's say, 2views: the front and the side. il project them and do some space carving from the front and from the side. im not limiting myself to a cube.im also working on different shapes.

wait,...yeah...maybe i can just rotate all the exterior voxels. il study if it will work in my case..

---

### Post by nephritiri on 2008-01-15
hey guys, thank you so much for all the suggestions. iv precomputed the values that needs to be precomputed...

anyway, i happen to think of a new solution (i hope): i just scaled down my input images in proportion to the original dimensions. 

the ratio of 640x480 is 1.333. i desired to hav a height of just 200 so i multiplied it w/ 1.333 and my new width will be 267. with these new dimensions, i was able to run my program less than 20 seconds/frame. its much faster. ;D  (though,il be able to print all the frames within 1.9 hrs) 

one of the things im trying to do here is compute the cubic volume (cm^3) of a real object through those 2D input images. so... with these adjustments and computations in the orig dimensions, maybe il let math and calculus do the work.

---

### Post by fyplinux on 2008-01-16
Some values might be reused, e.g., sin(0) = sin (360) = cos(90), if you know sin(0), you don't have to compute sin(360), cos(90) again, just assign them.

this idea is similar to stroyan: "It is very important to avoid computing the trig functions repeatedly for the same value. But you can go beyond that and keep just the delta values for each step in the x direction and each step in the y direction."

---

### Post by CptPicard on 2008-01-16
fyplinux, that kind of an optimization is already inplicitly included in the idea of precomputing into an array... you've got all the values instead of those special cases you'd have to specifically test for :)

---

### Post by popch on 2008-01-16
> **nephritiri said:**
> hey popch, i print the volume, well, not really the volume... i traverse the 3d space and along the z axis, when i encounter the first voxel, i save the value of z(the distance) and compute the gray value (with the percentage of gradient) and that gray value is what will be printed on the 2D image. the gray value is what makes this image look 3D-ish. ahm ur suggestion re rotating just a section?well, i cant see how will that work for my case...coz as iv mentioned, i have to get the z-distance after rotating the whole volume... maybe i dont get it, can u tell me how rotating just a section can help?

Rotating a (cross) section will not work for you since you will plot a view of the surface of an opaque solid.

---

### Post by Wybiral on 2008-01-16
I'm not sure I get exactly what you need to do, but wouldn't it be easier to just rotate each vertex and interpolate the image as texels (texture map it)? Or does it HAVE to be voxel?

---

### Post by nephritiri on 2008-01-16
yes,it does have to be voxels.

---

