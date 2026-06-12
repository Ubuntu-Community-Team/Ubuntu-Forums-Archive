---
title: "[C++] Beginner Question - Counting words"
date: 2011-03-16
forum: Programming Talk
---

### Post by abraxyz on 2011-03-16
I was doing this exercise from the Primer Plus book:

> Write a program that uses an array of *char* and a loop to read one word at a time until
the word *done* is entered. The program should then report the number of words entered
(not counting *done*). A sample run could look like this:

Enter words (to stop, type the word done):
[B]anteater birthday category dumpster
envy finagle geometry done for sure[/B]
You entered a total of 7 words.

You should include the cstring header file and use the strcmp() function to make the
comparison test.So, this should be the solution:

```
#include <iostream> 
#include <cstring>
const int STR_LIM = 50; 
int main() 
{ 
    using namespace std; 
    char word[STR_LIM]; 
    int count = 0; 
     
    cout << "Enter words (to stop, type the word done):\n"; 
     
    while (cin >> word && strcmp("done", word)) 
        ++count; 
 
    cout << "You entered a total of " << count << " words.\n"; 
    return 0;  
}
```And it does work. But, one thing I can't understand - how exactly is the word count distinguished from a mere use of the *cin* object here?
Thanks.

---

### Post by Some Penguin on 2011-03-16
[http://www.cplusplus.com/reference/iostream/istream/operator%3E%3E/]("http://www.cplusplus.com/reference/iostream/istream/operator%3E%3E/")

"Extracts characters and stores them as a c-string (i.e. in succesive locations starting at location pointed by str and terminated by a null-character). Extraction ends when the next character is either a valid whitespace or a null character, or if the End-Of-File is reached.
The terminating null character is automatically appended after the extracted characters.

The extraction operation can be limited to a certain number of characters (thus avoiding the possibility of buffer overflow) if the field width (which can be set with ios_base::width or setw) is set to a value greater than zero. In this case, the extraction ends one character before the count of characters extracted reaches the value of field width, leaving space for the ending null character. After a call to this extraction operation the value of the field width is automatically reset to zero."

The latter part is rather important when you're accepting input you don't control into a fixed-length buffer, at least for real applications.

---

### Post by abraxyz on 2011-03-16
Thanks! I didn't know that. Funny thing - nowhere in the chapter is mentioned this *cin* behavior. So, the *word* array is getting overwritten in each cycle, and the word *count* is incremented by each whitespace from the input stream, am I right?

---

### Post by Some Penguin on 2011-03-16
count is being incremented each time.

'word' itself doesn't change; the contents of the memory addressed by word does.  The (these days, usually 32 or 64) bits of the 'word' variable will remain the same memory address -- the location of a 50-byte block (assuming one byte per character, which is practically always the case) in memory, which will not move during the program.  The contents of that 50-byte block will change.  If one of the words is "the", for instance, the first three bytes in the array will be overwritten with 't', 'h', 'e'; and the fourth byte will be overwritten by the zero byte.  The remaining 46 bytes would be unchanged.

And if the word were 'abcdefghijklmnopqrstuvwyzabcdefghijklmnopqrstuvywxyz', you would have a problem; cin would attempt to write all 52 characters, plus the null byte terminating a string.  The 50 bytes of the buffer would get 'a..x', while 'yz\0' would overwrite whatever came *after* -- which may or may not be a legal write.  If it's legal, you might clobber data which somebody else is planning to read later...

---

### Post by abraxyz on 2011-03-16
Great! Thanks. I've just tried it with:

```
cout << word[5];
```at the end.

-------

Btw, how would you go about extracting the same word, namely "done", from the continuous input stream without whitespaces, say: "abcdefghijklmnopqrstuvwyzabcdefghijkl***done***mnopqrstuvyw".

Beats me...

---

### Post by nvteighen on 2011-03-16
> **abraxyz said:**
> 
Btw, how would you go about extracting the same word, namely "done", from the continuous input stream without whitespaces, say: "abcdefghijklmnopqrstuvwyzabcdefghijkl***done***mnopqrstuvyw".

Beats me...

For instance, if you're working with the assumption that words are strings delimited by whitespace, then "done" in your example wouldn't be the word "done", but just something in a larger string.

But, if you really need or want to extract that you may:
1) Using "brute force": in each iteration of the while loop, check the last 4 letters and see whether they form "done". Of course, in each iteration you'd discard the "oldest" letter, advance the other three one place and then add the newest one at the end, in a stack-like fashion. In C++, you could use a STL stack for this.

2) But that's impractical for anything more complex than this, so the usual way to do that would be to use regular expressions. Ok, maybe it's possible to do this by using some clever combination of C strtok() and other standard functions that search for delimeters. But, IMO, a regular expression would do it better. The thing is that C and C++ don't support them natively (like Perl or Python do), so you'd have to use some library for it.

---

### Post by abraxyz on 2011-03-16
Thanks a bunch! This is all too advanced for me, but makes sense so far. I'll try the brute force style, and see what I come up with.

---

### Post by abraxyz on 2011-03-16
I did a bit of homework today. So here it is:

```
#include <iostream>
int main()
{
    using namespace std;
    char ch;
    cin.get(ch);
    while (cin)
    {
        while (ch == 'd')
        {
            cin.get(ch);
            while (ch == 'o')
            {
                cin.get(ch);
                while (ch == 'n')
                {
                    cin.get(ch);
                    while (ch == 'e')
                    {
                        cout << "Word found!" << endl;
                        return 0;
                    }
                }
            }
        }
        cin.get(ch);
    }
    return 0;
}
```So, It won't stop until the word is found, EOF condition, or an error.

---

### Post by abraxyz on 2011-03-17
And here's a better version, I couldn't help it. This is so cool. LOL

```
#include <iostream>
int main()
{
    using namespace std;
    
    char ch;
    int count = 0;
    int sum = 0;

    do
    {
        while (count == 0)
        {    
            cin.get(ch);
            count++;
            sum++;
        }
        count = 0;
        while (ch == 'd')
        {
            cin.get(ch);
            sum++;
            while (ch == 'o' && count < 1)
            {
                cin.get(ch);
                count++;
                sum++;
                while (ch == 'n' && count < 2)
                {
                    cin.get(ch);
                    count++;
                    sum++;
                    while (ch == 'e')
                    {
                        cout << "Word found!" << endl;
                        sum++;
                        cout << "Characters entered before word occurrence: ";
                        cout << sum - 5 << endl;
                        return 0;
                    }
                }
            }
        }
    }
    while (cin);
    return 0;
}

```

---

### Post by Arndt on 2011-03-17
> **abraxyz said:**
> And here's a better version, I couldn't help it. This is so cool. LOL

```
#include <iostream>
int main()
{
    using namespace std;
    
    char ch;
    int count = 0;
    int sum = 0;

    do
    {
        while (count == 0)
        {    
            cin.get(ch);
            count++;
            sum++;
        }
        count = 0;
        while (ch == 'd')
        {
            cin.get(ch);
            sum++;
            while (ch == 'o' && count < 1)
            {
                cin.get(ch);
                count++;
                sum++;
                while (ch == 'n' && count < 2)
                {
                    cin.get(ch);
                    count++;
                    sum++;
                    while (ch == 'e')
                    {
                        cout << "Word found!" << endl;
                        sum++;
                        cout << "Characters entered before word occurrence: ";
                        cout << sum - 5 << endl;
                        return 0;
                    }
                }
            }
        }
    }
    while (cin);
    return 0;
}

```

Good attempt, but there's a classic mistake in there. I think everyone does it, and not only once:

```
$ echo "foo xodone bar" | ./done
Word found!
Characters entered before word occurrence: 6
```

Fine, but:

```
$ echo "foo dodone bar" | ./done
$ 

```

---

### Post by abraxyz on 2011-03-17
Hey! Thanks for the insight. Just made a small change at line 19:

```
while (ch == 'd')
```[FONT=monospace]

[/FONT]to:[FONT=monospace]

[/FONT]```
while (ch == 'd' && count < 1)
```[FONT=monospace]
[/FONT]

---

### Post by forrestcupp on 2011-03-17
This is all a great learning experience to show why it's a lot easier to just use the string class whenever possible. :)

But about your original question, this program doesn't actually keep track of the words entered. That's not the intent. You're just using a single char array for a temporary storage space to keep track of how many times a word was entered. The incrementing of your 'count' integer has nothing to do with what is entered. It is just incremented any time anything other than 'done' is inputted.

---

### Post by dwhitney67 on 2011-03-17
> **abraxyz said:**
> Thanks a bunch! This is all too advanced for me, but makes sense so far. I'll try the brute force style, and see what I come up with.

Question... why didn't you just read in the entire line of input at once, into an STL string, then parse the string for the number of words?

Compare your approach to this:
```

#include <string>
#include <iostream>

int main(int argc, char** argv)
{
   std::string words;

   if (argc == 1)
   {
      std::cout << "Enter your word(s): ";
      std::getline(std::cin, words);
   }
   else
   {
      words = argv[1];
   }

   int count = 0;

   if (!words.empty())
   {
      ++count;

      size_t pos = 0;

      while ((pos = words.find(' ', pos)) != std::string::npos)
      {
         ++pos;
         ++count;
      }
   }

   std::cout << "Your input had " << count << " word(s)." << std::endl;
}

```

---

### Post by abraxyz on 2011-03-17
Yeah, that looks great, but it was a while loop exercise at the end of the chapter, so I kind of had to use limited amount of knowledge, and besides that, I haven't encountered some of the stuff from your code yet, even though it makes sense to me intuitively. Thanks for the suggestions.

---

