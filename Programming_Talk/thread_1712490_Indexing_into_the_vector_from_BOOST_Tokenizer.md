---
title: "Indexing into the vector from BOOST Tokenizer"
date: 2011-03-22
forum: Programming Talk
---

### Post by m.dr on 2011-03-22
Hello -

I am using Boost Tokenizer to parse lines from a file. I am using the char separator. I need to index into the vector that the Tokenizer returns and compare each string in the vector to determine conditions. I am a little new to C++ (a few months now) but with a strong Java background.

So my main fileManager routine is such:

string data(configFileName_);
ifstream configFile(data.c_str());
if (!configFile.is_open()) return inputConfigurations;
while (getline(configFile, line)) {
TokenizerChar tokens(line); //defined as a Boost tokenizer with char separator
vectorTokens.assign(tokens.begin(),tokens.end());
inputConfigurations->assembleTokens(&vectorTokens); //here I have problem as defined in next snippet
}

so in InputConfiurations.assembleTokens defined as
-------------------------
void InputConfigurations::assembleTokens (VECTOR_String *vectorTokens) {
char* x = "SETUP"; //also tried string x = "SETUP"
char* y = vectorTokens[1];
if (boost::iequals(x, y)) {
//configType = vectorTokens[2];
};
}


I have tried various things - essentially I want to check if:
vectorTokens[1] == "SETUP" //the word SETUP
similarly I want to check for vectorTokens[2] and such.

What is the best way to do this - I tried strncmp, compare but in general get the following error:

src/Grains/InputConfigurations.cpp:25: error: cannot convert ‘std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >’ to ‘char*’ in initialization

Hope I have explained the situation. I see that the Tokenizer has iterators and such but I need to find the value of the string in certain locations and decide based on that - and if I use an iterator it will be too many if-then and also very kludgy.

Btw my input is such - so beased on SETUP, BOUNDS will perform certain functions (create certain structures).
SETUP CACHE
BOUNDS SIZE 64000
VALUES C B S
START 1 1 1
END 5 5 5
INSTANCE 3 3 3

Thank you much for your help in advance and hope I have explained the situation in as much detail as possible.

---

### Post by Some Penguin on 2011-03-23
First, use 'code' tags.

Second, read the error message.  The error message and 
```

VECTOR_String *vectorTokens)

```
are enough to tell you that vectorTokens is a pointer to a vector of strings, *not* a pointer to a string.  It makes no sense to attempt to take a single vector of strings (i.e. *vectorTokens -- dereferencing the pointer to a vector of strings) and assign that to a char*.

```

(*vectorTokens)[0]

```

would be the first String within the vector of strings pointed to by the argument.

---

### Post by m.dr on 2011-03-23
Thanks! I got it resolved.Appreciate your pointer.

Btw what do you mean by 'code tags'?

Thanks.

---

