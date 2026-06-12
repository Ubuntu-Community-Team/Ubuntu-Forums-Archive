---
title: "[C++] Can't fill 2D vector - need some help."
date: 2009-07-19
forum: Programming Talk
---

### Post by credobyte on 2009-07-19
```
          Col1           Col2
-----------------------------------
1:    filename       full path
2:    filename       full path
3:    filename       full path
4:    filename       full path
x:    filename       full path
```The idea is very simple - I'm trying to figure out how to save filename and full path in a 2D vector. So far, no luck .. Segmentation fault on every launch ( no errors while compiling ).

What would be the best/right way of doing such a thing ( none of these "examples" work for me ) ?

```
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    vector< vector<string> > file;

    file.push_back("myfile.txt", "/etc/myfile.txt");
    
    cin.get();
    return 0;
}
``````
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    vector< vector<string> > file;

    file[0][0] = "myfile.txt";
    file[0][1] = "/etc/myfile.txt";
    
    cin.get();
    return 0;
}

```

---

### Post by dwhitney67 on 2009-07-19
The first example you provided is jibberish; no way would it ever work.

In the second example, you have not pre-sized the vectors, thus you are unable to index into the vectors as you have shown.

Try something like:
```

std::vector<std::string> strVec;
strVec.push_back("One");
strVec.push_back("Two");
strVec.push_back("Etc");

std::vector<std::vector<std::string> > twoDeeVec;

twoDeeVec.push_back(strVec);

```
There are other ways to accomplish the same, but without knowing more about your data (structures), I can't/won't elaborate further.

You should check-out the [API]("http://www.cplusplus.com/reference/stl/vector/") for vector when you have the chance.

---

### Post by credobyte on 2009-07-19
Thnx, however, that's not exactly what I'm trying to achieve. Your example works just fine, except, I can't find the second dimension !

Result was:
```
vector[0][0] ... one
vector[0][1] ... two
vector[0][2] ... three
vector[0][3] ... four
```

I need:
```
vector[0][0] ... one
vector[0][1] ... another, a bit different "one"
vector[1][0] ... two
vector[1][1] ... another, a bit different "two"
```

As previously said, I need a way to store filename & path ( so I could access both details by knowing only their location ( like, third row ).

---

### Post by issih on 2009-07-19
The pattern you are creating us a vector or vectors...

In essence you have a vector, which contains two vectors of strings.

Unless you have some reason to need the flexibility of having a variable number of vectors, e.g. you plan to have modification time or whatever too, and the number of lists will potentially be variable, this is pointless...Just have two vectors, one for filenames and one for paths, and fill them as appropriate.

---

### Post by issih on 2009-07-19
```

std::vector<std::string> strVec;
strVec.push_back("One");
strVec.push_back("Two");
strVec.push_back("Etc");

std::vector<std::string> strVec2;
strVec.push_back("1");
strVec.push_back("2");
strVec.push_back("3");

std::vector<std::vector<std::string> > twoDeeVec;

twoDeeVec.push_back(strVec);
twoDeeVec.push_back(strVec2);

```
N.B. credit to dwhitney here, I'm just extrapolating what he/she thought was obvious..

Thats all you need to do, but as I say, its a bit pointless....If you really need to do this, I'd suggest making the top level one a vector of pointers, because the push_back copies things by value which is rather inefficient if these lists get large.

---

### Post by credobyte on 2009-07-19
> **issih said:**
> The pattern you are creating us a vector or vectors...

In essence you have a vector, which contains two vectors of strings.

Unless you have some reason to need the flexibility of having a variable number of vectors, e.g. you plan to have modification time or whatever too, and the number of lists will potentially be variable, this is pointless...Just have two vectors, one for filenames and one for paths, and fill them as appropriate.

Yes, that would work, however, if at least 1 allocation will fail, the whole program execution will be useless ( as data will be incorrect ). That's why I want them to be in 1 place - if something goes wrong, allocation fails but other data is still valid.

---

### Post by dribeas on 2009-07-20
> **issih said:**
> The pattern you are creating us a vector or vectors...

In essence you have a vector, which contains two vectors of strings.

Unless you have some reason to need the flexibility of having a variable number of vectors, e.g. you plan to have modification time or whatever too, and the number of lists will potentially be variable, this is pointless...Just have two vectors, one for filenames and one for paths, and fill them as appropriate.

It is not just a problem of flexibility, dealing with two different vectors is a design error that can lead to hard to track errors if you make a mistake later on (update just one of the two vectors, for example).

If you want to store pairs of 'filename', 'full path', just do so. Either use std:: pair, or define your own data structure.

```

std::vector< std::pair< std::string, std::string > > files;
files.push_back( 
   std::pair< std::string, std::string >( 
      "config.txt", 
      "/home/user/.app/config.txt" ) );
// ...

```

or with your own data structure:

```

struct file_path {
   file_path( std::string const & name, std::string const & full_name ) 
      : name( name ), full_name( full_name ) {}
   std::string name;
   std::string full_name;
};
int main() {
   std::vector< file_path > files;
   files.push_back( file_path( "config.txt", "/home/user/.app/config.txt" ) );
   // ...
}

```

Both solutions provide a great deal of flexibility. If what you want to do is just mapping from short names into full paths, another thing you can do is creating a map or multimap (depending on whether you want to allow a short name to be mapped into more than one full paths):

```

// does not allow repeated short names (limitation of design)
std::map< std::string, std::string > files;
files[ "config.txt" ] = "/home/user/.app/config.txt";
//...

// allow multiple full paths for a single short name
std::multimap< std::string, std::string > files;
files.insert( pair< std::string, std::string >("config.txt", "/home/user/.app/config.txt" ) );
//...

```

Where you can use a helper function to ease the syntax:

```

void insert_file( std::multimap<std::string, std::string> & map, std::string const & name, std::string const & path )
{
   map.insert( make_pair( name, path ) ); // the compiler knows you want std::strings at this time
}
int main()
{
   std::multimap<std::string, std::string> files;
   insert_file( files, "config.txt", "/home/user/.app/config.txt" );
   // ...
}

```

Where this solution can be used as a helper for the std::vector< std:: pair< std::string, std::string > > above. If you are using this inside a class, you can have the helper function being a private member and avoid the need to pass the multimap<> reference around (use the attribute directly).

---

### Post by MadCow108 on 2009-07-20
if you only need to save filename and path you can use pairs:
```

vector< pair<string,string> > files;
files.push_back(make_pair("path","filename"));
cout << files[0].first << " " << files[0].second << endl;

```

for real multidimensional arrays you could look at the boost library. It also has tuples (pairs with more than 2 entries)

(oops didn't read dribas post properly he already suggestet that :/ )

---

### Post by credobyte on 2009-07-20
Thanks to everyone who tried to help - problem solved ( pairs was exactly what I needed ) :)

---

### Post by dwhitney67 on 2009-07-20
Personally, I would have used a structure.  One never knows when an additional piece of information may be needed to be associated with the two you already have.

---

### Post by fr4nko on 2009-07-20
> **dwhitney67 said:**
> Personally, I would have used a structure.  One never knows when an additional piece of information may be needed to be associated with the two you already have.
I agree. For me something like that is more simple  and more flexible:
```

struct config_item {
  std::string key;
  std::string value;

  config_item(std::string _key, std::string _val) : key = _key, value = _val {}
};

// ...
std::vector<config_item> config;

config.push_back( config_item("home", "/home/myname") );

```
but this is just a matter of taste :-)

Francesco

---

### Post by credobyte on 2009-07-20
> **fr4nko said:**
> I agree. For me something like that is more simple  and more flexible:
```

struct config_item {
  std::string key;
  std::string value;

  config_item(std::string _key, std::string _val) : key = _key, value = _val {}
};

// ...
std::vector<config_item> config;

config.push_back( config_item("home", "/home/myname") );

```but this is just a matter of taste :-)

Francesco

For me, it's a matter of understanding ( still learning ) :) I will definitely take a look at this structure thing after finishing my current project.

---

