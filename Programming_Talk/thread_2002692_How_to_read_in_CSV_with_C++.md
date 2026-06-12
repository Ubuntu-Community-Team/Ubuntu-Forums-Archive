---
title: "How to read in CSV with C++?"
date: 2012-06-13
forum: Programming Talk
---

### Post by jsmidt on 2012-06-13
Hey everyone,

If I have a txt file with this as data: (file.txt)
```

1.0 2.0 4.0
2.0 4.0 8.0
3.0 6.0 12.0
```

and want to load the three double arrays that I can then print.  I can read in this data into double arrays and print it back using this c++ file read.cpp:

```

#include<iostream>
#include<fstream>
using std::cout;
using std::endl;
using std::ifstream;

int main()
{
   ifstream in;
   in.open("file.txt");
   double a[3],b[3],c[3];

   for (int i = 0; i < 3; i++) {
       in >> a[i] >> b[i] >> c[i];
       cout << a[i] << " " << b[i] << " " << c[i] << endl;
   }
   return 0;
}
```

However, let's say my file is not a .csv such as (file.csv)
```

1.0,2.0,4.0
2.0,4.0,8.0
3.0,6.0,12.0
```

Does anyone know how I can alter my read.cpp file above to handle comma delimiters?  To read into 3 double arrays and write data back to screen?  Thanks!

---

### Post by roelforg on 2012-06-13
Your second example (the one you say isn't csv) is actually csv. (**Comma** Separated Values)
 
This is how i'd do it:
```

vector< vector<string> > result;
while (!file.eof())
{
 //go through every line
 string line;
 vector<string> tmp;
 size_t pos=string::npos;
 getline(file,line);
 //loop through the ,
 while ((pos=line.find_first_of(","))!=string::npos)
 {
  //extract the component sans ,
  tmp.push_back(line.substr(0,pos-1));
  //erase the val including ,
  line.erase(0,pos);
 }
 result.push_back(tmp);
}

```
 
And then parse the vector to doubles.
I haven't tested it, but you should get the idea.

---

### Post by the_unforgiven on 2012-06-13
> **roelforg said:**
> Your second example (the one you say isn't csv) is actually csv. (**Comma** Separated Values)
 
This is how i'd do it:
```

vector< vector<string> > result;
while (!file.eof())
{
 //go through every line
 string line;
 vector<string> tmp;
 size_t pos=string::npos;
 getline(file,line);
 //loop through the ,
 while ((pos=line.find_first_of(","))!=string::npos)
 {
  //extract the component sans ,
  tmp.push_back(line.substr(0,pos-1));
  //erase the val including ,
  line.erase(0,pos);
 }
 result.push_back(tmp);
}

```
 
And then parse the vector to doubles.
I haven't tested it, but you should get the idea.

Damn, you beat me to it ... :(
Here is my version:
```

#include <iostream>
#include <fstream>
#include <string>
#include <cstdlib>
#include <list>

using namespace std;

void split_line(string& line, string delim, list<string>& values)
{
    size_t pos = 0;
    while ((pos = line.find(delim, (pos + 1))) != string::npos) {
        string p = line.substr(0, pos);
        values.push_back(p);
        line = line.substr(pos + 1);
    }

    if (!line.empty()) {
        values.push_back(line);
    }
}

int main()
{
    ifstream file ( "file.csv" ); // declare file stream: http://www.cplusplus.com/reference/iostream/ifstream/
    string value;
    list<string> values;
    while ( file.good() )
    {
        getline ( file, value, ',' ); // read a string until next comma: http://www.cplusplus.com/reference/string/getline/
        if (value.find('\n') != string::npos) {
            split_line(value, "\n", values);
        } else {
            values.push_back(value);
        }
    }

    list<string>::const_iterator it = values.begin();
    for (it = values.begin(); it != values.end(); it++) {
        string tmp = *it;
        double d;
        d = strtod(tmp.c_str(), NULL);
        cout << "Double val: " << right << showpoint << d << endl;
    }
}

```

---

### Post by dwhitney67 on 2012-06-13
> **jsmidt said:**
> 
Does anyone know how I can alter my read.cpp file above to handle comma delimiters?  To read into 3 double arrays and write data back to screen?  Thanks!

An easy way to parse simple data, such as CSV, is to use the Boost Tokenizer class.

Here's an example that places the values of each row into a separate "array" (actually, vector):
```

#include <boost/tokenizer.hpp>
#include <fstream>
#include <string>
#include <vector>
#include <iostream>
#include <cstdlib>

int main(int argc, char** argv)
{
    using namespace std;

    if (argc != 2)
    {
        cerr << "Usage: " << argv[0] << " <csv file>" << endl;
        return -1;
    }

    vector< vector<double> > csv_values;

    fstream file(argv[1], ios::in);

    if (file)
    {
        typedef boost::tokenizer< boost::char_separator<char> > Tokenizer;
        boost::char_separator<char> sep(",");
        string line;

        while (getline(file, line))
        {
            Tokenizer info(line, sep);   // tokenize the line of data
            vector<double> values;

            for (Tokenizer::iterator it = info.begin(); it != info.end(); ++it)
            {
                // convert data into double value, and store
                values.push_back(strtod(it->c_str(), 0));
            }

            // store array of values
            csv_values.push_back(values);
        }
    }
    else
    {
        cerr << "Error: Unable to open file " << argv[1] << endl;
        return -1;
    }

    // display results
    cout.precision(1);
    cout.setf(ios::fixed,ios::floatfield);

    for (vector< vector<double> >::const_iterator it = csv_values.begin(); it != csv_values.end(); ++it)
    {
        const vector<double>& values = *it;

        for (vector<double>::const_iterator it2 = values.begin(); it2 != values.end(); ++it2)
        {
            cout << *it2 << " ";
        }
        cout << endl;
    }
}

```

---

### Post by jsmidt on 2012-06-13
Thank you everyone!

---

### Post by jsmidt on 2012-06-13
> **dwhitney67 said:**
> An easy way to parse simple data, such as CSV, is to use the Boost Tokenizer class.

Here's an example that places the values of each row into a separate "array" (actually, vector):
```

...

    for (vector< vector<double> >::const_iterator it = csv_values.begin(); it != csv_values.end(); ++it)
    {
        const vector<double>& values = *it;

        for (vector<double>::const_iterator it2 = values.begin(); it2 != values.end(); ++it2)
        {
            cout << *it2 << " ";
        }
        cout << endl;
    }
}

```

So this last part prints to the screen (thanks), but how do you load the 3 columns into 3 separate double arrays?  Using iterators instead of something like (int i = 0; i < 3; i++)  is confusing me as I know how to say a[i] = ... but not a[it] = ... and so not sure how to assign these values to double vectors a, b and c.

---

### Post by jsmidt on 2012-06-13
Nevermind.  Figured it out.  Can us the .at() function.

---

### Post by dwhitney67 on 2012-06-13
> **jsmidt said:**
> Nevermind.  Figured it out.  Can us the .at() function.

You can also use the square brackets [].  The STL vector offers a [] operator method.

---

### Post by jsmidt on 2012-06-13
dwhitney67.  One last question.  Is there a way to print the second element of info?  There does not seem to be info.at() available for the Tokenizer class nor does info[1] work as brackets [] seem to also not be defined.

---

### Post by dwhitney67 on 2012-06-13
> **jsmidt said:**
> dwhitney67.  One last question.  Is there a way to print the second element of info?  There does not seem to be info.at() available for the Tokenizer class nor does info[1] work as brackets [] seem to also not be defined.

The code sample I offered employs a vector of vectors, which is almost synonymous with the concept of an array of arrays.

Perhaps the following might make it easier to understand:
```

    for (size_t i = 0; i < csv_values.size(); ++i)
    {
        const std::vector<double>& values = csv_values[i];

        for (size_t j = 0; j < values.size(); ++j)
        {
            cout << values[j] << " ";
        }
        cout << endl;
    }

```
The 'csv_values' is the outer vector, which contains one or more inner vectors (which I dubbed 'values').

P.S.  The Tokenizer (which btw, is a typedef for a longer declaration) merely works on one line at a time from the file.  You have to use an iterator to access its values (as I have previously shown).

---

### Post by jsmidt on 2012-06-13
> **dwhitney67 said:**
> 

P.S.  The Tokenizer (which btw, is a typedef for a longer declaration) merely works on one line at a time from the file.  You have to use an iterator to access its values (as I have previously shown).

Okay so there is no way to access without iterators?  For example, what if my data looked like:
```

1.0,line1,2.0,3.0
2.0,line2,4.0,6.0
4.0,line3,8.0,12.0

```

Where the second element in each line is a string not double.  I believe your example code converts everything to a double but in this case I would like to keep the second element of each line as a string.  If I can't access the second element of info such as info[1] how can I make your code only convert the first, second and fourth entries to doubles and the rest to doubles?

Sorry for so many questions.  Just trying to figure out how to do if statements for when sometimes they are doubles and sometimes strings.

---

### Post by roelforg on 2012-06-14
> **jsmidt said:**
> Okay so there is no way to access without iterators? For example, what if my data looked like:
```

1.0,line1,2.0,3.0
2.0,line2,4.0,6.0
4.0,line3,8.0,12.0

```
 
Where the second element in each line is a string not double. I believe your example code converts everything to a double but in this case I would like to keep the second element of each line as a string. If I can't access the second element of info such as info[1] how can I make your code only convert the first, second and fourth entries to doubles and the rest to doubles?
 
Sorry for so many questions. Just trying to figure out how to do if statements for when sometimes they are doubles and sometimes strings.
 
The way i did it, just have it push the values directly to the result vector instead of through the tmp vector.
I did it that way because csv's tend to be layed out like this:
         |COL1|COL2|...
ROW1|
ROW2|
........ |
And my way preserves the rows.

---

### Post by dwhitney67 on 2012-06-14
> **jsmidt said:**
> Okay so there is no way to access without iterators?  For example, what if my data looked like:
```

1.0,line1,2.0,3.0
2.0,line2,4.0,6.0
4.0,line3,8.0,12.0

```

Where the second element in each line is a string not double.  I believe your example code converts everything to a double but in this case I would like to keep the second element of each line as a string.  If I can't access the second element of info such as info[1] how can I make your code only convert the first, second and fourth entries to doubles and the rest to doubles?

Sorry for so many questions.  Just trying to figure out how to do if statements for when sometimes they are doubles and sometimes strings.

Only you will know what you data structure is; thus you will have to adjust your code as necessary.  If you are expecting the second column to always be a string, then use a conditional (ie if statement) to check when you are processing that particular field.

The Tokenizer parses the data as strings, not doubles.  It is only when strtod() is called that the string gets converted to a value.

Re-examining the code I posted, it could be adjusted as follows:
```

Tokenizer info(line, sep);   // tokenize the line of data
vector<double> values;
**int column = 0;**

for (Tokenizer::iterator it = info.begin(); it != info.end(); ++it, **++column**)
{
    if (column != 1)
    {
        // convert data into double value, and store
        values.push_back(strtod(it->c_str(), 0));
    }
    else
    {
        // do something, if anything, with string column.
        string columnName = *it;
    }
}

```

---

