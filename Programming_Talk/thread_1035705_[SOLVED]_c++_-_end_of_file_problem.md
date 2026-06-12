---
title: "[SOLVED] c++ - end of file problem"
date: 2009-01-10
forum: Programming Talk
---

### Post by Despot Despondency on 2009-01-10
Hey, I'm having a problem with my program that is meant to read a file into a vector<string>. Here's the code

```

#include "read_in_file.h"

#include <fstream>
#include <iostream>

using namespace std;

vector<string> read_in_file_vec(string filename){

  string line;

  ifstream file (filename.c_str());
  
  vector<string> text;  

  if(file.is_open()){

    while(!file.eof()){

      getline(file,line);

      cout << line << endl;

      text.push_back(line);

    }
    file.close();
  }
  else
    cout << "Could not open file" << endl;
}

```

Now when I run the code on a file called "teams" I get the following output

```

Liverpool
Chelsea
Man Utd
Aston Villa
Arsenal
Everton
Wigan
Hull
Fulham
West Ham
Bolton
Portsmouth
Man City
Newcastle
Sunderland
Tottenham
Middlesbrough
Stoke
Blackburn
West Brom
Segmentation fault

```

It seems to be a problem with the end of file, as 'West Brom' is the last line in the file. I don't understand why I'm getting this error. Any help would be appreciated.

---

### Post by lloyd_b on 2009-01-10
I'm not really that familiar with C++ (mostly program in straight C), but I suspect the problem is that file.eof() isn't returning TRUE until after a getline() actually fails because of EOF, and the text.push_back() doesn't like what it's finding in "line" after the failure.

Try this instead:
```
while(file.is_open()) {
    getline(file, line);
    if (file.eof()) {
        file.close();
    } else {
        cout << line << endl;
        text.push_back(line);
    }
}
```

Lloyd B.

---

### Post by Despot Despondency on 2009-01-10
Hey, thanks for your response. I've changed the code but I'm still getting a segmentation fault. It seems to occur when I'm trying to close the file. Is there a specific reason why this could happen?

---

### Post by monkeyking on 2009-01-10
remember to have a return statement in you read_in_file_vec()



Remember when you compile to use the -Wall flag.
This will catch some mistakes.

---

### Post by Despot Despondency on 2009-01-10
Doh... Can't believe I missed that. Strange that it didn't come up during compilation though. Cheers for the help.

---

