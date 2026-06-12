---
title: "[SOLVED] C++ - Reading string in a while loop"
date: 2008-11-16
forum: Programming Talk
---

### Post by Despot Despondency on 2008-11-16
Hi, I'm just trying to write a simple program to calculate the length of the smallest string in the input. However, when I try to read the strings in a while loop the loop never ends. Here's my code

```

#include <algorithm>
#include <iostream>
#include <string>
#include <vector>

using std::cin;
using std::cout;
using std::endl;
using std::string;
using std::vector;

int main()
{

  cout << "Please enter your text: ";

  typedef string::size_type string_size;

  vector<string_size> word_lengths;
  string x;

  while(cin >> x)
    word_lengths.push_back(x.size());

  sort(word_lengths.begin(),word_lengths.end());

  cout << "The smallest word in the text was of length " << word_lengths[0] << endl;

  return 0;

}

```

Any help would be appreciated. Cheers.

---

### Post by Idefix82 on 2008-11-16
You didn't build in any means of telling the program that the input has finished. You could for example check the value of the string and exit if the value is "x" or "q" or whatever you wish or count the number of words and exit after the 10th.

---

### Post by dwhitney67 on 2008-11-16
> **Idefix82 said:**
> You didn't build in any means of telling the program that the input has finished. You could for example check the value of the string and exit if the value is "x" or "q" or whatever you wish or count the number of words and exit after the 10th.
+1

[edited]

---

### Post by Despot Despondency on 2008-11-16
Thanks for your responses. I was taking my code from a similar example in my book, 'accelerated c++', only they where reading in doubles. There was a bit in the code that was doing whet you were suggesting only it didn't actually say that. Cheers for your help.

---

