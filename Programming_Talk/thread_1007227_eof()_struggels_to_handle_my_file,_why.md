---
title: "eof() struggels to handle my file, why?"
date: 2008-12-10
forum: Programming Talk
---

### Post by abraxas334 on 2008-12-10
Hi,
I have the following problem. I am reading a very large file into my program (around 15000000 lines). But my !eof() test does not seem to recognise the end of file, which results in my  program crashing.
Below the essential bit of the code:

[PHP]
//variables
ifstream inEdges ("homogEdges.dat");
vector<unsigned long long> Vertex;

   if(inEdges.good())
    {
        inEdges>>invalue;
       
        while(!inEdges.eof())
        {
           //cout<<invalue<<endl;
            Vertex.push_back(invalue);
            inEdges>>invalue;
            i++;
            if(i>30000000)
            {
                cout<<invalue<<endl;
                cout<<"this should not happen as the file is smaller"<<endl;
            }
           
        }
        inEdges.close();
    }

[/PHP]
my cout test is reached every single time, even tho i should not be any bigger than 25000000.
The file i am reading in looks like this:
233245  2345325
2341    21345
32466   234567
etc. (for ~12000000 lines)
obviously eof() cannot handle the file size? Is there any other way of testing for the end of file, as I don't want to do a for loop manually entering the amount of lines in the file every single time.

Thanks

---

### Post by Tony Flury on 2008-12-10
Does it work with a smaller file  - say 10 lines ?

If you say your code is going beyond the end of the file - what is the code reading after the end of the file ?

---

### Post by abraxas334 on 2008-12-10
yes i tried smaller files they worked
I have found the problem now, sorry i had a stray comma in my file which was not read by the program!

should have noticed it earlier but obviously difficult with such a big file!

Thanks tho

---

### Post by Zugzwang on 2008-12-10
Also do not forget to read the fail() value of your input stream. This will tell you if the program encountered a non-number in the input file.

---

### Post by dwhitney67 on 2008-12-10
I would suggest that the code be revisited and simplified:
[php]
  ifstream inEdges("homogEdges.dat");
  vector<unsigned long long> Vertex;

  if (inEdges)
  {
    unsigned long long invalue;

    while (inEdges >> invalue)
    {
      Vertex.push_back(invalue);
    }
  }
[/php]

---

