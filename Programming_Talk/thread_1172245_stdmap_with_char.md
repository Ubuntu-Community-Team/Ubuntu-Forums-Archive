---
title: "std::map with char*"
date: 2009-05-28
forum: Programming Talk
---

### Post by monkeyking on 2009-05-28
Hi,
can anyone tell me why i can't clean up the memory,
and maybe a small solution.


I'm allocing memory with strdup for each key,
but I cant figure out how to erase the key with free.
[PHP]

#include<iostream>

#include<cstring> //for cstring functions
#include<map> //associative array
#include<cstdlib> 


struct cmp_str {
  bool operator()(const char *a,const  char *b) {
    return std::strcmp(a, b) < 0;
  }
};

void printMap(std::map<const char*,int,cmp_str> &asso){
  for(std::map<const char*,int>::const_iterator it = asso.begin(); it != asso.end(); ++it){
    printf("%s:\t %d\n",it->first,it->second);
  }
}



std::map<const char*,int,cmp_str> build(){
  std::map<const char*, int,cmp_str> asso;
  
  const char *text = "does is work";
  char *tmp=NULL;
  tmp = strtok(strdup(text)," \t");
  
  while(tmp!=NULL){
    asso[strdup(tmp)] = 1;
    tmp=strtok(NULL," \t");
  }
  return asso;
}

void cleanup(std::map<const char*,int,cmp_str> &asso){
  std::map<const char*,int,cmp_str>::iterator it;
  asso.erase(asso.begin(),asso.end());
}


int main(int argc, char** argv){
  std::map <const char*, int,cmp_str> asso = build();
  printMap(asso);
  printf("should return 1: %d\n",asso["is"]);
  printf("should return 0: %d\n",asso["0"]);
  cleanup(asso);
  return 0;
}
[/PHP]

Thanks in advance

---

### Post by dwhitney67 on 2009-05-28
](*,)

Why are you mixing C-style functionality with C++ code?


Try something like this to populate your map:
```

#include <string>
#include <map>
#include <sstream>
#include <algorithm>
#include <iostream>


void display(const std::pair<std::string, int>& token_info)
{
  std::cout << "token = " << token_info.first << ", id = " << token_info.second << std::endl;
}

int main()
{
  std::string       str = "does this work";
  std::stringstream iss(str);
  std::map<std::string, int> token_id;

  std::string token;
  int         id = 0;

  while (iss >> token)
  {
    token_id.insert(std::make_pair(token, id++));
  }

  std::for_each(token_id.begin(), token_id.end(), display);
}

```
Note that I did not rely on char*, nor did I rely on any type of memory allocation.

---

### Post by monkeyking on 2009-05-28
Hi dwhitney
I don't understand your apartheid with mixing c++ and c.
Look at this program.

[PHP]
#include <algorithm>
#include <iostream>
#include<fstream> //ifstream requires fstream
#include <cstring>


#define LENS 10000

void display(const std::pair<std::string, int>& token_info)
{
  std::cout << "token = " << token_info.first << ", id = " << token_info.second << std::endl;
}

void printMap(const std::map<char*,int>& asso){
  
  for(std::map<char*,int>::const_iterator it = asso.begin(); it != asso.end(); ++it){  
    printf("%s\t%d\n",it->first,it->second);
  }



}


int first()
{
  std::ifstream pFile("tmp",std::ios::in);
  
  if(!pFile){
    return 0;
  }

  char buffer[LENS];
  while(!pFile.eof()){
    pFile.getline(buffer,LENS);
    std::string       str = std::string(buffer);
    std::stringstream iss(str);
    std::map<std::string, int> token_id;
    
    std::string token;
    int         id = 0;
    
    while (iss >> token)
      {
	token_id.insert(std::make_pair(token, id++));
      }
    
    std::for_each(token_id.begin(), token_id.end(), display);
  }
} 


int second()
{
  std::ifstream pFile("tmp",std::ios::in);
  
  if(!pFile){
    return 0;
  }

  std::map<char *, int> token_id;

  char buffer[LENS];
  int id =0;
  while(!pFile.eof()){
    pFile.getline(buffer,LENS);

    char *tok = strtok(buffer," \t");

    while (tok!=NULL){
      token_id[strdup(tok)]=id++;
      tok=strtok(NULL," \t");
    }
        
  }
  printMap(token_id);
  return 0;
} 



int main(){
  time_t t;
  int dif1 = time(&t);
  first();
  int dif2 = time(&t);
  std::cerr<<dif2-dif1<<std::endl;
  second();
  dif1 = time(&t);
  std::cerr<<dif1-dif2<<std::endl;

  return 0;
}
[/PHP]

Your program takes 42 second for 170 meg file,
mine takes 14 seconds.
```

./a.out >out
42
14

```
And if you scale it to 600 gig files like i'm currently doing,
this is huge time difference.

I can understand the argument that it is not as portable,
nor as beautifull, Maybe even ugly.

But these c++ streams are simply to slow.

---

### Post by dwhitney67 on 2009-05-29
Have you considered that it is probably the disk-IO that is affecting the performance?

Try running your program first, then the second program you wrote (based on my solution), to see if you yield comparable results as you did earlier.

Lastly, there is a hit when copying strings (as I did in my example).  You could attempt to use something similar to the following, where allocation/deallocation takes place:
```

#include <fstream>
#include <string>
#include <map>
#include <sstream>
#include <algorithm>
#include <iostream>


void display(const std::pair<std::string*, int>& token_info)
{
  std::cout << "token = " << *(token_info.first) << ", id = " << token_info.second << std::endl;
}

void destroyKey(const std::pair<std::string*, int>& token_info)
{
  delete token_info.first;
}

int main(int argc, char** argv)
{
  typedef std::map<std::string*, int> TokenMap;

  std::fstream file(argv[1], std::ios::in);
  char         line[1024];
  TokenMap     tokens;

  int id = 0;

  while (file.getline(line, sizeof(line)))
  {
    std::stringstream iss(line);

    while (!iss.eof())
    {
      std::string* token = new std::string;
      iss >> (*token);
      tokens.insert(std::make_pair(token, id++));
    }
  }

  //std::for_each(tokens.begin(), tokens.end(), display);   // commented out - will cause unnecessary delays
  std::for_each(tokens.begin(), tokens.end(), destroyKey);
}

```
Since I do not have an ASCII file containing 160MB of data, I cannot perform any benchmark testing.  Perhaps you can post your data file at a 3rd-party site?

---

### Post by MadCow108 on 2009-05-29
> **dwhitney67 said:**
> Since I do not have an ASCII file containing 160MB of data, I cannot perform any benchmark testing.  Perhaps you can post your data file at a 3rd-party site?

just copy paste some random ascii strings in a file until it reaches 160mb :)

Its better to directly use the filestream instead of converting the filestream to a stringstream and using the stringstream.

```

  std::ifstream pFile("tmp",std::ios::in); 
   
  if(!pFile){ 
    return 0; 
  } 

 std::map<std::string, int> token_id; 

  std::string token; 
  int         id = 0; 
     
  while (1)
  {
  	if (!pFile.good()) break;
  	pFile >> token;
  	token_id.insert(std::make_pair(token, id++)); 
  }
  //printMap(token_id); 
  return 0; 

```

shorter cleaner code and with and without -O3 its faster than the c/c++ mix
g++ -O3 test2.c && time ./a.out 
c/c++ 16
filestream 6

with a 41mb file with following content repeated:
t s d 2 r b g g

this data will obviously insert near nothing in the map (because it only allowes unique key's, [use multimap for normal associatve arrays]) but the file input is very fast.
(i don't really see the point in using a map here but i don't know the problem)
note that you can increase the speed of inserting into a map dramaticly when you give the insert function the position where the data should be inserted (if possible in your problem)

edit: I saw that you ad pointers to chars as a key to an array, which result is that every key is different but pointing to the same type of char, so it adds loads of entries into the map where it acually shouldn't from my understanding (remember map's are **unique** key containers). While the string map only has unique string keys. So the Code has completly different results.
If you want to put pointers into a map (which i wouldn't recommend) then you need to give the map a compare function to evaluate the pointer (except you delibratly want a integer comparision for a char pointer).

I don't quite understand what you are trying to archive with the map so I rebenchmarked with pure file input and no use of the map:
Result is similar (this time 187mb of upper data):
c/c++ mix:                      24s
let filestream do tokenization: 17s

as you see the use of filestream is still faster. Thats because you use a filestream read a whole line and tokenize that instead of directly tokenize the filestream like in my implemenation.

What you do with the read data is now up to you. My assumption is that you should rethink the use of maps (maybe use multimaps, unorderd maps, maps with strings or give the map an appropriate function to compare the pointers)

---

### Post by monkeyking on 2009-05-29
Hi,
Well I am supplying a compare function, called cmp_str.
It's the very first function in the code snippet.

The file are flatfiles.
with columns like
Id tab id2 tab data1 tab data2 tab etc.

So it wouldn't make sense to use one continues stream. I would have to check for newlines.

The value of id is not unique, neither is id2.
But the concatenation of (id,id2) is.

I doubt it will be faster to input 34 million std::string than cstrings into a map.

Atleast I couldn't do it.

Thanks for your responses, and input.
But I didn't start up with this mish mash of source code.

I tried the iterator,stringstream, and it was horribly slow.
Havn't checked the latest version of dwithney or madcow though.


If we forget these arguments about bad design choices,
and just want to delete a array of pointers as a key in a std::map,
how would you do it.

thanks again.

---

### Post by dwhitney67 on 2009-05-29
> **monkeyking said:**
> ...

If we forget these arguments about bad design choices,
and just want to delete a array of pointers as a key in a std::map,
how would you do it.

thanks again.

See the second code example I provided; if you know that your cstrings are allocated using malloc(), then just replace the delete with a free().

---

### Post by MadCow108 on 2009-05-29
I'm sorry I missed the compare function I didn't read your first post to thouroughly :/


checking for newline is pretty simple. Just insert following in the code:
if (pFile.peek() == '\n') {...}
You#ll have to test if this decreases performace stronger than the use of cstrings (note that your benchmark code is missing the compare function and therefore producing different results)
[with my data file and a empty if statement it's still slighly faster]
You could probably optimise it if there is a minimum coloumn length by not peeking x coloumns after a new line.

Inserting a string should not take longer than inserting a char. Internally it probably works with references anyway.
The string creation from the stream has already shown to be faster.

---

### Post by Habbit on 2009-05-29
> **MadCow108 said:**
> checking for newline is pretty simple. Just insert following in the code:
if (pFile.peek() == '\n') {...}
You should use either the [istream::getline(char*, size_t)]("http://www.cplusplus.com/reference/iostream/istream/getline/") or the [global getline(istream&, string&)]("http://www.cplusplus.com/reference/string/getline/") functions for such tasks - don't reinvent the wheel. Even if you extract the data from ifstream to a std::string object, you can use strtok instead of isstreams if you want: just use my_string.c_str() to get a C style char*.

Nevertheless, there is a C++ way of doing the whole thing. Here I suppose an ASCII file of tab-separated fields: ```

ifstream my_file("my_file.txt");
string line, field;
while(getline(my_file, line)) {
    int cur_pos = 0;
    int next_tab;
    while ((next_tab = line.find('\t', cur_pos)) != string::npos) {
        string field = line.substr(cur_pos, next_tab-cur_pos);
        // Use "field" however you want
        cur_pos = next_tab + 1;
    }
    // There are no more tabs, so we still have one field left
    line.erase(0, cur_pos);
    // Now use "line" as the last field
}
```
I haven't checked anything, so this code might containt a lot of off-by-one errors. If you want to be even more efficient and spare the alloc-and-dealloc cost of "string field = " you could declare a fixed-size char buffer, change the substr line to line.copy(buf, next_tab-cur_pos, cur_pos) and adapt the last field line accordingly.

---

### Post by MadCow108 on 2009-05-29
if you use getline and the tokenize it's slower than checking for newline by yourself (especially if you know the number of columns)
At least on my machine with my test file its about 20% slower.

using find is also slower but that can probably be optimised. Although I find the code harder to read.

op should have enough methods now to make an decision which fits his wishes the best :)

attached my benchmark code if you want to test the possibilities yourself.

---

### Post by Habbit on 2009-05-29
Well, if you know the number of columns you don't need to check for \n either, just read that amount of bytes into a buffer and tokenize it using whichever method you prefer. Different problems, different solutions.

---

### Post by MadCow108 on 2009-05-29
the use of a seperate buffer should be avoided if you want high performance.
The stream class handels that for you. The only thing you need to do is count the calls to the >> operator and act according to the data file you are parsing.
If you read a whole line into a buffer and then tokenize the buffer you read the same data twice (although the second time its faster because it's in the ram, still it is unecessary).

It's all not very important if you only have 1 or 2 columns and small files.
But with huge files and many columns it makes a huge difference (try it with 40-50 columns, the stream function is 4-5 times faster than with a buffer).

If the minimum column number is much smaller than the average column number it is probably better to write your own function to read formated data (kind of overload ">>") and let it returns value be dependend on what skip character it read. Like that you read the file data without another buffer and can still react to a new line.
Probably this is already built in into filestreams somehow, I just don't know it ^^
(or write into the datafile how many columns a line has when you create it etc...)

---

### Post by monkeyking on 2009-05-30
Thanks for your responses.

But this really isn't my question.


How do I cleanup?

[PHP]
const char* input = "key"; 
std::map<char*,int> aMap;
aMap[strdup(key)] = 1;

//or even more generally
const char* input = "key"; 
std::map<char*,int*> aMap;
aMap[strdup(key)] = new int[5];
[/PHP]

---

### Post by Habbit on 2009-05-30
Ok, sorry for battling over something not directly related with your question. Let's see, the map will not perform any cleanup actions on its keys/values other than those specified by their destructors - and pointers have no destructors. So, you need to ensure that whenever you extract something from the map, you release its resources. For example: ```
typedef map<char*, int*, my_str_cmp> my_map;
my_map data;

data[strdup("abc")] = new int(2);
// ...

// Now use it
my_map::iterator it = data.find("abc");
if (it != data.end()) {
    my_map::value_type item = *it;
    // ... (use the data)
    
    data.erase(it);
    free (item.first);  // key was alloced by strdup -> malloc
    delete item.second; // value wa alloced by new
}
```

---

### Post by monkeyking on 2009-05-30
Thanks habbit

I cleans up nicely now.

But I am puzzled by why

[PHP]
std::map <char*,size_t*,cmp_str>::iterator it;

for(it = asso.begin(); it != asso.end(); ++it){
    std::map <char*,size_t*,cmp_str>::value_type item = *it;
    free(item.first);
    delete [] (item.second);
}
[/PHP]

Whereas the following, (I just moved the type declaration out of the loop)
[PHP]
std::map <char*,size_t*,cmp_str>::iterator it;
std::map <char*,size_t*,cmp_str>::value_type item;
for(it = asso.begin(); it != asso.end(); ++it){
    item = *it;
    free(item.first);
    delete [] (item.second);
}
[/PHP]
gives a compile error

---

### Post by Habbit on 2009-05-30
AfaIk, map<T,E>::value_type translates to std::pair<const T, E>. Thus, "item" as a local object in your stack frame cannot be assigned to because item.first is of type "char *const" (not "const char*", which would be assignable). You could use a value_type* object instead of the object itself, but you'd need to release the key and value _before_ calling erase because the map might destroy the pointed-to std::pair on that call. However, doing that has its own problems if you are using multithreading (your are leaving the map in a partially inconsistent state), so I'd just stick to the first version, as constructing and destructing a std::pair<char *const,size_t*> on each loop is not that much of a tragedy.

---

### Post by dwhitney67 on 2009-05-30
You really do not need this statement:
```

std::map <char*,size_t*,cmp_str>::value_type item = *it;
...

```

This would have sufficed within your loop:
```

free(it->first);
delete it->second;

```

Btw, in your previous example(s), you allocated only one int for the map's value, not an array of them.  Thus the [] operator for the delete call is not warranted.

---

### Post by dwhitney67 on 2009-05-30
Btw, just for grins, I was working on a problem that involved the usage of an STL map, and I decided to try your approach of storing a char* as the key to the map.

One limitation I have found to this approach is that it is not possible to search for entries in the map using the find() method.  The reason for this is because the map is storing pointers, and unless I pass find() the exact same pointer address of the element I am looking for, find() fails.

Perhaps I can explain better with code:
```

map<char*, Value*> MyMap;

MyMap mm;

mm.insert(make_pair(strdup("foo"), new Value());

...

MyMap::iterator it = mm.find("foo");

assert(it != mm.end());

```

---

### Post by Habbit on 2009-05-30
> **dwhitney67 said:**
> One limitation I have found to this approach is that it is not possible to search for entries in the map using the find() method.  The reason for this is because the map is storing pointers, and unless I pass find() the exact same pointer address of the element I am looking for, find() fails.
True, this seems to be a defect of the STL map class. The TR1/C++0x unordered_map (hash table) class, on the other hand, allows you to specift a key equality comparison function, so it seems that "find" ought to work.

---

### Post by MadCow108 on 2009-05-30
the STL map class can also have a comparision function (a point missed by me earlier in this same thread :) ).
an example is in op's first code post.
```

std::map<const char*, int,compare_function> mymap;

```
(haven't tested it with chars though)

---

### Post by Habbit on 2009-05-30
> **MadCow108 said:**
> the STL map class can also have a comparision function (a point missed by me earlier in this same thread :) ).
an example is in op's first code post.
```

std::map<const char*, int,compare_function> mymap;

```
(haven't tested it with chars though)

Yes, but that function establishes a less-than ordering. It only serves to sort the keys, not to establish equality between them. That's why I mentioned unordered_map<Key, T, Hash=hash<Key>, Equality=equal_to<key>, Allocator=allocator<T> >. What I don't know is if such equality comparer is used in the find() function too or just for resolving hash collisions.

---

### Post by MadCow108 on 2009-05-30
weak ordering seems to be enough for find.
at least this code works:
```

#include <iostream>
#include <map>
#include <stdio.h>
#include <string.h>
using namespace std;

struct cmp_str { 
  bool operator()(const char *a,const  char *b) { 
    return strcmp(a, b) < 0; 
  } 
};

int main ()
{
  map<const char*,int,cmp_str> mymap;
  map<const char*,int,cmp_str>::iterator it;

  mymap.insert(make_pair(strdup("f"), 1001));
  mymap.insert(make_pair(strdup("g"), 2002));
  mymap.insert(make_pair(strdup("h"), 3003));
	const char * search = "h";
	 it=mymap.find(search);
	 cout << (*it).first<<" "<<(*it).second << endl;
	 const char * search2 = "g";
	 it=mymap.find(search2);
	 cout << (*it).first<<" "<<(*it).second << endl;
	 const char * search3 = "f";
	 it=mymap.find(search3);
         cout << (*it).first<<" "<<(*it).second << endl;
         const char * search4 = "z";
         it=mymap.find(search4); // fails although "z" > every member in map
         if (it != mymap.end()) cout << (*it).first<<" "<<(*it).second << endl;
         const char * search5 = "a";
         it=mymap.find(search5); // fails although "a" < every member in map
         if (it != mymap.end()) cout << (*it).first<<" "<<(*it).second << endl;

  return 0;
}

```
```

g++ test.c && ./a.out 
h 3003
f 1001
g 2002

```

whereas the map without the compare function fails as dwhitney67 pointed out
btw how to i check if a find was successful?
if (it == it.end())
gives me:
test.c:33: error: &#8216;struct std::_Rb_tree_iterator<std::pair<const char* const, int> >&#8217; has no member named &#8216;end&#8217;

---

### Post by Habbit on 2009-05-30
It seems you are right: according to the SGI documentation, in Sorted Associative Containers two keys a and b are considered equal if ((a < b) || (b < a)) is false. [http://www.sgi.com/tech/stl/SortedAssociativeContainer.html]("http://www.sgi.com/tech/stl/SortedAssociativeContainer.html")

EDIT: "end" is not a method of the iterator, but of the map itself, like all containers

---

### Post by monkeyking on 2009-05-31
Apparantly my original problem can be solved by a const_cast, like

[PHP]
void cleanup(std::map<const char*,int,cmp_str> &asso){
  std::map<const char*,int,cmp_str>::iterator it = asso.begin();
  for(;it!=asso.end();it++)
    free(const_cast<char*>(it->first));
}
[/PHP]

And if the value was an array

[PHP]
void cleanup(std::map<const char*,int,cmp_str> &asso){
  std::map<const char*,int,cmp_str>::iterator it = asso.begin();
  for(;it!=asso.end();it++){
    free(const_cast<char*>(it->first));
    delete [] it->second;
  }
}

[/PHP]

---

