---
title: "C++ arrays setting last value of one array to th first value of another"
date: 2012-01-05
forum: Programming Talk
---

### Post by thedemon13666 on 2012-01-05
Hi,

I have noticed a problem when using c++ on my ubuntu laptop, as the title suggests, when I am using two arrays it seems that for some reason the first value of one array is being set to thesecond value of another array and I am not sure why,  here is some example code of mine, please note this is root code however I have noticed this happen with normal c++ code:

A it of pseudo code, I am reading in an ASCII file containing two lists separated by a space in a file, these are read into a pair of vectors,  I couldnt find a simple way to do this so I used a counter to keep track of which number is was looking at, so it could be put in the correct vector.

As root does not seem to like vectors I then have to move the vectors into simple arrays.
The arrays are then used to plot a graph


```

#include "Riostream.h"
#include<iostream>
#include<fstream>
#include"TVector.h"
#include"TGraph.h"
#include"TCanvas.h"
#include"TROOT.h"
#include"TPad.h"
#include"TAxis.h"
#include"TMath.h"
#include"TH1F.h"
#include"TFrame.h"
#include"TLegend.h"

int main()
        {
        Double_t x;
        Double_t E[260], res[260];
        vector<Double_t> en;
        vector<Double_t> re;
        Int_t i = 0;
        ifstream file("q3data.txt");
        while(file>>x) 
               {
                if (i%2==0)
                        {
                        en.push_back(x);
                        }
                if (i%2>0)
                        {
                        re.push_back(x);
                        }
                i=i+1;
                }
        for(Int_t j=0;j<=260;j++)

                {

                        E[j]=en[j];

                        res[j]=re[j];
                        cout<<E[j]<<" "<<res[j]<<endl;
                }
        res[0]=re[0];  // IF THIS LINE IS NOT PRESENT THEN FOR SOME REASON res[0]=E[261]
        cout<<res[0]<<endl;
        cout<<E[0]<<endl;
       TCanvas *c1 = new TCanvas("c1","1",200,10,700,500);
        c1->SetFillColor(0);
        c1->SetGrid();

//TH1F *hr = c1->DrawFrame(20,0,100,150);
        TGraph *gr = new TGraph(260,E,res);

        gr->SetLineColor(2);
        gr->SetLineWidth(4);
        gr->SetMarkerColor(4);
        gr->SetMarkerStyle(21);
        gr->SetTitle("dsfdf");
        gr->GetXaxis()->SetTitle("df");
        gr->GetYaxis()->SetTitle("df");
        gr->Draw("ACP");
                c1->SaveAs("3.1.pdf");

        return 0;
        }


```I have indicated using a comment string in my code the line that seems to sort this out, however this is by no means a proper solution.....

In regards to this particular code for some reason res[0] is set equal to E[261] or en[261] IF res[0]=re[0] isnt added to the code as shown above

Does anyone have any idea why this is happening?

Thanks a bunch


EDIT I should add I am running ubuntu 11.10 x64

---

### Post by schauerlich on 2012-01-05
res and E are right next to each other on the stack. When you access E[261], you're going past the end of the E array and into the res array. The problem is in your for loop:

```
for(Int_t j=0;j<=260;j++)
```

The last thing you copy is element 260. Remember, however, that arrays in C++ are indexed from 0, making the elements of E and res 0-259, so that line should have j < 260 (not <=). E[260] is the same place in memory as res[0].

```
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
 ^ E[0]         ...        E[259] ^ | ^ res[0]        ...
                                      ^ E[260]
```

---

### Post by muteXe on 2012-01-05
Agreed. 
Also what do you mean by 'root doesn't like vectors'??

---

### Post by thedemon13666 on 2012-01-05
derp,

I had actually gone the other way, in the text file there are 261 lines of data, but like an idiot I forgot that when specifying the size of the array I.E res[261] that doesnt mean that the last value of the array is res[261] it is res[260], I had overcompensated for starting at zero, quite embarrassing.

The actual solution is to set res[261] and E[261] rather than with [260].

Cheers!

EDIT
> root doesn't like vectorsBy this I mean that if I substitute the arrays that are used in 
```
 TGraph *gr = new TGraph(260,E,res);
```
then the code does not compile, which is annoying as I have to specify the number of data points using arrays.... do you have  solution to this?

---

### Post by muteXe on 2012-01-05
put the vectors back in, do NOT compile as root, and paste your new code and your compiler errors in here please.

---

### Post by dwhitney67 on 2012-01-05
> **thedemon13666 said:**
> 
Does anyone have any idea why this is happening?


I believe your question has already been answered.

However, I wanted to point out that there are better ways to populate your arrays.  Consider the following:
```

#include <vector>
#include <iostream>
#include <iterator>

int main()
{
   std::vector<int> vec;

   // insert data into a vector
   for (int i = 0; i < 10; ++i)
   {
      vec.push_back((i+1) * 10);
   }

   //declare array
   int* arr = new int[vec.size()];

   // copy contents from the vector to the array
   std::copy(vec.begin(), vec.end(), arr);

   // display results (optional)
   std::copy(arr, arr + vec.size(), std::ostream_iterator<int>(std::cout, " "));
   std::cout << std::endl;

   // clean up
   delete[] arr;
}

```

---

### Post by thedemon13666 on 2012-01-06
Ive kind of negated the point of this thread by finding out how to use vectors in root.

The line for TGraph should read:

```
TGraph *gr = new TGraph(261,&en[0],&re[0]);
```

as the STL vector is desgined to give direct access to its internal array type,


STILL I have learned some stuff by making this thread.

Cheers guys.

---

### Post by muteXe on 2012-01-06
I am still not understanding how you think compiling as root you would need to change your code??

---

### Post by Arndt on 2012-01-06
> **muteXe said:**
> I am still not understanding how you think compiling as root you would need to change your code??

Maybe he refers to the root of a graph.

---

### Post by muteXe on 2012-01-06
Oh right :)

---

### Post by thedemon13666 on 2012-01-06
Ha actually I am referring to root as in the c++ plotting software provided by cern, hence why in my code I have the weird Double_t rather than double etc,

it wasnt handling passing the vectors to TGraph, but my above solution solves it.

Sorry for the confusion.

---

