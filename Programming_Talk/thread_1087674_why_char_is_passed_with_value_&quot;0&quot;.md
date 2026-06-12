---
title: "why char* is passed with value &quot;0&quot;?"
date: 2009-03-05
forum: Programming Talk
---

### Post by tneva82 on 2009-03-05
Strange bug I got when I altered piece of code. Basicly what happens:

```
vector<char*> creatureData; //which is filled with data
vector<creature*> allCreatures;

char *line=new char[256];
strcpy(line, creaturesData[i]);
allCreatures.push_back(new creature(line));
```

when I print out parameter on the creature's constructor I get 0. If I print out line before call there's big nice string as supposed to. What did I screw up?

Originally I had vectors element passed straight up but then I thought maybe that's the reason so created temporal buffer. Didn't solve it.

---

### Post by eye208 on 2009-03-05
Not enough info. What does the constructor look like? How do you print out the value of line?

---

### Post by dwhitney67 on 2009-03-05
Why are you using a a vector<char*>??  It would be better easier to use vector<string>.

---

### Post by tneva82 on 2009-03-05
> **eye208 said:**
> Not enough info. What does the constructor look like? How do you print out the value of line?

Constructor is supposed to parse the char* into pieces. I put before that happens though simple line:

while(1) { printf("%s\n", line); }

Yeah infinite loop. Before it segfaulted which has habit of preventing previous print so I have found this to be quick&easy solution to find value of variable(another is write it to file but that takes 3 lines).

---

### Post by tneva82 on 2009-03-05
> **dwhitney67 said:**
> Why are you using a a vector<char*>??  It would be better easier to use vector<string>.

Easier to simply use char* rather than keep switching between string and char*. Since functions that take char* as parameter don't understand string can't use just string.

---

### Post by dwhitney67 on 2009-03-05
> **tneva82 said:**
> Easier to simply use char* rather than keep switching between string and char*. Since functions that take char* as parameter don't understand string can't use just string.
:confused:

Define all of your functions to use std::string.  When you pass a hard-coded literal string, it gets converted auto-magically.  If you need to call a C-library function (and I can't imagine why) that requires a const char*, then use the c_str() function of std::string.

When receiving data from SDL_net, just use a regular char buffer (no need to allocate it; just declare the damn thing on the stack).
```

std::vector<std::string> messages;
char buf[256] = {0};
if (SDLNet_TCP_Recv(sd, buf, sizeof(buf) - 1) > 0)
{
  messages.push_back(buf);
}

```

---

### Post by tneva82 on 2009-03-05
> **dwhitney67 said:**
> Define all of your functions to use std::string.

Oh sure. All I then need is to rewrite whole bunch of standard library code. Yeah. Piece of cake :D That sounds like fun little project ;-) Or maybe not with my skills...I figure professional coders can do more robust and faster versions of them than I could do.

And it's not just passing strings to C functions but otherway around

---

### Post by Simian Man on 2009-03-05
Use std::string, dwhitney67 already mentioned the .c_str( ) function.  Your code is confusing, error-prone and dangerous.

---

### Post by dwhitney67 on 2009-03-05
> **tneva82 said:**
> Oh sure. All I then need is to rewrite whole bunch of standard library code. Yeah. Piece of cake :D That sounds like fun little project ;-) Or maybe not with my skills...I figure professional coders can do more robust and faster versions of them than I could do.

And it's not just passing strings to C functions but otherway around

Basically, you are unwilling to part with strcpy(), strtok(), strcmp(), etc... similar to a one- or two-year old when they are denied a baby bottle for their milk.

Get over the C standard library if you plan to program in C++.  C++ features a rich library which solves most of the issues you write about, but since it seems that you don't want to progress your knowledge, then damn, program in C.

---

### Post by tneva82 on 2009-03-05
> **dwhitney67 said:**
> Basically, you are unwilling to part with strcpy(), strtok(), strcmp(), etc... similar to a one- or two-year old when they are denied a baby bottle for their milk.

I use what I'm most comfortable with. Never been comfortable with string class, even less with their ioclasses, haven't seen anything that does the job of strtok(which my program depends heavily. No strtok equilavent, no go. Is there equilavent of fscanf either? Another function that is absolutly _essential_ and used more than I dare to count. If there's not equilavent in c++ then it's just ugly situation when I have to redesign design from the scratch).

> Get over the C standard library if you plan to program in C++.  C++ features a rich library which solves most of the issues you write about, but since it seems that you don't want to progress your knowledge, then damn, program in C.

I use tools that help me. C++ has tools I find useful so I use them. But if they don't have tools I need(like strtok. Point me to c++ function that does same job? I have tried to look but haven't found so far one) I use them. Simple as that. I use whatever allows me to get the job done most easily.

---

### Post by dwhitney67 on 2009-03-05
> **tneva82 said:**
> I use what I'm most comfortable with. Never been comfortable with string class, even less with their ioclasses, haven't seen anything that does the job of strtok(which my program depends heavily. No strtok equilavent, no go. Is there equilavent of fscanf either? Another function that is absolutly _essential_ and used more than I dare to count. If there's not equilavent in c++ then it's just ugly situation when I have to redesign design from the scratch).



I use tools that help me. C++ has tools I find useful so I use them. But if they don't have tools I need(like strtok. Point me to c++ function that does same job? I have tried to look but haven't found so far one) I use them. Simple as that. I use whatever allows me to get the job done most easily.

With Boost, a tokenizer class exists that allow one to reap the tokens from a string.

If you don't want to use boost, then here's strtok()... my version:
```

std::vector<std::string> strtok(const std::string& str, const std::string& delim)
{
  std::vector<std::string> tokens;

  size_t pos = 0;
  size_t loc = str.find_first_of(delim, pos);

  if (loc == std::string::npos)
  {
    tokens.push_back(str);
  }
  else
  {
    while (loc != std::string::npos)
    {
      tokens.push_back(str.substr(pos, loc - pos));
      pos = loc + 1;
      loc = str.find_first_of(delim, pos);
    }
  }

  return tokens;
}

```

Example usage:
```

void displayString(const std::string& str)
{
  std::cout << str << std::endl;
}

int main()
{
  const std::string        line   = "abc*def*ghi*jkl*";
  std::vector<std::string> tokens = strtok(line, "*");

  std::for_each(tokens.begin(), tokens.end(), displayString);
}

```

---

### Post by Can+~ on 2009-03-05
> **dwhitney67 said:**
> Get over the C standard library if you plan to program in C++.  C++ features a rich library which solves most of the issues you write about, but since it seems that you don't want to progress your knowledge, then damn, program in C.

Funny, I thought that was one of C++'s strengths. (Flamebait!)

As for the OP:
[http://www.linuxforums.org/forum/linux-programming-scripting/28655-c-strings.html](http://www.linuxforums.org/forum/linux-programming-scripting/28655-c-strings.html)

And I imagine you could write easily a home-made function that could split into the desired tokens. (Edit: lol, dwhitney already did)

---

### Post by the_unforgiven on 2009-03-06
> **Can+~ said:**
> 
As for the OP:
[http://www.linuxforums.org/forum/linux-programming-scripting/28655-c-strings.html](http://www.linuxforums.org/forum/linux-programming-scripting/28655-c-strings.html)

Good to see my post helping cross-forum users :p

---

### Post by cogitordi on 2010-03-01
> **dwhitney67 said:**
> If you don't want to use boost, then here's strtok()... my version:
```

std::vector<std::string> strtok(const std::string& str, const std::string& delim)
{
  std::vector<std::string> tokens;

  size_t pos = 0;
  size_t loc = str.find_first_of(delim, pos);

  if (loc == std::string::npos)
  {
    tokens.push_back(str);
  }
  else
  {
    while (loc != std::string::npos)
    {
      tokens.push_back(str.substr(pos, loc - pos));
      pos = loc + 1;
      loc = str.find_first_of(delim, pos);
    }
//ZNOTE: Need to add the final piece to vector!
  }

  return tokens;
}

```

Thanks for this code, dwhitney67! This is the way to do it in C++, folks. It's a clear and tidy solution to the problem of tokenizing or splitting a string using a delimiter in C++. The WWW is an unsemantic mess so I am adding a few search keywords to this thread. (o; 

One modification needs to be made: where you see my NOTE in the quoted code, we must add the remainder of the string to the vector.

Suggestion:
if (pos <= str.size()-1) 
tokens.push_back( str.substr(pos, str.size()-pos)  );

---

### Post by dwhitney67 on 2010-03-01
> **cogitordi said:**
> 
Suggestion:
if (pos <= str.size()-1) 
tokens.push_back( str.substr(pos, str.size()-pos)  );
Sorry about that; you are correct.

When I tested, I assumed the string was delimited by one of the *visible* chars in the delim string.  I forgot to consider the null-byte.

If you want to shorten the code a bit, use string's substr() default parameter for the second arg.
```

if (pos < str.size())
{
   tokens.push_back(str.substr(pos));
}

```

---

