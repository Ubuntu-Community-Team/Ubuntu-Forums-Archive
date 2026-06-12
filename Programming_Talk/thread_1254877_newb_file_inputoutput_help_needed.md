---
title: "newb file input/output help needed"
date: 2009-08-31
forum: Programming Talk
---

### Post by nite owl on 2009-08-31
I am needing to read in a txt file that is arranged for example:

ejvjanv
2542
isombs
rbionsb
..
...then the pattern of a string, new line, integer, new line, string, new line, string keeps repeating itself

I need to organise those lines into seperate data structures

i.e.

```

struct parts
{
string a;
int b;
string c;
string d;
};

```
 
I am trying something below, but it doesnt seem to be working:

```

..

while (!infile.eof())
{
infile >> parts[count].partNumber 
>> parts[count].partName 
>> parts[count].manufacturer 
>> parts[count].price 
>> parts[count].quantity; 
infile >> ws;
count++;
}

..

```

---

### Post by matsuzine on 2009-09-01
I misread the question.

---

### Post by dribeas on 2009-09-01
Your struct definition and the names used in the reading code do not correlate. The file definition and the data read does not correlate either (what are you reading? int, string, string, double?, int, ws??)

Please, rework the question with the actual code and the problem/symptoms you are facing. Note that C++ formatted input will skip whitespace (including newlines). If you want to process the newlines (they are used as separator tokens) use getline(). If you go the formatted input way, provide your own istream& operator>>( istream&, your_data_type& ), to encapsulate the formatted reading.

---

