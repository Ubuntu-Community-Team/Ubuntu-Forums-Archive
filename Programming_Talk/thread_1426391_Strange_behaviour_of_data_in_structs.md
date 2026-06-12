---
title: "Strange behaviour of data in structs"
date: 2010-03-10
forum: Programming Talk
---

### Post by TMagic*04 on 2010-03-10
I was wondering if someone could explain this seemingly bizarre phenomenon to me. I have a vector of custom struct type address defined as such:
```

struct address{
  char add[11];
  char owner[5];
};
vector<address> aList;

```and is filled in this function:
```

void AFC:: generateAddressBatch()
{
  int index =0;
  string foo;
  //if none generate first 5
  if(aList.empty()) 
  {
    foo = "192.168.0.";
    char addr[11];
    memcpy(addr, foo.c_str(), foo.size());
    for (index; index < 5; index++)
    {
      struct address tmp;
      addr[10] = index + 48;
   
      memcpy(tmp.add, addr, sizeof(addr));
      tmp.owner[0] = 0;
      cout << "NEW ADDRESS GENERATED: " << tmp.add << endl;
      aList.push_back(tmp);
    }
  }
  else
  {
    index = aList.size() - 1;
    int max = index+5;
    for (index; index < max; index++)
    {
      struct address tmp;
      foo = "192.168.0." + index;
      memcpy(tmp.add, foo.c_str(), foo.size());
      tmp.owner[0] = 0;
      aList.push_back(tmp);
    }
  }
}

OUTPUT:
NEW ADDRESS GENERATED: 192.168.0.0
NEW ADDRESS GENERATED: 192.168.0.1
NEW ADDRESS GENERATED: 192.168.0.2
NEW ADDRESS GENERATED: 192.168.0.3
NEW ADDRESS GENERATED: 192.168.0.4

```When I later try and pull the struct for editing, the data in the field add ouputs as It should, but after I edit owner it changes in a strange way which you can see in my output below.

```

address AFC:: getFreeAdd(string name)
{
  for(int i = 0; i < aList.size(); i++)
    {
      if(aList.at(i).owner[0] == 0)
      {
        cout << aList.at(i).add << endl;
        memcpy(aList.at(i).owner, name.c_str(), name.size());
        cout << aList.at(i).add << endl;
        return aList.at(i);
      }
    }
    cout << "| -- -- No more free address'..." << endl;    
}

OUTPUT:
192.168.0.0
192.168.0.0m&#65533;192.168.0.1

```Could anyone with more knowledge of C please explain to me why this happens, so that I can try and prevent it.

Thanks very much

---

### Post by MindSz on 2010-03-10
My vectors are a little rusty, but it looks like you're not terminating your strings correctly, like ```
addr[10] = '\0';
owner[4] = '\0';
```Note: Remember array indexes start from 0

---

### Post by TMagic*04 on 2010-03-10
> **MindSz said:**
> My vectors are a little rusty, but it looks like you're not terminating your strings correctly, like ```
addr[10] = '\0';
owner[4] = '\0';
```Note: Remember array indexes start from 0

That makes sense, however it didn't work as thought. I appended the endstring char onto the end of the address' I added, and in the owner field. Now my ouput is like so:

192.168.0.0
192.168.0.0me&#65533;192.168.0.1

where the value"me" was what I wanted the owner field to be. So it looks like it's appended the value and the next address onto the end. Could this be memory mismanagement due to me wanting to put something of size 2 into an array defined as size 5?

---

### Post by MindSz on 2010-03-10
No, you are allowed to do that, but you have to make sure that the '\0' character is right after the end of the word. So for the word 'me' the '\0' character should be in owner[2]. So the string would look like```
owner[0] = 'm';
owner[1] = 'e';
owner[2] = '\0';
```

---

### Post by TMagic*04 on 2010-03-10
Ahhh ok, that was my mistake I was always appending it at owner[4].

I did that and it outputted:

192.168.0.0me
192.168.0.0me

So I made sure that after editing owner I redefined address[11] as '\0', and it worked perfectly.

Thanks very much for all your help

---

### Post by Tony Flury on 2010-03-10
I am not a C++ expert, but since you are using vectors (which are a C++ construct), why not use the C++ strings class, which would allow you to avoid all of the problems with null tremination etc.

---

### Post by TMagic*04 on 2010-03-10
This may sound like a very stupid statement so please correct me if i'm wrong. But I was under the impression that strings in c were just char[] and that in c++ you could use string which is the same as std:: string if you're using namespace std.

---

### Post by MadCow108 on 2010-03-10
string is a C++ string class which, as already mentioned, handles all the difficulties of c strings for you.
Internally it may use a char[] as a buffer, but that is not of concern to the user.
it is strongly recommended to use c++ strings instead of c strings unless there is a good reason not to do so.

generally you should make better use of C++
you could make a class out of your address struct and its members should be in a more useful format than a string.
For printing you can then overload the << stream operator.

---

