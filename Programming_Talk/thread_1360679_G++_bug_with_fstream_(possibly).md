---
title: "G++ bug with fstream (possibly)"
date: 2009-12-21
forum: Programming Talk
---

### Post by OVERPOWER8 on 2009-12-21
The mistake i've done: I didn't close the stream when it needed to be done:
[CENTER][LEFT][CENTER][LEFT]
It should look like that:

```

#include <fstream>
#include <iostream>
#include <stdlib.h>

using namespace std;

void GenerateFile(fstream &File)
{
    srand(time(0));
    int number;
    
    for(int i=0; i<5; i++)
    {
        for(int j=0; j<5; j++)
        {
            number=rand()%100+1;
            File << number << " ";
        }
        File << "\n";
    }
}

int FindMin(fstream &File)
{
    char ch[5];
    File >> ch;
    int min = atoi(ch);
    
    while(!File.eof())
    {
        File >> ch;
        if(atoi(ch) < min)
            min = atoi(ch);
    }
    return min;
}

int FindMax(fstream &File)
{
    char ch[5];
    File >> ch;
    int max = atoi(ch);
    
    while(!File.eof())
    {
        File >> ch;
        if(atoi(ch) > max)
            max = atoi(ch);
    }
    return max;
}

int main()
{

    fstream File("Numbers.txt");
    GenerateFile(File);
    File.close();
    
    int min, max;
    char ch[5];
    
    File.open("Numbers.txt");
    min = FindMin(File);
    File.close();
    
    File.open("Numbers.txt");
    max = FindMax(File);
    File.close();
    
    cout << "Min: " << min;
    cout << endl << "Max: " << max << endl;
    
    return 0;
}

```
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]

---

