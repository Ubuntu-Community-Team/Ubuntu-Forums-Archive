---
title: "A C++ question."
date: 2009-10-20
forum: Programming Talk
---

### Post by jianan77818 on 2009-10-20
I have a homework problem, and I tired my best to do it. But it still have a lot of error, so can someone teach me what should I do to fix it? Please help me out.

Write a program that reads a string containing exactly    four words (separated by * symbols) into a single string object.     Next, extract each word from the original string and store each word in    a string object.  Then concatenate the words in reverse    order to form another string.  Display both the original and    final strings.  (Hint: To extract the words, you should use    the find member function to find each symbol *, assign the characters up to    the * to one of the four string objects, and then remove those characters from    the original string.)
   


#include <iostream>
#include    <string>

using namespace std;

int    main()
{

    string original;
       double remove_1;
    double remove_2;
       double remove_3;
    double remove_4;
       string star;
    string word_1;
    string    word_2;
    string word_3;
    string    word_4;
    string reverse_1;
    string    reverse_2;
    string reverse_3;
       string reverse_4;
    string    final;


    cout << "Please enter your    words..." << endl;
    cin >>    original;
    cout << "Please enter your method of    spacing..." << endl;
    cin >>    star;


    remove_1 =    original.find(star);
    reverse_1.assign(original, 0,    remove_1);
    original.erase(0,    remove_1);
    remove_2 =    original.find(star);
    reverse_2.assign(original, 0,    remove_2);
    original.erase(0,    remove_2);
    remove_3 =    original.find(star);
    reverse_3.assign(original, 0,    remove_3);
    original.erase(0,    remove_3);
    remove_4 =    original.find(star);
    reverse_4.assign(original, 0,    remove_4);
    final = reverse_4 + "*" + reverse_3 + "*" +    reverse_2 + "*" + reverse_1;

    cout << "The    original string was: " << original << endl;
       cout << "The reversed string is: " << final <<    endl;

return(0);
}

---

### Post by gktaylor on 2009-10-20
A couple of hints...

0. include frequent cout << myvariable << endl; statements for development purposes. You need to see that each statement is having the operation that you intended.
1. Save the original as another variable before you start erasing words from it.
2. original.erase(0, remove_1+1); will remove the word and the following star
3. for the fourth word, do not find a "*" as there are only three.

Best of luck!

---

### Post by dwhitney67 on 2009-10-20
Be aware that if the word-separator were a space (or tab) instead of a printable character (eg. '*'), that the following statement would not work as you would want:
```

cout << "Please enter your words..." << endl;
cin >> original;

```
Use getline() instead to read the entire input line; then armed with your delimiter, you can parse the string successfully.

Use something like the following to get input with respect to the delimiter:
```

   cout << "\nEnter the delimiter used, or <RTN> if white-space used: ";
   getline(cin, delimiter);

   if (delimiter.size() == 0)
   {
      delimiter = " ";
   }

```

Now, as for the rest of your code, you should think about the process that is required to examine a string for delimiters, an extract words.

If you envision it in your mind, you will (hopefully) realize that it is a repetitive process.  You should not need to have as many variables declared as you have.  All that is required are the obvious original string and the delimiter string, the reversed string, and a couple of position markers so that you can keep track of where you are when parsing the original string.

If you need to replace a character within the original string, you can use the operator[] function.  For example:
```

original[pos] = ' ';

```
The method find() can assist you in locating the delimiter(s), and substr() can assist with picking apart the string for the individual words.

Put these concepts to work in a loop, and voila you should be able to have the prettied original string and its reverse image.

P.S.  If you do not heed the advice above, think of the repercussions if say, your instructor were to change the input string to be five words, instead of four.  Your program would not capture the last word!

---

### Post by interval1066 on 2009-10-20
Seems like a string tokenizing template would be an ideal solution for something like this. Would cut down on the amount of global vars (to zero) and make it much more readable.

---

### Post by dwhitney67 on 2009-10-20
> **interval1066 said:**
> Seems like a string tokenizing template would be an ideal solution for something like this. Would cut down on the amount of global vars (to zero) and make it much more readable.

I agree; why not just forgo the learning process of tokenizing strings the manual way, and use something like [Boost's Tokenizer class]("http://www.boost.org/doc/libs/1_38_0/libs/tokenizer/index.html").

I'm sure the OP's instructor will be impressed that his student used the ingenuity of others for tokenizing the input string, and disregarded the project's requirements for the sake of saving a few lines of code.

---

### Post by unknownPoster on 2009-10-20
> **dwhitney67 said:**
> I agree; why not just forgo the learning process of tokenizing strings the manual way, and use something like [Boost's Tokenizer class]("http://www.boost.org/doc/libs/1_38_0/libs/tokenizer/index.html").

I'm sure the OP's instructor will be impressed that his student used the ingenuity of others for tokenizing the input string, and disregarded the project's requirements for the sake of saving a few lines of code.

I have to agree with this.

Back in my introductory Computer Science classes, taught in C, we were never allowed to use anything other than math.h, stdio.h, stdlib.h, and assert.h as using anything "advanced" was considered cheating.

Regardless, implementing a string tokenizer, delimited by whitespace, using a stringStream is fairly easy to do. If I remember correctly, I was able to do it in less than 10 lines. I'll have to look at it later...

---

### Post by dwhitney67 on 2009-10-20
> **unknownPoster said:**
> ...

Regardless, implementing a string tokenizer, delimited by whitespace, using a stringStream is fairly easy to do. If I remember correctly, I was able to do it in less than 10 lines. I'll have to look at it later...
You probably could do this in less than 10 lines.  IMO, no one would consider this approach to be "advanced programming", but nevertheless, based on the OP's requirements that the delimiter is an '*', I don't know if this approach is achievable.

It sure would be nice if the OP would chime in to let us know if he has achieved a working solution.

---

### Post by jianan77818 on 2009-10-20
I already figured it out. Thanks for all the reply. :)

---

### Post by unknownPoster on 2009-10-21
> **dwhitney67 said:**
> You probably could do this in less than 10 lines.  IMO, no one would consider this approach to be "advanced programming", but nevertheless, based on the OP's requirements that the delimiter is an '*', I don't know if this approach is achievable.

It sure would be nice if the OP would chime in to let us know if he has achieved a working solution.

Well, since the OP has finished, I'll post my old code, granted it's just a little function within a class. 

```

void tokenize(string input)
{
    string buf; 
    stringstream s(input); 

    while (s >> buf)
        tokens.push_back(buf); //tokens is a vector<string>
}


```

---

### Post by dwhitney67 on 2009-10-21
To meet the OP's requirements, I have done it as such:
```

#include <string>
#include <iostream>

int main()
{
   std::string original;
   std::string reversed;
   std::string delimiter;

   std::cout << "Enter multiple words separated by a common delimiter:" << std::endl;
   getline(std::cin, original);

   std::cout << "\nEnter the delimiter used, or <RTN> if white-space used: ";
   getline(std::cin, delimiter);

   if (delimiter.size() == 0)
   {
      delimiter = " ";
   }

   size_t curr_pos = 0;
   size_t prev_pos = 0;

   while (curr_pos != std::string::npos)
   {
      curr_pos = original.find(delimiter, curr_pos);
      reversed = original.substr(prev_pos, curr_pos - prev_pos) + reversed;

      if (curr_pos != std::string::npos)
      {
         reversed = " " + reversed;
         original[curr_pos] = ' ';
         prev_pos = ++curr_pos;
      }
   }

   std::cout << "Original string: " << original << std::endl;
   std::cout << "Reversed string: " << reversed << std::endl;
}

```

---

