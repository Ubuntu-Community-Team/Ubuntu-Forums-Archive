---
title: "C++ istream / stringstream problem"
date: 2008-10-10
forum: Programming Talk
---

### Post by irrdev on 2008-10-10
I am sure that there is an easy way to make this work, but I am rather new to using the std library. I am currently using a stringstream like this:
[PHP]

        std::string source = "int x; x=10;";

        std::string search = ";";
        std::stringstream replaced("");
        std::string buffer = "";
        std::string replace = " ; ";
        std::stringstream original(source);

        while (original >> buffer)
        {
            if (buffer == search)
            {
                replaced << replace << " ";
            }
            else
            {
                replaced << buffer << " ";
            }
        }[/PHP]
What I am trying to do, is to take the "source" string and replace every occurrence of ";" with " ; ". The problem is that the >> operator tokenizes the "original" stringstream by whitespaces and stores entire words into the "buffer". For example, the second reiteration of the loop returns *"x;"*.I would like to instead have the >> operator either tokenize by the ";" character, or instead have the >> operator do single-character input from the stringstream. How would I do this?

Thank you in advance for your help.

---

### Post by dribeas on 2008-10-10
> **irrdev said:**
> I would like to instead have the >> operator either tokenize by the ";" character, or instead have the >> operator do single-character input from the stringstream. 

You should use a tokenizer library (or implement yours). Consider using boost::tokenizer. Implementing your own tokenizer if your splitting pattern is just ; is fairly simple, but getting to know boost libs will be helpful in the long term.

---

