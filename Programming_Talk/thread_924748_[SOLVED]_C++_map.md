---
title: "[SOLVED] C++ map"
date: 2008-09-19
forum: Programming Talk
---

### Post by kjohansen on 2008-09-19
I am attempting to do some graph algorithms and store the nodes in a map.

I am reading in data from a file and filling the nodes, my program is not reading in the number of nodes it should.

[php]
    string line;
    vector<string> singMovie;
    vector<vector<string> >   allMovies;
    vector<string> actorsInCurrentMovie;
    map<string,int> actors;
    map<string,int>::const_iterator mlMap;
    int actorCount=0;
    typedef pair<string,int> Map_Pair;

    ifstream myfile("movie-top-grossing.txt");
    if(myfile.is_open()){
        while(!myfile.eof()){   //while not empty
            singMovie.clear();  //clear temp holder
            getline(myfile,line);  //read line from file
            if(line==""){    //if line is empty
                break;  //get out of loop
            }
            Tokenize(line,singMovie,"/");   //split the string on the delim
            allMovies.push_back(singMovie); //put the current movie into all movies
            for(int i=1;i<singMovie.size();i++){  //loop through all actors (movie title is at "0" so start at 1
                mlMap=actors.find(singMovie[i]);  //search for actor
                if(mlMap==actors.end()){     //if actor does not exist
                    actors.insert(Map_Pair(singMovie[i],actorCount));    //put the actor and the count into the map
                    actorCount++;  //increase actor count
                }
            }

        }
    }

    cout<<allMovies.size()<<endl<<actorCount;
[/php]

The number of movies I expect is 187 which I get correctly, but I do not the number of actors I expect.  The number of actors I expect is off by 13.  I know the file is right.

What I think is happening is that I am using the find function wrong. Since the find function returns an iterator, the iterator might return a result but not the the correct record I am looking for.  By that I mean I think the hash function is not unique for these values and the iterator is not equal to the end so it does not add the actor but it should.

How do I check to make sure the find function is returning the right result and not just one with the same hash?  Or am I way off base...

---

### Post by dwhitney67 on 2008-09-19
The for-loop, where you are looping through all actors of a single movie, should begin from 0, not 1.

Btw, you should consider defining data structures to hold your data, rather than depend on "floating" definitions.

Also consider moving declarations of data closer to where they are first used and only needed.  Case in point is some of the declarations you have outside the main loop.

Also consider adding white-space in your code; it would make it a lot easier to read.

---

### Post by kjohansen on 2008-09-19
The loop should start at 1 not 0 this is intentional.

the file is Movie name/actor 1/actor 2/actor 3......  and I want to remove movie name

Turns out I had a different input file than I thought, so this isnt a problem anymore.

But is my question in general valid?  Why does the find function return an iterator?  Is it possible for it to return multiple results, results that have the same hash value but are different?

---

### Post by dwhitney67 on 2008-09-19
Using an STL map, you can only use unique keys.  Thus when using find(), you are guaranteed to either obtain an iterator to a valid pair (key,value) or the end iterator of the map; the latter implies the key was not found.

The usage of find() in your code is correct.

If for example you are storing movie titles as the key, then you should consider using an STL multimap.

Back to your original code, I would suggest using a structure to define a movie.  For example:

[php]
// Vector of Actor names
typedef std::vector<std::string> Actors;

struct Movie
{
  std::string title;    // probably redundant??
  Actors      actors;
  // date released, producing studio, etc.
};

// key = movie title, value = Movie structure
//
typedef std::multimap< std::string, Movie > AllMovies;
typedef AllMovies::const_iterator           AllMovies_CIter;
typedef AllMovies::iterator                 AllMovies_Iter;
[/php]

---

### Post by kjohansen on 2008-09-19
oh, so the iterator is just returned to point to the key and the value.

in the final product there will be data structures, not as you mentioned but in a way to store a graph. most of what is in the loop is temporary to populate the graph nodes and edges.

the final product will have a class called node.  each node corresponds to an actor. each node has an adajcency list of actors with a corresponding movie name.

this will allow an easy breadth first search to solve the 6 degrees of Kevin Bacon problem.

---

