---
title: "For the math nerds..."
date: 2013-01-16
forum: Programming Talk
---

### Post by ofnuts on 2013-01-16
Not really programming, but...

Gimp has a "raw image data" format that just saves the RGB triplets, but doesn't save anything else (in particular, the image dimensions). So if you forgot the dimensions you are in rough waters. However, since it saves exactly three bytes per pixel, you can tell how many pixels there are in the picture (so you have the width*height product), and you will in practice have bounds for the aspect ratio (for most pictures, between 1 and 2 for landscape and 0.5 and 1 for portrait).

Hence the question: is there a smart algorithm to obtain all the (W,H) pairs that satisfy both conditions? My smarter algorithm so far is a brute force test of all the combination of the prime factors of the product...

---

### Post by ehrt74 on 2013-01-16
[http://en.wikipedia.org/wiki/Integer_factorization]("http://en.wikipedia.org/wiki/Integer_factorization")

I wonder which format for Gimp you mean. PPM for example contains a header with the height and width of the file.

---

### Post by ofnuts on 2013-01-16
> **ehrt74 said:**
> [http://en.wikipedia.org/wiki/Integer_factorization](http://en.wikipedia.org/wiki/Integer_factorization)

I wonder which format for Gimp you mean. PPM for example contains a header with the height and width of the file.
The factorization isn't that hard. Given the numbers plain algorithms are sufficient. The "problem" is after the factorization.

As to the format produced by Gimp, I'm talking about that one:

---

### Post by trent.josephsen on 2013-01-16
Hmm, interesting...

If you want to generate *all* the possible WxH combinations, I wouldn't think you could improve on brute force (with some logic to skip combinations you've already tried). Which is a pain because it requires a lot of Cartesian products...

Perhaps you could start not by factoring the number completely, but by splitting it as close to the square root as possible. That way you could start with the aspect ratios that are close to 1 and work your way down. Something like

```
aspect_ratios(product)
    let k = floor(sqrt(product))
    if k*k = product then
        let (k, k) be a result
    while k > 1
        let k = k - 1
        if product is divisible by k then
            let (k, product/k) be a result
            let (product/k, k) be another
```

This method has time complexity O(sqrt(n)) but I don't know how to calculate that of the Cartesian product method. My algorithm would likely consume less memory, though, unless you could do something really clever with the brute force method.

The biggest area for optimization might be the "let k = k - 1" part. If you can figure out how to skip over some numbers without testing them... I don't really know, I just thought it was an interesting problem.

---

### Post by ofnuts on 2013-01-16
Well assuming I have split the factors in two groups that are as close as possible to the square root, it's is clear that if I move a factor from one group to the other I change the ratio by the square of this factor (so, 4 minimum) so for ordinary pictures this won't happen. I can only swap factors between the groups if these factors have between them a ratio smaller than sqrt(max_aspect_ratio)(moving a factor as above can be seen as swapping it with a "1"), so to check each factor on one side against every factor on the other I would try only n/2 x n/2 swaps (assuming a 50/50 split of the factors).

But this, of course, assumes there is a good algorithm to "split the factors in two groups that are as close as possible to the square root".

---

### Post by Warren Hill on 2013-01-16
Not a programming solution as such but a simple math based approach.

You know the number of pixels in the image say 

p = 480000

Now factorise it 

p = 2 x 2 x 2 x 2 x 2 x 2 x 2 x 2 x 3 x  5

now length is some combination of these factors and height is all the other factors

so possibilites are 

  1 x 480000
  2 x 240000
   3 x 160000
   4 x 120000
   5 x   96000
   6 x   80000 
    8 x   60000
  10 x   48000
  15 x   32000
  16 x   30000
  20 x   24000
  30 x   16000
  32 x   15000

etc this gives 90 possible solutions

A  second simpler but slightly less efficient solution is to start by  taking the square root of the total number of pixels.  One side must be  no bigger than this.  

Now for every number 1<= x < sqrt(p)
Calculate other side if its an integer then its possibly a solution
remembering that just as 600 x 800 = 480000 so does 800 x 600 so you would have to try it both ways round.

Its a simple exercise to code this in C or any other language

---

### Post by trent.josephsen on 2013-01-16
(Edit: This was supposed to be in response to ofnuts' last post.)

Right, and a systematic way of swapping between groups so that you don't lose track of which combinations you've already tried...

No, wait, that still wouldn't work, because you still have to swap composite factors. Like if you have 2*3*5 on one side and 2^2*11 on the other, 11/5 might be greater than sqrt(max_aspect_ratio) but 11/10 might not be. So you have to swap 2*5 with 11.

Even disregarding the resources it would take to split the number into two sets of prime factors, you'd probably still be looking at (at least) O(n) for the rest of the algorithm in both time and memory.

(Disclaimer: I'm not taking these complexity estimations from any real figuring, just wild guesses. Actual benchmarking with realistic numbers would be preferable anyway.)

---

### Post by Bachstelze on 2013-01-16
Any half-decent CAS will let you iterate over all divisors of a given integer, and it's easy to go from there. For example in PARI/GP:

```
? n = 480000
%5 = 480000
? fordiv(n, w, h = n\w; r = w/h; if(r >= 1 && r <= 2, print([w, h])))
[750, 640]
[768, 625]
[800, 600]
[960, 500]
? 

```

If you find the syntax awful, look into Sage (it is based on Python and uses the same syntax). Also, PARI comes with a C library if you want to integrate it in a C program.

---

### Post by Vaphell on 2013-01-16
going from sqrt(n) down to 1 and checking if n%x==0 is plenty fast
i whipped up awk code (to avoid the hassle of creating files) that finds 60 pairs for n=240078886800 (number pulled out of the 4 letters) in under 1 second.

```
$ echo | awk 'BEGIN{ n=240078886800; } { for( x=int(sqrt(n)); x>0; x--) { if(n%x==0) { c++; printf("%dx%d (ar=%f)\n", n/x, x, n/x/x ); } } } END { print c " combinations (x2)"; }'
510285x470480 (ar=1.084605)
544304x441075 (ar=1.234040)
588100x408228 (ar=1.440617)
680380x352860 (ar=1.928187)
705720x340190 (ar=2.074488)
816456x294050 (ar=2.776589)
850475x282288 (ar=3.012792)
882150x272152 (ar=3.241387)
1020570x235240 (ar=4.338420)
1176200x204114 (ar=5.762466)
1360760x176430 (ar=7.712747)
1411440x170095 (ar=8.297951)
1632912x147025 (ar=11.106356)
1700950x141144 (ar=12.051168)
1764300x136076 (ar=12.965549)
2041140x117620 (ar=17.353681)
2352400x102057 (ar=23.049864)
2551425x94096 (ar=27.115127)
2721520x88215 (ar=30.850989)
3401900x70572 (ar=48.204670)
3528600x68038 (ar=51.862195)
4082280x58810 (ar=69.414725)
5102850x47048 (ar=108.460508)
6803800x35286 (ar=192.818682)
7057200x34019 (ar=207.448779)
8164560x29405 (ar=277.658902)
10205700x23524 (ar=433.842034)
13607600x17643 (ar=771.274727)
20411400x11762 (ar=1735.368135)
40822800x5881 (ar=6941.472539)
200065739x1200 (ar=166721.449167)
400131478x600 (ar=666885.796667)
600197217x400 (ar=1500493.042500)
800262956x300 (ar=2667543.186667)
1000328695x240 (ar=4168036.229167)
1200394434x200 (ar=6001972.170000)
1600525912x150 (ar=10670172.746667)
2000657390x120 (ar=16672144.916667)
2400788868x100 (ar=24007888.680000)
3000986085x80 (ar=37512326.062500)
3201051824x75 (ar=42680690.986667)
4001314780x60 (ar=66688579.666667)
4801577736x50 (ar=96031554.720000)
5001643475x48 (ar=104200905.729167)
6001972170x40 (ar=150049304.250000)
8002629560x30 (ar=266754318.666667)
9603155472x25 (ar=384126218.880000)
10003286950x24 (ar=416803622.916667)
12003944340x20 (ar=600197217.000000)
15004930425x16 (ar=937808151.562500)
16005259120x15 (ar=1067017274.666667)
20006573900x12 (ar=1667214491.666667)
24007888680x10 (ar=2400788868.000000)
30009860850x8 (ar=3751232606.250000)
40013147800x6 (ar=6668857966.666667)
48015777360x5 (ar=9603155472.000000)
60019721700x4 (ar=15004930425.000000)
80026295600x3 (ar=26675431866.666668)
120039443400x2 (ar=60019721700.000000)
240078886800x1 (ar=240078886800.000000)
60 combinations (x2)
```

with AR cutoff
```
$ echo | awk 'BEGIN{ n=240078886800; ar=2; } { for( x=int(sqrt(n)); x>0; x--) { if(n%x==0) { if(n/x/x > ar) break; c++; printf("%dx%d (ar=%f)\n", n/x, x, n/x/x ); } } } END { print c " combinations (x2)"; }'
510285x470480 (ar=1.084605)
544304x441075 (ar=1.234040)
588100x408228 (ar=1.440617)
680380x352860 (ar=1.928187)
4 combinations (x2)
```

---

### Post by spjackson on 2013-01-16
> **Warren Hill said:**
> 
p = 2 x 2 x 2 x 2 x 2 x 2 x 2 x 2 x 3 x  5

You are missing a few 5s there.

> 
A  second simpler but slightly less efficient solution is to start by  taking the square root of the total number of pixels.  One side must be  no bigger than this.  

Now for every number 1<= x < sqrt(p)

Taking the required aspect ratio into consideration, it can be shown that sqrt(p)/sqrt(2) <= x <= sqrt(p), where x is the shorter side (or p is square).

---

### Post by ofnuts on 2013-01-16
@Warren Hill: looking at your post it dawns on me that if there are N factors there are 2^N divisors to test (with likely many duplicates, but I don't care) and the binary form of the value iterated from 0 to 2^N-1makes it easy to compute the divisor... And if you take this value as path in a binary tree, and set the node value to the corresponding divisor, you can cut off everything beyond the nodes where the divisor is greater than the square root. 

@trent.josephsen: yes, alas :)

@Bachstelze: everything is easier with the right library :) but yes, iterating the divisors is likely the best solution (see above)

@Vaphell: nice awk hack!

@spjackson: yes, this limits the number of divisors to check (or to compute)

---

### Post by Warren Hill on 2013-01-17
Sorry you are correct I am missing a few 5s

If we take total pixels P = 480000 for example

Then in C

int x,y;
```

for (x = sqrt(P); x > 0; x--){
        y = P / x;
       if (x * y == P){
        printf( "Possible solutions %d x %d, and %d x %d \n", x, y, y,x);
    }
}
``` 

Is probably the simplest and while it may not be the fastest.  It should be fast enough for images where the total number of pixels is less than a few million on most computers

---

### Post by Vaphell on 2013-01-17
```
y = P / x;
if (x * y == P)...
```

dont we have % for that? :-)
otherwise i agree it's not worth the effort to think much about this problem, unless for mental gymnastics. Complexity of sqrt(n) nets you 10^6 operations for 10^12 magnitude input and that is what, less than a second of cpu time?

---

### Post by Warren Hill on 2013-01-17
True

Instead of 

if ( x * y == P)

if (x % y ==0) 

or 

if (!(x % y))

also works and may be slightly quicker, if less easy to understand

---

### Post by iMac71 on 2013-01-17
[PHP]from math import sqrt
def find_wh(n):
    sqrt_n = int(sqrt(n))
    for w in range(sqrt_n, 0, -1):
        h, remainder = divmod(n, w)
        ratio = float(h) / w
        if remainder == 0 and ratio >= 1 and ratio <= 2:
           print h, w[/PHP]

---

### Post by hardmath on 2013-05-25
Searching for two factors close to the square root of N is the strength of [Fermat's factoring method]("http://en.wikipedia.org/wiki/Fermat's_factorization_method").

Where trial division starts small and goes up (at least typically), Fermat's method starts with the first square a^2 greater than or equal to N and checks if a^2 - N happens to be another square b^2.  If so, then N = a^2 - b^2 = (a+b)(a-b) and we have our most nearly equal factors of N.

If that fails, increment a, etc. and test again, until a factorization is found or a reaches (N-1)/2, after which point if N is odd we find:

[(N+1)/2]^2 - N = [(N-1)/2]^2

implying the trivial factorization N = N*1.

In practice here we would stop once (a+b)/(a-b) exceeds the allowable aspect ratio, e.g. 2.

---

### Post by ofnuts on 2013-05-25
Thanks for the tip...

---

