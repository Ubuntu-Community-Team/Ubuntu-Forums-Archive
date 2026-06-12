---
title: "C++ copy mystery?"
date: 2009-06-24
forum: Programming Talk
---

### Post by kaspar_silas on 2009-06-24
Well a mystery to me anyway. Consider the following short program

```

class Array3D
{
public:
    Array3D();
    ~Array3D();
    Array3D(Array3D & Original);
    void SetUp(unsigned int rows,unsigned int columns, unsigned int numberofslices);
private:
    float* ImageData;
    unsigned long maxsize;
};

int main(int argc, char* argv[])
{
    Array3D* first= new Array3D[2];
    first[0].SetUp(10,10,5);
    first[1].SetUp(10,10,5);
    delete [] first;

    Array3D* second= new Array3D[2];
    second[0].SetUp(10,10,5);
    second[1].SetUp(10,10,5);//XXX-1-XXX//
    //second[1]=second[0];//XXX-2-XXX//
    delete [] second;
}//Main End

//////////////////////////////////////////////////////////////////////
Array3D::Array3D()
{
    maxsize=0;
    ImageData=0;
}
//////////////////////////////////////////////////////////////////////
void Array3D::SetUp(unsigned int parows,unsigned int pacolumns,unsigned int panumberofslices)
{
    maxsize=parows*pacolumns*panumberofslices;
    ImageData=new float[maxsize];
}
//////////////////////////////////////////////////////////////////////
Array3D::Array3D(Array3D& Original)
{
    maxsize=Original.maxsize;
    if(ImageData)delete[]ImageData;
    ImageData=new float[maxsize];
    for(unsigned long loop=0;loop<maxsize;loop++)
    {
       ImageData[loop]=Original.ImageData[loop];
    }
}
//////////////////////////////////////////////////////////////////////
Array3D::~Array3D()
{
    if(ImageData)delete[]ImageData;
}
//////////////////////////////////////////////////////////////////////

```

This runs fine in it's current form. If however you uncomment the 9th line in main (marked XXX-2-XXX) and comment out the line above (marked XXX-1-XXX). The program then produces:

```

7f70fb385000-7f70fb386000 r--p 00016000 08:01 7675948                    /lib/libgcc_s.so.1
7f70fb386000-7f70fb387000 rw-p 00017000 08:01 7675948                    /lib/libgcc_s.so.1
7f70fb387000-7f70fb40b000 r-xp 00000000 08:01 7676874                    /lib/libm-2.9.so
7f70fb40b000-7f70fb60a000 ---p 00084000 08:01 7676874                    /lib/libm-2.9.so
7f70fb60a000-7f70fb60b000 r--p 00083000 08:01 7676874                    /lib/libm-2.9.so
7f70fb60b000-7f70fb60c000 rw-p 00084000 08:01 7676874                    /lib/libm-2.9.so
7f70fb60c000-7f70fb6fd000 r-xp 00000000 08:01 3867379                    /usr/lib/libstdc++.so.6.0.10
7f70fb6fd000-7f70fb8fd000 ---p 000f1000 08:01 3867379                    /usr/lib/libstdc++.so.6.0.10
7f70fb8fd000-7f70fb904000 r--p 000f1000 08:01 3867379                    /usr/lib/libstdc++.so.6.0.10
7f70fb904000-7f70fb906000 rw-p 000f8000 08:01 3867379                    /usr/lib/libstdc++.so.6.0.10
7f70fb906000-7f70fb919000 rw-p 7f70fb906000 00:00 0 
7f70fb919000-7f70fb930000 r-xp 00000000 08:01 7676885                    /lib/libpthread-2.9.so
7f70fb930000-7f70fbb2f000 ---p 00017000 08:01 7676885                    /lib/libpthread-2.9.so
7f70fbb2f000-7f70fbb30000 r--p 00016000 08:01 7676885                    /lib/libpthread-2.9.so
7f70fbb30000-7f70fbb31000 rw-p 00017000 08:01 7676885                    /lib/libpthread-2.9.so
7f70fbb31000-7f70fbb35000 rw-p 7f70fbb31000 00:00 0 
7f70fbb35000-7f70fbb55000 r-xp 00000000 08:01 7675937                    /lib/ld-2.9.so
7f70fbd24000-7f70fbd27000 rw-p 7f70fbd24000 00:00 0 
7f70fbd50000-7f70fbd54000 rw-p 7f70fbd50000 00:00 0 
7f70fbd54000-7f70fbd55000 r--p 0001f000 08:01 7675937                    /lib/ld-2.9.so
7f70fbd55000-7f70fbd56000 rw-p 00020000 08:01 7675937                    /lib/ld-2.9.so
7fff03d41000-7fff03d56000 rw-p 7ffffffea000 00:00 0                      [stack]
7fff03dff000-7fff03e00000 r-xp 7fff03dff000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted


``` 

Which is not quite what I expected. What is so wrong with the copy constructor. I basically just want a value by value copy is that not what I am doing.

Thanks alot for any help as I am baffled.

---

### Post by Habbit on 2009-06-24
[COLOR="Silver"]You are operating on values of type Array3D*. The assignment operator for this type does a pointer copy, and thus when you delete[] the array (of Array3Ds) you are deleting the _same_ object twice. Bang, you're dead. Let me remark that even if you were using references, and thus value semantics,[/COLOR] it wold be the assignment operator and not the copy constructor who would be called. It would most likely crash too since your class does not have a custom assignment operator, so the default one would copy the float*, and then the destructors for both objects would try to delete[] the same float array. Bang, you are still dead.

[COLOR="Silver"]Furthermore, the object originally pointed to by second[1] is leaked because you lost the only pointer you had to it when you overwrote it with second[0].[/COLOR]

EDIT: I had my head somewhere else when typing the pointers part... However, as dwhitney76 kindly remarked, the assignment operator part is still true.

---

### Post by dwhitney67 on 2009-06-24
I did not pay to much attention to the copy-constructor, but I can tell you that it is not being called.

Your destructor is the evil one.  Actually, it is implemented correctly, but unfortunately it is deleting the same location twice.

Secondly, there is a difference between these two statements:
```

object_1 = object2;

// and

Object object_1 = object_2;

```

The first statement calls the operator=() overloaded operator, which if you do not provide, the compiler will do so for you.  The second statement calls the copy-constructor.  Your code is using the former, not the latter.

PS.  Consider using the space-key (the largest one on your keyboard) more often.  Scrunched up code looks crappy.

---

### Post by kaspar_silas on 2009-06-24
Thanks a lot to both of you that was very helpful. I have wrote the class assignment operator and all seems happy now.

p.s. DWhitney your far from the first to comment on the lack of spaces. I actually prefer it that way, strange I know. Still, you are right I should change it when I post I just forgot.

---

