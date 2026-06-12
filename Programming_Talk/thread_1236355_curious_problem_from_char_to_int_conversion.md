---
title: "curious problem from char to int conversion"
date: 2009-08-10
forum: Programming Talk
---

### Post by abraxas334 on 2009-08-10
I have a very curious problem, when reading some data from 2 different files and doing a char to int conversion.

I have to files called test.1.dat test.2.dat, both contain a binary string of length 5 like this:
test.1.dat:
10011

test.2.dat
11011

for reading them my code looks a bit like this:

[PHP]
 int length = 5; //length of binary number
 vector<int>vLine(length,0);
 char temp;
 char line[length+1];
/*test1.1.dat  is the original file and for test.2.dat originalFile is false*/
 infile.open(filename.c_str());
    
    if(infile.good())
    {
        while(!infile.getline(line,length+1).eof())
        {

          
            if(originalFile)
            {

                    for(int i =0; i<vLine.size(); i++)
                    {

                        temp = line[i];
                        bit = atoi(&temp);
                        cout<<bit<<endl;
                        vLine[i]=bit;
                    }


                    OrigTraj.push_back(vLine);
                        
                    
                
            }
            else
            {

                    for(int i =0; i<vLine.size(); i++)
                    {
                        temp = line[i];
                        bit = atoi(&temp);
                        cout<<bit<<endl;
                        vLine[i]=bit;
                    }

                    comparingTraj.push_back(vLine);
                    
                }
            


        }
    }

    else{cout<<"File cannot be read!"<<endl;
    exit(2);
    
    }
    infile.close();


[/PHP]


if originalFile is true i.e the if statement is satisfied then the converted char values in the for loop are strange
the input file is 10011, which should result in vLine[0] = 1; vLine[1]=0; vLine[2]=0 ...etc. however all my 0's turn into an int value of 1 and my 1's into 11, so vLine would look like this:
11111111, now the bizare thing:
in the else part of the code (which is exactly the same) it does exactly what i want. i.e. vLine will be the string found in the file.
I hate messing with casting like this and i know very little about it. But this is really confusing. If anyone has any idea's why this could be i'd be very greatful :)
Thanks

---

### Post by Habbit on 2009-08-10
This might be a somewhat silly question, but have you tried to isolate the problem _within_ the code? I mean, have you (for example) tried to debug printing the vLine just read, then each char _before_ it is processed, then the parsed int value?

---

### Post by abraxas334 on 2009-08-10
i have printed out the line (from the get line bit) which is exactly as in the input file. and i have printed vLine, which is obviously just 0's from the initalisation, and then i have printed temp, which is the char value from the line, but when i print bit, i.e. after my casting attempt it turns into the 1's and 11's and only for one of the files. (and i have tried feeding the same file to both the if part and the else part), so yeah i really don't know what is going on.

---

### Post by Habbit on 2009-08-10
This _might_ be what's happening: temp is a single char, but atoi expects a C string, thus a sequence of chars terminated by a '\0'. When you pass it &temp, it reads your "temp" character, and then it keeps reading the following bytes on memory until it finds a zero byte (not '0' = 0x30, but '\0' = 0x00). The reason for it to fail only if "originalFile" is true may be as arcane as you want to imagine, and the result could change in another computer, compiler, whatever - you are on the fun land of "undefined behavior".

A possible solution would be to declare 'temp' as an array of two chars: you put your char in the temp[0], and keep temp[1]='\0', so you have a proper null-terminated C-string you can pass to atoi.

---

### Post by abraxas334 on 2009-08-10
is there any other way of doing this conversion? Where i can be sure its safe to do?
Ah maybe i can answer that myself it this this will work well enough for me:
[PHP] 
if(line[i] == '0')
                        {
                            vLine[i]=0;
                        }
                        else{vLine[i]=1;}

[/PHP]

---

### Post by abraxas334 on 2009-08-10
> **Habbit said:**
> This _might_ be what's happening: temp is a single char, but atoi expects a C string, thus a sequence of chars terminated by a '\0'. When you pass it &temp, it reads your "temp" character, and then it keeps reading the following bytes on memory until it finds a zero byte (not '0' = 0x30, but '\0' = 0x00). The reason for it to fail only if "originalFile" is true may be as arcane as you want to imagine, and the result could change in another computer, compiler, whatever - you are on the fun land of "undefined behavior".

A possible solution would be to declare 'temp' as an array of two chars: you put your char in the temp[0], and keep temp[1]='\0', so you have a proper null-terminated C-string you can pass to atoi.

And thanks this explanation makes a lot of sense, just shows again how little i know about the things i use....

---

### Post by Habbit on 2009-08-10
> **abraxas334 said:**
> And thanks this explanation makes a lot of sense, just shows again how little i know about the things i use....

Well, it's not that strange: the language, and thus the compiler, is allowing you to do something you shouldn't be able to, namely passing a pointer-to-a-single-element to a function that expects an array. The assimilation between pointers and arrays allows very powerful code, but with power comes responsibility. This situation is the same as [when people use]("http://www.parashift.com/c++-faq-lite/freestore-mgmt.html#faq-16.12") "delete arr;" on a pointer that was allocated with "arr = new T[n];" - the initial tone of a [fandango on core]("http://catb.org/esr/jargon/html/F/fandango-on-core.html").

---

