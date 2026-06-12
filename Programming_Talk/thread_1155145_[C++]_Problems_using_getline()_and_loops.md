---
title: "[C++] Problems using getline() and loops"
date: 2009-05-10
forum: Programming Talk
---

### Post by Bodsda on 2009-05-10
Hi, I'm trying to use getline() to iterate over a file and increment a variable to discover the number of lines in a file.

Heres the section of code im using

```

else if(!(strcmp(argv[i], "--store")))
            {
                
                string homedir = getenv("HOME");
                string filename = "/.alias.cheat";
                string fullpath = homedir + filename;

                ifstream alias_in(fullpath.c_str());

                string line;
                int num;

                if(alias_in.is_open())
                {
                while(getline(alias_in, line))
                    {
                        getline(alias_in, line);
                        cout << line << endl;
                        num++;
                    }

                    alias_in.close();
                }


                ofstream alias_out(fullpath.c_str());


                alias_out << num << ": "<< argv[(i + 1)];

                cout << "Stored: " << argv[(i + 1)] << endl;
                return 0;
            }

```

NOTE: Ive also tried using while(!(alias_in.eof())) which yields the same results

What I expect this code to do is check the file and for every iteration increment 'num' then when eof is reached it should store the sting given on the command line with the appropriate line number. For example, on a blank file
```
cheat --store "This is a test"
``` 
should result in ```
1: This is a test
``` being saved to the file, but instead I get
```
157884275: This is a test
```
Which looks to me as if its not stopping at the end of the file.

Any thoughts as to what im doing wrong would be much appreciated, thanks

Bodsda

---

### Post by poisonkiller on 2009-05-10
Try replacing "int num;" with "int num = 0;".

EDIT: And delete "getline(alias_in, line);" from that while loop, because "while(getline(alias_in, line))" already calls it.

---

### Post by Bodsda on 2009-05-10
> **poisonkiller said:**
> Try replacing "int num;" with "int num = 0;".

EDIT: And delete "getline(alias_in, line);" from that while loop, because "while(getline(alias_in, line))" already calls it.

Il try that cheers,

As for the edit, I was advised to try getline as the loop condition because it should return non true when eof is reached.

EDIT: Wicked, that worked, thanks a lot, now i have to look back at my book and append things to the file rather then trashing them :), thanks dude/dude'ette

---

