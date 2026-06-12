---
title: "C++ strings appear to not compare correctly"
date: 2009-01-27
forum: Programming Talk
---

### Post by Tatty on 2009-01-27
Forgive me if the answer to this is something simple and I am being stupid, I make no claim to be an expert or experienced programmer. 

I am having a strange problem comparing two strings in an application I am writing.  It will never give a positive result (ie. that they are equal).
I have tried comparing them with both == and compare().

In trying to solve this I have simplified my code and added all manner of temporary code to test all the values, so its current version doesnt look very elegent at all, but here is the main bit that is causing me issue:

```
                string temp1 = thePupil->username;
                string temp2 = vecAllPupils[i]->username;
                
                cout << "\n\nSTART\ntemp1:" << temp1 << "::";              
                cout <<"\ntemp2:" << temp2 << "::";
                
                if(temp1 == temp2){
                    cout << "\n -- EQUAL --";
                }
                cout << "\nEND";
```

thePupil is a pointer to a struct called stPupil, in which username is a string object, vecAllPupils is a vector of stPupil objects. 

Here is the stPupil declaration:

```
struct stPupil{
    std::string firstname;
    std::string surname;
    std::string username;
    std::string password;
    std::string emailAddress;
    stPupil(std::string newFirstname, std::string newSurname);
};
```

Here is Part of the output from the application:

```
START
temp1:testta::
temp2:testta::
END

START
temp1:testta::
temp2:test2ta::
END
```

As you can see, the second of the two iterations has differnt values for temp1 and temp2.  However the first iteration appears to contain the same data but they were not judged to be the same for some reason and it did not print "-- EQUAL --"

What confuses me the most is that I have tested strings before without issue, and I just cant see what I am doing differently this time.

I imagine there is either something stupid im overlooking, or there is something about strings that I am not understanding.

---

### Post by wd5gnr on 2009-01-27
try:

if (!temp1.Compare(temp2)) .....

Try printing the length of temp1 and temp2 -- could there be a non printing character in there? Seems doubtful since you see the :: in the output, but something to try.

---

### Post by Tatty on 2009-01-27
> **wd5gnr said:**
> try:

if (!temp1.Compare(temp2)) .....

Try printing the length of temp1 and temp2 -- could there be a non printing character in there? Seems doubtful since you see the :: in the output, but something to try.

Thanks for the reply wd5gnr.

Using .compare() didnt seem to make a difference.  I changed the if statement to if(!temp1.compare(temp2)) but it still did not evaluate them as equal.

However I then followed your second suggestion and modified the testing output to print the string size like so:
```
                cout << "\n\nSTART\ntemp1:" << temp1 << "::string size:" << temp1.size();              
                cout <<"\ntemp2:" << temp2 << "::" << "string size:" << temp2.size();
```

And I got this:

```
START
temp1:testta::string size:7
temp2:testta::string size:6
END

START
temp1:testta::string size:7
temp2:test2ta::string size:7
END
```

What could account for the difference in the string size when they are both printing the same characters to a terminal?

---

### Post by geirha on 2009-01-27
Try printing the hex values of each character in the strings.
```

cout << hex;
for (int i= 0; i < temp1.size(); i++)
    cout << (int)temp1[i] << " ";

```

---

### Post by Simian Man on 2009-01-27
It's possible that the first string has a carriage return character in it.  When this character is printed, it causes the output to go back to the left of the screen.  These characters sometimes come up when reading text files from Windows which uses \r\n to end lines.

It is also possible that you have a backspace control character, but I have never seen that in practice.

Take geirha's suggestion and look for characters less than 32.

---

### Post by Tatty on 2009-01-27
Thank you all so much,

After printing the hex values, I noticed that certain strings appeared to have a 0 added to the start, which is why it was not evaluating to be equal.

I eventually managed to track the issue to a problem in the input to my application.  There was an extra space I left in a text file it was reading data from, once I removed it everything worked.

I still dont quite follow why the space was not printing correctly with cout, however it has for now enabled me to carry on.  

Thanks again.

---

### Post by wd5gnr on 2009-01-27
Score ;-)

---

