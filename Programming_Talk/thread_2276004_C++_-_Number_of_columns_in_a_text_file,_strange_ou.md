---
title: "C++ - Number of columns in a text file, strange output"
date: 2015-04-29
forum: Programming Talk
---

### Post by carlo8 on 2015-04-29
Hi guys, I needed to write a simple program to evaluate the number of columns in a text file....the file name is "Bg_frm.txt", it contains a matrix of doubles and the values on each line are separated by spaces, something like this

```

#       Age       Bg_m22       Bg_m32       Bg_m42       Bg_m52       Bg_m62       Bg_m72 
    0.10152      -0.0309   -0.0144999   0.00629997   0.00390005   0.00230002  -0.00489998  
    0.11391      -0.0223  -0.00820017   0.00900006   0.00709987  0.000599861  0.000699997  
     0.1278      -0.0102  -0.00600004       0.0125       0.0123   0.00559998   0.00670004  
     0.1434       0.0079  -0.00410008    0.0159001    0.0166001    0.0101998       0.0121  
     0.1609   0.00550008  -0.00160003       0.0186    0.0202999    0.0135002    0.0165999  
    0.18053  -0.00249982   0.00119996    0.0215001       0.0221    0.0141001    0.0235999  
    0.20256   -0.0078001   0.00499988       0.0281       0.0246    0.0170999       0.0323  
    0.22727  -0.00960016   0.00889993    0.0354002       0.0311    0.0247002    0.0413001  
      0.255  -0.00640011    0.0126998       0.0411    0.0362999    0.0333002    0.0510001  
    0.28612  -0.00270009    0.0163999    0.0450001    0.0420001    0.0417001    0.0603001  
    0.32103   0.00189996    0.0197999    0.0446999        0.046       0.0493    0.0674999  
     0.3602   0.00640011    0.0230999       0.0441    0.0486999       0.0544    0.0756998  
    0.40415   0.00960016    0.0253999        0.049    0.0533998       0.0597    0.0858002
```




So, I used this code

```


int main()
    {
    cout << "Count columns in the file" << endl << endl;
    fstream myfile("Bg_frm.txt");
    string line, temp;
    stringstream ss;
    int ncols=0;
    
    //discard first line from the file (it's a header)
    getline(myfile, line);
    


    getline(myfile, line);
    ss.clear();
    ss << line;
    
    while (ss)
        {
         ss >> temp;
        ++ncols;
         cout << temp << " ";
        }

    cout << "nrows = " << nrows;

    }
```

The program works, but it returns the number of columns +1....the output is


```

Count columns in the file


0.10152 -0.0309 -0.0144999 0.00629997 0.00390005 0.00230002 -0.00489998 -0.00489998 
nrows=8

```

it's counting the last value in the stringstream twice, so it gives a result of 8 instead of 7.

I don't understand what I am doing wrong, any suggestions?
Thanks!

---

### Post by TheFu on 2015-04-29
So ... I learned C++ before the Std Templates were useful. Don't know which methods are available for a "string" class, but wouldn't "isspace()" be one?

The requirements seem vague and could be interpreted in different ways. 
Are you looking for pure columns of text, the longest line with any characters or columns of number? 

Assuming the last option is it, the way I'd attack this is to 
Loop over the file, 1 line at a time {
* read a line
* remove all leading and trailing whitespace (it is common for humans to hit a space at the end of a line).
* if the first character is '#', skip the line
* convert all remaining multiple whitespace groups on the line (tabs, spaces) into a single tab
* count the number of tabs on the line (col = count+1)
* Keep the largest number of tabs found, since some rows may not have numbers for every column. Ignore smaller counts
}

Be certain to use :isspace: regex representations - so international spaces in different character sets are handled correctly. [http://www.cplusplus.com/reference/cctype/isspace/](http://www.cplusplus.com/reference/cctype/isspace/)

Sorry I don't know more.  I've been doing mainly perl for the last 15 yrs. Plus there must be 100 different ways to solve this. In perl, looks like a 5 line program.

BTW - if you had not posted code and attempted a reasonable solution, I would not have responded. 
Nice job on the learning!

---

### Post by xb12x2 on 2015-04-29
```
while (ss >> temp)
    {
//      ss >> temp;
        ncols++;
        cout << temp << " ";
    }
```

---

### Post by Vaphell on 2015-04-29
more on this

[http://stackoverflow.com/questions/17807634/stringstream-duplicates-last-word](http://stackoverflow.com/questions/17807634/stringstream-duplicates-last-word)

that said, if you don't have to use c++, it would be a really short awk code
```
awk 'NR==2 { print NF; }' Bg_frm.txt
```

---

### Post by carlo8 on 2015-05-18
Sorry guys, I completely forgot to thank you for the help! ;)

I solved using your suggestion to change the code to

```
while (ss >> temp)
{
ncols++;
cout << temp << " ";
}

```



To answer your questions (even if REAAAALLY late), the files whose columns I need to count contain columns of numbers like the example I posted.....I use C++ 'cause it's the language I know best, and I wanted to stick to using stringstream since I used it already in other parts of the code, so it looked more consistent that way.

Thanks again!









[COLOR=#222222][FONT=Verdana]

[/FONT][/COLOR]

---

