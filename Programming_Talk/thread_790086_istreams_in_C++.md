---
title: "istreams in C++"
date: 2008-05-11
forum: Programming Talk
---

### Post by dodu3784 on 2008-05-11
Hello everybody,
I am doing a program that reads from a text file and display what he reads. The only fact is that I don't know what should be the format of the file my program program is reading from, i.e. I tried file_to_read.txt but the compiler did not recognize this format. I am working with xemacs.
Thank you very much

---

### Post by WW on 2008-05-11
> **dodu3784 said:**
> Hello everybody,

Hey dodu3784!
> **dodu3784 said:**
> 
I am doing a program that reads from a text file and display what he reads. The only fact is that I don't know what should be the format of the file my program program is reading from, i.e. I tried file_to_read.txt but the compiler did not recognize this format.
I am confused by your question.  You talk about the "format of the file", which to me sounds like you are talking about the *contents* of the file.  You say the compiler did not recognize the format of "file_to_read.txt".  Is the problem with the *contents* of the file, or the *name* of the file?

Please explain a little more about what you are trying to do. Also, please show the code that you wrote, the commands that you executed, and the error messages that you see.

> 
 I am working with xemacs.

Unless I completely misunderstand what you are asking, the editor that you are using is not relevant.

---

### Post by JupiterV2 on 2008-05-11
As WW wisely stated, it sound more like you want to know a method of organizing data within a text file. There are many methods to use but it sounds like either using CSV (comma seperated values) or using any other method you devise to break up the data is what you desire.

Then, once your data has been entered into the text file (name it whatever you want: data.txt, something.csv, anything.dat...) and parse the input you read from the file using the method you want to implement.

---

### Post by Jessehk on 2008-05-11
Given a file test.txt such as
```

this
is
a
test

```

The code to read each line of the file is:
```

#include <iostream>
#include <fstream>
#include <string>

int main() {
    std::ifstream in( "test.txt" );
    std::string line;

    while ( std::getline( in, line ) )
        std::cout << line << std::endl;
}

```

---

